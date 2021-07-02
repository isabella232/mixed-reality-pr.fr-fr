---
title: Service de transition de scène
description: documentation relative à la transition de scène dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, SceneTransition,
ms.openlocfilehash: b645012a055f693fdac794b79e24fd20154fdb65
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176215"
---
# <a name="scene-transition-service"></a>Service de transition de scène

Cette extension simplifie les activités de fondu d’une scène, l’affichage d’un indicateur de progression, le chargement d’une scène, puis le fondu.

Les opérations de scène sont pilotées par le service SceneSystem, mais toute opération basée sur les tâches peut être utilisée pour conduire une transition.

## <a name="enabling-the-extension"></a>Activation de l’extension

Pour activer l’extension, ouvrez votre profil RegisteredServiceProvider. Cliquez sur inscrire un nouveau fournisseur de services pour ajouter une nouvelle configuration. Dans le champ type de composant, sélectionnez SceneTransitionService. Dans le champ Profil de configuration, sélectionnez le profil de transition de scène par défaut inclus avec l’extension.

## <a name="profile-options"></a>Options de profil

### <a name="use-default-progress-indicator"></a>Utiliser l’indicateur de progression par défaut

Si cette option est activée, l’indicateur de progression par défaut Prefab est utilisé quand aucun objet indicateur de progression n’est fourni lors `DoSceneTransition.` de l’appel de si un objet indicateur de progression est fourni, la valeur par défaut est ignorée.

### <a name="use-fade-color"></a>Utiliser la couleur de fondu

Si cette option est activée, le service de transition applique un fondu pendant votre transition. Ce paramètre peut être modifié au moment de l’exécution via la propriété du service `UseFadeColor` .

### <a name="fade-color"></a>Couleur de fondu

Contrôle la couleur de l’effet de fondu. Alpha est ignoré. Ce paramètre peut être modifié au moment de l’exécution avant une transition via la `FadeColor` propriété du service.

### <a name="fade-targets"></a>Atténuer les cibles

Détermine les appareils photo auxquels un effet de fondu sera appliqué. Ce paramètre peut être modifié au moment de l’exécution via la propriété du service `FadeTargets` .

Paramètre | Caméras ciblées
--- | --- | ---
Principal | Applique un effet d’atténuation à l’appareil photo principal.
Interface utilisateur du service | Applique un effet d’atténuation aux appareils photo sur la couche d’interface utilisateur. (N’affecte pas l’interface utilisateur de superposition)
Tous | S’applique à la fois aux caméras principale et d’interface utilisateur.
Custom | S’applique à un ensemble personnalisé de caméras fournies via `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Délai d’attente/fondu dans le temps

Paramètres par défaut pour la durée d’un fondu lors de l’entrée/sortie d’une transition. Ces paramètres peuvent être modifiés au moment de l’exécution via les `FadeOutTime` Propriétés et du service `FadeInTime` .

### <a name="camera-fader-type"></a>Type d’atténuation de l’appareil photo

`ICameraFader`Classe à utiliser pour appliquer un effet de fondu aux appareils photo. La classe par défaut `CameraFaderQuad` instancie un quadruple avec un matériau transparent devant la caméra cible près du plan de découpage. Une autre approche consiste à utiliser un système d’effets de la publication.

## <a name="using-the-extension"></a>En utilisant l’extension

Vous utilisez le service de transition en passant des tâches qui sont exécutées pendant que l’appareil photo est sorti.

### <a name="using-scene-system-tasks"></a>Utilisation des tâches système de scène

Dans la plupart des cas, vous utiliserez les tâches fournies par le service SceneSystem :

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a>Utilisation de tâches personnalisées

Dans d’autres cas, vous souhaiterez peut-être effectuer une transition sans réellement charger une scène :

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

Vous pouvez également charger une scène sans utiliser le service SceneSystem :

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a>Utilisation de plusieurs tâches

Vous pouvez également fournir plusieurs tâches qui seront exécutées dans l’ordre :

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a>Utilisation de l’indicateur de progression

Un indicateur de progression est tout ce qui implémente l' `IProgressIndicator` interface. Cela peut prendre la forme d’un écran de démarrage, d’un indicateur de chargement 3D accompagnent ou tout autre qui fournit des commentaires sur la progression de la transition.

Si `UseDefaultProgressIndicator` est activé dans le profil SceneTransitionService, un indicateur de progression est instancié au début d’une transition. Pour la durée de la transition, les propriétés et de cet indicateur sont `Progress` `Message` accessibles via les méthodes et de ce service `SetProgressValue` `SetProgressMessage` .

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

Si vous appelez, `DoSceneTransition` vous pouvez également fournir votre propre indicateur de progression à l’aide de l' `progressIndicator` argument facultatif. Cela remplacera l’indicateur de progression par défaut.
