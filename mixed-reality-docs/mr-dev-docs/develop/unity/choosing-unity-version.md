---
title: Choix d’une version Unity et d’un plug-in XR
description: Restez à jour avec les dernières recommandations en matière de plug-in Unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394412"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="3f412-104">Choix d’une version Unity et d’un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="3f412-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="3f412-105">Bien que nous **vous recommandons actuellement d’installer unity 2019,4 LTS et d’utiliser des XR intégrées héritées pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.</span><span class="sxs-lookup"><span data-stu-id="3f412-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="3f412-106">Unity 2019,4 LTS (recommandé)</span><span class="sxs-lookup"><span data-stu-id="3f412-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="3f412-107">La configuration d’Unity recommandée de Microsoft pour le développement HoloLens 2 et Windows Mixed Reality est **unity 2019,4 LTS à l’aide** de la prise en charge XR intégrée héritée.</span><span class="sxs-lookup"><span data-stu-id="3f412-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="3f412-108">La meilleure façon d’installer et de gérer Unity consiste à utiliser <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="3f412-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="3f412-109">Une fois l’installation terminée, ouvrez Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="3f412-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="3f412-110">Sélectionnez l’onglet **installations** , puis choisissez **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="3f412-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="3f412-111">Sélectionnez Unity 2019,4 LTS, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="3f412-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity Hub instal New version](images/unity-hub-img-2019.png)

3. <span data-ttu-id="3f412-113">Vérifiez les composants suivants sous **« plateformes »**</span><span class="sxs-lookup"><span data-stu-id="3f412-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="3f412-114">**Universal Windows Platform Build Support**</span><span class="sxs-lookup"><span data-stu-id="3f412-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="3f412-115">**Windows Build Support (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="3f412-115">**Windows Build Support (IL2CPP)**</span></span>

![Option Universal Windows Platform Build Support d’Unity](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="3f412-117">Si vous avez installé Unity sans ces options, vous pouvez les ajouter via le menu **Ajouter des modules** dans Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="3f412-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Option Windows Build Support d’Unity](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="3f412-119">Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :</span><span class="sxs-lookup"><span data-stu-id="3f412-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f412-120">Configurer des XR intégrées héritées</span><span class="sxs-lookup"><span data-stu-id="3f412-120">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="3f412-121">Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="3f412-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="3f412-122">Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="3f412-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="3f412-123">Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="3f412-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="3f412-124">Si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans Unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de Unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="3f412-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="3f412-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="3f412-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="3f412-126">Si vous utilisez **unity 2020,3 LTS**, la recommandation actuelle de Microsoft est le **plug-in OpenXR de réalité mixte** le plus récent.</span><span class="sxs-lookup"><span data-stu-id="3f412-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="3f412-127">Vous devez utiliser la version de patch Unity 2020.3.8 F1 ou une version ultérieure pour éviter les problèmes de performances connus avec les builds 2020,3 antérieures.</span><span class="sxs-lookup"><span data-stu-id="3f412-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="3f412-128">Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="3f412-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="3f412-129">Cela vous permet d’écrire du code de test de positionnement une fois qui s’étend sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="3f412-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="3f412-130">Toutefois, il existe des problèmes connus qui affectent les projets LTS Unity 2020 :</span><span class="sxs-lookup"><span data-stu-id="3f412-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="3f412-131">Le pipeline de rendu universel (URP) 10.5.0 ou antérieur présente des pénalités en matière de performances sur les appareils HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f412-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="3f412-132">Si vous choisissez de démarrer un nouveau projet dans Unity 2020 aujourd’hui, veillez à suivre les semaines à venir pour les builds Unity et les packages URP mis à jour avant d’expédier votre application.</span><span class="sxs-lookup"><span data-stu-id="3f412-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="3f412-133">Cela permet de s’assurer que vos utilisateurs connaissent une stabilité d’hologramme appropriée.</span><span class="sxs-lookup"><span data-stu-id="3f412-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f412-134">Utilisation du plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="3f412-134">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="3f412-135">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="3f412-135">Unity 2021.1</span></span>

<span data-ttu-id="3f412-136">Si vous essayez les builds **2021,1 premières Unity** , vous devez avancer jusqu’au **plug-in OpenXR**, car le plug-in Windows XR est déconseillé ici.</span><span class="sxs-lookup"><span data-stu-id="3f412-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="3f412-137">À partir de Unity 2021,2, le plug-in OpenXR sera le seul chemin pour le développement de la réalité mixte, car le plug-in Windows XR ne sera plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3f412-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="3f412-138">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="3f412-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="3f412-139">Si vous disposez déjà d’un projet utilisant Unity 2018,4 LTS, votre moteur Unity continue d’être pris en charge pendant 2 ans après sa sortie.</span><span class="sxs-lookup"><span data-stu-id="3f412-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="3f412-140">Unity 2018 LTS atteindra la fin du service au printemps de 2021.</span><span class="sxs-lookup"><span data-stu-id="3f412-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>