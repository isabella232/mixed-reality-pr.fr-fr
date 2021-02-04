---
title: Autoriser les modifications d’un projet
description: Découvrez comment autoriser les modifications d’un projet par Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243907"
---
# <a name="authorizing-project-changes"></a>Autoriser les modifications d’un projet

Avant de modifier le projet Unity, les modifications apportées aux fichiers manifeste et projet doivent être examinées et approuvées :

![Demande d’autorisation](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>Manifeste

Les modifications proposées pour le manifeste peuvent être visualisées dans la colonne **Manifest** à gauche. Le contenu est exactement ce qui sera écrit dans le manifeste du projet (**Packages/manifest.json**) :

![Aperçu du manifeste](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>Fichiers à copier dans le projet

La section **Files to be copied into the project** à droite liste les fichiers de package de fonctionnalités spécifiques qui seront copiés dans le projet Unity :

![Aperçu du manifeste avec les fichiers à copier](images/FilesToCopy.png)

## <a name="compare-manifests"></a>Comparer les manifestes

Vous pouvez voir une comparaison côte à côte détaillée de toutes les modifications proposées en sélectionnant **Compare** :

![Comparer les manifestes](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>Approbation des modifications

Quand les modifications proposées sont approuvées, les fichiers listés sont copiés dans le projet Unity et le manifeste est mis à jour avec des références à ces fichiers.

> [!NOTE]
> Les fichiers de package de fonctionnalités (*.tgz) doivent être ajoutés au contrôle de code source. Ils sont référencés en utilisant un chemin relatif pour permettre aux équipes de développement de partager facilement les fonctionnalités et les modifications du manifeste.

 Dans le cadre des modifications, le fichier **manifest.json** actuel est sauvegardé.

> [!IMPORTANT]
> Quand vous visualisez les sauvegardes de manifeste, le plus ancien est appelé **manifest.json.backup**. Les sauvegardes plus récentes sont annotées avec une valeur numérique, en commençant par zéro (0).

## <a name="going-back-to-the-previous-step"></a>Revenir à l’étape précédente

Si vous devez apporter des modifications à vos sélections de fonctionnalités, utilisez **Go Back** pour revenir à l’étape [Importer](importing-features.md).

## <a name="see-also"></a>Voir aussi

- [Bienvenue dans Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
- [Importation des packages sélectionnés](importing-features.md)
