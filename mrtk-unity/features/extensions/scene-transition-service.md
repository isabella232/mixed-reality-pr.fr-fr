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
# <a name="scene-transition-service"></a><span data-ttu-id="6cd90-104">Service de transition de scène</span><span class="sxs-lookup"><span data-stu-id="6cd90-104">Scene transition service</span></span>

<span data-ttu-id="6cd90-105">Cette extension simplifie les activités de fondu d’une scène, l’affichage d’un indicateur de progression, le chargement d’une scène, puis le fondu.</span><span class="sxs-lookup"><span data-stu-id="6cd90-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="6cd90-106">Les opérations de scène sont pilotées par le service SceneSystem, mais toute opération basée sur les tâches peut être utilisée pour conduire une transition.</span><span class="sxs-lookup"><span data-stu-id="6cd90-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="6cd90-107">Activation de l’extension</span><span class="sxs-lookup"><span data-stu-id="6cd90-107">Enabling the extension</span></span>

<span data-ttu-id="6cd90-108">Pour activer l’extension, ouvrez votre profil RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="6cd90-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="6cd90-109">Cliquez sur inscrire un nouveau fournisseur de services pour ajouter une nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="6cd90-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="6cd90-110">Dans le champ type de composant, sélectionnez SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="6cd90-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="6cd90-111">Dans le champ Profil de configuration, sélectionnez le profil de transition de scène par défaut inclus avec l’extension.</span><span class="sxs-lookup"><span data-stu-id="6cd90-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="6cd90-112">Options de profil</span><span class="sxs-lookup"><span data-stu-id="6cd90-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="6cd90-113">Utiliser l’indicateur de progression par défaut</span><span class="sxs-lookup"><span data-stu-id="6cd90-113">Use default progress indicator</span></span>

<span data-ttu-id="6cd90-114">Si cette option est activée, l’indicateur de progression par défaut Prefab est utilisé quand aucun objet indicateur de progression n’est fourni lors `DoSceneTransition.` de l’appel de si un objet indicateur de progression est fourni, la valeur par défaut est ignorée.</span><span class="sxs-lookup"><span data-stu-id="6cd90-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="6cd90-115">Utiliser la couleur de fondu</span><span class="sxs-lookup"><span data-stu-id="6cd90-115">Use fade color</span></span>

<span data-ttu-id="6cd90-116">Si cette option est activée, le service de transition applique un fondu pendant votre transition.</span><span class="sxs-lookup"><span data-stu-id="6cd90-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="6cd90-117">Ce paramètre peut être modifié au moment de l’exécution via la propriété du service `UseFadeColor` .</span><span class="sxs-lookup"><span data-stu-id="6cd90-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="6cd90-118">Couleur de fondu</span><span class="sxs-lookup"><span data-stu-id="6cd90-118">Fade color</span></span>

<span data-ttu-id="6cd90-119">Contrôle la couleur de l’effet de fondu.</span><span class="sxs-lookup"><span data-stu-id="6cd90-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="6cd90-120">Alpha est ignoré.</span><span class="sxs-lookup"><span data-stu-id="6cd90-120">Alpha is ignored.</span></span> <span data-ttu-id="6cd90-121">Ce paramètre peut être modifié au moment de l’exécution avant une transition via la `FadeColor` propriété du service.</span><span class="sxs-lookup"><span data-stu-id="6cd90-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="6cd90-122">Atténuer les cibles</span><span class="sxs-lookup"><span data-stu-id="6cd90-122">Fade targets</span></span>

<span data-ttu-id="6cd90-123">Détermine les appareils photo auxquels un effet de fondu sera appliqué.</span><span class="sxs-lookup"><span data-stu-id="6cd90-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="6cd90-124">Ce paramètre peut être modifié au moment de l’exécution via la propriété du service `FadeTargets` .</span><span class="sxs-lookup"><span data-stu-id="6cd90-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="6cd90-125">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6cd90-125">Setting</span></span> | <span data-ttu-id="6cd90-126">Caméras ciblées</span><span class="sxs-lookup"><span data-stu-id="6cd90-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="6cd90-127">Principal</span><span class="sxs-lookup"><span data-stu-id="6cd90-127">Main</span></span> | <span data-ttu-id="6cd90-128">Applique un effet d’atténuation à l’appareil photo principal.</span><span class="sxs-lookup"><span data-stu-id="6cd90-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="6cd90-129">Interface utilisateur du service</span><span class="sxs-lookup"><span data-stu-id="6cd90-129">UI</span></span> | <span data-ttu-id="6cd90-130">Applique un effet d’atténuation aux appareils photo sur la couche d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6cd90-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="6cd90-131">(N’affecte pas l’interface utilisateur de superposition)</span><span class="sxs-lookup"><span data-stu-id="6cd90-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="6cd90-132">Tous</span><span class="sxs-lookup"><span data-stu-id="6cd90-132">All</span></span> | <span data-ttu-id="6cd90-133">S’applique à la fois aux caméras principale et d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6cd90-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="6cd90-134">Custom</span><span class="sxs-lookup"><span data-stu-id="6cd90-134">Custom</span></span> | <span data-ttu-id="6cd90-135">S’applique à un ensemble personnalisé de caméras fournies via `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="6cd90-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="6cd90-136">Délai d’attente/fondu dans le temps</span><span class="sxs-lookup"><span data-stu-id="6cd90-136">Fade out time / fade in time</span></span>

<span data-ttu-id="6cd90-137">Paramètres par défaut pour la durée d’un fondu lors de l’entrée/sortie d’une transition.</span><span class="sxs-lookup"><span data-stu-id="6cd90-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="6cd90-138">Ces paramètres peuvent être modifiés au moment de l’exécution via les `FadeOutTime` Propriétés et du service `FadeInTime` .</span><span class="sxs-lookup"><span data-stu-id="6cd90-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="6cd90-139">Type d’atténuation de l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="6cd90-139">Camera fader type</span></span>

<span data-ttu-id="6cd90-140">`ICameraFader`Classe à utiliser pour appliquer un effet de fondu aux appareils photo.</span><span class="sxs-lookup"><span data-stu-id="6cd90-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="6cd90-141">La classe par défaut `CameraFaderQuad` instancie un quadruple avec un matériau transparent devant la caméra cible près du plan de découpage.</span><span class="sxs-lookup"><span data-stu-id="6cd90-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="6cd90-142">Une autre approche consiste à utiliser un système d’effets de la publication.</span><span class="sxs-lookup"><span data-stu-id="6cd90-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="6cd90-143">En utilisant l’extension</span><span class="sxs-lookup"><span data-stu-id="6cd90-143">Using the extension</span></span>

<span data-ttu-id="6cd90-144">Vous utilisez le service de transition en passant des tâches qui sont exécutées pendant que l’appareil photo est sorti.</span><span class="sxs-lookup"><span data-stu-id="6cd90-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="6cd90-145">Utilisation des tâches système de scène</span><span class="sxs-lookup"><span data-stu-id="6cd90-145">Using scene system tasks</span></span>

<span data-ttu-id="6cd90-146">Dans la plupart des cas, vous utiliserez les tâches fournies par le service SceneSystem :</span><span class="sxs-lookup"><span data-stu-id="6cd90-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

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

### <a name="using-custom-tasks"></a><span data-ttu-id="6cd90-147">Utilisation de tâches personnalisées</span><span class="sxs-lookup"><span data-stu-id="6cd90-147">Using custom tasks</span></span>

<span data-ttu-id="6cd90-148">Dans d’autres cas, vous souhaiterez peut-être effectuer une transition sans réellement charger une scène :</span><span class="sxs-lookup"><span data-stu-id="6cd90-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

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

<span data-ttu-id="6cd90-149">Vous pouvez également charger une scène sans utiliser le service SceneSystem :</span><span class="sxs-lookup"><span data-stu-id="6cd90-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

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

### <a name="using-multiple-tasks"></a><span data-ttu-id="6cd90-150">Utilisation de plusieurs tâches</span><span class="sxs-lookup"><span data-stu-id="6cd90-150">Using multiple tasks</span></span>

<span data-ttu-id="6cd90-151">Vous pouvez également fournir plusieurs tâches qui seront exécutées dans l’ordre :</span><span class="sxs-lookup"><span data-stu-id="6cd90-151">You can also supply multiple tasks, which will be executed in order:</span></span>

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

## <a name="using-the-progress-indicator"></a><span data-ttu-id="6cd90-152">Utilisation de l’indicateur de progression</span><span class="sxs-lookup"><span data-stu-id="6cd90-152">Using the progress indicator</span></span>

<span data-ttu-id="6cd90-153">Un indicateur de progression est tout ce qui implémente l' `IProgressIndicator` interface.</span><span class="sxs-lookup"><span data-stu-id="6cd90-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="6cd90-154">Cela peut prendre la forme d’un écran de démarrage, d’un indicateur de chargement 3D accompagnent ou tout autre qui fournit des commentaires sur la progression de la transition.</span><span class="sxs-lookup"><span data-stu-id="6cd90-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="6cd90-155">Si `UseDefaultProgressIndicator` est activé dans le profil SceneTransitionService, un indicateur de progression est instancié au début d’une transition.</span><span class="sxs-lookup"><span data-stu-id="6cd90-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="6cd90-156">Pour la durée de la transition, les propriétés et de cet indicateur sont `Progress` `Message` accessibles via les méthodes et de ce service `SetProgressValue` `SetProgressMessage` .</span><span class="sxs-lookup"><span data-stu-id="6cd90-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

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

<span data-ttu-id="6cd90-157">Si vous appelez, `DoSceneTransition` vous pouvez également fournir votre propre indicateur de progression à l’aide de l' `progressIndicator` argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="6cd90-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="6cd90-158">Cela remplacera l’indicateur de progression par défaut.</span><span class="sxs-lookup"><span data-stu-id="6cd90-158">This will override the default progress indicator.</span></span>
