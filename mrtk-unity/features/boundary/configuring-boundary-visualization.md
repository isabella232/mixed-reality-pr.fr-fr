---
title: Configuration de la visualisation des limites
description: Détails pour configurer le système de limites dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de limite,
ms.openlocfilehash: 29ffe7826d797fd32387fab42f24232f98ab283740848b7fce928718f95f0fc9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211561"
---
# <a name="configuring-boundary-visualization"></a>Configuration de la visualisation des limites

Le *profil de visualisation des limites* fournit des options pour configurer l’esthétique visuelle et d’autres paramètres associés pour le système de limite. Les visualisations de limites sont attachées à l’objet PlaySpace de la réalité mixte dans la scène et téléportent avec l’utilisateur.

## <a name="general-settings"></a>Paramètres généraux :

![Paramètres générale de visualisation des limites](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Hauteur limite

La hauteur limite indique la distance au-dessus du plan du plancher à laquelle le plafond de limite doit être rendu. La valeur par défaut est 3 mètres.

## <a name="floor-settings"></a>Paramètres du plancher

![Paramètres de la visualisation des limites](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Afficher**

Indique si un plan d’étage doit être créé et ajouté à la scène. La valeur par défaut est true.

**Matériau**

Indique la matière qui doit être utilisée lors de la création du plan de plancher.

**Mettre à l'échelle**

Indique la taille, en mètres, du plan d’étage à créer. L’échelle par défaut est un carré 3 mètres x 3 mètres.

**Couche physique**

Couche sur laquelle le plan d’étage doit être défini. La valeur par défaut est la couche *par défaut* .

## <a name="play-area-settings"></a>Paramètres de la zone de lecture

![zone de lecture de la visualisation des limites Paramètres](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Afficher**

Indique si un rectangle de zone de lecture doit être créé et ajouté à la scène. La valeur par défaut est true.

**Matériau**

Indique le matériel qui doit être utilisé lors de la création de l’objet de zone de lecture.

**Couche physique**

Couche sur laquelle la zone de lecture doit être définie. La valeur par défaut est la couche *Ignorer Raycast* .

## <a name="tracked-area-settings"></a>Paramètres de la zone suivie

![Paramètres de zone suivie de la visualisation limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Afficher**

Indique si le contour de la zone suivie doit être créé et ajouté à la scène. La valeur par défaut est true.

**Matériau**

Indique la matière qui doit être utilisée lors de la création de la structure de la zone suivie.

**Couche physique**

Couche sur laquelle la zone suivie doit être redéfinie. La valeur par défaut est la couche *Ignorer Raycast* .

## <a name="boundary-wall-settings"></a>Paramètres du mur des limites

![Paramètres du mur de la limite de visualisation des limites](../images/boundary/BoundaryVisualizationWallSettings.png)

**Afficher**

Indique si des plans muraux de limite doivent être créés et ajoutés à la scène. La valeur par défaut est false.

**Matériau**

Indique le matériau qui doit être utilisé lors de la création des plans muraux de la limite.

**Couche physique**

Couche sur laquelle les parois limites doivent être définies. La valeur par défaut est la couche *Ignorer Raycast* .

> [!NOTE]
> La définition du composant de paroi limite sur une couche physique autre que *Ignorer les Raycast* peut empêcher les utilisateurs d’interagir avec des objets dans la scène.

## <a name="boundary-ceiling-settings"></a>Paramètres de plafond de limite

![limite de visualisation limite Paramètres](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Afficher**

Indique si un plan de plafond de limite doit être créé et ajouté à la scène. La valeur par défaut est false.

**Matériau**

Indique le matériau qui doit être utilisé lors de la création du plan de plafond de limite.

**Couche physique**

Couche sur laquelle les parois limites doivent être définies. La valeur par défaut est la couche *Ignorer Raycast* .

> [!NOTE]
> La définition du composant Ceiling Limit sur une couche physique autre que *Ignorer les Raycast* peut empêcher les utilisateurs d’interagir avec des objets dans la scène.

## <a name="see-also"></a>Voir aussi

- [Documentation sur l’API de limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Système de limites](boundary-system-getting-started.md)
