---
title: Contrôleurs
description: Utilisation des contrôleurs dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, contrôleurs,
ms.openlocfilehash: bc6aea1abda85567ab1b0db2616b529a92b4165e9b9cbcbc4b8b3cecd8a34c9f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224755"
---
# <a name="controllers"></a>Controllers

Les contrôleurs sont créés et détruits automatiquement par les [**fournisseurs d’entrée**](input-providers.md). Chaque type de contrôleur a un certain nombre d' *entrées physiques* définies par un *type d’axe*, ce qui nous indique le type de données de la valeur d’entrée (numérique, axe unique, axe double, six DDL,...) et un *type d’entrée* (pression sur les boutons, déclencheur, barre de défilement, pointeur spatial, etc.) décrivant l’origine de l’entrée. les entrées physiques sont mappées à des *actions d’entrée* via dans le **profil de mappage d’entrée du contrôleur**, sous le *profil de système d’entrée* dans le composant Shared Computer Toolkit de la réalité mixte.

![Mappage d’entrée de contrôleur](../images/input/ControllerInputMapping.png)
