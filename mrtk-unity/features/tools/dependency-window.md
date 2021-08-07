---
title: Fenêtre de dépendance
description: Documentation sur l’utilisation de la fenêtre de dépendance dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 09425fa46cb9888c2e81e0771419d4bce3dd2334f31b5b922049af12479876c8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214321"
---
# <a name="dependency-window"></a>Fenêtre de dépendance

Dans Unity, il est souvent difficile de Gleam les ressources qui sont utilisées, et ce qui les référence. L’option « Rechercher des références dans la scène » fonctionne très bien lorsque vous vous intéressez uniquement à la scène actuelle, mais qu’en est-il de l’ensemble de votre projet Unity ? C’est là que la **fenêtre de dépendance** (Assets/MRTK/Tools/DependencyWindow) peut être utile.

La fenêtre dépendance affiche la manière dont les ressources référencent et dépendent les unes des autres. Les dépendances sont calculées en analysant les GUID dans les fichiers projet YAML (Remarque : les dépendances de script à script ne sont pas prises en compte).

## <a name="usage"></a>Utilisation

pour ouvrir la fenêtre, sélectionnez la fenêtre dépendance de la **réalité mixte**  >  **Shared Computer Toolkit**  >  **utilitaires**  >   qui ouvre la fenêtre et commence automatiquement à générer le graphique de dépendance de votre projet. Une fois le graphique de dépendance créé, vous pouvez sélectionner des éléments multimédias dans l’onglet projet pour inspecter leurs dépendances.

![Fenêtre de dépendance](../images/dependency-window/MRTK_Dependency_Window.png)

La fenêtre affiche la liste des ressources dont dépend la ressource actuellement sélectionnée, ainsi qu’une liste hiérarchique des ressources qui en dépendent. Si rien ne dépend de l’élément multimédia actuellement sélectionné, vous pouvez envisager de le supprimer de votre projet (Notez que certaines ressources sont chargées par programme via des API telles que shader. Find () et ne sont peut-être pas interceptées par le dispositif de suivi des dépendances).

La fenêtre peut également afficher uniquement une liste de toutes les ressources qui ne sont pas référencées par d’autres ressources et qui peuvent être prises en compte pour la suppression :

![Fenêtre de dépendance présentant des ressources non référencées](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> Si des ressources sont modifiées, ajoutées ou supprimées pendant l’utilisation de la fenêtre de dépendance, il est recommandé d’actualiser le graphique de dépendance pour obtenir les résultats les plus « à jour ».
