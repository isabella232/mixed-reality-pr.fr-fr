---
title: Mappage spatial dans Unreal
description: Guide d’utilisation du mappage spatial dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, mappage spatial, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354373"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="f5d22-104">Mappage spatial dans Unreal</span><span class="sxs-lookup"><span data-stu-id="f5d22-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="f5d22-105">Le mappage spatial permet de placer des objets sur des surfaces du monde physique en montrant l’environnement autour d’HoloLens, ce qui fait paraître les hologrammes encore plus réels à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5d22-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="f5d22-106">Le mappage spatial ancre également les objets dans le monde de l’utilisateur en tirant parti des indications de profondeur du monde réel. De cette façon, l’utilisateur a réellement l’impression que ces hologrammes se trouvent autour de lui. Les hologrammes qui flottent dans les airs ou qui se déplacent en même temps que l’utilisateur ne sembleront pas aussi réels.</span><span class="sxs-lookup"><span data-stu-id="f5d22-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="f5d22-107">Il est conseillé d’ajouter des éléments à des fins de confort dès que cela vous est possible.</span><span class="sxs-lookup"><span data-stu-id="f5d22-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="f5d22-108">Vous trouverez plus d’informations sur la qualité du mappage spatial, le positionnement, l’occlusion, le rendu et plus encore, dans le document [Mappage spatial](../../design/spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="f5d22-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="f5d22-109">Activation du mappage spatial</span><span class="sxs-lookup"><span data-stu-id="f5d22-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="f5d22-110">Pour activer le mappage spatial sur HoloLens :</span><span class="sxs-lookup"><span data-stu-id="f5d22-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="f5d22-111">Ouvrez **Edit > Project Settings** , puis faites défiler jusqu’à la section **Platforms**.</span><span class="sxs-lookup"><span data-stu-id="f5d22-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="f5d22-112">Sélectionnez **HoloLens**, puis cochez **Spatial Perception**.</span><span class="sxs-lookup"><span data-stu-id="f5d22-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![Capture d’écran des fonctionnalités des paramètres du projet HoloLens avec la perception spatiale mise en surbrillance](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="f5d22-114">Pour choisir le mappage spatial et déboguer **MRMesh** dans un jeu HoloLens :</span><span class="sxs-lookup"><span data-stu-id="f5d22-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="f5d22-115">Ouvrez **ARSessionConfig**, puis développez la section **ARSettings > World Mapping**.</span><span class="sxs-lookup"><span data-stu-id="f5d22-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="f5d22-116">Cochez **Generate Mesh Data from Tracked Geometry** (Générer les données de maillage à partir de la géométrie suivie), ce qui indique au plug-in HoloLens qu’il doit démarrer de manière asynchrone la récupération des données de mappage spatial et les afficher dans Unreal via **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="f5d22-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="f5d22-117">Cochez **Render Mesh Data in Wireframe** (Afficher les données de maillage dans un contour filaire) pour afficher un contour filaire blanc autour de chaque triangle dans **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="f5d22-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Magasin d’ancres spatiales prêt](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="f5d22-119">Mappage spatial au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="f5d22-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="f5d22-120">Vous pouvez modifier les paramètres suivants pour mettre à jour le comportement du runtime de mappage spatial :</span><span class="sxs-lookup"><span data-stu-id="f5d22-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="f5d22-121">Ouvrez **Edit > Project Settings**, faites défiler jusqu’à la section **Platforms**, puis sélectionnez **HoloLens > Spatial Mapping** :</span><span class="sxs-lookup"><span data-stu-id="f5d22-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Paramètres projet des ancres spatiales](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="f5d22-123">Le paramètre **Max Triangles Per Cubic Meter** (Nombre maximal de triangles par mètre cube) modifie la densité des triangles dans le maillage de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="f5d22-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="f5d22-124">Le paramètre **Spatial Meshing Volume Size** (Volume du maillage spatial) définit la taille du cube autour du joueur utilisé pour le rendu et la mise à jour des données de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="f5d22-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="f5d22-125">Si l’environnement d’exécution de l’application est supposé être grand, cette valeur devra être suffisamment grande pour s’adapter à l’espace réel.</span><span class="sxs-lookup"><span data-stu-id="f5d22-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="f5d22-126">À l’inverse, si l’application doit uniquement placer des hologrammes sur des surfaces proches de l’utilisateur, cette valeur pourra être plus petite.</span><span class="sxs-lookup"><span data-stu-id="f5d22-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="f5d22-127">Le volume de mappage spatial bougera en même temps que l’utilisateur se déplacera dans le monde.</span><span class="sxs-lookup"><span data-stu-id="f5d22-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="f5d22-128">Utilisation de MRMesh</span><span class="sxs-lookup"><span data-stu-id="f5d22-128">Working with MRMesh</span></span>

<span data-ttu-id="f5d22-129">Vous devez d’abord démarrer le mappage spatial :</span><span class="sxs-lookup"><span data-stu-id="f5d22-129">First, you need to start Spatial Mapping:</span></span>

![Blueprint de la fonction ToggleARCapture avec le type de capture de mappage spatial mis en surbrillance](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="f5d22-131">Une fois le mappage spatial capturé pour l’espace, nous vous recommandons de désactiver le mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="f5d22-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="f5d22-132">Le mappage spatial peut être effectué après un certain laps de temps ou quand les raycasts dans chaque direction renvoient des collisions sur le MRMesh.</span><span class="sxs-lookup"><span data-stu-id="f5d22-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="f5d22-133">Pour accéder à **MRMesh** au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="f5d22-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="f5d22-134">Ajoutez un composant **ARTrackableNotify** à l’acteur Blueprint.</span><span class="sxs-lookup"><span data-stu-id="f5d22-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Composant ARTrackableNotify pour les ancres spatiales](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="f5d22-136">Sélectionnez le composant **ARTrackableNotify**, puis développez la section **Events** (Événements) dans le panneau **Details**.</span><span class="sxs-lookup"><span data-stu-id="f5d22-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="f5d22-137">Cliquez sur le bouton **+** pour les événements que vous souhaitez superviser.</span><span class="sxs-lookup"><span data-stu-id="f5d22-137">Click the **+** button on the events you want to monitor.</span></span> 

![Événements d’ancres spatiales](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="f5d22-139">Dans ce cas, l’événement **On Add Tracked Geometry** (Lors de l’ajout d’une géométrie suivie) est supervisé. Celui-ci recherche les maillages valides de l’environnement qui correspondent aux données de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="f5d22-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="f5d22-140">Vous trouverez la liste complète des événements dans l’API du composant [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="f5d22-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="f5d22-141">Vous pouvez changer le matériau du maillage dans le graphe d’événements Blueprint ou dans le code C++.</span><span class="sxs-lookup"><span data-stu-id="f5d22-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="f5d22-142">La capture d’écran ci-dessous montre la route du blueprint :</span><span class="sxs-lookup"><span data-stu-id="f5d22-142">The screenshot below shows the Blueprint route:</span></span> 

![Exemple d’ancres spatiales](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="f5d22-144">Mappage spatial en C++</span><span class="sxs-lookup"><span data-stu-id="f5d22-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="f5d22-145">Dans le fichier build.cs de votre jeu, ajoutez **AugmentedReality** et **MRMesh** à la liste PublicDependencyModuleNames :</span><span class="sxs-lookup"><span data-stu-id="f5d22-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

<span data-ttu-id="f5d22-146">Pour accéder au MRMesh, abonnez-vous aux délégués **OnTrackableAdded** :</span><span class="sxs-lookup"><span data-stu-id="f5d22-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> <span data-ttu-id="f5d22-147">Il existe des délégués similaires pour les événements mis à jour et supprimés, respectivement **AddOnTrackableUpdatedDelegate_Handle** et **AddOnTrackableRemovedDelegate_Handle**.</span><span class="sxs-lookup"><span data-stu-id="f5d22-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="f5d22-148">Vous trouverez la liste complète des événements dans l’API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="f5d22-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5d22-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5d22-149">See also</span></span>
* [<span data-ttu-id="f5d22-150">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="f5d22-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
