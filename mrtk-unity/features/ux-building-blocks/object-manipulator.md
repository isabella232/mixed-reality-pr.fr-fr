---
title: Manipulateur d’objets
description: Comment utiliser le manipulateur d’objets dans MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Manipulation d’objets,
ms.openlocfilehash: 4c43a35e164d3e66e662afc927d28f84463e1586250e9847a2d88c219ba27f23
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191610"
---
# <a name="object-manipulator"></a>Manipulateur d’objets

![Manipulateur d’objets](../images/manipulation-handler/MRTK_Manipulation_Main.png)

Le *ObjectManipulator* est le nouveau composant pour le comportement de manipulation, précédemment trouvé dans *ManipulationHandler*. Le manipulateur d’objets apporte un certain nombre d’améliorations et de simplifications. Ce composant remplace le gestionnaire de manipulation, qui sera déconseillé.

Le script *ObjectManipulator* rend un objet déplaçable, évolutif et rotatif à l’aide d’une ou de deux mains. Le manipulateur d’objets peut être configuré pour contrôler la façon dont l’objet répondra à différentes entrées. le script doit fonctionner avec la plupart des formes d’interaction, telles que HoloLens 2 articulées, HoloLens 2 rayons, HoloLens 1 point de regard, les gestes et l’entrée du contrôleur de mouvement du casque immersif.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>Comment utiliser le manipulateur d’objets

Pour utiliser le manipulateur d’objets, ajoutez d’abord le `ObjectManipulator` composant script à un GameObject. Veillez à ajouter également un conflit à l’objet, en faisant correspondre ses limites récupérables.

Pour faire en sorte que l’objet réponde à une entrée presque articulée, ajoutez `NearInteractionGrabbable` également le script.

Le comportement physique peut être activé pour le manipulateur d’objets en ajoutant un composant RigidBody à l’objet. Le comportement physique activé par l’ajout de ce composant est abordé plus en détail dans [*physique et collisions*](#physics-and-collisions).

De même, la manipulation peut être contrainte en ajoutant des composants de [contrainte de manipulation](constraint-manager.md#transform-constraints) à l’objet. Il s’agit de composants spéciaux qui fonctionnent avec la manipulation et modifient le comportement de manipulation d’une certaine façon.

![Utilisation du gestionnaire de manipulation dans l’éditeur Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Propriétés et champs de l’inspecteur

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>Propriétés générales

#### <a name="host-transform"></a>Transformation de l’hôte

Transformation d’objet qui sera manipulée. La valeur par défaut est l’objet du composant.

#### <a name="manipulation-type"></a>Type de manipulation

Spécifie si l’objet peut être manipulé à l’aide d’une main ou de deux mains. Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.

- *Une droitier*: active une manipulation de la main si elle est sélectionnée.
- *Deux droitiers*: active deux manipulations de la main si elles sont sélectionnées.

#### <a name="allow-far-manipulation"></a>Autoriser la manipulation Far

Spécifie si la manipulation peut être effectuée à l’aide de l’interaction Far avec les pointeurs.

### <a name="one-handed-manipulation-properties"></a>Propriétés de manipulation à une seule main

#### <a name="one-hand-rotation-mode-near"></a>Mode de rotation à un seul côté

Spécifie la manière dont l’objet se comporte lorsqu’il est retiré d’une main à proximité. Ces options ne fonctionnent que pour les mains articulées.

- *Faire pivoter à propos du centre d’objets*: l’objet pivote à l’aide de la rotation de la main, mais à propos du point central de l’objet. L’objet s’affiche pour se déplacer moins au fur et à mesure qu’il pivote, mais il peut y avoir un sentiment de déconnexion entre la main et l’objet. Plus utile pour une interaction extrême.
- *Faire pivoter à propos du point de manipulation*: faire pivoter un objet à la main sur le point de manipulation entre le curseur de défilement et l’index. Elle doit ressembler à si l’objet est détenu par la main.

#### <a name="one-hand-rotation-mode-far"></a>Mode de rotation d’un côté

Spécifie la manière dont l’objet se comporte lorsqu’il est retiré d’une main à distance. Ces options ne fonctionnent que pour les mains articulées.

- *Faire pivoter à propos de Object Center*: faire pivoter l’objet à l’aide de la rotation de la main, mais à propos du point central de l’objet. Utile pour l’inspection à distance sans que le centre d’objets se déplace au fur et à mesure que l’objet pivote.
- *Faire pivoter à propos du point de manipulation*: faire pivoter l’objet à l’aide de la rotation de la main, mais à propos du point d’accès de Ray Utile pour l’inspection.

### <a name="two-handed-manipulation-properties"></a>Deux propriétés de manipulation de la main

#### <a name="two-handed-manipulation-type"></a>Type de manipulation à deux mains

Spécifie la manière dont deux manipulations de main peuvent transformer un objet. Étant donné que cette propriété est un indicateur, vous pouvez sélectionner n’importe quel nombre d’options.

- *Move*: le déplacement est autorisé si l’option est sélectionnée.
- *Scale*: la mise à l’échelle est autorisée si elle est sélectionnée.
- *Rotate*: la rotation est autorisée si elle est sélectionnée.

![Gestionnaire de manipulation](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Contraintes

#### <a name="enable-constraints"></a>Activer les contraintes

Ce paramètre active le gestionnaire de [contraintes](constraint-manager.md)lié. Les modifications de transformation sont traitées par les contraintes inscrites dans le [Gestionnaire de contraintes](constraint-manager.md)sélectionné.

#### <a name="constraint-manager"></a>Gestionnaire de contraintes

La liste déroulante permet de sélectionner l’un des [gestionnaires de contraintes](constraint-manager.md)attachés. Le manipulateur d’objets s’assure qu’un [Gestionnaire de contraintes](constraint-manager.md) est attaché à tout moment.
Notez que plusieurs composants du même type s’affichent sous le même nom dans Unity. Pour faciliter la distinction entre plusieurs gestionnaires de contraintes sur le même objet, les options disponibles présentent un indicateur sur la configuration du gestionnaire de contraintes sélectionné (sélection de contrainte manuelle ou automatique).

#### <a name="go-to-component"></a>Atteindre le composant

La sélection du gestionnaire de contraintes est accompagnée d’un bouton *atteindre le composant* . Ce bouton permet à l’inspecteur de faire défiler le composant sélectionné afin qu’il puisse être configuré.

### <a name="physics"></a>Physique

Paramètres dans cette section s’affichent uniquement lorsque l’objet a un composant RigidBody.

#### <a name="release-behavior"></a>Comportement de la version

Spécifiez les propriétés physiques qu’un objet manipulé doit conserver lors de la libération. Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.

- *Conserver la vélocité*: lorsque l’objet est relâché, si cette option est sélectionnée, elle conserve sa vélocité linéaire.
- *conserver Angular vélocité*: lorsque l’objet est relâché, si cette option est sélectionnée, elle conserve sa vélocité angulaire.

#### <a name="use-forces-for-near-manipulation"></a>Utiliser des forces pour la manipulation proche

Indique si les forces physiques sont utilisées pour déplacer l’objet lors de l’exécution de la manipulation proche. Si vous affectez la *valeur false* , l’objet sera plus directement connecté à la main des utilisateurs. Si vous affectez la *valeur true* , vous honorerez la masse et l’inertie de l’objet, mais cela peut être semblable au fait que l’objet est connecté via un ressort. La valeur par défaut est *false*.

### <a name="smoothing"></a>Adoucissage

#### <a name="smoothing-far"></a>Lissage Far

Indique si le lissage indépendant de la cadence d’images est activé pour les interactions Far. Le lissage FAR est activé par défaut.

#### <a name="smoothing-near"></a>Lissage à proximité

Indique si le lissage indépendant de la cadence d’images est activé pour les interactions proches. Le lissage proche est désactivé par défaut, car l’effet peut être perçu comme étant « déconnecté » de la main.

#### <a name="smoothing-active"></a>Lissage actif

Obsolète et sera supprimé dans une version ultérieure. Les applications doivent utiliser SmoothingFar, SmoothingNear ou une combinaison des deux.

#### <a name="move-lerp-time"></a>Déplacer le temps de Lerp

Quantité de lissage à appliquer au mouvement. Le lissage de 0 signifie qu’il n’y a pas de lissage. La valeur Max signifie qu’aucune modification n’est apportée à la valeur.

#### <a name="rotate-lerp-time"></a>Faire pivoter Lerp Time

Quantité de lissage à appliquer à la rotation. Le lissage de 0 signifie qu’il n’y a pas de lissage. La valeur Max signifie qu’aucune modification n’est apportée à la valeur.

#### <a name="scale-lerp-time"></a>Mettre à l’échelle le temps Lerp

Quantité de lissage à appliquer à l’échelle. Le lissage de 0 signifie qu’il n’y a pas de lissage. La valeur Max signifie qu’aucune modification n’est apportée à la valeur.

### <a name="manipulation-events"></a>Événements de manipulation

Le gestionnaire de manipulation fournit les événements suivants :

- *OnManipulationStarted*: déclenché lorsque la manipulation démarre.
- *OnManipulationEnded*: se déclenche lorsque la manipulation se termine.
- *OnHoverStarted*: se déclenche quand une main/un contrôleur pointe le manipulable, proche ou loin.
- *OnHoverEnded*: se déclenche quand une main/un contrôleur ne fait pas pointer le manipulable, à proximité ou à l’extrême.

L’ordre de déclenchement des événements pour la manipulation est le suivant :

*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*

S’il n’y a aucune manipulation, vous obtiendrez toujours des événements de pointage avec l’ordre de déclenchement suivant :

*OnHoverStarted*  ->  *OnHoverEnded*

## <a name="physics-and-collisions"></a>Physique et collisions

Le comportement physique peut être activé en ajoutant un composant RigidBody au même objet qu’un manipulateur d’objets. Non seulement cela permet la configuration du [comportement de mise en version](#release-behavior) ci-dessus, mais elle active également les collisions. Sans composant RigidBody, les collisions ne se comportent pas correctement pendant la manipulation :

- Les collisions entre un objet manipulé et un conflit statique (c’est-à-dire un objet avec un conflit mais sans RigidBody) ne fonctionnent pas, l’objet manipulé passe directement par le conflit statique qui n’est pas affecté.
- Collisions entre un objet manipulé et un RigidBody (c.-à-d. un objet avec à la fois un conflit et un RigidBody) entraîne une réponse de collision du RigidBody, mais la réponse est indirecte et non naturelle. Il n’y a pas non plus de réponse de collision sur l’objet manipulé.

Quand un RigidBody est ajouté, les collisions doivent fonctionner correctement.

### <a name="without-rigidbody"></a>Sans RigidBody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>Avec RigidBody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Élastiques (expérimental)

Les élastiques peuvent être utilisés lors de la manipulation d’objets via le manipulateur d’objets. Notez que le [système élastiques](../experimental/elastic-system.md) est toujours dans un État expérimental. Pour activer les élastiques, liez un composant Gestionnaire élastique existant ou créez et liez un nouveau gestionnaire élastiques à l’aide du `Add Elastics Manager` bouton.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>Voir aussi

- [Contrôle des limites](bounds-control.md)
- [Gestionnaire de contraintes](constraint-manager.md)
- [Fenêtre de migration](../tools/migration-window.md)
- [Système élastique (expérimental)](../experimental/elastic-system.md)
