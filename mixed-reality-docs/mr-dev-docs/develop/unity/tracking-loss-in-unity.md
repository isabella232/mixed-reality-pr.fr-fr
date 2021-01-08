---
title: Suivi des pertes dans Unity
description: Découvrez comment gérer les pertes de suivi manuelles et par défaut au sein d’une application Unity de réalité mixte.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perte de suivi, image de perte de suivi, interrogation, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009849"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="3402c-104">Suivi des pertes dans Unity</span><span class="sxs-lookup"><span data-stu-id="3402c-104">Tracking loss in Unity</span></span>

<span data-ttu-id="3402c-105">Lorsque l’appareil ne peut pas se trouver dans le monde entier, l’application rencontre une « perte de suivi ».</span><span class="sxs-lookup"><span data-stu-id="3402c-105">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="3402c-106">Par défaut, Unity interrompt la boucle de mise à jour et affiche une image de démarrage pour le suivi des utilisateurs à tout moment est perdu.</span><span class="sxs-lookup"><span data-stu-id="3402c-106">By default, Unity will pause the update loop and display a splash image to the user anytime tracking is lost.</span></span> <span data-ttu-id="3402c-107">Une fois le suivi récupéré, l’image de démarrage disparaît et la boucle de mise à jour se poursuit.</span><span class="sxs-lookup"><span data-stu-id="3402c-107">Once tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="3402c-108">En guise d’alternative, l’utilisateur peut gérer manuellement cette transition en désactivant le paramètre.</span><span class="sxs-lookup"><span data-stu-id="3402c-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="3402c-109">Tout le contenu semblera être verrouillé pendant le suivi de la perte si rien n’est fait pour le gérer.</span><span class="sxs-lookup"><span data-stu-id="3402c-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="3402c-110">Gestion par défaut</span><span class="sxs-lookup"><span data-stu-id="3402c-110">Default Handling</span></span>

<span data-ttu-id="3402c-111">La boucle de mise à jour et tous les messages et événements s’arrêtent pendant la durée du suivi de la perte par défaut.</span><span class="sxs-lookup"><span data-stu-id="3402c-111">The update loop and all messages and events will stop for the duration of tracking loss by default.</span></span> <span data-ttu-id="3402c-112">En même temps, une image sera affichée à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3402c-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="3402c-113">Vous pouvez personnaliser cette image en accédant à modifier >paramètres->Player, en cliquant sur image de l’écran de démarrage et en définissant l’image de perte de suivi holographique.</span><span class="sxs-lookup"><span data-stu-id="3402c-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="3402c-114">Gestion manuelle</span><span class="sxs-lookup"><span data-stu-id="3402c-114">Manual Handling</span></span>

<span data-ttu-id="3402c-115">Pour gérer manuellement le suivi des pertes, vous devez accéder à **modifier** les  >  **paramètres**  >    >  du projet plateforme Windows universelle de l'**onglet Paramètres**  >  de l'**image de démarrage**  >  **Windows holographique** et décocher « en cas de perte de suivi et d’affichage de l’image ».</span><span class="sxs-lookup"><span data-stu-id="3402c-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="3402c-116">Après quoi, vous devez gérer les modifications de suivi avec les API spécifiées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3402c-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="3402c-117">**Espace de noms :** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="3402c-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="3402c-118">**Type :** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="3402c-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="3402c-119">World Manager expose un événement pour détecter le suivi des pertes/gains (*WorldManager. OnPositionalLocatorStateChanged*) et une propriété pour interroger l’état actuel (*WorldManager. State*)</span><span class="sxs-lookup"><span data-stu-id="3402c-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="3402c-120">Lorsque l’état de suivi n’est pas actif, l’appareil photo n’apparaît pas dans le monde virtuel, même lorsque l’utilisateur se traduit.</span><span class="sxs-lookup"><span data-stu-id="3402c-120">When the tracking state isn't active, the camera won't appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="3402c-121">Les objets ne correspondent plus à aucun emplacement physique et tous les corps sont verrouillés.</span><span class="sxs-lookup"><span data-stu-id="3402c-121">Objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="3402c-122">Lorsque vous gérez le suivi des modifications par vous-même, vous devez interroger la propriété State pour chaque frame ou gérer l’événement *OnPositionalLocatorStateChanged* .</span><span class="sxs-lookup"><span data-stu-id="3402c-122">When handling tracking changes on your own, you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="3402c-123">Interrogation</span><span class="sxs-lookup"><span data-stu-id="3402c-123">Polling</span></span>

<span data-ttu-id="3402c-124">L’état le plus important est *PositionalLocatorState. active*, ce qui signifie que le suivi est entièrement fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="3402c-124">The most important state is *PositionalLocatorState.Active*, which means tracking is fully functional.</span></span> <span data-ttu-id="3402c-125">Tous les autres États entraînent uniquement des deltas de rotation vers la caméra principale.</span><span class="sxs-lookup"><span data-stu-id="3402c-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="3402c-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3402c-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="3402c-127">Gestion de l’événement OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="3402c-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="3402c-128">Plus pratique, vous pouvez également vous abonner à *OnPositionalLocatorStateChanged* pour gérer les transitions :</span><span class="sxs-lookup"><span data-stu-id="3402c-128">More conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="3402c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3402c-129">See also</span></span>

* [<span data-ttu-id="3402c-130">Gestion des pertes de suivi dans DirectX</span><span class="sxs-lookup"><span data-stu-id="3402c-130">Handling tracking loss in DirectX</span></span>](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
