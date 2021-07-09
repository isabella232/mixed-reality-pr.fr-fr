---
title: 2. Initialisation de votre projet et de votre première application
description: Partie 2 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: f7cf43e8f1c040660b6a2688e234a271bc071b00
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712644"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Initialisation de votre projet et de votre première application

Dans le premier tutoriel, vous allez commencer avec un nouveau projet Unreal et activer le plug-in HoloLens, créer et éclairer un niveau, et ajouter des pièces du jeu d’échecs. Vous allez utiliser des ressources prédéfinies pour tous les objets 3D et les matériaux : vous n’avez donc rien à modéliser vous-même. À la fin de ce tutoriel, vous disposerez d’un canevas vide prêt pour la réalité mixte.

> [!IMPORTANT]
> Vérifiez que vous avez tous les prérequis mentionnés dans la page [Bien démarrer](/windows/mixed-reality/unreal-uxt-ch1).

## <a name="objectives"></a>Objectifs

* Configuration d’un projet Unreal pour le développement HoloLens
* Importation de ressources et configuration d’une scène
* Création d’acteurs et d’événements au niveau du script avec des blueprints

## <a name="creating-a-new-unreal-project"></a>Création d’un projet Unreal

La première chose dont vous avez besoin est un projet avec lequel travailler. Si vous commencez juste à développer dans Unreal, vous devez [télécharger les fichiers de prise en charge](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) auprès d’Epic Launcher.

1. Lancer Unreal Engine

2. Sélectionnez **Games** dans **New Project Categories**, puis cliquez sur **Next**. 

![Sélectionner le modèle de projet Games](images/unreal-uxt/2-gamestemplate.png)

3. Sélectionnez le modèle **Blank**, puis cliquez sur **Next**. 

![Sélectionner le modèle Blank](images/unreal-uxt/2-template.PNG)

4. Définissez **C++** , **Scalable 3D or 2D, Mobile/Tablet** et **No Starter Content** dans **Project Settings**, puis choisissez un emplacement d’enregistrement et cliquez sur **Create Project**. 

> [!NOTE]
> Vous devez sélectionner un projet C++ plutôt qu’un projet Blueprint afin de générer le plug-in UX Tools, que vous configurerez plus loin dans la section 4.

![Paramètres du projet initial](images/unreal-uxt/2-project-settings.PNG)

Le projet doit s’ouvrir automatiquement dans l’éditeur Unreal, ce qui signifie que vous êtes prêt à passer à la section suivante.

## <a name="enabling-required-plugins"></a>Activation des plug-ins nécessaires

Pour utiliser les fonctionnalités disponibles via la plateforme de réalité mixte de Microsoft, vous devez d’abord installer et activer le plug-in Microsoft OpenXR. Pour en savoir plus sur le plug-in, consultez le projet sur [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).

1. Ouvrez le lanceur Epic Games. Accédez à la marketplace Unreal Engine et recherchez « [Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239) ». Installez le plug-in sur votre moteur.

![Marketplace Unreal](images/unreal-uxt/2-openxr-plugin.PNG)

2. De retour dans l’éditeur Unreal, accédez à **Paramètres du projet** > **Plug-ins** et recherchez « Microsoft OpenXR ». Vérifiez que le plug-in est activé et redémarrez l’éditeur si vous y êtes invité.

![Activation du plug-in Microsoft OpenXR](images/unreal-uxt/2-enable-plugin.PNG)

L’activation du plug-in Microsoft OpenXR active automatiquement tous les autres plug-ins requis pour le développement de la réalité mixte. Notez que le plug-in « Microsoft Windows Mixed Reality » doit être désactivé pour pouvoir utiliser OpenXR. 

## <a name="creating-a-level"></a>Création d’un niveau
La tâche suivante consiste à créer une configuration de joueur avec un point de départ, et un cube pour la référence et la mise à l’échelle.

1. Sélectionnez **File > New Level**, puis choisissez **Empty Level**. La scène par défaut dans la fenêtre d’affichage doit maintenant être vide.

2. Sélectionnez **Basic** sous l’onglet **Modes**, puis faites glisser **PlayerStart** dans la scène. 
    * Définissez **Location** sur **X = 0**, **Y = 0** et **Z = 0** dans l’onglet **Details** pour définir l’utilisateur au centre de la scène lors du démarrage de l’application.

![Fenêtre d’affichage avec PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. Faites glisser un **cube** à partir de l’onglet **Basic** dans la scène. 
    * Affectez à **Location** les valeurs **X = 50**, **Y = 0** et **Z = 0**. pour placer le cube à 50 cm du joueur au moment du démarrage. 
    * Affectez à **Scale** les valeurs **X = 0,2**, **Y = 0,2** et **Z = 0,2** pour réduire le cube. 

Vous ne pouvez pas voir le cube, sauf si vous ajoutez une lumière à votre scène, ce qui constitue votre dernière tâche avant de tester la scène.

4. Passez à l’onglet **Lights** dans le panneau **Modes**, puis faites glisser un **Directional Light** dans la scène. Placez la lumière au-dessus de **PlayerStart** pour pouvoir la voir.

![Fenêtre d’affichage avec une lumière ajoutée](images/unreal-uxt/2-light.PNG)

5. Accédez à **File > Save Current**, nommez votre niveau **Main**, puis sélectionnez **Save**. 

Une fois la scène définie, appuyez sur **Play** dans la barre d’outils pour voir votre cube en action ! Lorsque vous avez fini d’admirer votre travail, appuyez sur **Échap** pour arrêter l’application.

![Un cube dans la fenêtre d’affichage](images/unreal-uxt/2-cube.PNG)

Maintenant que la scène est configurée, vous pouvez commencer à y ajouter l’échiquier et la pièce pour compléter l’environnement de l’application.

## <a name="importing-assets"></a>Importation de ressources
La scène a l’air un peu vide pour le moment, mais vous allez y remédier en important les ressources prêtes à l’emploi dans le projet.

1. Téléchargez et décompressez le dossier des ressources [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) avec [7-zip](https://www.7-zip.org/).

2. Sélectionnez **Add New > New Folder** à partir du **Content Browser** et nommez ce dossier **ChessAssets**. 
    * Double-cliquez sur le nouveau dossier où vous allez importer les ressources 3D.

![Afficher ou masquer le panneau des sources](images/unreal-uxt/2-showhidesources.PNG)

3. Sélectionnez **Import** à partir du **Content Browser**, sélectionnez tous les éléments inclus dans le dossier des ressources décompressé, puis cliquez sur **Open**. 
    * Les ressources incluent les maillages d’objets 3D pour l’échiquier et les pièces au format FBX ainsi que les cartes de texture au format TGA que vous allez utiliser pour les matériaux.  

4. Lorsque la fenêtre FBX Import Options s’affiche, développez la section **Material** et affectez à **Material Import Method** la valeur **Do Not Create Material**.
    * Sélectionnez **Import All**.

![Options d’importation FBX](images/unreal-uxt/2-nocreatemat.PNG)

C’est tout ce que vous devez faire pour les ressources. Votre prochaine série de tâches consiste à créer les composants de l’application avec des blueprints.

## <a name="adding-blueprints"></a>Ajout de blueprints

1. Sélectionnez **Add New > New Folder** dans le **Content Browser** et nommez ce dossier **Blueprints**. 

> [!NOTE]
> Si vous ne connaissez pas les [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), il s’agit de ressources spéciales qui fournissent une interface basée sur des nœuds pour créer des types d’acteurs et d’événements au niveau des scripts. 

2. Double-cliquez dans le dossier **Blueprints**, puis cliquez avec le bouton droit et sélectionnez **Blueprint Class**.         
    * Sélectionnez **Actor** et nommez le blueprint **Board**. 

![Sélectionner une classe parente pour votre blueprint](images/unreal-uxt/2-bpparent.PNG)

Le nouveau blueprint **Board** apparaît maintenant dans le dossier **Blueprints**, comme l’illustre la capture d’écran suivante. 

![Le nouveau blueprint Board](images/unreal-uxt/2-bpboard.PNG)

Vous êtes fin prêt pour commencer à ajouter des matériaux aux objets créés.

## <a name="working-with-materials"></a>Utilisation de matériaux
Les objets que vous avez créés sont gris par défaut, ce qui n’est pas très agréable à regarder. L’ajout de matériaux et de maillages à vos objets constitue la dernière série de tâches de ce tutoriel.

1. Double-cliquez sur **Board** pour ouvrir l’éditeur de blueprint. 

2. Sélectionnez **Add Component > Scene** dans le panneau **Components** et nommez-le composant **Root**. Notez que **Root** apparaît en tant qu’enfant de **DefaultSceneRoot** dans la capture d’écran ci-dessous :

![Remplacement de root dans le blueprint](images/unreal-uxt/2-root-blueprint.PNG)


3. Cliquez et faites glisser **Root** sur **DefaultSceneRoot** pour le remplacer et vous débarrasser de la sphère dans la fenêtre d’affichage. 

![Remplacement de la racine](images/unreal-uxt/2-root.PNG)


4. Sélectionnez **Add Component > Static Mesh** dans le panneau **Components** et nommez le composant **SM_Board**. Il apparaît en tant qu’objet enfant sous **Root**.

![Ajout d’un maillage statique](images/unreal-uxt/2-sm-board.PNG)

4. Sélectionnez **SM_Board**, faites défiler vers le bas jusqu’à la section **Static Mesh** du panneau **Details**, puis sélectionnez **ChessBoard** dans la liste déroulante. 

![Le maillage de l’échiquier dans la fenêtre d’affichage](images/unreal-uxt/2-sm-board-view.PNG)

5.  Toujours dans le panneau **Details**, développez la section **Materials**, puis sélectionnez **Create New Asset > Material** dans la liste déroulante. 
    * Nommez le matériau **M_ChessBoard** et enregistrez-le dans le dossier **ChessAssets**. 

![Créer un matériau](images/unreal-uxt/2-newmat.PNG)

6.  Double-cliquez sur l’image du matériau **M_ChessBoard** pour ouvrir l’éditeur de matériau. 

![Ouvrir l’éditeur de matériau](images/unreal-uxt/2-material-editor.PNG)

7. Dans l’éditeur de matériau, cliquez avec le bouton droit et recherchez **Texture Sample**. 
    * Développez la section **Material Expression Texture Base** dans le panneau **Details** et affectez à **Texture** la valeur **ChessBoard_Albedo**. 
    * Faites glisser le repère de sortie **RGB** vers le repère Base Color de **M_ChessBoard**. 

![Définir la couleur de base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  Répétez l’étape précédente 4 fois de plus pour créer quatre autres nœuds **Texture Sample** avec les paramètres suivants :
    * Affectez à **Texture** la valeur **ChessBoard_AO** et liez le repère **RGB** au repère **Ambient Occlusion**.
    * Affectez à **Texture** la valeur **ChessBoard_Metal** et liez le repère **RGB** au repère **Metallic**. 
    * Affectez à **Texture** la valeur **ChessBoard_Normal** et liez le repère **RGB** au repère **Normal**.
    * Affectez à **Texture** la valeur **ChessBoard_Rough** et liez le repère **RGB** au repère **Roughness**. 
    * Cliquez sur **Enregistrer**. 

![Raccorder les textures restantes](images/unreal-uxt/2-boardmat.PNG)

Vérifiez que la configuration de votre matériau ressemble à la capture d’écran ci-dessus.

## <a name="populating-the-scene"></a>Remplissage de la scène
Si vous revenez au blueprint **Board**, vous voyez que le matériau que vous venez de créer a été appliqué. Il ne vous reste plus qu’à installer la scène ! Pour commencer, modifiez les propriétés suivantes pour vous assurer que l’échiquier est de taille raisonnable et qu’il est correctement incliné lorsqu’il est placé dans la scène :
1.  Affectez à **Scale** la valeur **(0,05, 0,05, 0,05)** et à **Z Rotation** la valeur **90**. 
    * Cliquez sur **Compile** dans la barre d’outils supérieure, puis sur **Save** pour revenir à la fenêtre Main. 

![Échiquier avec un matériau appliqué](images/unreal-uxt/2-chessboard.PNG)

2.  Cliquez avec le bouton droit sur **Cube > Edit > Delete**, puis faites glisser **Board** depuis le **Content Browser** dans la fenêtre d’affichage. 
    * Affectez à **Location** les valeurs **X = 80**, **Y = 0** et **Z = -20**. 

3.  Sélectionnez le bouton **Play** pour visualiser votre nouvel échiquier dans le niveau. Appuyez sur **Échap** pour revenir à l’éditeur. 

À présent, vous allez suivre les mêmes étapes pour créer une pièce de jeu d’échecs que celles que vous avez effectuées pour l’échiquier :

1. Accédez au dossier **Blueprints**, cliquez avec le bouton droit et sélectionnez **Blueprint Class**, puis choisissez **Actor**. Nommez cet acteur **WhiteKing**.

2. Double-cliquez sur **WhiteKing** pour l’ouvrir dans l’éditeur de blueprint, sélectionnez **Add Component > Scene** et nommez-le **Root**. 
    * Glissez-déposez **Root** dans **DefaultSceneRoot** pour le remplacer. 

3. Cliquez sur **Add Component > Static Mesh** et nommez ce composant **SM_King**. 
    * Affectez à **Static Mesh** la valeur **Chess_King** et à **Material** la valeur d’un nouveau matériau appelé **M_ChessWhite** dans le panneau Details. 

4. Ouvrez **M_ChessWhite** dans l’éditeur de matériau et raccordez les nœuds **Texture Sample** suivants aux éléments suivants :
   * Affectez à **Texture** la valeur **ChessWhite_Albedo** et liez le repère **RGB** au repère **Base Color**.
    * Affectez à **Texture** la valeur **ChessWhite_AO** et liez le repère **RGB** au repère **Ambient Occlusion**.
    * Affectez à **Texture** la valeur **ChessWhite_Metal** et liez le repère **RGB** au repère **Metallic**. 
    * Affectez à **Texture** la valeur **ChessWhite_Normal** et liez le repère **RGB** au repère **Normal**.
    * Affectez à **Texture** la valeur **ChessWhite_Rough** et liez le repère **RGB** au repère **Roughness**. 
    * Cliquez sur **Enregistrer**. 

Votre matériau **M_ChessKing** doit ressembler à l’image suivante avant de continuer.

![Créer le matériau pour le roi](images/unreal-uxt/2-chesskingmat.PNG)

Vous y êtes presque, il vous suffit d’ajouter la nouvelle pièce à la scène : 

1. Ouvrez le blueprint **WhiteKing** et affectez à **Scale** la valeur **(0,05, 0,05, 0,05)** et à **Z Rotation** la valeur **90**.
    * Compilez et enregistrez votre blueprint, puis revenez à la fenêtre principale. 

2.  Faites glisser **WhiteKing** dans la fenêtre d’affichage, basculez vers le panneau **World Outliner**, faites glisser **WhiteKing** sur **Board** pour en faire un objet enfant.

![World Outliner](images/unreal-uxt/2-child.PNG)

3.  Dans le panneau **Details** sous **Transform**, affectez au paramètre **Location** de **WhiteKing** les valeurs **X = -26**, **Y = 4** et **Z = 0**.

C’est terminé ! Sélectionnez **Play** pour voir votre niveau rempli en action, puis appuyez sur **Échap** quand vous êtes prêt à quitter. Vous avez abordé de nombreux points liés à la création d’un projet simple, mais vous êtes maintenant prêt à passer à la partie suivante de la série : la configuration pour la réalité mixte. 

[Section suivante : 3. Configurer votre projet pour la réalité mixte](unreal-uxt-ch3.md)