---
title: Visualisation du balayage d’une pièce
description: Les applications qui requièrent le mappage spatial utilisent l’appareil pour collecter des données dans le temps et entre les sessions.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, modèles d’application, conception, HoloLens, Scan Room, mappage spatial, maille, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143614"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="31657-104">Visualisation du balayage d’une pièce</span><span class="sxs-lookup"><span data-stu-id="31657-104">Room scan visualization</span></span>

<span data-ttu-id="31657-105">Les applications qui requièrent un mappage spatial s’appuient sur l’appareil pour collecter des données au fil du temps et entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="31657-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="31657-106">L’exhaustivité et la qualité des données de mappage dépendent de nombreux facteurs, notamment la quantité d’exploration effectuée par l’utilisateur, le temps écoulé depuis l’exploration et si les objets tels que les meubles et les portes ont été déplacés depuis que l’appareil a analysé la zone.</span><span class="sxs-lookup"><span data-stu-id="31657-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="31657-107">Pour garantir l’utilité des données de mappage spatiale, les développeurs d’applications disposent de plusieurs options :</span><span class="sxs-lookup"><span data-stu-id="31657-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="31657-108">S’appuyer sur ce qui a déjà été collecté.</span><span class="sxs-lookup"><span data-stu-id="31657-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="31657-109">Ces données peuvent être incomplètes au départ.</span><span class="sxs-lookup"><span data-stu-id="31657-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="31657-110">Demandez à l’utilisateur d’utiliser le geste fleuri pour accéder à la page d’hébergement Windows Mixed Reality, puis explorez la zone qu’il souhaite utiliser pour l’expérience.</span><span class="sxs-lookup"><span data-stu-id="31657-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="31657-111">Ils peuvent utiliser l’utilisation de l’air pour confirmer que toutes les zones nécessaires sont connues de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="31657-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="31657-112">Créez une expérience d’exploration personnalisée dans leur propre application.</span><span class="sxs-lookup"><span data-stu-id="31657-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="31657-113">Dans tous ces cas, les données réelles recueillies lors de l’exploration sont stockées par le système et l’application n’a pas besoin de le faire.</span><span class="sxs-lookup"><span data-stu-id="31657-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="31657-114">Si vous souhaitez voir la visualisation de l’analyse de la salle en action, consultez notre démonstration [conception d’hologrammes-spatiales de sensibilisation]() ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="31657-114">If you'd like to see room scan visualization in action, check out our [Designing Holograms - Spatial Awareness]() video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="device-support"></a><span data-ttu-id="31657-115">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="31657-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31657-116"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="31657-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="31657-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31657-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31657-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="31657-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31657-119">Visualisation du balayage d’une pièce</span><span class="sxs-lookup"><span data-stu-id="31657-119">Room scan visualization</span></span></td>
        <td><span data-ttu-id="31657-120">✔️</span><span class="sxs-lookup"><span data-stu-id="31657-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="31657-121">Création d’une expérience d’analyse personnalisée</span><span class="sxs-lookup"><span data-stu-id="31657-121">Building a custom scanning experience</span></span>

<span data-ttu-id="31657-122">Les applications peuvent analyser les données de mappage spatiale au début de l’expérience afin de déterminer si elles souhaitent que l’utilisateur effectue des étapes supplémentaires pour améliorer son exhaustivité et sa qualité.</span><span class="sxs-lookup"><span data-stu-id="31657-122">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="31657-123">Si l’analyse indique que la qualité doit être améliorée, les développeurs doivent fournir une visualisation à superposer au monde pour indiquer :</span><span class="sxs-lookup"><span data-stu-id="31657-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="31657-124">La quantité totale de volume total des utilisateurs avoisinants doit faire partie de l’expérience</span><span class="sxs-lookup"><span data-stu-id="31657-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="31657-125">Emplacement où l’utilisateur doit accéder à l’amélioration des données</span><span class="sxs-lookup"><span data-stu-id="31657-125">Where the user should go to improve data</span></span>

<span data-ttu-id="31657-126">Les utilisateurs ne savent pas ce qui effectue une « bonne » analyse.</span><span class="sxs-lookup"><span data-stu-id="31657-126">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="31657-127">Ils doivent être affichés ou informés des éléments à rechercher s’ils sont invités à évaluer une analyse, à la distance, à la distance par rapport aux murs réels, etc.</span><span class="sxs-lookup"><span data-stu-id="31657-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="31657-128">Le développeur doit implémenter une boucle de commentaires qui comprend l’actualisation des données de mappage spatiale pendant la phase d’analyse ou d’exploration.</span><span class="sxs-lookup"><span data-stu-id="31657-128">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="31657-129">Dans de nombreux cas, il est préférable d’indiquer à l’utilisateur ce qu’il doit faire pour obtenir la qualité d’analyse nécessaire.</span><span class="sxs-lookup"><span data-stu-id="31657-129">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="31657-130">Par exemple, Regardez le plafond, regardez derrière le mobilier, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="31657-130">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="31657-131">Mise en cache et mappage spatial continu</span><span class="sxs-lookup"><span data-stu-id="31657-131">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="31657-132">Les données de mappage spatiale sont les applications de source de données les plus lourdes pouvant être consommées.</span><span class="sxs-lookup"><span data-stu-id="31657-132">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="31657-133">Pour éviter des problèmes de performances, tels que des images ignorées ou des interruptions, la consommation de ces données doit être effectuée avec précaution.</span><span class="sxs-lookup"><span data-stu-id="31657-133">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="31657-134">L’analyse active au cours d’une expérience peut être à la fois bénéfique et néfaste. vous devrez donc décider de la méthode à utiliser en fonction de l’expérience.</span><span class="sxs-lookup"><span data-stu-id="31657-134">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="31657-135">Mappage spatial mis en cache</span><span class="sxs-lookup"><span data-stu-id="31657-135">Cached spatial mapping</span></span>

<span data-ttu-id="31657-136">Si des données de mappage spatiale sont mises en cache, l’application prend généralement un instantané des données de mappage spatiale et utilise cet instantané pendant l’expérience.</span><span class="sxs-lookup"><span data-stu-id="31657-136">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="31657-137">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="31657-137">**Benefits**</span></span>
* <span data-ttu-id="31657-138">Réduction de la surcharge sur le système pendant que l’expérience s’exécute et entraîne des gains de performances spectaculaires en matière d’alimentation, de température et d’UC.</span><span class="sxs-lookup"><span data-stu-id="31657-138">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="31657-139">Une implémentation plus simple de l’expérience principale, car elle n’est pas interrompue par les modifications apportées aux données spatiales.</span><span class="sxs-lookup"><span data-stu-id="31657-139">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="31657-140">Un coût unique à un moment donné sur tout traitement de la publication des données spatiales à des fins physiques, graphiques et autres.</span><span class="sxs-lookup"><span data-stu-id="31657-140">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="31657-141">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="31657-141">**Drawbacks**</span></span>
* <span data-ttu-id="31657-142">Le déplacement d’objets ou de personnes réels n’est pas reflété par les données mises en cache.</span><span class="sxs-lookup"><span data-stu-id="31657-142">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="31657-143">par exemple, l’application peut considérer une porte ouverte lorsqu’elle est maintenant fermée.</span><span class="sxs-lookup"><span data-stu-id="31657-143">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="31657-144">Potentiellement plus de mémoire d’application pour gérer la version mise en cache des données.</span><span class="sxs-lookup"><span data-stu-id="31657-144">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="31657-145">Une bonne casse pour cette méthode est un environnement contrôlé ou un jeu en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="31657-145">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="31657-146">Mappage spatial continu</span><span class="sxs-lookup"><span data-stu-id="31657-146">Continuous spatial mapping</span></span>

<span data-ttu-id="31657-147">Certaines applications peuvent reposer sur poursuivre l’analyse pour actualiser les données de mappage spatiale.</span><span class="sxs-lookup"><span data-stu-id="31657-147">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="31657-148">**Avantages**</span><span class="sxs-lookup"><span data-stu-id="31657-148">**Benefits**</span></span>
* <span data-ttu-id="31657-149">Vous n’avez pas besoin de créer une expérience d’analyse ou d’exploration distincte dans votre application.</span><span class="sxs-lookup"><span data-stu-id="31657-149">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="31657-150">Le déplacement d’objets réels peut être reflété par le jeu, bien qu’avec un certain délai.</span><span class="sxs-lookup"><span data-stu-id="31657-150">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="31657-151">**Inconvénients**</span><span class="sxs-lookup"><span data-stu-id="31657-151">**Drawbacks**</span></span>
* <span data-ttu-id="31657-152">Plus grande complexité dans l’implémentation de l’expérience principale.</span><span class="sxs-lookup"><span data-stu-id="31657-152">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="31657-153">Surcharge potentielle due au graphique supplémentaire et au traitement physique, puisque les modifications doivent être ingérées de manière incrémentielle par ces systèmes.</span><span class="sxs-lookup"><span data-stu-id="31657-153">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="31657-154">Impact plus élevé, thermique et processeur.</span><span class="sxs-lookup"><span data-stu-id="31657-154">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="31657-155">Un bon cas pour cette méthode est celui où les hologrammes sont censés interagir avec les objets mobiles, par exemple, une voiture holographique dont les lecteurs sont susceptibles d’être amenés dans une porte, selon qu’elle est ouverte ou fermée.</span><span class="sxs-lookup"><span data-stu-id="31657-155">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="31657-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31657-156">See also</span></span>

* [<span data-ttu-id="31657-157">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="31657-157">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="31657-158">Systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="31657-158">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="31657-159">Conception du son spatial</span><span class="sxs-lookup"><span data-stu-id="31657-159">Spatial sound design</span></span>](spatial-sound-design.md)