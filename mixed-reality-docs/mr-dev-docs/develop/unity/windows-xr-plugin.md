---
title: Utilisation du plug-in XR Windows
description: Découvrez comment configurer vos projets Unity avec et sans MRTK à l’aide de la prise en charge de Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performance, Legacy, mrtk, Windows
ms.openlocfilehash: 5d2d27a7ac5ea30515907a08eab6f6bfe70e6686
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906955"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="cace5-104">Utilisation du plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="cace5-104">Using Windows XR plugin</span></span>

<span data-ttu-id="cace5-105">Pour les développeurs ciblant Unity 2020, le plug-in Windows XR permet d’accéder aux fonctionnalités de réalité mixte sur les casques HoloLens 2 et Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="cace5-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="cace5-106">Ce plug-in est également pris en charge sur Unity 2019, bien qu’il existe des incompatibilités connues avec les ancres spatiales Azure lors de l’utilisation de ce plug-in sur cette version.</span><span class="sxs-lookup"><span data-stu-id="cace5-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="cace5-107">Alors que Microsoft et la communauté ont créé des outils open source tels que le [Kit de MRTK (Mixed Reality Toolkit)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) qui configure automatiquement l’environnement WMR, de nombreux développeurs souhaitent créer leurs expériences dès le départ.</span><span class="sxs-lookup"><span data-stu-id="cace5-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="cace5-108">La documentation suivante montre comment configurer correctement un projet pour le développement de réalité mixte, que vous utilisiez MRTK ou non.</span><span class="sxs-lookup"><span data-stu-id="cace5-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="cace5-109">Les paramètres que vous devez modifier sont divisés en deux catégories : les paramètres par projet et les paramètres par scène.</span><span class="sxs-lookup"><span data-stu-id="cace5-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="cace5-110">Configuration de votre projet avec MRTK</span><span class="sxs-lookup"><span data-stu-id="cace5-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="cace5-111">MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales.</span><span class="sxs-lookup"><span data-stu-id="cace5-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="cace5-112">MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.</span><span class="sxs-lookup"><span data-stu-id="cace5-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="cace5-113">Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="cace5-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cace5-114">Essayer nos tutoriels MRTK</span><span class="sxs-lookup"><span data-stu-id="cace5-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="cace5-115">Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="cace5-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="cace5-116">Configuration manuelle sans MRTK</span><span class="sxs-lookup"><span data-stu-id="cace5-116">Manual setup without MRTK</span></span>

<span data-ttu-id="cace5-117">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="cace5-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](images/wmr-config-img-3.png)

<span data-ttu-id="cace5-119">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="cace5-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="cace5-120">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="cace5-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="cace5-121">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="cace5-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="cace5-122">Définissez **Architecture** sur **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="cace5-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="cace5-123">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="cace5-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="cace5-124">Définissez **Build Type** sur **D3D**.</span><span class="sxs-lookup"><span data-stu-id="cace5-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="cace5-125">Définissez **UWP SDK** sur **Latest installed**.</span><span class="sxs-lookup"><span data-stu-id="cace5-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="cace5-126">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="cace5-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](images/wmr-config-img-4.png)

<span data-ttu-id="cace5-128">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :</span><span class="sxs-lookup"><span data-stu-id="cace5-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="cace5-129">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**</span><span class="sxs-lookup"><span data-stu-id="cace5-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="cace5-130">Sélectionnez **installer la gestion des plug-ins XR**</span><span class="sxs-lookup"><span data-stu-id="cace5-130">Select **Install XR Plugin Management**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-5.png)

3. <span data-ttu-id="cace5-132">Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="cace5-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-7.png)

4. <span data-ttu-id="cace5-134">Développez la section **gestion du plug-in XR** et sélectionnez universels onglet Paramètres de la **plateforme Windows** .</span><span class="sxs-lookup"><span data-stu-id="cace5-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="cace5-135">Si vous utilisez Unity 2020 ou une version ultérieure, vous verrez les options permettant de vérifier **OpenXR** ou **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="cace5-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="cace5-136">Vous pouvez choisir l’un ou l’autre Runtime.</span><span class="sxs-lookup"><span data-stu-id="cace5-136">You can choose either runtime.</span></span>  <span data-ttu-id="cace5-137">Si vous développez spécifiquement pour HoloLens 2 ou la réverbération HP G2 et que vous décidez d’essayer le **OpenXR**, sélectionnez la zone OpenXR et passez en revue notre guide pour [utiliser le plug-in OpenXR de réalité mixte pour Unity](./xr-project-setup.md) afin de vous préparer correctement pour ces appareils avant de revenir à ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="cace5-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](./xr-project-setup.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="cace5-138">À partir de Unity 2020 LTS, Microsoft adopte le développement avec OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cace5-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="cace5-139">À mesure que nous migrons vers ce chemin, dans Unity 2021,1, le plug-in Windows XR sera déconseillé et supprimé dans 2021,2, OpenXR le seul chemin pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cace5-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="cace5-140">Vous trouverez plus d’informations dans [utilisation du plug-in OpenXR de la réalité mixte](./xr-project-setup.md).</span><span class="sxs-lookup"><span data-stu-id="cace5-140">You can find more information in [Using the Mixed Reality OpenXR plugin](./xr-project-setup.md).</span></span>

6. <span data-ttu-id="cace5-141">Si vous décidez de choisir le plug-in **Windows Mixed Reality** , cochez toutes les cases et définissez le **mode d’envoi de profondeur** sur une profondeur de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="cace5-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](images/wmr-config-img-8.png)