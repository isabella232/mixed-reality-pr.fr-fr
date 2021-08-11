---
title: Expériences partagées dans Unity
description: Apprenez à partager les mêmes hologrammes entre plusieurs utilisateurs dans une application Unity avec des ancres spatiales Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Partage, ancrer, WorldAnchor, MR partageant 250, WorldAnchorTransferBatch, SpatialPerception, Azure, ancres spatiales Azure, ASA, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: b9fdd09740dc6197c46a2d017f61e97898f213cd44bb504cbbf306f6a7ae21ec
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195921"
---
# <a name="shared-experiences-in-unity"></a>Expériences partagées dans Unity

une expérience partagée permet à plusieurs utilisateurs, chacun disposant de leurs propres HoloLens, iOS ou Android device, d’afficher et d’interagir de manière collective avec le même hologramme. les Hologrammes sont positionnés à un point fixe dans l’espace via le partage d’ancrage spatial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

les <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> créent des ancres spatiales durables sur le cloud, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android.  En partageant une ancre spatiale commune sur plusieurs appareils, chaque utilisateur peut voir le contenu affiché par rapport à cette ancre dans le même emplacement physique. 

vous pouvez également utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour la persistance d’hologrammes asynchrones sur des appareils HoloLens, iOS et Android.  En partageant une ancre spatiale Cloud durable, plusieurs appareils peuvent observer le même hologramme persistant dans le temps, même si ces appareils ne sont pas présents simultanément.

Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.

Une fois les ancres spatiales Azure configurées, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.

## <a name="local-anchor-transfers"></a>Transferts d’ancrage locaux

dans les situations où vous ne pouvez pas utiliser d’ancres spatiales Azure, les [transferts d’ancrage locaux](../../out-of-scope/local-anchor-transfers-in-unity.md) permettent à un appareil HoloLens d’exporter une ancre afin qu’une deuxième HoloLens puisse l’importer.  Cette approche n’est pas prise en charge sur les appareils iOS et Android, et fournit un rappel d’ancrage moins fiable que les ancres spatiales Azure.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des fonctionnalités de la plateforme de réalité mixte et des API. À partir de là, vous pouvez passer à la section suivante :

> [!div class="nextstepaction"]
> [Appareil photo localisable](locatable-camera-in-unity.md)

Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :

> [!div class="nextstepaction"]
> [déployez sur HoloLens ou Windows Mixed Reality des casques immersifs](../platform-capabilities-and-apis/using-visual-studio.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#3-advanced-features) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Expériences partagées dans Mixed Reality](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a>