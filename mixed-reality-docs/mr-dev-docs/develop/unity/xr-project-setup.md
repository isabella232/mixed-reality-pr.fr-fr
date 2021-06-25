---
title: Configuration de votre configuration XR
description: Restez à jour avec les dernières recommandations de configuration de XR Unity pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906938"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="9044d-104">Configuration de votre configuration XR</span><span class="sxs-lookup"><span data-stu-id="9044d-104">Setting up your XR configuration</span></span>

<span data-ttu-id="9044d-105">Lorsque vous démarrez un nouveau projet Unity, vous disposez de trois options différentes pour gérer vos besoins en matière de XR :</span><span class="sxs-lookup"><span data-stu-id="9044d-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="9044d-106">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="9044d-106">OpenXR plugin</span></span>
* <span data-ttu-id="9044d-107">Plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="9044d-107">Windows XR plugin</span></span>
* <span data-ttu-id="9044d-108">Plug-in XR hérité</span><span class="sxs-lookup"><span data-stu-id="9044d-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="9044d-109">Configuration de votre projet avec MRTK</span><span class="sxs-lookup"><span data-stu-id="9044d-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="9044d-110">MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales.</span><span class="sxs-lookup"><span data-stu-id="9044d-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="9044d-111">MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.</span><span class="sxs-lookup"><span data-stu-id="9044d-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="9044d-112">Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="9044d-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9044d-113">Essayer nos tutoriels MRTK</span><span class="sxs-lookup"><span data-stu-id="9044d-113">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="9044d-114">Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="9044d-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="9044d-115">Utilisation de MRTK avec prise en charge de OpenXR</span><span class="sxs-lookup"><span data-stu-id="9044d-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="9044d-116">MRTK-Unity version 2,7 fournit de meilleures prises en charge pour le plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="9044d-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="9044d-117">Ouvrez de nouveau l' [outil Mixed Reality Feature](welcome-to-mr-feature-tool.md) pour installer la boîte à outils de la réalité mixte, si ce n’est déjà fait.</span><span class="sxs-lookup"><span data-stu-id="9044d-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="9044d-118">La prise en charge de OpenXR est dans le package de **base** .</span><span class="sxs-lookup"><span data-stu-id="9044d-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="9044d-119">Pour [plus d’informations sur la migration vers OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline), consultez la documentation MRTK.</span><span class="sxs-lookup"><span data-stu-id="9044d-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="9044d-120">Lorsque vous effectuez une mise à niveau à partir d’une version antérieure de MRTK antérieure à **2.5.3**, vérifiez que la ligne suivante se trouve dans le fichier **Assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="9044d-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="9044d-121">Cette ligne sera ajoutée par défaut si vous avez démarré avec MRTK 2.5.4 ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="9044d-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="9044d-122">Configuration manuelle sans MRTK</span><span class="sxs-lookup"><span data-stu-id="9044d-122">Manual setup without MRTK</span></span>

<span data-ttu-id="9044d-123">Alors que Microsoft et la communauté ont créé des outils open source tels que le [Kit de MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) qui configure automatiquement l’environnement WMR, de nombreux développeurs souhaitent créer leurs expériences dès le départ.</span><span class="sxs-lookup"><span data-stu-id="9044d-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]