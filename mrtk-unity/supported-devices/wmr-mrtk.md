---
title: Déploiement sur les appareils Hololens et WMR
description: Documentation pour créer et déployer des applications sur différents appareils.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Visual Studio
ms.openlocfilehash: ec66c6ccb8cf1c702fed804230f5cf3ca0526139
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852374"
---
# <a name="building-and-deploying-mrtk-uwp"></a>Génération et déploiement de MRTK (UWP)

Pour exécuter une application sur un appareil en tant qu’application autonome (pour HoloLens, Android, iOS, etc.), l’étape de génération et de déploiement doit être exécutée dans le projet Unity. La création et le déploiement d’une application qui utilise le MRTK ressemble à la création et au déploiement d’une autre application Unity. Il n’existe aucune instruction propre au MRTK. Lisez les informations ci-dessous pour obtenir des instructions détaillées sur la création et le déploiement d’une application Unity pour HoloLens. Pour en savoir plus sur la création de solutions pour d’autres plateformes, consultez la page sur la [publication de builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>Génération et déploiement de MRTK sur HoloLens 1, HoloLens 2 et WMR casques (UWP)

Vous trouverez des instructions sur la génération et le déploiement de **hololens 1** et **hololens 2** (UWP) dans la rubrique [création de votre application sur un appareil](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Ces étapes vous permettent également de déployer sur des **casques WMR**.

**Conseil :** Lors de la génération pour HoloLens 1, HoloLens 2 ou WMR, il est recommandé que les paramètres de build « version du kit de développement logiciel (SDK) cible » et « version de plateforme minimale » se présentent comme dans l’image ci-dessous :

![Fenêtre Build](../features/images/getting-started/BuildWindow.png)

Les autres paramètres peuvent être différents (par exemple, configuration de build/architecture/type de build, et d’autres peuvent toujours être modifiés dans la solution Visual Studio).

Vérifiez que la liste déroulante « Version cible du Kit de développement logiciel (SDK) » contient l’option « 10.0.18362.0 ». Si ce n’est pas le cas, [le SDK Windows le plus récent](https://developer.microsoft.com/windows/downloads/windows-10-sdk) doit être installé.

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 et HoloLens

Si une application HoloLens apparaît sous la forme d’un panneau 2D sur l’appareil, vérifiez que les paramètres suivants ont été configurés dans Unity 2019.3.x avant de déployer votre application UWP :

Si vous utilisez le XR hérité :

1. Accédez à Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)
1. Sous **XR Settings (Paramètres XR)** sous l’onglet UWP, vérifiez que l’option **Virtual Reality Supported (Réalité virtuelle prise en charge)** est activée et que le SDK **Windows Mixed Reality** a été ajouté aux SDK.
1. Générer et déployer dans Visual Studio

Si vous utilisez le plug-in XR :

1. Suivez les étapes décrites dans [Prise en main de XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Vérifiez que le profil de configuration est **DefaultXRSDKConfigurationProfile**
1. Accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), XR-Plugin Management (Gestion du plugin XR)** et vérifiez que **Windows Mixed Reality** est activé.
1. Générer et déployer dans Visual Studio

>[!IMPORTANT]
> Si vous utilisez Unity 2019.3.x, sélectionnez **ARM64** et non **ARM** comme architecture de build dans Visual Studio. Avec les paramètres Unity par défaut dans Unity 2019.3.x, une application Unity n’est pas déployée sur un HoloLens si ARM est sélectionné en raison d’un bogue Unity. Ce suivi peut être effectué dans le [dispositif de suivi des problèmes d’Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).
>
> Si l’architecture ARM est requise, accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)** , puis dans le menu **Other Settings (Autres paramètres)** , désactivez **Graphics Jobs (Travaux graphiques)** . Même si la désactivation de **Graphics Jobs (Travaux graphiques)** permettra à l’application de se déployer à l’aide de l’architecture de build ARM pour Unity 2019.3.x, ARM64 est recommandé.

## <a name="building-and-deploying-mrtk-standalone"></a>Génération et déploiement de MRTK (autonome)

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