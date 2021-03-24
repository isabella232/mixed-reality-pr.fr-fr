---
title: Présentation de WebVR
description: Découvrez les principes de base de l’utilisation et du développement d’applications WebVR s’exécutant sur des casques immersifs Windows Mixed Reality.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 vidéos, 360 photo, 360 photos, 360 content, Internet immersif, immersiveweb, IW
ROBOTS: NOINDEX
ms.openlocfilehash: dba3ca6b0cb9404f488db0b69a5bd89d6093a3ef
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909029"
---
# <a name="webvr-overview"></a><span data-ttu-id="6c48d-104">Présentation de WebVR</span><span class="sxs-lookup"><span data-stu-id="6c48d-104">WebVR Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c48d-105">Les **API WebVR 1,1** sont dépréciées et remplacées par les **API d’appareil WebXR**.</span><span class="sxs-lookup"><span data-stu-id="6c48d-105">**WebVR 1.1 API** s are deprecated and replaced by **WebXR Device API** s.</span></span>

<span data-ttu-id="6c48d-106">Les API WebVR 1,1 sont déconseillées et supprimées du chrome et du nouveau Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="6c48d-106">WebVR 1.1 APIs are deprecated and removed from Chrome and the new Microsoft Edge.</span></span> <span data-ttu-id="6c48d-107">Les API WebVR sont remplacées par les API d’appareil WebXR.</span><span class="sxs-lookup"><span data-stu-id="6c48d-107">WebVR APIs are superseded by WebXR Device APIs.</span></span> <span data-ttu-id="6c48d-108">Vous pouvez consulter la liste des navigateurs qui prennent actuellement en charge les API WebVR sur [caniuse.com](https://caniuse.com/#search=webvr).</span><span class="sxs-lookup"><span data-stu-id="6c48d-108">You can check the list of browsers currently supporting WebVR APIs on [caniuse.com](https://caniuse.com/#search=webvr).</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="6c48d-109">Affichage du contenu WebVR dans les casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6c48d-109">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="6c48d-110">Vous trouverez des instructions sur l’accès au contenu WebVR dans vos casques immersifs avec les **versions antérieures de Microsoft Edge (15-18)** dans le [Guide du passionné](/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="6c48d-110">Instructions for accessing WebVR content in your immersive headsets with **older versions of Microsoft Edge(15-18)** can be found in the [Enthusiast's Guide](/windows/mixed-reality/enthusiast-guide/webvr).</span></span> <span data-ttu-id="6c48d-111">Vous pouvez vérifier votre version Edge en tapant « edge://version/ » dans la barre de recherche des navigateurs de périphérie.</span><span class="sxs-lookup"><span data-stu-id="6c48d-111">You can check your edge version by typing "edge://version/" in your Edge browsers search bar.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c48d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c48d-112">See Also</span></span>

* [<span data-ttu-id="6c48d-113">Présentation de WebXR</span><span class="sxs-lookup"><span data-stu-id="6c48d-113">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="6c48d-114">Spécification de l’API d’appareil WebXR</span><span class="sxs-lookup"><span data-stu-id="6c48d-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="6c48d-115">Windows Mixed Reality et le nouveau Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6c48d-115">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge)
* [<span data-ttu-id="6c48d-116">Informations WebVR</span><span class="sxs-lookup"><span data-stu-id="6c48d-116">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="6c48d-117">Spécification WebVR</span><span class="sxs-lookup"><span data-stu-id="6c48d-117">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="6c48d-118">[API WebVR](/previous-versions//mt806281(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6c48d-118">[WebVR API](/previous-versions//mt806281(v=vs.85))</span></span>
* <span data-ttu-id="6c48d-119">[API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6c48d-119">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="6c48d-120">[API du boîtier de manette](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) et les [extensions de boîtier](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="6c48d-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="6c48d-121">Gestion du contexte perdu dans WebGL</span><span class="sxs-lookup"><span data-stu-id="6c48d-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="6c48d-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="6c48d-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="6c48d-123">glTF</span><span class="sxs-lookup"><span data-stu-id="6c48d-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="6c48d-124">Utilisation de Babylon.js pour activer WebVR</span><span class="sxs-lookup"><span data-stu-id="6c48d-124">Using Babylon.js to enable WebVR</span></span>](/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)