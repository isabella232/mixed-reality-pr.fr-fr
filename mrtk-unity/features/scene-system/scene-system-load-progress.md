---
title: Système de scène - Progression du chargement
description: Documentation sur le chargement de contenu des scènes dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144400"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="23330-104">Surveillance du chargement du contenu</span><span class="sxs-lookup"><span data-stu-id="23330-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="23330-105">Progression de l’opération de scène</span><span class="sxs-lookup"><span data-stu-id="23330-105">Scene operation progress</span></span>

<span data-ttu-id="23330-106">Lorsque le contenu est chargé ou déchargé, la `SceneOperationInProgress` propriété retourne la valeur true.</span><span class="sxs-lookup"><span data-stu-id="23330-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="23330-107">Vous pouvez surveiller la progression de cette opération via la `SceneOperationProgress` propriété.</span><span class="sxs-lookup"><span data-stu-id="23330-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="23330-108">La `SceneOperationProgress` valeur est la moyenne de toutes les opérations de scène asynchrones en cours.</span><span class="sxs-lookup"><span data-stu-id="23330-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="23330-109">Au début d’un chargement de contenu, `SceneOperationProgress` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="23330-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="23330-110">Une fois complètement terminé, `SceneOperationProgress` aura la valeur 1 et restera à 1 jusqu’à ce que l’opération suivante se produise.</span><span class="sxs-lookup"><span data-stu-id="23330-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="23330-111">Notez que seules les opérations de scène de contenu affectent ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="23330-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="23330-112">Ces propriétés reflètent l’état d’une *opération entière* du début à la fin, même si cette opération comprend plusieurs étapes :</span><span class="sxs-lookup"><span data-stu-id="23330-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a><span data-ttu-id="23330-113">Exemples de progression</span><span class="sxs-lookup"><span data-stu-id="23330-113">Progress examples</span></span>

<span data-ttu-id="23330-114">`SceneOperationInProgress` peut être utile si l’activité doit être interrompue pendant le chargement du contenu :</span><span class="sxs-lookup"><span data-stu-id="23330-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

<span data-ttu-id="23330-115">`SceneOperationProgress` peut être utilisé pour afficher des boîtes de dialogue de progression :</span><span class="sxs-lookup"><span data-stu-id="23330-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a><span data-ttu-id="23330-116">Surveillance avec des actions</span><span class="sxs-lookup"><span data-stu-id="23330-116">Monitoring with actions</span></span>

<span data-ttu-id="23330-117">Le système de scène fournit plusieurs actions qui vous permettent de savoir quand des scènes sont chargées ou déchargées.</span><span class="sxs-lookup"><span data-stu-id="23330-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="23330-118">Chaque action relaie le nom de la scène affectée.</span><span class="sxs-lookup"><span data-stu-id="23330-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="23330-119">Si une opération de chargement ou de déchargement implique plusieurs scènes, les actions pertinentes sont appelées une fois par scène affectée.</span><span class="sxs-lookup"><span data-stu-id="23330-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="23330-120">Ils sont également appelés en même temps lorsque l’opération de chargement ou de déchargement est *entièrement terminée.*</span><span class="sxs-lookup"><span data-stu-id="23330-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="23330-121">Pour cette raison, il est recommandé d’utiliser des actions *OnWillUnload* pour détecter le contenu qui *sera* détruit, par opposition à l’utilisation d’actions *OnUnloaded* pour détecter le contenu détruit une fois le fait effectué.</span><span class="sxs-lookup"><span data-stu-id="23330-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="23330-122">Du côté du basculement, étant donné que les actions *OnLoaded* sont appelées uniquement lorsque toutes les scènes sont activées et entièrement chargées, l’utilisation d’actions *OnLoaded* pour détecter et utiliser le nouveau contenu est garantie.</span><span class="sxs-lookup"><span data-stu-id="23330-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="23330-123">Action</span><span class="sxs-lookup"><span data-stu-id="23330-123">Action</span></span> | <span data-ttu-id="23330-124">Quand elle est appelée</span><span class="sxs-lookup"><span data-stu-id="23330-124">When it's invoked</span></span> | <span data-ttu-id="23330-125">Scènes du contenu</span><span class="sxs-lookup"><span data-stu-id="23330-125">Content Scenes</span></span> | <span data-ttu-id="23330-126">Scènes d’éclairage</span><span class="sxs-lookup"><span data-stu-id="23330-126">Lighting Scenes</span></span> | <span data-ttu-id="23330-127">Scènes du gestionnaire</span><span class="sxs-lookup"><span data-stu-id="23330-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="23330-128">Juste avant le chargement d’une scène de contenu</span><span class="sxs-lookup"><span data-stu-id="23330-128">Just prior to a content scene load</span></span> | <span data-ttu-id="23330-129">•</span><span class="sxs-lookup"><span data-stu-id="23330-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="23330-130">Une fois que toutes les scènes de contenu d’une opération de chargement ont été entièrement chargées et activées</span><span class="sxs-lookup"><span data-stu-id="23330-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="23330-131">•</span><span class="sxs-lookup"><span data-stu-id="23330-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="23330-132">Juste avant une opération de déchargement de scène de contenu</span><span class="sxs-lookup"><span data-stu-id="23330-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="23330-133">•</span><span class="sxs-lookup"><span data-stu-id="23330-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="23330-134">Une fois que toutes les scènes de contenu d’une opération de déchargement ont été entièrement déchargées</span><span class="sxs-lookup"><span data-stu-id="23330-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="23330-135">•</span><span class="sxs-lookup"><span data-stu-id="23330-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="23330-136">Juste avant une charge de scène d’éclairage</span><span class="sxs-lookup"><span data-stu-id="23330-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="23330-137">•</span><span class="sxs-lookup"><span data-stu-id="23330-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="23330-138">Après le chargement et l’activation d’une scène d’éclairage</span><span class="sxs-lookup"><span data-stu-id="23330-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="23330-139">•</span><span class="sxs-lookup"><span data-stu-id="23330-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="23330-140">Juste avant le déchargement d’une scène d’éclairage</span><span class="sxs-lookup"><span data-stu-id="23330-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="23330-141">•</span><span class="sxs-lookup"><span data-stu-id="23330-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="23330-142">Après le déchargement complet d’une scène d’éclairage</span><span class="sxs-lookup"><span data-stu-id="23330-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="23330-143">•</span><span class="sxs-lookup"><span data-stu-id="23330-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="23330-144">Juste avant le chargement d’une scène</span><span class="sxs-lookup"><span data-stu-id="23330-144">Just prior to a scene load</span></span> | <span data-ttu-id="23330-145">•</span><span class="sxs-lookup"><span data-stu-id="23330-145">•</span></span> | <span data-ttu-id="23330-146">•</span><span class="sxs-lookup"><span data-stu-id="23330-146">•</span></span> | <span data-ttu-id="23330-147">•</span><span class="sxs-lookup"><span data-stu-id="23330-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="23330-148">Après le chargement complet et l’activation de toutes les scènes dans une opération</span><span class="sxs-lookup"><span data-stu-id="23330-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="23330-149">•</span><span class="sxs-lookup"><span data-stu-id="23330-149">•</span></span> | <span data-ttu-id="23330-150">•</span><span class="sxs-lookup"><span data-stu-id="23330-150">•</span></span> | <span data-ttu-id="23330-151">•</span><span class="sxs-lookup"><span data-stu-id="23330-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="23330-152">Juste avant le déchargement d’une scène</span><span class="sxs-lookup"><span data-stu-id="23330-152">Just prior to a scene unload</span></span> | <span data-ttu-id="23330-153">•</span><span class="sxs-lookup"><span data-stu-id="23330-153">•</span></span> | <span data-ttu-id="23330-154">•</span><span class="sxs-lookup"><span data-stu-id="23330-154">•</span></span> | <span data-ttu-id="23330-155">•</span><span class="sxs-lookup"><span data-stu-id="23330-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="23330-156">Après le déchargement complet d’une scène</span><span class="sxs-lookup"><span data-stu-id="23330-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="23330-157">•</span><span class="sxs-lookup"><span data-stu-id="23330-157">•</span></span> | <span data-ttu-id="23330-158">•</span><span class="sxs-lookup"><span data-stu-id="23330-158">•</span></span> | <span data-ttu-id="23330-159">•</span><span class="sxs-lookup"><span data-stu-id="23330-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="23330-160">Exemples d’actions</span><span class="sxs-lookup"><span data-stu-id="23330-160">Action examples</span></span>

<span data-ttu-id="23330-161">Un autre exemple de boîte de dialogue de progression utilisant des actions et une Coroutine plutôt qu’une mise à jour :</span><span class="sxs-lookup"><span data-stu-id="23330-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a><span data-ttu-id="23330-162">Contrôle de l’activation des scènes</span><span class="sxs-lookup"><span data-stu-id="23330-162">Controlling scene activation</span></span>

<span data-ttu-id="23330-163">Par défaut, le contenu est activé lorsqu’il est chargé.</span><span class="sxs-lookup"><span data-stu-id="23330-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="23330-164">Si vous souhaitez contrôler manuellement l’activation des scènes, vous pouvez passer une `SceneActivationToken` à toute méthode de chargement de contenu.</span><span class="sxs-lookup"><span data-stu-id="23330-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="23330-165">Si plusieurs scènes de contenu sont chargées par une seule opération, ce jeton d’activation s’appliquera à toutes les scènes.</span><span class="sxs-lookup"><span data-stu-id="23330-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="23330-166">Vérification du contenu chargé</span><span class="sxs-lookup"><span data-stu-id="23330-166">Checking which content is loaded</span></span>

<span data-ttu-id="23330-167">La `ContentSceneNames` propriété fournit un tableau des scènes de contenu disponibles par ordre d’index de Build.</span><span class="sxs-lookup"><span data-stu-id="23330-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="23330-168">Vous pouvez vérifier si ces scènes sont chargées via `IsContentLoaded(string contentName)` .</span><span class="sxs-lookup"><span data-stu-id="23330-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
