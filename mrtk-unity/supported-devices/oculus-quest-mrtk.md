---
title: Génération et déploiement sur Oculus Quest
description: Documentation à configurer pour Oculus Quest dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Oculus Quest
ms.openlocfilehash: 96b4b5b8a68c3b61d54b6796ba01c9e2516ba959
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449758"
---
# <a name="building-and-deploying-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="fe0be-104">Génération et déploiement sur Oculus Quest à l’aide du pipeline du kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="fe0be-104">Building and deploying to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="fe0be-105">Une [quête Oculus](https://www.oculus.com/quest/) est requise.</span><span class="sxs-lookup"><span data-stu-id="fe0be-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="fe0be-106">La prise en charge de MRTK pour Oculus Quest est fournie par le biais de deux sources différentes : le pipeline SDK XR de Unity et le package Unity d’intégration Oculus.</span><span class="sxs-lookup"><span data-stu-id="fe0be-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="fe0be-107">Le **fournisseur de données XRSDK Oculus** permet l’utilisation des deux sources et doit être utilisé pour déployer MRTK sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="fe0be-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="fe0be-108">Le [pipeline Unity XR SDK](https://docs.unity3d.com/Manual/XR.html) permet d’utiliser les contrôleurs tactiles Oculus et le suivi des têtes avec le Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="fe0be-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="fe0be-109">Ce pipeline est la norme pour le développement d’applications XR dans Unity 2019,3 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="fe0be-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="fe0be-110">Pour utiliser ce pipeline, assurez-vous que vous utilisez **unity 2019,3 ou une version plus récente**.</span><span class="sxs-lookup"><span data-stu-id="fe0be-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="fe0be-111">Cela est **nécessaire** pour déployer des applications MRTK sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="fe0be-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="fe0be-112">Le [package Unity d’intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permet d’utiliser le suivi de la **main** avec Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="fe0be-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="fe0be-113">Ce fournisseur de données n’utilise **pas** le **pipeline du kit de développement logiciel (SDK) XR** d’Unity ou le **pipeline XR hérité**.</span><span class="sxs-lookup"><span data-stu-id="fe0be-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="fe0be-114">Configuration de Project pour Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="fe0be-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="fe0be-115">Procédez comme [suit](https://developer.oculus.com/documentation/unity/book-unity-gsg/) pour vous assurer que votre projet est prêt pour le déploiement sur Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="fe0be-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="fe0be-116">Assurez-vous que le [mode développeur](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) est activé sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="fe0be-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="fe0be-117">L’installation des pilotes ADB Oculus est facultative.</span><span class="sxs-lookup"><span data-stu-id="fe0be-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="fe0be-118">Configuration du pipeline du kit de développement logiciel (SDK) XR pour Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="fe0be-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="fe0be-119">Assurez-vous que le **plug-in Oculus XR** est installé sous **Window--> gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="fe0be-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Package de plug-in XR Oculus](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="fe0be-121">Assurez-vous que le fournisseur de plug-ins Oculus est inclus dans votre projet en accédant à **modifier--> paramètres du projet--> gestion du plug-in XR--> fournisseurs de plug-** in</span><span class="sxs-lookup"><span data-stu-id="fe0be-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Fournisseur de plug-ins Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="fe0be-123">Configuration du package Unity d’intégration Oculus pour activer handtracking</span><span class="sxs-lookup"><span data-stu-id="fe0be-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="fe0be-124">Téléchargez et importez l' [intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) à partir du magasin d’actifs Unity.</span><span class="sxs-lookup"><span data-stu-id="fe0be-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="fe0be-125">La dernière version testée pour fonctionner est 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="fe0be-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="fe0be-126">Les versions antérieures sont disponibles dans cette [Archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span><span class="sxs-lookup"><span data-stu-id="fe0be-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="fe0be-127">Accédez à la boîte à outils de réalité mixte > utilitaires > Oculus > intégrer les modules Unity Oculus Integration.</span><span class="sxs-lookup"><span data-stu-id="fe0be-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="fe0be-128">Cela a pour effet de mettre à jour le asmdefs avec les définitions et les références nécessaires au bon fonctionnement du code Oculus Quest approprié.</span><span class="sxs-lookup"><span data-stu-id="fe0be-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="fe0be-129">Il met également à jour le fichier CSC pour filtrer les avertissements obsolètes produits par les ressources d’intégration Oculus.</span><span class="sxs-lookup"><span data-stu-id="fe0be-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="fe0be-130">Le référentiel MRTK contient un fichier CSC qui convertit les avertissements en erreurs, cette conversion interrompt le processus de configuration MRTK-Quest.</span><span class="sxs-lookup"><span data-stu-id="fe0be-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="fe0be-132">Dans le dossier Oculus importé (il doit être trouvé dans Assets/Oculus), il existe un objet scriptable appelé OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="fe0be-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="fe0be-133">Dans ce fichier de configuration, vous devez définir HandTrackingSupport sur « Controllers and handles ».</span><span class="sxs-lookup"><span data-stu-id="fe0be-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Contrôleur d’intégration Oculus et mains](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="fe0be-135">Configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="fe0be-135">Setting up the scene</span></span>

1. <span data-ttu-id="fe0be-136">Créez une nouvelle scène Unity ou ouvrez une scène préexistante telle que HandInteractionExamples.</span><span class="sxs-lookup"><span data-stu-id="fe0be-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="fe0be-137">Ajoutez MRTK à la scène en accédant à **Mixed Reality Toolkit**  >  **Add to Scene et configure**.</span><span class="sxs-lookup"><span data-stu-id="fe0be-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="fe0be-138">Utilisation du kit de développement logiciel (SDK) Oculus XR Fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="fe0be-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="fe0be-139">Configurez votre profil pour utiliser le **Kit de développement logiciel (SDK) Oculus XR fournisseur de données**</span><span class="sxs-lookup"><span data-stu-id="fe0be-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="fe0be-140">Si vous n’avez pas l’intention de modifier les profils de configuration</span><span class="sxs-lookup"><span data-stu-id="fe0be-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="fe0be-141">Utilisez l’un des profils MRTK par défaut, qui sont tous configurés dans les pipelines XR d’Unity.</span><span class="sxs-lookup"><span data-stu-id="fe0be-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="fe0be-142">Le DefaultXRSDKConfigurationProfile précédent est maintenant marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="fe0be-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="fe0be-143">Accédez à [Build et déployez votre projet sur Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="fe0be-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="fe0be-144">Sinon, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fe0be-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="fe0be-145">Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="fe0be-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Cloner le profil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="fe0be-147">Sélectionnez le profil de configuration **d’entrée** .</span><span class="sxs-lookup"><span data-stu-id="fe0be-147">Select the **Input** Configuration Profile.</span></span>

        ![Profil de configuration d’entrée](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="fe0be-149">Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.</span><span class="sxs-lookup"><span data-stu-id="fe0be-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Cloner le profil du système d’entrée](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="fe0be-151">Ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **Ajouter un fournisseur de données** en haut, et le nouveau fournisseur de données sera ajouté à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="fe0be-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="fe0be-152">Ouvrez le nouveau fournisseur de données et définissez le **type** sur **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.</span><span class="sxs-lookup"><span data-stu-id="fe0be-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus ajouter XRSDK Fournisseur de données](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="fe0be-154">Configurez votre profil pour utiliser le **Kit de développement logiciel (SDK) Oculus XR fournisseur de données**</span><span class="sxs-lookup"><span data-stu-id="fe0be-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="fe0be-155">Si vous n’avez pas l’intention de modifier les profils de configuration</span><span class="sxs-lookup"><span data-stu-id="fe0be-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="fe0be-156">Remplacez votre profil par DefaultXRSDKConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="fe0be-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="fe0be-157">Accédez à [Build et déployez votre projet sur Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span><span class="sxs-lookup"><span data-stu-id="fe0be-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="fe0be-158">Sinon, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fe0be-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="fe0be-159">Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="fe0be-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Cloner le profil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="fe0be-161">Sélectionnez le profil de configuration **d’entrée** .</span><span class="sxs-lookup"><span data-stu-id="fe0be-161">Select the **Input** Configuration Profile.</span></span>

        ![Profil de configuration d’entrée](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="fe0be-163">Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.</span><span class="sxs-lookup"><span data-stu-id="fe0be-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Cloner le profil du système d’entrée](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="fe0be-165">Ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **Ajouter un fournisseur de données** en haut, et le nouveau fournisseur de données sera ajouté à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="fe0be-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="fe0be-166">Ouvrez le nouveau fournisseur de données et définissez le **type** sur **Microsoft. MixedReality. Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.</span><span class="sxs-lookup"><span data-stu-id="fe0be-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus ajouter XRSDK Fournisseur de données](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="fe0be-168">Le kit de développement logiciel (SDK) Oculus XR Fournisseur de données comprend une plate-forme de caméra RFP Prefab qui configure automatiquement le projet avec une plate-forme RFP et des mains RFP pour acheminer correctement les entrées.</span><span class="sxs-lookup"><span data-stu-id="fe0be-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="fe0be-169">L’ajout manuel d’une plate-forme RFP à la scène nécessite une configuration manuelle des paramètres et de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="fe0be-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="fe0be-170">Créez et déployez votre projet sur Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="fe0be-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="fe0be-171">Branchez votre Oculus Quest via un câble USB C 3,0-></span><span class="sxs-lookup"><span data-stu-id="fe0be-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="fe0be-172">Accédez à **fichier > paramètres de build**</span><span class="sxs-lookup"><span data-stu-id="fe0be-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="fe0be-173">Changer le déploiement en **Android**</span><span class="sxs-lookup"><span data-stu-id="fe0be-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="fe0be-174">Vérifiez que la Oculus Quest est sélectionnée en tant qu’unité d’exécution applicable.</span><span class="sxs-lookup"><span data-stu-id="fe0be-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus exécuter l’appareil](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="fe0be-176">Sélectionner générer et exécuter</span><span class="sxs-lookup"><span data-stu-id="fe0be-176">Select Build and Run</span></span>
    - <span data-ttu-id="fe0be-177">Vous rencontrerez probablement le jeu d’erreurs de génération suivant lorsque vous sélectionnez *générer et exécuter* la première fois.</span><span class="sxs-lookup"><span data-stu-id="fe0be-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="fe0be-178">Vous devez être en mesure de procéder à un déploiement en sélectionnant *générer et exécuter* à nouveau.</span><span class="sxs-lookup"><span data-stu-id="fe0be-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus des erreurs de build attendues](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="fe0be-180">Accepter l’invite _autoriser le débogage USB_ de l’intérieur de la Quest</span><span class="sxs-lookup"><span data-stu-id="fe0be-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="fe0be-181">Consultez votre scène à l’intérieur de Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="fe0be-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="fe0be-182">Suppression de l’intégration de Oculus du projet</span><span class="sxs-lookup"><span data-stu-id="fe0be-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="fe0be-183">Accédez à la boîte à outils de réalité mixte > Oculus > modules Unity d’intégration Oculus distincts  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="fe0be-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="fe0be-184">Permettre à l’actualisation Unity en tant que références dans Microsoft. MixedReality. Toolkit. Providers. Oculus. asmdef et d’autres fichiers sont modifiés dans cette étape</span><span class="sxs-lookup"><span data-stu-id="fe0be-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="fe0be-185">Fermer Unity</span><span class="sxs-lookup"><span data-stu-id="fe0be-185">Close Unity</span></span>
1. <span data-ttu-id="fe0be-186">Fermez Visual Studio, s’il est ouvert</span><span class="sxs-lookup"><span data-stu-id="fe0be-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="fe0be-187">Ouvrez l’Explorateur de fichiers et accédez à la racine du projet MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="fe0be-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="fe0be-188">Supprimer le répertoire UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="fe0be-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="fe0be-189">Supprimer le répertoire UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="fe0be-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="fe0be-190">Supprimer le fichier UnityProjectName/Assets/Oculus. meta</span><span class="sxs-lookup"><span data-stu-id="fe0be-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="fe0be-191">Rouvrir Unity</span><span class="sxs-lookup"><span data-stu-id="fe0be-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="fe0be-192">Erreurs courantes</span><span class="sxs-lookup"><span data-stu-id="fe0be-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="fe0be-193">Quest non reconnu par Unity</span><span class="sxs-lookup"><span data-stu-id="fe0be-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="fe0be-194">Assurez-vous que vos chemins Android sont correctement configurés.</span><span class="sxs-lookup"><span data-stu-id="fe0be-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="fe0be-195">Si vous continuez à rencontrer des problèmes, suivez ce [Guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="fe0be-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="fe0be-196">**Modifier > préférences > outils externes > Android**</span><span class="sxs-lookup"><span data-stu-id="fe0be-196">**Edit > Preferences > External Tools > Android**</span></span>

![Configuration des outils Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
