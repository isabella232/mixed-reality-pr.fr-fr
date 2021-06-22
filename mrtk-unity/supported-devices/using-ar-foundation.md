---
title: Génération et déploiement sur Android et iOS via AR Foundation
description: Documentation pour configurer MRTK pour Android et iOS (ARFoundation) dans Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, de réalité mixte, développement, MRTK, AR Core, kit AR, iOS, IOS, Android, comptabilité basique
ms.openlocfilehash: 352afbbc11c7cc6fcd2557395c5dd36d956f396d
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449738"
---
# <a name="building-and-deploying-to-android-and-ios-via-ar-foundation-experimental"></a><span data-ttu-id="8fd80-104">Génération et déploiement sur Android et iOS via AR Foundation [expérimental]</span><span class="sxs-lookup"><span data-stu-id="8fd80-104">Building and Deploying to Android and iOS via AR Foundation [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="8fd80-105">Installer les packages nécessaires</span><span class="sxs-lookup"><span data-stu-id="8fd80-105">Install required packages</span></span>

1. <span data-ttu-id="8fd80-106">Téléchargez et importez le package **Microsoft. MixedReality. Toolkit. Unity. Foundation** à partir de [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) ou du [Gestionnaire de package Unity](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="8fd80-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="8fd80-107">Dans le gestionnaire de package Unity (UPM), installez les packages suivants :</span><span class="sxs-lookup"><span data-stu-id="8fd80-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="8fd80-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="8fd80-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="8fd80-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="8fd80-109">**Android**</span></span> | <span data-ttu-id="8fd80-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8fd80-110">**iOS**</span></span> | <span data-ttu-id="8fd80-111">Commentaires</span><span class="sxs-lookup"><span data-stu-id="8fd80-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="8fd80-112">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="8fd80-112">AR Foundation</span></span>  <br/> <span data-ttu-id="8fd80-113">Version : 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="8fd80-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="8fd80-114">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="8fd80-114">AR Foundation</span></span>  <br/> <span data-ttu-id="8fd80-115">Version : 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="8fd80-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="8fd80-116">Pour Unity 2018,4, ce package est inclus en tant que version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="8fd80-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="8fd80-117">Pour afficher le package : `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="8fd80-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="8fd80-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="8fd80-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8fd80-119">Version : 2.1.2</span><span class="sxs-lookup"><span data-stu-id="8fd80-119">Version: 2.1.2</span></span> | <span data-ttu-id="8fd80-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="8fd80-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8fd80-121">Version : 2.1.2</span><span class="sxs-lookup"><span data-stu-id="8fd80-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="8fd80-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="8fd80-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="8fd80-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="8fd80-123">**Android**</span></span> | <span data-ttu-id="8fd80-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8fd80-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="8fd80-125">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="8fd80-125">AR Foundation</span></span>  <br/> <span data-ttu-id="8fd80-126">Version : 2.1.8</span><span class="sxs-lookup"><span data-stu-id="8fd80-126">Version: 2.1.8</span></span> |  <span data-ttu-id="8fd80-127">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="8fd80-127">AR Foundation</span></span>  <br/> <span data-ttu-id="8fd80-128">Version : 2.1.8</span><span class="sxs-lookup"><span data-stu-id="8fd80-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="8fd80-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="8fd80-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8fd80-130">Version : 2.1.11</span><span class="sxs-lookup"><span data-stu-id="8fd80-130">Version: 2.1.11</span></span> | <span data-ttu-id="8fd80-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="8fd80-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8fd80-132">Version : 2.1.9</span><span class="sxs-lookup"><span data-stu-id="8fd80-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="8fd80-133">**Unity 2020.3. x**</span><span class="sxs-lookup"><span data-stu-id="8fd80-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="8fd80-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="8fd80-134">**Android**</span></span> | <span data-ttu-id="8fd80-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8fd80-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="8fd80-136">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="8fd80-136">AR Foundation</span></span>  <br/> <span data-ttu-id="8fd80-137">Version : 3.1.3</span><span class="sxs-lookup"><span data-stu-id="8fd80-137">Version: 3.1.3</span></span> |  <span data-ttu-id="8fd80-138">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="8fd80-138">AR Foundation</span></span>  <br/> <span data-ttu-id="8fd80-139">Version : 4.0.12</span><span class="sxs-lookup"><span data-stu-id="8fd80-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="8fd80-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="8fd80-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8fd80-141">Version : 3.1.4</span><span class="sxs-lookup"><span data-stu-id="8fd80-141">Version: 3.1.4</span></span> | <span data-ttu-id="8fd80-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="8fd80-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8fd80-143">Version : 4.1.7</span><span class="sxs-lookup"><span data-stu-id="8fd80-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="8fd80-144">Mettez à jour les définitions de script MRTK Unity en appelant l’élément de menu : **Mixed reality > Toolkit > Utilities > unity > de mise à jour des scripts de mise à jour définit**</span><span class="sxs-lookup"><span data-stu-id="8fd80-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Les scripts de mise à jour définissent](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="8fd80-146">Activation du fournisseur de paramètres d’appareil photo Unity AR</span><span class="sxs-lookup"><span data-stu-id="8fd80-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="8fd80-147">Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="8fd80-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="8fd80-148">Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.</span><span class="sxs-lookup"><span data-stu-id="8fd80-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="8fd80-149">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="8fd80-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="8fd80-151">Sélectionnez **copier et personnaliser** pour cloner le profil MRTK afin d’activer la configuration personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8fd80-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Cloner le profil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="8fd80-153">Sélectionnez **clone** en regard du profil de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="8fd80-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Cloner le profil de la caméra MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="8fd80-155">Dans le panneau de l’inspecteur, accédez à la section système de l’appareil photo et développez la section paramètres de l' **appareil photo** .</span><span class="sxs-lookup"><span data-stu-id="8fd80-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Développez Paramètres fournisseurs](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="8fd80-157">Cliquez sur **Ajouter un fournisseur de paramètres d’appareil photo** , puis développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.</span><span class="sxs-lookup"><span data-stu-id="8fd80-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Développer le nouveau fournisseur de paramètres](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="8fd80-159">Sélectionner le fournisseur de paramètres de l’appareil Unity AR</span><span class="sxs-lookup"><span data-stu-id="8fd80-159">Select the Unity AR Camera Settings provider</span></span>

    ![Sélectionner le fournisseur de paramètres Unity](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="8fd80-161">Pour plus d’informations sur la configuration du fournisseur de paramètres de l’appareil Unity AR, fournisseur des paramètres de l' [appareil Unity AR](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8fd80-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8fd80-162">Cette installation vérifie (au démarrage de l’application) si les composants de fondation de base se trouvent dans la scène.</span><span class="sxs-lookup"><span data-stu-id="8fd80-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="8fd80-163">Si ce n’est pas le cas, ils sont automatiquement ajoutés pour qu’ils fonctionnent avec ARCore et ARKit.</span><span class="sxs-lookup"><span data-stu-id="8fd80-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="8fd80-164">Si vous devez définir un comportement spécifique, vous devez ajouter les composants dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="8fd80-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="8fd80-165">Pour plus d’informations sur les composants et l’installation de comptabilité clients, consultez cette [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="8fd80-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="8fd80-166">Création d’une scène pour les appareils Android et iOS</span><span class="sxs-lookup"><span data-stu-id="8fd80-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="8fd80-167">Vérifiez que vous avez ajouté le fournisseur de paramètres d’appareil photo Unity à votre scène.</span><span class="sxs-lookup"><span data-stu-id="8fd80-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="8fd80-168">Basculer la plateforme sur Android ou iOS dans les paramètres de build Unity</span><span class="sxs-lookup"><span data-stu-id="8fd80-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="8fd80-169">Vérifier que le fournisseur de gestion du plug-in XR associé est activé</span><span class="sxs-lookup"><span data-stu-id="8fd80-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="8fd80-170">Gestion du plug-in XR iOS :  ![ gestion du plug-in XR iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="8fd80-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="8fd80-171">Générer et exécuter la scène</span><span class="sxs-lookup"><span data-stu-id="8fd80-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="8fd80-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fd80-172">See also</span></span>

- [<span data-ttu-id="8fd80-173">Paramètres de l’appareil Unity AR</span><span class="sxs-lookup"><span data-stu-id="8fd80-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
