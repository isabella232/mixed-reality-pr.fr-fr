---
title: Extension de l’éditeur dans Unreal
description: Découvrez comment étendre l’éditeur Unreal Engine avec des scripts personnalisés, des actions de script et des widgets d’utilitaire.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, extensions de l’éditeur, éditeur Unreal, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, portage, mise à niveau
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584797"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="d3312-104">Extension de l’éditeur dans Unreal</span><span class="sxs-lookup"><span data-stu-id="d3312-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="d3312-105">Unreal fournit un ensemble complet de fonctionnalités qui vous permettent de personnaliser le moteur en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="d3312-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="d3312-106">Les fonctionnalités peuvent être simples mais limitées, ou très puissantes mais complexes.</span><span class="sxs-lookup"><span data-stu-id="d3312-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="d3312-107">Les étapes suivantes sont listées par ordre de complexité croissante.</span><span class="sxs-lookup"><span data-stu-id="d3312-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="d3312-108">D’une façon générale, il est conseillé d’essayer d’abord les solutions les plus simples pour votre problème et d’utiliser toutes leurs options avant de passer à un choix plus complexe.</span><span class="sxs-lookup"><span data-stu-id="d3312-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="d3312-109">À titre d’exemple, nous avons découvert que la plupart du temps, le script de construction de base peut être utilisé à la place des plug-ins.</span><span class="sxs-lookup"><span data-stu-id="d3312-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="d3312-110">Scripts de construction</span><span class="sxs-lookup"><span data-stu-id="d3312-110">Construction scripts</span></span>

<span data-ttu-id="d3312-111">Vous pouvez utiliser des scripts de construction pour effectuer des actions d’initialisation, qui s’exécutent lors de la création de l’instance Blueprint.</span><span class="sxs-lookup"><span data-stu-id="d3312-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="d3312-112">Scripts de construction utilisateur</span><span class="sxs-lookup"><span data-stu-id="d3312-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="d3312-113">Exemple de blueprint</span><span class="sxs-lookup"><span data-stu-id="d3312-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="d3312-114">Didacticiel vidéo</span><span class="sxs-lookup"><span data-stu-id="d3312-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="d3312-115">Actions de script</span><span class="sxs-lookup"><span data-stu-id="d3312-115">Scripted actions</span></span>

<span data-ttu-id="d3312-116">Les actions de script sont des blueprints d’utilitaire de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="d3312-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="d3312-117">Vous pouvez les lancer dans l’éditeur Unreal comme suit :</span><span class="sxs-lookup"><span data-stu-id="d3312-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="d3312-118">En cliquant avec le bouton droit sur **Assets** dans le navigateur de contenu.</span><span class="sxs-lookup"><span data-stu-id="d3312-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="d3312-119">En cliquant avec le bouton droit sur **Actors** dans la fenêtre d’affichage des niveaux ou dans le World Outliner.</span><span class="sxs-lookup"><span data-stu-id="d3312-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="d3312-120">Les actions de script conviennent seulement quand vous avez besoin de votre logique de blueprint pour avoir une reconnaissance contextuelle d’ensembles de ressources ou d’acteurs.</span><span class="sxs-lookup"><span data-stu-id="d3312-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="d3312-121">En règle générale, une action de script obtient une liste des ressources ou des acteurs que vous avez sélectionnés quand l’action est exécutée, puis elle modifie ces objets ou les prend en compte dans son graphique.</span><span class="sxs-lookup"><span data-stu-id="d3312-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="d3312-122">Actions de script</span><span class="sxs-lookup"><span data-stu-id="d3312-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="d3312-123">Exécution d’actions de script au démarrage du projet</span><span class="sxs-lookup"><span data-stu-id="d3312-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="d3312-124">Widgets d’utilitaire de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="d3312-124">Editor utility widgets</span></span>

<span data-ttu-id="d3312-125">Vous pouvez utiliser des [widgets d’utilitaire de l’éditeur](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) quand vous voulez ajouter de nouveaux éléments à l’interface utilisateur de l’éditeur Unreal.</span><span class="sxs-lookup"><span data-stu-id="d3312-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="d3312-126">Les widgets d’utilitaire de l’éditeur sont basés sur Unreal Motion Graphics (UMG) : vous pouvez donc configurer des widgets dans un blueprint comme vous le feriez pour n’importe quel autre blueprint de widget UMG.</span><span class="sxs-lookup"><span data-stu-id="d3312-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="d3312-127">Ces widgets sont spécifiquement destinés à l’interface utilisateur de l’éditeur, et vous pouvez les utiliser pour créer des onglets personnalisés dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="d3312-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="d3312-128">Vous pouvez ensuite sélectionner ces onglets personnalisés dans le menu Windows, comme vous le feriez avec les onglets existants de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="d3312-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="d3312-129">Plug-ins</span><span class="sxs-lookup"><span data-stu-id="d3312-129">Plugins</span></span>

<span data-ttu-id="d3312-130">Unreal vous permet de développer et de gérer vos propres [plug-ins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) personnalisés pour les utiliser avec les outils et le runtime UE4.</span><span class="sxs-lookup"><span data-stu-id="d3312-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="d3312-131">Vous pouvez activer ou désactiver vos plug-ins à tout moment dans l’éditeur Unreal.</span><span class="sxs-lookup"><span data-stu-id="d3312-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="d3312-132">Les plug-ins peuvent ajouter des fonctionnalités d’exécution du jeu, modifier des fonctionnalités intégrées du moteur, créer de nouveaux types de fichiers et étendre les fonctionnalités de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="d3312-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

