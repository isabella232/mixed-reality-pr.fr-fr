---
title: Configuration des diagnostics
description: Documentation sur la configuration des diagnostics dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 211ee2ed06ba9b13bd90169bcc7ee50da4594034
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121797"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="4e88d-104">Configuration du système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="4e88d-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="4e88d-105">Paramètres généraux :</span><span class="sxs-lookup"><span data-stu-id="4e88d-105">General settings</span></span>

![Paramètres généraux des diagnostics](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="4e88d-107">Activer la journalisation documentée</span><span class="sxs-lookup"><span data-stu-id="4e88d-107">Enable verbose logging</span></span>

<span data-ttu-id="4e88d-108">Indique si la journalisation MRTK détaillée est activée.</span><span class="sxs-lookup"><span data-stu-id="4e88d-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="4e88d-109">La valeur par défaut est false, mais peut être activée pour effectuer des suivis détaillés permettant à l’équipe MRTK de déboguer/explorer les problèmes.</span><span class="sxs-lookup"><span data-stu-id="4e88d-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="4e88d-110">Par exemple, lors de l’enregistrement d’un problème, l’attachement des journaux du lecteur Unity (à partir de l’éditeur ou du lecteur) peut aider à réduire la source des bogues et des problèmes.</span><span class="sxs-lookup"><span data-stu-id="4e88d-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="4e88d-111">Notez que cette option est indépendante du fait que le système de diagnostics soit activé ou non, ce qui s’affiche sous le système de diagnostics, car il s’agit d’une option de journalisation, mais qui, au final, fonctionne à un niveau supérieur, car il affecte la journalisation sur l’ensemble du code base MRTK.</span><span class="sxs-lookup"><span data-stu-id="4e88d-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="4e88d-112">Afficher les diagnostics</span><span class="sxs-lookup"><span data-stu-id="4e88d-112">Show diagnostics</span></span>

<span data-ttu-id="4e88d-113">Indique si le système de diagnostics doit afficher ou non les options de diagnostic configurées.</span><span class="sxs-lookup"><span data-stu-id="4e88d-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="4e88d-114">Lorsque cette option est désactivée, toutes les options de diagnostic configurées sont masquées.</span><span class="sxs-lookup"><span data-stu-id="4e88d-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="4e88d-115">Paramètres du profileur</span><span class="sxs-lookup"><span data-stu-id="4e88d-115">Profiler settings</span></span>

![Paramètres du profileur de diagnostic](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="4e88d-117">Afficher le profileur</span><span class="sxs-lookup"><span data-stu-id="4e88d-117">Show profiler</span></span>

<span data-ttu-id="4e88d-118">Indique si le générateur de profils visuels doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="4e88d-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="4e88d-119">Taux d’échantillonnage de trame</span><span class="sxs-lookup"><span data-stu-id="4e88d-119">Frame sample rate</span></span>

<span data-ttu-id="4e88d-120">Durée, en secondes, de collecte des frames pour le calcul de la fréquence d’images.</span><span class="sxs-lookup"><span data-stu-id="4e88d-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="4e88d-121">La plage est comprise entre 0 et 5 secondes.</span><span class="sxs-lookup"><span data-stu-id="4e88d-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="4e88d-122">Ancre de fenêtre</span><span class="sxs-lookup"><span data-stu-id="4e88d-122">Window anchor</span></span>

<span data-ttu-id="4e88d-123">À quelle partie du port d’affichage la fenêtre du profileur doit-elle être ancrée.</span><span class="sxs-lookup"><span data-stu-id="4e88d-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="4e88d-124">La valeur par défaut est Lower Center.</span><span class="sxs-lookup"><span data-stu-id="4e88d-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="4e88d-125">Décalage de la fenêtre</span><span class="sxs-lookup"><span data-stu-id="4e88d-125">Window offset</span></span>

<span data-ttu-id="4e88d-126">Décalage, à partir du centre du port d’affichage, pour placer le générateur de profils Visual.</span><span class="sxs-lookup"><span data-stu-id="4e88d-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="4e88d-127">Le décalage sera dans le sens de la propriété d’ancrage de la *fenêtre* .</span><span class="sxs-lookup"><span data-stu-id="4e88d-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="4e88d-128">Échelle de fenêtre</span><span class="sxs-lookup"><span data-stu-id="4e88d-128">Window scale</span></span>

<span data-ttu-id="4e88d-129">Multiplicateur de taille appliqué à la fenêtre du profileur.</span><span class="sxs-lookup"><span data-stu-id="4e88d-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="4e88d-130">Par exemple, si vous définissez la valeur sur 2, la taille de la fenêtre sera double.</span><span class="sxs-lookup"><span data-stu-id="4e88d-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="4e88d-131">Fenêtre suivre la vitesse</span><span class="sxs-lookup"><span data-stu-id="4e88d-131">Window follow speed</span></span>

<span data-ttu-id="4e88d-132">Vitesse à laquelle déplacer la fenêtre du profileur pour maintenir la visibilité dans le port d’affichage.</span><span class="sxs-lookup"><span data-stu-id="4e88d-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="4e88d-133">Contrôle du système de diagnostics par programmation</span><span class="sxs-lookup"><span data-stu-id="4e88d-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="4e88d-134">Il est également possible d’activer ou de désactiver la visibilité du système de diagnostic et du profileur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4e88d-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="4e88d-135">Par exemple, le code ci-dessous masque le système de diagnostic et le profileur.</span><span class="sxs-lookup"><span data-stu-id="4e88d-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="4e88d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e88d-136">See also</span></span>

- [<span data-ttu-id="4e88d-137">Système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="4e88d-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="4e88d-138">Utilisation du générateur de profils Visual</span><span class="sxs-lookup"><span data-stu-id="4e88d-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
