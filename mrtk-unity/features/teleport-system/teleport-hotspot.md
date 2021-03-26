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
# <a name="teleport-hotspot-experimental"></a>Point d’accès de téléhébergement [expérimental]

La zone réactive de télétentative est un composant que vous pouvez ajouter à votre gameobject pour vous assurer que l’utilisateur est dans une certaine position et orientation lorsqu’il se téléporte à cet emplacement.

## <a name="usage"></a>Utilisation

### <a name="how-to-create-a-teleport-hotspot"></a>Comment créer une zone réactive de télétentative

Pour créer une zone réactive de télétentative, ajoutez le composant TeleportHotspot à un objet qui a également un composant de collision. 

![Composant HotSpot de téléporte](../images/teleport/TeleportHotspotComponent.png)

À présent, l’indicateur du pointeur de téléchargement change de couleur lorsqu’il est dirigé sur un TeleportHotspot. Lorsque l’action de téléchargement est terminée sur la zone réactive, l’utilisateur se téléporte au centre du TeleportHotspot.

Si l’indicateur d’orientation de remplacement est coché, l’orientation de l’utilisateur correspond à celle de la zone réactive de téléchargement.

![Exemple de hotspot de téléchaud](../images/teleport/TeleportHotspotExample.gif)
