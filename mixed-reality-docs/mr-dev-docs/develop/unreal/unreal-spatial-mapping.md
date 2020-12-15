---
title: Mappage spatial dans Unreal
description: Guide d’utilisation du mappage spatial dans Unreal
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, mappage spatial, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 6d70e7f2d32fbf39bc51534661b8224547c36acc
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926044"
---
# <a name="spatial-mapping-in-unreal"></a>Mappage spatial dans Unreal

Le mappage spatial vous permet de placer des objets sur des surfaces physiques dans le monde réel. Quand le monde autour du HoloLens est mappé, les hologrammes semblent plus réels pour l’utilisateur. Le mappage spatial ancre également les objets dans le monde de l’utilisateur en tirant parti des indicateurs de profondeur, ce qui permet de les convaincre que ces hologrammes sont en fait dans leur espace. Les hologrammes qui flottent dans l’espace ou qui se déplacent avec l’utilisateur n’ont pas l’air aussi réels, si bien qu’il est conseillé d’ajouter des éléments pour plus de confort dès que cela est possible.

Vous trouverez plus d’informations sur la qualité du mappage spatial, le positionnement, l’occlusion, le rendu et plus encore, dans le document [Mappage spatial](../../design/spatial-mapping.md).

## <a name="enabling-spatial-mapping"></a>Activation du mappage spatial

Pour activer le mappage spatial sur HoloLens :
- Ouvrez **Edit > Project Settings** , puis faites défiler jusqu’à la section **Platforms**.    
    + Sélectionnez **HoloLens**, puis cochez **Spatial Perception**.

![Capture d’écran des fonctionnalités des paramètres du projet HoloLens avec la perception spatiale mise en surbrillance](images/unreal-spatial-mapping-img-01.png)

Pour choisir le mappage spatial et déboguer **MRMesh** dans un jeu HoloLens :
1. Ouvrez **ARSessionConfig**, puis développez la section **ARSettings > World Mapping**. 

2. Cochez **Generate Mesh Data from Tracked Geometry** (Générer les données de maillage à partir de la géométrie suivie), ce qui indique au plug-in HoloLens qu’il doit démarrer de manière asynchrone la récupération des données de mappage spatial et les afficher dans Unreal via **MRMesh**. 
3. Cochez **Render Mesh Data in Wireframe** (Afficher les données de maillage dans un contour filaire) pour afficher un contour filaire blanc autour de chaque triangle dans **MRMesh**. 

![Magasin d’ancres spatiales prêt](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Mappage spatial au moment de l’exécution
Vous pouvez modifier les paramètres suivants pour mettre à jour le comportement du runtime de mappage spatial :

- Ouvrez **Edit > Project Settings**, faites défiler jusqu’à la section **Platforms**, puis sélectionnez **HoloLens > Spatial Mapping** : 

![Paramètres projet des ancres spatiales](images/unreal-spatialmapping-projectsettings.PNG)

- Le paramètre **Max Triangles Per Cubic Meter** (Nombre maximal de triangles par mètre cube) modifie la densité des triangles dans le maillage de mappage spatial.  
- Le paramètre **Spatial Meshing Volume Size** (Volume du maillage spatial) définit la taille du cube autour du joueur utilisé pour le rendu et la mise à jour des données de mappage spatial.  
    + Si l’environnement d’exécution de l’application est supposé être grand, cette valeur devra être suffisamment grande pour s’adapter à l’espace réel. Si l’application doit uniquement placer des hologrammes sur des surfaces proches de l’utilisateur, cette valeur pourra être plus petite. Le volume de mappage spatial bougera en même temps que l’utilisateur se déplacera dans le monde. 

## <a name="working-with-mrmesh"></a>Utilisation de MRMesh

Vous devez d’abord démarrer le mappage spatial :

![Blueprint de la fonction ToggleARCapture avec le type de capture de mappage spatial mis en surbrillance](images/unreal-spatial-mapping-img-02.png)

Une fois le mappage spatial capturé pour l’espace, nous vous recommandons de le désactiver.  Le mappage spatial peut être effectué après un certain laps de temps ou quand les raycasts dans chaque direction renvoient des collisions sur le MRMesh.

Pour accéder à **MRMesh** au moment de l’exécution :
1. Ajoutez un composant **ARTrackableNotify** à l’acteur Blueprint. 

![Composant ARTrackableNotify pour les ancres spatiales](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Sélectionnez le composant **ARTrackableNotify**, puis développez la section **Events** (Événements) dans le panneau **Details**. 
    - Sélectionnez le bouton **+** pour les événements à superviser. 

![Événements d’ancres spatiales](images/unreal-spatialmapping-events.PNG)

Dans ce cas, l’événement **On Add Tracked Geometry** (Lors de l’ajout d’une géométrie suivie) est supervisé. Celui-ci recherche les maillages valides de l’environnement qui correspondent aux données de mappage spatial. Vous trouverez la liste complète des événements dans l’API du composant [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Vous pouvez changer le matériau du maillage dans le graphe d’événements Blueprint ou dans le code C++. La capture d’écran ci-dessous montre la route du blueprint : 

![Exemple d’ancres spatiales](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>Mappage spatial en C++

Dans le fichier build.cs de votre jeu, ajoutez **AugmentedReality** et **MRMesh** à la liste PublicDependencyModuleNames :

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

Pour accéder au MRMesh, abonnez-vous aux délégués **OnTrackableAdded** :

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
> Il existe des délégués similaires pour les événements mis à jour et supprimés, respectivement **AddOnTrackableUpdatedDelegate_Handle** et **AddOnTrackableRemovedDelegate_Handle**.
>
> Vous trouverez la liste complète des événements dans l’API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Voir aussi
* [Mappage spatial](../../design/spatial-mapping.md)
