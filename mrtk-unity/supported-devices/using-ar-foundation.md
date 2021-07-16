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
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a><span data-ttu-id="a34dd-104">Déploiement sur Android et iOS (AR Foundation) [expérimental]</span><span class="sxs-lookup"><span data-stu-id="a34dd-104">Deploying to Android and iOS (AR Foundation) [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="a34dd-105">Installer les packages nécessaires</span><span class="sxs-lookup"><span data-stu-id="a34dd-105">Install required packages</span></span>

1. <span data-ttu-id="a34dd-106">téléchargez et importez le fichier **Microsoft. MixedReality. Shared Computer Toolkit. package unity. Foundation** , [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) ou [unity Gestionnaire de package](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="a34dd-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="a34dd-107">dans l’Gestionnaire de package unity (UPM), installez les packages suivants :</span><span class="sxs-lookup"><span data-stu-id="a34dd-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="a34dd-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="a34dd-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="a34dd-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="a34dd-109">**Android**</span></span> | <span data-ttu-id="a34dd-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a34dd-110">**iOS**</span></span> | <span data-ttu-id="a34dd-111">Commentaires</span><span class="sxs-lookup"><span data-stu-id="a34dd-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="a34dd-112">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="a34dd-112">AR Foundation</span></span>  <br/> <span data-ttu-id="a34dd-113">Version : 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="a34dd-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="a34dd-114">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="a34dd-114">AR Foundation</span></span>  <br/> <span data-ttu-id="a34dd-115">Version : 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="a34dd-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="a34dd-116">Pour Unity 2018,4, ce package est inclus en tant que version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="a34dd-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="a34dd-117">Pour afficher le package : `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="a34dd-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="a34dd-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="a34dd-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a34dd-119">Version : 2.1.2</span><span class="sxs-lookup"><span data-stu-id="a34dd-119">Version: 2.1.2</span></span> | <span data-ttu-id="a34dd-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="a34dd-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a34dd-121">Version : 2.1.2</span><span class="sxs-lookup"><span data-stu-id="a34dd-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="a34dd-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="a34dd-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="a34dd-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="a34dd-123">**Android**</span></span> | <span data-ttu-id="a34dd-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a34dd-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="a34dd-125">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="a34dd-125">AR Foundation</span></span>  <br/> <span data-ttu-id="a34dd-126">Version : 2.1.8</span><span class="sxs-lookup"><span data-stu-id="a34dd-126">Version: 2.1.8</span></span> |  <span data-ttu-id="a34dd-127">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="a34dd-127">AR Foundation</span></span>  <br/> <span data-ttu-id="a34dd-128">Version : 2.1.8</span><span class="sxs-lookup"><span data-stu-id="a34dd-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="a34dd-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="a34dd-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a34dd-130">Version : 2.1.11</span><span class="sxs-lookup"><span data-stu-id="a34dd-130">Version: 2.1.11</span></span> | <span data-ttu-id="a34dd-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="a34dd-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a34dd-132">Version : 2.1.9</span><span class="sxs-lookup"><span data-stu-id="a34dd-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="a34dd-133">**Unity 2020.3. x**</span><span class="sxs-lookup"><span data-stu-id="a34dd-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="a34dd-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="a34dd-134">**Android**</span></span> | <span data-ttu-id="a34dd-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a34dd-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="a34dd-136">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="a34dd-136">AR Foundation</span></span>  <br/> <span data-ttu-id="a34dd-137">Version : 3.1.3</span><span class="sxs-lookup"><span data-stu-id="a34dd-137">Version: 3.1.3</span></span> |  <span data-ttu-id="a34dd-138">Fondement de base</span><span class="sxs-lookup"><span data-stu-id="a34dd-138">AR Foundation</span></span>  <br/> <span data-ttu-id="a34dd-139">Version : 4.0.12</span><span class="sxs-lookup"><span data-stu-id="a34dd-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="a34dd-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="a34dd-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a34dd-141">Version : 3.1.4</span><span class="sxs-lookup"><span data-stu-id="a34dd-141">Version: 3.1.4</span></span> | <span data-ttu-id="a34dd-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="a34dd-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a34dd-143">Version : 4.1.7</span><span class="sxs-lookup"><span data-stu-id="a34dd-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="a34dd-144">mettez à jour les définitions de script MRTK unity en appelant l’élément de menu : **Mixed reality > Shared Computer Toolkit > Utilities > unity > script Update définit**</span><span class="sxs-lookup"><span data-stu-id="a34dd-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Les scripts de mise à jour définissent](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="a34dd-146">Activation du fournisseur de paramètres d’appareil photo Unity AR</span><span class="sxs-lookup"><span data-stu-id="a34dd-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="a34dd-147">Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="a34dd-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="a34dd-148">Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.</span><span class="sxs-lookup"><span data-stu-id="a34dd-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="a34dd-149">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="a34dd-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="a34dd-151">Sélectionnez **copier et personnaliser** pour cloner le profil MRTK afin d’activer la configuration personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a34dd-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Cloner le profil MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="a34dd-153">Sélectionnez **clone** en regard du profil de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="a34dd-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Cloner le profil de la caméra MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="a34dd-155">dans le panneau inspecteur, accédez à la section système de l’appareil photo et développez la section **camera Paramètres providers** .</span><span class="sxs-lookup"><span data-stu-id="a34dd-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Développez Paramètres fournisseurs](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="a34dd-157">cliquez sur **ajouter un appareil photo Paramètres fournisseur** et développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.</span><span class="sxs-lookup"><span data-stu-id="a34dd-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Développer le nouveau fournisseur de paramètres](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="a34dd-159">sélectionner le fournisseur de Paramètres unity AR</span><span class="sxs-lookup"><span data-stu-id="a34dd-159">Select the Unity AR Camera Settings provider</span></span>

    ![Sélectionner le fournisseur de paramètres Unity](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="a34dd-161">Pour plus d’informations sur la configuration du fournisseur de paramètres de l’appareil Unity AR, fournisseur des paramètres de l' [appareil Unity AR](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a34dd-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a34dd-162">Cette installation vérifie (au démarrage de l’application) si les composants de fondation de base se trouvent dans la scène.</span><span class="sxs-lookup"><span data-stu-id="a34dd-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="a34dd-163">Si ce n’est pas le cas, ils sont automatiquement ajoutés pour qu’ils fonctionnent avec ARCore et ARKit.</span><span class="sxs-lookup"><span data-stu-id="a34dd-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="a34dd-164">Si vous devez définir un comportement spécifique, vous devez ajouter les composants dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="a34dd-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="a34dd-165">Pour plus d’informations sur les composants et l’installation de comptabilité clients, consultez cette [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="a34dd-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="a34dd-166">Création d’une scène pour les appareils Android et iOS</span><span class="sxs-lookup"><span data-stu-id="a34dd-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="a34dd-167">assurez-vous que vous avez ajouté le fournisseur de Paramètres d’appareil photo unity à votre scène.</span><span class="sxs-lookup"><span data-stu-id="a34dd-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="a34dd-168">basculez la plateforme sur Android ou iOS dans la Build unity Paramètres</span><span class="sxs-lookup"><span data-stu-id="a34dd-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="a34dd-169">Vérifier que le fournisseur de gestion du plug-in XR associé est activé</span><span class="sxs-lookup"><span data-stu-id="a34dd-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="a34dd-170">Gestion du plug-in XR iOS :  ![ gestion du plug-in XR iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="a34dd-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="a34dd-171">Générer et exécuter la scène</span><span class="sxs-lookup"><span data-stu-id="a34dd-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="a34dd-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a34dd-172">See also</span></span>

- [<span data-ttu-id="a34dd-173">Paramètres de caméra unity AR</span><span class="sxs-lookup"><span data-stu-id="a34dd-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
