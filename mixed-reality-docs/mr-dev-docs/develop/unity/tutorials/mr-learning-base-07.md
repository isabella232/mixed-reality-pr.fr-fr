---
title: Interaction avec les objets 3D
description: Ce cours vous montre comment utiliser Mixed Reality Toolkit (MRTK) pour interagir avec des objets 3D et les manipuler dans des applications de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, interactions avec des objets, contrôle des limites
ms.localizationpriority: high
ms.openlocfilehash: 1ab7b3a334639be564717d77d3bbc478a25e8326
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237240"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="14275-104">7. Interaction avec les objets 3D</span><span class="sxs-lookup"><span data-stu-id="14275-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="14275-105">Dans ce tutoriel, vous allez apprendre à activer la manipulation proche et lointaine des objets 3D et à limiter les types de manipulation autorisés.</span><span class="sxs-lookup"><span data-stu-id="14275-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="14275-106">Vous allez aussi découvrir comment ajouter des contrôles de limites autour des objets 3D afin de faciliter le contrôle de la manipulation des objets.</span><span class="sxs-lookup"><span data-stu-id="14275-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="14275-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="14275-107">Objectives</span></span>

* <span data-ttu-id="14275-108">Apprendre à configurer des objets 3D afin de pouvoir interagir avec</span><span class="sxs-lookup"><span data-stu-id="14275-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="14275-109">Découvrir comment ajouter un contrôle de limites à des objets 3D</span><span class="sxs-lookup"><span data-stu-id="14275-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="14275-110">Manipulation d’objets 3D</span><span class="sxs-lookup"><span data-stu-id="14275-110">Manipulating 3D objects</span></span>

<span data-ttu-id="14275-111">Dans cette section, vous allez ajouter la capacité à manipuler toutes les pièces du Rover que vous avez disposées sur la table durant le tutoriel [Positionnement des objets dans la scène](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="14275-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="14275-112">Voici les principales étapes à suivre pour y parvenir :</span><span class="sxs-lookup"><span data-stu-id="14275-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="14275-113">Ajouter le composant Object Manipulator (Script) à tous les objets de la pièce</span><span class="sxs-lookup"><span data-stu-id="14275-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="14275-114">Ajouter le composant NearInteractionGrabbable à tous les objets de la pièce</span><span class="sxs-lookup"><span data-stu-id="14275-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="14275-115">Configurer le composant Object Manipulator (Script)</span><span class="sxs-lookup"><span data-stu-id="14275-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="14275-116">Pour pouvoir **manipuler un objet**, celui-ci doit avoir les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="14275-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="14275-117">Le composant **Collider**, par exemple un Box Collider</span><span class="sxs-lookup"><span data-stu-id="14275-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="14275-118">Le composant **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="14275-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="14275-119">Pour pouvoir **manipuler** et **saisir** un objet avec les mains suivies, celui-ci doit avoir les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="14275-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="14275-120">Le composant **Collider**, par exemple un Box Collider</span><span class="sxs-lookup"><span data-stu-id="14275-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="14275-121">Le composant **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="14275-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="14275-122">Le composant **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="14275-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="14275-123">De plus, vous configurerez le RoverExplorer afin de pouvoir placer les pièces du Rover sur le Rover pour en faire un assemblage complet.</span><span class="sxs-lookup"><span data-stu-id="14275-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="14275-124">Dans la fenêtre de hiérarchie, développez l’objet RoverExplorer > **RoverParts** et sélectionnez tous ses objets de pièces de Rover enfants et l’objet **RoverAssembly** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** (Ajouter un composant) pour ajouter les composants suivants à tous les objets sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="14275-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="14275-125">Le composant **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="14275-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="14275-126">Le composant **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="14275-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="14275-127">Le composant **Part Assembly Controller (Script)**</span><span class="sxs-lookup"><span data-stu-id="14275-127">**Part Assembly Controller (Script)** component</span></span>

![Unity avec RoverAssembly et tous les objets de composant du Rover sélectionnés, et les composants ajoutés](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="14275-129">Pour sélectionner plusieurs objets qui ne sont pas les uns à côté des autres, appuyez sur la touche Ctrl et maintenez-la enfoncée pendant que vous utilisez la souris pour sélectionner un objet.</span><span class="sxs-lookup"><span data-stu-id="14275-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="14275-130">Quand vous ajoutez un Object Manipulator (Script), dans ce cas, le Constraint Manager (Script) est ajouté automatiquement, car Object Manipulator (Script) en dépend.</span><span class="sxs-lookup"><span data-stu-id="14275-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="14275-131">Dans le cadre de ce tutoriel, des colliders ont déjà été ajoutés aux pièces du Rover.</span><span class="sxs-lookup"><span data-stu-id="14275-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="14275-132">Pour plus d’informations sur les colliders, vous pouvez consulter la documentation <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> d’Unity.</span><span class="sxs-lookup"><span data-stu-id="14275-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="14275-133">Part Assembly Controller (Script) ne fait pas partie du MRTK, mais il a été inclus avec les ressources du tutoriel.</span><span class="sxs-lookup"><span data-stu-id="14275-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="14275-134">Toujours avec les objets de pièces de Rover et l’objet RoverAssembly sélectionnés, dans la fenêtre de l’inspecteur, configurez le composant **Object Manipulator (Script)** comme suit :</span><span class="sxs-lookup"><span data-stu-id="14275-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="14275-135">Dans la liste déroulante **Two Handed Manipulation Type** (Type de manipulation à deux mains), décochez Scale (Mise à l’échelle) afin que seuls **Move** (Déplacer) et **Rotate** (Faire pivoter) soient activés.</span><span class="sxs-lookup"><span data-stu-id="14275-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![Unity avec Two Handed Manipulation Type configuré](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="14275-137">À ce stade, vous avez activé la manipulation d’objet pour tous les objets de pièces de Rover et l’objet RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="14275-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="14275-138">Dans la fenêtre Project, accédez au dossier **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** pour trouver les clips audio :</span><span class="sxs-lookup"><span data-stu-id="14275-138">In the Project window, navigate to **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** folder to locate the audio clips:</span></span>

![Fenêtre de projet Unity avec le dossier Audio sélectionné](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="14275-140">Dans la fenêtre de hiérarchie, resélectionnez tous les **objets de pièces de Rover** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** pour ajouter le composant **Audio Sources** et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="14275-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="14275-141">Affectez le clip audio **MRTK_Scale_Start** au champ **AudioClip**.</span><span class="sxs-lookup"><span data-stu-id="14275-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="14275-142">Décochez la case **Play On Awake** (Lire en cas d’activité)</span><span class="sxs-lookup"><span data-stu-id="14275-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="14275-143">Affectez la valeur 1 à **Spatial Blend**.</span><span class="sxs-lookup"><span data-stu-id="14275-143">Change **Spatial Blend** to 1</span></span>

![Unity avec tous les objets de composant du Rover sélectionnés, et le composant Audio Source ajouté et configuré](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="14275-145">Dans la fenêtre de hiérarchie, développez l’objet RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** pour révéler tous les objets d’indicateur de placement, puis sélectionnez la première pièce de Rover, RoverParts > **Camera_Part**, et configurez le composant **Part Assembly Controller (Script)** comme suit :</span><span class="sxs-lookup"><span data-stu-id="14275-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="14275-146">Assignez l’objet **Camera_PlacementHint** au champ **Location To Place** (Emplacement).</span><span class="sxs-lookup"><span data-stu-id="14275-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Unity avec composant Camera_Part PartAssemblyController configuré](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="14275-148">**Répétez** cette étape pour chacun des objets de pièces de Rover restants et l’objet RoverAssembly afin de configurer le composant **Part Assembly Controller (Script)** comme suit :</span><span class="sxs-lookup"><span data-stu-id="14275-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="14275-149">Pour **Generator_Part**, assignez l’objet **Generator_PlacementHint** au champ **Location To Place**.</span><span class="sxs-lookup"><span data-stu-id="14275-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="14275-150">Pour **Lights_Part**, assignez l’objet **Lights_PlacementHint** au champ **Location To Place**.</span><span class="sxs-lookup"><span data-stu-id="14275-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="14275-151">Pour **UHFAntenna_Part**, assignez l’objet **UHFAntenna_PlacementHint** au champ **Location To Place**.</span><span class="sxs-lookup"><span data-stu-id="14275-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="14275-152">Pour **Spectrometer_Part**, assignez l’objet **Spectrometer_PlacementHint** au champ **Location To Place**.</span><span class="sxs-lookup"><span data-stu-id="14275-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="14275-153">Pour **RoverAssembly**, assignez l’objet lui-même (c’est-à-dire le même objet **RoverAssembly**), au champ **Location To Place**.</span><span class="sxs-lookup"><span data-stu-id="14275-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="14275-154">Dans la fenêtre de hiérarchie, sélectionnez l’objet de bouton RoverExplorer > Buttons > **Reset** puis, dans la fenêtre de l’inspecteur, configurez l’événement **OnClick ()** comme suit :</span><span class="sxs-lookup"><span data-stu-id="14275-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="14275-155">Assignez l’objet **RoverAssembly** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="14275-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="14275-156">Dans la liste déroulante **No Function**, sélectionnez **PartAssemblyController** > **ResetPlacement ()** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="14275-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity avec l’événement OnClick de l’objet de bouton Reset configuré](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="14275-158">Si vous basculez maintenant en mode Game, vous pouvez utiliser l’interaction proche ou lointaine pour placer les pièces sur le Rover.</span><span class="sxs-lookup"><span data-stu-id="14275-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="14275-159">Une fois que la pièce est proche de l’indicateur de placement correspondant, elle s’imbrique en place et devient partie intégrante du Rover.</span><span class="sxs-lookup"><span data-stu-id="14275-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="14275-160">Pour réinitialiser les placements, vous pouvez appuyer sur le bouton Reset :</span><span class="sxs-lookup"><span data-stu-id="14275-160">To reset the placements, you can press the Reset button:</span></span>

![Vue partagée du mode Play d’Unity avec le bouton Reset enfoncé](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="14275-162">Pour en savoir plus sur le composant Object Manipulator et ses propriétés associées, vous pouvez consulter le guide [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span><span class="sxs-lookup"><span data-stu-id="14275-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="adding-bounds-control"></a><span data-ttu-id="14275-163">Ajout d’un contrôle des limites</span><span class="sxs-lookup"><span data-stu-id="14275-163">Adding Bounds Control</span></span>

<span data-ttu-id="14275-164">Un contrôle des limites (BoundsControl) rend plus facile et plus intuitive la manipulation d’objets avec une main pour l’interaction proche et lointaine, en fournissant des poignées qui peuvent être utilisées pour la mise à l’échelle et la rotation.</span><span class="sxs-lookup"><span data-stu-id="14275-164">Bounds Control makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="14275-165">Dans cet exemple, vous allez ajouter un BoundsControl à l’objet RoverExplorer pour faciliter son déplacement, sa rotation et sa mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="14275-165">In this example, you will add a BoundsControl to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="14275-166">Vous allez aussi configurer le menu afin de pouvoir activer ou désactiver le contrôle des limites.</span><span class="sxs-lookup"><span data-stu-id="14275-166">Additionally, you will configure the Menu so you can turn the Bounds Control on and off.</span></span>

<span data-ttu-id="14275-167">Dans la fenêtre de hiérarchie, sélectionnez l’objet **RoverExplorer** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** pour ajouter les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="14275-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="14275-168">Composant **BoundsControl**</span><span class="sxs-lookup"><span data-stu-id="14275-168">**BoundsControl** component</span></span>
* <span data-ttu-id="14275-169">Le composant **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="14275-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="14275-170">Ensuite, **décochez** la case en regard de tous les composants afin de les rendre **désactivés** par défaut :</span><span class="sxs-lookup"><span data-stu-id="14275-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![Unity avec l’objet RoverExplorer sélectionné, et des composants ajoutés et désactivés](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="14275-172">La visualisation du contrôle des limites est créée au moment de l’exécution et n’est donc pas visible avant l’entrée en mode Game.</span><span class="sxs-lookup"><span data-stu-id="14275-172">The Bounds Control visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
><span data-ttu-id="14275-173">Object Manipulator (Script) ajoute automatiquement Constraint Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="14275-173">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="14275-174">Dans la fenêtre de hiérarchie, développez l’objet Menu > **ButtonCollection** pour afficher les quatre boutons et renommez le troisième bouton **BoundsControl_Enable** puis, dans la fenêtre de l’inspecteur, configurez le composant **Button Config Helper (Script)** comme suit :</span><span class="sxs-lookup"><span data-stu-id="14275-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundsControl_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="14275-175">Affectez la valeur **Enable** à **Main Label Text** (Texte de l'étiquette principale).</span><span class="sxs-lookup"><span data-stu-id="14275-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="14275-176">Assignez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="14275-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="14275-177">Dans la liste déroulante **No Function**, sélectionnez **BoundsControl** > **bool enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="14275-177">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="14275-178">Vérifiez que la case de l’argument est **cochée**.</span><span class="sxs-lookup"><span data-stu-id="14275-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="14275-179">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="14275-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="14275-180">Assignez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="14275-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="14275-181">Dans la liste déroulante **No Function**, sélectionnez **ObjectManipulator** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="14275-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="14275-182">Vérifiez que la case de l’argument est **cochée**.</span><span class="sxs-lookup"><span data-stu-id="14275-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="14275-183">Conservez « cube avec contrôle des limites » comme **icône**.</span><span class="sxs-lookup"><span data-stu-id="14275-183">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![Unity avec l’objet de bouton BoundsControl_Enable sélectionné et le composant Button Config Helper configuré](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="14275-185">Renommez **BoundsControl_Disable** le quatrième et dernier bouton puis, dans la fenêtre de l’inspecteur, configurez le composant **Button Config Helper (Script)** comme suit :</span><span class="sxs-lookup"><span data-stu-id="14275-185">Rename the forth and last button to **BoundsControl_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="14275-186">Affectez la valeur **Disable** à **Main Label Text**.</span><span class="sxs-lookup"><span data-stu-id="14275-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="14275-187">Assignez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="14275-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="14275-188">Dans la liste déroulante **No Function**, sélectionnez **BoundsControl** > **bool enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="14275-188">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="14275-189">Vérifiez que la case de l’argument est **décochée**.</span><span class="sxs-lookup"><span data-stu-id="14275-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="14275-190">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="14275-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="14275-191">Assignez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="14275-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="14275-192">Dans la liste déroulante **No Function**, sélectionnez **ObjectManipulator** > **bool Enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="14275-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="14275-193">Vérifiez que la case de l’argument est **décochée**.</span><span class="sxs-lookup"><span data-stu-id="14275-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="14275-194">Remplacez l’**icône** par « cube avec contrôle des limites ».</span><span class="sxs-lookup"><span data-stu-id="14275-194">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![Unity avec l’objet de bouton BoundsControl_Disable sélectionné et le composant Button Config Helper configuré](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="14275-196">Si vous passez maintenant en mode Game et que vous activez le contrôle des limites en cliquant sur le bouton Enable, vous pouvez utiliser l’interaction proche ou lointaine pour le déplacer, faire pivoter et mettre à l’échelle, et utiliser le bouton Disable pour le désactiver à nouveau :</span><span class="sxs-lookup"><span data-stu-id="14275-196">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounds Control, and use the Disable button to disable the Bounds Control again:</span></span>

![Vue partagée du mode Play de Unity avec le contrôle des limites en train d’être manipulé](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="14275-198">Pour plus d’informations sur le composant BoundsControl et ses propriétés associées, vous pouvez consulter le guide [Bounds Control](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span><span class="sxs-lookup"><span data-stu-id="14275-198">To learn more about the Bounds Control component and its associated properties, you can visit the [Bounds Control](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="congratulations"></a><span data-ttu-id="14275-199">Félicitations</span><span class="sxs-lookup"><span data-stu-id="14275-199">Congratulations</span></span>

<span data-ttu-id="14275-200">Dans ce tutoriel, vous avez appris à activer la manipulation proche et lointaine pour les objets 3D et comment limiter les types de manipulation autorisés.</span><span class="sxs-lookup"><span data-stu-id="14275-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="14275-201">Vous avez aussi appris à ajouter un contrôle des limites autour des objets 3D afin de faciliter le contrôle de la manipulation des objets.</span><span class="sxs-lookup"><span data-stu-id="14275-201">You also learned how to add Bounds Control around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="14275-202">Tutoriel suivant : 8. Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="14275-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
