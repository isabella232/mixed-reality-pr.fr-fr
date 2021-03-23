---
title: Importation des fonctionnalités
description: Découvrez comment importer et installer des fonctionnalités à partir de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230811"
---
# <a name="importing-features"></a>Importation des fonctionnalités

Une fois que vos fonctionnalités ont été téléchargées, elles peuvent être passées en revue et importées dans le projet Unity. À cette étape, la fenêtre de votre application doit ressembler à l’image suivante :

![Importation des fonctionnalités](images/FeatureToolImport.png)

## <a name="features-list"></a>Features list

La liste **Features** contient la collection de packages sélectionnés lors de la découverte. Chaque fonctionnalité peut être sélectionnée ou désélectionnée avant d’être importée. Vous pouvez consulter les détails des packages en utilisant le lien **Details** montré ci-dessous.

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>Liste des dépendances requises

La liste **Required dependencies** contient les packages requis par une ou plusieurs des fonctionnalités sélectionnées pour fonctionner. Cette liste contient également les dépendances des dépendances. Chaque dépendance peut être sélectionnée ou désélectionnée avant d’être importée. Vous pouvez consulter les détails des packages en utilisant le lien **Details** montré ci-dessous.

![Liste des dépendances](images/RequiredDependencyList.png)

> [!NOTE]
> La désélection des dépendances requises entraîne une ou plusieurs erreurs de dépendances manquantes lors du chargement du projet dans Unity. Ces fonctionnalités ne seront pas utilisables dans le projet.

## <a name="validating-selections"></a>Validation des sélections

Nous vous recommandons fortement de valider les sélections de fonctionnalités avant l’importation. Cette étape va détecter tous les problèmes susceptibles d’empêcher la réussite du développement des projets.

![Problèmes de validation](images/ValidationIssues.png)

Mixed Reality Feature Tool fournit deux résolutions de problème automatiques (décrites dans les sections suivantes), et la possibilité d’annuler et de résoudre les problèmes manuellement.

### <a name="enable-dependencies"></a>Activer les dépendances

Le bouton **Enable dependencies** va resélectionner automatiquement les dépendances manquantes. C’est vrai pour les dépendances qui ont été explicitement sélectionnées (qui apparaissent dans la liste **Features**) et pour celles qui ont été sélectionnées implicitement en fonction des exigences des fonctionnalités sélectionnées.

### <a name="disable-features"></a>Désactiver des fonctionnalités

Le fait de sélectionner **Disable features** désélectionne automatiquement les fonctionnalités qui dépendent d’une ou de plusieurs des dépendances qui ont été désactivées. C’est vrai pour les packages de dépendances implicitement sélectionnés et pour les fonctionnalités explicitement sélectionnées.

## <a name="importing"></a>Importation en cours

Sélectionnez **Import** pour ajouter vos fonctionnalités sélectionnées et pour donner une [approbation finale](reviewing-changes.md) avant de mettre à jour votre projet cible.

> [!IMPORTANT]
> Si un problème de validation persiste lors de l’importation, un message d’avertissement s’affiche. Il est recommandé de sélectionner No, de cliquer sur **Validate** et de résoudre les problèmes présentés.
>
> ![Continuer avec les problèmes de validation](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>Revenir à l’étape précédente

Dans **Import features**, Mixed Reality Feature Tool permet de revenir en arrière jusqu’au la [découverte](discovering-features.md). Sélectionnez **Go back** pour télécharger d’autres packages de fonctionnalités.

## <a name="see-also"></a>Voir aussi

- [Bienvenue dans Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
- [Découverte et acquisition](discovering-features.md)
- [Visualisation des détails des packages de fonctionnalités](viewing-package-details.md)
- [Examen et approbation des modifications du projet](reviewing-changes.md)