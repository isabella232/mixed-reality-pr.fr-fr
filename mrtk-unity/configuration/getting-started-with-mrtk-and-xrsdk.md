---
title: GettingStartedWithMRTKAndXRSDK
description: Page d’accueil de MRTK avec XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, XRSDK,
ms.openlocfilehash: fe50de31ae24b415738db64073822b2aff061636
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850425"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="ea234-104">Prise en main de MRTK et du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="ea234-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="ea234-105">Le kit de développement logiciel (SDK) XR est le [nouveau pipeline XR unity 2019,3 et ultérieur](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="ea234-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="ea234-106">Dans Unity 2019, il fournit une alternative au pipeline XR existant.</span><span class="sxs-lookup"><span data-stu-id="ea234-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="ea234-107">Dans Unity 2020, il deviendra le seul pipeline XR dans Unity.</span><span class="sxs-lookup"><span data-stu-id="ea234-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea234-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ea234-108">Prerequisites</span></span>

<span data-ttu-id="ea234-109">Pour commencer à utiliser le Toolkit de réalité mixte, suivez [les étapes fournies](../install-the-tools.md#importing-the-mixed-reality-toolkit) pour ajouter MRTK à un projet.</span><span class="sxs-lookup"><span data-stu-id="ea234-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="ea234-110">Configuration d’Unity pour le pipeline du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="ea234-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="ea234-111">Le pipeline du kit de développement logiciel (SDK) XR prend actuellement en charge 3 plateformes : Windows Mixed Reality, Oculus et OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ea234-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="ea234-112">Les sections ci-dessous décrivent les étapes nécessaires à la configuration du kit de développement logiciel (SDK) XR pour chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="ea234-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="ea234-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ea234-113">Windows Mixed Reality</span></span>

<span data-ttu-id="ea234-114">Accédez au **Gestionnaire de package de Unity** et installez le package de plug-in XR Windows, qui ajoute la prise en charge de Windows Mixed Reality dans le kit de développement logiciel (SDK) XR.</span><span class="sxs-lookup"><span data-stu-id="ea234-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="ea234-115">Cela entraîne également l’extraction de quelques packages de dépendance.</span><span class="sxs-lookup"><span data-stu-id="ea234-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="ea234-116">Vérifiez que les éléments suivants ont été correctement installés :</span><span class="sxs-lookup"><span data-stu-id="ea234-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="ea234-117">Gestion du plug-in XR</span><span class="sxs-lookup"><span data-stu-id="ea234-117">XR Plugin Management</span></span>
   * <span data-ttu-id="ea234-118">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="ea234-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="ea234-119">XR des assistances d’entrée héritées</span><span class="sxs-lookup"><span data-stu-id="ea234-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="ea234-120">Accédez à **Edit > Project Settings**.</span><span class="sxs-lookup"><span data-stu-id="ea234-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="ea234-121">Cliquez sur l’onglet gestion du plug-in XR dans la fenêtre Paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="ea234-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="ea234-122">Accédez aux paramètres de plateforme Windows universelle et vérifiez que Windows Mixed Reality est vérifié sous les fournisseurs de plug-in.</span><span class="sxs-lookup"><span data-stu-id="ea234-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="ea234-123">Vérifiez que l’option initialiser XR au démarrage est cochée.</span><span class="sxs-lookup"><span data-stu-id="ea234-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="ea234-124">(**_Requis pour la communication à distance HoloLens dans l’éditeur, sinon facultatif_**) Accédez aux paramètres autonomes et assurez-vous que Windows Mixed Reality est coché sous fournisseurs de plug-ins.</span><span class="sxs-lookup"><span data-stu-id="ea234-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="ea234-125">Vérifiez également que l’option initialiser XR au démarrage est cochée.</span><span class="sxs-lookup"><span data-stu-id="ea234-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Onglet gestion du plug-in XR avec option autonome sélectionnée](images/xr-management-img-02.png)

7. <span data-ttu-id="ea234-127">(**_Facultatif_**) Cliquez sur l’onglet Windows Mixed Reality sous gestion du plug-in XR, puis créez un profil de paramètres personnalisés pour modifier les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea234-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="ea234-128">Si la liste des paramètres existe déjà, aucun profil ne doit être créé.</span><span class="sxs-lookup"><span data-stu-id="ea234-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Onglet gestion du plug-in XR avec Windows sélectionné](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="ea234-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="ea234-130">Oculus</span></span>

1. <span data-ttu-id="ea234-131">Pour terminer, suivez la [procédure de configuration de Oculus Quest dans MRTK à l’aide du Guide de pipeline du kit de développement logiciel (SDK) XR](../supported-devices/oculus-quest-mrtk.md) .</span><span class="sxs-lookup"><span data-stu-id="ea234-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="ea234-132">Le guide décrit les étapes nécessaires à la configuration de Unity et de MRTK pour utiliser le pipeline du kit de développement logiciel (SDK) XR pour Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="ea234-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="ea234-133">OpenXR (préversion)</span><span class="sxs-lookup"><span data-stu-id="ea234-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea234-134">OpenXR dans Unity est pris en charge uniquement sur Unity 2020,2 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ea234-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="ea234-135">Actuellement, il prend également en charge uniquement les versions x64 et ARM64.</span><span class="sxs-lookup"><span data-stu-id="ea234-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="ea234-136">Suivez les étapes de la section [utilisation du plug-in OpenXR de la réalité mixte pour Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, y compris les étapes de configuration de la gestion et de l’optimisation du plug-in XR pour installer le plug-in OpenXR dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="ea234-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="ea234-137">Assurez-vous que les éléments suivants ont été correctement installés :</span><span class="sxs-lookup"><span data-stu-id="ea234-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="ea234-138">Gestion du plug-in XR</span><span class="sxs-lookup"><span data-stu-id="ea234-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="ea234-139">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="ea234-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="ea234-140">Plug-in OpenXR de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="ea234-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="ea234-141">Accédez à modifier > paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="ea234-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="ea234-142">Cliquez sur l’onglet gestion du plug-in XR dans la fenêtre Paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="ea234-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="ea234-143">Vérifiez que l’option initialiser XR au démarrage est cochée.</span><span class="sxs-lookup"><span data-stu-id="ea234-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="ea234-144">(**_Facultatif_**) Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez ensemble de fonctionnalités Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ea234-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Gestion des plug-ins ouverte XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="ea234-146">Si vous avez un projet préexistant qui utilise MRTK à partir de UPM, assurez-vous que la ligne suivante se trouve dans le fichier **link.xml** situé dans le dossier MixedRealityToolkit. generated.</span><span class="sxs-lookup"><span data-stu-id="ea234-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="ea234-147">Pour la version initiale de MRTK et OpenXR, seuls les contrôleurs de mouvement HoloLens 2 et Windows Mixed Reality sont pris en charge en mode natif.</span><span class="sxs-lookup"><span data-stu-id="ea234-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="ea234-148">La prise en charge d’un matériel supplémentaire sera ajoutée dans les versions à venir.</span><span class="sxs-lookup"><span data-stu-id="ea234-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="ea234-149">Configuration de MRTK pour le pipeline du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="ea234-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="ea234-150">Si vous utilisez OpenXR, choisissez « DefaultOpenXRConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.</span><span class="sxs-lookup"><span data-stu-id="ea234-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ea234-151">Si vous utilisez d’autres runtimes XR dans la configuration de gestion du plug-in XR, comme Windows Mixed Reality ou Oculus, choisissez « DefaultXRSDKConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.</span><span class="sxs-lookup"><span data-stu-id="ea234-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ea234-152">Ces profils sont configurés avec les systèmes et fournisseurs appropriés, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ea234-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="ea234-153">Pour plus d’informations sur le profil et l’exemple de prise en charge avec XR SDK, consultez [la documentation](../features/profiles/profiles.md#xr-sdk) relative aux profils.</span><span class="sxs-lookup"><span data-stu-id="ea234-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="ea234-154">Pour migrer un profil existant vers le kit de développement logiciel (SDK) XR, les services et fournisseurs de données suivants doivent être mis à jour :</span><span class="sxs-lookup"><span data-stu-id="ea234-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="ea234-155">Appareil photo</span><span class="sxs-lookup"><span data-stu-id="ea234-155">Camera</span></span>

<span data-ttu-id="ea234-156">De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="ea234-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Paramètres de l’appareil photo hérité](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="ea234-158">to</span><span class="sxs-lookup"><span data-stu-id="ea234-158">to</span></span>

| <span data-ttu-id="ea234-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ea234-159">OpenXR</span></span> | <span data-ttu-id="ea234-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ea234-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="ea234-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**et**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="ea234-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Paramètres de l’appareil photo SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="ea234-163">Entrée</span><span class="sxs-lookup"><span data-stu-id="ea234-163">Input</span></span>

<span data-ttu-id="ea234-164">De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="ea234-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Paramètres d’entrée hérités](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="ea234-166">to</span><span class="sxs-lookup"><span data-stu-id="ea234-166">to</span></span>

| <span data-ttu-id="ea234-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ea234-167">OpenXR</span></span> | <span data-ttu-id="ea234-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ea234-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="ea234-169">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="ea234-169">__OpenXR__:</span></span>

![Paramètres d’entrée OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="ea234-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="ea234-171">__Windows Mixed Reality__:</span></span>

![Paramètres d’entrée du SDK XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="ea234-173">Limite</span><span class="sxs-lookup"><span data-stu-id="ea234-173">Boundary</span></span>

<span data-ttu-id="ea234-174">De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="ea234-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Paramètres des limites héritées](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="ea234-176">to</span><span class="sxs-lookup"><span data-stu-id="ea234-176">to</span></span>

| <span data-ttu-id="ea234-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ea234-177">OpenXR</span></span> | <span data-ttu-id="ea234-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ea234-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Paramètres des limites du SDK XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="ea234-180">Sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="ea234-180">Spatial awareness</span></span>

<span data-ttu-id="ea234-181">De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="ea234-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Paramètres de sensibilisation spatiale hérités](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="ea234-183">to</span><span class="sxs-lookup"><span data-stu-id="ea234-183">to</span></span>

| <span data-ttu-id="ea234-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ea234-184">OpenXR</span></span> | <span data-ttu-id="ea234-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ea234-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="ea234-186">En cours</span><span class="sxs-lookup"><span data-stu-id="ea234-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Paramètres de sensibilisation spatiale du SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="ea234-188">Mappages de contrôleur</span><span class="sxs-lookup"><span data-stu-id="ea234-188">Controller mappings</span></span>

<span data-ttu-id="ea234-189">Si vous utilisez des profils de mappage de contrôleur personnalisés, ouvrez l’un d’eux et exécutez la boîte à outils de réalité mixte-> utilitaires-> mise à jour-> les profils de mappage de contrôleur pour vous assurer que les nouveaux types de contrôleur du kit de développement logiciel (SDK) XR sont définis.</span><span class="sxs-lookup"><span data-stu-id="ea234-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea234-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea234-190">See also</span></span>

* [<span data-ttu-id="ea234-191">Prise en main du développement de clients dans Unity</span><span class="sxs-lookup"><span data-stu-id="ea234-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="ea234-192">Prise en main du développement VR dans Unity</span><span class="sxs-lookup"><span data-stu-id="ea234-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)