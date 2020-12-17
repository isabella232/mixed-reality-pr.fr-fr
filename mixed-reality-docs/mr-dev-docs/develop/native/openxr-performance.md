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
# <a name="openxr-performance"></a>Performances OpenXR

Sur HoloLens 2, il existe plusieurs façons d’envoyer des données de composition par `xrEndFrame` le biais de, ce qui peut entraîner des pénalités en matière de performances et de traitement.
Pour éviter de mauvaises performances, [soumettez `XrCompositionProjectionLayer` un seul](openxr-best-practices.md#use-a-single-projection-layer) avec les caractéristiques suivantes :
* [Utiliser un tableau de textures utilise permutation](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Utiliser le format utilise permutation de couleurs primaires](openxr-best-practices.md#select-a-swapchain-format)
* [Utiliser les dimensions de la vue recommandée](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Ne pas définir l' `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` indicateur
* Définir `XrCompositionLayerDepthInfoKHR` `minDepth` sur 0.0 f et `maxDepth` sur 1.0 f

Pour de meilleures performances, tenez compte des éléments suivants :
* [Utilisation du format de profondeur 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Effectuer des appels de dessin instanciés](openxr-best-practices.md#render-with-texture-array-and-vprt)
