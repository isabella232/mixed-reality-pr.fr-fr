---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906939"
---
# <a name="openxr"></a>[<span data-ttu-id="0d32e-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="0d32e-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="0d32e-102">Le plug-in OpenXR de réalité mixte est **recommandé par Microsoft** pour unity 2020 LTS ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0d32e-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="0d32e-103">À mesure que de nouvelles fonctionnalités sont développées à l’avenir, elles sont uniquement incluses dans le plug-in OpenXR de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="0d32e-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="0d32e-104">Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="0d32e-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="0d32e-105">Cela vous permet d’écrire le code Raycasting une seule fois qui s’étend ensuite sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="0d32e-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0d32e-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0d32e-106">Prerequisites</span></span> 

* <span data-ttu-id="0d32e-107">[Outils les plus récents pour le développement HoloLens 2](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="0d32e-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="0d32e-108">Dernière Unity 2020,3 LTS, (nous recommandons 2020.3.8 F1 ou supérieur)</span><span class="sxs-lookup"><span data-stu-id="0d32e-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="0d32e-109">Versions minimales</span><span class="sxs-lookup"><span data-stu-id="0d32e-109">Minimum versions</span></span>

<span data-ttu-id="0d32e-110">Les instructions de cette page vous configurent avec les exigences les plus récentes et les OpenXR les plus importantes indiquées ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="0d32e-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="0d32e-111">Dernier plug-in OpenXR Unity, (nous vous recommandons 1,2 ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="0d32e-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="0d32e-112">Dernier plug-in OpenXR de réalité mixte, (nous vous recommandons la version 1.0.0 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="0d32e-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="0d32e-113">**(Facultatif)** Dernière version de MRTK, (nous recommandons la version 2,7 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="0d32e-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="0d32e-114">**(Facultatif)** Dernier package de pipeline de rendu universel, (nous recommandons la version 10.5.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="0d32e-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="0d32e-115">Si vous générez des applications VR sur un PC Windows, le plug-in OpenXR de réalité mixte n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0d32e-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="0d32e-116">Toutefois, vous souhaiterez installer le plug-in si vous personnalisez le mappage de contrôleur pour les contrôleurs de reréverbérations de HP ou si vous créez des applications qui fonctionnent à la fois sur les casques HoloLens 2 et VR.</span><span class="sxs-lookup"><span data-stu-id="0d32e-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="0d32e-117">XR Windows</span><span class="sxs-lookup"><span data-stu-id="0d32e-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="0d32e-118">Microsoft ne recommande pas l’utilisation du plug-in XR Windows pour les nouveaux projets dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="0d32e-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="0d32e-119">Toutefois, si vous utilisez Unity 2019 et que vous avez besoin de l’unité de 2,0 base de ARCore/ARKit pour la compatibilité avec les appareils/, ce plug-in active la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="0d32e-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d32e-120">L’utilisation de ce plug-in Unity 2019 ne prend pas en charge les ancres spatiales Azure.</span><span class="sxs-lookup"><span data-stu-id="0d32e-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="0d32e-121">XR antérieur</span><span class="sxs-lookup"><span data-stu-id="0d32e-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="0d32e-122">Si vous êtes toujours sur Unity 2019 ou une version antérieure, Microsoft recommande d’utiliser la prise en charge XR intégrée héritée.</span><span class="sxs-lookup"><span data-stu-id="0d32e-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="0d32e-123">Alors que le plug-in XR Windows est fonctionnel sur Unity 2019, cela n’est pas recommandé, car les ancres spatiales Azure ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0d32e-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>