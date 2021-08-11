---
title: Système de scène - Chargement de contenu
description: Documentation chargement du système de scène avec MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: df4437a0640637328c3f8f0d78be63a492d4bba15acb8a37bdf2dd3c32d89a59
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223033"
---
# <a name="scene-system-content-loading"></a>Système de scène - Chargement de contenu

Toutes les opérations de chargement de contenu sont asynchrones et, par défaut, tout le chargement du contenu est additif. Les scènes de gestion et d’éclairage ne sont jamais affectées par les opérations de chargement de contenu. Pour plus d’informations sur la surveillance de la progression de la charge et l’activation des scènes, consultez [surveillance du chargement du contenu](scene-system-load-progress.md).

## <a name="loading-content"></a>Chargement du contenu

Pour charger des scènes de contenu, utilisez la `LoadContent` méthode :

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Chargement d’une scène unique

L’équivalent d’une charge de scène unique peut être obtenu à l’aide de l' `mode` argument facultatif. `LoadSceneMode.Single` va d’abord décharger toutes les scènes de contenu chargé avant de procéder à la charge.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a>Chargement de scène suivant/précédent

Le contenu peut être chargé de façon unique dans l’ordre de création de l’index. Cela est utile pour présenter les applications qui permettent aux utilisateurs d’effectuer un ensemble de scènes de démonstration un par un.

![Scènes actuelles dans la build dans les paramètres du lecteur](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Notez que le chargement du contenu suivant/précédent utilise LoadSceneMode. Single par défaut pour s’assurer que le contenu précédent est déchargé.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

`PrevContentExists` retourne la valeur true s’il y a au moins une scène de contenu qui a un index de build inférieur à l’index de build le plus bas actuellement chargé. `NextContentExists` retourne la valeur true s’il existe au moins une scène de contenu qui a un index de build plus élevé que l’index de build le plus élevé actuellement chargé.

Si l' `wrap` argument a la valeur true, le contenu repasse au premier et au dernier index de la Build. Cela supprime la nécessité de vérifier le contenu suivant/précédent :

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a>Charger par balise

![Chargement de scènes de contenu par balise](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

Il est parfois souhaitable de charger des scènes de contenu dans des groupes. Par exemple, une étape d’une expérience peut être composée de plusieurs scènes, qui doivent toutes être chargées simultanément pour fonctionner. Pour faciliter cette tâche, vous pouvez baliser vos scènes, puis les charger ou les décharger avec cette balise.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

Le chargement par balise peut également être utile si les artistes souhaitent incorporer/supprimer des éléments d’une expérience sans avoir à modifier les scripts. Par exemple, l’exécution de ce script avec les deux ensembles de balises suivants produit des résultats différents :

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Test du contenu

Nom de la scène | Étiquette de scène | Chargé par le script
---|---|---
DebugTerrainPhysics | Cartographi | •
StructureTesting | Structures | •
VegetationTools | Végétal | •
Mountain | Cartographi | •
Cabin | Structures | •
Arborescences | Végétal | •

### <a name="final-content"></a>Contenu final

Nom de la scène | Étiquette de scène | Chargé par le script
---|---|---
DebugTerrainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
VegetationTools | DoNotInclude |
Mountain | Cartographi | •
Cabin | Structures | •
Arborescences | Végétal | •

---

## <a name="editor-behavior"></a>Comportement de l’éditeur

Vous pouvez effectuer toutes ces opérations dans l’éditeur et en mode lecture à l’aide de l' [inspecteur de service](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) du système de scène. En mode édition, les chargements de scène sont instantanés, alors qu’en mode lecture, vous pouvez observer la progression du chargement et utiliser des [jetons d’activation.](scene-system-load-progress.md)

![Système de scène dans l’inspecteur avec chargement du contenu mis en surbrillance](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
