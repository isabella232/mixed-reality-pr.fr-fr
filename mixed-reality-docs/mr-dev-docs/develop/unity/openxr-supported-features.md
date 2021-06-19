---
title: Fonctionnalités prises en charge par le plug-in OpenXR dans Unity
description: Découvrez les fonctionnalités prises en charge par OpenXR pour le développement de réalité mixte dans Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main
ms.openlocfilehash: 371815d6410a7add8ee9c62f72d746d74ad397b0
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392667"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>OpenXR en réalité mixte fonctionnalités prises en charge dans Unity

Le package de **plug-in OpenXR de réalité mixte** est une extension du **plug-in OpenXR** d’Unity et prend en charge une suite de fonctionnalités pour les casques HoloLens 2 et Windows Mixed Reality. Avant de continuer, assurez-vous que votre projet Unity est [configuré pour OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>Opérations prises en charge

Les fonctionnalités suivantes sont actuellement prises en charge :

* Prend en charge les applications UWP pour HoloLens 2 et optimise le modèle d’application HoloLens 2.
* Prend en charge les applications Win32 VR pour le casque Windows Mixed Reality avec les derniers profils de contrôleur et la communication à distance des applications holographiques.
* Suivi de la mise à l’échelle mondiale utilisant les ancres et l’espace non limité.
* [API de stockage d’ancrage pour rendre les ancres persistantes](spatial-anchors-in-unity.md) dans le stockage local HoloLens 2.
* [Interactions entre le contrôleur de mouvement et la main](#motion-controller-and-hand-interactions), y compris le nouveau contrôleur de réverbération HP G2.
* Suivi articulé à l’aide de 26 jointures et d’entrées RADIUS jointes.
* Interaction de regard sur HoloLens 2.
* Recherche de l’appareil photo/vidéo (PV) sur HoloLens 2.
* Capture de la réalité mixte à l’aide d’un rendu de 3e œil via l’appareil photo PV.
* Prend en charge [la « lecture » dans HoloLens 2 avec l’application de communication à distance holographique](unity-play-mode.md#unity-play-mode-with-holographic-remoting), ce qui permet aux développeurs de déboguer les scripts sans les générer et les déployer sur l’appareil.
* Compatible avec MRTK Unity 2.5.3 et versions ultérieures via la [prise en charge des fournisseurs MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Compatible avec Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou version ultérieure.
* (Ajouté dans 0.1.3) Prend en charge la [communication à distance holographique des applications de bureau](holographic-remoting-desktop.md) à partir d’une application Windows autonome créée et déployée.
* (Ajouté dans 0.1.4) Prend en charge le [suivi du code QR](#qr-codes) sur HoloLens2 via SpatialGraphNode
* (Ajouté dans 0.2.0) Prend en charge l' **ancrage** dans la communication à distance holographique
* (Ajouté dans 0.2.0) Prend en charge les **jointures manuelle et le suivi de maillage de main**
* (Ajouté dans 0.2.0) Prend en charge **ARPlaneSubsystems** pour la détection de plan et place l’hologramme à l’aide de **ARRaycastManager**.
* (0.9.0) prend en charge **XRMeshSubsystem** et **ARMeshManager** pour le mappage spatial.
* (Ajouté dans 0.9.0) Prend en charge le plug-in du kit de développement logiciel (SDK) d’ancrage spatial Azure pour Windows. Pour plus d’informations, consultez l' [exemple de projet Mixed Reality + OpenXR Azure spatial Anchors sur GitHub](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample).
* (Ajouté dans 0.9.1) Prend en charge la communication à distance holographique des applications de bureau à partir d’une application Windows UWP créée et déployée.
* (Ajouté dans 0.9.4) Prend en charge la plateforme ARM en plus de ARM64 pour l’application HoloLens 2.

## <a name="motion-controller-and-hand-interactions"></a>Interactions entre le contrôleur de mouvement et la main

Pour connaître les principes de base des interactions de réalité mixte dans Unity, visitez le [Manuel Unity pour l’entrée Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Cette documentation Unity couvre les mappages entre les entrées spécifiques au contrôleur et les **InputFeatureUsages** plus généralisables, la manière dont les entrées XR disponibles peuvent être identifiées et catégorisées, comment lire les données à partir de ces entrées, et bien plus encore.

Le plug-in OpenXR de réalité mixte fournit des profils d’interaction d’entrée supplémentaires, mappés à des **InputFeatureUsage** standard, comme indiqué ci-dessous :

| InputFeatureUsage | Contrôleur de réverbération HP G2 (OpenXR) | Manuel HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Croix | |
| primary2DAxisClick | Manette de jeu-clic | |
| déclencheur | Déclencheur  | |
| délicat | Délicat | Appuyez ou appuyez sur l’air |
| primaryButton | [X/A]-Appuyez sur | Clic aérien |
| secondaryButton | [Y/B]-Appuyez sur | |
| gripButton | Appuyez sur la poignée | |
| triggerButton | Déclencher-appuyer sur | |
| menuButton | Menu | |

### <a name="aim-and-grip-poses"></a>Poses de la AIM et de la poignée

Vous avez accès à deux ensembles de poses via des interactions d’entrée OpenXR :

* La poignée pose le rendu des objets de la main
* L’objectif est de pointer dans le monde.

Pour plus d’informations sur cette conception et les différences entre les deux poses, consultez la [spécification OpenXR-sous-chemins d’entrée](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Les poses fournies par les InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** et **DeviceAngularVelocity** représentent toutes la pose de la **poignée** OpenXR. Les InputFeatureUsages relatives aux poses de poignée sont définis dans les [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)d’Unity.

Les poses fournies par les InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** et **PointerAngularVelocity** représentent toutes **la pose du** OpenXR. Ces InputFeatureUsages ne sont pas définis dans les fichiers C# inclus. vous devez donc définir votre propre InputFeatureUsages comme suit :

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptique

Pour plus d’informations sur l’utilisation des haptique dans le système d’entrée XR Unity, consultez le [Manuel Unity pour Unity XR Input-haptiques](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>Codes QR

HoloLens 2 peut détecter les codes QR dans l’environnement situé autour du casque, ce qui permet d’établir un système de coordonnées à l’emplacement réel de chaque code. Pour plus d’informations, consultez notre documentation sur le [suivi du code QR](../platform-capabilities-and-apis/qr-code-tracking.md) .  Lorsque vous utilisez le plug-in OpenXR, récupérez le [ `SpatialGraphNodeId` à partir de l’API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) et utilisez l' `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API pour localiser le code QR.

Pour référence, nous disposons d’un [exemple de projet de suivi QR sur GitHub](https://github.com/yl-msft/QRTracking) avec davantage d’explications sur l’utilisation de l' [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="troubleshooting"></a>Dépannage

Lorsque vous suspendez et reprenez une application Unity sur HoloLens 2, l’application ne peut pas reprendre correctement, ce qui a pour conséquence 4 points de rotation dans la vue HoloLens.

* Définir le **mode d’envoi de profondeur** sur **aucun** dans les paramètres du projet OpenXR comme solution de contournement
