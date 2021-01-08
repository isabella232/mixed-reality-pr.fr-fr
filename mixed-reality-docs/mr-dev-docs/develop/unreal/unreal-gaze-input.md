---
title: Entrée en pointage en regard
description: Découvrez comment configurer et utiliser l’entrée en regard avec le suivi des yeux et l’orientation des têtes pour les applications HoloLens dans un environnement inréel.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, HoloLens 2, suivi des yeux, entrée de regard, affichage monté en tête, moteur non réel, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: e546867fe02acd5e72ee76b4108a369ec25fd32f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010139"
---
# <a name="gaze-input"></a><span data-ttu-id="fcf6c-104">Entrée en regard</span><span class="sxs-lookup"><span data-stu-id="fcf6c-104">Gaze Input</span></span>

<span data-ttu-id="fcf6c-105">Les entrées de regard dans les applications de réalité mixte concernent la recherche de ce que vos utilisateurs cherchent.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="fcf6c-106">Lorsque les caméras de suivi oculaire sur votre appareil correspondent à des rayons dans l’espace universel, les données de la ligne de vue de votre utilisateur deviennent disponibles.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="fcf6c-107">Le point de regard peut être utilisé à la fois dans les plans et C++, et est une fonctionnalité de base pour l’interaction des objets, les recherches et les contrôles d’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="fcf6c-108">Activation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="fcf6c-108">Enabling eye tracking</span></span>

- <span data-ttu-id="fcf6c-109">Dans **paramètres du projet > HoloLens**, activez la fonctionnalité **d’entrée en regard** :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Capture d’écran des fonctionnalités des paramètres du projet HoloLens avec l’entrée en regard en surbrillance](images/unreal-gaze-img-01.png)

- <span data-ttu-id="fcf6c-111">Créer un acteur et l’ajouter à votre scène</span><span class="sxs-lookup"><span data-stu-id="fcf6c-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="fcf6c-112">Le suivi oculaire HoloLens en non réel a un seul rayon de regard pour les deux yeux.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="fcf6c-113">Le suivi STEREOSCOPIQUE, qui nécessite deux rayons, n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="fcf6c-114">Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="fcf6c-114">Using eye tracking</span></span>

<span data-ttu-id="fcf6c-115">Tout d’abord, vérifiez que votre appareil prend en charge le suivi oculaire avec la fonction **IsEyeTrackerConnected** .</span><span class="sxs-lookup"><span data-stu-id="fcf6c-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="fcf6c-116">Si la fonction retourne la valeur true, appelez **GetGazeData** pour Rechercher l’endroit où les yeux de l’utilisateur regardent dans le frame actuel :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![Le plan de la fonction est connecté au suivi oculaire](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="fcf6c-118">Le point de fixation et la valeur de confiance ne sont pas disponibles sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="fcf6c-119">Utilisez l’origine du regard et la direction dans un suivi de ligne pour déterminer exactement où vos utilisateurs cherchent.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="fcf6c-120">La valeur de point d’interligne est un vecteur, commençant à l’origine du point de regard et se terminant à l’origine plus la direction du point d’arrêt multipliée par la distance de trace de la ligne :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Plan de la fonction d’extraction de données de regard](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="fcf6c-122">Obtention de l’orientation des têtes</span><span class="sxs-lookup"><span data-stu-id="fcf6c-122">Getting head orientation</span></span>

<span data-ttu-id="fcf6c-123">Vous pouvez également utiliser la rotation de l’affichage monté en tête (HMD) pour représenter la direction de l’en-tête de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="fcf6c-124">Vous pouvez accéder à la direction de la tête des utilisateurs sans activer la fonction d’entrée en regard, mais vous ne pourrez pas accéder aux informations de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="fcf6c-125">Ajoutez une référence au plan comme contexte universel pour obtenir les données de sortie correctes :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="fcf6c-126">L’obtention de données HMD n’est disponible que dans les versions 4,26 et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Plan de la fonction d’extraction de HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="fcf6c-128">Utilisation de C++</span><span class="sxs-lookup"><span data-stu-id="fcf6c-128">Using C++</span></span>

- <span data-ttu-id="fcf6c-129">Dans le fichier **Build.cs** de votre jeu, ajoutez **EyeTracker** à la liste **PublicDependencyModuleNames** :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

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

- <span data-ttu-id="fcf6c-130">Dans **fichier/nouvelle classe c++**, créez un acteur C++ appelé **EyeTracker**</span><span class="sxs-lookup"><span data-stu-id="fcf6c-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="fcf6c-131">Une solution Visual Studio ouvre la nouvelle classe EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="fcf6c-132">Générez et exécutez pour ouvrir le jeu inréel avec le nouvel acteur EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="fcf6c-133">Recherchez « EyeTracker » dans la fenêtre **Placer les acteurs** , puis faites glisser et déposez la classe dans la fenêtre de jeu pour l’ajouter au projet :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![Capture d’écran d’un acteur avec la fenêtre placer l’acteur ouverte](images/unreal-gaze-img-06.png)

- <span data-ttu-id="fcf6c-135">Dans **EyeTracker. cpp**, ajoutez includes pour **EyeTrackerFunctionLibrary** et **DrawDebugHelpers**:</span><span class="sxs-lookup"><span data-stu-id="fcf6c-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="fcf6c-136">Vérifiez que votre appareil prend en charge le suivi oculaire avec **UEyeTrackerFunctionLibrary :: IsEyeTrackerConnected** avant d’essayer d’accéder aux données de regard.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="fcf6c-137">Si le suivi oculaire est pris en charge, recherchez le début et la fin d’un rayon pour une trace ligne à partir de **UEyeTrackerFunctionLibrary :: GetGazeData**.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="fcf6c-138">À partir de là, vous pouvez construire un vecteur de pointage et transmettre son contenu à **LineTraceSingleByChannel** pour déboguer les résultats d’accès aux rayons :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="fcf6c-139">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="fcf6c-139">Next Development Checkpoint</span></span>

<span data-ttu-id="fcf6c-140">Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="fcf6c-141">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fcf6c-142">Suivi de la main</span><span class="sxs-lookup"><span data-stu-id="fcf6c-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="fcf6c-143">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="fcf6c-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fcf6c-144">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="fcf6c-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="fcf6c-145">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="fcf6c-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcf6c-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcf6c-146">See also</span></span>
* [<span data-ttu-id="fcf6c-147">Étalonnage</span><span class="sxs-lookup"><span data-stu-id="fcf6c-147">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="fcf6c-148">Confort</span><span class="sxs-lookup"><span data-stu-id="fcf6c-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="fcf6c-149">Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="fcf6c-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="fcf6c-150">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="fcf6c-150">Voice input</span></span>](../../out-of-scope/voice-design.md)
