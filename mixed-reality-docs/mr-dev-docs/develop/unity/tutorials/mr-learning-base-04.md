---
title: Tutoriels sur MRTK - 4. Positionnement des objets dans la scène
description: Ce cours vous montre comment positionner des objets dans la scène et comment utiliser Mixed Reality Toolkit (MRTK) pour organiser les objets dans une grille.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, solveurs, collection d’objets de grille
ms.localizationpriority: high
ms.openlocfilehash: b21f2833067c3496febcf5bdd1cfffe491597e9083845b18e9c220c75d3e7cee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228005"
---
# <a name="4-positioning-objects-in-the-scene"></a>4. Positionnement des objets dans la scène

## <a name="overview"></a>Vue d’ensemble

Dans ce tutoriel, vous allez positionner les objets fournis comme ressources du tutoriel dans la scène.

## <a name="objectives"></a>Objectifs

* Apprendre à positionner des objets dans la scène
* Apprendre à utiliser la fonctionnalité Grid Object Collection du MRTK

## <a name="importing-the-textmeshpro-essential-resources"></a>Importation des ressources TextMeshPro Essential
Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK. Dans le menu Unity, sélectionnez **Window** > **TextMeshPro** > **Import TMP Essential Resources** pour ouvrir la fenêtre Import Unity Package :

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importation des ressources du tutoriel

Téléchargez le package personnalisé Unity suivant. Ce package comprend des ressources 3D, telles que Mars Rover, que nous allons utiliser dans ce tutoriel.

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

Pour importer un package personnalisé Unity, dans le menu Unity, sélectionnez **Assets** > **Import Package** > **Custom Package...** pour ouvrir la fenêtre Import package :

![Importation d’un package personnalisé](images/mr-learning-base/base-02-section7-step1-1.png)

Dans la fenêtre Import package, sélectionnez le package **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que vous avez téléchargé, puis cliquez sur le bouton Open :

![Sélection d’un package de ressources](images/mr-learning-base/base-02-section7-step1-2.png)

Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton Tous pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton Importer pour importer les ressources :

![Sélection de toutes les ressources à importer](images/mr-learning-base/base-02-section7-step1-3.png)

Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :

![Fenêtre de projet Unity après l’importation de ressources](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="creating-the-parent-object"></a>Création de l’objet parent

Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur une zone vide et sélectionnez **Create Empty** pour ajouter un objet vide à votre scène :

![Menu contextuel Create Empty d’Unity](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> Pour afficher côte à côte les fenêtres Scene et Game comme dans l’image ci-dessus, faites glisser la fenêtre Game à droite de la fenêtre Scene. Pour en savoir plus, consultez la page consacrée à la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personnalisation de votre espace de travail</a> dans la documentation Unity.

Cliquez avec le bouton droit sur l’objet que vous venez de créer, sélectionnez **Rename**, puis remplacez le nom par **RoverExplorer** :

![Menu contextuel Rename d’Unity](images/mr-learning-base/base-04-section1-step1-2.png)

L’objet RoverExplorer étant toujours sélectionné, dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :

* **Position** : X = 0, Y = -0.6, Z = 2
* **Rotation** : X = 0, Y = 0, Z = 0
* **Scale** : X = 1, Y = 1, Z = 1

![Unity avec un objet RoverExplorer sélectionné et positionné](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> L’appareil photo, qui représente la tête de l’utilisateur, est positionné à l’origine (X = 0, Y = 0, Z = 0). En règle générale, 1 unité dans Unity correspond à peu près à 1 mètre dans le monde physique. Il y a cependant des exceptions à cela, par exemple quand les objets sont des enfants d’objets mis à l’échelle. Dans le scénario ci-dessus, l’objet RoverExplorer est positionné 2 mètres devant la tête de l’utilisateur et 0,6 mètre en dessous.

## <a name="adding-the-tutorial-prefabs"></a>Ajout des préfabriqués du tutoriel

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** :

![Fenêtre de projet Unity avec le dossier Prefabs sélectionné](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">préfabriqué</a> (Prefab) est un GameObject préconfiguré stocké en tant que ressource Unity et qui peut être réutilisé dans tout votre projet.

Dans la fenêtre Project, cliquez sur le préfabriqué **Table** et faites-le glisser sur l’objet **RoverExplorer** pour en faire un enfant de cet objet, puis dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :

* **Position** : X = 0, Y = -0.005, Z = 0
* **Rotation** : X = 0, Y = 0, Z = 0
* **Scale** : X = 1.2, Y = 0.01, Z = 1.2

![Unity avec le préfabriqué nouvellement ajouté Table, sélectionné et positionné](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> Pour afficher votre scène comme dans l’image ci-dessus, utilisez le <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">gizmo Scene</a> en haut à droite de la fenêtre Scene pour ajuster l’angle de visualisation sur l’axe Z vers l’avant, double-cliquez sur l’objet MixedRealityPlayspace dans la fenêtre Hierarchy pour avoir le focus sur l’appareil photo, puis faites un zoom avant si nécessaire.

Dans la fenêtre Project, cliquez sur le préfabriqué **RoverAssembly** et faites-le glisser sur l’objet **RoverExplorer** pour en faire un enfant de cet objet, puis dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :

* **Position** : X = -0.1, Y = 0, Z = 0
* **Rotation** : X = 0, Y = -135, Z = 0
* **Scale** : X = 1, Y = 1, Z = 1

![Unity avec le préfabriqué nouvellement ajouté RoverAssembly, sélectionné et positionné](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>Organisation des objets dans une collection

Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **RoverExplorer**, puis sélectionnez **Create Empty** pour ajouter un objet vide en tant qu’enfant de RoverExplorer. Nommez l’objet **RoverParts**, puis configurez le composant **Transform** comme ceci :

* **Position** : X = 0, Y = 0.06, Z = 0
* **Rotation** : X = 0, Y = 90, Z = 0
* **Scale** : X = 1, Y = 1, Z = 1

![Unity avec l’objet RoverParts nouvellement créé, sélectionné et positionné](images/mr-learning-base/base-04-section3-step1-1.png)

Dans la fenêtre Hierarchy, sélectionnez tous les objets enfants RoverExplorer > RoverAssembly > RoverModel > **Parts**, cliquez dessus avec le bouton droit, puis sélectionnez **Duplicate** pour créer une copie de chaque élément :

![Unity avec toutes les pièces (Parts) sélectionnées et le menu contextuel Duplicate](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> Pour sélectionner plusieurs objets adjacents, maintenez la touche Maj enfoncée tout en utilisant la souris pour sélectionner le premier et le dernier objet.

Les objets enfants Parts que vous venez de dupliquer étant toujours sélectionnés, cliquez dessus et faites-les glisser sur l’objet **RoverParts** pour en faire des objets enfants de cet objet :

![Unity avec les pièces (parts) nouvellement dupliquées en tant qu’enfants de l’objet RoverParts](images/mr-learning-base/base-04-section3-step1-3.png)

Pour faciliter l’utilisation de votre scène, dans la fenêtre Hierarchy, cliquez sur l’icône **œil** à gauche de l’objet pour désactiver la **visibilité de la scène** pour l’objet **RoverAssembly**. Cette opération masque l’objet dans la fenêtre Scene sans changer sa visibilité dans le jeu :

![Unity avec la visibilité de la scène RoverAssembly désactivée](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> Pour en savoir plus sur les contrôles de visibilité de la scène et sur la façon dont vous pouvez les utiliser pour optimiser l’affichage et le workflow de votre scène, reportez-vous à la documentation <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> d’Unity.

Dans la fenêtre Hierarchy, nettoyez les noms des objets enfants RoverParts en remplaçant le suffixe **(1)** par **_Part** :

![Unity avec le nom des pièces (parts) dupliquées effacé](images/mr-learning-base/base-04-section3-step1-5.png)

Dans la fenêtre Hierarchy, sélectionnez l’objet **RoverParts**. Dans la fenêtre Inspector, cliquez sur le bouton **Add Component**, puis recherchez et sélectionnez **GridObjectCollection** pour ajouter le composant GridObjectCollection à l’objet RoverParts :

![Objet RoverParts d’Unity avec l’ajout du composant de collection d’objets de grille en cours](images/mr-learning-base/base-04-section3-step1-6.png)

Configurez les valeurs du composant **GridObjectCollection** comme ceci :

* **Sort Type** : Alphabetic
* **Layout** : Horizontale
* **Cell Width** : 0.25
* **Distance from parent** : 0.38

![Unity avec le composant GridObjectCollection configuré](images/mr-learning-base/base-04-section3-step1-7.png)

Cliquez ensuite sur le bouton **Update Collection** pour mettre à jour la position des objets enfants de RoverParts :

![Unity avec le composant GridObjectCollection appliqué](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez appris à positionner des objets dans la scène par rapport à l’utilisateur et à utiliser la fonctionnalité Grid Object Collection du MRTK pour organiser les objets dans une collection.

> [!div class="nextstepaction"]
>[Tutoriel suivant : 5. Création de contenu dynamique avec des solveurs](mr-learning-base-05.md)
