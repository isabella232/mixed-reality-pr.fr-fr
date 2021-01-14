---
title: Création d’interfaces utilisateur
description: Ce cours vous montre comment utiliser Mixed Reality Toolkit (MRTK) pour créer des interfaces utilisateur statiques et dynamiques.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, préfabriqués, hologrammes, info-bulles
ms.localizationpriority: high
ms.openlocfilehash: 989de4871332608448619e75ffd760c616332533
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008059"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="ea129-104">6. Création d’interfaces utilisateur</span><span class="sxs-lookup"><span data-stu-id="ea129-104">6. Creating user interfaces</span></span>

<span data-ttu-id="ea129-105">Dans ce tutoriel, vous allez voir comment créer une interface utilisateur simple avec les préfabriqués de boutons et de menus MRTK, ainsi qu’avec le composant TextMeshPro d’Unity.</span><span class="sxs-lookup"><span data-stu-id="ea129-105">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="ea129-106">Vous allez également voir comment configurer les boutons pour déclencher des événements, et comment ajouter des éléments d’interface utilisateur d’info-bulle dynamiques pour fournir des informations supplémentaires à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea129-106">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="ea129-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ea129-107">Objectives</span></span>

* <span data-ttu-id="ea129-108">Apprendre à organiser les boutons dans une collection</span><span class="sxs-lookup"><span data-stu-id="ea129-108">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="ea129-109">Apprendre à utiliser les préfabriqués de menu de MRTK</span><span class="sxs-lookup"><span data-stu-id="ea129-109">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="ea129-110">Apprendre à interagir avec des hologrammes en utilisant des menus et des boutons</span><span class="sxs-lookup"><span data-stu-id="ea129-110">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="ea129-111">Apprendre à ajouter des éléments de texte</span><span class="sxs-lookup"><span data-stu-id="ea129-111">Learn how to add text elements</span></span>
* <span data-ttu-id="ea129-112">Apprendre à générer dynamiquement des info-bulles pour des objets</span><span class="sxs-lookup"><span data-stu-id="ea129-112">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="ea129-113">Création d’un panneau de boutons statique</span><span class="sxs-lookup"><span data-stu-id="ea129-113">Creating a static panel of buttons</span></span>

<span data-ttu-id="ea129-114">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **RoverExplorer**, puis sélectionnez **Create Empty** (Créer un élément vide) pour ajouter un objet vide en tant qu’enfant de RoverExplorer. Ensuite, nommez l’objet **Buttons**, puis configurez le composant **Transform** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-114">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="ea129-115">**Position** : X = -0.6, Y = 0.036, Z = -0.5</span><span class="sxs-lookup"><span data-stu-id="ea129-115">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="ea129-116">**Rotation** : X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="ea129-116">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="ea129-117">**Scale** (Échelle) : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="ea129-117">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity avec l’objet Boutons nouvellement créé, sélectionné et positionné](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="ea129-119">Dans la fenêtre Project, accédez au dossier **Ressources** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, cliquez sur le préfabriqué **PressableRoundButton** puis faites-le glisser vers l’objet **Buttons**. Ensuite, cliquez avec le bouton droit sur PressableRoundButton, puis sélectionnez **Duplicate** pour créer une copie. Répétez l’opération jusqu’à obtenir un total de trois objets PressableRoundButton :</span><span class="sxs-lookup"><span data-stu-id="ea129-119">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![Unity avec le préfabriqué PressableRoundButton nouvellement ajouté](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="ea129-121">Dans la fenêtre Hierarchy, sélectionnez l’objet **Buttons**, puis, dans la fenêtre Inspector (Inspecteur), utilisez le bouton **Add Component** pour ajouter le composant **GridObjectCollection** et le configurer de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-121">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="ea129-122">**Sort Type** (Type de tri) : Child Order (Classement enfant)</span><span class="sxs-lookup"><span data-stu-id="ea129-122">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="ea129-123">**Layout** (Disposition) : Horizontale</span><span class="sxs-lookup"><span data-stu-id="ea129-123">**Layout**: Horizontal</span></span>
* <span data-ttu-id="ea129-124">**Cell Width** (Largeur de cellule) : 0.2</span><span class="sxs-lookup"><span data-stu-id="ea129-124">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="ea129-125">**Anchor** (Ancrage) : Middle Left (Milieu gauche)</span><span class="sxs-lookup"><span data-stu-id="ea129-125">**Anchor**: Middle Left</span></span>

<span data-ttu-id="ea129-126">Cliquez ensuite sur le bouton **Update Collection** (Mettre à jour la collection) pour mettre à jour la position des objets enfants de l’objet Buttons :</span><span class="sxs-lookup"><span data-stu-id="ea129-126">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![Objet Buttons d’Unity avec le composant GridObjectCollection ajouté, configuré et appliqué](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="ea129-128">Dans la fenêtre Hierarchy, nommez les boutons **Hints**, **Explode** et **Reset**.</span><span class="sxs-lookup"><span data-stu-id="ea129-128">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="ea129-129">Pour chaque bouton, sélectionnez l’objet enfant **SeeItSayItLabel** > **TextMeshPro**, puis, dans la fenêtre Inspector, modifiez le texte du composant **TextMeshPro - Text** pour qu’il corresponde aux noms des boutons :</span><span class="sxs-lookup"><span data-stu-id="ea129-129">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![Unity avec des étiquettes de texte de bouton configurées](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="ea129-131">Une fois terminé, réduisez les objets enfants de l’objet Buttons.</span><span class="sxs-lookup"><span data-stu-id="ea129-131">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="ea129-132">Dans la fenêtre Hierarchy, sélectionnez l’objet de bouton **Hints**, puis, dans la fenêtre Inspector, configurez l’événement **Interactable.OnClick ()** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-132">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="ea129-133">Affectez l’objet **RoverAssembly** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="ea129-133">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="ea129-134">Dans la liste déroulante **No Function**, sélectionnez **PlacementHintsController** > **TogglePlacementHints ()** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="ea129-134">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity avec l’événement OnClick de l’objet de bouton Hints configuré](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> <span data-ttu-id="ea129-136">Le composant Interactable est un conteneur tout-en-un qui permet à tout objet de pouvoir facilement interagir et répondre aux entrées.</span><span class="sxs-lookup"><span data-stu-id="ea129-136">The Interactable component is an all-in-one container to make any object easily interactable and responsive to input.</span></span> <span data-ttu-id="ea129-137">Le composant Interactable agit comme un fourre-tout pour tous les types d’entrée, notamment les entrées tactiles, les rayons manuels, la parole, entre autres, et achemine ces interactions dans des événements et des réponses de thème visuel.</span><span class="sxs-lookup"><span data-stu-id="ea129-137">Interactable acts as a catch-all for all types of input including touch, hand rays, speech, etc. and funnels these interactions into events and visual theme responses.</span></span> <span data-ttu-id="ea129-138">Pour savoir comment le configurer pour différents types d’entrée et pour personnaliser son thème visuel, vous pouvez consulter le guide [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) dans le [portail de la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="ea129-138">To learn how to configure it for different input types and customize it's visual theme, you can refer to the [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="ea129-139">Dans la fenêtre Hierarchy, sélectionnez l’objet de bouton **Explode**, puis, dans la fenêtre Inspector, configurez l’événement **Interactable.OnClick ()** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-139">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="ea129-140">Affectez l’objet **RoverAssembly** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="ea129-140">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="ea129-141">Dans la liste déroulante **No Function**, sélectionnez **ExplodedViewController** > **ToggleExplodedView ()** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="ea129-141">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity avec l’événement OnClick de l’objet de bouton Explode configuré](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="ea129-143">Appuyez sur le bouton Play pour passer en mode jeu. Ensuite, maintenez le bouton de la barre d’espace appuyé pour activer la main, et utilisez la souris pour appuyer sur le bouton **Hints** afin d’activer/désactiver la visibilité des objets indicateurs de placement :</span><span class="sxs-lookup"><span data-stu-id="ea129-143">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![Vue partagée du mode Play d’Unity avec le bouton Hints enfoncé](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="ea129-145">et le bouton **Explode** pour activer ou désactiver la vue éclatée :</span><span class="sxs-lookup"><span data-stu-id="ea129-145">and the **Explode** button to toggle the exploded view on and off:</span></span>

![Vue partagée du mode Play d’Unity avec le bouton Explode enfoncé](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="ea129-147">Création d’un menu dynamique qui suit l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="ea129-147">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="ea129-148">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus**. Cliquez sur le préfabriqué **NearMenu4x1** puis faites-le glisser vers la fenêtre Hierarchy. Définissez la **Position** du composant Transform sur X = 0, Y =-0.4, Z = 0, puis configurez-le de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-148">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="ea129-149">Vérifiez que le **Tracked Target Type** du composant **SolverHandler** est défini sur **Head**.</span><span class="sxs-lookup"><span data-stu-id="ea129-149">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="ea129-150">Cochez la case à côté de **RadialView** pour le composant Solver afin de l’activer par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea129-150">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![Unity avec le préfabriqué Menu nouvellement ajouté à proximité sélectionné](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="ea129-152">Dans la fenêtre Hierarchy, attribuez le nom **Menu** à l’objet, puis développez son objet enfant **ButtonCollection** pour afficher les quatre boutons :</span><span class="sxs-lookup"><span data-stu-id="ea129-152">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![Unity avec l’objet Menu sélectionné et l’objet ButtonCollection développé](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="ea129-154">Renommez le premier bouton **Indicator**, puis, dans la fenêtre Inspector, configurez le composant **Button Config Helper (Script)** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-154">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="ea129-155">Modifiez la valeur de **Main Label Text** pour qu’elle corresponde au nom du bouton.</span><span class="sxs-lookup"><span data-stu-id="ea129-155">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="ea129-156">Affectez l’objet **Indicator** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="ea129-156">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="ea129-157">Dans la liste déroulante **No Function**, sélectionnez **GameObject** > **SetActive (bool)** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="ea129-157">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="ea129-158">Vérifiez que la case de l’argument est **cochée**.</span><span class="sxs-lookup"><span data-stu-id="ea129-158">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="ea129-159">Remplacez la valeur **Icon** par l’icône de recherche.</span><span class="sxs-lookup"><span data-stu-id="ea129-159">Change the **Icon** to the 'search' icon</span></span>

![Unity avec l’objet de bouton Indicator et le Button Config Helper configuré](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="ea129-161">Dans la fenêtre Hierarchy, sélectionnez l’objet **Indicator**, puis dans la fenêtre Inspector :</span><span class="sxs-lookup"><span data-stu-id="ea129-161">In the Hierarchy window, select the **Indicator** object, then in the Inspector window:</span></span>

* <span data-ttu-id="ea129-162">Décochez la case à côté de son nom pour le rendre inactif par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea129-162">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="ea129-163">Utilisez le bouton **Add Component** pour ajouter le composant **Directional Indicator Controller (Script)**</span><span class="sxs-lookup"><span data-stu-id="ea129-163">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![Unity avec l’objet Indicator sélectionné et désactivé, et le composant DirectionalIndicatorController ajouté](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="ea129-165">Désormais, lorsque l’application démarre, l’objet Indicator est désactivé par défaut. Vous pouvez l’activer en appuyant sur le bouton Indicator.</span><span class="sxs-lookup"><span data-stu-id="ea129-165">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="ea129-166">Renommez le deuxième bouton **TapToPlace**, puis, dans la fenêtre Inspector, configurez le composant **Button Config Helper (Script)** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-166">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="ea129-167">Modifiez la valeur de **Main Label Text** pour qu’elle corresponde au nom du bouton.</span><span class="sxs-lookup"><span data-stu-id="ea129-167">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="ea129-168">Affectez l’objet RoverExplorer > **RoverAssembly** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="ea129-168">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="ea129-169">Dans la liste déroulante **No Function**, sélectionnez **TapToPlace** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="ea129-169">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="ea129-170">Vérifiez que la case de l’argument est **cochée**.</span><span class="sxs-lookup"><span data-stu-id="ea129-170">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="ea129-171">Remplacez la valeur **Icon** par l’icône représentant un rayon émanant d’une main.</span><span class="sxs-lookup"><span data-stu-id="ea129-171">Change the **Icon** to the 'hand with ray' icon</span></span>

![Unity avec l’objet de bouton TapToPlace et le Button Config Helper configuré](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="ea129-173">Dans la fenêtre Hierarchy, sélectionnez l’objet **RoverAssembly** puis, dans la fenêtre Inspector, configurez le composant **Tap To Place (Script)** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-173">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="ea129-174">Décochez la case à côté de son nom pour le rendre inactif par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea129-174">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="ea129-175">Dans la section d’événement **On Placing Stopped ()** , cliquez sur l’icône **+** pour ajouter un événement :</span><span class="sxs-lookup"><span data-stu-id="ea129-175">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="ea129-176">Affectez l’objet RoverExplorer > **RoverAssembly** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="ea129-176">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="ea129-177">Dans la liste déroulante **No Function**, sélectionnez **TapToPlace** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="ea129-177">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="ea129-178">Vérifiez que la case de l’argument est **décochée**.</span><span class="sxs-lookup"><span data-stu-id="ea129-178">Verify that the argument checkbox is **unchecked**</span></span>

![Unity avec le composant TapToPlace reconfiguré](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="ea129-180">Désormais, lorsque l’application démarre, la fonctionnalité Tap to Place est désactivée par défaut. Vous pouvez l’activer en appuyant sur le bouton Tap to Place.</span><span class="sxs-lookup"><span data-stu-id="ea129-180">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="ea129-181">En outre, une fois que l’opération Tap to Place est terminée, cette fonctionnalité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="ea129-181">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="ea129-182">Ajout de texte à la scène</span><span class="sxs-lookup"><span data-stu-id="ea129-182">Adding text to the scene</span></span>

<span data-ttu-id="ea129-183">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **Table**, puis sélectionnez **3D Object** > **Text - TextMeshPro** pour ajouter un objet texte en tant qu’enfant de l’objet Table. Ensuite, dans la fenêtre Inspector, configurez le composant **Rect Transform** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-183">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="ea129-184">Attribuez la valeur 1 à **Pos Y**.</span><span class="sxs-lookup"><span data-stu-id="ea129-184">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="ea129-185">Attribuez la valeur 1 à **Width**.</span><span class="sxs-lookup"><span data-stu-id="ea129-185">Change **Width** to 1</span></span>
* <span data-ttu-id="ea129-186">Attribuez la valeur 1 à **Height**.</span><span class="sxs-lookup"><span data-stu-id="ea129-186">Change **Height** to 1</span></span>
* <span data-ttu-id="ea129-187">Attribuez la valeur 90 à **Rotation X**.</span><span class="sxs-lookup"><span data-stu-id="ea129-187">Change **Rotation X** to 90</span></span>

![Unity avec l’objet TextMeshPro nouvellement créé sélectionné](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="ea129-189">Configurez ensuite le composant **TextMeshPro - Text** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-189">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="ea129-190">Remplacez la valeur de **Text** par Rover Explorer.</span><span class="sxs-lookup"><span data-stu-id="ea129-190">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="ea129-191">Remplacez la valeur de **Font Style** par Bold.</span><span class="sxs-lookup"><span data-stu-id="ea129-191">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="ea129-192">Attribuez la valeur 1 à **Font Size**.</span><span class="sxs-lookup"><span data-stu-id="ea129-192">Change **Font Size** to 1</span></span>
* <span data-ttu-id="ea129-193">Modifiez la valeur de Extra Settings > **Margins** sur 0.03.</span><span class="sxs-lookup"><span data-stu-id="ea129-193">Change Extra Settings > **Margins** to 0.03</span></span>

![Unity avec le composant TextMeshPro configuré](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="ea129-195">Ajout d’info-bulles</span><span class="sxs-lookup"><span data-stu-id="ea129-195">Adding tooltips</span></span>

<span data-ttu-id="ea129-196">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** pour localiser les préfabriqués d’info-bulle :</span><span class="sxs-lookup"><span data-stu-id="ea129-196">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Fenêtre de projet Unity avec le dossier ToolTips sélectionné](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="ea129-198">Dans la fenêtre Hierarchy, développez l’objet RoverExplorer > **RoverParts**, puis sélectionnez tous les objets enfants RoverParts. Ensuite, dans la fenêtre Inspector, utilisez le bouton **Add Component** (Ajouter un composant) pour ajouter le composant **ToolTipSpawner** et le configurer de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-198">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="ea129-199">Vérifiez que la case **Focus Enabled** (Focus activé) est cochée, afin que l’affichage de l’info-bulle soit déclenché lorsque l’utilisateur regarde le composant.</span><span class="sxs-lookup"><span data-stu-id="ea129-199">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="ea129-200">Affectez le préfabriqué **Simple Line ToolTip** de la fenêtre Project au champ **Tool Tip Prefab**.</span><span class="sxs-lookup"><span data-stu-id="ea129-200">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="ea129-201">Configurez ToolTip Override Settings > **Settings Mode** sur **Override**.</span><span class="sxs-lookup"><span data-stu-id="ea129-201">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="ea129-202">Configurez ToolTip Override Settings > **Manual Pivot Local Position Y** sur **1.5**</span><span class="sxs-lookup"><span data-stu-id="ea129-202">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![Unity avec tous les objets de composant du Rover sélectionnés, et le composant ToolTipSpawner ajouté et configuré](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="ea129-204">Dans la fenêtre Hierarchy, sélectionnez le premier composant Rover, RoverParts > **Camera_Part**, puis configurez le composant **ToolTipSpawner** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-204">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="ea129-205">Remplacez la valeur de **Tool Tip Text** pour qu’elle reflète le nom du composant, en l’occurrence, **Camera**.</span><span class="sxs-lookup"><span data-stu-id="ea129-205">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![Unity avec la caméra ToolTipText configurée](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="ea129-207">**Répétez** cette étape pour chacun des objets du composant Rover afin de configurer le composant **ToolTipSpawner** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ea129-207">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="ea129-208">Pour **Generator_Part**, remplacez la valeur de **Tool Tip Text** par **Generator**.</span><span class="sxs-lookup"><span data-stu-id="ea129-208">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="ea129-209">Pour **Lights_Part**, remplacez la valeur de **Tool Tip Text** par **Lights**.</span><span class="sxs-lookup"><span data-stu-id="ea129-209">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="ea129-210">Pour **UHFAntenna_Part**, remplacez la valeur de **Tool Tip Text** par **UHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="ea129-210">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="ea129-211">Pour **Spectrometer_Part**, remplacez la valeur de **Tool Tip Text** par **Spectrometer**.</span><span class="sxs-lookup"><span data-stu-id="ea129-211">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="ea129-212">Appuyez sur le bouton Play pour passer en mode jeu. Ensuite, maintenez le bouton droit de la souris appuyé tout en déplaçant la souris jusqu’à ce que le regard atteigne l’un des composants et que l’info-bulle de ce composant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="ea129-212">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![Vue partagée du mode Play d’Unity avec une info-bulle déclenchée par le suivi](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="ea129-214">Félicitations</span><span class="sxs-lookup"><span data-stu-id="ea129-214">Congratulations</span></span>

<span data-ttu-id="ea129-215">Dans ce tutoriel, vous avez vu comment créer une interface utilisateur simple avec les préfabriqués de boutons et de menus MRTK, ainsi qu’avec le composant TextMeshPro d’Unity. Vous avez également vu comment configurer les boutons pour déclencher des événements lorsque l’utilisateur appuie dessus.</span><span class="sxs-lookup"><span data-stu-id="ea129-215">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="ea129-216">Enfin, vous avez vu comment ajouter des info-bulles dynamiques pour fournir à l’utilisateur des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ea129-216">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="ea129-217">Tutoriel suivant : 7. Interaction avec les objets 3D</span><span class="sxs-lookup"><span data-stu-id="ea129-217">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)