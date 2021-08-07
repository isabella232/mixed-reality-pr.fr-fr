---
title: Déploiement sur des casques Hololens et WMR
description: Documentation pour créer et déployer des applications sur différents appareils.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Visual Studio
ms.openlocfilehash: 622c7ca4b9c527630b5677fe377d1d3108bdfe08c9dc616bfd4d3256b83b9ab0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209476"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>Déploiement sur des casques Hololens et WMR

il existe deux façons de déployer des applications générées avec MRTK sur votre appareil windows, la plateforme universels Windows (UWP) et la plateforme autonome. les applications générées pour HoloLens 1 ou HoloLens 2 doivent cibler uwp, tandis que les applications conçues pour les casques WMR peuvent cibler uwp ou autonome.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>génération et déploiement de MRTK sur HoloLens 1, HoloLens 2 et des casques WMR (UWP)

vous trouverez des Instructions sur la création et le déploiement de pour **HoloLens 1** et **HoloLens 2** (UWP) dans la rubrique [création de votre application sur un appareil](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Ces étapes vous permettent également de déployer sur des **casques WMR**.

> [!NOTE]
> lors du déploiement de votre application sur votre appareil dans Visual Studio, vous devez configurer Visual Studio légèrement différemment en fonction de l’appareil. Les configurations sont les suivantes :
>
>| Plateforme | Configuration | Architecture | Cible |
|---|---|---|---|
| HoloLens 2 | Release ou Master | ARM64 | Appareil |
| HoloLens 1 | Release ou Master | x86 | Appareil |
| Casques WMR | Release ou Master | x64 | Ordinateur local |

**Conseil :** lors de la génération pour HoloLens 1, HoloLens 2 ou WMR, il est recommandé que les paramètres de build « version du kit de développement logiciel (SDK) cible » et « version de plateforme minimale » se présentent comme dans l’image ci-dessous :

![Fenêtre Build](../features/images/getting-started/BuildWindow.png)

Les autres paramètres peuvent être différents (par exemple, configuration de build/architecture/type de build, et d’autres peuvent toujours être modifiés dans la solution Visual Studio).

Vérifiez que la liste déroulante « Version cible du Kit de développement logiciel (SDK) » contient l’option « 10.0.18362.0 ». Si ce n’est pas le cas, [le SDK Windows le plus récent](https://developer.microsoft.com/windows/downloads/windows-10-sdk) doit être installé.

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 et HoloLens

si une application HoloLens s’affiche sous la forme d’un panneau 2d sur l’appareil, assurez-vous que les paramètres suivants ont été configurés dans unity avant de déployer votre application UWP :

Si vous utilisez la prise en charge XR intégrée héritée (Unity 2019 uniquement) :

1. Accédez à Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)
1. Sous **XR Settings (Paramètres XR)** sous l’onglet UWP, vérifiez que l’option **Virtual Reality Supported (Réalité virtuelle prise en charge)** est activée et que le SDK **Windows Mixed Reality** a été ajouté aux SDK.
1. Générer et déployer dans Visual Studio

si vous utilisez les plug-ins OpenXR ou Windows XR :

1. Suivez les étapes décrites dans [Prise en main de XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Vérifiez que le profil de configuration est **DefaultXRSDKConfigurationProfile**
1. Accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), XR-Plugin Management (Gestion du plugin XR)** et vérifiez que **Windows Mixed Reality** est activé.
1. Générer et déployer dans Visual Studio

>[!IMPORTANT]
> Si vous utilisez Unity 2019.3.x, sélectionnez **ARM64** et non **ARM** comme architecture de build dans Visual Studio. Avec les paramètres Unity par défaut dans Unity 2019.3.x, une application Unity n’est pas déployée sur un HoloLens si ARM est sélectionné en raison d’un bogue Unity.
>
> Si l’architecture ARM est requise, accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)** , puis dans le menu **Other Settings (Autres paramètres)** , désactivez **Graphics Jobs (Travaux graphiques)** . Même si la désactivation de **Graphics Jobs (Travaux graphiques)** permettra à l’application de se déployer à l’aide de l’architecture de build ARM pour Unity 2019.3.x, ARM64 est recommandé.
>
> Ce problème a été résolu dans Unity 2019,4 et Unity 2020,3.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>Génération et déploiement de MRTK sur des casques WMR (autonomes)

Les versions autonomes de MRTK peuvent être utilisées sur des casques WMR. Une version autonome d’un casque WMR requiert d’effectuer les étapes supplémentaires suivantes :

> [!NOTE]
> Le SDK XR d’Unity prend également en charge les WMR natifs dans les builds autonomes, mais ne nécessite pas de plug-in WMR ou SteamVR. Ces étapes sont requises pour les XR hérités d’Unity.

1. Installer [Steam](https://store.steampowered.com/about/)
1. Installer [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. Installer le [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>Utiliser le plug-in WMR

1. Ouvrir Steam et rechercher le plug-in Windows Mixed Reality
    - Vérifiez que SteamVR est fermé avant de lancer le plug-in WMR. Le lancement du plug-in WMR a pour effet de lancer également SteamVR.
    - Vérifiez que le casque WMR est branché.

    ![Recherche de plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Sélectionnez **Lancer** pour lancer le plug-in Windows Mixed Reality pour le plug-in SteamVR.

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - SteamVR et le plug-in WMR démarrent et une nouvelle fenêtre d’état de suivi du casque WMR s’affiche.
    - Pour plus d’informations, consultez la [documentation sur l’utilisation de Steam avec Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).

        ![Apparence du lancement de WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. Dans Unity, avec votre scène MRTK ouverte, accédez à **File (Fichier) > Build Settings (Paramètres de build)**

1. Générer la scène
    - Sélectionnez **Ajouter une scène ouverte**
    - Assurez-vous que la plateforme est définie sur **Standalone (Autonome)** .
    - Sélectionnez **Build**.
    - Choisissez l’emplacement de la nouvelle build dans l’Explorateur de fichiers.

    ![Paramètres de build pour l’option Autonome](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Un nouvel exécutable Unity sera créé. Pour lancer votre application, sélectionnez l’exécutable Unity dans l’Explorateur de fichiers.

    ![Explorateur de fichiers dans Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Voir aussi

- [Support Android et iOS](using-ar-foundation.md)
- [Prise en charge de Leap Motion](leap-motion-mrtk.md)
- [Détection des fonctionnalités de plateforme](detecting-platform-capabilities.md)
