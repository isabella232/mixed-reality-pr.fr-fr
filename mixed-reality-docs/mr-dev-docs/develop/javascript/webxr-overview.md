---
title: Utilisation de WebXR avec Windows Mixed Reality
description: Découvrez les principes de base de l’utilisation et du développement d’applications WebXR s’exécutant sur des casques immersifs Windows Mixed Reality.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 vidéos, 360 photo, 360 photos, 360 content, Internet immersif, immersiveweb, IW
ms.openlocfilehash: 0954d6554acea8474548a3703de35971a76f7770
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088478"
---
# <a name="webxr-overview"></a><span data-ttu-id="56795-104">Présentation de WebXR</span><span class="sxs-lookup"><span data-stu-id="56795-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="56795-105">Qu’est-ce que WebXR</span><span class="sxs-lookup"><span data-stu-id="56795-105">What is WebXR</span></span>

<span data-ttu-id="56795-106">L' [**API d’appareil WebXR**](https://www.w3.org/TR/webxr/) permet d’accéder à des appareils de réalité **virtuelle (VR)** et de **réalité augmentée (AR)** , notamment des **capteurs** et des **affichages montés en tête** sur le **Web**.</span><span class="sxs-lookup"><span data-stu-id="56795-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="56795-107">L’API d’appareil WebXR est actuellement disponible sur Microsoft Edge et Chrome version 79 et les versions ultérieures prennent en charge WebXR comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="56795-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="56795-108">Vous pouvez vérifier l’état de prise en charge du navigateur le plus récent pour WebXR sur [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="56795-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="56795-109">Affichage de WebXR</span><span class="sxs-lookup"><span data-stu-id="56795-109">Viewing WebXR</span></span>

<span data-ttu-id="56795-110">Vous pouvez afficher WebXR experinces sur [Windows Mixed Reality et la nouvelle réalité Microsoft Edge](/windows/mixed-reality/whats-new/new-microsoft-edge) et [Firefox](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="56795-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](/windows/mixed-reality/whats-new/new-microsoft-edge) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="56795-111">Pour tester si votre navigateur prend en charge WebXR, vous pouvez accéder à des [exemples WebXR](https://immersive-web.github.io/webxr-samples/) dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="56795-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="56795-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56795-112">See Also</span></span>

* [<span data-ttu-id="56795-113">Utilisation de Babylon.js pour créer des expériences WebXR</span><span class="sxs-lookup"><span data-stu-id="56795-113">Using Babylon.js to create WebXR experiences</span></span>](/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-helloworld/introduction-01)
* [<span data-ttu-id="56795-114">Spécification de l’API d’appareil WebXR</span><span class="sxs-lookup"><span data-stu-id="56795-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="56795-115">Documentation de l’API d’appareil WebXR</span><span class="sxs-lookup"><span data-stu-id="56795-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="56795-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="56795-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="56795-117">Exemples WebXR</span><span class="sxs-lookup"><span data-stu-id="56795-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="56795-118">Windows Mixed Reality et le nouveau Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="56795-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/whats-new/new-microsoft-edge)
* [<span data-ttu-id="56795-119">Github du W3C sur le Web immersif</span><span class="sxs-lookup"><span data-stu-id="56795-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="56795-120">[API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="56795-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="56795-121">[API du boîtier de manette](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) et les [extensions de boîtier](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="56795-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="56795-122">Gestion du contexte perdu dans WebGL</span><span class="sxs-lookup"><span data-stu-id="56795-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="56795-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="56795-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="56795-124">glTF</span><span class="sxs-lookup"><span data-stu-id="56795-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="56795-125">Groupe de communauté Web immersif</span><span class="sxs-lookup"><span data-stu-id="56795-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
