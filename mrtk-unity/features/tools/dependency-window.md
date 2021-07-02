---
title: Fenêtre de dépendance
description: Documentation sur l’utilisation de la fenêtre de dépendance dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176659"
---
# <a name="dependency-window"></a><span data-ttu-id="ac5f4-104">Fenêtre de dépendance</span><span class="sxs-lookup"><span data-stu-id="ac5f4-104">Dependency window</span></span>

<span data-ttu-id="ac5f4-105">Dans Unity, il est souvent difficile de Gleam les ressources qui sont utilisées, et ce qui les référence.</span><span class="sxs-lookup"><span data-stu-id="ac5f4-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="ac5f4-106">L’option « Rechercher des références dans la scène » fonctionne très bien lorsque vous vous intéressez uniquement à la scène actuelle, mais qu’en est-il de l’ensemble de votre projet Unity ?</span><span class="sxs-lookup"><span data-stu-id="ac5f4-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="ac5f4-107">C’est là que la **fenêtre de dépendance** (Assets/MRTK/Tools/DependencyWindow) peut être utile.</span><span class="sxs-lookup"><span data-stu-id="ac5f4-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="ac5f4-108">La fenêtre dépendance affiche la manière dont les ressources référencent et dépendent les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="ac5f4-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="ac5f4-109">Les dépendances sont calculées en analysant les GUID dans les fichiers projet YAML (Remarque : les dépendances de script à script ne sont pas prises en compte).</span><span class="sxs-lookup"><span data-stu-id="ac5f4-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="ac5f4-110">Usage</span><span class="sxs-lookup"><span data-stu-id="ac5f4-110">Usage</span></span>

<span data-ttu-id="ac5f4-111">pour ouvrir la fenêtre, sélectionnez la fenêtre dépendance de la **réalité mixte**  >  **Shared Computer Toolkit**  >  **utilitaires**  >   qui ouvre la fenêtre et commence automatiquement à générer le graphique de dépendance de votre projet.</span><span class="sxs-lookup"><span data-stu-id="ac5f4-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="ac5f4-112">Une fois le graphique de dépendance créé, vous pouvez sélectionner des éléments multimédias dans l’onglet projet pour inspecter leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="ac5f4-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![Fenêtre de dépendance](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="ac5f4-114">La fenêtre affiche la liste des ressources dont dépend la ressource actuellement sélectionnée, ainsi qu’une liste hiérarchique des ressources qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="ac5f4-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="ac5f4-115">Si rien ne dépend de l’élément multimédia actuellement sélectionné, vous pouvez envisager de le supprimer de votre projet (Notez que certaines ressources sont chargées par programme via des API telles que shader. Find () et ne sont peut-être pas interceptées par le dispositif de suivi des dépendances).</span><span class="sxs-lookup"><span data-stu-id="ac5f4-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="ac5f4-116">La fenêtre peut également afficher uniquement une liste de toutes les ressources qui ne sont pas référencées par d’autres ressources et qui peuvent être prises en compte pour la suppression :</span><span class="sxs-lookup"><span data-stu-id="ac5f4-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![Fenêtre de dépendance présentant des ressources non référencées](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="ac5f4-118">Si des ressources sont modifiées, ajoutées ou supprimées pendant l’utilisation de la fenêtre de dépendance, il est recommandé d’actualiser le graphique de dépendance pour obtenir les résultats les plus « à jour ».</span><span class="sxs-lookup"><span data-stu-id="ac5f4-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
