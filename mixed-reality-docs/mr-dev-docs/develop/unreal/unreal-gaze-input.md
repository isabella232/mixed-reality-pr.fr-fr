---
title: Entrée en pointage en regard
description: Découvrez comment configurer et utiliser l’entrée en regard avec le suivi des yeux et l’orientation des têtes pour les applications HoloLens dans un environnement inréel.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, HoloLens 2, suivi des yeux, entrée de regard, affichage monté en tête, moteur non réel, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 0c5191534313b94a5382d1065f5a5dd1a208bb49
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98579985"
---
# <a name="gaze-input"></a>Entrée en regard

Les entrées de regard dans les applications de réalité mixte concernent la recherche de ce que vos utilisateurs cherchent. Lorsque les caméras de suivi oculaire sur votre appareil correspondent à des rayons dans l’espace universel, les données de la ligne de vue de votre utilisateur deviennent disponibles. Le point de regard peut être utilisé à la fois dans les plans et C++, et est une fonctionnalité de base pour l’interaction des objets, les recherches et les contrôles d’appareil photo.

## <a name="enabling-eye-tracking"></a>Activation du suivi oculaire

- Dans **paramètres du projet > HoloLens**, activez la fonctionnalité **d’entrée en regard** :

![Capture d’écran des fonctionnalités des paramètres du projet HoloLens avec l’entrée en regard en surbrillance](images/unreal-gaze-img-01.png)

- Créer un acteur et l’ajouter à votre scène

> [!NOTE]
> Le suivi oculaire HoloLens en non réel a un seul rayon de regard pour les deux yeux. Le suivi STEREOSCOPIQUE, qui nécessite deux rayons, n’est pas pris en charge.

## <a name="using-eye-tracking"></a>Utilisation du suivi oculaire

Tout d’abord, vérifiez que votre appareil prend en charge le suivi oculaire avec la fonction **IsEyeTrackerConnected** .  Si la fonction retourne la valeur true, appelez **GetGazeData** pour Rechercher l’endroit où les yeux de l’utilisateur regardent dans le frame actuel :

![Le plan de la fonction est connecté au suivi oculaire](images/unreal-gaze-img-02.png)

> [!NOTE]
> Le point de fixation et la valeur de confiance ne sont pas disponibles sur HoloLens.

Utilisez l’origine du regard et la direction dans un suivi de ligne pour déterminer exactement où vos utilisateurs cherchent.  La valeur de point d’interligne est un vecteur, commençant à l’origine du point de regard et se terminant à l’origine plus la direction du point d’arrêt multipliée par la distance de trace de la ligne :

![Plan de la fonction d’extraction de données de regard](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Obtention de l’orientation des têtes

Vous pouvez également utiliser la rotation de l’affichage monté en tête (HMD) pour représenter la direction de l’en-tête de l’utilisateur. Vous pouvez accéder à la direction de la tête des utilisateurs sans activer la fonction d’entrée en regard, mais vous ne pourrez pas accéder aux informations de suivi oculaire.  Ajoutez une référence au plan comme contexte universel pour obtenir les données de sortie correctes :

> [!NOTE]
> L’obtention de données HMD n’est disponible que dans les versions 4,26 et ultérieures.

![Plan de la fonction d’extraction de HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Utilisation de C++

- Dans le fichier **Build.cs** de votre jeu, ajoutez **EyeTracker** à la liste **PublicDependencyModuleNames** :

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- Dans **fichier/nouvelle classe c++**, créez un acteur C++ appelé **EyeTracker**
    - Une solution Visual Studio ouvre la nouvelle classe EyeTracker. Générez et exécutez pour ouvrir le jeu inréel avec le nouvel acteur EyeTracker.  Recherchez « EyeTracker » dans la fenêtre **Placer les acteurs** , puis faites glisser et déposez la classe dans la fenêtre de jeu pour l’ajouter au projet :

![Capture d’écran d’un acteur avec la fenêtre placer l’acteur ouverte](images/unreal-gaze-img-06.png)

- Dans **EyeTracker. cpp**, ajoutez includes pour **EyeTrackerFunctionLibrary** et **DrawDebugHelpers**:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Vérifiez que votre appareil prend en charge le suivi oculaire avec **UEyeTrackerFunctionLibrary :: IsEyeTrackerConnected** avant d’essayer d’accéder aux données de regard.  Si le suivi oculaire est pris en charge, recherchez le début et la fin d’un rayon pour une trace ligne à partir de **UEyeTrackerFunctionLibrary :: GetGazeData**. À partir de là, vous pouvez construire un vecteur de pointage et transmettre son contenu à **LineTraceSingleByChannel** pour déboguer les résultats d’accès aux rayons :

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK. À partir de là, vous pouvez passer au module suivant :

> [!div class="nextstepaction"]
> [Suivi de la main](unreal-hand-tracking.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Caméra HoloLens](unreal-hololens-camera.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Étalonnage](/hololens/hololens-calibration)
* [Confort](../../design/comfort.md)
* [Pointer et valider](../../design/gaze-and-commit.md)
* [Entrée vocale](../../out-of-scope/voice-design.md)