---
title: Oculus Quest dans MRTK
description: Documentation à configurer pour Oculus Quest dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Oculus Quest,
ms.openlocfilehash: 0892e0d416cd07d1bedbeea0ddb316e3eb012b94
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441173"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="b08e0-104">Génération et déploiement de MRTK sur Oculus Quest à l’aide du pipeline du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="b08e0-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="b08e0-105">Une [quête Oculus](https://www.oculus.com/quest/) est requise.</span><span class="sxs-lookup"><span data-stu-id="b08e0-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="b08e0-106">La prise en charge de MRTK pour Oculus Quest est fournie par le biais de deux sources différentes : le pipeline SDK XR de Unity et le package Unity d’intégration Oculus.</span><span class="sxs-lookup"><span data-stu-id="b08e0-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="b08e0-107">Le **fournisseur de données XRSDK Oculus** permet l’utilisation des deux sources et doit être utilisé pour déployer MRTK sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="b08e0-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="b08e0-108">Le [pipeline Unity XR SDK](https://docs.unity3d.com/Manual/XR.html) permet d’utiliser les contrôleurs tactiles Oculus et le suivi des têtes avec le Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="b08e0-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="b08e0-109">Ce pipeline est la norme pour le développement d’applications XR dans Unity 2019,3 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="b08e0-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="b08e0-110">Pour utiliser ce pipeline, assurez-vous que vous utilisez **unity 2019,3 ou une version plus récente**.</span><span class="sxs-lookup"><span data-stu-id="b08e0-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="b08e0-111">Cela est **nécessaire** pour déployer des applications MRTK sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="b08e0-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span> 

<span data-ttu-id="b08e0-112">Le [package Unity d’intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permet d’utiliser le suivi de la **main** avec Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="b08e0-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="b08e0-113">Ce fournisseur de données n’utilise **pas** le **pipeline du kit de développement logiciel (SDK) XR** d’Unity ou le **pipeline XR hérité**.</span><span class="sxs-lookup"><span data-stu-id="b08e0-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="b08e0-114">Configuration de Project pour Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="b08e0-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="b08e0-115">Procédez comme [suit](https://developer.oculus.com/documentation/unity/book-unity-gsg/) pour vous assurer que votre projet est prêt pour le déploiement sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="b08e0-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="b08e0-116">Assurez-vous que le [mode développeur](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) est activé sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="b08e0-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="b08e0-117">L’installation des pilotes ADB Oculus est facultative.</span><span class="sxs-lookup"><span data-stu-id="b08e0-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="b08e0-118">Configuration du pipeline du kit de développement logiciel (SDK) XR pour Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="b08e0-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="b08e0-119">Assurez-vous que le **plug-in Oculus XR** est installé sous **Window--> gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="b08e0-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Package de plug-in XR Oculus](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="b08e0-121">Assurez-vous que le fournisseur de plug-ins Oculus est inclus dans votre projet en accédant à **modifier--> paramètres du projet--> gestion du plug-in XR--> fournisseurs de plug-** in</span><span class="sxs-lookup"><span data-stu-id="b08e0-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Fournisseur de plug-ins Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="b08e0-123">Configuration du package Unity d’intégration Oculus pour activer handtracking</span><span class="sxs-lookup"><span data-stu-id="b08e0-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="b08e0-124">Téléchargez et importez l' [intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) à partir du magasin d’actifs Unity.</span><span class="sxs-lookup"><span data-stu-id="b08e0-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="b08e0-125">La dernière version testée pour fonctionner est 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="b08e0-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="b08e0-126">Des versions antérieures sont disponibles dans cette [Archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="b08e0-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="b08e0-127">Accédez à la boîte à outils de réalité mixte > utilitaires > Oculus > intégrer les modules Unity Oculus Integration.</span><span class="sxs-lookup"><span data-stu-id="b08e0-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="b08e0-128">Cela a pour effet de mettre à jour le asmdefs avec les définitions et les références nécessaires au bon fonctionnement du code Oculus Quest approprié.</span><span class="sxs-lookup"><span data-stu-id="b08e0-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="b08e0-129">Il met également à jour le fichier CSC pour filtrer les avertissements obsolètes produits par les ressources d’intégration Oculus.</span><span class="sxs-lookup"><span data-stu-id="b08e0-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="b08e0-130">Le référentiel MRTK contient un fichier CSC qui convertit les avertissements en erreurs, cette conversion interrompt le processus de configuration MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="b08e0-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="b08e0-132">Dans le dossier Oculus importé (il doit être trouvé dans Assets/Oculus), il existe un objet scriptable appelé OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="b08e0-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="b08e0-133">Dans ce fichier de configuration, vous devez définir HandTrackingSupport sur « Controllers and handles ».</span><span class="sxs-lookup"><span data-stu-id="b08e0-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Contrôleur d’intégration Oculus et mains](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="b08e0-135">Configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="b08e0-135">Setting up the scene</span></span>

1. <span data-ttu-id="b08e0-136">Créer une nouvelle scène Unity ou ouvrir une scène préexistante telle que HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="b08e0-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="b08e0-137">Ajoutez MRTK à la scène en accédant à **Mixed Reality Toolkit**  >  **Add to Scene et configure**</span><span class="sxs-lookup"><span data-stu-id="b08e0-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="b08e0-138">Utilisation du kit de développement logiciel (SDK) Oculus XR Fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="b08e0-138">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="b08e0-139">Configurez votre profil pour utiliser le **Kit de développement logiciel (SDK) Oculus XR fournisseur de données**</span><span class="sxs-lookup"><span data-stu-id="b08e0-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="b08e0-140">Si vous n’avez pas l’intention de modifier les profils de configuration</span><span class="sxs-lookup"><span data-stu-id="b08e0-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="b08e0-141">Modifiez votre profil en DefaultXRSDKConfigurationProfile et accédez à [générer et déployer votre projet sur Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="b08e0-141">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="b08e0-142">Sinon, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b08e0-142">Otherwise follow the following:</span></span>
        - <span data-ttu-id="b08e0-143">Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="b08e0-143">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Cloner le profil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="b08e0-145">Sélectionner le profil de configuration **d’entrée**</span><span class="sxs-lookup"><span data-stu-id="b08e0-145">Select the **Input** Configuration Profile</span></span>

        ![Profil de configuration d’entrée](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="b08e0-147">Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.</span><span class="sxs-lookup"><span data-stu-id="b08e0-147">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Cloner le profil du système d’entrée](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="b08e0-149">Ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **Ajouter un fournisseur de données** en haut, et le nouveau fournisseur de données sera ajouté à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="b08e0-149">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="b08e0-150">Ouvrez le nouveau fournisseur de données et définissez le **type** sur **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="b08e0-150">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus ajouter XRSDK Fournisseur de données](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="b08e0-152">Le kit de développement logiciel (SDK) Oculus XR Fournisseur de données comprend une plate-forme de caméra RFP Prefab qui configure automatiquement le projet avec une plate-forme RFP et des mains RFP pour acheminer correctement les entrées.</span><span class="sxs-lookup"><span data-stu-id="b08e0-152">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="b08e0-153">L’ajout manuel d’une plate-forme RFP à la scène nécessite une configuration manuelle des paramètres et de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b08e0-153">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="b08e0-154">Créez et déployez votre projet sur Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="b08e0-154">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="b08e0-155">Branchez votre Oculus Quest via un câble USB C 3,0-></span><span class="sxs-lookup"><span data-stu-id="b08e0-155">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="b08e0-156">Accédez à **fichier > paramètres de build**</span><span class="sxs-lookup"><span data-stu-id="b08e0-156">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="b08e0-157">Changer le déploiement en **Android**</span><span class="sxs-lookup"><span data-stu-id="b08e0-157">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="b08e0-158">Vérifiez que la Oculus Quest est sélectionnée en tant qu’unité d’exécution applicable.</span><span class="sxs-lookup"><span data-stu-id="b08e0-158">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus exécuter l’appareil](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="b08e0-160">Sélectionner générer et exécuter</span><span class="sxs-lookup"><span data-stu-id="b08e0-160">Select Build and Run</span></span>
    - <span data-ttu-id="b08e0-161">Vous rencontrerez probablement le jeu d’erreurs de génération suivant lorsque vous sélectionnez *générer et exécuter* la première fois.</span><span class="sxs-lookup"><span data-stu-id="b08e0-161">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="b08e0-162">Vous devez être en mesure de procéder à un déploiement en sélectionnant *générer et exécuter* à nouveau.</span><span class="sxs-lookup"><span data-stu-id="b08e0-162">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus des erreurs de build attendues](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="b08e0-164">Accepter l’invite _autoriser le débogage USB_ de l’intérieur de la Quest</span><span class="sxs-lookup"><span data-stu-id="b08e0-164">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="b08e0-165">Consultez votre scène à l’intérieur de Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="b08e0-165">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="b08e0-166">Suppression de l’intégration de Oculus du projet</span><span class="sxs-lookup"><span data-stu-id="b08e0-166">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="b08e0-167">Accédez à la boîte à outils de réalité mixte > Oculus > modules Unity d’intégration Oculus distincts  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="b08e0-167">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="b08e0-168">Permettre à l’actualisation Unity en tant que références dans Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef et d’autres fichiers sont modifiés dans cette étape</span><span class="sxs-lookup"><span data-stu-id="b08e0-168">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="b08e0-169">Fermer Unity</span><span class="sxs-lookup"><span data-stu-id="b08e0-169">Close Unity</span></span>
1. <span data-ttu-id="b08e0-170">Fermez Visual Studio, s’il est ouvert</span><span class="sxs-lookup"><span data-stu-id="b08e0-170">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="b08e0-171">Ouvrez l’Explorateur de fichiers et accédez à la racine du projet MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="b08e0-171">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="b08e0-172">Supprimer le répertoire UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="b08e0-172">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="b08e0-173">Supprimer le répertoire UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="b08e0-173">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="b08e0-174">Supprimer le fichier UnityProjectName/Assets/Oculus. meta</span><span class="sxs-lookup"><span data-stu-id="b08e0-174">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="b08e0-175">Rouvrir Unity</span><span class="sxs-lookup"><span data-stu-id="b08e0-175">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="b08e0-176">Erreurs courantes</span><span class="sxs-lookup"><span data-stu-id="b08e0-176">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="b08e0-177">Quest non reconnu par Unity</span><span class="sxs-lookup"><span data-stu-id="b08e0-177">Quest not recognized by Unity</span></span>

<span data-ttu-id="b08e0-178">Assurez-vous que vos chemins Android sont correctement configurés.</span><span class="sxs-lookup"><span data-stu-id="b08e0-178">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="b08e0-179">Si vous continuez à rencontrer des problèmes, suivez ce [Guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="b08e0-179">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="b08e0-180">**Modifier > préférences > outils externes > Android**</span><span class="sxs-lookup"><span data-stu-id="b08e0-180">**Edit > Preferences > External Tools > Android**</span></span>

![Configuration des outils Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
