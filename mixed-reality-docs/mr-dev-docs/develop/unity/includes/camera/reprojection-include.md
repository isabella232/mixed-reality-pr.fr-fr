---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636293"
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