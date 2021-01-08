---
title: Utilisation de WebXR avec Windows Mixed Reality
description: Découvrez les principes de base de l’utilisation et du développement d’applications WebXR s’exécutant sur des casques immersifs Windows Mixed Reality.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 vidéos, 360 photo, 360 photos, 360 content, Internet immersif, immersiveweb, IW
ms.openlocfilehash: e49f5f2422c9802f94b63943f8a38949a2969f83
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006939"
---
# <a name="webxr-overview"></a>Présentation de WebXR

## <a name="what-is-webxr"></a>Qu’est-ce que WebXR

L' **API d’appareil WebXR** permet d’accéder à des appareils de réalité **virtuelle (VR)** et de **réalité augmentée (AR)** , notamment des **capteurs** et des **affichages montés en tête** sur le **Web**. L’API d’appareil WebXR est actuellement disponible sur Microsoft Edge et Chrome version 79 et les versions ultérieures prennent en charge WebXR comme valeur par défaut. Vous pouvez vérifier l’état de prise en charge du navigateur le plus récent pour WebXR sur [caniuse.com](https://caniuse.com/#search=webxr).

Apprenez-en davantage sur [Windows Mixed Reality et le nouveau Microsoft Edge dans la](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)section [Nouveautés](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) .

## <a name="viewing-webxr"></a>Affichage de WebXR

> [!IMPORTANT]
> Microsoft Edge (hérité) prend uniquement en charge WebVR, une API déconseillée qui n’est pas disponible dans les navigateurs actuels. Toutefois, le nouveau **[navigateur Edge basé sur le chrome](../../whats-new/new-microsoft-edge.md)** prend en charge WebXR et est disponible pour le prototypage de VR dans Windows Mixed Reality. WebVR ne sera pas disponible dans le nouveau navigateur Edge basé sur le chrome.
> 
> Si vous cherchez un moyen de prototyper WebXR sur HoloLens 2 aujourd’hui, consultez la [réalité de Firefox](https://mixedreality.mozilla.org/firefox-reality/).

Pour tester si votre navigateur prend en charge WebXR, vous pouvez accéder à des [exemples WebXR](https://immersive-web.github.io/webxr-samples/) dans votre navigateur.

## <a name="see-also"></a>Voir aussi

* [Spécification de l’API d’appareil WebXR](https://immersive-web.github.io/webxr/)
* [Documentation de l’API d’appareil WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb. dev](https://immersiveweb.dev/)
* [Exemples WebXR](https://immersive-web.github.io/webxr-samples/)
* [Windows Mixed Reality et le nouveau Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Github du W3C sur le Web immersif](https://github.com/immersive-web)
* [API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [API du boîtier de manette](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) et les [extensions de boîtier](https://w3c.github.io/gamepad/extensions.html)
* [Gestion du contexte perdu dans WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Utilisation de Babylon.js pour créer des expériences WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Groupe de communauté Web immersif](https://www.w3.org/community/immersive-web/)
