---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394583"
---
# <a name="openxr"></a>[<span data-ttu-id="63d25-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="63d25-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="63d25-102">Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="63d25-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="63d25-103">Suivez les [instructions d’installation et d’utilisation](../../welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de la réalité mixte** dans la catégorie de la réalité mixte Toolkit :</span><span class="sxs-lookup"><span data-stu-id="63d25-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="63d25-105">Définition de votre cible de génération</span><span class="sxs-lookup"><span data-stu-id="63d25-105">Setting your build target</span></span>

<span data-ttu-id="63d25-106">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="63d25-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="63d25-108">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="63d25-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="63d25-109">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="63d25-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="63d25-110">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="63d25-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="63d25-111">Définissez **Architecture** sur **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="63d25-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="63d25-112">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="63d25-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="63d25-113">Définissez **Build Type** sur **D3D**.</span><span class="sxs-lookup"><span data-stu-id="63d25-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="63d25-114">Définissez **UWP SDK** sur **Latest installed**.</span><span class="sxs-lookup"><span data-stu-id="63d25-114">Set **UWP SDK** to **Latest installed**</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="63d25-116">Configuration de la gestion des plug-ins XR pour OpenXR</span><span class="sxs-lookup"><span data-stu-id="63d25-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="63d25-117">Pour définir OpenXR comme Runtime dans Unity :</span><span class="sxs-lookup"><span data-stu-id="63d25-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="63d25-118">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**</span><span class="sxs-lookup"><span data-stu-id="63d25-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="63d25-119">Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="63d25-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="63d25-120">Cochez les cases **Initialize XR on Startup** et **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="63d25-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="63d25-121">Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez **ensemble de fonctionnalités Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="63d25-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="63d25-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="63d25-123">Optimization</span></span>

<span data-ttu-id="63d25-124">Si vous développez pour HoloLens 2, accédez à la **réalité mixte> OpenXR > appliquer les paramètres de projet recommandés pour HoloLens 2** afin d’obtenir de meilleures performances d’application.</span><span class="sxs-lookup"><span data-stu-id="63d25-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="63d25-126">Si vous voyez une icône d’avertissement jaune en regard du **plug-in OpenXR**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="63d25-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="63d25-127">L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="63d25-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Capture d’écran de la fenêtre de validation du projet OpenXR](../../images/openxr-img-06.png)

<span data-ttu-id="63d25-129">Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !</span><span class="sxs-lookup"><span data-stu-id="63d25-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="63d25-130">Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.</span><span class="sxs-lookup"><span data-stu-id="63d25-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="63d25-131">Exemples de projets Unity pour OpenXR et HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="63d25-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="63d25-132">Consultez les [exemples de référentiel OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) pour les exemples de projets Unity montrant comment créer des applications Unity pour des casques HoloLens 2 ou de réalité mixte à l’aide du plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="63d25-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="63d25-133">XR Windows</span><span class="sxs-lookup"><span data-stu-id="63d25-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="63d25-134">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="63d25-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="63d25-136">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="63d25-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="63d25-137">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="63d25-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="63d25-138">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="63d25-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="63d25-139">Définissez **Architecture** sur **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="63d25-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="63d25-140">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="63d25-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="63d25-141">Définissez **Build Type** sur **D3D**.</span><span class="sxs-lookup"><span data-stu-id="63d25-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="63d25-142">Définissez **UWP SDK** sur **Latest installed**.</span><span class="sxs-lookup"><span data-stu-id="63d25-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="63d25-143">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="63d25-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

<span data-ttu-id="63d25-145">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :</span><span class="sxs-lookup"><span data-stu-id="63d25-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="63d25-146">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="63d25-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="63d25-147">Sélectionnez **installer la gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="63d25-147">Select **Install XR Plugin Management**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="63d25-149">Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="63d25-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="63d25-151">Développez la section **gestion du plug-in XR** et sélectionnez universels onglet Paramètres de la **plateforme Windows** .</span><span class="sxs-lookup"><span data-stu-id="63d25-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="63d25-152">Si vous utilisez Unity 2020 ou une version ultérieure, vous verrez les options permettant de vérifier **OpenXR** ou **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="63d25-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="63d25-153">Vous pouvez choisir l’un ou l’autre Runtime.</span><span class="sxs-lookup"><span data-stu-id="63d25-153">You can choose either runtime.</span></span>  <span data-ttu-id="63d25-154">Si vous développez spécifiquement pour HoloLens 2 ou la réverbération HP G2 et que vous décidez d’essayer le **OpenXR**, sélectionnez la zone OpenXR et passez en revue notre guide pour [utiliser le plug-in OpenXR de réalité mixte pour Unity](../../openxr-getting-started.md) afin de vous préparer correctement pour ces appareils avant de revenir à ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="63d25-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="63d25-155">À partir de Unity 2020 LTS, Microsoft adopte le développement avec OpenXR.</span><span class="sxs-lookup"><span data-stu-id="63d25-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="63d25-156">À mesure que nous migrons vers ce chemin, dans Unity 2021,1, le plug-in Windows XR sera déconseillé et supprimé dans 2021,2, OpenXR le seul chemin pris en charge.</span><span class="sxs-lookup"><span data-stu-id="63d25-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="63d25-157">Vous trouverez plus d’informations dans [utilisation du plug-in OpenXR de la réalité mixte](../../openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="63d25-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="63d25-158">Si vous décidez de choisir le plug-in **Windows Mixed Reality** , cochez toutes les cases et définissez le **mode d’envoi de profondeur** sur une profondeur de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="63d25-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="63d25-160">XR antérieur</span><span class="sxs-lookup"><span data-stu-id="63d25-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="63d25-161">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="63d25-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](../../images/wmr-config-img-3.png)

<span data-ttu-id="63d25-163">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="63d25-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="63d25-164">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="63d25-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="63d25-165">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="63d25-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="63d25-166">Définissez **Architecture** sur **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="63d25-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="63d25-167">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="63d25-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="63d25-168">Définissez **Build Type** sur **D3D**.</span><span class="sxs-lookup"><span data-stu-id="63d25-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="63d25-169">Définissez **UWP SDK** sur **Latest installed**.</span><span class="sxs-lookup"><span data-stu-id="63d25-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="63d25-170">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="63d25-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](../../images/wmr-config-img-4.png)

<span data-ttu-id="63d25-172">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.</span><span class="sxs-lookup"><span data-stu-id="63d25-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="63d25-173">Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="63d25-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="63d25-174">Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**</span><span class="sxs-lookup"><span data-stu-id="63d25-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="63d25-175">Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle</span><span class="sxs-lookup"><span data-stu-id="63d25-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="63d25-176">Définir le **format de profondeur** sur **16 bits** et activer le partage de **mémoire tampon de profondeur**</span><span class="sxs-lookup"><span data-stu-id="63d25-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="63d25-177">Définir le **mode de rendu stéréo** sur **une seule instance de passage**</span><span class="sxs-lookup"><span data-stu-id="63d25-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="63d25-178">Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="63d25-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](../../images/wmr-config-img-9.png)