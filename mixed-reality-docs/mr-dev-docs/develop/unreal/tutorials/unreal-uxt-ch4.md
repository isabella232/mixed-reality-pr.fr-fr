---
title: 4. Rendre votre scène interactive
description: Partie 4 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 74d4fb7ebab2f5ba2df477cc29d8787367c1f105cc7a65d87460ac1e033b0fbb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203778"
---
# <a name="4-making-your-scene-interactive"></a>4. Rendre votre scène interactive

Dans le tutoriel précédent, vous avez ajouté une session de réalité augmentée (ARSession), un pion (Pawn) et un mode Jeu (Game Mode) pour finaliser la configuration de réalité mixte de l’application de jeu d’échecs. Cette section se concentre sur l’utilisation du plug-in open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), qui fournit des outils permettant de rendre une scène interactive. À la fin de cette section, les pièces de votre jeu d’échecs se déplaceront en fonction des entrées utilisateur.

## <a name="objectives"></a>Objectifs

* Installation du plug-in Mixed Reality UX Tools
* Ajout d’acteurs d’interaction manuelle à vos doigts
* Création et ajout de manipulateurs aux objets de la scène
* Utilisation de la simulation d’entrée pour valider le projet

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a>Téléchargement du plug-in Mixed Reality UX Tools
Avant de commencer à utiliser les entrées d’utilisateur, vous devez ajouter le plug-in Mixed Reality UX Tools au projet. Pour en savoir plus sur UX Tools, vous pouvez consulter le projet sur [GitHub](https://aka.ms/uxt-unreal).

1. Ouvrez le lanceur Epic Games. Accédez à la marketplace Unreal Engine et recherchez « [Mixed Reality UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools) ». Installez le plug-in sur votre moteur.

![Marketplace Unreal](images/unreal-uxt/2-uxt-plugin.PNG)

2. De retour dans l’éditeur Unreal, accédez à **Paramètres du projet** > **Plug-ins** et recherchez « Mixed Reality UX Tools ». Vérifiez que le plug-in est activé et redémarrez l’éditeur si vous y êtes invité.

![Activation du plug-in Mixed Reality UX Tools](images/unreal-uxt/2-enable-uxt.PNG)

3.  Le plug-in UXTools comprend un dossier Contenu avec des sous-dossiers pour les composants, notamment **Boutons**, **Simulation XR** et **Pointeurs**, ainsi qu’un dossier Classes C++ avec du code supplémentaire.  

> [!NOTE]
> Si vous ne voyez pas la section **Contenu UXTools** dans le **Navigateur de contenu**, cliquez sur **Afficher les options > Afficher le contenu du plug-in**.

![Afficher le contenu du moteur](images/unreal-uxt/4-showenginecontent.PNG)

Vous trouverez de la documentation supplémentaire sur le plug-in dans le [dépôt](https://aka.ms/uxt-unreal) GitHub de Mixed Reality UX Tools.

Une fois le plug-in installé, vous pouvez commencer à utiliser les outils qu’il propose, en commençant par les acteurs d’interaction manuelle.

## <a name="spawning-hand-interaction-actors"></a>Génération d’acteurs d’interaction manuelle

L’interaction manuelle avec les éléments de l’expérience utilisateur se fait avec des acteurs d’interaction manuelle qui créent et pilotent les pointeurs et les visuels pour les interactions proches et lointaines.
- *Interactions proches* : en pinçant des éléments entre le pouce et l’index, ou en les poussant du bout du doigt.
- *Interactions lointaines* : en pointant le rayon émanant de la main virtuelle sur un élément, et en appuyant simultanément avec l’index et le pouce.

Dans le cas présent, l’ajout d’un acteur d’interaction manuelle à **MRPawn** va :
- Ajouter un curseur au bout de l’index du pion (Pawn)
- Fournir des événements d’entrées manuelles articulées qui peuvent être manipulés par le pion
- Autoriser les événements d’entrées d’interactions lointaines effectuées à l’aide des rayons qui émanent de la paume de la main virtuelle

Avant de continuer, nous vous recommandons de lire la [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) sur les interactions manuelles.

Lorsque vous êtes prêt, ouvrez le blueprint **MRPawn** et accédez à **Event Graph**.

1. Faites glisser puis relâchez la broche d’exécution à partir de **Event BeginPlay** pour placer un nouveau nœud.
    * Sélectionnez **Spawn Actor from Class** (Générer un acteur à partir d’une classe), cliquez sur la liste déroulante à côté de la broche **Class**, puis recherchez **Uxt Hand Interaction Actor**.  

2. Générez un deuxième **Uxt Hand Interaction Actor**, mais cette fois-ci, choisissez la main droite. Pour cela, définissez **Hand** avec la valeur **Right**. Lorsque l’événement démarre, un acteur d’interaction manuelle Uxt est généré pour chaque main.

Votre graphe d’événements (**Event Graph**) doit correspondre à la capture d’écran suivante :

![Générer des acteurs d’interaction manuelle UXT](images/unreal-uxt/4-spawnactor.PNG)

Les deux acteurs d’interaction manuelle Uxt ont besoin de propriétaires et d’emplacements de transformation initiale. La transformation initiale n’a pas d’importance dans ce cas, car les Acteurs d’interaction manuelle utiliseront les Outils UX pour accéder aux mains virtuelles dès qu’elles seront visibles. Toutefois, la fonction `SpawnActor` nécessite une entrée de transformation pour éviter une erreur du compilateur. Vous devez donc utiliser les valeurs par défaut.

1. Faites glisser puis relâchez la broche de l’une des broches **Spawn Transform** pour placer un nouveau nœud.
    * Recherchez le nœud **Make Transform** (Effectuer une transformation), puis faites glisser la valeur de retour (**Return Value**) vers le **Spawn Transform** de l’autre main, afin que les deux nœuds **SpawnActor** soient connectés.

2.  Sélectionnez la **flèche bas** située en bas des deux nœuds **SpawnActor** pour afficher la broche **Owner**.    
    * Faites glisser la broche de l’une des broches **Owner** et relâchez-la pour placer un nouveau nœud.
    * Recherchez **self** et sélectionnez la variable **Get a reference to self**.
    * Créez un lien entre le nœud de référence de l’objet **Self** et la broche **Owner** de l’acteur d’interaction manuelle.
3. Enfin, cochez la case **Show Near Cursor on Grab Targets** pour les deux acteurs d’interaction manuelle. Un curseur doit apparaître sur la cible de préhension quand votre index s’approche, pour vous permettre de voir où est votre doigt par rapport à la cible.
    * **Compilez**, **enregistrez**, puis revenez à la fenêtre principale.

Vérifiez que les connexions correspondent à la capture d’écran suivante ; n’hésitez cependant pas à déplacer les nœuds pour rendre votre blueprint plus lisible.

![Effectuer la configuration de l’acteur d’interaction manuelle UXT](images/unreal-uxt/4-fingerptrs.PNG)

Vous trouverez plus d’informations sur les acteurs d’interaction manuelle dans la [documentation UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html).

À présent, les mains virtuelles du projet disposent d’un moyen pour sélectionner des objets. Toutefois, elles ne peuvent toujours pas les manipuler. Avant de tester l’application, la dernière tâche consiste à ajouter des composants Manipulateur aux acteurs de la scène.

## <a name="attaching-manipulators"></a>Ajout de manipulateurs

Un manipulateur est un composant qui répond à une entrée manuelle articulée. Il peut s’agir d’une saisie, d’une rotation ou d’une translation. L’application de la transformation du manipulateur à une transformation d’acteur permet une manipulation directe de l’acteur.

1. Dans le blueprint **Board**, cliquez sur **Add Component** (Ajouter un composant), puis recherchez **Uxt Generic Manipulator**. dans le panneau **Components**.

![Ajouter un manipulateur générique](images/unreal-uxt/4-addmanip.PNG)

2. Développez la section **Generic Manipulator** (Manipulateur générique) dans le panneau **Details**. Vous pouvez définir une manipulation à une ou à deux mains, le mode de rotation, ainsi que l’adoucissage. N’hésitez pas à sélectionner le mode que vous souhaitez, puis **compilez** et **enregistrez** l’échiquier.

![Définir le mode](images/unreal-uxt/4-setrotmode.PNG)

3. Répétez les étapes ci-dessus pour l’acteur **WhiteKing**.

Vous trouverez plus d’informations sur les composants du manipulateur qui sont fournis dans le plug-in Mixed Reality UX Tools dans la [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html).

## <a name="testing-the-scene"></a>Test de la scène

Bonne nouvelle ! Vous êtes prêt à tester l’application avec ses nouvelles mains virtuelles et vos entrées utilisateur. Appuyez sur **Play** dans la fenêtre principale : vous devez voir deux mains maillées avec des rayons émanant de la paume de chaque main. Vous pouvez contrôler les mains et leurs interactions de la façon suivante :
- Maintenez enfoncée la touche **Alt de gauche** pour contrôler la **main gauche**, et la touche **Maj de gauche** pour contrôler la **main droite**.
- Déplacez votre souris pour bouger la main, puis faites défiler avec la **roulette de la souris** pour déplacer la main **vers l’avant** ou **vers l’arrière**.
- Utilisez le bouton gauche de la souris pour **pincer**, et le bouton central de la souris pour **pousser avec le doigt**.

> [!NOTE]
> La simulation d’entrée peut ne pas fonctionner si plusieurs casques sont branchés sur votre ordinateur. Si vous rencontrez des problèmes, essayez de débrancher vos autres casques.

![Mains simulées dans la fenêtre d’affichage](images/unreal-uxt/4-handsim.PNG)

Essayez à présent d’utiliser les mains simulées pour sélectionner, déplacer et déposer le roi blanc du jeu d’échecs et manipuler l’échiquier. Expérimentez les interactions de près et de loin : quand vos mains sont suffisamment proches pour saisir directement l’échiquier et le roi, un curseur au bout de l’index remplace le rayon émanant de la main.

Pour plus d’informations sur les fonctionnalités des mains simulées fournies dans le plug-in UX Tools de MRTK, consultez la [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html).

Maintenant que vos mains virtuelles peuvent interagir avec les objets, vous êtes prêt à passer au tutoriel suivant pour ajouter des interfaces utilisateur et des événements.

[Section suivante : 5. Ajout d’un bouton et réinitialisation des emplacements de pièces](unreal-uxt-ch5.md)
