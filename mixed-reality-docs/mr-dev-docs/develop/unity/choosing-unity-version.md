---
title: Choix d’une version Unity et d’un plug-in XR
description: Restez à jour avec les dernières recommandations en matière de plug-in Unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921422"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="4ad46-104">Choix d’une version Unity et d’un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="4ad46-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="4ad46-105">Bien que nous **vous recommandons actuellement d’installer unity 2020,3 LTS avec le dernier plug-in OpenXR de réalité mixte pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad46-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="4ad46-106">Unity 2020,3 LTS (recommandé)</span><span class="sxs-lookup"><span data-stu-id="4ad46-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="4ad46-107">La configuration d’Unity recommandée de Microsoft pour le développement HoloLens 2 et Windows Mixed Reality est **unity 2020,3 LTS avec le plug-in OpenXR de réalité mixte le plus récent**.</span><span class="sxs-lookup"><span data-stu-id="4ad46-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="4ad46-108">Vous devez utiliser la version de patch Unity 2020.3.8 F1 ou une version ultérieure pour éviter les problèmes de performances connus avec les builds 2020,3 antérieures.</span><span class="sxs-lookup"><span data-stu-id="4ad46-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4ad46-109">Unity 2020 ne prend pas en charge le ciblage HoloLens (1re génération).</span><span class="sxs-lookup"><span data-stu-id="4ad46-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="4ad46-110">Ces casques restent pris en charge dans **[unity 2019 LTS](#unity-20194-lts)** avec des XR intégrés hérités pour le cycle de vie complet de unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="4ad46-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="4ad46-111">Certains packages ne sont pas encore compatibles avec les projets de réalité mixte dans Unity 2020 LTS :</span><span class="sxs-lookup"><span data-stu-id="4ad46-111">Some packages are not yet compatible with mixed reality projects in Unity 2020 LTS:</span></span>
> 
> * <span data-ttu-id="4ad46-112">Le pipeline de rendu universel (URP) 10.5.0 ou antérieur présente un problème de performance connu sur les appareils HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4ad46-112">The Universal Rendering Pipeline (URP) 10.5.0 or older has a known performance issue on HoloLens 2 devices.</span></span> <span data-ttu-id="4ad46-113">_(résolu dans la prochaine version de URP)_</span><span class="sxs-lookup"><span data-stu-id="4ad46-113">_(fixed in the next URP release)_</span></span>
> * <span data-ttu-id="4ad46-114">Le rendu à distance Azure n’a pas encore fourni une version mise à jour prenant en charge Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="4ad46-114">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="4ad46-115">Si votre projet Unity utilise le pipeline de rendu universel ou le rendu distant Azure, nous vous recommandons de ne pas mettre à niveau votre projet vers Unity 2020 jusqu’à ce que les packages mis à jour soient disponibles.</span><span class="sxs-lookup"><span data-stu-id="4ad46-115">If your Unity project uses the Universal Rendering Pipeline or Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until updated packages are available.</span></span>

<span data-ttu-id="4ad46-116"><a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a> est le meilleur moyen d’installer et de gérer Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad46-116">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="4ad46-117">Une fois l’installation terminée, ouvrez Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="4ad46-117">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="4ad46-118">Sélectionnez l’onglet **installations** , puis choisissez **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="4ad46-118">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="4ad46-119">Sélectionnez Unity 2020,3 LTS, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="4ad46-119">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity Hub instal New version](images/unity-hub-img-01.png)

3. <span data-ttu-id="4ad46-121">Vérifiez les composants suivants sous **« plateformes »**</span><span class="sxs-lookup"><span data-stu-id="4ad46-121">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="4ad46-122">**Universal Windows Platform Build Support**</span><span class="sxs-lookup"><span data-stu-id="4ad46-122">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="4ad46-123">**Windows Build Support (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="4ad46-123">**Windows Build Support (IL2CPP)**</span></span>

![Option Universal Windows Platform Build Support d’Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="4ad46-125">Si vous avez installé Unity sans ces options, vous pouvez les ajouter via le menu **Ajouter des modules** dans Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="4ad46-125">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Option Windows Build Support d’Unity](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ad46-127">Utilisation du plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="4ad46-127">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="4ad46-128">Bien que nous vous recommandons d’utiliser OpenXR pour tous les nouveaux projets, Unity 2020,3 LTS prend également en charge le [plug-in XR de Windows](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span><span class="sxs-lookup"><span data-stu-id="4ad46-128">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="4ad46-129">Ce plug-in est entièrement pris en charge, bien qu’il ne reçoive pas de nouvelles fonctionnalités telles que la prise en charge de comptabilité clients 4,0.</span><span class="sxs-lookup"><span data-stu-id="4ad46-129">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="4ad46-130">Unity 2019,4 LTS</span><span class="sxs-lookup"><span data-stu-id="4ad46-130">Unity 2019.4 LTS</span></span>

<span data-ttu-id="4ad46-131">Si vous devez utiliser Unity 2019, vous pouvez utiliser **unity 2019 LTS avec des XR intégrées héritées**.</span><span class="sxs-lookup"><span data-stu-id="4ad46-131">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="4ad46-132">Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :</span><span class="sxs-lookup"><span data-stu-id="4ad46-132">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ad46-133">Configurer des XR intégrées héritées</span><span class="sxs-lookup"><span data-stu-id="4ad46-133">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="4ad46-134">Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="4ad46-134">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="4ad46-135">Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="4ad46-135">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="4ad46-136">Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="4ad46-136">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="4ad46-137">Si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans Unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de Unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="4ad46-137">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="4ad46-138">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="4ad46-138">Unity 2021.1</span></span>

<span data-ttu-id="4ad46-139">Si vous essayez les builds **2021,1 premières Unity** , vous devez avancer jusqu’au **plug-in OpenXR**, car le plug-in Windows XR est déconseillé ici.</span><span class="sxs-lookup"><span data-stu-id="4ad46-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="4ad46-140">À partir de Unity 2021,2, le plug-in OpenXR sera le seul chemin pour le développement de la réalité mixte, car le plug-in Windows XR ne sera plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4ad46-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="4ad46-141">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="4ad46-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="4ad46-142">Si vous disposez déjà d’un projet utilisant Unity 2018,4 LTS, votre moteur Unity continue d’être pris en charge pendant 2 ans après sa sortie.</span><span class="sxs-lookup"><span data-stu-id="4ad46-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="4ad46-143">Unity 2018 LTS atteindra la fin du service au printemps de 2021.</span><span class="sxs-lookup"><span data-stu-id="4ad46-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
