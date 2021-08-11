---
title: Ancres spatiales partagées dans DirectX
description: découvrez comment synchroniser deux HoloLens appareils en partageant des ancres spatiales locales et Azure dans des applications DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, synchroniser, ancrage spatial, transfert, multijoueur, vue, scénario, procédure pas à pas, exemple de code, azure, ancres spatiales azure, ASA
ms.openlocfilehash: df78d9e2477fe377d61d2f2c13fc35e0a25b0b2cc37eeb883a69d2041fe42f9b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193543"
---
# <a name="shared-experiences-in-directx"></a>Expériences partagées dans DirectX

> [!NOTE]
> Cet article s’applique aux API natives WinRT héritées.  Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](../native/openxr-getting-started.md)**.

une expérience partagée consiste à utiliser plusieurs utilisateurs avec leur propre HoloLens, iOS ou Android, à afficher et interagir de manière collective avec le même hologramme. L’hologramme est positionné à un point fixe dans l’espace à l’aide du partage d’ancrage spatial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

vous pouvez utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer des ancres spatiales durables dans le cloud, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android.  En partageant une ancre spatiale commune sur plusieurs appareils, chaque utilisateur peut voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.  Cette technique autorise les expériences partagées en temps réel.

vous pouvez également utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour la persistance d’hologrammes asynchrones sur des appareils HoloLens, iOS et Android.  En partageant une ancre spatiale Cloud durable, plusieurs appareils peuvent observer le même hologramme persistant dans le temps, même si ces appareils ne sont pas présents simultanément.

pour commencer à créer des expériences partagées dans votre application HoloLens, essayez le guide de démarrage rapide de 5 minutes sur les <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">ancres spatiales Azure HoloLens</a>.

Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">créer et localiser des ancres sur HoloLens</a>.  Les procédures pas à pas sont également disponibles pour <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android et iOS</a> , ce qui vous permet de partager les mêmes ancres sur tous les appareils.

## <a name="local-anchor-transfers"></a>Transferts d’ancrage locaux

dans les situations où vous ne pouvez pas utiliser les ancres spatiales Azure, les [transferts d’ancrage locaux](../../out-of-scope/local-anchor-transfers-in-directx.md) permettent à un appareil HoloLens d’exporter une ancre pour qu’elle soit importée par un deuxième HoloLens appareil.  Cette approche offre un rappel d’ancrage moins fiable que les ancres spatiales Azure, et les appareils iOS et Android ne sont pas pris en charge par cette approche.

## <a name="see-also"></a>Voir aussi

* [Expériences partagées dans Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour HoloLens</a>