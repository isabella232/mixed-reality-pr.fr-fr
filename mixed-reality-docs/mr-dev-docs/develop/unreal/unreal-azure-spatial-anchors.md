---
title: Azure Spatial Anchors dans Unreal
description: Découvrez comment créer, gérer et localiser des ancres spatiales Azure existantes dans des applications de réalité mixte Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, développement azure, ancres spatiales, réalité mixte, développement, fonctionnalités, nouveau projet, émulateur, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 95e8ad708dd44a05fb306b2ea49f167fd400c5d8
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009769"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="6cc11-104">Azure Spatial Anchors dans Unreal</span><span class="sxs-lookup"><span data-stu-id="6cc11-104">Azure Spatial Anchors in Unreal</span></span>

<span data-ttu-id="6cc11-105">Azure Spatial Anchors est un service de Réalité mixte Microsoft qui permet aux appareils de réalité augmentée de découvrir, de partager et de conserver des points d’ancrage dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="6cc11-105">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="6cc11-106">La documentation ci-dessous fournit des instructions pour l’intégration du service Azure Spatial Anchors à un projet Unreal.</span><span class="sxs-lookup"><span data-stu-id="6cc11-106">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="6cc11-107">Si vous souhaitez obtenir plus d’informations, consultez la documentation sur le [service Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="6cc11-107">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="6cc11-108">Unreal Engine 4.26 a maintenant des plug-ins pour la prise en charge d’ARKit et d’ARCore quand vous ciblez iOS ou Android.</span><span class="sxs-lookup"><span data-stu-id="6cc11-108">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cc11-109">Les ancres locales sont stockées sur l’appareil, alors que les ancres spatiales Azure sont stockées dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="6cc11-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="6cc11-110">Si vous envisagez de stocker vos ancres localement sur un appareil, nous mettons à votre disposition un document sur les [ancres spatiales locales](unreal-spatial-anchors.md) qui peut vous guider tout au long du processus.</span><span class="sxs-lookup"><span data-stu-id="6cc11-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="6cc11-111">Notez que vous pouvez avoir des ancres locales et Azure dans le même projet sans conflit.</span><span class="sxs-lookup"><span data-stu-id="6cc11-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6cc11-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="6cc11-112">Prerequisites</span></span>

<span data-ttu-id="6cc11-113">Pour suivre ce guide, vous devez avoir :</span><span class="sxs-lookup"><span data-stu-id="6cc11-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="6cc11-114">Installé [Unreal version 4.25](https://www.unrealengine.com/get-now) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6cc11-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="6cc11-115">Un projet [HoloLens 2](tutorials/unreal-uxt-ch1.md) configuré dans Unreal.</span><span class="sxs-lookup"><span data-stu-id="6cc11-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="6cc11-116">Lu la [vue d’ensemble d’Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="6cc11-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="6cc11-117">Une connaissance de base de C++ et Unreal.</span><span class="sxs-lookup"><span data-stu-id="6cc11-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="6cc11-118">Obtention d’informations sur le compte Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="6cc11-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="6cc11-119">Avant d’utiliser Azure Spatial Anchors dans votre projet, vous devez :</span><span class="sxs-lookup"><span data-stu-id="6cc11-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="6cc11-120">[Créer une ressource d’ancres spatiales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) et copier les champs de compte listés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6cc11-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="6cc11-121">Ces valeurs sont utilisées pour authentifier les utilisateurs auprès du compte de votre application :</span><span class="sxs-lookup"><span data-stu-id="6cc11-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="6cc11-122">**ID de compte**</span><span class="sxs-lookup"><span data-stu-id="6cc11-122">**Account ID**</span></span>
    * <span data-ttu-id="6cc11-123">**Clé de compte**</span><span class="sxs-lookup"><span data-stu-id="6cc11-123">**Account Key**</span></span>

<span data-ttu-id="6cc11-124">Pour plus d’informations, consultez la documentation sur l’[authentification Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="6cc11-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc11-125">Azure Spatial Anchors dans Unreal 4.25 ne prend pas en charge les jetons d’authentification Azure AD, mais la prise en charge de cette fonctionnalité sera disponible dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6cc11-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="6cc11-126">Ajout des plug-ins Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="6cc11-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="6cc11-127">Activez les plug-ins Azure Spatial Anchors dans l’éditeur Unreal en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6cc11-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="6cc11-128">Cliquez sur **Edit > Plugins** et recherchez **AzureSpatialAnchors** et **AzureSpatialAnchorsForWMR**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="6cc11-129">Cochez la case **Enabled** dans les deux plug-ins pour autoriser l’accès aux bibliothèques de blueprints Azure Spatial Anchors dans votre application.</span><span class="sxs-lookup"><span data-stu-id="6cc11-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Capture d’écran des plugins Spatial Anchors dans l’éditeur Unreal](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="6cc11-131">Une fois cette opération terminée, redémarrez l’éditeur Unreal pour que les modifications apportées aux plug-ins prennent effet.</span><span class="sxs-lookup"><span data-stu-id="6cc11-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="6cc11-132">Le projet est maintenant prêt à utiliser Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="6cc11-133">Démarrage d’une session Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="6cc11-133">Starting a Spatial Anchors session</span></span>

<span data-ttu-id="6cc11-134">Une session Azure Spatial Anchors permet aux applications clientes de communiquer avec le service Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="6cc11-135">Vous devez créer et démarrer une session Azure Spatial Anchors pour créer, conserver et partager des ancres spatiales Azure :</span><span class="sxs-lookup"><span data-stu-id="6cc11-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="6cc11-136">Ouvrez le blueprint du Pawn que vous utilisez dans l’application.</span><span class="sxs-lookup"><span data-stu-id="6cc11-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="6cc11-137">Ajoutez deux variables de chaîne pour l’**ID de compte** et la **clé de compte**, puis affectez les valeurs correspondantes à partir de votre compte Azure Spatial Anchors pour authentifier la session.</span><span class="sxs-lookup"><span data-stu-id="6cc11-137">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Capture d’écran du volet d’informations avec mise en évidence de l’ID de compte, de la clé et du type de variable Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="6cc11-139">Démarrez une session Azure Spatial Anchors en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6cc11-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="6cc11-140">Vérifiez qu’une **session RA** est en cours d’exécution dans l’application HoloLens, car la session Azure Spatial Anchors ne peut pas démarrer tant qu’une session RA n’est pas en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6cc11-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="6cc11-141">Si vous n’en avez pas configuré, [créez une ressource de session RA](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="6cc11-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="6cc11-142">Ajoutez l’événement personnalisé **Démarrer une session Azure Spatial Anchors** et configurez-le comme indiqué dans la capture d’écran ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6cc11-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="6cc11-143">La création d’une session ne provoque pas son démarrage par défaut, ce qui vous permet de configurer la session pour l’authentification auprès du service Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-143">Creating a session doesn't start the session by default, which allows you to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Blueprint de l’événement personnalisé lié au démarrage de la session Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="6cc11-145">Configurez la session Azure Spatial Anchors pour fournir l’**ID de compte** et la **clé de compte**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Blueprint de la fonction de configuration de session avec ajout de l’ID de compte et de la clé de compte](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="6cc11-147">Démarrez la session Azure Spatial Anchors afin de permettre à l’application de créer et de localiser les ancres spatiales Azure.</span><span class="sxs-lookup"><span data-stu-id="6cc11-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Blueprint de la fonction de démarrage de session Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="6cc11-149">Nous vous recommandons de nettoyer les ressources Azure Spatial Anchors dans votre blueprint de graphe d’événements lorsque vous n’utilisez plus le service :</span><span class="sxs-lookup"><span data-stu-id="6cc11-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="6cc11-150">Arrêtez la session Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="6cc11-151">La session ne sera plus en cours d’exécution, mais ses ressources associées existeront toujours dans le plug-in Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Blueprint de l’événement personnalisé lié à l’arrêt de la session Azure Spatial Anchors et de la fonction d’arrêt de session](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="6cc11-153">Détruisez la session Azure Spatial Anchors pour nettoyer toutes les ressources de session Azure Spatial Anchors, toujours connues du plug-in Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Blueprint de la fonction de destruction de session](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="6cc11-155">Votre blueprint de graphe d’événements doit ressembler à la capture d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="6cc11-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Blueprint du graphe d’événements complet pour la configuration de session Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a><span data-ttu-id="6cc11-157">Création d’une ancre</span><span class="sxs-lookup"><span data-stu-id="6cc11-157">Creating an anchor</span></span>

<span data-ttu-id="6cc11-158">Une ancre spatiale Azure représente un environnement physique dans l’espace de l’application de réalité augmentée, qui verrouille le contenu de réalité augmentée à des emplacements physiques.</span><span class="sxs-lookup"><span data-stu-id="6cc11-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to physical locations.</span></span> <span data-ttu-id="6cc11-159">Les ancres spatiales Azure peuvent également être partagées par différents utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6cc11-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="6cc11-160">Ce partage permet de placer du contenu de réalité augmenté sur différents appareils au même emplacement dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="6cc11-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="6cc11-161">Pour créer une ancre spatiale Azure</span><span class="sxs-lookup"><span data-stu-id="6cc11-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="6cc11-162">Vérifiez qu’une session Azure Spatial Anchors est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6cc11-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="6cc11-163">L’application ne peut pas créer ou conserver une ancre spatiale Azure quand aucune session Azure Spatial Anchors n’est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6cc11-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Blueprint de l’événement personnalisé lié à la création d’une ancre spatiale Azure](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="6cc11-165">Créez ou obtenez un **[composant de scène](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** Unreal dont l’emplacement doit être conservé.</span><span class="sxs-lookup"><span data-stu-id="6cc11-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="6cc11-166">Dans l’image ci-dessous, le composant **Scene Component Needing Anchor** est utilisé comme variable.</span><span class="sxs-lookup"><span data-stu-id="6cc11-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="6cc11-167">Un composant de scène Unreal est nécessaire pour établir une transformation universelle d’application pour une [épingle RA](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) et une ancre spatiale Azure.</span><span class="sxs-lookup"><span data-stu-id="6cc11-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Blueprint de l’événement personnalisé lié à la création d’une ancre spatiale Azure avec un composant de scène](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="6cc11-169">Pour construire et enregistrer une ancre spatiale Azure pour un composant de scène Unreal</span><span class="sxs-lookup"><span data-stu-id="6cc11-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="6cc11-170">Appelez le [composant d’épingle](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) pour le composant de scène Unreal et spécifiez la **transformation universelle** du composant de scène comme transformation universelle utilisée pour l’épingle RA.</span><span class="sxs-lookup"><span data-stu-id="6cc11-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="6cc11-171">Unreal effectue le suivi des points RA dans l’espace de l’application à l’aide d’épingles RA, qui sont utilisées pour créer une ancre spatiale Azure.</span><span class="sxs-lookup"><span data-stu-id="6cc11-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="6cc11-172">Dans Unreal, une épingle RA est analogue à un SpatialAnchor sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6cc11-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Blueprint du composant de scène connecté à la fonction du composant d’épingle](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="6cc11-174">Appelez **Create Cloud Anchor** à l’aide de l’épingle RA que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="6cc11-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="6cc11-175">Create Cloud Anchor crée une ancre spatiale Azure localement mais pas dans le service Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="6cc11-176">Les paramètres de l’ancre spatiale Azure, tels que la date d’expiration, peuvent être définis avant de créer l’ancre spatiale Azure avec le service.</span><span class="sxs-lookup"><span data-stu-id="6cc11-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Blueprint de la fonction de composant d’épingle connectée à la fonction Create Cloud Anchor, qui retourne l’épingle de réalité augmentée](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="6cc11-178">Définissez l’expiration de l’ancre spatiale Azure.</span><span class="sxs-lookup"><span data-stu-id="6cc11-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="6cc11-179">Le paramètre Durée de vie de cette fonction permet au développeur de spécifier, en secondes, la durée pendant laquelle l’ancre doit être tenue à jour par le service.</span><span class="sxs-lookup"><span data-stu-id="6cc11-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="6cc11-180">Par exemple, un délai d’expiration d’une semaine prendrait une valeur de 60 secondes x 60 minutes x 24 heures x 7 jours = 604 800 secondes.</span><span class="sxs-lookup"><span data-stu-id="6cc11-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Blueprint de l’ancre cloud connectée à la fonction de définition du délai d’expiration avec une valeur de durée de vie fixée à 604 800 secondes](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="6cc11-182">Après avoir défini les paramètres de l’ancre, déclarez-la comme prête à être enregistrée.</span><span class="sxs-lookup"><span data-stu-id="6cc11-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="6cc11-183">Dans l’exemple ci-dessous, la nouvelle ancre spatiale Azure est ajoutée à un ensemble d’ancres spatiales Azure nécessitant un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="6cc11-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="6cc11-184">Cet ensemble est déclaré en tant que variable pour le blueprint de Pawn.</span><span class="sxs-lookup"><span data-stu-id="6cc11-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![Blueprint de l’ancre prête à être enregistrée dans la variable définie](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="6cc11-186">Enregistrement d’une ancre</span><span class="sxs-lookup"><span data-stu-id="6cc11-186">Saving an Anchor</span></span>

<span data-ttu-id="6cc11-187">Après avoir configuré l’ancre spatiale Azure avec vos paramètres, appelez **Save Cloud Anchor**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="6cc11-188">Save Cloud Anchor déclare l’ancre auprès du service Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="6cc11-189">Lorsque l’appel à Save Cloud Anchor s’effectue correctement, l’ancre spatiale Azure est disponible pour les autres utilisateurs du service Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Blueprint de l’appel de la fonction Save Cloud Anchor](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="6cc11-191">Save Cloud Anchor est une fonction asynchrone qui peut être appelée uniquement sur un événement de thread de jeu, par exemple **EventTick**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="6cc11-192">Save Cloud Anchor peut ne pas apparaître en tant que fonction de blueprint disponible dans les fonctions de blueprint personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6cc11-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="6cc11-193">Toutefois, elle devrait être disponible dans l’éditeur de blueprint de graphe d’événements de Pawn.</span><span class="sxs-lookup"><span data-stu-id="6cc11-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="6cc11-194">Dans l’exemple ci-dessous, l’ancre spatiale Azure est stockée dans un ensemble pendant un rappel d’événement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="6cc11-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="6cc11-195">Elle est ensuite enregistrée sur l’EventTick.</span><span class="sxs-lookup"><span data-stu-id="6cc11-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="6cc11-196">L’enregistrement d’une ancre spatiale Azure peut nécessiter plusieurs tentatives, en fonction de la quantité de données spatiales créées par votre session Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="6cc11-197">Il est donc préférable de vérifier si l’appel d’enregistrement a réussi.</span><span class="sxs-lookup"><span data-stu-id="6cc11-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="6cc11-198">Si l’ancre n’est pas enregistrée, rajoutez-la à l’ensemble d’ancres à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="6cc11-198">If the anchor doesn't save, readd it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="6cc11-199">Les prochains EventTicks vont continuer d’essayer d’enregistrer l’ancre jusqu’à ce qu’elle soit correctement stockée.</span><span class="sxs-lookup"><span data-stu-id="6cc11-199">Future EventTicks will keep trying to save the anchor until it's successfully stored.</span></span>

![Blueprint des ancres non enregistrées, qui sont réenregistrées dans la variable définie](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="6cc11-201">Une fois l’ancre enregistrée, la transformation d’épingles de réalité augmentée sert de transformation de référence pour le placement du contenu dans votre application.</span><span class="sxs-lookup"><span data-stu-id="6cc11-201">Once the anchor saves, the AR Pins' transform acts as a reference transform for placing content in your app.</span></span> <span data-ttu-id="6cc11-202">D’autres utilisateurs peuvent détecter cette ancre et aligner du contenu RA pour différents appareils dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="6cc11-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="6cc11-203">Suppression d’une ancre</span><span class="sxs-lookup"><span data-stu-id="6cc11-203">Deleting an Anchor</span></span>

<span data-ttu-id="6cc11-204">Vous pouvez supprimer des ancres du service Azure Spatial Anchors en appelant **Delete Cloud Anchor**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Blueprint de l’appel de la fonction Delete Cloud Anchor](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="6cc11-206">Delete Cloud Anchor est une fonction latente qui peut être appelée uniquement sur un événement de thread de jeu, tel qu’EventTick.</span><span class="sxs-lookup"><span data-stu-id="6cc11-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="6cc11-207">Delete Cloud Anchor peut ne pas apparaître en tant que fonction de blueprint disponible dans les fonctions de blueprint personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6cc11-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="6cc11-208">Elle devrait toutefois être disponible dans l’éditeur de blueprint de graphe d’événements de Pawn.</span><span class="sxs-lookup"><span data-stu-id="6cc11-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="6cc11-209">Dans l’exemple ci-dessous, l’ancre est marquée pour suppression sur un événement d’entrée personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6cc11-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="6cc11-210">La suppression est ensuite tentée sur l’EventTick.</span><span class="sxs-lookup"><span data-stu-id="6cc11-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="6cc11-211">En cas d’échec de la suppression de l’ancre spatiale Azure, ajoutez-la à l’ensemble d’ancres marquées pour suppression. La suppression sera retentée lors des EventTicks ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="6cc11-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="6cc11-212">Votre blueprint de graphe d’événements doit maintenant ressembler à la capture d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="6cc11-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Blueprint du graphe d’événements complet pour la gestion des ancres cloud](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="6cc11-214">Recherche d’ancres préexistantes</span><span class="sxs-lookup"><span data-stu-id="6cc11-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="6cc11-215">Les ancres existantes peuvent être créées par des pairs à partir du service Azure Spatial Anchors :</span><span class="sxs-lookup"><span data-stu-id="6cc11-215">Existing anchors can be created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="6cc11-216">Obtenez un identificateur Azure Spatial Anchors pour l’ancre que vous souhaitez détecter.</span><span class="sxs-lookup"><span data-stu-id="6cc11-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="6cc11-217">Un identificateur d’ancre peut être obtenu pour une ancre créée par le même appareil lors d’une session Azure Spatial Anchors précédente.</span><span class="sxs-lookup"><span data-stu-id="6cc11-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="6cc11-218">Il peut également être créé et partagé par des appareils homologues qui interagissent avec le service Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="6cc11-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Blueprint de l’événement personnalisé lié au stockage de l’identificateur d’ancre spatiale Azure, et de la fonction d’obtention de l’identificateur de cloud Azure](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="6cc11-220">Ajoutez un composant **AzureSpatialAnchorsEvent** à votre blueprint de Pawn.</span><span class="sxs-lookup"><span data-stu-id="6cc11-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="6cc11-221">Ce composant vous permet de vous abonner à différents événements Azure Spatial Anchors, tels que des événements appelés quand des ancres spatiales Azure sont localisées.</span><span class="sxs-lookup"><span data-stu-id="6cc11-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Capture d’écran montrant BP_Pawn ouvert dans l’éditeur de blueprint avec les composants et les volets d’informations ouverts également](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="6cc11-223">Abonnez-vous à l’**ASAAnchor Located Delegate** pour le composant **AzureSpatialAnchorsEvent**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="6cc11-224">Le délégué permet à l’application de savoir quand de nouvelles ancres associées au compte Azure Spatial Anchors ont été localisées.</span><span class="sxs-lookup"><span data-stu-id="6cc11-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="6cc11-225">Avec le rappel d’événement, les ancres spatiales Azure créées par les homologues à l’aide de la session Azure Spatial Anchors n’auront pas d’épingles RA créées par défaut.</span><span class="sxs-lookup"><span data-stu-id="6cc11-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="6cc11-226">Pour créer une épingle RA pour l’ancre spatiale Azure détectée, les développeurs peuvent appeler **Create ARPin Around Azure Cloud Spatial Anchor**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Blueprint de l’événement de début de lecture connecté à ASAAnchor Located Delegate](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="6cc11-228">Pour localiser les ancres spatiales Azure créées par des pairs à l’aide du service Azure Spatial Anchors, l’application doit créer un **observateur Azure Spatial Anchors** :</span><span class="sxs-lookup"><span data-stu-id="6cc11-228">To locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="6cc11-229">Vérifiez qu’une session Azure Spatial Anchors est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6cc11-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="6cc11-230">Créez un **AzureSpatialAnchorsLocateCriteria**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-230">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="6cc11-231">Vous pouvez spécifier différents paramètres d’emplacement tels que la distance par rapport à l’utilisateur ou la distance par rapport à une autre ancre.</span><span class="sxs-lookup"><span data-stu-id="6cc11-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="6cc11-232">Déclarez l’identificateur Azure Spatial Anchors recherché dans **AzureSpatialAnchorsLocateCritieria**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-232">Declare the Azure Spatial Anchor identifier you're looking for in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="6cc11-233">Appelez **Create Watcher**.</span><span class="sxs-lookup"><span data-stu-id="6cc11-233">Call **Create Watcher**.</span></span>

![Blueprint de l’événement personnalisé lié au démarrage de l’observateur Azure Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="6cc11-235">L’application commence maintenant à rechercher les ancres spatiales Azure connues du service Azure Spatial Anchors, ce qui signifie que les utilisateurs peuvent localiser les ancres spatiales Azure créées par leurs homologues.</span><span class="sxs-lookup"><span data-stu-id="6cc11-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="6cc11-236">Après avoir localisé l’ancre spatiale Azure, appelez **Stop Watcher** pour arrêter l’observateur Azure Spatial Anchors et nettoyer ses ressources.</span><span class="sxs-lookup"><span data-stu-id="6cc11-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Blueprint de l’appel de la fonction Stop Watcher](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="6cc11-238">Votre blueprint de graphe d’événements final doit maintenant ressembler à la capture d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="6cc11-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Blueprint du graphe d’événements complet pour la gestion des événements liés aux délégués d’ancres](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="6cc11-240">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="6cc11-240">Next Development Checkpoint</span></span>

<span data-ttu-id="6cc11-241">Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="6cc11-241">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="6cc11-242">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="6cc11-242">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="6cc11-243">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="6cc11-243">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="6cc11-244">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="6cc11-244">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6cc11-245">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="6cc11-245">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="6cc11-246">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="6cc11-246">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="6cc11-247">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6cc11-247">Next steps</span></span>
* [<span data-ttu-id="6cc11-248">Ancres spatiales locales</span><span class="sxs-lookup"><span data-stu-id="6cc11-248">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="6cc11-249">Documentation sur les ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="6cc11-249">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="6cc11-250">Fonctionnalités des ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="6cc11-250">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="6cc11-251">Recommandations pour une expérience d’ancrage efficace</span><span class="sxs-lookup"><span data-stu-id="6cc11-251">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)