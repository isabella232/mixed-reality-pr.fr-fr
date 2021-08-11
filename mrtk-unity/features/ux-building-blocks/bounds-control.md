---
title: Contrôle des limites
description: Vue d’ensemble du contrôle de limites dans MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, la réalité mixte, le développement, le MRTK, le contrôle des limites,
ms.openlocfilehash: 3abefd142753c34c9126d71cde77ebca0b40f1f9b7a81b5815777b9e938e172a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217182"
---
# <a name="bounds-control"></a>Contrôle des limites

![Contrôle des limites](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* est le nouveau composant pour la manipulation du comportement, précédemment trouvé dans *BoundingBox*. Le contrôle des limites effectue un certain nombre d’améliorations et de simplifications dans le programme d’installation et ajoute de nouvelles fonctionnalités. Ce composant remplace le cadre englobant, qui est déconseillé.

Le [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fournit des fonctionnalités de base pour transformer des objets en réalité mixte. Un contrôle de limites affiche une zone autour de l’hologramme pour indiquer qu’il est possible d’interagir avec. Les poignées sur les angles et les bords de la zone permettent la mise à l’échelle, la rotation ou la traduction de l’objet. Le contrôle de limites réagit également aux entrées d’utilisateur. sur HoloLens 2, par exemple, le contrôle de limites répond à la proximité d’un doigt, en fournissant un retour visuel pour aider à percevoir la distance par rapport à l’objet. Toutes les interactions et tous les visuels peuvent être facilement personnalisés.

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples de configurations de contrôle de limites dans la `BoundsControlExamples` scène.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Propriétés de l’inspecteur

### <a name="target-object"></a>Objet cible

Cette propriété spécifie quel objet sera transformé par la manipulation de contrôle de limites. Si aucun objet n’est défini, la valeur par défaut est l’objet propriétaire.

### <a name="activation-behavior"></a>Comportement d’activation

Il existe plusieurs options pour activer l’interface de contrôle des limites.

* *Activer sur Start*: le contrôle des limites devient visible une fois la scène démarrée.
* *Activer par proximité*: le contrôle des limites devient visible quand une main articulée est proche de l’objet.
* *Activer par pointeur*: le contrôle de limites devient visible lorsqu’il est ciblé par un pointeur de rayon.
* *Activer par proximité et pointeur*: le contrôle des limites devient visible lorsqu’il est ciblé par un pointeur de rayon de la main ou une main articulée est proche de l’objet.
* *Activer manuellement*: le contrôle de limites ne devient pas visible automatiquement. Vous pouvez l’activer manuellement par le biais d’un script en accédant à la propriété boundsControl. active.

### <a name="bounds-override"></a>Substitutions de limites

Définit un conflit de cases à partir de l’objet pour le calcul de limites.

### <a name="box-padding"></a>Remplissage de zone

Ajoute une marge intérieure aux limites du conflit utilisées pour calculer les étendues du contrôle. Cela influence non seulement l’interaction, mais également l’impact sur les visuels.

### <a name="flatten-axis"></a>Aplatir l’axe

Indique si le contrôle est aplati dans l’un des axes, en le rendant en deux dimensions et en interautorisant la manipulation le long de cet axe. Cette fonctionnalité peut être utilisée pour les objets fins comme les ardoises.
Si l’option aplatir l’axe est définie sur *aplatir* automatiquement, le script sélectionne automatiquement l’axe avec l’étendue la plus petite comme axe aplati.

### <a name="smoothing"></a>Adoucissage

La section lissage permet de configurer le comportement de lissage pour la mise à l’échelle et la rotation du contrôle.

### <a name="visuals"></a>Objets visuels

L’apparence du contrôle des limites peut être configurée en modifiant l’une des configurations de visuels correspondantes.
Les configurations visuelles sont des objets scriptables liés ou incorporés et sont décrites plus en détail dans la [section relative](#configuration-objects)à l’objet de configuration.

## <a name="configuration-objects"></a>Objets de configuration

Le contrôle est fourni avec un ensemble d’objets de configuration qui peuvent être stockés en tant qu’objets pouvant faire l’objet d’un script et partagés entre différentes instances ou prefabs. Les configurations peuvent être partagées et liées en tant que fichiers de ressources pouvant faire l’élément d’un script ou imbriqués dans prefabs. D’autres configurations peuvent également être définies directement sur l’instance sans liaison à une ressource scriptable externe ou imbriquée.

L’inspecteur de contrôle des limites indique si une configuration est partagée ou inline dans le cadre de l’instance actuelle en indiquant un message dans l’inspecteur de propriété. En outre, les instances partagées ne peuvent pas être modifiées directement dans la fenêtre des propriétés du contrôle de limites lui-même, mais au lieu de cela, la ressource à laquelle elle est liée doit être directement modification pour éviter toute modification accidentelle des configurations partagées.

Le contrôle des limites actuelles offre des options d’objets de configuration pour les fonctionnalités suivantes :

* Poignées
  * [Poignées d’échelle](#scale-handles-configuration)
  * [Poignées de rotation](#rotation-handles-configuration)
  * [Descripteurs de traduction](#translation-handles-configuration)
* [Liens/filaire](#links-configuration-wireframe)
* [Affichage de zone](#box-configuration)
* [Effet de proximité](#proximity-effect-configuration)

### <a name="box-configuration"></a>Configuration de Box

La configuration Box est responsable du rendu d’un rectangle plein avec les limites définies par la taille du conflit et la marge intérieure. Les propriétés suivantes peuvent être définies :

* **Box Material**: définit la matière appliquée à la zone rendue quand aucune interaction n’a lieu. Une zone s’affiche uniquement si ce matériau est défini.
* **Matériau à boîte de Box**: matériau pour la zone lorsque l’utilisateur interagit avec le contrôle en saisissant via une interaction proche ou éloignée.
* **Échelle d’affichage de l’axe aplati**: échelle appliquée à la zone affichée si l’un des axes est [aplati](#flatten-axis).

### <a name="scale-handles-configuration"></a>Configuration des poignées d’échelle

Ce tiroir de propriété permet de modifier le comportement et la visualisation des poignées d’échelle du contrôle des limites.

* **Matériau de gestion**: matériau appliqué aux descripteurs.
* **Gérer un matériau retiré**: matériau appliqué à la poignée saisie.
* **Handle Prefab**: Prefab facultatif pour le descripteur de mise à l’échelle. Si la valeur n’est pas définie, MRTK utilise un cube comme valeur par défaut.
* **Taille du handle**: taille du handle d’échelle.
* **Remplissage du conflit**: remplissage à ajouter au conflit de handles.
* **Dessiner** la connexion lors de la manipulation : lorsqu’Active dessine une ligne de connexion du point de début de l’interaction à la position actuelle ou du pointeur.
* **Handles ignore le conflit**: si un conflit est lié ici, les handles ignorent toute collision avec ce conflit.
* **Handle ardoise Prefab**: Prefab à utiliser pour le handle lorsque le contrôle est aplati.
* **Afficher les poignées d’échelle**: contrôle la visibilité du handle.
* **Comportement** de mise à l’échelle : peut être défini avec une mise à l’échelle uniforme ou non uniforme.

### <a name="rotation-handles-configuration"></a>Configuration des poignées de rotation

Cette configuration définit le comportement de la poignée de rotation.

* **Matériau de gestion**: matériau appliqué aux descripteurs.
* **Gérer un matériau retiré**: matériau appliqué à la poignée saisie.
* **Handle Prefab**: Prefab facultatif pour le descripteur. Si la valeur n’est pas définie, MRTK utilise une sphère comme valeur par défaut.
* **Taille du handle**: taille du handle.
* **Remplissage du conflit**: remplissage à ajouter au conflit de handles.
* **Dessiner** la connexion lors de la manipulation : lorsqu’Active dessine une ligne de connexion du point de début de l’interaction à la position actuelle ou du pointeur.
* **Handles ignore le conflit**: si un conflit est lié ici, les handles ignorent toute collision avec ce conflit.
* **Handle Prefab type de conflit**: type de conflit à utiliser avec le handle créé.
* **Afficher le handle pour x**: contrôle la visibilité du handle pour l’axe x.
* **Afficher le handle pour y**: contrôle la visibilité du handle pour l’axe y.
* **Afficher le handle pour z**: contrôle la visibilité du handle pour l’axe z.

### <a name="translation-handles-configuration"></a>Configuration des handles de traduction

Permet d’activer et de configurer des handles de traduction pour le contrôle des limites. Notez que les descripteurs de traduction sont désactivés par défaut.

* **Matériau de gestion**: matériau appliqué aux descripteurs.
* **Gérer un matériau retiré**: matériau appliqué à la poignée saisie.
* **Handle Prefab**: Prefab facultatif pour le descripteur. Si la valeur n’est pas définie, MRTK utilise une sphère comme valeur par défaut.
* **Taille du handle**: taille du handle.
* **Remplissage du conflit**: remplissage à ajouter au conflit de handles.
* **Dessiner** la connexion lors de la manipulation : lorsqu’Active dessine une ligne de connexion du point de début de l’interaction à la position actuelle ou du pointeur.
* **Handles ignore le conflit**: si un conflit est lié ici, les handles ignorent toute collision avec ce conflit.
* **Handle Prefab type de conflit**: type de conflit à utiliser avec le handle créé.
* **Afficher le handle pour x**: contrôle la visibilité du handle pour l’axe x.
* **Afficher le handle pour y**: contrôle la visibilité du handle pour l’axe y.
* **Afficher le handle pour z**: contrôle la visibilité du handle pour l’axe z.

### <a name="links-configuration-wireframe"></a>Configuration des liens (filaire)

La configuration des liens active la fonctionnalité filaire du contrôle des limites. Les propriétés suivantes peuvent être configurées :

* **Matériau filaire**: matériau appliqué à la maille filaire.
* **Rayon de périphérie filaire**: épaisseur du filaire.
* **Forme filaire**: la forme du filaire peut être cubique ou cylindrique.
* **Afficher le filaire**: contrôle la visibilité du filaire.

### <a name="proximity-effect-configuration"></a>Configuration de l’effet de proximité

Affichez et masquez les poignées avec l’animation en fonction de la distance des mains. Il a une animation de mise à l’échelle en deux étapes. les valeurs par défaut sont définies sur le comportement de style HoloLens 2.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Effet de proximité actif**: activer l’activation du handle basé sur la proximité
* **Proximité** de l’objet : distance pour la mise à l’échelle du 1er échelon
* **Proximité** de l’objet : distance pour la mise à l’échelle du 2e échelon
* Mise à l' **échelle lointaine**: valeur de mise à l’échelle par défaut de la ressource de poignée lorsque les mains sont hors limites de l’interaction de contrôle des limites (distance définie ci-dessus par « gérer la proximité moyenne ». Utilisez 0 pour masquer le descripteur par défaut)
* **Échelle moyenne**: valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction de contrôle des limites (distance définie ci-dessus par « gérer la proximité ». Utiliser 1 pour afficher la taille normale
* **Clôture** de l’échelle : valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction de manipulation (distance définie ci-dessus par « poignée de proximité ». Utiliser 1. x pour afficher une taille supérieure)
* **Taux de croissance lointaine**: évalue l’échelle d’un objet à l’échelle de proximité lorsque la main passe d’une distance moyenne à l’extrême.
* **Taux d’augmentation moyenne**: calcul de l’échelle d’un objet mis à l’échelle lorsque la main passe d’une valeur moyenne à une proximité proche.
* **Taux de croissance proche**: taux d’échelle d’un objet à l’échelle de proximité lorsque la main passe de proximité au centre de l’objet.

## <a name="constraint-system"></a>Système de contrainte

Le contrôle de limites prend en charge l’utilisation du [Gestionnaire de contraintes](constraint-manager.md) pour limiter ou modifier le comportement de translation, de rotation ou de mise à l’échelle lors de l’utilisation de handles de contrôle de limites.

L’inspecteur de propriété affiche tous les gestionnaires de contraintes disponibles attachés au même objet de jeu dans une liste déroulante avec une option permettant de faire défiler et de mettre en surbrillance le gestionnaire de contraintes sélectionné.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Événements

Le contrôle de limites fournit les événements suivants. Cet exemple utilise ces événements pour lire les commentaires audio.

* **Rotate Started**: déclenché au début de la rotation.
* **Rotation arrêtée**: déclenché lorsque la rotation s’arrête.
* Mise à l' **échelle démarrée**: se déclenche lors du démarrage de la mise à l’échelle.
* **Arrêt** de l’échelle : se déclenche lorsque la mise à l’échelle s’arrête.
* **Conversion démarrée**: se déclenche au démarrage de la traduction.
* **Translate Stopped**: se déclenche lorsque la traduction s’arrête.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Élastiques (expérimental)

Les élastiques peuvent être utilisés lors de la manipulation d’objets via le contrôle des limites. Notez que le [système élastiques](../experimental/elastic-system.md) est toujours dans un État expérimental. Pour activer les élastiques, liez un composant Gestionnaire élastique existant ou créez et liez un nouveau gestionnaire élastiques à l’aide du `Add Elastics Manager` bouton.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Gérer les styles

par défaut, lorsque vous affectez simplement le [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, il affiche le descripteur de la HoloLens premier style gen. pour utiliser HoloLens 2 poignées de style, vous devez assigner les prefabs et les matériaux de handle appropriés.

![Styles de handle de contrôle des limites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

vous trouverez ci-dessous les prefabs, les matériaux et les valeurs de mise à l’échelle pour les poignées de contrôle des limites de style HoloLens 2. Cet exemple se trouve dans la `BoundsControlExamples` scène.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a>handles (programme d’installation de HoloLens 2 style)

* **Matériau de gestion**: BoundingBoxHandleWhite. mat
* **Gérer un matériau retiré**: BoundingBoxHandleBlueGrabbed. mat
* Descripteur de mise à l' **échelle Prefab**: MRTK_BoundingBox_ScaleHandle. Prefab
* **Poignée d’échelle ardoise Prefab**: MRTK_BoundingBox_ScaleHandle_Slate. Prefab
* **Taille du handle** de l’échelle : 0,016 (1,6 cm)
* Mise à l' **échelle du remplissage du conflit**: 0,016 (rend le conflit de manipulation légèrement plus grand que le visuel de la poignée)
* **Handle de rotation Prefab**: MRTK_BoundingBox_RotateHandle. Prefab
* **Taille du handle de rotation**: 0,016
* La **poignée de rotation marge intérieure du conflit**: 0,016 (rend le conflit de manipulation légèrement plus grand que le visuel de la poignée)

## <a name="transformation-changes-with-object-manipulator"></a>Modifications de transformation avec manipulateur d’objets

Un contrôle de limites peut être utilisé conjointement avec [`ObjectManipulator.cs`](object-manipulator.md) pour autoriser certains types de manipulations (par exemple, déplacement de l’objet) sans utiliser de handles. Le gestionnaire de manipulation prend en charge les interactions une et deux. Le suivi de la [main](../input/hand-tracking.md) peut être utilisé pour interagir avec un objet plus proche.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Pour que les bords du contrôle des limites se comportent de la même façon lors de leur déplacement à l’aide [`ObjectManipulator`](object-manipulator.md) de l’interaction Far, il est recommandé de connecter ses événements pour la *manipulation démarrée*  /  *sur la manipulation terminée* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` respectivement, comme illustré dans la capture d’écran ci-dessus.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Comment ajouter et configurer un contrôle de limites à l’aide de l’inspecteur Unity

1. Ajouter un conflit de zone à un objet
2. Affecter `BoundsControl` un script à un objet
3. Configurer des options, telles que les méthodes « activation » (voir la section Propriétés de l' [inspecteur](#inspector-properties) ci-dessous)
4. Facultatif assigner des prefabs et des matériaux pour un contrôle de limites de style HoloLens 2 (consultez la section relative aux [styles de Handle](#handle-styles) ci-dessous)

> [!NOTE]
> Utilisez l' *objet cible* et le champ de *remplacement de limites* dans l’inspecteur pour assigner un objet et un conflit spécifiques dans l’objet avec plusieurs composants enfants.

![Contrôle des limites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Comment ajouter et configurer un contrôle de limites dans le code

1. Instancier le cube GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Assigner `BoundsControl` un script à un objet avec un conflit à l’aide de AddComponent<> ()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Configurez les options soit directement sur le contrôle, soit par le biais de l’une des configurations scriptables (voir la section Propriétés et [configurations](#configuration-objects) de l' [inspecteur](#inspector-properties) ci-dessous).

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. Facultatif assignez des prefabs et des matériaux pour un contrôle de limites de style HoloLens 2. Cela nécessite toujours des affectations via l’inspecteur, car les matériaux et les prefabs doivent être chargés dynamiquement.

> [!NOTE]
> Utilisation du dossier « Resources » ou du [nuanceur Unity. Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) pour le chargement dynamique des nuanceurs n’est pas recommandé, car les permutations de nuanceur peuvent être manquantes au moment de l’exécution.

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Exemple : définir l’échelle de contrôle des limites maximales et minimales à l’aide de MinMaxScaleConstraint

Pour définir l’échelle minimale et maximale, attachez un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) à votre contrôle. Comme le contrôle de limites As associe et active automatiquement le gestionnaire de contraintes, le MinMaxScaleConstraint est appliqué automatiquement à la transformation change une fois qu’elle est attachée et configurée.

Vous pouvez également utiliser MinMaxScaleConstraint pour définir une échelle minimale et maximale pour [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>Exemple : ajouter un contrôle de limites autour d’un objet de jeu

Pour ajouter un contrôle de limites autour d’un objet, ajoutez simplement un `BoundsControl` composant à ce dernier :

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migration à partir d’un cadre englobant

Les prefabs et les instances existantes qui utilisent le [cadre englobant](bounding-box.md) peuvent être mis à niveau vers le nouveau contrôle des limites via la [fenêtre de migration](../tools/migration-window.md) qui fait partie du package d’outils MRTK.

Pour mettre à niveau des instances individuelles du cadre englobant, il existe également une option de migration à l’intérieur de l’inspecteur de propriété du composant.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Voir aussi

* [Manipulateur d’objets](object-manipulator.md)
* [Gestionnaire de contraintes](constraint-manager.md)
* [Fenêtre de migration](../tools/migration-window.md)
* [Système élastique (expérimental)](../experimental/elastic-system.md)
