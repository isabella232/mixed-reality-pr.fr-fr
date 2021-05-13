---
title: OculusQuestMRTK
description: Documentation à configurer pour Oculus Quest dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Oculus Quest,
ms.openlocfilehash: 9350ed7c8426c3bb31cf41493056fb6fc1e26107
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852368"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a><span data-ttu-id="5211b-104">Comment configurer Oculus Quest dans MRTK à l’aide du pipeline du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="5211b-104">How to configure Oculus Quest in MRTK using the XR SDK pipeline</span></span>

<span data-ttu-id="5211b-105">Une [Oculus Quest](https://www.oculus.com/quest/) est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5211b-105">A [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="5211b-106">La prise en charge de MRTK pour Oculus Quest est fournie par le biais de deux sources différentes : le pipeline XR de Unity et le package Unity d’intégration Oculus.</span><span class="sxs-lookup"><span data-stu-id="5211b-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="5211b-107">Le **fournisseur de données XRSDK Oculus** permet l’utilisation des deux sources et doit être utilisé pour utiliser MRTK sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="5211b-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to use MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="5211b-108">Le [pipeline XR de l’Unity](https://docs.unity3d.com/Manual/XR.html) permet d’utiliser les contrôleurs tactiles Oculus et le suivi des têtes avec le Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="5211b-108">The [Unity's XR Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="5211b-109">Ce pipeline est la norme pour le développement d’applications XR dans Unity 2019,3 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="5211b-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="5211b-110">Pour utiliser ce pipeline, assurez-vous que vous utilisez **unity 2019,3 ou une version plus récente**.</span><span class="sxs-lookup"><span data-stu-id="5211b-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span>

<span data-ttu-id="5211b-111">Le [package Unity d’intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permet d’utiliser le suivi de la **main** avec Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="5211b-111">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span>
<span data-ttu-id="5211b-112">Ce fournisseur de données n’utilise **pas** le **pipeline XR** ou le **pipeline XR hérité** de Unity, mais comme les contrôleurs et headtracking sont gérés par le pipeline XR de l’Unity, les étapes de **configuration de Project pour la Quest Oculus** doivent être suivies pour s’assurer que vous utilisez le **pipeline XR** et non le **pipeline XR hérité** à déprécier.</span><span class="sxs-lookup"><span data-stu-id="5211b-112">This data provider does **NOT** use Unity's **XR Pipeline** or **Legacy XR Pipeline**, but because controllers and headtracking are handled by the Unity's XR Pipeline, the steps in **Setting up project for the Oculus Quest** must be followed to ensure that you are using the **XR Pipeline** and not the to-be-deprecated **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="5211b-113">Configuration de Project pour Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="5211b-113">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="5211b-114">Procédez comme [suit](https://developer.oculus.com/documentation/unity/book-unity-gsg/) pour vous assurer que votre projet est prêt pour le déploiement sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="5211b-114">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="5211b-115">Assurez-vous que le [mode développeur](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) est activé sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="5211b-115">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="5211b-116">L’installation des pilotes ADB Oculus est facultative.</span><span class="sxs-lookup"><span data-stu-id="5211b-116">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a><span data-ttu-id="5211b-117">Configuration du pipeline XR pour Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="5211b-117">Setting up the XR Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="5211b-118">Assurez-vous que le **plug-in Oculus XR** est installé sous **Window--> gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="5211b-118">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Package de plug-in XR Oculus](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="5211b-120">Assurez-vous que le fournisseur de plug-ins Oculus est inclus dans votre projet en accédant à **modifier--> paramètres du projet--> gestion du plug-in XR--> fournisseurs de plug-** in</span><span class="sxs-lookup"><span data-stu-id="5211b-120">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Fournisseur de plug-ins Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="5211b-122">Configuration du package Unity d’intégration Oculus pour activer handtracking</span><span class="sxs-lookup"><span data-stu-id="5211b-122">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="5211b-123">Téléchargez et importez l' [intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) à partir du magasin d’actifs Unity.</span><span class="sxs-lookup"><span data-stu-id="5211b-123">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="5211b-124">La dernière version testée pour fonctionner est 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="5211b-124">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="5211b-125">Des versions antérieures sont disponibles dans cette [Archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="5211b-125">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="5211b-126">Accédez à la boîte à outils de réalité mixte > utilitaires > Oculus > intégrer les modules Unity Oculus Integration.</span><span class="sxs-lookup"><span data-stu-id="5211b-126">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="5211b-127">Cela a pour effet de mettre à jour le asmdefs avec les définitions et les références nécessaires au bon fonctionnement du code Oculus Quest approprié.</span><span class="sxs-lookup"><span data-stu-id="5211b-127">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="5211b-128">Il met également à jour le fichier CSC pour filtrer les avertissements obsolètes produits par les ressources d’intégration Oculus.</span><span class="sxs-lookup"><span data-stu-id="5211b-128">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="5211b-129">Le référentiel MRTK contient un fichier CSC qui convertit les avertissements en erreurs, cette conversion interrompt le processus de configuration MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="5211b-129">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="5211b-131">Dans le dossier Oculus importé (il doit être trouvé dans Assets/Oculus), il existe un objet scriptable appelé OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="5211b-131">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="5211b-132">Dans ce fichier de configuration, vous devez définir HandTrackingSupport sur « Controllers and handles ».</span><span class="sxs-lookup"><span data-stu-id="5211b-132">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Contrôleur d’intégration Oculus et mains](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="5211b-134">Configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="5211b-134">Setting up the scene</span></span>

1. <span data-ttu-id="5211b-135">Créer une nouvelle scène Unity ou ouvrir une scène préexistante telle que HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="5211b-135">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="5211b-136">Ajoutez MRTK à la scène en accédant à **Mixed Reality Toolkit**  >  **Add to Scene et configure**</span><span class="sxs-lookup"><span data-stu-id="5211b-136">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="5211b-137">Utilisation du kit de développement logiciel (SDK) Oculus XR Fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="5211b-137">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="5211b-138">Configurez votre profil pour utiliser le **Kit de développement logiciel (SDK) Oculus XR fournisseur de données**</span><span class="sxs-lookup"><span data-stu-id="5211b-138">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="5211b-139">Si vous n’avez pas l’intention de modifier les profils de configuration</span><span class="sxs-lookup"><span data-stu-id="5211b-139">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="5211b-140">Modifiez votre profil en DefaultXRSDKConfigurationProfile et accédez à [générer et déployer votre projet sur Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="5211b-140">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="5211b-141">Sinon, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5211b-141">Otherwise follow the following:</span></span>
        - <span data-ttu-id="5211b-142">Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="5211b-142">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Cloner le profil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="5211b-144">Sélectionner le profil de configuration **d’entrée**</span><span class="sxs-lookup"><span data-stu-id="5211b-144">Select the **Input** Configuration Profile</span></span>

        ![Profil de configuration d’entrée](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="5211b-146">Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.</span><span class="sxs-lookup"><span data-stu-id="5211b-146">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Cloner le profil du système d’entrée](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="5211b-148">Ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **Ajouter un fournisseur de données** en haut, et le nouveau fournisseur de données sera ajouté à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="5211b-148">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="5211b-149">Ouvrez le nouveau fournisseur de données et définissez le **type** sur **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="5211b-149">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus ajouter XRSDK Fournisseur de données](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="5211b-151">Le kit de développement logiciel (SDK) Oculus XR Fournisseur de données comprend une plate-forme de caméra RFP Prefab qui configure automatiquement le projet avec une plate-forme RFP et des mains RFP pour acheminer correctement les entrées.</span><span class="sxs-lookup"><span data-stu-id="5211b-151">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="5211b-152">L’ajout manuel d’une plate-forme RFP à la scène nécessite une configuration manuelle des paramètres et de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="5211b-152">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="5211b-153">Créez et déployez votre projet sur Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="5211b-153">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="5211b-154">Branchez votre Oculus Quest via un câble USB C 3,0-></span><span class="sxs-lookup"><span data-stu-id="5211b-154">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="5211b-155">Accédez à **fichier > paramètres de build**</span><span class="sxs-lookup"><span data-stu-id="5211b-155">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="5211b-156">Changer le déploiement en **Android**</span><span class="sxs-lookup"><span data-stu-id="5211b-156">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="5211b-157">Vérifiez que la Oculus Quest est sélectionnée en tant qu’unité d’exécution applicable.</span><span class="sxs-lookup"><span data-stu-id="5211b-157">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus exécuter l’appareil](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="5211b-159">Sélectionner générer et exécuter</span><span class="sxs-lookup"><span data-stu-id="5211b-159">Select Build and Run</span></span>
    - <span data-ttu-id="5211b-160">Vous rencontrerez probablement le jeu d’erreurs de génération suivant lorsque vous sélectionnez *générer et exécuter* la première fois.</span><span class="sxs-lookup"><span data-stu-id="5211b-160">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="5211b-161">Vous devez être en mesure de procéder à un déploiement en sélectionnant *générer et exécuter* à nouveau.</span><span class="sxs-lookup"><span data-stu-id="5211b-161">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus des erreurs de build attendues](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="5211b-163">Accepter l’invite _autoriser le débogage USB_ de l’intérieur de la Quest</span><span class="sxs-lookup"><span data-stu-id="5211b-163">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="5211b-164">Consultez votre scène à l’intérieur de Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="5211b-164">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="5211b-165">Suppression de l’intégration de Oculus du projet</span><span class="sxs-lookup"><span data-stu-id="5211b-165">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="5211b-166">Accédez à la boîte à outils de réalité mixte > Oculus > modules Unity d’intégration Oculus distincts  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="5211b-166">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="5211b-167">Permettre à l’actualisation Unity en tant que références dans Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef et d’autres fichiers sont modifiés dans cette étape</span><span class="sxs-lookup"><span data-stu-id="5211b-167">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="5211b-168">Fermer Unity</span><span class="sxs-lookup"><span data-stu-id="5211b-168">Close Unity</span></span>
1. <span data-ttu-id="5211b-169">Fermez Visual Studio, s’il est ouvert</span><span class="sxs-lookup"><span data-stu-id="5211b-169">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="5211b-170">Ouvrez l’Explorateur de fichiers et accédez à la racine du projet MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="5211b-170">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="5211b-171">Supprimer le répertoire UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="5211b-171">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="5211b-172">Supprimer le répertoire UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="5211b-172">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="5211b-173">Supprimer le fichier UnityProjectName/Assets/Oculus. meta</span><span class="sxs-lookup"><span data-stu-id="5211b-173">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="5211b-174">Rouvrir Unity</span><span class="sxs-lookup"><span data-stu-id="5211b-174">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="5211b-175">Erreurs courantes</span><span class="sxs-lookup"><span data-stu-id="5211b-175">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="5211b-176">Quest non reconnu par Unity</span><span class="sxs-lookup"><span data-stu-id="5211b-176">Quest not recognized by Unity</span></span>

<span data-ttu-id="5211b-177">Assurez-vous que vos chemins Android sont correctement configurés.</span><span class="sxs-lookup"><span data-stu-id="5211b-177">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="5211b-178">Si vous continuez à rencontrer des problèmes, suivez ce [Guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="5211b-178">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="5211b-179">**Modifier > préférences > outils externes > Android**</span><span class="sxs-lookup"><span data-stu-id="5211b-179">**Edit > Preferences > External Tools > Android**</span></span>

![Configuration des outils Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
