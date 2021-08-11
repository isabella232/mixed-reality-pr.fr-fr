---
title: Dictation
description: Docummentation sur l’enregistrement des clips audio et l’obtention d’une transcription dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 14061197031282dcc9dd20a141101b65ee92ca2376bdc009fa8790076681a970
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220000"
---
# <a name="dictation"></a>Dictation

La dictée permet aux utilisateurs d’enregistrer des clips audio et d’obtenir une transcription. Pour l’utiliser, assurez-vous qu’un système de dictée est inscrit dans le *profil de système d’entrée*. **Windows fournisseur d’entrée de dictée** est le système de dictée prêt à l’emploi, mais d’autres systèmes de dictée peuvent être mis en œuvre [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Configuration requise

le système de dictée utilise [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) d’unity, qui utilise lui-même les api de reconnaissance vocale Windows sous-jacentes pour la gestion de la dictée. notez que cela implique que cette fonctionnalité est uniquement présente sur les plateformes basées sur Windows.

L’utilisation du système de dictée nécessite les fonctionnalités de l’application « client Internet » et « microphone » dans la [section PlayerSettings-Capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).
pour plus d’informations sur l’entrée vocale dans unity, consultez [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) .

## <a name="configuration"></a>Configuration

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Une fois que vous avez configuré un service de dictée, vous pouvez utiliser le [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script pour démarrer et arrêter l’enregistrement de sessions et obtenir les résultats de transcription via UnityEvents.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- L' **hypothèse de dictée** est déclenchée lorsque l’utilisateur parle de transcriptions précoces et approximatives du son capturé jusqu’à présent.
- Le résultat de la **dictée** est déclenché à la fin de chaque phrase (c’est-à-dire lorsque l’utilisateur s’arrête) avec la transcription finale de l’audio capturé jusqu’à présent.
- La **dictée terminée** est déclenchée à la fin de la session d’enregistrement avec la transcription complète et finale de l’audio.
- Une **erreur de dictée** est générée pour signaler des erreurs dans le service de dictée. Dans ce cas, la transcription contient une description de l’erreur.

## <a name="example-scene"></a>Exemple de scène

La scène de **dictée** dans `MRTK/Examples/Demos/Input/Scenes/Dictation` montre le `DictationHandler` script en cours d’utilisation. Si vous avez besoin de davantage de contrôle, vous pouvez étendre ce script ou créer votre propre implémentation [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) pour recevoir directement les événements de dictée.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
