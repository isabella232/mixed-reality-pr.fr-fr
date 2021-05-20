---
title: Utilisation d’AR Foundation
description: Documentation relative à l’utilisation de ARFoundation dans Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, de réalité mixte, développement, MRTK, AR Core, kit AR, iOS, IOS, Android, comptabilité basique
ms.openlocfilehash: 0f02eb94d95c2900348adaa9e1a02c3e54832a96
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207447"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>Configuration de MRTK pour iOS et Android [expérimental]

## <a name="install-required-packages"></a>Installer les packages nécessaires

1. Téléchargez et importez le package **Microsoft. MixedReality. Toolkit. Unity. Foundation** à partir de [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) ou du [Gestionnaire de package Unity](../configuration/usingupm.md)

1. Dans le gestionnaire de package Unity (UPM), installez les packages suivants :

    **Unity 2018.4.x**

    | **Android** | **iOS** | Commentaires |
    | --- | --- | --- |
    | Fondement de base  <br/> Version : 1.5.0-Preview 6 | Fondement de base  <br/> Version : 1.5.0-Preview 6 | Pour Unity 2018,4, ce package est inclus en tant que version préliminaire. Pour afficher le package : `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | Plug-in ARCore XR <br/> Version : 2.1.2 | Plug-in ARKit XR <br/> Version : 2.1.2 | |

    **Unity 2019.4. x**

    | **Android** | **iOS** |
    | --- | --- |
    | Fondement de base  <br/> Version : 2.1.8 |  Fondement de base  <br/> Version : 2.1.8 |
    | Plug-in ARCore XR <br/> Version : 2.1.11 | Plug-in ARKit XR <br/> Version : 2.1.9 |

    **Unity 2020.1. x (non prise en charge pour l’instant, incluse à titre d’information uniquement)**

    | **Android** | **iOS** |
    | --- | --- |
    | Fondement de base  <br/> Version : 3.1.3 |  Fondement de base  <br/> Version : 3.1.3 |
    | Plug-in ARCore XR <br/> Version : 3.1.4 | Plug-in ARKit XR <br/> Version : 3.1.3 |

1. Mettez à jour les définitions de script MRTK Unity en appelant l’élément de menu : **Mixed reality > Toolkit > Utilities > unity > de mise à jour des scripts de mise à jour définit**

    ![Les scripts de mise à jour définissent](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Activation du fournisseur de paramètres d’appareil photo Unity AR

Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit. Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.

    ![Hiérarchie de scène configurée par MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. Sélectionnez **copier et personnaliser** pour cloner le profil MRTK afin d’activer la configuration personnalisée.

    ![Cloner le profil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. Sélectionnez **clone** en regard du profil de l’appareil photo.

    ![Cloner le profil de la caméra MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. Dans le panneau de l’inspecteur, accédez à la section système de l’appareil photo et développez la section paramètres de l' **appareil photo** .

    ![Développez Paramètres fournisseurs](../features/images/camera-system/ExpandProviders.png)

1. Cliquez sur **Ajouter un fournisseur de paramètres d’appareil photo** , puis développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.

    ![Développer le nouveau fournisseur de paramètres](../features/images/camera-system/ExpandNewProvider.png)

1. Sélectionner le fournisseur de paramètres de l’appareil Unity AR

    ![Sélectionner le fournisseur de paramètres Unity](../features/images/camera-system/SelectUnityArSettings.png)

    Pour plus d’informations sur la configuration du fournisseur de paramètres de l’appareil Unity AR, fournisseur des paramètres de l' [appareil Unity AR](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Cette installation vérifie (au démarrage de l’application) si les composants de fondation de base se trouvent dans la scène. Si ce n’est pas le cas, ils sont automatiquement ajoutés pour qu’ils fonctionnent avec ARCore et ARKit.
> Si vous devez définir un comportement spécifique, vous devez ajouter les composants dont vous avez besoin.
> Pour plus d’informations sur les composants et l’installation de comptabilité clients, consultez cette [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).

## <a name="building-a-scene-for-android-and-ios-devices"></a>Création d’une scène pour les appareils Android et iOS

1. Vérifiez que vous avez ajouté le fournisseur de paramètres d’appareil photo Unity à votre scène.

1. Basculer la plateforme sur Android ou iOS dans les paramètres de build Unity

1. Vérifier que le fournisseur de gestion du plug-in XR associé est activé

    Gestion du plug-in XR iOS :  ![ gestion du plug-in XR iOS](../features/images/XRManagementiOS.png)

1. Générer et exécuter la scène

## <a name="see-also"></a>Voir aussi

- [Paramètres de l’appareil Unity AR](../features/camera-system/unity-ar-camera-settings.md)
