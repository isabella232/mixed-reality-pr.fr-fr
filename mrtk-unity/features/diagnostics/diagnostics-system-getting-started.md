---
title: Vue d’ensemble du système de diagnostics
description: Documentation pour activer et désactiver les diagnostics dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 536a35a0af0c0d0190f2f423f4a39e0d89e92c1acaa105ab37e8cf7fdc37cbf5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221810"
---
# <a name="diagnostics-system-overview"></a>Vue d’ensemble du système de diagnostics

la réalité mixte Shared Computer Toolkit système de diagnostic fournit des outils de diagnostic qui s’exécutent dans l’application pour permettre l’analyse des problèmes d’application.

La première version du système de diagnostic contient le [Générateur de profils Visual](using-visual-profiler.md) pour permettre l’analyse des problèmes de performances lors de l’utilisation de l’application.

## <a name="getting-started"></a>Prise en main

> [!IMPORTANT]
> Il est **_vivement_** recommandé d’activer le système de diagnostic tout au long du cycle de développement du produit et de désactiver la dernière modification avant de générer et de publier la version finale.

Il existe deux étapes clés pour commencer à utiliser le système de diagnostic.

1. [Activer](#enable-diagnostics) le système de diagnostic
2. [Configurer](#configure-diagnostic-options) les options de diagnostic

### <a name="enable-diagnostics"></a>Activation des diagnostics

Le système de diagnostic est géré par l’objet MixedRealityToolkit (ou un autre composant d' [inscription de service](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).

Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit. Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Naviguez dans le panneau de l’inspecteur jusqu’à la section système de diagnostic et cochez la case Activer
1. Sélectionner l’implémentation du système de diagnostic

    ![Sélectionner l’implémentation du système de diagnostic](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Les utilisateurs du profil par défaut `DefaultMixedRealityToolkitConfigurationProfile` (ressources/MRTK/Kit de développement logiciel (SDK)/profils) disposent du système de diagnostic préconfiguré pour utiliser l' [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) objet.

### <a name="configure-diagnostic-options"></a>Configurer les options de diagnostic

Le système de diagnostics utilise un profil de configuration pour spécifier les composants à afficher et pour configurer leurs paramètres. Pour plus d’informations sur les paramètres des composants disponibles, consultez [configuration du système de diagnostics](configuring-diagnostics.md) .

> [!IMPORTANT]
> Bien qu’il soit possible d’utiliser le mode de lecture d’Unity tout en développant des applications sans nécessiter les étapes de création et de déploiement, il est important d’évaluer les résultats du système de diagnostic à l’aide d’une application compilée qui s’exécute sur le matériel et la plateforme cibles.
>
> Les diagnostics de performances, tels que le [Générateur de profils visuels](using-visual-profiler.md), peuvent ne pas refléter avec précision les performances réelles des applications lorsqu’elles sont exécutées à partir de l’éditeur.

## <a name="see-also"></a>Voir aussi

- [Documentation de l’API de diagnostic](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Configuration du système de diagnostic](configuring-diagnostics.md)
- [Utilisation du générateur de profils Visual](using-visual-profiler.md)
