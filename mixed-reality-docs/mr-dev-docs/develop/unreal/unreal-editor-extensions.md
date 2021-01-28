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
# <a name="editor-extensions-in-unreal"></a>Extension de l’éditeur dans Unreal

Unreal fournit un ensemble complet de fonctionnalités qui vous permettent de personnaliser le moteur en fonction de vos besoins. Les fonctionnalités peuvent être simples mais limitées, ou très puissantes mais complexes. Les étapes suivantes sont listées par ordre de complexité croissante. D’une façon générale, il est conseillé d’essayer d’abord les solutions les plus simples pour votre problème et d’utiliser toutes leurs options avant de passer à un choix plus complexe. À titre d’exemple, nous avons découvert que la plupart du temps, le script de construction de base peut être utilisé à la place des plug-ins. 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>Scripts de construction

Vous pouvez utiliser des scripts de construction pour effectuer des actions d’initialisation, qui s’exécutent lors de la création de l’instance Blueprint.

* [Scripts de construction utilisateur](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [Exemple de blueprint](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [Didacticiel vidéo](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>Actions de script

Les actions de script sont des blueprints d’utilitaire de l’éditeur. Vous pouvez les lancer dans l’éditeur Unreal comme suit :
* En cliquant avec le bouton droit sur **Assets** dans le navigateur de contenu.
* En cliquant avec le bouton droit sur **Actors** dans la fenêtre d’affichage des niveaux ou dans le World Outliner.

Les actions de script conviennent seulement quand vous avez besoin de votre logique de blueprint pour avoir une reconnaissance contextuelle d’ensembles de ressources ou d’acteurs. En règle générale, une action de script obtient une liste des ressources ou des acteurs que vous avez sélectionnés quand l’action est exécutée, puis elle modifie ces objets ou les prend en compte dans son graphique.

* [Actions de script](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [Exécution d’actions de script au démarrage du projet](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Widgets d’utilitaire de l’éditeur

Vous pouvez utiliser des [widgets d’utilitaire de l’éditeur](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) quand vous voulez ajouter de nouveaux éléments à l’interface utilisateur de l’éditeur Unreal. Les widgets d’utilitaire de l’éditeur sont basés sur Unreal Motion Graphics (UMG) : vous pouvez donc configurer des widgets dans un blueprint comme vous le feriez pour n’importe quel autre blueprint de widget UMG.

Ces widgets sont spécifiquement destinés à l’interface utilisateur de l’éditeur, et vous pouvez les utiliser pour créer des onglets personnalisés dans l’éditeur. Vous pouvez ensuite sélectionner ces onglets personnalisés dans le menu Windows, comme vous le feriez avec les onglets existants de l’éditeur.

## <a name="plugins"></a>Plug-ins

Unreal vous permet de développer et de gérer vos propres [plug-ins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) personnalisés pour les utiliser avec les outils et le runtime UE4. Vous pouvez activer ou désactiver vos plug-ins à tout moment dans l’éditeur Unreal. Les plug-ins peuvent ajouter des fonctionnalités d’exécution du jeu, modifier des fonctionnalités intégrées du moteur, créer de nouveaux types de fichiers et étendre les fonctionnalités de l’éditeur.

<!-- ## Engine modifications -->

