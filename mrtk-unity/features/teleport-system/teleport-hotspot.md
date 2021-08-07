---
title: Point d’accès à la téléportation
description: Documentation sur le composant HotSpot de télérelais dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de téléchaud, point d’accès
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 755b0e8f53be2f393b52395309ed9ab0fad96cadc2e4289400cfff45a99aa6a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189455"
---
# <a name="teleport-hotspot"></a>Point d’accès à la téléportation

La zone réactive de télétentative est un composant que vous pouvez ajouter à votre gameobject pour vous assurer que l’utilisateur est dans une certaine position et orientation lorsqu’il se téléporte à cet emplacement.

## <a name="usage"></a>Utilisation

### <a name="how-to-create-a-teleport-hotspot"></a>Comment créer une zone réactive de télétentative

Pour créer une zone réactive de télétentative, ajoutez le composant TeleportHotspot à un objet qui a également un composant de collision. 

![Composant HotSpot de téléporte](../images/teleport/TeleportHotspotComponent.png)

À présent, l’indicateur du pointeur de téléchargement change de couleur lorsqu’il est dirigé sur un TeleportHotspot. Lorsque l’action de téléchargement est terminée sur la zone réactive, l’utilisateur se téléporte au centre du TeleportHotspot.

Si l’indicateur d’orientation de remplacement est coché, l’orientation de l’utilisateur correspond à celle de la zone réactive de téléchargement.

![Exemple de hotspot de téléchaud](../images/teleport/TeleportHotspotExample.gif)
