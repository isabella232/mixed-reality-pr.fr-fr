---
title: Utilisation du plug-in OpenXR de la réalité mixte pour Unity
description: Découvrez comment activer le plug-in OpenXR de réalité mixte pour les projets Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main
ms.openlocfilehash: a4606eeb1fa6c8dc0858653a196c1e536ae473d4
ms.sourcegitcommit: e2228b9585302eeff1d853ddb54be8421a21c954
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102189121"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="85519-104">Utilisation du plug-in OpenXR de la réalité mixte pour Unity</span><span class="sxs-lookup"><span data-stu-id="85519-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="85519-105">À partir de Unity version 2020,2, le package de plug-in OpenXR de réalité mixte de Microsoft est disponible à l’aide du gestionnaire de package Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="85519-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85519-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="85519-106">Prerequisites</span></span>

* <span data-ttu-id="85519-107">Unity 2020,2 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="85519-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="85519-108">Plug-in Unity OpenXR 0.1.3 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="85519-108">Unity OpenXR plugin 0.1.3 or later</span></span>
* <span data-ttu-id="85519-109">Visual Studio 2019 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="85519-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="85519-110">Installer la prise en charge de plateforme **UWP** dans Unity pour les applications HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="85519-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="85519-111">Si vous générez des applications VR sur un PC Windows, le plug-in OpenXR de réalité mixte n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="85519-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="85519-112">Toutefois, vous souhaiterez installer le plug-in si vous personnalisez le mappage de contrôleur pour les contrôleurs de reréverbérations de HP ou si vous créez des applications qui fonctionnent à la fois sur les casques HoloLens 2 et VR.</span><span class="sxs-lookup"><span data-stu-id="85519-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="85519-113">Installation de OpenXR avec l’outil de la fonctionnalité de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="85519-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="85519-114">Installez le plug-in OpenXR avec la nouvelle application outil de la fonctionnalité de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="85519-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="85519-115">Suivez les [instructions d’installation et d’utilisation](welcome-to-mr-feature-tool.md) , puis sélectionnez le package de **plug-in OpenXR de la réalité mixte** dans la catégorie de la réalité mixte Toolkit :</span><span class="sxs-lookup"><span data-stu-id="85519-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Fenêtre packages de l’outil de réalité mixte avec plug-in Open XR mis en surbrillance](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="85519-117">Configuration de la gestion des plug-ins XR pour OpenXR</span><span class="sxs-lookup"><span data-stu-id="85519-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="85519-118">Pour définir OpenXR comme Runtime dans Unity :</span><span class="sxs-lookup"><span data-stu-id="85519-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="85519-119">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**</span><span class="sxs-lookup"><span data-stu-id="85519-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="85519-120">Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="85519-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="85519-121">Cochez les cases **Initialize XR on Startup** et **OpenXR (Preview)**</span><span class="sxs-lookup"><span data-stu-id="85519-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="85519-122">Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez **ensemble de fonctionnalités Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="85519-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="85519-124">Si une icône d’avertissement rouge s’affiche en regard du **plug-in OpenXR (version préliminaire)**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="85519-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="85519-125">L’éditeur Unity peut avoir besoin de redémarrer lui-même pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="85519-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Capture d’écran de la fenêtre de validation du projet OpenXR](images/openxr-img-06.png)

<span data-ttu-id="85519-127">Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !</span><span class="sxs-lookup"><span data-stu-id="85519-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="85519-128">Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.</span><span class="sxs-lookup"><span data-stu-id="85519-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="85519-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="85519-129">Optimization</span></span>

<span data-ttu-id="85519-130">Si vous développez pour HoloLens 2, accédez à la **réalité mixte> OpenXR > appliquer les paramètres de projet recommandés pour HoloLens 2** afin d’obtenir de meilleures performances d’application.</span><span class="sxs-lookup"><span data-stu-id="85519-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="85519-132">Essayer les scènes de l’exemple Unity</span><span class="sxs-lookup"><span data-stu-id="85519-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="85519-133">Pour utiliser un ou plusieurs des exemples, installez [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) à partir du **Gestionnaire de package**:</span><span class="sxs-lookup"><span data-stu-id="85519-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Capture d’écran du gestionnaire de package Unity ouverte dans l’éditeur Unity avec AR Foundation en surbrillance](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="85519-135">Exemples HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="85519-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="85519-136">Dans l’éditeur Unity, accédez à **fenêtre > gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="85519-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="85519-137">Dans la liste des packages, sélectionnez le **plug-in OpenXR de réalité mixte**</span><span class="sxs-lookup"><span data-stu-id="85519-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="85519-138">Recherchez l’exemple dans la liste d' **exemples** et sélectionnez **Importer**</span><span class="sxs-lookup"><span data-stu-id="85519-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Capture d’écran du gestionnaire de package Unity ouverte dans l’éditeur Unity avec le plug-in OpenXR de réalité mixte sélectionné et le bouton d’importation en surbrillance](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="85519-140">Lorsqu’un package est mis à jour, Unity offre la possibilité de mettre à jour les exemples importés.</span><span class="sxs-lookup"><span data-stu-id="85519-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="85519-141">La mise à jour d’un échantillon importé remplace toutes les modifications apportées à l’exemple et aux ressources associées.</span><span class="sxs-lookup"><span data-stu-id="85519-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="85519-142">Utilisation de MRTK avec prise en charge de OpenXR</span><span class="sxs-lookup"><span data-stu-id="85519-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="85519-143">MRTK-Unity prend en charge le plug-in OpenXR de réalité mixte à partir de la version 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="85519-143">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="85519-144">Ouvrez de nouveau l' [outil Mixed Reality Feature](welcome-to-mr-feature-tool.md) pour installer la boîte à outils de la réalité mixte, si ce n’est déjà fait.</span><span class="sxs-lookup"><span data-stu-id="85519-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="85519-145">La prise en charge de OpenXR est dans le package de **base** .</span><span class="sxs-lookup"><span data-stu-id="85519-145">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="85519-146">Accédez au script du composant MixedReality Toolkit dans l’inspecteur et basculez vers le profil **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="85519-146">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Capture d’écran de basculement de la configuration MRTK dans le composant de la réalité mixte du composant dans l’inspecteur](images/openxr-img-11.png)

    1. <span data-ttu-id="85519-148">Pour [plus d’informations sur la migration vers OpenXR](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline), consultez la documentation MRTK.</span><span class="sxs-lookup"><span data-stu-id="85519-148">See the MRTK documentation for [more in-depth information on migrating to OpenXR](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="85519-149">Lorsque vous effectuez une mise à niveau à partir d’une version antérieure de MRTK, vérifiez que la ligne suivante se trouve dans le fichier **Assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="85519-149">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="85519-150">Cette ligne sera ajoutée par défaut si vous avez démarré avec MRTK 2.5.4 ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="85519-150">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="85519-151">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="85519-151">Next steps</span></span>

<span data-ttu-id="85519-152">Maintenant que votre projet est configuré pour OpenXR et que vous avez accès à des exemples, consultez les [fonctionnalités](openxr-supported-features.md) actuellement prises en charge dans notre plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="85519-152">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="85519-153">Vous avez des commentaires ?</span><span class="sxs-lookup"><span data-stu-id="85519-153">Have Feedback?</span></span>

<span data-ttu-id="85519-154">OpenXR est toujours expérimental. nous apprécions donc des commentaires que vous pouvez nous aider à améliorer.</span><span class="sxs-lookup"><span data-stu-id="85519-154">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="85519-155">Vous les trouverez sur les [Forums Unity](https://aka.ms/unityforums) en marquant votre billet de forum avec **Microsoft**  +  **OpenXR** et **HoloLens 2** ou **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="85519-155">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="85519-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85519-156">See also</span></span>

* [<span data-ttu-id="85519-157">Configuration de votre projet sans MRTK</span><span class="sxs-lookup"><span data-stu-id="85519-157">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="85519-158">Paramètres recommandés pour Unity</span><span class="sxs-lookup"><span data-stu-id="85519-158">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="85519-159">Recommandations de performances pour Unity</span><span class="sxs-lookup"><span data-stu-id="85519-159">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
