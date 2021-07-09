---
title: Vue d'ensemble des résolveurs
description: Vue d’ensemble des résolveurs dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK, résolveurs
ms.openlocfilehash: bf9bbfe578ace576fca8870f038f145037a6838d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176457"
---
# <a name="solver-overview"></a>Vue d'ensemble des résolveurs

![Résolveur principal](../../images/solver/MRTK_Solver_Main.png)

Les résolveurs sont des composants qui facilitent le calcul de la position d’un objet et l’orientation en fonction d’un algorithme prédéfini. Il est par exemple possible de placer un objet sur la surface actuellement visée par le raycast du pointage du regard de l’utilisateur.

En outre, le système de résolveur définit de manière déterministe un ordre des opérations pour ces calculs de transformation, car il n’existe pas de méthode fiable pour indiquer à Unity l’ordre de mise à jour des composants.

Les résolveurs offrent un éventail de comportements pour attacher des objets à d’autres objets ou systèmes. Un autre exemple est un objet tag-along qui pointe vers l’avant de l’utilisateur (en fonction de l’appareil photo). Un résolveur peut également être attaché à un contrôleur et à un objet pour faire de l’objet tag-along le contrôleur. Tous les résolveurs peuvent être empilés en toute sécurité, par exemple un comportement avec objet tag-along + aimantation de surface + dynamisme.

## <a name="how-to-use-a-solver"></a>Comment utiliser un résolveur

Le système du résolveur se compose de trois catégories de scripts :

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver) : classe abstraite de base de laquelle tous les résolveurs dérivent. Elle fournit le suivi d’état, les paramètres de lissage et l’implémentation, l’intégration du système de résolveur automatique et l’ordre des mises à jour.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) : définit l’objet de référence selon lequel assurer le suivi (par exemple, la transformation de la caméra principale, le rayon émanant de la main, etc.), gère la collecte des composants du résolveur et exécute leur mise à jour dans l’ordre approprié.

La troisième catégorie est le résolveur lui-même. Les résolveurs suivants fournissent les blocs de construction pour le comportement de base :

* [`Orbital`](#orbital) : verrouille sur une position et un offset spécifiés à partir de l’objet référencé.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize) : met à l’échelle pour conserver une taille constante relative à la vue de l’objet référencé.
* [`RadialView`](#radialview) : conserve l’objet dans une vue de type cône converti par l’objet référencé.
* [`Follow`](#follow) : conserve l’objet dans un ensemble de limites définies par l’utilisateur de l’objet référencé.
* [`InBetween`](#inbetween) : conserve un objet entre deux objets suivis.
* [`SurfaceMagnetism`](#surfacemagnetism) : convertit les rayons en surfaces dans le monde et aligne l’objet sur cette surface.
* [`DirectionalIndicator`](#directionalindicator) : détermine la position et l’orientation d’un objet sous la forme d’un indicateur directionnel. À partir du point de référence de la cible suivie SolverHandler, cet indicateur va orienter vers la DirectionalTarget fournie.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum) : applique l’accélération/la vélocité/la friction pour simuler le dynamisme et les souplesse d’un objet déplacé par d’autres résolveurs/composants.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup) : limite l’objet pour suivre les mains dans une région qui ne croise pas le GameObject avec les mains. Utile pour le contenu interactif à la main, comme les menus, etc. Ce solveur est conçu pour fonctionner avec [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) , mais il fonctionne également avec [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController).
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup) : dérive de HandConstraint mais comprend une logique permettant de tester si la paume fait face à l’utilisateur avant l’activation. Ce résolveur fonctionne uniquement avec les contrôleurs [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand), avec d’autres types de contrôleur. ce résolveur se comporte comme sa classe de base.

Pour utiliser le système du résolveur, ajoutez simplement l’un des composants repris ci-dessus à un GameObject. Étant donné que tous les résolveurs requièrent un(e) [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler), il y en a un(e) qui est créé(e) automatiquement par Unity.

> [!NOTE]
> Vous trouverez des exemples d’utilisation du système de résolveurs dans le fichier **SolverExamples.scene**.

## <a name="how-to-change-tracking-reference"></a>Comment modifier la référence de suivi

La propriété *Tracked Target Type* du composant [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) définit le point de référence que tous les résolveurs utiliseront pour calculer leurs algorithmes. Par exemple, un type valeur de [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) avec un composant [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) simple se traduira par un raycast à partir de la tête et dans la direction du pointage du regard de l’utilisateur pour déterminer la surface atteinte. Les valeurs potentielles pour la propriété `TrackedTargetType` sont :

* *Head* : le point de référence est la transformation de la caméra principale
* *ControllerRay* : le point de référence est la transformation [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) sur un contrôleur (c.-à-d. origine du pointeur sur un contrôleur de mouvement ou un contrôleur de main) pointant dans la direction du rayon de la ligne
  * Utilisez la propriété `TrackedHandedness` pour sélectionner la préférence de main (par exemple, gaucher, droitier, ambidextre)
* *HandJoint* : le point de référence est la transformation d’une articulation de la main spécifique
  * Utilisez la propriété `TrackedHandedness` pour sélectionner la préférence de main (par exemple, gaucher, droitier, ambidextre)
  * Utilisez la propriété `TrackedHandJoint` pour déterminer la transformation d’articulation à utiliser
* *CustomOverride* : point de référence depuis le/la `TransformOverride` affecté(e)

> [!NOTE]
> Pour les types *ControllerRay* et *HandJoint*, le gestionnaire de résolveur tentera de fournir d’abord la transformation de contrôleur/main gauche, puis du droit si le premier n’est pas disponible ou à moins que la propriété `TrackedHandedness` spécifie autre chose.

![Objet suivi du résolveur](../../images/solver/TrackedObjectType-Example.gif) 
*Exemple de propriétés variées associées à chaque TrackedTargetType*

> [!IMPORTANT]
> La plupart des résolveurs utilisent le vecteur vers l’avant de la cible de transformation suivie fournie par `SolverHandler`. Lors de l’utilisation d’un type de cible *Articulation de la main* suivi, le vecteur avant de l’articulation de la paume peut pointer avec les doigts et non avec la paume. Cela dépend de la plateforme fournissant les données jointes à la main. Pour la simulation d’entrée et Windows Mixed Reality, c’est le *vecteur vers le haut* qui pointe vers la paume (c.-à-d. le vecteur vert est vers le haut, le vecteur bleu est vers l’avant).
>
> ![Transférer le vecteur vers le haut](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> Pour remédier à cela, mettez à jour la propriété *Rotation supplémentaire* sur le/la `SolverHandler` pour **<90, 0,0>** . Cela permet de s’assurer que le vecteur direct fourni aux résolveurs pointe via la paume et vers l’extérieur de la main.
>
> ![Rotation supplémentaire](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> Vous pouvez également utiliser le type de cible *Ray Controller* suivi pour obtenir un comportement similaire pour le pointage avec les mains.

## <a name="how-to-chain-solvers"></a>Comment joindre des résolveurs

Il est possible d’ajouter plusieurs composants `Solver` au même GameObject, et ainsi de joindre leurs algorithmes. Les composants `SolverHandler` gèrent la mise à jour de tous les résolveurs sur le même GameObject. Par défaut, les `SolverHandler` appels `GetComponents<Solver>()` à Start retournent les résolveurs dans l’ordre dans lequel ils apparaissent dans l’inspecteur.

En outre, l’affectation de la valeur true à la propriété *Updated Linked Transform* indique ce/cette `Solver` pour enregistrer sa position calculée, son orientation et son échelle calculées vers une variable intermédiaire accessible par tous les résolveurs (c.-à-d. `GoalPosition`). Quand la valeur est false, le/la `Solver` met directement à jour la transformation de GameObject. En enregistrant les propriétés de transformation dans un emplacement intermédiaire, les autres résolveurs sont en mesure d’effectuer leurs calculs à partir de la variable intermédiaire. En effet, Unity ne permet pas aux mises à jour de gameObject.transform de s’empiler dans le même cadre.

> [!NOTE]
> Les développeurs peuvent modifier l’ordre d’exécution des résolveurs en définissant la propriété `SolverHandler.Solvers` directement.

## <a name="how-to-create-a-new-solver"></a>Création d'un résolveur

Tous les résolveurs doivent hériter de la classe de base abstraite, [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver) . Les exigences principales d’une extension du résolveur impliquent la substitution de la méthode `SolverUpdate`. Dans cette méthode, les développeurs doivent mettre à jour les propriétés héritées `GoalPosition`, `GoalRotation` et `GoalScale` avec les valeurs souhaitées. En outre, il est généralement utile de tirer parti de `SolverHandler.TransformTarget` comme cadre de référence souhaité par le consommateur.

Le code fourni ci-dessous donne un exemple d’un nouveau composant de résolveur appelé `InFront` qui place l’objet attaché à deux mètres devant le/la `SolverHandler.TransformTarget` . Si le/la `SolverHandler.TrackedTargetType` est défini(e) par le consommateur en tant que [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), le/la `SolverHandler.TransformTarget` sera la transformation de la caméra et, par conséquent, ce résolveur placera le GameObject en pièce jointe à deux mètres en face du point de regard de chaque cadre des utilisateurs.

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>Guides d’implémentation du résolveur

### <a name="common-solver-properties"></a>Propriétés courantes du résolveur

Chaque composant du résolveur possède un ensemble de propriétés identiques qui contrôlent le comportement du résolveur principal.

Si le *lissage* est activé, le résolveur met progressivement à jour la transformation du GameObject au fil du temps sur les valeurs calculées. La vitesse de cette modification est déterminée par la propriété *LerpTime* de chaque composant de transformation. Par exemple, une valeur *MoveLerpTime* supérieure entraîne des incréments plus lents entre les cadres.

Si *MaintainScale* est activé, le résolveur utilisera l’échelle locale par défaut de GameObject.

![Propriétés du résolveur principal](../../images/solver/GeneralSolverProperties.png)  
*Propriétés communes héritées par tous les composants du résolveur*

### <a name="orbital"></a>Orbital

La classe [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) est un composant tag-along qui se comporte comme des planètes dans un système solaire. Ce solveur garantit que le GameObject joint orbite autour de la transformation suivie. Ainsi, si le *Tracked Target Type* du/de la [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) est défini sur [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), le GameObject orbite autour de la tête de l’utilisateur avec un décalage fixe appliqué.

Les développeurs peuvent modifier ce décalage fixe pour conserver des menus ou d’autres composants de scène au niveau de l’œil ou au niveau de la taille, etc. autour d’un utilisateur. Cela est effectué par la modification des propriétés *Local Offset* et *World Offset* . La propriété *Orientation Type* détermine la rotation appliquée à l’objet s’il doit conserver sa rotation d’origine, ou s’il doit toujours faire face à la caméra ou à la transformation qui dirige sa position, etc.

![Exemple orbital](../../images/solver/OrbitalExample.png)  
*Exemple orbital*

### <a name="radialview"></a>RadialView

Le/la [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) est un autre composant tag-along qui conserve une portion spécifique d’un GameObject dans le tronc de cône de la vue de l’utilisateur.

Les propriétés *Min & Max View Degrees* déterminent la taille qu’une partie du GameObject doit toujours avoir dans la vue.

Les propriétés *Min &amp; Max distance* déterminent la durée pendant laquelle le GameObject doit être conservé par l’utilisateur. Par exemple, si vous parcourez le GameObject avec une *Distance minimale* d’un mètre, vous éloignez le GameObject pour vous assurer qu’il n’est jamais plus proche qu’un mètre par rapport à l’utilisateur.

En règle générale, le/la [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) est utilisé(e) conjointement avec la propriété *Tracked Target Type* définie sur [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) afin que le composant suive le pointage du regard de l’utilisateur. Toutefois, ce composant peut fonctionner pour être conservé dans la *« vue »* de n’importe quel *Tracked Target Type*.

![Exemple RadialView](../../images/solver/RadialViewExample.png)  
*Exemple RadialView*

### <a name="follow"></a>Suivi

La classe [`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) positionne un élément devant la cible suivie par rapport à son axe de transfert local. L’élément peut être faiblement contraint (également appelé tag-along) afin qu’il ne soit pas suivi jusqu’à ce que la cible suivie passe au-delà des limites définies par l’utilisateur.

Il fonctionne de la même façon que le résolveur RadialView, avec des contrôles supplémentaires pour gérer le *nombre maximal de niveaux d’affichage verticaux et horizontaux* et des mécanismes permettant de modifier l'*orientation* de l’objet.

![Suivre les propriétés](../../images/solver/FollowExample.png)  
*Suivre les propriétés*

![Suivre l’exemple de scène](../../images/solver/FollowExampleScene.gif)  
*Suivre l’exemple de scène (Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>InBetween

La classe [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) conserve le gameobject joint entre deux transformations. Ces deux points de terminaison de transformation sont définis par le [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) *Tracked Target Type* propre au GameObject et le composant [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) de la propriété *Second Tracked Target Type*. En règle générale, les deux types ont la valeur [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride) et les valeurs résultantes `SolverHandler.TransformOverride` et `InBetween.SecondTransformOverride` définies sur les deux points de terminaison suivis.

Au moment de l’exécution, le composant [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) crée un autre composant [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) en fonction des propriétés *Second Tracked Target Type* et *Second Transform Override*.

Le/la `PartwayOffset` définit l’emplacement de l’objet le long de la ligne entre deux transformations. L’objet doit être placé 0,5 à mi-chemin, 1,0 à la première transformation et 0,0 à la deuxième transformation.

![Exemple InBetween](../../images/solver/InBetweenExample.png)  
*Exemple d’utilisation d’un solveur InBetween pour conserver l’objet entre deux transformations*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

Le/la [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) fonctionne en effectuant un raycast sur un LayerMask défini de surfaces et en plaçant le GameObject à ce point de contact.

La propriété *Surface Normal Offset* place le GameObject à une distance définie en mètres à l’extérieur de la surface dans la direction normale par rapport au point d’accès de la surface.

À l’inverse, la propriété *Surface Ray Offset* place le GameObject à une distance définie en mètres par rapport à la surface, mais dans la direction opposée du raycast effectué. Par conséquent, si le raycast est le pointage du regard de l’utilisateur, le GameObject se rapprochera le long de la ligne du point d’accès de la surface vers la caméra.

La propriété *Orientation Mode* détermine le type de rotation à appliquer par rapport à la normale sur la surface.

* *None* - aucune rotation appliquée
* *TrackedTarget* - L’objet va faire face à la transformation suivie qui dirige le raycast
* *SurfaceNormal* - L’objet est aligné normalement en fonction du point d’accès sur la surface
* *Blended* - L’objet est aligné en fonction de la normale sur le point d’accès sur la surface ET en se basant sur la transformation suivie.

Pour forcer le GameObject associé à rester vertical dans n’importe quel mode autre que *None*, activez *Keep Orientation Vertical*.

> [!NOTE]
> Utilisez la propriété *Orientation Blend* pour contrôler l’équilibre entre les facteurs de rotation lorsque le *mode d’orientation* a la valeur *Blended*. La valeur 0,0 aura une orientation entièrement pilotée par le mode *TrackedTarget* et la valeur 1,0 aura une orientation entièrement pilotée par *SurfaceNormal*.

![Exemple SurfaceMagnetism](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>Détermination des surfaces qui peuvent être atteintes

Lorsque vous ajoutez un composant [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) à un GameObject, il est important de tenir compte de la couche du GameObject et de ses enfants, en présence de colliders. Le composant fonctionne en exécutant différents types de raycasts pour déterminer la surface sur laquelle il peut agir comme un « aimant ». Si le résolveur GameObject a un collider sur l’une des couches répertoriéez dans la propriété `MagneticSurfaces` de `SurfaceMagnetism`, le raycast sera probablement atteint, ce qui entraînera un attachement de GameObject à son propre point de collider. Ce comportement étrange peut être évité en définissant le GameObject principal et tous les enfants sur la couche *Ignore Raycast* ou en modifiant le tableau LayerMask `MagneticSurfaces` de manière appropriée.

À l’inverse, un GameObject [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) n’entrera pas en conflit avec des surfaces sur une couche non répertoriée dans la propriété `MagneticSurfaces`. Il est généralement recommandé de placer toutes les surfaces souhaitées sur une couche dédiée (par exemple, *Surfaces*) et en définissant simplement la propriété `MagneticSurfaces` sur cette couche.  L’utilisation de la *default* ou de *everything* peut entraîner des composants de l’interface utilisateur ou des curseurs contribuant au résolveur.

Enfin, les surfaces plus éloignées que le paramètre de propriété `MaxRaycastDistance` seront ignorées par les raycasts `SurfaceMagnetism`.

### <a name="directionalindicator"></a>DirectionalIndicator

La classe [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) est un composant tag-along qui s’oriente vers la direction d’un point souhaité dans l’espace.

La plus couramment utilisée lorsque la propriété *Tracked Target Type* du/de la [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) est défini(e) sur [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head). De cette manière, un composant d’expérience utilisateur avec le résolveur [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) indiquera à l’utilisateur d’examiner le point souhaité dans l’espace.

Le point souhaité dans l’espace est déterminé par la propriété *Directional Target*.

Si la cible directionnelle est affichable par l’utilisateur, ou quel que soit le cadre de référence défini dans le/la [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler), ce résolveur désactive tous les composants [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) qui le précèdent. S’il n’est pas visible, tout sera activé sur l’indicateur.

La taille de l’indicateur diminuera à mesure que l’utilisateur est proche de capturer la *Directional Target* dans son champ de vue.

* *Min Indicator Scale* - L’échelle minimale pour l’objet indicateur
* *Max Indicator Scale* - L’échelle maximale pour l’objet indicateur

* *Visibility Scale Factor* - Multiplicateur pour augmenter ou diminuer le champ de vue qui détermine si le point *Directional Target* est affichable ou non
* *View Offset* - À partir du point de vue du cadre de référence (c.-à-d. possiblement avec caméra), cette propriété définit à quel point l’objet doit être éloigné du centre de la fenêtre d’affichage.

![Propriétés de l’indicateur directionnel](../../images/solver/DirectionalIndicatorExample.png)  
*Propriétés de l’indicateur directionnel*

![Exemple de scène de l’indicateur directionnel](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*Exemple de scène de l’indicateur directionnel Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>Menu Main avec HandConstraint et HandConstraintPalmUp

![Exemple d’expérience utilisateur du menu Main](../../images/solver/MRTK_UX_HandMenu.png)

Le comportement [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) fournit un résolveur qui limite l’objet suivi à une région sécurisée pour le contenu contraint à la main (par exemple, l’interface utilisateur manuelle, les menus, etc.). Les régions sécurisées sont considérées comme des zones qui ne se croisent pas avec la main. Une classe dérivée de [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) appelée [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) est également incluse pour illustrer un comportement courant de l’activation de l’objet suivi du résolveur lorsque la paume est orientée vers l’utilisateur.

Pour obtenir des exemples d’utilisation du résolveur Hand Constraint pour créer des menus manuels, [consultez la page du menu Main](../hand-menu.md).

## <a name="see-also"></a>Voir aussi

* [Suivi de la main](../../input/hand-tracking.md)
* [Pointage du regard](../../input/gaze.md)
