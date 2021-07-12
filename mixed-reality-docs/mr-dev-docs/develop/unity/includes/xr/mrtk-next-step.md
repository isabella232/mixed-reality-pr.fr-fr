---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603710"
---
# <a name="openxr"></a>[<span data-ttu-id="0797f-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="0797f-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="0797f-102">Pour commencer à utiliser un **nouveau projet Unity** à l’aide de MRTK, commencez à l’étape 2 dans le didacticiel MRTK :</span><span class="sxs-lookup"><span data-stu-id="0797f-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0797f-103">Configurer un nouveau projet OpenXR avec MRTK</span><span class="sxs-lookup"><span data-stu-id="0797f-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="0797f-104">Si vous effectuez la mise à niveau d’un **projet MRTK existant vers OpenXR**, vous devez d’abord mettre à niveau MRTK-Unity vers la dernière version (version 2.7.2 ou ultérieure) pour obtenir des correctifs clés pour la compatibilité avec le plug-in de réalité mixte OpenXR.</span><span class="sxs-lookup"><span data-stu-id="0797f-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="0797f-105">Utilisez l' [outil de la fonctionnalité de réalité mixte](../../welcome-to-mr-feature-tool.md) pour effectuer une mise à niveau vers la dernière version de MRTK, puis suivez les [étapes de configuration manuelle de OpenXR ci-dessous](#manual-setup-without-mrtk).</span><span class="sxs-lookup"><span data-stu-id="0797f-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="0797f-106">Pour [plus d’informations sur la migration d’un projet MRTK existant vers OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline), consultez la documentation MRTK.</span><span class="sxs-lookup"><span data-stu-id="0797f-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="0797f-107">Lorsque vous effectuez une mise à niveau à partir d’une version antérieure de MRTK antérieure à **2.5.3**, vérifiez que la ligne suivante se trouve dans le fichier **Assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="0797f-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="0797f-108">Cette ligne sera ajoutée par défaut si vous avez démarré avec MRTK 2.5.4 ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="0797f-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="0797f-109">Windows XR</span><span class="sxs-lookup"><span data-stu-id="0797f-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="0797f-110">Pour commencer à utiliser un **nouveau projet Unity** à l’aide de MRTK, commencez à l’étape 2 dans le didacticiel MRTK :</span><span class="sxs-lookup"><span data-stu-id="0797f-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0797f-111">configurer un nouveau projet Windows XR avec MRTK</span><span class="sxs-lookup"><span data-stu-id="0797f-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="0797f-112">XR antérieur</span><span class="sxs-lookup"><span data-stu-id="0797f-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="0797f-113">Pour commencer à utiliser un **nouveau projet Unity** à l’aide de MRTK, commencez à l’étape 2 dans le didacticiel MRTK :</span><span class="sxs-lookup"><span data-stu-id="0797f-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0797f-114">Configurer un nouveau projet XR hérité avec MRTK</span><span class="sxs-lookup"><span data-stu-id="0797f-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)