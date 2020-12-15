---
title: Profilage avec des Insights inréels
description: Découvrez comment utiliser des Insights inréels sur HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Moteur 4, UE4, HoloLens, HoloLens 2, développement, profilage non réel, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486338"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="d748d-104">Profilage avec des Insights inréels</span><span class="sxs-lookup"><span data-stu-id="d748d-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="d748d-105">Le système de profilage qui collecte, analyse et visualise les données à partir d’un moteur inréel [est un](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) système de profilage.</span><span class="sxs-lookup"><span data-stu-id="d748d-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="d748d-106">Le système de profilage peut vous aider à identifier les goulots d’étranglement d’optimisation et les zones où les performances des applications peuvent utiliser une augmentation.</span><span class="sxs-lookup"><span data-stu-id="d748d-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="d748d-107">Normalement, vous activez les Insights non réels directement à partir de l’éditeur, mais pour HoloLens 2, vous devez utiliser la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d748d-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="d748d-108">Programme d’installation</span><span class="sxs-lookup"><span data-stu-id="d748d-108">Setup</span></span>

<span data-ttu-id="d748d-109">Non réel vous permet de créer et de configurer un « profil personnalisé » dans le lanceur HoloLens avec les paramètres de ligne de commande qui permettent d’obtenir des informations non réelles.</span><span class="sxs-lookup"><span data-stu-id="d748d-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="d748d-110">Recherchez l’adresse IP de votre ordinateur à l’aide de la commande **ipconfig** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="d748d-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="d748d-111">L’adresse IP est l’adresse IPv4 indiquée par ipconfig.</span><span class="sxs-lookup"><span data-stu-id="d748d-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="d748d-112">Gardez cela à l’esprit pour plus tard lorsque vous définissez des paramètres de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d748d-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d748d-113">Si vous êtes derrière un VPN, vous devrez peut-être fournir l’adresse IP fournie par le biais du VPN à la place.</span><span class="sxs-lookup"><span data-stu-id="d748d-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Capture d’écran des résultats de la ligne de commande pour la commande ipconfig](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="d748d-115">Accédez au début du panneau du moteur inréel et ouvrez **Device Manager** sous le bouton **lancer** :</span><span class="sxs-lookup"><span data-stu-id="d748d-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![Capture d’écran des options de lancement avec le gestionnaire de périphériques en surbrillance](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="d748d-117">Dans le Device Manager, sélectionnez **Ajouter un appareil non répertorié**:</span><span class="sxs-lookup"><span data-stu-id="d748d-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![Capture d’écran du gestionnaire de périphériques ouverte dans un moteur inréel](images/unreal-insights-img-03.png)

4. <span data-ttu-id="d748d-119">Cliquez sur **Sélectionner une plateforme** , puis choisissez **HoloLens**:</span><span class="sxs-lookup"><span data-stu-id="d748d-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![Capture d’écran de la liste déroulante Ajouter un appareil sans liste avec HoloLens mis en surbrillance](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="d748d-121">Si vous utilisez IPoverUSB, entrez 127.0.0.1:10 080 comme identificateur d’appareil.</span><span class="sxs-lookup"><span data-stu-id="d748d-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="d748d-122">Entrez votre utilisateur et votre mot de passe HoloLens dans leurs champs respectifs et renseignez le **nom d’affichage** comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="d748d-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d748d-123">L’identificateur d’appareil est l’adresse IP du HoloLens, et non de l’ordinateur qui exécute des analyses inréelless que vous avez trouvé à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="d748d-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![Capture d’écran des détails de l’appareil HoloLens dans le gestionnaire de périphériques](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="d748d-125">Sélectionnez **Ajouter** et votre HoloLens doit apparaître dans la liste des appareils du gestionnaire de périphériques :</span><span class="sxs-lookup"><span data-stu-id="d748d-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![Capture d’écran de HoloLens ajoutée à la liste des appareils](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="d748d-127">Lancer</span><span class="sxs-lookup"><span data-stu-id="d748d-127">Launch</span></span>

1. <span data-ttu-id="d748d-128">Ouvrez le **lanceur de projet** à partir du panneau UE4 sous le bouton **lancer** :</span><span class="sxs-lookup"><span data-stu-id="d748d-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![Capture d’écran des options de lancement avec le lanceur de projet en surbrillance](images/unreal-insights-img-07.png)

2. <span data-ttu-id="d748d-130">Sélectionnez le **+** bouton pour créer un profil personnalisé sous **profils de lancement personnalisés**.</span><span class="sxs-lookup"><span data-stu-id="d748d-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="d748d-131">Une fois créé, vous pouvez toujours modifier ce profil ultérieurement :</span><span class="sxs-lookup"><span data-stu-id="d748d-131">Once created, you can always edit this profile later:</span></span>

![Capture d’écran du lanceur de projet avec les profils de lancement personnalisés mis en surbrillance](images/unreal-insights-img-08.png)

3. <span data-ttu-id="d748d-133">Sélectionnez le bouton **modifier le profil** dans le profil de lancement personnalisé HoloLens et configurez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d748d-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="d748d-134">Sélectionnez **Cook** to dans **le livre** pour activer la copie sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="d748d-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="d748d-135">Vous pouvez vérifier que **vous souhaitez archiver ?** dans la section **Archive** pour conserver le fichier. appxbundle généré au lieu de le supprimer pour économiser de l’espace disque.</span><span class="sxs-lookup"><span data-stu-id="d748d-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="d748d-136">Spécifiez un emplacement pour le. appxbundle et basculez vers une build de développement si vous le souhaitez</span><span class="sxs-lookup"><span data-stu-id="d748d-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![Capture d’écran des options de Cook dans Configuration de profil avec Cook par le livre et HoloLens mis en surbrillance](images/unreal-insights-img-09.png)

4. <span data-ttu-id="d748d-138">Définir **Comment voulez-vous déployer la build ?** pour la **copier sur l’appareil** afin d’activer la section de **lancement** de l’interface utilisateur :</span><span class="sxs-lookup"><span data-stu-id="d748d-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![Capture d’écran du lanceur de projet avec les options de déploiement avec copier sur l’appareil mis en surbrillance](images/unreal-insights-img-10.png)

5. <span data-ttu-id="d748d-140">Définissez **des paramètres de ligne de commande supplémentaires** dans la section **Launch** .</span><span class="sxs-lookup"><span data-stu-id="d748d-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="d748d-141">Les paramètres sont écrits dans un fichier ue4commandline.txt, empaquetés dans le bundle et utilisés au lancement.</span><span class="sxs-lookup"><span data-stu-id="d748d-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="d748d-142">Essayez celles-ci pour les starters : **-tracehost = IP_OF_YOUR_PC-trace = Journal, Bookmark, Frame, CPU, GPU, LoadTime, file, net**</span><span class="sxs-lookup"><span data-stu-id="d748d-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="d748d-143">Vous trouverez une liste complète des paramètres de lancement disponibles dans la [documentation de référence sur les informations inréelles](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span><span class="sxs-lookup"><span data-stu-id="d748d-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="d748d-144">« IP_OF_YOUR_PC » est l’adresse IP que nous avons trouvée à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="d748d-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="d748d-145">Il s’agit de l’adresse IP de l’ordinateur qui exécute des informations non réelles, et non de l’adresse IP du HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d748d-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d748d-146">Les suivis peuvent être très rapidement volumineux.</span><span class="sxs-lookup"><span data-stu-id="d748d-146">Traces can get large very quickly.</span></span> <span data-ttu-id="d748d-147">Activez uniquement les canaux dont vous avez besoin pour réduire la taille de la trace.</span><span class="sxs-lookup"><span data-stu-id="d748d-147">Enable only those channels you need to keep trace size low.</span></span>

![Capture d’écran des options de configuration du lancement](images/unreal-insights-img-11.png)

6. <span data-ttu-id="d748d-149">Lancer des analyses non réelles avant le lancement de l’application ; sinon, les informations non réelles ne peuvent pas s’initialiser correctement avant l’application :</span><span class="sxs-lookup"><span data-stu-id="d748d-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="d748d-150">L’exécutable Unreal Insights est stocké dans le dossier du moteur de fichiers binaires, généralement comme suit : « C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe »</span><span class="sxs-lookup"><span data-stu-id="d748d-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![Capture d’écran de l’exécution d’un exécutable d’Insights inréel](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="d748d-152">Sélectionnez **précédent** pour revenir à la racine de la boîte de dialogue du **lanceur de projet**</span><span class="sxs-lookup"><span data-stu-id="d748d-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="d748d-153">De retour dans l’éditeur, cliquez sur **lancer** sur votre profil de lancement personnalisé</span><span class="sxs-lookup"><span data-stu-id="d748d-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![Capture d’écran des profils de lancement personnalisés](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="d748d-155">Regardez quand votre projet est empaqueté, installé sur votre appareil et lancé</span><span class="sxs-lookup"><span data-stu-id="d748d-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="d748d-156">Profilage</span><span class="sxs-lookup"><span data-stu-id="d748d-156">Profiling</span></span>

<span data-ttu-id="d748d-157">De retour dans informations non réelles, sélectionnez la connexion **active** à votre appareil pour démarrer le profilage</span><span class="sxs-lookup"><span data-stu-id="d748d-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="d748d-158">Le profil personnalisé est partagé entre les projets.</span><span class="sxs-lookup"><span data-stu-id="d748d-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="d748d-159">À partir de là, vous pouvez utiliser le profil personnalisé que vous avez créé au lieu de le faire à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="d748d-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="d748d-160">Il vous suffit de recréer la connexion à l’appareil chaque fois que vous démarrez sans réel avec les étapes 3 à 6 de la [section Configuration](#setup).</span><span class="sxs-lookup"><span data-stu-id="d748d-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="d748d-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d748d-161">See also</span></span>
* [<span data-ttu-id="d748d-162">Documentation sur les informations non réelles</span><span class="sxs-lookup"><span data-stu-id="d748d-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

