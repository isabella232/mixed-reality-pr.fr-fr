---
title: Ancrer
description: Description pour les contrôles Dock.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226571"
---
# <a name="dock"></a>Ancrer

![Ancrer](../images/dock/MRTK_UX_Dock_Main.png)

Ce contrôle permet de déplacer des objets vers et depuis des positions prédéterminées, de créer des palettes, des étagères et des barres de navigation.

## <a name="features"></a>Fonctionnalités

- Prend en charge un nombre quelconque de positions et de dispositions d’ancrage (Works parfait avec [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) )
- Les objets ancrés se déplacent automatiquement pour créer de l’espace pour les nouveaux objets
- Les objets sont mis à l’échelle pour s’ajuster à l’espace ancré, puis redimensionner à leur position d’origine lors de leur déplacement.

## <a name="getting-started-with-dock"></a>Prise en main de la station d’accueil

- Créez un GameObject avec le composant Dock et ajoutez-y des enfants GameObjects.
- Ajoutez le composant DockPosition à chacun des enfants.
- Ajoutez le composant Ancrable à un nombre quelconque d’objets dans la scène pour permettre leur ancrage. Ils doivent également avoir le [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) composant et un conflit.
- *Facultatif :* utilisez un [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) sur la station d’accueil pour disposer automatiquement le DockPositions.

### <a name="prerequisites"></a>Prérequis

- Chaque objet Ancrable doit avoir un conflit avec un [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) ou un [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .
- Si vous souhaitez qu’un objet commence à s’ancrer lors du chargement de la scène, assignez-le à toute propriété d’objet ancré de DockPosition.

## <a name="how-it-works"></a>Fonctionnement

Le composant Ancrable s’appuie sur les événements de manipulation pour permettre aux objets glissables d’être ancrés et non ancrés à des positions spécifiques. Le positionnement est déterminé par le DockPosition déclenché le plus proche de l’objet déplacé. les deux objets doivent donc avoir des conflits pour que le déclencheur soit activé.
