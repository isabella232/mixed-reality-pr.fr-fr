---
title: Performances OpenXR
description: Découvrez comment déboguer les performances du GPU de vos applications de réalité mixte OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, native, application native, moteur personnalisé, intergiciel, performances, optimisation, débogage GPU, RenderDoc, PIX
ms.openlocfilehash: f4462da954a3b6093e47f03e75b460671e7638f406b761ad6e05689ab97b3ddc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213173"
---
# <a name="openxr-performance"></a>Performances OpenXR

sur HoloLens 2, il existe plusieurs façons d’envoyer des données de composition par `xrEndFrame` le biais de, ce qui peut entraîner des pénalités en matière de performances et de traitement.

Pour éviter de mauvaises performances, [soumettez `XrCompositionProjectionLayer` un seul](openxr-best-practices.md#use-a-single-projection-layer) avec les caractéristiques suivantes :

* [Utiliser un tableau de textures utilise permutation](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Utiliser le format utilise permutation de couleurs primaires](openxr-best-practices.md#select-a-swapchain-format)
* [Utiliser les dimensions de la vue recommandée](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Ne pas définir l' `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` indicateur
* Définir `XrCompositionLayerDepthInfoKHR` `minDepth` sur 0.0 f et `maxDepth` sur 1.0 f

Pour de meilleures performances, tenez compte des éléments suivants :

* [Utilisation du format de profondeur 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Effectuer des appels de dessin instanciés](openxr-best-practices.md#render-with-texture-array-and-vprt)
