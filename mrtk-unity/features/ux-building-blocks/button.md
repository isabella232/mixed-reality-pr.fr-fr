---
title: Boutons
description: Vue d’ensemble des boutons dans MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, MRTK, boutons
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003106"
---
# <a name="button"></a><span data-ttu-id="1e319-104">Bouton</span><span class="sxs-lookup"><span data-stu-id="1e319-104">Button</span></span>

![Bouton principal](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="1e319-106">Un bouton permet à l’utilisateur de déclencher une action immédiate.</span><span class="sxs-lookup"><span data-stu-id="1e319-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="1e319-107">Il s’agit de l’un des composants les plus fondamentaux de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="1e319-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="1e319-108">MRTK fournit différents types de prefabs de bouton.</span><span class="sxs-lookup"><span data-stu-id="1e319-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="1e319-109">Bouton prefabs dans MRTK</span><span class="sxs-lookup"><span data-stu-id="1e319-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="1e319-110">Exemples du bouton prefabs sous le ``MRTK/SDK/Features/UX/Interactable/Prefabs`` dossier</span><span class="sxs-lookup"><span data-stu-id="1e319-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="1e319-111">Image de l’interface utilisateur Unity/boutons basés sur un graphique</span><span class="sxs-lookup"><span data-stu-id="1e319-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="1e319-112">Boutons basés sur un conflit</span><span class="sxs-lookup"><span data-stu-id="1e319-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="1e319-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="1e319-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="1e319-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="1e319-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="1e319-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="1e319-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="1e319-119">Bouton de style Shell de HoloLens 2 avec une plaque arrière qui prend en charge différents commentaires visuels tels qu’une bordure claire, une lumière de proximité et une plaque avant compressée</span><span class="sxs-lookup"><span data-stu-id="1e319-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-120">Bouton de style Shell de HoloLens 2 sans arrière-plaque</span><span class="sxs-lookup"><span data-stu-id="1e319-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-121">Bouton de style Shell de HoloLens 2 avec forme circulaire</span><span class="sxs-lookup"><span data-stu-id="1e319-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="1e319-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="1e319-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="1e319-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="1e319-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="1e319-125">Bouton de style Shell de la largeur de l’interface HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="1e319-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-126">Barre de boutons HoloLens 2 horizontale avec arrière partagé</span><span class="sxs-lookup"><span data-stu-id="1e319-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-127">Barre de boutons HoloLens 2 verticale avec arrière partagé</span><span class="sxs-lookup"><span data-stu-id="1e319-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="1e319-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="1e319-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="1e319-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="1e319-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="1e319-131">Case à cocher de type Shell de HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="1e319-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-132">Commutateur de style Shell de HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="1e319-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-133">32x32mm radio de style Shell de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1e319-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="1e319-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="1e319-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="1e319-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="1e319-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="1e319-137">Case à cocher de type Shell de HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="1e319-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-138">Commutateur de style Shell de HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="1e319-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-139">32x96mm radio de style Shell de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1e319-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="1e319-140">![Radial ](../images/button/MRTK_Button_Radial.png)  radial</span><span class="sxs-lookup"><span data-stu-id="1e319-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-141">![Case à cocher](../images/button/MRTK_Button_Checkbox.png) **Case à cocher**</span><span class="sxs-lookup"><span data-stu-id="1e319-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="1e319-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="1e319-143">Bouton radial</span><span class="sxs-lookup"><span data-stu-id="1e319-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-144">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="1e319-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-145">Commutateur bascule</span><span class="sxs-lookup"><span data-stu-id="1e319-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="1e319-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="1e319-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="1e319-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-148">![](../images/button/MRTK_Button_Base.png)  Bouton de base du bouton</span><span class="sxs-lookup"><span data-stu-id="1e319-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="1e319-149">Bouton de style d’interpréteur de commandes HoloLens 1re génération</span><span class="sxs-lookup"><span data-stu-id="1e319-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-150">Bouton de commande de la forme ronde</span><span class="sxs-lookup"><span data-stu-id="1e319-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="1e319-151">Bouton de base</span><span class="sxs-lookup"><span data-stu-id="1e319-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="1e319-152">Le `Button` (ressources/MRTK/SDK/features/UX/interactive/Prefabs/Button. Prefab) est basé sur le [](interactable.md) concept interactif pour fournir des contrôles d’interface utilisateur faciles pour les boutons ou d’autres types de surfaces interactives.</span><span class="sxs-lookup"><span data-stu-id="1e319-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="1e319-153">Le bouton de ligne de base prend en charge toutes les méthodes d’entrée disponibles, y compris l’entrée articulée pour les interactions proches et le point d’appui sur l’air pour les interactions lointaines.</span><span class="sxs-lookup"><span data-stu-id="1e319-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="1e319-154">Vous pouvez également utiliser la commande vocale pour déclencher le bouton.</span><span class="sxs-lookup"><span data-stu-id="1e319-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="1e319-155">`PressableButtonHoloLens2` (Ressources/MRTK/Kit de développement logiciel/fonctionnalités/UX/accessible en interaction/Prefabs/PressableButtonHoloLens2. Prefab) est un bouton de style d’interpréteur de commandes HoloLens 2 qui prend en charge le déplacement précis du bouton pour l’entrée de suivi direct.</span><span class="sxs-lookup"><span data-stu-id="1e319-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="1e319-156">Il combine un `Interactable` script avec un `PressableButton` script.</span><span class="sxs-lookup"><span data-stu-id="1e319-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="1e319-157">Pour HoloLens 2, il est recommandé d’utiliser des boutons avec une plaque arrière opaque.</span><span class="sxs-lookup"><span data-stu-id="1e319-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="1e319-158">Les boutons transparents ne sont pas recommandés en raison de ces problèmes d’utilisation et de stabilité :</span><span class="sxs-lookup"><span data-stu-id="1e319-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="1e319-159">L’icône et le texte sont difficiles à lire avec l’environnement physique</span><span class="sxs-lookup"><span data-stu-id="1e319-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="1e319-160">Il est difficile de comprendre quand les déclencheurs d’événements</span><span class="sxs-lookup"><span data-stu-id="1e319-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="1e319-161">Les hologrammes affichés via un plan transparent peuvent être instables avec la stabilisation LSR profondeur de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1e319-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Bouton plaqué](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="1e319-163">Comment utiliser les boutons avec pression</span><span class="sxs-lookup"><span data-stu-id="1e319-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="1e319-164">Boutons basés sur l’interface utilisateur Unity</span><span class="sxs-lookup"><span data-stu-id="1e319-164">Unity UI based buttons</span></span>

<span data-ttu-id="1e319-165">Créez un canevas dans votre scène (GameObject-> UI-> canevas).</span><span class="sxs-lookup"><span data-stu-id="1e319-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="1e319-166">Dans le panneau de l’inspecteur de votre canevas :</span><span class="sxs-lookup"><span data-stu-id="1e319-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="1e319-167">Cliquez sur « convertir en canevas MRTK »</span><span class="sxs-lookup"><span data-stu-id="1e319-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="1e319-168">Cliquez sur « Ajouter NearInteractionTouchableUnityUI ».</span><span class="sxs-lookup"><span data-stu-id="1e319-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="1e319-169">Définissez les échelles X, Y et Z du composant de transformation Rect sur 0,001</span><span class="sxs-lookup"><span data-stu-id="1e319-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="1e319-170">Ensuite, faites glisser `PressableButtonUnityUI` (ressources/MRTK/Kit de développement logiciel/fonctionnalités/UX/interactive/Prefabs/PressableButtonUnityUI. Prefab), `PressableButtonUnityUICircular` (ressources/MRTK/Kit de développement logiciel (SDK)/fonctionnalités/UX/exploitable/Prefabs/PressableButtonUnityUICircular. Prefab), ou `PressableButtonHoloLens2UnityUI` (ressources/MRTK/Kit de développement logiciel/SDK/featurables/Prefabs/PressableButtonHoloLens2UnityUI. Prefab) sur le canevas</span><span class="sxs-lookup"><span data-stu-id="1e319-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="1e319-171">Boutons basés sur un conflit</span><span class="sxs-lookup"><span data-stu-id="1e319-171">Collider based buttons</span></span>

<span data-ttu-id="1e319-172">Il vous suffit `PressableButtonHoloLens2` de faire un glisser (ressources/MRTK/SDK/features/UX/interactive/Prefabs/PressableButtonHoloLens2. Prefab) ou `PressableButtonHoloLens2Unplated` (ressources/MRTK/SDK/features/UX/interactive/Prefabs/PressableButtonHoloLens2Unplated. Prefab) dans la scène.</span><span class="sxs-lookup"><span data-stu-id="1e319-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="1e319-173">Ces prefabs de bouton sont déjà configurés pour obtenir des commentaires visuels audio pour les différents types d’entrées, y compris l’entrée articulée et le point de regard.</span><span class="sxs-lookup"><span data-stu-id="1e319-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="1e319-174">Les événements exposés dans le Prefab lui-même, ainsi que [le composant pouvant](interactable.md) être utilisé, peuvent être utilisés pour déclencher des actions supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1e319-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="1e319-175">Les boutons d’appui de la [scène HandInteractionExample](../example-scenes/hand-interaction-examples.md) utilisent l’événement *OnClick* de l’interagissant pour déclencher une modification de la couleur d’un cube.</span><span class="sxs-lookup"><span data-stu-id="1e319-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="1e319-176">Cet événement est déclenché pour différents types de méthodes d’entrée, telles que le point de suspension, l’air-TAP, le rayon de la main, ainsi que l’appui sur le bouton physique via le script du bouton d’appui.</span><span class="sxs-lookup"><span data-stu-id="1e319-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="1e319-177">Vous pouvez configurer le moment où le bouton enfoncé déclenche l’événement *OnClick* via le `PhysicalPressEventRouter` sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="1e319-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="1e319-178">Par exemple, vous pouvez définir *OnClick* pour qu’il se déclenche quand le bouton est activé pour la première fois, par opposition à l’enfoncement et à la libération, en définissant l’option interactiver sur *événement* sur *clic* .</span><span class="sxs-lookup"><span data-stu-id="1e319-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="1e319-179">Pour tirer parti des informations d’état d’entrée articulées spécifiques, vous pouvez utiliser les boutons accessibles par événements- *Touch Begin*, *Touch end*, *bouton enfoncé*, *bouton relâché*.</span><span class="sxs-lookup"><span data-stu-id="1e319-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="1e319-180">Toutefois, ces événements ne sont pas déclenchés en réponse à des entrées d’entrée aérienne, de rayon de main ou d’oeil.</span><span class="sxs-lookup"><span data-stu-id="1e319-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="1e319-181">**Pour prendre en charge à la fois les interactions proches et Far, il est recommandé d’utiliser l’événement *OnClick* d’Interactive.**</span><span class="sxs-lookup"><span data-stu-id="1e319-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="1e319-182">États d’interaction</span><span class="sxs-lookup"><span data-stu-id="1e319-182">Interaction states</span></span>

<span data-ttu-id="1e319-183">Dans l’état inactif, la plaque avant du bouton n’est pas visible.</span><span class="sxs-lookup"><span data-stu-id="1e319-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="1e319-184">Comme une approche par doigt ou un curseur de l’entrée de regard cible la surface, la bordure lumineuse de la plaque avant devient visible.</span><span class="sxs-lookup"><span data-stu-id="1e319-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="1e319-185">La surface de la plaque avant présente une surbrillance supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="1e319-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="1e319-186">Quand vous appuyez sur un doigt, la plaque avant se déplace à la main.</span><span class="sxs-lookup"><span data-stu-id="1e319-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="1e319-187">Lorsque le doigt touche la surface de la plaque avant, il affiche un effet d’impulsion subtil pour fournir un retour visuel du point tactile.</span><span class="sxs-lookup"><span data-stu-id="1e319-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="1e319-188">Dans le bouton de style Shell HoloLens 2, il existe de nombreux signaux visuels et intuitivité pour augmenter la confiance de l’utilisateur sur l’interaction.</span><span class="sxs-lookup"><span data-stu-id="1e319-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Lumière de proximité](../images/button/ux_button_affordance_proximitylight.jpg) | ![Sélection du focus](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compression du boîtier](../images/button/ux_button_affordance_compression.jpg) | ![Impulsion sur le déclencheur](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="1e319-193">Lumière de proximité</span><span class="sxs-lookup"><span data-stu-id="1e319-193">Proximity light</span></span> | <span data-ttu-id="1e319-194">Sélection du focus</span><span class="sxs-lookup"><span data-stu-id="1e319-194">Focus highlight</span></span> | <span data-ttu-id="1e319-195">Compression du boîtier</span><span class="sxs-lookup"><span data-stu-id="1e319-195">Compressing cage</span></span> | <span data-ttu-id="1e319-196">Impulsion sur le déclencheur</span><span class="sxs-lookup"><span data-stu-id="1e319-196">Pulse on trigger</span></span> |

<span data-ttu-id="1e319-197">L’effet d’impulsion subtil est déclenché par le bouton enfoncé, qui recherche des *ProximityLight* qui vivent sur le pointeur actuellement en interaction.</span><span class="sxs-lookup"><span data-stu-id="1e319-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="1e319-198">Si des lumières de proximité sont détectées, la `ProximityLight.Pulse` méthode est appelée, ce qui anime automatiquement les paramètres du nuanceur pour afficher une impulsion.</span><span class="sxs-lookup"><span data-stu-id="1e319-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="1e319-199">Propriétés de l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="1e319-199">Inspector properties</span></span>

![Structure de bouton](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="1e319-201"> 
 Collision `Box Collide\r` de Box pour la plaque avant du bouton.</span><span class="sxs-lookup"><span data-stu-id="1e319-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="1e319-202">**Bouton enfoncé** Logique pour le mouvement du bouton avec l’interaction avec la main.</span><span class="sxs-lookup"><span data-stu-id="1e319-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="1e319-203">**Routeur d’événements de presse physique** Ce script envoie des événements à partir d’une interaction d’appui à la main pour [interagir](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="1e319-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="1e319-204">**En interaction** 
 L' [interaction gère divers](interactable.md) types d’États et d’événements d’interaction.</span><span class="sxs-lookup"><span data-stu-id="1e319-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="1e319-205">Les entrées du point de contrôle de l’entrée et du mouvement du regard HoloLens, ainsi que l’entrée du contrôleur de mouvement du casque immersif sont directement gérées par ce script.</span><span class="sxs-lookup"><span data-stu-id="1e319-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="1e319-206">**Source audio** Source audio Unity pour les séquences de commentaires audio.</span><span class="sxs-lookup"><span data-stu-id="1e319-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="1e319-207">*NearInteractionTouchable. cs* requis pour transformer tout objet touchable en entrée articulée.</span><span class="sxs-lookup"><span data-stu-id="1e319-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="1e319-208">Disposition Prefab</span><span class="sxs-lookup"><span data-stu-id="1e319-208">Prefab layout</span></span>

<span data-ttu-id="1e319-209">L’objet *ButtonContent* contient une plaque avant, une étiquette de texte et une icône.</span><span class="sxs-lookup"><span data-stu-id="1e319-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="1e319-210">Le *FrontPlate* répond à la proximité de l’index à l’aide du nuanceur de *Button_Box* .</span><span class="sxs-lookup"><span data-stu-id="1e319-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="1e319-211">Il affiche les bordures lumineuses, la lumière de proximité et un effet d’impulsion sur Touch.</span><span class="sxs-lookup"><span data-stu-id="1e319-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="1e319-212">L’étiquette de texte est créée avec TextMesh Pro.</span><span class="sxs-lookup"><span data-stu-id="1e319-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="1e319-213">La visibilité de *SeeItSayItLabel* est contrôlée par le thème de l' [interaction](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="1e319-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Disposition du bouton](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="1e319-215">Comment modifier l’icône et le texte</span><span class="sxs-lookup"><span data-stu-id="1e319-215">How to change the icon and text</span></span>

<span data-ttu-id="1e319-216">Les boutons MRTK utilisent un `ButtonConfigHelper` composant pour vous aider à modifier l’icône, le texte et l’étiquette du bouton.</span><span class="sxs-lookup"><span data-stu-id="1e319-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="1e319-217">(Notez que certains champs peuvent être absents si les éléments ne sont pas présents sur le bouton sélectionné.)</span><span class="sxs-lookup"><span data-stu-id="1e319-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Helper de configuration de bouton](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="1e319-219">Création et modification de jeux d’icônes</span><span class="sxs-lookup"><span data-stu-id="1e319-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="1e319-220">Un **jeu d’icônes** est un ensemble partagé de ressources d’icône utilisées par le `ButtonConfigHelper` composant.</span><span class="sxs-lookup"><span data-stu-id="1e319-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="1e319-221">Trois *styles* d’icône sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1e319-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="1e319-222">Les icônes **Quad** sont rendues sur un quadruple à l’aide d’un `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="1e319-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="1e319-223">Il s’agit du style d’icône par défaut.</span><span class="sxs-lookup"><span data-stu-id="1e319-223">This is the default icon style.</span></span>
* <span data-ttu-id="1e319-224">Les icônes de **Sprite** sont rendues à l’aide d’un `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="1e319-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="1e319-225">Cela est utile si vous préférez importer vos icônes sous la forme d’une feuille de Sprite, ou si vous souhaitez que vos ressources d’icône soient partagées avec des composants de l’interface utilisateur Unity.</span><span class="sxs-lookup"><span data-stu-id="1e319-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="1e319-226">Pour utiliser ce style, vous devez installer le package de l’éditeur Sprite **(Windows-> Package Manager-> 2D sprite)**</span><span class="sxs-lookup"><span data-stu-id="1e319-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="1e319-227">Les icônes **char** sont rendues à l’aide d’un `TextMeshPro` composant.</span><span class="sxs-lookup"><span data-stu-id="1e319-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="1e319-228">Cela est utile si vous préférez utiliser une police d’icône.</span><span class="sxs-lookup"><span data-stu-id="1e319-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="1e319-229">Pour utiliser la police de l’icône HoloLens, vous devez créer une `TextMeshPro` ressource de police.</span><span class="sxs-lookup"><span data-stu-id="1e319-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="1e319-230">Pour modifier le style utilisé par votre bouton, développez la liste déroulante *icônes* dans le ButtonConfigHelper et sélectionnez un style dans la liste déroulante *style d’icône* .</span><span class="sxs-lookup"><span data-stu-id="1e319-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="1e319-231">Vous pouvez créer un jeu d’icônes de bouton à l’aide du menu Asset : **créer > ensemble d’icônes de réalité mixte > jeu d’icônes.**</span><span class="sxs-lookup"><span data-stu-id="1e319-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="1e319-232">Pour ajouter des icônes Quad et Sprite, il suffit de les faire glisser dans leurs tableaux respectifs.</span><span class="sxs-lookup"><span data-stu-id="1e319-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="1e319-233">Pour ajouter des icônes de type char, vous devez d’abord créer et assigner une ressource de police.</span><span class="sxs-lookup"><span data-stu-id="1e319-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="1e319-234">Dans MRTK 2,4 et au-delà, nous vous recommandons de déplacer les textures d’icône personnalisées vers un IconSet.</span><span class="sxs-lookup"><span data-stu-id="1e319-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="1e319-235">Pour mettre à niveau les ressources sur tous les boutons d’un projet au nouveau format recommandé, utilisez ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="1e319-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="1e319-236">(Kit d’outils de réalité mixte-utilitaires de >-fenêtre de migration de >-> sélection du gestionnaire de migration-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="1e319-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="1e319-237">Importation du package Microsoft. MixedRealityToolkit. Unity. Tools requis pour mettre à niveau les boutons.</span><span class="sxs-lookup"><span data-stu-id="1e319-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Boîte de dialogue mettre à niveau la fenêtre](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="1e319-239">Si aucune icône n’est trouvée dans le jeu d’icônes par défaut lors de la migration, un jeu d’icônes personnalisé est créé dans MixedRealityToolkit. generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="1e319-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="1e319-240">Une boîte de dialogue indiquera que cette opération a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="1e319-240">A dialog will indicate that this has taken place.</span></span>

![Notification d’icône personnalisée](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="1e319-242">Création d’une ressource de police d’icône HoloLens</span><span class="sxs-lookup"><span data-stu-id="1e319-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="1e319-243">Tout d’abord, importez la police d’icône dans Unity.</span><span class="sxs-lookup"><span data-stu-id="1e319-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="1e319-244">Sur les ordinateurs Windows, vous pouvez trouver la police HoloLens par défaut dans *Windows/Fonts/holomdl2. ttf.*</span><span class="sxs-lookup"><span data-stu-id="1e319-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="1e319-245">Copiez et collez ce fichier dans votre dossier de ressources.</span><span class="sxs-lookup"><span data-stu-id="1e319-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="1e319-246">Ensuite, ouvrez le créateur de la ressource de police TextMeshPro à l’aide de **windows > TextMeshPro > police Creator.**</span><span class="sxs-lookup"><span data-stu-id="1e319-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="1e319-247">Voici les paramètres recommandés pour la génération d’un Atlas de polices HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1e319-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="1e319-248">Pour inclure toutes les icônes, collez la plage Unicode suivante dans le champ *séquence de caractères* :</span><span class="sxs-lookup"><span data-stu-id="1e319-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Création de bouton 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="1e319-250">Une fois la ressource de police générée, enregistrez-la dans votre projet et affectez-la au champ police de l' *icône de caractère* de votre jeu d’icônes.</span><span class="sxs-lookup"><span data-stu-id="1e319-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="1e319-251">La liste déroulante *icônes disponibles* est maintenant remplie.</span><span class="sxs-lookup"><span data-stu-id="1e319-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="1e319-252">Pour qu’une icône soit disponible en vue d’une utilisation par un bouton, cliquez dessus.</span><span class="sxs-lookup"><span data-stu-id="1e319-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="1e319-253">Il sera ajouté à la liste déroulante des *icônes sélectionnées* et s’affichera dans le, `ButtonConfigHelper.` vous pouvez éventuellement lui attribuer une étiquette.</span><span class="sxs-lookup"><span data-stu-id="1e319-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="1e319-254">Cela permet de définir l’icône au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1e319-254">This enables setting the icon at runtime.</span></span>

![Création de bouton 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Création de bouton 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="1e319-257">Pour utiliser le jeu d’icônes, sélectionnez un bouton, développez la liste déroulante des icônes dans le `ButtonConfigHelper` et affectez-le au champ *jeu d’icônes* .</span><span class="sxs-lookup"><span data-stu-id="1e319-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Icône de bouton définie](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="1e319-259">Comment modifier la taille d’un bouton</span><span class="sxs-lookup"><span data-stu-id="1e319-259">How to change the size of a button</span></span>

<span data-ttu-id="1e319-260">La taille du bouton de style Shell de HoloLens 2 est 32x32mm.</span><span class="sxs-lookup"><span data-stu-id="1e319-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="1e319-261">Pour personnaliser la dimension, modifiez la taille de ces objets dans le bouton Prefab :</span><span class="sxs-lookup"><span data-stu-id="1e319-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="1e319-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="1e319-262">**FrontPlate**</span></span>
2. <span data-ttu-id="1e319-263">**Quadruple** sous la plaque arrière</span><span class="sxs-lookup"><span data-stu-id="1e319-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="1e319-264">**Collision de Box** à la racine</span><span class="sxs-lookup"><span data-stu-id="1e319-264">**Box Collider** on the root</span></span>

<span data-ttu-id="1e319-265">Ensuite, cliquez sur le bouton **corriger les limites** dans le script NearInteractionTouchable qui se trouve à la racine du bouton.</span><span class="sxs-lookup"><span data-stu-id="1e319-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="1e319-266">Mettre à jour la taille de la personnalisation de la ![ taille du bouton FrontPlate 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="1e319-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="1e319-267">Mettre à jour la taille de la personnalisation de la ![ taille du bouton quadruple 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="1e319-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="1e319-268">Mettre à jour la taille du bouton de conflit de cases ![ personnalisation 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="1e319-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="1e319-269">Cliquez sur la personnalisation de la taille du bouton « fixer les limites » ![ 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="1e319-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="1e319-270">Commande vocale ('See-It, disons-it')</span><span class="sxs-lookup"><span data-stu-id="1e319-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="1e319-271">**Gestionnaire d’entrée vocale** Le script d' [interaction](interactable.md) dans le bouton enfoncé implémente déjà `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="1e319-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="1e319-272">Un mot clé de commande vocale peut être défini ici.</span><span class="sxs-lookup"><span data-stu-id="1e319-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="1e319-273">**Profil d’entrée vocal** En outre, vous devez inscrire le mot clé de commande vocale dans le *profil des commandes vocales* globales.</span><span class="sxs-lookup"><span data-stu-id="1e319-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="1e319-274">**Voir-IT, étiquette** Le bouton Prefab a un espace réservé TextMesh Pro sous l’objet *SeeItSayItLabel* .</span><span class="sxs-lookup"><span data-stu-id="1e319-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="1e319-275">Vous pouvez utiliser cette étiquette pour communiquer le mot clé de commande vocale du bouton à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1e319-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="1e319-276">Comment créer un bouton à partir de zéro</span><span class="sxs-lookup"><span data-stu-id="1e319-276">How to make a button from scratch</span></span>

<span data-ttu-id="1e319-277">Vous trouverez les exemples de ces boutons dans la scène **PressableButtonExample** .</span><span class="sxs-lookup"><span data-stu-id="1e319-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="1e319-278">1. création d’un bouton enfoncé avec un cube (proche de l’interaction uniquement)</span><span class="sxs-lookup"><span data-stu-id="1e319-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="1e319-279">Créer un cube Unity (GameObject > 3D Object > cube)</span><span class="sxs-lookup"><span data-stu-id="1e319-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="1e319-280">Ajouter un `PressableButton.cs` script</span><span class="sxs-lookup"><span data-stu-id="1e319-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="1e319-281">Ajouter un `NearInteractionTouchable.cs` script</span><span class="sxs-lookup"><span data-stu-id="1e319-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="1e319-282">Dans le `PressableButton` panneau de l’inspecteur de, assignez l’objet de cube aux éléments **visuels du bouton mobile**.</span><span class="sxs-lookup"><span data-stu-id="1e319-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="1e319-283">Lorsque vous sélectionnez le cube, vous verrez plusieurs couches de couleur sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="1e319-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="1e319-284">Cela visualise les valeurs de distance sous les **paramètres de presse**.</span><span class="sxs-lookup"><span data-stu-id="1e319-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="1e319-285">À l’aide des descripteurs, vous pouvez configurer à quel moment démarrer la pression (déplacer l’objet) et le déclenchement de l’événement.</span><span class="sxs-lookup"><span data-stu-id="1e319-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="1e319-286">Lorsque vous appuyez sur le bouton, il déplace et génère les événements appropriés exposés dans le `PressableButton.cs` script, tels que TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().</span><span class="sxs-lookup"><span data-stu-id="1e319-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="1e319-287">Dépannage</span><span class="sxs-lookup"><span data-stu-id="1e319-287">Troubleshooting</span></span>

<span data-ttu-id="1e319-288">Si votre bouton exécute une double pression, assurez-vous que la propriété **appliquer le push frontal** est active et que le plan de la **distance de départ** est placé devant le plan **touchable near interaction** .</span><span class="sxs-lookup"><span data-stu-id="1e319-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="1e319-289">Le plan **touchable near interaction** est indiqué par le plan bleu placé devant l’origine de la flèche blanche dans le GIF ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1e319-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Composant de script de bouton enfoncé avec la propriété appliquer un push frontal mis en surbrillance](../images/button/MRTK_Button_Enforce_Push.png)

![Exemple animé de déplacement de la distance de transmission de type push devant le plan touchable near interaction](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="1e319-292">2. Ajout d’un retour visuel au bouton cube de base</span><span class="sxs-lookup"><span data-stu-id="1e319-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="1e319-293">Le nuanceur standard MRTK fournit diverses fonctionnalités qui facilitent l’ajout de commentaires visuels.</span><span class="sxs-lookup"><span data-stu-id="1e319-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="1e319-294">Créez un matériau et sélectionnez le nuanceur `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="1e319-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="1e319-295">Ou vous pouvez utiliser ou dupliquer l’un des matériaux existants sous `/SDK/StandardAssets/Materials/` qui utilise le nuanceur standard MRTK.</span><span class="sxs-lookup"><span data-stu-id="1e319-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="1e319-296">Activez la case à cocher `Hover Light` et `Proximity Light` sous **options Fluent**.</span><span class="sxs-lookup"><span data-stu-id="1e319-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="1e319-297">Cela permet d’obtenir des commentaires visuels pour les interactions près de la main (lumière de proximité) et du pointeur Far (point d’éclairage).</span><span class="sxs-lookup"><span data-stu-id="1e319-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="1e319-298">3. Ajout de commentaires audio au bouton cube de base</span><span class="sxs-lookup"><span data-stu-id="1e319-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="1e319-299">Étant donné que le `PressableButton.cs` script expose des événements tels que TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), nous pouvons facilement assigner des commentaires audio.</span><span class="sxs-lookup"><span data-stu-id="1e319-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="1e319-300">Ajoutez simplement Unity `Audio Source` à l’objet cube, puis affectez des clips audio en sélectionnant audiosource. PlayOneShot ().</span><span class="sxs-lookup"><span data-stu-id="1e319-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="1e319-301">Vous pouvez utiliser MRTK_Select_Main et MRTK_Select_Secondary des clips audio dans le `/SDK/StandardAssets/Audio/` dossier.</span><span class="sxs-lookup"><span data-stu-id="1e319-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="1e319-302">4. Ajout d’États visuels et gestion des événements d’interaction Far</span><span class="sxs-lookup"><span data-stu-id="1e319-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="1e319-303">L’opération [interactive](interactable.md) est un script qui facilite la création d’un état visuel pour les différents types d’interactions d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1e319-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="1e319-304">Il gère également les événements d’interaction Far.</span><span class="sxs-lookup"><span data-stu-id="1e319-304">It also handles far interaction events.</span></span> <span data-ttu-id="1e319-305">Ajoutez `Interactable.cs` et glissez-déposez l’objet cube dans le champ **cible** sous **profils**.</span><span class="sxs-lookup"><span data-stu-id="1e319-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="1e319-306">Créez ensuite un nouveau thème avec un type **ScaleOffsetColorTheme**.</span><span class="sxs-lookup"><span data-stu-id="1e319-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="1e319-307">Sous ce thème, vous pouvez spécifier la couleur de l’objet pour les États d’interaction spécifiques, tels que **focus** et **enfoncé**.</span><span class="sxs-lookup"><span data-stu-id="1e319-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="1e319-308">Vous pouvez également contrôler l’échelle et le décalage.</span><span class="sxs-lookup"><span data-stu-id="1e319-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="1e319-309">Vérifiez l' **accélération** et définissez Duration pour lisser la transition visuelle.</span><span class="sxs-lookup"><span data-stu-id="1e319-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Sélectionner le thème du profil](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="1e319-311">Vous verrez que l’objet répond à la fois aux interactions Far (Ray ou point de regard) et près (main).</span><span class="sxs-lookup"><span data-stu-id="1e319-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="1e319-312">Exemples de boutons personnalisés</span><span class="sxs-lookup"><span data-stu-id="1e319-312">Custom button examples</span></span>

<span data-ttu-id="1e319-313">Dans la [scène HandInteractionExample](../example-scenes/hand-interaction-examples.md), consultez les exemples de bouton piano et rond qui utilisent tous les deux `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="1e319-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="1e319-314">Chaque clé piano est associée à un `PressableButton` et à un `NearInteractionTouchable` script.</span><span class="sxs-lookup"><span data-stu-id="1e319-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="1e319-315">Il est important de vérifier que la direction de *transfert local* de `NearInteractionTouchable` est correcte.</span><span class="sxs-lookup"><span data-stu-id="1e319-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="1e319-316">Elle est représentée par une flèche blanche dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="1e319-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="1e319-317">Assurez-vous que la flèche pointe sur la face avant du bouton :</span><span class="sxs-lookup"><span data-stu-id="1e319-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="1e319-318">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e319-318">See also</span></span>

* [<span data-ttu-id="1e319-319">Avec interaction</span><span class="sxs-lookup"><span data-stu-id="1e319-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="1e319-320">Thèmes visuels</span><span class="sxs-lookup"><span data-stu-id="1e319-320">Visual Themes</span></span>](visual-themes.md)
