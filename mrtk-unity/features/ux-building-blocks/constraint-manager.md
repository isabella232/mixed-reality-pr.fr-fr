---
title: Gestionnaire de contraintes
description: Vue d’ensemble du gestionnaire de contraintes dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177550"
---
# <a name="constraint-manager"></a>Gestionnaire de contraintes

Le gestionnaire de contraintes permet d’appliquer un ensemble de composants de contrainte à une transformation. Les composants de type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) qui sont attachés à l’objet de jeu peuvent être pris en compte.
Par défaut, le gestionnaire de contraintes collecte automatiquement tous les [composants de contrainte](#transform-constraints) attachés à l’objet de jeu et les applique aux transformations traitées.
Toutefois, les utilisateurs peuvent opter pour la configuration manuelle de la liste des contraintes appliquées et autoriser uniquement l’application d’un sous-ensemble de contraintes attachées.

Actuellement, les éléments MRTK UX suivants prennent en charge le gestionnaire de contraintes :

- [Contrôle de limites](bounds-control.md)
- [Manipulateur d’objets](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Propriétés et champs de l’inspecteur

Le gestionnaire de contraintes peut être utilisé en deux modes :

- Sélection de contrainte automatique
- Sélection manuelle des contraintes

### <a name="auto-constraint-selection"></a>Sélection de contrainte automatique

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

Le mode par défaut du gestionnaire de contraintes, la sélection de contrainte automatique, fournit une liste de tous les composants de contrainte attachés, ainsi que les [boutons](#go-to-component) et le [bouton Ajouter une contrainte](#add-constraint-to-game-object).

#### <a name="add-constraint-to-game-object"></a>Ajouter une contrainte à un objet de jeu

Ce bouton permet d’ajouter un composant de contrainte directement à partir de l’inspecteur du gestionnaire de contraintes. Tous les types de contrainte d’un projet doivent être visibles ici. Pour plus d’informations, consultez [contraintes de transformation](#transform-constraints) .

#### <a name="go-to-component"></a>Atteindre le composant

Toutes les contraintes trouvées sur l’objet sont répertoriées ici avec un bouton *atteindre le composant* . Ce bouton permet à l’inspecteur de faire défiler le composant de contrainte sélectionné afin qu’il puisse être configuré.

### <a name="manual-constraint-selection"></a>Sélection manuelle des contraintes

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

Si le gestionnaire de contraintes est défini en mode manuel, seules les contraintes qui sont liées dans la liste de contraintes sont traitées et appliquées à la transformation. La liste affichée affiche uniquement les contraintes sélectionnées par l’utilisateur, ainsi que les [boutons](#go-to-component) ou options permettant de supprimer ou d’ajouter des entrées.
Lorsque vous activez le mode manuel pour la première fois, le gestionnaire de contraintes remplit la liste tous les composants disponibles comme point de départ pour sélectionner les composants de contrainte attachés.

### <a name="remove-entry"></a>Supprimer l’entrée

Cela supprime l’entrée de la liste sélectionnée manuellement. Notez que cette option ne supprime pas le composant de contrainte de l’objet de jeu. Les composants de contrainte doivent toujours être supprimés manuellement pour éviter toute rupture accidentelle d’un autre composant faisant référence à ce composant.

### <a name="add-entry"></a>Ajouter une entrée

Ajouter une entrée ouvre une liste déroulante indiquant tous les composants de contrainte disponibles qui ne sont pas encore dans la liste manuelle. En cliquant sur l’une des entrées que le composant sera ajouté à la sélection de contrainte manuelle.

### <a name="add-new-constraint"></a>Ajouter une nouvelle contrainte

Cette option permet d’ajouter un composant du type sélectionné à l’objet de jeu et d’ajouter le composant de contrainte nouvellement créé à la liste de contraintes manuelle.

## <a name="transform-constraints"></a>Contraintes de transformation

Les contraintes peuvent être utilisées pour limiter la manipulation d’une certaine façon. Par exemple, certaines applications peuvent nécessiter une rotation, mais nécessitent également que l’objet reste debout. Dans ce cas, un `RotationAxisConstraint` peut être ajouté à l’objet et utilisé pour limiter la rotation à la rotation de l’axe y. MRTK fournit un certain nombre de contraintes, qui sont toutes décrites ci-dessous.

Il est également possible de définir de nouvelles contraintes et de les utiliser pour créer des comportements de manipulation uniques qui peuvent être nécessaires pour certaines applications. Pour ce faire, créez un script qui hérite de [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) et implémentez la `ConstraintType` propriété abstraite et la méthode abstraite `ApplyConstraint` . Lors de l’ajout d’une nouvelle contrainte à l’objet, elle doit contraindre la manipulation de la manière définie. Cette nouvelle contrainte doit également apparaître dans la liste déroulante gestionnaire de contraintes [automatique](#auto-constraint-selection) ou [Ajouter une entrée](#add-entry) en mode manuel.

Toutes les contraintes fournies par MRTK partagent les propriétés suivantes :

#### <a name="hand-type"></a>Type de main

Spécifie si la contrainte est utilisée pour une main, deux types de manipulation ou les deux. Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.

- *Une droitier*: la contrainte sera utilisée pendant une manipulation de la droitier, si elle est sélectionnée.
- *Deux droitiers*: la contrainte sera utilisée pendant deux manipulations de la main, si elle est sélectionnée.

#### <a name="proximity-type"></a>Type de proximité

Spécifie si la contrainte est utilisée pour les genres near ou FAR, ou les deux. Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.

- *Near*: la contrainte sera utilisée pendant une manipulation proche si elle est sélectionnée.
- *Far*: la contrainte sera utilisée lors de la manipulation Far si elle est sélectionnée.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

Lorsque cette contrainte est attachée à un objet, la rotation est limitée afin que l’objet soit toujours à la tête de l’utilisateur. Cela est utile pour les ardoises ou les panneaux. Les propriétés de `FaceUserConstraint` sont les suivantes :

#### <a name="face-away"></a>Facer

L’objet est face à l’utilisateur si la valeur est true.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

Cette contrainte fixe la distance entre l’objet manipulé et une autre transformation d’objet au début de la manipulation. Cela est utile pour le comportement, par exemple la résolution de la distance entre l’objet manipulé et la transformation de l’en-tête. Les propriétés de `FixedDistanceConstraint` sont les suivantes :

#### <a name="constraint-transform"></a>Transformation de contrainte

Il s’agit de l’autre transformation que l’objet manipulé aura une distance fixe. La valeur par défaut est la transformation de l’appareil photo.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

Cette contrainte résout la rotation relative entre l’utilisateur et l’objet manipulé pendant qu’il est manipulé. Cela est utile pour les ardoises ou les panneaux, car il garantit que l’objet manipulé affiche toujours la même face à l’utilisateur qu’au début de la manipulation. Le `FixedRotationToUserConstraint` n’a pas de propriétés uniques.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

Cette contrainte résout la rotation globale de l’objet manipulé pendant qu’il est manipulé. Cela peut être utile dans les cas où aucune rotation ne doit être concédée par une manipulation. Le `FixedRotationToWorldConstraint` n’a pas de propriétés uniques :

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

Lorsque cette contrainte est attachée à un objet, quelle que soit la portée de l’objet par rapport à l’utilisateur, elle conserve la même taille apparente pour l’utilisateur (autrement dit, elle prend la même proportion du champ de vue de l’utilisateur). Cela peut être utilisé pour s’assurer qu’un ardoise ou un panneau de texte restent lisibles lors de la manipulation. Le `MaintainApparentSizeConstraint` n’a pas de propriétés uniques :

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Cette contrainte peut être utilisée pour résoudre les axes sur lesquels un objet manipulé peut être déplacé. Cela peut être utile pour manipuler des objets sur la surface d’un plan ou sur une ligne. Les propriétés de `MoveAxisConstraint` sont les suivantes :

#### <a name="constraint-on-movement"></a>Contrainte de mouvement

Spécifie les axes sur lesquels le déplacement doit être interdit. Par défaut, ces axes sont globaux plutôt que locaux, mais cela peut être modifié ci-dessous. Étant donné que cette propriété est un indicateur, vous pouvez sélectionner n’importe quel nombre d’options.

- *Axe des x*: le mouvement le long de l’axe x est restreint s’il est sélectionné.
- *Axe y*: le mouvement le long de l’axe y est restreint s’il est sélectionné.
- *Axe z*: le mouvement le long de l’axe z est restreint s’il est sélectionné.

#### <a name="use-local-space-for-constraint"></a>Utiliser l’espace local pour la contrainte

Applique une contrainte relative aux axes de transformation locaux de l’objet manipulé si la valeur est true. False par défaut.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Cette contrainte peut être utilisée pour résoudre les axes sur lesquels un objet manipulé peut pivoter. Cela peut être utile pour maintenir un objet manipulé à la verticale, tout en autorisant les rotations de l’axe y, par exemple. Les propriétés de `RotationAxisConstraint` sont les suivantes :

#### <a name="constraint-on-rotation"></a>Contrainte de rotation

Spécifie les axes à propos desquels empêcher la rotation. Par défaut, ces axes sont globaux plutôt que locaux, mais cela peut être modifié ci-dessous. Étant donné que cette propriété est un indicateur, vous pouvez sélectionner n’importe quel nombre d’options.

- *Axe y*: la rotation autour de l’axe des y est restreinte si elle est sélectionnée.
- *Axe z*: la rotation autour de l’axe z est restreinte si elle est sélectionnée.
- *Axe x*: la rotation autour de l’axe des x est restreinte si elle est sélectionnée.

#### <a name="use-local-space-for-constraint"></a>Utiliser l’espace local pour la contrainte

Applique une contrainte relative aux axes de transformation locaux de l’objet manipulé si la valeur est true. False par défaut.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

Cette contrainte permet de définir des valeurs minimales et maximales pour l’échelle de l’objet manipulé. Cela est utile pour empêcher les utilisateurs de mettre à l’échelle un objet trop petit ou trop grand. Les propriétés de `MinMaxScaleConstraint` sont les suivantes :

#### <a name="scale-minimum"></a>Échelle minimale

Valeur de mise à l’échelle minimale pendant la manipulation.

#### <a name="scale-maximum"></a>Échelle maximale

Valeur d’échelle maximale pendant la manipulation.

#### <a name="relative-to-initial-state"></a>Par rapport à l’état initial

Si la valeur est true, les valeurs ci-dessus seront interprétées par rapport à l’échelle initiale des objets. Dans le cas contraire, ils seront interprétés comme des valeurs de mise à l’échelle absolue.
