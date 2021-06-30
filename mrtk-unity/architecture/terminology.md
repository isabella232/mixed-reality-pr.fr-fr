---
title: Terminologie
description: Termes du système d’entrée différents dans MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, entrée,
ms.openlocfilehash: 33f423fba286e9e85e6d0bedac82bff0b7aae81f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121457"
---
# <a name="input-system"></a>Système d’entrée

Le système d’entrée est l’un des plus grands systèmes de toutes les fonctionnalités offertes par MRTK.
De nombreux éléments de la boîte à outils sont générés par-dessus (pointeurs, Focus, prefabs). Le code dans le système d’entrée est ce qui permet des interactions naturelles telles que la capture et la rotation entre les plateformes.

Le système d’entrée présente une partie de sa terminologie qui mérite de définir :

- **Fournisseurs de données**

    Les paramètres d’entrée du profil d’entrée comportent des références à des entités appelées fournisseurs de données. un autre mot qui décrit ce sont les gestionnaires d’appareils. Il s’agit de composants dont la tâche consiste à étendre le système d’entrée MRTK en utilisant un système sous-jacent spécifique. Un exemple de fournisseur est le fournisseur Windows Mixed Reality, dont le travail est de communiquer avec les API Windows Mixed Reality sous-jacentes, puis de traduire les données de ces API en concepts d’entrée spécifiques à MRTK ci-dessous. Un autre exemple est le fournisseur OpenVR (dont le travail est de communiquer avec Unity, version abstraite des API OpenVR, puis de traduire ces données en concepts d’entrée MRTK).

- **Contrôleur**

    Représentation d’un contrôleur physique (qu’il s’agisse d’un contrôleur à 6 degrés de liberté, d’une main de style HoloLens 1 avec prise en charge des mouvements, d’une main entièrement articulée, d’un contrôleur de mouvement LEAP, etc.). Les contrôleurs sont générés par les gestionnaires d’appareils (par exemple, le gestionnaire d’appareils WMR génère un contrôleur et gère sa durée de vie lorsqu’il voit une main articulée en cours d’existence).

- **Pointeur**

    Les contrôleurs utilisent des pointeurs pour interagir avec les objets de jeu. Par exemple, le pointeur near interaction est responsable de la détection lorsque la main (qui est un contrôleur) est proche des objets qui se publient eux-mêmes en prenant en charge « near interaction ». D’autres exemples de pointeurs sont les téléportages ou les pointeurs Far (c’est-à-dire le pointeur de rayon de Shell) qui utilisent Far raycasts pour s’associer à du contenu dont la longueur est supérieure à celle des bras de l’utilisateur.

    Les pointeurs sont créés par le gestionnaire de périphériques, puis attachés à une source d’entrée. Pour obtenir tous les pointeurs d’un contrôleur, procédez comme suit : `controller.InputSource.Pointers`

    Notez qu’un contrôleur peut être associé à de nombreux pointeurs différents en même temps. Pour vous assurer que cela n’est pas dévolu au chaos, il existe un médiateur de pointeur qui contrôle les pointeurs autorisés à être actifs (par exemple, le médiateur désactive les pointeurs d’interaction Far lorsque l’interaction near est détectée).

- **Spécialisés**

    Les événements de pointeur sont envoyés aux objets qui sont **activés**. La sélection du focus varie selon le type de pointeur ; un pointeur de rayon de la main utilise raycasts, tandis qu’un pointeur de l’aidette utilise spherecasts. Un objet doit implémenter IMixedRealityFocusHandler pour recevoir le focus. Il est possible d’inscrire globalement un objet pour recevoir des événements de pointeur non filtrés, mais cette approche n’est pas recommandée.

    Le composant qui met à jour les objets qui sont activés est le [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Curseur**

    Entité associée à un pointeur qui donne des signaux visuels supplémentaires autour de l’interaction du pointeur. Par exemple, le FingerCursor affiche un anneau autour de votre doigt et peut faire pivoter ce cercle quand votre doigt est proche des objets « near-interagis ». Un pointeur peut être associé à un seul curseur à la fois.

- **Interaction et manipulation**

    Les objets peuvent être balisés avec un script d’interaction ou de manipulation. Il peut s’agir de [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) , par exemple, de [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    Par exemple, NearInteractionGrabbable et NearInteractionTouchable permettent à certains pointeurs (en particulier les pointeurs d’interaction proches) de savoir quels objets peuvent se concentrer.

    Les ManipulationHandlerables et interactifs sont des exemples de composants qui écoutent les événements de pointeur pour modifier les visuels de l’interface utilisateur ou déplacer/mettre à l’échelle/faire pivoter des objets jeux.

L’image ci-dessous capture la build de haut niveau (du bas vers le haut) de la pile d’entrée MRTK :

![Diagramme du système d’entrée](../features/images/input/MRTK_InputSystem.png)
