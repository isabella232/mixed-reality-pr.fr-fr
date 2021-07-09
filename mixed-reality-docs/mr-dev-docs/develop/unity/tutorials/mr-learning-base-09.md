---
title: Utilisation des commandes vocales
description: Ce cours vous montre comment configurer, créer et utiliser des commandes vocales dans vos applications de réalité mixte avec le Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, commandes vocales, entrée vocale
ms.localizationpriority: high
ms.openlocfilehash: 9422c16781af33fa3d68d7f6046e3a86c4b36b44
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403370"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="20460-104">9. Utilisation des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="20460-104">9. Using speech commands</span></span>

<span data-ttu-id="20460-105">Dans ce tutoriel, vous allez apprendre à créer des commandes vocales et à les contrôler globalement.</span><span class="sxs-lookup"><span data-stu-id="20460-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="20460-106">Vous allez également apprendre à contrôler les commandes vocales locales qui demandent à l’utilisateur de regarder l’objet qui contrôle la commande vocale.</span><span class="sxs-lookup"><span data-stu-id="20460-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="20460-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="20460-107">Objectives</span></span>

* <span data-ttu-id="20460-108">Apprendre à créer des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="20460-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="20460-109">Apprendre à contrôler les commandes vocales globalement et localement</span><span class="sxs-lookup"><span data-stu-id="20460-109">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="20460-110">Vérification de l’activation de la fonctionnalité Microphone</span><span class="sxs-lookup"><span data-stu-id="20460-110">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="20460-111">Dans le menu Unity, sélectionnez Mixed Reality > Kit de ressources > Utilitaires > **Configurer le projet pour MRTK** afin d’ouvrir la fenêtre **MRTK Project Configurator**. Ensuite, dans la section **Fonctionnalités UWP**, vérifiez que l’option **Activer la fonctionnalité du microphone** est grisée :</span><span class="sxs-lookup"><span data-stu-id="20460-111">In the Unity menu, select Mixed Reality > Toolkit > Utilities > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Activer la fonctionnalité du microphone](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="20460-113">La fonctionnalité Microphone doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="20460-113">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="20460-114">Toutefois, si elle n’est pas activée, veillez à l’activer maintenant.</span><span class="sxs-lookup"><span data-stu-id="20460-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="20460-115">Création de commandes vocales</span><span class="sxs-lookup"><span data-stu-id="20460-115">Creating speech commands</span></span>

<span data-ttu-id="20460-116">Dans la fenêtre de hiérarchie, sélectionnez l’objet **MixedRealityToolkit** puis, dans la fenêtre de l’inspecteur, sélectionnez l’onglet MixedRealityToolkit > **Input** et effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="20460-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="20460-117">Développez la section **Speech**.</span><span class="sxs-lookup"><span data-stu-id="20460-117">Expand the **Speech** section</span></span>
* <span data-ttu-id="20460-118">Clonez le **DefaultMixedRealitySpeechCommandsProfile** et donnez-lui un nom approprié, par exemple _GettingStarted_MixedRealitySpeechCommandsProfile_.</span><span class="sxs-lookup"><span data-stu-id="20460-118">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="20460-119">Vérifiez que **Start Behaviour** (Comportement de démarrage) est défini sur **Auto Start** (Démarrage automatique).</span><span class="sxs-lookup"><span data-stu-id="20460-119">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Création de commandes vocales](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="20460-121">Pour vous rappeler comment cloner des profils MRTK, vous pouvez consulter les instructions fournies dans [Configuration des profils MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="20460-121">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="20460-122">Dans la section Speech > **Speech Commands**, cliquez à quatre reprises sur le bouton **+ Add a New Speech Command** (Ajouter une commande vocale) pour ajouter quatre nouvelles commandes vocales à la liste des commandes vocales existantes puis, dans le champ **Keyword** (Mot clé), entrez les expressions suivantes :</span><span class="sxs-lookup"><span data-stu-id="20460-122">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="20460-123">Activer l’indicateur</span><span class="sxs-lookup"><span data-stu-id="20460-123">Enable Indicator</span></span>
* <span data-ttu-id="20460-124">Activer l’appui pour placement</span><span class="sxs-lookup"><span data-stu-id="20460-124">Enable Tap to Place</span></span>
* <span data-ttu-id="20460-125">Activer le contrôle des limites</span><span class="sxs-lookup"><span data-stu-id="20460-125">Enable Bounds Control</span></span>
* <span data-ttu-id="20460-126">Désactiver le contrôle des limites</span><span class="sxs-lookup"><span data-stu-id="20460-126">Disable Bounds Control</span></span>

![Ajout de nouvelles commandes vocales](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="20460-128">Si votre ordinateur ne dispose pas d’un microphone, vous pouvez affecter un code-clé aux commandes vocales, ce qui vous permettra de les déclencher lorsque vous appuierez sur la touche correspondante.</span><span class="sxs-lookup"><span data-stu-id="20460-128">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="20460-129">Contrôle des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="20460-129">Controlling speech commands</span></span>

<span data-ttu-id="20460-130">Dans la fenêtre Project, accédez au dossier **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** pour trouver les préfabriqués d’info-bulle :</span><span class="sxs-lookup"><span data-stu-id="20460-130">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Ouverture du dossier d’info-bulles](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="20460-132">Dans la fenêtre de hiérarchie, cliquez avec le bouton droit sur une zone vide et sélectionnez **Create Empty** pour ajouter un objet vide à votre scène.</span><span class="sxs-lookup"><span data-stu-id="20460-132">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="20460-133">Nommez l’objet **SpeechInputHandler_Global** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** pour ajouter le composant **SpeechInputHandler** et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="20460-133">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="20460-134">**Décochez** la case **Is Focus Required** afin que l’utilisateur ne soit pas obligé de regarder l’objet avec le composant SpeechInputHandler pour déclencher la commande vocale.</span><span class="sxs-lookup"><span data-stu-id="20460-134">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="20460-135">À partir de la fenêtre Project, affectez le préfabriqué **SpeechConfirmation Tooltip** au champ **Speech Confirmation Tooltip Prefab** (Préfabriqué d’info-bulle de confirmation vocale) afin que ce préfabriqué s’affiche quand une commande vocale est reconnue.</span><span class="sxs-lookup"><span data-stu-id="20460-135">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Configuration du composant gestionnaire d’entrée vocale](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="20460-137">Sur le composant SpeechInputHandler, cliquez trois fois sur la petite icône **+** pour ajouter trois éléments de mot clé :</span><span class="sxs-lookup"><span data-stu-id="20460-137">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Ajout d’éléments de mot clé au gestionnaire d’entrée vocal](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="20460-139">Développez **Element 0** et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="20460-139">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="20460-140">Dans le champ **Keyword**, entrez **Activer l’indicateur** afin de référencer la commande vocale Activer l’indicateur que vous avez créée dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="20460-140">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="20460-141">Cliquez sur la petite icône **+** pour ajouter un événement.</span><span class="sxs-lookup"><span data-stu-id="20460-141">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="20460-142">Dans la fenêtre de hiérarchie, affectez l’objet **Indicator** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="20460-142">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="20460-143">Dans la liste déroulante **No Function**, sélectionnez **GameObject** > **SetActive (bool)** pour définir cette fonction en tant qu’action à exécuter lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="20460-143">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="20460-144">**Cochez** la case de l’argument.</span><span class="sxs-lookup"><span data-stu-id="20460-144">Check the argument checkbox, so it is **checked**</span></span>

![Configurer l’élément de mot clé 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="20460-146">Développez **Element 1** et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="20460-146">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="20460-147">Dans le champ **Mot clé**, entrez **Activer le cadre des limites** afin de référencer la commande Activer le contrôle des limites que vous avez créée dans la section précédente</span><span class="sxs-lookup"><span data-stu-id="20460-147">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="20460-148">Cliquez sur la petite icône **+** pour ajouter un événement.</span><span class="sxs-lookup"><span data-stu-id="20460-148">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="20460-149">Dans la fenêtre de hiérarchie, affectez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="20460-149">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="20460-150">Dans la liste déroulante **Aucune fonction**, sélectionnez **BoundsControl** > **bool activé** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché</span><span class="sxs-lookup"><span data-stu-id="20460-150">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="20460-151">**Cochez** la case de l’argument.</span><span class="sxs-lookup"><span data-stu-id="20460-151">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="20460-152">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="20460-152">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="20460-153">Dans la fenêtre de hiérarchie, affectez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="20460-153">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="20460-154">Dans la liste déroulante **No Function**, sélectionnez **ObjectManipulator** > **bool enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="20460-154">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="20460-155">**Cochez** la case de l’argument.</span><span class="sxs-lookup"><span data-stu-id="20460-155">Check the argument checkbox, so it is **checked**</span></span>

![Configurer l’élément de mot clé 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="20460-157">Développez **Element 2** et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="20460-157">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="20460-158">Dans le champ **Mot clé**, entrez **Désactiver le contrôle des limites** afin de référencer la commande Activer le contrôle des limites que vous avez créée dans la section précédente</span><span class="sxs-lookup"><span data-stu-id="20460-158">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="20460-159">Cliquez sur la petite icône **+** pour ajouter un événement.</span><span class="sxs-lookup"><span data-stu-id="20460-159">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="20460-160">Dans la fenêtre de hiérarchie, affectez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="20460-160">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="20460-161">Dans la liste déroulante **Aucune fonction**, sélectionnez **BoundsControl** > **bool activé** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché</span><span class="sxs-lookup"><span data-stu-id="20460-161">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="20460-162">Vérifiez que la case de l’argument est **décochée**.</span><span class="sxs-lookup"><span data-stu-id="20460-162">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="20460-163">Cliquez sur la petite icône **+** pour ajouter un autre événement.</span><span class="sxs-lookup"><span data-stu-id="20460-163">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="20460-164">Dans la fenêtre de hiérarchie, affectez l’objet **RoverExplorer** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="20460-164">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="20460-165">Dans la liste déroulante **No Function**, sélectionnez **ObjectManipulator** > **bool enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="20460-165">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="20460-166">Vérifiez que la case de l’argument est **décochée**.</span><span class="sxs-lookup"><span data-stu-id="20460-166">Verify that the argument checkbox is **unchecked**</span></span>

![Configurer l’élément de mot clé 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="20460-168">Dans la fenêtre de hiérarchie, sélectionnez l’objet RoverExplorer > **RoverAssembly** puis, dans la fenêtre de l’inspecteur, utilisez le bouton **Add Component** pour ajouter le composant **SpeechInputHandler** et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="20460-168">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="20460-169">Vérifiez que la case **Is Focus Required** est **cochée** afin que l’utilisateur ne soit pas obligé de regarder l’objet avec le composant SpeechInputHandler (autrement dit, RoverAssembly) pour déclencher la commande vocale.</span><span class="sxs-lookup"><span data-stu-id="20460-169">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="20460-170">À partir de la fenêtre Project, affectez le préfabriqué **SpeechConfirmation Tooltip** au champ **Speech Confirmation Tooltip Prefab** (Préfabriqué d’info-bulle de confirmation vocale) afin que ce préfabriqué s’affiche quand une commande vocale est reconnue.</span><span class="sxs-lookup"><span data-stu-id="20460-170">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Ajouter un gestionnaire d’entrée vocale à l’assemblage de Rover](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="20460-172">Sur le composant SpeechInputHandler, cliquez sur la petite icône **+** pour ajouter un élément Keyword, développez l’élément qui vient d’être créé, puis configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="20460-172">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="20460-173">Dans le champ **Keyword**, entrez **Activer l’appui pour placement** afin de référencer la commande vocale Activer l’appui pour placement que vous avez créée dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="20460-173">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="20460-174">Cliquez sur la petite icône **+** pour ajouter un événement.</span><span class="sxs-lookup"><span data-stu-id="20460-174">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="20460-175">Dans la fenêtre de hiérarchie, assignez l’objet lui-même, c’est-à-dire le même objet **RoverAssembly**, au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="20460-175">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="20460-176">Dans la liste déroulante **No Function**, sélectionnez **TapToPlace** > **bool enabled** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="20460-176">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="20460-177">**Cochez** la case de l’argument.</span><span class="sxs-lookup"><span data-stu-id="20460-177">Check the argument checkbox, so it is **checked**</span></span>

![Configurer le gestionnaire d’entrée vocale sur l’assemblage de Rover](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="20460-179">Félicitations</span><span class="sxs-lookup"><span data-stu-id="20460-179">Congratulations</span></span>

<span data-ttu-id="20460-180">Dans ce tutoriel, vous avez appris à créer des commandes vocales et à les contrôler globalement.</span><span class="sxs-lookup"><span data-stu-id="20460-180">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="20460-181">Vous avez également appris à contrôler les commandes vocales locales qui demandent à l’utilisateur de regarder l’objet qui contrôle la commande vocale.</span><span class="sxs-lookup"><span data-stu-id="20460-181">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="20460-182">Cela conclut également la série de [Tutoriels de démarrage](mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="20460-182">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="20460-183">En suivant ces tutoriels, vous avez réussi à créer une expérience de réalité mixte complète à l’aide de MRTK.</span><span class="sxs-lookup"><span data-stu-id="20460-183">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="20460-184">Dans les deux prochaines séries de tutoriels, [Tutoriels Azure Spatial Anchors](mr-learning-asa-01.md) et [Tutoriels sur les fonctionnalités multiutilisateurs](mr-learning-sharing-01.md), vous allez d’abord apprendre à intégrer Azure Spatial Anchors dans votre projet afin d’ancrer l’expérience Rover Explorer que vous avez créée dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="20460-184">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="20460-185">Ensuite, vous apprendrez à ajouter des fonctionnalités multiutilisateurs à votre projet afin de partager des mouvements d’utilisateur et d’objet en temps réel.</span><span class="sxs-lookup"><span data-stu-id="20460-185">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="20460-186">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="20460-186">Next Development Checkpoint</span></span>

<span data-ttu-id="20460-187">Si vous suivez le parcours de points de contrôle de développement Unity que nous avons élaboré, la tâche suivante consiste à vous familiariser avec les composants de base des applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="20460-187">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20460-188">Interactions de base</span><span class="sxs-lookup"><span data-stu-id="20460-188">Basic interactions</span></span>](/windows/mixed-reality/mrtk-unity/)

<span data-ttu-id="20460-189">Vous pouvez revenir aux [points de contrôle de développement Unity](../unity-development-overview.md#1-getting-started) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="20460-189">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>
