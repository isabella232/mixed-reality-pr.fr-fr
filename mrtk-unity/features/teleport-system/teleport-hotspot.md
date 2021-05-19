---
title: Point d’accès de télérelais
description: Documentation sur le composant HotSpot de télérelais dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, hololens, hololens 2, réalité mixte, développement, MRTK, système de téléchaud, point d’accès de
ms.openlocfilehash: 0cbdad3c038d457109077b742d3f453d63436ae4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144434"
---
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="be289-104">Point d’accès de téléhébergement [expérimental]</span><span class="sxs-lookup"><span data-stu-id="be289-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="be289-105">La zone réactive de télétentative est un composant que vous pouvez ajouter à votre gameobject pour vous assurer que l’utilisateur est dans une certaine position et orientation lorsqu’il se téléporte à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="be289-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="be289-106">Usage</span><span class="sxs-lookup"><span data-stu-id="be289-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="be289-107">Comment créer une zone réactive de télétentative</span><span class="sxs-lookup"><span data-stu-id="be289-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="be289-108">Pour créer une zone réactive de télétentative, ajoutez le composant TeleportHotspot à un objet qui a également un composant de collision.</span><span class="sxs-lookup"><span data-stu-id="be289-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Composant HotSpot de téléporte](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="be289-110">À présent, l’indicateur du pointeur de téléchargement change de couleur lorsqu’il est dirigé sur un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="be289-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="be289-111">Lorsque l’action de téléchargement est terminée sur la zone réactive, l’utilisateur se téléporte au centre du TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="be289-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="be289-112">Si l’indicateur d’orientation de remplacement est coché, l’orientation de l’utilisateur correspond à celle de la zone réactive de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="be289-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Exemple de hotspot de téléchaud](../images/teleport/TeleportHotspotExample.gif)
