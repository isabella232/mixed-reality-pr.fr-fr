---
title: Déploiement sur les appareils Hololens et WMR
description: Documentation pour créer et déployer des applications sur différents appareils.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Visual Studio
ms.openlocfilehash: ec66c6ccb8cf1c702fed804230f5cf3ca0526139
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852374"
---
# <a name="building-and-deploying-mrtk-uwp"></a><span data-ttu-id="302bc-104">Génération et déploiement de MRTK (UWP)</span><span class="sxs-lookup"><span data-stu-id="302bc-104">Building and deploying MRTK (UWP)</span></span>

<span data-ttu-id="302bc-105">Pour exécuter une application sur un appareil en tant qu’application autonome (pour HoloLens, Android, iOS, etc.), l’étape de génération et de déploiement doit être exécutée dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="302bc-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="302bc-106">La création et le déploiement d’une application qui utilise le MRTK ressemble à la création et au déploiement d’une autre application Unity.</span><span class="sxs-lookup"><span data-stu-id="302bc-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="302bc-107">Il n’existe aucune instruction propre au MRTK.</span><span class="sxs-lookup"><span data-stu-id="302bc-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="302bc-108">Lisez les informations ci-dessous pour obtenir des instructions détaillées sur la création et le déploiement d’une application Unity pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="302bc-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span> <span data-ttu-id="302bc-109">Pour en savoir plus sur la création de solutions pour d’autres plateformes, consultez la page sur la [publication de builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="302bc-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="302bc-110">Génération et déploiement de MRTK sur HoloLens 1, HoloLens 2 et WMR casques (UWP)</span><span class="sxs-lookup"><span data-stu-id="302bc-110">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="302bc-111">Vous trouverez des instructions sur la génération et le déploiement de **hololens 1** et **hololens 2** (UWP) dans la rubrique [création de votre application sur un appareil](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="302bc-111">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="302bc-112">Ces étapes vous permettent également de déployer sur des **casques WMR**.</span><span class="sxs-lookup"><span data-stu-id="302bc-112">These steps also allow you to deploy to **WMR headsets**.</span></span>

<span data-ttu-id="302bc-113">**Conseil :** Lors de la génération pour HoloLens 1, HoloLens 2 ou WMR, il est recommandé que les paramètres de build « version du kit de développement logiciel (SDK) cible » et « version de plateforme minimale » se présentent comme dans l’image ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="302bc-113">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Fenêtre Build](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="302bc-115">Les autres paramètres peuvent être différents (par exemple, configuration de build/architecture/type de build, et d’autres peuvent toujours être modifiés dans la solution Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="302bc-115">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="302bc-116">Vérifiez que la liste déroulante « Version cible du Kit de développement logiciel (SDK) » contient l’option « 10.0.18362.0 ». Si ce n’est pas le cas, [le SDK Windows le plus récent](https://developer.microsoft.com/windows/downloads/windows-10-sdk) doit être installé.</span><span class="sxs-lookup"><span data-stu-id="302bc-116">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="302bc-117">Unity 2019.3 et HoloLens</span><span class="sxs-lookup"><span data-stu-id="302bc-117">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="302bc-118">Si une application HoloLens apparaît sous la forme d’un panneau 2D sur l’appareil, vérifiez que les paramètres suivants ont été configurés dans Unity 2019.3.x avant de déployer votre application UWP :</span><span class="sxs-lookup"><span data-stu-id="302bc-118">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="302bc-119">Si vous utilisez le XR hérité :</span><span class="sxs-lookup"><span data-stu-id="302bc-119">If using the legacy XR:</span></span>

1. <span data-ttu-id="302bc-120">Accédez à Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)</span><span class="sxs-lookup"><span data-stu-id="302bc-120">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="302bc-121">Sous **XR Settings (Paramètres XR)** sous l’onglet UWP, vérifiez que l’option **Virtual Reality Supported (Réalité virtuelle prise en charge)** est activée et que le SDK **Windows Mixed Reality** a été ajouté aux SDK.</span><span class="sxs-lookup"><span data-stu-id="302bc-121">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="302bc-122">Générer et déployer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="302bc-122">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="302bc-123">Si vous utilisez le plug-in XR :</span><span class="sxs-lookup"><span data-stu-id="302bc-123">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="302bc-124">Suivez les étapes décrites dans [Prise en main de XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="302bc-124">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="302bc-125">Vérifiez que le profil de configuration est **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="302bc-125">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="302bc-126">Accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), XR-Plugin Management (Gestion du plugin XR)** et vérifiez que **Windows Mixed Reality** est activé.</span><span class="sxs-lookup"><span data-stu-id="302bc-126">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="302bc-127">Générer et déployer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="302bc-127">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="302bc-128">Si vous utilisez Unity 2019.3.x, sélectionnez **ARM64** et non **ARM** comme architecture de build dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="302bc-128">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="302bc-129">Avec les paramètres Unity par défaut dans Unity 2019.3.x, une application Unity n’est pas déployée sur un HoloLens si ARM est sélectionné en raison d’un bogue Unity.</span><span class="sxs-lookup"><span data-stu-id="302bc-129">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="302bc-130">Ce suivi peut être effectué dans le [dispositif de suivi des problèmes d’Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="302bc-130">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="302bc-131">Si l’architecture ARM est requise, accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)** , puis dans le menu **Other Settings (Autres paramètres)** , désactivez **Graphics Jobs (Travaux graphiques)** .</span><span class="sxs-lookup"><span data-stu-id="302bc-131">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="302bc-132">Même si la désactivation de **Graphics Jobs (Travaux graphiques)** permettra à l’application de se déployer à l’aide de l’architecture de build ARM pour Unity 2019.3.x, ARM64 est recommandé.</span><span class="sxs-lookup"><span data-stu-id="302bc-132">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-standalone"></a><span data-ttu-id="302bc-133">Génération et déploiement de MRTK (autonome)</span><span class="sxs-lookup"><span data-stu-id="302bc-133">Building and deploying MRTK (Standalone)</span></span>

<span data-ttu-id="302bc-134">Les versions autonomes de MRTK peuvent être utilisées sur des casques WMR.</span><span class="sxs-lookup"><span data-stu-id="302bc-134">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="302bc-135">Une version autonome d’un casque WMR requiert d’effectuer les étapes supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="302bc-135">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="302bc-136">Le SDK XR d’Unity prend également en charge les WMR natifs dans les builds autonomes, mais ne nécessite pas de plug-in WMR ou SteamVR.</span><span class="sxs-lookup"><span data-stu-id="302bc-136">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="302bc-137">Ces étapes sont requises pour les XR hérités d’Unity.</span><span class="sxs-lookup"><span data-stu-id="302bc-137">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="302bc-138">Installer [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="302bc-138">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="302bc-139">Installer [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="302bc-139">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="302bc-140">Installer le [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="302bc-140">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="302bc-141">Utiliser le plug-in WMR</span><span class="sxs-lookup"><span data-stu-id="302bc-141">How to use WMR plugin</span></span>

1. <span data-ttu-id="302bc-142">Ouvrir Steam et rechercher le plug-in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="302bc-142">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="302bc-143">Vérifiez que SteamVR est fermé avant de lancer le plug-in WMR.</span><span class="sxs-lookup"><span data-stu-id="302bc-143">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="302bc-144">Le lancement du plug-in WMR a pour effet de lancer également SteamVR.</span><span class="sxs-lookup"><span data-stu-id="302bc-144">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="302bc-145">Vérifiez que le casque WMR est branché.</span><span class="sxs-lookup"><span data-stu-id="302bc-145">Make sure the WMR headset is plugged in.</span></span>

    ![Recherche de plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="302bc-147">Sélectionnez **Lancer** pour lancer le plug-in Windows Mixed Reality pour le plug-in SteamVR.</span><span class="sxs-lookup"><span data-stu-id="302bc-147">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="302bc-149">SteamVR et le plug-in WMR démarrent et une nouvelle fenêtre d’état de suivi du casque WMR s’affiche.</span><span class="sxs-lookup"><span data-stu-id="302bc-149">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="302bc-150">Pour plus d’informations, consultez la [documentation sur l’utilisation de Steam avec Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="302bc-150">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Apparence du lancement de WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="302bc-152">Dans Unity, avec votre scène MRTK ouverte, accédez à **File (Fichier) > Build Settings (Paramètres de build)**</span><span class="sxs-lookup"><span data-stu-id="302bc-152">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="302bc-153">Générer la scène</span><span class="sxs-lookup"><span data-stu-id="302bc-153">Build the scene</span></span>
    - <span data-ttu-id="302bc-154">Sélectionnez **Ajouter une scène ouverte**</span><span class="sxs-lookup"><span data-stu-id="302bc-154">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="302bc-155">Assurez-vous que la plateforme est définie sur **Standalone (Autonome)** .</span><span class="sxs-lookup"><span data-stu-id="302bc-155">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="302bc-156">Sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="302bc-156">Select **Build**</span></span>
    - <span data-ttu-id="302bc-157">Choisissez l’emplacement de la nouvelle build dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="302bc-157">Choose the location for the new build in File Explorer</span></span>

    ![Paramètres de build pour l’option Autonome](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="302bc-159">Un nouvel exécutable Unity sera créé. Pour lancer votre application, sélectionnez l’exécutable Unity dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="302bc-159">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Explorateur de fichiers dans Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="302bc-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="302bc-161">See also</span></span>

- [<span data-ttu-id="302bc-162">Support Android et iOS</span><span class="sxs-lookup"><span data-stu-id="302bc-162">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="302bc-163">Prise en charge de Leap Motion</span><span class="sxs-lookup"><span data-stu-id="302bc-163">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="302bc-164">Détection des fonctionnalités de plateforme</span><span class="sxs-lookup"><span data-stu-id="302bc-164">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)