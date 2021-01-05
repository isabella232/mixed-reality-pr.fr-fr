---
title: Achats dans l'application
description: Les achats dans l’application sont pris en charge dans les applications de réalité mixte, mais il existe un certain travail pour les configurer.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: achats dans l’application, hololens, XAML, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 905c1be72bf2a3d6fa167cab68a4cb71e6538acc
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757778"
---
# <a name="in-app-purchases"></a><span data-ttu-id="80e4d-104">Achats dans l'application</span><span class="sxs-lookup"><span data-stu-id="80e4d-104">In-app purchases</span></span>

<span data-ttu-id="80e4d-105">Les achats dans l’application sont pris en charge dans HoloLens, mais il existe un certain travail pour les configurer.</span><span class="sxs-lookup"><span data-stu-id="80e4d-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="80e4d-106">Pour utiliser la fonctionnalité dans l’achat d’applications, vous devez :</span><span class="sxs-lookup"><span data-stu-id="80e4d-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="80e4d-107">Créer une [vue 2D](../design/app-views.md) XAML pour qu’elle apparaisse en tant que ardoise</span><span class="sxs-lookup"><span data-stu-id="80e4d-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="80e4d-108">Basculez vers celui-ci pour activer le placement, ce qui laisse la vue immersive</span><span class="sxs-lookup"><span data-stu-id="80e4d-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="80e4d-109">Appeler l’API : await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="80e4d-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="80e4d-110">Cette API affiche la fenêtre contextuelle du système d’exploitation Windows qui affiche le nom, la description et le prix de l’achat dans l’application.</span><span class="sxs-lookup"><span data-stu-id="80e4d-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="80e4d-111">L’utilisateur peut ensuite choisir des options d’achat.</span><span class="sxs-lookup"><span data-stu-id="80e4d-111">The user can then choose purchase options.</span></span> <span data-ttu-id="80e4d-112">Une fois l’action terminée, l’application doit présenter l’interface utilisateur, ce qui permet à l’utilisateur de revenir à sa [vue immersive](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="80e4d-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="80e4d-113">Pour les applications ciblant des casques immersifs de la réalité Windows mixte basés sur le bureau, il n’est pas nécessaire de basculer manuellement vers une vue XAML avant d’appeler l’API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="80e4d-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
