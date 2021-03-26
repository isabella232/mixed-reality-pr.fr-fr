---
title: TeleportHotspot
description: Documentation sur le composant HotSpot de télérelais dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, hololens, hololens 2, réalité mixte, développement, MRTK, système de téléchaud, point d’accès de
ms.openlocfilehash: 986105dd771c38b1e26fd9f86df90224110591a4
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105582955"
---
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="bc087-104">Point d’accès de téléhébergement [expérimental]</span><span class="sxs-lookup"><span data-stu-id="bc087-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="bc087-105">La zone réactive de télétentative est un composant que vous pouvez ajouter à votre gameobject pour vous assurer que l’utilisateur est dans une certaine position et orientation lorsqu’il se téléporte à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="bc087-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="bc087-106">Utilisation</span><span class="sxs-lookup"><span data-stu-id="bc087-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="bc087-107">Comment créer une zone réactive de télétentative</span><span class="sxs-lookup"><span data-stu-id="bc087-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="bc087-108">Pour créer une zone réactive de télétentative, ajoutez le composant TeleportHotspot à un objet qui a également un composant de collision.</span><span class="sxs-lookup"><span data-stu-id="bc087-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Composant HotSpot de téléporte](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="bc087-110">À présent, l’indicateur du pointeur de téléchargement change de couleur lorsqu’il est dirigé sur un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="bc087-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="bc087-111">Lorsque l’action de téléchargement est terminée sur la zone réactive, l’utilisateur se téléporte au centre du TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="bc087-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="bc087-112">Si l’indicateur d’orientation de remplacement est coché, l’orientation de l’utilisateur correspond à celle de la zone réactive de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="bc087-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Exemple de hotspot de téléchaud](../images/teleport/TeleportHotspotExample.gif)
