---
title: Verrouillage universel et ancrages spatiaux dans Unity
description: Découvrez comment utiliser les outils de verrouillage universel et les ancres spatiales dans les applications de réalité mixte Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: unity, ancres spatiales, magasin d’ancrages, HoloLens, casque de réalité mixte, casque de réalité windows mixte, casque de réalité virtuelle, outils de verrouillage universel, hologrammes
ms.openlocfilehash: 34ef74ab968bff04188b1010eb4c863fd73d76ee6b1dd8a0bd89c7d4232a2be9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208846"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Verrouillage universel et ancrages spatiaux dans Unity

![Image du héros de l’outil de verrouillage universel](images/wlt-img-01.jpeg)

La mise en place de vos hologrammes, le déplacement avec vous ou, dans certains cas, la position par rapport à d’autres hologrammes est une partie importante de la création d’applications de réalité mixte. Cet article vous guide tout au long de la solution recommandée à l’aide des outils de verrouillage universel, mais nous aborderons également la configuration manuelle des ancres spatiales dans vos projets Unity. Avant de passer à un code, il est important de comprendre comment Unity gère l’espace de coordonnées et les ancres dans son propre moteur.

## <a name="world-scale-coordinate-systems"></a>Systèmes de coordonnées à l’échelle mondiale

Aujourd’hui, lors de l’écriture de jeux, d’applications de visualisation de données ou d’applications de réalité virtuelle, l’approche classique consiste à établir un **système de coordonnées universel** unique sur lequel toutes les autres coordonnées peuvent être mappées de manière fiable. Dans cet environnement, vous pouvez toujours trouver une transformation stable qui définit une relation entre deux objets dans ce monde. Si vous n’avez pas déplacé ces objets, leurs transformations relatives restent toujours les mêmes. Ce type de système de coordonnées global est facile à trouver lors du rendu d’un monde purement virtuel où vous connaissez toute la géométrie à l’avance. Aujourd’hui, les applications de la mise à l’échelle de la salle établissent généralement ce type de système de coordonnées à l’échelle de la pièce, avec son origine sur le plancher.

en revanche, un appareil de réalité mixte non attaché, tel que HoloLens, a une compréhension dynamique pilotée par les capteurs du monde, en ajustant continuellement ses connaissances au fil du temps de l’utilisateur lorsqu’il parcourt de nombreux compteurs à travers l’ensemble d’un étage d’un bâtiment. Dans le cas d’une expérience à l’échelle mondiale, si vous avez placé tous vos hologrammes dans un système de coordonnées rigides naïve, ces hologrammes finissent par être décomposés au fil du temps, soit en se basant sur le monde, soit de l’un par rapport à l’autre.

Par exemple, le casque peut considérer deux endroits du monde comme étant séparés de 4 mètres, puis affiner cette compréhension, en sachant que les emplacements sont en fait de 3,9 mètres de distance. Si ces hologrammes avaient initialement été placés à 4 mètres en un seul système de coordonnées rigides, l’un d’eux présenterait toujours 0,1 mètres du monde réel.

Vous pouvez placer manuellement les **ancres spatiales** dans Unity pour maintenir la position d’un hologramme dans le monde physique lorsque l’utilisateur est mobile. Toutefois, cela sacrifie l’auto-cohérence dans le monde virtuel. Les différentes ancres se déplacent constamment les unes par rapport aux autres et se déplacent également dans l’espace de coordonnées global. Dans ce scénario, des tâches simples telles que la mise en page deviennent difficiles et la simulation physique pose problème.

Les **outils de verrouillage universel** vous offrent le meilleur des deux mondes, en stabilisant un système de coordonnées rigides unique à l’aide d’une alimentation interne d’ancres spatiales réparties sur l’ensemble de la scène virtuelle à mesure que l’utilisateur se déplace. Les outils analysent les coordonnées de l’appareil photo et les ancres spatiales de chaque image. Au lieu de modifier les coordonnées de tout le monde pour compenser les corrections dans les coordonnées de la tête de l’utilisateur, les outils corrigent simplement les coordonnées de l’en-tête à la place.

## <a name="choosing-your-world-locking-approach"></a>Choix de votre approche de verrouillage universel

* **Nous vous recommandons** d’utiliser les **outils de verrouillage universel** pour tous vos besoins en matière de positionnement d’hologramme. 
    * Les outils de verrouillage universel offrent un système de coordonnées stable qui réduit les incohérences visibles entre les marqueurs virtuels et réels. En d’autres termes, il verrouille l’ensemble de la scène avec un pool partagé d’ancres, au lieu de verrouiller chaque groupe d’objets avec la propre ancre individuelle du groupe.
* **pour unity 2019/2020 utilisant OpenXR ou le plug-in Windows XR**, vous devez utiliser **ARAnchorManager**
* **Pour les versions Unity plus anciennes ou les projets WSA** , vous devez utiliser **WorldAnchor**

## <a name="setting-up-world-locking"></a>Configuration du verrouillage universel 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>Verrouillage de monde persistant

Les ancres spatiales enregistrent les hologrammes dans un espace réel entre les sessions d’application. une fois enregistrées dans le magasin d’ancrage HoloLens, elles peuvent être recherchées et chargées dans différentes sessions et constituent une solution de secours idéale en l’absence de connectivité internet.

> [!IMPORTANT]
> Les ancres locales sont stockées sur l’appareil, alors que les ancres spatiales Azure sont stockées dans le cloud. Si vous envisagez d’utiliser les services cloud Azure pour stocker vos ancres, nous avons créé un guide qui vous aidera à intégrer [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors). Notez que vous pouvez avoir des ancres locales et Azure dans le même projet sans conflit.

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>Partage des espaces de coordonnées 

Si vous souhaitez partager un espace de coordonnées universel, consultez notre documentation complète sur l' [expérience partagée](shared-experiences-in-unity.md).

Notez que les ancres spatiales Azure ne sont pas encore prises en charge directement dans les outils de verrouillage universel, et les expériences partagées vous obligent donc à créer manuellement des ancres spatiales.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement Unity que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte. À partir de là, vous pouvez passer au module suivant :

> [!div class="nextstepaction"]
> [Mappage spatial](spatial-mapping-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Présentation des outils de verrouillage universel](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [Guides de démarrage rapide](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [Tutoriels](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [Exemples](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [Persistance d’ancrage spatial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a>
* [Échelle de l’expérience](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Étape spatiale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Suivi des pertes dans Unity](tracking-loss-in-unity.md)
* [Ancres spatiales](../../design/spatial-anchors.md)
* [Expériences partagées dans Unity](shared-experiences-in-unity.md)
