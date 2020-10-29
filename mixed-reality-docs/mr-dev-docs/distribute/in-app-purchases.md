---
title: Achats dans l'application
description: Les achats dans l’application sont pris en charge dans les applications de réalité mixte, mais il existe un certain travail pour les configurer.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: achats dans l’application, hololens
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679843"
---
# <a name="in-app-purchases"></a><span data-ttu-id="d832d-104">Achats dans l'application</span><span class="sxs-lookup"><span data-stu-id="d832d-104">In-app purchases</span></span>

<span data-ttu-id="d832d-105">Les achats dans l’application sont pris en charge dans HoloLens, mais il existe un certain travail pour les configurer.</span><span class="sxs-lookup"><span data-stu-id="d832d-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="d832d-106">Pour tirer parti de la fonctionnalité d’achat d’applications, vous devez :</span><span class="sxs-lookup"><span data-stu-id="d832d-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="d832d-107">Créer une [vue 2D](../design/app-views.md) XAML pour qu’elle apparaisse en tant que ardoise</span><span class="sxs-lookup"><span data-stu-id="d832d-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="d832d-108">Basculez vers celui-ci pour activer le placement, ce qui laisse la vue immersive</span><span class="sxs-lookup"><span data-stu-id="d832d-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="d832d-109">Appeler l’API : await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="d832d-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="d832d-110">Cette API affiche la fenêtre contextuelle du système d’exploitation Windows qui affiche le nom, la description et le prix de l’achat dans l’application.</span><span class="sxs-lookup"><span data-stu-id="d832d-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="d832d-111">L’utilisateur peut ensuite choisir des options d’achat.</span><span class="sxs-lookup"><span data-stu-id="d832d-111">The user can then choose purchase options.</span></span> <span data-ttu-id="d832d-112">Une fois l’action terminée, l’application doit présenter une interface utilisateur qui permet à l’utilisateur de revenir à sa [vue immersive](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="d832d-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="d832d-113">Pour les applications ciblant des casques immersifs de la réalité Windows mixte basés sur le bureau, il n’est pas nécessaire de basculer manuellement vers une vue XAML avant d’appeler l’API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="d832d-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
