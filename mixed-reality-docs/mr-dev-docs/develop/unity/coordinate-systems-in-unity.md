---
title: Systèmes de coordonnées dans Unity
description: Découvrez comment créer des expériences de réalité mixte assiste, debout, à l’échelle de la place et à l’échelle mondiale dans Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: système de coordonnées, système de coordonnées spatiales, orientation uniquement, à l’échelle assise, à l’échelle debout, mise à l’échelle de l’espace, à l’échelle mondiale, 360 de degrés, assis, debout, salle, monde, échelle, position, orientation, Unity, Ancre, ancrage spatial, point d’ancrage universel, verrouillage universel, verrouillage universel, verrouillage du corps, verrouillage du corps, perte de suivi, localisabilité, limites, recentre, casque de réalité mixte, casque de réalité
ms.openlocfilehash: 3372b9bd259202145fd658e225a36d2125f4a86d01eb90bc765b65918540db8b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203581"
---
# <a name="coordinate-systems-in-unity"></a>Systèmes de coordonnées dans Unity

Windows Mixed Reality prend en charge les applications à travers une large gamme d’expériences, des applications en orientation uniquement et à l’échelle à l’échelle jusqu’à des applications à l’échelle de la place. sur HoloLens, vous pouvez aller plus loin et créer des applications à l’échelle mondiale qui permettent aux utilisateurs d’aller au-delà de 5 mètres, en explorant un étage entier d’un immeuble et au-delà.

La première étape de la création d’une expérience de réalité mixte dans Unity consiste à comprendre [les systèmes de coordonnées et à choisir la mise à l’échelle](../../design/coordinate-systems.md) ciblée par votre application.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Création d’une expérience d’orientation seule ou de mise à l’échelle installée

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *XRDevice*

Pour créer une expérience d' **orientation uniquement** ou de mise à l' **échelle assise**, vous devez définir Unity sur le type d’espace de suivi fixe. Espace de suivi fixe définit le système de coordonnées universelles de l’unité pour suivre le [cadre stationnaire de référence](../../design/coordinate-systems.md#spatial-coordinate-systems). Dans le mode de suivi fixe, le contenu placé dans l’éditeur juste devant l’emplacement par défaut de l’appareil photo (Forward is-Z) s’affiche devant l’utilisateur au lancement de l’application.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *InputTracking*

Pour une expérience purement en **orientation uniquement** telle qu’une visionneuse vidéo de 360 degrés (où les mises à jour de la tête de position dépasseraient l’illusion), vous pouvez définir [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) sur true :

```cs
InputTracking.disablePositionalTracking = true;
```

Pour une expérience de mise à l' **échelle assiste**, pour permettre à l’utilisateur de recentrer plus tard l’origine assise, vous pouvez appeler [XR. Méthode InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Création d’une expérience de mise à l’échelle permanente ou à l’échelle de l’espace

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *XRDevice*

Pour une expérience à l’échelle **permanente** ou à l’échelle de l' **espace**, vous devez placer du contenu par rapport à l’étage. Vous avez raison de l’étage de l’utilisateur à l’aide de la **[Phase spatiale](../../design/coordinate-systems.md#spatial-coordinate-systems)**, qui représente l’origine de l’utilisateur et la limite facultative de l’espace, configurées lors de la première exécution.

Pour vous assurer que Unity fonctionne avec son système de coordonnées universel à l’étage, vous pouvez définir et tester qu’Unity utilise le type d’espace de suivi RoomScale :

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Si SetTrackingSpaceType retourne la valeur true, Unity a correctement basculé son système de coordonnées universel pour suivre le [cadre de la phase de référence](../../design/coordinate-systems.md#spatial-coordinate-systems).
* Si SetTrackingSpaceType retourne la valeur false, Unity n’a pas pu basculer vers le cadre de la phase de référence, probablement parce que l’utilisateur n’a pas configuré d’étage dans son environnement. Bien qu’une valeur de retour false ne soit pas courante, elle peut se produire si l’étape est configurée dans une salle différente et que l’appareil est déplacé dans la salle actuelle sans que l’utilisateur ne configure une nouvelle étape.

Une fois que votre application a correctement défini le type d’espace de suivi RoomScale, le contenu placé sur le plan y = 0 s’affiche sur le plancher. L’origine à 0, 0 correspond à l’emplacement spécifique sur le plancher où l’utilisateur a pris la main pendant la configuration de la salle, avec-Z représentant la direction vers l’avant pendant la configuration.

**Espace de noms :** *UnityEngine. expérimentale. XR*<br>
**Type :** *limite*

Dans le code de script, vous pouvez ensuite appeler la méthode TryGetGeometry sur le type UnityEngine. expérimentale. XR. Boundary pour obtenir un polygone de limite, en spécifiant un type de limite de TrackedArea. Si l’utilisateur a défini une limite (vous récupérez une liste de vertex), il est possible de fournir une expérience de mise à l’échelle de l' **espace** à l’utilisateur, où il peut se déplacer dans la scène que vous créez.

> [!NOTE]
> Le système affiche automatiquement la limite lorsque l’utilisateur l’approche. Votre application n’a pas besoin d’utiliser ce polygone pour restituer la limite elle-même. Toutefois, vous pouvez choisir de disposer vos objets de scène à l’aide de ce polygone limite pour vous assurer que l’utilisateur peut atteindre physiquement ces objets sans téléportage :

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Création d’une expérience à l’échelle mondiale

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Type :** *WorldAnchor*

pour les **expériences réelles à l’échelle mondiale** sur les HoloLens qui permettent aux utilisateurs d’aller au-delà de 5 mètres, vous aurez besoin de nouvelles techniques au-delà de celles utilisées pour les expériences à l’échelle de la place. Une technique clé que vous allez utiliser consiste à créer une [ancre spatiale](../../design/coordinate-systems.md#spatial-anchors) pour verrouiller un cluster d’hologrammes précisément en place dans le monde physique, quel que soit le degré d’itinérance de l’utilisateur, puis [retrouvez ces hologrammes dans les sessions ultérieures](../../design/coordinate-systems.md#spatial-anchor-persistence).

Dans Unity, vous créez une ancre spatiale en ajoutant le composant **WorldAnchor** Unity à un GameObject.

### <a name="adding-a-world-anchor"></a>Ajout d’une ancre mondiale

Pour ajouter une ancre universelle, appelez AddComponent <WorldAnchor> () sur l’objet de jeu avec la transformation que vous souhaitez ancrer dans le monde réel.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Et voilà ! Cet objet de jeu sera désormais ancré à son emplacement actuel dans le monde physique : vous pouvez constater que ses coordonnées universelles s’ajustent légèrement au fil du temps pour garantir l’alignement physique. Utilisez la [persistance](persistence-in-unity.md) pour rechercher à nouveau cet emplacement d’ancrage dans une session d’application future.

### <a name="removing-a-world-anchor"></a>Suppression d’une ancre mondiale

Si vous ne souhaitez plus que les GameObject soient verrouillés sur un emplacement géographique physique et que vous n’envisagez pas de déplacer ce cadre, vous pouvez simplement appeler Destroy sur le composant d’ancrage du monde.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Si vous souhaitez déplacer le GameObject ce frame, vous devez appeler DestroyImmediate à la place.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Déplacement d’un GameObject ancré dans le monde

Les GameObject ne peuvent pas être déplacées pendant qu’une ancre mondiale y est. Si vous devez déplacer le GameObject ce frame, vous devez :
1. DestroyImmediate le composant d’ancrage universel
2. Déplacer le GameObject
3. Ajoutez un nouveau composant d’ancrage du monde au GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestion des modifications de localisabilité

Un WorldAnchor peut ne pas être localisable dans le monde physique à un moment donné. Si cela se produit, Unity ne met pas à jour la transformation de l’objet ancré. Cela peut également changer pendant l’exécution d’une application. Si la modification de la localisation n’est pas prise en charge, l’objet n’apparaîtra pas à l’emplacement physique approprié dans le monde.

Pour être informé des changements de localisation :
1. S’abonner à l’événement OnTrackingChanged
2. Gérer l’événement

L’événement **OnTrackingChanged** est appelé chaque fois que l’ancrage spatial sous-jacent change entre un État localisable et n’est pas localisable.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Ensuite, gérez l’événement :

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Parfois, les ancres se trouvent immédiatement. Dans ce cas, cette propriété isLocated de l’ancre sera définie sur true lorsque AddComponent <WorldAnchor> () retourne. Par conséquent, l’événement OnTrackingChanged n’est pas déclenché. Un modèle propre serait d’appeler votre gestionnaire OnTrackingChanged avec l’état initial de IsLocated après avoir attaché une ancre.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Partage d’ancres sur plusieurs appareils

utilisez les <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android.  En partageant une ancre spatiale commune sur plusieurs appareils, chaque utilisateur peut voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.  Cette technique autorise les expériences partagées en temps réel.

Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.

Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement Unity que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte. À partir d’ici, vous pouvez passer au composant suivant :

> [!div class="nextstepaction"]
> [Pointage du regard](gaze-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Échelle de l’expérience](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Étape spatiale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Suivi des pertes dans Unity](tracking-loss-in-unity.md)
* [Ancres spatiales](../../design/spatial-anchors.md)
* [Persistance dans Unity](persistence-in-unity.md)
* [Expériences partagées dans Unity](shared-experiences-in-unity.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a>