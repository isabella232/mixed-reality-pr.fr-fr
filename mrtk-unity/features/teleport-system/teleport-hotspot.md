---
title: Point d’accès de télérelais
description: Documentation sur le composant HotSpot de télérelais dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, hololens, hololens 2, réalité mixte, développement, MRTK, système de téléchaud, point d’accès de
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 2d6160570b43ca931d46f4ec04c604b53b18d731
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647042"
---
# <a name="teleport-hotspot"></a><span data-ttu-id="feb1d-104">Point d’accès de télérelais</span><span class="sxs-lookup"><span data-stu-id="feb1d-104">Teleport Hotspot</span></span>

<span data-ttu-id="feb1d-105">La zone réactive de télétentative est un composant que vous pouvez ajouter à votre gameobject pour vous assurer que l’utilisateur est dans une certaine position et orientation lorsqu’il se téléporte à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="feb1d-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="feb1d-106">Utilisation</span><span class="sxs-lookup"><span data-stu-id="feb1d-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="feb1d-107">Comment créer une zone réactive de télétentative</span><span class="sxs-lookup"><span data-stu-id="feb1d-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="feb1d-108">Pour créer une zone réactive de télétentative, ajoutez le composant TeleportHotspot à un objet qui a également un composant de collision.</span><span class="sxs-lookup"><span data-stu-id="feb1d-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Composant HotSpot de téléporte](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="feb1d-110">À présent, l’indicateur du pointeur de téléchargement change de couleur lorsqu’il est dirigé sur un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="feb1d-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="feb1d-111">Lorsque l’action de téléchargement est terminée sur la zone réactive, l’utilisateur se téléporte au centre du TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="feb1d-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="feb1d-112">Si l’indicateur d’orientation de remplacement est coché, l’orientation de l’utilisateur correspond à celle de la zone réactive de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="feb1d-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Exemple de hotspot de téléchaud](../images/teleport/TeleportHotspotExample.gif)
