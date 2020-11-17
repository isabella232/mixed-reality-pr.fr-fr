---
title: Expériences partagées dans Unity
description: Partager les mêmes hologrammes entre plusieurs utilisateurs dans une application Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Partage, ancrer, WorldAnchor, MR partageant 250, WorldAnchorTransferBatch, SpatialPerception, Azure, ancres spatiales Azure, ASA, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: c9f432a2ef26e28a2329f9fd191f680a4148ca7e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678458"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="87fcd-104">Expériences partagées dans Unity</span><span class="sxs-lookup"><span data-stu-id="87fcd-104">Shared experiences in Unity</span></span>

<span data-ttu-id="87fcd-105">Une expérience partagée est celle où plusieurs utilisateurs, chacun disposant de leurs propres appareils HoloLens, iOS ou Android, affichent et interagissent collectivement avec le même hologramme, qui est positionné à un point fixe dans l’espace.</span><span class="sxs-lookup"><span data-stu-id="87fcd-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="87fcd-106">Pour ce faire, vous devez utiliser le partage d’ancrage spatial.</span><span class="sxs-lookup"><span data-stu-id="87fcd-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="87fcd-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="87fcd-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="87fcd-108">Vous pouvez utiliser des <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer des ancres spatiales durables dans le Cloud, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="87fcd-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="87fcd-109">En partageant une ancre spatiale commune sur plusieurs appareils, chaque utilisateur peut voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.</span><span class="sxs-lookup"><span data-stu-id="87fcd-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="87fcd-110">Cette technique autorise les expériences partagées en temps réel.</span><span class="sxs-lookup"><span data-stu-id="87fcd-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="87fcd-111">Vous pouvez également utiliser <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> pour la persistance asynchrone des hologrammes sur les appareils HoloLens, iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="87fcd-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="87fcd-112">En partageant une ancre spatiale cloud durable, plusieurs appareils peuvent observer le même hologramme conservé au fil du temps, même si ces appareils ne sont pas présents ensemble en même temps.</span><span class="sxs-lookup"><span data-stu-id="87fcd-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="87fcd-113">Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="87fcd-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="87fcd-114">Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="87fcd-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="87fcd-115">Transferts d’ancrage locaux</span><span class="sxs-lookup"><span data-stu-id="87fcd-115">Local anchor transfers</span></span>

<span data-ttu-id="87fcd-116">Dans les situations où vous ne pouvez pas utiliser les ancres spatiales Azure, les [transferts d’ancrage locaux](../../out-of-scope/local-anchor-transfers-in-unity.md) permettent à un appareil hololens d’exporter une ancre à importer par un deuxième appareil hololens.</span><span class="sxs-lookup"><span data-stu-id="87fcd-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="87fcd-117">Notez que cette approche offre un rappel d’ancrage moins fiable que les ancres spatiales Azure, et les appareils iOS et Android ne sont pas pris en charge par cette approche.</span><span class="sxs-lookup"><span data-stu-id="87fcd-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="87fcd-118">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="87fcd-118">Next Development Checkpoint</span></span>

<span data-ttu-id="87fcd-119">Si vous suivez le parcours du point de contrôle de développement Unity que nous avons disposé, vous êtes en train d’explorer les fonctionnalités de la plateforme de réalité mixte et les API.</span><span class="sxs-lookup"><span data-stu-id="87fcd-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="87fcd-120">À partir de là, vous pouvez passer à la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="87fcd-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87fcd-121">Appareil photo localisable</span><span class="sxs-lookup"><span data-stu-id="87fcd-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="87fcd-122">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="87fcd-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87fcd-123">Déployer sur HoloLens ou sur des casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="87fcd-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="87fcd-124">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#3-platform-capabilities-and-apis) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="87fcd-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="87fcd-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87fcd-125">See also</span></span>
* [<span data-ttu-id="87fcd-126">Expériences partagées dans Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="87fcd-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="87fcd-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="87fcd-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="87fcd-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a></span><span class="sxs-lookup"><span data-stu-id="87fcd-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
