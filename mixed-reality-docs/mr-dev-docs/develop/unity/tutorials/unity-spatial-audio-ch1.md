---
title: Ajout de données audio spatiales à votre projet
description: Ajoutez le plug-in Microsoft Spatializer à votre projet Unity pour accéder au déchargement matériel HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007469"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="f2414-104">Ajout de données audio spatiales à votre projet Unity</span><span class="sxs-lookup"><span data-stu-id="f2414-104">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="f2414-105">Bienvenue dans le didacticiel sur l’audio spatial pour Unity sur HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="f2414-105">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="f2414-106">Cette séquence de didacticiel présente les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f2414-106">This tutorial sequence shows:</span></span>
* <span data-ttu-id="f2414-107">Comment utiliser le déchargement de la fonction de transfert HRTF sur HoloLens 2 dans Unity</span><span class="sxs-lookup"><span data-stu-id="f2414-107">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="f2414-108">Comment activer le réverbe lors de l’utilisation du déchargement HRTF</span><span class="sxs-lookup"><span data-stu-id="f2414-108">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="f2414-109">Le [dépôt github Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) a un projet Unity terminé de cette séquence de didacticiels.</span><span class="sxs-lookup"><span data-stu-id="f2414-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="f2414-110">Pour savoir à quoi cela sert à spatialiser des sons à l’aide des technologies Spatialization basées sur HRTF et des recommandations pour savoir quand cela peut être utile, consultez [conception de son spatial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="f2414-110">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="f2414-111">Qu’est-ce que le déchargement HRTF ?</span><span class="sxs-lookup"><span data-stu-id="f2414-111">What is HRTF offload?</span></span>

<span data-ttu-id="f2414-112">Le traitement de l’audio à l’aide d’algorithmes basés sur HRTF nécessite une grande quantité de calcul spécialisé.</span><span class="sxs-lookup"><span data-stu-id="f2414-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="f2414-113">HoloLens 2 comprend un matériel dédié qui peut être utilisé pour éviter la charge du processeur d’application, ce qui « décharge » le traitement des algorithmes basés sur HRTF.</span><span class="sxs-lookup"><span data-stu-id="f2414-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="f2414-114">Le plug-in Microsoft Spatializer offre un moyen simple pour votre application de tirer parti du matériel HRTF dédié afin que votre application puisse utiliser davantage de processeurs d’applications pour les opérations autres que l’audio spatial.</span><span class="sxs-lookup"><span data-stu-id="f2414-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="f2414-115">Objectifs</span><span class="sxs-lookup"><span data-stu-id="f2414-115">Objectives</span></span>

<span data-ttu-id="f2414-116">Dans ce premier chapitre, vous allez :</span><span class="sxs-lookup"><span data-stu-id="f2414-116">In this first chapter, you'll:</span></span>
* <span data-ttu-id="f2414-117">Créer un projet Unity et importer MRTK</span><span class="sxs-lookup"><span data-stu-id="f2414-117">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="f2414-118">Importer le plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="f2414-118">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="f2414-119">Activer le plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="f2414-119">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="f2414-120">Activer l’audio spatial sur votre station de travail de développeur</span><span class="sxs-lookup"><span data-stu-id="f2414-120">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="f2414-121">Créer un projet et ajouter NuGet pour Unity</span><span class="sxs-lookup"><span data-stu-id="f2414-121">Create a project and add NuGet for Unity</span></span>

<span data-ttu-id="f2414-122">Commencez avec un projet Unity vide, puis ajoutez et configurez NuGet pour Unity :</span><span class="sxs-lookup"><span data-stu-id="f2414-122">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="f2414-123">Téléchargez la dernière version de [NuGetForUnity. pour Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="f2414-123">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="f2414-124">Dans la barre de menus Unity, cliquez sur **ressources-> importer un package-> package personnalisé...** et installer le package NuGetForUnity :</span><span class="sxs-lookup"><span data-stu-id="f2414-124">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importer un package personnalisé](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="f2414-126">Ajouter le package Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f2414-126">Add the Windows Mixed Reality package</span></span>

<span data-ttu-id="f2414-127">La prise en charge de Windows Mixed Reality dans Unity 2019 et versions ultérieures est contenue dans un package facultatif.</span><span class="sxs-lookup"><span data-stu-id="f2414-127">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="f2414-128">Pour l’ajouter à votre projet, ouvrez la **fenêtre > gestionnaire de package** à partir de la barre de menus Unity :</span><span class="sxs-lookup"><span data-stu-id="f2414-128">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menu du gestionnaire de package](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="f2414-130">Recherchez et installez le package **Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="f2414-130">Then find and install the **Windows Mixed Reality** package:</span></span>

![Fenêtre du gestionnaire de package](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="f2414-132">Installer MRTK et Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="f2414-132">Install MRTK and Microsoft Spatializer</span></span>

<span data-ttu-id="f2414-133">À l’aide de NuGet pour Unity, installez les plug-ins MRTK et Microsoft Spatializer :</span><span class="sxs-lookup"><span data-stu-id="f2414-133">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="f2414-134">Dans la barre de menus de Unity, cliquez sur **NuGet-> gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f2414-134">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Gérer des packages NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="f2414-136">Dans la zone de **recherche** , entrez « Microsoft. MixedReality. Toolkit » et installez le package MRTK Core : **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="f2414-136">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Package NuGet MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="f2414-138">Le [package NuGet MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) contient un contexte et des détails supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f2414-138">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="f2414-139">Dans la zone de **recherche** , entrez « Microsoft. SpatialAudio » et installez le package Microsoft Spatializer : **Microsoft. SpatialAudio. Spatializer. Unity**</span><span class="sxs-lookup"><span data-stu-id="f2414-139">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Plug-in Spatializer NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="f2414-141">Configurer MRTK dans votre projet</span><span class="sxs-lookup"><span data-stu-id="f2414-141">Set up MRTK in your project</span></span>

1. <span data-ttu-id="f2414-142">Ouvrez la fenêtre Paramètres de build en accédant à **fichiers-> paramètres de build**.</span><span class="sxs-lookup"><span data-stu-id="f2414-142">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="f2414-143">Sélectionnez le _plateforme Windows universelle_ , puis cliquez sur **basculer la plateforme**.</span><span class="sxs-lookup"><span data-stu-id="f2414-143">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="f2414-144">Cliquez sur **paramètres du lecteur** dans la **fenêtre générer** pour ouvrir les propriétés des **paramètres du lecteur** dans le volet **inspecteur** .</span><span class="sxs-lookup"><span data-stu-id="f2414-144">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="f2414-145">Sous **paramètres de XR**, activez la case à cocher **réalité virtuelle prise en charge**</span><span class="sxs-lookup"><span data-stu-id="f2414-145">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="f2414-146">Sous **paramètres XR**, définissez le **mode de rendu stéréo** sur **Single-instanced**.</span><span class="sxs-lookup"><span data-stu-id="f2414-146">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="f2414-147">Sous **paramètres de publication**, activez la case à cocher **perception spatiale** dans la section **fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="f2414-147">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="f2414-148">Dans la barre de menus, cliquez sur **Kit de pratiques de réalité mixte-> ajouter à la scène et configurer.**</span><span class="sxs-lookup"><span data-stu-id="f2414-148">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="f2414-149">pour ajouter MRTK à votre scène.</span><span class="sxs-lookup"><span data-stu-id="f2414-149">to add MRTK to your scene.</span></span>

<span data-ttu-id="f2414-150">Pour obtenir des conseils supplémentaires, notamment la façon de créer votre application et de la déployer sur un HoloLens 2, consultez [le chapitre 1 du module de base de l’apprentissage de RM](../../../mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="f2414-150">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="f2414-151">Activer le plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="f2414-151">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="f2414-152">Activez le plug-in **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="f2414-152">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="f2414-153">Ouvrez les **paramètres de projet Edit->-> audio**, puis remplacez le **plug-in Spatializer** par "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="f2414-153">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="f2414-154">La section **audio** des **paramètres du projet** doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="f2414-154">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Paramètres du projet présentant le plug-in Spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="f2414-156">Activer l’audio spatial sur votre station de travail</span><span class="sxs-lookup"><span data-stu-id="f2414-156">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="f2414-157">Sur les versions de bureau de Windows, l’audio spatial est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="f2414-157">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="f2414-158">Pour l’activer, cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="f2414-158">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="f2414-159">Pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2, choisissez **son Spatial > Windows Sonic pour casque**.</span><span class="sxs-lookup"><span data-stu-id="f2414-159">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Paramètres audio spatiaux du Bureau](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="f2414-161">Ce paramètre est requis uniquement si vous envisagez de tester votre projet dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="f2414-161">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2414-162">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f2414-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2414-163">Audio spatial Unity-chapitre 2</span><span class="sxs-lookup"><span data-stu-id="f2414-163">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

