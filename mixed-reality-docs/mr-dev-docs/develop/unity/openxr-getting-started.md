---
title: Utilisation du plug-in OpenXR Mixed Reality
description: Découvrez comment activer le plug-in OpenXR de réalité mixte pour les projets Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main
ms.openlocfilehash: ffec0cbe2ea9fd87cbb5f38010dad2d64e2e82ee
ms.sourcegitcommit: adbe3baa6b1c284ed1c4fd796d8b5612c3ca3f42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112270434"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="ddc81-104">Utilisation du plug-in OpenXR Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ddc81-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="ddc81-105">Pour les développeurs ciblant Unity 2020 pour générer des applications HoloLens 2 ou de réalité mixte, le plug-in OpenXR peut être utilisé à la place du plug-in WindowsXR pour de meilleures compatibilités entre les plateformes.</span><span class="sxs-lookup"><span data-stu-id="ddc81-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="ddc81-106">Le plug-in OpenXR de réalité mixte fonctionne également bien avec le dernier outil de la [réalité mixte](welcome-to-mr-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ddc81-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ddc81-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ddc81-107">Prerequisites</span></span>

* <span data-ttu-id="ddc81-108">Le dernier LTS Unity 2020,3, recommander 2020.3.6 F1 ou supérieur.</span><span class="sxs-lookup"><span data-stu-id="ddc81-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="ddc81-109">Dernier plug-in OpenXR Unity, recommander 1,2 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="ddc81-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="ddc81-110">[Outils les plus récents pour le développement HoloLens 2](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="ddc81-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="ddc81-111">Dernière version de MRTK (facultatif), recommander la version 2,6 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="ddc81-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="ddc81-112">Dernier plug-in OpenXR de réalité mixte, recommander la version 0.9.5 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="ddc81-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="ddc81-113">Si vous générez des applications VR sur un PC Windows, le plug-in OpenXR de réalité mixte n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ddc81-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ddc81-114">Toutefois, vous souhaiterez installer le plug-in si vous personnalisez le mappage de contrôleur pour les contrôleurs de reréverbérations de HP ou si vous créez des applications qui fonctionnent à la fois sur les casques HoloLens 2 et VR.</span><span class="sxs-lookup"><span data-stu-id="ddc81-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="ddc81-115">Configuration de votre projet avec MRTK</span><span class="sxs-lookup"><span data-stu-id="ddc81-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="ddc81-116">MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales.</span><span class="sxs-lookup"><span data-stu-id="ddc81-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="ddc81-117">MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.</span><span class="sxs-lookup"><span data-stu-id="ddc81-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="ddc81-118">Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ddc81-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ddc81-119">Configurer votre projet à l’aide de MRTK</span><span class="sxs-lookup"><span data-stu-id="ddc81-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="ddc81-120">Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="ddc81-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="ddc81-121">Configuration manuelle sans MRTK</span><span class="sxs-lookup"><span data-stu-id="ddc81-121">Manual setup without MRTK</span></span>

<span data-ttu-id="ddc81-122">Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ddc81-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="ddc81-123">Suivez les [instructions d’installation et d’utilisation](welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de la réalité mixte** dans la catégorie de la réalité mixte Toolkit :</span><span class="sxs-lookup"><span data-stu-id="ddc81-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="ddc81-125">Définition de votre cible de génération</span><span class="sxs-lookup"><span data-stu-id="ddc81-125">Setting your build target</span></span>

<span data-ttu-id="ddc81-126">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="ddc81-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](images/wmr-config-img-3.png)

<span data-ttu-id="ddc81-128">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="ddc81-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="ddc81-129">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="ddc81-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="ddc81-130">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="ddc81-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="ddc81-131">Définissez **Architecture** sur **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="ddc81-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="ddc81-132">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="ddc81-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="ddc81-133">Définissez **Build Type** sur **D3D**.</span><span class="sxs-lookup"><span data-stu-id="ddc81-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="ddc81-134">Définissez **UWP SDK** sur **Latest installed**.</span><span class="sxs-lookup"><span data-stu-id="ddc81-134">Set **UWP SDK** to **Latest installed**</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="ddc81-136">Configuration de la gestion des plug-ins XR pour OpenXR</span><span class="sxs-lookup"><span data-stu-id="ddc81-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="ddc81-137">Pour définir OpenXR comme Runtime dans Unity :</span><span class="sxs-lookup"><span data-stu-id="ddc81-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="ddc81-138">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**</span><span class="sxs-lookup"><span data-stu-id="ddc81-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="ddc81-139">Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="ddc81-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="ddc81-140">Cochez les cases **Initialize XR on Startup** et **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="ddc81-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="ddc81-141">Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez **ensemble de fonctionnalités Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="ddc81-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="ddc81-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="ddc81-143">Optimization</span></span>

<span data-ttu-id="ddc81-144">Si vous développez pour HoloLens 2, accédez à la **réalité mixte> OpenXR > appliquer les paramètres de projet recommandés pour HoloLens 2** afin d’obtenir de meilleures performances d’application.</span><span class="sxs-lookup"><span data-stu-id="ddc81-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="ddc81-146">Si une icône d’avertissement rouge s’affiche en regard du **plug-in OpenXR**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ddc81-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="ddc81-147">L’éditeur Unity devra peut-être redémarrer pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="ddc81-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Capture d’écran de la fenêtre de validation du projet OpenXR](images/openxr-img-06.png)

<span data-ttu-id="ddc81-149">Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !</span><span class="sxs-lookup"><span data-stu-id="ddc81-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="ddc81-150">Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ddc81-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="ddc81-151">Exemples de projets Unity pour OpenXR et HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ddc81-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="ddc81-152">Consultez les [exemples de référentiel OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) pour les exemples de projets Unity montrant comment créer des applications Unity pour des casques HoloLens 2 ou de réalité mixte à l’aide du plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ddc81-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="ddc81-153">Utilisation de MRTK avec prise en charge de OpenXR</span><span class="sxs-lookup"><span data-stu-id="ddc81-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="ddc81-154">MRTK-Unity prend en charge le plug-in OpenXR de réalité mixte à partir de la version 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="ddc81-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="ddc81-155">Ouvrez de nouveau l' [outil Mixed Reality Feature](welcome-to-mr-feature-tool.md) pour installer la boîte à outils de la réalité mixte, si ce n’est déjà fait.</span><span class="sxs-lookup"><span data-stu-id="ddc81-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="ddc81-156">La prise en charge de OpenXR est dans le package de **base** .</span><span class="sxs-lookup"><span data-stu-id="ddc81-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="ddc81-157">Accédez au script du composant MixedReality Toolkit dans l’inspecteur et basculez vers le profil **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="ddc81-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Capture d’écran de basculement de la configuration MRTK dans le composant de la réalité mixte du composant dans l’inspecteur](images/openxr-img-11.png)

    1. <span data-ttu-id="ddc81-159">Pour [plus d’informations sur la migration vers OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline), consultez la documentation MRTK.</span><span class="sxs-lookup"><span data-stu-id="ddc81-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="ddc81-160">Lorsque vous effectuez une mise à niveau à partir d’une version antérieure de MRTK, vérifiez que la ligne suivante se trouve dans le fichier **Assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="ddc81-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ddc81-161">Cette ligne sera ajoutée par défaut si vous avez démarré avec MRTK 2.5.4 ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="ddc81-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ddc81-162">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ddc81-162">Next steps</span></span>

<span data-ttu-id="ddc81-163">Maintenant que votre projet est configuré pour OpenXR et que vous avez accès à des exemples, consultez les [fonctionnalités](openxr-supported-features.md) actuellement prises en charge dans notre plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ddc81-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="ddc81-164">Vous avez des commentaires ?</span><span class="sxs-lookup"><span data-stu-id="ddc81-164">Have Feedback?</span></span>

<span data-ttu-id="ddc81-165">OpenXR est toujours expérimental. nous apprécions donc des commentaires que vous pouvez nous aider à améliorer.</span><span class="sxs-lookup"><span data-stu-id="ddc81-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="ddc81-166">Vous les trouverez sur les [Forums Unity](https://aka.ms/unityforums) en marquant votre billet de forum avec **Microsoft**  +  **OpenXR** et **HoloLens 2** ou **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="ddc81-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddc81-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddc81-167">See also</span></span>

* [<span data-ttu-id="ddc81-168">Configuration de votre projet sans MRTK</span><span class="sxs-lookup"><span data-stu-id="ddc81-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="ddc81-169">Paramètres recommandés pour Unity</span><span class="sxs-lookup"><span data-stu-id="ddc81-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ddc81-170">Recommandations de performances pour Unity</span><span class="sxs-lookup"><span data-stu-id="ddc81-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)