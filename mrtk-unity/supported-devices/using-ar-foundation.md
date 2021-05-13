---
title: UsingARFoundation
description: Documentation relative à l’utilisation de ARFoundation dans Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, AR Core, kit AR
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852365"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="b4924-104">Configuration de MRTK pour iOS et Android [expérimental]</span><span class="sxs-lookup"><span data-stu-id="b4924-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="b4924-105">Installer les packages nécessaires</span><span class="sxs-lookup"><span data-stu-id="b4924-105">Install required packages</span></span>

1. <span data-ttu-id="b4924-106">Téléchargez et importez le package **Microsoft. MixedReality. Toolkit. Unity. Foundation** à partir de [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) ou du [Gestionnaire de package Unity](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="b4924-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="b4924-107">Dans le gestionnaire de package Unity (UPM), installez les packages suivants :</span><span class="sxs-lookup"><span data-stu-id="b4924-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="b4924-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="b4924-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="b4924-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="b4924-109">**Android**</span></span> | <span data-ttu-id="b4924-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="b4924-110">**iOS**</span></span> | <span data-ttu-id="b4924-111">Commentaires</span><span class="sxs-lookup"><span data-stu-id="b4924-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="b4924-112">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="b4924-112">AR Foundation</span></span>  <br/> <span data-ttu-id="b4924-113">Version : 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="b4924-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="b4924-114">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="b4924-114">AR Foundation</span></span>  <br/> <span data-ttu-id="b4924-115">Version : 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="b4924-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="b4924-116">Pour Unity 2018,4, ce package est inclus en tant que version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="b4924-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="b4924-117">Pour afficher le package : `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="b4924-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="b4924-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="b4924-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="b4924-119">Version : 2.1.2</span><span class="sxs-lookup"><span data-stu-id="b4924-119">Version: 2.1.2</span></span> | <span data-ttu-id="b4924-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="b4924-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="b4924-121">Version : 2.1.2</span><span class="sxs-lookup"><span data-stu-id="b4924-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="b4924-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="b4924-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="b4924-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="b4924-123">**Android**</span></span> | <span data-ttu-id="b4924-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="b4924-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="b4924-125">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="b4924-125">AR Foundation</span></span>  <br/> <span data-ttu-id="b4924-126">Version : 2.1.8</span><span class="sxs-lookup"><span data-stu-id="b4924-126">Version: 2.1.8</span></span> |  <span data-ttu-id="b4924-127">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="b4924-127">AR Foundation</span></span>  <br/> <span data-ttu-id="b4924-128">Version : 2.1.8</span><span class="sxs-lookup"><span data-stu-id="b4924-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="b4924-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="b4924-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="b4924-130">Version : 2.1.11</span><span class="sxs-lookup"><span data-stu-id="b4924-130">Version: 2.1.11</span></span> | <span data-ttu-id="b4924-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="b4924-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="b4924-132">Version : 2.1.9</span><span class="sxs-lookup"><span data-stu-id="b4924-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="b4924-133">**Unity 2020.1. x (non prise en charge pour l’instant, incluse à titre d’information uniquement)**</span><span class="sxs-lookup"><span data-stu-id="b4924-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="b4924-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="b4924-134">**Android**</span></span> | <span data-ttu-id="b4924-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="b4924-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="b4924-136">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="b4924-136">AR Foundation</span></span>  <br/> <span data-ttu-id="b4924-137">Version : 3.1.3</span><span class="sxs-lookup"><span data-stu-id="b4924-137">Version: 3.1.3</span></span> |  <span data-ttu-id="b4924-138">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="b4924-138">AR Foundation</span></span>  <br/> <span data-ttu-id="b4924-139">Version : 3.1.3</span><span class="sxs-lookup"><span data-stu-id="b4924-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="b4924-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="b4924-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="b4924-141">Version : 3.1.4</span><span class="sxs-lookup"><span data-stu-id="b4924-141">Version: 3.1.4</span></span> | <span data-ttu-id="b4924-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="b4924-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="b4924-143">Version : 3.1.3</span><span class="sxs-lookup"><span data-stu-id="b4924-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="b4924-144">Mettez à jour les définitions de script MRTK Unity en appelant l’élément de menu : **Mixed Reality Toolkit > Utilities > unity > script Update définit**</span><span class="sxs-lookup"><span data-stu-id="b4924-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="b4924-145">Activation du fournisseur de paramètres d’appareil photo Unity AR</span><span class="sxs-lookup"><span data-stu-id="b4924-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="b4924-146">Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="b4924-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="b4924-147">Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.</span><span class="sxs-lookup"><span data-stu-id="b4924-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="b4924-148">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="b4924-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="b4924-150">Sélectionnez **copier et personnaliser** pour cloner le profil MRTK afin d’activer la configuration personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b4924-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Cloner le profil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="b4924-152">Sélectionnez **clone** en regard du profil de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="b4924-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Cloner le profil de la caméra MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="b4924-154">Dans le panneau de l’inspecteur, accédez à la section système de l’appareil photo et développez la section paramètres de l' **appareil photo** .</span><span class="sxs-lookup"><span data-stu-id="b4924-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Développez Paramètres fournisseurs](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="b4924-156">Cliquez sur **Ajouter un fournisseur de paramètres d’appareil photo** , puis développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.</span><span class="sxs-lookup"><span data-stu-id="b4924-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Développer le nouveau fournisseur de paramètres](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="b4924-158">Sélectionner le fournisseur de paramètres de l’appareil Unity AR</span><span class="sxs-lookup"><span data-stu-id="b4924-158">Select the Unity AR Camera Settings provider</span></span>

    ![Sélectionner le fournisseur de paramètres Unity](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="b4924-160">Pour plus d’informations sur la configuration du fournisseur de paramètres de l’appareil Unity AR, fournisseur des paramètres de l' [appareil Unity AR](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b4924-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b4924-161">Cette installation vérifie (au démarrage de l’application) si les composants de fondation de base se trouvent dans la scène.</span><span class="sxs-lookup"><span data-stu-id="b4924-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="b4924-162">Si ce n’est pas le cas, ils sont automatiquement ajoutés pour qu’ils fonctionnent avec ARCore et ARKit.</span><span class="sxs-lookup"><span data-stu-id="b4924-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="b4924-163">Si vous devez définir un comportement spécifique, vous devez ajouter les composants dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="b4924-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="b4924-164">Pour plus d’informations sur les composants et l’installation de comptabilité clients, consultez cette [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="b4924-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="b4924-165">Création d’une scène pour les appareils Android et iOS</span><span class="sxs-lookup"><span data-stu-id="b4924-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="b4924-166">Vérifiez que vous avez ajouté le fournisseur de paramètres d’appareil photo Unity à votre scène.</span><span class="sxs-lookup"><span data-stu-id="b4924-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="b4924-167">Basculer la plateforme sur Android ou iOS dans les paramètres de build Unity</span><span class="sxs-lookup"><span data-stu-id="b4924-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="b4924-168">Lorsque vous basculez la plateforme, vous devez voir la fenêtre du Configurateur de projet MRTK avec les paramètres de la plateforme que vous avez choisie.</span><span class="sxs-lookup"><span data-stu-id="b4924-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="b4924-169">Cliquez sur appliquer pour activer les paramètres spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="b4924-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="b4924-170">Paramètres du Configurateur de projet iOS</span><span class="sxs-lookup"><span data-stu-id="b4924-170">iOS Project Configurator Settings</span></span>

    ![Configurateur de projet iOS](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="b4924-172">Il n’y a aucune étape supplémentaire après avoir basculé la plateforme pour Android.</span><span class="sxs-lookup"><span data-stu-id="b4924-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="b4924-173">Si la plateforme est iOS, modifiez > paramètres du projet > lecteur > d’autres paramètres, sous l’en-tête optimisation, **décochez l’option** supprimer le code du moteur.</span><span class="sxs-lookup"><span data-stu-id="b4924-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Paramètres iOS](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="b4924-175">Le fait de décocher le code du moteur de bandes est la solution à terme pour une erreur dans Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="b4924-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="b4924-176">Nous travaillons sur une solution à long terme.</span><span class="sxs-lookup"><span data-stu-id="b4924-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="b4924-177">Générer et exécuter la scène</span><span class="sxs-lookup"><span data-stu-id="b4924-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="b4924-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4924-178">See also</span></span>

- [<span data-ttu-id="b4924-179">Paramètres de l’appareil Unity AR</span><span class="sxs-lookup"><span data-stu-id="b4924-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
