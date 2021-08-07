---
title: Système de scène - Progression du chargement
description: Documentation sur le chargement de contenu des scènes dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 1d2382e11092b20aca5bf8480ade521ffb94a70a325540e70487d7f581e8cf15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186615"
---
# <a name="monitoring-content-loading"></a>Surveillance du chargement du contenu

## <a name="scene-operation-progress"></a>Progression de l’opération de scène

Lorsque le contenu est chargé ou déchargé, la `SceneOperationInProgress` propriété retourne la valeur true. Vous pouvez surveiller la progression de cette opération via la `SceneOperationProgress` propriété.

La `SceneOperationProgress` valeur est la moyenne de toutes les opérations de scène asynchrones en cours. Au début d’un chargement de contenu, `SceneOperationProgress` est égal à zéro. Une fois complètement terminé, `SceneOperationProgress` aura la valeur 1 et restera à 1 jusqu’à ce que l’opération suivante se produise. Notez que seules les opérations de scène de contenu affectent ces propriétés.

Ces propriétés reflètent l’état d’une *opération entière* du début à la fin, même si cette opération comprend plusieurs étapes :

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

### <a name="progress-examples"></a>Exemples de progression

`SceneOperationInProgress` peut être utile si l’activité doit être interrompue pendant le chargement du contenu :

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

`SceneOperationProgress` peut être utilisé pour afficher des boîtes de dialogue de progression :

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

## <a name="monitoring-with-actions"></a>Surveillance avec des actions

Le système de scène fournit plusieurs actions qui vous permettent de savoir quand des scènes sont chargées ou déchargées. Chaque action relaie le nom de la scène affectée.

Si une opération de chargement ou de déchargement implique plusieurs scènes, les actions pertinentes sont appelées une fois par scène affectée. Ils sont également appelés en même temps lorsque l’opération de chargement ou de déchargement est *entièrement terminée.* Pour cette raison, il est recommandé d’utiliser des actions *OnWillUnload* pour détecter le contenu qui *sera* détruit, par opposition à l’utilisation d’actions *OnUnloaded* pour détecter le contenu détruit une fois le fait effectué.

Du côté du basculement, étant donné que les actions *OnLoaded* sont appelées uniquement lorsque toutes les scènes sont activées et entièrement chargées, l’utilisation d’actions *OnLoaded* pour détecter et utiliser le nouveau contenu est garantie.

Action | Quand elle est appelée | Scènes du contenu | Scènes d’éclairage | Scènes du gestionnaire
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | Juste avant le chargement d’une scène de contenu | • | |  
`OnContentLoaded` | Une fois que toutes les scènes de contenu d’une opération de chargement ont été entièrement chargées et activées | • | |
`OnWillUnloadContent` | Juste avant une opération de déchargement de scène de contenu | • | |
`OnContentUnloaded` | Une fois que toutes les scènes de contenu d’une opération de déchargement ont été entièrement déchargées | • | |
`OnWillLoadLighting` | Juste avant une charge de scène d’éclairage | | • |
`OnLightingLoaded` | Après le chargement et l’activation d’une scène d’éclairage| | • |
`OnWillUnloadLighting` | Juste avant le déchargement d’une scène d’éclairage | | • |
`OnLightingUnloaded` | Après le déchargement complet d’une scène d’éclairage | | • |
`OnWillLoadScene` | Juste avant le chargement d’une scène | • | • | •
`OnSceneLoaded` | Après le chargement complet et l’activation de toutes les scènes dans une opération | • | • | •
`OnWillUnloadScene` | Juste avant le déchargement d’une scène | • | • | •
`OnSceneUnloaded` | Après le déchargement complet d’une scène |  • | • | •

### <a name="action-examples"></a>Exemples d’actions

Un autre exemple de boîte de dialogue de progression utilisant des actions et une Coroutine plutôt qu’une mise à jour :

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

## <a name="controlling-scene-activation"></a>Contrôle de l’activation des scènes

Par défaut, le contenu est activé lorsqu’il est chargé. Si vous souhaitez contrôler manuellement l’activation des scènes, vous pouvez passer une `SceneActivationToken` à toute méthode de chargement de contenu. Si plusieurs scènes de contenu sont chargées par une seule opération, ce jeton d’activation s’appliquera à toutes les scènes.

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

## <a name="checking-which-content-is-loaded"></a>Vérification du contenu chargé

La `ContentSceneNames` propriété fournit un tableau des scènes de contenu disponibles par ordre d’index de Build. Vous pouvez vérifier si ces scènes sont chargées via `IsContentLoaded(string contentName)` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
