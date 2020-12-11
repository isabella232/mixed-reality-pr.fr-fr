---
title: Son spatial dans Unreal
description: Découvrez tous les détails du plug-in de son spatial pour Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, communication à distance, réalité mixte, développement, démarrage, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, son spatial
ms.openlocfilehash: fa87862f6a6af456ea344b67e22f1640c9cfafb4
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609540"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="42ebd-104">Son spatial dans Unreal</span><span class="sxs-lookup"><span data-stu-id="42ebd-104">Spatial Audio in Unreal</span></span>

<span data-ttu-id="42ebd-105">Contrairement à la vue, les êtres humains entendent les sons ambiants à 360 degrés.</span><span class="sxs-lookup"><span data-stu-id="42ebd-105">Unlike vision, humans hear in 360-degree surround sound.</span></span> <span data-ttu-id="42ebd-106">Le son spatial émule le fonctionnement de l’audition humaine, en fournissant les signaux nécessaires pour identifier les emplacements sonores dans l’espace.</span><span class="sxs-lookup"><span data-stu-id="42ebd-106">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="42ebd-107">Quand vous ajoutez un son spatial dans vos applications de réalité mixte, vous améliorez le niveau d’immersion de l’expérience de votre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="42ebd-107">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your user's experience.</span></span>  

<span data-ttu-id="42ebd-108">Le traitement du son spatial en haute qualité est complexe : HoloLens 2 est donc fourni avec un matériel dédié pour le traitement de ces objets audio.</span><span class="sxs-lookup"><span data-stu-id="42ebd-108">High-quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="42ebd-109">Pour pouvoir accéder à cette prise en charge du traitement matériel, vous devez installer le plug-in **MicrosoftSpatialSound** dans votre projet Unreal.</span><span class="sxs-lookup"><span data-stu-id="42ebd-109">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="42ebd-110">Cet article vous guide tout au long de l’installation et de la configuration de ce plug-in, et vous oriente vers des ressources plus approfondies.</span><span class="sxs-lookup"><span data-stu-id="42ebd-110">This article will walk you through the installation and configuration of the plugin and point you towards more in-depth resources.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="42ebd-111">Installation du plug-in Microsoft Spatial Sound</span><span class="sxs-lookup"><span data-stu-id="42ebd-111">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="42ebd-112">La première étape pour ajouter un son spatial à votre projet consiste à installer le plug-in de son spatial Microsoft, que vous trouverez en :</span><span class="sxs-lookup"><span data-stu-id="42ebd-112">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="42ebd-113">Cliquant sur **Modifier > Plug-ins** et en recherchant **MicrosoftSpatialSound** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="42ebd-113">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="42ebd-114">Cochant la case **Activé** dans le plug-in **MicrosoftSpatialSound**.</span><span class="sxs-lookup"><span data-stu-id="42ebd-114">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="42ebd-115">Redémarrant l’éditeur Unreal en sélectionnant **Redémarrer maintenant** à partir de la page de plug-ins.</span><span class="sxs-lookup"><span data-stu-id="42ebd-115">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="42ebd-116">Si ce n’est déjà fait, vous devez installer les plug-ins **Microsoft Windows Mixed Reality** et **HoloLens** en suivant les instructions fournies dans la section **[Initialisation de votre projet](tutorials/unreal-uxt-ch2.md)** de notre série de tutoriels Unreal.</span><span class="sxs-lookup"><span data-stu-id="42ebd-116">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Plug-in audio spatial Unreal](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="42ebd-118">Une fois l’éditeur redémarré, vous pouvez commencer votre projet.</span><span class="sxs-lookup"><span data-stu-id="42ebd-118">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="42ebd-119">Définition du plug-in de spatialisation pour la plateforme HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="42ebd-119">Setting the spatialization plugin for HoloLens 2 platform</span></span>

<span data-ttu-id="42ebd-120">La configuration du plug-in de spatialisation s’effectue sur la base de chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="42ebd-120">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="42ebd-121">Pour activer le plug-in Microsoft Spatial Sound pour HoloLens 2, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="42ebd-121">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="42ebd-122">Sélectionnez **Edit > Project Settings**, faites défiler jusqu’à \*\*Platforms, puis cliquez sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="42ebd-122">Selecting **Edit > Project Settings**, scrolling to \*\*Platforms, and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="42ebd-123">Développez les propriétés **Audio** et affectez la valeur **Microsoft Spatial Sound** au champ **Spatialization Plugin**.</span><span class="sxs-lookup"><span data-stu-id="42ebd-123">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![Plug-in de spatialisation pour la plateforme HoloLens](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="42ebd-125">Si vous prévoyez d’afficher un aperçu de votre application dans l’éditeur Unreal sur un PC de bureau, vous devez répéter les étapes ci-dessus pour la plateforme **Windows** :</span><span class="sxs-lookup"><span data-stu-id="42ebd-125">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Plug-in de spatialisation pour la plateforme Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="42ebd-127">Activation de l’audio spatial sur votre station de travail</span><span class="sxs-lookup"><span data-stu-id="42ebd-127">Enabling spatial audio on your workstation</span></span>

<span data-ttu-id="42ebd-128">L’audio spatial est désactivé par défaut sur les versions de bureau de Windows.</span><span class="sxs-lookup"><span data-stu-id="42ebd-128">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="42ebd-129">Pour l’activer, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="42ebd-129">You can enable it by:</span></span>
* <span data-ttu-id="42ebd-130">Cliquez avec le bouton droit sur l’icône de **volume** dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="42ebd-130">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="42ebd-131">Choisissez **Son spatial-> Windows Sonic pour casque** pour obtenir la meilleure représentation de ce que vous entendrez sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="42ebd-131">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Plug-in de spatialisation](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="42ebd-133">Ce paramètre est obligatoire uniquement si vous envisagez de tester votre projet dans l’éditeur Unreal.</span><span class="sxs-lookup"><span data-stu-id="42ebd-133">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="42ebd-134">Création d’objets d’atténuation</span><span class="sxs-lookup"><span data-stu-id="42ebd-134">Creating Attenuation objects</span></span>

<span data-ttu-id="42ebd-135">Une fois que vous avez installé et configuré les plug-ins nécessaires :</span><span class="sxs-lookup"><span data-stu-id="42ebd-135">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="42ebd-136">Recherchez un acteur **Ambient Sound** (Son ambiant) dans la fenêtre **Place Actors** (Placer des acteurs), puis faites-le glisser dans la fenêtre **Scene**.</span><span class="sxs-lookup"><span data-stu-id="42ebd-136">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Ajout d’un acteur de son ambiant](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="42ebd-138">Faites de l’acteur **Ambient Sound** un enfant d’un visuel dans votre scène.</span><span class="sxs-lookup"><span data-stu-id="42ebd-138">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="42ebd-139">Un acteur Ambient Sound n’a pas de représentation visuelle par défaut, donc vous n’entendrez un son que de sa position dans la scène.</span><span class="sxs-lookup"><span data-stu-id="42ebd-139">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="42ebd-140">Si vous l’attachez à un visuel, vous pouvez voir et déplacer l’acteur comme n’importe quel autre actif multimédia.</span><span class="sxs-lookup"><span data-stu-id="42ebd-140">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="42ebd-141">Cliquez avec le bouton droit sur **Content Browser** (Navigateur de contenu) et sélectionnez **Create Advanced Asset -> Sounds -> Sound Attenuation** (Créer un actif multimédia avancé -> Sons -> Atténuation du son) :</span><span class="sxs-lookup"><span data-stu-id="42ebd-141">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![Création d’un actif multimédia d’atténuation du son](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="42ebd-143">Cliquez avec le bouton droit sur l’élément **Sound Attenuation** dans la fenêtre **Content Browser** et sélectionnez l’option **Edit** pour afficher la fenêtre de propriétés.</span><span class="sxs-lookup"><span data-stu-id="42ebd-143">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="42ebd-144">Basculez l’option **Spatialization Method** sur **Binaural**.</span><span class="sxs-lookup"><span data-stu-id="42ebd-144">Switch the **Spatialization Method** to **Binaural**.</span></span>

![Définir la méthode de spatialisation](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="42ebd-146">Sélectionnez l’acteur **Ambient Sound** et faites défiler jusqu’à la section **Attenuation** dans le panneau **Details**.</span><span class="sxs-lookup"><span data-stu-id="42ebd-146">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="42ebd-147">Affectez l’actif **Sound Attenuation** que vous avez créé comme valeur de la propriété **Attenuation Settings**.</span><span class="sxs-lookup"><span data-stu-id="42ebd-147">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Définir le paramètre d’atténuation](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="42ebd-149">Définissez le **Sound Asset** que vous voulez attacher à l’acteur Ambient Sound :</span><span class="sxs-lookup"><span data-stu-id="42ebd-149">Set the **Sound Asset** you want to attach to the Ambient Sound actor:</span></span>
    * <span data-ttu-id="42ebd-150">Mettez à jour la propriété **Sound** de l’acteur Ambient Sound pour spécifier le fichier SoundAsset à utiliser.</span><span class="sxs-lookup"><span data-stu-id="42ebd-150">Update the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Définir l’actif sonore](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="42ebd-152">Le fichier SoundAsset doit être mono pour être spatialisé avec le plug-in Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="42ebd-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="42ebd-153">Vous trouverez les propriétés du fichier son en pointant sur l’actif multimédia dans la fenêtre Content Browser, comme indiqué dans la capture d’écran ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="42ebd-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Nouvel actif multimédia d’atténuation du son](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="42ebd-155">Quand la ressource audio est configurée, le son ambiant peut être spatialisé en utilisant la prise en charge du déchargement matériel dédié sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="42ebd-155">When the sound asset is configured, the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="42ebd-156">Configuration des objets pour la spatialisation</span><span class="sxs-lookup"><span data-stu-id="42ebd-156">Configuring objects for spatialization</span></span>

<span data-ttu-id="42ebd-157">L’utilisation de l’audio spatial signifie que vous responsable de la gestion du comportement sonore dans un environnement virtuel.</span><span class="sxs-lookup"><span data-stu-id="42ebd-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="42ebd-158">Votre objectif principal est de créer des objets sonores qui semblent plus bruyants quand l’utilisateur est proche, et moins bruyants quand l’utilisateur est éloigné.</span><span class="sxs-lookup"><span data-stu-id="42ebd-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="42ebd-159">C’est ce que l’on appelle l’atténuation sonore : faire en sorte que les sons semblent positionnés à un endroit fixe.</span><span class="sxs-lookup"><span data-stu-id="42ebd-159">This is referred to as sound attenuation, making sounds appear as if they're positioned in a fixed spot.</span></span>

<span data-ttu-id="42ebd-160">Tous les objets d’atténuation sont fournis avec des paramètres modifiables de :</span><span class="sxs-lookup"><span data-stu-id="42ebd-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="42ebd-161">Distance</span><span class="sxs-lookup"><span data-stu-id="42ebd-161">Distance</span></span>
* <span data-ttu-id="42ebd-162">Spatialisation</span><span class="sxs-lookup"><span data-stu-id="42ebd-162">Spatialization</span></span>
* <span data-ttu-id="42ebd-163">Absorption de l’air</span><span class="sxs-lookup"><span data-stu-id="42ebd-163">Air Absorption</span></span>
* <span data-ttu-id="42ebd-164">Focus de l’auditeur</span><span class="sxs-lookup"><span data-stu-id="42ebd-164">Listener Focus</span></span>
* <span data-ttu-id="42ebd-165">Envoi de réverbération</span><span class="sxs-lookup"><span data-stu-id="42ebd-165">Reverb Send</span></span>
* <span data-ttu-id="42ebd-166">Occlusion</span><span class="sxs-lookup"><span data-stu-id="42ebd-166">Occlusion</span></span>

<span data-ttu-id="42ebd-167">L’article [Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) fournit des détails et des informations sur l’implémentation de chacun de ces aspects.</span><span class="sxs-lookup"><span data-stu-id="42ebd-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="42ebd-168">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="42ebd-168">Next Development Checkpoint</span></span>

<span data-ttu-id="42ebd-169">Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous explorez actuellement les composants de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="42ebd-169">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="42ebd-170">À partir d’ici, vous pouvez passer au composant suivant :</span><span class="sxs-lookup"><span data-stu-id="42ebd-170">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="42ebd-171">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="42ebd-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="42ebd-172">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="42ebd-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="42ebd-173">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="42ebd-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="42ebd-174">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="42ebd-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="42ebd-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42ebd-175">See also</span></span>
* [<span data-ttu-id="42ebd-176">Son spatial</span><span class="sxs-lookup"><span data-stu-id="42ebd-176">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="42ebd-177">Conception du son spatial</span><span class="sxs-lookup"><span data-stu-id="42ebd-177">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="42ebd-178">Réalité mixte - Fonctionnalités spatiales - Cours 220 : Son spatial</span><span class="sxs-lookup"><span data-stu-id="42ebd-178">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
