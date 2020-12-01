---
title: Entrée en pointage en regard
description: Didacticiel sur la configuration de l’entrée de regard pour HoloLens et le moteur inréel
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, HoloLens 2, suivi des yeux, entrée de regard, affichage monté en tête, moteur non réel, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: f89638cef6b90e004f097c701c3df13edaf74fac
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354322"
---
# <a name="gaze-input"></a><span data-ttu-id="15e8c-104">Entrée en regard</span><span class="sxs-lookup"><span data-stu-id="15e8c-104">Gaze Input</span></span>

<span data-ttu-id="15e8c-105">Le point de regard est utilisé pour indiquer ce que l’utilisateur examine.</span><span class="sxs-lookup"><span data-stu-id="15e8c-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="15e8c-106">Cela utilise les caméras de suivi oculaire sur l’appareil pour trouver un rayon dans l’espace non réel correspondant à ce que l’utilisateur examine actuellement.</span><span class="sxs-lookup"><span data-stu-id="15e8c-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="15e8c-107">Activation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="15e8c-107">Enabling eye tracking</span></span>

- <span data-ttu-id="15e8c-108">Dans **paramètres du projet > HoloLens**, activez la fonctionnalité **d’entrée en regard** :</span><span class="sxs-lookup"><span data-stu-id="15e8c-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Capture d’écran des fonctionnalités des paramètres du projet HoloLens avec l’entrée en regard en surbrillance](images/unreal-gaze-img-01.png)

- <span data-ttu-id="15e8c-110">Créer un acteur et l’ajouter à votre scène</span><span class="sxs-lookup"><span data-stu-id="15e8c-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="15e8c-111">Le suivi oculaire HoloLens en non réel a un seul rayon de regard pour les yeux au lieu des deux rayons nécessaires pour le suivi STEREOSCOPIQUE, ce qui n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="15e8c-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="15e8c-112">Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="15e8c-112">Using eye tracking</span></span>

<span data-ttu-id="15e8c-113">Vérifiez tout d’abord que l’appareil prend en charge le suivi oculaire avec la fonction IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="15e8c-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="15e8c-114">Si la valeur est true, appelez GetGazeData pour Rechercher l’endroit où les yeux de l’utilisateur regardent au cours du frame actuel :</span><span class="sxs-lookup"><span data-stu-id="15e8c-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![Le plan de la fonction est connecté au suivi oculaire](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="15e8c-116">Le point de fixation et la valeur de confiance ne sont pas disponibles sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15e8c-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="15e8c-117">Pour trouver ce que l’utilisateur examine, utilisez l’origine du regard et la direction dans une trace de ligne.</span><span class="sxs-lookup"><span data-stu-id="15e8c-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="15e8c-118">Le début de ce vecteur est l’origine du point de regard et la fin est l’origine plus la direction du point de regard multipliée par la distance souhaitée :</span><span class="sxs-lookup"><span data-stu-id="15e8c-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Plan de la fonction d’extraction de données de regard](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="15e8c-120">Obtention de l’orientation des têtes</span><span class="sxs-lookup"><span data-stu-id="15e8c-120">Getting head orientation</span></span>

<span data-ttu-id="15e8c-121">Vous pouvez également utiliser la rotation HMD pour représenter la direction de l’en-tête de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15e8c-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="15e8c-122">Cela ne nécessite pas la fonctionnalité d’entrée en regard, mais ne vous donne aucune information de suivi visuel.</span><span class="sxs-lookup"><span data-stu-id="15e8c-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="15e8c-123">Une référence au plan doit être ajoutée comme contexte universel pour obtenir les données de sortie correctes :</span><span class="sxs-lookup"><span data-stu-id="15e8c-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="15e8c-124">L’obtention de données HMD n’est disponible que dans les versions 4,26 et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="15e8c-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Plan de la fonction d’extraction de HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="15e8c-126">Utilisation de C++</span><span class="sxs-lookup"><span data-stu-id="15e8c-126">Using C++</span></span> 

- <span data-ttu-id="15e8c-127">Dans le fichier build.cs de votre jeu, ajoutez « EyeTracker » à la liste PublicDependencyModuleNames :</span><span class="sxs-lookup"><span data-stu-id="15e8c-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="15e8c-128">Dans « fichier/nouvelle classe C++ », créez un acteur C++ appelé « EyeTracker »</span><span class="sxs-lookup"><span data-stu-id="15e8c-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="15e8c-129">Une solution Visual Studio s’ouvre à la nouvelle classe EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="15e8c-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="15e8c-130">Générez et exécutez pour ouvrir le jeu inréel avec le nouvel acteur EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="15e8c-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="15e8c-131">Recherchez « EyeTracker » dans la fenêtre « placer les acteurs ».</span><span class="sxs-lookup"><span data-stu-id="15e8c-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="15e8c-132">Faites glisser et déposez cette classe dans la fenêtre de jeu pour l’ajouter au projet :</span><span class="sxs-lookup"><span data-stu-id="15e8c-132">Drag and drop this class into the game window to add it to the project:</span></span>

![Capture d’écran d’un acteur avec la fenêtre placer l’acteur ouverte](images/unreal-gaze-img-06.png)

- <span data-ttu-id="15e8c-134">Dans EyeTracker. cpp, ajoutez includes pour EyeTrackerFunctionLibrary et DrawDebugHelpers :</span><span class="sxs-lookup"><span data-stu-id="15e8c-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="15e8c-135">Dans Tick, vérifiez que l’appareil prend en charge le suivi oculaire avec UEyeTrackerFunctionLibrary :: IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="15e8c-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="15e8c-136">Recherchez ensuite le début et la fin d’un rayon pour une trace de ligne à partir de UEyeTrackerFunctionLibrary :: GetGazeData :</span><span class="sxs-lookup"><span data-stu-id="15e8c-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="15e8c-137">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="15e8c-137">Next Development Checkpoint</span></span>

<span data-ttu-id="15e8c-138">Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les modules de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="15e8c-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="15e8c-139">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="15e8c-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="15e8c-140">Suivi de la main</span><span class="sxs-lookup"><span data-stu-id="15e8c-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="15e8c-141">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="15e8c-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="15e8c-142">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="15e8c-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="15e8c-143">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="15e8c-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="15e8c-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15e8c-144">See also</span></span>
* [<span data-ttu-id="15e8c-145">Étalonnage</span><span class="sxs-lookup"><span data-stu-id="15e8c-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="15e8c-146">Confort</span><span class="sxs-lookup"><span data-stu-id="15e8c-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="15e8c-147">Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="15e8c-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="15e8c-148">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="15e8c-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
