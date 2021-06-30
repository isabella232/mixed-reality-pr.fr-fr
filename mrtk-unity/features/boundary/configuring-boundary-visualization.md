---
title: Configuration de la visualisation des limites
description: Détails pour configurer le système de limites dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de limite,
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121247"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="cc0b7-104">Configuration de la visualisation des limites</span><span class="sxs-lookup"><span data-stu-id="cc0b7-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="cc0b7-105">Le *profil de visualisation des limites* fournit des options pour configurer l’esthétique visuelle et d’autres paramètres associés pour le système de limite.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="cc0b7-106">Les visualisations de limites sont attachées à l’objet PlaySpace de la réalité mixte dans la scène et téléportent avec l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="cc0b7-107">Paramètres généraux :</span><span class="sxs-lookup"><span data-stu-id="cc0b7-107">General settings</span></span>

![Paramètres généraux de visualisation des limites](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="cc0b7-109">Hauteur limite</span><span class="sxs-lookup"><span data-stu-id="cc0b7-109">Boundary height</span></span>

<span data-ttu-id="cc0b7-110">La hauteur limite indique la distance au-dessus du plan du plancher à laquelle le plafond de limite doit être rendu.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="cc0b7-111">La valeur par défaut est 3 mètres.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="cc0b7-112">Paramètres du plancher</span><span class="sxs-lookup"><span data-stu-id="cc0b7-112">Floor settings</span></span>

![Paramètres d’étage de visualisation de la limite](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="cc0b7-114">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-114">**Show**</span></span>

<span data-ttu-id="cc0b7-115">Indique si un plan d’étage doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="cc0b7-116">La valeur par défaut est true.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-116">The default value is true.</span></span>

<span data-ttu-id="cc0b7-117">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-117">**Material**</span></span>

<span data-ttu-id="cc0b7-118">Indique la matière qui doit être utilisée lors de la création du plan de plancher.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="cc0b7-119">**Mise à l’échelle**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-119">**Scale**</span></span>

<span data-ttu-id="cc0b7-120">Indique la taille, en mètres, du plan d’étage à créer.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="cc0b7-121">L’échelle par défaut est un carré 3 mètres x 3 mètres.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="cc0b7-122">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-122">**Physics Layer**</span></span>

<span data-ttu-id="cc0b7-123">Couche sur laquelle le plan d’étage doit être défini.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="cc0b7-124">La valeur par défaut est la couche *par défaut* .</span><span class="sxs-lookup"><span data-stu-id="cc0b7-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="cc0b7-125">Paramètres de la zone de lecture</span><span class="sxs-lookup"><span data-stu-id="cc0b7-125">Play area settings</span></span>

![Paramètres de la zone de lecture des limites](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="cc0b7-127">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-127">**Show**</span></span>

<span data-ttu-id="cc0b7-128">Indique si un rectangle de zone de lecture doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="cc0b7-129">La valeur par défaut est true.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-129">The default value is true.</span></span>

<span data-ttu-id="cc0b7-130">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-130">**Material**</span></span>

<span data-ttu-id="cc0b7-131">Indique le matériel qui doit être utilisé lors de la création de l’objet de zone de lecture.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="cc0b7-132">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-132">**Physics Layer**</span></span>

<span data-ttu-id="cc0b7-133">Couche sur laquelle la zone de lecture doit être définie.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="cc0b7-134">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="cc0b7-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="cc0b7-135">Paramètres de la zone suivie</span><span class="sxs-lookup"><span data-stu-id="cc0b7-135">Tracked area settings</span></span>

![Paramètres de zone suivie de visualisation de la limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="cc0b7-137">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-137">**Show**</span></span>

<span data-ttu-id="cc0b7-138">Indique si le contour de la zone suivie doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="cc0b7-139">La valeur par défaut est true.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-139">The default value is true.</span></span>

<span data-ttu-id="cc0b7-140">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-140">**Material**</span></span>

<span data-ttu-id="cc0b7-141">Indique la matière qui doit être utilisée lors de la création de la structure de la zone suivie.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="cc0b7-142">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-142">**Physics Layer**</span></span>

<span data-ttu-id="cc0b7-143">Couche sur laquelle la zone suivie doit être redéfinie.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="cc0b7-144">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="cc0b7-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="cc0b7-145">Paramètres du mur des limites</span><span class="sxs-lookup"><span data-stu-id="cc0b7-145">Boundary wall settings</span></span>

![Paramètres du mur des limites de visualisation des limites](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="cc0b7-147">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-147">**Show**</span></span>

<span data-ttu-id="cc0b7-148">Indique si des plans muraux de limite doivent être créés et ajoutés à la scène.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="cc0b7-149">La valeur par défaut est false.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-149">The default value is false.</span></span>

<span data-ttu-id="cc0b7-150">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-150">**Material**</span></span>

<span data-ttu-id="cc0b7-151">Indique le matériau qui doit être utilisé lors de la création des plans muraux de la limite.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="cc0b7-152">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-152">**Physics Layer**</span></span>

<span data-ttu-id="cc0b7-153">Couche sur laquelle les parois limites doivent être définies.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="cc0b7-154">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="cc0b7-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="cc0b7-155">La définition du composant de paroi limite sur une couche physique autre que *Ignorer les Raycast* peut empêcher les utilisateurs d’interagir avec des objets dans la scène.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="cc0b7-156">Paramètres de plafond de limite</span><span class="sxs-lookup"><span data-stu-id="cc0b7-156">Boundary ceiling settings</span></span>

![Paramètres du plafond de visualisation des limites](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="cc0b7-158">**Afficher**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-158">**Show**</span></span>

<span data-ttu-id="cc0b7-159">Indique si un plan de plafond de limite doit être créé et ajouté à la scène.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="cc0b7-160">La valeur par défaut est false.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-160">The default value is false.</span></span>

<span data-ttu-id="cc0b7-161">**Matériau**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-161">**Material**</span></span>

<span data-ttu-id="cc0b7-162">Indique le matériau qui doit être utilisé lors de la création du plan de plafond de limite.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="cc0b7-163">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="cc0b7-163">**Physics Layer**</span></span>

<span data-ttu-id="cc0b7-164">Couche sur laquelle les parois limites doivent être définies.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="cc0b7-165">La valeur par défaut est la couche *Ignorer Raycast* .</span><span class="sxs-lookup"><span data-stu-id="cc0b7-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="cc0b7-166">La définition du composant Ceiling Limit sur une couche physique autre que *Ignorer les Raycast* peut empêcher les utilisateurs d’interagir avec des objets dans la scène.</span><span class="sxs-lookup"><span data-stu-id="cc0b7-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc0b7-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc0b7-167">See also</span></span>

- [<span data-ttu-id="cc0b7-168">Documentation sur l’API de limite</span><span class="sxs-lookup"><span data-stu-id="cc0b7-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="cc0b7-169">Système de limites</span><span class="sxs-lookup"><span data-stu-id="cc0b7-169">Boundary System</span></span>](boundary-system-getting-started.md)
