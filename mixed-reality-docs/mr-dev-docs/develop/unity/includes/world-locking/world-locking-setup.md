---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528760"
---
# <a name="world-locking-tools-recommended"></a>[Outils de verrouillage universel (recommandé)](#tab/wlt)

Nous vous recommandons d’installer les outils de verrouillage du monde à l’aide de la nouvelle fonctionnalité de réalité mixte. Une fois que vous avez téléchargé l’outil Mixed Reality Feature à partir du lien ci-dessous, sélectionnez la dernière version de **WLT Core** dans la section **outils de verrouillage du monde** :

![Fenêtre de sélection des fonctionnalités de l’outil de réalité mixte avec les outils de verrouillage du monde sélectionnés](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [Installer les outils de verrouillage du monde avec l’outil de fonctionnalité MR](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>Installation automatisée

Quand votre projet est prêt à l’emploi, exécutez l’utilitaire configurer la scène à partir du kit de tâches de la **réalité mixte > utilitaires > outils de verrouillage du monde**:

![Éditeur Unity avec le menu du kit d’outils de réalité mixte sélectionné](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> L’utilitaire de configuration de scène peut être réexécuté à tout moment. Par exemple, elle doit être réexécutée si la cible AR a été remplacée par le kit de développement logiciel (SDK) XR. Si la scène est déjà configurée correctement, l’exécution de l’utilitaire n’a aucun effet.

### <a name="visualizers"></a>Visualiseurs

Lors du développement anticipé, l’ajout de visualiseurs peut être utile pour s’assurer que WLT est configuré et fonctionne correctement. Elles peuvent être supprimées pour des performances de production, ou si, pour une raison quelconque, elles ne sont plus nécessaires, à l’aide de l’utilitaire Remove visualisers. Vous trouverez plus d’informations sur les visualiseurs dans la [documentation des outils](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Le plug-in OpenXR de réalité mixte fournit des fonctionnalités d’ancre de base via une implémentation du **ARAnchorManager** ARFoundation d’Unity. Pour connaître les principes de base de ARAnchors dans ARFoundation, consultez le [Manuel ARFoundation du gestionnaire d’ancrage AR](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>Création d’une expérience à l’échelle mondiale

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Type :** *WorldAnchor*

Pour les expériences réelles à l' **échelle mondiale** sur HoloLens qui permettent aux utilisateurs d’aller au-delà de 5 mètres, vous aurez besoin de nouvelles techniques au-delà de celles utilisées pour les expériences à l’échelle de la place. Une technique clé que vous allez utiliser consiste à créer une [ancre spatiale](../../../../design/coordinate-systems.md#spatial-anchors) pour verrouiller un cluster d’hologrammes précisément en place dans le monde physique, quel que soit le degré d’itinérance de l’utilisateur, puis [retrouvez ces hologrammes dans les sessions ultérieures](../../../../design/coordinate-systems.md#spatial-anchor-persistence).

Dans Unity, vous créez une ancre spatiale en ajoutant le composant **WorldAnchor** Unity à un GameObject.

### <a name="adding-a-world-anchor"></a>Ajout d’une ancre mondiale

Pour ajouter une ancre universelle, appelez `AddComponent<WorldAnchor>()` sur l’objet de jeu avec la transformation que vous souhaitez ancrer dans le monde réel.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Et c’est tout ! Cet objet de jeu sera désormais ancré à son emplacement actuel dans le monde physique : vous pouvez constater que ses coordonnées universelles s’ajustent légèrement au fil du temps pour garantir l’alignement physique. Reportez-vous à [chargement d’une ancre mondiale](#loading-a-worldanchor) pour rechercher cet emplacement d’ancrage dans une session d’application future.

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