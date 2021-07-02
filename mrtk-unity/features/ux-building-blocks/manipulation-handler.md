---
title: Gestionnaire de manipulation
description: Documentation sur le gestionnaire de manipulation dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Manipulation,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176633"
---
# <a name="manipulation-handler"></a>Gestionnaire de manipulation

![Gestionnaire de manipulation](../images/manipulation-handler/MRTK_Manipulation_Main.png)

Le script *ManipulationHandler* permet à un objet d’être rendu mobile, évolutif et rotatif à l’aide d’une ou de deux mains. La manipulation peut être restreinte afin d’autoriser uniquement certains genres de transformations. le script fonctionne avec différents types d’entrées, y compris HoloLens 2 entrée articulée, des rayons, des HoloLens (1ère génération) entrée de mouvement et une entrée de contrôleur de mouvement du casque immersif.

## <a name="how-to-use-the-manipulation-handler"></a>Comment utiliser le gestionnaire de manipulation

Ajoutez le `ManipulationHandler` composant script à un GameObject. Veillez à ajouter également un conflit à l’objet, en faisant correspondre ses limites récupérables.

Pour faire en sorte que l’objet réponde à une entrée presque articulée, ajoutez `NearInteractionGrabbable` également le script.

![Utilisation du gestionnaire de manipulation dans l’éditeur Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>Propriétés de l’inspecteur

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**Transformation** de l’hôte Transformation qui sera glissée. La valeur par défaut est l’objet du composant.

**Type de manipulation** Spécifie si l’objet peut être manipulé à l’aide d’une main, de deux mains ou les deux.

* *Une seule remise*
* *Deux mains uniquement*
* *Un et deux droitiers*

**Type de manipulation à deux mains**

* *Scale*: seule la mise à l’échelle est autorisée.
* *Rotate*: seule la rotation est autorisée.
* *Échelle de déplacement*: le déplacement et la mise à l’échelle sont autorisés.
* *Move Rotate*: le déplacement et la rotation sont autorisés.
* *Rotation* de l’échelle : la rotation et la mise à l’échelle sont autorisées.
* *Déplacer l’échelle de rotation*: le déplacement, la rotation et la mise à l’échelle sont autorisés.

![Gestionnaire de manipulation](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**Autoriser la manipulation Far** Spécifie si la manipulation peut être effectuée à l’aide de l’interaction Far avec les pointeurs.

**Mode de rotation à un seul côté** Spécifie la manière dont l’objet se comporte lorsqu’il est retiré d’une main ou d’un contrôleur à proximité.

**Mode de rotation d’un côté** Spécifie la manière dont l’objet se comportera lorsqu’il sera retiré d’une main/d’un contrôleur à distance.

**Options du mode de rotation d’une main** Spécifie le mode de rotation de l’objet lorsqu’il est retiré d’une main.

* *Conserver la rotation d’origine*: ne pivote pas l’objet tel qu’il est déplacé
* *Conserver la rotation vers l’utilisateur*: maintient la rotation d’origine de l’objet pour l’axe X/Y à l’utilisateur
* La *gravité alignée maintenir la rotation sur l’utilisateur*: maintient la rotation d’origine de l’objet à l’utilisateur, mais rend l’objet vertical. Utile pour les objets avec un contrôle de limites.
* *Visage User*: garantit que l’objet est toujours face à l’utilisateur. Utile pour les ardoises/panneaux.
* *Face à l’utilisateur*: garantit que l’objet est toujours face à l’utilisateur. Utile pour les ardoises/panneaux configurés en arrière.
* *Faire pivoter à propos du centre d’objets*: fonctionne uniquement pour les mains/contrôleurs articulés. Faire pivoter l’objet à l’aide de la rotation de la main/du contrôleur, mais à propos du point central de l’objet. Utile pour l’inspection à distance.
* *Faire pivoter à propos du point de manipulation*: fonctionne uniquement pour les mains/contrôleurs articulés. Faire pivoter l’objet comme s’il était maintenu par la main/le contrôleur. Utile pour l’inspection.

**Comportement** de la version Lorsqu’un objet est relâché, spécifiez son comportement de déplacement physique. Nécessite un composant RigidBody pour être sur cet objet.

* *Nothing*
* *Tout*
* *Conserver la vélocité*
* *conserver Angular vélocité*

**Contraintes de rotation** Spécifie l’axe avec lequel l’objet pivotera lorsqu’il est interagi.

* *Aucun*
* *Axe X uniquement*
* *Axe Y uniquement*
* *Axe Z uniquement*

**Utiliser l’espace local pour la contrainte** Bouton bascule pour basculer entre l’application de contraintes par rapport à l’axe d’espace universel ou l’axe d’espace local.

**Contraintes sur le mouvement**

* *Aucun*
* *Corriger la distance par rapport à la tête*

**Lissage actif** Spécifie si le lissage est actif.

**Lissage de la quantité d’une main** Quantité de lissage à appliquer au mouvement, à l’échelle et à la rotation. Le lissage de 0 signifie qu’il n’y a pas de lissage. La valeur Max signifie qu’aucune modification n’est apportée à la valeur.

## <a name="events"></a>Événements

Le gestionnaire de manipulation fournit les événements suivants :

* *OnManipulationStarted*: déclenché lorsque la manipulation démarre.
* *OnManipulationEnded*: se déclenche lorsque la manipulation se termine.
* *OnHoverStarted*: se déclenche quand une main/un contrôleur pointe le manipulable, proche ou loin.
* *OnHoverEnded*: se déclenche quand une main/un contrôleur ne fait pas pointer le manipulable, à proximité ou à l’extrême.
