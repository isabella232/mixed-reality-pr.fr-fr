---
title: Azure Spatial Anchors pour Android et iOS
description: Suivez ce cours pour découvrir comment déployer un projet Unity avec Mixed Reality Toolkit (MRTK) et Azure Spatial Anchors sur Android et iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, android, ios, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403415"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="a752f-104">5. Azure Spatial Anchors pour Android et iOS</span><span class="sxs-lookup"><span data-stu-id="a752f-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="a752f-105">Dans ce tutoriel, vous allez découvrir comment créer votre projet pour des appareils Android et iOS à l’aide des packages AR Foundation, ARCore XR Plugin et ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="a752f-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="a752f-106">Objectifs</span><span class="sxs-lookup"><span data-stu-id="a752f-106">Objectives</span></span>

* <span data-ttu-id="a752f-107">Apprendre à générer votre projet sur votre appareil Android à l’aide des packages AR Foundation et ARCore XR Plugin de Unity</span><span class="sxs-lookup"><span data-stu-id="a752f-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="a752f-108">Apprendre à générer votre projet sur votre appareil iOS à l’aide des packages AR Foundation et ARKit XR Plugin de Unity</span><span class="sxs-lookup"><span data-stu-id="a752f-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="a752f-109">Installation de packages Unity intégrés</span><span class="sxs-lookup"><span data-stu-id="a752f-109">Installing inbuilt Unity packages</span></span>

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="a752f-110">Configurer MRTK pour l’appareil photo AR Foundation</span><span class="sxs-lookup"><span data-stu-id="a752f-110">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="a752f-111">Dans cette section, vous allez découvrir comment configurer MRTK pour le déploiement sur un appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="a752f-111">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="a752f-112">Dans la fenêtre de hiérarchie, sélectionnez l’objet **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="a752f-112">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="a752f-113">Ensuite, dans la fenêtre de l’inspecteur, sélectionnez l’onglet **Camera**, clonez le profil de la caméra et attribuez-lui un nom pertinent, par exemple **AzureSpatialAnchors_ARCameraProfile** :</span><span class="sxs-lookup"><span data-stu-id="a752f-113">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![Unity avec le profil nouvellement créé ARCameraProfile sélectionné](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a752f-115">Pour vous rappeler comment cloner des profils MRTK, vous pouvez consulter les instructions fournies dans [Configuration des profils Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="a752f-115">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="a752f-116">Avec l’onglet **Caméra** toujours sélectionné dans la fenêtre Inspecteur, développez les **Fournisseurs des paramètres de la caméra**, puis cliquez sur "-" pour supprimer le **Paramètre de la caméra Windows Mixed Reality** ou le **Paramètre de la caméra Windows Mixed Reality SDK XR** :</span><span class="sxs-lookup"><span data-stu-id="a752f-116">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and by clicking the "-" remove the **Windows Mixed Reality Camera Setting** or **XR SDK Windows Mixed Reality Camera Setting**:</span></span>

![<span data-ttu-id="a752f-117">Profil ARCameraProfile d’Unity avec ajout d’un nouveau fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="a752f-117">Unity ARCameraProfile with new data provider added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="a752f-118">et cliquez sur le bouton **+ Ajouter un fournisseur de paramètres de caméra**, puis développez le **Nouveau fournisseur de données** que vous venez d’ajouter :</span><span class="sxs-lookup"><span data-stu-id="a752f-118">and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider**:</span></span>

![Caméra de réalité augmentée ajoutée pour Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="a752f-120">À l’aide de la liste déroulante **Type**, sélectionnez le type **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings** :</span><span class="sxs-lookup"><span data-stu-id="a752f-120">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![Profil ARCameraProfile d’Unity avec le chemin vers la sélection du type de fournisseur de données](images/mr-learning-asa/asa-05-section2-step1-4.png)

<span data-ttu-id="a752f-122">Mettre à jour les définitions de script UnityAR MRTK en appelant l’élément de menu : **Mixed Reality** > **Toolkit** > **Utilitaires** > **UnityAR** > Mise à jour des définitions de script</span><span class="sxs-lookup"><span data-stu-id="a752f-122">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="a752f-123">Génération de votre application sur votre appareil Android</span><span class="sxs-lookup"><span data-stu-id="a752f-123">Building your application to your Android device</span></span>

<span data-ttu-id="a752f-124">Dans cette section, vous allez découvrir comment configurer votre projet pour le générer et le déployer sur un appareil Android.</span><span class="sxs-lookup"><span data-stu-id="a752f-124">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="a752f-125">Dans le menu Unity, sélectionnez **File** > **Build Settings...** pour ouvrir la fenêtre Build Settings, puis basculez vers la plateforme Android :</span><span class="sxs-lookup"><span data-stu-id="a752f-125">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Fenêtre Build Settings d’Unity avec la plateforme Android sélectionnée](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="a752f-127">Pour vous rappeler comment changer de plateforme de génération, consultez les instructions fournies dans [Changement de la plateforme de génération](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="a752f-127">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="a752f-128">Fermez la fenêtre Build Settings.</span><span class="sxs-lookup"><span data-stu-id="a752f-128">Close the Build Settings window.</span></span>

<span data-ttu-id="a752f-129">Dans le menu Unity, sélectionnez **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer le projet pour MRTK** pour ouvrir la fenêtre **MRTK Project Configurator**, vérifiez que toutes les options sont sélectionnées, puis cliquez sur le bouton **Appliquer** pour appliquer les paramètres :</span><span class="sxs-lookup"><span data-stu-id="a752f-129">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![MRTK Project Configurator Unity 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="a752f-131">Dans le menu Unity, sélectionnez **Edit** > **Project Settings...** pour ouvrir la fenêtre Player Settings, recherchez la section **Player** >  **Other Settings**, sélectionnez **Vulkan** et supprimez-le en cliquant sur le symbole **« - »**  :</span><span class="sxs-lookup"><span data-stu-id="a752f-131">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Fenêtre Other Settings d’Unity avec Vulcan sélectionné](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

<span data-ttu-id="a752f-133">Dans la fenêtre Build Settings, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste des scènes de la build (**Scenes In Build**).</span><span class="sxs-lookup"><span data-stu-id="a752f-133">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="a752f-134">Ensuite, utilisez un câble USB pour connecter votre appareil Android à votre ordinateur et sélectionnez-le dans la liste déroulante **Run Device** :</span><span class="sxs-lookup"><span data-stu-id="a752f-134">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![Fenêtre Build Settings d’Unity avec la scène ajoutée et Run Device sélectionné](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="a752f-136">Si votre appareil n’apparaît pas dans la liste déroulante Run Device, vous devrez peut-être appuyer sur le bouton Refresh à côté de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a752f-136">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="a752f-137">Dans la fenêtre Build Settings, cliquez sur le bouton **Build And Run** (Générer et exécuter) pour ouvrir la fenêtre Build Android.</span><span class="sxs-lookup"><span data-stu-id="a752f-137">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="a752f-138">Choisissez un emplacement approprié où stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, attribuez un nom pertinent à l’apk, par exemple _MRTKTutorials-AzureSpatialAnchors_, puis cliquez sur le bouton **Save** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="a752f-138">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Save - Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> <span data-ttu-id="a752f-140">Si vous recevez une erreur dans la fenêtre Unity Console relative aux modules Android SDK, NDK ou JDK, vous devez ouvrir Unity Hub et installer les modules Android Build Support associés.</span><span class="sxs-lookup"><span data-stu-id="a752f-140">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="a752f-141">Une fois le processus de génération terminé, vos applications doivent se charger automatiquement sur votre appareil Android.</span><span class="sxs-lookup"><span data-stu-id="a752f-141">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="a752f-142">Génération de votre application sur votre appareil iOS</span><span class="sxs-lookup"><span data-stu-id="a752f-142">Building your application to your iOS device</span></span>

<span data-ttu-id="a752f-143">Dans cette section, vous allez découvrir comment configurer votre projet pour le générer et le déployer sur votre appareil iOS.</span><span class="sxs-lookup"><span data-stu-id="a752f-143">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="a752f-144">Dans le menu Unity, sélectionnez **File** > **Build Settings...** pour ouvrir la fenêtre Build Settings et basculez vers la plateforme iOS :</span><span class="sxs-lookup"><span data-stu-id="a752f-144">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![Fenêtre Build Settings d’Unity avec iOS sélectionné](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="a752f-146">Pour vous rappeler comment changer de plateforme de génération, consultez les instructions fournies dans [Changement de la plateforme de génération](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="a752f-146">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="a752f-147">Fermez la fenêtre Build Settings.</span><span class="sxs-lookup"><span data-stu-id="a752f-147">Close the Build Settings window.</span></span>

<span data-ttu-id="a752f-148">Dans le menu Unity, sélectionnez **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer le projet pour MRTK** pour ouvrir la fenêtre **MRTK Project Configurator**, vérifiez que toutes les options sont sélectionnées, puis cliquez sur le bouton **Appliquer** pour appliquer les paramètres :</span><span class="sxs-lookup"><span data-stu-id="a752f-148">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Fenêtre MRTK Project Configurator d’Unity - iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

<span data-ttu-id="a752f-150">Dans le menu Unity, sélectionnez **Edit** > **Project Settings...** pour ouvrir la fenêtre Player Settings, recherchez la section **Player** >  **Other Settings**, et décochez la case **Strip Engine Code** (Supprimer le code du moteur) :</span><span class="sxs-lookup"><span data-stu-id="a752f-150">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![Fenêtre Other Settings d’Unity avec Strip Engine Code désactivé](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="a752f-152">Fermez la fenêtre Player Settings et rouvrez la fenêtre **Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="a752f-152">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="a752f-153">Dans la fenêtre Build Settings, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste des scènes de la build (**Scenes In Build**) :</span><span class="sxs-lookup"><span data-stu-id="a752f-153">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![Fenêtre Build Settings d’Unity avec une scène ajoutée](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="a752f-155">Dans la fenêtre Build Settings, cliquez sur le bouton **Build** pour ouvrir la fenêtre Build iOS.</span><span class="sxs-lookup"><span data-stu-id="a752f-155">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="a752f-156">Choisissez un emplacement approprié où stocker votre projet Xcode, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _MRTKTutorials-AzureSpatialAnchors_, puis cliquez sur le bouton **Select Folder** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="a752f-156">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Save - iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="a752f-158">Une fois le processus de génération terminé, suivez les instructions fournies dans [Exporter le projet Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) pour découvrir comment déployer votre projet Xcode sur votre appareil iOS.</span><span class="sxs-lookup"><span data-stu-id="a752f-158">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a752f-159">Félicitations</span><span class="sxs-lookup"><span data-stu-id="a752f-159">Congratulations</span></span>

<span data-ttu-id="a752f-160">Dans ce tutoriel, vous avez appris à générer votre projet pour des appareils Android et iOS à l’aide des packages AR Foundation, ARCore XR Plugin et ARKit XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="a752f-160">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
