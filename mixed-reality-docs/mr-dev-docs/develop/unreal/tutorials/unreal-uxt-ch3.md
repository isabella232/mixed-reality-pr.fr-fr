---
title: 3. Configuration de votre projet pour la réalité mixte
description: Partie 3 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 26bb874578e56b21d319741b8b1c1ff6decebe4b
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609700"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Configuration de votre projet pour la réalité mixte

Dans le tutoriel précédent, vous avez configuré le projet d’application de jeu d’échecs. Cette section va vous expliquer comment configurer l’application pour le développement de réalité mixte, ce qui implique l’ajout d’une session de réalité augmentée. Pour cette tâche, vous allez utiliser une ressource de données ARSessionConfig, qui contient des paramètres pratiques pour la réalité augmentée, comme le mappage spatial et l’occlusion. Vous trouverez plus de détails sur la ressource [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) et la classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) dans la documentation d’Unreal.

## <a name="objectives"></a>Objectifs

* Utilisation des paramètres de réalité augmentée d’Unreal Engine
* Utilisation d’une ressource de données ARSessionConfig
* Configuration d’un pion et du mode Jeu

## <a name="adding-the-session-asset"></a>Ajout de la ressource de session

Les sessions de réalité augmentée n’arrivent pas toutes seules. Pour utiliser une session, vous devez créer une ressource de données ARSessionConfig, ce qui est d’ailleurs votre tâche suivante :

1. Cliquez sur **Add New > Miscellaneous > Data Asset** (Ajouter > Divers > Ressource de données) dans le navigateur de contenu (**Content Browser**). Vérifiez que vous vous trouvez au niveau du dossier **Content** racine.
    * Sélectionnez **ARSessionConfig**, cliquez sur **Select**, puis nommez la ressource **ARSessionConfig**.

![Créer une ressource de données](images/unreal-uxt/3-createasset.PNG)

3. Double-cliquez sur **ARSessionConfig** pour l’ouvrir, conservez tous les paramètres par défaut, puis appuyez sur **Save** (Enregistrer). Revenez dans la fenêtre principale.

![Configuration de la session AR](images/unreal-uxt/3-arsessionconfig.PNG)

Une fois cette opération effectuée, l’étape suivante consiste à faire en sorte que la session de réalité augmentée démarre et s’arrête quand le niveau se charge et se termine. Unreal comprend un blueprint spécial appelé **Level Blueprint** (« Blueprint de niveau ») qui joue le rôle de graphe d’événements global à l’échelle du niveau. Le fait de connecter la ressource ARSessionConfig dans le **blueprint de niveau** garantit que la session de réalité augmentée se déclenchera juste au début du jeu.

1. Cliquez sur **Blueprints > Open Level Blueprint** (Blueprints > Ouvrir le blueprint de niveau) dans la barre d’outils de l’éditeur :

![Ouverture du blueprint de niveau](images/unreal-uxt/3-level-blueprint.PNG)

5. Faites glisser le nœud d’exécution (icône représentant une flèche vers la gauche) à partir de **Event BeginPlay** et relâchez le bouton, puis recherchez le nœud **Start AR Session** et appuyez sur Entrée.  
    * Cliquez sur la liste déroulante **Select Asset** (Sélectionner une ressource) sous **Session Config** (Configuration de la session), puis sélectionnez la ressource **ARSessionConfig**.

![Démarrer la session AR](images/unreal-uxt/3-start-ar-session.PNG)

6. Cliquez avec le bouton droit n’importe où dans l’EventGraph et créez un nœud **Event EndPlay**. Faites glisser la broche d’exécution et relâchez le bouton, puis recherchez le nœud **Stop AR Session** et appuyez sur Entrée. Si la session de réalité augmentée est toujours en cours quand le niveau se termine, certaines fonctionnalités peuvent cesser de fonctionner si vous redémarrez votre application lors du streaming sur un casque.
    * Cliquez sur **Compile**, puis sur **Save** pour revenir à la fenêtre principale.

![Arrêter la session AR](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>Créer un Pawn

À ce stade, le projet a toujours besoin d’un objet de lecteur. Dans Unreal, un pion (**Pawn**) représente l’utilisateur dans le jeu, mais ici, il s’agira de l’expérience HoloLens 2.

1. Cliquez sur **Add New > Blueprint Class** (Ajouter > Classe de blueprint) dans le dossier **Content**, puis développez la section **All Classes** située en bas.
    * Recherchez **DefaultPawn**, cliquez sur **Select**, nommez-le **MRPawn**, puis double-cliquez sur la ressource pour l’ouvrir.

![Créer un Pawn héritant de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2. Cliquez sur **Add Component > Camera** dans le panneau **Components** et nommez le composant **Camera**. Vérifiez que le composant **Camera** est un enfant direct de la racine (**CollisionComponent**). Cela permet à la caméra du joueur de se déplacer avec l’appareil HoloLens 2.

> [!NOTE]
> Par défaut, les pions (Pawns) ont des composants de maillage et de collision. Dans la plupart des projets Unreal, les pions sont des objets solides qui peuvent entrer en collision avec d’autres composants. Étant donné que le pion et l’utilisateur sont une seule et même entité dans la réalité mixte, vous devez pouvoir passer par des hologrammes sans aucune collision.

3. Sélectionnez **CollisionComponent** dans le panneau **Components**, puis faites défiler jusqu’à la section **Collision** du panneau **Details**.
    * Cliquez sur la liste déroulante **Collision Presets** (Valeurs prédéfinies de collision), puis remplacez la valeur par **NoCollision**.
    * Répétez cette opération pour **MeshComponent**.

![Changer la valeur Pawn dans Collision Presets](images/unreal-uxt/3-nocollision.PNG)

4. **Compilez** et **enregistrez** le blueprint.

Une fois votre travail terminé, revenez à la fenêtre principale.

## <a name="create-a-game-mode"></a>Créer un mode de jeu

La dernière étape de configuration de la réalité mixte est le mode Jeu. Le mode Jeu (Game Mode) définit plusieurs paramètres du jeu ou de l’expérience, y compris le pion par défaut à utiliser.

1.  Cliquez sur **Add New > Blueprint Class** dans le dossier **Content**, puis sélectionnez **Game Mode Base** comme classe parente. Nommez-la **MRGameMode**, puis double-cliquez dessus pour l’ouvrir.

![MRGameMode dans le navigateur de contenu](images/unreal-uxt/3-gamemode.PNG)

2.  Accédez à la section **Classes** dans le panneau **Details**, puis définissez **Default Pawn Class** (Classe du pion par défaut) sur **MRPawn**.
    * Cliquez sur **Compile**, puis sur **Save** pour revenir à la fenêtre principale.

![Définir l’option Default Pawn Class](images/unreal-uxt/3-setpawn.PNG)

3.  Sélectionnez **Edit > Projects Settings** (Modifier > Paramètres du projet), puis cliquez sur **Maps & Modes** (Cartes et modes) dans la liste de gauche.
    * Développez **Default Modes** (Modes par défaut), puis définissez **Default Game Mode** (Mode Jeu par défaut) sur **MRGameMode**.
    * Développez **Default Maps** (Cartes par défaut), puis définissez **EditorStartupMap** et **GameDefaultMap** sur **Main**. Quand vous fermez puis que vous rouvrez l’éditeur ou quand vous faites une partie, la carte principale (Main) est maintenant sélectionnée par défaut.

![Project Settings - Maps & Modes](images/unreal-uxt/3-mapsandmodes.PNG)

Une fois le projet entièrement configuré pour la réalité mixte, vous êtes prêt à passer au tutoriel suivant et à ajouter une entrée utilisateur à la scène.

[Section suivante : 4. Rendre votre scène interactive](unreal-uxt-ch4.md)
