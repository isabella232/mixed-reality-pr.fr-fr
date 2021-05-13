---
title: Contrôleurs
description: Utilisation des contrôleurs dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, contrôleurs,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850335"
---
# <a name="controllers"></a>Controllers

Les contrôleurs sont créés et détruits automatiquement par les [**fournisseurs d’entrée**](input-providers.md). Chaque type de contrôleur a un certain nombre d' *entrées physiques* définies par un *type d’axe*, ce qui nous indique le type de données de la valeur d’entrée (numérique, axe unique, axe double, six DDL,...) et un *type d’entrée* (pression sur les boutons, déclencheur, barre de défilement, pointeur spatial, etc.) décrivant l’origine de l’entrée. Les entrées physiques sont mappées à des *actions d’entrée* via dans le **profil de mappage d’entrée du contrôleur**, sous le *profil de système d’entrée* dans le composant d’outils de la réalité mixte.

MRTK détectera automatiquement les contrôleurs WMR et les affichera lors de l’installation du package [**Microsoft. MixedReality. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) . Les modèles de contrôleurs s’affichent uniquement dans l’éditeur lors de l’utilisation du pipeline OpenXR. Pour visualiser les modèles de contrôleur Oculus, suivez les [instructions de déploiement de Oculus Quest](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md) .

![Mappage d’entrée de contrôleur](../images/input/ControllerInputMapping.png)