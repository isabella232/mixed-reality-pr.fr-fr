---
title: Voix
description: configuration de l’entrée vocale dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, discours,
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228408"
---
# <a name="speech"></a>Voix

![Menu Proximité](../images/input/MRTK_Input_Speech.png)

les fournisseurs d’entrée vocale, comme *Windows entrée vocale*, ne créent aucun contrôleur, mais vous permettent de définir des mots clés qui déclencheront des événements d’entrée vocale lorsqu’ils sont reconnus. Le **profil de commandes vocales** dans le *profil de système d’entrée* vous permet de configurer les mots clés à reconnaître. Pour chaque commande, vous pouvez également :

- Sélectionnez une **action d’entrée** à mapper. De cette façon, vous pouvez utiliser le mot clé *Select* pour avoir le même effet qu’un clic gauche de la souris, en mappant les deux à la même action.
- Spécifiez un **Code de clé** qui produira le même événement vocal lorsqu’il sera enfoncé.
- Ajoutez une **clé de localisation** qui sera utilisée dans les applications UWP pour obtenir le mot clé localisé à partir des ressources de l’application.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>Gestion de l’entrée vocale

Le [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script peut être ajouté à un gameobject pour gérer les commandes vocales à l’aide de [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html). Il affiche automatiquement la liste des mots clés définis à partir du **profil des commandes vocales**.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

Affectez la valeur facultative **SpeechConfirmationTooltip. Prefab** pour afficher l’étiquette d’info-bulle de confirmation animée sur la reconnaissance.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

Les développeurs peuvent également implémenter l' [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface dans un composant de script personnalisé pour [gérer les événements d’entrée vocale](input-events.md#input-event-interface-example).

## <a name="example-scene"></a>Exemple de scène

La scène **SpeechInputExample** , dans `MRTK/Examples/Demos/Input/Scenes/Speech` , montre comment utiliser la reconnaissance vocale. Vous pouvez également écouter des événements de commande vocale directement dans votre propre script en implémentant [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (voir le tableau des [gestionnaires d’événements](input-events.md)).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
