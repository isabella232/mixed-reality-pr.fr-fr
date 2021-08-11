---
title: Utilisation du gestionnaire de package Unity
description: utilisation de MRTK dans unity Gestionnaire de package
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, Packages MRTK,
ms.openlocfilehash: fb96a910b86e8ec9f6d73b8239e0ae008ea021c65f2c52edc613d2fe02719e58
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194464"
---
# <a name="using-the-unity-package-manager"></a>Utilisation du gestionnaire de package Unity

à partir de la version 2.5.0, à l’aide de l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), le Shared Computer Toolkit de la réalité mixte Microsoft s’intègre avec unity Gestionnaire de package (UPM) lors de l’utilisation d’unity 2019,4 et plus récent.

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

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>gestion des fonctionnalités de réalité mixte avec unity Gestionnaire de package

une fois qu’une réalité mixte Shared Computer Toolkit package a été ajouté au manifeste du package, elle peut être gérée à l’aide de l’interface utilisateur unity Gestionnaire de package.

![Package UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> si une réalité mixte Shared Computer Toolkit package est supprimé à l’aide de unity Gestionnaire de package, il devra être rajouté à l’aide des [étapes décrites précédemment](#using-the-mixed-reality-feature-tool).

### <a name="using-mixed-reality-toolkit-examples"></a>exemples d’utilisation de la réalité mixte Shared Computer Toolkit

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

- [packages de Shared Computer Toolkit de réalité mixte](../packages/mrtk-packages.md)
