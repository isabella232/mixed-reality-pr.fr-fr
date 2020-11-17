---
title: Vue d’ensemble du développement natif
description: Créez un moteur de réalité mixte DirectX en utilisant directement les API Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, rendu holographique, native, application native, WinRT, application WinRT, API de plateforme, moteur personnalisé, intergiciel, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 0d5e364fdb4faac73f28649f5c009823a74ac595
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679648"
---
# <a name="native-development-overview"></a>Vue d’ensemble du développement natif

![Logo de bannière Native](../images/native_logo_banner.png)

les moteurs 3D comme [Unity](../unity/unity-development-overview.md) ou [Unreal](../unreal/unreal-development-overview.md) ne sont pas les seuls chemins de développement de réalité mixte qui vous sont ouverts. Vous pouvez également créer des applications de réalité mixte en les codant directement sur les API de réalité mixte Windows avec DirectX 11 ou DirectX 12. En tirant parti de la plateforme, vous créez essentiellement votre propre infrastructure ou intergiciel (middleware). 

> [!IMPORTANT]
> Si vous avez un projet WinRT existant que vous souhaitez conserver, accédez à notre [documentation WinRT](creating-a-holographic-directx-project.md)principale. 

## <a name="development-checkpoints"></a>Points de contrôle de développement

Utilisez les points de contrôle suivants pour intégrer vos jeux et applications Unity dans le monde de la réalité mixte.

### <a name="1-getting-started"></a>1. Mise en route

Windows Mixed Reality prend en charge [deux types d’applications](../../design/app-views.md):
* **Applications en réalité mixte** (UWP ou Win32) qui utilisent l’API [HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou l' [API OpenXR](openxr.md) pour restituer une [vue immersive](../../design/app-views.md) à l’utilisateur qui remplit l’affichage du casque
* **applications 2D** (UWP) qui utilisent DirectX, XAML ou une autre infrastructure pour restituer des [vues 2D](../../design/app-views.md#2d-views) sur des ardoises dans la page d’hébergement de Windows Mixed Reality

Les différences entre le développement DirectX pour les [vues 2D et les vues immersives](../../design/app-views.md) concernent principalement le rendu holographique et l’entrée spatiale. Le [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) de votre application UWP ou le HWND de votre application Win32 sont requis et restent en grande partie les mêmes. Il en va de même pour les API WinRT qui sont disponibles pour votre application. Toutefois, vous devez utiliser un sous-ensemble différent de ces API pour tirer parti des fonctionnalités holographiques. Par exemple, le utilise permutation et le frame présent sont gérés par le système pour les applications holographiques afin d’activer une boucle de frame de prédiction de pose.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Fonctionnalités principales

Les applications Windows Mixed Reality utilisent les API suivantes pour créer des expériences de [réalité mixte](../../discover/mixed-reality.md) pour HoloLens et d’autres casques immersifs :

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

Vous pouvez développer avec OpenXR sur HoloLens 2 ou un casque immersif Windows Mixed Reality sur le bureau.  Si vous n’avez pas accès à un casque, vous pouvez utiliser l' [émulateur HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) à la place.

## <a name="whats-next"></a>Quelle est l’étape suivante ?

Le travail d’un développeur n’est jamais terminé, en particulier lorsqu’il s’agit d’apprendre un nouvel outil ou kit SDK. Les sections suivantes peuvent vous amener dans des domaines qui vont au-delà de la documentation niveau débutant que vous connaissez déjà, et vous fournir des ressources utiles si vous êtes bloqué. Notez que ces rubriques et ressources ne sont pas listées dans un ordre séquentiel particulier. N’hésitez donc pas à vous y plonger et à les explorer !

### <a name="additional-resources"></a>Ressources supplémentaires

Si vous envisagez de monter en charge votre jeu OpenXR, consultez les liens ci-dessous :

* [Bonnes pratiques sur OpenXR](openxr-best-practices.md)
* [Performances OpenXR](openxr-performance.md)
* [Résolution des problèmes OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>Voir aussi
* [Modèle d’application](../../design/app-model.md)
* [Vues d’applications](../../design/app-views.md)
