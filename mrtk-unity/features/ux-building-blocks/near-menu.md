---
title: Menu proche
description: Vue d’ensemble des types de menus proches dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Menu proche,
ms.openlocfilehash: 75e7ee195a5838e88c42b7547e7b75205bfe1ee2fa1c8b1ba0a868b294883347
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190620"
---
# <a name="near-menu"></a>Menu proche

![Menu Proximité](../images/near-menu/MRTK_UX_NearMenu.png)

Le menu proche est un contrôle d’expérience utilisateur qui fournit une collection de boutons ou d’autres composants d’interface utilisateur. Il est flottant autour du corps de l’utilisateur et facilement accessible à tout moment. Étant donné qu’elle est faiblement couplée avec l’utilisateur, elle ne perturbe pas l’interaction de l’utilisateur avec le contenu cible. L’utilisateur peut utiliser le bouton « épingler » pour verrouiller/déverrouiller le menu. Le menu peut être retiré et placé à une position spécifique.

## <a name="interaction-behavior"></a>Comportement d’interaction

- **Balise**: le menu vous suit et reste dans la plage de 30 60cm de l’utilisateur pour les interactions proches.
- **Pin**: à l’aide du bouton « épingler », le menu peut être verrouillé et relâché.
- **Manipulation et déplacement**: le menu est toujours pouvant être retiré et déplaçable. Quel que soit l’état précédent, le menu est épinglé (verrouillage universel) lorsqu’il est retiré et relâché. Il existe des signaux visuels pour la zone qui peut être saisie. Ils sont révélés à proximité.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Prefabs

Le menu prefabs est conçu pour illustrer l’utilisation de divers composants de MRTK pour générer des menus pour les interactions proches.

- **NearMenu2x4. Prefab**
- **NearMenu3x1. Prefab**
- **NearMenu3x2. Prefab**
- **NearMenu3x3. Prefab**
- **NearMenu4x1. Prefab**
- **NearMenu4x2. Prefab**

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples de prefabs dans la `NearMenuExamples` scène.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Structure

Les prefabs des menus proches sont créés avec les composants MRTK suivants.

- [**PressableButtonHoloLens2**](button.md) Prefab
- [**Collection d’objets Grid**](object-collection.md): disposition à plusieurs boutons dans la grille
- [**Gestionnaire de manipulation**](manipulation-handler.md): récupérer et déplacer le menu
- [**Solveur RadialView**](solvers/solver.md): suivre le comportement (balise)

![Près du menu Prefab](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Comment personnaliser

**1. Ajouter/supprimer des boutons**

Sous `ButtonCollection` objet, ajoutez ou supprimez des boutons.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. mettre à jour la collection d’objets Grid**

Cliquez sur `Update Collection` le bouton dans l’inspecteur de l' `ButtonCollection` objet. Elle met à jour la disposition de grille.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

Vous pouvez configurer le nombre de lignes à l’aide `Rows` de la propriété de la collection d’objets Grid.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. ajuster la taille de la plaque**

Ajustez la taille du `Quad` sous- `Backplate` objet. La largeur et la hauteur de l’arrière-plaque doivent être `0.032 * [Number of the buttons + 1]` . Par exemple, si vous avez 3 boutons x 2, la largeur de l’arrière-plaque est `0.032 * 4` et la hauteur est `0.032 * 3` . Vous pouvez placer cette expression directement dans le champ Unity.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- la taille par défaut du bouton HoloLens 2 est 3,2 x 3,2 cm (0.032 m)

## <a name="see-also"></a>Voir aussi

- [**Boutons**](button.md)
- [**Contrôle de limites**](bounds-control.md)
- [**Curseur**](sliders.md)
- [**Collection d’objets Grid**](object-collection.md)
- [**Gestionnaire de manipulation**](manipulation-handler.md)
- [**Solveur RadialView**](solvers/solver.md)
