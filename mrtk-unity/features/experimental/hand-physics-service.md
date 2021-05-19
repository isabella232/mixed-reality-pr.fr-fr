---
title: Main service extension physique
description: Description services d’extension physique.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143431"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="85bf9-104">Main services d’extension physique</span><span class="sxs-lookup"><span data-stu-id="85bf9-104">Hand physics extension services</span></span>

<span data-ttu-id="85bf9-105">La main physique service Active les événements de collision de corps rigides et les interactions avec les mains articulées.</span><span class="sxs-lookup"><span data-stu-id="85bf9-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="85bf9-106">Prise en main du service d’extension physique de main</span><span class="sxs-lookup"><span data-stu-id="85bf9-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="85bf9-107">Ajoutez le service physique de la main à la liste des services d’extension et utilisez le profil par défaut.</span><span class="sxs-lookup"><span data-stu-id="85bf9-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="85bf9-108">Une fois activé, utilisez la propriété IsTrigger de l’un des conflits pour recevoir les événements de collision des 10 chiffres (et des palmiers s’ils sont activés).</span><span class="sxs-lookup"><span data-stu-id="85bf9-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="85bf9-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="85bf9-109">Prerequisites</span></span>

- <span data-ttu-id="85bf9-110">Activation du service d’extension</span><span class="sxs-lookup"><span data-stu-id="85bf9-110">Enabled the extension service</span></span>
- <span data-ttu-id="85bf9-111">Assignez un Prefab approprié à la jointure Finger/Palm.</span><span class="sxs-lookup"><span data-stu-id="85bf9-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="85bf9-112">Recommandations</span><span class="sxs-lookup"><span data-stu-id="85bf9-112">Recommendations</span></span>

<span data-ttu-id="85bf9-113">Si le service utilise par défaut la couche « par défaut », il est recommandé d’utiliser une couche distincte pour les objets HandPhysics.</span><span class="sxs-lookup"><span data-stu-id="85bf9-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="85bf9-114">Dans le cas contraire, il peut y avoir des conflits indésirables et/ou des raycasts inexacts.</span><span class="sxs-lookup"><span data-stu-id="85bf9-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
