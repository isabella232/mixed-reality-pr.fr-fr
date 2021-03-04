---
title: Configurer votre projet sans MRTK
description: Découvrez comment configurer un nouveau projet Unity pour Windows Mixed Reality sans la boîte à outils de la réalité mixte.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performances
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117623"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="206ab-104">Configuration de votre projet sans MRTK</span><span class="sxs-lookup"><span data-stu-id="206ab-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="206ab-105">Windows Mixed Reality (WMR) est une plate-forme Microsoft introduite dans le cadre du système d’exploitation Windows 10.</span><span class="sxs-lookup"><span data-stu-id="206ab-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="206ab-106">La plateforme WMR vous permet de créer des applications qui restituent du contenu numérique sur des appareils d’écran holographiques et VR.</span><span class="sxs-lookup"><span data-stu-id="206ab-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="206ab-107">Alors que Microsoft et la communauté ont créé des outils open source tels que le [Kit de MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) qui configure automatiquement l’environnement WMR, de nombreux développeurs souhaitent créer leurs expériences dès le départ.</span><span class="sxs-lookup"><span data-stu-id="206ab-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="206ab-108">La documentation suivante montre comment configurer correctement un projet pour le développement de réalité mixte, que vous utilisiez MRTK ou non.</span><span class="sxs-lookup"><span data-stu-id="206ab-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="206ab-109">Les paramètres que vous devez modifier sont divisés en deux catégories : les paramètres par projet et les paramètres par scène.</span><span class="sxs-lookup"><span data-stu-id="206ab-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="206ab-110">Vous pouvez toujours importer des MRTK par la suite. il n’y a donc aucune pénalité pour passer d’abord à l’itinéraire manuel.</span><span class="sxs-lookup"><span data-stu-id="206ab-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="206ab-111">Si vous choisissez la configuration manuelle WMR, les paramètres que vous devez modifier sont réparties en deux catégories : par projet et par scène.</span><span class="sxs-lookup"><span data-stu-id="206ab-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="206ab-112">Paramètres par projet</span><span class="sxs-lookup"><span data-stu-id="206ab-112">Per-project settings</span></span>

<span data-ttu-id="206ab-113">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="206ab-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](images/wmr-config-img-3.png)

<span data-ttu-id="206ab-115">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="206ab-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="206ab-116">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="206ab-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="206ab-117">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="206ab-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="206ab-118">Définir l' **architecture** sur **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="206ab-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="206ab-119">Définir l' **appareil cible** sur **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="206ab-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="206ab-120">Définir le **type de build** sur **D3D**</span><span class="sxs-lookup"><span data-stu-id="206ab-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="206ab-121">Définir le **SDK UWP** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="206ab-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="206ab-122">Définir la **configuration de build** sur **Release** en raison de problèmes de performances connus avec Debug</span><span class="sxs-lookup"><span data-stu-id="206ab-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](images/wmr-config-img-4.png)

<span data-ttu-id="206ab-124">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.</span><span class="sxs-lookup"><span data-stu-id="206ab-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="206ab-125">Pour XRSDK</span><span class="sxs-lookup"><span data-stu-id="206ab-125">For XRSDK</span></span> 

1. <span data-ttu-id="206ab-126">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="206ab-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="206ab-127">Sélectionnez **installer la gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="206ab-127">Select **Install XR Plugin Management**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-5.png)

3. <span data-ttu-id="206ab-129">Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="206ab-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-7.png)

4. <span data-ttu-id="206ab-131">Développez la section **gestion du plug-in XR** et sélectionnez universels onglet Paramètres de la **plateforme Windows** .</span><span class="sxs-lookup"><span data-stu-id="206ab-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="206ab-132">Si vous utilisez Unity 2020 ou une version ultérieure, vous verrez les options permettant de vérifier **OpenXR (version préliminaire)** ou **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="206ab-132">If you are using Unity 2020 or later, you will see the options to check **OpenXR (preview)** or **Windows Mixed Reality**</span></span>
6. <span data-ttu-id="206ab-133">Vous pouvez choisir l’un ou l’autre Runtime.</span><span class="sxs-lookup"><span data-stu-id="206ab-133">You can choose either runtime.</span></span>  <span data-ttu-id="206ab-134">Si vous développez spécifiquement pour HoloLens 2 ou la réverbération HP G2 et que vous décidez d’essayer **OpenXR (** préversion), sélectionnez la zone OpenXR (préversion) et consultez notre guide pour [utiliser le plug-in OpenXR de réalité mixte pour Unity](openxr-getting-started.md) afin de vous préparer correctement à ces appareils avant de revenir à ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="206ab-134">If you are specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR (preview)**, select the OpenXR (preview) box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>
7. <span data-ttu-id="206ab-135">Si vous décidez de choisir le plug-in **Windows Mixed Reality** , cochez toutes les cases et définissez le **mode d’envoi de profondeur** sur une profondeur de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="206ab-135">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="206ab-137">Pour les XR hérités</span><span class="sxs-lookup"><span data-stu-id="206ab-137">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="206ab-138">Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="206ab-138">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="206ab-139">Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**</span><span class="sxs-lookup"><span data-stu-id="206ab-139">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="206ab-140">Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle</span><span class="sxs-lookup"><span data-stu-id="206ab-140">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="206ab-141">Définir le **format de profondeur** sur **16 bits** et activer le partage de **mémoire tampon de profondeur**</span><span class="sxs-lookup"><span data-stu-id="206ab-141">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="206ab-142">Définir le **mode de rendu stéréo** sur **une seule instance de passage**</span><span class="sxs-lookup"><span data-stu-id="206ab-142">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="206ab-143">Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="206ab-143">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="206ab-145">Mise à jour du manifeste</span><span class="sxs-lookup"><span data-stu-id="206ab-145">Updating the manifest</span></span>

<span data-ttu-id="206ab-146">Votre application peut désormais gérer le rendu holographique et l’entrée spatiale.</span><span class="sxs-lookup"><span data-stu-id="206ab-146">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="206ab-147">Toutefois, votre application doit déclarer les fonctionnalités appropriées dans son manifeste pour tirer parti de certaines fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="206ab-147">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="206ab-148">Vous pouvez trouver les fonctionnalités de vos projets en accédant à **paramètres du lecteur > paramètres pour plateforme Windows universelle > paramètres de publication > fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="206ab-148">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="206ab-149">Il est recommandé de rendre les déclarations de manifeste dans Unity pour les inclure dans tous les projets futurs que vous exportez.</span><span class="sxs-lookup"><span data-stu-id="206ab-149">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="206ab-150">Les fonctionnalités applicables à l’activation des API Unity couramment utilisées pour la réalité mixte sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="206ab-150">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="206ab-151">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="206ab-151">Capability</span></span>  |  <span data-ttu-id="206ab-152">API nécessitant des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="206ab-152">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="206ab-153">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="206ab-153">SpatialPerception</span></span>  |  <span data-ttu-id="206ab-154">SurfaceObserver (accès aux maillages de [mappage spatial](../../design/spatial-mapping.md) sur HoloLens) &mdash; *aucune fonctionnalité nécessaire pour le suivi spatial général du casque*</span><span class="sxs-lookup"><span data-stu-id="206ab-154">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="206ab-155">WebCam</span><span class="sxs-lookup"><span data-stu-id="206ab-155">WebCam</span></span>  |  <span data-ttu-id="206ab-156">PhotoCapture et VideoCapture</span><span class="sxs-lookup"><span data-stu-id="206ab-156">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="206ab-157">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="206ab-157">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="206ab-158">PhotoCapture ou VideoCapture, respectivement (lors du stockage du contenu capturé)</span><span class="sxs-lookup"><span data-stu-id="206ab-158">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="206ab-159">Microphone</span><span class="sxs-lookup"><span data-stu-id="206ab-159">Microphone</span></span>  |  <span data-ttu-id="206ab-160">VideoCapture (lors de la capture de l’audio), DictationRecognizer, GrammarRecognizer et KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="206ab-160">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="206ab-161">InternetClient</span><span class="sxs-lookup"><span data-stu-id="206ab-161">InternetClient</span></span>  |  <span data-ttu-id="206ab-162">DictationRecognizer (et pour utiliser le profileur Unity)</span><span class="sxs-lookup"><span data-stu-id="206ab-162">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="206ab-163">Paramètres de qualité</span><span class="sxs-lookup"><span data-stu-id="206ab-163">Quality settings</span></span>

<span data-ttu-id="206ab-164">HoloLens possède un GPU de classe mobile.</span><span class="sxs-lookup"><span data-stu-id="206ab-164">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="206ab-165">Si votre application cible HoloLens, vous devez commencer par les paramètres de qualité de votre application réglés pour des performances plus rapides afin de garantir qu’elle gère la fréquence d’images complète.</span><span class="sxs-lookup"><span data-stu-id="206ab-165">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="206ab-166">Une fois que vous avez plus d’informations sur votre développement, vous pouvez envisager de Upping les paramètres de qualité pour trouver le juste équilibre entre qualité et performances :</span><span class="sxs-lookup"><span data-stu-id="206ab-166">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="206ab-167">Sélectionnez **modifier > paramètres du projet > qualité**</span><span class="sxs-lookup"><span data-stu-id="206ab-167">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="206ab-168">Sélectionnez la **liste déroulante** sous le logo du  **Windows Store**   et sélectionnez  **très faible**.</span><span class="sxs-lookup"><span data-stu-id="206ab-168">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="206ab-169">Vous saurez que le paramètre est appliqué correctement lorsque la zone de la colonne du Windows Store et la ligne très basse sont vertes</span><span class="sxs-lookup"><span data-stu-id="206ab-169">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="206ab-170">Dans la section **Shadows**   , sélectionnez **Disable Shadows** .</span><span class="sxs-lookup"><span data-stu-id="206ab-170">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="206ab-171">![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres de qualité mise en surbrillance](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="206ab-171">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="206ab-172">*Paramètres de qualité Unity*</span><span class="sxs-lookup"><span data-stu-id="206ab-172">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="206ab-173">Paramètres par scène</span><span class="sxs-lookup"><span data-stu-id="206ab-173">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="206ab-174">Paramètres de l’appareil photo Unity</span><span class="sxs-lookup"><span data-stu-id="206ab-174">Unity camera settings</span></span>

<span data-ttu-id="206ab-175">Une fois la **réalité virtuelle prise en charge** activée, le composant [appareil photo Unity](camera-in-unity.md) gère le [suivi des têtes et le rendu stéréoscopique](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="206ab-175">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="206ab-176">Cela signifie que vous n’avez pas besoin de remplacer l’objet caméra principal par une caméra personnalisée.</span><span class="sxs-lookup"><span data-stu-id="206ab-176">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="206ab-177">Si votre application cible en particulier HoloLens, vous devez modifier quelques paramètres pour optimiser les affichages transparents de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="206ab-177">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="206ab-178">Ces paramètres permettent à votre contenu holographique de s’afficher dans le monde physique :</span><span class="sxs-lookup"><span data-stu-id="206ab-178">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="206ab-179">Dans la **hiérarchie**, sélectionnez l' **appareil photo principal** .</span><span class="sxs-lookup"><span data-stu-id="206ab-179">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="206ab-180">Dans le panneau **inspecteur** , définissez la **position** de la transformation sur **0, 0, 0** de sorte que l’emplacement de la tête de l’utilisateur commence à l’origine Unity World.</span><span class="sxs-lookup"><span data-stu-id="206ab-180">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="206ab-181">Remplacez **effacer les indicateurs** par **couleur unie**.</span><span class="sxs-lookup"><span data-stu-id="206ab-181">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="206ab-182">Remplacez la couleur d' **arrière-plan** par **RVBA 0, 0,** 0, 0.</span><span class="sxs-lookup"><span data-stu-id="206ab-182">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="206ab-183">Le rendu noir est transparent dans HoloLens.</span><span class="sxs-lookup"><span data-stu-id="206ab-183">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="206ab-184">Modifiez les **plans de découpage-près** de [HoloLens recommandé](camera-in-unity.md#clip-planes) 0,85 (mètres).</span><span class="sxs-lookup"><span data-stu-id="206ab-184">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="206ab-185">![Capture d’écran de l’onglet inspecteur ouvert dans l’éditeur Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="206ab-185">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="206ab-186">*Paramètres de l’appareil photo Unity*</span><span class="sxs-lookup"><span data-stu-id="206ab-186">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="206ab-187">Si vous supprimez et créez un appareil photo, assurez-vous que votre nouvelle caméra est marquée comme **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="206ab-187">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="206ab-188">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="206ab-188">Next steps</span></span>

<span data-ttu-id="206ab-189">Maintenant que votre projet est prêt, vous pouvez commencer à développer votre expérience de réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="206ab-189">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="206ab-190">Ajouter des [blocs de construction principaux](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="206ab-190">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="206ab-191">Découvrez les [API et les fonctionnalités de plateforme](unity-development-overview.md#3-advanced-features) disponibles</span><span class="sxs-lookup"><span data-stu-id="206ab-191">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="206ab-192">Découvrez comment [déployer votre application](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="206ab-192">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="206ab-193">Utiliser le [simulateur de réalité mixte](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="206ab-193">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="206ab-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="206ab-194">See also</span></span>
* [<span data-ttu-id="206ab-195">Installer les outils</span><span class="sxs-lookup"><span data-stu-id="206ab-195">Install the tools</span></span>](../install-the-tools.md)