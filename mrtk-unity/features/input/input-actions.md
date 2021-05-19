---
title: Actions d’entrée
description: Documentation pour créer des actions d’entrée dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144153"
---
# <a name="input-actions"></a>Actions d’entrée

Les [**actions d’entrée**](input-actions.md) sont des abstractions sur les entrées brutes destinées à aider à isoler la logique d’application des sources d’entrée spécifiques produisant une entrée. Il peut être utile, par exemple, de définir une action *Select* et de la mapper au bouton gauche de la souris, un bouton dans un boîtier de commande et un déclencheur dans un contrôleur 6 DDL. Vous pouvez ensuite faire en sorte que la logique de votre application écoute les événements de l’action d’entrée *Select* au lieu d’avoir à connaître toutes les différentes entrées pouvant la produire.

## <a name="creating-an-input-action"></a>Création d’une action d’entrée

Les actions d’entrée sont configurées dans le **Profil actions d’entrée**, à l’intérieur du *profil de système d’entrée* dans le composant d’outils de réalité mixte, en spécifiant un nom pour l’action et le type d’entrées (*contrainte d’axe*) qu’elle peut être mappée à :

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Il s’agit des valeurs les plus couramment utilisées pour la **contrainte d’axe**:

Contrainte d’axe | Description
--- | ---
Digital | Entrée on/off comme un bouton binaire dans un boîtier de connexion ou une souris.
Axe unique | Entrée analogique à un seul axe comme un déclencheur analogique dans un boîtier de souformement.
Axe double | Entrée analogique à deux axes comme un stick analogique.
Six DDL | composition 3D avec traduction et rotation comme celle produite par 6 contrôleurs DDL.

Vous trouverez la liste complète dans [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Mappage de l’entrée aux actions

La façon dont vous mappez une entrée à et l’action dépend du type de la source d’entrée :

### <a name="controller-input"></a>Entrée du contrôleur

Accédez au **profil de mappage d’entrée du contrôleur**, sous le profil de *système d’entrée*. Vous y trouverez une liste de tous les contrôleurs pris en charge :

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Sélectionnez celui que vous souhaitez configurer et une fenêtre de dialogue s’affiche avec toutes les entrées du contrôleur, ce qui vous permet de définir une action pour chacun d’entre eux :

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>SpeechInput

Dans le **profil de commande Speech**, sous le *profil de système d’entrée*, vous trouverez la liste des commandes vocales actuellement définies. Pour mapper l’une d’entre elles à une action, sélectionnez-la dans la liste déroulante *action* .

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Entrée de mouvement

Le **profil de mouvements**, sous le *profil de système d’entrée*, contient tous les mouvements définis. Vous pouvez mapper chacune d’elles à une action en la sélectionnant dans la liste déroulante *action* .

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Gestion des actions d’entrée

> [!WARNING]
> Actuellement, seules les actions d’entrée de type *numérique* peuvent être gérées à l’aide des méthodes décrites dans cette section. Pour les autres types d’action, vous devez gérer directement les événements pour les entrées correspondantes. Par exemple, pour gérer une action de 6 DDL mappée aux entrées du contrôleur, vous devez utiliser [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) avec T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Le moyen le plus simple de gérer les actions d’entrée consiste à utiliser le [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script. Cela vous permet de définir l’action que vous souhaitez écouter et de réagir aux événements d’action démarrés et terminés à l’aide d’événements Unity.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Si vous souhaitez davantage de contrôle, vous pouvez implémenter l' [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directement dans votre script. Pour plus d’informations sur la gestion des événements via des interfaces de gestionnaire, consultez la section [**événements d’entrée**](input-events.md) .

## <a name="examples"></a>Exemples

`MRTK/Examples/Demos/Input/Scenes/InputActions`Pour obtenir un exemple de scène illustrant comment créer une action, mappez-la à des entrées de contrôleur, de voix et de mouvement et utilisez-la pour faire pivoter un objet sur une commande.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
