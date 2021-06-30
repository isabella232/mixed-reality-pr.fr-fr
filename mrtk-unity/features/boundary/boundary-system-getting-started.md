---
title: Vue d’ensemble du système de limites
description: Page d’accueil du système de limites dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de limite,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121357"
---
# <a name="boundary-system"></a>Système de limites

Le système de limites prend en charge la visualisation des composants limite de réalité virtuelle dans les applications de réalité mixte. Les limites définissent la zone dans laquelle les utilisateurs peuvent se déplacer en toute sécurité tout en portant un casque VR. Les limites sont un composant important d’une expérience de réalité mixte qui permet aux utilisateurs d’éviter les obstacles non visibles tout en portant un casque VR.

De nombreuses plates-formes de réalité virtuelle fournissent un affichage automatique, par exemple un contour blanc superposé sur le monde virtuel lorsque l’utilisateur ou le contrôleur approche de la limite. Le système de limite du Toolkit de réalité mixte étend cette fonctionnalité pour permettre l’affichage d’un plan de la zone suivie, d’un plan de plancher et d’autres fonctionnalités qui peuvent être utilisées pour fournir des informations supplémentaires aux utilisateurs.

## <a name="getting-started"></a>Prise en main

L’ajout de la prise en charge des limites requiert deux composants clés du kit de tâches de la réalité mixte : le système de limites et une plateforme de réalité virtuelle configurée avec une limite.

1. [Activer](#enable-boundary-system) le système de limites
2. [Configurer](#configure-boundary-visualization) la visualisation des limites
3. [Créez et déployez](#build-and-deploy) sur une plateforme VR avec une limite configurée

## <a name="enable-boundary-system"></a>Activer le système de limite

Le système de limites est géré par l’objet MixedRealityToolkit (ou un autre composant d' [inscription de service](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).

Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit. Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Naviguez dans le panneau de l’inspecteur jusqu’à la section système de limite et cochez Activer

    ![Activer le système de limites](../images/boundary/MRTKConfig_Boundary.png)

1. Sélectionnez l’implémentation du système de limites. L’implémentation de classe par défaut fournie par MRTK est le [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![Sélectionner l’implémentation du système de limites](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> Toutes les implémentations du système de limites doivent étendre [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>Configurer la visualisation des limites

Le [système de limites utilise un profil de configuration](configuring-boundary-visualization.md) pour spécifier les composants de limite à afficher et pour configurer leur apparence.

![Options de visualisation des limites](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> Le système de limite est préconfiguré pour les utilisateurs du profil par défaut `DefaultMixedRealityBoundaryVisualizationProfile` (ressources/MRTK/Kit de développement logiciel (SDK)/profils) pour afficher un plan d’étage, la zone de lecture et la zone suivie.

## <a name="build-and-deploy"></a>Générer et déployer

Une fois que le système de limites est configuré avec les options de visualisation souhaitées, le projet peut être créé sur la plateforme cible.

> [!NOTE]
> Le mode de lecture Unity permet la visualisation dans l’éditeur de la limite configurée. Cette fonctionnalité permet un développement et des tests rapides sans nécessiter l’étape de création et de déploiement. Veillez à effectuer des tests d’acceptation finaux à l’aide d’une version générée et déployée de l’application, qui s’exécute sur le matériel et la plateforme cibles.

## <a name="accessing-boundary-system-via-code"></a>Accès au système de limites par le biais du code

S’il est activé et configuré, le système de limite est accessible via la classe d’assistance statique CoreServices. La référence peut ensuite être utilisée pour modifier dynamiquement les paramètres de limite et accéder aux GameObjectss associés gérés par le système.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>Voir aussi

- [Documentation sur l’API de limite](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Configuration de la visualisation des limites](configuring-boundary-visualization.md)
