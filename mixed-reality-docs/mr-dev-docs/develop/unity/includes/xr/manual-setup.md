---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112536160"
---
# <a name="openxr"></a>[<span data-ttu-id="6c1de-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="6c1de-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="6c1de-102">Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="6c1de-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="6c1de-103">Suivez les [instructions d’installation et d’utilisation](../../welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de réalité mixte** dans la catégorie **prise en charge** de la plateforme :</span><span class="sxs-lookup"><span data-stu-id="6c1de-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="6c1de-105">Définition de votre cible de génération</span><span class="sxs-lookup"><span data-stu-id="6c1de-105">Setting your build target</span></span>

<span data-ttu-id="6c1de-106">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="6c1de-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="6c1de-108">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="6c1de-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="6c1de-109">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="6c1de-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="6c1de-110">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="6c1de-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="6c1de-111">Définissez **Architecture** sur **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="6c1de-112">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="6c1de-113">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="6c1de-114">Définir la **version du SDK cible** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="6c1de-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="6c1de-116">Configuration de la gestion des plug-ins XR pour OpenXR</span><span class="sxs-lookup"><span data-stu-id="6c1de-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="6c1de-117">Pour définir OpenXR comme Runtime dans Unity :</span><span class="sxs-lookup"><span data-stu-id="6c1de-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="6c1de-118">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**</span><span class="sxs-lookup"><span data-stu-id="6c1de-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="6c1de-119">Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="6c1de-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="6c1de-120">Sélectionnez **installer la gestion des plug-ins XR** s’il s’agit ![ d’une capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="6c1de-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="6c1de-121">Cochez la case **Initialize XR on Startup** .</span><span class="sxs-lookup"><span data-stu-id="6c1de-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="6c1de-122">Si vous ciblez Desktop VR, restez sur l’onglet autonome du PC (le moniteur) et cochez les cases de l’ensemble de fonctionnalités **OpenXR** et **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="6c1de-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="6c1de-123">Si vous ciblez HoloLens 2, basculez vers l’onglet plateforme Windows universelle (le logo Windows), puis sélectionnez les zones ensemble de fonctionnalités **OpenXR** et **Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="6c1de-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="6c1de-125">Si vous voyez une icône d’avertissement jaune en regard du **plug-in OpenXR**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6c1de-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="6c1de-126">L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="6c1de-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Capture d’écran de la fenêtre de validation du projet OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="6c1de-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="6c1de-128">Optimization</span></span>

<span data-ttu-id="6c1de-129">Si vous développez pour HoloLens 2, sélectionnez le **projet > de la réalité mixte > appliquer les paramètres de projet recommandés pour** l’élément de menu HoloLens 2 afin d’obtenir de meilleures performances d’application.</span><span class="sxs-lookup"><span data-stu-id="6c1de-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](../../images/openxr-img-08.png)

<span data-ttu-id="6c1de-131">Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !</span><span class="sxs-lookup"><span data-stu-id="6c1de-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="6c1de-132">Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.</span><span class="sxs-lookup"><span data-stu-id="6c1de-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="6c1de-133">Exemples de projets Unity pour OpenXR et HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6c1de-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="6c1de-134">Consultez les [exemples de référentiel OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) pour les exemples de projets Unity montrant comment créer des applications Unity pour des casques HoloLens 2 ou de réalité mixte à l’aide du plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="6c1de-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="6c1de-135">Ou, si vous êtes prêt à commencer par vous-même à partir d’un projet vide, passez à l’article Configuration de l' [appareil photo](../../camera-in-unity.md) .</span><span class="sxs-lookup"><span data-stu-id="6c1de-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="6c1de-136">XR Windows</span><span class="sxs-lookup"><span data-stu-id="6c1de-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="6c1de-137">Le plug-in XR Windows est déconseillé dans Unity 2021,1 et sera supprimé dans Unity 2021,2.</span><span class="sxs-lookup"><span data-stu-id="6c1de-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="6c1de-138">Pour le développement Unity 2020, Microsoft recommande le plug-in OpenXR à la place.</span><span class="sxs-lookup"><span data-stu-id="6c1de-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="6c1de-139">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="6c1de-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="6c1de-141">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="6c1de-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="6c1de-142">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="6c1de-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="6c1de-143">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="6c1de-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="6c1de-144">Définissez **Architecture** sur **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="6c1de-145">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="6c1de-146">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="6c1de-147">Définir la **version du SDK cible** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="6c1de-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="6c1de-148">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="6c1de-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

<span data-ttu-id="6c1de-150">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :</span><span class="sxs-lookup"><span data-stu-id="6c1de-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="6c1de-151">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="6c1de-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="6c1de-152">Sélectionnez **installer la gestion des plug-ins XR** si elle apparaît</span><span class="sxs-lookup"><span data-stu-id="6c1de-152">Select **Install XR Plugin Management** if it appears</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="6c1de-154">Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="6c1de-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="6c1de-156">Sélectionnez la section **gestion du plug-in XR**  >  **Windows Mixed Reality** , cochez toutes les cases et définissez le format de la **mémoire tampon** de profondeur sur le **tampon de profondeur 16 bits**</span><span class="sxs-lookup"><span data-stu-id="6c1de-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="6c1de-158">XR antérieur</span><span class="sxs-lookup"><span data-stu-id="6c1de-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="6c1de-159">Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="6c1de-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="6c1de-160">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="6c1de-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="6c1de-162">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="6c1de-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="6c1de-163">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="6c1de-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="6c1de-164">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="6c1de-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="6c1de-165">Définissez **Architecture** sur **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="6c1de-166">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="6c1de-167">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="6c1de-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="6c1de-168">Définir la **version du SDK cible** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="6c1de-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="6c1de-169">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="6c1de-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

<span data-ttu-id="6c1de-171">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.</span><span class="sxs-lookup"><span data-stu-id="6c1de-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="6c1de-172">Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**</span><span class="sxs-lookup"><span data-stu-id="6c1de-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="6c1de-173">Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle</span><span class="sxs-lookup"><span data-stu-id="6c1de-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="6c1de-174">Définissez le **format de profondeur** sur **16 bits** et cochez **activer le partage du tampon de profondeur**</span><span class="sxs-lookup"><span data-stu-id="6c1de-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="6c1de-175">Définissez **Stereo Rendering Mode** (Mode de rendu stéréo) sur **Single Pass Instanced** (Instance à passe unique).</span><span class="sxs-lookup"><span data-stu-id="6c1de-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="6c1de-176">Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser l’accès distant en mode de lecture holographique</span><span class="sxs-lookup"><span data-stu-id="6c1de-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](../../images/wmr-config-img-9.png)
