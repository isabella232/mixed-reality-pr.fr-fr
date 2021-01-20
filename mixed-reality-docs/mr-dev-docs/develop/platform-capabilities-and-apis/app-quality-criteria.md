---
title: Critères de qualité des applications
description: Ce document décrit les principaux facteurs qui ont un impact sur la qualité des applications de réalité mixte.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critères de qualité des applications, réalité mixte, application de réalité mixte, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 3f6752c0a15ae7db21be1f4a6d2843339ab28a5c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581266"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="1eeeb-104">Critères de qualité des applications</span><span class="sxs-lookup"><span data-stu-id="1eeeb-104">App quality criteria</span></span>

<span data-ttu-id="1eeeb-105">Ce document décrit les principaux facteurs qui ont un impact sur la qualité des applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="1eeeb-106">Pour chaque facteur, les informations suivantes sont fournies</span><span class="sxs-lookup"><span data-stu-id="1eeeb-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="1eeeb-107">Vue d’ensemble : brève description du facteur de qualité et de la raison pour laquelle il est important.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="1eeeb-108">Impact sur l’appareil : le type de périphérique de la réalité mixte de fenêtre est affecté.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="1eeeb-109">Critères de qualité : comment évaluer le facteur de qualité.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="1eeeb-110">Comment mesurer : méthodes pour mesurer (ou expérimenter) le problème.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="1eeeb-111">Recommandations : Résumé des approches pour offrir une meilleure expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="1eeeb-112">Ressources : ressources de conception et de développement pertinentes qui sont utiles pour créer de meilleures expériences d’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="1eeeb-113">Fréquence d’images</span><span class="sxs-lookup"><span data-stu-id="1eeeb-113">Frame rate</span></span>

<span data-ttu-id="1eeeb-114">La fréquence d’images est le premier pilier de la stabilité de l’hologramme et du confort de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="1eeeb-115">La fréquence d’images en dessous des cibles recommandées peut provoquer l’apparition d’hologrammes, ce qui a un impact négatif sur la qualité de l’expérience et éventuellement une fatigue oculaire.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="1eeeb-116">La fréquence d’images cible pour votre expérience sur les casques immersifs Windows Mixed Reality est soit 60 Hz, soit 90 Hz selon les PC compatibles Windows Mixed Reality que vous prenez en charge.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="1eeeb-117">Pour HoloLens, la fréquence d’images cible est de 60 Hz.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-118">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-121">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-121">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-122">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-123">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-123">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-124">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-124">Best</span></span>  |  <span data-ttu-id="1eeeb-125">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-125">Meets</span></span> |  <span data-ttu-id="1eeeb-126">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="1eeeb-127">L’application répond régulièrement à l’objectif des images par seconde (FPS) pour l’appareil cible : 60 fps sur HoloLens ; 90 fps sur ultra PC ; et 60 fps sur les PC standard.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="1eeeb-128">L’application a des chutes de trames intermittentes qui n’entravent pas l’expérience de base, ou FPS est toujours plus faible que l’objectif souhaité, mais n’empêche pas l’expérience de l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="1eeeb-129">L’application rencontre une baisse de la fréquence d’images en moyenne toutes les 10 secondes ou moins.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-130">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-130">How to measure</span></span>

* <span data-ttu-id="1eeeb-131">Un graphique de fréquence d’images en temps réel est fourni par le biais du [portail d’appareils Windows](using-the-windows-device-portal.md#system-performance) sous « performances système ».</span><span class="sxs-lookup"><span data-stu-id="1eeeb-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="1eeeb-132">Pour le débogage de développement, ajoutez un compteur de diagnostic de fréquence d’images dans l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="1eeeb-133">Consultez ressources pour obtenir un exemple de compteur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="1eeeb-134">Les chutes de fréquence d’images peuvent être rencontrées dans l’appareil pendant que l’application est en cours d’exécution en déplaçant votre tête d’un côté à l’autre.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="1eeeb-135">Si l’hologramme présente un mouvement instable inattendue, la fréquence d’images faible ou le plan de stabilité est probablement la cause.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-136">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-136">Recommendations</span></span>

* <span data-ttu-id="1eeeb-137">Ajoutez un compteur de fréquence d’images au début du travail de développement.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="1eeeb-138">Les modifications qui entraînent une chute de la fréquence d’images doivent être évaluées et résolues de manière appropriée en tant que bogue de performance.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-139">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-140">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-140">Documentation</span></span>

* [<span data-ttu-id="1eeeb-141">Comprendre les performances de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="1eeeb-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="1eeeb-142">Stabilité et fréquence d’hologramme</span><span class="sxs-lookup"><span data-stu-id="1eeeb-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="1eeeb-143">Budget des performances des actifs</span><span class="sxs-lookup"><span data-stu-id="1eeeb-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="1eeeb-144">Recommandations de performances pour Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1eeeb-145">Outils et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-145">Tools and tutorials</span></span>

* [<span data-ttu-id="1eeeb-146">Boîte à outils de réalité mixte, affichage du compteur FPS</span><span class="sxs-lookup"><span data-stu-id="1eeeb-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="1eeeb-147">Boîte à outils de réalité mixte, nuanceurs</span><span class="sxs-lookup"><span data-stu-id="1eeeb-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="1eeeb-148">Références externes</span><span class="sxs-lookup"><span data-stu-id="1eeeb-148">External references</span></span>

* [<span data-ttu-id="1eeeb-149">Unity, optimisation des applications mobiles</span><span class="sxs-lookup"><span data-stu-id="1eeeb-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="1eeeb-150">Stabilité des hologrammes</span><span class="sxs-lookup"><span data-stu-id="1eeeb-150">Hologram stability</span></span>

<span data-ttu-id="1eeeb-151">Les hologrammes stables augmenteront la convivialité et l’incroyableté de votre application et créeront une expérience d’affichage plus confortable pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="1eeeb-152">La qualité de la stabilité des hologrammes résulte d’un développement d’applications correct et de la capacité de l’appareil à comprendre (suivre) son environnement.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="1eeeb-153">Alors que la fréquence d’images est le premier pilier de la stabilité, d’autres facteurs peuvent avoir un impact sur la stabilité, notamment :</span><span class="sxs-lookup"><span data-stu-id="1eeeb-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="1eeeb-154">Utilisation du plan de stabilisation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="1eeeb-155">Distance aux ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="1eeeb-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="1eeeb-156">Suivi</span><span class="sxs-lookup"><span data-stu-id="1eeeb-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-157">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-160">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-161">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-161">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-162">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-162">Best</span></span>  |  <span data-ttu-id="1eeeb-163">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-163">Meets</span></span> |  <span data-ttu-id="1eeeb-164">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-165">Les hologrammes semblent constamment stables.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="1eeeb-166">Le contenu secondaire montre un mouvement inattendu. ou un mouvement inattendu ne fait pas obstacle à l’expérience globale de l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="1eeeb-167">Le contenu principal du frame montre un mouvement inattendu.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-168">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-168">How to measure</span></span>

<span data-ttu-id="1eeeb-169">Lors de l’usure de l’appareil et de l’affichage de l’expérience :</span><span class="sxs-lookup"><span data-stu-id="1eeeb-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="1eeeb-170">Déplacez votre tête d’un côté à l’autre.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-170">Move your head from side to side.</span></span> <span data-ttu-id="1eeeb-171">Si les hologrammes indiquent un mouvement inattendu, une fréquence d’images faible ou un alignement incorrect du plan de stabilité vers le plan focal est probablement la cause probable.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="1eeeb-172">Déplacez-vous autour des hologrammes et de l’environnement, recherchez des comportements tels que natation et jumpiness.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="1eeeb-173">Ce type de mouvement est probablement dû au fait que l’appareil n’effectue pas le suivi de l’environnement ou à la distance vers l’ancrage spatial.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="1eeeb-174">Si un grand nombre ou plusieurs hologrammes se trouvent dans le cadre, observez le comportement de l’hologramme à différentes profondes tout en déplaçant la position de votre tête d’un côté à l’autre, si shakiness apparaît que cela est probablement dû au plan de stabilisation.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-175">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-175">Recommendations</span></span>

* <span data-ttu-id="1eeeb-176">Ajoutez un compteur de fréquence d’images au début du travail de développement.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="1eeeb-177">Utilisez le plan de stabilisation.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="1eeeb-178">Affichez toujours les hologrammes ancrés dans les 3 mètres de leur ancrage.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="1eeeb-179">Assurez-vous que votre environnement est configuré pour un suivi correct.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="1eeeb-180">Concevez votre expérience afin d’éviter les hologrammes à différents niveaux de profondeur focale dans le cadre.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-181">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-182">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-182">Documentation</span></span>

* [<span data-ttu-id="1eeeb-183">Stabilité et fréquence d’hologramme</span><span class="sxs-lookup"><span data-stu-id="1eeeb-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="1eeeb-184">Étude de cas, à l’aide du plan de stabilisation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="1eeeb-185">Comprendre les performances de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="1eeeb-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="1eeeb-186">Recommandations de performances pour Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="1eeeb-187">Ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="1eeeb-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="1eeeb-188">Gestion des erreurs de suivi</span><span class="sxs-lookup"><span data-stu-id="1eeeb-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="1eeeb-189">Cadre de référence stationnaire</span><span class="sxs-lookup"><span data-stu-id="1eeeb-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1eeeb-190">Outils et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-190">Tools and tutorials</span></span>

* [<span data-ttu-id="1eeeb-191">Kit de complément MR, IPD Kinect</span><span class="sxs-lookup"><span data-stu-id="1eeeb-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="1eeeb-192">Position des hologrammes sur les surfaces réelles</span><span class="sxs-lookup"><span data-stu-id="1eeeb-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="1eeeb-193">Les mauvais alignements d’hologrammes avec des objets physiques (s’ils sont destinés à être placés les uns par rapport aux autres) sont une indication claire de l’absence d’Union des hologrammes et du monde réel.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="1eeeb-194">La précision de la position doit être relative aux besoins du scénario ; par exemple, le positionnement de surface général peut utiliser la carte spatiale, mais un positionnement plus précis nécessitera l’utilisation de marqueurs et d’étalonnage.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-195">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-198">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-199">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-199">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-200">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-200">Best</span></span>  |  <span data-ttu-id="1eeeb-201">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-201">Meets</span></span> |  <span data-ttu-id="1eeeb-202">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="1eeeb-203">Les hologrammes s’alignent sur la surface généralement dans la plage de centimètres en pouces.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="1eeeb-204">Si vous avez besoin de plus de précision, l’application doit fournir un moyen efficace de collaboration dans les spécifications de l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="1eeeb-205">NA</span><span class="sxs-lookup"><span data-stu-id="1eeeb-205">NA</span></span> | <span data-ttu-id="1eeeb-206">Les hologrammes apparaissent non alignés avec l’objet cible physique en rompant le plan de surface ou en s’éloignant de l’aire.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="1eeeb-207">Si la précision est requise, les hologrammes doivent répondre aux spécifications de proximité du scénario.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-208">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-208">How to measure</span></span>

* <span data-ttu-id="1eeeb-209">Les hologrammes placés sur la carte spatiale ne doivent pas sembler très flotter au-dessus ou en dessous de la surface.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="1eeeb-210">Les hologrammes qui nécessitent un placement précis doivent avoir une forme de système de marqueur et de système d’étalonnage qui est précis à l’exigence du scénario.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-211">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-211">Recommendations</span></span>

* <span data-ttu-id="1eeeb-212">La carte spatiale est utile pour placer des objets sur des surfaces lorsque la précision n’est pas requise.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="1eeeb-213">Pour une meilleure précision, utilisez des marqueurs ou des affiches pour définir les hologrammes et un contrôleur Xbox (ou un mécanisme d’alignement manuel) pour l’étalonnage final.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="1eeeb-214">Envisagez de casser des hologrammes très grands en parties logiques et en alignant chaque partie sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="1eeeb-215">La définition incorrecte de la distance interpupillary (IPD) peut également affecter l’alignement de l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="1eeeb-216">Configurez toujours HoloLens sur l’IPD de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-217">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-218">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-218">Documentation</span></span>

* [<span data-ttu-id="1eeeb-219">Positionnement du mappage spatial</span><span class="sxs-lookup"><span data-stu-id="1eeeb-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="1eeeb-220">Processus d’analyse de la salle</span><span class="sxs-lookup"><span data-stu-id="1eeeb-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="1eeeb-221">Meilleures pratiques pour les ancrages spatiaux</span><span class="sxs-lookup"><span data-stu-id="1eeeb-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="1eeeb-222">Gestion des erreurs de suivi</span><span class="sxs-lookup"><span data-stu-id="1eeeb-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="1eeeb-223">Mappage spatial dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="1eeeb-224">Présentation du développement Vuforia</span><span class="sxs-lookup"><span data-stu-id="1eeeb-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1eeeb-225">Outils et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-225">Tools and tutorials</span></span>

* [<span data-ttu-id="1eeeb-226">Boîte à outils MR, bibliothèques de mappage spatiale</span><span class="sxs-lookup"><span data-stu-id="1eeeb-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="1eeeb-227">Kit de complément MR, exemple d’étalonnage d’affiches</span><span class="sxs-lookup"><span data-stu-id="1eeeb-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="1eeeb-228">Kit de complément MR, IPD Kinect</span><span class="sxs-lookup"><span data-stu-id="1eeeb-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="1eeeb-229">Références externes</span><span class="sxs-lookup"><span data-stu-id="1eeeb-229">External references</span></span>

* [<span data-ttu-id="1eeeb-230">Étude de cas Lowes, alignement de précision</span><span class="sxs-lookup"><span data-stu-id="1eeeb-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="1eeeb-231">Affichage de la zone de confort</span><span class="sxs-lookup"><span data-stu-id="1eeeb-231">Viewing zone of comfort</span></span>

<span data-ttu-id="1eeeb-232">Les développeurs d’applications contrôlent l’emplacement des yeux des utilisateurs en plaçant le contenu et les hologrammes à différents niveaux.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="1eeeb-233">Les utilisateurs qui ont le port HoloLens s’adapteront toujours à 2,0 m pour maintenir une image claire, car les affichages HoloLens sont fixés à une distance optique d’environ 2,0 mètres de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="1eeeb-234">Une profondeur de contenu incorrecte peut entraîner une gêne visuelle ou une fatigue.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-235">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-238">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-239">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="1eeeb-240">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="1eeeb-241">Placez le contenu à 2 h.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="1eeeb-242">Lorsque les hologrammes ne peuvent pas être placés à 2 mètres et que les conflits entre la convergence et l’hébergement ne peuvent pas être évités, la zone optimale pour le placement de l’hologramme est comprise entre 1,25 m et 5 mètres.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="1eeeb-243">Dans tous les cas, les concepteurs doivent structurer le contenu pour encourager les utilisateurs à interagir à distance de 1 + m (par exemple, ajuster la taille du contenu et les paramètres de positionnement par défaut).</span><span class="sxs-lookup"><span data-stu-id="1eeeb-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="1eeeb-244">À moins qu’il ne soit pas requis par le scénario, un plan de découpage doit être implémenté avec un fondu sortant à partir de 1 m.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="1eeeb-245">Dans les cas où une observation plus proche d’un hologramme motionless est requise, le contenu ne doit pas être plus proche de 50 cm.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="1eeeb-246">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-246">Meets</span></span></td><td> <span data-ttu-id="1eeeb-247">Le contenu se trouve dans le Guide d’affichage et de mouvement, mais il n’utilise pas ou n’utilise pas le plan de découpage.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1eeeb-248">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-248">Fail</span></span> </td><td> <span data-ttu-id="1eeeb-249">Le contenu est présenté trop près (généralement &lt; 1,25 m, ou &lt; 50 cm pour les hologrammes fixes nécessitant une observation plus proche).</span><span class="sxs-lookup"><span data-stu-id="1eeeb-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-250">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-250">How to measure</span></span>

* <span data-ttu-id="1eeeb-251">Le contenu doit généralement être à 2 mètres de distance, mais pas plus proche de 1,25 ou plus de 5 mètres.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="1eeeb-252">À quelques exceptions près, la distance de rendu du découpage HoloLens doit être définie sur 85CM avec disparition en fondu du contenu à partir de 1 m.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="1eeeb-253">Approchez le contenu et notez l’effet plan de découpage.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="1eeeb-254">Le contenu fixe ne doit pas être plus proche de 50 cm.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-255">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-255">Recommendations</span></span>

* <span data-ttu-id="1eeeb-256">Concevez du contenu pour une distance de visualisation optimale de 2 m.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="1eeeb-257">Définissez la distance de rendu du découpage à 85 cm avec disparition en fondu du contenu à partir de 1 m.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="1eeeb-258">Pour les hologrammes fixes qui nécessitent un affichage plus étroit, le plan de découpage ne doit pas être plus proche de 30 cm et la disparition en fondu doit commencer au moins 10 cm du plan de découpage.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-259">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-259">Resources</span></span>

* [<span data-ttu-id="1eeeb-260">Distance de rendu</span><span class="sxs-lookup"><span data-stu-id="1eeeb-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="1eeeb-261">Point de focus dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="1eeeb-262">Expérimentation avec l’échelle</span><span class="sxs-lookup"><span data-stu-id="1eeeb-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="1eeeb-263">Texte, taille de police recommandée</span><span class="sxs-lookup"><span data-stu-id="1eeeb-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="1eeeb-264">Basculement de profondeur</span><span class="sxs-lookup"><span data-stu-id="1eeeb-264">Depth switching</span></span>

<span data-ttu-id="1eeeb-265">Indépendamment de l’affichage des problèmes liés à la zone de confort, les demandes pour l’utilisateur de basculer fréquemment ou rapidement entre des objets de niveau proche et lointain (y compris des hologrammes et du contenu réel) peuvent entraîner une fatigue oculomotor et une gêne générale.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-266">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-269">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-269">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-270">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-271">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-271">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-272">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-272">Best</span></span>  |  <span data-ttu-id="1eeeb-273">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-273">Meets</span></span> |  <span data-ttu-id="1eeeb-274">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-275">Basculement de profondeur limitée ou naturelle qui ne permet pas à l’utilisateur de se concentrer de manière non naturelle.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="1eeeb-276">Commutateur à profondeur brusque : il s’agit du noyau et est conçu pour l’expérience de l’application, ou le commutateur de profondeur brusque provoqué par un contenu réel inattendu.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="1eeeb-277">Commutateur de profondeur cohérent ou basculement de profondeur brusque qui n’est pas nécessaire ou essentiel à l’expérience de l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-278">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-278">How to measure</span></span>

* <span data-ttu-id="1eeeb-279">Si l’application exige que l’utilisateur change de manière cohérente et/ou brusquement le focus de profondeur, il y a un problème de changement de profondeur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-280">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-280">Recommendations</span></span>

* <span data-ttu-id="1eeeb-281">Conservez le contenu principal dans un plan focal cohérent et assurez-vous que le plan de stabilisation correspond au plan focal.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="1eeeb-282">Cela permet d’atténuer la fatigue oculomotor et le mouvement d’hologramme inattendu.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-283">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-283">Resources</span></span>

* [<span data-ttu-id="1eeeb-284">Distance de rendu</span><span class="sxs-lookup"><span data-stu-id="1eeeb-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="1eeeb-285">Point de focus dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="1eeeb-286">Utilisation du son spatial</span><span class="sxs-lookup"><span data-stu-id="1eeeb-286">Use of spatial sound</span></span>

<span data-ttu-id="1eeeb-287">Dans Windows Mixed Reality, le moteur audio fournit le composant d’acoustique de l’expérience de la réalité mixte en simulant le son en 3D à l’aide de la direction, de la distance et des simulations environnementales.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="1eeeb-288">L’utilisation d’un son spatial dans une application permet aux développeurs de placer des sons dans un espace à 3 Dimensions (sphère) autour de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="1eeeb-289">Ces sons semblent apparaître comme s’ils étaient issus d’objets physiques réels ou d’hologrammes de réalité mixte dans l’environnement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="1eeeb-290">Le son spatial est un outil puissant pour la conception de l’immersion, de l’accessibilité et de l’expérience utilisateur dans les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-291">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-294">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-294">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-295">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-296">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-296">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-297">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-297">Best</span></span>  |  <span data-ttu-id="1eeeb-298">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-298">Meets</span></span> |  <span data-ttu-id="1eeeb-299">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-300">Le son est logiquement spatial, et l’expérience utilisateur utilise le son de manière appropriée pour faciliter la détection d’objets et les commentaires des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="1eeeb-301">Les sons sont naturels et pertinents pour les objets et normalisés dans le scénario.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="1eeeb-302">L’audio spatial est utilisé de façon appropriée pour la récupération, mais il est manquant comme moyen d’aider aux commentaires des utilisateurs et à la découverte.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="1eeeb-303">Le son n’est pas spatial comme prévu, et/ou manque de son pour aider l’utilisateur au sein de l’expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="1eeeb-304">Ou l’audio spatial n’a pas été pris en compte ou utilisé dans la conception du scénario.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-305">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-305">How to measure</span></span>

* <span data-ttu-id="1eeeb-306">En général, les sons pertinents doivent émettre des hologrammes cibles (par exemple, des sons d’écorce provenant du chien holographique).</span><span class="sxs-lookup"><span data-stu-id="1eeeb-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="1eeeb-307">Des signaux sonores doivent être utilisés tout au long de l’expérience utilisateur pour aider l’utilisateur à faire part de ses commentaires ou à connaître des actions en dehors du cadre holographique.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-308">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-308">Recommendations</span></span>

* <span data-ttu-id="1eeeb-309">Utilisez l’audio spatial pour faciliter la détection d’objets et les interfaces utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="1eeeb-310">Les sons réels fonctionnent mieux que la synthèse ou le son non naturel.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="1eeeb-311">La plupart des sons doivent être spatiaux.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="1eeeb-312">Évitez les émetteurs invisibles.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="1eeeb-313">Évitez le masquage spatial.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="1eeeb-314">Normaliser tous les sons.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-315">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-316">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-316">Documentation</span></span>

* [<span data-ttu-id="1eeeb-317">Son spatial</span><span class="sxs-lookup"><span data-stu-id="1eeeb-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="1eeeb-318">Conception du son spatial</span><span class="sxs-lookup"><span data-stu-id="1eeeb-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="1eeeb-319">Son spatial dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="1eeeb-320">Étude de cas, son spatial pour HoloTour</span><span class="sxs-lookup"><span data-stu-id="1eeeb-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="1eeeb-321">Étude de cas utilisant le son spatial dans RoboRaid</span><span class="sxs-lookup"><span data-stu-id="1eeeb-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1eeeb-322">Outils et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-322">Tools and tutorials</span></span>

* [<span data-ttu-id="1eeeb-323">Boîte à outils de réalité mixte-audio spatial</span><span class="sxs-lookup"><span data-stu-id="1eeeb-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="1eeeb-324">Focalisation sur les limites du cadre holographique</span><span class="sxs-lookup"><span data-stu-id="1eeeb-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="1eeeb-325">Les expériences utilisateur bien conçues peuvent créer et gérer le contexte utile de l’environnement virtuel qui s’étend autour des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="1eeeb-326">L’atténuation de l’effet des limites de l’aide implique une conception réfléchie de l’échelle et du contexte du contenu, l’utilisation de l’audio spatial, les systèmes d’aide et la position de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="1eeeb-327">Si vous avez terminé, l’utilisateur se sentira moins affecté par les limites de l’aide, tout en disposant d’une expérience d’application confortable.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-328">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-331">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-332">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-332">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-333">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-333">Best</span></span>  |  <span data-ttu-id="1eeeb-334">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-334">Meets</span></span> |  <span data-ttu-id="1eeeb-335">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-336">L’utilisateur ne perd jamais de contexte et l’affichage est à l’aise.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="1eeeb-337">L’assistance contextuelle est fournie pour les objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="1eeeb-338">Les informations de découverte et d’affichage sont fournies pour les objets en dehors du frame.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="1eeeb-339">En général, la conception de mouvement et l’échelle des hologrammes sont appropriées pour une expérience d’affichage confortable.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="1eeeb-340">L’utilisateur ne perd jamais de contexte, mais un mouvement de cou supplémentaire peut être nécessaire dans des situations limitées.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="1eeeb-341">Dans le cas d’une mise à l’échelle limitée, les hologrammes rompent le cadre vertical ou horizontal provoquant un mouvement du cou pour afficher les hologrammes.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="1eeeb-342">L’utilisateur risque de perdre du contexte et/ou un mouvement de cou cohérent est nécessaire pour afficher les hologrammes.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="1eeeb-343">Aucun guide de contexte pour les grands objets holographiques, déplacement d’objets facile à perdre en dehors du cadre sans guide de détectabilité, ou hologrammes de haut, nécessite un mouvement de cou normal.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-344">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-344">How to measure</span></span>

* <span data-ttu-id="1eeeb-345">Le contexte d’un (grand) hologramme est perdu ou n’est pas compris en raison d’un découpage aux limites.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="1eeeb-346">Les emplacements des hologrammes sont difficiles à trouver en raison de l’absence de directeurs ou de contenus qui se déplacent rapidement dans le cadre holographique.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="1eeeb-347">Le scénario nécessite un mouvement de tête normal et répétitif pour voir entièrement un hologramme entraînant une fatigue du cou.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-348">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-348">Recommendations</span></span>

* <span data-ttu-id="1eeeb-349">Démarrez l’expérience avec les petits objets qui correspondent à l’angle d’ouverture, puis faites la transition avec des signaux visuels vers des versions plus grandes.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="1eeeb-350">Utilisez des directeurs audio et d’avertissement pour aider l’utilisateur à trouver du contenu en dehors de l’aide.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="1eeeb-351">Évitez autant que possible les hologrammes qui découpent verticalement l’angle de la verticale.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="1eeeb-352">Fournissez à l’utilisateur des conseils dans l’application pour un meilleur affichage de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-353">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-354">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-354">Documentation</span></span>

* [<span data-ttu-id="1eeeb-355">Image holographique</span><span class="sxs-lookup"><span data-stu-id="1eeeb-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="1eeeb-356">Étude de cas, interface utilisateur HoloStudio et apprentissages de conception d’interaction</span><span class="sxs-lookup"><span data-stu-id="1eeeb-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="1eeeb-357">Échelle des objets et des environnements</span><span class="sxs-lookup"><span data-stu-id="1eeeb-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="1eeeb-358">Curseurs, signaux visuels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="1eeeb-359">Références externes</span><span class="sxs-lookup"><span data-stu-id="1eeeb-359">External references</span></span>

* [<span data-ttu-id="1eeeb-360">Bien d’ADO sur l’angle d’été</span><span class="sxs-lookup"><span data-stu-id="1eeeb-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="1eeeb-361">Le contenu réagit à la position de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="1eeeb-361">Content reacts to user position</span></span>

<span data-ttu-id="1eeeb-362">Les hologrammes doivent réagir à la position de l’utilisateur à peu près de la même façon que les objets « réels ».</span><span class="sxs-lookup"><span data-stu-id="1eeeb-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="1eeeb-363">L’un des éléments d’interface utilisateur qui ne peuvent pas nécessairement supposer que la position d’un utilisateur est stationnaire et s’adapte au mouvement de l’utilisateur est une considération notable.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="1eeeb-364">La conception d’une application qui s’adapte correctement à la position de l’utilisateur crée une expérience plus crédible et la rend plus facile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-365">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-368">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-368">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-369">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-370">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="1eeeb-371">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-371">Best</span></span> </td><td> <span data-ttu-id="1eeeb-372">Le contenu et l’interface utilisateur s’adaptent aux postes des utilisateurs, ce qui permet à l’utilisateur d’interagir naturellement avec le contenu dans le cadre du déplacement d’utilisateur attendu.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1eeeb-373">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-373">Meets</span></span> </td><td> <span data-ttu-id="1eeeb-374">L’interface utilisateur s’adapte à la position de l’utilisateur, mais peut empêcher l’affichage du contenu de la clé qui oblige l’utilisateur à ajuster sa position.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1eeeb-375">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="1eeeb-376">Les éléments d’interface utilisateur sont perdus ou verrouillés au cours du mouvement, provoquant ainsi un retour à (ou une recherche) anormal des contrôles.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="1eeeb-377">Les éléments d’interface utilisateur limitent l’affichage du contenu principal.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="1eeeb-378"><a href="../../design/billboarding-and-tag-along.md">Le</a> déplacement de l’interface utilisateur n’est pas optimisé pour l’affichage de la distance et de l’inertie, en particulier avec les éléments d’interface.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-379">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-379">How to measure</span></span>

* <span data-ttu-id="1eeeb-380">Toutes les mesures doivent être effectuées dans une étendue raisonnable du scénario.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="1eeeb-381">Si le déplacement des utilisateurs varie, n’essayez pas de tromper l’application avec un déplacement extrême de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="1eeeb-382">Pour les éléments d’interface utilisateur, les contrôles pertinents doivent être disponibles quel que soit le déplacement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="1eeeb-383">Par exemple, si l’utilisateur consulte et parcourt une carte 3D avec zoom, le contrôle de zoom doit être immédiatement accessible à l’utilisateur, quel que soit son emplacement.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-384">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-384">Recommendations</span></span>

* <span data-ttu-id="1eeeb-385">L’utilisateur est l’appareil photo et il contrôle le mouvement.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="1eeeb-386">Laissez-les sur le lecteur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-386">Let them drive.</span></span>
* <span data-ttu-id="1eeeb-387">Envisagez l’utilisation de panneaux pour le texte et les systèmes de menus qui, autrement, seraient universellement verrouillés ou obscurcis si un utilisateur devait se déplacer.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="1eeeb-388">Utilisez tag-avec pour le contenu qui doit suivre l’utilisateur tout en permettant à l’utilisateur de voir ce qui est devant eux.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-389">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-390">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-390">Documentation</span></span>

* [<span data-ttu-id="1eeeb-391">Conception des interactions</span><span class="sxs-lookup"><span data-stu-id="1eeeb-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="1eeeb-392">Couleur, lumière et matériau</span><span class="sxs-lookup"><span data-stu-id="1eeeb-392">Color, light, and material</span></span>](../../design/color-light-and-materials.md)
* [<span data-ttu-id="1eeeb-393">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="1eeeb-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="1eeeb-394">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="1eeeb-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="1eeeb-395">Mouvement propre et locomotion utilisateur</span><span class="sxs-lookup"><span data-stu-id="1eeeb-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="1eeeb-396">Clarté d’interaction d’entrée</span><span class="sxs-lookup"><span data-stu-id="1eeeb-396">Input interaction clarity</span></span>

<span data-ttu-id="1eeeb-397">La clarté de l’interaction d’entrée est essentielle à l’utilisation d’une application et comprend la cohérence des entrées, l’approche, la détectabilité des méthodes d’interaction.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="1eeeb-398">L’utilisateur peut utiliser des interactions communes à l’ensemble de la plateforme sans réapprendre.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="1eeeb-399">Si l’application dispose d’une entrée personnalisée, elle doit être clairement communiquée et démontrée.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-400">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-403">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-403">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-404">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-405">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-405">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-406">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-406">Best</span></span>  |  <span data-ttu-id="1eeeb-407">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-407">Meets</span></span> |  <span data-ttu-id="1eeeb-408">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-409">Les méthodes d’interaction d’entrée sont cohérentes avec les [recommandations](../../design/interaction-fundamentals.md)fournies par Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="1eeeb-410">Toute entrée personnalisée ne doit pas être redondante avec une entrée standard (plutôt que d’utiliser l’interaction standard) et doit être clairement communiquée et présentée à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="1eeeb-411">Semblable au meilleur, mais les entrées personnalisées sont redondantes avec des méthodes d’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="1eeeb-412">L’utilisateur peut toujours atteindre l’objectif et progresser dans l’expérience de l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="1eeeb-413">Il est difficile de comprendre la méthode d’entrée ou le mappage de bouton.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="1eeeb-414">L’entrée est fortement personnalisée, ne prend pas en charge les entrées standard, aucune instruction, ou risque de causer des problèmes de fatigue et de confort.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-415">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-415">How to measure</span></span>

* <span data-ttu-id="1eeeb-416">L’application utilise des [méthodes d’entrée standard](../../design/interaction-fundamentals.md) cohérentes.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="1eeeb-417">Si l’application dispose d’une entrée personnalisée, elle est clairement communiquée à :</span><span class="sxs-lookup"><span data-stu-id="1eeeb-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="1eeeb-418">Expérience de première exécution</span><span class="sxs-lookup"><span data-stu-id="1eeeb-418">First-run experience</span></span>
* <span data-ttu-id="1eeeb-419">Écrans d’introduction</span><span class="sxs-lookup"><span data-stu-id="1eeeb-419">Introductory screens</span></span>
* <span data-ttu-id="1eeeb-420">Info-bulles</span><span class="sxs-lookup"><span data-stu-id="1eeeb-420">Tooltips</span></span>
* <span data-ttu-id="1eeeb-421">Coach de main</span><span class="sxs-lookup"><span data-stu-id="1eeeb-421">Hand coach</span></span>
* <span data-ttu-id="1eeeb-422">Section d’aide</span><span class="sxs-lookup"><span data-stu-id="1eeeb-422">Help section</span></span>
* <span data-ttu-id="1eeeb-423">VoiceOver</span><span class="sxs-lookup"><span data-stu-id="1eeeb-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-424">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-424">Recommendations</span></span>

* <span data-ttu-id="1eeeb-425">Utilisez des méthodes d’entrée standard dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="1eeeb-426">Fournissez des démonstrations, des didacticiels et des info-bulles pour les méthodes d’entrée non standard.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="1eeeb-427">Utilisez un modèle d’interaction cohérent dans l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-428">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-429">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-429">Documentation</span></span>

* [<span data-ttu-id="1eeeb-430">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="1eeeb-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="1eeeb-431">Objets interactifs</span><span class="sxs-lookup"><span data-stu-id="1eeeb-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="1eeeb-432">Suivre de la tête et stabiliser</span><span class="sxs-lookup"><span data-stu-id="1eeeb-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="1eeeb-433">Curseurs</span><span class="sxs-lookup"><span data-stu-id="1eeeb-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="1eeeb-434">Confort et point de regard</span><span class="sxs-lookup"><span data-stu-id="1eeeb-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="1eeeb-435">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="1eeeb-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="1eeeb-436">Contrôleurs de mouvement</span><span class="sxs-lookup"><span data-stu-id="1eeeb-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="1eeeb-437">Guide de portage des entrées pour Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="1eeeb-438">Saisie au clavier dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="1eeeb-439">Pointage du regard dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="1eeeb-440">Contrôleurs de mouvement dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-440">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="1eeeb-441">Mouvements dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-441">Gestures in Unity</span></span>](../unity/gestures-in-unity.md)
* [<span data-ttu-id="1eeeb-442">Entrée vocale dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-442">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="1eeeb-443">Saisie à l’aide de la commande de jeu, du clavier et de la souris dans DirectX</span><span class="sxs-lookup"><span data-stu-id="1eeeb-443">Keyboard, mouse, and controller input in DirectX</span></span>](./keyboard-mouse-and-controller-input-in-directx.md)
* [<span data-ttu-id="1eeeb-444">Suivre de la tête et du regard dans DirectX</span><span class="sxs-lookup"><span data-stu-id="1eeeb-444">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="1eeeb-445">Mains et contrôleurs de mouvement dans DirectX</span><span class="sxs-lookup"><span data-stu-id="1eeeb-445">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="1eeeb-446">Entrée vocale dans DirectX</span><span class="sxs-lookup"><span data-stu-id="1eeeb-446">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1eeeb-447">Outils et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-447">Tools and tutorials</span></span>

* [<span data-ttu-id="1eeeb-448">Étude de cas : la poursuite de l’informatique plus personnelle</span><span class="sxs-lookup"><span data-stu-id="1eeeb-448">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="1eeeb-449">Étude de Cast : interface utilisateur HoloStudio et apprentissages de conception d’interaction</span><span class="sxs-lookup"><span data-stu-id="1eeeb-449">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="1eeeb-450">Exemple d’application : table périodique des éléments</span><span class="sxs-lookup"><span data-stu-id="1eeeb-450">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="1eeeb-451">Exemple d’application : module lunaire</span><span class="sxs-lookup"><span data-stu-id="1eeeb-451">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="1eeeb-452">Objets interactifs</span><span class="sxs-lookup"><span data-stu-id="1eeeb-452">Interactable objects</span></span>

<span data-ttu-id="1eeeb-453">Un bouton a longtemps été une métaphore utilisée pour déclencher un événement dans le monde abstrait en 2D.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-453">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="1eeeb-454">Dans le monde de la réalité mixte en trois dimensions, nous n’avons plus à limiter le monde de l’abstraction.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-454">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="1eeeb-455">Tout peut être un objet pouvant être utilisé qui déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-455">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="1eeeb-456">Un objet pouvant être en interaction peut être représenté sous la forme d’un objet à partir d’une tasse de café sur la table.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-456">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="1eeeb-457">Quelle que soit la forme, les objets interactifs doivent être clairement reconnus par l’utilisateur via des signaux visuels et audio.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-457">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-458">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-458">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-461">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-461">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-462">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-462">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-463">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-463">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-464">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-464">Best</span></span>  |  <span data-ttu-id="1eeeb-465">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-465">Meets</span></span> |  <span data-ttu-id="1eeeb-466">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-466">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-467">Quelle que soit la forme, les objets interactifs sont reconnaissables par des signaux audio et visuels dans les trois États : inactif, ciblé et sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-467">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="1eeeb-468">« Regardez-le, dites-le » est clair et constamment utilisé tout au long de l’expérience.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-468">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="1eeeb-469">Les objets sont mis à l’échelle et distribués pour permettre le ciblage gratuit des erreurs.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-469">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="1eeeb-470">L’utilisateur peut reconnaître un objet comme étant en interaction avec des retours audio ou visuels, et peut cibler et activer l’objet.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-470">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="1eeeb-471">En l’absence de signaux visuels ou audio, l’utilisateur ne peut pas reconnaître un objet pouvant être en interaction.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-471">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="1eeeb-472">Les interactions sont sujettes aux erreurs en raison de l’échelle de l’objet ou de la distance entre les objets.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-472">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-473">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-473">How to measure</span></span>

* <span data-ttu-id="1eeeb-474">Les objets interactifs sont reconnaissables comme « interactifs »; y compris les boutons, les menus et le contenu spécifique à l’application.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-474">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="1eeeb-475">En règle générale, il doit exister un signal visuel et audio pour cibler les objets interactifs.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-475">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-476">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-476">Recommendations</span></span>

* <span data-ttu-id="1eeeb-477">Utilisez des commentaires visuels et audio pour les interactions.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-477">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="1eeeb-478">Les commentaires visuels doivent être différenciés pour chaque État d’entrée (inactif, ciblé, sélectionné)</span><span class="sxs-lookup"><span data-stu-id="1eeeb-478">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="1eeeb-479">Les objets interactifs doivent être mis à l’échelle et placés en vue d’une erreur de ciblage libre.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-479">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="1eeeb-480">Les objets interactifs groupés (tels qu’une barre de menus ou une liste) doivent avoir un espacement correct pour le ciblage.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-480">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="1eeeb-481">Les boutons et les menus qui prennent en charge les commandes vocales doivent fournir des étiquettes de texte pour le mot clé de commande (« consultez-le », dites-le «»)</span><span class="sxs-lookup"><span data-stu-id="1eeeb-481">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-482">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-482">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-483">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-483">Documentation</span></span>

* [<span data-ttu-id="1eeeb-484">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="1eeeb-484">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="1eeeb-485">Texte dans Unity</span><span class="sxs-lookup"><span data-stu-id="1eeeb-485">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="1eeeb-486">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="1eeeb-486">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="1eeeb-487">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="1eeeb-487">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1eeeb-488">Outils et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-488">Tools and tutorials</span></span>

* [<span data-ttu-id="1eeeb-489">Kit de pratiques de réalité mixte-UX</span><span class="sxs-lookup"><span data-stu-id="1eeeb-489">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="1eeeb-490">Analyse de la salle</span><span class="sxs-lookup"><span data-stu-id="1eeeb-490">Room scanning</span></span>

<span data-ttu-id="1eeeb-491">Les applications qui requièrent des données de mappage spatiale s’appuient sur l’appareil pour collecter automatiquement ces données au fil du temps et entre les sessions lorsque l’utilisateur explore son environnement avec l’appareil actif.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-491">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="1eeeb-492">L’exhaustivité et la qualité de ces données dépendent d’un certain nombre de facteurs, notamment la quantité d’exploration effectuée par l’utilisateur, le temps écoulé depuis l’exploration et si les objets tels que les meubles et les portes ont été déplacés depuis que l’appareil a analysé la zone.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-492">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="1eeeb-493">De nombreuses applications analysent les données de mappage spatiale au début de l’expérience afin de déterminer si l’utilisateur doit effectuer des étapes supplémentaires pour améliorer l’exhaustivité et la qualité de la carte spatiale.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-493">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="1eeeb-494">Si l’utilisateur est invité à analyser l’environnement, vous devez fournir des instructions claires au cours de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-494">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-495">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-495">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-498">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-498">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-499">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-499">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-500">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-500">Best</span></span>  |  <span data-ttu-id="1eeeb-501">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-501">Meets</span></span> |  <span data-ttu-id="1eeeb-502">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-502">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-503">La visualisation de la maille spatiale indique aux utilisateurs que l’analyse est en cours.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-503">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="1eeeb-504">L’utilisateur sait clairement ce qu’il doit faire et quand l’analyse démarre et s’arrête.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-504">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="1eeeb-505">La visualisation du maillage spatial est fournie, mais l’utilisateur peut ne pas savoir clairement ce qu’il faut faire et aucune information de progression n’est fournie.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-505">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="1eeeb-506">Aucune visualisation de la maille.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-506">No visualization of mesh.</span></span> <span data-ttu-id="1eeeb-507">Aucune information n’est fournie à l’utilisateur quant à son emplacement ou au démarrage ou à l’arrêt de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-507">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-508">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-508">How to measure</span></span>

* <span data-ttu-id="1eeeb-509">Au cours d’une analyse de la salle requise, des conseils visuels et audio sont fournis pour indiquer l’emplacement et le moment du démarrage et de l’arrêt de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-509">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-510">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-510">Recommendations</span></span>

* <span data-ttu-id="1eeeb-511">Indiquez la quantité de volume total des utilisateurs avoisinants qui doit faire partie de l’expérience.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-511">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="1eeeb-512">Communiquer quand l’analyse démarre et s’arrête, comme un indicateur de progression.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-512">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="1eeeb-513">Utilisez une visualisation de la maille pendant l’analyse.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-513">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="1eeeb-514">Fournissez des signaux visuels et audio pour encourager l’utilisateur à regarder et à se déplacer dans la pièce.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-514">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="1eeeb-515">Informez l’utilisateur où accéder à pour améliorer les données.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-515">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="1eeeb-516">Dans de nombreux cas, il peut être préférable de dire à l’utilisateur ce qu’il doit faire (par exemple, regarder le plafond, regarder derrière le mobilier), afin d’obtenir la qualité d’analyse nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-516">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-517">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-517">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1eeeb-518">Documentation</span><span class="sxs-lookup"><span data-stu-id="1eeeb-518">Documentation</span></span>

* [<span data-ttu-id="1eeeb-519">Visualisation du balayage d’une pièce</span><span class="sxs-lookup"><span data-stu-id="1eeeb-519">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="1eeeb-520">Étude de cas : développement des fonctionnalités de mappage spatial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="1eeeb-520">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="1eeeb-521">Étude de cas : conception de son spatial pour HoloTour</span><span class="sxs-lookup"><span data-stu-id="1eeeb-521">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="1eeeb-522">Étude de cas : création d’une expérience immersive dans des fragments</span><span class="sxs-lookup"><span data-stu-id="1eeeb-522">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1eeeb-523">Outils et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-523">Tools and tutorials</span></span>

* [<span data-ttu-id="1eeeb-524">Kit de pratiques de réalité mixte-UX</span><span class="sxs-lookup"><span data-stu-id="1eeeb-524">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="1eeeb-525">Indicateurs directionnels</span><span class="sxs-lookup"><span data-stu-id="1eeeb-525">Directional indicators</span></span>

<span data-ttu-id="1eeeb-526">Dans une application de réalité mixte, le contenu peut être en dehors du champ de vue ou bloqués par des objets réels.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-526">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="1eeeb-527">Une application bien conçue permettra à l’utilisateur de trouver plus facilement du contenu non visible.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-527">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="1eeeb-528">Les indicateurs directionnels signalent à un utilisateur un contenu important et fournissent des conseils sur le contenu relatif à la position de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-528">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="1eeeb-529">Les instructions relatives au contenu non visible peuvent prendre la forme d’émetteurs de sons, de flèches directionnelles ou de signaux visuels directs.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-529">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-530">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-530">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-533">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-533">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-534">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-534">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-535">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-535">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-536">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-536">Best</span></span>  |  <span data-ttu-id="1eeeb-537">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-537">Meets</span></span> |  <span data-ttu-id="1eeeb-538">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-538">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-539">Les signaux audio et visuel guident directement l’utilisateur vers du contenu pertinent en dehors du champ de vue.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-539">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="1eeeb-540">Une flèche ou un indicateur qui dirige l’utilisateur dans la direction générale du contenu.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-540">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="1eeeb-541">Le contenu pertinent est en dehors du champ de la vue, et de mauvaises instructions de localisation sont fournies à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-541">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-542">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-542">How to measure</span></span>

* <span data-ttu-id="1eeeb-543">Le contenu pertinent en dehors du champ utilisateur de la vue est détectable via des signaux visuels et/ou audio.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-543">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-544">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-544">Recommendations</span></span>

* <span data-ttu-id="1eeeb-545">Quand le contenu pertinent est en dehors du champ de vue de l’utilisateur, utilisez des indicateurs directionnels et des signaux audio pour guider l’utilisateur vers le contenu.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-545">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="1eeeb-546">Dans de nombreux cas, un guide visuel direct est préférable sur les flèches directionnelles.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-546">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="1eeeb-547">Les indicateurs directionnels ne doivent pas être intégrés au curseur.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-547">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-548">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-548">Resources</span></span>

* [<span data-ttu-id="1eeeb-549">Image holographique</span><span class="sxs-lookup"><span data-stu-id="1eeeb-549">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="1eeeb-550">Chargement de données</span><span class="sxs-lookup"><span data-stu-id="1eeeb-550">Data loading</span></span>

<span data-ttu-id="1eeeb-551">Un contrôle de progression offre un retour à l’utilisateur lorsqu’une longue opération est en cours.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-551">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="1eeeb-552">Cela peut signifier que l’utilisateur ne peut pas interagir avec l’application lorsque l’indicateur de progression est visible et peut également indiquer la durée du délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-552">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1eeeb-553">Impact de l’appareil</span><span class="sxs-lookup"><span data-stu-id="1eeeb-553">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1eeeb-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="1eeeb-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="1eeeb-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1eeeb-556">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-556">✔️</span></span></td>
        <td><span data-ttu-id="1eeeb-557">✔️</span><span class="sxs-lookup"><span data-stu-id="1eeeb-557">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1eeeb-558">Critères de qualité</span><span class="sxs-lookup"><span data-stu-id="1eeeb-558">Quality criteria</span></span>

|  <span data-ttu-id="1eeeb-559">La meilleure</span><span class="sxs-lookup"><span data-stu-id="1eeeb-559">Best</span></span>  |  <span data-ttu-id="1eeeb-560">Présente</span><span class="sxs-lookup"><span data-stu-id="1eeeb-560">Meets</span></span> |  <span data-ttu-id="1eeeb-561">Échec</span><span class="sxs-lookup"><span data-stu-id="1eeeb-561">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1eeeb-562">Indicateur visuel animé, sous la forme d’une barre de progression ou d’un anneau, indiquant la progression pendant le chargement ou le traitement des données.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-562">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="1eeeb-563">L’indicateur visuel fournit des indications sur la durée de l’attente.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-563">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="1eeeb-564">L’utilisateur est informé que le chargement des données est en cours, mais il n’existe aucune indication sur la durée de l’attente.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-564">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="1eeeb-565">Aucun chargement de données ou indicateur de processus pour la tâche ne dure plus de 5 secondes.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-565">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1eeeb-566">Comment mesurer</span><span class="sxs-lookup"><span data-stu-id="1eeeb-566">How to measure</span></span>

* <span data-ttu-id="1eeeb-567">Pendant le chargement des données, vérifiez qu’il n’y a pas d’état vide pendant plus de 5 secondes.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-567">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1eeeb-568">Recommandations</span><span class="sxs-lookup"><span data-stu-id="1eeeb-568">Recommendations</span></span>

* <span data-ttu-id="1eeeb-569">Fournissez un animateur de chargement des données qui indique la progression dans toutes les situations où l’utilisateur peut percevoir cette application comme étant bloquée ou bloquée.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-569">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="1eeeb-570">Une règle raisonnable est toute activité de « chargement » qui peut prendre plus de 5 secondes.</span><span class="sxs-lookup"><span data-stu-id="1eeeb-570">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="1eeeb-571">Ressources</span><span class="sxs-lookup"><span data-stu-id="1eeeb-571">Resources</span></span>

* [<span data-ttu-id="1eeeb-572">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="1eeeb-572">Displaying progress</span></span>](../../design/progress.md)