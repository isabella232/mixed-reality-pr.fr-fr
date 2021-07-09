---
title: Tutoriels sur MRTK - 4. Positionnement des objets dans la scène
description: Ce cours vous montre comment positionner des objets dans la scène et comment utiliser Mixed Reality Toolkit (MRTK) pour organiser les objets dans une grille.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, solveurs, collection d’objets de grille
ms.localizationpriority: high
ms.openlocfilehash: d5d10893ba8274139c6e09b8cd426d58a0b3a0cb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175470"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="c766c-105">4. Positionnement des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="c766c-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="c766c-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="c766c-106">Overview</span></span>

<span data-ttu-id="c766c-107">Dans ce tutoriel, vous allez positionner les objets fournis comme ressources du tutoriel dans la scène.</span><span class="sxs-lookup"><span data-stu-id="c766c-107">In this tutorial, you will position the provided objects from the tutorial assets in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="c766c-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="c766c-108">Objectives</span></span>

* <span data-ttu-id="c766c-109">Apprendre à positionner des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="c766c-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="c766c-110">Apprendre à utiliser la fonctionnalité Grid Object Collection du MRTK</span><span class="sxs-lookup"><span data-stu-id="c766c-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="c766c-111">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="c766c-111">Importing the TextMeshPro Essential Resources</span></span>
<span data-ttu-id="c766c-112">Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK.</span><span class="sxs-lookup"><span data-stu-id="c766c-112">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="c766c-113">Dans le menu Unity, sélectionnez **Window** > **TextMeshPro** > **Import TMP Essential Resources** pour ouvrir la fenêtre Import Unity Package :</span><span class="sxs-lookup"><span data-stu-id="c766c-113">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="c766c-115">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="c766c-115">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="c766c-117">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="c766c-117">Importing the tutorial assets</span></span>

<span data-ttu-id="c766c-118">Téléchargez le package personnalisé Unity suivant.</span><span class="sxs-lookup"><span data-stu-id="c766c-118">Download the following Unity custom package.</span></span> <span data-ttu-id="c766c-119">Ce package comprend des ressources 3D, telles que Mars Rover, que nous allons utiliser dans ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="c766c-119">This package includes 3D assets such as Mars Rover that we are going to use in this tutorial.</span></span>

* [<span data-ttu-id="c766c-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="c766c-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="c766c-121">Pour importer un package personnalisé Unity, dans le menu Unity, sélectionnez **Assets** > **Import Package** > **Custom Package...** pour ouvrir la fenêtre Import package :</span><span class="sxs-lookup"><span data-stu-id="c766c-121">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Importation d’un package personnalisé](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="c766c-123">Dans la fenêtre Import package, sélectionnez le package **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que vous avez téléchargé, puis cliquez sur le bouton Open :</span><span class="sxs-lookup"><span data-stu-id="c766c-123">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Sélection d’un package de ressources](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="c766c-125">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton Tous pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton Importer pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="c766c-125">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Sélection de toutes les ressources à importer](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="c766c-127">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="c766c-127">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtre de projet Unity après l’importation de ressources](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="creating-the-parent-object"></a><span data-ttu-id="c766c-129">Création de l’objet parent</span><span class="sxs-lookup"><span data-stu-id="c766c-129">Creating the parent object</span></span>

<span data-ttu-id="c766c-130">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur une zone vide et sélectionnez **Create Empty** pour ajouter un objet vide à votre scène :</span><span class="sxs-lookup"><span data-stu-id="c766c-130">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menu contextuel Create Empty d’Unity](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="c766c-132">Pour afficher côte à côte les fenêtres Scene et Game comme dans l’image ci-dessus, faites glisser la fenêtre Game à droite de la fenêtre Scene.</span><span class="sxs-lookup"><span data-stu-id="c766c-132">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="c766c-133">Pour en savoir plus, consultez la page consacrée à la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personnalisation de votre espace de travail</a> dans la documentation Unity.</span><span class="sxs-lookup"><span data-stu-id="c766c-133">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="c766c-134">Cliquez avec le bouton droit sur l’objet que vous venez de créer, sélectionnez **Rename**, puis remplacez le nom par **RoverExplorer** :</span><span class="sxs-lookup"><span data-stu-id="c766c-134">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menu contextuel Rename d’Unity](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="c766c-136">L’objet RoverExplorer étant toujours sélectionné, dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c766c-136">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="c766c-137">**Position** : X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="c766c-137">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="c766c-138">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="c766c-138">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="c766c-139">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="c766c-139">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity avec un objet RoverExplorer sélectionné et positionné](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> <span data-ttu-id="c766c-141">L’appareil photo, qui représente la tête de l’utilisateur, est positionné à l’origine (X = 0, Y = 0, Z = 0).</span><span class="sxs-lookup"><span data-stu-id="c766c-141">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="c766c-142">En règle générale, 1 unité dans Unity correspond à peu près à 1 mètre dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="c766c-142">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="c766c-143">Il y a cependant des exceptions à cela, par exemple quand les objets sont des enfants d’objets mis à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="c766c-143">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="c766c-144">Dans le scénario ci-dessus, l’objet RoverExplorer est positionné 2 mètres devant la tête de l’utilisateur et 0,6 mètre en dessous.</span><span class="sxs-lookup"><span data-stu-id="c766c-144">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="c766c-145">Ajout des préfabriqués du tutoriel</span><span class="sxs-lookup"><span data-stu-id="c766c-145">Adding the tutorial prefabs</span></span>

<span data-ttu-id="c766c-146">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** :</span><span class="sxs-lookup"><span data-stu-id="c766c-146">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Fenêtre de projet Unity avec le dossier Prefabs sélectionné](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="c766c-148">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">préfabriqué</a> (Prefab) est un GameObject préconfiguré stocké en tant que ressource Unity et qui peut être réutilisé dans tout votre projet.</span><span class="sxs-lookup"><span data-stu-id="c766c-148">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="c766c-149">Dans la fenêtre Project, cliquez sur le préfabriqué **Table** et faites-le glisser sur l’objet **RoverExplorer** pour en faire un enfant de cet objet, puis dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c766c-149">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="c766c-150">**Position** : X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="c766c-150">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="c766c-151">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="c766c-151">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="c766c-152">**Scale** : X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="c766c-152">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity avec le préfabriqué nouvellement ajouté Table, sélectionné et positionné](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="c766c-154">Pour afficher votre scène comme dans l’image ci-dessus, utilisez le <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">gizmo Scene</a> en haut à droite de la fenêtre Scene pour ajuster l’angle de visualisation sur l’axe Z vers l’avant, double-cliquez sur l’objet MixedRealityPlayspace dans la fenêtre Hierarchy pour avoir le focus sur l’appareil photo, puis faites un zoom avant si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c766c-154">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="c766c-155">Dans la fenêtre Project, cliquez sur le préfabriqué **RoverAssembly** et faites-le glisser sur l’objet **RoverExplorer** pour en faire un enfant de cet objet, puis dans la fenêtre Inspector, configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c766c-155">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="c766c-156">**Position** : X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="c766c-156">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="c766c-157">**Rotation** : X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="c766c-157">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="c766c-158">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="c766c-158">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity avec le préfabriqué nouvellement ajouté RoverAssembly, sélectionné et positionné](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="c766c-160">Organisation des objets dans une collection</span><span class="sxs-lookup"><span data-stu-id="c766c-160">Organizing objects in a collection</span></span>

<span data-ttu-id="c766c-161">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **RoverExplorer**, puis sélectionnez **Create Empty** pour ajouter un objet vide en tant qu’enfant de RoverExplorer. Nommez l’objet **RoverParts**, puis configurez le composant **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c766c-161">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="c766c-162">**Position** : X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="c766c-162">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="c766c-163">**Rotation** : X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="c766c-163">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="c766c-164">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="c766c-164">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity avec l’objet RoverParts nouvellement créé, sélectionné et positionné](images/mr-learning-base/base-04-section3-step1-1.png)

<span data-ttu-id="c766c-166">Dans la fenêtre Hierarchy, sélectionnez tous les objets enfants RoverExplorer > RoverAssembly > RoverModel > **Parts**, cliquez dessus avec le bouton droit, puis sélectionnez **Duplicate** pour créer une copie de chaque élément :</span><span class="sxs-lookup"><span data-stu-id="c766c-166">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity avec toutes les pièces (Parts) sélectionnées et le menu contextuel Duplicate](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="c766c-168">Pour sélectionner plusieurs objets adjacents, maintenez la touche Maj enfoncée tout en utilisant la souris pour sélectionner le premier et le dernier objet.</span><span class="sxs-lookup"><span data-stu-id="c766c-168">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="c766c-169">Les objets enfants Parts que vous venez de dupliquer étant toujours sélectionnés, cliquez dessus et faites-les glisser sur l’objet **RoverParts** pour en faire des objets enfants de cet objet :</span><span class="sxs-lookup"><span data-stu-id="c766c-169">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity avec les pièces (parts) nouvellement dupliquées en tant qu’enfants de l’objet RoverParts](images/mr-learning-base/base-04-section3-step1-3.png)

<span data-ttu-id="c766c-171">Pour faciliter l’utilisation de votre scène, dans la fenêtre Hierarchy, cliquez sur l’icône **œil** à gauche de l’objet pour désactiver la **visibilité de la scène** pour l’objet **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="c766c-171">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="c766c-172">Cette opération masque l’objet dans la fenêtre Scene sans changer sa visibilité dans le jeu :</span><span class="sxs-lookup"><span data-stu-id="c766c-172">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity avec la visibilité de la scène RoverAssembly désactivée](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> <span data-ttu-id="c766c-174">Pour en savoir plus sur les contrôles de visibilité de la scène et sur la façon dont vous pouvez les utiliser pour optimiser l’affichage et le workflow de votre scène, reportez-vous à la documentation <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> d’Unity.</span><span class="sxs-lookup"><span data-stu-id="c766c-174">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="c766c-175">Dans la fenêtre Hierarchy, nettoyez les noms des objets enfants RoverParts en remplaçant le suffixe **(1)** par **_Part** :</span><span class="sxs-lookup"><span data-stu-id="c766c-175">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity avec le nom des pièces (parts) dupliquées effacé](images/mr-learning-base/base-04-section3-step1-5.png)

<span data-ttu-id="c766c-177">Dans la fenêtre Hierarchy, sélectionnez l’objet **RoverParts**. Dans la fenêtre Inspector, cliquez sur le bouton **Add Component**, puis recherchez et sélectionnez **GridObjectCollection** pour ajouter le composant GridObjectCollection à l’objet RoverParts :</span><span class="sxs-lookup"><span data-stu-id="c766c-177">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objet RoverParts d’Unity avec l’ajout du composant de collection d’objets de grille en cours](images/mr-learning-base/base-04-section3-step1-6.png)

<span data-ttu-id="c766c-179">Configurez les valeurs du composant **GridObjectCollection** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c766c-179">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="c766c-180">**Sort Type** : Alphabetic</span><span class="sxs-lookup"><span data-stu-id="c766c-180">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="c766c-181">**Layout** : Horizontale</span><span class="sxs-lookup"><span data-stu-id="c766c-181">**Layout**: Horizontal</span></span>
* <span data-ttu-id="c766c-182">**Cell Width** : 0.25</span><span class="sxs-lookup"><span data-stu-id="c766c-182">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="c766c-183">**Distance from parent** : 0.38</span><span class="sxs-lookup"><span data-stu-id="c766c-183">**Distance from parent**: 0.38</span></span>

![Unity avec le composant GridObjectCollection configuré](images/mr-learning-base/base-04-section3-step1-7.png)

<span data-ttu-id="c766c-185">Cliquez ensuite sur le bouton **Update Collection** pour mettre à jour la position des objets enfants de RoverParts :</span><span class="sxs-lookup"><span data-stu-id="c766c-185">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity avec le composant GridObjectCollection appliqué](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="c766c-187">Félicitations</span><span class="sxs-lookup"><span data-stu-id="c766c-187">Congratulations</span></span>

<span data-ttu-id="c766c-188">Dans ce tutoriel, vous avez appris à positionner des objets dans la scène par rapport à l’utilisateur et à utiliser la fonctionnalité Grid Object Collection du MRTK pour organiser les objets dans une collection.</span><span class="sxs-lookup"><span data-stu-id="c766c-188">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="c766c-189">Tutoriel suivant : 5. Création de contenu dynamique avec des solveurs</span><span class="sxs-lookup"><span data-stu-id="c766c-189">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
