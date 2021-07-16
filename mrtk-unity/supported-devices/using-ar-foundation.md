---
title: Déploiement sur Android et iOS (AR Foundation) [expérimental]
description: Documentation pour configurer MRTK pour Android et iOS (ARFoundation) dans Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, ar Core, ar Kit, ios, ios, Android, ar Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281945"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a>Déploiement sur Android et iOS (AR Foundation) [expérimental]

## <a name="install-required-packages"></a>Installer les packages nécessaires

1. téléchargez et importez le fichier **Microsoft. MixedReality. Shared Computer Toolkit. package unity. Foundation** , [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) ou [unity Gestionnaire de package](../configuration/usingupm.md)

1. dans l’Gestionnaire de package unity (UPM), installez les packages suivants :

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

    **Unity 2020.3. x**

    | **Android** | **iOS** |
    | --- | --- |
    | Fondement de base  <br/> Version : 3.1.3 |  Fondement de base  <br/> Version : 4.0.12 |
    | Plug-in ARCore XR <br/> Version : 3.1.4 | Plug-in ARKit XR <br/> Version : 4.1.7 |

1. mettez à jour les définitions de script MRTK unity en appelant l’élément de menu : **Mixed reality > Shared Computer Toolkit > Utilities > unity > script Update définit**

    ![Les scripts de mise à jour définissent](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Activation du fournisseur de paramètres d’appareil photo Unity AR

Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit. Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.

    ![Hiérarchie de scène configurée par MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. Sélectionnez **copier et personnaliser** pour cloner le profil MRTK afin d’activer la configuration personnalisée.

    ![Cloner le profil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. Sélectionnez **clone** en regard du profil de l’appareil photo.

    ![Cloner le profil de la caméra MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. dans le panneau inspecteur, accédez à la section système de l’appareil photo et développez la section **camera Paramètres providers** .

    ![Développez Paramètres fournisseurs](../features/images/camera-system/ExpandProviders.png)

1. cliquez sur **ajouter un appareil photo Paramètres fournisseur** et développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.

    ![Développer le nouveau fournisseur de paramètres](../features/images/camera-system/ExpandNewProvider.png)

1. sélectionner le fournisseur de Paramètres unity AR

    ![Sélectionner le fournisseur de paramètres Unity](../features/images/camera-system/SelectUnityArSettings.png)

    Pour plus d’informations sur la configuration du fournisseur de paramètres de l’appareil Unity AR, fournisseur des paramètres de l' [appareil Unity AR](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Cette installation vérifie (au démarrage de l’application) si les composants de fondation de base se trouvent dans la scène. Si ce n’est pas le cas, ils sont automatiquement ajoutés pour qu’ils fonctionnent avec ARCore et ARKit.
> Si vous devez définir un comportement spécifique, vous devez ajouter les composants dont vous avez besoin.
> Pour plus d’informations sur les composants et l’installation de comptabilité clients, consultez cette [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).

## <a name="building-a-scene-for-android-and-ios-devices"></a>Création d’une scène pour les appareils Android et iOS

1. assurez-vous que vous avez ajouté le fournisseur de Paramètres d’appareil photo unity à votre scène.

1. basculez la plateforme sur Android ou iOS dans la Build unity Paramètres

1. Vérifier que le fournisseur de gestion du plug-in XR associé est activé

    Gestion du plug-in XR iOS :  ![ gestion du plug-in XR iOS](../features/images/XRManagementiOS.png)

1. Générer et exécuter la scène

## <a name="see-also"></a>Voir aussi

- [Paramètres de caméra unity AR](../features/camera-system/unity-ar-camera-settings.md)
