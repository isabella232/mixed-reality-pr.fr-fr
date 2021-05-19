---
title: Vue d’ensemble du système de téléporte
description: Vue d’ensemble de l’activation et de la désactivation du système de téléMRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de télé-,
ms.openlocfilehash: a44ad1827597dd0b27bc88a9420a3b251f934afd
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144140"
---
# <a name="teleport-system"></a>Système de téléportation

Le système de téléchargement est un sous-système du MRTK qui gère le téléporting de l’utilisateur lorsque l’application utilise un affichage opaque. Pour les expériences AR (comme HoloLens), le système de téléportage n’est pas actif. Pour les expériences HMD immersifs (OpenVR, WMR), le système de téléchargement peut être activé.

## <a name="enabling-and-disabling"></a>Activation et désactivation

Le système de téléchargement peut être activé ou désactivé en coactivant la case à cocher dans son profil.
Pour ce faire, sélectionnez l’objet MixedRealityToolkit dans la scène, cliquez sur « téléporter », puis désactivez la case à cocher « Activer le système de téléopération ».

Cela peut également être fait au moment de l’exécution :

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

## <a name="events"></a>Événements

Le système de télétentative expose des événements par le biais [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) de l’interface pour fournir des signaux sur la date de début, la fin ou l’annulation des actions de télétentative.
Pour plus d’informations sur le mécanisme des événements et sur la charge utile associée, consultez la documentation de l’API liée.

## <a name="usage"></a>Usage

### <a name="how-to-register-for-teleportation-events"></a>Comment s’inscrire aux événements de téléportage

Le code ci-dessous montre comment créer un monocomportement qui écoute les événements de téléportage. Ce code suppose que le système de téléchargement est activé.

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

## <a name="teleporting-on-mrtk"></a>Téléportage sur MRTK

Pour vous téléporter avec un contrôleur sur des appareils MR avec des configurations par défaut, utilisez le stick analogique. Pour vous téléporter avec des mains articulées, rendez un geste avec votre paume face à l’index et faites-le pointer vers l’extérieur, en effectuant la télétentative en faisant évoluer le doigt de l’index. Pour vous téléporter avec la simulation d’entrée, consultez notre documentation sur le [service de simulation d’entrée](../input-simulation/input-simulation-service.md)mis à jour.

  ![Geste de](../images/teleport/handteleport.gif)