---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748474"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK fournit un [système](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) de télétentative intégré qui fonctionne automatiquement sur des mains et des contrôleurs articulés.

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.
Si vous choisissez de ne pas utiliser MRTK, Unity fournit une implémentation de téléportage dans le [Kit d’outils d’interaction XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo. En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place. Il s’agit de l’équivalent du PlaySpace de MRTK.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.
Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo. En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place. Il s’agit de l’équivalent du PlaySpace de MRTK.