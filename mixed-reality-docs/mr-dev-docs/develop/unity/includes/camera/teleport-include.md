---
ms.openlocfilehash: 879d8083f832e716389e4b4598aa0fffe6930ff1c06d7a07fe9e4dacc98e7937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212309"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK fournit un [système](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) de télétentative intégré qui fonctionne automatiquement sur des mains et des contrôleurs articulés.

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.
si vous choisissez de ne pas utiliser MRTK, unity fournit une implémentation de téléportage dans le [Shared Computer Toolkit d’Interaction XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo. En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place. Il s’agit de l’équivalent du PlaySpace de MRTK.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.
Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo. En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place. Il s’agit de l’équivalent du PlaySpace de MRTK.