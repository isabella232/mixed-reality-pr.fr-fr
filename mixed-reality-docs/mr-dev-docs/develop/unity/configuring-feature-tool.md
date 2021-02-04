---
title: Configuration de Mixed Reality Feature Tool
description: Découvrez comment télécharger et installer des packages Mixed Reality Unity à partir de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243930"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Configuration de Mixed Reality Feature Tool

Quand vous utilisez Mixed Reality Feature Tool, vous avez accès à trois catégories de paramètres différentes, que vous pouvez personnaliser à volonté :

* [Paramètres de téléchargement](#download-settings)
* [Paramètres de fonctionnalité](#feature-settings)
* [Paramètres d’importation](#import-settings)

![Paramètres](images/FeatureToolSettings.png)

## <a name="download-settings"></a>Paramètres de téléchargement

### <a name="overwrite-existing-package-files"></a>Remplacer les fichiers de packages existants

L’activation de ce paramètre fait que les fichiers de package sont téléchargés chaque fois qu’ils sont acquis. 
* **Nous vous recommandons de laisser cette option désactivée pour réduire l’utilisation de la bande passante réseau**
* Par défaut, les fichiers de package précédemment acquis ne sont pas retéléchargés.

### <a name="package-cache"></a>Package cache

Changez ce paramètre pour mettre à jour l’emplacement de téléchargement des packages de fonctionnalités.

> [!NOTE]
> Ce paramètre est **en lecture seule** dans cette version. Les versions ultérieures peuvent rendre ce paramètre configurable.

## <a name="feature-settings"></a>Paramètres de fonctionnalité

### <a name="include-preview-releases"></a>Include preview releases

Activez ce paramètre pour acquérir les préversions.
* Par défaut, les préversions ne sont pas montrées dans Mixed Reality Feature Tool 

> [!NOTE]
> Une préversion est indiquée par la mention **« -preview »** dans la version du package.

## <a name="import-settings"></a>Paramètres d’importation

### <a name="replace-existing-package-files"></a>Replace existing package files

Par défaut, Mixed Reality Feature Tool supprime les copies précédentes des packages importés pour réduire la taille du fichier et les traitements inutiles. 
* Décochez ce paramètre pour conserver toutes les versions

### <a name="project-relative-import-path"></a>Project relative import path

Changez ce paramètre pour mettre à jour le chemin du dossier du projet où les packages de fonctionnalités sont copiés lors de l’importation. 
* Par exemple, si le dossier du projet est **C:\GalaxyExplorer**, le chemin d’importation complet est **C:\GalaxyExplorer\Packages\MixedReality**.

> [!NOTE]
> Ce paramètre est **en lecture seule** dans cette version. Les versions ultérieures peuvent rendre ce paramètre configurable.

## <a name="see-also"></a>Voir aussi

- [Bienvenue dans Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)