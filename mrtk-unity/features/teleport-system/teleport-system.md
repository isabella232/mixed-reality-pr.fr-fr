---
title: Système de téléordinateur
description: Vue d’ensemble de l’activation et de la désactivation du système de téléMRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de télé,
ms.openlocfilehash: 7a49b1fea36eb1809c57abee4cede1216c07d5bf
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176184"
---
# <a name="teleport-system"></a><span data-ttu-id="47d5a-104">Système de téléportation</span><span class="sxs-lookup"><span data-stu-id="47d5a-104">Teleport system</span></span>

<span data-ttu-id="47d5a-105">Le système de téléchargement est un sous-système du MRTK qui gère le téléporting de l’utilisateur lorsque l’application utilise un affichage opaque.</span><span class="sxs-lookup"><span data-stu-id="47d5a-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="47d5a-106">pour les expériences AR (comme HoloLens), le système de téléportage n’est pas actif.</span><span class="sxs-lookup"><span data-stu-id="47d5a-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="47d5a-107">Pour les expériences HMD immersifs (OpenVR, WMR), le système de téléchargement peut être activé.</span><span class="sxs-lookup"><span data-stu-id="47d5a-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="47d5a-108">Activation et désactivation</span><span class="sxs-lookup"><span data-stu-id="47d5a-108">Enabling and disabling</span></span>

<span data-ttu-id="47d5a-109">Le système de téléchargement peut être activé ou désactivé en coactivant la case à cocher dans son profil.</span><span class="sxs-lookup"><span data-stu-id="47d5a-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="47d5a-110">Pour ce faire, sélectionnez l’objet MixedRealityToolkit dans la scène, cliquez sur « téléporter », puis désactivez la case à cocher « Activer le système de téléopération ».</span><span class="sxs-lookup"><span data-stu-id="47d5a-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="47d5a-111">Cela peut également être fait au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="47d5a-111">This can also be done at runtime:</span></span>

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a><span data-ttu-id="47d5a-112">Événements</span><span class="sxs-lookup"><span data-stu-id="47d5a-112">Events</span></span>

<span data-ttu-id="47d5a-113">Le système de télétentative expose des événements par le biais [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) de l’interface pour fournir des signaux sur la date de début, la fin ou l’annulation des actions de télétentative.</span><span class="sxs-lookup"><span data-stu-id="47d5a-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="47d5a-114">Pour plus d’informations sur le mécanisme des événements et sur la charge utile associée, consultez la documentation de l’API liée.</span><span class="sxs-lookup"><span data-stu-id="47d5a-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="47d5a-115">Usage</span><span class="sxs-lookup"><span data-stu-id="47d5a-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="47d5a-116">Comment s’inscrire aux événements de téléportage</span><span class="sxs-lookup"><span data-stu-id="47d5a-116">How to register for teleportation events</span></span>

<span data-ttu-id="47d5a-117">Le code ci-dessous montre comment créer un monocomportement qui écoute les événements de téléportage.</span><span class="sxs-lookup"><span data-stu-id="47d5a-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="47d5a-118">Ce code suppose que le système de téléchargement est activé.</span><span class="sxs-lookup"><span data-stu-id="47d5a-118">This code assumes that the teleport system is enabled.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="47d5a-119">Téléportage sur MRTK</span><span class="sxs-lookup"><span data-stu-id="47d5a-119">Teleporting on MRTK</span></span>

<span data-ttu-id="47d5a-120">Pour vous téléporter avec un contrôleur sur des appareils MR avec des configurations par défaut, utilisez le stick analogique.</span><span class="sxs-lookup"><span data-stu-id="47d5a-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="47d5a-121">Pour vous téléporter avec des mains articulées, rendez un geste avec votre paume face à l’index et faites-le pointer vers l’extérieur, en effectuant la télétentative en faisant évoluer le doigt de l’index.</span><span class="sxs-lookup"><span data-stu-id="47d5a-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="47d5a-122">Pour vous téléporter avec la simulation d’entrée, consultez notre documentation sur le [service de simulation d’entrée](../input-simulation/input-simulation-service.md)mis à jour.</span><span class="sxs-lookup"><span data-stu-id="47d5a-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Geste de](../images/teleport/handteleport.gif)
