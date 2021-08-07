---
title: Coach de main
description: Description et exemples pour la surveillance manuelle.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 3e5a56f7498288e79963acea6fca223421fee2607004a9a2bae639f81441e0d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209022"
---
# <a name="hand-coach"></a>Coach de main

![Menu de la main](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

La main est modelée en 3D qui est déclenchée lorsque le système ne détecte pas les mains de l’utilisateur. Elle est implémentée en tant que composant « d’apprentissage » qui aide à guider l’utilisateur lorsque le mouvement n’a pas été enseigné. Si les utilisateurs n’ont pas effectué le mouvement spécifié pour un point, les mains sont en boucle avec un délai. L’autocar peut être utilisé pour représenter une pression sur un bouton ou un hologramme.

Le modèle d’interaction actuel représente un large éventail de contrôles de mouvement, tels que le défilement, l’amplitude de sélection et le TAP. Vous trouverez ci-dessous une liste complète des exemples de coachs existants :

- Presque appuyé : utilisé pour les boutons ou fermer les objets interactifs
- Bien sélectionner – utilisé pour les objets éloignés
- Move : permet de déplacer un hologramme dans l’espace
- Rotate : utilisé pour montrer comment faire pivoter des hologrammes ou des objets
- Scale : utilisé pour montrer comment manipuler les hologrammes pour les agrandir ou les réduire
- Flip main : permet d’ouvrir un panneau de démarrage de l’interface utilisateur ou des menus manuels
- Paume, utilisé pour le moment Hummingbird dans l’expérience prête à l’emploi. Une autre suggestion consiste à afficher un panneau de démarrage de l’interface utilisateur
- Scroll : utilisé pour faire défiler une liste ou un long document

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples dans la scène **HandCoachExample** sous : [MixedRealityToolkit. examples/expérimental/HandCoach/scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Ressources 3D main

Vous pouvez trouver les ressources sous : [MixedRealityToolkit. SDK/expérimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualité

Si vous remarquez des distorsions sur le maillage dépouillé, vous devez vous assurer que votre projet utilise la quantité appropriée de jointures.
accédez à modifier > Project Paramètres > qualité > autres poids de fusion >. Assurez-vous que « 4 segments » sont sélectionnés pour afficher des articulations lisses.
![Project Défini](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>scripts ;

### <a name="interaction-hint"></a>Indicateur d’interaction

Le `InteractionHint.cs` script fournit des fonctionnalités wrapper pour déclencher des animations et des fondus pour la plate-forme de test.

#### <a name="how-to-set-up-an-interaction-hint"></a>Comment configurer un indicateur d’interaction

Pour configurer un indicateur d’interaction, il est recommandé d’utiliser le prefabs « StaticHandCoachRoot_L. Prefab » et le « StaticHandCoachRoot_R. Prefab » fournis. Ce Prefab contient le script InteractionHint et la plate-forme, ainsi que la hiérarchie appropriée pour s’assurer que les animations Hint fournies fonctionnent comme prévu.
Dans le cas contraire, vous devez placer le script sur un niveau parent gameObject à partir de votre plate-forme à l’aide de l’animateur.

#### <a name="inspector-properties"></a>Propriétés de l’inspecteur

- **HideIfHandTracked** Cette valeur booléenne spécifie si l’état de suivi de la main doit être utilisé pour masquer les éléments visuels lorsque les mains d’un utilisateur font l’objet d’un suivi. Si la valeur est false, seule la propriété de script « customShouldHideVisuals » sera utilisée pour déterminer s’il faut masquer l’indicateur.

- **MinDelay** Cette propriété spécifie le délai minimal pour l’indication des visuels. Par défaut, les visuels de la main s’affichent après ce nombre de secondes si les mains de l’utilisateur ne sont pas suivies.

- **MaxDelay** Cette propriété spécifie le délai maximal pour l’indication des visuels. Par défaut, les visuels de la main s’affichent après ce nombre de secondes, même si les mains de l’utilisateur font l’objet d’un suivi.

- **UseMaxTimer** Si cette valeur booléenne est définie sur false, elle désactive la minuterie Max et autorise uniquement l’affichage de l’indicateur main lorsque les mains de l’utilisateur ne sont pas affichées, ou lorsque la condition personnalisée retourne false.

- **Répète** Cette propriété contrôle le nombre de fois que l’animation des indicateurs est lue lorsque la minuterie min ou Max est passée. L’indicateur masque et attend à nouveau le délai.

- **Activer auto** Lorsque cette valeur booléenne est définie sur true, l’indicateur s’exécute automatiquement via la logique du minuteur lorsque le GameObject du script est actif dans la hiérarchie et que le script est activé. Cette valeur doit être définie sur false uniquement si vous envisagez de contrôler manuellement l’apparence et la disparition de l’indicateur par le biais du code.

- **AnimationState** Nom de l’état d’animation qui doit s’exécuter lorsque l’indicateur est actif. Cette valeur doit être définie avant l’appel de la fonction StartHintLoop () (au cours de OnEnable si AutoActivate est activé).

#### <a name="controlling-interactionhint-via-script"></a>Contrôle des InteractionHint à l’aide d’un script

- **StartHintLoop** Cette fonction démarre la boucle d’affichage/de masquage qui, sinon, démarre OnEnable si l’indicateur AutoActivate a la valeur true.
- **StopHintLoop** Cette fonction appelle l’état de l’animation disparition en fondu si elle n’est pas en cours de lecture, puis désactive la boucle afficher/masquer et définit la montée en mains inactive dans la hiérarchie.
- **AnimationState** Cette chaîne détermine l’état de l’animation qui est joué pendant la boucle. Vous pouvez modifier cette chaîne pour changer l’État joué, mais vous devez le faire après avoir appelé StopHintLoop, et vous devez appeler à nouveau StartHintLoop une fois que vous avez modifié l’État.
- **CustomShouldHideVisuals** Vous pouvez définir cette propriété avec votre propre fonction, qui doit retourner la valeur true lorsque vous souhaitez masquer les visuels de la main (Gardez à l’esprit le MinMaxTimer, en particulier le paramètre Max).

#### <a name="custom-animation-considerations"></a>Considérations sur les animations personnalisées

Les fondus sont par défaut de 0,5 secondes, donc les animations personnalisées créées pour une utilisation avec la plate-forme doivent être de 1,5 secondes au minimum pour que toutes les informations significatives soient transmises.

Les États par défaut de disparition en fondu et en fondu, Fade_In et Fade_Out peuvent être ajustés en modifiant l’horodateur de la deuxième image clé pour définir la longueur de fondu.

L’animateur et le script ont été configurés d’une manière qui devrait rendre l’installation aussi simple que possible. Pour ajouter de nouveaux États d’animation, importez simplement vos FBX, vérifiez que le nom de l’animation est défini avec un nom distinct, puis faites glisser cette animation dans l’animateur.

### <a name="movetotarget"></a>MoveToTarget

Le script MoveToTarget. cs fournit les fonctionnalités permettant de déplacer l’indicateur main d’une position de suivi à une position cible dans le temps.

#### <a name="how-to-set-up-movetotarget"></a>Configuration de MoveToTarget

Les prefabs « MovingHandCoachRoot_L. Prefab » et « MovingHandCoachRoot_R. Prefab » fournis contiennent un MoveToTarget dans leurs hiérarchies. Si vous souhaitez utiliser ce script dans votre propre installation, vous devez le placer sur le gameobject racine contenant l’animateur de votre plate-forme de test.

#### <a name="inspector-properties"></a>Propriétés de l’inspecteur

- **TrackingObject** Définissez cette valeur avec l’objet que vous souhaitez que la plate-forme suive avant de commencer son mouvement. Il est recommandé de créer un GameObject vide et de le déplacer vers une position spécifique pour vous aider à identifier le suivi.
- **TargetObject** Définissez cette valeur avec l’objet vers lequel vous souhaitez déplacer la plate-forme lors de son mouvement. Il est recommandé de créer un GameObject vide et de le déplacer vers une position spécifique pour vous aider à identifier le suivi.
- **RootObject** Définissez cette valeur sur un parent partagé entre le suivi et l’objet cible afin que les positions relatives puissent être calculées correctement. Le Prefab inclus a à la fois des objets de suivi et cibles dans sa hiérarchie, mais vous pouvez définir l’objet cible comme un gameObject en dehors du Prefab et changer l’objet racine en un parent partagé.
- **Durée** Temps nécessaire (en secondes) pour passer de TrackingObject à TargetObject en secondes.
- **TargetOffset** Décalage réglable pour obtenir le GameObject à la position cible appropriée. Cela est utile si votre animation comprend un décalage de position pendant l’animation.
- **AnimationCurve** Par défaut, il s’agit d’une courbe linéaire, mais vous pouvez modifier la courbe pour fournir une accélération en cas de démarrage et d’arrêt de la trajectoire.

#### <a name="controlling-movetotarget-via-script"></a>Contrôle des MoveToTarget à l’aide d’un script

Dans votre script personnalisé, effectuez un appel pour suivre () pendant que vous souhaitez que la plateforme de test suive le TrackingObject, puis effectuez un appel à MoveToTargetPosition () lorsque vous souhaitez que la plate-forme commence son mouvement sur le TargetObject.

#### <a name="controlling-movetotarget-via-animations"></a>Contrôle des MoveToTarget via des animations

Dans l’animation qui doit être déplacée, définissez deux événements : l’un avec un appel à follow () et l’autre avec un appel à MoveToTargetPosition (). La fonction doit être définie sur la première image clé, car elle fait en sorte que la plateforme de test suive votre TrackingObject. MoveToTargetPosition doit être défini sur l’image clé où vous souhaitez que la plate-forme commence à se déplacer vers la cible. Voici comment la fonctionnalité de script est utilisée dans le prefabs fourni.

### <a name="rotatearoundpoint"></a>RotateAroundPoint

Le script RotateAroundPoint. cs fournit les fonctionnalités permettant de faire pivoter l’indicateur main autour d’un point pivot dans le temps.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Configuration de RotateAroundPoint

Les prefabs « RotatingHandCoachRoot_L. Prefab » et « RotatingHandCoachRoot_R. Prefab » fournis contiennent un RotateAroundPoint dans leurs hiérarchies. Si vous souhaitez utiliser ce script dans votre propre installation, vous devez le placer sur le gameobject racine contenant l’animateur de votre plate-forme de test.

#### <a name="inspector-properties"></a>Propriétés de l’inspecteur

- **CenteredParent** Définissez cette valeur avec l’objet parent que vous souhaitez faire pivoter avec la plate-forme de test.
- **InverseParent** Définissez cette valeur avec le parent pour faire pivoter l’inverse vers centeredParent afin de conserver la même orientation de main. En général, il s’agit de l’objet parent avec le script InteractionHint.
- **PivotPosition** Définissez cette valeur à un point où vous souhaitez que l’indicateur commence à se déplacer.
- **Durée** Durée (en secondes) nécessaire à la rotation autour du CenteredParent.
- **AnimationCurve** Par défaut, il s’agit d’une courbe linéaire, mais vous pouvez modifier la courbe pour fournir une accélération en cas de démarrage et d’arrêt de la trajectoire.
- **RotationVector** Nombre de degrés à faire pivoter le long de chaque axe.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Contrôle des RotateAroundPoint à l’aide d’un script

Dans votre script personnalisé, effectuez un appel à RotateToTarget () lorsque vous souhaitez que la plate-forme commence sa rotation autour du CenteredParent. Lorsque vous souhaitez que la position soit rétablie à l’PivotPosition d’origine, effectuez un appel à ResetAndDeterminePivot ().

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Contrôle des RotateAroundPoint via des animations

Dans l’animation qui doit être déplacée, définissez deux événements : l’un avec un appel à ResetAndDeterminePivot () et l’autre avec un appel à RotateToTarget (). ResetAndDeterminePivot doit être défini sur la première image clé, car elle entraîne la réinitialisation de la plate-forme à PivotPosition. RotateToTarget doit être défini sur l’image clé où vous souhaitez que la plate-forme commence à pivoter autour du CenteredParent. Voici comment la fonctionnalité de script est utilisée dans le prefabs fourni.
