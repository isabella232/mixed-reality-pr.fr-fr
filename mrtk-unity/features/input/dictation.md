---
title: Dictation
description: Docummentation sur l’enregistrement des clips audio et l’obtention d’une transcription dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176476"
---
# <a name="dictation"></a><span data-ttu-id="e324a-104">Dictation</span><span class="sxs-lookup"><span data-stu-id="e324a-104">Dictation</span></span>

<span data-ttu-id="e324a-105">La dictée permet aux utilisateurs d’enregistrer des clips audio et d’obtenir une transcription.</span><span class="sxs-lookup"><span data-stu-id="e324a-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="e324a-106">Pour l’utiliser, assurez-vous qu’un système de dictée est inscrit dans le *profil de système d’entrée*.</span><span class="sxs-lookup"><span data-stu-id="e324a-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="e324a-107">**Windows fournisseur d’entrée de dictée** est le système de dictée prêt à l’emploi, mais d’autres systèmes de dictée peuvent être mis en œuvre [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .</span><span class="sxs-lookup"><span data-stu-id="e324a-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="e324a-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e324a-108">Requirements</span></span>

<span data-ttu-id="e324a-109">le système de dictée utilise [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) d’unity, qui utilise lui-même les api de reconnaissance vocale Windows sous-jacentes pour la gestion de la dictée.</span><span class="sxs-lookup"><span data-stu-id="e324a-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="e324a-110">notez que cela implique que cette fonctionnalité est uniquement présente sur les plateformes basées sur Windows.</span><span class="sxs-lookup"><span data-stu-id="e324a-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="e324a-111">L’utilisation du système de dictée nécessite les fonctionnalités de l’application « client Internet » et « microphone » dans la [section PlayerSettings-Capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span><span class="sxs-lookup"><span data-stu-id="e324a-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="e324a-112">pour plus d’informations sur l’entrée vocale dans unity, consultez [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) .</span><span class="sxs-lookup"><span data-stu-id="e324a-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="e324a-113">Configuration</span><span class="sxs-lookup"><span data-stu-id="e324a-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="e324a-114">Une fois que vous avez configuré un service de dictée, vous pouvez utiliser le [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script pour démarrer et arrêter l’enregistrement de sessions et obtenir les résultats de transcription via UnityEvents.</span><span class="sxs-lookup"><span data-stu-id="e324a-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="e324a-115">L' **hypothèse de dictée** est déclenchée lorsque l’utilisateur parle de transcriptions précoces et approximatives du son capturé jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="e324a-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="e324a-116">Le résultat de la **dictée** est déclenché à la fin de chaque phrase (c’est-à-dire lorsque l’utilisateur s’arrête) avec la transcription finale de l’audio capturé jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="e324a-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="e324a-117">La **dictée terminée** est déclenchée à la fin de la session d’enregistrement avec la transcription complète et finale de l’audio.</span><span class="sxs-lookup"><span data-stu-id="e324a-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="e324a-118">Une **erreur de dictée** est générée pour signaler des erreurs dans le service de dictée.</span><span class="sxs-lookup"><span data-stu-id="e324a-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="e324a-119">Dans ce cas, la transcription contient une description de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="e324a-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="e324a-120">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="e324a-120">Example scene</span></span>

<span data-ttu-id="e324a-121">La scène de **dictée** dans `MRTK/Examples/Demos/Input/Scenes/Dictation` montre le `DictationHandler` script en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="e324a-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="e324a-122">Si vous avez besoin de davantage de contrôle, vous pouvez étendre ce script ou créer votre propre implémentation [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) pour recevoir directement les événements de dictée.</span><span class="sxs-lookup"><span data-stu-id="e324a-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
