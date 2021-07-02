---
title: Utilisation du générateur de profils Visual
description: documentation relative à l’utilisation de Visual Profiler dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 018d6bf2087b73697a1e1f43e206c96ae25e1f21
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177227"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="58a3e-104">Utilisation du générateur de profils Visual</span><span class="sxs-lookup"><span data-stu-id="58a3e-104">Using the visual profiler</span></span>

<span data-ttu-id="58a3e-105">Le VisualProfiler fournit une vue en toute simplicité et en application des performances d’une application de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="58a3e-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="58a3e-106">le profileur est pris en charge sur toutes les plateformes Shared Computer Toolkit de réalité mixte, y compris :</span><span class="sxs-lookup"><span data-stu-id="58a3e-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="58a3e-107">Microsoft HoloLens (1re génération)</span><span class="sxs-lookup"><span data-stu-id="58a3e-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="58a3e-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="58a3e-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="58a3e-109">Casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="58a3e-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="58a3e-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="58a3e-110">OpenVR</span></span>

<span data-ttu-id="58a3e-111">Lors du développement d’une application, concentrez-vous sur plusieurs parties de la scène, car le profileur visuel affiche les données relatives à la vue actuelle.</span><span class="sxs-lookup"><span data-stu-id="58a3e-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58a3e-112">Concentrez-vous sur certaines parties de la scène avec des objets complexes, des effets de particules ou une activité.</span><span class="sxs-lookup"><span data-stu-id="58a3e-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="58a3e-113">Ces facteurs contribuent souvent à réduire les performances des applications et à offrir une expérience utilisateur moins que idéale.</span><span class="sxs-lookup"><span data-stu-id="58a3e-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="58a3e-114">Interface du profileur Visual</span><span class="sxs-lookup"><span data-stu-id="58a3e-114">Visual profiler interface</span></span>

![Interface du profileur Visual](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="58a3e-116">L’interface du profileur Visual comprend les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="58a3e-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="58a3e-117">Fréquence d’images</span><span class="sxs-lookup"><span data-stu-id="58a3e-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="58a3e-118">Heure du frame</span><span class="sxs-lookup"><span data-stu-id="58a3e-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="58a3e-119">Graph de frame</span><span class="sxs-lookup"><span data-stu-id="58a3e-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="58a3e-120">Utilisation de la mémoire</span><span class="sxs-lookup"><span data-stu-id="58a3e-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="58a3e-121">Fréquence d’images</span><span class="sxs-lookup"><span data-stu-id="58a3e-121">Frame rate</span></span>

<span data-ttu-id="58a3e-122">Dans le coin supérieur gauche de l’interface se trouve la fréquence d’images, mesurée en images par seconde.</span><span class="sxs-lookup"><span data-stu-id="58a3e-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="58a3e-123">Pour optimiser l’expérience utilisateur et le confort, cette valeur doit être aussi élevée que possible.</span><span class="sxs-lookup"><span data-stu-id="58a3e-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="58a3e-124">La configuration matérielle et la plateforme spécifique jouent un rôle significatif dans la fréquence d’images maximale réalisable.</span><span class="sxs-lookup"><span data-stu-id="58a3e-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="58a3e-125">Les valeurs cibles courantes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="58a3e-125">Some common target values include:</span></span>

- <span data-ttu-id="58a3e-126">Microsoft HoloLens : 60</span><span class="sxs-lookup"><span data-stu-id="58a3e-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="58a3e-127">Windows Mixed Reality Ultra : 90</span><span class="sxs-lookup"><span data-stu-id="58a3e-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="58a3e-128">en raison de la [limitation de la fréquence d’images sur HoloLens lorsque la valeur de l’option MRC par défaut est active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), le profileur visual est masqué lors de la capture des vidéos et des photos.</span><span class="sxs-lookup"><span data-stu-id="58a3e-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="58a3e-129">Ce paramètre peut être remplacé dans le profil du système de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="58a3e-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="58a3e-130">Durée de frame</span><span class="sxs-lookup"><span data-stu-id="58a3e-130">Frame time</span></span>

<span data-ttu-id="58a3e-131">À droite de la fréquence d’images se trouve le temps d’image, en millisecondes, passé sur le processeur.</span><span class="sxs-lookup"><span data-stu-id="58a3e-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="58a3e-132">Pour atteindre les fréquences d’images cibles mentionnées précédemment, une application peut consacrer la durée suivante par image :</span><span class="sxs-lookup"><span data-stu-id="58a3e-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="58a3e-133">60 FPS : 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="58a3e-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="58a3e-134">90 FPS : 11,1 ms</span><span class="sxs-lookup"><span data-stu-id="58a3e-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="58a3e-135">L’heure du GPU est prévue pour être ajoutée dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="58a3e-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="58a3e-136">Graphique de frame</span><span class="sxs-lookup"><span data-stu-id="58a3e-136">Frame graph</span></span>

<span data-ttu-id="58a3e-137">Le graphique de Frame fournit un affichage graphique de l’historique de la fréquence d’images de l’application.</span><span class="sxs-lookup"><span data-stu-id="58a3e-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Graph de frame manqué du profileur Visual](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="58a3e-139">Lorsque vous utilisez l’application, recherchez les trames manquées qui indiquent que l’application n’atteint pas sa fréquence d’images cible et peut nécessiter un travail d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="58a3e-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="58a3e-140">Utilisation de la mémoire</span><span class="sxs-lookup"><span data-stu-id="58a3e-140">Memory utilization</span></span>

<span data-ttu-id="58a3e-141">L’affichage de l’utilisation de la mémoire permet de comprendre facilement comment la vue actuelle influe sur la consommation de mémoire d’une application.</span><span class="sxs-lookup"><span data-stu-id="58a3e-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Graph de mémoire du profileur Visual](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="58a3e-143">Lorsque vous utilisez l’application, recherchez l’utilisation totale de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="58a3e-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="58a3e-144">Les indicateurs clés incluent l’approche de la limite de la mémoire et des modifications rapides de l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="58a3e-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="58a3e-145">Personnalisation du générateur de profils Visual</span><span class="sxs-lookup"><span data-stu-id="58a3e-145">Customizing the visual profiler</span></span>

<span data-ttu-id="58a3e-146">L’apparence et le comportement de Visual Profiler sont personnalisables via le profil de système de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="58a3e-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="58a3e-147">Pour plus d’informations, consultez [configuration du système de diagnostics](configuring-diagnostics.md) .</span><span class="sxs-lookup"><span data-stu-id="58a3e-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="58a3e-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58a3e-148">See also</span></span>

- [<span data-ttu-id="58a3e-149">Système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="58a3e-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="58a3e-150">Configuration du système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="58a3e-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
