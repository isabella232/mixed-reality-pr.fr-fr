---
title: GettingStartedWithMRTKAndXRSDK
description: Page d’accueil de MRTK avec XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, XRSDK,
ms.openlocfilehash: d5ab9bf51828c84759b72e87e1c41f885c7d6738
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300410"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Prise en main de MRTK et du kit de développement logiciel (SDK) XR

Le kit de développement logiciel (SDK) XR est le [nouveau pipeline XR unity 2019,3 et ultérieur](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). Dans Unity 2019, il fournit une alternative au pipeline XR existant. Dans Unity 2020, il deviendra le seul pipeline XR dans Unity.

## <a name="prerequisites"></a>Prérequis

Pour commencer à utiliser le Toolkit de réalité mixte, suivez [les étapes fournies](../install-the-tools.md#importing-the-mixed-reality-toolkit) pour ajouter MRTK à un projet.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configuration d’Unity pour le pipeline du kit de développement logiciel (SDK) XR

Le pipeline du kit de développement logiciel (SDK) XR prend actuellement en charge 3 plateformes : Windows Mixed Reality, Oculus et OpenXR. Les sections ci-dessous décrivent les étapes nécessaires à la configuration du kit de développement logiciel (SDK) XR pour chaque plateforme.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Accédez au **Gestionnaire de package de Unity** et installez le package de plug-in XR Windows, qui ajoute la prise en charge de Windows Mixed Reality dans le kit de développement logiciel (SDK) XR. Cela entraîne également l’extraction de quelques packages de dépendance. 

1. Vérifiez que les éléments suivants ont été correctement installés :
   * Gestion du plug-in XR
   * Plug-in XR Windows
   * XR des assistances d’entrée héritées

2. Accédez à **Edit > Project Settings**.
3. Cliquez sur l’onglet gestion du plug-in XR dans la fenêtre Paramètres du projet.
4. Accédez aux paramètres de plateforme Windows universelle et vérifiez que Windows Mixed Reality est vérifié sous les fournisseurs de plug-in.
5. Vérifiez que l’option initialiser XR au démarrage est cochée.
6. (**_Requis pour la communication à distance HoloLens dans l’éditeur, sinon facultatif_**) Accédez aux paramètres autonomes et assurez-vous que Windows Mixed Reality est coché sous fournisseurs de plug-ins. Vérifiez également que l’option initialiser XR au démarrage est cochée.

![Onglet gestion du plug-in XR avec option autonome sélectionnée](images/xr-management-img-02.png)

7. (**_Facultatif_**) Cliquez sur l’onglet Windows Mixed Reality sous gestion du plug-in XR, puis créez un profil de paramètres personnalisés pour modifier les valeurs par défaut. Si la liste des paramètres existe déjà, aucun profil ne doit être créé.

![Onglet gestion du plug-in XR avec Windows sélectionné](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Pour terminer, suivez la [procédure de configuration de Oculus Quest dans MRTK à l’aide du Guide de pipeline du kit de développement logiciel (SDK) XR](../features/cross-platform/oculus-quest-mrtk.md) . Le guide décrit les étapes nécessaires à la configuration de Unity et de MRTK pour utiliser le pipeline du kit de développement logiciel (SDK) XR pour Oculus Quest.

### <a name="openxr-preview"></a>OpenXR (préversion)

> [!IMPORTANT]
> OpenXR dans Unity est pris en charge uniquement sur Unity 2020,2 et les versions ultérieures.
>
> Actuellement, il prend également en charge uniquement les versions x64 et ARM64.

1. Suivez les étapes de la section [utilisation du plug-in OpenXR de la réalité mixte pour Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, y compris les étapes de configuration de la gestion et de l’optimisation du plug-in XR pour installer le plug-in OpenXR dans votre projet. Assurez-vous que les éléments suivants ont été correctement installés :
   1. Gestion du plug-in XR
   1. Plug-in OpenXR
   1. Plug-in OpenXR de réalité mixte
1. Accédez à modifier > paramètres du projet.
1. Cliquez sur l’onglet gestion du plug-in XR dans la fenêtre Paramètres du projet.
1. Vérifiez que l’option initialiser XR au démarrage est cochée.
1. (**_Facultatif_**) Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez ensemble de fonctionnalités Microsoft HoloLens.

![Gestion des plug-ins ouverte XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Si vous avez un projet préexistant qui utilise MRTK à partir de UPM, assurez-vous que la ligne suivante se trouve dans le fichier **link.xml** situé dans le dossier MixedRealityToolkit. generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Pour la version initiale de MRTK et OpenXR, seuls les contrôleurs de mouvement HoloLens 2 et Windows Mixed Reality sont pris en charge en mode natif. La prise en charge d’un matériel supplémentaire sera ajoutée dans les versions à venir.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configuration de MRTK pour le pipeline du kit de développement logiciel (SDK) XR

Si vous utilisez OpenXR, choisissez « DefaultOpenXRConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.

Si vous utilisez d’autres runtimes XR dans la configuration de gestion du plug-in XR, comme Windows Mixed Reality ou Oculus, choisissez « DefaultXRSDKConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.

Ces profils sont configurés avec les systèmes et fournisseurs appropriés, si nécessaire. Pour plus d’informations sur le profil et l’exemple de prise en charge avec XR SDK, consultez [la documentation](../features/profiles/profiles.md#xr-sdk) relative aux profils.

Pour migrer un profil existant vers le kit de développement logiciel (SDK) XR, les services et fournisseurs de données suivants doivent être mis à jour :

### <a name="camera"></a>Appareil photo

De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Paramètres de l’appareil photo hérité](../features/images/xrsdk/CameraSystemLegacy.png)

par

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**et**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Paramètres de l’appareil photo SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrée

De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Paramètres d’entrée hérités](../features/images/xrsdk/InputSystemWMRLegacy.png)

par

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![Paramètres d’entrée OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Paramètres d’entrée du SDK XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Paramètres des limites héritées](../features/images/xrsdk/BoundarySystemLegacy.png)

par

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Paramètres des limites du SDK XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Sensibilisation spatiale

De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Paramètres de sensibilisation spatiale hérités](../features/images/xrsdk/SpatialAwarenessLegacy.png)

par

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| En cours | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Paramètres de sensibilisation spatiale du SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mappages de contrôleur

Si vous utilisez des profils de mappage de contrôleur personnalisés, ouvrez l’un d’eux et exécutez la boîte à outils de réalité mixte-> utilitaires-> mise à jour-> les profils de mappage de contrôleur pour vous assurer que les nouveaux types de contrôleur du kit de développement logiciel (SDK) XR sont définis.

## <a name="see-also"></a>Voir aussi

* [Prise en main du développement de clients dans Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Prise en main du développement VR dans Unity](https://docs.unity3d.com/Manual/VROverview.html)