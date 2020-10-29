---
title: Suivi des pertes dans Unity
description: Gestion des pertes de suivi dans une application Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perte de suivi, image de perte de suivi
ms.openlocfilehash: 5aa17def844735088bcee6137a7b76a586107e44
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91678980"
---
# <a name="tracking-loss-in-unity"></a>Suivi des pertes dans Unity

Lorsque l’appareil ne peut pas se trouver dans le monde entier, l’application rencontre une « perte de suivi ». Par défaut, Unity met en pause la boucle de mise à jour et affiche une image de démarrage pour l’utilisateur. Lorsque le suivi est retrouvé, l’image de démarrage disparaît et la boucle de mise à jour se poursuit.

En guise d’alternative, l’utilisateur peut gérer manuellement cette transition en désactivant le paramètre. Tout le contenu semblera être verrouillé pendant le suivi de la perte si rien n’est fait pour le gérer.

## <a name="default-handling"></a>Gestion par défaut

Par défaut, la boucle de mise à jour de l’application, ainsi que tous les messages et événements, s’arrête pendant la durée du suivi des pertes. En même temps, une image sera affichée à l’utilisateur. Vous pouvez personnaliser cette image en accédant à modifier >paramètres->Player, en cliquant sur image de l’écran de démarrage et en définissant l’image de perte de suivi holographique.

## <a name="manual-handling"></a>Gestion manuelle

Pour gérer manuellement le suivi des pertes, vous devez accéder à **modifier** les  >  **paramètres**  >  **Player**  >  du projet plateforme Windows universelle de l' **onglet Paramètres**  >  de l' **image de démarrage**  >  **Windows holographique** et décocher « en cas de perte de suivi et d’affichage de l’image ». Après quoi, vous devez gérer les modifications de suivi avec les API spécifiées ci-dessous.

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Type :** *WorldManager*

* World Manager expose un événement pour détecter le suivi des pertes/gains ( *WorldManager. OnPositionalLocatorStateChanged* ) et une propriété pour interroger l’état actuel ( *WorldManager. State* )
* Lorsque l’état de suivi n’est pas actif, l’appareil photo n’apparaît pas dans le monde virtuel, même lorsque l’utilisateur se traduit. Cela signifie que les objets ne correspondent plus à aucun emplacement physique et que tous les corps sont verrouillés.

Lors du traitement des modifications de suivi, vous devez interroger la propriété d’état de chaque trame ou gérer l’événement *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Interrogation

L’état le plus important est *PositionalLocatorState. active* , ce qui signifie que le suivi est entièrement fonctionnel. Tous les autres États entraînent uniquement des deltas de rotation vers la caméra principale. Par exemple :

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

En guise d’alternative et de commodité, vous pouvez également vous abonner à *OnPositionalLocatorStateChanged* pour gérer les transitions :

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
