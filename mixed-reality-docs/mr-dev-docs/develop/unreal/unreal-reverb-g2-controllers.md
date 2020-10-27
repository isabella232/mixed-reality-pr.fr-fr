---
title: Contrôleurs de reréverbérations de HP G2 inréel
description: Instructions sur l’utilisation des contrôleurs de réverbération de HP G2 dans OpenXR et SteamVR
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, réverbération, réverbération G2, réverbération HP G2, réalité mixte, développement, contrôleurs de mouvement, entrée utilisateur, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux
ms.openlocfilehash: c9d3ea3a8dd52ed0712f9df5c1a789121a68fd35
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638719"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="bf9f9-104">Contrôleurs de reréverbérations de HP G2 inréel</span><span class="sxs-lookup"><span data-stu-id="bf9f9-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="bf9f9-105">Prise en main</span><span class="sxs-lookup"><span data-stu-id="bf9f9-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf9f9-106">Le moteur 4,26 et OpenXR ou SteamVR est requis pour accéder au plug-in du contrôleur de mouvement HP. vous devez utiliser les contrôleurs de réverbération de HP G2.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="bf9f9-107">Portage d’une application OpenXR existante</span><span class="sxs-lookup"><span data-stu-id="bf9f9-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="bf9f9-108">Si aucune liaison de contrôleur n’existe dans le jeu pour le contrôleur de réalité mixte HP, le runtime OpenXR tente de remapper les liaisons existantes au contrôleur actif.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="bf9f9-109">Dans ce cas, le jeu présente des liaisons tactiles Oculus et aucune liaison de contrôleur de réalité mixte HP.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![Remappage des liaisons existantes lorsqu’il n’existe aucune liaison de contrôleur](images/reverb-g2-img-04.png)

<span data-ttu-id="bf9f9-111">Les événements sont toujours déclenchés, mais si le jeu doit utiliser des liaisons spécifiques au contrôleur, comme le bouton de menu droit, le profil d’interaction de la réalité mixte HP doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="bf9f9-112">Plusieurs liaisons de contrôleur peuvent être spécifiées par action pour mieux prendre en charge différents appareils.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![Utilisation de plusieurs liaisons de contrôleur](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="bf9f9-114">Ajout de mappages d’actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="bf9f9-114">Adding input action mappings</span></span> 

<span data-ttu-id="bf9f9-115">Définissez une nouvelle action et mappez à l’une des combinaisons de touches dans la section HP Mixed Reality Controller.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![Définition de nouvelles actions et mappages](images/reverb-g2-img-02.png)

<span data-ttu-id="bf9f9-117">Le contrôleur de réverbération HP G2 a également une poignée analogique, qui peut être utilisée dans les mappages d’axe avec la liaison « axe de l’axe ».</span><span class="sxs-lookup"><span data-stu-id="bf9f9-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="bf9f9-118">Il existe une liaison serrée distincte, qui doit être utilisée pour les mappages d’action lorsque le bouton de la poignée est entièrement enfoncé.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![Utilisation des liaisons d’axe Press](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="bf9f9-120">Ajout d’événements d’entrée</span><span class="sxs-lookup"><span data-stu-id="bf9f9-120">Adding input events</span></span>

<span data-ttu-id="bf9f9-121">Cliquez avec le bouton droit sur un plan et recherchez les nouveaux noms d’action à partir du système d’entrée pour ajouter des événements pour ces actions.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="bf9f9-122">Ici, le plan répond aux événements avec une chaîne d’impression déplaçant le bouton actuel et l’état de l’axe.</span><span class="sxs-lookup"><span data-stu-id="bf9f9-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![Blueprint répondant aux événements et générant l’état actuel du bouton et de l’axe](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="bf9f9-124">Utilisation de l’entrée</span><span class="sxs-lookup"><span data-stu-id="bf9f9-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="bf9f9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf9f9-125">See also</span></span>
* [<span data-ttu-id="bf9f9-126">Entrée SteamVR</span><span class="sxs-lookup"><span data-stu-id="bf9f9-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="bf9f9-127">Utilisation de SteamVR avec Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bf9f9-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="bf9f9-128">Appareil photo à lecteur non réel</span><span class="sxs-lookup"><span data-stu-id="bf9f9-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)