---
title: Fournisseurs d’entrée
description: Documentation sur les différents types de fournisseurs d’entrée dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145259"
---
# <a name="input-providers"></a>Fournisseurs d’entrée

Les fournisseurs d’entrée sont enregistrés dans le **profil des fournisseurs de services inscrits**, qui se trouve dans le composant d’outils de réalité mixte :

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
