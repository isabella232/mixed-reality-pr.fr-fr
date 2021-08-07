---
title: Rectangle englobant
description: Vue d’ensemble du cadre englobant dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, cadre englobant
ms.openlocfilehash: fa1ace9d7aaf547ee677accfc4254ce9c64aebdfa6a01f11962812b058bc9ceb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214211"
---
# <a name="bounding-box"></a>Rectangle englobant

![Rectangle englobant](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> Le cadre englobant est déconseillé et remplacé par son [contrôle de limites](bounds-control.md)de successeurs. Utilisez l' [une des options de migration](#migrating-to-bounds-control) pour mettre à niveau les objets de jeu existants.

Le [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fournit des fonctionnalités de base pour transformer des objets en réalité mixte. Un cadre englobant affiche un cube autour de l’hologramme pour indiquer qu’il peut être utilisé avec. Les poignées sur les angles et les bords du cube autorisent la mise à l’échelle ou la rotation de l’objet. Le cadre englobant réagit également aux entrées d’utilisateur. sur HoloLens 2, par exemple, le cadre englobant répond à la proximité d’un doigt, en fournissant un retour visuel pour aider à percevoir la distance par rapport à l’objet. Toutes les interactions et tous les visuels peuvent être facilement personnalisés.

pour plus d’informations, consultez [zone englobante et barre d’application](/windows/mixed-reality/app-bar-and-bounding-box) dans le Centre de développement Windows.

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples de configurations de cadre englobant dans la `BoundingBoxExamples` scène.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Comment ajouter et configurer un cadre englobant à l’aide de l’inspecteur Unity

1. Ajouter un conflit de zone à un objet
2. Affecter `BoundingBox` un script à un objet
3. Configurer des options, telles que les méthodes « activation » (voir la section Propriétés de l' [inspecteur](#inspector-properties) ci-dessous)
4. Facultatif assigner des prefabs et des matériaux pour un cadre englobant de style HoloLens 2 (consultez la section relative aux [styles de Handle](#handle-styles) ci-dessous)

> [!NOTE]
> Utilisez l' *objet cible* et le champ de *remplacement de limites* dans l’inspecteur pour assigner un objet et un conflit spécifiques dans l’objet avec plusieurs composants enfants.

![Cadre englobant 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Comment ajouter et configurer un cadre englobant dans le code

1. Instancier le cube GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Assigner `BoundingBox` un script à un objet avec un conflit à l’aide de AddComponent<> ()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Configurer les options (voir la section Propriétés de l' [inspecteur](#inspector-properties) ci-dessous)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. Facultatif affectez prefabs et materials pour un cadre englobant de style HoloLens 2. Cela nécessite toujours des affectations via l’inspecteur, car les matériaux et les prefabs doivent être chargés dynamiquement.

> [!NOTE]
> Utilisation du dossier « Resources » ou du [nuanceur Unity. Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) pour le chargement dynamique des nuanceurs n’est pas recommandé, car les permutations de nuanceur peuvent être manquantes au moment de l’exécution.

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>Exemple : définir la mise à l’échelle du cadre englobant maximal à l’aide de MinMaxScaleConstraint

Pour définir l’échelle minimale et maximale, utilisez [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . Vous pouvez également utiliser MinMaxScaleConstraint pour définir une échelle minimale et maximale pour [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>Exemple : ajouter un cadre englobant autour d’un objet de jeu

Pour ajouter un cadre englobant autour d’un objet, ajoutez simplement un `BoundingBox` composant à ce dernier :

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Propriétés de l’inspecteur

### <a name="target-object"></a>Objet cible

Cette propriété spécifie l’objet qui sera transformé par la manipulation de cadre englobant. Si aucun objet n’est défini, la zone englobante prend par défaut la valeur de l’objet propriétaire.

### <a name="bounds-override"></a>Substitutions de limites

Définit un conflit de cases à partir de l’objet pour le calcul de limites.

### <a name="activation-behavior"></a>Comportement d’activation

Il existe plusieurs options pour activer l’interface de cadre englobant.

* *Activer sur Start*: le cadre englobant devient visible une fois la scène démarrée.
* *Activer par proximité*: le cadre englobant devient visible quand une main articulée est proche de l’objet.
* *Activer par pointeur*: le cadre englobant devient visible lorsqu’il est ciblé par un pointeur de rayon.
* *Activer manuellement*: le cadre englobant ne devient pas visible automatiquement. Vous pouvez l’activer manuellement par le biais d’un script en accédant à la propriété boundingBox. active.

### <a name="scale-minimum"></a>Échelle minimale

Échelle minimale autorisée. Cette propriété est déconseillée et il est préférable d’ajouter un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Si ce script est ajouté, l’échelle minimale est prise à partir de celle-ci plutôt que du rectangle englobant.

### <a name="scale-maximum"></a>Échelle maximale

Échelle maximale autorisée. Cette propriété est déconseillée et il est préférable d’ajouter un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Si ce script est ajouté, la mise à l’échelle maximale est prise à partir de celle-ci plutôt que du rectangle englobant.

### <a name="box-display"></a>Affichage de zone

Diverses options de visualisation de cadre englobant.

Si l’option aplatir l’axe est définie sur *aplatir automatiquement*, le script interdit la manipulation le long de l’axe avec la plus petite étendue. Il en résulte une zone englobante 2D, qui est généralement utilisée pour les objets légers.

### <a name="handles"></a>Poignées

Vous pouvez assigner les éléments Material et Prefab pour remplacer le style de handle. Si aucun handle n’est affecté, ils sont affichés dans le style par défaut.

## <a name="events"></a>Événements

Le cadre englobant fournit les événements suivants. Cet exemple utilise ces événements pour lire les commentaires audio.

* **Rotate Started**: déclenché au début de la rotation.
* **Rotation terminée**: déclenché à la fin de la rotation.
* Mise à l' **échelle démarrée**: se déclenche lors du démarrage de la mise à l’échelle.
* Mise à l' **échelle terminée**: se déclenche lorsque la mise à l’échelle se termine.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Gérer les styles

par défaut, lorsque vous affectez simplement le [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, il affiche le descripteur de la HoloLens premier style gen. pour utiliser HoloLens 2 poignées de style, vous devez assigner les prefabs et les matériaux de handle appropriés.

![Styles de handle de cadre englobant](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

vous trouverez ci-dessous les prefabs, les matériaux et les valeurs de mise à l’échelle pour les poignées de cadre englobant de style HoloLens 2. Cet exemple se trouve dans la `BoundingBoxExamples` scène.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

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

### <a name="proximity-setup-for-hololens-2-style"></a>proximité (configuration du style de HoloLens 2)

Affichez et masquez les poignées avec l’animation en fonction de la distance des mains. Il a une animation de mise à l’échelle en deux étapes.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Effet de proximité actif**: activer l’activation du handle basé sur la proximité
* **Gérer la proximité moyenne**: distance pour la mise à l’échelle des premières étapes
* **Approche de proximité**: distance pour la mise à l’échelle de la deuxième étape
* **Échelle lointaine**: valeur de mise à l’échelle par défaut de la ressource de descripteur lorsque les mains sont hors de portée de l’interaction du cadre englobant (distance définie ci-dessus par « handle la proximité moyenne ». Utilisez 0 pour masquer le descripteur par défaut)
* **Échelle moyenne**: valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction du cadre englobant (distance définie ci-dessus par « gérer la proximité ». Utiliser 1 pour afficher la taille normale
* **Clôture** de l’échelle : valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction de manipulation (distance définie ci-dessus par « poignée de proximité ». Utiliser 1. x pour afficher une taille supérieure)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Rendre un objet déplaçable avec le gestionnaire de manipulation

Un cadre englobant peut être combiné avec [`ManipulationHandler.cs`](manipulation-handler.md) pour rendre l’objet déplaçable à l’aide de l’interaction Far. Le gestionnaire de manipulation prend en charge les interactions une et deux. Le suivi de la [main](../input/hand-tracking.md) peut être utilisé pour interagir avec un objet plus proche.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Pour que les bords du cadre englobant se comportent de la même façon lors de leur déplacement à l’aide [`ManipulationHandler`](manipulation-handler.md) de l’interaction Far, il est recommandé de connecter ses événements pour la *manipulation démarrée*  /  *sur la manipulation terminée* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` , comme illustré dans la capture d’écran ci-dessus.

## <a name="migrating-to-bounds-control"></a>Migrer vers le contrôle de limites

Les prefabs et les instances existantes qui utilisent le [cadre englobant](bounding-box.md) peuvent être mis à niveau vers le nouveau contrôle des limites via la [fenêtre de migration](../tools/migration-window.md) qui fait partie du package d’outils MRTK.

Pour mettre à niveau des instances individuelles du cadre englobant, il existe également une option de migration à l’intérieur de l’inspecteur de propriété du composant.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
