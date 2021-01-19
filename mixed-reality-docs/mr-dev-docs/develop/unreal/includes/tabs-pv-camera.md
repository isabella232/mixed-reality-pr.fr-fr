---
ms.openlocfilehash: 53d22260603c4e52096eccf1d7af6a3b0732124e
ms.sourcegitcommit: 672a7a145cfc656273af4ea34f99583eb9fa849c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98225185"
---
# <a name="426"></a>[<span data-ttu-id="bc97f-101">4.26</span><span class="sxs-lookup"><span data-stu-id="bc97f-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="bc97f-102">Configuration du flux de la caméra PV</span><span class="sxs-lookup"><span data-stu-id="bc97f-102">PV Camera Feed Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc97f-103">La caméra PV est implémentée dans les plug-ins Windows Mixed Reality et OpenXR.</span><span class="sxs-lookup"><span data-stu-id="bc97f-103">PV camera is implemented in both Windows Mixed Reality and OpenXR plugins.</span></span> <span data-ttu-id="bc97f-104">Cependant, OpenXR a besoin que le [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) soit installé.</span><span class="sxs-lookup"><span data-stu-id="bc97f-104">However OpenXR needs [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) to be installed.</span></span> <span data-ttu-id="bc97f-105">OpenXR a également une limitation actuelle : la caméra peut fonctionner avec DirectX11 RHI.</span><span class="sxs-lookup"><span data-stu-id="bc97f-105">Also OpenXR has current limitation, camera can work with DirectX11 RHI.</span></span> <span data-ttu-id="bc97f-106">Cette limitation sera levée dans une version d’Unreal à venir.</span><span class="sxs-lookup"><span data-stu-id="bc97f-106">This limitation will be fixed in a further Unreal version.</span></span> 

- <span data-ttu-id="bc97f-107">Dans **Project Settings > HoloLens**, activez la fonctionnalité **Webcam** :</span><span class="sxs-lookup"><span data-stu-id="bc97f-107">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![Capture d’écran des paramètres du projet HoloLens avec la propriété Webcam mise en surbrillance](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="bc97f-109">Créez un acteur appelé « CamCapture » et ajoutez un plan pour rendre le flux de la caméra :</span><span class="sxs-lookup"><span data-stu-id="bc97f-109">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![Capture d’écran d’un acteur avec un plan ajouté](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="bc97f-111">Ajoutez l’acteur à votre scène, créez un matériau appelé CamTextureMaterial avec un paramètre d’objet de texture et un échantillon de texture.</span><span class="sxs-lookup"><span data-stu-id="bc97f-111">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="bc97f-112">Envoyez les données RVB de la texture à la couleur d’émission en sortie :</span><span class="sxs-lookup"><span data-stu-id="bc97f-112">Send the texture’s rgb data to the output emissive color:</span></span>

![Blueprint d’un échantillon de matériau et de texture](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="bc97f-114">Rendu du flux de la caméra PV</span><span class="sxs-lookup"><span data-stu-id="bc97f-114">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="bc97f-115">Dans le blueprint CamCapture, activez la caméra PV :</span><span class="sxs-lookup"><span data-stu-id="bc97f-115">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![Blueprint de la fonction Activer/désactiver ARCapture avec la caméra PV activée](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="bc97f-117">Créez une instance de matériau dynamique à partir de CamTextureMaterial et affectez ce matériau au plan de l’acteur :</span><span class="sxs-lookup"><span data-stu-id="bc97f-117">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Blueprint de la fonction Créer une instance de matériau dynamique](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="bc97f-119">Récupérez la texture du flux de la caméra, et affectez-la au matériau dynamique, si elle est valide.</span><span class="sxs-lookup"><span data-stu-id="bc97f-119">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="bc97f-120">Si la texture n’est pas valide, démarrez un minuteur, puis réessayez une fois le délai d’expiration écoulé :</span><span class="sxs-lookup"><span data-stu-id="bc97f-120">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![Blueprint de la texture du flux de la caméra affectée au matériau dynamique](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="bc97f-122">Enfin, mettez à l’échelle le plan selon les proportions de l’image de la caméra :</span><span class="sxs-lookup"><span data-stu-id="bc97f-122">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![Blueprint du plan mis à l’échelle par rapport aux proportions des images de la caméra](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="bc97f-124">Rechercher des positions de la caméra dans l’espace universel</span><span class="sxs-lookup"><span data-stu-id="bc97f-124">Find Camera Positions in World Space</span></span>

<span data-ttu-id="bc97f-125">La caméra sur le casque HoloLens 2 est décalée verticalement par rapport au suivi de la tête de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="bc97f-125">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="bc97f-126">Pour tenir compte du décalage, il existe quelques fonctions qui permettent de localiser la caméra dans l’espace universel.</span><span class="sxs-lookup"><span data-stu-id="bc97f-126">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="bc97f-127">GetPVCameraToWorldTransform obtient la transformation dans l’espace universel de la caméra PV, et est positionné sur l’objectif de la caméra :</span><span class="sxs-lookup"><span data-stu-id="bc97f-127">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Blueprint de la fonction Obtenir la transformation de la caméra PV en monde](../images/unreal-pvc-img-08.png)

<span data-ttu-id="bc97f-129">GetWorldSpaceRayFromCameraPoint diffuse un rayon de l’objectif de la caméra vers la scène dans l’espace universel Unreal pour rechercher le contenu d’un pixel dans le cadre de la caméra :</span><span class="sxs-lookup"><span data-stu-id="bc97f-129">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![Blueprint de la fonction Obtenir un rayon de l’espace universel depuis un point de la caméra](../images/unreal-pvc-img-09.png)

<span data-ttu-id="bc97f-131">GetPVCameraIntrinsics retourne les valeurs intrinsèques de la caméra, qui peuvent être utilisées lors du traitement de la vision par ordinateur sur un cadre de la caméra :</span><span class="sxs-lookup"><span data-stu-id="bc97f-131">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Blueprint de fonctions intrinsèques de la caméra PV](../images/unreal-pvc-img-10.png)

<span data-ttu-id="bc97f-133">Pour trouver ce qui existe dans l’espace universel à une coordonnée d’un pixel particulier, utilisez un suivi de ligne avec le rayon d’espace universel :</span><span class="sxs-lookup"><span data-stu-id="bc97f-133">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![Blueprint du rayon d’espace universel utilisé pour déterminer ce qui existe dans l’espace universel à une coordonnée particulière](../images/unreal-pvc-img-11.png)

<span data-ttu-id="bc97f-135">Nous convertissons ici un rayon à 2 mètres de l’objectif de la caméra en une position dans l’espace de la caméra à ¼ à partir du coin supérieur gauche du cadre.</span><span class="sxs-lookup"><span data-stu-id="bc97f-135">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="bc97f-136">Nous utilisons ensuite le résultat du pointage pour rendre quelque chose là où l’objet existe dans l’espace universel :</span><span class="sxs-lookup"><span data-stu-id="bc97f-136">Then use the hit result to render something where the object exists in world space:</span></span>

![Blueprint de la conversion d’un rayon à 2 mètres de l’objectif de la caméra en une position dans l’espace de la caméra à 1/4 à partir du coin supérieur gauche du cadre.](../images/unreal-pvc-img-12.png)

<span data-ttu-id="bc97f-138">Quand vous utilisez le mappage spatial, cette position du pointage correspond à la surface vue par la caméra.</span><span class="sxs-lookup"><span data-stu-id="bc97f-138">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="bc97f-139">Rendu du flux de la caméra PV en C++</span><span class="sxs-lookup"><span data-stu-id="bc97f-139">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="bc97f-140">Créer un acteur C++ appelé CamCapture</span><span class="sxs-lookup"><span data-stu-id="bc97f-140">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="bc97f-141">Dans le fichier build.cs du projet, ajoutez « AugmentedReality » à la liste PublicDependencyModuleNames :</span><span class="sxs-lookup"><span data-stu-id="bc97f-141">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="bc97f-142">Dans CamCapture. h, incluez ARBlueprintLibrary.h</span><span class="sxs-lookup"><span data-stu-id="bc97f-142">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="bc97f-143">Vous devez aussi ajouter des variables locales pour le maillage et le matériau :</span><span class="sxs-lookup"><span data-stu-id="bc97f-143">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="bc97f-144">Dans CamCapture.cpp, mettez à jour le constructeur en ajoutant un maillage statique à la scène :</span><span class="sxs-lookup"><span data-stu-id="bc97f-144">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

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

<span data-ttu-id="bc97f-145">Dans BeginPlay, créez une instance de matériau dynamique à partir du matériau de la caméra du projet, appliquez-la au composant de maillage statique et démarrez la caméra HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bc97f-145">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="bc97f-146">Dans l’éditeur, cliquez avec le bouton droit sur CamTextureMaterial dans l’explorateur de contenu, puis sélectionnez Copy Reference pour obtenir la chaîne de CameraMatPath.</span><span class="sxs-lookup"><span data-stu-id="bc97f-146">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="bc97f-147">Dans Tick, récupérez la texture de la caméra, définissez-la sur le paramètre de texture dans le matériau CamTextureMaterial et mettez à l’échelle le composant de maillage statique selon les proportions du cadre de la caméra :</span><span class="sxs-lookup"><span data-stu-id="bc97f-147">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

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

# <a name="425"></a>[<span data-ttu-id="bc97f-148">4.25</span><span class="sxs-lookup"><span data-stu-id="bc97f-148">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="bc97f-149">Affichage à partir de l’appareil photo/vidéo pour la capture de Réalité Mixte</span><span class="sxs-lookup"><span data-stu-id="bc97f-149">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="bc97f-150">Cela nécessite **Unreal Engine 4.25** ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="bc97f-150">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="bc97f-151">Le système et les enregistreurs personnalisés créent des captures de réalité mixte en combinant la caméra PV à des hologrammes affichés par l’application.</span><span class="sxs-lookup"><span data-stu-id="bc97f-151">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="bc97f-152">Par défaut, la capture de Réalité Mixte utilise la sortie holographique de l’œil droit.</span><span class="sxs-lookup"><span data-stu-id="bc97f-152">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="bc97f-153">Si une application immersive choisit d’être [affichée à partir de la caméra PV](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), ce mode de rendu est utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="bc97f-153">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="bc97f-154">Le rendu à partir de la caméra PV améliore le mappage entre le monde réel et les hologrammes dans la vidéo de capture de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="bc97f-154">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="bc97f-155">Pour choisir le rendu à partir de la caméra PV :</span><span class="sxs-lookup"><span data-stu-id="bc97f-155">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="bc97f-156">Appelez **SetEnabledMixedRealityCamera** et **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="bc97f-156">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="bc97f-157">Utilisez les valeurs de taille **Size X** et **Size Y** pour définir les dimensions de la vidéo.</span><span class="sxs-lookup"><span data-stu-id="bc97f-157">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Troisième caméra](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="bc97f-159">Unreal va ensuite gérer les requêtes de capture de Réalité Mixte pour effectuer le rendu du point de vue de l’appareil photo/vidéo.</span><span class="sxs-lookup"><span data-stu-id="bc97f-159">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="bc97f-160">C’est seulement quand la [capture de Réalité Mixte](../../../mixed-reality-capture.md) est déclenchée qu’il est demandé à l’application de s’afficher du point de vue de l’appareil photo/vidéo.</span><span class="sxs-lookup"><span data-stu-id="bc97f-160">Only when [Mixed Reality Capture](../../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="bc97f-161">Utilisation de l’appareil photo/vidéo</span><span class="sxs-lookup"><span data-stu-id="bc97f-161">Using the PV Camera</span></span>

<span data-ttu-id="bc97f-162">La texture de la webcam peut être récupérée dans le jeu au moment de l’exécution. Toutefois, vous devez l’activer dans l’éditeur **Edit > Project Settings** (Modifier > Paramètres du projet) :</span><span class="sxs-lookup"><span data-stu-id="bc97f-162">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="bc97f-163">Accédez à **Platforms > HoloLens > Capabilities** (Plateformes > HoloLens > Fonctionnalités), puis cochez **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="bc97f-163">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="bc97f-164">Utilisez la fonction **StartCameraCapture** pour utiliser la webcam au moment de l’exécution, et la fonction **StopCameraCapture** pour arrêter l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="bc97f-164">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Démarrer/Arrêter la caméra](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="bc97f-166">Affichage d’une image</span><span class="sxs-lookup"><span data-stu-id="bc97f-166">Rendering an image</span></span>
<span data-ttu-id="bc97f-167">Pour afficher l’image de l’appareil photo :</span><span class="sxs-lookup"><span data-stu-id="bc97f-167">To render the camera image:</span></span>
1. <span data-ttu-id="bc97f-168">Créez une instance de matériau dynamique basée sur un matériau du projet, nommé **PVCamMat** dans la capture d’écran ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="bc97f-168">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="bc97f-169">Définissez l’instance de matériau dynamique sur une variable **Material Instance Dynamic Object Reference**.</span><span class="sxs-lookup"><span data-stu-id="bc97f-169">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="bc97f-170">Définissez le matériau de l’objet de la scène qui affichera le flux de l’appareil sur cette nouvelle instance de matériau dynamique.</span><span class="sxs-lookup"><span data-stu-id="bc97f-170">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="bc97f-171">Démarrez un minuteur qui sera utilisé pour lier l’image de l’appareil au matériau.</span><span class="sxs-lookup"><span data-stu-id="bc97f-171">Start a timer that will be used to bind the camera image to the material.</span></span>

![Rendu de la caméra](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="bc97f-173">Créez une fonction pour ce minuteur, dans ce cas **MaterialTimer**, puis appelez **GetARCameraImage** pour obtenir la texture à partir de la webcam.</span><span class="sxs-lookup"><span data-stu-id="bc97f-173">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="bc97f-174">Si la texture est correcte, définissez un paramètre de texture dans le nuanceur de cette image.</span><span class="sxs-lookup"><span data-stu-id="bc97f-174">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="bc97f-175">Sinon, redémarrez le minuteur de matériau.</span><span class="sxs-lookup"><span data-stu-id="bc97f-175">Otherwise, start the material timer again.</span></span>

![Texture de la caméra à partir de la webcam](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="bc97f-177">Vérifiez que le matériau a un paramètre correspondant au nom indiqué dans **SetTextureParameterValue**, qui est lié à une entrée de couleur.</span><span class="sxs-lookup"><span data-stu-id="bc97f-177">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="bc97f-178">Sans ce paramètre, l’image de la caméra ne peut pas s’afficher correctement.</span><span class="sxs-lookup"><span data-stu-id="bc97f-178">Without the parameter, the camera image can't be displayed properly.</span></span>

![Texture de la caméra](../images/unreal-camera-material.PNG)

