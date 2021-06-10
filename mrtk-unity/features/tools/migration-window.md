---
title: Fenêtre de migration
description: Documentation sur la migration vers une mise à jour dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647122"
---
# <a name="migration-window"></a>Fenêtre de migration

À mesure que le MRTK subit des modifications, certains composants peuvent être déconseillés et les remplacements seront introduits.
La fenêtre de migration est un outil qui permet aux utilisateurs de migrer automatiquement un sous-ensemble de ces composants déconseillés vers les nouveaux remplacements.

![Fenêtre de migration](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Utilisation

Pour ouvrir la fenêtre, sélectionnez la fenêtre de  >    >    >  **migration** utilitaires d’outils de réalité mixte. Une fois la fenêtre de migration ouverte, les onglets de navigation du mode de sélection peuvent être activés en choisissant l’implémentation spécifique au composant du gestionnaire de migration.  

![Modes de sélection de la migration](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Mode Objet

La sélection de l’onglet objets Active le champ objet à l’emplacement où l’utilisateur peut glisser-déplacer des objets de jeu à partir de la scène actuellement ouverte ou prefabs à partir du dossier du projet à migrer.
Le fait d’appuyer sur le bouton supprimer *(-)* affiché sur le côté droit de l’objet répertorié supprime l’objet de la liste de sélection.

Une fois que tous les objets souhaités figurent dans la liste, le fait d’appuyer sur le bouton *migrer* applique les modifications requises par l’implémentation du gestionnaire de migration choisi à tous les composants de la sélection qui correspondent à l’implémentation.

![Migration de la sélection](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Mode scène

Permet à l’utilisateur de faire glisser et déposer des ressources de scène contenant des objets à migrer.

![Sélection de scènes pour la migration](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Mode projet

Le fait d’appuyer sur le bouton *migrer* met à jour le composant ciblé par l’implémentation du gestionnaire de migration pour tous les prefabs et scènes du projet.

![Migration d’un projet complet](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Voir aussi

- [Mise à jour à partir de versions antérieures](../../updates-deployment/updating.md)
- [Versions de Microsoft Mixed Reality Toolkit](../../release-notes/mrtk-26-release-notes.md)
- [Feuille de route MRTK](../../roadmap.md)
