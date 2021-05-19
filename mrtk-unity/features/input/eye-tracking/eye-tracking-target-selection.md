---
title: Sélection de la cible de suivi oculaire
description: Comment accéder aux données de regard visuel et aux événements spécifiques du regard pour sélectionner des cibles dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144192"
---
# <a name="eye-supported-target-selection"></a>Sélection de la cible prise en charge par l’œil

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

Cette page présente les différentes options permettant d’accéder aux données de regard oculaire et aux événements spécifiques du regard pour sélectionner des cibles dans MRTK. Le suivi oculaire permet des sélections de cibles rapides et sans effort à l’aide d’une combinaison d’informations sur ce qu’un utilisateur examine avec d’autres entrées, telles que le suivi de la _main_ et les _commandes vocales_:

- Regardez & dites _« Sélectionner »_ (commande vocale par défaut)
- Regardez & dites _« Eclater »_ ou _« pop »_ (commandes vocales personnalisées)
- Bouton regarder & Bluetooth
- Regardez & pincez-vous (par exemple, maintenez votre main à l’avant et apportez votre doigt et votre index ensemble)
  - Notez que pour que cela fonctionne, les [rayons manuels doivent être désactivés](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)

Pour sélectionner un contenu holographique à l’aide d’un point de vue oculaire, vous avez le choix entre plusieurs options :

[**1. Utilisez le pointeur de focus principal :**](#1-use-generic-focus-and-pointer-handlers)

Cela peut être assimilé à votre curseur par ordre de priorité.
Par défaut, si les mains sont en vue, il s’agit de rayons de main.
Si aucun mains n’est en cours d’affichage, le pointeur de priorité est en tête ou en regard.
Par conséquent, veuillez noter que, en fonction de l’en-tête de conception actuel ou de l’œil, le point de regard est supprimé en tant qu’entrée de curseur si des rayons de main sont utilisés.

Par exemple :

Un utilisateur souhaite sélectionner un bouton holographique distant.
En tant que développeur, vous souhaitez fournir une solution flexible qui permet à l’utilisateur d’accomplir ces tâches dans diverses conditions :

- Parcourez le bouton et surmontez-le
- Examinez-la à partir d’une distance et dites « sélectionner »
- Ciblez le bouton à l’aide d’un rayon et effectuez un pincement. dans ce cas, la solution la plus souple consiste à utiliser le gestionnaire de focus principal, car il vous avertit chaque fois que le pointeur principal actuellement prioritaire déclenche un événement. Notez que si les rayons de main sont activés, le pointeur du point de vue de la tête ou de l’œil est désactivé dès l’apparition des mains.

> [!IMPORTANT]
> Notez que si les rayons de main sont activés, le pointeur du point de vue de la tête ou de l’œil est désactivé dès l’apparition des mains. Si vous souhaitez prendre en charge une [interaction _« look et pince »_ , vous devez désactiver le rayon de la main](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray). Dans nos exemples de suivi oculaire, nous avons désactivé le rayon de la main pour permettre la présentation des interactions plus riches à l’aide des yeux et des mouvements [manuels. pour plus d’exemples,](eye-tracking-eyes-and-hands.md)consultez la rubrique.

[**2. Utilisez à la fois le focus visuel et les rayons main :**](#2-independent-eye-gaze-specific-eyetrackingtarget)

Il peut y avoir des cas où vous souhaitez être plus précis que le type de pointeurs de Focus peut déclencher certains événements et permettre l’utilisation simultanée de plusieurs techniques d’interaction Far.

Par exemple : dans votre application, un utilisateur peut utiliser des rayons de loin pour manipuler des configurations mécaniques holographiques, par exemple, saisir et maintenir des éléments de moteur holographique distants et les maintenir en place. Dans ce cas, l’utilisateur doit suivre un certain nombre d’instructions et enregistrer sa progression en marquant certaines cases à cocher. Si l’utilisateur a ses mains _non occupées_, il serait instinctual de simplement toucher à la case à cocher ou de la sélectionner à l’aide d’un rayon de la main. Toutefois, si l’utilisateur a ses mains occupées, comme dans le cas où des parties de moteur holographique sont en place, vous souhaitez permettre à l’utilisateur de faire défiler en toute transparence les instructions à l’aide de leur point de regard, et de simplement regarder une case à cocher et de « vérifier ».

Pour ce faire, vous devez utiliser un script EyeTrackingTarget spécifique à l’oeil qui est indépendant du MRTK principal FocusHandlers et qui sera abordé plus loin ci-dessous.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. utiliser le focus générique et les gestionnaires de pointeurs

Si le suivi des yeux est correctement configuré (voir [le programme d’installation de base MRTK pour utiliser le suivi oculaire](eye-tracking-basic-setup.md)), permettre aux utilisateurs de sélectionner des hologrammes à l’aide de leurs yeux est le même que pour toute autre entrée de focus (par exemple, point de regard ou rayon de la tête). Vous bénéficiez ainsi d’un moyen flexible d’interagir avec vos hologrammes en définissant le type de focus principal dans votre profil de pointeur d’entrée MRTK en fonction des besoins de votre utilisateur, tout en laissant votre code intact. Cela permet de basculer entre le point de regard d’une tête ou d’un œil sans modifier une ligne de code ou de remplacer les rayons de main avec le ciblage oculaire pour les interactions lointaines.

### <a name="focusing-on-a-hologram"></a>Se concentrer sur un hologramme

Pour détecter le moment auquel un hologramme est concentré, utilisez l’interface _« IMixedRealityFocusHandler »_ qui vous fournit deux membres de l’interface : _OnFocusEnter_ et _OnFocusExit_.

Voici un exemple simple de [ColorTap. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) permettant de modifier la couleur d’un hologramme lors de la consultation.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a>Sélection d’un hologramme concentré

Pour sélectionner un hologramme concentré, utilisez _PointerHandler_ pour écouter les événements d’entrée et confirmer une sélection.
Par exemple, l’ajout de _IMixedRealityPointerHandler_ fait réagir à une entrée de pointeur simple.
L’interface _IMixedRealityPointerHandler_ nécessite l’implémentation des trois membres d’interface suivants : _OnPointerUp_, _OnPointerDown_ et _OnPointerClicked_.

Dans l’exemple ci-dessous, nous modifions la couleur d’un hologramme en regardant et en pinceant ou en disant « sélectionner ».
L’action requise pour déclencher l’événement est définie par le fait `eventData.MixedRealityInputAction == selectAction` que nous pouvons définir le type de `selectAction` dans l’éditeur Unity : par défaut, il s’agit de l’action « sélectionner ». Les types de [MixedRealityInputActions](../input-actions.md) disponibles peuvent être configurés dans le profil MRTK via des   ->    ->  _actions d'_ entrée de profil de configuration de MRTK.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a>Yeux-BaseEyeFocusHandler spécifiques

Étant donné que le point de vue de l’œil peut être très différent des autres entrées de pointeur, vous souhaiterez peut-être vous assurer de réagir uniquement à l’entrée de focus s’il s’agit d’un point de vue _oculaire_ et qu’il s’agit actuellement du pointeur d’entrée principal.
À cet effet, vous utiliseriez le [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) qui est spécifique au suivi oculaire et qui dérive de [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .
Comme mentionné précédemment, il se déclenchera uniquement si la cible du point de regard de l’œil est actuellement l’entrée du pointeur principal (c’est-à-dire qu’aucun rayon de la main n’est actif). Pour plus d’informations, consultez Guide pratique [pour prendre en charge les gestes oculaires + main](eye-tracking-eyes-and-hands.md).

Voici un exemple de `EyeTrackingDemo-03-Navigation` (ressources/MRTK/examples/démonstrations/EyeTracking/scènes).
Dans cette démonstration, il y a deux hologrammes 3D qui s’affichent en fonction de la partie de l’objet qui est recherchée : si l’utilisateur regarde à gauche de l’hologramme, cette partie se déplacera lentement vers l’avant de l’utilisateur.
Si le côté droit est examiné, cette partie se déplace lentement vers l’avant.
Il s’agit d’un comportement que vous ne souhaitez peut-être pas activer à tout moment et que vous ne souhaitez peut-être pas déclencher accidentellement par un rayon de main ou un point de vue de tête.
[`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze)Une fois attaché, un gameobject pivote en cours de recherche.

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

Consultez la documentation de l’API pour obtenir une liste complète des événements disponibles du [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :

- **OnEyeFocusStart :** Déclenché une fois que le point de regard oculaire *commence* à se croiser avec le conflit de cette cible.
- **OnEyeFocusStay :** Déclenché *lorsque* le point de regard de l’oeil est en intersection avec le conflit de cette cible.
- **OnEyeFocusStop :** Déclenché une fois que le point de regard oculaire *arrête* l’intersection avec le conflit de cette cible.
- **OnEyeFocusDwell :** Déclenché une fois que le point de regard de l’œil a croisé avec le conflit de cette cible pendant un laps de temps spécifié.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. œil indépendant-EyeTrackingTarget spécifique au point de regard

Enfin, nous vous proposons une solution qui vous permet de traiter les entrées basées sur les yeux entièrement indépendantes des autres pointeurs de focalisation via le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.

Cela présente trois _avantages_:

- Vous pouvez vous assurer que l’hologramme réagit uniquement au regard de l’utilisateur.
- Cela est indépendant de l’entrée principale actuellement active. Par conséquent, vous pouvez traiter plusieurs entrées en même temps, par exemple, en combinant rapidement le ciblage oculaire avec les gestes manuels.
- Plusieurs événements Unity ont déjà été configurés pour accélérer et faciliter la gestion et la réutilisation des comportements existants à partir de l’éditeur Unity ou à l’aide de code.

Il existe également quelques _inconvénients :_

- Plus d’effort pour gérer individuellement les entrées distinctes.
- Aucune dégradation élégante : elle ne prend en charge que le ciblage oculaire. Si le suivi oculaire ne fonctionne pas, vous avez besoin de secours supplémentaire.

À l’instar de _BaseFocusHandler_, le _EyeTrackingTarget_ est prêt avec plusieurs événements Unity spécifiques aux regards, que vous pouvez écouter facilement à l’aide de l’éditeur Unity (Voir l’exemple ci-dessous) ou en utilisant _AddListener ()_ dans le code :

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- OnDwell()
- OnSelected()

Dans ce qui suit, nous vous guidons à travers quelques exemples d’utilisation de _EyeTrackingTarget_.

### <a name="example-1-eye-supported-smart-notifications"></a>Exemple #1 : notifications intelligentes prises en charge par l’œil

Dans `EyeTrackingDemo-02-TargetSelection` (ressources/MRTK/examples/démonstrations/EyeTracking/Scenes), vous pouvez trouver un exemple pour les _« notifications Smart précis »_ qui réagissent à votre regard.
Il s’agit de zones de texte en 3D qui peuvent être placées dans la scène et qui s’agrandissent et s’allument vers l’utilisateur pour faciliter la lisibilité. Pendant que l’utilisateur lit la notification, les informations s’affichent de façon claire et claire. Après l’avoir lu et extrait de la notification, la notification est automatiquement ignorée et disparaît en fondu. Pour ce faire, il existe quelques scripts de comportement génériques qui ne sont pas spécifiques au suivi oculaire, par exemple :

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

L’avantage de cette approche est que les mêmes scripts peuvent être réutilisés par différents événements. Par exemple, un hologramme peut commencer à faire face à l’utilisateur en fonction de commandes vocales ou après avoir appuyé sur un bouton virtuel. Pour déclencher ces événements, vous pouvez simplement référencer les méthodes qui doivent être exécutées dans le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script attaché à votre GameObject.

Pour l’exemple des _« notifications Smart précis »_, voici ce qui se produit :

- **OnLookAtStart ()**: la notification commence à...
  - *FaceUser. engagement :* ... tourner vers l’utilisateur.
  - *Change. engagement :* ... augmentation de _la taille (jusqu’à une échelle maximale spécifiée)_.
  - *BlendOut. engagement :* ... commence à fusionner en plus _(après avoir été à un état d’inactivité plus subtil)_.  

- **OnDwell ()**: informe le script _BlendOut_ que la notification a été examinée suffisamment.

- **OnLookAway ()**: la notification commence à...
  - *FaceUser. DEBRAYAGE :* ... rétablir l’orientation d’origine.
  - *Change. Debray :* ... Diminuez sa taille d’origine.
  - *BlendOut. DEBRAYAGE :* ... commence à mélanger-si _OnDwell ()_ a été déclenché, est entièrement fusionné et détruit, sinon revient à son état inactif.

Considérations relatives à la **conception :** La clé d’une expérience agréable consiste à régler avec soin la vitesse de l’un de ces comportements afin d’éviter de provoquer une gêne en réagissant à l’oeil de l’utilisateur trop rapidement tout le temps.
Dans le cas contraire, cela peut rapidement sembler extrêmement écrasant.

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>Exemple #2 : la marque de gemme holographique pivote lentement lorsqu’elle est examinée

Comme pour les exemples de #1, nous pouvons facilement créer des commentaires sur le pointage pour nos gemmes holographiques dans `EyeTrackingDemo-02-TargetSelection` une scène (ressources/MRTK/examples/démonstrations/EyeTracking/scènes) qui se tournera lentement dans une direction constante et à une vitesse constante (par opposition à l’exemple de rotation ci-dessus) lors de la consultation. Tout ce dont vous avez besoin, c’est de déclencher la rotation de la gemme holographique à partir de l’événement _WhileLookingAtTarget ()_ de _EyeTrackingTarget_. Voici quelques informations supplémentaires :

1. Créez un script générique qui comprend une fonction publique pour faire pivoter le GameObject auquel il est attaché. Vous trouverez ci-dessous un exemple de _RotateWithConstSpeedDir. cs_ dans lequel nous pouvons ajuster le sens et la vitesse de rotation à partir de l’éditeur Unity.

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. Ajoutez le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script à votre gameobject cible et référencez la fonction _RotateTarget ()_ dans le déclencheur UnityEvent, comme illustré dans la capture d’écran ci-dessous :

    ![Exemple EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>Exemple de #3 : dépiler ces gemmes alias _sélection multimodale_ de la cible avec pointage en regard

Dans l’exemple précédent, nous avons montré combien il est facile de détecter si une cible est examinée et comment déclencher une réaction. Ensuite, nous allons faire exploser les gemmes à l’aide de l’événement _OnSelected ()_ de [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) . La partie intéressante est la *façon dont* la sélection est déclenchée. [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)Permet d’assigner rapidement différentes façons d’appeler une sélection :

- _Mouvement de pincement_: l’affectation de la valeur « SELECT » à « SELECT » utilise le mouvement de main par défaut pour déclencher la sélection.
Cela signifie que l’utilisateur peut simplement soulever sa main et pincer son doigt et son index ensemble pour confirmer la sélection.

- Dites _« Sélectionner »_: utilisez la commande vocale par défaut _« Select »_ pour sélectionner un hologramme.

- Dites _« Eclater »_ ou _« pop »_: pour utiliser des commandes vocales personnalisées, vous devez suivre deux étapes :
    1. Configurer une action personnalisée comme _« DestroyTarget »_
        - Accéder aux _actions d’entrée de > d’entrée MRTK->_
        - Cliquez sur « Ajouter une nouvelle action ».

    2. Configurer les commandes vocales qui déclenchent cette action, telles que _« Eclater »_ ou _« pop »_
        - Accédez à _MRTK-> entrée-> Speech_
        - Cliquez sur « Ajouter une nouvelle commande vocale ».
            - Associer l’action que vous venez de créer
            - Assigner un _keyCode_ pour permettre le déclenchement de l’action via une pression sur un bouton

![Exemple de commandes vocales EyeTrackingTarget](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

Lorsqu’une gemme est sélectionnée, elle explose, ce qui crée un son et disparaît. Cela est géré par le [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script. Deux options s'offrent à vous :

- **Dans l’éditeur Unity :** Vous pouvez simplement lier le script attaché à chacun de nos modèles GEM à l’événement OnSelected () Unity dans l’éditeur Unity.
- **Dans le code :** Si vous ne souhaitez pas faire glisser et déposer GameObjects, vous pouvez également simplement ajouter un écouteur d’événements directement à votre script.  
Voici un exemple de la façon dont nous l’avons fait dans le [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script :

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>Exemple #4 : utiliser des rayons de main et des entrées de regard oculaire ensemble

Les rayons de main sont prioritaires par rapport au point de contrôle du regard. Cela signifie que si les rayons de main sont activés, le moment où les mains entrent en vue, le rayon de la main agit comme pointeur principal.
Toutefois, il peut arriver que vous souhaitiez utiliser des rayons de main tout en détectant si un utilisateur Regarde un certain hologramme. Facile ! Pour l’essentiel, vous avez besoin de deux étapes :

**1. activer le rayon de la main :** pour activer le rayon de la main, accédez à la boîte à outils de la _réalité mixte-> pointeurs d’entrée->_.
Dans le _EyeTrackingDemo-00-RootScene_ où la boîte à outils de réalité mixte est configurée une seule fois pour toutes les scènes de démonstration du suivi oculaire, vous devez voir le _EyeTrackingDemoPointerProfile_.
Vous pouvez créer un nouveau _profil d’entrée_ à partir de zéro ou adapter le suivi visuel actuel :

- **À partir de zéro :** Dans l’onglet _pointeurs_ , sélectionnez _DefaultMixedRealityInputPointerProfile_ dans le menu contextuel.
Il s’agit du profil de pointeur par défaut pour lequel le rayon de la main est déjà activé.
Pour modifier le curseur par défaut (un point blanc opaque), clonez simplement le profil et créez votre propre profil de pointeur personnalisé.
Ensuite, remplacez _DefaultCursor_ par _EyeGazeCursor_ sous le _curseur en regard Prefab_.  
- **Selon le _EyeTrackingDemoPointerProfile_ existant :** double-cliquez sur _EyeTrackingDemoPointerProfile_ et ajoutez l’entrée suivante sous _Options du pointeur_:
  - **Type de contrôleur :** « Articulée », « Windows Mixed Reality »
  - La **main :** Aux
  - **Pointeur Prefab :** DefaultControllerPointer

**2. détecter qu’un hologramme est examiné :** utilisez le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script pour activer la détection d’un hologramme comme décrit ci-dessus. Vous pouvez également jeter un coup d’œil à l' `FollowEyeGaze` exemple de script, car il montre un hologramme à la suite de votre point de regard (par exemple, un curseur) si les rayons de main sont activés ou non.

À présent, lorsque vous démarrez les scènes de démonstration du suivi oculaire, vous devriez voir un rayon venant de vos mains.
Par exemple, dans la démonstration de sélection de la cible de suivi oculaire, le cercle semi-transparent est toujours à la suite de votre point de vue et les gemmes répondent à la présence ou à la non-utilisation du pointeur d’entrée principal (vos mains).

---
[Retour à « suivi oculaire dans le MixedRealityToolkit »](eye-tracking-main.md)
