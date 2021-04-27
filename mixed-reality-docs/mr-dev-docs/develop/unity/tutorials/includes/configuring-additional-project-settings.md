---
ms.openlocfilehash: d8d46da1a1a095074f059b53ebd997e1b6f89961
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984428"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="a7f77-101">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="a7f77-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="a7f77-102">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="a7f77-102">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity - Project Settings... Chemin du menu](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="a7f77-104">Dans la fenêtre Project Settings, sélectionnez **XR Plug-in Managemen** > **Install XR Plug-in Management** pour installer XR Plug-in Management :</span><span class="sxs-lookup"><span data-stu-id="a7f77-104">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Paramètres XR d’Unity](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="a7f77-106">quand Unity a terminé l’installation de XR Plug-in Management.</span><span class="sxs-lookup"><span data-stu-id="a7f77-106">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="a7f77-107">Vérifiez que vous êtes dans les paramètres Universal Windows Platform, puis cochez les cases **Initialize XR on Startup** et **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="a7f77-107">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup** and **Windows Mixed Reality** checkbox.</span></span>

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality](../images/mr-learning-base/base-02-section5-step2-2-1.png)

<span data-ttu-id="a7f77-109">Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître.</span><span class="sxs-lookup"><span data-stu-id="a7f77-109">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="a7f77-110">Si ce n’est pas le cas, utilisez le menu Unity pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="a7f77-110">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="a7f77-111">Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :</span><span class="sxs-lookup"><span data-stu-id="a7f77-111">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Paramètres XR d’Unity avec l’option SDK Windows Mixed Reality sélectionnée](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="a7f77-113">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="a7f77-113">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="a7f77-114">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="a7f77-114">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="a7f77-115">Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.</span><span class="sxs-lookup"><span data-stu-id="a7f77-115">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="a7f77-116">Dans la fenêtre Project, sélectionnez **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, puis utilisez la liste déroulante **Depth Buffer Format** pour sélectionner **16-bit depth** :</span><span class="sxs-lookup"><span data-stu-id="a7f77-116">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth:**</span></span>

![Fenêtre Publishing Settings d’Unity avec le nom du package mis en évidence](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> <span data-ttu-id="a7f77-118">La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="a7f77-118">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="a7f77-119">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> de la documentation sur les <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">performances</a> de MRTK.</span><span class="sxs-lookup"><span data-stu-id="a7f77-119">To learn more about this topic, you can refer to the   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="a7f77-120">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="a7f77-120">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Fenêtre Publishing Settings d’Unity avec le nom du package](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="a7f77-122">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7f77-122">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="a7f77-123">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="a7f77-123">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="a7f77-124">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a7f77-124">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="a7f77-125">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="a7f77-125">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="a7f77-126">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="a7f77-126">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="a7f77-127">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="a7f77-127">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity - Project Settings... Chemin du menu](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="a7f77-129">Dans la fenêtre Project Settings, sélectionnez **XR Plug-in Managemen** > **Install XR Plug-in Management** pour installer XR Plug-in Management :</span><span class="sxs-lookup"><span data-stu-id="a7f77-129">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Paramètres XR d’Unity avec l’option Install XR Plug-in Management sélectionnée](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="a7f77-131">quand Unity a terminé l’installation de XR Plug-in Management.</span><span class="sxs-lookup"><span data-stu-id="a7f77-131">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="a7f77-132">Vérifiez que vous êtes dans les paramètres Universal Windows Platform, puis cochez les cases **Initialize XR on Startup**, **OpenXR** et **Microsoft HoloLens feature set**.</span><span class="sxs-lookup"><span data-stu-id="a7f77-132">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup**, **OpenXR** and **Microsoft HoloLens feature set** checkboxes.</span></span>

![Paramètres XR d’Unity avec les options OpenXR et Microsoft HoloLens feature set sélectionnées](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

>[!Important]
><span data-ttu-id="a7f77-134">Si une icône d’avertissement rouge apparaît à côté d’OpenXR Plugin (Preview), cliquez dessus et sélectionnez Fix all avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a7f77-134">If you see a red warning icon next to OpenXR Plugin (Preview), click the icon and select Fix all before continuing.</span></span> <span data-ttu-id="a7f77-135">L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="a7f77-135">The Unity Editor may need to restart itself for the changes to take effect.</span></span>
><span data-ttu-id="a7f77-136">![Menu de validation du projet OpenXR avec tous les problèmes à corriger sélectionnés.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span><span class="sxs-lookup"><span data-stu-id="a7f77-136">![OpenXR project validation menu with all issues selected to be fixed.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span></span>

<span data-ttu-id="a7f77-137">Dans la barre de menus en haut de l’écran, accédez à **Mixed Reality > OpenXR > Apply recommended project settings for HoloLens 2** pour optimiser les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7f77-137">In the menu bar at the top of the screen, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Menu Mixed Reality avec les options OpenXR et Apply recommended project settings for HoloLens 2 sélectionnées](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

<span data-ttu-id="a7f77-139">Une fois qu’Unity a fini d’importer les fichiers nécessaires, la fenêtre MRTK Project Configurator doit réapparaître.</span><span class="sxs-lookup"><span data-stu-id="a7f77-139">After Unity has finished importing necessary files, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="a7f77-140">Si ce n’est pas le cas, utilisez le menu Unity pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="a7f77-140">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="a7f77-141">Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :</span><span class="sxs-lookup"><span data-stu-id="a7f77-141">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Fenêtre de configuration de MRTK avec les options par défaut sélectionnées](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="a7f77-143">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="a7f77-143">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="a7f77-144">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="a7f77-144">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="a7f77-145">Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.</span><span class="sxs-lookup"><span data-stu-id="a7f77-145">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>


<span data-ttu-id="a7f77-146">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="a7f77-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Paramètres de publication Unity](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="a7f77-148">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7f77-148">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="a7f77-149">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="a7f77-149">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="a7f77-150">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a7f77-150">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="a7f77-151">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="a7f77-151">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="a7f77-152">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="a7f77-152">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="a7f77-153">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="a7f77-153">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="a7f77-154">Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, cochez la case **Virtual Reality Supported**, cliquez sur l’icône **+** et sélectionnez Windows Mixed Reality pour ajouter le SDK Windows Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="a7f77-154">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](../images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="a7f77-156">Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître.</span><span class="sxs-lookup"><span data-stu-id="a7f77-156">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="a7f77-157">Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement dans le menu Unity en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**.</span><span class="sxs-lookup"><span data-stu-id="a7f77-157">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="a7f77-158">Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :</span><span class="sxs-lookup"><span data-stu-id="a7f77-158">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Fenêtre de configuration de MRTK](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="a7f77-160">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="a7f77-160">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="a7f77-161">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="a7f77-161">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="a7f77-162">Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.</span><span class="sxs-lookup"><span data-stu-id="a7f77-162">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="a7f77-163">Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, puis utilisez la liste déroulante **Depth Format** pour sélectionner **16-bit depth** :</span><span class="sxs-lookup"><span data-stu-id="a7f77-163">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity - 16 Depth activé](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="a7f77-165">La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="a7f77-165">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="a7f77-166">Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.</span><span class="sxs-lookup"><span data-stu-id="a7f77-166">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="a7f77-167">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="a7f77-167">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Paramètres de publication Unity.](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="a7f77-170">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7f77-170">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="a7f77-171">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="a7f77-171">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="a7f77-172">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a7f77-172">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="a7f77-173">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="a7f77-173">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
