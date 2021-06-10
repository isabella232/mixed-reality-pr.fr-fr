---
title: Contrôleurs de mouvement dans Unity
description: Apprenez à prendre des mesures sur votre point de regard avec l’entrée de contrôleur de mouvement à l’aide de XR et des API de bouton et d’axe courantes.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: contrôleurs de mouvement, Unity, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: ff1eedcc337edd2d7edfe8d961bb88bcb859cd23
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743482"
---
# <a name="motion-controllers-in-unity"></a>Contrôleurs de mouvement dans Unity

Il existe deux façons principales d’agir sur votre point [de regard](gaze-in-unity.md), les [gestes manuels](../../design/gaze-and-commit.md#composite-gestures) et les [contrôleurs de mouvement](../../design/motion-controllers.md) dans HoloLens et les HMD immersifs. Vous accédez aux données des deux sources d’entrée spatiale via les mêmes API dans Unity.

Unity fournit deux méthodes principales pour accéder aux données d’entrée spatiale pour Windows Mixed Reality. Les API *d’entrée. GetButton/Input. GetAxis* courantes fonctionnent sur plusieurs kits de développement logiciel (SDK) XR, tandis que l’API *InteractionManager/GestureRecognizer* propre à Windows Mixed Reality expose l’ensemble complet des données d’entrée spatiale.

## <a name="unity-xr-input-apis"></a>API d’entrée Unity XR

Pour les nouveaux projets, nous vous recommandons d’utiliser les nouvelles API d’entrée XR dès le début. 

Vous trouverez plus d’informations sur les [API XR ici](https://docs.unity3d.com/Manual/xr_input.html).

## <a name="unity-buttonaxis-mapping-table"></a>Bouton Unity/table de mappage des axes

Le gestionnaire d’entrée Unity pour les contrôleurs de mouvement Windows Mixed Reality prend en charge les ID de bouton et d’axe listés ci-dessous via les API *Input. GetButton/GetAxis* . La colonne « propre à Windows MR » fait référence aux propriétés disponibles à partir du type *InteractionSourceState* . Chacune de ces API est décrite en détail dans les sections ci-dessous.

Les mappages de bouton/ID d’axe pour Windows Mixed Reality correspondent généralement aux ID d’axe/bouton Oculus.

Les mappages de bouton/ID d’axe pour Windows Mixed Reality diffèrent des mappages de OpenVR de deux façons :
1. Le mappage utilise des ID de pavé tactile distincts du stick analogique, pour prendre en charge des contrôleurs avec Thumbsticks et des pavés tactiles.
2. Le mappage évite de surcharger les ID de bouton A et X pour les boutons de menu afin de les rendre disponibles pour les boutons ABXY physiques.

<table>
<tr>
<th rowspan="2">Entrée </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API Unity courantes</a><br />(Input. GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API d’entrée spécifique à Windows MR</a><br />XR. WSA. Entrée</th>
</tr><tr>
<th> Main gauche </th><th> À droite</th>
</tr><tr>
<td> Sélectionner le déclencheur enfoncé </td><td> Axe 9 = 1,0 </td><td> Axe 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Sélectionner la valeur analogique du déclencheur </td><td> Axe 9 </td><td> Axe 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Sélectionner le déclencheur partiellement enfoncé </td><td> Bouton 14 <i>(compatibilité du boîtier de</i> l’option) </td><td> Bouton 15 <i>(compatibilité du boîtier de</i> l’option) </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Bouton de menu enfoncé </td><td> Bouton 6 * </td><td> Bouton 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Bouton de préhension enfoncé </td><td> Axe 11 = 1,0 (aucune valeur analogique)<br />Bouton 4 <i>(compatibilité du boîtier de</i> l’option) </td><td> Axe 12 = 1,0 (aucune valeur analogique)<br />Bouton 5 <i>(compatibilité du boîtier de</i> l’option) </td><td> saisi</td>
</tr><tr>
<td> Stick analogique X <i>(gauche :-1,0, droite : 1,0)</i> </td><td> Axe 1 </td><td> Axe 4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> Joystick Y <i>(haut :-1,0, bas : 1,0)</i> </td><td> Axe 2 </td><td> Axe 5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> Stick analogique appuyé </td><td> Bouton 8 </td><td> Bouton 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Pavé tactile X <i>(à gauche :-1,0, droite : 1,0)</i> </td><td> Axe 17 * </td><td> Axe 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> Pavé tactile Y <i>(haut :-1,0, bas : 1,0)</i> </td><td> Axe 18 * </td><td> Axe 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> Pavé tactile touché </td><td> Bouton 18 * </td><td> Bouton 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Pavé tactile enfoncé </td><td> Bouton 16 * </td><td> Bouton 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> pose de la poignée ou du pointeur 6DoF </td><td colspan="2"> <i>Poignée</i> de pose uniquement : <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></td><td> <i>Poignée</i> ou <i>pointeur</i> en tant qu’argument : SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> État du suivi </td><td colspan="2"> <i>Précision de la position et risque de perte de source uniquement disponible via une API spécifique à MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. Properties. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Ces ID de bouton/axe diffèrent des ID utilisés par Unity pour les OpenVR en raison de collisions dans les mappages utilisés par les boîtiers de soucodeurs, Oculus touch et OpenVR.

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a>Poignée de pose et pose de pointage

Windows Mixed Reality prend en charge les contrôleurs de mouvement dans un large éventail de facteurs de forme. La conception de chaque contrôleur diffère dans sa relation entre la position de l’utilisateur et la direction « avant » naturelle que les applications doivent utiliser pour pointer lors du rendu du contrôleur.

Pour mieux représenter ces contrôleurs, il existe deux genres de poses que vous pouvez examiner pour chaque source d’interaction, le pose de la **poignée** et le **pointeur se posent**. Les coordonnées de pose de la poignée et du pointeur sont exprimées par toutes les API Unity dans les coordonnées universelles Unity universel.

### <a name="grip-pose"></a>Poignée de pose

La **poignée** représente l’emplacement de la paume des utilisateurs, qu’elle soit détectée par une carte HoloLens ou qu’elle détient un contrôleur de mouvement.

Sur les casques immersifs, le pose de la poignée est utilisé pour restituer **la main de l’utilisateur** ou **un objet détenu par l’utilisateur**. La poignée est également utilisée lors de la visualisation d’un contrôleur de mouvement. Le **modèle de rendu** fourni par Windows pour un contrôleur de mouvement utilise la poignée comme son origine et le centre de la rotation.

La poignée est définie spécifiquement comme suit :
* Position de la **poignée**: le centre de la poche quand il maintient le contrôleur naturellement, ajusté à gauche ou à droite pour centrer la position au sein de la poignée. Sur le contrôleur de mouvement Windows Mixed Reality, cette position s’aligne généralement avec le bouton de saisie.
* **Axe droit de l’orientation de la poignée**: lorsque vous ouvrez complètement votre main pour former une pose plate à 5 doigts, le rayon normal à votre paume (en avant à partir de la poche de gauche, en arrière depuis la paume de droite)
* **Axe avant de l’orientation de la poignée**: quand vous fermez partiellement votre main (comme si vous détenir le contrôleur), le rayon qui pointe vers l’avant dans le tube formé par vos doigts non thumbs.
* **Axe vers le haut de l’orientation**: l’axe vers le haut, impliqué dans les définitions Right et Forward.

Vous pouvez accéder à la poignée à l’aide de l’API d’entrée entre fournisseurs de l’unité Unity (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/rotation*) ou via l’API propre à Windows Mr (*SourceState. SourcePose. TryGetPosition/rotation*, en demandant des données de pose pour le nœud de **poignée** ).

### <a name="pointer-pose"></a>Pose du pointeur

Le **pointeur de pose** représente l’extrémité du contrôleur pointant vers l’avant.

Le pointeur fourni par le système est le mieux utilisé pour raycast lorsque vous effectuez **le rendu du modèle de contrôleur lui-même**. Si vous effectuez le rendu d’un autre objet virtuel à la place du contrôleur, tel qu’un pistolet virtuel, vous devez faire pointer un rayon qui est le plus naturel pour cet objet virtuel, tel qu’un rayon qui traverse le canon du modèle de pistolet défini par l’application. Étant donné que les utilisateurs peuvent voir l’objet virtuel et non le contrôleur physique, le fait de pointer avec l’objet virtuel sera probablement plus naturel pour ceux qui utilisent votre application.

Actuellement, le pointeur de pose est disponible dans Unity uniquement par le biais de l’API propre à Windows MR, *sourceState. sourcePose. TryGetPosition/rotation*, en passant *InteractionSourceNode. pointeur* comme argument.

## <a name="controller-tracking-state"></a>État du suivi du contrôleur

À l’instar des casques, le contrôleur de mouvement Windows Mixed Reality ne nécessite pas de configuration de capteurs de suivi externe. Au lieu de cela, les contrôleurs sont suivis par des capteurs dans le casque lui-même.

Si l’utilisateur déplace les contrôleurs en dehors du champ de vue du casque, Windows continue à déduire les positions des contrôleurs dans la plupart des cas. Lorsque le contrôleur a perdu le suivi visuel suffisamment longtemps, les positions du contrôleur sont découpées à des positions de précision approximatives.

À ce stade, le système va verrouiller le contrôleur à l’utilisateur, en effectuant le suivi de la position de l’utilisateur lors de son déplacement, tout en exposant l’orientation réelle du contrôleur à l’aide de ses capteurs d’orientation internes. De nombreuses applications qui utilisent des contrôleurs pour pointer et activer des éléments d’interface utilisateur peuvent fonctionner normalement avec une précision approximative sans que l’utilisateur ne remarque.

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>Raisonnement sur le suivi de l’État explicitement

Les applications qui souhaitent traiter différemment les positions en fonction de l’état de suivi peuvent aller plus loin et inspecter les propriétés de l’état du contrôleur, telles que *SourceLossRisk* et *PositionAccuracy*:

<table>
<tr>
<th> État du suivi </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Haute précision</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Élevé </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Haute précision (risque de perte)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Élevé </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Précision approximative</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Approximatif </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Aucune position</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Approximatif </td><td style="background-color: orange"> false</td>
</tr>
</table>

Ces États de suivi du contrôleur de mouvement sont définis comme suit :
* **Précision élevée :** Alors que le contrôleur de mouvement se trouve dans le champ de vision du casque, il fournit généralement des positions à grande précision, en fonction du suivi visuel. Un contrôleur mobile qui laisse momentanément le champ de vue ou est momentanément masqué des capteurs du casque (par exemple, par l’autre côté de l’utilisateur) continue à retourner des poses de grande précision pendant une brève période, en se basant sur le suivi inertiel du contrôleur lui-même.
* **Haute précision (risque de perte) :** Lorsque l’utilisateur déplace le contrôleur de mouvement au-delà du bord du champ de vue du casque, le casque ne pourra bientôt pas suivre la position du contrôleur. L’application sait quand le contrôleur a atteint cette limite d’aide en regardant le **SourceLossRisk** REACH 1,0. À ce stade, l’application peut choisir de suspendre les gestes de contrôleur qui nécessitent un flux constant de poses de haute qualité.
* **Précision approximative :** Lorsque le contrôleur a perdu le suivi visuel suffisamment longtemps, les positions du contrôleur sont découpées à des positions de précision approximatives. À ce stade, le système va verrouiller le contrôleur à l’utilisateur, en effectuant le suivi de la position de l’utilisateur lors de son déplacement, tout en exposant l’orientation réelle du contrôleur à l’aide de ses capteurs d’orientation internes. De nombreuses applications qui utilisent des contrôleurs pour pointer et activer des éléments d’interface utilisateur peuvent fonctionner normalement, tout en ayant une précision approximative, sans que l’utilisateur ne remarque. Les applications avec des exigences d’entrée plus lourdes peuvent choisir de déterminer ce déplacement de la **haute** précision à une précision **approximative** en inspectant la propriété **PositionAccuracy** , par exemple pour accorder à l’utilisateur un hitbox plus généreux sur les cibles hors écran pendant cette période.
* **Aucune position :** Alors que le contrôleur peut fonctionner à des fins de précision approximative pendant une longue période, le système sait parfois que même une position verrouillée par le corps n’est pas significative pour le moment. Par exemple, un contrôleur qui a été activé n’a peut-être jamais été observé visuellement, ou un utilisateur peut mettre un contrôleur qui est ensuite récupéré par quelqu’un d’autre. À ce moment-là, le système ne fournit pas de position à l’application, et *TryGetPosition* retourne la valeur false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API Unity courantes (Input. GetButton/GetAxis)

**Espace de noms :** *UnityEngine*, *UnityEngine. XR*<br>
**Types**: *Input*, *XR. InputTracking*

Unity utilise actuellement ses API *d’entrée. GetButton/Input. GetAxis* pour exposer l’entrée pour [le kit de développement logiciel (SDK) Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [le kit de développement logiciel (SDK) OpenVR et la](https://docs.unity3d.com/Manual/OpenVRControllers.html) réalité mixte Windows, y compris les contrôleurs mains et motion. Si votre application utilise ces API pour l’entrée, elle peut facilement prendre en charge des contrôleurs de mouvement sur plusieurs kits de développement logiciel (SDK) XR, y compris Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Obtention de l’état enfoncé d’un bouton logique

Pour utiliser les API d’entrée Unity générales, vous commencez généralement par associer des boutons et des axes aux noms logiques dans le [Gestionnaire d’entrée Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), en liant un bouton ou des ID d’axe à chaque nom. Vous pouvez ensuite écrire du code qui fait référence à ce nom d’axe/bouton logique.

Par exemple, pour mapper le bouton de déclenchement du contrôleur de mouvement gauche à l’action envoyer, accédez à **modifier > paramètres du projet > entrée** dans Unity, puis développez les propriétés de la section envoyer sous axes. Modifiez le bouton **positif** ou la propriété **ALT positive du bouton** pour lire le bouton de la manette de jeu **14**, comme suit :

![InputManager d’Unity](images/unity-input-manager.png)<br>
*InputManager Unity*

Votre script peut ensuite Rechercher l’action envoyer à l’aide de *Input. GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Vous pouvez ajouter des boutons logiques en modifiant la propriété **taille** sous **axes**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obtention directe d’un état enfoncé d’un bouton physique

Vous pouvez également accéder manuellement aux boutons à l’aide de leur nom complet, en utilisant *Input. GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Obtention d’une main ou d’une pose de contrôleur de mouvement

Vous pouvez accéder à la position et à la rotation du contrôleur, à l’aide de *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> Le code ci-dessus représente la poignée du contrôleur (où l’utilisateur détient le contrôleur), qui est utile pour le rendu d’une arme ou d’un pistolet dans la main de l’utilisateur, ou un modèle du contrôleur lui-même.
> 
> La relation entre cette poignée se pose et le pointeur pose (où l’extrémité du contrôleur pointe) peut varier d’un contrôle à l’autre. À ce stade, l’accès au pointeur du contrôleur est possible uniquement via l’API d’entrée spécifique à MR, décrite dans les sections ci-dessous.

## <a name="windows-specific-apis-xrwsainput"></a>API spécifiques à Windows (XR. WSA. Entrée

> [!CAUTION]
> Si votre projet utilise l’un des XR. Les API WSA, elles sont en passe en faveur du kit de développement logiciel (SDK) XR dans les futures versions Unity. Pour les nouveaux projets, nous vous recommandons d’utiliser le kit de développement logiciel (SDK) XR dès le début. Vous trouverez plus d’informations sur le [système d’entrée XR et les API ici](https://docs.unity3d.com/Manual/xr_input.html).

**Espace de noms :** *UnityEngine. XR. WSA. Input*<br>
**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Pour obtenir des informations plus détaillées sur l’entrée manuelle de Windows Mixed Reality (pour HoloLens) et les contrôleurs de mouvement, vous pouvez choisir d’utiliser les API d’entrée spatiale spécifiques à Windows sous l’espace de noms *UnityEngine. XR. WSA. Input* . Cela vous permet d’accéder à des informations supplémentaires, telles que la précision de la position ou le genre de source, vous permettant de distinguer les mains et les contrôleurs.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Interrogation de l’état des contrôleurs mains et motion

Vous pouvez interroger l’état de ce frame pour chaque source d’interaction (contrôleur de main ou de mouvement) à l’aide de la méthode *GetCurrentReading* .

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Chaque *InteractionSourceState* que vous récupérez représente une source d’interaction à l’instant courant. *InteractionSourceState* expose des informations telles que :
* Quels sont les [types d’enfoncement](../../design/motion-controllers.md) (Select/menu///-pavé/Stick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Autres données spécifiques aux contrôleurs de mouvement, telles que le pavé tactile et/ou les coordonnées XY et l’État touché

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* InteractionSourceKind à savoir si la source est une main ou un contrôleur de mouvement

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Interrogation pour les poses de rendu prédits par progression

* Lors de l’interrogation des données sources d’interaction à partir de mains et de contrôleurs, les poses que vous recevez sont des poses prédites pour le moment où les photons de ce frame atteindront les yeux de l’utilisateur.  Les poses préprédits sont préférables pour le **rendu** du contrôleur ou de l’objet détenu dans chaque frame.  Si vous ciblez une pression ou une mise en route donnée avec le contrôleur, celles-ci seront plus précises si vous utilisez les API d’événements historiques décrites ci-dessous.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Vous pouvez également obtenir la pose de tête préprédite pour ce frame actuel.  Comme avec la source, cela est utile pour le **rendu** d’un curseur, bien que le ciblage d’une presse ou d’une version donnée soit plus précis si vous utilisez les API d’événements historiques décrites ci-dessous.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Gestion des événements de source d’interaction

Pour gérer les événements d’entrée à mesure qu’ils se produisent avec leurs données d’historique exactes, vous pouvez gérer les événements de source d’interaction au lieu d’interroger.

Pour gérer les événements de source d’interaction :
* Inscrivez-vous pour un événement d’entrée *InteractionManager* . Pour chaque type d’événement d’interaction qui vous intéresse, vous devez vous y abonner.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Gérez l’événement. Une fois que vous êtes abonné à un événement d’interaction, vous obtiendrez le rappel le cas échéant. Dans l’exemple *SourcePressed* , c’est une fois que la source a été détectée et avant qu’elle soit libérée ou perdue.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Comment arrêter la gestion d’un événement

Vous devez arrêter la gestion d’un événement lorsque vous n’êtes plus intéressé par l’événement ou si vous détruisez l’objet qui s’est abonné à l’événement. Pour arrêter la gestion de l’événement, vous devez vous désabonner de l’événement.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Liste des événements de source d’interaction

Les événements de la source d’interaction disponibles sont les suivants :
* *InteractionSourceDetected* (la source devient active)
* *InteractionSourceLost* (devient inactif)
* *InteractionSourcePressed* (appuyez sur, appuyez sur le bouton ou sélectionnez « Sélectionner »)
* *InteractionSourceReleased* (fin d’un TAP, d’un bouton relâché ou d’une fin de « SELECT »)
* *InteractionSourceUpdated* (déplace ou change un État)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Les événements pour le ciblage historique posent qui correspondent le plus précisément à une pression ou à une mise en sortie

Les API d’interrogation décrites précédemment fournissent à votre application des poses préprédits.  Bien que ces éléments prédits soient les plus adaptés pour le rendu du contrôleur ou d’un objet de poche virtuel, les nouvelles poses ne sont pas optimales pour le ciblage, pour deux raisons principales :
* Quand l’utilisateur appuie sur un bouton sur un contrôleur, il peut y avoir environ 20 ms de latence sans fil sur Bluetooth avant que le système ne reçoive la presse.
* Ensuite, si vous utilisez une pose préprédite, il y aura une autre 10-20 ms de prédiction de transfert appliquée pour cibler le moment où les photons du frame actuel atteindront les yeux de l’utilisateur.

Cela signifie que l’interrogation vous donne une source de pose ou de tête qui est de 30-40 ms à partir de là où la tête et la mains de l’utilisateur ont été retirées lorsque l’appui ou la mise en place a eu lieu.  Pour l’entrée de la main HoloLens, bien qu’il n’y ait pas de délai de transmission sans fil, il existe un délai de traitement similaire pour détecter la presse.

Pour cibler avec précision en fonction de l’intention initiale de l’utilisateur pour une presse ou un contrôleur, vous devez utiliser la base de l’historique de la source ou de l’en-tête à partir de cet événement d’entrée *InteractionSourcePressed* ou *InteractionSourceReleased* .

Vous pouvez cibler une presse ou une mise en route avec des données de pose historiques à partir de la tête de l’utilisateur ou de son contrôleur :
* L’en-tête pose au moment où un mouvement ou un contrôleur s’est produit, ce qui peut être utilisé pour **cibler** pour déterminer à quoi l’utilisateur a [Gazing](../../design/gaze-and-commit.md) :

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* La source pose au moment où une pression du contrôleur de mouvement s’est produite, qui peut être utilisée pour le **ciblage** afin de déterminer le point de contrôle de l’utilisateur sur le contrôleur.  Il s’agit de l’état du contrôleur qui a rencontré la presse.  Si vous effectuez le rendu du contrôleur lui-même, vous pouvez demander le point de pose plutôt que le pose de la poignée pour faire tourner le ciblage de la cible à partir de ce que l’utilisateur prendra en compte l’astuce naturelle de ce contrôleur rendu :

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Exemple de gestionnaires d’événements

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a>Contrôleurs de mouvement dans MRTK

Vous pouvez accéder au contrôleur de mouvement [et de mouvement](/windows/mixed-reality/mrtk-unity/features/input/controllers) à partir du gestionnaire d’entrée.

## <a name="follow-along-with-tutorials"></a>Avancer avec des tutoriels

Des didacticiels pas à pas, avec des exemples de personnalisation plus détaillés, sont disponibles dans Mixed Reality Academy :

- [Réalité mixte - Entrées - Cours 211 : Mouvement](tutorials/holograms-211.md)
- [Réalité mixte - Entrées - Cours 213 : Contrôleurs de mouvement](../../deprecated/mixed-reality-213.md)

[![Entrée MR 213-contrôleur de mouvement](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Entrée MR 213-contrôleur de mouvement*

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core. À partir de là, vous pouvez passer au module suivant :

> [!div class="nextstepaction"]
> [Suivi du regard et des mains](./hand-eye-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Suivre de la tête et valider](../../design/gaze-and-commit.md)
* [Contrôleurs de mouvement](../../design/motion-controllers.md)