---
title: Utilisation du gestionnaire de package Unity
description: Utilisation de MRTK dans le gestionnaire de package Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, packages MRTK,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345072"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>Trousse à outils de réalité mixte et gestionnaire de packages Unity

À partir de la version 2.5.0, à l’aide de l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), Microsoft Mixed Reality Toolkit est intégré au gestionnaire de package Unity (UPM) lors de l’utilisation d’unity 2019,4 et de versions ultérieures.

## <a name="using-the-mixed-reality-feature-tool"></a>Utilisation de Mixed Reality Feature Tool

Comme décrit dans [Bienvenue dans l’outil de fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) , vous pouvez télécharger l’outil à l’aide de [ce lien](https://aka.ms/MRFeatureTool).

> [!IMPORTANT]
> Si le manifeste du projet a une `Microsoft Mixed Reality` entrée dans la `scopedRegistries` section, il est recommandé de le supprimer.
>
> Pour supprimer un registre avec étendue configuré, accédez à `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Suppression du Registre étendu](../features/images/packaging/RemoveScopedRegistry.png)

Les packages MRTK s’affichent sous l' `Mixed Reality Toolkit` en-tête lors de la découverte des fonctionnalités.

![Découvrir les fonctionnalités](../features/images/packaging/DiscoverFeatures.png)

Lorsque vous sélectionnez des fonctionnalités, vous n’avez pas besoin de vous préoccuper des dépendances requises, l’outil les télécharge et les intègre automatiquement dans le projet.

![Dépendances requises](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Gestion des fonctionnalités de réalité mixte avec le gestionnaire de package Unity

Une fois qu’un package de boîte à outils de réalité mixte a été ajouté au manifeste du package, il peut être géré à l’aide de l’interface utilisateur du gestionnaire de package Unity.

![Package UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Si un package de boîte à outils de réalité mixte est supprimé à l’aide du gestionnaire de package Unity, il devra être rajouté à l’aide des [étapes décrites précédemment](#using-the-mixed-reality-feature-tool).

### <a name="using-mixed-reality-toolkit-examples"></a>Utilisation d’exemples d’outils de réalité mixte

Contrairement à l’utilisation de fichiers de package de ressources (. pour Unity), `com.microsoft.mixedreality.toolkit.examples` et `com.microsoft.mixedreality.toolkit.handphysicsservice` n’importent pas automatiquement les exemples de scènes et les éléments multimédias.

Pour utiliser un ou plusieurs des exemples, procédez comme suit :

1. Dans l’éditeur Unity, accédez à `Window` > `Package Manager`
1. Dans la liste des packages, sélectionnez `Mixed Reality Toolkit Examples`
1. Rechercher les exemples souhaités dans la `Samples` liste
1. Cliquez sur `Import into Project`

![Importation d’exemples](../features/images/packaging/MRTK_ExamplesUpm.png)

Lorsqu’un exemple de package est mis à jour, Unity offre la possibilité de mettre à jour les exemples importés.

> [!NOTE]
> La mise à jour d’un exemple importé remplace toutes les modifications apportées à cet exemple et les ressources associées.

## <a name="see-also"></a>Voir aussi

- [Packages Toolkit de réalité mixte](../packages/mrtk-packages.md)