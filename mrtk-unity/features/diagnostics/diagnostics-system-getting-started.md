---
title: Système de diagnostic - Bien démarrer
description: documentation pour activer et désactiver les diagnostics dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 66d68902dd9ffa36a5b30c1130a8640d154ac5e1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144719"
---
# <a name="diagnostic-system"></a><span data-ttu-id="64e96-104">Système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="64e96-104">Diagnostic system</span></span>

<span data-ttu-id="64e96-105">Le système de diagnostic de la réalité mixte Toolkit fournit des outils de diagnostic qui s’exécutent dans l’application pour permettre l’analyse des problèmes liés aux applications.</span><span class="sxs-lookup"><span data-stu-id="64e96-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="64e96-106">La première version du système de diagnostic contient le [Générateur de profils Visual](using-visual-profiler.md) pour permettre l’analyse des problèmes de performances lors de l’utilisation de l’application.</span><span class="sxs-lookup"><span data-stu-id="64e96-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="64e96-107">Prise en main</span><span class="sxs-lookup"><span data-stu-id="64e96-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64e96-108">Il est **_vivement_** recommandé d’activer le système de diagnostic tout au long du cycle de développement du produit et de désactiver la dernière modification avant de générer et de publier la version finale.</span><span class="sxs-lookup"><span data-stu-id="64e96-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="64e96-109">Il existe deux étapes clés pour commencer à utiliser le système de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="64e96-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="64e96-110">[Activer](#enable-diagnostics) le système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="64e96-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="64e96-111">[Configurer](#configure-diagnostic-options) les options de diagnostic</span><span class="sxs-lookup"><span data-stu-id="64e96-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="64e96-112">Activation des diagnostics</span><span class="sxs-lookup"><span data-stu-id="64e96-112">Enable diagnostics</span></span>

<span data-ttu-id="64e96-113">Le système de diagnostic est géré par l’objet MixedRealityToolkit (ou un autre composant d' [inscription de service](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="64e96-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="64e96-114">Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="64e96-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="64e96-115">Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.</span><span class="sxs-lookup"><span data-stu-id="64e96-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="64e96-116">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="64e96-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="64e96-118">Naviguez dans le panneau de l’inspecteur jusqu’à la section système de diagnostic et cochez la case Activer</span><span class="sxs-lookup"><span data-stu-id="64e96-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="64e96-119">Sélectionner l’implémentation du système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="64e96-119">Select the Diagnostics System implementation</span></span>

    ![Sélectionner l’implémentation du système de diagnostic](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="64e96-121">Les utilisateurs du profil par défaut `DefaultMixedRealityToolkitConfigurationProfile` (ressources/MRTK/Kit de développement logiciel (SDK)/profils) disposent du système de diagnostic préconfiguré pour utiliser l' [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) objet.</span><span class="sxs-lookup"><span data-stu-id="64e96-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="64e96-122">Configurer les options de diagnostic</span><span class="sxs-lookup"><span data-stu-id="64e96-122">Configure diagnostic options</span></span>

<span data-ttu-id="64e96-123">Le système de diagnostics utilise un profil de configuration pour spécifier les composants à afficher et pour configurer leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="64e96-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="64e96-124">Pour plus d’informations sur les paramètres des composants disponibles, consultez [configuration du système de diagnostics](configuring-diagnostics.md) .</span><span class="sxs-lookup"><span data-stu-id="64e96-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64e96-125">Bien qu’il soit possible d’utiliser le mode de lecture d’Unity tout en développant des applications sans nécessiter les étapes de création et de déploiement, il est important d’évaluer les résultats du système de diagnostic à l’aide d’une application compilée qui s’exécute sur le matériel et la plateforme cibles.</span><span class="sxs-lookup"><span data-stu-id="64e96-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="64e96-126">Les diagnostics de performances, tels que le [Générateur de profils visuels](using-visual-profiler.md), peuvent ne pas refléter avec précision les performances réelles des applications lorsqu’elles sont exécutées à partir de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="64e96-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="64e96-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64e96-127">See also</span></span>

- [<span data-ttu-id="64e96-128">Documentation de l’API de diagnostic</span><span class="sxs-lookup"><span data-stu-id="64e96-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="64e96-129">Configuration du système de diagnostic</span><span class="sxs-lookup"><span data-stu-id="64e96-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="64e96-130">Utilisation du générateur de profils Visual</span><span class="sxs-lookup"><span data-stu-id="64e96-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
