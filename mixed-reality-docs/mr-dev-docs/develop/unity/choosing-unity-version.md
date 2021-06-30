---
title: Choix d’une version Unity et d’un plug-in XR
description: Restez à jour avec les dernières recommandations en matière de plug-in Unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080696"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="ac5a7-104">Choix d’une version Unity et d’un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="ac5a7-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="ac5a7-105">Bien que nous **vous recommandons actuellement d’installer unity 2020,3 LTS avec le dernier plug-in OpenXR de réalité mixte pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="ac5a7-106">Unity 2020,3 LTS (recommandé)</span><span class="sxs-lookup"><span data-stu-id="ac5a7-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="ac5a7-107">La configuration d’Unity recommandée de Microsoft pour le développement HoloLens 2 et Windows Mixed Reality est **unity 2020,3 LTS avec le plug-in OpenXR de réalité mixte le plus récent**.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="ac5a7-108">Vous devez utiliser la version de patch Unity 2020.3.8 F1 ou une version ultérieure pour éviter les problèmes de performances connus avec les builds 2020,3 antérieures.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac5a7-109">Unity 2020 ne prend pas en charge le ciblage HoloLens (1re génération).</span><span class="sxs-lookup"><span data-stu-id="ac5a7-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="ac5a7-110">Ces casques restent pris en charge dans **[unity 2019 LTS](#unity-20194-lts)** avec des XR intégrés hérités pour le cycle de vie complet de unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="ac5a7-111">Le rendu à distance Azure n’a pas encore fourni une version mise à jour prenant en charge Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-111">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="ac5a7-112">Si votre projet Unity utilise le rendu distant Azure, nous vous recommandons de ne pas mettre à niveau votre projet vers Unity 2020 jusqu’à ce qu’un package mis à jour soit disponible.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-112">If your Unity project uses Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until an updated package is available.</span></span>

<span data-ttu-id="ac5a7-113"><a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a> est le meilleur moyen d’installer et de gérer Unity.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-113">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="ac5a7-114">Une fois l’installation terminée, ouvrez Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="ac5a7-114">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="ac5a7-115">Sélectionnez l’onglet **installations** , puis choisissez **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="ac5a7-115">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="ac5a7-116">Sélectionnez Unity 2020,3 LTS, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="ac5a7-116">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity Hub instal New version](images/unity-hub-img-01.png)

3. <span data-ttu-id="ac5a7-118">Vérifiez les composants suivants sous **« plateformes »**</span><span class="sxs-lookup"><span data-stu-id="ac5a7-118">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="ac5a7-119">**Universal Windows Platform Build Support**</span><span class="sxs-lookup"><span data-stu-id="ac5a7-119">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="ac5a7-120">**Windows Build Support (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="ac5a7-120">**Windows Build Support (IL2CPP)**</span></span>

![Option Universal Windows Platform Build Support d’Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="ac5a7-122">Si vous avez installé Unity sans ces options, vous pouvez les ajouter via le menu **Ajouter des modules** dans Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="ac5a7-122">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Option Windows Build Support d’Unity](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac5a7-124">Utilisation du plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="ac5a7-124">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="ac5a7-125">Bien que nous vous recommandons d’utiliser OpenXR pour tous les nouveaux projets, Unity 2020,3 LTS prend également en charge le [plug-in XR de Windows](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span><span class="sxs-lookup"><span data-stu-id="ac5a7-125">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="ac5a7-126">Ce plug-in est entièrement pris en charge, bien qu’il ne reçoive pas de nouvelles fonctionnalités telles que la prise en charge de comptabilité clients 4,0.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-126">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="ac5a7-127">Unity 2019,4 LTS</span><span class="sxs-lookup"><span data-stu-id="ac5a7-127">Unity 2019.4 LTS</span></span>

<span data-ttu-id="ac5a7-128">Si vous devez utiliser Unity 2019, vous pouvez utiliser **unity 2019 LTS avec des XR intégrées héritées**.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-128">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="ac5a7-129">Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :</span><span class="sxs-lookup"><span data-stu-id="ac5a7-129">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac5a7-130">Configurer des XR intégrées héritées</span><span class="sxs-lookup"><span data-stu-id="ac5a7-130">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="ac5a7-131">Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-131">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="ac5a7-132">Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-132">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="ac5a7-133">Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-133">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="ac5a7-134">Si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans Unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de Unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-134">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="ac5a7-135">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="ac5a7-135">Unity 2021.1</span></span>

<span data-ttu-id="ac5a7-136">Si vous essayez les builds **2021,1 premières Unity** , vous devez avancer jusqu’au **plug-in OpenXR**, car le plug-in Windows XR est déconseillé ici.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="ac5a7-137">À partir de Unity 2021,2, le plug-in OpenXR sera le seul chemin pour le développement de la réalité mixte, car le plug-in Windows XR ne sera plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="ac5a7-138">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="ac5a7-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="ac5a7-139">Si vous disposez déjà d’un projet utilisant Unity 2018,4 LTS, votre moteur Unity continue d’être pris en charge pendant 2 ans après sa sortie.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="ac5a7-140">Unity 2018 LTS atteindra la fin du service au printemps de 2021.</span><span class="sxs-lookup"><span data-stu-id="ac5a7-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
