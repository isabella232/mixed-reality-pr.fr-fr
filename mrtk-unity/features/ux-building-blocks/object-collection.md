---
title: Collection d’objets
description: Vue d’ensemble de la collection d’objets dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, collection d’objets,
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177049"
---
# <a name="object-collection"></a>Collection d’objets

![Collection d’objets](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

La collection d’objets est un script qui permet de disposer un tableau d’objets dans des formes tridimensionnelles prédéfinies. Il prend en charge divers styles de surface, y compris les plans, les cylindres, les sphères et les radiales. Comme il prend en charge n’importe quel objet dans Unity, il peut être utilisé pour mettre en forme des objets 2D et 3D.

## <a name="object-collection-scripts"></a>Scripts de collection d’objets

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) prend en charge les types de surface cylindrique, plan, sphère et radial
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) prend en charge la collection de styles éparpillés  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fournit des options supplémentaires à GridObjectCollection. **Remarque :** TileGridObjectCollection ne s’étend pas [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) et a plusieurs bogues (voir le [problème 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)). Par conséquent, il est recommandé d’utiliser [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

|![Collection d’objets Grid-Cylindre](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Collection d’objets Grid-Cylindre | ![Collection d’objets GRID-SPHERE](../images/object-collection/MRTK_ObjectCollectionSphere.png) Collection d’objets GRID-SPHERE |
|:--- | :--- |
|![Collection d’objets Grid-radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) Collection d’objets Grid-radial | ![Collection d’objets Grid-plan](../images/object-collection/MRTK_ObjectCollectionPlane.png) Collection d’objets Grid-plan |
|![Collection d’objets éparpillés](../images/object-collection/MRTK_ObjectCollectionScattered.png) Collection d’objets éparpillés | ![Collection d’objets de grille de mosaïques](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Collection d’objets de grille de mosaïques |

## <a name="how-to-use-an-object-collection"></a>Utilisation d’une collection d’objets

Pour créer un regroupement, créez un GameObject vide et affectez-lui l’un des scripts de collection d’objets. Un ou plusieurs objets peuvent être ajoutés en tant qu’enfant de GameObject. Une fois que vous avez fini d’ajouter des objets enfants, cliquez sur le bouton *mettre à jour la collection* dans le panneau Inspecteur pour générer la collection d’objets. Les objets sont disposés dans la scène conformément aux paramètres de la collection. La mise à jour de la collection est également accessible par le biais du code.

![Script de collection d’objets](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` alignement du contenu

Le contenu d’un GridObjectCollection peut être aligné pour que l’objet parent soit ancré aux sommets, au milieu et à la gauche/au centre/à droite de la collection. Utilisez la propriété **Anchor** pour spécifier l’alignement du contenu.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` ordre de la disposition

Utilisez le champ **disposition** pour spécifier l’ordre des lignes/colonnes que les enfants sont disposés :

**Colonne Then** les enfants de ligne sont d’abord disposés horizontalement (par colonne), puis verticalement (par ligne). Utilisez la propriété **num Columns** (ou la propriété Columns dans le code) pour spécifier le nombre de colonnes dans la grille.

![Colonne, puis disposition de ligne](../images/object-collection/MRTK_ColumnThenRow.png)

La **ligne Then** , les enfants de colonne sont d’abord disposés verticalement (par ligne), puis horizontalement (par colonnes). Utilisez la propriété **num Rows** (ou la propriété Rows dans le code) pour spécifier le nombre de lignes dans la grille.

![Ligne, puis disposition des colonnes](../images/object-collection/MRTK_RowThenColumn.png)

Les enfants **horizontaux** sont disposés sur une seule ligne à l’aide de colonnes uniquement

**Vertical** -les enfants sont disposés dans une seule colonne à l’aide de lignes uniquement.

## <a name="object-collection-examples"></a>Exemples de collection d’objets

L' `ObjectCollectionExamples` exemple de scène (ressources/MRTK/exemples/démonstrations/UX/Collections/scènes/ObjectCollectionExamples. Unity) contient plusieurs exemples de types de collections d’objets.

[La table périodique des éléments](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) est un exemple d’application qui illustre le fonctionnement des collections d’objets. Elle utilise la collection d’objets pour mettre en forme les zones d’élément 3D dans différentes formes.

## <a name="object-collection-types"></a>Types de collections d’objets

**objets 3D**

Une collection d’objets peut être utilisée pour mettre en forme des objets 3D importés. L’exemple ci-dessous montre les dispositions planes et cylindriques des objets du modèle de chaise 3D à l’aide d’une collection.

![Collection d’objets 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**Objets 2D**

Une collection d’objets peut également être créé à partir d’images 2D. Par exemple, plusieurs images peuvent être placées dans un style de grille.

![Collection d’objets 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
