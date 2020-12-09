---
title: WinRT dans Unreal
description: Vue d’ensemble du plug-in d’audio spatial pour le moteur Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, streaming, communication à distance, réalité mixte, développement, prise en main, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité Windows mixte, casque de réalité virtuelle, WinRT, DLL
ms.openlocfilehash: f86939ee53b51fad1e31d18f810d92c3d20611f8
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926067"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="8fdcd-104">WinRT dans Unreal</span><span class="sxs-lookup"><span data-stu-id="8fdcd-104">WinRT in Unreal</span></span>

<span data-ttu-id="8fdcd-105">Au cours de votre développement HoloLens, vous devrez peut-être écrire une fonctionnalité à l’aide de WinRT.</span><span class="sxs-lookup"><span data-stu-id="8fdcd-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="8fdcd-106">Par exemple, l’ouverture d’une boîte de dialogue de fichier dans une application HoloLens nécessiterait FileSavePicker dans le fichier d’en-tête WinRT/Windows. Storage. Pickrs. h.</span><span class="sxs-lookup"><span data-stu-id="8fdcd-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="8fdcd-107">WinRT est pris en charge dans le système de génération inréel à partir de la version 4,26 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8fdcd-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="8fdcd-108">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="8fdcd-108">Next Development Checkpoint</span></span>

<span data-ttu-id="8fdcd-109">Si vous suivez le parcours de développement inréel que nous avons disposé, vous êtes en train d’explorer les fonctionnalités de la plateforme de réalité mixte et les API.</span><span class="sxs-lookup"><span data-stu-id="8fdcd-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="8fdcd-110">À partir de là, vous pouvez accéder à n’importe quelle [rubrique](unreal-development-overview.md#3-platform-capabilities-and-apis) ou passer directement au déploiement de votre application sur un appareil ou un émulateur.</span><span class="sxs-lookup"><span data-stu-id="8fdcd-110">From here, you can continue to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8fdcd-111">Déploiement sur un appareil</span><span class="sxs-lookup"><span data-stu-id="8fdcd-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="8fdcd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fdcd-112">See also</span></span>
* [<span data-ttu-id="8fdcd-113">API C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="8fdcd-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="8fdcd-114">FileSavePicker, classe</span><span class="sxs-lookup"><span data-stu-id="8fdcd-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="8fdcd-115">Bibliothèques tierces non réelles</span><span class="sxs-lookup"><span data-stu-id="8fdcd-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
