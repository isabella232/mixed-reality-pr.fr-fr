---
title: Configuration de la visualisation des limites
description: Détails pour configurer le système de limites dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de limite,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144497"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="778a6-104">Configuration de la visualisation des limites</span><span class="sxs-lookup"><span data-stu-id="778a6-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="778a6-105">Le *profil de visualisation des limites* fournit des options pour configurer l’esthétique visuelle et d’autres paramètres associés pour le système de limite.</span><span class="sxs-lookup"><span data-stu-id="778a6-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="778a6-106">Les visualisations de limites sont attachées à l’objet PlaySpace de la réalité mixte dans la scène et téléportent avec l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="778a6-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="778a6-107">Paramètres généraux :</span><span class="sxs-lookup"><span data-stu-id="778a6-107">General settings</span></span>

![Paramètres généraux de visualisation des limites](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="778a6-109">Hauteur limite</span><span class="sxs-lookup"><span data-stu-id="778a6-109">Boundary height</span></span>

<span data-ttu-id="778a6-110">La hauteur limite indique la distance au-dessus du plan du plancher à laquelle le plafond de limite doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="778a6-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="778a6-111">La valeur par défaut est 3 mètres.</span><span class="sxs-lookup"><span data-stu-id="778a6-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="778a6-112">Paramètres du plancher</span><span class="sxs-lookup"><span data-stu-id="778a6-112">Floor settings</span></span>

![Paramètres d’étage de visualisation de la limite](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="778a6-114">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="778a6-114">**Show**</span></span>

<span data-ttu-id="778a6-115">Indique si un plan d’étage doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="778a6-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="778a6-116">La valeur par défaut est true.</span><span class="sxs-lookup"><span data-stu-id="778a6-116">The default value is true.</span></span>

<span data-ttu-id="778a6-117">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="778a6-117">**Material**</span></span>

<span data-ttu-id="778a6-118">Indique la matière qui doit être utilisée lors de la création du plan de plancher.</span><span class="sxs-lookup"><span data-stu-id="778a6-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="778a6-119">**Mise à l’échelle**</span><span class="sxs-lookup"><span data-stu-id="778a6-119">**Scale**</span></span>

<span data-ttu-id="778a6-120">Indique la taille, en mètres, du plan d’étage à créer.</span><span class="sxs-lookup"><span data-stu-id="778a6-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="778a6-121">L’échelle par défaut est un carré 3 mètres x 3 mètres.</span><span class="sxs-lookup"><span data-stu-id="778a6-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="778a6-122">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="778a6-122">**Physics Layer**</span></span>

<span data-ttu-id="778a6-123">Couche sur laquelle le plan d’étage doit être défini.</span><span class="sxs-lookup"><span data-stu-id="778a6-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="778a6-124">La valeur par défaut est la couche *par défaut* .</span><span class="sxs-lookup"><span data-stu-id="778a6-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="778a6-125">Paramètres de la zone de lecture</span><span class="sxs-lookup"><span data-stu-id="778a6-125">Play area settings</span></span>

![Paramètres de la zone de lecture des limites](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="778a6-127">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="778a6-127">**Show**</span></span>

<span data-ttu-id="778a6-128">Indique si un rectangle de zone de lecture doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="778a6-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="778a6-129">La valeur par défaut est true.</span><span class="sxs-lookup"><span data-stu-id="778a6-129">The default value is true.</span></span>

<span data-ttu-id="778a6-130">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="778a6-130">**Material**</span></span>

<span data-ttu-id="778a6-131">Indique le matériel qui doit être utilisé lors de la création de l’objet de zone de lecture.</span><span class="sxs-lookup"><span data-stu-id="778a6-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="778a6-132">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="778a6-132">**Physics Layer**</span></span>

<span data-ttu-id="778a6-133">Couche sur laquelle la zone de lecture doit être définie.</span><span class="sxs-lookup"><span data-stu-id="778a6-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="778a6-134">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="778a6-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="778a6-135">Paramètres de la zone suivie</span><span class="sxs-lookup"><span data-stu-id="778a6-135">Tracked area settings</span></span>

![Paramètres de zone suivie de visualisation de la limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="778a6-137">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="778a6-137">**Show**</span></span>

<span data-ttu-id="778a6-138">Indique si le contour de la zone suivie doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="778a6-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="778a6-139">La valeur par défaut est true.</span><span class="sxs-lookup"><span data-stu-id="778a6-139">The default value is true.</span></span>

<span data-ttu-id="778a6-140">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="778a6-140">**Material**</span></span>

<span data-ttu-id="778a6-141">Indique la matière qui doit être utilisée lors de la création de la structure de la zone suivie.</span><span class="sxs-lookup"><span data-stu-id="778a6-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="778a6-142">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="778a6-142">**Physics Layer**</span></span>

<span data-ttu-id="778a6-143">Couche sur laquelle la zone suivie doit être redéfinie.</span><span class="sxs-lookup"><span data-stu-id="778a6-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="778a6-144">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="778a6-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="778a6-145">Paramètres du mur des limites</span><span class="sxs-lookup"><span data-stu-id="778a6-145">Boundary wall settings</span></span>

![Paramètres du mur des limites de visualisation des limites](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="778a6-147">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="778a6-147">**Show**</span></span>

<span data-ttu-id="778a6-148">Indique si des plans muraux de limite doivent être créés et ajoutés à la scène.</span><span class="sxs-lookup"><span data-stu-id="778a6-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="778a6-149">La valeur par défaut est false.</span><span class="sxs-lookup"><span data-stu-id="778a6-149">The default value is false.</span></span>

<span data-ttu-id="778a6-150">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="778a6-150">**Material**</span></span>

<span data-ttu-id="778a6-151">Indique le matériau qui doit être utilisé lors de la création des plans muraux de la limite.</span><span class="sxs-lookup"><span data-stu-id="778a6-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="778a6-152">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="778a6-152">**Physics Layer**</span></span>

<span data-ttu-id="778a6-153">Couche sur laquelle les parois limites doivent être définies.</span><span class="sxs-lookup"><span data-stu-id="778a6-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="778a6-154">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="778a6-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="778a6-155">La définition du composant de paroi limite sur une couche physique autre que *Ignorer les Raycast* peut empêcher les utilisateurs d’interagir avec des objets dans la scène.</span><span class="sxs-lookup"><span data-stu-id="778a6-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="778a6-156">Paramètres de plafond de limite</span><span class="sxs-lookup"><span data-stu-id="778a6-156">Boundary ceiling settings</span></span>

![Paramètres du plafond de visualisation des limites](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="778a6-158">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="778a6-158">**Show**</span></span>

<span data-ttu-id="778a6-159">Indique si un plan de plafond de limite doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="778a6-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="778a6-160">La valeur par défaut est false.</span><span class="sxs-lookup"><span data-stu-id="778a6-160">The default value is false.</span></span>

<span data-ttu-id="778a6-161">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="778a6-161">**Material**</span></span>

<span data-ttu-id="778a6-162">Indique le matériau qui doit être utilisé lors de la création du plan de plafond de limite.</span><span class="sxs-lookup"><span data-stu-id="778a6-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="778a6-163">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="778a6-163">**Physics Layer**</span></span>

<span data-ttu-id="778a6-164">Couche sur laquelle les parois limites doivent être définies.</span><span class="sxs-lookup"><span data-stu-id="778a6-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="778a6-165">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="778a6-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="778a6-166">La définition du composant Ceiling Limit sur une couche physique autre que *Ignorer les Raycast* peut empêcher les utilisateurs d’interagir avec des objets dans la scène.</span><span class="sxs-lookup"><span data-stu-id="778a6-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="778a6-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="778a6-167">See also</span></span>

- [<span data-ttu-id="778a6-168">Documentation sur l’API de limite</span><span class="sxs-lookup"><span data-stu-id="778a6-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="778a6-169">Système de limites</span><span class="sxs-lookup"><span data-stu-id="778a6-169">Boundary System</span></span>](boundary-system-getting-started.md)
