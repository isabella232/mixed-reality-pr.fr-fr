---
title: Déploiement sur des casques Hololens et WMR
description: Documentation pour créer et déployer des applications sur différents appareils.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Visual Studio
ms.openlocfilehash: 1547f0630d307e9e87505890adef4cad366d6c00
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441151"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="23a2a-104">Déploiement sur des casques Hololens et WMR</span><span class="sxs-lookup"><span data-stu-id="23a2a-104">Deploying to Hololens and WMR headsets</span></span>

<span data-ttu-id="23a2a-105">Il existe deux façons de déployer des applications générées avec MRTK sur votre appareil Windows, la plateforme Windows universels (UWP) et la plateforme autonome.</span><span class="sxs-lookup"><span data-stu-id="23a2a-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="23a2a-106">Les applications conçues pour HoloLens 1 ou HoloLens 2 doivent cibler UWP, tandis que les applications conçues pour les casques WMR peuvent cibler UWP ou autonome.</span><span class="sxs-lookup"><span data-stu-id="23a2a-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="23a2a-107">Génération et déploiement de MRTK sur HoloLens 1, HoloLens 2 et WMR casques (UWP)</span><span class="sxs-lookup"><span data-stu-id="23a2a-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="23a2a-108">Vous trouverez des instructions sur la génération et le déploiement de **hololens 1** et **hololens 2** (UWP) dans la rubrique [création de votre application sur un appareil](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="23a2a-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="23a2a-109">Ces étapes vous permettent également de déployer sur des **casques WMR**.</span><span class="sxs-lookup"><span data-stu-id="23a2a-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="23a2a-110">Lors du déploiement de votre application sur votre appareil dans Visual Studio, vous devez configurer Visual Studio légèrement différemment en fonction de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="23a2a-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="23a2a-111">Les configurations sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="23a2a-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="23a2a-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="23a2a-112">Platform</span></span> | <span data-ttu-id="23a2a-113">Configuration</span><span class="sxs-lookup"><span data-stu-id="23a2a-113">Configuration</span></span> | <span data-ttu-id="23a2a-114">Architecture</span><span class="sxs-lookup"><span data-stu-id="23a2a-114">Architecture</span></span> | <span data-ttu-id="23a2a-115">Cible</span><span class="sxs-lookup"><span data-stu-id="23a2a-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="23a2a-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="23a2a-116">HoloLens 2</span></span> | <span data-ttu-id="23a2a-117">Release ou Master</span><span class="sxs-lookup"><span data-stu-id="23a2a-117">Release or Master</span></span> | <span data-ttu-id="23a2a-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="23a2a-118">ARM64</span></span> | <span data-ttu-id="23a2a-119">Périphérique</span><span class="sxs-lookup"><span data-stu-id="23a2a-119">Device</span></span> |
| <span data-ttu-id="23a2a-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="23a2a-120">HoloLens 1</span></span> | <span data-ttu-id="23a2a-121">Release ou Master</span><span class="sxs-lookup"><span data-stu-id="23a2a-121">Release or Master</span></span> | <span data-ttu-id="23a2a-122">x86</span><span class="sxs-lookup"><span data-stu-id="23a2a-122">x86</span></span> | <span data-ttu-id="23a2a-123">Périphérique</span><span class="sxs-lookup"><span data-stu-id="23a2a-123">Device</span></span> |
| <span data-ttu-id="23a2a-124">Casques WMR</span><span class="sxs-lookup"><span data-stu-id="23a2a-124">WMR Headsets</span></span> | <span data-ttu-id="23a2a-125">Release ou Master</span><span class="sxs-lookup"><span data-stu-id="23a2a-125">Release or Master</span></span> | <span data-ttu-id="23a2a-126">x64</span><span class="sxs-lookup"><span data-stu-id="23a2a-126">x64</span></span> | <span data-ttu-id="23a2a-127">Ordinateur local</span><span class="sxs-lookup"><span data-stu-id="23a2a-127">Local Machine</span></span> |

<span data-ttu-id="23a2a-128">**Conseil :** Lors de la génération pour HoloLens 1, HoloLens 2 ou WMR, il est recommandé que les paramètres de build « version du kit de développement logiciel (SDK) cible » et « version de plateforme minimale » se présentent comme dans l’image ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="23a2a-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Fenêtre Build](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="23a2a-130">Les autres paramètres peuvent être différents (par exemple, configuration de build/architecture/type de build, et d’autres peuvent toujours être modifiés dans la solution Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="23a2a-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="23a2a-131">Vérifiez que la liste déroulante « Version cible du Kit de développement logiciel (SDK) » contient l’option « 10.0.18362.0 ». Si ce n’est pas le cas, [le SDK Windows le plus récent](https://developer.microsoft.com/windows/downloads/windows-10-sdk) doit être installé.</span><span class="sxs-lookup"><span data-stu-id="23a2a-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="23a2a-132">Unity 2019.3 et HoloLens</span><span class="sxs-lookup"><span data-stu-id="23a2a-132">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="23a2a-133">Si une application HoloLens apparaît sous la forme d’un panneau 2D sur l’appareil, vérifiez que les paramètres suivants ont été configurés dans Unity 2019.3.x avant de déployer votre application UWP :</span><span class="sxs-lookup"><span data-stu-id="23a2a-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="23a2a-134">Si vous utilisez le XR hérité :</span><span class="sxs-lookup"><span data-stu-id="23a2a-134">If using the legacy XR:</span></span>

1. <span data-ttu-id="23a2a-135">Accédez à Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)</span><span class="sxs-lookup"><span data-stu-id="23a2a-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="23a2a-136">Sous **XR Settings (Paramètres XR)** sous l’onglet UWP, vérifiez que l’option **Virtual Reality Supported (Réalité virtuelle prise en charge)** est activée et que le SDK **Windows Mixed Reality** a été ajouté aux SDK.</span><span class="sxs-lookup"><span data-stu-id="23a2a-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="23a2a-137">Générer et déployer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="23a2a-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="23a2a-138">Si vous utilisez le plug-in XR :</span><span class="sxs-lookup"><span data-stu-id="23a2a-138">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="23a2a-139">Suivez les étapes décrites dans [Prise en main de XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="23a2a-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="23a2a-140">Vérifiez que le profil de configuration est **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="23a2a-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="23a2a-141">Accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), XR-Plugin Management (Gestion du plugin XR)** et vérifiez que **Windows Mixed Reality** est activé.</span><span class="sxs-lookup"><span data-stu-id="23a2a-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="23a2a-142">Générer et déployer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="23a2a-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="23a2a-143">Si vous utilisez Unity 2019.3.x, sélectionnez **ARM64** et non **ARM** comme architecture de build dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="23a2a-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="23a2a-144">Avec les paramètres Unity par défaut dans Unity 2019.3.x, une application Unity n’est pas déployée sur un HoloLens si ARM est sélectionné en raison d’un bogue Unity.</span><span class="sxs-lookup"><span data-stu-id="23a2a-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="23a2a-145">Ce suivi peut être effectué dans le [dispositif de suivi des problèmes d’Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="23a2a-145">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="23a2a-146">Si l’architecture ARM est requise, accédez à **Edit (Modifier) > Project Settings (Paramètres du projet), Player (Lecteur)** , puis dans le menu **Other Settings (Autres paramètres)** , désactivez **Graphics Jobs (Travaux graphiques)** .</span><span class="sxs-lookup"><span data-stu-id="23a2a-146">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="23a2a-147">Même si la désactivation de **Graphics Jobs (Travaux graphiques)** permettra à l’application de se déployer à l’aide de l’architecture de build ARM pour Unity 2019.3.x, ARM64 est recommandé.</span><span class="sxs-lookup"><span data-stu-id="23a2a-147">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="23a2a-148">Génération et déploiement de MRTK sur des casques WMR (autonomes)</span><span class="sxs-lookup"><span data-stu-id="23a2a-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="23a2a-149">Les versions autonomes de MRTK peuvent être utilisées sur des casques WMR.</span><span class="sxs-lookup"><span data-stu-id="23a2a-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="23a2a-150">Une version autonome d’un casque WMR requiert d’effectuer les étapes supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="23a2a-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="23a2a-151">Le SDK XR d’Unity prend également en charge les WMR natifs dans les builds autonomes, mais ne nécessite pas de plug-in WMR ou SteamVR.</span><span class="sxs-lookup"><span data-stu-id="23a2a-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="23a2a-152">Ces étapes sont requises pour les XR hérités d’Unity.</span><span class="sxs-lookup"><span data-stu-id="23a2a-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="23a2a-153">Installer [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="23a2a-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="23a2a-154">Installer [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="23a2a-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="23a2a-155">Installer le [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="23a2a-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="23a2a-156">Utiliser le plug-in WMR</span><span class="sxs-lookup"><span data-stu-id="23a2a-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="23a2a-157">Ouvrir Steam et rechercher le plug-in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="23a2a-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="23a2a-158">Vérifiez que SteamVR est fermé avant de lancer le plug-in WMR.</span><span class="sxs-lookup"><span data-stu-id="23a2a-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="23a2a-159">Le lancement du plug-in WMR a pour effet de lancer également SteamVR.</span><span class="sxs-lookup"><span data-stu-id="23a2a-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="23a2a-160">Vérifiez que le casque WMR est branché.</span><span class="sxs-lookup"><span data-stu-id="23a2a-160">Make sure the WMR headset is plugged in.</span></span>

    ![Recherche de plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="23a2a-162">Sélectionnez **Lancer** pour lancer le plug-in Windows Mixed Reality pour le plug-in SteamVR.</span><span class="sxs-lookup"><span data-stu-id="23a2a-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="23a2a-164">SteamVR et le plug-in WMR démarrent et une nouvelle fenêtre d’état de suivi du casque WMR s’affiche.</span><span class="sxs-lookup"><span data-stu-id="23a2a-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="23a2a-165">Pour plus d’informations, consultez la [documentation sur l’utilisation de Steam avec Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="23a2a-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Apparence du lancement de WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="23a2a-167">Dans Unity, avec votre scène MRTK ouverte, accédez à **File (Fichier) > Build Settings (Paramètres de build)**</span><span class="sxs-lookup"><span data-stu-id="23a2a-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="23a2a-168">Générer la scène</span><span class="sxs-lookup"><span data-stu-id="23a2a-168">Build the scene</span></span>
    - <span data-ttu-id="23a2a-169">Sélectionnez **Ajouter une scène ouverte**</span><span class="sxs-lookup"><span data-stu-id="23a2a-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="23a2a-170">Assurez-vous que la plateforme est définie sur **Standalone (Autonome)** .</span><span class="sxs-lookup"><span data-stu-id="23a2a-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="23a2a-171">Sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="23a2a-171">Select **Build**</span></span>
    - <span data-ttu-id="23a2a-172">Choisissez l’emplacement de la nouvelle build dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="23a2a-172">Choose the location for the new build in File Explorer</span></span>

    ![Paramètres de build pour l’option Autonome](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="23a2a-174">Un nouvel exécutable Unity sera créé. Pour lancer votre application, sélectionnez l’exécutable Unity dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="23a2a-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Explorateur de fichiers dans Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="23a2a-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23a2a-176">See also</span></span>

- [<span data-ttu-id="23a2a-177">Support Android et iOS</span><span class="sxs-lookup"><span data-stu-id="23a2a-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="23a2a-178">Prise en charge de Leap Motion</span><span class="sxs-lookup"><span data-stu-id="23a2a-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="23a2a-179">Détection des fonctionnalités de plateforme</span><span class="sxs-lookup"><span data-stu-id="23a2a-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)