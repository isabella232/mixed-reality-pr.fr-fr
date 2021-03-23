---
title: Exemples d’applications et de fonctionnalités
description: Restez informé de tous les exemples Microsoft et toutes les applications des fonctionnalités de réalité mixte disponibles pour HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: réalité mixte, Unity, tutoriel, HoloLens, formation, exemples, MRTK, mode de recherche, HoloLens 2, codes QR, WebRTC, Capture de Réalité Mixte, communication à distance holographique, outils d’expérience utilisateur
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583193"
---
# <a name="samples-and-feature-apps"></a>Exemples d’applications et de fonctionnalités

![Image d’un utilisateur portant un HoloLens et manipulant un hologramme en déplaçant les mains](unreal/images/unreal-developer.jpg)

Chaque parcours de développement commence par un retour sur ce que les autres développeurs ont réussi à créer. De ce point de vue, la réalité mixte ne fait pas exception à la règle. Tous nos tutoriels et exemples d’applications sont actuellement créés dans Unity ou Unreal. À mesure que nous développerons du contenu pour d’autres moteurs et plateformes, nous ajouterons des titres à la table des matières.

## <a name="sample-apps"></a>Exemples d’application

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Exemples de fonctionnalités

Les exemples de fonctionnalités listés ci-dessous correspondent à des implémentations spécifiques traitées dans notre documentation. Ils couvrent tout un éventail de plateformes de développement et de périphériques matériels.

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
| [Codes QR](platform-capabilities-and-apis/qr-code-tracking.md) | [Suivi des codes QR dans Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

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