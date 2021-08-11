---
title: Vue d’ensemble du développement natif
description: découvrez comment créer un moteur de réalité mixte DirectX en utilisant directement les api Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, rendu holographique, native, application native, WinRT, application WinRT, API de plateforme, moteur personnalisé, intergiciel, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 056cb0c07002cb319e8acadf66e7f59650f5e00413440d6ad0103aa8ee936400
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200158"
---
# <a name="native-development-overview"></a>Vue d’ensemble du développement natif

![Logo de bannière Native](../images/native_logo_banner.png)

les moteurs 3D comme [Unity](../unity/unity-development-overview.md) ou [Unreal](../unreal/unreal-development-overview.md) ne sont pas les seuls chemins de développement de réalité mixte qui vous sont ouverts. vous pouvez également créer des applications de réalité mixte à l’aide des api Windows Mixed Reality avec directx 11 ou directx 12. En accédant à la source de la plateforme, vous créez essentiellement votre propre infrastructure ou intergiciel. 

> [!IMPORTANT]
> Si vous avez un projet WinRT existant que vous souhaitez conserver, accédez à notre [documentation WinRT](creating-a-holographic-directx-project.md)principale. 

## <a name="development-checkpoints"></a>Points de contrôle de développement

Utilisez les points de contrôle suivants pour intégrer vos jeux et applications Unity dans le monde de la réalité mixte.

### <a name="1-getting-started"></a>1. Mise en route

Windows Mixed Reality prend en charge [deux types d’applications](../../design/app-views.md):
* Applications UWP ou de **réalité mixte** Win32 qui utilisent l' [API HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou l' [API OpenXR](openxr.md) pour afficher un [affichage immersif](../../design/app-views.md) qui remplit l’affichage du casque
* **applications 2d** (UWP) qui utilisent DirectX, XAML ou une autre infrastructure pour restituer des [vues 2d](../../design/app-views.md#2d-views) sur des ardoises dans la Windows Mixed Reality page d’hébergement

Les différences entre le développement DirectX pour les [vues 2D et les vues immersives](../../design/app-views.md) concernent principalement le rendu holographique et l’entrée spatiale. Le [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) de votre application UWP ou le HWND de votre application Win32 sont requis et restent en grande partie les mêmes. Il en va de même pour les API WinRT qui sont disponibles pour votre application. Toutefois, vous devez utiliser un sous-ensemble différent de ces API pour tirer parti des fonctionnalités holographiques. Par exemple, le système pour les applications holographiques gère le utilise permutation et le frame présent pour activer une boucle de frames prédite.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Fonctionnalités principales

les applications Windows Mixed Reality utilisent les api suivantes pour créer des expériences de [réalité mixte](../../discover/mixed-reality.md) pour HoloLens et d’autres casques immersifs :

|  Fonctionnalité  |  Utilité  |
| --- | --- |
| [Pointage du regard](../../design/gaze-and-commit.md) | Autorisez des utilisateurs à cibler des hologrammes en les regardant |
| [Mouvement](../../design/gaze-and-commit.md#composite-gestures) | Ajouter des actions spatiales à vos applications |
| [Rendu holographique](../platform-capabilities-and-apis/rendering.md) | Dessinez un hologramme à un endroit précis dans le monde autour de vos utilisateurs |
| [Contrôleur de mouvement](../../design/motion-controllers.md) | Permettez aux utilisateurs de prendre des mesures dans vos environnements de réalité mixte |
| [Mappage spatial](../../design/spatial-mapping.md) | Mappez votre espace physique avec une superposition de maillage virtuel afin de marquer les limites de votre environnement |
| [Voice](../../design/voice-input.md) | Capturez des mots clés, des expressions et une dictée à partir de vos utilisateurs |
 
> [!NOTE]
> Vous trouverez des fonctionnalités de base à venir et en développement dans la documentation de la feuille de [route](openxr.md#roadmap) OpenXR.

### <a name="3-deploying-and-testing"></a>3. déploiement et test

vous pouvez développer sur un bureau à l’aide de OpenXR sur un HoloLens 2 ou Windows Mixed Reality un casque immersif.  si vous n’avez pas accès à un casque, vous pouvez utiliser le [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou le [simulateur Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) à la place.

## <a name="whats-next"></a>Quelle est l’étape suivante ?

Le travail d’un développeur n’est jamais terminé, en particulier lorsqu’il s’agit d’apprendre un nouvel outil ou SDK. Les sections suivantes peuvent vous permettre d’aller au-delà des éléments de niveau débutant que vous avez déjà effectués. Ces rubriques et ressources ne sont pas dans un ordre séquentiel. n’hésitez pas à vous plonger dans l’exploration.

### <a name="additional-resources"></a>Ressources supplémentaires

Si vous envisagez de monter en charge votre jeu OpenXR, consultez les liens ci-dessous :

* [Bonnes pratiques sur OpenXR](openxr-best-practices.md)
* [Performances OpenXR](openxr-performance.md)
* [Résolution des problèmes OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>Voir aussi
* [Modèle d’application](../../design/app-model.md)
* [Vues d’applications](../../design/app-views.md)