---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603709"
---
# <a name="openxr"></a>[<span data-ttu-id="78218-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="78218-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="78218-102">Le plug-in OpenXR de réalité mixte est **recommandé par Microsoft** pour **Unity 2020 LTS** ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="78218-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="78218-103">À mesure que de nouvelles fonctionnalités sont développées à l’avenir, elles sont uniquement incluses dans le plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="78218-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="78218-104">Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="78218-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="78218-105">cela vous permet d’écrire le code raycasting une seule fois qui s’étend sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="78218-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="78218-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="78218-106">Prerequisites</span></span> 

* <span data-ttu-id="78218-107">[outils les plus récents pour le développement de HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="78218-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="78218-108">Dernière Unity 2020,3 LTS : version 2020.3.8 F1 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="78218-109">Versions de package recommandées</span><span class="sxs-lookup"><span data-stu-id="78218-109">Recommended package versions</span></span>

<span data-ttu-id="78218-110">les instructions de cette page vous permettent de configurer les packages OpenXR core unity nécessaires au déploiement d’applications HoloLens 2 ou Windows Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="78218-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="78218-111">Plug-in Unity OpenXR : version 1,2 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="78218-112">Plug-in OpenXR de réalité mixte : version 1.0.0 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="78218-113">Si vous utilisez les packages suivants dans votre projet, vous devez vous assurer que vous utilisez au moins les versions minimales listées ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="78218-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="78218-114">MRTK : version 2.7.2 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="78218-115">AR-base : version 4.1.1 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="78218-116">Pipeline de rendu universel (URP) : version 10.5.1 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="78218-117">Ancres spatiales Azure : version 2,10 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="78218-118">Rendu distant Azure : version 1.0.15 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="78218-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="78218-119">si vous créez des applications VR sur Windows PC, le plug-in OpenXR de réalité mixte n’est pas strictement requis.</span><span class="sxs-lookup"><span data-stu-id="78218-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="78218-120">toutefois, vous souhaiterez installer le plug-in si vous configurez des liaisons d’entrée pour les contrôleurs de réinitialisation HP ou si vous créez des applications qui fonctionnent sur les écouteurs HoloLens 2 et VR.</span><span class="sxs-lookup"><span data-stu-id="78218-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="78218-121">Windows XR</span><span class="sxs-lookup"><span data-stu-id="78218-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="78218-122">Microsoft ne recommande pas l’utilisation du plug-in Windows XR pour les nouveaux projets dans unity 2020.</span><span class="sxs-lookup"><span data-stu-id="78218-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="78218-123">Au lieu de cela, vous devez utiliser le plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="78218-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="78218-124">Toutefois, si vous utilisez Unity 2019 et que vous avez besoin de l’unité de 2,0 base de ARCore/ARKit pour la compatibilité avec les appareils/, ce plug-in active la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="78218-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78218-125">L’utilisation de ce plug-in Unity 2019 n’est pas compatible avec les ancres spatiales Azure.</span><span class="sxs-lookup"><span data-stu-id="78218-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="78218-126">XR antérieur</span><span class="sxs-lookup"><span data-stu-id="78218-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="78218-127">Si vous êtes toujours sur **unity 2019** ou une version antérieure, Microsoft recommande d’utiliser la **prise en charge XR intégrée héritée**.</span><span class="sxs-lookup"><span data-stu-id="78218-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="78218-128">alors que le plug-in Windows XR est fonctionnel sur unity 2019, ce n’est pas recommandé, car ce plug-in n’est pas compatible avec les ancres spatiales Azure sur unity 2019.</span><span class="sxs-lookup"><span data-stu-id="78218-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="78218-129">Si vous démarrez un nouveau projet, nous vous recommandons d' [installer unity 2020](../../choosing-unity-version.md) à la place et d’utiliser le plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="78218-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>