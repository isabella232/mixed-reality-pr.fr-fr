---
title: Paramètres de la caméra Windows Mixed Reality
description: Documentation sur l’utilisation de la caméra Windows Mixed Reality dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, appareil photo,
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145165"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Fournisseur de paramètres d’appareil photo Windows Mixed Reality

Le fournisseur de paramètres de l’appareil photo Windows Mixed Reality détermine le type d’appareil sur lequel l’application s’exécute et applique les paramètres de configuration appropriés en fonction de l’affichage (transparent ou opaque).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Activation du fournisseur de paramètres d’appareil photo Windows Mixed Reality

Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit. Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Dans le panneau de l’inspecteur, accédez à la section système de l’appareil photo et développez la section paramètres de l' **appareil photo** .

    ![Développez Paramètres fournisseurs](../images/camera-system/ExpandProviders.png)

3. Cliquez sur **Ajouter un fournisseur de paramètres d’appareil photo** , puis développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.

    ![Développer le nouveau fournisseur de paramètres](../images/camera-system/ExpandNewProvider.png)

4. Sélectionner le fournisseur de paramètres d’appareil photo Windows Mixed Reality

    ![Sélectionner le fournisseur de paramètres Windows Mixed Reality](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Lorsque vous utilisez les profils par défaut de Microsoft Mixed Reality Toolkit, le fournisseur de paramètres d’appareil photo Windows Mixed Real est déjà activé et configuré.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Configuration du fournisseur de paramètres d’appareil photo Windows Mixed Reality

Les paramètres de la caméra Windows Mixed Reality prennent également en charge un profil. Ce profil fournit les options suivantes :

![Configuration des paramètres de l’appareil photo Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Rendu de la capture de la réalité mixte à partir de la caméra photo/vidéo

Avec ce paramètre sur HoloLens 2, vous pouvez activer l’alignement des hologrammes dans vos captures de réalité mixte. S’il est activé, la plateforme fournira un HolographicCamera supplémentaire à l’application lorsqu’une réalité mixte capture une photo ou une vidéo est prise. Ce HolographicCamera fournit des matrices d’affichage correspondant à l’emplacement de la caméra photo/vidéo, et fournit des matrices de projection à l’aide du champ de vue caméra photo/vidéo. Cela permet de s’assurer que les hologrammes, tels que les maillages de main, restent alignés de manière visible dans la sortie vidéo.

### <a name="hololens-2-reprojection-method"></a>Méthode de reprojection HoloLens 2

Définit la méthode initiale pour la reprojection HoloLens 2. La recommandation par défaut consiste à utiliser la reprojection de profondeur, car toutes les parties de la scène seront stabilisées indépendamment en fonction de leur distance par rapport à l’utilisateur. Si les hologrammes semblent toujours instables, essayez de vous assurer que tous les objets ont correctement envoyé leur profondeur au tampon de profondeur. Il s’agit parfois d’un paramètre de nuanceur. Si la profondeur semble être correctement soumise et que l’instabilité est toujours présente, essayez la stabilisation autoplanaire, qui utilise la mémoire tampon de profondeur pour calculer un plan de stabilisation. Si une application ne peut pas envoyer suffisamment de données de profondeur pour que l’une de ces options soit utilisable, la reprojection planaire est fournie en tant que secours. Cette méthode sera basée sur les données de point de focus fournies par une application via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).

Pour mettre à jour la méthode de reprojection au moment de l’exécution, accédez à l’exemple de la `WindowsMixedRealityReprojectionUpdater` façon suivante :

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Cela ne doit être mis à jour qu’une seule fois et la valeur est réutilisée pour tous les frames suivants. Si la méthode est fréquemment mise à jour, il est recommandé de mettre en cache le résultat de `EnsureComponent` au lieu de l’appeler souvent.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du système de caméras](camera-system-overview.md)
- [Création d’un fournisseur de paramètres d’appareil photo](create-settings-provider.md)
- [Rendu de la capture de la réalité mixte à partir de l’appareil photo PV](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Reprojection holographique](/windows/mixed-reality/hologram-stability#reprojection)