---
title: Chargement du contenu du système de scène
description: Documentation chargement du système de scène avec MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177578"
---
# <a name="scene-system-content-loading"></a><span data-ttu-id="ccb10-104">Chargement du contenu du système de scène</span><span class="sxs-lookup"><span data-stu-id="ccb10-104">Scene system content loading</span></span>

<span data-ttu-id="ccb10-105">Toutes les opérations de chargement de contenu sont asynchrones et, par défaut, tout le chargement du contenu est additif.</span><span class="sxs-lookup"><span data-stu-id="ccb10-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="ccb10-106">Les scènes de gestion et d’éclairage ne sont jamais affectées par les opérations de chargement de contenu.</span><span class="sxs-lookup"><span data-stu-id="ccb10-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="ccb10-107">Pour plus d’informations sur la surveillance de la progression de la charge et l’activation des scènes, consultez [surveillance du chargement du contenu](scene-system-load-progress.md).</span><span class="sxs-lookup"><span data-stu-id="ccb10-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="ccb10-108">Chargement du contenu</span><span class="sxs-lookup"><span data-stu-id="ccb10-108">Loading content</span></span>

<span data-ttu-id="ccb10-109">Pour charger des scènes de contenu, utilisez la `LoadContent` méthode :</span><span class="sxs-lookup"><span data-stu-id="ccb10-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="ccb10-110">Chargement d’une scène unique</span><span class="sxs-lookup"><span data-stu-id="ccb10-110">Single scene loading</span></span>

<span data-ttu-id="ccb10-111">L’équivalent d’une charge de scène unique peut être obtenu à l’aide de l' `mode` argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="ccb10-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="ccb10-112">`LoadSceneMode.Single` va d’abord décharger toutes les scènes de contenu chargé avant de procéder à la charge.</span><span class="sxs-lookup"><span data-stu-id="ccb10-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="ccb10-113">Chargement de scène suivant/précédent</span><span class="sxs-lookup"><span data-stu-id="ccb10-113">Next / previous scene loading</span></span>

<span data-ttu-id="ccb10-114">Le contenu peut être chargé de façon unique dans l’ordre de création de l’index.</span><span class="sxs-lookup"><span data-stu-id="ccb10-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="ccb10-115">Cela est utile pour présenter les applications qui permettent aux utilisateurs d’effectuer un ensemble de scènes de démonstration un par un.</span><span class="sxs-lookup"><span data-stu-id="ccb10-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Scènes actuelles dans la build dans les paramètres du lecteur](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="ccb10-117">Notez que le chargement du contenu suivant/précédent utilise LoadSceneMode. Single par défaut pour s’assurer que le contenu précédent est déchargé.</span><span class="sxs-lookup"><span data-stu-id="ccb10-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="ccb10-118">`PrevContentExists` retourne la valeur true s’il y a au moins une scène de contenu qui a un index de build inférieur à l’index de build le plus bas actuellement chargé.</span><span class="sxs-lookup"><span data-stu-id="ccb10-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="ccb10-119">`NextContentExists` retourne la valeur true s’il existe au moins une scène de contenu qui a un index de build plus élevé que l’index de build le plus élevé actuellement chargé.</span><span class="sxs-lookup"><span data-stu-id="ccb10-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="ccb10-120">Si l' `wrap` argument a la valeur true, le contenu repasse au premier et au dernier index de la Build.</span><span class="sxs-lookup"><span data-stu-id="ccb10-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="ccb10-121">Cela supprime la nécessité de vérifier le contenu suivant/précédent :</span><span class="sxs-lookup"><span data-stu-id="ccb10-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="ccb10-122">Charger par balise</span><span class="sxs-lookup"><span data-stu-id="ccb10-122">Loading by tag</span></span>

![Chargement de scènes de contenu par balise](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="ccb10-124">Il est parfois souhaitable de charger des scènes de contenu dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="ccb10-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="ccb10-125">Par exemple, une étape d’une expérience peut être composée de plusieurs scènes, qui doivent toutes être chargées simultanément pour fonctionner.</span><span class="sxs-lookup"><span data-stu-id="ccb10-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="ccb10-126">Pour faciliter cette tâche, vous pouvez baliser vos scènes, puis les charger ou les décharger avec cette balise.</span><span class="sxs-lookup"><span data-stu-id="ccb10-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="ccb10-127">Le chargement par balise peut également être utile si les artistes souhaitent incorporer/supprimer des éléments d’une expérience sans avoir à modifier les scripts.</span><span class="sxs-lookup"><span data-stu-id="ccb10-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="ccb10-128">Par exemple, l’exécution de ce script avec les deux ensembles de balises suivants produit des résultats différents :</span><span class="sxs-lookup"><span data-stu-id="ccb10-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="ccb10-129">Test du contenu</span><span class="sxs-lookup"><span data-stu-id="ccb10-129">Testing content</span></span>

<span data-ttu-id="ccb10-130">Nom de la scène</span><span class="sxs-lookup"><span data-stu-id="ccb10-130">Scene Name</span></span> | <span data-ttu-id="ccb10-131">Étiquette de scène</span><span class="sxs-lookup"><span data-stu-id="ccb10-131">Scene Tag</span></span> | <span data-ttu-id="ccb10-132">Chargé par le script</span><span class="sxs-lookup"><span data-stu-id="ccb10-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="ccb10-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="ccb10-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="ccb10-134">Cartographi</span><span class="sxs-lookup"><span data-stu-id="ccb10-134">Terrain</span></span> | <span data-ttu-id="ccb10-135">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-135">•</span></span>
<span data-ttu-id="ccb10-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="ccb10-136">StructureTesting</span></span> | <span data-ttu-id="ccb10-137">Structures</span><span class="sxs-lookup"><span data-stu-id="ccb10-137">Structures</span></span> | <span data-ttu-id="ccb10-138">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-138">•</span></span>
<span data-ttu-id="ccb10-139">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="ccb10-139">VegetationTools</span></span> | <span data-ttu-id="ccb10-140">Végétal</span><span class="sxs-lookup"><span data-stu-id="ccb10-140">Vegetation</span></span> | <span data-ttu-id="ccb10-141">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-141">•</span></span>
<span data-ttu-id="ccb10-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="ccb10-142">Mountain</span></span> | <span data-ttu-id="ccb10-143">Cartographi</span><span class="sxs-lookup"><span data-stu-id="ccb10-143">Terrain</span></span> | <span data-ttu-id="ccb10-144">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-144">•</span></span>
<span data-ttu-id="ccb10-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="ccb10-145">Cabin</span></span> | <span data-ttu-id="ccb10-146">Structures</span><span class="sxs-lookup"><span data-stu-id="ccb10-146">Structures</span></span> | <span data-ttu-id="ccb10-147">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-147">•</span></span>
<span data-ttu-id="ccb10-148">Arborescences</span><span class="sxs-lookup"><span data-stu-id="ccb10-148">Trees</span></span> | <span data-ttu-id="ccb10-149">Végétal</span><span class="sxs-lookup"><span data-stu-id="ccb10-149">Vegetation</span></span> | <span data-ttu-id="ccb10-150">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="ccb10-151">Contenu final</span><span class="sxs-lookup"><span data-stu-id="ccb10-151">Final content</span></span>

<span data-ttu-id="ccb10-152">Nom de la scène</span><span class="sxs-lookup"><span data-stu-id="ccb10-152">Scene Name</span></span> | <span data-ttu-id="ccb10-153">Étiquette de scène</span><span class="sxs-lookup"><span data-stu-id="ccb10-153">Scene Tag</span></span> | <span data-ttu-id="ccb10-154">Chargé par le script</span><span class="sxs-lookup"><span data-stu-id="ccb10-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="ccb10-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="ccb10-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="ccb10-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="ccb10-156">DoNotInclude</span></span> |
<span data-ttu-id="ccb10-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="ccb10-157">StructureTesting</span></span> | <span data-ttu-id="ccb10-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="ccb10-158">DoNotInclude</span></span> |
<span data-ttu-id="ccb10-159">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="ccb10-159">VegetationTools</span></span> | <span data-ttu-id="ccb10-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="ccb10-160">DoNotInclude</span></span> |
<span data-ttu-id="ccb10-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="ccb10-161">Mountain</span></span> | <span data-ttu-id="ccb10-162">Cartographi</span><span class="sxs-lookup"><span data-stu-id="ccb10-162">Terrain</span></span> | <span data-ttu-id="ccb10-163">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-163">•</span></span>
<span data-ttu-id="ccb10-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="ccb10-164">Cabin</span></span> | <span data-ttu-id="ccb10-165">Structures</span><span class="sxs-lookup"><span data-stu-id="ccb10-165">Structures</span></span> | <span data-ttu-id="ccb10-166">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-166">•</span></span>
<span data-ttu-id="ccb10-167">Arborescences</span><span class="sxs-lookup"><span data-stu-id="ccb10-167">Trees</span></span> | <span data-ttu-id="ccb10-168">Végétal</span><span class="sxs-lookup"><span data-stu-id="ccb10-168">Vegetation</span></span> | <span data-ttu-id="ccb10-169">•</span><span class="sxs-lookup"><span data-stu-id="ccb10-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="ccb10-170">Comportement de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="ccb10-170">Editor behavior</span></span>

<span data-ttu-id="ccb10-171">Vous pouvez effectuer toutes ces opérations dans l’éditeur et en mode lecture à l’aide de l' [inspecteur de service](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) du système de scène.</span><span class="sxs-lookup"><span data-stu-id="ccb10-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="ccb10-172">En mode édition, les chargements de scène sont instantanés, alors qu’en mode lecture, vous pouvez observer la progression du chargement et utiliser des [jetons d’activation.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="ccb10-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Système de scène dans l’inspecteur avec chargement du contenu mis en surbrillance](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
