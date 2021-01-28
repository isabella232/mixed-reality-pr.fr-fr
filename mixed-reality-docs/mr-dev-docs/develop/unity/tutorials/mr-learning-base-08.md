---
title: Utilisation du suivi oculaire
description: Ce cours vous montre comment utiliser le suivi oculaire dans votre application de réalité mixte avec Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, suivi oculaire
ms.localizationpriority: high
ms.openlocfilehash: 5efe1c54d9e3b4096dfec4221e4ce04e7370ca47
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635472"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="c1b6a-104">8. Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="c1b6a-104">8. Using eye-tracking</span></span>

<span data-ttu-id="c1b6a-105">Dans ce tutoriel, vous allez voir comment activer le suivi oculaire (eye-tracking) pour HoloLens 2 et comment l’ajouter aux objets en vue de déclencher des actions lorsque l’utilisateur regarde ces objets.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="c1b6a-106">Si vous déployez également ce projet sur HoloLens (1re génération), notez que le suivi oculaire est pris en charge uniquement sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="c1b6a-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="c1b6a-107">Objectives</span></span>

* <span data-ttu-id="c1b6a-108">Apprendre à activer le suivi oculaire pour HoleLens 2</span><span class="sxs-lookup"><span data-stu-id="c1b6a-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="c1b6a-109">Apprendre à utiliser le suivi oculaire pour déclencher une action</span><span class="sxs-lookup"><span data-stu-id="c1b6a-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="c1b6a-110">Vérifier que la fonctionnalité d’entrée avec le pointage du regard est activée</span><span class="sxs-lookup"><span data-stu-id="c1b6a-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="c1b6a-111">Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Eye Gaze Input Capability** est grisée :</span><span class="sxs-lookup"><span data-stu-id="c1b6a-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Fenêtre MRTK Project Configurator d’Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="c1b6a-113">La fonctionnalité Gaze Input doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](mr-learning-base-02.md#creating-and-configuring-the-scene) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="c1b6a-114">Toutefois, si elle n’est pas activée, activez-la maintenant.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="c1b6a-115">Activation du pointage du regard dans le fournisseur de regard</span><span class="sxs-lookup"><span data-stu-id="c1b6a-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="c1b6a-116">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet MixedRealityToolkit > **Input**, puis effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1b6a-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="c1b6a-117">Clonez **DefaultHoloLens2InputSystemProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="c1b6a-118">Développez la section **Pointers**.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="c1b6a-119">Clonez **DefaultMixedRealityPointerProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="c1b6a-120">Recherchez la section **Gaze Settings** (Paramètres du regard), puis cochez la case **Is Eye Tracking Enabled** (Activation du suivi oculaire).</span><span class="sxs-lookup"><span data-stu-id="c1b6a-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Composant MixedRealityToolkit d’Unity avec les profils nouvellement créés appliqués et le suivi du regard activé](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="c1b6a-122">Pour obtenir un rappel de la façon de cloner des profils MRTK, vous pouvez consulter les instructions fournies dans [Configuration des profils MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="c1b6a-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="c1b6a-123">Activation du suivi oculaire simulé pour l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="c1b6a-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="c1b6a-124">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, accédez à l’onglet **Input**, puis :</span><span class="sxs-lookup"><span data-stu-id="c1b6a-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="c1b6a-125">Développez la section **Input Data Providers** > **Input Simulation Service**.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="c1b6a-126">Clonez **DefaultMixedRealityInputSimulationProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="c1b6a-127">Recherchez **Eye Gaze Simulation** et définissez **Default Eye Gaze Simulation Mode** sur **Camera Forward Axis**</span><span class="sxs-lookup"><span data-stu-id="c1b6a-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity avec l’objet TextMeshPro sélectionné](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="c1b6a-129">Ajout du suivi oculaire aux objets</span><span class="sxs-lookup"><span data-stu-id="c1b6a-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="c1b6a-130">Dans la fenêtre Hierarchy, développez l’objet RoverExplorer > **Buttons**, puis, pour chacun des trois objets enfants Buttons, développez et sélectionnez l’objet SeeItSayItLabel > **TextMeshPro** :</span><span class="sxs-lookup"><span data-stu-id="c1b6a-130">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![Unity avec l’objet TextMeshPro sélectionné](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="c1b6a-132">Avec les trois objets TextMeshPro toujours sélectionnés, dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter les composants suivants à tous les objets sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="c1b6a-132">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="c1b6a-133">Composant **Box Collider**</span><span class="sxs-lookup"><span data-stu-id="c1b6a-133">**Box Collider** component</span></span>
* <span data-ttu-id="c1b6a-134">Composant **EyeTrackingTarget**</span><span class="sxs-lookup"><span data-stu-id="c1b6a-134">**EyeTrackingTarget** component</span></span>

![Unity avec l’objet TextMeshPro sélectionné et des composants ajoutés](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="c1b6a-136">Dans la fenêtre Hierarchy, sélectionnez l’objet **Hints** > SeeItSayItLabel > **TextMeshPro**, puis configurez le composant **EyeTrackingTarget** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="c1b6a-136">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="c1b6a-137">Dans la section d’événement **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="c1b6a-137">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="c1b6a-138">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-138">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="c1b6a-139">Affectez l’objet **TextMeshPro** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="c1b6a-139">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="c1b6a-140">Dans la liste déroulante **No Function**, sélectionnez **TextMeshPro** > **float fontSize** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-140">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="c1b6a-141">Définissez l’argument sur **0.06** pour augmenter la taille de police actuelle (0.04) de 50 %.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-141">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="c1b6a-142">Dans la section d’événement **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="c1b6a-142">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="c1b6a-143">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-143">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="c1b6a-144">Affectez l’objet **TextMeshPro** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="c1b6a-144">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="c1b6a-145">Dans la liste déroulante **No Function**, sélectionnez **TextMeshPro** > **float fontSize** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-145">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="c1b6a-146">Définissez l’argument sur **0.04** pour rétablir la taille de la police à 0.04.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-146">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity avec l’objet Hints TextMeshPro sélectionné et le composant EyeTrackingTarget configuré](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="c1b6a-148">**Répétez** cette étape pour l’objet **Explode** > SeeItSayItLabel > **TextMeshPro** et pour l’objet **Reset** > SeeItSayItLabel > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-148">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="c1b6a-149">Si vous passez maintenant en mode jeu, puis maintenez enfoncé le bouton droit de la souris tout en déplaçant la souris jusqu’à ce que le regard atteigne l’une des étiquettes, vous verrez que la taille de police augmente de 50 % et retourne à sa taille d’origine lorsque l’utilisateur regarde ailleurs :</span><span class="sxs-lookup"><span data-stu-id="c1b6a-149">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![Vue partagée du mode Play d’Unity avec le suivi atteignant Eye Tracking Target - Étiquette du bouton Explode](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="c1b6a-151">Félicitations</span><span class="sxs-lookup"><span data-stu-id="c1b6a-151">Congratulations</span></span>

<span data-ttu-id="c1b6a-152">Dans ce tutoriel, vous avez vu comment activer le suivi oculaire pour HoloLens 2 et comment l’ajouter aux objets en vue de déclencher des actions lorsque l’utilisateur regarde ces objets.</span><span class="sxs-lookup"><span data-stu-id="c1b6a-152">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1b6a-153">Tutoriel suivant : 9. Utilisation des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="c1b6a-153">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
