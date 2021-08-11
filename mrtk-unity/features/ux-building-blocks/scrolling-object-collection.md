---
title: Défilement de la collection d’objets
description: Types de menu vue d’ensemble MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, objet de défilement
ms.openlocfilehash: a97ea9919cf484cf5240dde027f38baca37ba9570588bca032bee9c116aed873
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221750"
---
# <a name="scrolling-object-collection"></a>Défilement de la collection d’objets

![Défilement de la collection d’objets](../images/scrolling-collection/ScrollingCollection_Main.jpg)

La collection d’objets de défilement MRTK est un composant d’expérience utilisateur qui permet de faire défiler le contenu 3D dans une zone affichable contenue. Le mouvement de défilement peut être déclenché par une interaction d’entrée near ou FAR et par une pagination discrète. Il prend en charge les objets interactifs et non interactifs.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Prise en main de la collection d’objets de défilement

### <a name="setting-up-the-scene"></a>Configuration de la scène

1. Créer une nouvelle scène Unity.
1. ajoutez MRTK à la scène en accédant à la **réalité mixte Shared Computer Toolkit**  >  **ajouter à la scène et configurer**.

### <a name="setting-up-the-scrolling-object"></a>Configuration de l’objet de défilement

1. Créez un objet de jeu vide dans la scène et remplacez sa position par (0, 0, 1).
1. Ajoutez un composant de [collection d’objets de défilement](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) à l’objet de jeu.

    Lorsque la collection d’objets de défilement est ajoutée, un conflit de cases et un composant [touchable near-interaction](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) sont automatiquement attachés à l’objet de jeu racine. Ces composants permettent à l’objet Scroll d’écouter des événements d’entrée d’interaction near et Far, comme un pointeur tactile ou un clic.  

    La collection d’objets de défilement MRTK comporte deux éléments importants qui sont créés en tant qu’objets de jeu enfants dans la hiérarchie d’objets de défilement racine :
    * `Container` -Tous les objets de contenu de défilement doivent être des enfants de l’objet de jeu de conteneurs.
    * `Clipping bounds` -Si le masquage du contenu de défilement est activé, l’élément de limites de découpage garantit que seul le contenu défilant à l’intérieur de ses limites est visible. L’objet de jeu limites de découpage a deux composants : un conflit de case désactivé et une [zone de découpage](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).

![Défilement des éléments de la collection d’objets](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Ajout de contenu à l’objet de défilement

La collection d’objets de défilement peut être combinée avec une [collection d’objets Grid](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) pour mettre en forme le contenu dans une grille d’éléments alignés dont la taille et l’espacement sont uniformes.

1. Créez un objet de jeu vide en tant qu’enfant du conteneur de défilement.
1. Ajoutez un composant de collection d’objets Grid à l’objet de jeu.
1. Pour un défilement vertical à une seule colonne, sous l’onglet inspecteur, configurez la collection d’objets Grid comme suit :
    * **Nombre de colonnes**: 1
    * **Disposition**: colonne puis ligne
    * **Ancrer**: en haut à gauche
1. Modifiez la **largeur** et la **hauteur** des cellules en fonction des dimensions des objets de contenu.
1. Ajoutez les objets de contenu en tant qu’enfants de l’objet Grid.
1. Appuyez sur **mettre à jour la collection**.

![Disposition de la grille](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Tout élément de contenu de défilement doit utiliser le [nuanceur standard MRTK](../rendering/MRTK-standard-shader.md) pour que l’effet de découpage sur la zone affichable fonctionne correctement.

> [!NOTE]
> Si le masquage du contenu de défilement est activé, la collection d’objets de défilement ajoute un composant d' [instance de matériau](../rendering/material-instance.md) à tous les objets de contenu auxquels un convertisseur est attaché. Ce composant est utilisé pour gérer la durée de vie des matériaux instanciés et améliorer les performances de la mémoire.

### <a name="configuring-the-scrolling-viewable-area"></a>Configuration de la zone affichable du défilement

1. Pour le défilement vertical au sein d’une seule colonne d’objets, dans l’onglet inspecteur, configurez la collection d’objets de défilement comme suit :
    * **Cellules par niveau**: 1
    * Choisir le nombre de **niveaux par page** en fonction du nombre de lignes visibles souhaité
1. Modifiez la **largeur**, la **hauteur** et la **profondeur** des cellules de la page en fonction des dimensions des objets de contenu.

Notez que les objets de contenu situés en dehors de la zone affichable par défilement sont désormais désactivés, tandis que les objets qui croisent le filaire de défilement peuvent être partiellement masqués par la primitive de découpage.

![Zone affichable](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Test de la collection d’objets de défilement dans l’éditeur

1. Appuyez sur Lire et maintenez la barre Espace enfoncée pour afficher une main de simulation d’entrée.
1. Déplacez la main jusqu’à ce que le conflit de détourage ou le contenu interactif de défilement soit activé et déclenchez le mouvement de défilement en cliquant et en faisant glisser le curseur vers le haut et vers le haut avec la souris gauche.

## <a name="controlling-the-scrolling-object-from-code"></a>Contrôle de l’objet de défilement à partir du code

La collection d’objets de défilement MRTK expose quelques méthodes publiques qui permettent de déplacer le conteneur de défilement en alignant sa position en fonction de la `pagination` Configuration des propriétés.

Un exemple d’accès à l’interface de pagination de la collection d’objets de défilement peut être utilisé dans le ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` dossier. L’exemple de script de [pagination avec défilement](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) peut être lié à une collection d’objets de défilement existante dans la scène. Le script peut ensuite être référencé par des composants de scène exposant des événements Unity (par exemple, le [bouton MRTK](button.md)).

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }
}
```

## <a name="scrolling-object-collection-properties"></a>Propriétés de la collection d’objets de défilement

| Général          | Description                                   |
| :--------------- | :-------------------------------------------- |
| Sens de défilement | Sens dans lequel le contenu doit défiler. |

| Pagination     | Description                                                                                               |
| :------------- | :-------------------------------------------------------------------------------------------------------- |
| Cellules par niveau | Nombre de cellules d’une ligne dans l’affichage de défilement vers le haut ou le nombre de cellules dans une colonne dans l’affichage de défilement de gauche à droite. |
| Niveaux par page | Nombre de niveaux visibles dans la zone de défilement.                                                            |
| Cellule de page      | Dimensions de la cellule de pagination.                                                                        |

| Paramètres avancés           | Description                                                                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mode d’édition de masque              | Modes de modification permettant de définir les limites de masquage de la zone de découpage. 'Auto’utilise automatiquement les valeurs de pagination. 'Manual’permet la manipulation directe de l’objet de zone de découpage. |
| Mode d’édition d’un conflit          | Modes de modification permettant de définir les limites de collision d’interaction de défilement. 'Auto’utilise automatiquement les valeurs de pagination. « Manual » permet une manipulation directe du conflit.     |
| Peut faire défiler                  | Active/désactive le défilement avec une interaction proche/éloignée.                                                                                                                      |
| Utiliser lors du pré-rendu           | Indique si le scrollingObjectCollection utilise l’événement OnPreRender de l’appareil photo pour gérer la visibilité du contenu.                                                          |
| Courbe de pagination            | Courbe d’animation pour la pagination.                                                                                                                                            |
| Longueur de l’animation            | Durée (en secondes) nécessaire à l’évaluation de PaginationCurve.                                                                                                 |
| Seuil de défilement Delta à la main | Distance, en mètres, du pointeur actuel peut se déplacer le long de la direction de défilement avant de déclencher un glissement de défilement.                                                        |
| Distance avant pression        | Distance, en mètres, pour positionner un plan XY local utilisé pour vérifier si une interaction tactile a démarré à l’avant de la vue de défilement.                                           |
| Seuil de mise en sortie           | Retirez le montant, en mètres, des limites de défilement nécessaires pour passer de la touche Touch engagée à la version finale.                                                                |

| Vélocité            | Description                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------- |
| Type de vélocité    | Type souhaité de retrait de vitesse pour le défilement.                                                      |
| Multiplicateur de vélocité | Quantité de vélocité (supplémentaire) à appliquer au défilement.                                                       |
| Vélocité de vélocité     | Quantité de retrait appliqué à la vélocité.                                                                  |
| Multiplicateur de rebond   | Multiplicateur pour ajouter plus de rebond au défilant d’une liste lors de l’utilisation de l’atténuation par image ou de la dépassement par élément. |

| Options de débogage         | Description                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| Masque activé          | Mode de visibilité du contenu de défilement. La valeur par défaut masque tous les objets en dehors de la zone d’affichage de défilement. |
| Afficher les plans de seuil | Si la valeur est true, l’éditeur restitue les plans de seuil de libération tactile autour des limites de défilement.            |
| Pagination de débogage      | Utilisez cette section pour déboguer la pagination de défilement pendant l’exécution.                                             |

| Événements              | Description                                                                                                                   |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| En cas de clic            | Déclenché lorsque le conflit d’arrière-plan de défilement ou l’un de ses contenus interactifs reçoit un clic.                             |
| Démarrage tactile    | Déclenché lorsque le conflit d’arrière-plan de défilement ou l’un de ses contenus interactifs reçoit une pression tactile proche de l’interaction.            |
| À la saisie tactile terminée      | Déclenché lorsqu’une interaction tactile active est terminée lorsque le pointeur d’interaction proche traverse un plan de seuil de mise en sortie. |
| Au démarrage du momentum | Déclenché lorsque le curseur de défilement commence à se déplacer par interaction, atténuation de vélocité ou pagination.                            |
| À la fin de l’inertie   | Déclenché lorsque le conteneur de défilement cesse de se déplacer par interaction, atténuation de vélocité ou pagination.                             |

## <a name="scrolling-example-scene"></a>Exemple de scène de défilement

La scène de l’exemple **ScrollingObjectCollection. Unity** est composée de 3 exemples de défilement, chacun avec une configuration d’atténuation de vélocité différente. L’exemple de scène contient des murs pour montrer le comportement de placement de la surface qui est désactivé par défaut dans la hiérarchie. L’exemple de scène se trouve sous le ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` dossier.

![Exemple de scène de collection d’objets de défilement](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Exemple de défilement prefabs

Pour plus de commodité, deux prefabs de collection d’objets de défilement peuvent être utilisés. L’exemple prefabs se trouve dans le ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` dossier.

![Défilement de la collection d’objets prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Voir aussi

* [Primitive de découpage](../rendering/clipping-primitive.md)
* [Instance de matériau](../rendering/material-instance.md)
* [Nuanceur standard](../rendering/MRTK-standard-shader.md)
* [Collection d’objets](object-collection.md)
