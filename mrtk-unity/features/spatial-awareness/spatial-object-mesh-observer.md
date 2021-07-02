---
title: Observateur de maillage d’objets spatiaux
description: Documentation sur l’observateur de maillage spatial dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176694"
---
# <a name="spatial-object-mesh-observer"></a><span data-ttu-id="f8fe6-104">Observateur de maillage d’objets spatiaux</span><span class="sxs-lookup"><span data-stu-id="f8fe6-104">Spatial object mesh observer</span></span>

<span data-ttu-id="f8fe6-105">Un moyen pratique de fournir des données de maillage d’environnement dans l’éditeur Unity consiste à utiliser la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="f8fe6-106">L' *Observateur d’objets spatiaux* est un fournisseur de données d’éditeur uniquement pour le [système de sensibilisation spatiale](spatial-awareness-getting-started.md) qui permet d’importer des données de modèle 3D pour représenter un maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="f8fe6-107">une utilisation courante de l' *observateur de maillage d’objets spatiaux* consiste à importer des données analysées via une Microsoft HoloLens pour tester la façon dont une expérience s’adapte aux différents environnements à partir d’unity.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="f8fe6-108">Prise en main</span><span class="sxs-lookup"><span data-stu-id="f8fe6-108">Getting started</span></span>

<span data-ttu-id="f8fe6-109">Ce guide vous aidera à configurer un *Observateur de maillage d’objets spatiaux*.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="f8fe6-110">Il existe trois étapes clés pour activer cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="f8fe6-111">Ajouter un *Observateur de maillage d’objets spatiaux* au profil de système de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="f8fe6-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="f8fe6-112">Définir l’objet de données de maillage de l’environnement</span><span class="sxs-lookup"><span data-stu-id="f8fe6-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="f8fe6-113">Configurer le reste des propriétés de profil de l’observateur de maillage</span><span class="sxs-lookup"><span data-stu-id="f8fe6-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="f8fe6-114">Configurer un profil d' *Observateur d’objets spatiaux*</span><span class="sxs-lookup"><span data-stu-id="f8fe6-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="f8fe6-115">sélectionnez la *réalité mixte Shared Computer Toolkit* profil de configuration de votre choix ou sélectionnez la *réalité mixte Shared Computer Toolkit* objet dans la scène</span><span class="sxs-lookup"><span data-stu-id="f8fe6-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="f8fe6-116">Ouvrir ou développer l’onglet *système de sensibilisation spatiale*</span><span class="sxs-lookup"><span data-stu-id="f8fe6-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="f8fe6-117">Cliquez sur le bouton *« Ajouter un observateur spatial »*</span><span class="sxs-lookup"><span data-stu-id="f8fe6-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Ajouter un observateur spatial](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="f8fe6-119">Sélectionner le type de *SpatialObjectMeshObserver*</span><span class="sxs-lookup"><span data-stu-id="f8fe6-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Sélectionner l’observateur de maillage d’objet spatial](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="f8fe6-121">Sélectionnez l' *objet de maillage spatial* souhaité.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="f8fe6-122">Par défaut, l’observateur est configuré avec un exemple de modèle.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="f8fe6-123">ce modèle a été créé à l’aide d’un Microsoft HoloLens, mais il est possible de [créer un nouvel objet de maillage d’analyse](#acquiring-environment-scans).</span><span class="sxs-lookup"><span data-stu-id="f8fe6-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="f8fe6-124">Configurer le reste des propriétés de profil de l’observateur de maillage</span><span class="sxs-lookup"><span data-stu-id="f8fe6-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Sélectionner l’objet de maillage](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="f8fe6-126">Notes de profil de l’observateur d’objets spatiaux</span><span class="sxs-lookup"><span data-stu-id="f8fe6-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="f8fe6-127">Étant donné que l' *Observateur d’objets spatiaux* charge des données à partir d’un modèle 3D, il n’honore pas certains des paramètres d’observateur de maillage standard qui sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="f8fe6-128">**Intervalle de mise à jour**</span><span class="sxs-lookup"><span data-stu-id="f8fe6-128">**Update Interval**</span></span>

<span data-ttu-id="f8fe6-129">L'  *Observateur d’objets spatiaux* envoie tous les maillages à une application lorsque le modèle est chargé.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="f8fe6-130">Il ne simule pas les deltas horaires entre les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="f8fe6-131">Une application peut recevoir à nouveau les événements de maillage en appelant [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) et [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="f8fe6-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="f8fe6-132">**Est un observateur stationnaire**</span><span class="sxs-lookup"><span data-stu-id="f8fe6-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="f8fe6-133">L' *Observateur de maillage d’objets spatiaux* considère que tous les objets de maillage 3D sont stationnaires et ignore l’origine.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="f8fe6-134">**Forme et étendues de l’observateur**</span><span class="sxs-lookup"><span data-stu-id="f8fe6-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="f8fe6-135">L'  *Observateur d’objets spatiaux* envoie l’intégralité du maillage 3D à l’application.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="f8fe6-136">La forme et les étendues de l’observateur ne sont pas prises en compte.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="f8fe6-137">**Niveau de détail et triangles/compteur cubique**</span><span class="sxs-lookup"><span data-stu-id="f8fe6-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="f8fe6-138">L’observateur ne tente pas de trouver des LODs de modèle 3D lors de l’envoi des maillages à l’application.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="f8fe6-139">Acquisition d’analyses d’environnement</span><span class="sxs-lookup"><span data-stu-id="f8fe6-139">Acquiring environment scans</span></span>

<span data-ttu-id="f8fe6-140">Cette section décrit des informations supplémentaires pour créer et rassembler des fichiers *objets de maillage spatial* à utiliser avec l' *Observateur de maillage d’objets spatiaux*.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="f8fe6-141">Portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="f8fe6-141">Windows Device Portal</span></span>

<span data-ttu-id="f8fe6-142">le [portail d’appareils Windows](/windows/mixed-reality/using-the-windows-device-portal) peut être utilisé pour télécharger le maillage spatial, sous forme de fichier. obj, à partir d’un appareil Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="f8fe6-143">Effectuez une analyse en parcourant et en visualisant simplement l’environnement souhaité à l’aide d’un HoloLens</span><span class="sxs-lookup"><span data-stu-id="f8fe6-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="f8fe6-144">Connecter au HoloLens à l’aide du portail des appareils Windows</span><span class="sxs-lookup"><span data-stu-id="f8fe6-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="f8fe6-145">Accéder à la page de la *vue 3D*</span><span class="sxs-lookup"><span data-stu-id="f8fe6-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="f8fe6-146">Cliquez sur le bouton *mettre à jour* sous la section *mappage spatial* .</span><span class="sxs-lookup"><span data-stu-id="f8fe6-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="f8fe6-147">Cliquez sur le bouton *Enregistrer* sous la section *mappage spatial* pour enregistrer le fichier OBJ sur le PC.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="f8fe6-148">**Fichiers HoloToolkit. Room**</span><span class="sxs-lookup"><span data-stu-id="f8fe6-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="f8fe6-149">De nombreux développeurs auront précédemment utilisé HoloToolkit pour analyser les environnements et créer des fichiers. Room.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="f8fe6-150">la réalité mixte Shared Computer Toolkit prend maintenant en charge l’importation de ces fichiers en tant que GameObjects dans unity et les utilise en tant qu' *objets de maillage Spatial* dans l’observateur.</span><span class="sxs-lookup"><span data-stu-id="f8fe6-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8fe6-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8fe6-151">See also</span></span>

- [<span data-ttu-id="f8fe6-152">Profils</span><span class="sxs-lookup"><span data-stu-id="f8fe6-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="f8fe6-153">guide de configuration de la réalité mixte Shared Computer Toolkit profil</span><span class="sxs-lookup"><span data-stu-id="f8fe6-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="f8fe6-154">Prise en main de la sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="f8fe6-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="f8fe6-155">Configuration des observateurs de maillage sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="f8fe6-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="f8fe6-156">Configuration des observateurs de maillage par le biais de code</span><span class="sxs-lookup"><span data-stu-id="f8fe6-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="f8fe6-157">Utilisation du portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="f8fe6-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)
