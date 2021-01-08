---
title: Achats dans l'application
description: Apprenez à utiliser des achats dans l’application dans vos applications de réalité mixte avec des vues XAML 2D et une fenêtre contextuelle du système d’exploitation Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: achats dans l’application, hololens, XAML, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: a87cc68f67def1d46a3a6ba352e723d356f51fa2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008669"
---
# <a name="in-app-purchases"></a><span data-ttu-id="bebcf-104">Achats dans l'application</span><span class="sxs-lookup"><span data-stu-id="bebcf-104">In-app purchases</span></span>

<span data-ttu-id="bebcf-105">Les achats dans l’application sont pris en charge dans HoloLens, mais il existe un certain travail pour les configurer.</span><span class="sxs-lookup"><span data-stu-id="bebcf-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="bebcf-106">Pour utiliser la fonctionnalité dans l’achat d’applications, vous devez :</span><span class="sxs-lookup"><span data-stu-id="bebcf-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="bebcf-107">Créer une [vue 2D](../design/app-views.md) XAML pour qu’elle apparaisse en tant que ardoise</span><span class="sxs-lookup"><span data-stu-id="bebcf-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="bebcf-108">Basculez vers celui-ci pour activer le placement, ce qui laisse la vue immersive</span><span class="sxs-lookup"><span data-stu-id="bebcf-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="bebcf-109">Appeler l’API : await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="bebcf-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="bebcf-110">Cette API affiche la fenêtre contextuelle du système d’exploitation Windows qui affiche le nom, la description et le prix de l’achat dans l’application.</span><span class="sxs-lookup"><span data-stu-id="bebcf-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="bebcf-111">L’utilisateur peut ensuite choisir des options d’achat.</span><span class="sxs-lookup"><span data-stu-id="bebcf-111">The user can then choose purchase options.</span></span> <span data-ttu-id="bebcf-112">Une fois l’action terminée, l’application doit présenter l’interface utilisateur, ce qui permet à l’utilisateur de revenir à sa [vue immersive](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="bebcf-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="bebcf-113">Pour les applications ciblant des casques immersifs de la réalité Windows mixte basés sur le bureau, il n’est pas nécessaire de basculer manuellement vers une vue XAML avant d’appeler l’API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="bebcf-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
