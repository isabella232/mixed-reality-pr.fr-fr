---
title: Main service extension physique
description: Description services d’extension physique.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143431"
---
# <a name="hand-physics-extension-services"></a>Main services d’extension physique

La main physique service Active les événements de collision de corps rigides et les interactions avec les mains articulées.

## <a name="getting-started-with-hand-physics-extension-service"></a>Prise en main du service d’extension physique de main

Ajoutez le service physique de la main à la liste des services d’extension et utilisez le profil par défaut.

Une fois activé, utilisez la propriété IsTrigger de l’un des conflits pour recevoir les événements de collision des 10 chiffres (et des palmiers s’ils sont activés).

### <a name="prerequisites"></a>Prérequis

- Activation du service d’extension
- Assignez un Prefab approprié à la jointure Finger/Palm.

## <a name="recommendations"></a>Recommandations

Si le service utilise par défaut la couche « par défaut », il est recommandé d’utiliser une couche distincte pour les objets HandPhysics. Dans le cas contraire, il peut y avoir des conflits indésirables et/ou des raycasts inexacts.
