---
title: Service de suivi perdu
description: Vue d’ensemble du service LostTracking dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144520"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="65302-104">Visualisation de suivi perdue</span><span class="sxs-lookup"><span data-stu-id="65302-104">Lost tracking visualization</span></span>

![Suivi perdu](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="65302-106">Le service d’extension de suivi perdu fournit un visuel animé de style de Shell HoloLens pour l’état de suivi perdu.</span><span class="sxs-lookup"><span data-stu-id="65302-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="65302-107">Utilisation des extensions de suivi perdues</span><span class="sxs-lookup"><span data-stu-id="65302-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="65302-108">Dans le profil MRTK, ajoutez le **service de suivi perdu** aux extensions.</span><span class="sxs-lookup"><span data-stu-id="65302-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="65302-109">Assignez **DefaultLostTrackingServiceProfile** qui comprend **LostTrackingVisualPrefab**.</span><span class="sxs-lookup"><span data-stu-id="65302-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
