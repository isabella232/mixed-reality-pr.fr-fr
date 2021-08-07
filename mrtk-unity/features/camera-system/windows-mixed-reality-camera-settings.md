---
title: Paramètres de la caméra Windows Mixed Reality
description: Documentation relative à l’utilisation de Windows Mixed Reality paramètres d’appareil photo dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, appareil photo,
ms.openlocfilehash: 6d0231c070cd001d7e01b4a82ab66c2a9c5c115240b03e28b7d49a14de1753f1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212687"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>fournisseur de paramètres de l’appareil photo Windows Mixed Reality

le fournisseur de paramètres d’appareil photo Windows Mixed Reality détermine le type d’appareil sur lequel l’application s’exécute et applique les paramètres de configuration appropriés en fonction de l’affichage (transparent ou opaque).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>activation du fournisseur de paramètres d’appareil photo Windows Mixed Reality

Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit. Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. dans le panneau inspecteur, accédez à la section système de l’appareil photo et développez la section **camera Paramètres providers** .

    ![Développez Paramètres fournisseurs](../images/camera-system/ExpandProviders.png)

3. cliquez sur **ajouter un appareil photo Paramètres fournisseur** et développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.

    ![Développer le nouveau fournisseur de paramètres](../images/camera-system/ExpandNewProvider.png)

4. sélectionner le fournisseur de Paramètres de caméra Windows Mixed Reality

    ![sélectionner le fournisseur de paramètres Windows Mixed Reality](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> lorsque vous utilisez les profils par défaut de la réalité mixte Microsoft Shared Computer Toolkit, le fournisseur de paramètres d’appareil photo Windows Mixed Reality est déjà activé et configuré.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>configuration du fournisseur de paramètres d’appareil photo Windows Mixed Reality

l’Paramètres Windows Mixed Reality Camera prend également en charge un profil. Ce profil fournit les options suivantes :

![configuration des paramètres de l’appareil photo Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Rendu de la capture de la réalité mixte à partir de la caméra photo/vidéo

avec ce paramètre sur HoloLens 2, vous pouvez activer l’alignement des hologrammes dans vos captures de réalité mixte. S’il est activé, la plateforme fournira un HolographicCamera supplémentaire à l’application lorsqu’une réalité mixte capture une photo ou une vidéo est prise. Ce HolographicCamera fournit des matrices d’affichage correspondant à l’emplacement de la caméra photo/vidéo, et fournit des matrices de projection à l’aide du champ de vue caméra photo/vidéo. Cela permet de s’assurer que les hologrammes, tels que les maillages de main, restent alignés de manière visible dans la sortie vidéo.

### <a name="hololens-2-reprojection-method"></a>méthode de reprojection HoloLens 2

définit la méthode initiale pour la reprojection HoloLens 2. La recommandation par défaut consiste à utiliser la reprojection de profondeur, car toutes les parties de la scène seront stabilisées indépendamment en fonction de leur distance par rapport à l’utilisateur. Si les hologrammes semblent toujours instables, essayez de vous assurer que tous les objets ont correctement envoyé leur profondeur au tampon de profondeur. Il s’agit parfois d’un paramètre de nuanceur. Si la profondeur semble être correctement soumise et que l’instabilité est toujours présente, essayez la stabilisation autoplanaire, qui utilise la mémoire tampon de profondeur pour calculer un plan de stabilisation. Si une application ne peut pas envoyer suffisamment de données de profondeur pour que l’une de ces options soit utilisable, la reprojection planaire est fournie en tant que secours. Cette méthode sera basée sur les données de point de focus fournies par une application via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).

Pour mettre à jour la méthode de reprojection au moment de l’exécution, accédez à l’exemple de la `WindowsMixedRealityReprojectionUpdater` façon suivante :

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Cela ne doit être mis à jour qu’une seule fois et la valeur est réutilisée pour tous les frames suivants. Si la méthode est fréquemment mise à jour, il est recommandé de mettre en cache le résultat de `EnsureComponent` au lieu de l’appeler souvent.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du système d’appareil photo](camera-system-overview.md)
- [création d’un fournisseur de Paramètres d’appareil photo](create-settings-provider.md)
- [Rendu de la capture de la réalité mixte à partir de l’appareil photo PV](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Reprojection holographique](/windows/mixed-reality/hologram-stability#reprojection)