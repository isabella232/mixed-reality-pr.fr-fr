---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636293"
---
# <a name="mrtk"></a>[<span data-ttu-id="21bf6-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="21bf6-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="21bf6-102">MRTK ne possède pas actuellement d’assistance pour le mode de reprojection.</span><span class="sxs-lookup"><span data-stu-id="21bf6-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="21bf6-103">Pour plus d’informations, consultez l’un des autres onglets.</span><span class="sxs-lookup"><span data-stu-id="21bf6-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="21bf6-104">Kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="21bf6-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="21bf6-105">Le mode de reprojection peut être configuré en définissant [XRDisplaySubsystem. reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) sur la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="21bf6-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="21bf6-106">Par exemple, si vous créez une [expérience d’orientation uniquement](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) avec du contenu verrouillé rigidement (par exemple, du contenu vidéo de 360 degrés), vous pouvez définir explicitement le mode de reprojection sur orientation uniquement en lui affectant la valeur [ReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="21bf6-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="21bf6-107">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="21bf6-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="21bf6-108">Le mode de reprojection peut être configuré en définissant [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) sur la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="21bf6-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="21bf6-109">Par exemple, si vous créez une [expérience d’orientation uniquement](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) avec du contenu verrouillé rigidement (par exemple, du contenu vidéo de 360 degrés), vous pouvez définir explicitement le mode de reprojection sur orientation uniquement en lui affectant la valeur [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="21bf6-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>