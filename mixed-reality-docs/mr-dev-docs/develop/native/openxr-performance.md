---
title: Performances OpenXR
description: Déboguez les performances du GPU pour vos applications OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, native, application native, moteur personnalisé, intergiciel, performances, optimisation, débogage GPU, RenderDoc, PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613173"
---
# <a name="openxr-performance"></a><span data-ttu-id="3c567-104">Performances OpenXR</span><span class="sxs-lookup"><span data-stu-id="3c567-104">OpenXR performance</span></span>

<span data-ttu-id="3c567-105">Sur HoloLens 2, il existe plusieurs façons d’envoyer des données de composition par `xrEndFrame` le biais de, ce qui peut entraîner des pénalités en matière de performances et de traitement.</span><span class="sxs-lookup"><span data-stu-id="3c567-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>
<span data-ttu-id="3c567-106">Pour éviter de mauvaises performances, [soumettez `XrCompositionProjectionLayer` un seul](openxr-best-practices.md#use-a-single-projection-layer) avec les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c567-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="3c567-107">Utiliser un tableau de textures utilise permutation</span><span class="sxs-lookup"><span data-stu-id="3c567-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="3c567-108">Utiliser le format utilise permutation de couleurs primaires</span><span class="sxs-lookup"><span data-stu-id="3c567-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="3c567-109">Utiliser les dimensions de la vue recommandée</span><span class="sxs-lookup"><span data-stu-id="3c567-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="3c567-110">Ne pas définir l' `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` indicateur</span><span class="sxs-lookup"><span data-stu-id="3c567-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="3c567-111">Définir `XrCompositionLayerDepthInfoKHR` `minDepth` sur 0.0 f et `maxDepth` sur 1.0 f</span><span class="sxs-lookup"><span data-stu-id="3c567-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="3c567-112">Pour de meilleures performances, tenez compte des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3c567-112">For better performance, consider:</span></span>
* [<span data-ttu-id="3c567-113">Utilisation du format de profondeur 16 bits</span><span class="sxs-lookup"><span data-stu-id="3c567-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="3c567-114">Effectuer des appels de dessin instanciés</span><span class="sxs-lookup"><span data-stu-id="3c567-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
