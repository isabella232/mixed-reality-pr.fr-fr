---
title: UMG et clavier inréel
description: Découvrez comment utiliser des graphiques de mouvement inréalistes pour créer un système d’interface utilisateur en dehors des widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, HoloLens 2, suivi des yeux, entrée de regard, affichage monté en tête, moteur non réel, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, widgets, UI, UMG, graphiques de mouvement inréel, moteur inréel, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355321"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="e4b46-104">UMG et clavier inréel</span><span class="sxs-lookup"><span data-stu-id="e4b46-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="e4b46-105">Les graphiques de mouvement inréel (UMG) sont des systèmes d’interface utilisateur intégrés au moteur, qui permettent de créer des interfaces telles que des menus et des zones de texte.</span><span class="sxs-lookup"><span data-stu-id="e4b46-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="e4b46-106">Les interfaces utilisateur créées avec UMG consistent en des widgets.</span><span class="sxs-lookup"><span data-stu-id="e4b46-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="e4b46-107">Ce guide vous montre comment créer un nouveau widget, l’ajouter à l’espace universel et activer l’interaction avec ce widget en réalité mixte, en utilisant le clavier système comme exemple.</span><span class="sxs-lookup"><span data-stu-id="e4b46-107">This guide will show you how to create a new widget, add it to world space, and enable interaction with that widget in mixed reality, using the system keyboard as an example.</span></span> <span data-ttu-id="e4b46-108">Pour plus d’informations sur UMG, consultez la [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)officielle sur le moteur.</span><span class="sxs-lookup"><span data-stu-id="e4b46-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="e4b46-109">Créer un widget</span><span class="sxs-lookup"><span data-stu-id="e4b46-109">Create a new widget</span></span>

- <span data-ttu-id="e4b46-110">Créez un modèle de widget pour disposer l’interface utilisateur du jeu :</span><span class="sxs-lookup"><span data-stu-id="e4b46-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Capture d’écran de l’ajout d’un modèle de widget à partir du menu non réel](images/unreal-umg-img-01.png)

- <span data-ttu-id="e4b46-112">Ouvrez le nouveau plan et ajoutez des composants de la palette au canevas.</span><span class="sxs-lookup"><span data-stu-id="e4b46-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="e4b46-113">Dans ce cas, nous avons ajouté deux composants de zone de texte à partir de la section « entrée » :</span><span class="sxs-lookup"><span data-stu-id="e4b46-113">In this case we have added two Text Box components from the “Input” section:</span></span>

![Capture d’écran de la fenêtre de hiérarchie avec le composant widget de texte mis en surbrillance et développé](images/unreal-umg-img-02.png)

- <span data-ttu-id="e4b46-115">Sélectionnez un widget dans la fenêtre hiérarchie ou concepteur et modifiez les paramètres dans le panneau détails.</span><span class="sxs-lookup"><span data-stu-id="e4b46-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="e4b46-116">Dans ce cas, nous avons ajouté un « texte d’indication » par défaut et une couleur de teinte lorsque le curseur pointe sur la zone de texte pour fournir des commentaires que le widget est prêt à interagir.</span><span class="sxs-lookup"><span data-stu-id="e4b46-116">In this case, we’ve added some default “Hint Text” and a tint color when the cursor is hovering over the text box to give feedback that the widget is ready to be interacted with.</span></span>  <span data-ttu-id="e4b46-117">Une zone de texte affiche un clavier virtuel sur HoloLens lorsqu’il est interagi avec :</span><span class="sxs-lookup"><span data-stu-id="e4b46-117">A text box will pop up a virtual keyboard on HoloLens when it is interacted with:</span></span>

![Capture d’écran des paramètres modifiés dans la fenêtre hiérarchie](images/unreal-umg-img-03.png)

- <span data-ttu-id="e4b46-119">Les événements peuvent également être abonnés à dans le volet d’informations :</span><span class="sxs-lookup"><span data-stu-id="e4b46-119">Events can also be subscribed to in the details panel:</span></span>

![Capture d’écran des événements dans le volet d’informations](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="e4b46-121">Ajouter un widget à l’espace universel</span><span class="sxs-lookup"><span data-stu-id="e4b46-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="e4b46-122">Créez un acteur, ajoutez un composant widget et ajoutez l’acteur à la scène :</span><span class="sxs-lookup"><span data-stu-id="e4b46-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Capture d’écran d’un acteur avec un widget attaché](images/unreal-umg-img-05.png)

- <span data-ttu-id="e4b46-124">Dans le volet d’informations du widget, définissez la **classe widget** sur le modèle de widget créé précédemment :</span><span class="sxs-lookup"><span data-stu-id="e4b46-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Capture d’écran du panneau Détails du plan avec la classe de widget définie](images/unreal-umg-img-06.png)

- <span data-ttu-id="e4b46-126">Dans le cas d’un widget de texte, assurez-vous que l' **entrée de matériel Receive** est désactivée. nous mettons donc à jour uniquement son texte à partir du clavier virtuel :</span><span class="sxs-lookup"><span data-stu-id="e4b46-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Capture d’écran de la section d’interaction avec l’entrée de matériel Receive désactivée](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="e4b46-128">Interaction du widget</span><span class="sxs-lookup"><span data-stu-id="e4b46-128">Widget Interaction</span></span>

<span data-ttu-id="e4b46-129">Les widgets UMG reçoivent généralement une entrée à partir d’une souris.</span><span class="sxs-lookup"><span data-stu-id="e4b46-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="e4b46-130">Sur HoloLens ou VR, nous devons simuler une souris avec un composant d’interaction de widget pour obtenir les mêmes événements.</span><span class="sxs-lookup"><span data-stu-id="e4b46-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="e4b46-131">Créez un acteur, ajoutez un composant d' **interaction du widget** et ajoutez l’acteur à votre scène :</span><span class="sxs-lookup"><span data-stu-id="e4b46-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Capture d’écran d’un nouvel acteur avec un composant d’interaction de widget mis en surbrillance](images/unreal-umg-img-08.png)

- <span data-ttu-id="e4b46-133">Dans le volet d’informations du composant interaction du widget, définissez la distance d’interaction sur la distance souhaitée, définissez la **source d’interaction** sur **personnalisé**, et pour développement, affectez à **afficher le débogage** la **valeur true**:</span><span class="sxs-lookup"><span data-stu-id="e4b46-133">In the details panel for the Widget Interaction component, set the interaction distance to the desired distance, set the **Interaction Source** to **custom**, and for development, set **Show Debug** to **true**:</span></span>

![Capture d’écran des propriétés du composant d’interaction et de débogage du widget](images/unreal-umg-img-09.png)

<span data-ttu-id="e4b46-135">La valeur par défaut de la source d’interaction est « World », qui doit envoyer des raycasts en fonction de la position universelle du composant d’interaction du widget, mais dans AR et VR, cela ne semble pas être le cas.</span><span class="sxs-lookup"><span data-stu-id="e4b46-135">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component, but in AR and VR this does not appear to be the case.</span></span>  <span data-ttu-id="e4b46-136">L’activation de l’option « Afficher le débogage » et l’ajout d’une teinte de survol aux widgets pendant le développement est importante pour la vérification de la validité. le composant d’interaction des widgets fait ce que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="e4b46-136">Enabling “Show Debug” and adding a hover tint to widgets while developing is important to sanity check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="e4b46-137">La solution consiste à utiliser une source personnalisée et à définir raycast dans le graphique d’événements à partir de la main Ray.</span><span class="sxs-lookup"><span data-stu-id="e4b46-137">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="e4b46-138">Ici, nous appelons ce code à partir de l’événement :</span><span class="sxs-lookup"><span data-stu-id="e4b46-138">Here we are calling this from Event Tick:</span></span>

![Plan du cycle des événements](images/unreal-umg-img-10.png)

<span data-ttu-id="e4b46-140">Ajoutez ensuite des événements de pointeur de souris virtuelle au composant d’interaction du widget en réagissant à l’entrée HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e4b46-140">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="e4b46-141">Dans ce cas, envoyez un événement d’enfoncement de la souris lorsque la main est prélevée et un événement de libération de la souris gauche lorsqu’il n’est pas saisi :</span><span class="sxs-lookup"><span data-stu-id="e4b46-141">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Plan avec ajout d’événements de pointeur de souris virtuelle](images/unreal-umg-img-13.png)

<span data-ttu-id="e4b46-143">Désormais, lorsque vous déployez l’application sur HoloLens 2, vous verrez un rayon de main qui s’étend de votre main droite.</span><span class="sxs-lookup"><span data-stu-id="e4b46-143">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="e4b46-144">Si vous le dirigez vers l’une des zones de texte modifiables et appuyez sur air, le clavier système s’affiche devant vous et vous permet d’entrer du texte.</span><span class="sxs-lookup"><span data-stu-id="e4b46-144">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="e4b46-145">Le clavier du système HoloLens requiert un moteur inréel 4,26 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="e4b46-145">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="e4b46-146">En outre, le clavier n’apparaît pas quand votre application est en train d’être diffusée à partir de l’éditeur non réel sur le casque, uniquement lorsque l’application s’exécute sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="e4b46-146">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4b46-147">Voir aussi :</span><span class="sxs-lookup"><span data-stu-id="e4b46-147">See Also:</span></span>
* [<span data-ttu-id="e4b46-148">Documentation UMG de la non-réalisation</span><span class="sxs-lookup"><span data-stu-id="e4b46-148">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="e4b46-149">Didacticiels UMG inréel</span><span class="sxs-lookup"><span data-stu-id="e4b46-149">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
