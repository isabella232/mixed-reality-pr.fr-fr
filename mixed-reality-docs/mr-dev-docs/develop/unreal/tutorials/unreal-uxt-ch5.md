---
title: 5. Ajout d’un bouton et réinitialisation des positions des pièces
description: Cinquième tutoriel d’une série de six visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 08/14/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: f7b57cf8a023874aa14118ff5cd50076bbf344e0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699186"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="c7452-104">5. Ajout d’un bouton et réinitialisation des positions des pièces</span><span class="sxs-lookup"><span data-stu-id="c7452-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="c7452-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="c7452-105">Overview</span></span>

<span data-ttu-id="c7452-106">Dans le tutoriel précédent, vous avez ajouté des acteurs d’interaction manuelle aux composants Pawn et Manipulator de l’échiquier pour les rendre interactifs.</span><span class="sxs-lookup"><span data-stu-id="c7452-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="c7452-107">Dans cette section, vous allez continuer de travailler avec le plug-in Mixed Reality Toolkit UX Tools en développant les fonctionnalités de votre application de jeu d’échecs.</span><span class="sxs-lookup"><span data-stu-id="c7452-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="c7452-108">Vous allez notamment créer une fonction et apprendre à obtenir des références aux acteurs dans un blueprint.</span><span class="sxs-lookup"><span data-stu-id="c7452-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="c7452-109">À la fin de cette section, vous serez prêt à empaqueter et déployer l’application de réalité mixte sur un appareil ou un émulateur.</span><span class="sxs-lookup"><span data-stu-id="c7452-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="c7452-110">Objectifs</span><span class="sxs-lookup"><span data-stu-id="c7452-110">Objectives</span></span>

* <span data-ttu-id="c7452-111">Ajouter un bouton interactif</span><span class="sxs-lookup"><span data-stu-id="c7452-111">Adding an interactive button</span></span>
* <span data-ttu-id="c7452-112">Créer une fonction pour réinitialiser l’emplacement d’une pièce</span><span class="sxs-lookup"><span data-stu-id="c7452-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="c7452-113">Lier le bouton pour déclencher la fonction quand l’utilisateur appuie dessus</span><span class="sxs-lookup"><span data-stu-id="c7452-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="c7452-114">Création d’une fonction de réinitialisation</span><span class="sxs-lookup"><span data-stu-id="c7452-114">Creating a reset function</span></span>
<span data-ttu-id="c7452-115">Votre première tâche consiste à créer un blueprint de fonction qui remet une pièce d’échec à sa position d’origine dans la scène.</span><span class="sxs-lookup"><span data-stu-id="c7452-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="c7452-116">Ouvrez **WhiteKing** , cliquez sur l’icône **+** en regard de la section **Functions** de **My Blueprint** , puis nommez-la **Reset Location** .</span><span class="sxs-lookup"><span data-stu-id="c7452-116">Open **WhiteKing** , click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location** .</span></span> 

2.  <span data-ttu-id="c7452-117">Faites glisser l’exécution de **Drag and release** vers la grille Blueprint pour créer un nœud **SetActorRelativeTransform** .</span><span class="sxs-lookup"><span data-stu-id="c7452-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="c7452-118">Cette fonction définit la transformation (position, rotation et échelle) d’un acteur par rapport à son parent.</span><span class="sxs-lookup"><span data-stu-id="c7452-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="c7452-119">Vous allez utiliser cette fonction pour réinitialiser la position du roi sur l’échiquier, même si celui-ci a été déplacé de sa position d’origine.</span><span class="sxs-lookup"><span data-stu-id="c7452-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="c7452-120">Cliquez avec le bouton droit dans le graphique d’événements, sélectionnez **Make Transform** , puis déplacez-le en définissant le paramètre **Location** comme suit : **X =-26** , **Y = 4** , **Z = 0** .</span><span class="sxs-lookup"><span data-stu-id="c7452-120">Right-click inside the Event Graph, select **Make Transform** , and change its **Location** to **X = -26** , **Y = 4** , **Z = 0** .</span></span>
    * <span data-ttu-id="c7452-121">Connectez sa valeur de retour ( **Return Value** ) au repère **New Relative Transform** dans **SetActorRelativeTransform** .</span><span class="sxs-lookup"><span data-stu-id="c7452-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform** .</span></span> 

![Fonction Reset Location](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="c7452-123">**Compilez** et **enregistrez** le projet avant de revenir à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="c7452-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="c7452-124">Ajouter un bouton</span><span class="sxs-lookup"><span data-stu-id="c7452-124">Adding a button</span></span>
<span data-ttu-id="c7452-125">Maintenant que la fonction est correctement configurée, la tâche suivante consiste à créer un bouton qui la déclenche quand le joueur appuie dessus.</span><span class="sxs-lookup"><span data-stu-id="c7452-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 


1.  <span data-ttu-id="c7452-126">Cliquez sur **Add New > Blueprint Class** , développez la section **All Classes** , puis recherchez **BP_ButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="c7452-126">Click **Add New > Blueprint Class** , expand the **All Classes** section, and search for **BP_ButtonHoloLens2** .</span></span> 
    * <span data-ttu-id="c7452-127">Nommez ce bouton **ResetButton** et double-cliquez pour ouvrir le blueprint.</span><span class="sxs-lookup"><span data-stu-id="c7452-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="c7452-128">**BP_ButtonHoloLens2** est un bouton 3D d’un acteur Blueprint qui est intégré au plug-in UX Tools.</span><span class="sxs-lookup"><span data-stu-id="c7452-128">**BP_ButtonHoloLens2** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span>

![Sous-classe du nouveau Blueprint à partir du bouton de style HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="c7452-130">Vérifiez que **ResetButton(self)** est sélectionné dans le volet **Components** .</span><span class="sxs-lookup"><span data-stu-id="c7452-130">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="c7452-131">Dans le volet **Details** , accédez à la section **Button** .</span><span class="sxs-lookup"><span data-stu-id="c7452-131">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="c7452-132">Remplacez l’élément **Button Label** par défaut par « Reset ».</span><span class="sxs-lookup"><span data-stu-id="c7452-132">Change the default **Button Label** to "Reset".</span></span> <span data-ttu-id="c7452-133">Développez la section **Button Icon Brush** et appuyez sur le bouton **Open Icon Brush Editor** .</span><span class="sxs-lookup"><span data-stu-id="c7452-133">Expand the **Button Icon Brush** section and press the **Open Icon Brush Editor** button.</span></span> 

![Définir l’étiquette et l’icône sur le bouton](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="c7452-135">L’éditeur Icon Brush Editor s’ouvre. Vous pouvez utiliser cet utilitaire fourni par le plug-in UX Tools pour sélectionner une nouvelle icône pour votre bouton.</span><span class="sxs-lookup"><span data-stu-id="c7452-135">This will open up the Icon Brush Editor, which is a utility provided by the UX Tools plugin which you can use to select a new icon for your button.</span></span> 

![Sélectionner une icône pour le bouton](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="c7452-137">Vous pouvez ajuster de nombreux autres paramètres pour configurer votre bouton.</span><span class="sxs-lookup"><span data-stu-id="c7452-137">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="c7452-138">Pour en savoir plus sur le composant UXT Pressable Button, consultez la [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).</span><span class="sxs-lookup"><span data-stu-id="c7452-138">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="c7452-139">Cliquez sur **UxtPressableButton (Inherited)** dans le panneau **Components** et faites défiler le volet **Details** vers le bas jusqu’à la section **Events** .</span><span class="sxs-lookup"><span data-stu-id="c7452-139">Click **UxtPressableButton (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="c7452-140">Cliquez sur le bouton vert **+** à côté de **On Button Pressed** pour ajouter un événement au graphique d’événements, qui est appelé quand le joueur appuie sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="c7452-140">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="c7452-141">À partir de là, vous devez appeler la fonction **Reset Location** de **WhiteKing** , qui a besoin d’une référence à l’acteur **WhiteKing** dans le niveau.</span><span class="sxs-lookup"><span data-stu-id="c7452-141">From here, you’ll want to call **WhiteKing** ’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

4.  <span data-ttu-id="c7452-142">Dans le volet **My Blueprint** , accédez à la section **Variables** , cliquez sur le bouton **+** et nommez la variable **WhiteKing** .</span><span class="sxs-lookup"><span data-stu-id="c7452-142">In the **My Blueprint** panel, navigate to the **Variables** section , click the **+** button and name the variable **WhiteKing** .</span></span> 
    * <span data-ttu-id="c7452-143">Dans le volet **Details** , sélectionnez la liste déroulante à côté de **Variable Type** , recherchez **WhiteKing** , puis sélectionnez **Object Reference** .</span><span class="sxs-lookup"><span data-stu-id="c7452-143">In the **Details** panel, select the dropdown next to **Variable Type** , search for **WhiteKing** , and select the **Object Reference** .</span></span> 
    * <span data-ttu-id="c7452-144">Cochez la case à côté de **Instance Editable** .</span><span class="sxs-lookup"><span data-stu-id="c7452-144">Check the box next to **Instance Editable** .</span></span> <span data-ttu-id="c7452-145">Cela permettra de définir la variable à partir du niveau principal (Main).</span><span class="sxs-lookup"><span data-stu-id="c7452-145">This will allow the variable to be set from the Main Level.</span></span> 

![Créer une variable](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="c7452-147">Faites glisser la variable WhiteKing de **My Blueprint > Variables** vers le graphique d’événements de Reset Button et choisissez **Get WhiteKing** .</span><span class="sxs-lookup"><span data-stu-id="c7452-147">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing** .</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="c7452-148">Déclenchement de la fonction</span><span class="sxs-lookup"><span data-stu-id="c7452-148">Firing the function</span></span>
<span data-ttu-id="c7452-149">Il ne reste plus qu’à déclencher expressément la fonction de réinitialisation dès lors que le joueur appuie sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="c7452-149">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="c7452-150">Faites glisser la broche de sortie WhiteKing et relâchez-la pour placer un nouveau nœud.</span><span class="sxs-lookup"><span data-stu-id="c7452-150">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="c7452-151">Sélectionnez la fonction **Reset Location** .</span><span class="sxs-lookup"><span data-stu-id="c7452-151">Select the **Reset Location** function.</span></span> <span data-ttu-id="c7452-152">Pour finir, faites glisser la broche d’exécution sortante depuis **On Button Pressed** vers la broche d’exécution entrante sur **Reset Location** .</span><span class="sxs-lookup"><span data-stu-id="c7452-152">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location** .</span></span> <span data-ttu-id="c7452-153">**Compilez** et **enregistrez** le Blueprint ResetButton, puis revenez dans la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="c7452-153">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![Appeler la fonction Reset Location à partir de l’événement On Button Pressed](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="c7452-155">Faites glisser **ResetButton** vers la fenêtre Viewport et définissez son emplacement sur **X = 50** , **Y = -25** et **Z = 10** .</span><span class="sxs-lookup"><span data-stu-id="c7452-155">Drag **ResetButton** into the viewport and set its location to **X = 50** , **Y = -25** , and **Z = 10** .</span></span> <span data-ttu-id="c7452-156">Définissez sa rotation comme ceci : **Z = 180** .</span><span class="sxs-lookup"><span data-stu-id="c7452-156">Set its rotation to **Z = 180** .</span></span> <span data-ttu-id="c7452-157">Sous **Default** , attribuez à la variable **WhiteKing** la valeur **WhiteKing** .</span><span class="sxs-lookup"><span data-stu-id="c7452-157">Under **Default** , set the value of the **WhiteKing** variable to **WhiteKing** .</span></span>

![Définir la variable](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="c7452-159">Exécutez l’application, déplacez la pièce d’échec vers son nouvel emplacement, puis appuyez sur le bouton de style HoloLens 2 pour voir la logique de réinitialisation en action.</span><span class="sxs-lookup"><span data-stu-id="c7452-159">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="c7452-160">Votre application de réalité mixte comporte maintenant un échiquier et une pièce avec laquelle vous pouvez interagir, ainsi qu’un bouton entièrement opérationnel qui réinitialise l’emplacement de la pièce.</span><span class="sxs-lookup"><span data-stu-id="c7452-160">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="c7452-161">Vous trouverez l’application à ce stade d’avancement dans son dépôt [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span><span class="sxs-lookup"><span data-stu-id="c7452-161">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="c7452-162">N’hésitez pas à aller au-delà de ce tutoriel et à configurer les autres pièces du jeu d’échecs en faisant en sorte que l’échiquier se réinitialise entièrement quand le joueur appuie sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="c7452-162">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![Scène finale dans la fenêtre Viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="c7452-164">Vous êtes prêt à passer à la dernière section de ce tutoriel, dans laquelle vous allez apprendre à empaqueter et déployer correctement l’application sur un appareil ou un émulateur.</span><span class="sxs-lookup"><span data-stu-id="c7452-164">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7452-165">À ce stade, vous devez mettre à jour votre projet avec les **[paramètres de performances Unreal](../performance-recommendations-for-unreal.md)** recommandés avant de déployer votre application sur un appareil ou un émulateur.</span><span class="sxs-lookup"><span data-stu-id="c7452-165">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="c7452-166">Section suivante : 6. Empaquetage et déploiement sur un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="c7452-166">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
