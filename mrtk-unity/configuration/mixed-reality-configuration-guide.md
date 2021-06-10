---
title: Guide de configuration de la réalité mixte
description: Documentation pour configurer MRTK dans Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK,
ms.openlocfilehash: b714e01a0969b88a4ca7a3a5047bc5d61516e3f3
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345142"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="2eac1-104">Guide de configuration du profil du Toolkit de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2eac1-104">Mixed Reality Toolkit profile configuration guide</span></span>

![Logo MRTK](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="2eac1-106">La boîte à outils de réalité mixte centralise la plus grande partie de la configuration requise pour gérer le kit de tâches (à l’exception des « choses » du véritable Runtime).</span><span class="sxs-lookup"><span data-stu-id="2eac1-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="2eac1-107">Ce guide est une procédure pas à pas simple pour chacun des écrans de profil de configuration actuellement disponibles pour la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="2eac1-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="2eac1-108">Profil de configuration principal de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2eac1-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="2eac1-109">Le profil de configuration principal, qui est attaché au gameobject *MixedRealityToolkit* dans votre scène, fournit le point d’entrée principal de la boîte à outils dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="2eac1-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="2eac1-110">La boîte à outils de réalité mixte « verrouille » les écrans de configuration par défaut pour s’assurer que vous avez toujours un point de départ commun pour votre projet et il est recommandé de commencer à définir vos propres paramètres à mesure que votre projet évolue.</span><span class="sxs-lookup"><span data-stu-id="2eac1-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="2eac1-111">La configuration MRTK n’est pas modifiable en mode lecture.</span><span class="sxs-lookup"><span data-stu-id="2eac1-111">The MRTK configuration is not editable during play-mode.</span></span>

![Profil de configuration MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="2eac1-113">Tous les profils « par défaut » pour la réalité mixte Toolkit se trouvent dans le projet SDK dans le dossier ressources/MRTK/Kit de développement logiciel (SDK)/profils.</span><span class="sxs-lookup"><span data-stu-id="2eac1-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2eac1-114">DefaultHoloLens2ConfigurationProfile est optimisé pour HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2eac1-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="2eac1-115">Pour plus d’informations, consultez [profils](../features/profiles/profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="2eac1-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="2eac1-116">Lorsque vous ouvrez le profil de configuration principal de la réalité mixte, l’écran suivant s’affiche dans l’inspecteur :</span><span class="sxs-lookup"><span data-stu-id="2eac1-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="2eac1-117">Si vous sélectionnez un élément multimédia MixedRealityToolkitConfigurationProfile sans MixedRealityToolkit dans la scène, vous êtes invité à indiquer si vous souhaitez que le MRTK configure automatiquement la scène pour vous.</span><span class="sxs-lookup"><span data-stu-id="2eac1-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="2eac1-118">Toutefois, cette option est facultative, mais un objet MixedRealityToolkit actif doit être présent dans la scène pour accéder à tous les écrans de configuration.</span><span class="sxs-lookup"><span data-stu-id="2eac1-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="2eac1-119">Cela abrite la configuration active Runtime actuelle pour le projet.</span><span class="sxs-lookup"><span data-stu-id="2eac1-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="2eac1-120">À partir de là, vous pouvez accéder à tous les profils de configuration pour le MRTK, notamment :</span><span class="sxs-lookup"><span data-stu-id="2eac1-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="2eac1-121">Guide de configuration du profil du Toolkit de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2eac1-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="2eac1-122">Profil de configuration principal de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2eac1-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="2eac1-123">Paramètres d’expérience</span><span class="sxs-lookup"><span data-stu-id="2eac1-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="2eac1-124">Paramètres de l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="2eac1-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="2eac1-125">Paramètres du système d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="2eac1-126">Paramètres de visualisation des limites</span><span class="sxs-lookup"><span data-stu-id="2eac1-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="2eac1-127">Sélection du système de téléporting</span><span class="sxs-lookup"><span data-stu-id="2eac1-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="2eac1-128">Paramètres de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="2eac1-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="2eac1-129">Paramètres de diagnostic</span><span class="sxs-lookup"><span data-stu-id="2eac1-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="2eac1-130">Paramètres système de la scène</span><span class="sxs-lookup"><span data-stu-id="2eac1-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="2eac1-131">Paramètres des services supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2eac1-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="2eac1-132">Paramètres des actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="2eac1-133">Règles d’actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="2eac1-134">Configuration du pointeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="2eac1-135">Configuration des mouvements</span><span class="sxs-lookup"><span data-stu-id="2eac1-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="2eac1-136">Commandes vocales</span><span class="sxs-lookup"><span data-stu-id="2eac1-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="2eac1-137">Configuration du mappage du contrôleur</span><span class="sxs-lookup"><span data-stu-id="2eac1-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="2eac1-138">Paramètres de visualisation du contrôleur</span><span class="sxs-lookup"><span data-stu-id="2eac1-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="2eac1-139">Utilitaires de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="2eac1-140">Inspecteurs de service</span><span class="sxs-lookup"><span data-stu-id="2eac1-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="2eac1-141">Convertisseur de mémoire tampon de profondeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="2eac1-142">Modification des profils au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="2eac1-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="2eac1-143">Commutateur de profil d’initialisation de pré MRTK</span><span class="sxs-lookup"><span data-stu-id="2eac1-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="2eac1-144">Commutateur de profil actif</span><span class="sxs-lookup"><span data-stu-id="2eac1-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="2eac1-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2eac1-145">See also</span></span>](#see-also)

<span data-ttu-id="2eac1-146">Ces profils de configuration sont détaillés ci-dessous dans les sections qui s’y rapportent :</span><span class="sxs-lookup"><span data-stu-id="2eac1-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="2eac1-147">Paramètres d’expérience</span><span class="sxs-lookup"><span data-stu-id="2eac1-147">Experience settings</span></span>

<span data-ttu-id="2eac1-148">Situé sur la page de configuration principale de l’ensemble d’outils de réalité mixte, ce paramètre définit l’opération par défaut de l’échelle de l’environnement de la [réalité mixte](/windows/mixed-reality/coordinate-systems-in-unity) pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="2eac1-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="2eac1-149">Paramètres de caméra</span><span class="sxs-lookup"><span data-stu-id="2eac1-149">Camera settings</span></span>

<span data-ttu-id="2eac1-150">Les paramètres de l’appareil photo définissent la façon dont l’appareil photo sera configuré pour votre projet de réalité mixte, définissant les paramètres génériques de découpage, de qualité et de transparence.</span><span class="sxs-lookup"><span data-stu-id="2eac1-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="2eac1-151">Paramètres du système d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-151">Input system settings</span></span>

<span data-ttu-id="2eac1-152">Le projet de réalité mixte fournit un système d’entrée robuste et bien formé pour le routage de tous les événements d’entrée dans le projet, qui est sélectionné par défaut.</span><span class="sxs-lookup"><span data-stu-id="2eac1-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="2eac1-153">Derrière le système d’entrée fourni par le MRTK sont plusieurs autres systèmes, ils aident à piloter et à gérer les intertissages complexes nécessaires à l’abstraction de la complexité d’une infrastructure de réalité multiplateforme/de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="2eac1-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="2eac1-154">Chacun des profils individuels est détaillé ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2eac1-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="2eac1-155">Paramètres de focus</span><span class="sxs-lookup"><span data-stu-id="2eac1-155">Focus Settings</span></span>
- [<span data-ttu-id="2eac1-156">Paramètres des actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="2eac1-157">Règles d’actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="2eac1-158">Configuration du pointeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="2eac1-159">Configuration des mouvements</span><span class="sxs-lookup"><span data-stu-id="2eac1-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="2eac1-160">Commandes vocales</span><span class="sxs-lookup"><span data-stu-id="2eac1-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="2eac1-161">Configuration du mappage du contrôleur</span><span class="sxs-lookup"><span data-stu-id="2eac1-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="2eac1-162">Paramètres de visualisation du contrôleur</span><span class="sxs-lookup"><span data-stu-id="2eac1-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="2eac1-163">Paramètres de visualisation des limites</span><span class="sxs-lookup"><span data-stu-id="2eac1-163">Boundary visualization settings</span></span>

<span data-ttu-id="2eac1-164">Le système de limites traduit la limite perçue signalée par le système de limite/Guardian des plateformes sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="2eac1-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="2eac1-165">La configuration du visualiseur de limites vous donne la possibilité d’afficher automatiquement la limite enregistrée dans votre scène, en fonction de la position de l’utilisateur. La limite réagit également/met à jour en fonction de l’endroit où l’utilisateur téléporte dans la scène.</span><span class="sxs-lookup"><span data-stu-id="2eac1-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="2eac1-166">Sélection du système de téléporting</span><span class="sxs-lookup"><span data-stu-id="2eac1-166">Teleportation system selection</span></span>

<span data-ttu-id="2eac1-167">Le projet de réalité mixte fournit un système de téléportage complet pour la gestion des événements de téléportage dans le projet, qui est sélectionné par défaut.</span><span class="sxs-lookup"><span data-stu-id="2eac1-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="2eac1-168">Paramètres de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="2eac1-168">Spatial awareness settings</span></span>

<span data-ttu-id="2eac1-169">Le projet de réalité mixte fournit un système de sensibilisation spatiale reconstruit pour travailler avec des systèmes d’analyse spatiale dans le projet, qui est sélectionné par défaut.</span><span class="sxs-lookup"><span data-stu-id="2eac1-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="2eac1-170">La configuration de la sensibilisation spatiale de la réalité mixte vous permet de personnaliser le mode de démarrage du système, s’il est exécuté automatiquement au démarrage de l’application ou par la suite, et de définir les étendues du champ de la vue.</span><span class="sxs-lookup"><span data-stu-id="2eac1-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="2eac1-171">Il vous permet également de configurer les paramètres de maillage et de surface, de personnaliser davantage la façon dont votre projet comprend l’environnement qui vous est autour.</span><span class="sxs-lookup"><span data-stu-id="2eac1-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="2eac1-172">Cela s’applique uniquement aux appareils qui peuvent fournir un environnement analysé.</span><span class="sxs-lookup"><span data-stu-id="2eac1-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="2eac1-173">Paramètres de diagnostic</span><span class="sxs-lookup"><span data-stu-id="2eac1-173">Diagnostics settings</span></span>

<span data-ttu-id="2eac1-174">Une fonctionnalité facultative mais très utile du MRTK est la fonctionnalité de diagnostics de plug-in.</span><span class="sxs-lookup"><span data-stu-id="2eac1-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="2eac1-175">Le profil de diagnostic fournit plusieurs systèmes simples à surveiller pendant l’exécution du projet, y compris un commutateur d’activation/désactivation pratique pour activer/désactiver le panneau d’affichage dans la scène.</span><span class="sxs-lookup"><span data-stu-id="2eac1-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="2eac1-176">Paramètres système de la scène</span><span class="sxs-lookup"><span data-stu-id="2eac1-176">Scene system settings</span></span>

<span data-ttu-id="2eac1-177">Le MRTK fournit ce service facultatif pour vous aider à gérer le chargement/déchargement complexe des scènes.</span><span class="sxs-lookup"><span data-stu-id="2eac1-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="2eac1-178">Pour déterminer si le système de scène est adapté à votre projet, lisez le Guide de [prise en main du système de scène.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2eac1-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="2eac1-179">Paramètres des services supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2eac1-179">Additional services settings</span></span>

<span data-ttu-id="2eac1-180">L’une des zones les plus avancées du kit d’outils de réalité mixte est son implémentation de [modèle de localisateur de service](https://en.wikipedia.org/wiki/Service_locator_pattern) qui permet d’inscrire n’importe quel « service » avec l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="2eac1-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="2eac1-181">Cela permet d’étendre facilement le Framework avec de nouvelles fonctionnalités et de nouveaux systèmes, mais permet également aux projets de tirer parti de ces fonctionnalités pour inscrire leurs propres composants d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2eac1-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="2eac1-182">Tout service inscrit obtient toujours l’avantage total de tous les événements Unity, sans la surcharge et le coût de l’implémentation d’un monocomportement ou de modèles de singletons sourds.</span><span class="sxs-lookup"><span data-stu-id="2eac1-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="2eac1-183">Cela permet aux composants C# purs sans surcharge de scène d’exécuter à la fois les processus de premier plan et d’arrière-plan, par exemple les systèmes de génération, la logique du jeu d’exécution ou pratiquement tout autre.</span><span class="sxs-lookup"><span data-stu-id="2eac1-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="2eac1-184">Paramètres des actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-184">Input actions settings</span></span>

<span data-ttu-id="2eac1-185">Les actions d’entrée permettent d’extraire les interactions physiques et les entrées d’un projet d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2eac1-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="2eac1-186">Toutes les entrées physiques (des contrôleurs/mains/souris, etc.) sont traduites en une action d’entrée logique pour une utilisation dans votre projet d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2eac1-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="2eac1-187">Cela garantit quel que soit l’emplacement d’origine de l’entrée, votre projet implémente simplement ces actions comme « choses à faire » ou « interagir avec » dans vos scènes.</span><span class="sxs-lookup"><span data-stu-id="2eac1-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="2eac1-188">Pour créer une nouvelle action d’entrée, cliquez simplement sur le bouton « Ajouter une nouvelle action », puis entrez un nom convivial pour ce qu’elle représente.</span><span class="sxs-lookup"><span data-stu-id="2eac1-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="2eac1-189">Vous devez alors uniquement sélectionner un axe (le type de données) que l’action doit transmettre, ou, dans le cas de contrôleurs physiques, le type d’entrée physique auquel elle peut être jointe, par exemple :</span><span class="sxs-lookup"><span data-stu-id="2eac1-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="2eac1-190">Contrainte d’axe</span><span class="sxs-lookup"><span data-stu-id="2eac1-190">Axis Constraint</span></span> | <span data-ttu-id="2eac1-191">Type de données</span><span class="sxs-lookup"><span data-stu-id="2eac1-191">Data Type</span></span> | <span data-ttu-id="2eac1-192">Description</span><span class="sxs-lookup"><span data-stu-id="2eac1-192">Description</span></span> | <span data-ttu-id="2eac1-193">Exemple d’utilisation</span><span class="sxs-lookup"><span data-stu-id="2eac1-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="2eac1-194">Aucun</span><span class="sxs-lookup"><span data-stu-id="2eac1-194">None</span></span> | <span data-ttu-id="2eac1-195">Pas de données</span><span class="sxs-lookup"><span data-stu-id="2eac1-195">No data</span></span> | <span data-ttu-id="2eac1-196">Utilisé pour une action ou un événement vide</span><span class="sxs-lookup"><span data-stu-id="2eac1-196">Used for an empty action or event</span></span> | <span data-ttu-id="2eac1-197">Déclencheur d’événement</span><span class="sxs-lookup"><span data-stu-id="2eac1-197">Event Trigger</span></span> |
| <span data-ttu-id="2eac1-198">Brut (réservé)</span><span class="sxs-lookup"><span data-stu-id="2eac1-198">Raw (reserved)</span></span> | <span data-ttu-id="2eac1-199">object</span><span class="sxs-lookup"><span data-stu-id="2eac1-199">object</span></span> | <span data-ttu-id="2eac1-200">Paramètres réservés pour un usage ultérieur</span><span class="sxs-lookup"><span data-stu-id="2eac1-200">Reserved for future use</span></span> | <span data-ttu-id="2eac1-201">N/A</span><span class="sxs-lookup"><span data-stu-id="2eac1-201">N/A</span></span> |
| <span data-ttu-id="2eac1-202">Digital</span><span class="sxs-lookup"><span data-stu-id="2eac1-202">Digital</span></span> | <span data-ttu-id="2eac1-203">bool</span><span class="sxs-lookup"><span data-stu-id="2eac1-203">bool</span></span> | <span data-ttu-id="2eac1-204">Données de type Boolean on ou OFF</span><span class="sxs-lookup"><span data-stu-id="2eac1-204">A boolean on or off type data</span></span> | <span data-ttu-id="2eac1-205">Bouton de contrôleur</span><span class="sxs-lookup"><span data-stu-id="2eac1-205">A controller button</span></span> |
| <span data-ttu-id="2eac1-206">Axe unique</span><span class="sxs-lookup"><span data-stu-id="2eac1-206">Single Axis</span></span> | <span data-ttu-id="2eac1-207">float</span><span class="sxs-lookup"><span data-stu-id="2eac1-207">float</span></span> | <span data-ttu-id="2eac1-208">Une valeur de données de précision unique</span><span class="sxs-lookup"><span data-stu-id="2eac1-208">A single precision data value</span></span> | <span data-ttu-id="2eac1-209">Une entrée étendue, par exemple un déclencheur</span><span class="sxs-lookup"><span data-stu-id="2eac1-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="2eac1-210">Axe double</span><span class="sxs-lookup"><span data-stu-id="2eac1-210">Dual Axis</span></span> | <span data-ttu-id="2eac1-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="2eac1-211">Vector2</span></span> | <span data-ttu-id="2eac1-212">Une date de type float double pour plusieurs axes</span><span class="sxs-lookup"><span data-stu-id="2eac1-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="2eac1-213">Un dpad ou un stick analogique</span><span class="sxs-lookup"><span data-stu-id="2eac1-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="2eac1-214">Trois positions DDL</span><span class="sxs-lookup"><span data-stu-id="2eac1-214">Three Dof Position</span></span> | <span data-ttu-id="2eac1-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="2eac1-215">Vector3</span></span> | <span data-ttu-id="2eac1-216">Données de type positionnel de à l’aide de l’axe 3 flottant</span><span class="sxs-lookup"><span data-stu-id="2eac1-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="2eac1-217">contrôleur de style de position 3D uniquement</span><span class="sxs-lookup"><span data-stu-id="2eac1-217">3D position style only controller</span></span> |
| <span data-ttu-id="2eac1-218">Rotation à trois DDL</span><span class="sxs-lookup"><span data-stu-id="2eac1-218">Three Dof Rotation</span></span> | <span data-ttu-id="2eac1-219">Quaternion</span><span class="sxs-lookup"><span data-stu-id="2eac1-219">Quaternion</span></span> | <span data-ttu-id="2eac1-220">Entrée de rotation uniquement avec 4 axes à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="2eac1-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="2eac1-221">Un contrôleur de style à trois degrés, par exemple Oculus Go Controller</span><span class="sxs-lookup"><span data-stu-id="2eac1-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="2eac1-222">Six DDL</span><span class="sxs-lookup"><span data-stu-id="2eac1-222">Six Dof</span></span> | <span data-ttu-id="2eac1-223">Pose de réalité mixte (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="2eac1-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="2eac1-224">Entrée de style de position et de rotation avec les composants Vector3 et Quaternion</span><span class="sxs-lookup"><span data-stu-id="2eac1-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="2eac1-225">Contrôleur de mouvement ou pointeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="2eac1-226">Les événements qui utilisent des actions d’entrée ne sont pas limités aux contrôleurs physiques et peuvent toujours être utilisés dans le projet pour que les effets de Runtime génèrent de nouvelles actions.</span><span class="sxs-lookup"><span data-stu-id="2eac1-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="2eac1-227">Les actions d’entrée sont l’un des quelques composants qui ne peuvent pas être modifiés au moment de l’exécution ; ils ne sont qu’une configuration au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="2eac1-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="2eac1-228">Ce profil ne doit pas être échangé pendant que le projet est en cours d’exécution en raison de la dépendance entre l’infrastructure (et vos projets) et l’ID généré pour chaque action.</span><span class="sxs-lookup"><span data-stu-id="2eac1-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="2eac1-229">Règles d’actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="2eac1-229">Input actions rules</span></span>

<span data-ttu-id="2eac1-230">Les règles d’action d’entrée permettent de traduire automatiquement un événement déclenché pour une action d’entrée en différentes actions en fonction de sa valeur de données.</span><span class="sxs-lookup"><span data-stu-id="2eac1-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="2eac1-231">Celles-ci sont gérées en toute transparence dans le cadre et n’entraînent pas de coûts de performances.</span><span class="sxs-lookup"><span data-stu-id="2eac1-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="2eac1-232">Par exemple, la conversion de l’événement d’entrée d’un seul axe double à partir d’un DPad dans en 4 actions « dpad up »/« DPad OFF »/« dpad Left »/« dpad Right » correspondantes (comme indiqué dans l’image ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="2eac1-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="2eac1-233">Cela peut également se faire dans votre propre code.</span><span class="sxs-lookup"><span data-stu-id="2eac1-233">This could also be done in your own code.</span></span> <span data-ttu-id="2eac1-234">Toutefois, comme il s’agit d’un modèle très courant, le Framework fournit un mécanisme permettant d’effectuer cette opération « prête à l’emploi »</span><span class="sxs-lookup"><span data-stu-id="2eac1-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="2eac1-235">Les règles d’action d’entrée peuvent être configurées pour l’un des axes d’entrée disponibles.</span><span class="sxs-lookup"><span data-stu-id="2eac1-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="2eac1-236">Toutefois, les actions d’entrée d’un type d’axe peuvent être traduites en une autre action d’entrée du même type d’axe.</span><span class="sxs-lookup"><span data-stu-id="2eac1-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="2eac1-237">Vous pouvez mapper une action à deux axes sur une autre action d’axe double, mais pas sur une action numérique ou aucune.</span><span class="sxs-lookup"><span data-stu-id="2eac1-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Profil des règles d’action d’entrée](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="2eac1-239">Configuration du pointeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-239">Pointer configuration</span></span>

<span data-ttu-id="2eac1-240">Les pointeurs sont utilisés pour piloter l’interactivité dans la scène à partir de n’importe quel appareil d’entrée, ce qui donne à la fois une direction et un test de positionnement avec n’importe quel objet dans une scène (qui a un conflit attaché ou est un composant d’interface utilisateur).</span><span class="sxs-lookup"><span data-stu-id="2eac1-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="2eac1-241">Les pointeurs sont configurés automatiquement par défaut pour les contrôleurs, les casques (en regard/Focus) et l’entrée de souris/toucher.</span><span class="sxs-lookup"><span data-stu-id="2eac1-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="2eac1-242">Les pointeurs peuvent également être visualisés dans la scène active à l’aide de l’un des nombreux composants de ligne fournis par le Toolkit de réalité mixte, ou de l’un de vos propres composants s’ils implémentent l’interface MRTK IMixedRealityPointer.</span><span class="sxs-lookup"><span data-stu-id="2eac1-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="2eac1-243">Étendue de pointage : détermine l’étendue de pointage globale pour tous les pointeurs, y compris le point de regard.</span><span class="sxs-lookup"><span data-stu-id="2eac1-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="2eac1-244">Pointer les masques de couche Raycast : détermine les pointeurs de couches à Raycast.</span><span class="sxs-lookup"><span data-stu-id="2eac1-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="2eac1-245">Déboguer les rayons de pointage : un programme d’assistance de débogage pour visualiser les rayons utilisés pour Raycasting.</span><span class="sxs-lookup"><span data-stu-id="2eac1-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="2eac1-246">Déboguer les rayons de pointage de couleur : un ensemble de couleurs à utiliser pour la visualisation.</span><span class="sxs-lookup"><span data-stu-id="2eac1-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="2eac1-247">Curseur en regard Prefab : permet de spécifier facilement un curseur en forme de pointage global pour une scène.</span><span class="sxs-lookup"><span data-stu-id="2eac1-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="2eac1-248">Il existe un autre bouton d’assistance pour accéder rapidement au fournisseur de regard pour remplacer des valeurs spécifiques pour le point de regard, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2eac1-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="2eac1-249">Configuration des mouvements</span><span class="sxs-lookup"><span data-stu-id="2eac1-249">Gestures configuration</span></span>

<span data-ttu-id="2eac1-250">Les gestes sont une implémentation spécifique au système qui vous permet d’affecter des actions d’entrée aux diverses méthodes d’entrée de « geste » fournies par divers kits de développement logiciel (par exemple, HoloLens).</span><span class="sxs-lookup"><span data-stu-id="2eac1-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="2eac1-251">L’implémentation des mouvements actuels concerne le HoloLens uniquement et sera améliorée pour les autres systèmes, car ils seront ajoutés à la boîte à outils à l’avenir (aucune date pour le moment).</span><span class="sxs-lookup"><span data-stu-id="2eac1-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="2eac1-252">Commandes vocales</span><span class="sxs-lookup"><span data-stu-id="2eac1-252">Speech commands</span></span>

<span data-ttu-id="2eac1-253">À l’instar des gestes, certaines plateformes Runtime fournissent également une fonctionnalité de « parole à texte » intelligente, avec la possibilité de générer des commandes qui peuvent être reçues par un projet Unity.</span><span class="sxs-lookup"><span data-stu-id="2eac1-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="2eac1-254">Ce profil de configuration vous permet de configurer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2eac1-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="2eac1-255">Paramètres généraux : « comportement de démarrage » défini sur démarrage automatique ou démarrage manuel détermine s’il faut initialiser KeywordRecognizer au démarrage du système d’entrée ou laisser le projet décider quand initialiser le KeywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="2eac1-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="2eac1-256">« Niveau de confiance de reconnaissance » est utilisé pour initialiser l' [API KeywordRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) de l’unité</span><span class="sxs-lookup"><span data-stu-id="2eac1-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="2eac1-257">Commandes vocales : enregistre les « mots » et les convertit en actions d’entrée qui peuvent être reçues par votre projet.</span><span class="sxs-lookup"><span data-stu-id="2eac1-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="2eac1-258">Ils peuvent également être joints aux actions du clavier, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2eac1-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2eac1-259">Actuellement, le système ne prend en charge que la reconnaissance vocale sur les plateformes Windows 10, par exemple HoloLens et Windows 10 Desktop. il sera amélioré pour les autres systèmes tels qu’ils sont ajoutés à MRTK à l’avenir (aucune date n’est encore).</span><span class="sxs-lookup"><span data-stu-id="2eac1-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="2eac1-260">Configuration du mappage du contrôleur</span><span class="sxs-lookup"><span data-stu-id="2eac1-260">Controller mapping configuration</span></span>

<span data-ttu-id="2eac1-261">L’un des écrans de configuration principaux pour la réalité mixte Toolkit est la possibilité de configurer et de mapper les différents types de contrôleurs qui peuvent être utilisés par votre projet.</span><span class="sxs-lookup"><span data-stu-id="2eac1-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="2eac1-262">L’écran de configuration ci-dessous vous permet de configurer les contrôleurs actuellement reconnus par la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="2eac1-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="2eac1-263">MRTK fournit une configuration par défaut pour les contrôleurs/systèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="2eac1-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="2eac1-264">Souris (y compris la prise en charge de la souris spatiale 3D)</span><span class="sxs-lookup"><span data-stu-id="2eac1-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="2eac1-265">Touch Screen</span><span class="sxs-lookup"><span data-stu-id="2eac1-265">Touch Screen</span></span>
- <span data-ttu-id="2eac1-266">Manettes Xbox</span><span class="sxs-lookup"><span data-stu-id="2eac1-266">Xbox controllers</span></span>
- <span data-ttu-id="2eac1-267">Contrôleurs de réalité mixte Windows</span><span class="sxs-lookup"><span data-stu-id="2eac1-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="2eac1-268">Gestes HoloLens</span><span class="sxs-lookup"><span data-stu-id="2eac1-268">HoloLens Gestures</span></span>
- <span data-ttu-id="2eac1-269">Contrôleurs à baguettes vives HTC</span><span class="sxs-lookup"><span data-stu-id="2eac1-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="2eac1-270">Contrôleurs tactiles Oculus</span><span class="sxs-lookup"><span data-stu-id="2eac1-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="2eac1-271">Contrôleur distant Oculus</span><span class="sxs-lookup"><span data-stu-id="2eac1-271">Oculus Remote controller</span></span>
- <span data-ttu-id="2eac1-272">Appareils OpenVR génériques (utilisateurs expérimentés uniquement)</span><span class="sxs-lookup"><span data-stu-id="2eac1-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="2eac1-273">En cliquant sur l’image de l’un des systèmes de contrôleur prédéfinis, vous pouvez configurer une seule action d’entrée pour toutes les entrées correspondantes. par exemple, consultez l’écran de configuration du contrôleur tactile Oculus ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2eac1-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="2eac1-274">Il existe également un écran avancé pour la configuration d’autres contrôleurs d’entrée OpenVR ou Unity qui ne sont pas identifiés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2eac1-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="2eac1-275">Paramètres de visualisation du contrôleur</span><span class="sxs-lookup"><span data-stu-id="2eac1-275">Controller visualization settings</span></span>

<span data-ttu-id="2eac1-276">En plus du mappage de contrôleur, un profil de configuration distinct est fourni pour personnaliser la façon dont vos contrôleurs sont présentés dans vos scènes.</span><span class="sxs-lookup"><span data-stu-id="2eac1-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="2eac1-277">Cela peut être configuré à un « global » (toutes les instances d’un contrôleur pour une main spécifique) ou spécifique à un type ou à une main de contrôleur individuel.</span><span class="sxs-lookup"><span data-stu-id="2eac1-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="2eac1-278">MRTK prend également en charge les modèles de contrôleur SDK natifs pour Windows Mixed Reality et OpenVR.</span><span class="sxs-lookup"><span data-stu-id="2eac1-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="2eac1-279">Ceux-ci sont chargés en tant que GameObjects dans votre scène et positionnés à l’aide du suivi du contrôleur de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="2eac1-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="2eac1-280">Si la représentation de votre contrôleur dans la scène doit être décalée à partir de la position du contrôleur physique, il suffit de définir ce décalage par rapport à l’Prefab du modèle de contrôleur (par exemple, en définissant la position de la transformation du Prefab du contrôleur avec une position de décalage).</span><span class="sxs-lookup"><span data-stu-id="2eac1-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="2eac1-281">Utilitaires de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-281">Editor utilities</span></span>

<span data-ttu-id="2eac1-282">Les utilitaires suivants fonctionnent uniquement dans l’éditeur et sont utiles pour améliorer la productivité du développement.</span><span class="sxs-lookup"><span data-stu-id="2eac1-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilitaires de configuration de l’éditeur MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="2eac1-284">Inspecteurs de service</span><span class="sxs-lookup"><span data-stu-id="2eac1-284">Service inspectors</span></span>

<span data-ttu-id="2eac1-285">Les inspecteurs de service sont une fonctionnalité d’éditeur uniquement qui génère des objets dans la scène représentant des services actifs.</span><span class="sxs-lookup"><span data-stu-id="2eac1-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="2eac1-286">La sélection de ces objets permet d’afficher les inspecteurs qui proposent des liens vers la documentation, de contrôler les visualisations de l’éditeur et de comprendre l’état du service.</span><span class="sxs-lookup"><span data-stu-id="2eac1-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="2eac1-287">Vous pouvez activer les inspecteurs de service en cochant la case *utiliser les inspecteurs de service* sous paramètres de l' *éditeur* dans le profil de configuration.</span><span class="sxs-lookup"><span data-stu-id="2eac1-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="2eac1-288">Convertisseur de mémoire tampon de profondeur</span><span class="sxs-lookup"><span data-stu-id="2eac1-288">Depth buffer renderer</span></span>

<span data-ttu-id="2eac1-289">Le partage de la mémoire tampon de profondeur avec certaines plateformes de réalité mixte peut améliorer la [stabilisation des hologrammes](../performance/hologram-stabilization.md).</span><span class="sxs-lookup"><span data-stu-id="2eac1-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="2eac1-290">Par exemple, la plateforme Windows Mixed Reality peut modifier la scène rendue par pixel pour tenir compte des mouvements de têtes subtiles pendant le temps nécessaire pour afficher un frame.</span><span class="sxs-lookup"><span data-stu-id="2eac1-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="2eac1-291">Toutefois, ces techniques requièrent des tampons de profondeur avec des données précises pour savoir où et dans quelle mesure la géométrie provient de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2eac1-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="2eac1-292">Pour s’assurer qu’une scène effectue le rendu de toutes les données nécessaires dans le tampon de profondeur, les développeurs peuvent basculer la fonctionnalité de *tampon de profondeur de rendu* sous les paramètres de l' *éditeur* dans le profil de configuration.</span><span class="sxs-lookup"><span data-stu-id="2eac1-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="2eac1-293">Cela prend la mémoire tampon de profondeur actuelle et l’affiche en couleur dans l’affichage scène en appliquant un effet de suivi, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) à l’appareil photo principal.</span><span class="sxs-lookup"><span data-stu-id="2eac1-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="2eac1-294">![Utilitaire de tampon ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>de profondeur de rendu le cylindre bleu dans la scène a un matériau avec ZWrite désactivé, donc aucune donnée de profondeur n’est écrite</sup></span><span class="sxs-lookup"><span data-stu-id="2eac1-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="2eac1-295">Modification des profils au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="2eac1-295">Changing profiles at runtime</span></span>

<span data-ttu-id="2eac1-296">Il est possible de mettre à jour les profils au moment de l’exécution, et il y a généralement deux scénarios et périodes différents dans lesquels cela est utile :</span><span class="sxs-lookup"><span data-stu-id="2eac1-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="2eac1-297">**Commutateur de configuration d’initialisation avant MRTK**: au démarrage, avant l’initialisation du MRTK, le profil devient actif, en remplaçant le profil qui n’est pas encore utilisé pour activer ou désactiver les différentes fonctionnalités en fonction des fonctionnalités de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="2eac1-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="2eac1-298">Par exemple, si l’expérience s’exécute en VR qui n’a pas de matériel de mappage spatial, il n’est probablement pas judicieux d’activer le composant de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="2eac1-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="2eac1-299">**Commutateur de profil actif**: après le démarrage, une fois que le MRTK est initialisé et qu’un profil est devenu actif, échangez le profil actuellement utilisé pour modifier la façon dont certaines fonctionnalités se comportent.</span><span class="sxs-lookup"><span data-stu-id="2eac1-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="2eac1-300">Par exemple, il peut y avoir une sous-expérience spécifique dans l’application qui souhaite que les pointeurs les plus éloignés soient complètement supprimés.</span><span class="sxs-lookup"><span data-stu-id="2eac1-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="2eac1-301">Commutateur de profil d’initialisation de pré MRTK</span><span class="sxs-lookup"><span data-stu-id="2eac1-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="2eac1-302">Pour ce faire, vous pouvez attacher un monocomportement (exemple ci-dessous) qui s’exécute avant l’initialisation MRTK (c.-à-d. éveillé ()).</span><span class="sxs-lookup"><span data-stu-id="2eac1-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="2eac1-303">Notez que le script (c’est-à-dire l’appel à `SetProfileBeforeInitialization` ) doit être exécuté avant le `MixedRealityToolkit` script, ce qui peut être effectué en définissant des paramètres d’ordre d’exécution de [script](https://docs.unity3d.com/Manual/class-MonoManager.html).</span><span class="sxs-lookup"><span data-stu-id="2eac1-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="2eac1-304">Au lieu de « profileToUse », il est possible d’avoir un ensemble arbitraire de profils qui s’appliquent à des plateformes spécifiques (par exemple, une pour HoloLens 1, une pour VR, une pour HoloLens 2, etc.).</span><span class="sxs-lookup"><span data-stu-id="2eac1-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="2eac1-305">Il est possible d’utiliser d’autres indicateurs (par exemple https://docs.unity3d.com/ScriptReference/SystemInfo.html , ou si l’appareil photo est opaque/transparent), pour déterminer le profil à charger.</span><span class="sxs-lookup"><span data-stu-id="2eac1-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="2eac1-306">Commutateur de profil actif</span><span class="sxs-lookup"><span data-stu-id="2eac1-306">Active profile switch</span></span>

<span data-ttu-id="2eac1-307">Pour ce faire, vous pouvez affecter `MixedRealityToolkit.Instance.ActiveProfile` à la propriété un nouveau profil qui remplace le profil actif.</span><span class="sxs-lookup"><span data-stu-id="2eac1-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="2eac1-308">Remarque Lorsque vous définissez au moment de l' `ActiveProfile` exécution, la destruction des services en cours d’exécution se produit après le dernier LateUpdate () de tous les services, et l’instanciation et l’initialisation des services associés au nouveau profil se produisent avant la première mise à jour () de tous les services.</span><span class="sxs-lookup"><span data-stu-id="2eac1-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="2eac1-309">Une hésitation d’application notable peut se produire au cours de ce processus.</span><span class="sxs-lookup"><span data-stu-id="2eac1-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="2eac1-310">En outre, tout script avec une priorité plus élevée que le `MixedRealityToolkit` script peut entrer dans sa mise à jour avant que le nouveau profil soit correctement configuré.</span><span class="sxs-lookup"><span data-stu-id="2eac1-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="2eac1-311">Pour plus d’informations sur la priorité de script, consultez [paramètres de l’ordre d’exécution des scripts](https://docs.unity3d.com/Manual/class-MonoManager.html) .</span><span class="sxs-lookup"><span data-stu-id="2eac1-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="2eac1-312">Dans le processus de basculement de profil, l’appareil photo de l’interface utilisateur existante reste inchangé, ce qui garantit que les composants de l’interface utilisateur Unity qui nécessitent un canevas fonctionnent toujours après le commutateur.</span><span class="sxs-lookup"><span data-stu-id="2eac1-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="2eac1-313">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2eac1-313">See also</span></span>

- [<span data-ttu-id="2eac1-314">Stabilisation d’hologramme</span><span class="sxs-lookup"><span data-stu-id="2eac1-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)