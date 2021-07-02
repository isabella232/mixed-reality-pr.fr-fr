---
title: Barre de l’application
description: Vue d’ensemble de la barre d’application dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, barre d’application,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175694"
---
# <a name="app-bar"></a>Barre de l’application

![Barre de l’application](../images/app-bar/MRTK_AppBar_Main.png)

La barre de l’application est un composant d’interface utilisateur qui est utilisé conjointement avec le script de [contrôle des limites](bounds-control.md) . Elle ajoute des contrôles bouton à un objet dans le but de le manipuler. À l’aide du bouton « ajuster », l’interface de contrôle des limites pour un objet peut être désactivée. Le bouton « supprimer » doit supprimer l’objet de la scène.

## <a name="how-to-use-app-bar"></a>Comment utiliser la barre d’application

Glisser-déplacer `AppBar` (Assets/MRTK/SDK/features/UX/Prefabs/appbar/appbar. Prefab) dans la hiérarchie de la scène. Dans le volet de l’inspecteur du composant, assignez n’importe quel objet avec un contrôle de limites comme *cadre englobant cible* pour y ajouter la barre d’application.

**Important :** L’option d’activation du contrôle des limites pour l’objet cible doit être « activer manuellement ».

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
