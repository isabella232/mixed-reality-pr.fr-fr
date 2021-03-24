---
title: BuildAndDeploy
description: Documentation pour créer et déployer des applications sur différents appareils.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK, Visual Studio, Android, iOS
ms.openlocfilehash: cbf17cfd463ee375d285a36aef1705b4d911107f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687429"
---
# <a name="building-and-deploying-mrtk"></a><span data-ttu-id="ca74f-104">Génération et déploiement du MRTK</span><span class="sxs-lookup"><span data-stu-id="ca74f-104">Building and deploying MRTK</span></span>

<span data-ttu-id="ca74f-105">Pour exécuter une application sur un appareil en tant qu’application autonome (pour HoloLens, Android, iOS, etc.), l’étape de génération et de déploiement doit être exécutée dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="ca74f-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="ca74f-106">La création et le déploiement d’une application qui utilise le MRTK ressemble à la création et au déploiement d’une autre application Unity.</span><span class="sxs-lookup"><span data-stu-id="ca74f-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="ca74f-107">Il n’existe aucune instruction propre au MRTK.</span><span class="sxs-lookup"><span data-stu-id="ca74f-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="ca74f-108">Lisez les informations ci-dessous pour obtenir des instructions détaillées sur la création et le déploiement d’une application Unity pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca74f-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span>  <span data-ttu-id="ca74f-109">Pour en savoir plus sur la création de solutions pour d’autres plateformes, consultez la page sur la [publication de builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="ca74f-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a><span data-ttu-id="ca74f-110">Génération et déploiement du MRTK sur HoloLens 1 et HoloLens 2 (UWP)</span><span class="sxs-lookup"><span data-stu-id="ca74f-110">Building and deploying MRTK to HoloLens 1 and HoloLens 2 (UWP)</span></span>

<span data-ttu-id="ca74f-111">Pour obtenir des instructions sur la génération et le déploiement pour HoloLens 1 et HoloLens 2 (UWP), consultez la rubrique sur [la génération de votre application sur un appareil](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="ca74f-111">Instructions on how to build and deploy for HoloLens 1 and HoloLens 2 (UWP) can be found at [building your application to device](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span>

<span data-ttu-id="ca74f-112">**Conseil :** lors de la génération pour WMR, HoloLens 1 ou HoloLens 2, il est recommandé que les paramètres de build Target SDK Version (Version cible du SDK) et Minimum Platform Version (Version de plateforme minimale) se présentent comme dans l’image ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ca74f-112">**Tip:** When building for WMR, HoloLens 1, or HoloLens 2, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Fenêtre Build](../features/Images/getting_started/BuildWindow.png)

<span data-ttu-id="ca74f-114">Les autres paramètres peuvent être différents (par exemple, configuration de build/architecture/type de build, et d’autres peuvent toujours être modifiés dans la solution Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="ca74f-114">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="ca74f-115">Vérifiez que la liste déroulante « Version cible du Kit de développement logiciel (SDK) » contient l’option « 10.0.18362.0 ». Si ce n’est pas le cas, [le SDK Windows le plus récent](https://developer.microsoft.com/windows/downloads/windows-10-sdk) doit être installé.</span><span class="sxs-lookup"><span data-stu-id="ca74f-115">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="ca74f-116">Unity 2019.3 et HoloLens</span><span class="sxs-lookup"><span data-stu-id="ca74f-116">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="ca74f-117">Si une application HoloLens apparaît sous la forme d’un panneau 2D sur l’appareil, vérifiez que les paramètres suivants ont été configurés dans Unity 2019.3.x avant de déployer votre application UWP :</span><span class="sxs-lookup"><span data-stu-id="ca74f-117">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="ca74f-118">Si vous utilisez le XR hérité :</span><span class="sxs-lookup"><span data-stu-id="ca74f-118">If using the legacy XR:</span></span>

1. <span data-ttu-id="ca74f-119">Accédez à Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)</span><span class="sxs-lookup"><span data-stu-id="ca74f-119">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="ca74f-120">Sous **XR Settings (Paramètres XR)** sous l’onglet UWP, vérifiez que l’option **Virtual Reality Supported (Réalité virtuelle prise en charge)** est activée et que le SDK **Windows Mixed Reality** a été ajouté aux SDK.</span><span class="sxs-lookup"><span data-stu-id="ca74f-120">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="ca74f-121">Générer et déployer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca74f-121">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="ca74f-122">Si vous utilisez le plug-in XR :</span><span class="sxs-lookup"><span data-stu-id="ca74f-122">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="ca74f-123">Suivez les étapes décrites dans [Prise en main de XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span><span class="sxs-lookup"><span data-stu-id="ca74f-123">Follow the steps found in [Getting Started with XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span></span>
1. <span data-ttu-id="ca74f-124">Vérifiez que le profil de configuration est **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="ca74f-124">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="ca74f-125">Accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), XR-Plugin Management (Gestion du plugin XR)** et vérifiez que **Windows Mixed Reality** est activé.</span><span class="sxs-lookup"><span data-stu-id="ca74f-125">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="ca74f-126">Générer et déployer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca74f-126">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="ca74f-127">Si vous utilisez Unity 2019.3.x, sélectionnez **ARM64** et non **ARM** comme architecture de build dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca74f-127">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="ca74f-128">Avec les paramètres Unity par défaut dans Unity 2019.3.x, une application Unity n’est pas déployée sur un HoloLens si ARM est sélectionné en raison d’un bogue Unity.</span><span class="sxs-lookup"><span data-stu-id="ca74f-128">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="ca74f-129">Ce suivi peut être effectué dans le [dispositif de suivi des problèmes d’Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="ca74f-129">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="ca74f-130">Si l’architecture ARM est requise, accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)** , puis dans le menu **Other Settings (Autres paramètres)** , désactivez **Graphics Jobs (Travaux graphiques)** .</span><span class="sxs-lookup"><span data-stu-id="ca74f-130">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="ca74f-131">Même si la désactivation de **Graphics Jobs (Travaux graphiques)** permettra à l’application de se déployer à l’aide de l’architecture de build ARM pour Unity 2019.3.x, ARM64 est recommandé.</span><span class="sxs-lookup"><span data-stu-id="ca74f-131">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a><span data-ttu-id="ca74f-132">Génération et déploiement du MRTK sur un casque Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ca74f-132">Building and deploying MRTK to a Windows Mixed Reality Headset</span></span>

<span data-ttu-id="ca74f-133">Le casque Windows Mixed Reality (WMR) peut être utilisé pour les plateforme Windows universelles (UWP) et les builds autonomes.</span><span class="sxs-lookup"><span data-stu-id="ca74f-133">The Windows Mixed Reality (WMR) headset can be used for Universal Windows Platform (UWP) and Standalone builds.</span></span>  <span data-ttu-id="ca74f-134">Une version autonome d’un casque WMR requiert d’effectuer les étapes supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="ca74f-134">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="ca74f-135">Le SDK XR d’Unity prend également en charge les WMR natifs dans les builds autonomes, mais ne nécessite pas de plug-in WMR ou SteamVR.</span><span class="sxs-lookup"><span data-stu-id="ca74f-135">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="ca74f-136">Ces étapes sont requises pour les XR hérités d’Unity.</span><span class="sxs-lookup"><span data-stu-id="ca74f-136">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="ca74f-137">Installer [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="ca74f-137">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="ca74f-138">Installer [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="ca74f-138">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="ca74f-139">Installer le [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="ca74f-139">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="ca74f-140">Utiliser le plug-in WMR</span><span class="sxs-lookup"><span data-stu-id="ca74f-140">How to use WMR plugin</span></span>

1. <span data-ttu-id="ca74f-141">Ouvrir Steam et rechercher le plug-in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ca74f-141">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="ca74f-142">Vérifiez que SteamVR est fermé avant de lancer le plug-in WMR.</span><span class="sxs-lookup"><span data-stu-id="ca74f-142">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="ca74f-143">Le lancement du plug-in WMR a pour effet de lancer également SteamVR.</span><span class="sxs-lookup"><span data-stu-id="ca74f-143">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="ca74f-144">Vérifiez que le casque WMR est branché.</span><span class="sxs-lookup"><span data-stu-id="ca74f-144">Make sure the WMR headset is plugged in.</span></span>

    ![Recherche de plug-in WMR](../features/Images/BuildDeploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="ca74f-146">Sélectionnez **Lancer** pour lancer le plug-in Windows Mixed Reality pour le plug-in SteamVR.</span><span class="sxs-lookup"><span data-stu-id="ca74f-146">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in WMR](../features/Images/BuildDeploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="ca74f-148">SteamVR et le plug-in WMR démarrent et une nouvelle fenêtre d’état de suivi du casque WMR s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ca74f-148">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="ca74f-149">Pour plus d’informations, consultez la [documentation sur l’utilisation de Steam avec Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="ca74f-149">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Apparence du lancement de WMR](../features/Images/BuildDeploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="ca74f-151">Dans Unity, avec votre scène MRTK ouverte, accédez à **File (Fichier) > Build Settings (Paramètres de build)**</span><span class="sxs-lookup"><span data-stu-id="ca74f-151">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="ca74f-152">Générer la scène</span><span class="sxs-lookup"><span data-stu-id="ca74f-152">Build the scene</span></span>
    - <span data-ttu-id="ca74f-153">Sélectionnez **Ajouter une scène ouverte**</span><span class="sxs-lookup"><span data-stu-id="ca74f-153">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="ca74f-154">Assurez-vous que la plateforme est définie sur **Standalone (Autonome)** .</span><span class="sxs-lookup"><span data-stu-id="ca74f-154">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="ca74f-155">Sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="ca74f-155">Select **Build**</span></span>
    - <span data-ttu-id="ca74f-156">Choisissez l’emplacement de la nouvelle build dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ca74f-156">Choose the location for the new build in File Explorer</span></span>

    ![Paramètres de build pour l’option Autonome](../features/Images/BuildDeploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="ca74f-158">Un nouvel exécutable Unity sera créé. Pour lancer votre application, sélectionnez l’exécutable Unity dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ca74f-158">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Explorateur de fichiers dans Unity](../features/Images/BuildDeploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="ca74f-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca74f-160">See also</span></span>

- [<span data-ttu-id="ca74f-161">Support Android et iOS</span><span class="sxs-lookup"><span data-stu-id="ca74f-161">Android and iOS Support</span></span>](../features/CrossPlatform/UsingARFoundation.md)
- [<span data-ttu-id="ca74f-162">Prise en charge de Leap Motion</span><span class="sxs-lookup"><span data-stu-id="ca74f-162">Leap Motion Support</span></span>](../features/CrossPlatform/LeapMotionMRTK.md)
- [<span data-ttu-id="ca74f-163">Détection des fonctionnalités de plateforme</span><span class="sxs-lookup"><span data-stu-id="ca74f-163">Detecting Platform Capabilities</span></span>](../features/DetectingPlatformCapabilities.md)
