---
title: Tutoriels sur MRTK - 4. Positionnement des objets dans la scène
description: Ce cours vous montre comment positionner des objets dans la scène et comment utiliser Mixed Reality Toolkit (MRTK) pour organiser les objets dans une grille.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, solveurs, collection d’objets de grille
ms.localizationpriority: high
ms.openlocfilehash: 9087800eca3536704ed4ef01a5d8178720b6a875
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590503"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="23832-105">4. Positionnement des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="23832-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="23832-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="23832-106">Overview</span></span>

<span data-ttu-id="23832-107">Dans ce tutoriel, vous allez importer les ressources du tutoriel et positionner les objets fournis dans la scène.</span><span class="sxs-lookup"><span data-stu-id="23832-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="23832-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="23832-108">Objectives</span></span>

* <span data-ttu-id="23832-109">Apprendre à positionner des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="23832-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="23832-110">Apprendre à utiliser la fonctionnalité Grid Object Collection du MRTK</span><span class="sxs-lookup"><span data-stu-id="23832-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="23832-111">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="23832-111">Importing the tutorial assets</span></span>

<span data-ttu-id="23832-112">Téléchargez le package personnalisé Unity suivant :</span><span class="sxs-lookup"><span data-stu-id="23832-112">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="23832-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="23832-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="23832-114">Pour importer un package personnalisé Unity, dans le menu Unity, sélectionnez **Assets** > **Import Package** > **Custom Package...** pour ouvrir la fenêtre Import package :</span><span class="sxs-lookup"><span data-stu-id="23832-114">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](images/mr-learning-base/base-04-section1-step1-1.png)

<span data-ttu-id="23832-116">Dans la fenêtre Import package, sélectionnez le package **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage** que vous avez téléchargé, puis cliquez sur le bouton Open :</span><span class="sxs-lookup"><span data-stu-id="23832-116">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage** you downloaded and click the Open button:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="23832-118">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton Tous pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton Importer pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="23832-118">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](images/mr-learning-base/base-04-section1-step1-3.png)

<span data-ttu-id="23832-120">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="23832-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](images/mr-learning-base/base-04-section1-step1-4.png)

## <a name="creating-the-parent-object"></a><span data-ttu-id="23832-122">Création de l’objet parent</span><span class="sxs-lookup"><span data-stu-id="23832-122">Creating the parent object</span></span>

<span data-ttu-id="23832-123">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur une zone vide et sélectionnez **Create Empty** pour ajouter un objet vide à votre scène :</span><span class="sxs-lookup"><span data-stu-id="23832-123">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menu contextuel Create Empty d’Unity](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="23832-125">Pour afficher côte à côte les fenêtres Scene et Game comme dans l’image ci-dessus, faites glisser la fenêtre Game à droite de la fenêtre Scene.</span><span class="sxs-lookup"><span data-stu-id="23832-125">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="23832-126">Pour en savoir plus, consultez la page consacrée à la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personnalisation de votre espace de travail</a> dans la documentation Unity.</span><span class="sxs-lookup"><span data-stu-id="23832-126">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="23832-127">Cliquez avec le bouton droit sur l’objet que vous venez de créer, sélectionnez **Rename**, puis remplacez le nom par **RoverExplorer** :</span><span class="sxs-lookup"><span data-stu-id="23832-127">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menu contextuel Rename d’Unity](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="23832-129">L’objet RoverExplorer étant toujours sélectionné, dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="23832-129">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="23832-130">**Position** : X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="23832-130">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="23832-131">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23832-131">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="23832-132">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="23832-132">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity avec un objet RoverExplorer sélectionné et positionné](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="23832-134">L’appareil photo, qui représente la tête de l’utilisateur, est positionné à l’origine (X = 0, Y = 0, Z = 0).</span><span class="sxs-lookup"><span data-stu-id="23832-134">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="23832-135">En règle générale, 1 unité dans Unity correspond à peu près à 1 mètre dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="23832-135">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="23832-136">Il y a cependant des exceptions à cela, par exemple quand les objets sont des enfants d’objets mis à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="23832-136">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="23832-137">Dans le scénario ci-dessus, l’objet RoverExplorer est positionné 2 mètres devant la tête de l’utilisateur et 0,6 mètre en dessous.</span><span class="sxs-lookup"><span data-stu-id="23832-137">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="23832-138">Ajout des préfabriqués du tutoriel</span><span class="sxs-lookup"><span data-stu-id="23832-138">Adding the tutorial prefabs</span></span>

<span data-ttu-id="23832-139">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** :</span><span class="sxs-lookup"><span data-stu-id="23832-139">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Fenêtre de projet Unity avec le dossier Prefabs sélectionné](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="23832-141">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">préfabriqué</a> (Prefab) est un GameObject préconfiguré stocké en tant que ressource Unity et qui peut être réutilisé dans tout votre projet.</span><span class="sxs-lookup"><span data-stu-id="23832-141">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="23832-142">Dans la fenêtre Project, cliquez sur le préfabriqué **Table** et faites-le glisser sur l’objet **RoverExplorer** pour en faire un enfant de cet objet, puis dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="23832-142">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="23832-143">**Position** : X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23832-143">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="23832-144">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23832-144">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="23832-145">**Scale** : X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="23832-145">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity avec le préfabriqué nouvellement ajouté Table, sélectionné et positionné](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="23832-147">Pour afficher votre scène comme dans l’image ci-dessus, utilisez le <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">gizmo Scene</a> en haut à droite de la fenêtre Scene pour ajuster l’angle de visualisation sur l’axe Z vers l’avant, double-cliquez sur l’objet MixedRealityPlayspace dans la fenêtre Hierarchy pour avoir le focus sur l’appareil photo, puis faites un zoom avant si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="23832-147">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="23832-148">Dans la fenêtre Project, cliquez sur le préfabriqué **RoverAssembly** et faites-le glisser sur l’objet **RoverExplorer** pour en faire un enfant de cet objet, puis dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="23832-148">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="23832-149">**Position** : X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23832-149">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="23832-150">**Rotation** : X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23832-150">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="23832-151">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="23832-151">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity avec le préfabriqué nouvellement ajouté RoverAssembly, sélectionné et positionné](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="23832-153">Organisation des objets dans une collection</span><span class="sxs-lookup"><span data-stu-id="23832-153">Organizing objects in a collection</span></span>

<span data-ttu-id="23832-154">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **RoverExplorer**, puis sélectionnez **Create Empty** pour ajouter un objet vide en tant qu’enfant de RoverExplorer. Nommez l’objet **RoverParts**, puis configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="23832-154">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="23832-155">**Position** : X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23832-155">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="23832-156">**Rotation** : X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23832-156">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="23832-157">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="23832-157">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity avec l’objet RoverParts nouvellement créé, sélectionné et positionné](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="23832-159">Dans la fenêtre Hierarchy, sélectionnez tous les objets enfants RoverExplorer > RoverAssembly > RoverModel > **Parts**, cliquez dessus avec le bouton droit, puis sélectionnez **Duplicate** pour créer une copie de chaque élément :</span><span class="sxs-lookup"><span data-stu-id="23832-159">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity avec toutes les pièces (Parts) sélectionnées et le menu contextuel Duplicate](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="23832-161">Pour sélectionner plusieurs objets adjacents, maintenez la touche Maj enfoncée tout en utilisant la souris pour sélectionner le premier et le dernier objet.</span><span class="sxs-lookup"><span data-stu-id="23832-161">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="23832-162">Les objets enfants Parts que vous venez de dupliquer étant toujours sélectionnés, cliquez dessus et faites-les glisser sur l’objet **RoverParts** pour en faire des objets enfants de cet objet :</span><span class="sxs-lookup"><span data-stu-id="23832-162">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity avec les pièces (parts) nouvellement dupliquées en tant qu’enfants de l’objet RoverParts](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="23832-164">Pour faciliter l’utilisation de votre scène, dans la fenêtre Hierarchy, cliquez sur l’icône **œil** à gauche de l’objet pour désactiver la **visibilité de la scène** pour l’objet **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="23832-164">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="23832-165">Cette opération masque l’objet dans la fenêtre Scene sans changer sa visibilité dans le jeu :</span><span class="sxs-lookup"><span data-stu-id="23832-165">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity avec la visibilité de la scène RoverAssembly désactivée](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="23832-167">Pour en savoir plus sur les contrôles de visibilité de la scène et sur la façon dont vous pouvez les utiliser pour optimiser l’affichage et le workflow de votre scène, reportez-vous à la documentation <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> d’Unity.</span><span class="sxs-lookup"><span data-stu-id="23832-167">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="23832-168">Dans la fenêtre Hierarchy, nettoyez les noms des objets enfants RoverParts en remplaçant le suffixe **(1)** par **_Part** :</span><span class="sxs-lookup"><span data-stu-id="23832-168">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity avec le nom des pièces (parts) dupliquées effacé](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="23832-170">Dans la fenêtre Hierarchy, sélectionnez l’objet **RoverParts**. Dans la fenêtre Inspector, cliquez sur le bouton **Add Component**, puis recherchez et sélectionnez **GridObjectCollection** pour ajouter le composant GridObjectCollection à l’objet RoverParts :</span><span class="sxs-lookup"><span data-stu-id="23832-170">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objet RoverParts d’Unity avec l’ajout du composant de collection d’objets de grille en cours](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="23832-172">Configurez les valeurs du composant **GridObjectCollection** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="23832-172">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="23832-173">**Sort Type** : Alphabetic</span><span class="sxs-lookup"><span data-stu-id="23832-173">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="23832-174">**Layout** : Horizontale</span><span class="sxs-lookup"><span data-stu-id="23832-174">**Layout**: Horizontal</span></span>
* <span data-ttu-id="23832-175">**Cell Width** : 0.25</span><span class="sxs-lookup"><span data-stu-id="23832-175">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="23832-176">**Distance from parent** : 0.38</span><span class="sxs-lookup"><span data-stu-id="23832-176">**Distance from parent**: 0.38</span></span>

![Unity avec le composant GridObjectCollection configuré](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="23832-178">Cliquez ensuite sur le bouton **Update Collection** pour mettre à jour la position des objets enfants de RoverParts :</span><span class="sxs-lookup"><span data-stu-id="23832-178">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity avec le composant GridObjectCollection appliqué](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="23832-180">Félicitations</span><span class="sxs-lookup"><span data-stu-id="23832-180">Congratulations</span></span>

<span data-ttu-id="23832-181">Dans ce tutoriel, vous avez appris à positionner des objets dans la scène par rapport à l’utilisateur et à utiliser la fonctionnalité Grid Object Collection du MRTK pour organiser les objets dans une collection.</span><span class="sxs-lookup"><span data-stu-id="23832-181">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="23832-182">Tutoriel suivant : 5. Création de contenu dynamique avec des solveurs</span><span class="sxs-lookup"><span data-stu-id="23832-182">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
