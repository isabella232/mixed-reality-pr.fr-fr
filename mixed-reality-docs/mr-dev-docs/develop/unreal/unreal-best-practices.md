---
title: Bonnes pratiques générales
description: Restez informés de toutes les bonnes pratiques recommandées pour le développement d’applications de réalité mixte dans Unreal Engine.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, extensions de l’éditeur, éditeur Unreal, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, portage, mise à niveau
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584790"
---
# <a name="general-best-practices"></a>Bonnes pratiques générales

Voici quelques-unes des bonnes pratiques générales que tous les développeurs devraient suivre lors de la création d’un projet Unreal Engine pour la réalité mixte.

## <a name="constructors"></a>Constructeurs

Si vous avez besoin de l’équivalent d’un « constructeur » dans des blueprints, utilisez le [script de construction](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html) d’Unreal. Le principal avantage par rapport à l’utilisation d’événements « BeginPlay » est que le script de constructeur s’exécute également dans l’éditeur. La plupart du temps, les valeurs peuvent être mises en cache directement au démarrage ou même au moment de la compilation.

> [!NOTE]
> Pour plus d’informations sur la prise en charge des scripts de construction, consultez notre [Vue d’ensemble des extensions de l’éditeur](unreal-editor-extensions.md#construction-scripts).

## <a name="3d-buttons-and-textures"></a>Boutons et textures 3D

Il est naturel de penser aux performances lors de la création ou de la planification de l’utilisation de boutons 3D dans des applications de réalité mixte. Cependant, tous les éléments ne doivent pas nécessairement être conçus à partir de maillages pour être perçus comme étant en 3D. Vous avez la possibilité d’utiliser Paper2D avec des textures soigneusement conçues pour obtenir cette apparence 3D. Cela fonctionne très bien pour les boutons qui « semblent » être en 3D, mais qui sont simplement des images retouchées sur un quad. Une version sophistiquée de ceci est appelée [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).

## <a name="variants"></a>Variantes

Utilisez des [variantes Unreal](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) dans les scénarios où vous créez une scène avec plusieurs configurations d’objets au moment de l’exécution. Les variations peuvent inclure des matériaux ou des maillages qui changent. 

## <a name="animation"></a>Animation

Tirez parti du [composant Spline](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (ce n’est pas le composant Spline « Mesh ») et des [nœuds de chronologie](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) si vous créez un grand nombre d’« animations interactives ». 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>Communications

Utilisez un [blueprint de niveau](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) si vous avez des difficultés à trouver dynamiquement des objets ou si vous utilisez trop de bande passante pour communiquer entre plusieurs acteurs et plusieurs blueprints. Rappelez-vous qu’Unreal Engine 4 n’est pas comme Unity : tout ne doit pas nécessairement être à l’intérieur d’un composant. Les blueprints de niveau sont un moyen parfaitement valide et recommandé de simplifier la communication entre plusieurs acteurs. Les références d’objet peuvent même être « mises en cache » au démarrage dans l’élément OnBeginPlay du blueprint de niveau.

## <a name="global-state"></a>État global

Vous devrez souvent stocker un état spécifique au niveau, comme le score, les données du niveau, des informations spécifiques au joueur ou n’importe quoi d’autre qui n’appartient pas tout à fait à un objet particulier. Ne négligez pas le [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html). La plupart des gens oublient qu’il existe, mais le GameMode peut être créé par niveau et contenir des données spécifiques à chaque niveau.

## <a name="optimizing-blueprints"></a>Optimisation des blueprints

Si vous trouvez que vos blueprints sont trop lents, laissez Unreal « nativiser » vos blueprints avant de réécrire le code en C++. Essayez d’utiliser la [nativisation](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) automatique avant de créer votre propre solution personnalisée.

![Paramètre des blueprints avec la méthode de nativisation de blueprint inclusive mis en évidence](images/unreal-general-practices-img-01.jpg)
