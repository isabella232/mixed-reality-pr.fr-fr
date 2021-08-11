---
title: Création de votre première application HoloLens Unreal
description: Découvrez comment configurer correctement un projet Unreal avec des objets de scène et des interactions d’entrée pour le développement de réalité mixte HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, éditeur Unreal, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, portage, mise à niveau
ms.openlocfilehash: 07ec2760d691938015619d097d214d205cdbab78f250ff9dd8a793dd27f10c4a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209567"
---
# <a name="creating-your-first-hololens-unreal-application"></a>Création de votre première application HoloLens Unreal

Ce guide vous permet de créer votre première application de réalité mixte s’exécutant sur HoloLens dans Unreal Engine. Dans la tradition de « Hello World », vous allez créer une application simple qui affiche un cube à l’écran. Pour la rendre plus utile, vous allez également créer votre premier geste pour faire pivoter le cube et pour quitter l’application. 

## <a name="objectives"></a>Objectifs

* Démarrer un projet HoloLens
* Activer les plug-ins corrects
* Créer une ressource de données ARSessionConfig
* Configurer les entrées de geste
* Créer un niveau de base
* Implémenter un geste de pincement

## <a name="creating-a-new-project"></a>Création d’un projet

La première chose dont vous avez besoin est un projet avec lequel travailler. Si vous commencez juste à développer dans Unreal, vous devez [télécharger les fichiers de prise en charge](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) auprès d’Epic Launcher.

1. Lancer Unreal Engine
2. Dans **New Project Categories**, sélectionnez **Games**, puis cliquez sur **Next** :

![Fenêtre des projets récents ouverte avec Games mis en évidence](images/unreal-quickstart-img-01.png)

3. Sélectionnez le modèle **Blank**, puis cliquez sur **Next** :

![Fenêtre du navigateur de projet Unreal avec le modèle Blank mis en évidence](images/unreal-quickstart-img-02.png)

4. Dans **Project Settings**, définissez **C++, Scalable 3D or 2D, Mobile/Tablet** et **No Starter Content**, puis choisissez un emplacement d’enregistrement et cliquez sur **Create Project**.

> [!NOTE] 
> Vous utilisez un projet C++ au lieu d’un projet Blueprint pour être prêt à utiliser le plug-in OpenXR ultérieurement. Ce guide de démarrage rapide utilise le plug-in OpenXR par défaut qui est fourni avec Unreal Engine. Il est cependant recommandé de télécharger et d’utiliser le plug-in Microsoft OpenXR officiel. Cela nécessite que le projet soit un projet C++.

![Fenêtre des paramètres de projet avec les choix pour le projet, les performances, la plateforme cible et le contenu au démarrage mis en évidence](images/unreal-quickstart-img-03.png)

Votre nouveau projet doit s’ouvrir automatiquement dans l’éditeur Unreal, ce qui signifie que vous êtes prêt à passer à la section suivante.

## <a name="enabling-required-plugins"></a>Activation des plug-ins nécessaires

Vous devez activer deux plug-ins pour pouvoir commencer à ajouter des objets à la scène.

1. Ouvrez **Edit > Plugins** et sélectionnez **Augmented Reality** dans la liste des options prédéfinies.
* Faites défiler vers le bas jusqu’à **HoloLens** et cochez la case **Enabled**.

![Fenêtre des plug-ins avec la section de la réalité augmentée ouverte et HoloLens mis en évidence](images/unreal-quickstart-img-04.png)

2. Tapez **OpenXR** dans la zone de recherche en haut à droite et activez les plug-ins **OpenXR** et **OpenXRMsftHandInteraction** :

![Fenêtre des plug-ins avec OpenXR activé](images/unreal-quickstart-img-05.jpg)

![Fenêtre des plug-ins avec Open XR Msft Hand Interaction activé](images/unreal-quickstart-img-06.jpg)

3. Redémarrer votre éditeur

> [!NOTE]
> Ce tutoriel utilise OpenXR, mais les deux plug-ins que vous avez installés ci-dessus ne fournissent actuellement pas l’ensemble complet de fonctionnalités pour le développement HoloLens. Le plug-in HandInteraction sera suffisant pour le geste de pincement que vous allez utiliser plus tard, mais si vous voulez aller plus loin, vous devez [télécharger le plug-in OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).

Une fois les plug-ins activés, vous pouvez vous concentrer sur le remplissage du contenu.

## <a name="creating-a-level"></a>Création d’un niveau

La tâche suivante consiste à créer une configuration de joueur avec un point de départ, et un cube pour la référence et la mise à l’échelle.

1. Sélectionnez **File > New Level**, puis choisissez **Empty Level**. La scène par défaut dans la fenêtre d’affichage doit maintenant être vide.
2. Sous l’onglet **Mode**, sélectionnez **Basic**, puis faites glisser **PlayerStart** dans la scène.
* Sous l’onglet **Details**, définissez **Location** sur **X = 0, Y = 0** et **Z = 0** pour placer l’utilisateur au centre de la scène lors du démarrage de l’application.

![Scène de l’éditeur Unreal avec l’emplacement et le joueur ajoutés](images/unreal-quickstart-img-07.png)

3. Sous l’onglet **Basic**, faites glisser un **Cube** dans la scène.
* Définissez **Location** pour le cube sur **X = 50, Y = 0** et **Z = 0** pour positionner le cube à 50 cm du joueur au démarrage.
* Changez **Scale** pour le cube en **X = 0,2, Y = 0,2** et **Z = 0,2**. 

Vous ne pouvez pas voir le cube, sauf si vous ajoutez une lumière à votre scène, ce qui constitue votre dernière tâche avant de tester la scène.

4. Dans le panneau **Modes**, passez à l’onglet **Lights**, puis faites glisser une **Directional Light** dans la scène.
* Positionnez la lumière au-dessus de **PlayerStart** pour pouvoir la voir.

![Scène de l’éditeur Unreal avec le cube et la lumière directionnelle ajoutés](images/unreal-quickstart-img-08.png)

5. Accédez à **File > Save Current**, nommez votre niveau **Main**, puis sélectionnez **Save**.

Une fois la scène définie, appuyez sur **Play** dans la barre d’outils pour voir votre cube en action ! Lorsque vous avez fini d’admirer votre travail, appuyez sur Échap pour arrêter l’application.

![Scène en mode lecture avec le cube au milieu de l’écran](images/unreal-quickstart-img-09.png)

Maintenant que la scène est configurée, préparons-la pour quelques interactions simples dans AR. Tout d’abord, vous devez créer une session AR, et vous pouvez aussi ajouter des blueprints pour permettre une interaction manuelle.

## <a name="adding-a-session-asset"></a>Ajout d’une ressource de session

Les sessions de réalité augmentée n’arrivent pas toutes seules. Pour utiliser une session, vous devez créer une ressource de données ARSessionConfig, ce qui est d’ailleurs votre tâche suivante :

1. Dans le **Content Browser**, sélectionnez **Add New > Miscellaneous > Data Asset** et vérifiez que vous êtes au niveau du dossier Content racine.
2. Sélectionnez **ARSessionConfig**, cliquez sur **Select**, puis nommez la ressource **ARSessionConfig** :

![Fenêtre de sélection d’une classe de ressources de données ouverte avec la ressource de configuration de session AR mise en évidence](images/unreal-quickstart-img-10.png)

2. Double-cliquez sur **ARSessionConfig** pour l’ouvrir, choisissez **Save** avec toutes les valeurs par défaut, puis revenez à la fenêtre principale :

![Fenêtre des détails des ressources de configuration de session AR](images/unreal-quickstart-img-11.png)

Une fois cette opération effectuée, l’étape suivante consiste à faire en sorte que la session de réalité augmentée démarre et s’arrête quand le niveau se charge et se termine. Unreal comprend un blueprint spécial appelé **Level Blueprint** (« Blueprint de niveau ») qui joue le rôle de graphe d’événements global à l’échelle du niveau. Le fait de connecter la ressource ARSessionConfig dans le blueprint de niveau garantit que la session de réalité augmentée se déclenchera juste au début du jeu.

3. Dans la barre d’outils de l’éditeur, sélectionnez **Blueprints > Open Level Blueprint** :

![Menu Blueprint ouvert avec l’option Open Level Blueprint en évidence](images/unreal-quickstart-img-12.png)

4. Faites glisser le nœud d’exécution (la flèche pointant vers la gauche) en dehors de **Event BeginPlay**, puis relâchez.
* Recherchez le **nœud Start AR Session**, puis appuyez sur Entrée.
* Cliquez sur la liste déroulante **Select Asset** sous **Session Config**, puis sélectionnez la ressource **ARSessionConfig**.

![Graphique de blueprint avec Event BeginPlay connecté à la fonction Start AR Session](images/unreal-quickstart-img-13.png)

5. Cliquez avec le bouton droit n’importe où dans l’EventGraph et créez un nœud **Event EndPlay**. 
* Faites glisser la broche d’exécution et relâchez le bouton, puis recherchez le nœud **Stop AR Session** et appuyez sur Entrée. 
* Cliquez sur **Compile**, puis sur **Save**, et revenez à la fenêtre principale.

> [!IMPORTANT]
> Si la session de réalité augmentée est toujours en cours quand le niveau se termine, certaines fonctionnalités peuvent cesser de fonctionner si vous redémarrez votre application lors du streaming sur un casque.

![Nœud Event EndPlay attaché à la fonction Stop AR Session](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>Configuration des entrées

1. Sélectionnez **Edit > Project Settings**, puis accédez à **Engine > Input**.
2. Sélectionnez l’icône **+** à côté de **Action Mappings**, puis créez des actions **RightPinch** et **LeftPinch** :

![Liaison des paramètres d’entrée avec les mappages des actions de pincement droit et gauche mis en évidence](images/unreal-quickstart-img-15.jpg)

3. Mappez les actions **RightPinch** et **LeftPinch** aux actions **OpenXR Msft Hand Interaction** correspondantes :

![Mappages d’actions avec les options Open XR Msft Hand Interaction en évidence](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>Configuration des gestes

Maintenant que nous avons configuré les entrées, nous pouvons accéder à la partie intéressante : L’ajout de gestes ! Faisons pivoter le cube sur le pincement à droite et quitter l’application sur le pincement à gauche.

1. Ouvrez le **Level Blueprint** et ajoutez un **InputAction RightPinch** et un **InputAction LeftPinch**.
* Connectez l’événement pincement droit à une **AddActorLocalRotation** avec votre **Cube**  comme cible, et **Delta Rotation** défini sur **X = 0, Y = 0** et **Z = 20**. Le cube va maintenant pivoter de 20 degrés chaque fois que vous pincez.
* Connectez l’événement de pincement gauche à **Quit Game**.

![Blueprint de niveau ouvert avec des actions d’entrée pour les événements de pincement droit et gauche](images/unreal-quickstart-img-17.jpg)

2. Dans les paramètres **Transform** du cube, définissez **Mobility** sur **Movable** pour qu’il puisse se déplacer dynamiquement :

![Paramètres de transformation avec la propriété de mobilité mis en évidence](images/unreal-quickstart-img-18.jpg)

À ce stade, vous êtes prêt à déployer et à tester l’application !