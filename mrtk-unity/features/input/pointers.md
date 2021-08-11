---
title: Pointeurs
description: Documentation sur les pointeurs dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, pointeurs,
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190977"
---
# <a name="pointers"></a>Pointeurs

![Pointeur](../images/pointers/MRTK_Pointer_Main.png)

Cet article explique comment configurer et répondre à l’entrée du pointeur dans la pratique, par rapport à l' [architecture du pointeur](../../architecture/controllers-pointers-and-focus.md)

Les pointeurs sont automatiquement instanciés au moment de l’exécution lorsqu’un nouveau contrôleur est détecté. Plusieurs pointeurs peuvent être attachés à un contrôleur. par exemple, avec le profil de pointeur par défaut, les contrôleurs de Windows Mixed Reality obtiennent une ligne et un pointeur parabolique pour la sélection normale et la téléporting, respectivement.

## <a name="pointer-configuration"></a>Configuration du pointeur

Les pointeurs sont configurés dans le cadre du système d’entrée dans MRTK via un [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) . Ce type de profil est affecté à un [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) dans l’inspecteur de configuration MRTK. Le profil de pointeur détermine le curseur, les types de pointeurs disponibles au moment de l’exécution et la manière dont ces pointeurs communiquent les uns avec les autres pour déterminer celui qui est actif.

- *Étendue de pointage* : définit la distance maximale pour laquelle un pointeur peut interagir avec un GameObject.

- *Pointer les masques de couche Raycast* : il s’agit d’un tableau de LayerMasks par ordre de priorité pour déterminer le GameObjects possible avec lequel un pointeur donné peut interagir et l’ordre d’interaction à essayer. Cela peut être utile pour garantir que les pointeurs interagissent d’abord avec les éléments d’interface utilisateur avant d’autres objets de scène.
![Exemple de profil de pointeur](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>Configuration des options du pointeur

La configuration par défaut du profil de pointeur MRTK comprend les classes de pointeurs suivantes et les prefabs associés prêts à l’emploi. La liste des pointeurs disponibles pour le système au moment de l’exécution est définie sous *Options du pointeur* dans le profil du pointeur. Les développeurs peuvent utiliser cette liste pour reconfigurer des pointeurs existants, ajouter de nouveaux pointeurs ou en supprimer un.

![Exemple de profil d’options de pointeur](../images/input/pointers/PointerOptionsProfile.PNG)

Chaque entrée de pointeur est définie par le jeu de données suivant :

- *Type de contrôleur* : ensemble de contrôleurs pour lesquels un pointeur est valide.
  - Par exemple, le *PokePointer* est responsable des objets « percer » avec un doigt et est, par défaut, marqué comme prenant uniquement en charge le type de contrôleur manuel articulé. Les pointeurs sont instanciés uniquement lorsqu’un contrôleur devient disponible et, en particulier, le *type de contrôleur* définit les contrôleurs avec lesquels ce pointeur Prefab peut être créé.

- *Droitier* -autorise l’instanciation d’un pointeur uniquement pour une main spécifique (gauche/droite)

> [!NOTE]
> La définition de *la propriété d'* accès d’une entrée de pointeur sur *None* la désactivera effectivement du système comme alternative à la suppression de ce pointeur de la liste.

- *Pointeur Prefab* : cette ressource Prefab est instanciée lorsqu’un contrôleur correspondant au type et à la saisie de contrôleur spécifiés commence le suivi.

Il est possible d’avoir plusieurs pointeurs associés à un contrôleur. Par exemple, dans `DefaultHoloLens2InputSystemProfile` (ressources/MRTK/Kit de développement logiciel/profils/HoloLens2/), le contrôleur de la main articulée est associé aux *PokePointer*, *GrabPointer* et *DefaultControllerPointer* (c.-à-d. rayons de main).

> [!NOTE]
> MRTK fournit un ensemble de prefabs de pointeur dans *ressources/MRTK/Kit de développement logiciel (SDK)/fonctionnalités/UX/prefabs/pointeurs*. Un nouveau Prefab personnalisé peut être généré tant qu’il contient l’un des scripts de pointeur dans éléments multimédias/ *MRTK/SDK/features/UX/scripts/pointeurs* ou tout autre script implémentant [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) .

### <a name="default-pointer-classes"></a>Classes de pointeurs par défaut

Les classes suivantes sont les pointeurs MRTK out-of-Box disponibles et définis dans le *profil de pointeur MRTK* par défaut décrit ci-dessus. Chaque pointeur Prefab fourni sous *Assets/MRTK/SDK/features/UX/Prefabs/Pointers* contient l’un des composants de pointeur attachés.

![Pointeurs par défaut MRTK](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>Pointeurs Far

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *LinePointer*, une classe de pointeur de base, dessine une ligne à partir de la source de l’entrée (c.-à-d. le contrôleur) dans la direction du pointeur et prend en charge une conversion de rayon unique dans cette direction. En règle générale, les classes enfants telles que [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) et les pointeurs de télétentative sont instanciées et utilisées (qui dessinent également des lignes pour indiquer l’emplacement où les téléportions se termineront) au lieu de cette classe qui fournit principalement des fonctionnalités communes.

pour les contrôleurs de mouvement comme dans Oculus, Vive et Windows Mixed Reality, la rotation correspondra à la rotation du contrôleur. pour les autres contrôleurs comme HoloLens 2 mains articulées, la rotation correspond à la pose de la main fournie par le système.

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* étend la classe *LinePointer* en autorisant les conversions de rayon en plusieurs étapes sur une courbe. Cette classe de pointeur de base est utile pour les instances courbées, telles que les pointeurs de téléportage où la ligne est courbe de manière cohérente dans un Parabola.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

L’implémentation de *ShellHandRayPointer*, qui s’étend de [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) , est utilisée comme valeur par défaut pour le *profil de pointeur MRTK*. Le Prefab *DefaultControllerPointer* implémente la [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) classe.

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

également connu sous le nom de pointeur en forme de point d’interligne *(GGV)* , le GGVPointer HoloLens alimente les interactions d’apparence et de frappe de style 1, principalement par le biais du robinet et du toucher à l’Air ou du regard et de l’interaction de sélection vocale. La position et la direction du pointeur GGV est pilotée par la position et la rotation de l’en-tête.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

Le *TouchPointer* est responsable de l’utilisation des entrées tactiles Unity (par exemple, un écran tactile). Il s’agit de « interactions lointaines », car l’action consistant à toucher l’écran transporte un rayon de l’appareil photo vers un emplacement potentiellement lointain dans la scène.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

Le *MousePointer* alimente un écran raycast dans le monde entier pour les interactions lointaines, mais pour la souris au lieu de toucher.

![Pointeur de souris](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> la prise en charge de la souris n’est pas disponible par défaut dans MRTK, mais peut être activée en ajoutant un nouveau *Fournisseur de données d’entrée* de type [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) au profil d’entrée MRTK et en affectant au [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) fournisseur de données.

#### <a name="near-pointers"></a>Pointeurs Near

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

Le *[PokePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* est utilisé pour interagir avec les objets de jeu qui prennent en charge « near interaction touchable ». qui sont des GameObjects qui ont un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script attaché. Dans le cas de UnityUI, ce pointeur recherche NearInteractionTouchableUnityUIs.  PokePointer utilise un SphereCast pour déterminer l’élément touchable le plus proche et est utilisé pour alimenter des éléments tels que les boutons d’appui.

 Quand vous configurez le GameObject avec le [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) composant, veillez à configurer le paramètre *localForward* pour qu’il pointe vers le début du bouton ou d’un autre objet qui doit être rendu touchable. Assurez-vous également que les *limites* de touchable correspondent aux limites de l’objet touchable.

Propriétés utiles du pointeur de l’en-and :

- *TouchableDistance*: distance maximale à laquelle une surface touchable peut être associée
- *Visuels*: objet de jeu utilisé pour afficher le visuel des info-bulles de doigts (l’anneau sur le doigt, par défaut).
- *Line*: ligne facultative à dessiner de bout en bout vers la surface d’entrée active.
- *Masques de couche* d’aide-main : tableau de LayerMasks par ordre de priorité pour déterminer le GameObjects possible avec lequel le pointeur peut interagir et l’ordre d’interaction à essayer. Notez qu’un GameObject doit également avoir un `NearInteractionTouchable` composant pour interagir avec un pointeur d’aide-main.

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* utilise [UnityEngine. physique. OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) afin d’identifier l’objet le plus proche [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) pour l’interaction, ce qui est utile pour l’entrée « pouvant être saisie » comme le `ManipulationHandler` . À l’instar de la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) paire fonctionnelle, pour pouvoir interagir avec le pointeur de sphère, l’objet de jeu doit contenir un composant qui est le [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

Propriétés de pointeur de sphère utiles :

- *Rayon de moulage par sphères*: rayon de la sphère utilisée pour interroger des objets récupérables.
- *Marge de l’objet proche*: distance au-dessus du rayon de cast de la sphère à interroger pour détecter si un objet est proche du pointeur. Nombre total de détections d’objets proches rayon de la sphère sphère rayon + marge de l’objet proche
- *Angle du secteur proche* de l’objet : angle autour de l’axe avant du pointeur pour interroger les objets les plus proches. Fait de la `IsNearObject` fonction de requête comme un cône. Cette valeur est définie sur 66 degrés par défaut pour correspondre au comportement de Hololens 2

![Pointeur de sphère modifié pour rechercher uniquement les objets dans la direction vers l’avant](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *Facteur de lissage proche* de l’objet : facteur de lissage pour la détection near Object. Si un objet est détecté dans le rayon de l’objet proche, le rayon interrogé est alors proche de rayon d’objet * (1 + facteur proche du lissage d’objet) pour réduire la sensibilité et compliquer la création d’un objet pour la sortie de la plage de détection.
- Les *masques de couche de manipulation* : tableau de LayerMasks par ordre de priorité pour déterminer le GameObjects possible avec lequel le pointeur peut interagir et l’ordre d’interaction à essayer. Notez qu’un GameObject doit également avoir un `NearInteractionGrabbable` pour interagir avec un SpherePointer.
    > [!NOTE]
    > La couche de sensibilisation spatiale est désactivée dans le Prefab GrabPointer par défaut fourni par MRTK. Cela permet de réduire l’impact sur les performances d’une requête de chevauchement de sphère avec la maille spatiale. Vous pouvez l’activer en modifiant le Prefab GrabPointer.
- *Ignorer les conflits qui ne se trouvent pas dans* le point de vue, s’il faut ignorer les conflits qui peuvent être proches du pointeur, mais qui ne sont pas réellement dans l’angle visuel.
Cela peut empêcher les saisies accidentelles, et permet aux rayons de main de s’allumer lorsque vous pouvez être à proximité d’une capture, mais ne le voyez pas. L' *angle visuel* est défini à l’aide d’un cône au lieu de l’frustum typique pour des raisons de performances. Ce cône est centré et orienté de la même manière que le frustum de l’appareil photo avec un rayon égal à la moitié de la hauteur d’affichage (ou un angle vertical).

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Pointeurs de téléversion

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) déclenche une demande de réintervention lorsque des actions sont effectuées (par exemple, le bouton de télétentative est enfoncé pour déplacer l’utilisateur.
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) déclenche une demande de réintervention lorsque des actions sont effectuées (par exemple, le bouton de télépression est enfoncé) avec un raycast de ligne parabolique pour déplacer l’utilisateur.

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>Prise en charge des pointeurs pour les plateformes de réalité mixte

Le tableau suivant détaille les types de pointeur généralement utilisés pour les plateformes courantes dans MRTK. Remarque : il est possible d’ajouter différents types de pointeur à ces plateformes. Par exemple, vous pouvez ajouter un pointeur de pointage ou une sphère de la sphère à VR. En outre, les appareils VR avec un boîtier de l’appareil peuvent utiliser le pointeur GGV.

|       Pointeur              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | Valide   | Valide                 |            | Valide      |
| TeleportPointer     | Valide   | Valide                 |            |            |
| GGVPointer          |         |                       | Valide      |            |
| SpherePointer       |         |                       |            | Valide      |
| PokePointer         |         |                       |            | Valide      |

## <a name="pointer-interactions-via-code"></a>Interactions de pointeur par le biais du code

### <a name="pointer-event-interfaces"></a>Interfaces d’événements de pointeur

Les monocomportements qui implémentent une ou plusieurs des interfaces suivantes et sont affectés à un GameObject avec un recevront `Collider` les événements d’interactions de pointeur comme défini par l’interface associée.

| Événement | Description | Handler |
| --- | --- | --- |
| Avant modification du focus/modification du focus | Levée à la fois sur l’objet de jeu perdant le focus et sur celui qui l’obtient chaque fois qu’un pointeur change de focus. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
Focus-entrée/sortie | Déclenché sur l’objet de jeu qui obtient le focus lorsque le premier pointeur l’entre et sur le focus perd le focus lorsque le dernier pointeur le quitte. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
Pointeur vers le haut/glisser-déplacer/vers le haut/clic | En pointant sur le pointeur de rapport, appuyez sur glisser-déplacer. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Toucher démarré/mis à jour/terminé | Déclenché par des pointeurs tactiles comme l' [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) activité de rapport tactile. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) et [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) doivent être gérés dans les objets sur lesquels ils sont déclenchés. Il est possible de recevoir des événements de focus globalement mais, contrairement à d’autres événements d’entrée, le gestionnaire d’événements global ne bloque pas la réception d’événements en fonction du focus (l’événement sera reçu par le gestionnaire global et un objet correspondant dans le focus).

#### <a name="pointer-input-events-in-action"></a>Événements d’entrée de pointeur en action

Les événements d’entrée de pointeur sont reconnus et gérés par le système d’entrée MRTK de la même façon que les [événements d’entrée standard](input-events.md#input-events-in-action). La différence réside dans le fait que les événements d’entrée de pointeur sont gérés uniquement par le GameObject en focus par le pointeur qui a déclenché l’événement d’entrée, ainsi que pour tous les gestionnaires d’entrée globaux. Les événements d’entrée standard sont gérés par GameObjects dans le focus pour tous les pointeurs actifs.

1. Le système d’entrée MRTK reconnaît qu’un événement d’entrée s’est produit
1. Le système d’entrée MRTK déclenche la fonction d’interface appropriée pour l’événement d’entrée à tous les gestionnaires d’entrée globaux inscrits
1. Le système d’entrée détermine quel GameObject est en focus pour le pointeur qui a déclenché l’événement.
    1. Le système d’entrée utilise le [système d’événements Unity](https://docs.unity3d.com/Manual/EventSystem.html) pour déclencher la fonction d’interface appropriée pour tous les composants correspondants sur le gameobject ciblé.
    1. Si, à un moment donné, un événement d’entrée a été [marqué comme étant utilisé](input-events.md#how-to-stop-input-events), le processus se termine et aucun autre GameObjects ne reçoit les rappels.
        - Exemple : les composants qui implémentent l’interface [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) feront l’gameobject d’une recherche de gains ou perdent le focus
        - Remarque : le système d’événements Unity se propage pour rechercher le GameObject parent si aucun composant correspondant à l’interface souhaitée n’est trouvé sur le GameObject actuel..
1. Si aucun gestionnaire d’entrée global n’est inscrit et qu’aucun GameObject n’est trouvé avec un composant/une interface correspondant, le système d’entrée appellera chaque gestionnaire d’entrée de secours inscrit

#### <a name="example"></a>Exemple

Vous trouverez ci-dessous un exemple de script qui modifie la couleur du convertisseur attaché lorsqu’un pointeur prend ou quitte le focus ou lorsqu’un pointeur sélectionne l’objet.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>Pointeurs de requête

Il est possible de rassembler tous les pointeurs actuellement actifs en effectuant une boucle dans les sources d’entrée disponibles (par exemple, contrôleurs et entrées disponibles) pour identifier les pointeurs qui leur sont attachés.

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>Pointeur principal

Les développeurs peuvent s’abonner à l’événement FocusProviders PrimaryPointerChanged pour être avertis lorsque le pointeur principal dans le focus a changé. Cela peut être extrêmement utile pour déterminer si l’utilisateur interagit actuellement avec une scène par le biais d’un point de contact ou d’un rayon de main ou d’une autre source d’entrée.

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

La `PrimaryPointerExample` scène (ressources/MRTK/exemples/démonstrations/entrée/scènes/PrimaryPointer) montre comment utiliser le [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) pour les événements pour répondre à un nouveau pointeur principal.

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>Résultat du pointeur

La propriété du pointeur [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) contient le résultat actuel de la requête de scène utilisée pour déterminer l’objet qui a le focus. Pour un pointeur raycast, comme celui créé par défaut pour les contrôleurs de mouvement, les rayons d’entrée et de main, il contiendra l’emplacement et la normale de l’accès raycast.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

La `PointerResultExample` scène (ressources/MRTK/exemples/démonstrations/entrée/scènes/PointerResult/PointerResultExample. Unity) montre comment utiliser le pointeur [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) pour générer un objet à l’emplacement de l’accès.

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>Désactiver les pointeurs

Pour activer et désactiver les pointeurs (par exemple, pour désactiver le rayon de la main), définissez [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) pour un type de pointeur donné via [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) .

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Pour plus d’exemples, consultez et.

## <a name="pointer-interactions-via-editor"></a>Interactions de pointeur via l’éditeur

Pour les événements de pointeur gérés par [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) , MRTK fournit plus de commodité sous la forme du [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) composant, qui permet aux événements de pointeur d’être gérés directement via des événements Unity.

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>Étendue du pointeur

Les pointeurs Far ont des paramètres qui limitent la raycast et interagissent avec d’autres objets dans la scène.
Par défaut, cette valeur est définie sur 10 mètres. cette valeur a été choisie pour rester cohérente avec le comportement de l’interpréteur de commandes HoloLens.

Cela peut être modifié en mettant à jour les `DefaultControllerPointer` champs du composant de Prefab [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) :

*Étendue du pointeur* : contrôle la distance maximale avec laquelle les pointeurs interagissent.

*Étendue du pointeur par défaut* : définit la longueur du rayon/de la ligne du pointeur qui s’affiche lorsque le pointeur n’interagit pas avec quoi que ce soit.

## <a name="see-also"></a>Voir aussi

- [Architecture du pointeur](../../architecture/controllers-pointers-and-focus.md)
- [Événements d’entrée](input-events.md)
