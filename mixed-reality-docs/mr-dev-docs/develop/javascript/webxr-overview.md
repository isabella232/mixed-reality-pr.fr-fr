---
title: Utilisation de WebXR avec Windows Mixed Reality
description: Découvrez les principes de base de l’utilisation et du développement d’applications WebXR s’exécutant sur des casques immersifs Windows Mixed Reality.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 vidéos, 360 photo, 360 photos, 360 content, Internet immersif, immersiveweb, IW
ms.openlocfilehash: fa4d11fac59e25f43d9d55de16d3b0c35e8166b7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600108"
---
# <a name="webxr-overview"></a><span data-ttu-id="f92ad-104">Présentation de WebXR</span><span class="sxs-lookup"><span data-stu-id="f92ad-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="f92ad-105">Qu’est-ce que WebXR</span><span class="sxs-lookup"><span data-stu-id="f92ad-105">What is WebXR</span></span>

<span data-ttu-id="f92ad-106">L' [**API d’appareil WebXR**](https://www.w3.org/TR/webxr/) permet d’accéder à des appareils de réalité **virtuelle (VR)** et de **réalité augmentée (AR)** , notamment des **capteurs** et des **affichages montés en tête** sur le **Web**.</span><span class="sxs-lookup"><span data-stu-id="f92ad-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="f92ad-107">L’API d’appareil WebXR est actuellement disponible sur Microsoft Edge et Chrome version 79 et les versions ultérieures prennent en charge WebXR comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f92ad-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="f92ad-108">Vous pouvez vérifier l’état de prise en charge du navigateur le plus récent pour WebXR sur [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="f92ad-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="f92ad-109">Affichage de WebXR</span><span class="sxs-lookup"><span data-stu-id="f92ad-109">Viewing WebXR</span></span>

<span data-ttu-id="f92ad-110">Vous pouvez afficher WebXR experinces sur [Windows Mixed Reality et la nouvelle réalité Microsoft Edge](../../whats-new/new-microsoft-edge.md) et [Firefox](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="f92ad-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](../../whats-new/new-microsoft-edge.md) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="f92ad-111">Pour tester si votre navigateur prend en charge WebXR, vous pouvez accéder à des [exemples WebXR](https://immersive-web.github.io/webxr-samples/) dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="f92ad-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="f92ad-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f92ad-112">See Also</span></span>

* [<span data-ttu-id="f92ad-113">Utilisation de Babylon.js pour créer des expériences WebXR</span><span class="sxs-lookup"><span data-stu-id="f92ad-113">Using Babylon.js to create WebXR experiences</span></span>](./tutorials/babylonjs-webxr-helloworld/introduction-01.md)
* [<span data-ttu-id="f92ad-114">Spécification de l’API d’appareil WebXR</span><span class="sxs-lookup"><span data-stu-id="f92ad-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="f92ad-115">Documentation de l’API d’appareil WebXR</span><span class="sxs-lookup"><span data-stu-id="f92ad-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="f92ad-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="f92ad-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="f92ad-117">Exemples WebXR</span><span class="sxs-lookup"><span data-stu-id="f92ad-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="f92ad-118">Windows Mixed Reality et le nouveau Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f92ad-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](../../whats-new/new-microsoft-edge.md)
* [<span data-ttu-id="f92ad-119">Github du W3C sur le Web immersif</span><span class="sxs-lookup"><span data-stu-id="f92ad-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="f92ad-120">[API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f92ad-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="f92ad-121">[API du boîtier de manette](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) et les [extensions de boîtier](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="f92ad-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="f92ad-122">Gestion du contexte perdu dans WebGL</span><span class="sxs-lookup"><span data-stu-id="f92ad-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="f92ad-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="f92ad-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="f92ad-124">glTF</span><span class="sxs-lookup"><span data-stu-id="f92ad-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="f92ad-125">Groupe de communauté Web immersif</span><span class="sxs-lookup"><span data-stu-id="f92ad-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)