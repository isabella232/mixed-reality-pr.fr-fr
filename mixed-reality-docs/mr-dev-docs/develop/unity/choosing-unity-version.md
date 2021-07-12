---
title: Choix d’une version Unity et d’un plug-in XR
description: restez à jour avec les dernières recommandations en matière de plug-in unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603680"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="3a376-104">Choix d’une version Unity et d’un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="3a376-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="3a376-105">Bien que nous **vous recommandons actuellement d’installer unity 2020,3 LTS avec le dernier plug-in OpenXR de réalité mixte pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.</span><span class="sxs-lookup"><span data-stu-id="3a376-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="3a376-106">Unity 2020,3 LTS (recommandé)</span><span class="sxs-lookup"><span data-stu-id="3a376-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="3a376-107">la configuration d’unity recommandée de Microsoft pour le développement de HoloLens 2 et d’Windows Mixed Reality est **unity 2020,3 LTS avec le dernier plug-in OpenXR de réalité mixte**.</span><span class="sxs-lookup"><span data-stu-id="3a376-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="3a376-108">Vous **devez** utiliser la version de patch Unity 2020.3.8 F1 ou une version ultérieure pour éviter les problèmes de performances connus avec les builds 2020,3 antérieures.</span><span class="sxs-lookup"><span data-stu-id="3a376-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a376-109">unity 2020 ne prend pas en charge le ciblage HoloLens (1er génération).</span><span class="sxs-lookup"><span data-stu-id="3a376-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="3a376-110">Ces casques restent pris en charge dans **[unity 2019 LTS](#unity-20194-lts)** avec des XR intégrés hérités pour le cycle de vie complet de unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="3a376-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="3a376-111">La meilleure façon d’installer et de gérer Unity consiste à utiliser le **concentrateur Unity**:</span><span class="sxs-lookup"><span data-stu-id="3a376-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="3a376-112">Installez <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span><span class="sxs-lookup"><span data-stu-id="3a376-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="3a376-113">Sélectionnez l’onglet **installations** , puis choisissez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="3a376-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="3a376-114">Sélectionnez **unity 2020,3 LTS** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="3a376-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Installation d’Unity Hub-nouvelle version](images/unity-hub-img-01.png)

4. <span data-ttu-id="3a376-116">Vérifiez les composants suivants sous **« plateformes »**:</span><span class="sxs-lookup"><span data-stu-id="3a376-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="3a376-117">**Universal Windows Platform Build Support**</span><span class="sxs-lookup"><span data-stu-id="3a376-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="3a376-118">**Windows Build Support (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="3a376-118">**Windows Build Support (IL2CPP)**</span></span>

![Option Universal Windows Platform Build Support d’Unity](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="3a376-120">Si vous avez déjà installé Unity sans ces options, vous pouvez les ajouter via le menu **« Ajouter des modules »** dans Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="3a376-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Option Windows Build Support d’Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="3a376-122">Une fois Unity 2020,3 installé, commencez à créer un projet ou à mettre à niveau un projet existant à l’aide du plug-in OpenXR de la réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="3a376-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a376-123">Configurer votre projet avec le plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="3a376-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="3a376-124">bien que nous vous recommandons d’utiliser OpenXR pour tous les nouveaux projets, unity 2020,3 LTS prend également en charge le [plug-in XR Windows](xr-project-setup.md?tabs=windowsxr).</span><span class="sxs-lookup"><span data-stu-id="3a376-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="3a376-125">Ce plug-in est entièrement pris en charge, bien qu’il ne reçoive pas de nouvelles fonctionnalités telles que la prise en charge de comptabilité clients 4,0.</span><span class="sxs-lookup"><span data-stu-id="3a376-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="3a376-126">Unity 2019,4 LTS</span><span class="sxs-lookup"><span data-stu-id="3a376-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="3a376-127">Si vous devez utiliser Unity 2019, vous pouvez utiliser **unity 2019 LTS avec des XR intégrées héritées**.</span><span class="sxs-lookup"><span data-stu-id="3a376-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="3a376-128">Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :</span><span class="sxs-lookup"><span data-stu-id="3a376-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a376-129">Configurer votre projet avec des XR intégrées héritées</span><span class="sxs-lookup"><span data-stu-id="3a376-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="3a376-130">Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="3a376-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="3a376-131">Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="3a376-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="3a376-132">Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="3a376-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="3a376-133">si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="3a376-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="3a376-134">Unity 2021,2</span><span class="sxs-lookup"><span data-stu-id="3a376-134">Unity 2021.2</span></span>

<span data-ttu-id="3a376-135">Si vous essayez les builds **2021,2 premières Unity** , commencez avec le [**plug-in OpenXR de la réalité mixte**](xr-project-setup.md?tabs=openxr).</span><span class="sxs-lookup"><span data-stu-id="3a376-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="3a376-136">le plug-in OpenXR est le seul chemin d’accès pour le développement de réalité mixte dans unity 2021,2 et versions ultérieures, car la version unity finale qui prend en charge le plug-in Windows XR était unity 2021,1.</span><span class="sxs-lookup"><span data-stu-id="3a376-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="3a376-137">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="3a376-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="3a376-138">Unity 2018,4 LTS a atteint la fin de la période de prise en charge de deux Long-Term ans d’Unity et ne reçoit plus de mises à jour d’Unity, bien que vos projets continuent de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="3a376-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="3a376-139">Si vous avez un projet Unity 2018, vous devez envisager de planifier une migration vers Unity 2020,3 LTS et le plug-in OpenXR de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="3a376-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>