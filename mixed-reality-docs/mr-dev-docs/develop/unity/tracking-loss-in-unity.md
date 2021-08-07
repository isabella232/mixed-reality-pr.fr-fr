---
title: Suivi des pertes dans Unity
description: Découvrez comment gérer les pertes de suivi manuelles et par défaut au sein d’une application Unity de réalité mixte.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perte de suivi, image de perte de suivi, interrogation, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: fe11c88bec60042901bd7ebb5c55116da97b6e28f0e44e889ef517a03d67245a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211351"
---
# <a name="tracking-loss-in-unity"></a>Suivi des pertes dans Unity

Lorsque l’appareil ne peut pas se trouver dans le monde entier, l’application rencontre une « perte de suivi ». Par défaut, Unity interrompt la boucle de mise à jour et affiche une image de démarrage pour le suivi des utilisateurs à tout moment est perdu. Une fois le suivi récupéré, l’image de démarrage disparaît et la boucle de mise à jour se poursuit.

En guise d’alternative, l’utilisateur peut gérer manuellement cette transition en désactivant le paramètre. Tout le contenu semblera être verrouillé pendant le suivi de la perte si rien n’est fait pour le gérer.

## <a name="default-handling"></a>Gestion par défaut

La boucle de mise à jour et tous les messages et événements s’arrêtent pendant la durée du suivi de la perte par défaut. En même temps, une image sera affichée à l’utilisateur. vous pouvez personnaliser cette image en accédant à Edit->Paramètres->Player, en cliquant sur image de l’écran de démarrage et en définissant l’image de perte de suivi holographique.

## <a name="manual-handling"></a>Gestion manuelle

pour gérer manuellement le suivi des pertes, vous devez accéder à **modifier**  >  **Project Paramètres**  >  **lecteur**  >  **plateforme Windows universelle paramètres onglet**  >  de **démarrage Image** de l’écran d’accueil  >  **Windows holographique** et décocher « en cas de suspension de perte de suivi et d’affichage de l’image ». Après quoi, vous devez gérer les modifications de suivi avec les API spécifiées ci-dessous.

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Type :** *WorldManager*

* World Manager expose un événement pour détecter le suivi des pertes/gains (*WorldManager. OnPositionalLocatorStateChanged*) et une propriété pour interroger l’état actuel (*WorldManager. State*)
* Lorsque l’état de suivi n’est pas actif, l’appareil photo n’apparaît pas dans le monde virtuel, même lorsque l’utilisateur se traduit. Les objets ne correspondent plus à aucun emplacement physique et tous les corps sont verrouillés.

Lorsque vous gérez le suivi des modifications par vous-même, vous devez interroger la propriété State pour chaque frame ou gérer l’événement *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Interrogation

L’état le plus important est *PositionalLocatorState. active*, ce qui signifie que le suivi est entièrement fonctionnel. Tous les autres États entraînent uniquement des deltas de rotation vers la caméra principale. Par exemple :

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Gestion de l’événement OnPositionalLocatorStateChanged

Plus pratique, vous pouvez également vous abonner à *OnPositionalLocatorStateChanged* pour gérer les transitions :

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

## <a name="see-also"></a>Voir aussi

* [Gestion des pertes de suivi dans DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
