---
title: Bien démarrer avec le kit SDK MRTK et XR
description: Page d’accueil de MRTK avec le kit de développement logiciel (SDK) XR
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, XRSDK, kit de développement logiciel (SDK) XR
ms.openlocfilehash: 681352ff854598ab34bd9521b46ae9f4e6f42f02
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905749"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Bien démarrer avec le kit SDK MRTK et XR

Le kit de développement logiciel (SDK) XR est le [nouveau pipeline XR unity 2019,3 et ultérieur](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). Dans Unity 2019, il fournit une alternative au pipeline XR existant. Dans Unity 2020, il s’agit du seul pipeline XR dans Unity.

## <a name="prerequisites"></a>Prérequis

pour commencer à utiliser la Shared Computer Toolkit de la réalité mixte, suivez [les étapes fournies](/windows/mixed-reality/develop/install-the-tools#importing-the-mixed-reality-toolkit) pour ajouter MRTK à un projet.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configuration d’Unity pour le pipeline du kit de développement logiciel (SDK) XR

le pipeline du kit de développement logiciel (SDK) XR prend actuellement en charge 3 plateformes : Windows Mixed Reality, Oculus et OpenXR. Les sections ci-dessous décrivent les étapes nécessaires à la configuration du kit de développement logiciel (SDK) XR pour chaque plateforme.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

accédez à la **Gestionnaire de package d’unity** et installez le package de plug-in Windows XR, qui ajoute la prise en charge de Windows Mixed Reality sur XR SDK. Cela entraîne également l’extraction de quelques packages de dépendance.

1. Vérifiez que les éléments suivants ont été correctement installés :
   * Gestion du plug-in XR
   * Windows Plug-in XR
   * XR des assistances d’entrée héritées

2. Accédez à **Edit > Project Settings**.
3. cliquez sur l’onglet gestion du Plug-in XR dans la fenêtre Paramètres Project.
4. accédez aux paramètres de plateforme Windows universelle et vérifiez Windows Mixed Reality est cochée sous fournisseurs de Plug-ins.
5. Vérifiez que l’option initialiser XR au démarrage est cochée.
6. (**_requis pour l’éditeur HoloLens communication à distance, sinon facultatif_**) accédez aux paramètres autonomes et assurez-vous que Windows Mixed Reality est coché sous fournisseurs de Plug-ins. Vérifiez également que l’option initialiser XR au démarrage est cochée.

    ![Onglet gestion du plug-in XR avec option autonome sélectionnée](images/xr-management-img-02.png)

7. (**_Facultatif_**) cliquez sur l’onglet Windows Mixed Reality sous gestion du Plug-in XR, puis créez un profil de paramètres personnalisés pour modifier les valeurs par défaut. Si la liste des paramètres existe déjà, aucun profil ne doit être créé.

    ![gestion du plug-in XR avec l’onglet Windows sélectionné](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Pour terminer, suivez la [procédure de configuration de Oculus Quest dans MRTK à l’aide du Guide de pipeline du kit de développement logiciel (SDK) XR](../supported-devices/oculus-quest-mrtk.md) . Le guide décrit les étapes nécessaires à la configuration de Unity et de MRTK pour utiliser le pipeline du kit de développement logiciel (SDK) XR pour Oculus Quest.

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> OpenXR dans Unity est pris en charge uniquement sur Unity 2020,2 et les versions ultérieures.
> Il prend également en charge uniquement les versions x64, ARM et ARM64.

1. Suivez les étapes de la section [utilisation du plug-in OpenXR de la réalité mixte pour Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, y compris les étapes de configuration de la gestion et de l’optimisation du plug-in XR pour installer le plug-in OpenXR dans votre projet. Assurez-vous que les éléments suivants ont été correctement installés :
   1. Gestion du plug-in XR
   1. Plug-in OpenXR
   1. Plug-in OpenXR de réalité mixte
1. accédez à modifier > Project Paramètres.
1. cliquez sur l’onglet gestion du Plug-in XR dans la fenêtre Paramètres Project.
1. Vérifiez que l’option initialiser XR au démarrage est cochée.
1. (**_Facultatif_**) si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez Microsoft HoloLens ensemble de fonctionnalités.

![OpenXR gestion des plug-ins](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Si vous avez un projet préexistant qui utilise MRTK à partir de UPM, assurez-vous que la ligne suivante se trouve dans le fichier **link.xml** situé dans le dossier MixedRealityToolkit. generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> pour la version initiale de MRTK et OpenXR, seuls les contrôleurs de mouvement des mains et des Windows Mixed Realitys HoloLens 2 sont pris en charge en mode natif. La prise en charge d’un matériel supplémentaire sera ajoutée dans les versions à venir.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configuration de MRTK pour le pipeline du kit de développement logiciel (SDK) XR

::: moniker range=">= mrtkunity-2021-05"
Utilisez l’un des profils MRTK par défaut, qui sont tous configurés dans les pipelines XR d’Unity. Les « DefaultOpenXRConfigurationProfile » et « DefaultXRSDKConfigurationProfile » précédents sont maintenant marqués comme obsolètes.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Si vous utilisez OpenXR, choisissez « DefaultOpenXRConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.

si vous utilisez d’autres runtimes XR dans la configuration de gestion du Plug-in XR, comme Windows Mixed Reality ou Oculus, choisissez « DefaultXRSDKConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.

Ces profils sont configurés avec les systèmes et fournisseurs appropriés, si nécessaire. Pour plus d’informations sur le profil et l’exemple de prise en charge avec XR SDK, consultez [la documentation](../features/profiles/profiles.md#xr-sdk) relative aux profils.
::: moniker-end

Pour migrer un profil existant vers le kit de développement logiciel (SDK) XR, les services et fournisseurs de données suivants doivent être mis à jour.
::: moniker range=">= mrtkunity-2021-05"
Vous pourrez voir les nouveaux fournisseurs de données sous l’onglet Kit de développement logiciel (SDK) XR dans Unity 2019 ou dans l’affichage principal/uniquement dans Unity 2020 +, où Legacy XR n’existe pas.

![Onglet Kit de développement logiciel (SDK) XR](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>Appareil photo

::: moniker range=">= mrtkunity-2021-05"
Ajouter les fournisseurs de données suivants
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Paramètres de l’appareil photo hérité](../features/images/xrsdk/CameraSystemLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Paramètres de l’appareil photo SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrée

::: moniker range=">= mrtkunity-2021-05"
Ajouter les fournisseurs de données suivants
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Paramètres d’entrée hérités](../features/images/xrsdk/InputSystemWMRLegacy.png)

to
::: moniker-end

| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![Paramètres d’entrée OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Paramètres d’entrée du SDK XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

::: moniker range=">= mrtkunity-2021-05"
Ajouter les fournisseurs de données suivants
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Paramètres des limites héritées](../features/images/xrsdk/BoundarySystemLegacy.png)

to
::: moniker-end

| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Paramètres des limites du SDK XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Reconnaissance spatiale

::: moniker range=">= mrtkunity-2021-05"
Ajouter les fournisseurs de données suivants
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Paramètres de sensibilisation spatiale hérités](../features/images/xrsdk/SpatialAwarenessLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (pour UWP) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (pour UWP) |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (pour les plateformes non UWP) | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Paramètres de sensibilisation spatiale du SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mappages de contrôleur

si vous utilisez des profils de mappage de contrôleur personnalisés, ouvrez l’un d’eux et exécutez l’élément de menu Shared Computer Toolkit de la réalité mixte-> utilitaires-> mise à jour > des profils de mappage du contrôleur pour vous assurer que les nouveaux types de contrôleur du kit de développement logiciel (SDK) XR sont définis.

## <a name="see-also"></a>Voir aussi

* [Prise en main du développement de clients dans Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Prise en main du développement VR dans Unity](https://docs.unity3d.com/Manual/VROverview.html)