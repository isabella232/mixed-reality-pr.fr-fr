---
title: Fonctionnalités prises en charge par le plug-in OpenXR dans Unity
description: Découvrez les fonctionnalités prises en charge par OpenXR pour le développement de réalité mixte dans Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main
ms.openlocfilehash: 09067498d33fb2c96da53aa54c0449959355d809
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583514"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>OpenXR en réalité mixte fonctionnalités prises en charge dans Unity

Le package de **plug-in OpenXR de réalité mixte** est une extension du **plug-in OpenXR** d’Unity et prend en charge une suite de fonctionnalités pour les casques HoloLens 2 et Windows Mixed Reality. Avant de continuer, vérifiez que vous avez installé **unity 2020,2** ou une version ultérieure, le **plug-in OpenXR version 0.1.2** ou ultérieure et votre projet Unity est [configuré pour OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>Opérations prises en charge

Les fonctionnalités suivantes sont actuellement prises en charge :

* Prend en charge les applications UWP pour HoloLens 2 et optimise le modèle d’application HoloLens 2.
* Prend en charge les applications Win32 VR pour le casque Windows Mixed Reality avec les derniers profils de contrôleur et la communication à distance des applications holographiques.
* Suivi de la mise à l’échelle mondiale utilisant les ancres et l’espace non limité.
* [API de stockage d’ancrage pour rendre les ancres persistantes](#anchors-and-anchor-persistence) dans le stockage local HoloLens 2.
* [Interactions entre le contrôleur de mouvement et la main](#motion-controller-and-hand-interactions), y compris le nouveau contrôleur de réverbération HP G2.
* Suivi articulé à l’aide de 26 jointures et d’entrées RADIUS jointes.
* Interaction de regard sur HoloLens 2.
* Recherche de l’appareil photo/vidéo (PV) sur HoloLens 2.
* Capture de la réalité mixte à l’aide d’un rendu de 3e œil via l’appareil photo PV.
* Prend en charge [la « lecture » dans HoloLens 2 avec l’application de communication à distance holographique](#holographic-remoting-in-unity-editor-play-mode), ce qui permet aux développeurs de déboguer les scripts sans les générer et les déployer sur l’appareil.
* Compatible avec MRTK Unity 2.5.3 et versions ultérieures via la [prise en charge des fournisseurs MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Compatible avec Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou version ultérieure

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Communication à distance holographique en mode de lecture de l’éditeur Unity

La création d’un projet Unity UWP dans Visual Studio Project et son empaquetage et son déploiement sur un appareil HoloLens 2 peuvent prendre un certain temps. Une solution consiste à activer la communication à distance de l’éditeur holographique, qui vous permet de déboguer votre script C# en mode « lecture » directement sur un appareil HoloLens 2 sur votre réseau. Ce scénario évite la surcharge liée à la création et au déploiement d’un package UWP sur un appareil distant.

1. Tout d’abord, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Store sur votre HoloLens 2
2. Exécutez l’application de lecteur de communication à distance holographique sur HoloLens 2 et vous verrez le numéro de version et l’adresse IP à laquelle se connecter.
    * V 2.4 ou version ultérieure est nécessaire pour fonctionner avec le plug-in OpenXR

    ![Capture d’écran du lecteur de communication à distance holographique s’exécutant dans HoloLens](images/openxr-features-img-01.png)

3. Ouvrez les **paramètres du projet de modification >**, accédez à **gestion du plug-in XR**, puis cochez la case **Windows Mixed Reality Feature Set** :

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-features-img-02.png)

4. Développez la section **fonctionnalités** sous **OpenXR** et sélectionnez **Afficher tout** .
5. Cochez la case **accès distant de l’éditeur holographique** et entrez l’adresse IP obtenue à partir de l’application de communication à distance holographique :

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec les fonctionnalités mises en surbrillance](images/openxr-features-img-03.png)

Vous pouvez maintenant cliquer sur le bouton « lecture » pour lire votre application Unity dans l’application de communication à distance holographique sur votre HoloLens. Vous pouvez également [attacher Visual Studio à Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) pour déboguer des scripts C# en mode lecture.

> [!NOTE]
> À partir de la version 0.1.0, le runtime de communication à distance holographique ne prend pas en charge les ancres, et les fonctionnalités ARAnchorManager ne fonctionnent pas via la communication à distance.  Cette fonctionnalité est disponible dans les versions ultérieures.

## <a name="anchors-and-anchor-persistence"></a>Ancres et persistance d’ancrage

Le plug-in OpenXR de réalité mixte fournit des fonctionnalités d’ancre de base via une implémentation du **ARAnchorManager** ARFoundation d’Unity. Pour en savoir plus sur les principes de base de **ARAnchor** dans ARFoundation, consultez le [Manuel ARFoundation du gestionnaire d’ancrage AR](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). À partir de la version 0.1.0, ce plug-in prend en charge toutes les fonctionnalités ARAnchorManager, à l’exception de la création d’ancres attachées à un plan, qui est disponible dans une version ultérieure.

### <a name="anchor-persistence-and-the-xranchorstore"></a>Persistance d’ancrage et XRAnchorStore

Une API supplémentaire appelée **XRAnchorStore** permet aux ancres d’être rendues persistantes entre les sessions. Le XRAnchorStore est une représentation des ancres enregistrées sur votre appareil. Les ancres peuvent être rendues persistantes à partir de **ARAnchors** dans la scène Unity, chargées à partir du stockage dans un nouveau **ARAnchors**, ou supprimées du stockage.

> [!NOTE]
> Ces ancres doivent être enregistrées et chargées sur le même appareil. Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Pour charger XRAnchorStore, le plug-in fournit une méthode d’extension sur XRAnchorSubsystem, le sous-système d’un ARAnchorManager :

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager, comme suit :

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Pour voir un exemple complet d’ancres persistantes/non persistantes, consultez l’exemple d’ancres-> ancrages GameObject et AnchorsSample.cs script dans l' [exemple de scène de plug-in de réalité mixte OpenXR](openxr-getting-started.md#hololens-2-samples):

![Capture d’écran de l’ouverture du panneau de la hiérarchie dans l’éditeur Unity avec l’exemple ancres mis en surbrillance](images/openxr-features-img-04.png)

![Capture d’écran du panneau Inspecteur ouvert dans l’éditeur Unity avec l’exemple de script Anchors mis en surbrillance](images/openxr-features-img-05.png)

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

## <a name="whats-coming-soon"></a>Bientôt disponible

Les problèmes suivants et les fonctionnalités manquantes sont connus avec le plug-in OpenXR de réalité mixte **version 0.1.0**. Nous travaillons sur ces versions et publierons des correctifs et de nouvelles fonctionnalités dans les versions à venir.

* **ARPlaneSubsystem** n’est pas encore pris en charge. **ARPlaneManager**, **ARRAYCASTMANAGER** et l’API associée comme **ARAnchorManager. AttachAnchor** ne sont pas non plus prises en charge sur HoloLens 2.
* Le **point d’ancrage** n’est pas encore pris en charge par la communication à distance holographique, mais dans un avenir proche.
* Le suivi du maillage de la **main** , les **codes QR** et les **XRMeshSubsystem** ne sont pas encore pris en charge.
* La prise en charge des **ancres spatiales Azure** est disponible dans une version ultérieure.
* **ARM64** est la seule plateforme prise en charge pour les applications HoloLens 2. La plateforme **ARM** est disponible dans une version ultérieure.

## <a name="troubleshooting"></a>Dépannage

Lorsque vous suspendez et reprenez une application Unity sur HoloLens 2, l’application ne peut pas reprendre correctement, ce qui a pour conséquence 4 points de rotation dans la vue HoloLens.
* Définir le **mode d’envoi de profondeur** sur **aucun** dans les paramètres du projet OpenXR comme solution de contournement