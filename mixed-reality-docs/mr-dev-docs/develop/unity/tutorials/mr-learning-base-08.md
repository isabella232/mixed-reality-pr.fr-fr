---
title: Utilisation du suivi oculaire
description: Ce cours vous montre comment utiliser le suivi oculaire dans votre application de réalité mixte avec Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, suivi oculaire
ms.localizationpriority: high
ms.openlocfilehash: 08793622917ca977c51be56267d8710e5abb78e8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237169"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="7b086-104">8. Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="7b086-104">8. Using eye-tracking</span></span>

<span data-ttu-id="7b086-105">Dans ce tutoriel, vous allez voir comment activer le suivi oculaire (eye-tracking) pour HoloLens 2 et comment l’ajouter aux objets en vue de déclencher des actions lorsque l’utilisateur regarde ces objets.</span><span class="sxs-lookup"><span data-stu-id="7b086-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="7b086-106">Si vous déployez également ce projet sur HoloLens (1re génération), notez que le suivi oculaire est pris en charge uniquement sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7b086-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="7b086-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="7b086-107">Objectives</span></span>

* <span data-ttu-id="7b086-108">Apprendre à activer le suivi oculaire pour HoleLens 2</span><span class="sxs-lookup"><span data-stu-id="7b086-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="7b086-109">Apprendre à utiliser le suivi oculaire pour déclencher une action</span><span class="sxs-lookup"><span data-stu-id="7b086-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="7b086-110">Vérifier que la fonctionnalité d’entrée avec le pointage du regard est activée</span><span class="sxs-lookup"><span data-stu-id="7b086-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="7b086-111">Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Eye Gaze Input Capability** est grisée :</span><span class="sxs-lookup"><span data-stu-id="7b086-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Fenêtre MRTK Project Configurator d’Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="7b086-113">La fonctionnalité Gaze Input doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](mr-learning-base-02.md#creating-and-configuring-the-scene) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="7b086-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="7b086-114">Toutefois, si elle n’est pas activée, activez-la maintenant.</span><span class="sxs-lookup"><span data-stu-id="7b086-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="7b086-115">Activation du pointage du regard dans le fournisseur de regard</span><span class="sxs-lookup"><span data-stu-id="7b086-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="7b086-116">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet MixedRealityToolkit > **Input**, puis effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b086-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="7b086-117">Clonez **DefaultHoloLens2InputSystemProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_HoloLens2InputSystemProfile_.</span><span class="sxs-lookup"><span data-stu-id="7b086-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="7b086-118">Développez la section **Pointers**.</span><span class="sxs-lookup"><span data-stu-id="7b086-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="7b086-119">Clonez **DefaultMixedRealityPointerProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_MixedRealityPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="7b086-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="7b086-120">Recherchez la section **Gaze Settings** (Paramètres du regard), puis cochez la case **Is Eye Tracking Enabled** (Activation du suivi oculaire).</span><span class="sxs-lookup"><span data-stu-id="7b086-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Composant MixedRealityToolkit d’Unity avec les profils nouvellement créés appliqués et le suivi du regard activé](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="7b086-122">Pour obtenir un rappel de la façon de cloner des profils MRTK, vous pouvez consulter les instructions fournies dans [Configuration des profils MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="7b086-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="7b086-123">Activation du suivi oculaire simulé pour l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="7b086-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="7b086-124">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, accédez à l’onglet **Input**, puis :</span><span class="sxs-lookup"><span data-stu-id="7b086-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="7b086-125">Développez la section **Input Data Providers** > **Input Simulation Service**.</span><span class="sxs-lookup"><span data-stu-id="7b086-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="7b086-126">Clonez **DefaultMixedRealityInputSimulationProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_MixedRealityInputSimulationProfile_.</span><span class="sxs-lookup"><span data-stu-id="7b086-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="7b086-127">Recherchez **Eye Gaze Simulation** et définissez **Default Eye Gaze Simulation Mode** sur **Camera Forward Axis**</span><span class="sxs-lookup"><span data-stu-id="7b086-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity avec l’objet TextMeshPro sélectionné](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="7b086-129">Ajout du suivi oculaire aux objets</span><span class="sxs-lookup"><span data-stu-id="7b086-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="7b086-130">Dans la fenêtre Hiérarchie, développez les **boutons** > **RoverExplorerButtons**, puis sélectionnez les trois objets bouton enfants :</span><span class="sxs-lookup"><span data-stu-id="7b086-130">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity avec l’objet Bouton sélectionné](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="7b086-132">Avec les trois objets Bouton toujours sélectionnés, dans la fenêtre Inspecteur, utilisez le bouton **Ajouter composant** pour ajouter le composant **EyeTrackingTarget** à tous les objets sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="7b086-132">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity avec l’objet TextMeshPro sélectionné et des composants ajoutés](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="7b086-134">Dans la fenêtre Hiérarchie, développez **RoverExplorer** > **Boutons** > **Indicateurs** > **SeeItSayItLabel** > **TextMeshPro**</span><span class="sxs-lookup"><span data-stu-id="7b086-134">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="7b086-135">Ensuite, dans la fenêtre Hiérarchie, sélectionnez l’objet bouton **Indicateurs**, puis configurez le composant **EyeTrackingTarget** comme suit :</span><span class="sxs-lookup"><span data-stu-id="7b086-135">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="7b086-136">Dans la section d’événement **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="7b086-136">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="7b086-137">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="7b086-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="7b086-138">Assignez l’objet **TextMeshPro** à partir du bouton **Indicateurs** au champ **Aucun (objet)**</span><span class="sxs-lookup"><span data-stu-id="7b086-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="7b086-139">Dans la liste déroulante **No Function**, sélectionnez **TextMeshPro** > **float fontSize** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="7b086-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="7b086-140">Définissez l’argument sur **0.06** pour augmenter la taille de police actuelle (0.04) de 50 %.</span><span class="sxs-lookup"><span data-stu-id="7b086-140">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="7b086-141">Dans la section d’événement **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="7b086-141">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="7b086-142">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="7b086-142">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="7b086-143">Assignez l’objet **TextMeshPro** à partir du bouton **Indicateurs** au champ **Aucun (objet)**</span><span class="sxs-lookup"><span data-stu-id="7b086-143">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="7b086-144">Dans la liste déroulante **No Function**, sélectionnez **TextMeshPro** > **float fontSize** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="7b086-144">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="7b086-145">Définissez l’argument sur **0.04** pour rétablir la taille de la police à 0.04.</span><span class="sxs-lookup"><span data-stu-id="7b086-145">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity avec l’objet Hints TextMeshPro sélectionné et le composant EyeTrackingTarget configuré](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="7b086-147">**Répétez** cette étape pour l’objet bouton **Éclater** et **Réinitialiser** pour configurer le suivi oculaire des boutons restants.</span><span class="sxs-lookup"><span data-stu-id="7b086-147">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="7b086-148">Si vous passez maintenant en mode jeu, puis maintenez enfoncé le bouton de droite tout en déplaçant la souris jusqu’à ce que le regard atteigne l’un des boutons, vous verrez que la taille de police du texte augmente de 50 % et revient à sa taille d’origine lorsque l’utilisateur regarde ailleurs :</span><span class="sxs-lookup"><span data-stu-id="7b086-148">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Vue partagée du mode Play d’Unity avec le suivi atteignant Eye Tracking Target - Étiquette du bouton Explode](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="7b086-150">Félicitations</span><span class="sxs-lookup"><span data-stu-id="7b086-150">Congratulations</span></span>

<span data-ttu-id="7b086-151">Dans ce tutoriel, vous avez vu comment activer le suivi oculaire pour HoloLens 2 et comment l’ajouter aux objets en vue de déclencher des actions lorsque l’utilisateur regarde ces objets.</span><span class="sxs-lookup"><span data-stu-id="7b086-151">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7b086-152">Tutoriel suivant : 9. Utilisation des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="7b086-152">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
