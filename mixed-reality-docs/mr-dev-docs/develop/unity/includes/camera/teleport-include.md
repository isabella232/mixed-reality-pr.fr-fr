---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636295"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK fournit un [système](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) de télétentative intégré qui fonctionne automatiquement sur des mains et des contrôleurs articulés.

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.
Si vous choisissez de ne pas utiliser MRTK, Unity fournit une implémentation de téléportage dans le [Kit d’outils d’interaction XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo. En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place. Il s’agit de l’équivalent du PlaySpace de MRTK.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.
Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo. En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place. Il s’agit de l’équivalent du PlaySpace de MRTK.