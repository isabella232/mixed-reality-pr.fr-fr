---
title: Découverte et acquisition de fonctionnalités
description: Découvrez et téléchargez des fonctionnalités de Réalité Mixte.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107732003"
---
# <a name="discovering-and-acquiring-features"></a>Découverte et acquisition de fonctionnalités

Les sections de cet article décrivent comment rechercher des packages de fonctionnalités dans Mixed Reality Feature Tool. Reportez-vous à la capture d’écran ci-dessous si vous avez besoin d’une référence pour une section donnée :

![Découverte de fonctionnalités](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>Fonctionnalités disponibles

### <a name="category"></a>Category

Mixed Reality Feature Tool affiche une collection de catégories de fonctionnalités pour faciliter la recherche de ce que vous voulez. Développez une des catégories pour afficher sa collection de fonctionnalités disponibles.

> [!NOTE]
> Si vous ne trouvez pas la fonctionnalité que vous recherchez, consultez **Autres fonctionnalités**.

![Catégorie de fonctionnalité](images/FeatureCategory.png)

L’en-tête de catégorie dans la capture d’écran ci-dessus contient les propriétés suivantes, de gauche à droite :

- Bouton Développer et réduire
- Nom de la catégorie (par exemple : Mixed Reality Toolkit)
- Nombre de fonctionnalités sélectionnées
- Nombre de fonctionnalités disponibles
- Boutons de sélection

> [!NOTE]
> Les boutons de sélection varient selon le contexte. En fonction de l’état de la sélection des fonctionnalités dans la catégorie, un ou plusieurs boutons `Select All` et `Select None` sont affichés.

### <a name="feature"></a>Fonctionnalité

![Entrée de fonctionnalité](images/FeatureEntry.png)

Les fonctionnalités sont listées dans leur catégorie appropriée. De gauche à droite dans la capture d’écran ci-dessus, les entrées de fonctionnalités contiennent les éléments suivants :

- Case à cocher de sélection
- Nom de la fonctionnalité (par exemple : Mixed Reality Toolkit Foundation)
- Liste des versions disponibles
- Lien vers les [détails des packages de fonctionnalités](viewing-package-details.md)

> [!NOTE]
> Si une fonctionnalité est fournie par un programme accessible en avant-première (on parle également de « préversion privée »), l’icône ![accès en avant-première](images/EarlyAccess.png) s’affiche.

## <a name="refresh-the-feature-catalog"></a>Actualiser le catalogue des fonctionnalités

Pour rechercher les fonctionnalités nouvelles et mises à jour, cliquez sur le bouton ![Refresh](images/RefreshButton.png) . Ceci permet de se connecter au site du catalogue et de récupérer les informations les plus récentes. Une fois que le catalogue a été lu, la date et l’heure de la dernière mise à jour sont affichées.

## <a name="select-features"></a>Sélectionner les caractéristiques

Vous sélectionnez les fonctionnalités en développant une catégorie, en sélectionnant une version, puis en cliquant sur la case à cocher :

![Fonctionnalités sélectionnées](images/SelectedFeatures.png)

Pour sélectionner chaque package dans une catégorie, un bouton `Select All` est fourni. `Select None` désélectionne tous les packages sélectionnés. 

Chaque catégorie avec une ou plusieurs fonctionnalités sélectionnées est alors mise à jour pour afficher le nombre de ces fonctionnalités.

## <a name="acquiring-features"></a>Acquisition des fonctionnalités

Une fois que vous avez choisi vos fonctionnalités, sélectionnez **Get features** pour commencer à télécharger les fichiers de package des fonctionnalités sélectionnées.

> [!NOTE]
> Par défaut, les fichiers de package de fonctionnalités précédemment acquis ne sont pas retéléchargés. Pour changer ce comportement, consultez [Configuration de Feature Tool](configuring-feature-tool.md).

Une fois le téléchargement terminé, Mixed Reality Feature Tool passe à l’étape [Importation des fonctionnalités](importing-features.md).

## <a name="going-back-to-the-previous-step"></a>Revenir à l’étape précédente

Dans les **fonctionnalités Discover**, l’outil Fonctionnalité de Réalité mixte permet de revenir en arrière jusqu’à la sélection du projet. Sélectionnez **Go back** pour recommencer.

## <a name="see-also"></a>Voir aussi

- [Bienvenue dans Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
- [Configuration de Feature Tool](configuring-feature-tool.md)
- [Visualisation des détails des packages de fonctionnalités](viewing-package-details.md)
- [Importation des packages sélectionnés](importing-features.md)
