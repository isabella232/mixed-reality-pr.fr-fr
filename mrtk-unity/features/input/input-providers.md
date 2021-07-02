---
title: Fournisseurs d’entrée
description: Documentation sur les différents types de fournisseurs d’entrée dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176749"
---
# <a name="input-providers"></a>Fournisseurs d’entrée

les fournisseurs d’entrée sont enregistrés dans le **profil des fournisseurs de services inscrits**, situé dans le composant Shared Computer Toolkit de la réalité mixte :

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Il s’agit des fournisseurs d’entrée prêts à l’emploi, ainsi que des contrôleurs correspondants :

| Fournisseur d’entrée | Controllers |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Simulation de main |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Souris  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | OpenVR générique, baguette vive, vive Knuckles, Oculus Touch, Oculus à distance, Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Manette de jeu générique  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Contrôleur tactile Unity  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *Aucun*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | WMR articulée, WMR Controller, WMR GGV (point de regard, geste et voix) |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *Aucun* |

Les fournisseurs de dictée et de reconnaissance vocale ne créent pas de contrôleurs, ils génèrent leurs propres événements d’entrée spécialisés directement.

Vous pouvez créer des fournisseurs d’entrée personnalisés en implémentant l' [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.

Pour plus d’informations, consultez [création d’un fournisseur de données de système d’entrée](create-data-provider.md).
