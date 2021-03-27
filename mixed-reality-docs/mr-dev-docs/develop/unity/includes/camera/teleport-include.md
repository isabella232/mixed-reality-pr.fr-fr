---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636295"
---
# <a name="mrtk"></a>[<span data-ttu-id="589bb-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="589bb-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="589bb-102">MRTK fournit un [système](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) de télétentative intégré qui fonctionne automatiquement sur des mains et des contrôleurs articulés.</span><span class="sxs-lookup"><span data-stu-id="589bb-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="589bb-103">Kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="589bb-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="589bb-104">Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589bb-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="589bb-105">Si vous choisissez de ne pas utiliser MRTK, Unity fournit une implémentation de téléportage dans le [Kit d’outils d’interaction XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span><span class="sxs-lookup"><span data-stu-id="589bb-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="589bb-106">Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="589bb-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="589bb-107">En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place.</span><span class="sxs-lookup"><span data-stu-id="589bb-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="589bb-108">Il s’agit de l’équivalent du PlaySpace de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589bb-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="589bb-109">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="589bb-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="589bb-110">Nous vous recommandons d’utiliser l’implémentation de téléportation de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589bb-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="589bb-111">Si vous choisissez d’implémenter les vôtres, il est judicieux de garder à l’esprit que vous ne pouvez pas déplacer directement l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="589bb-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="589bb-112">En raison du contrôle de la caméra de l’appareil photo pour le suivi des têtes, vous devez lui attribuer un parent dans la hiérarchie et déplacer ce GameObject à la place.</span><span class="sxs-lookup"><span data-stu-id="589bb-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="589bb-113">Il s’agit de l’équivalent du PlaySpace de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589bb-113">This is the equivalent of MRTK's Playspace.</span></span>