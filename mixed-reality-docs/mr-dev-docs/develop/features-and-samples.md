---
title: Exemples d’applications et de fonctionnalités
description: Restez informé de tous les exemples Microsoft et toutes les applications des fonctionnalités de réalité mixte disponibles pour HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: réalité mixte, Unity, tutoriel, HoloLens, formation, exemples, MRTK, mode de recherche, HoloLens 2, codes QR, WebRTC, Capture de Réalité Mixte, communication à distance holographique, outils d’expérience utilisateur
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906895"
---
# <a name="samples-and-feature-apps"></a>Exemples d’applications et de fonctionnalités

![Image d’un utilisateur portant un HoloLens et manipulant un hologramme en déplaçant les mains](unreal/images/unreal-developer.jpg)

Chaque parcours de développement commence par un retour sur ce que les autres développeurs ont réussi à créer. De ce point de vue, la réalité mixte ne fait pas exception à la règle. Tous nos tutoriels et exemples d’applications sont actuellement créés dans Unity ou Unreal. À mesure que nous développerons du contenu pour d’autres moteurs et plateformes, nous ajouterons des titres à la table des matières.

## <a name="sample-apps"></a>Exemples d’application

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Exemples de fonctionnalités

Les exemples de fonctionnalités listés ci-dessous correspondent à des implémentations spécifiques traitées dans notre documentation. Ils couvrent tout un éventail de plateformes de développement et de périphériques matériels.

### <a name="openxr"></a>OpenXR

Les développeurs ciblant Unity 2020 pour créer des applications HoloLens 2 ou de réalité mixte peuvent utiliser le plug-in OpenXR à la place du plug-in WindowsXR pour de meilleures compatibilités entre les plateformes. Le plug-in Mixed Reality OpenXR fonctionne également bien avec la dernière version de Mixed Reality Toolkit 2.7.

<br>

| Article de référence | Exemple |
| --- | --- |
| [Utilisation du plug-in OpenXR](./unity/xr-project-setup.md) | [Exemples de Mixed Reality OpenXR avec Unity](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| N/A | [Projet Unity de base OpenXR MRTK](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a>Mode Recherche

Le mode Recherche a été introduit dans la 1re génération des HoloLens afin de permettre l’accès aux capteurs clés de l’appareil, en particulier pour les applications de recherche qui ne sont pas destinées au déploiement. Les exemples d’applications ci-dessous sont des exemples d’accès et d’enregistrement des flux du mode Recherche. Ils correspondent également à des exemples d’utilisation des propriétés [intrinsèques et extrinsèques](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).

<br>

| Article de référence | Exemple d’application |
| --- | --- |
| [Mode Recherche](platform-capabilities-and-apis/research-mode.md) | [HoloLens (1ère génération)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Mode Recherche](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>Codes QR

HoloLens 2 peut détecter les codes QR dans l’environnement situé autour du casque, ce qui permet d’établir un système de coordonnées à l’emplacement réel de chaque code.

<br>

| Article de référence | Exemple |
| --- | --- |
| [Codes QR](platform-capabilities-and-apis/qr-code-tracking.md) | [Suivi des codes QR dans Unity](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a>Compréhension des scènes

La compréhension des scènes fournit aux développeurs de réalité mixte une représentation d’environnement structurée et de haut niveau, conçue pour rendre intuitif le développement pour les applications compatibles avec l’environnement. Pour ce faire, la compréhension des scènes combine la puissance de runtimes de réalité mixte existants, tels que le mappage spatial très précis mais moins structuré, et de nouveaux runtimes reposant sur l’IA.

<br>

| Article de référence | Exemple |
| --- | --- |
| [Compréhension des scènes](../design/scene-understanding.md) | [Exemples de compréhension de scènes de réalité mixte](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a>WebRTC

Le projet MixedReality-WebRTC est une collection de composants destinés à aider les développeurs d’applications de réalité mixte à intégrer les transmissions audio, vidéo et de données pair à pair ainsi que les communications en temps réel dans leurs applications. Les composants WebRTC sont basés sur le protocole WebRTC pour la communication en temps réel (RTC), qui est pris en charge par la plupart des navigateurs web modernes.

<br>

| Article de référence | Exemple |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [Exemples d’applications WebRTC](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>Capture de réalité mixte holographique

La capture de réalité mixte (MRC) permet de capturer une expérience utilisateur à la première personne, qui consiste à mélanger les mondes réel et numérique sous forme de photo ou de vidéo, et à partager ce que vous voyez avec les autres en temps réel.

<br>

| Article de référence | Exemple |
| --- | --- |
| [Capture de réalité mixte](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [Exemples de captures de réalité mixte](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>Communication à distance holographique

Holographic Remoting Player est un complément qui se connecte aux applications et aux jeux PC prenant en charge la communication à distance holographique. Holographic Remoting transmet en streaming le contenu holographique d’un PC vers votre Microsoft HoloLens en temps réel, à l’aide d’une connexion Wi-Fi. Il est pris en charge par HoloLens (1re génération) et HoloLens 2.

<br>

| Article de référence | Exemple |
| --- | --- |
| [Communication à distance holographique](platform-capabilities-and-apis/holographic-remoting-player.md) | [Exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |