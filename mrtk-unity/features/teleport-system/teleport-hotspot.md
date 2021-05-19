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
# <a name="teleport-hotspot-experimental"></a>Point d’accès de téléhébergement [expérimental]

La zone réactive de télétentative est un composant que vous pouvez ajouter à votre gameobject pour vous assurer que l’utilisateur est dans une certaine position et orientation lorsqu’il se téléporte à cet emplacement.

## <a name="usage"></a>Usage

### <a name="how-to-create-a-teleport-hotspot"></a>Comment créer une zone réactive de télétentative

Pour créer une zone réactive de télétentative, ajoutez le composant TeleportHotspot à un objet qui a également un composant de collision. 

![Composant HotSpot de téléporte](../images/teleport/TeleportHotspotComponent.png)

À présent, l’indicateur du pointeur de téléchargement change de couleur lorsqu’il est dirigé sur un TeleportHotspot. Lorsque l’action de téléchargement est terminée sur la zone réactive, l’utilisateur se téléporte au centre du TeleportHotspot.

Si l’indicateur d’orientation de remplacement est coché, l’orientation de l’utilisateur correspond à celle de la zone réactive de téléchargement.

![Exemple de hotspot de téléchaud](../images/teleport/TeleportHotspotExample.gif)
