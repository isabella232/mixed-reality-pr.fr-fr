---
title: Ancres spatiales dans Unity
description: Découvrez comment créer, stocker et récupérer des ancres spatiales dans des applications de réalité mixte Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, ancres spatiales, magasin d’ancrage, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623619"
---
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="59095-104">Ancres spatiales dans Unity</span><span class="sxs-lookup"><span data-stu-id="59095-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="59095-105">Les ancres spatiales enregistrent les hologrammes dans un espace réel entre les sessions d’application.</span><span class="sxs-lookup"><span data-stu-id="59095-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="59095-106">Une fois enregistrées dans le magasin d’ancres HoloLens, elles peuvent être recherchées et chargées dans différentes sessions et constituent une solution de secours idéale en l’absence de connectivité Internet.</span><span class="sxs-lookup"><span data-stu-id="59095-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59095-107">Les ancres locales sont stockées sur l’appareil, alors que les ancres spatiales Azure sont stockées dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="59095-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="59095-108">Si vous envisagez d’utiliser les services cloud Azure pour stocker vos ancres, nous avons créé un guide qui vous aidera à intégrer [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span><span class="sxs-lookup"><span data-stu-id="59095-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="59095-109">Notez que vous pouvez avoir des ancres locales et Azure dans le même projet sans conflit.</span><span class="sxs-lookup"><span data-stu-id="59095-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="59095-110">Comprendre les points d’ancrage</span><span class="sxs-lookup"><span data-stu-id="59095-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="59095-111">Utilisation de AnchorStore</span><span class="sxs-lookup"><span data-stu-id="59095-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="59095-112">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="59095-112">Next Development Checkpoint</span></span>

<span data-ttu-id="59095-113">Si vous suivez le parcours du point de contrôle de développement Unity que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="59095-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="59095-114">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="59095-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="59095-115">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="59095-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="59095-116">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="59095-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="59095-117">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="59095-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="59095-118">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="59095-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="59095-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59095-119">See Also</span></span>
* [<span data-ttu-id="59095-120">Persistance d’ancrage spatial</span><span class="sxs-lookup"><span data-stu-id="59095-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="59095-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="59095-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="59095-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a></span><span class="sxs-lookup"><span data-stu-id="59095-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="59095-123">Échelle de l’expérience</span><span class="sxs-lookup"><span data-stu-id="59095-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="59095-124">Étape spatiale</span><span class="sxs-lookup"><span data-stu-id="59095-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="59095-125">Suivi des pertes dans Unity</span><span class="sxs-lookup"><span data-stu-id="59095-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="59095-126">Ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="59095-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="59095-127">Expériences partagées dans Unity</span><span class="sxs-lookup"><span data-stu-id="59095-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)