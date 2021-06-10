---
title: Prise en main de MRTK et du kit de développement logiciel (SDK) XR
description: Page d’accueil de MRTK avec le kit de développement logiciel (SDK) XR
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, XRSDK, SDK XR
ms.openlocfilehash: 01aca42ab4e883d26a814a1572d39eda7576ab57
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908386"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="94e49-104">Prise en main de MRTK et du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="94e49-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="94e49-105">Le kit de développement logiciel (SDK) XR est le [nouveau pipeline XR unity 2019,3 et ultérieur](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="94e49-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="94e49-106">Dans Unity 2019, il fournit une alternative au pipeline XR existant.</span><span class="sxs-lookup"><span data-stu-id="94e49-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="94e49-107">Dans Unity 2020, il s’agit du seul pipeline XR dans Unity.</span><span class="sxs-lookup"><span data-stu-id="94e49-107">In Unity 2020, it is the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94e49-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="94e49-108">Prerequisites</span></span>

<span data-ttu-id="94e49-109">Pour commencer à utiliser le Toolkit de réalité mixte, suivez [les étapes fournies](../install-the-tools.md#importing-the-mixed-reality-toolkit) pour ajouter MRTK à un projet.</span><span class="sxs-lookup"><span data-stu-id="94e49-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="94e49-110">Configuration d’Unity pour le pipeline du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="94e49-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="94e49-111">Le pipeline du kit de développement logiciel (SDK) XR prend actuellement en charge 3 plateformes : Windows Mixed Reality, Oculus et OpenXR.</span><span class="sxs-lookup"><span data-stu-id="94e49-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="94e49-112">Les sections ci-dessous décrivent les étapes nécessaires à la configuration du kit de développement logiciel (SDK) XR pour chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="94e49-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="94e49-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="94e49-113">Windows Mixed Reality</span></span>

<span data-ttu-id="94e49-114">Accédez au **Gestionnaire de package de Unity** et installez le package de plug-in XR Windows, qui ajoute la prise en charge de Windows Mixed Reality dans le kit de développement logiciel (SDK) XR.</span><span class="sxs-lookup"><span data-stu-id="94e49-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="94e49-115">Cela entraîne également l’extraction de quelques packages de dépendance.</span><span class="sxs-lookup"><span data-stu-id="94e49-115">This will pull down a few dependency packages as well.</span></span>

1. <span data-ttu-id="94e49-116">Vérifiez que les éléments suivants ont été correctement installés :</span><span class="sxs-lookup"><span data-stu-id="94e49-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="94e49-117">Gestion du plug-in XR</span><span class="sxs-lookup"><span data-stu-id="94e49-117">XR Plugin Management</span></span>
   * <span data-ttu-id="94e49-118">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="94e49-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="94e49-119">XR des assistances d’entrée héritées</span><span class="sxs-lookup"><span data-stu-id="94e49-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="94e49-120">Accédez à **Edit > Project Settings**.</span><span class="sxs-lookup"><span data-stu-id="94e49-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="94e49-121">Cliquez sur l’onglet gestion du plug-in XR dans la fenêtre Paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="94e49-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="94e49-122">Accédez aux paramètres de plateforme Windows universelle et vérifiez que Windows Mixed Reality est vérifié sous les fournisseurs de plug-in.</span><span class="sxs-lookup"><span data-stu-id="94e49-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="94e49-123">Vérifiez que l’option initialiser XR au démarrage est cochée.</span><span class="sxs-lookup"><span data-stu-id="94e49-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="94e49-124">(**_Requis pour la communication à distance HoloLens dans l’éditeur, sinon facultatif_**) Accédez aux paramètres autonomes et assurez-vous que Windows Mixed Reality est coché sous fournisseurs de plug-ins.</span><span class="sxs-lookup"><span data-stu-id="94e49-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="94e49-125">Vérifiez également que l’option initialiser XR au démarrage est cochée.</span><span class="sxs-lookup"><span data-stu-id="94e49-125">Also ensure that Initialize XR on Startup is checked.</span></span>

    ![Onglet gestion du plug-in XR avec option autonome sélectionnée](images/xr-management-img-02.png)

7. <span data-ttu-id="94e49-127">(**_Facultatif_**) Cliquez sur l’onglet Windows Mixed Reality sous gestion du plug-in XR, puis créez un profil de paramètres personnalisés pour modifier les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="94e49-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="94e49-128">Si la liste des paramètres existe déjà, aucun profil ne doit être créé.</span><span class="sxs-lookup"><span data-stu-id="94e49-128">If the list of settings are already there, no profile needs to be created.</span></span>

    ![Onglet gestion du plug-in XR avec Windows sélectionné](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="94e49-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="94e49-130">Oculus</span></span>

1. <span data-ttu-id="94e49-131">Pour terminer, suivez la [procédure de configuration de Oculus Quest dans MRTK à l’aide du Guide de pipeline du kit de développement logiciel (SDK) XR](../supported-devices/oculus-quest-mrtk.md) .</span><span class="sxs-lookup"><span data-stu-id="94e49-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="94e49-132">Le guide décrit les étapes nécessaires à la configuration de Unity et de MRTK pour utiliser le pipeline du kit de développement logiciel (SDK) XR pour Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="94e49-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="94e49-133">OpenXR (préversion)</span><span class="sxs-lookup"><span data-stu-id="94e49-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94e49-134">OpenXR dans Unity est pris en charge uniquement sur Unity 2020,2 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="94e49-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
> <span data-ttu-id="94e49-135">Il prend également en charge uniquement les versions x64, ARM et ARM64.</span><span class="sxs-lookup"><span data-stu-id="94e49-135">It also only supports x64, ARM, and ARM64 builds.</span></span>

1. <span data-ttu-id="94e49-136">Suivez les étapes de la section [utilisation du plug-in OpenXR de la réalité mixte pour Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, y compris les étapes de configuration de la gestion et de l’optimisation du plug-in XR pour installer le plug-in OpenXR dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="94e49-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="94e49-137">Assurez-vous que les éléments suivants ont été correctement installés :</span><span class="sxs-lookup"><span data-stu-id="94e49-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="94e49-138">Gestion du plug-in XR</span><span class="sxs-lookup"><span data-stu-id="94e49-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="94e49-139">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="94e49-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="94e49-140">Plug-in OpenXR de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="94e49-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="94e49-141">Accédez à modifier > paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="94e49-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="94e49-142">Cliquez sur l’onglet gestion du plug-in XR dans la fenêtre Paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="94e49-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="94e49-143">Vérifiez que l’option initialiser XR au démarrage est cochée.</span><span class="sxs-lookup"><span data-stu-id="94e49-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="94e49-144">(**_Facultatif_**) Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez ensemble de fonctionnalités Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="94e49-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![OpenXR gestion des plug-ins](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="94e49-146">Si vous avez un projet préexistant qui utilise MRTK à partir de UPM, assurez-vous que la ligne suivante se trouve dans le fichier **link.xml** situé dans le dossier MixedRealityToolkit. generated.</span><span class="sxs-lookup"><span data-stu-id="94e49-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="94e49-147">Pour la version initiale de MRTK et OpenXR, seuls les contrôleurs de mouvement HoloLens 2 et Windows Mixed Reality sont pris en charge en mode natif.</span><span class="sxs-lookup"><span data-stu-id="94e49-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="94e49-148">La prise en charge d’un matériel supplémentaire sera ajoutée dans les versions à venir.</span><span class="sxs-lookup"><span data-stu-id="94e49-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="94e49-149">Configuration de MRTK pour le pipeline du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="94e49-149">Configuring MRTK for the XR SDK pipeline</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="94e49-150">Utilisez l’un des profils MRTK par défaut, qui sont tous configurés dans les pipelines XR d’Unity.</span><span class="sxs-lookup"><span data-stu-id="94e49-150">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="94e49-151">Les « DefaultOpenXRConfigurationProfile » et « DefaultXRSDKConfigurationProfile » précédents sont maintenant marqués comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="94e49-151">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="94e49-152">Si vous utilisez OpenXR, choisissez « DefaultOpenXRConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.</span><span class="sxs-lookup"><span data-stu-id="94e49-152">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="94e49-153">Si vous utilisez d’autres runtimes XR dans la configuration de gestion du plug-in XR, comme Windows Mixed Reality ou Oculus, choisissez « DefaultXRSDKConfigurationProfile » comme profil actif ou clonez-le pour effectuer des personnalisations.</span><span class="sxs-lookup"><span data-stu-id="94e49-153">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="94e49-154">Ces profils sont configurés avec les systèmes et fournisseurs appropriés, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="94e49-154">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="94e49-155">Pour plus d’informations sur le profil et l’exemple de prise en charge avec XR SDK, consultez [la documentation](../features/profiles/profiles.md#xr-sdk) relative aux profils.</span><span class="sxs-lookup"><span data-stu-id="94e49-155">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>
::: moniker-end

<span data-ttu-id="94e49-156">Pour migrer un profil existant vers le kit de développement logiciel (SDK) XR, les services et fournisseurs de données suivants doivent être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="94e49-156">To migrate an existing profile to XR SDK, the following services and data providers should be updated.</span></span>
::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="94e49-157">Vous pourrez voir les nouveaux fournisseurs de données sous l’onglet Kit de développement logiciel (SDK) XR dans Unity 2019 ou dans l’affichage principal/uniquement dans Unity 2020 +, où Legacy XR n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="94e49-157">You will be able to see the new data providers under the XR SDK tab in Unity 2019, or in the main/only view in Unity 2020+, where legacy XR doesn't exist.</span></span>

![Onglet Kit de développement logiciel (SDK) XR](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a><span data-ttu-id="94e49-159">Appareil photo</span><span class="sxs-lookup"><span data-stu-id="94e49-159">Camera</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="94e49-160">Ajouter les fournisseurs de données suivants</span><span class="sxs-lookup"><span data-stu-id="94e49-160">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="94e49-161">De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="94e49-161">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Paramètres de l’appareil photo hérité](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="94e49-163">to</span><span class="sxs-lookup"><span data-stu-id="94e49-163">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="94e49-164">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="94e49-164">OpenXR Plugin</span></span> | <span data-ttu-id="94e49-165">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="94e49-165">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="94e49-166">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="94e49-166">OpenXR Plugin</span></span> | <span data-ttu-id="94e49-167">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="94e49-167">Windows XR Plugin</span></span> |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Paramètres de l’appareil photo SDK XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="94e49-169">Entrée</span><span class="sxs-lookup"><span data-stu-id="94e49-169">Input</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="94e49-170">Ajouter les fournisseurs de données suivants</span><span class="sxs-lookup"><span data-stu-id="94e49-170">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="94e49-171">De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="94e49-171">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Paramètres d’entrée hérités](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="94e49-173">to</span><span class="sxs-lookup"><span data-stu-id="94e49-173">to</span></span>
::: moniker-end

| <span data-ttu-id="94e49-174">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="94e49-174">OpenXR Plugin</span></span> | <span data-ttu-id="94e49-175">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="94e49-175">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="94e49-176">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="94e49-176">__OpenXR__:</span></span>

![Paramètres d’entrée OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="94e49-178">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="94e49-178">__Windows Mixed Reality__:</span></span>

![Paramètres d’entrée du SDK XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="94e49-180">Limite</span><span class="sxs-lookup"><span data-stu-id="94e49-180">Boundary</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="94e49-181">Ajouter les fournisseurs de données suivants</span><span class="sxs-lookup"><span data-stu-id="94e49-181">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="94e49-182">De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="94e49-182">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Paramètres des limites héritées](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="94e49-184">to</span><span class="sxs-lookup"><span data-stu-id="94e49-184">to</span></span>
::: moniker-end

| <span data-ttu-id="94e49-185">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="94e49-185">OpenXR Plugin</span></span> | <span data-ttu-id="94e49-186">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="94e49-186">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Paramètres des limites du SDK XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="94e49-188">Sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="94e49-188">Spatial awareness</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="94e49-189">Ajouter les fournisseurs de données suivants</span><span class="sxs-lookup"><span data-stu-id="94e49-189">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="94e49-190">De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="94e49-190">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Paramètres de sensibilisation spatiale hérités](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="94e49-192">to</span><span class="sxs-lookup"><span data-stu-id="94e49-192">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="94e49-193">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="94e49-193">OpenXR Plugin</span></span> | <span data-ttu-id="94e49-194">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="94e49-194">Windows XR Plugin</span></span> |
|---------------|-------------------|
| <span data-ttu-id="94e49-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (pour UWP)</span><span class="sxs-lookup"><span data-stu-id="94e49-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (for UWP)</span></span> | <span data-ttu-id="94e49-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (pour UWP)</span><span class="sxs-lookup"><span data-stu-id="94e49-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (for UWP)</span></span> |
| <span data-ttu-id="94e49-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (pour les plateformes non UWP)</span><span class="sxs-lookup"><span data-stu-id="94e49-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (for non-UWP)</span></span> | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="94e49-198">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="94e49-198">OpenXR Plugin</span></span> | <span data-ttu-id="94e49-199">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="94e49-199">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Paramètres de sensibilisation spatiale du SDK XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="94e49-201">Mappages de contrôleur</span><span class="sxs-lookup"><span data-stu-id="94e49-201">Controller mappings</span></span>

<span data-ttu-id="94e49-202">Si vous utilisez des profils de mappage de contrôleur personnalisés, ouvrez l’un d’eux et exécutez la boîte à outils de réalité mixte-> utilitaires-> mise à jour-> les profils de mappage de contrôleur pour vous assurer que les nouveaux types de contrôleur du kit de développement logiciel (SDK) XR sont définis.</span><span class="sxs-lookup"><span data-stu-id="94e49-202">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="94e49-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94e49-203">See also</span></span>

* [<span data-ttu-id="94e49-204">Prise en main du développement de clients dans Unity</span><span class="sxs-lookup"><span data-stu-id="94e49-204">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="94e49-205">Prise en main du développement VR dans Unity</span><span class="sxs-lookup"><span data-stu-id="94e49-205">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
