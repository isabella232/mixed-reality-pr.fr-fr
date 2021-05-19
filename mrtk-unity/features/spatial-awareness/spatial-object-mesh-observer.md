---
title: Observateur de maillage des objets dans l’espace
description: Documentation sur l’observateur de maillage spatial dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144449"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="62337-104">Configuration des observateurs de maillage pour l’éditeur</span><span class="sxs-lookup"><span data-stu-id="62337-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="62337-105">Un moyen pratique de fournir des données de maillage d’environnement dans l’éditeur Unity consiste à utiliser la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe.</span><span class="sxs-lookup"><span data-stu-id="62337-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="62337-106">L' *Observateur d’objets spatiaux* est un fournisseur de données d’éditeur uniquement pour le [système de sensibilisation spatiale](spatial-awareness-getting-started.md) qui permet d’importer des données de modèle 3D pour représenter un maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="62337-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="62337-107">Une utilisation courante de l' *Observateur de maillage d’objets spatiaux* consiste à importer des données analysées par le biais d’un Microsoft HoloLens pour tester la façon dont une expérience s’adapte aux différents environnements à partir d’Unity.</span><span class="sxs-lookup"><span data-stu-id="62337-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="62337-108">Prise en main</span><span class="sxs-lookup"><span data-stu-id="62337-108">Getting started</span></span>

<span data-ttu-id="62337-109">Ce guide vous aidera à configurer un *Observateur de maillage d’objets spatiaux*.</span><span class="sxs-lookup"><span data-stu-id="62337-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="62337-110">Il existe trois étapes clés pour activer cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="62337-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="62337-111">Ajouter un *Observateur de maillage d’objets spatiaux* au profil de système de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="62337-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="62337-112">Définir l’objet de données de maillage de l’environnement</span><span class="sxs-lookup"><span data-stu-id="62337-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="62337-113">Configurer le reste des propriétés de profil de l’observateur de maillage</span><span class="sxs-lookup"><span data-stu-id="62337-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="62337-114">Configurer un profil d' *Observateur d’objets spatiaux*</span><span class="sxs-lookup"><span data-stu-id="62337-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="62337-115">Sélectionnez le profil de configuration de la *réalité mixte* souhaitée ou sélectionnez l’objet de la *boîte à outils de réalité mixte* dans Scene</span><span class="sxs-lookup"><span data-stu-id="62337-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="62337-116">Ouvrir ou développer l’onglet *système de sensibilisation spatiale*</span><span class="sxs-lookup"><span data-stu-id="62337-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="62337-117">Cliquez sur le bouton *« Ajouter un observateur spatial »*</span><span class="sxs-lookup"><span data-stu-id="62337-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Ajouter un observateur spatial](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="62337-119">Sélectionner le type de *SpatialObjectMeshObserver*</span><span class="sxs-lookup"><span data-stu-id="62337-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Sélectionner l’observateur de maillage d’objet spatial](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="62337-121">Sélectionnez l' *objet de maillage spatial* souhaité.</span><span class="sxs-lookup"><span data-stu-id="62337-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="62337-122">Par défaut, l’observateur est configuré avec un exemple de modèle.</span><span class="sxs-lookup"><span data-stu-id="62337-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="62337-123">Ce modèle a été créé à l’aide d’un Microsoft HoloLens, mais il est possible de [créer un nouvel objet de maillage d’analyse](#acquiring-environment-scans).</span><span class="sxs-lookup"><span data-stu-id="62337-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="62337-124">Configurer le reste des propriétés de profil de l’observateur de maillage</span><span class="sxs-lookup"><span data-stu-id="62337-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Sélectionner l’objet de maillage](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="62337-126">Notes de profil de l’observateur d’objets spatiaux</span><span class="sxs-lookup"><span data-stu-id="62337-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="62337-127">Étant donné que l' *Observateur d’objets spatiaux* charge des données à partir d’un modèle 3D, il n’honore pas certains des paramètres d’observateur de maillage standard qui sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="62337-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="62337-128">**Intervalle de mise à jour**</span><span class="sxs-lookup"><span data-stu-id="62337-128">**Update Interval**</span></span>

<span data-ttu-id="62337-129">L'  *Observateur d’objets spatiaux* envoie tous les maillages à une application lorsque le modèle est chargé.</span><span class="sxs-lookup"><span data-stu-id="62337-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="62337-130">Il ne simule pas les deltas horaires entre les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="62337-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="62337-131">Une application peut recevoir à nouveau les événements de maillage en appelant [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) et [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="62337-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="62337-132">**Est un observateur stationnaire**</span><span class="sxs-lookup"><span data-stu-id="62337-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="62337-133">L' *Observateur de maillage d’objets spatiaux* considère que tous les objets de maillage 3D sont stationnaires et ignore l’origine.</span><span class="sxs-lookup"><span data-stu-id="62337-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="62337-134">**Forme et étendues de l’observateur**</span><span class="sxs-lookup"><span data-stu-id="62337-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="62337-135">L'  *Observateur d’objets spatiaux* envoie l’intégralité du maillage 3D à l’application.</span><span class="sxs-lookup"><span data-stu-id="62337-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="62337-136">La forme et les étendues de l’observateur ne sont pas prises en compte.</span><span class="sxs-lookup"><span data-stu-id="62337-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="62337-137">**Niveau de détail et triangles/compteur cubique**</span><span class="sxs-lookup"><span data-stu-id="62337-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="62337-138">L’observateur ne tente pas de trouver des LODs de modèle 3D lors de l’envoi des maillages à l’application.</span><span class="sxs-lookup"><span data-stu-id="62337-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="62337-139">Acquisition d’analyses d’environnement</span><span class="sxs-lookup"><span data-stu-id="62337-139">Acquiring environment scans</span></span>

<span data-ttu-id="62337-140">Cette section décrit des informations supplémentaires pour créer et rassembler des fichiers *objets de maillage spatial* à utiliser avec l' *Observateur de maillage d’objets spatiaux*.</span><span class="sxs-lookup"><span data-stu-id="62337-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="62337-141">Portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="62337-141">Windows Device Portal</span></span>

<span data-ttu-id="62337-142">Le [portail de périphériques Windows](/windows/mixed-reality/using-the-windows-device-portal) peut être utilisé pour télécharger le maillage spatial, sous forme de fichier. obj, à partir d’un appareil Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="62337-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="62337-143">Analyse en parcourant et en affichant simplement l’environnement souhaité à l’aide d’un HoloLens</span><span class="sxs-lookup"><span data-stu-id="62337-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="62337-144">Se connecter au HoloLens à l’aide du portail de périphériques Windows</span><span class="sxs-lookup"><span data-stu-id="62337-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="62337-145">Accéder à la page de la *vue 3D*</span><span class="sxs-lookup"><span data-stu-id="62337-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="62337-146">Cliquez sur le bouton *mettre à jour* sous la section *mappage spatial* .</span><span class="sxs-lookup"><span data-stu-id="62337-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="62337-147">Cliquez sur le bouton *Enregistrer* sous la section *mappage spatial* pour enregistrer le fichier OBJ sur le PC.</span><span class="sxs-lookup"><span data-stu-id="62337-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="62337-148">**Fichiers HoloToolkit. Room**</span><span class="sxs-lookup"><span data-stu-id="62337-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="62337-149">De nombreux développeurs auront précédemment utilisé HoloToolkit pour analyser les environnements et créer des fichiers. Room.</span><span class="sxs-lookup"><span data-stu-id="62337-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="62337-150">La boîte à outils de réalité mixte prend désormais en charge l’importation de ces fichiers en tant que GameObjects dans Unity et les utilise en tant qu' *objets de maillage spatial* dans l’observateur.</span><span class="sxs-lookup"><span data-stu-id="62337-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="62337-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62337-151">See also</span></span>

- [<span data-ttu-id="62337-152">Profils</span><span class="sxs-lookup"><span data-stu-id="62337-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="62337-153">Guide de configuration du profil du Toolkit de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="62337-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="62337-154">Prise en main de la sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="62337-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="62337-155">Configuration des observateurs de maillage sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="62337-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="62337-156">Configuration des observateurs de maillage par le biais de code</span><span class="sxs-lookup"><span data-stu-id="62337-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="62337-157">Utilisation du portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="62337-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)