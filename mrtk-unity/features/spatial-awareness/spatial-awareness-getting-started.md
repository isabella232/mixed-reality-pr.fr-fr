---
title: Reconnaissance spatiale
description: décrit la sensibilisation spatiale dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 776033dbb4736ccaa44cdb683c4fce284758a51c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144466"
---
# <a name="spatial-awareness"></a><span data-ttu-id="fe0ef-104">Reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="fe0ef-104">Spatial Awareness</span></span>

![Reconnaissance spatiale](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="fe0ef-106">Le système de sensibilisation spatiale offre une reconnaissance environnementale réaliste dans les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="fe0ef-107">Une fois introduit sur Microsoft HoloLens, la sensibilisation spatiale a fourni un ensemble de mailles représentant la géométrie de l’environnement, qui permettait des interactions attrayantes entre les hologrammes et le monde réel.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="fe0ef-108">À ce stade, le kit d’outils de réalité mixte n’est pas fourni avec des algorithmes de compréhension spatiale tels qu’ils ont été empaquetés à l’origine dans le HoloToolkit.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="fe0ef-109">La compréhension spatiale implique généralement la transformation des données de maillage spatial pour créer des données de maillage simples et/ou groupées, telles que des plans, des murs, des planchers, des plafonds, etc.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="fe0ef-110">Prise en main</span><span class="sxs-lookup"><span data-stu-id="fe0ef-110">Getting started</span></span>

<span data-ttu-id="fe0ef-111">L’ajout de la prise en charge de la sensibilisation spatiale requiert deux composants clés du kit de tâches de réalité mixte : le système de sensibilisation spatiale et un fournisseur de plateforme pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="fe0ef-112">[Activer](#enable-the-spatial-awareness-system) le système de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="fe0ef-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="fe0ef-113">[Inscrire](#register-observers) et [configurer](configuring-spatial-awareness-mesh-observer.md) un ou plusieurs observateurs spatiaux pour fournir des données de maillage</span><span class="sxs-lookup"><span data-stu-id="fe0ef-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="fe0ef-114">[Créez et déployez](#build-and-deploy) sur une plateforme qui prend en charge la sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="fe0ef-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="fe0ef-115">Activer le système de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="fe0ef-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="fe0ef-116">Le système de sensibilisation spatiale est géré par l’objet MixedRealityToolkit (ou un autre composant d' [inscription de service](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="fe0ef-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="fe0ef-117">Suivez les étapes ci-dessous pour activer ou désactiver le *système de sensibilisation spatiale* dans le profil *MixedRealityToolkit* .</span><span class="sxs-lookup"><span data-stu-id="fe0ef-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="fe0ef-118">La boîte à outils de réalité mixte est fournie avec quelques profils préconfigurés par défaut.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="fe0ef-119">Dans certains cas, le système de sensibilisation spatiale est activé ou désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="fe0ef-120">L’objectif de cette préconfiguration, en particulier lorsqu’elle est désactivée, est d’éviter la surcharge visuelle du calcul et du rendu des mailles.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="fe0ef-121">Profil</span><span class="sxs-lookup"><span data-stu-id="fe0ef-121">Profile</span></span> | <span data-ttu-id="fe0ef-122">Système activé par défaut</span><span class="sxs-lookup"><span data-stu-id="fe0ef-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="fe0ef-123">`DefaultHoloLens1ConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel/profils/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="fe0ef-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="fe0ef-124">Faux</span><span class="sxs-lookup"><span data-stu-id="fe0ef-124">False</span></span> |
| <span data-ttu-id="fe0ef-125">`DefaultHoloLens2ConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel/profils/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="fe0ef-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="fe0ef-126">Faux</span><span class="sxs-lookup"><span data-stu-id="fe0ef-126">False</span></span> |
| <span data-ttu-id="fe0ef-127">`DefaultMixedRealityToolkitConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel/profils)</span><span class="sxs-lookup"><span data-stu-id="fe0ef-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="fe0ef-128">Vrai</span><span class="sxs-lookup"><span data-stu-id="fe0ef-128">True</span></span> |

1. <span data-ttu-id="fe0ef-129">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie des scènes pour l’ouvrir dans le panneau Inspecteur.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="fe0ef-131">Accédez à la section *système de sensibilisation spatiale* et cochez *activer le système de sensibilisation spatiale* .</span><span class="sxs-lookup"><span data-stu-id="fe0ef-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Activer la sensibilisation spatiale](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="fe0ef-133">Sélectionnez le type d’implémentation du système de sensibilisation spatiale souhaité.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="fe0ef-134">[`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)Est la valeur par défaut fournie.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Sélectionner l’implémentation du système de sensibilisation spatiale](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="fe0ef-136">Inscrire des observateurs</span><span class="sxs-lookup"><span data-stu-id="fe0ef-136">Register observers</span></span>

<span data-ttu-id="fe0ef-137">Les services de la boîte à outils de la réalité mixte peuvent avoir des [services de fournisseur de données](../../architecture/systems-extensions-providers.md) qui complètent le service principal avec des données et des contrôles d’implémentation spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="fe0ef-138">Par exemple, le système d’entrée de réalité mixte qui dispose de [plusieurs fournisseurs de données](../input/input-providers.md) pour accéder au contrôleur et à d’autres informations d’entrée connexes à partir de différentes API spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="fe0ef-139">Le système de sensibilisation spatiale est similaire dans le fait que les fournisseurs de données fournissent au système des données de maillage relatives au monde réel.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="fe0ef-140">Au moins un observateur spatial doit être inscrit dans le profil de sensibilisation spatiale.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="fe0ef-141">Les observateurs spatiaux sont généralement des composants spécifiques à la plateforme qui jouent le rôle de fournisseur pour le revêtement de différents types de données de maillage à partir d’un point de terminaison spécifique à une plateforme (par exemple,</span><span class="sxs-lookup"><span data-stu-id="fe0ef-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="fe0ef-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="fe0ef-142">HoloLens).</span></span>

1. <span data-ttu-id="fe0ef-143">Ouvrir ou développer le *profil système de sensibilisation spatiale*</span><span class="sxs-lookup"><span data-stu-id="fe0ef-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Profil système de sensibilisation spatiale](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="fe0ef-145">Cliquez sur le bouton *« Ajouter un observateur spatial »*</span><span class="sxs-lookup"><span data-stu-id="fe0ef-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="fe0ef-146">Sélectionner le *type d’implémentation d’observateur spatial* souhaité</span><span class="sxs-lookup"><span data-stu-id="fe0ef-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Sélectionner l’implémentation de l’observateur spatial](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="fe0ef-148">[Modifiez les propriétés de configuration de l’observateur](configuring-spatial-awareness-mesh-observer.md) si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="fe0ef-149">Les utilisateurs du `DefaultMixedRealityToolkitConfigurationProfile` (ressources/MRTK/Kit de développement logiciel (SDK)/profils) auront le système de sensibilisation spatiale préconfiguré pour la plateforme Windows Mixed Reality qui utilise la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="fe0ef-150">Générer et déployer</span><span class="sxs-lookup"><span data-stu-id="fe0ef-150">Build and deploy</span></span>

<span data-ttu-id="fe0ef-151">Une fois que le système de sensibilisation spatiale est configuré avec le (s) observateur (s) souhaité (s), le projet peut être généré et déployé sur la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe0ef-152">Si vous ciblez la plateforme Windows Mixed Reality (par exemple, HoloLens), il est important de veiller à ce que la [fonction de perception spatiale](/windows/mixed-reality/spatial-mapping-in-unity) soit activée afin d’utiliser le système de sensibilisation spatiale sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="fe0ef-153">Certaines plateformes, y compris Microsoft HoloLens, fournissent une prise en charge de l’exécution à distance à partir d’Unity.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="fe0ef-154">Cette fonctionnalité permet un développement et des tests rapides sans nécessiter l’étape de création et de déploiement.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="fe0ef-155">Veillez à effectuer des tests d’acceptation finaux à l’aide d’une version générée et déployée de l’application, qui s’exécute sur le matériel et la plateforme cibles.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fe0ef-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fe0ef-156">Next steps</span></span>

<span data-ttu-id="fe0ef-157">Une fois que vous avez effectué les procédures ci-dessus pour activer le système de sensibilisation spatiale, le système peut être configuré et contrôlé de manière plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="fe0ef-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="fe0ef-158">Informations pour la configuration des observateurs dans Inspector :</span><span class="sxs-lookup"><span data-stu-id="fe0ef-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="fe0ef-159">Configuration des observateurs pour l’utilisation de l’appareil</span><span class="sxs-lookup"><span data-stu-id="fe0ef-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="fe0ef-160">Configuration des observateurs pour l’utilisation dans l’éditeur</span><span class="sxs-lookup"><span data-stu-id="fe0ef-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="fe0ef-161">Informations pour le contrôle et l’extension des observateurs par le biais du code :</span><span class="sxs-lookup"><span data-stu-id="fe0ef-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="fe0ef-162">Configuration des observateurs par le biais de code</span><span class="sxs-lookup"><span data-stu-id="fe0ef-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="fe0ef-163">Création d’un observateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="fe0ef-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="fe0ef-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe0ef-164">See also</span></span>

- [<span data-ttu-id="fe0ef-165">Documentation sur l’API de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="fe0ef-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="fe0ef-166">Vue d’ensemble du mappage spatial WMR</span><span class="sxs-lookup"><span data-stu-id="fe0ef-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="fe0ef-167">Mappage spatial dans Unity WMR</span><span class="sxs-lookup"><span data-stu-id="fe0ef-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)