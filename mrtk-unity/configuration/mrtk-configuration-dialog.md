---
title: Boîte de dialogue de configuration MRTK
description: Configurer MRTK dans le projet Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Unity
ms.openlocfilehash: ef326a4e4c9e34479cebacf3f3f575cd902ff24e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144832"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="ac253-104">Boîte de dialogue de configuration de projet MRTK</span><span class="sxs-lookup"><span data-stu-id="ac253-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="ac253-105">La boîte de dialogue de configuration MRTK s’affiche lorsque Unity charge un projet et détermine qu’une ou plusieurs options de configuration nécessitent l’attention du développeur.</span><span class="sxs-lookup"><span data-stu-id="ac253-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Appliquer ultérieurement ignorer](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="ac253-107">Pour appliquer les modifications, cliquez sur le bouton **appliquer** .</span><span class="sxs-lookup"><span data-stu-id="ac253-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="ac253-108">Le bouton **ultérieur** diffère les modifications jusqu’à ce que le projet soit rechargé à une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ac253-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="ac253-109">La boîte de dialogue de configuration s’affiche à présent si un ou plusieurs des paramètres recommandés restent désactivés.</span><span class="sxs-lookup"><span data-stu-id="ac253-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="ac253-110">Pour éviter ce problème, appliquez les options souhaitées, puis relancez la boîte de dialogue via les utilitaires de la **réalité mixte du kit**  >    >  de **configuration** , puis cliquez sur **Ignorer**.</span><span class="sxs-lookup"><span data-stu-id="ac253-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="ac253-111">Cela empêchera la boîte de dialogue de configuration de réapparaître automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ac253-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="ac253-112">Paramètres communs</span><span class="sxs-lookup"><span data-stu-id="ac253-112">Common settings</span></span>

<span data-ttu-id="ac253-113">Toutes les cibles de build partagent une collection d’options communes.</span><span class="sxs-lookup"><span data-stu-id="ac253-113">All build targets share a collection of common options.</span></span>

![Paramètres courants](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="ac253-115">Forcer la sérialisation des éléments de texte et activer les fichiers de métadonnées visibles</span><span class="sxs-lookup"><span data-stu-id="ac253-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="ac253-116">Ces paramètres permettent de simplifier l’utilisation des projets Unity et des systèmes de contrôle de code source (par ex. git).</span><span class="sxs-lookup"><span data-stu-id="ac253-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="ac253-117">Activer VR pris en charge</span><span class="sxs-lookup"><span data-stu-id="ac253-117">Enable VR supported</span></span>

<span data-ttu-id="ac253-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="ac253-118">**Unity 2018**</span></span>

<span data-ttu-id="ac253-119">Configure les options de la réalité virtuelle prise en charge et du SDK Virtual Reality dans les paramètres du **lecteur**  >  **paramètres XR**.</span><span class="sxs-lookup"><span data-stu-id="ac253-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="ac253-120">Définir le chemin de rendu de l’instance à passage unique</span><span class="sxs-lookup"><span data-stu-id="ac253-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="ac253-121">Configure les paramètres du **lecteur**  >  **XR** le  >  **mode de rendu stéréo** sur **une instance à passage unique**.</span><span class="sxs-lookup"><span data-stu-id="ac253-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="ac253-122">Définir la couche de sensibilisation spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="ac253-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="ac253-123">Enregistre la sensibilisation spatiale en tant que couche 31 pour permettre une configuration simple et cohérente des options raycast et physique.</span><span class="sxs-lookup"><span data-stu-id="ac253-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="ac253-124">Spatializer audio</span><span class="sxs-lookup"><span data-stu-id="ac253-124">Audio spatializer</span></span>

<span data-ttu-id="ac253-125">Les spatializers audio sont les composants qui déverrouillent la puissance du son spatial et de l’audio positionnel pour rendre les expériences de la réalité mélangée véritablement immersives.</span><span class="sxs-lookup"><span data-stu-id="ac253-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="ac253-126">La définition du Spatializer audio sur aucun désactive les fonctionnalités audio positionnelles.</span><span class="sxs-lookup"><span data-stu-id="ac253-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="ac253-127">Spatializers courantes</span><span class="sxs-lookup"><span data-stu-id="ac253-127">Common spatializers</span></span>

- <span data-ttu-id="ac253-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="ac253-128">Microsoft Spatializer</span></span>

<span data-ttu-id="ac253-129">Microsoft a fourni Spatializer qui prend en charge l’utilisation de l’accélération matérielle sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ac253-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="ac253-130">Ce Spatializer est disponible via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) et [GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="ac253-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="ac253-131">Pour plus d’informations sur Microsoft Spatializer, consultez la [documentation sur le son spatial](/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="ac253-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="ac253-132">MS HRTF Spatializer</span><span class="sxs-lookup"><span data-stu-id="ac253-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="ac253-133">Microsoft Windows Spatializer fourni par Unity dans le cadre des packages Windows Mixed Reality et Windows XR Platform.</span><span class="sxs-lookup"><span data-stu-id="ac253-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="ac253-134">Resonance audio</span><span class="sxs-lookup"><span data-stu-id="ac253-134">Resonance Audio</span></span>

<span data-ttu-id="ac253-135">Spatializer multiplateforme de Google, fournie par Unity.</span><span class="sxs-lookup"><span data-stu-id="ac253-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="ac253-136">Pour plus d’informations, consultez le site de [documentation audio](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) sur la résonance.</span><span class="sxs-lookup"><span data-stu-id="ac253-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="ac253-137">Paramètres de plateforme Windows universelle</span><span class="sxs-lookup"><span data-stu-id="ac253-137">Universal Windows Platform settings</span></span>

![Paramètres UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="ac253-139">Fonctionnalités UWP</span><span class="sxs-lookup"><span data-stu-id="ac253-139">UWP Capabilities</span></span>

<span data-ttu-id="ac253-140">Active des fonctionnalités d’application spécifiques pour plateforme Windows universelle application.</span><span class="sxs-lookup"><span data-stu-id="ac253-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="ac253-141">Ces fonctionnalités permettent à la plateforme d’informer et de demander l’autorisation d’activer des fonctionnalités spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ac253-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="ac253-142">Microphone</span><span class="sxs-lookup"><span data-stu-id="ac253-142">Microphone</span></span>

  <span data-ttu-id="ac253-143">Permet la capture du son via le microphone.</span><span class="sxs-lookup"><span data-stu-id="ac253-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="ac253-144">Client Internet</span><span class="sxs-lookup"><span data-stu-id="ac253-144">Internet Client</span></span>

  <span data-ttu-id="ac253-145">Active la prise en charge de l’accès aux ressources sur Internet.</span><span class="sxs-lookup"><span data-stu-id="ac253-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="ac253-146">Perception spatiale</span><span class="sxs-lookup"><span data-stu-id="ac253-146">Spatial Perception</span></span>

  <span data-ttu-id="ac253-147">Active la prise en charge de l’environnement réel.</span><span class="sxs-lookup"><span data-stu-id="ac253-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="ac253-148">Point de regard</span><span class="sxs-lookup"><span data-stu-id="ac253-148">Eye Gaze</span></span>

  <span data-ttu-id="ac253-149">**Unity 2019,3 et versions ultérieures**</span><span class="sxs-lookup"><span data-stu-id="ac253-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="ac253-150">Active la prise en charge du suivi de l’oeil de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ac253-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="ac253-151">Éviter le blocage de Unity « PlayerSettings. graphicsJob »</span><span class="sxs-lookup"><span data-stu-id="ac253-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="ac253-152">**Unity 2019,3 et versions ultérieures**</span><span class="sxs-lookup"><span data-stu-id="ac253-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="ac253-153">Dans la dernière version de Unity 2019, lorsque l’option « travaux graphiques » est activée, l’application se bloque lors du déploiement sur un HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ac253-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="ac253-154">Ce paramètre est activé par défaut dans Unity : si ce bogue existe (voir le [bogue Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), le configurateur définit par défaut les tâches graphiques sur « false » (ce qui permet aux applications déployées sur HoloLens 2 de ne pas se bloquer).</span><span class="sxs-lookup"><span data-stu-id="ac253-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="ac253-155">Paramètres Android</span><span class="sxs-lookup"><span data-stu-id="ac253-155">Android settings</span></span>

<span data-ttu-id="ac253-156">Paramètres de configuration pour la prise en charge des applications AR sur des appareils Android.</span><span class="sxs-lookup"><span data-stu-id="ac253-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Paramètres Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="ac253-158">Désactiver le rendu multithread</span><span class="sxs-lookup"><span data-stu-id="ac253-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="ac253-159">Désactive les **paramètres du lecteur**  >  **autres paramètres** de  >  **rendu multithread** comme requis par la prise en charge des fournisseurs d’appareils Android.</span><span class="sxs-lookup"><span data-stu-id="ac253-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="ac253-160">Définir le niveau d’API minimal</span><span class="sxs-lookup"><span data-stu-id="ac253-160">Set Minimum API Level</span></span>

<span data-ttu-id="ac253-161">Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **niveau d’API minimal** pour appliquer la configuration de système d’exploitation requise pour les applications AR.</span><span class="sxs-lookup"><span data-stu-id="ac253-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="ac253-162">Paramètres iOS</span><span class="sxs-lookup"><span data-stu-id="ac253-162">iOS settings</span></span>

<span data-ttu-id="ac253-163">Paramètres de configuration pour la prise en charge des applications AR sur des appareils iOS.</span><span class="sxs-lookup"><span data-stu-id="ac253-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Paramètres iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="ac253-165">Définir la version requise du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="ac253-165">Set Required OS Version</span></span>

<span data-ttu-id="ac253-166">Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **ciblent la version IOS minimale** pour appliquer la configuration de système d’exploitation requise pour les applications AR.</span><span class="sxs-lookup"><span data-stu-id="ac253-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="ac253-167">Définir l’architecture requise</span><span class="sxs-lookup"><span data-stu-id="ac253-167">Set Required Architecture</span></span>

<span data-ttu-id="ac253-168">Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **architecture** pour appliquer les spécifications de plateforme pour les applications AR.</span><span class="sxs-lookup"><span data-stu-id="ac253-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="ac253-169">Définir les descriptions de l’utilisation de l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="ac253-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="ac253-170">Définit la valeur des **paramètres du lecteur**  >  **autres paramètres**  >  **Description de l’utilisation de l’appareil photo** utilisée pour demander l’autorisation d’utiliser l’appareil photo de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="ac253-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>