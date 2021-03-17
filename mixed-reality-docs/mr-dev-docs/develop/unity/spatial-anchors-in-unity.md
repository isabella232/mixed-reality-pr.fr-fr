---
title: Ancres spatiales dans Unity
description: Découvrez comment créer, stocker et récupérer des ancres spatiales dans des applications de réalité mixte Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, ancres spatiales, magasin d’ancrage, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623619"
---
# <a name="spatial-anchors-in-unity"></a>Ancres spatiales dans Unity

Les ancres spatiales enregistrent les hologrammes dans un espace réel entre les sessions d’application. Une fois enregistrées dans le magasin d’ancres HoloLens, elles peuvent être recherchées et chargées dans différentes sessions et constituent une solution de secours idéale en l’absence de connectivité Internet.

> [!IMPORTANT]
> Les ancres locales sont stockées sur l’appareil, alors que les ancres spatiales Azure sont stockées dans le cloud. Si vous envisagez d’utiliser les services cloud Azure pour stocker vos ancres, nous avons créé un guide qui vous aidera à intégrer [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors). Notez que vous pouvez avoir des ancres locales et Azure dans le même projet sans conflit.

## <a name="understanding-anchors"></a>Comprendre les points d’ancrage

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>Utilisation de AnchorStore

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement Unity que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte. À partir de là, vous pouvez passer au module suivant :

> [!div class="nextstepaction"]
> [Mappage spatial](spatial-mapping-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Persistance d’ancrage spatial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a>
* [Échelle de l’expérience](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Étape spatiale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Suivi des pertes dans Unity](tracking-loss-in-unity.md)
* [Ancres spatiales](../../design/spatial-anchors.md)
* [Expériences partagées dans Unity](shared-experiences-in-unity.md)