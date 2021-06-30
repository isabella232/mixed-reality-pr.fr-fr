---
title: Utilisation du générateur de profils Visual
description: documentation relative à l’utilisation de Visual Profiler dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: c3238aed60f6bbf824c74c034ddf506f49f436c7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121647"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="d927d-104">Utilisation du générateur de profils Visual</span><span class="sxs-lookup"><span data-stu-id="d927d-104">Using the visual profiler</span></span>

<span data-ttu-id="d927d-105">Le VisualProfiler fournit une vue en toute simplicité et en application des performances d’une application de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="d927d-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="d927d-106">Le profileur est pris en charge sur toutes les plateformes d’outils de réalité mixte, y compris :</span><span class="sxs-lookup"><span data-stu-id="d927d-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="d927d-107">Microsoft HoloLens (1ère génération)</span><span class="sxs-lookup"><span data-stu-id="d927d-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="d927d-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d927d-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="d927d-109">Casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d927d-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="d927d-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="d927d-110">OpenVR</span></span>

<span data-ttu-id="d927d-111">Lors du développement d’une application, concentrez-vous sur plusieurs parties de la scène, car le profileur visuel affiche les données relatives à la vue actuelle.</span><span class="sxs-lookup"><span data-stu-id="d927d-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d927d-112">Concentrez-vous sur certaines parties de la scène avec des objets complexes, des effets de particules ou une activité.</span><span class="sxs-lookup"><span data-stu-id="d927d-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="d927d-113">Ces facteurs contribuent souvent à réduire les performances des applications et à offrir une expérience utilisateur moins que idéale.</span><span class="sxs-lookup"><span data-stu-id="d927d-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="d927d-114">Interface du profileur Visual</span><span class="sxs-lookup"><span data-stu-id="d927d-114">Visual profiler interface</span></span>

![Interface du profileur Visual](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="d927d-116">L’interface du profileur Visual comprend les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="d927d-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="d927d-117">Fréquence d’images</span><span class="sxs-lookup"><span data-stu-id="d927d-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="d927d-118">Heure du frame</span><span class="sxs-lookup"><span data-stu-id="d927d-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="d927d-119">Graphique de frame</span><span class="sxs-lookup"><span data-stu-id="d927d-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="d927d-120">Utilisation de la mémoire</span><span class="sxs-lookup"><span data-stu-id="d927d-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="d927d-121">Fréquence d’images</span><span class="sxs-lookup"><span data-stu-id="d927d-121">Frame rate</span></span>

<span data-ttu-id="d927d-122">Dans le coin supérieur gauche de l’interface se trouve la fréquence d’images, mesurée en images par seconde.</span><span class="sxs-lookup"><span data-stu-id="d927d-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="d927d-123">Pour optimiser l’expérience utilisateur et le confort, cette valeur doit être aussi élevée que possible.</span><span class="sxs-lookup"><span data-stu-id="d927d-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="d927d-124">La configuration matérielle et la plateforme spécifique jouent un rôle significatif dans la fréquence d’images maximale réalisable.</span><span class="sxs-lookup"><span data-stu-id="d927d-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="d927d-125">Les valeurs cibles courantes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d927d-125">Some common target values include:</span></span>

- <span data-ttu-id="d927d-126">Microsoft HoloLens : 60</span><span class="sxs-lookup"><span data-stu-id="d927d-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="d927d-127">Windows Mixed Reality ultra : 90</span><span class="sxs-lookup"><span data-stu-id="d927d-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="d927d-128">En raison de la [limitation de la fréquence d’images sur HoloLens lorsque la fonction MRC par défaut est active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), le profileur Visual est masqué lors de la capture des vidéos et des photos.</span><span class="sxs-lookup"><span data-stu-id="d927d-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="d927d-129">Ce paramètre peut être remplacé dans le profil du système de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="d927d-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="d927d-130">Durée de frame</span><span class="sxs-lookup"><span data-stu-id="d927d-130">Frame time</span></span>

<span data-ttu-id="d927d-131">À droite de la fréquence d’images se trouve le temps d’image, en millisecondes, passé sur le processeur.</span><span class="sxs-lookup"><span data-stu-id="d927d-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="d927d-132">Pour atteindre les fréquences d’images cibles mentionnées précédemment, une application peut consacrer la durée suivante par image :</span><span class="sxs-lookup"><span data-stu-id="d927d-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="d927d-133">60 FPS : 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="d927d-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="d927d-134">90 FPS : 11,1 ms</span><span class="sxs-lookup"><span data-stu-id="d927d-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="d927d-135">L’heure du GPU est prévue pour être ajoutée dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d927d-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="d927d-136">Graphique de frame</span><span class="sxs-lookup"><span data-stu-id="d927d-136">Frame graph</span></span>

<span data-ttu-id="d927d-137">Le graphique de Frame fournit un affichage graphique de l’historique de la fréquence d’images de l’application.</span><span class="sxs-lookup"><span data-stu-id="d927d-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Graphique de frame manqué du profileur Visual](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="d927d-139">Lorsque vous utilisez l’application, recherchez les trames manquées qui indiquent que l’application n’atteint pas sa fréquence d’images cible et peut nécessiter un travail d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="d927d-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="d927d-140">Utilisation de la mémoire</span><span class="sxs-lookup"><span data-stu-id="d927d-140">Memory utilization</span></span>

<span data-ttu-id="d927d-141">L’affichage de l’utilisation de la mémoire permet de comprendre facilement comment la vue actuelle influe sur la consommation de mémoire d’une application.</span><span class="sxs-lookup"><span data-stu-id="d927d-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Graphique de mémoire du profileur Visual](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="d927d-143">Lorsque vous utilisez l’application, recherchez l’utilisation totale de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="d927d-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="d927d-144">Les indicateurs clés incluent l’approche de la limite de la mémoire et des modifications rapides de l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d927d-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="d927d-145">Personnalisation du générateur de profils Visual</span><span class="sxs-lookup"><span data-stu-id="d927d-145">Customizing the visual profiler</span></span>

<span data-ttu-id="d927d-146">L’apparence et le comportement de Visual Profiler sont personnalisables via le profil de système de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="d927d-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="d927d-147">Pour plus d’informations, consultez [configuration du système de diagnostics](configuring-diagnostics.md) .</span><span class="sxs-lookup"><span data-stu-id="d927d-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="d927d-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d927d-148">See also</span></span>

- [<span data-ttu-id="d927d-149">Système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="d927d-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="d927d-150">Configuration du système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="d927d-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)