---
ms.openlocfilehash: eb51caa4caf0d425b5e49c3abca2a523b08fc312
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718089"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>Configuration du flux de la caméra PV

- Dans **Project Settings > HoloLens**, activez la fonctionnalité **Webcam** :

![Capture d’écran des paramètres du projet HoloLens avec la propriété Webcam mise en surbrillance](../images/unreal-pvc-img-01.png)

- Créez un acteur appelé « CamCapture » et ajoutez un plan pour rendre le flux de la caméra :

![Capture d’écran d’un acteur avec un plan ajouté](../images/unreal-pvc-img-02.png)

- Ajoutez l’acteur à votre scène, créez un matériau appelé CamTextureMaterial avec un paramètre d’objet de texture et un échantillon de texture.  Envoyez les données RVB de la texture à la couleur d’émission en sortie :

![Blueprint d’un échantillon de matériau et de texture](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>Rendu du flux de la caméra PV

- Dans le blueprint CamCapture, activez la caméra PV :

![Blueprint de la fonction Activer/désactiver ARCapture avec la caméra PV activée](../images/unreal-pvc-img-04.png)

- Créez une instance de matériau dynamique à partir de CamTextureMaterial et affectez ce matériau au plan de l’acteur :

![Blueprint de la fonction Créer une instance de matériau dynamique](../images/unreal-pvc-img-05.png)

- Récupérez la texture du flux de la caméra, et affectez-la au matériau dynamique, si elle est valide.  Si la texture n’est pas valide, démarrez un minuteur, puis réessayez une fois le délai d’expiration écoulé :

![Blueprint de la texture du flux de la caméra affectée au matériau dynamique](../images/unreal-pvc-img-06.png)

- Enfin, mettez à l’échelle le plan selon les proportions de l’image de la caméra :

![Blueprint du plan mis à l’échelle par rapport aux proportions des images de la caméra](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>Rechercher des positions de la caméra dans l’espace universel

La caméra sur le casque HoloLens 2 est décalée verticalement par rapport au suivi de la tête de l’appareil.  Pour tenir compte du décalage, il existe quelques fonctions qui permettent de localiser la caméra dans l’espace universel.

GetPVCameraToWorldTransform obtient la transformation dans l’espace universel de la caméra PV, et est positionné sur l’objectif de la caméra :

![Blueprint de la fonction Obtenir la transformation de la caméra PV en monde](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint diffuse un rayon de l’objectif de la caméra vers la scène dans l’espace universel Unreal pour rechercher le contenu d’un pixel dans le cadre de la caméra :

![Blueprint de la fonction Obtenir un rayon de l’espace universel depuis un point de la caméra](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics retourne les valeurs intrinsèques de la caméra, qui peuvent être utilisées lors du traitement de la vision par ordinateur sur un cadre de la caméra :

![Blueprint de fonctions intrinsèques de la caméra PV](../images/unreal-pvc-img-10.png)

Pour trouver ce qui existe dans l’espace universel à une coordonnée d’un pixel particulier, utilisez un suivi de ligne avec le rayon d’espace universel :

![Blueprint du rayon d’espace universel utilisé pour déterminer ce qui existe dans l’espace universel à une coordonnée particulière](../images/unreal-pvc-img-11.png)

Nous convertissons ici un rayon à 2 mètres de l’objectif de la caméra en une position dans l’espace de la caméra à ¼ à partir du coin supérieur gauche du cadre.  Nous utilisons ensuite le résultat du pointage pour rendre quelque chose là où l’objet existe dans l’espace universel :

![Blueprint de la conversion d’un rayon à 2 mètres de l’objectif de la caméra en une position dans l’espace de la caméra à 1/4 à partir du coin supérieur gauche du cadre.](../images/unreal-pvc-img-12.png)

Quand vous utilisez le mappage spatial, cette position du pointage correspond à la surface vue par la caméra.

## <a name="rendering-the-pv-camera-feed-in-c"></a>Rendu du flux de la caméra PV en C++

- Créer un acteur C++ appelé CamCapture
- Dans le fichier build.cs du projet, ajoutez « AugmentedReality » à la liste PublicDependencyModuleNames :

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- Dans CamCapture. h, incluez ARBlueprintLibrary.h

```cpp
#include "ARBlueprintLibrary.h"
```

- Vous devez aussi ajouter des variables locales pour le maillage et le matériau :

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- Dans CamCapture.cpp, mettez à jour le constructeur en ajoutant un maillage statique à la scène :

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

Dans BeginPlay, créez une instance de matériau dynamique à partir du matériau de la caméra du projet, appliquez-la au composant de maillage statique et démarrez la caméra HoloLens. 
 
Dans l’éditeur, cliquez avec le bouton droit sur CamTextureMaterial dans l’explorateur de contenu, puis sélectionnez Copy Reference pour obtenir la chaîne de CameraMatPath.

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMateriall = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

Dans Tick, récupérez la texture de la caméra, définissez-la sur le paramètre de texture dans le matériau CamTextureMaterial et mettez à l’échelle le composant de maillage statique selon les proportions du cadre de la caméra :

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>Affichage à partir de l’appareil photo/vidéo pour la capture de Réalité Mixte

> [!NOTE]
> Cela nécessite **Unreal Engine 4.25** ou ultérieur.

Le système et les enregistreurs personnalisés créent des captures de réalité mixte en combinant la caméra PV à des hologrammes affichés par l’application.

Par défaut, la capture de Réalité Mixte utilise la sortie holographique de l’œil droit. Si une application immersive choisit d’être [affichée à partir de la caméra PV](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), ce mode de rendu est utilisé à la place. Le rendu à partir de la caméra PV améliore le mappage entre le monde réel et les hologrammes dans la vidéo de capture de réalité mixte.

Pour choisir le rendu à partir de la caméra PV :

1. Appelez **SetEnabledMixedRealityCamera** et **ResizeMixedRealityCamera**
    * Utilisez les valeurs de taille **Size X** et **Size Y** pour définir les dimensions de la vidéo.

![Troisième caméra](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

Unreal va ensuite gérer les requêtes de capture de Réalité Mixte pour effectuer le rendu du point de vue de l’appareil photo/vidéo.

> [!NOTE]
> C’est seulement quand la [capture de Réalité Mixte](../../../mixed-reality-capture.md) est déclenchée qu’il est demandé à l’application de s’afficher du point de vue de l’appareil photo/vidéo.

## <a name="using-the-pv-camera"></a>Utilisation de l’appareil photo/vidéo

La texture de la webcam peut être récupérée dans le jeu au moment de l’exécution. Toutefois, vous devez l’activer dans l’éditeur **Edit > Project Settings** (Modifier > Paramètres du projet) :
1. Accédez à **Platforms > HoloLens > Capabilities** (Plateformes > HoloLens > Fonctionnalités), puis cochez **Webcam**.
    * Utilisez la fonction **StartCameraCapture** pour utiliser la webcam au moment de l’exécution, et la fonction **StopCameraCapture** pour arrêter l’enregistrement.

![Démarrer/Arrêter la caméra](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Affichage d’une image
Pour afficher l’image de l’appareil photo :
1. Créez une instance de matériau dynamique basée sur un matériau du projet, nommé **PVCamMat** dans la capture d’écran ci-dessous.  
2. Définissez l’instance de matériau dynamique sur une variable **Material Instance Dynamic Object Reference**.  
3. Définissez le matériau de l’objet de la scène qui affichera le flux de l’appareil sur cette nouvelle instance de matériau dynamique.
    * Démarrez un minuteur qui sera utilisé pour lier l’image de l’appareil au matériau.

![Rendu de la caméra](../images/unreal-camera-render.PNG)

4. Créez une fonction pour ce minuteur, dans ce cas **MaterialTimer**, puis appelez **GetARCameraImage** pour obtenir la texture à partir de la webcam.  
5. Si la texture est correcte, définissez un paramètre de texture dans le nuanceur de cette image.  Sinon, redémarrez le minuteur de matériau.

![Texture de la caméra à partir de la webcam](../images/unreal-camera-texture.PNG)

5. Vérifiez que le matériau a un paramètre correspondant au nom indiqué dans **SetTextureParameterValue**, qui est lié à une entrée de couleur. Sans ce paramètre, l’image de la caméra ne peut pas s’afficher correctement.

![Texture de la caméra](../images/unreal-camera-material.PNG)

