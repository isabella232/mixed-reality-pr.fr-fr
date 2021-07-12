---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603712"
---
# <a name="openxr"></a>[<span data-ttu-id="4229d-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4229d-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="4229d-102">Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="4229d-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="4229d-103">Suivez les [instructions d’installation et d’utilisation](../../welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de réalité mixte** dans la catégorie **prise en charge** de la plateforme :</span><span class="sxs-lookup"><span data-stu-id="4229d-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="4229d-105">Définition de votre cible de génération</span><span class="sxs-lookup"><span data-stu-id="4229d-105">Setting your build target</span></span>

<span data-ttu-id="4229d-106">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="4229d-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="4229d-108">si vous ciblez HoloLens 2, vous devez basculer vers le plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="4229d-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="4229d-109">sélectionner le **fichier > la Paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="4229d-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="4229d-110">sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="4229d-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="4229d-111">Définissez **Architecture** sur **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="4229d-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="4229d-112">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="4229d-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="4229d-113">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="4229d-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="4229d-114">Définir la **version du SDK cible** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="4229d-114">Set **Target SDK Version** to **Latest installed**</span></span>

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="4229d-116">Configuration de la gestion des plug-ins XR pour OpenXR</span><span class="sxs-lookup"><span data-stu-id="4229d-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="4229d-117">Pour définir OpenXR comme Runtime dans Unity :</span><span class="sxs-lookup"><span data-stu-id="4229d-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="4229d-118">dans l’éditeur unity, accédez à **modifier > Project Paramètres**</span><span class="sxs-lookup"><span data-stu-id="4229d-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="4229d-119">dans la liste des Paramètres, sélectionnez **gestion des plug-ins XR** (doit déjà être installé si vous avez installé le plug-in OpenXR de réalité mixte à l’aide de MRFT)</span><span class="sxs-lookup"><span data-stu-id="4229d-119">In the list of Settings, select **XR Plugin Management** (should already be installed if you installed the Mixed Reality OpenXR plugin using MRFT)</span></span>
3. <span data-ttu-id="4229d-120">Cochez la case **Initialize XR on Startup** .</span><span class="sxs-lookup"><span data-stu-id="4229d-120">Check the **Initialize XR on Startup** box</span></span>
4. <span data-ttu-id="4229d-121">si vous ciblez Desktop VR, restez sur l’onglet autonome du PC (le moniteur) et cochez les cases **OpenXR** et **Windows Mixed Reality ensemble de fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="4229d-121">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
5. <span data-ttu-id="4229d-122">si vous ciblez HoloLens 2, basculez vers l’onglet plateforme Windows universelle (le logo Windows) et sélectionnez les zones de **jeu de fonctionnalités** **OpenXR** et Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="4229d-122">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="4229d-124">Si vous voyez une icône d’avertissement jaune en regard du **plug-in OpenXR**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="4229d-124">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="4229d-125">L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="4229d-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Capture d’écran de la fenêtre de validation du projet OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="4229d-127">Optimization</span><span class="sxs-lookup"><span data-stu-id="4229d-127">Optimization</span></span>

<span data-ttu-id="4229d-128">si vous développez pour HoloLens 2, sélectionnez l’élément de menu **> de réalité mixte Project > appliquer les paramètres de projet recommandés pour HoloLens 2** pour obtenir de meilleures performances d’application.</span><span class="sxs-lookup"><span data-stu-id="4229d-128">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](../../images/openxr-img-08.png)

<span data-ttu-id="4229d-130">Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !</span><span class="sxs-lookup"><span data-stu-id="4229d-130">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="4229d-131">Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.</span><span class="sxs-lookup"><span data-stu-id="4229d-131">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="4229d-132">Exemples de projets Unity pour OpenXR et HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4229d-132">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="4229d-133">consultez les [exemples de référentiel OpenXR Mixed reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) pour obtenir des exemples de projets unity montrant comment créer des applications unity pour HoloLens 2 ou des casques de réalité mixtes à l’aide du plug-in OpenXR de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="4229d-133">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="4229d-134">Ou, si vous êtes prêt à commencer par vous-même à partir d’un projet vide, passez à l’article Configuration de l' [appareil photo](../../camera-in-unity.md) .</span><span class="sxs-lookup"><span data-stu-id="4229d-134">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="4229d-135">Windows XR</span><span class="sxs-lookup"><span data-stu-id="4229d-135">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="4229d-136">le plug-in Windows XR est déconseillé dans unity 2021,1 et sera supprimé dans unity 2021,2.</span><span class="sxs-lookup"><span data-stu-id="4229d-136">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="4229d-137">Pour le développement Unity 2020, Microsoft recommande le plug-in OpenXR à la place.</span><span class="sxs-lookup"><span data-stu-id="4229d-137">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="4229d-138">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="4229d-138">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="4229d-140">si vous ciblez HoloLens 2, vous devez basculer vers le plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="4229d-140">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="4229d-141">sélectionner le **fichier > la Paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="4229d-141">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="4229d-142">sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="4229d-142">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="4229d-143">Définissez **Architecture** sur **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="4229d-143">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="4229d-144">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="4229d-144">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="4229d-145">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="4229d-145">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="4229d-146">Définir la **version du SDK cible** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="4229d-146">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="4229d-147">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="4229d-147">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

<span data-ttu-id="4229d-149">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :</span><span class="sxs-lookup"><span data-stu-id="4229d-149">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="4229d-150">dans l’éditeur unity, accédez à **modifier > paramètres Project** et sélectionnez **gestion du plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="4229d-150">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="4229d-151">Sélectionnez **installer la gestion des plug-ins XR** si elle apparaît</span><span class="sxs-lookup"><span data-stu-id="4229d-151">Select **Install XR Plugin Management** if it appears</span></span>

![capture d’écran de la fenêtre de Paramètres Project ouverte dans l’éditeur unity avec la gestion du plug-in XR mise en évidence](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="4229d-153">sélectionnez **initialize XR au démarrage** et **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="4229d-153">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![capture d’écran de la fenêtre paramètres Project ouverte dans l’éditeur unity avec la gestion du plug-in XR mise en évidence](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="4229d-155">sélectionnez la section Windows Mixed Reality **de la gestion du Plug-in XR**  >   , cochez toutes les cases et définissez le Format de la **mémoire tampon** de profondeur sur le **tampon de profondeur 16 bits**</span><span class="sxs-lookup"><span data-stu-id="4229d-155">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![capture d’écran de la fenêtre paramètres Project ouverte dans l’éditeur unity avec la section Windows Mixed Reality mise en surbrillance](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="4229d-157">XR antérieur</span><span class="sxs-lookup"><span data-stu-id="4229d-157">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="4229d-158">Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="4229d-158">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="4229d-159">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="4229d-159">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="4229d-161">si vous ciblez HoloLens 2, vous devez basculer vers le plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="4229d-161">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="4229d-162">sélectionner le **fichier > la Paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="4229d-162">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="4229d-163">sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="4229d-163">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="4229d-164">Définissez **Architecture** sur **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="4229d-164">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="4229d-165">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="4229d-165">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="4229d-166">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="4229d-166">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="4229d-167">Définir la **version du SDK cible** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="4229d-167">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="4229d-168">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="4229d-168">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

<span data-ttu-id="4229d-170">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.</span><span class="sxs-lookup"><span data-stu-id="4229d-170">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="4229d-171">ouvrir le **Paramètres du lecteur...** à partir de la **Paramètres de Build... et** développez le groupe de **Paramètres XR**</span><span class="sxs-lookup"><span data-stu-id="4229d-171">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="4229d-172">dans la section **Paramètres XR** , sélectionnez **virtual reality pris en charge** pour ajouter la liste des appareils de réalité virtuelle</span><span class="sxs-lookup"><span data-stu-id="4229d-172">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="4229d-173">Définissez le **format de profondeur** sur **16 bits** et cochez **activer le partage du tampon de profondeur**</span><span class="sxs-lookup"><span data-stu-id="4229d-173">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="4229d-174">Définissez **Stereo Rendering Mode** (Mode de rendu stéréo) sur **Single Pass Instanced** (Instance à passe unique).</span><span class="sxs-lookup"><span data-stu-id="4229d-174">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="4229d-175">Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser l’accès distant en mode de lecture holographique</span><span class="sxs-lookup"><span data-stu-id="4229d-175">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![capture d’écran de la fenêtre paramètres Project ouverte dans l’éditeur unity avec la section paramètres du lecteur mise en surbrillance](../../images/wmr-config-img-9.png)
