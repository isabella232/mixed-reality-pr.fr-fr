---
title: Boîte de dialogue de configuration MRTK
description: Configurer MRTK dans le projet Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345092"
---
# <a name="mrtk-project-configuration-dialog"></a>Boîte de dialogue de configuration de projet MRTK

La boîte de dialogue de configuration MRTK s’affiche lorsque Unity charge un projet et détermine qu’une ou plusieurs options de configuration nécessitent l’attention du développeur.

![Appliquer ultérieurement ignorer](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Pour appliquer les modifications, cliquez sur le bouton **appliquer** . Le bouton **ultérieur** diffère les modifications jusqu’à ce que le projet soit rechargé à une date ultérieure.

> [!NOTE]
> La boîte de dialogue de configuration s’affiche à présent si un ou plusieurs des paramètres recommandés restent désactivés. Pour éviter ce problème, appliquez les options souhaitées, puis relancez la boîte de dialogue via les utilitaires de la **réalité mixte du kit**  >    >  de **configuration** , puis cliquez sur **Ignorer**. Cela empêchera la boîte de dialogue de configuration de réapparaître automatiquement.

## <a name="common-settings"></a>Paramètres communs

Toutes les cibles de build partagent une collection d’options communes.

![Paramètres courants](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forcer la sérialisation des éléments de texte et activer les fichiers de métadonnées visibles

Ces paramètres permettent de simplifier l’utilisation des projets Unity et des systèmes de contrôle de code source (par ex. git).

### <a name="enable-vr-supported"></a>Activer VR pris en charge

**Unity 2018**

Configure les options de la réalité virtuelle prise en charge et du SDK Virtual Reality dans les paramètres du **lecteur**  >  **paramètres XR**.

### <a name="set-single-pass-instanced-rendering-path"></a>Définir le chemin de rendu de l’instance à passage unique

Configure les paramètres du **lecteur**  >  **XR** le  >  **mode de rendu stéréo** sur **une instance à passage unique**.

### <a name="set-default-spatial-awareness-layer"></a>Définir la couche de sensibilisation spatiale par défaut

Enregistre la sensibilisation spatiale en tant que couche 31 pour permettre une configuration simple et cohérente des options raycast et physique.

### <a name="audio-spatializer"></a>Spatializer audio

Les spatializers audio sont les composants qui déverrouillent la puissance du son spatial et de l’audio positionnel pour rendre les expériences de la réalité mélangée véritablement immersives.

> [!NOTE]
> La définition du Spatializer audio sur aucun désactive les fonctionnalités audio positionnelles.

#### <a name="common-spatializers"></a>Spatializers courantes

- Microsoft Spatializer

Microsoft a fourni Spatializer qui prend en charge l’utilisation de l’accélération matérielle sur HoloLens 2.

Ce Spatializer est disponible via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) et [GitHub](https://github.com/microsoft/spatialaudio-unity).

Pour plus d’informations sur Microsoft Spatializer, consultez la [documentation sur le son spatial](/windows/mixed-reality/spatial-sound-in-unity).

- MS HRTF Spatializer

Microsoft Windows Spatializer fourni par Unity dans le cadre des packages Windows Mixed Reality et Windows XR Platform.

- Resonance audio

Spatializer multiplateforme de Google, fournie par Unity.

Pour plus d’informations, consultez le site de [documentation audio](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) sur la résonance.

## <a name="universal-windows-platform-settings"></a>Paramètres de plateforme Windows universelle

![Paramètres UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Fonctionnalités UWP

Active des fonctionnalités d’application spécifiques pour plateforme Windows universelle application. Ces fonctionnalités permettent à la plateforme d’informer et de demander l’autorisation d’activer des fonctionnalités spécifiques.

- Microphone

  Permet la capture du son via le microphone.

- Client Internet

  Active la prise en charge de l’accès aux ressources sur Internet.

- Perception spatiale

  Active la prise en charge de l’environnement réel.

- Point de regard

  **Unity 2019,3 et versions ultérieures**

  Active la prise en charge du suivi de l’oeil de l’utilisateur.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Éviter le blocage de Unity « PlayerSettings. graphicsJob »

**Unity 2019,3 et versions ultérieures**

Dans la dernière version de Unity 2019, lorsque l’option « travaux graphiques » est activée, l’application se bloque lors du déploiement sur un HoloLens 2.
Ce paramètre est activé par défaut dans Unity : si ce bogue existe (voir le [bogue Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), le configurateur définit par défaut les tâches graphiques sur « false » (ce qui permet aux applications déployées sur HoloLens 2 de ne pas se bloquer).

## <a name="android-settings"></a>Paramètres Android

Paramètres de configuration pour la prise en charge des applications AR sur des appareils Android.

![Paramètres Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Désactiver le rendu multithread

Désactive les **paramètres du lecteur**  >  **autres paramètres** de  >  **rendu multithread** comme requis par la prise en charge des fournisseurs d’appareils Android.

### <a name="set-minimum-api-level"></a>Définir le niveau d’API minimal

Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **niveau d’API minimal** pour appliquer la configuration de système d’exploitation requise pour les applications AR.

## <a name="ios-settings"></a>Paramètres iOS

Paramètres de configuration pour la prise en charge des applications AR sur des appareils iOS.

![Paramètres iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Définir la version requise du système d’exploitation

Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **ciblent la version IOS minimale** pour appliquer la configuration de système d’exploitation requise pour les applications AR.

### <a name="set-required-architecture"></a>Définir l’architecture requise

Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **architecture** pour appliquer les spécifications de plateforme pour les applications AR.

### <a name="set-camera-usage-descriptions"></a>Définir les descriptions de l’utilisation de l’appareil photo

Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **Description de l’utilisation de l’appareil photo** utilisée pour demander l’autorisation d’utiliser l’appareil photo de l’appareil.