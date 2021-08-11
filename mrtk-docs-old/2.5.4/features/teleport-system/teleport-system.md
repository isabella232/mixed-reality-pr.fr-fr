---
title: TeleportSystemOverview
description: Vue d’ensemble de l’activation et de la désactivation du système de téléportation dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, réalité mixte, développement, MRTK, système de téléportation,
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197639"
---
# <a name="teleport-system"></a>Système de téléportation

Le système de téléportation est un sous-système du MRTK qui gère la téléportation de l’utilisateur lorsque l’application utilise un écran opaque. Pour les expériences de réalité augmentée ou AR (comme HoloLens), le système de téléportation n’est pas actif. Pour les expériences immersives avec un casque audiovisuel ou HMD (OpenVR, WMR), le système de téléportation peut être activé.

## <a name="enabling-and-disabling"></a>Activation et désactivation

Vous pouvez activer/désactiver le système de téléportation à l’aide de la case à cocher située dans son profil.
Pour ce faire, sélectionnez l’objet MixedRealityToolkit dans la scène, cliquez sur « Teleport » (Téléporter), puis cochez/décochez la case « Enable Teleport System » (Activer le système de téléopération).

Ceci peut aussi s’effectuer au moment de l’exécution :

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

Le système de téléportation expose les événements par le biais de l’interface [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) pour fournir des signaux sur le début, la fin ou l’annulation des actions de téléportation.
Pour plus d’informations sur le mécanisme des événements et la charge utile associée, consultez la documentation API liée.

## <a name="usage"></a>Usage

### <a name="how-to-register-for-teleportation-events"></a>Comment s’inscrire aux événements de téléportation

Le code ci-dessous vous montre comment créer un MonoBehaviour qui écoute les événements de téléportation. Ce code part du principe que le système de téléportation est activé.

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
