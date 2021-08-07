---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212308"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK ne possède pas actuellement d’assistance pour le mode de reprojection. Pour plus d’informations, consultez l’un des autres onglets.

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Le mode de reprojection peut être configuré en définissant [XRDisplaySubsystem. reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) sur la valeur appropriée.

Par exemple, si vous créez une [expérience d’orientation uniquement](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) avec du contenu verrouillé rigidement (par exemple, du contenu vidéo de 360 degrés), vous pouvez définir explicitement le mode de reprojection sur orientation uniquement en lui affectant la valeur [ReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Le mode de reprojection peut être configuré en définissant [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) sur la valeur appropriée.

Par exemple, si vous créez une [expérience d’orientation uniquement](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) avec du contenu verrouillé rigidement (par exemple, du contenu vidéo de 360 degrés), vous pouvez définir explicitement le mode de reprojection sur orientation uniquement en lui affectant la valeur [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).