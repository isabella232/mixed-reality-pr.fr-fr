---
title: Entrée d’un enregistrement d’animation
description: Documentation sur le système d’enregistrement d’animation d’entrée dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 6bdb764c5905352b9aec7c1512a73e727b60573a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176942"
---
# <a name="input-animation-recording"></a>Entrée d’un enregistrement d’animation

MRTK comporte un système d’enregistrement par lequel les données de mouvement des têtes et de suivi des mains peuvent être stockées dans des fichiers d’animation. Les données enregistrées peuvent ensuite être lues à l’aide du [système de simulation d’entrée](input-simulation-service.md).

L’enregistrement d’entrée est un outil utile dans différentes situations :

* Création de tests automatisés pour l’interaction, les manipulations, les solveurs, etc. La création du déplacement des contrôleurs et des mains pour ces tests peut prendre du temps. L’enregistrement d’une entrée directement peut accélérer le processus et fournir des données réelles.
* Apprentissage de l’utilisation d’éléments UX à travers les animations.
  Montrer aux utilisateurs comment interagir avec les boutons et d’autres objets peut lisser la courbe d’apprentissage.
* Débogage d’un comportement inattendu qui peut se produire lors d’une utilisation normale.
  Le système d’enregistrement prend en charge un concept de « tampon enchaîné » qui permet d’enregistrer les entrées récentes en arrière-plan.
  Consultez [service d’enregistrement d’entrée](#input-recording-service).

## <a name="recording-and-playback-services"></a>Services d’enregistrement et de lecture

Deux services de système d’entrée sont fournis pour enregistrer et lire les entrées respectivement.

### <a name="input-recording-service"></a>Service d’enregistrement d’entrée

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) Récupère les données de la transformation principale de la caméra et des contrôleurs de la main active et les stocke dans une mémoire tampon interne. À la demande, ces données sont ensuite sérialisées en fichiers binaires pour le stockage et la relecture ultérieures.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="Animation d’entrée d’enregistrement" width="80%" alt="Recording diagram" class="center" />
</a>

Pour démarrer l’enregistrement d’entrée [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) , appelez la fonction. [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) interrompt l’enregistrement (mais ne supprime pas les données enregistrées jusqu’à présent, utilisez [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) pour effectuer cette opération si nécessaire).

Par défaut, la taille de la mémoire tampon d’enregistrement est limitée à 30 secondes. Cela permet au service d’enregistrement de conserver l’enregistrement en arrière-plan sans accumuler trop de données, puis d’enregistrer les 30 dernières secondes si nécessaire. L’intervalle de temps peut être modifié à l’aide de la [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) propriété, ou l’enregistrement peut être illimité à l’aide de l' [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) option.

Les données de la mémoire tampon d’enregistrement peuvent être enregistrées dans un fichier binaire à l’aide de la fonction [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) .

Pour plus d’informations sur le format de fichier binaire, consultez [spécification de format de fichier d’animation d’entrée](input-animation-file-format.md).

### <a name="input-playback-service"></a>Service de lecture d’entrée

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) lit un fichier binaire avec les données d’animation d’entrée, puis applique ces données via le [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) pour recréer les mouvements enregistrés.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Lire une animation d’entrée" width="80%" alt="Play Back diagram" class="center" />
</a>

Pour commencer à lire une animation d’entrée, celle-ci doit être chargée à partir d’un fichier à l’aide de la fonction [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) .

Appelez [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [Pause](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)ou [Stop](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) pour contrôler la lecture de l’animation.

L’heure actuelle de l’animation peut également être contrôlée directement avec la propriété [localtime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) .

> [!WARNING]
> Le bouclage ou la réinitialisation [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) directe de l’animation ou du paramètre en cas de nettoyage de la chronologie peut produire des résultats inattendus lors de la manipulation de la scène ! Seuls les mouvements d’entrée sont enregistrés, les modifications supplémentaires, telles que le déplacement d’objets ou le basculement de commutateurs, ne sont pas réinitialisées. Veillez à recharger la scène si des modifications irréversibles ont été apportées.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Outils de l’éditeur pour l’enregistrement et la diffusion d’une animation d’entrée

Un certain nombre d’outils sont disponibles dans l’éditeur Unity pour l’enregistrement et l’examen de l’animation d’entrée. ces outils sont accessibles dans la [fenêtre outils de simulation d’entrée](input-simulation-service.md#input-simulation-tools-window), qui peut être ouverte à partir de la _réalité mixte Shared Computer Toolkit > utilitaires > menu simulation d’entrée_ .

> [!NOTE]
> L’enregistrement et la lecture en entrée ne fonctionnent qu’en mode lecture.

La fenêtre d’enregistrement d’entrée a deux modes :

* _Enregistrement_ de l’entrée d’enregistrement en mode lecture et enregistrement de celle-ci dans des fichiers d’animation.

  Lorsque vous activez le bouton enregistrement, le [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) est activé pour enregistrer l’entrée.
  Quand vous désactivez le bouton enregistrement, la sélection enregistrer un fichier est affichée et l’animation d’entrée enregistrée est enregistrée dans la destination sélectionnée.

  La limite de temps de la mémoire tampon peut également être modifiée dans ce mode.

* _Lecture_ pour le chargement des fichiers d’animation, puis recréation de l’entrée via le système de simulation d’entrée.

  Une animation doit d’abord être chargée dans ce mode. Après l’enregistrement d’une entrée en mode d’enregistrement, l’animation qui en résulte est automatiquement chargée. Vous pouvez également cliquer sur le bouton « charger » pour sélectionner un fichier d’animation existant.

  Les boutons de contrôle d’heure de gauche à droite sont les suivants :

  * _Réinitialisez_ l’heure de lecture au début de l’animation.
  * _Lisez_ l’animation en continu dans le temps.
  * _Étape suivante d'_ une étape.

  Le curseur peut également être utilisé pour effectuer un nettoyage dans la chronologie d’animation.

> [!WARNING]
> L’animation ou la réinitialisation d’une animation d’entrée ou le nettoyage de la chronologie peut produire des résultats inattendus lors de la manipulation de la scène ! Seuls les mouvements d’entrée sont enregistrés, les modifications supplémentaires, telles que le déplacement d’objets ou le basculement de commutateurs, ne sont pas réinitialisées. Veillez à recharger la scène si des modifications irréversibles ont été apportées.
