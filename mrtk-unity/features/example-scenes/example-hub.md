---
title: Exemple de hub
description: Vue d’ensemble des exemples de scènes dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 212fc6e1489a22995241368a9bf4db96d206c44a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144754"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="8ef86-104">Hub d’exemples MRTK</span><span class="sxs-lookup"><span data-stu-id="8ef86-104">MRTK Examples Hub</span></span>

![Hub d’exemples MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="8ef86-106">MRTK exemple Hub est une scène Unity qui facilite l’expérience dans plusieurs scènes.</span><span class="sxs-lookup"><span data-stu-id="8ef86-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="8ef86-107">Elle utilise le système de scène de MRTK pour charger & décharger les scènes.</span><span class="sxs-lookup"><span data-stu-id="8ef86-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="8ef86-108">**MRTKExamplesHub. Unity** est la scène de conteneur qui a des composants partagés, y compris ``MixedRealityToolkit`` et ``MixedRealityPlayspace`` .</span><span class="sxs-lookup"><span data-stu-id="8ef86-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="8ef86-109">La scène **MRTKExamplesHubMainMenu. Unity** contient les boutons de cube.</span><span class="sxs-lookup"><span data-stu-id="8ef86-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="8ef86-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ef86-110">Prerequisite</span></span>

<span data-ttu-id="8ef86-111">MRTK exemple Hub utilise le [service de transition de scène](../extensions/scene-transition-service.md) et les scripts associés.</span><span class="sxs-lookup"><span data-stu-id="8ef86-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="8ef86-112">Si vous utilisez MRTK via des packages Unity, importez **Microsoft. MixedReality. Toolkit. Unity. extensions. x. x. x. pour Unity** , qui fait partie des [packages de version](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="8ef86-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="8ef86-113">Si vous utilisez MRTK via le clone du référentiel, vous devez déjà disposer du dossier **MRTK/extensions** dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="8ef86-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="8ef86-114">MRTKExamplesHub Scene et le système de scène</span><span class="sxs-lookup"><span data-stu-id="8ef86-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="8ef86-115">Ouvrez **MRTKExamplesHub. Unity** qui se trouve à `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` l’emplacement est une scène vide avec MixedRealityToolkit, MixedRealityPlayspace et LoadHubOnStartup.</span><span class="sxs-lookup"><span data-stu-id="8ef86-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="8ef86-116">Cette scène est configurée pour utiliser le système de scène de MRTK.</span><span class="sxs-lookup"><span data-stu-id="8ef86-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="8ef86-117">Cliquez `MixedRealitySceneSystem` sous MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="8ef86-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="8ef86-118">Elle affiche les informations du système de scène dans le panneau de l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="8ef86-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="8ef86-119">En bas de l’inspecteur, il affiche la liste des scènes définies dans le profil de système de scène.</span><span class="sxs-lookup"><span data-stu-id="8ef86-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="8ef86-120">Vous pouvez cliquer sur les noms des scènes pour les charger/décharger.</span><span class="sxs-lookup"><span data-stu-id="8ef86-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="8ef86-121">Exemple de chargement de la scène _MRTKExamplesHub_ en cliquant sur le nom de la scène dans la liste.</span><span class="sxs-lookup"><span data-stu-id="8ef86-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="8ef86-122">Exemple de chargement de la scène _HandInteractionExamples_ .</span><span class="sxs-lookup"><span data-stu-id="8ef86-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="8ef86-123">Exemple de chargement de plusieurs scènes.</span><span class="sxs-lookup"><span data-stu-id="8ef86-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="8ef86-124">Exécution de la scène</span><span class="sxs-lookup"><span data-stu-id="8ef86-124">Running the scene</span></span>

<span data-ttu-id="8ef86-125">La scène fonctionne dans le mode jeu de Unity et sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="8ef86-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="8ef86-126">Exécutez la scène **MRTKExamplesHub** dans l’éditeur Unity et utilisez la simulation d’entrée de MRTK pour interagir avec le contenu de la scène.</span><span class="sxs-lookup"><span data-stu-id="8ef86-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="8ef86-127">Pour générer et déployer, il vous suffit de créer une scène **MRTKExamplesHub** avec d’autres scènes incluses dans la liste du système de scène.</span><span class="sxs-lookup"><span data-stu-id="8ef86-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="8ef86-128">L’inspecteur facilite également l’ajout de scènes aux paramètres de génération.</span><span class="sxs-lookup"><span data-stu-id="8ef86-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="8ef86-129">Dans les paramètres de création, vérifiez que **MRTKExamplesHub** Scene est en haut de la liste à l’index 0.</span><span class="sxs-lookup"><span data-stu-id="8ef86-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="8ef86-130">Comment MRTKExamplesHub charge une scène</span><span class="sxs-lookup"><span data-stu-id="8ef86-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="8ef86-131">Dans la scène **MRTKExamplesHub** , vous pouvez trouver ``ExamplesHubButton`` Prefab.</span><span class="sxs-lookup"><span data-stu-id="8ef86-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="8ef86-132">Il existe un objet **FrontPlate** dans le Prefab qui contient ``Interactable`` .</span><span class="sxs-lookup"><span data-stu-id="8ef86-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="8ef86-133">À l’aide des ``OnClick()`` événements et de l' ``OnTouch()`` événement, il déclenche la fonction **LoadContent ()** du script **LoadContentScene** .</span><span class="sxs-lookup"><span data-stu-id="8ef86-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="8ef86-134">Dans l’inspecteur du script **LoadContentScene** , vous pouvez définir le nom de la scène à charger.</span><span class="sxs-lookup"><span data-stu-id="8ef86-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="8ef86-135">Le script utilise la fonction LoadContent () du système de scène pour charger la scène.</span><span class="sxs-lookup"><span data-stu-id="8ef86-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="8ef86-136">Pour plus d’informations, reportez-vous à la page [système de scène](../scene-system/scene-system-getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="8ef86-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="8ef86-137">Retour à la scène du menu principal</span><span class="sxs-lookup"><span data-stu-id="8ef86-137">Returning to the main menu scene</span></span>

<span data-ttu-id="8ef86-138">Pour revenir à la scène du menu principal (MRTKExamplesHubMainMenu Scene), vous pouvez utiliser la même méthode système de scène `LoadContent()` .</span><span class="sxs-lookup"><span data-stu-id="8ef86-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="8ef86-139">**ToggleFeaturesPanelExamplesHub. Prefab** fournit le bouton « démarrage » qui contient le script **LoadContentScene** .</span><span class="sxs-lookup"><span data-stu-id="8ef86-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="8ef86-140">Utilisez ce Prefab ou un bouton Accueil personnalisé dans chaque scène pour permettre à l’utilisateur de revenir à la scène principale.</span><span class="sxs-lookup"><span data-stu-id="8ef86-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="8ef86-141">Vous pouvez placer **ToggleFeaturesPanelExamplesHub. Prefab** dans la scène **MRTKExamplesHub** pour le rendre toujours visible, car **MRTKExamplesHub** est une scène de conteneur partagée.</span><span class="sxs-lookup"><span data-stu-id="8ef86-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="8ef86-142">Veillez à masquer/désactiver **ToggleFeaturesPanel. Prefab** dans chaque exemple de scène.</span><span class="sxs-lookup"><span data-stu-id="8ef86-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="8ef86-143">Ajout de boutons supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8ef86-143">Adding additional buttons</span></span>

<span data-ttu-id="8ef86-144">Dans l’objet **CubeCollection** , dupliquez (ou ajoutez) _ExampleHubButton_ prefabs, puis cliquez sur **mettre à jour la collection** dans le `GridObjectCollection` .</span><span class="sxs-lookup"><span data-stu-id="8ef86-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="8ef86-145">La disposition du cylindre sera mise à jour en fonction du nouveau nombre total de boutons.</span><span class="sxs-lookup"><span data-stu-id="8ef86-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="8ef86-146">Pour plus d’informations, reportez-vous à la page [collection d’objets](../ux-building-blocks/object-collection.md) .</span><span class="sxs-lookup"><span data-stu-id="8ef86-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="8ef86-147">Après avoir ajouté les boutons, mettez à jour le nom de la scène dans le script **LoadContentScene** (comme expliqué ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="8ef86-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="8ef86-148">Ajoutez des scènes supplémentaires au profil du système de scène.</span><span class="sxs-lookup"><span data-stu-id="8ef86-148">Add additional scenes to the Scene System's profile.</span></span>
