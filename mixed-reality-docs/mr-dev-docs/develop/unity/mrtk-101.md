---
title: MRTK 101 - Guide pratique pour utiliser Mixed Reality Toolkit d’Unity pour les interactions spatiales courantes (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Guide pratique pour utiliser Mixed Reality Toolkit avec Unity pour les interactions de base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, conception, exemple d’application, contrôles
ms.localizationpriority: high
ms.openlocfilehash: d10de5c9f16e0caa289d5110647b4c45a8a8fcf9
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386264"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="d14dc-104">MRTK 101 : Guide pratique pour utiliser Mixed Reality Toolkit d’Unity pour les interactions spatiales courantes</span><span class="sxs-lookup"><span data-stu-id="d14dc-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>
![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="d14dc-106">Découvrez comment utiliser MRTK pour obtenir certains des modèles d’interaction les plus largement utilisés dans le domaine de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="d14dc-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="d14dc-107">Comment simuler des interactions d’entrée dans l’éditeur Unity ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="d14dc-108">Comment saisir et déplacer un objet ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-108">How to grab and move an object?</span></span>
- <span data-ttu-id="d14dc-109">Comment redimensionner un objet ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-109">How to resize an object?</span></span>
- <span data-ttu-id="d14dc-110">Comment déplacer ou faire pivoter un objet avec précision ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="d14dc-111">Comment faire en sorte qu’un objet réponde à des événements d’entrée ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="d14dc-112">Comment ajouter un retour visuel ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-112">How to add visual feedback?</span></span>
- <span data-ttu-id="d14dc-113">Comment ajouter un retour audio ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-113">How to add audio feedback?</span></span>
- <span data-ttu-id="d14dc-114">Comment utiliser des préfabriqués de bouton de style HoloLens 2 ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="d14dc-115">Comment faire en sorte qu’un objet vous suive ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-115">How to make an object follow you?</span></span>
- <span data-ttu-id="d14dc-116">Comment faire en sorte qu’un objet se mette en face de vous ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="d14dc-117">Cet article a été mis à jour de façon à refléter les modifications apportées à la [publication de MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span><span class="sxs-lookup"><span data-stu-id="d14dc-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="d14dc-118">Tout le contenu de cette page peut être testé dans l’éditeur Unity avec la simulation d’entrée de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d14dc-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="d14dc-119">Si vous n’en disposez pas, suivez le [Guide d’installation de MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) pour installer la dernière version de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d14dc-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="d14dc-120">Comment simuler des interactions d’entrée dans l’éditeur Unity ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-120">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="d14dc-121">MRTK prend en charge la simulation d’une entrée dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="d14dc-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="d14dc-122">Exécutez simplement votre scène en cliquant sur le bouton de lecture dans Unity.</span><span class="sxs-lookup"><span data-stu-id="d14dc-122">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="d14dc-123">Utilisez ces touches pour simuler une entrée.</span><span class="sxs-lookup"><span data-stu-id="d14dc-123">Use these keys to simulate input.</span></span>
<span data-ttu-id="d14dc-124">Appuyez sur les touches W, A, S, D pour déplacer la caméra.</span><span class="sxs-lookup"><span data-stu-id="d14dc-124">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="d14dc-125">Maintenez le bouton droit de la souris enfoncé et déplacez la souris pour regarder autour de vous.</span><span class="sxs-lookup"><span data-stu-id="d14dc-125">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="d14dc-126">Pour faire apparaître les mains simulées, appuyez sur la barre d’espace (avec la main droite) ou sur la touche Maj gauche (avec la main gauche). Pour garder les mains simulées dans la vue, appuyez sur la touche T ou Y. Pour faire pivoter les mains simulées, appuyez sur Q ou E (horizontal)/R ou F (vertical).</span><span class="sxs-lookup"><span data-stu-id="d14dc-126">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="d14dc-127">En savoir plus sur la simulation d’entrée dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-127">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="d14dc-128">Comment saisir et déplacer un objet ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-128">How to grab and move an object?</span></span>
<span data-ttu-id="d14dc-129">Pour rendre un objet saisissable, affectez ces deux scripts : **ObjectManipulator.cs** et **NearInteractionGrabbable.cs** (pour une entrée par saisie directe avec le suivi de la main articulée). ObjectManipulator prend en charge les interactions proches et éloignées.</span><span class="sxs-lookup"><span data-stu-id="d14dc-129">To make an object grabbable, assign these two scripts: **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** (for direct grab with articulated hand tracking input) ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="d14dc-130">Avec Hololens 2, vous pouvez saisir et déplacer un objet avec une entrée par suivi de la main articulée (interaction proche), avec un rayon émanant de la main (interaction éloignée), avec le faisceau du contrôleur de mouvement (interaction éloignée), avec le curseur oculaire HoloLens et le clic aérien (interaction éloignée).</span><span class="sxs-lookup"><span data-stu-id="d14dc-130">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="d14dc-131">Comment redimensionner un objet ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-131">How to resize an object?</span></span>
<span data-ttu-id="d14dc-132">**ObjectManipulator.cs** prend en charge la rotation/mise à l’échelle à deux mains.</span><span class="sxs-lookup"><span data-stu-id="d14dc-132">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="d14dc-133">Cela fonctionne avec divers types d’entrée : suivi de la main articulée avec HoloLens 2, pointage du regard + mouvement avec HoloLens 1 et contrôleur de mouvement du casque immersif de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d14dc-133">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="d14dc-134">En savoir plus sur Object Manipulator dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-134">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="d14dc-135">Comment déplacer ou faire pivoter un objet avec précision ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-135">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="d14dc-136">Affectez **BoundsControl.cs** à un objet pour utiliser un cadre englobant qui constitue l’interface pour la mise à l’échelle et la rotation d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d14dc-136">Assign **BoundsControl.cs** to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="d14dc-137">Par défaut, il présente les poignées et les lignes bleues de style HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="d14dc-137">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="d14dc-138">Pour utiliser des poignées animées de proximité de style HoloLens 2, vous devez affecter des préfabriqués et des matériaux.</span><span class="sxs-lookup"><span data-stu-id="d14dc-138">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="d14dc-139">En savoir plus sur le contrôle des limites dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-139">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="d14dc-140">Comment faire en sorte qu’un objet réponde à des événements d’entrée ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-140">How to make an object respond to input events?</span></span>
<span data-ttu-id="d14dc-141">Affectez **PointerHandler.cs** à un objet.</span><span class="sxs-lookup"><span data-stu-id="d14dc-141">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="d14dc-142">Dans l’inspecteur, vous allez pouvoir utiliser des événements OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Pour utiliser ces événements dans un script, implémentez **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="d14dc-142">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="d14dc-143">En savoir plus sur le système d’entrée dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-143">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="d14dc-144">Comment ajouter un retour visuel ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-144">How to add visual feedback?</span></span>
<span data-ttu-id="d14dc-145">Affectez **Interactable.cs** à un objet.</span><span class="sxs-lookup"><span data-stu-id="d14dc-145">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="d14dc-146">Dans l’inspecteur, ajoutez l’objet cible et créez un thème.</span><span class="sxs-lookup"><span data-stu-id="d14dc-146">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="d14dc-147">À l’aide des profils de thème d’Interactable, vous pouvez facilement ajouter un retour visuel à tous les états d’interaction d’entrée disponibles.</span><span class="sxs-lookup"><span data-stu-id="d14dc-147">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="d14dc-148">Interactable fournit divers types de thèmes, notamment le thème du nuanceur, qui vous permet de contrôler les propriétés du nuanceur par état d’interaction.</span><span class="sxs-lookup"><span data-stu-id="d14dc-148">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="d14dc-149">En savoir plus sur Interactable dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-149">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="d14dc-150">Un autre module important pour le feedback visuel est le **nuanceur MRTK standard**.</span><span class="sxs-lookup"><span data-stu-id="d14dc-150">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="d14dc-151">Avec le nuanceur MRTK standard, vous pouvez facilement ajouter des effets de retour visuel comme une lumière de survol et une lumière de proximité.</span><span class="sxs-lookup"><span data-stu-id="d14dc-151">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="d14dc-152">Étant donné que le nuanceur MRTK standard effectue beaucoup moins de calcul que le nuanceur Unity standard, vous pouvez ainsi créer une expérience performante.</span><span class="sxs-lookup"><span data-stu-id="d14dc-152">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="d14dc-153">Créez un matériau et sélectionnez le nuanceur « Mixed Reality Toolkit > Standard ».</span><span class="sxs-lookup"><span data-stu-id="d14dc-153">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="d14dc-154">Ou vous pouvez choisir l’un des matériaux existants qui utilisent le nuanceur MRTK standard.</span><span class="sxs-lookup"><span data-stu-id="d14dc-154">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="d14dc-155">En savoir plus sur le nuanceur MRTK standard dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-155">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="d14dc-156">Comment ajouter un retour audio ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-156">How to add audio feedback?</span></span>
<span data-ttu-id="d14dc-157">Ajoutez **AudioSource** à un objet.</span><span class="sxs-lookup"><span data-stu-id="d14dc-157">Add **AudioSource** to an object.</span></span> <span data-ttu-id="d14dc-158">Ensuite, dans les scripts qui exposent des événements d’entrée (par exemple Interactable.cs ou PointerHandler.cs), affectez l’objet avec AudioSource à l’événement et sélectionnez **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="d14dc-158">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="d14dc-159">Vous pouvez utiliser vos clips audio ou en choisir un à partir des ressources audio de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d14dc-159">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="d14dc-160">Comment utiliser des préfabriqués de bouton de style HoloLens 2 ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-160">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="d14dc-161">MRTK fournit divers types de boutons de style shell (système d’exploitation) HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d14dc-161">MRTK provides various types of HoloLens 2's shell (OS) style buttons.</span></span> <span data-ttu-id="d14dc-162">Il offre des feedbacks visuels sophistiqués, comme la lumière de proximité, le cadre de compression et un effet d’ondulation à la surface du bouton qui améliorent la confiance de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d14dc-162">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="d14dc-163">Il vous suffit de glisser-déposer un des **préfabriqués de boutons sur lequel appuyer de style HoloLens 2** dans votre scène.</span><span class="sxs-lookup"><span data-stu-id="d14dc-163">Simply drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="d14dc-164">Le préfabriqué utilise Interactable.cs, décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="d14dc-164">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="d14dc-165">Vous pouvez utiliser des événements exposés comme OnClick() dans Interactable pour déclencher des actions.</span><span class="sxs-lookup"><span data-stu-id="d14dc-165">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="d14dc-166">En savoir plus sur les préfabriqués de bouton dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-166">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="d14dc-167">Comment faire en sorte qu’un objet vous suive ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-167">How to make an object follow you?</span></span>
<span data-ttu-id="d14dc-168">Affectez le script **RadialView.cs** ou **Follow.cs** à un objet.</span><span class="sxs-lookup"><span data-stu-id="d14dc-168">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="d14dc-169">Il fait partie de la série de scripts Solver qui vous permet d’obtenir divers types de positionnement des objets dans l’espace 3D.</span><span class="sxs-lookup"><span data-stu-id="d14dc-169">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="d14dc-170">**SolverHandler.cs** est ajouté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d14dc-170">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="d14dc-171">Voici un exemple de configuration de RadialView pour obtenir un comportement de suivi tardif, à l’instar du menu Démarrer dans le shell HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d14dc-171">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="d14dc-172">Vous pouvez spécifier la distance minimale/maximale et les degrés d’affichage minimaux/maximaux.</span><span class="sxs-lookup"><span data-stu-id="d14dc-172">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="d14dc-173">L’exemple ci-dessous montre le positionnement de l’objet dans une plage comprise entre 0,4 et 0,8 mètre à 15 °.</span><span class="sxs-lookup"><span data-stu-id="d14dc-173">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="d14dc-174">Ajustez les valeurs de délai Lerp pour accélérer ou ralentir la mise à jour de la position.</span><span class="sxs-lookup"><span data-stu-id="d14dc-174">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="d14dc-175">En savoir plus sur Solver dans la documentation MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-175">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="d14dc-176">Comment faire en sorte qu’un objet se mette en face de vous ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-176">How to make an object face you?</span></span>
<span data-ttu-id="d14dc-177">Affectez le script **Billboard.cs** à un objet.</span><span class="sxs-lookup"><span data-stu-id="d14dc-177">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="d14dc-178">L’objet vous fera toujours face, quelle que soit votre position.</span><span class="sxs-lookup"><span data-stu-id="d14dc-178">It will always face you, regardless of your position.</span></span> <span data-ttu-id="d14dc-179">Vous pouvez spécifier l’option d’axe pivot.</span><span class="sxs-lookup"><span data-stu-id="d14dc-179">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="d14dc-180">Vous êtes prêt à créer des expériences étonnantes pour la réalité mixte ?</span><span class="sxs-lookup"><span data-stu-id="d14dc-180">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="d14dc-181">Consultez les pages ci-dessous pour en savoir plus sur MRTK et la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="d14dc-181">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d14dc-182">À propos de l’auteur</span><span class="sxs-lookup"><span data-stu-id="d14dc-182">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d14dc-183"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="d14dc-183"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d14dc-184">Concepteur d’expérience utilisateur @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d14dc-184">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d14dc-185">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="d14dc-185">Next Development Checkpoint</span></span>

<span data-ttu-id="d14dc-186">Si vous suivez le parcours de points de contrôle de développement Unity que nous avons élaboré, vous explorez actuellement les composants de base de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d14dc-186">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="d14dc-187">À partir de là, vous pouvez passer au composant suivant :</span><span class="sxs-lookup"><span data-stu-id="d14dc-187">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="d14dc-188">Appareil photo</span><span class="sxs-lookup"><span data-stu-id="d14dc-188">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="d14dc-189">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="d14dc-189">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d14dc-190">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="d14dc-190">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="d14dc-191">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="d14dc-191">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d14dc-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d14dc-192">See also</span></span>
* [<span data-ttu-id="d14dc-193">MRTK - Guide d’installation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d14dc-193">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="d14dc-194">Mixed Reality Toolkit - Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="d14dc-194">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="d14dc-195">Portail de la documentation MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d14dc-195">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="d14dc-196">Instructions de portage de HoloToolkit vers MRTK</span><span class="sxs-lookup"><span data-stu-id="d14dc-196">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
