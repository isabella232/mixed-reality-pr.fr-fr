---
title: Configuration de Mixed Reality Feature Tool
description: Découvrez comment télécharger et installer des packages Mixed Reality Unity à partir de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731946"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Configuration de Mixed Reality Feature Tool

Quand vous utilisez Mixed Reality Feature Tool, vous avez accès à trois catégories de paramètres différentes, que vous pouvez personnaliser à volonté :

* [Paramètres de téléchargement](#download-settings)
* [Paramètres de fonctionnalité](#feature-settings)
* [Paramètres d’importation](#import-settings)

## <a name="download-settings"></a>Paramètres de téléchargement

![Paramètres de téléchargement](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>Remplacer les fichiers de packages existants

L’activation de ce paramètre fait que les fichiers de package sont téléchargés chaque fois qu’ils sont acquis. 

* **Nous vous recommandons de laisser cette option désactivée pour réduire l’utilisation de la bande passante réseau**
* Par défaut, les fichiers de package précédemment acquis ne sont pas retéléchargés.

### <a name="package-cache"></a>Package cache

Changez ce paramètre pour mettre à jour l’emplacement de téléchargement des packages de fonctionnalités.

> [!NOTE]
> Ce paramètre est **en lecture seule** dans cette version. Les versions ultérieures peuvent rendre ce paramètre configurable.

## <a name="feature-settings"></a>Paramètres de fonctionnalité

![Paramètres de fonctionnalité](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>Show preview releases

Activez ce paramètre pour acquérir les préversions.
* Par défaut, les préversions ne sont pas listées dans Mixed Reality Feature Tool. 

> [!NOTE]
> Une préversion est indiquée par la mention **« -preview »** dans la version du package.

### <a name="show-early-access-program-features"></a>Show early access program features

Activez ce paramètre pour acquérir les fonctionnalités de programmes inscrits accessibles en avant-première.

* Par défaut, les fonctionnalités accessibles en avant-première ne sont pas listées dans Mixed Reality Feature Tool. 

> [!NOTE]
> Si vous activez `Show early access program features` sans `Show preview releases`, les packages accessibles en avant-première peuvent ne pas apparaître dans la découverte.

## <a name="import-settings"></a>Paramètres d’importation

![Paramètres d’importation](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>Replace existing package files

Par défaut, Mixed Reality Feature Tool supprime les copies précédentes des packages importés pour réduire la taille du fichier et les traitements inutiles. 

* Décochez ce paramètre pour conserver toutes les versions

### <a name="project-relative-import-path"></a>Project relative import path

Changez ce paramètre pour mettre à jour le chemin du dossier du projet où les packages de fonctionnalités sont copiés lors de l’importation. 

* Par exemple, si le dossier du projet est **C:\GalaxyExplorer**, le chemin d’importation complet est **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Ce paramètre est **en lecture seule** dans cette version. Les versions ultérieures peuvent rendre ce paramètre configurable.

## <a name="early-access-settings"></a>Paramètres d’accès en avant-première

![Paramètres d’accès en avant-première](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>Ask for confirmation before removing an early access program

Ce paramètre détermine si une invite doit être affichée chaque fois qu’un programme accessible en avant-première est supprimé.

### <a name="my-previews"></a>My previews

Liste des programmes inscrits accessibles en avant-première. Utilisez `Add` , `Edit` et `Remove` pour gérer la collection de programmes inscrits.

## <a name="diagnostic-settings"></a>Paramètres de diagnostic

![Paramètres de diagnostic](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>Fichier journal

Affiche le chemin au fichier journal de diagnostic.

## <a name="see-also"></a>Voir aussi

- [Bienvenue dans Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)