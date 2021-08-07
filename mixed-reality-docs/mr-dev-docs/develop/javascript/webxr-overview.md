---
title: Utilisation de WebXR avec Windows Mixed Reality
description: découvrez les principes de base de l’utilisation et du développement d’applications WebXR s’exécutant sur Windows Mixed Reality des casques immersifs.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 video, 360 vidéos, 360 photo, 360 photos, 360 content, internet immersif, immersiveweb, IW
ms.openlocfilehash: e670135cb00db26082b73f8465390a686de6a3e946bbffa561f9df90085970f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216265"
---
# <a name="webxr-overview"></a>Présentation de WebXR

## <a name="javascript-development"></a>Développement JavaScript

JavaScript est l’un des langages de programmation les plus populaires au monde ! C’est simple, léger et largement utilisé sur le Web. Tirez parti de la puissance de vos compétences en langage JavaScript et Web pour créer des expériences de réalité mixte plus attrayantes.

## <a name="mixed-reality-applications-on-the-web"></a>Applications de réalité mixte sur le Web

Les fonctionnalités de réalité mixte sont disponibles sur le Web à l’aide de [WebXR](webxr-overview.md). Vous pouvez voir le contenu de la réalité virtuelle et de la réalité augmentée (AR) dans un navigateur compatible WebXR sans installer de logiciel ou de plug-ins supplémentaires. Vous pouvez utiliser ce même navigateur avec un appareil physique tel que le HoloLens 2.

L' [**API d’appareil WebXR**](https://www.w3.org/TR/webxr/) permet d’accéder à des appareils de réalité **virtuelle (VR)** et de **réalité augmentée (AR)** , notamment des **capteurs** et des **affichages montés en tête** sur le **Web**. l’API d’appareil WebXR est actuellement disponible sur Microsoft Edge et Chrome version 79 et les versions ultérieures prennent en charge WebXR comme valeur par défaut. Vous pouvez vérifier l’état de prise en charge du navigateur le plus récent pour WebXR sur [caniuse.com](https://caniuse.com/#search=webxr).

> [!NOTE]
> **WebVR** est déconseillé et n’est pas disponible dans les navigateurs actuels. par conséquent, il ne doit pas être utilisé pour un nouveau développement. Vous devrez migrer toutes les implémentations de **WebVR** existantes vers **WebXR**.

### <a name="viewing-webxr"></a>Affichage de WebXR

vous pouvez afficher WebXR experinces sur [Windows Mixed Reality et la nouvelle Microsoft Edge et la](../../whats-new/new-microsoft-edge.md) [réalité de Firefox](https://mixedreality.mozilla.org/firefox-reality/).
Pour tester si votre navigateur prend en charge WebXR, vous pouvez accéder aux [exemples WebXR](https://immersive-web.github.io/webxr-samples/) dans votre navigateur.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Que puis-je utiliser pour développer des expériences Web immersifs ?

La liste suivante répertorie les infrastructures et les API JavaScript pour créer des expériences immersifs qui dominent actuellement le marché et qui sont largement acceptées et adoptées par les développeurs JavaScript de réalité mixte :

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon est un moteur 3D JavaScript qui facilite le développement de contenu 3D et d’applications immersifs. Avant de commencer à utiliser des applications immersifs, nous vous recommandons d’apprendre les principes fondamentaux du développement Babylon.js.<br/><br/>-Apprenez à créer des applications 3D avec babylon.js la [prise](https://doc.babylonjs.com/start)en main.<br/>-Jouez avec des exemples 3D et leur code source à l’aide de babylon.js [terrain](https://doc.babylonjs.com/examples/)<br/>-Explorez plus en détail [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-Découvrez comment prendre en main nos didacticiels [créer votre première application « Hello World ! »](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Logo BabylonJS](images/babylon.js.example.png) |
|[**Frame-**](https://aframe.io/) <br/><br/>Un frame est un framework JavaScript déclaratif qui permet de prendre en main la réalité virtuelle sur le Web. Pour en savoir plus, consultez la [documentation d’un cadre](https://aframe.io/docs/1.2.0/introduction/) . |![Frame-](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js est une bibliothèque 3D populaire pour créer des expériences immersifs. En savoir plus sur [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) dans la page de documentation et en explorant des [exemples](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Vous pouvez accéder aux API d’appareil WebXR directement à l’aide des API WebGL. WebGL (Web Graphics Library) est une API JavaScript pour le rendu de graphiques 3D et 2D interactifs à hautes performances dans n’importe quel navigateur Web compatible sans utiliser de plug-ins. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>Voir aussi

* [Présentation de WebXR](webxr-overview.md)
* [Spécification de l’API d’appareil WebXR](https://immersive-web.github.io/webxr/)
* [Documentation de l’API d’appareil WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Exemples WebXR](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Utilisation de Babylon.js pour créer des expériences WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [API du boîtier de manette](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) et les [extensions de boîtier](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality et le nouveau Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [Gestion du contexte perdu dans WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Groupe de communauté Web immersif](https://www.w3.org/community/immersive-web/)
* [Github du W3C sur le Web immersif](https://github.com/immersive-web)