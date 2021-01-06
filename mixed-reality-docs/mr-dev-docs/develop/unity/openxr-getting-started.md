---
title: Utilisation du plug-in OpenXR de la réalité mixte pour Unity
description: Découvrez comment activer le plug-in OpenXR de réalité mixte pour les projets Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main
ms.openlocfilehash: 7d28dd50e111da4b010bcae699b7451d967e8f35
ms.sourcegitcommit: 653ddcae6d7a1617c89da1153fa8e7b482ef6818
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97905291"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="7df6d-104">Utilisation du plug-in OpenXR de la réalité mixte pour Unity</span><span class="sxs-lookup"><span data-stu-id="7df6d-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="7df6d-105">À partir de Unity version 2020,2, le package de plug-in OpenXR de réalité mixte de Microsoft est disponible à l’aide du gestionnaire de package Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="7df6d-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7df6d-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="7df6d-106">Prerequisites</span></span>

* <span data-ttu-id="7df6d-107">Unity 2020,2 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="7df6d-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="7df6d-108">Plug-in Unity OpenXR 0.1.1 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="7df6d-108">Unity OpenXR plugin 0.1.1 or later</span></span>
* <span data-ttu-id="7df6d-109">Visual Studio 2019 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="7df6d-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="7df6d-110">Installer la prise en charge de plateforme **UWP** dans Unity pour les applications HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7df6d-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="7df6d-111">Si vous générez des applications VR sur un PC Windows, le plug-in OpenXR de réalité mixte n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7df6d-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="7df6d-112">Toutefois, vous souhaiterez installer le plug-in si vous personnalisez le mappage de contrôleur pour les contrôleurs de reréverbérations de HP ou si vous créez des applications qui fonctionnent à la fois sur les casques HoloLens 2 et VR.</span><span class="sxs-lookup"><span data-stu-id="7df6d-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="7df6d-113">Installation du plug-in OpenXR de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="7df6d-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="7df6d-114">Votre projet doit installer le plug-in **OpenXR** et les packages de gestion du **plug-in XR** avant d’utiliser le plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="7df6d-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="7df6d-115">Si vous les avez déjà installés, c’est génial !</span><span class="sxs-lookup"><span data-stu-id="7df6d-115">If you've already installed them, great!</span></span> <span data-ttu-id="7df6d-116">Si ce n’est pas le cas, l’installation du plug-in OpenXR de la réalité mixte les installe automatiquement en tant que dépendances :</span><span class="sxs-lookup"><span data-stu-id="7df6d-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="7df6d-117">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet > gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="7df6d-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="7df6d-118">Développez la section **registres délimités** , entrez les informations suivantes, puis sélectionnez **Enregistrer**:</span><span class="sxs-lookup"><span data-stu-id="7df6d-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>
    * <span data-ttu-id="7df6d-119">Définir le **nom** sur la **réalité mixte Microsoft**</span><span class="sxs-lookup"><span data-stu-id="7df6d-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="7df6d-120">Définir l' **URL** sur **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="7df6d-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="7df6d-121">Définir la **ou les étendues** sur **com. Microsoft. mixedreality**</span><span class="sxs-lookup"><span data-stu-id="7df6d-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="7df6d-122">Sous **Paramètres avancés**, sélectionnez **activer les packages d’aperçus**</span><span class="sxs-lookup"><span data-stu-id="7df6d-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Capture d’écran de la fenêtre du gestionnaire de package Unity ouverte dans les paramètres du projet](images/openxr-img-01.png)

<span data-ttu-id="7df6d-124">Le gestionnaire de package Unity utilise un fichier manifeste nommé *manifest.js* pour déterminer les packages à installer et les registres à partir desquels ils peuvent être installés.</span><span class="sxs-lookup"><span data-stu-id="7df6d-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7df6d-125">OpenXR est toujours expérimental dans Unity et ce processus peut évoluer au fil du temps, au fur et à mesure que nous travaillons pour optimiser l’expérience du développeur.</span><span class="sxs-lookup"><span data-stu-id="7df6d-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="7df6d-126">Enregistrement de la dépendance de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="7df6d-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="7df6d-127">Une fois que le registre de l’étendue de la réalité mixte Microsoft a été ajouté au manifeste, le package OpenXR peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="7df6d-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="7df6d-128">Pour ajouter le package OpenXR :</span><span class="sxs-lookup"><span data-stu-id="7df6d-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="7df6d-129">Ouvrez **[projectRoot]/Packages/manifest.js** dans un éditeur de texte comme Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="7df6d-129">Open **[projectRoot]/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
    1. <span data-ttu-id="7df6d-130">Pour ce faire, cliquez avec le bouton droit sur **packages** dans le volet gauche de la fenêtre du projet.</span><span class="sxs-lookup"><span data-stu-id="7df6d-130">To get here, right click on **Packages** in the left panel of the Project window.</span></span> <span data-ttu-id="7df6d-131">Ensuite, cliquez sur **afficher dans l’Explorateur**.</span><span class="sxs-lookup"><span data-stu-id="7df6d-131">Then, click **Show in Explorer**.</span></span>
    <span data-ttu-id="7df6d-132">![Capture d’écran de la liste des packages dans la fenêtre projet](images/packages.png)</span><span class="sxs-lookup"><span data-stu-id="7df6d-132">![Screenshot of the packages listing in the Project window](images/packages.png)</span></span>
1. <span data-ttu-id="7df6d-133">Modifiez la section des dépendances du fichier *packages/manifest.js* comme suit :</span><span class="sxs-lookup"><span data-stu-id="7df6d-133">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7df6d-134">Il peut y avoir plus de dépendances dans votre fichier manifeste que ce qui est indiqué ici.</span><span class="sxs-lookup"><span data-stu-id="7df6d-134">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="7df6d-135">Ne les supprimez pas, ajoutez simplement la dépendance OpenXR à la liste.</span><span class="sxs-lookup"><span data-stu-id="7df6d-135">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. <span data-ttu-id="7df6d-136">Enregistrez le fichier, revenez à l’éditeur Unity et ouvrez le **Gestionnaire de package** pour confirmer que le plug-in est installé :</span><span class="sxs-lookup"><span data-stu-id="7df6d-136">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span>

    ![Capture d’écran du gestionnaire de package Unity ouverte dans l’éditeur Unity avec le plug-in OpenXR de réalité mixte mis en surbrillance](images/openxr-img-03.png)

    > [!Note]
    > <span data-ttu-id="7df6d-138">Si le package OpenXR est supprimé à l’aide du gestionnaire de package Unity, vous devez le rajouter à l’aide des étapes décrites précédemment.</span><span class="sxs-lookup"><span data-stu-id="7df6d-138">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="7df6d-139">Configuration de la gestion des plug-ins XR pour OpenXR</span><span class="sxs-lookup"><span data-stu-id="7df6d-139">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="7df6d-140">Pour définir OpenXR comme Runtime dans Unity :</span><span class="sxs-lookup"><span data-stu-id="7df6d-140">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="7df6d-141">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet**</span><span class="sxs-lookup"><span data-stu-id="7df6d-141">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="7df6d-142">Dans la liste des paramètres, sélectionnez **gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="7df6d-142">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="7df6d-143">Cochez les cases **Initialize XR on Startup** et **OpenXR (Preview)**</span><span class="sxs-lookup"><span data-stu-id="7df6d-143">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="7df6d-144">Si vous ciblez HoloLens 2, assurez-vous que vous êtes sur la plateforme UWP et sélectionnez **ensemble de fonctionnalités Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="7df6d-144">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="7df6d-146">Si une icône d’avertissement rouge s’affiche en regard du **plug-in OpenXR (version préliminaire)**, cliquez sur l’icône et sélectionnez **corriger tout** avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="7df6d-146">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="7df6d-147">L’éditeur Unity peut avoir besoin de redémarrer lui-même pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="7df6d-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Capture d’écran de la fenêtre de validation du projet OpenXR](images/openxr-img-06.png)

<span data-ttu-id="7df6d-149">Vous êtes maintenant prêt à commencer à développer avec OpenXR dans Unity !</span><span class="sxs-lookup"><span data-stu-id="7df6d-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="7df6d-150">Passez à la section suivante pour savoir comment utiliser les exemples OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7df6d-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="7df6d-151">Optimization</span><span class="sxs-lookup"><span data-stu-id="7df6d-151">Optimization</span></span>

<span data-ttu-id="7df6d-152">Si vous développez pour HoloLens 2, accédez à la **réalité mixte> OpenXR > appliquer les paramètres de projet recommandés pour HoloLens 2** afin d’obtenir de meilleures performances d’application.</span><span class="sxs-lookup"><span data-stu-id="7df6d-152">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Capture d’écran de l’élément de menu de réalité mixte ouvert avec OpenXR sélectionné](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="7df6d-154">Essayer les scènes de l’exemple Unity</span><span class="sxs-lookup"><span data-stu-id="7df6d-154">Try out the Unity sample scenes</span></span>

<span data-ttu-id="7df6d-155">Pour utiliser un ou plusieurs des exemples, installez [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) à partir du **Gestionnaire de package**:</span><span class="sxs-lookup"><span data-stu-id="7df6d-155">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Capture d’écran du gestionnaire de package Unity ouverte dans l’éditeur Unity avec AR Foundation en surbrillance](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="7df6d-157">Exemples HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7df6d-157">HoloLens 2 samples</span></span>

1. <span data-ttu-id="7df6d-158">Dans l’éditeur Unity, accédez à **fenêtre > gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="7df6d-158">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="7df6d-159">Dans la liste des packages, sélectionnez le **plug-in OpenXR de réalité mixte**</span><span class="sxs-lookup"><span data-stu-id="7df6d-159">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="7df6d-160">Recherchez l’exemple dans la liste d' **exemples** et sélectionnez **Importer**</span><span class="sxs-lookup"><span data-stu-id="7df6d-160">Locate the sample in the **Samples** list and select **Import**</span></span>

![Capture d’écran du gestionnaire de package Unity ouverte dans l’éditeur Unity avec le plug-in OpenXR de réalité mixte sélectionné et le bouton d’importation en surbrillance](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="7df6d-162">Lorsqu’un package est mis à jour, Unity offre la possibilité de mettre à jour les exemples importés.</span><span class="sxs-lookup"><span data-stu-id="7df6d-162">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="7df6d-163">La mise à jour d’un échantillon importé remplace toutes les modifications apportées à l’exemple et aux ressources associées.</span><span class="sxs-lookup"><span data-stu-id="7df6d-163">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7df6d-164">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7df6d-164">Next steps</span></span>

<span data-ttu-id="7df6d-165">Maintenant que votre projet est configuré pour OpenXR et que vous avez accès à des exemples, consultez les [fonctionnalités](openxr-supported-features.md) actuellement prises en charge dans notre plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7df6d-165">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="7df6d-166">Vous avez des commentaires ?</span><span class="sxs-lookup"><span data-stu-id="7df6d-166">Have Feedback?</span></span>

<span data-ttu-id="7df6d-167">OpenXR est toujours expérimental. nous apprécions donc des commentaires que vous pouvez nous aider à améliorer.</span><span class="sxs-lookup"><span data-stu-id="7df6d-167">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="7df6d-168">Vous les trouverez sur les [Forums Unity](https://aka.ms/unityforums) en marquant votre billet de forum avec **Microsoft**  +  **OpenXR** et **HoloLens 2** ou **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="7df6d-168">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7df6d-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7df6d-169">See also</span></span>

* [<span data-ttu-id="7df6d-170">Configuration de votre projet sans MRTK</span><span class="sxs-lookup"><span data-stu-id="7df6d-170">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="7df6d-171">Paramètres recommandés pour Unity</span><span class="sxs-lookup"><span data-stu-id="7df6d-171">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="7df6d-172">Recommandations de performances pour Unity</span><span class="sxs-lookup"><span data-stu-id="7df6d-172">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
