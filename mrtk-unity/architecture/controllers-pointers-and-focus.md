---
title: Contrôleurs, pointeurs et focus
description: Interaction avec les contrôleurs, les pointeurs et le focus.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, pointeurs, contrôleurs
ms.openlocfilehash: 00bc0641182c566b045f959dfa361e1311b3cd224fc998f154010ad2996679ae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196289"
---
# <a name="controllers-pointers-and-focus"></a>Contrôleurs, pointeurs et focus

Les contrôleurs, les pointeurs et le focus sont des concepts de niveau supérieur qui s’appuient sur la fondation établie par le système d’entrée principal. Ensemble, ils fournissent une grande partie du mécanisme pour l’interaction avec les objets dans la scène.

## <a name="controllers"></a>Controllers

Les contrôleurs sont des représentations d’un contrôleur physique (6 degrés de liberté, articulés, etc.). Ils sont créés par les gestionnaires d’appareils et sont responsables de la communication avec le système sous-jacent correspondant et de la traduction de ces données en données et événements en forme de MRTK. a

par exemple, sur la plateforme Windows Mixed Reality, [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) est un contrôleur qui est chargé de l’interfaçage avec les [api de suivi de main](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Windows sous-jacentes pour obtenir des informations sur les jointures, les poses et d’autres propriétés de la main. Il est chargé de convertir ces données en événements MRTK pertinents (par exemple, en appelant RaisePoseInputChanged ou RaiseHandJointsUpdated) et en mettant à jour son propre état interne afin que les requêtes pour [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) renvoient des données correctes.

En règle générale, le cycle de vie d’un contrôleur implique ce qui suit :

1. Un contrôleur est créé par un gestionnaire de périphériques lors de la détection d’une nouvelle source (par exemple, le gestionnaire de périphériques détecte et démarre le suivi d’une main).

2. Dans la boucle Update () du contrôleur, il appelle le système d’API sous-jacent.

3. Dans la même boucle de mise à jour, elle déclenche des modifications d’événements d’entrée en appelant directement dans le système d’entrée principal lui-même (par exemple, en déclenchant HandMeshUpdated ou HandJointsUpdated).

## <a name="pointers-and-focus"></a>Pointeurs et Focus

Les pointeurs sont utilisés pour interagir avec les objets de jeu. Cette section décrit comment les pointeurs sont créés, comment ils sont mis à jour et comment ils déterminent le ou les objets qui sont activés. Il couvre également les différents types de pointeurs qui existent et les scénarios dans lesquels ils sont actifs.

### <a name="pointer-categories"></a>Catégories de pointeurs

Les pointeurs appartiennent généralement à l’une des catégories suivantes :

- **Pointeurs Far**

  Ces types de pointeurs sont utilisés pour interagir avec des objets éloignés de l’utilisateur (bien que loin soit défini comme simplement « pas près de »). Ces types de pointeurs effectuent généralement un cast des lignes qui peuvent se trouver dans le monde entier et permettent à l’utilisateur d’interagir avec les objets qui ne sont pas immédiatement en regard de ceux-ci et de les manipuler.

- **Pointeurs Near**

  Ces types de pointeurs sont utilisés pour interagir avec des objets suffisamment proches de l’utilisateur pour les saisir, les toucher et les manipuler. En règle générale, ces types de pointeurs interagissent avec les objets en recherchant des objets dans le voisinage voisin (en effectuant des Raycasting à de petites distances, en effectuant une conversion sphérique à la recherche d’objets dans le voisinage ou en énumérant des listes d’objets considérés comme pouvant être recherchés/touchable).

- **Pointeurs de téléversion**

  Ces types de pointeurs se connectent au système de téléportage pour gérer le déplacement de l’utilisateur vers l’emplacement ciblé par le pointeur.

## <a name="pointer-mediation"></a>Médiation du pointeur

Étant donné qu’un seul contrôleur peut avoir plusieurs pointeurs (par exemple, la main articulée peut avoir à la fois des pointeurs d’interaction near et FAR), il existe un composant qui est responsable de la médiation du pointeur qui doit être actif.

Par exemple, comme l’utilisateur approche un bouton enfoncé, le [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) doit s’arrêter et le [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) doit être engagé.

Cela est géré par le [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) , qui est chargé de déterminer les pointeurs actifs, en fonction de l’état de tous les pointeurs. L’une des principales choses à faire est de désactiver les pointeurs Far quand un pointeur near est proche d’un objet (consultez [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

Il est possible de fournir une autre implémentation du médiateur du pointeur en modifiant la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) propriété sur le profil de pointeur.

### <a name="how-to-disable-pointers"></a>Comment désactiver des pointeurs

Étant donné que le médiateur du pointeur exécute chaque frame, il finit par contrôler l’état actif/inactif de tous les pointeurs. Par conséquent, si vous définissez la propriété IsInteractionEnabled d’un pointeur dans le code, elle est remplacée par le médiateur du pointeur à chaque frame. Au lieu de cela, vous pouvez spécifier le [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) pour contrôler si les pointeurs doivent être activés ou désactivés. Notez que cela ne fonctionne que si vous utilisez la valeur par défaut [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) et [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) dans MRTK.

#### <a name="example-disable-hand-rays-in-mrtk"></a>Exemple : désactiver les rayons de main dans MRTK

Le code suivant permet de désactiver les rayons main dans MRTK :

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

Le code suivant renverra des rayons de main à leur comportement par défaut dans MRTK :

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

Le code suivant force les rayons de main à être activés, sans tenir compte du fait qu’ils sont à portée de main :

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Pour plus d’exemples, consultez et.

### <a name="focusprovider"></a>FocusProvider

Le [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) est le principal responsable de l’itération au sein de la liste de tous les pointeurs et de la définition de l’objet ayant le focus pour chaque pointeur.

Dans chaque `Update()` appel, ce qui suit :

1. Mettez à jour tous les pointeurs, par Raycasting et en procédant à la détection d’atteinte configurée par le pointeur lui-même (par exemple, le pointeur Sphere pourrait spécifier le raycastMode SphereOverlap, de sorte que FocusProvider effectue une collision basée sur les sphères)

2. Mettre à jour l’objet ayant le focus en fonction du pointeur (par exemple, si un objet a acquis le focus, il déclenche également des événements pour ces objets, si un objet a perdu le focus, il déclenche le focus, etc.).

### <a name="pointer-configuration-and-lifecycle"></a>Configuration du pointeur et cycle de vie

Les [pointeurs peuvent être configurés](../features/input/pointers.md) dans la section *pointeurs* du profil de système d’entrée.

La durée de vie d’un pointeur est généralement la suivante :

1. Un gestionnaire de périphériques détectera la présence d’un contrôleur. Ce gestionnaire de périphériques créera ensuite le jeu de pointeurs associé au contrôleur via un appel à [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. Le FocusProvider, dans sa boucle Update (), effectue une itération sur tous les pointeurs valides et effectue la logique de détection d’accès raycast ou associée. Utilisé pour déterminer l’objet qui est axé sur chaque pointeur particulier.

    - Étant donné qu’il est possible d’avoir plusieurs sources d’entrée actives en même temps (par exemple, deux mains actives), il est également possible d’avoir plusieurs objets qui ont le focus en même temps.

3. Lors de la découverte de la perte d’une source de contrôleur, le gestionnaire de périphériques détruit les pointeurs associés au contrôleur perdu.