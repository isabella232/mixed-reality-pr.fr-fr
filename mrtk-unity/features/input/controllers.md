---
title: Contrôleurs
description: Utilisation des contrôleurs dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, contrôleurs,
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176926"
---
# <a name="controllers"></a><span data-ttu-id="323e1-104">Controllers</span><span class="sxs-lookup"><span data-stu-id="323e1-104">Controllers</span></span>

<span data-ttu-id="323e1-105">Les contrôleurs sont créés et détruits automatiquement par les [**fournisseurs d’entrée**](input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="323e1-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="323e1-106">Chaque type de contrôleur a un certain nombre d' *entrées physiques* définies par un *type d’axe*, ce qui nous indique le type de données de la valeur d’entrée (numérique, axe unique, axe double, six DDL,...) et un *type d’entrée* (pression sur les boutons, déclencheur, barre de défilement, pointeur spatial, etc.) décrivant l’origine de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="323e1-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="323e1-107">les entrées physiques sont mappées à des *actions d’entrée* via dans le **profil de mappage d’entrée du contrôleur**, sous le *profil de système d’entrée* dans le composant Shared Computer Toolkit de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="323e1-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

![Mappage d’entrée de contrôleur](../images/input/ControllerInputMapping.png)
