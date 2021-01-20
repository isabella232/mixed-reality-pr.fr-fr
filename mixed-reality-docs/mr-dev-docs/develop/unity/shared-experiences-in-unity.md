---
title: Expériences partagées dans Unity
description: Apprenez à partager les mêmes hologrammes entre plusieurs utilisateurs dans une application Unity avec des ancres spatiales Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Partage, ancrer, WorldAnchor, MR partageant 250, WorldAnchorTransferBatch, SpatialPerception, Azure, ancres spatiales Azure, ASA, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 7762a76e1eaa944f69153b13fb0f380c7dce643e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583363"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="8f55f-104">Expériences partagées dans Unity</span><span class="sxs-lookup"><span data-stu-id="8f55f-104">Shared experiences in Unity</span></span>

<span data-ttu-id="8f55f-105">Une expérience partagée permet à plusieurs utilisateurs, chacun avec leur propre appareil HoloLens, iOS ou Android, d’afficher et d’interagir de manière collective avec le même hologramme.</span><span class="sxs-lookup"><span data-stu-id="8f55f-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="8f55f-106">Les hologrammes sont positionnés à un point fixe dans l’espace via le partage d’ancrage spatial.</span><span class="sxs-lookup"><span data-stu-id="8f55f-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="8f55f-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8f55f-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="8f55f-108">Les <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> créent des ancres spatiales durables sur le Cloud, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="8f55f-108"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="8f55f-109">En partageant une ancre spatiale commune sur plusieurs appareils, chaque utilisateur peut voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.</span><span class="sxs-lookup"><span data-stu-id="8f55f-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="8f55f-110">Vous pouvez également utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour la persistance des hologrammes asynchrones sur les appareils HoloLens, iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="8f55f-110">You can also use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="8f55f-111">En partageant une ancre spatiale Cloud durable, plusieurs appareils peuvent observer le même hologramme persistant dans le temps, même si ces appareils ne sont pas présents simultanément.</span><span class="sxs-lookup"><span data-stu-id="8f55f-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="8f55f-112">Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="8f55f-112">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="8f55f-113">Une fois les ancres spatiales Azure configurées, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="8f55f-113">Once Azure Spatial Anchors is set up, you can <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="8f55f-114">Transferts d’ancrage locaux</span><span class="sxs-lookup"><span data-stu-id="8f55f-114">Local anchor transfers</span></span>

<span data-ttu-id="8f55f-115">Dans les situations où vous ne pouvez pas utiliser d’ancres spatiales Azure, les [transferts d’ancrage locaux](../../out-of-scope/local-anchor-transfers-in-unity.md) permettent à un appareil HoloLens d’exporter une ancre afin qu’un second HoloLens puisse l’importer.</span><span class="sxs-lookup"><span data-stu-id="8f55f-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="8f55f-116">Cette approche n’est pas prise en charge sur les appareils iOS et Android, et fournit un rappel d’ancrage moins fiable que les ancres spatiales Azure.</span><span class="sxs-lookup"><span data-stu-id="8f55f-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="8f55f-117">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="8f55f-117">Next Development Checkpoint</span></span>

<span data-ttu-id="8f55f-118">Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des fonctionnalités de la plateforme de réalité mixte et des API.</span><span class="sxs-lookup"><span data-stu-id="8f55f-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="8f55f-119">À partir de là, vous pouvez passer à la section suivante :</span><span class="sxs-lookup"><span data-stu-id="8f55f-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f55f-120">Appareil photo localisable</span><span class="sxs-lookup"><span data-stu-id="8f55f-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="8f55f-121">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="8f55f-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f55f-122">Déployer sur HoloLens ou sur des casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8f55f-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="8f55f-123">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#3-advanced-features) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="8f55f-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f55f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f55f-124">See also</span></span>
* [<span data-ttu-id="8f55f-125">Expériences partagées dans Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8f55f-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="8f55f-126"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="8f55f-126"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="8f55f-127"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a></span><span class="sxs-lookup"><span data-stu-id="8f55f-127"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>