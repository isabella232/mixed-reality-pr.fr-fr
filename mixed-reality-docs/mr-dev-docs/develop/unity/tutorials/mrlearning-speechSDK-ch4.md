---
title: Configuration des intentions et compréhension du langage naturel
description: Suivez ce cours pour découvrir comment configurer l’intention et la compréhension du langage naturel dans les applications de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, reconnaissance vocale, Windows 10, LUIS, portail LUIS, intention, entités, énoncés, compréhension du langage naturel
ms.localizationpriority: high
ms.openlocfilehash: 8d840855321de5d4e055b944783649c9d8028f9a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581469"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="6241a-104">4. Configuration des intentions et compréhension du langage naturel</span><span class="sxs-lookup"><span data-stu-id="6241a-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="6241a-105">Dans ce tutoriel, vous allez découvrir la reconnaissance de l’intention du service Azure Speech.</span><span class="sxs-lookup"><span data-stu-id="6241a-105">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="6241a-106">La reconnaissance de l’intention vous permet d’équiper notre application de commandes vocales optimisées par l’IA (intelligence artificielle). Ainsi, si les utilisateurs énoncent des commandes vocales imprécises, le système peut quand même comprendre leur intention.</span><span class="sxs-lookup"><span data-stu-id="6241a-106">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="6241a-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="6241a-107">Objectives</span></span>

* <span data-ttu-id="6241a-108">Découvrir comment configurer l’intention, les entités et les énoncés dans le portail LUIS</span><span class="sxs-lookup"><span data-stu-id="6241a-108">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="6241a-109">Apprendre à implémenter la compréhension de l’intention et du langage naturel dans notre application</span><span class="sxs-lookup"><span data-stu-id="6241a-109">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="6241a-110">Préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="6241a-110">Preparing the scene</span></span>

<span data-ttu-id="6241a-111">Dans la fenêtre Hierachy, sélectionnez l’objet **Lunarcom** puis, dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Lunarcom Intent Recognizer (Script)** à l’objet Lunarcom :</span><span class="sxs-lookup"><span data-stu-id="6241a-111">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="6241a-113">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, faites glisser le préfabriqué **RocketLauncher_Complete** dans la fenêtre Hierarchy et placez-le à un emplacement approprié devant la caméra, par exemple :</span><span class="sxs-lookup"><span data-stu-id="6241a-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="6241a-114">Transform **Position** X = 0, Y = -0.4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="6241a-114">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="6241a-115">Transform **Rotation** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="6241a-115">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="6241a-117">Dans la fenêtre Hierachy, re-sélectionnez l’objet **Lunarcom**, puis développez l’objet **RocketLauncher_Complete** > **Button** et affectez à chaque objet enfant de l’objet **Buttons** le champ **Lunar Launcher Buttons** correspondant :</span><span class="sxs-lookup"><span data-stu-id="6241a-117">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="6241a-119">Création de la ressource Azure Language Understanding</span><span class="sxs-lookup"><span data-stu-id="6241a-119">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="6241a-120">Dans cette section, vous allez créer une ressource de prédiction Azure pour l’application LUIS (Language Understanding Intelligent Service) que vous allez créer dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="6241a-120">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="6241a-121">Connectez-vous à <a href="https://portal.azure.com" target="_blank">Azure</a>, puis cliquez sur **Créer une ressource**.</span><span class="sxs-lookup"><span data-stu-id="6241a-121">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="6241a-122">Ensuite, recherchez et sélectionnez **Language Understanding** :</span><span class="sxs-lookup"><span data-stu-id="6241a-122">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="6241a-124">Cliquez sur le bouton **Créer** pour créer une instance de ce service :</span><span class="sxs-lookup"><span data-stu-id="6241a-124">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="6241a-126">Dans la page Créer, cliquez sur l’option **Prédiction** et entrez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="6241a-126">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="6241a-127">Pour **Abonnement**, sélectionnez **Essai gratuit** si vous disposez d’un abonnement à l’essai, sinon, sélectionnez l’un de vos autres abonnements.</span><span class="sxs-lookup"><span data-stu-id="6241a-127">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="6241a-128">Pour le **Groupe de ressources**, cliquez sur le lien **Créer nouveau**, entrez un nom approprié, par exemple *MRKT-Tutorials*, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6241a-128">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click on **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="6241a-130">Au moment de la rédaction de cet article, vous n’avez pas besoin de créer une ressource de création, car une clé d’essai de création est automatiquement générée dans LUIS quand vous créez l’application LUIS (Language Understanding Intelligent Service) dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="6241a-130">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="6241a-131">Si vous avez déjà un autre groupe de ressources approprié dans votre compte Azure, par exemple, si vous avez suivi le tutoriel [Azure Spatial Anchors](mr-learning-asa-01.md), vous pouvez utiliser ce groupe de ressources au lieu d’en créer un.</span><span class="sxs-lookup"><span data-stu-id="6241a-131">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mr-learning-asa-01.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="6241a-132">Toujours dans la page Créer, entrez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="6241a-132">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="6241a-133">Pour **Nom**, entrez un nom approprié pour le service, par exemple, *MRTK-Tutorials-AzureSpeechServices*.</span><span class="sxs-lookup"><span data-stu-id="6241a-133">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="6241a-134">Pour **Emplacement de prédiction**, choisissez un emplacement proche de l’emplacement physique des utilisateurs de votre application, par exemple, *USA Ouest*.</span><span class="sxs-lookup"><span data-stu-id="6241a-134">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="6241a-135">Pour **Niveau tarifaire de prédiction**, dans le cadre de ce tutoriel, sélectionnez **F0 (5 appels par seconde, 10 000 appels par mois)**</span><span class="sxs-lookup"><span data-stu-id="6241a-135">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="6241a-137">Cliquez ensuite sur l’onglet **Vérifier + créer**, passez en revue les détails, puis cliquez sur le bouton **Créer** situé dans le bas de la page pour créer la ressource et le nouveau groupe de ressources si vous en avez créé un :</span><span class="sxs-lookup"><span data-stu-id="6241a-137">Next, click on **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="6241a-139">Après avoir cliqué sur le bouton Créer, vous devez attendre que le service soit créé, ce qui peut prendre quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="6241a-139">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="6241a-140">Une fois le processus de création de la ressource terminé, le message **Votre déploiement a été effectué** s’affiche :</span><span class="sxs-lookup"><span data-stu-id="6241a-140">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="6241a-142">Création de l’application LUIS (Language Understanding Intelligent Service)</span><span class="sxs-lookup"><span data-stu-id="6241a-142">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="6241a-143">Dans cette section, vous allez créer une application LUIS, configurer et entraîner son modèle de prédiction, puis la connecter à la ressource de prédiction Azure que vous avez créée à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="6241a-143">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="6241a-144">Plus précisément, vous allez créer une intention qui veut que, si l’utilisateur déclare qu’une action doit être effectuée, l’application déclenche l’événement Interactable.OnClick() sur l’un des trois boutons rouges de la scène, en fonction de celui auquel l’utilisateur fait référence.</span><span class="sxs-lookup"><span data-stu-id="6241a-144">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="6241a-145">Par exemple, si l’utilisateur dit **procéder au lancement de la fusée**, l’application va prédire que **procéder** implique une **action** à effectuer, et que l’événement Interactable.OnClick() à **cibler** se trouve sur le bouton de **lancement**.</span><span class="sxs-lookup"><span data-stu-id="6241a-145">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="6241a-146">Voici les principales étapes à suivre pour y parvenir :</span><span class="sxs-lookup"><span data-stu-id="6241a-146">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6241a-147">Créer une application LUIS</span><span class="sxs-lookup"><span data-stu-id="6241a-147">Create a LUIS app</span></span>
2. <span data-ttu-id="6241a-148">Créer des intentions</span><span class="sxs-lookup"><span data-stu-id="6241a-148">Create intents</span></span>
3. <span data-ttu-id="6241a-149">Créer des exemples d’énoncés</span><span class="sxs-lookup"><span data-stu-id="6241a-149">Create example utterances</span></span>
4. <span data-ttu-id="6241a-150">Créer des entités</span><span class="sxs-lookup"><span data-stu-id="6241a-150">Create entities</span></span>
5. <span data-ttu-id="6241a-151">Attribuer des entités aux exemples d’énoncés</span><span class="sxs-lookup"><span data-stu-id="6241a-151">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="6241a-152">Entraîner, tester et publier l’application</span><span class="sxs-lookup"><span data-stu-id="6241a-152">Train, test, and publish the app</span></span>
7. <span data-ttu-id="6241a-153">Attribuer une ressource de prédiction Azure à l’application</span><span class="sxs-lookup"><span data-stu-id="6241a-153">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="6241a-154">1. Créer une application LUIS</span><span class="sxs-lookup"><span data-stu-id="6241a-154">1. Create a LUIS app</span></span>

<span data-ttu-id="6241a-155">À l’aide du même compte d’utilisateur que celui que vous avez utilisé pour créer la ressource Azure dans la section précédente, connectez-vous à <a href="https://www.luis.ai" target="_blank">LUIS</a>, sélectionnez votre pays et acceptez les conditions d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="6241a-155">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="6241a-156">À l’étape suivante, lorsque vous êtes invité à **lier votre compte Azure**, choisissez **Continuer à utiliser votre clé d’essai**, pour utiliser une ressource de création Azure à la place.</span><span class="sxs-lookup"><span data-stu-id="6241a-156">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="6241a-157">Si vous êtes déjà inscrit à LUIS et que votre clé d’essai de création a expiré, vous pouvez consulter la documentation [Migrer vers une clé de création de ressource Azure](/azure/cognitive-services/luis/luis-migration-authoring) pour basculer votre ressource de création LUIS vers Azure.</span><span class="sxs-lookup"><span data-stu-id="6241a-157">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="6241a-158">Une fois connecté, cliquez sur **Nouvelle application**, puis entrez les valeurs suivantes dans la fenêtre contextuelle **Créer une application** :</span><span class="sxs-lookup"><span data-stu-id="6241a-158">Once signed in, click **New app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="6241a-159">Pour **Nom**, entrez un nom approprié, par exemple, *MRTK Tutorials - AzureSpeechServices*.</span><span class="sxs-lookup"><span data-stu-id="6241a-159">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="6241a-160">Pour **Culture**, sélectionnez **Anglais**.</span><span class="sxs-lookup"><span data-stu-id="6241a-160">For **Culture**, select **English**</span></span>
* <span data-ttu-id="6241a-161">Pour **Description**, entrez éventuellement une description appropriée.</span><span class="sxs-lookup"><span data-stu-id="6241a-161">For **Description**, optionally enter a suitable description</span></span>
* <span data-ttu-id="6241a-162">Pour **Ressource de prédiction**, sélectionnez dans la liste déroulante la ressource de prédiction qui avait été créée avec le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="6241a-162">For **Prediction resource**, select the prediction resource by dropdown list that had been created azure portal.</span></span>

<span data-ttu-id="6241a-163">Cliquez ensuite sur le bouton **Terminé** pour créer l’application :</span><span class="sxs-lookup"><span data-stu-id="6241a-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="6241a-165">Une fois l’application créée, vous êtes dirigé vers sa page **Tableau de bord** :</span><span class="sxs-lookup"><span data-stu-id="6241a-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="6241a-167">2. Créer des intentions</span><span class="sxs-lookup"><span data-stu-id="6241a-167">2. Create intents</span></span>

<span data-ttu-id="6241a-168">À partir de la page Tableau de bord, accédez à la page Générer > Ressources d’application > **Intentions**, puis cliquez sur **Créer** et entrez la valeur suivante dans la fenêtre contextuelle **Créer une intention** :</span><span class="sxs-lookup"><span data-stu-id="6241a-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="6241a-169">Pour **Nom de l’intention**, entrez **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="6241a-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="6241a-170">Cliquez ensuite sur le bouton **Terminé** pour créer l’intention :</span><span class="sxs-lookup"><span data-stu-id="6241a-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="6241a-172">Dans le cadre de ce tutoriel, votre projet Unity va référencer cette intention par son nom, c.-à-d. « PressButton ».</span><span class="sxs-lookup"><span data-stu-id="6241a-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="6241a-173">Il est donc extrêmement important de nommer votre intention de manière strictement identique.</span><span class="sxs-lookup"><span data-stu-id="6241a-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="6241a-174">Une fois l’intention créée, vous êtes dirigé vers sa page :</span><span class="sxs-lookup"><span data-stu-id="6241a-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="6241a-176">3. Créer des exemples d’énoncés</span><span class="sxs-lookup"><span data-stu-id="6241a-176">3. Create example utterances</span></span>

<span data-ttu-id="6241a-177">À la liste des **exemples d’énoncés** de l’intention **PressButton**, ajoutez les exemples d’énoncés suivants :</span><span class="sxs-lookup"><span data-stu-id="6241a-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="6241a-178">activer la séquence de lancement</span><span class="sxs-lookup"><span data-stu-id="6241a-178">activate launch sequence</span></span>
* <span data-ttu-id="6241a-179">me montrer un indicateur de placement</span><span class="sxs-lookup"><span data-stu-id="6241a-179">show me a placement hint</span></span>
* <span data-ttu-id="6241a-180">démarrer la séquence de lancement</span><span class="sxs-lookup"><span data-stu-id="6241a-180">initiate the launch sequence</span></span>
* <span data-ttu-id="6241a-181">appuyer sur le bouton des indicateurs de placement</span><span class="sxs-lookup"><span data-stu-id="6241a-181">press placement hints button</span></span>
* <span data-ttu-id="6241a-182">me donner un indicateur</span><span class="sxs-lookup"><span data-stu-id="6241a-182">give me a hint</span></span>
* <span data-ttu-id="6241a-183">appuyer sur le bouton de lancement</span><span class="sxs-lookup"><span data-stu-id="6241a-183">push the launch button</span></span>
* <span data-ttu-id="6241a-184">j’ai besoin d’un indicateur</span><span class="sxs-lookup"><span data-stu-id="6241a-184">i need a hint</span></span>
* <span data-ttu-id="6241a-185">appuyer sur le bouton de réinitialisation</span><span class="sxs-lookup"><span data-stu-id="6241a-185">press the reset button</span></span>
* <span data-ttu-id="6241a-186">délai de réinitialisation de l’expérience</span><span class="sxs-lookup"><span data-stu-id="6241a-186">time to reset the experience</span></span>
* <span data-ttu-id="6241a-187">procéder au lancement de la fusée</span><span class="sxs-lookup"><span data-stu-id="6241a-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="6241a-188">Une fois que tous les exemples d’énoncés ont été ajoutés, la page de l’intention PressButton doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="6241a-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="6241a-190">Dans le cadre de ce tutoriel, votre projet Unity va référencer les mots « indicateur », « indicateurs » « réinitialisation » et « lancement ».</span><span class="sxs-lookup"><span data-stu-id="6241a-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="6241a-191">Il est donc extrêmement important de prononcer ces mots exactement de la même façon.</span><span class="sxs-lookup"><span data-stu-id="6241a-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="6241a-192">4. Créer des entités</span><span class="sxs-lookup"><span data-stu-id="6241a-192">4. Create entities</span></span>

<span data-ttu-id="6241a-193">À partir de la page de l’intention PressButton, accédez à la page Générer > Ressources d’application > **Entités**, puis cliquez sur **Créer** et entrez les valeurs suivantes dans la fenêtre contextuelle **Créer une entité** :</span><span class="sxs-lookup"><span data-stu-id="6241a-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="6241a-194">Pour **Nom de l’entité**, entrez **Action**.</span><span class="sxs-lookup"><span data-stu-id="6241a-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="6241a-195">Pour **Type d’entité**, sélectionnez **Appris par machine learning**.</span><span class="sxs-lookup"><span data-stu-id="6241a-195">For **Entity type**, select **Machine learned**</span></span>

<span data-ttu-id="6241a-196">Cliquez ensuite sur le bouton **Créer** pour créer l’entité :</span><span class="sxs-lookup"><span data-stu-id="6241a-196">Then click the **Create** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="6241a-198">**Répétez** l’étape précédente pour créer une autre entité nommée **Cible**. Vous avez donc deux entités nommées Action et Cible :</span><span class="sxs-lookup"><span data-stu-id="6241a-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="6241a-200">Dans le cadre de ce tutoriel, votre projet Unity va référencer ces entités par leurs noms, c.-à-d. « Action » et « Cible ».</span><span class="sxs-lookup"><span data-stu-id="6241a-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="6241a-201">Il est donc extrêmement important de nommer vos entités de manière strictement identique.</span><span class="sxs-lookup"><span data-stu-id="6241a-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="6241a-202">5. Attribuer des entités aux exemples d’énoncés</span><span class="sxs-lookup"><span data-stu-id="6241a-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="6241a-203">À partir de la page Entités, revenez à la page de l’intention **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="6241a-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="6241a-204">Dans cette page, cliquez sur le mot **procéder** et sur le mot **au**, puis sélectionnez **Action (Simple)** dans le menu contextuel pour étiqueter **procéder au** comme valeur d’entité **Action** :</span><span class="sxs-lookup"><span data-stu-id="6241a-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="6241a-206">La locution **procéder au** est maintenant définie en tant que valeur d’entité **Action**.</span><span class="sxs-lookup"><span data-stu-id="6241a-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="6241a-207">Vous pouvez maintenant noter la valeur de l’entité Action sous le mot « go ahead » :</span><span class="sxs-lookup"><span data-stu-id="6241a-207">Now you can notice the action entity value under the word go ahead:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="6241a-209">La ligne rouge qui apparaît sous l’étiquette dans l’image ci-dessus indique que la valeur d’entité n’a pas été prédite, ce que vous allez résoudre quand vous entraînerez le modèle dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="6241a-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="6241a-210">Ensuite, cliquez sur le mot **lancement**, puis sélectionnez **Cible (Simple)** dans le menu contextuel pour étiqueter **lancement** comme valeur d’entité **Cible** :</span><span class="sxs-lookup"><span data-stu-id="6241a-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="6241a-212">Le mot **launch** est maintenant défini en tant valeur d’entité **Cible**. Vous pouvez maintenant noter la valeur de l’entité cible sous le mot « launch » :</span><span class="sxs-lookup"><span data-stu-id="6241a-212">The **launch** word is now defined as a **Target** entity value.Now you can notice the Target entity value under the word launch :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="6241a-214">L’exemple d’énoncé de l’intention PressButton « procéder au lancement de la fusée » est maintenant configuré pour être prédit ainsi :</span><span class="sxs-lookup"><span data-stu-id="6241a-214">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="6241a-215">Intention : PressButton</span><span class="sxs-lookup"><span data-stu-id="6241a-215">Intent: PressButton</span></span>
* <span data-ttu-id="6241a-216">Entité Action : procéder au</span><span class="sxs-lookup"><span data-stu-id="6241a-216">Action entity: go ahead</span></span>
* <span data-ttu-id="6241a-217">Entité Cible : lancement</span><span class="sxs-lookup"><span data-stu-id="6241a-217">Target entity: launch</span></span>

<span data-ttu-id="6241a-218">**Répétez** le processus en deux étapes précédent pour attribuer une étiquette d’entité Action et Cible à chacun des exemples d’énoncés, en gardant à l’esprit que les mots suivants doivent être étiquetés comme des entités **Cible** :</span><span class="sxs-lookup"><span data-stu-id="6241a-218">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="6241a-219">**indicateur** (Cible HintsButton dans le projet Unity.)</span><span class="sxs-lookup"><span data-stu-id="6241a-219">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="6241a-220">**indicateurs** (Cible HintsButton dans le projet Unity.)</span><span class="sxs-lookup"><span data-stu-id="6241a-220">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="6241a-221">**réinitialisation** (Cible ResetButton dans le projet Unity.)</span><span class="sxs-lookup"><span data-stu-id="6241a-221">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="6241a-222">**lancement** (Cible LaunchButton dans le projet Unity.)</span><span class="sxs-lookup"><span data-stu-id="6241a-222">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="6241a-223">Une fois que tous les exemples d’énoncés ont été étiquetés, la page de l’intention PressButton doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="6241a-223">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="6241a-225">6. Entraîner, tester et publier l’application</span><span class="sxs-lookup"><span data-stu-id="6241a-225">6. Train, test, and publish the app</span></span>

<span data-ttu-id="6241a-226">Pour entraîner l’application, cliquez sur le bouton **Entraîner** et attendez que le processus d’entraînement se termine :</span><span class="sxs-lookup"><span data-stu-id="6241a-226">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="6241a-228">Comme vous pouvez le voir dans l’image ci-dessus, les lignes rouges situées sous toutes les étiquettes ont été supprimées, ce qui indique que toutes les valeurs d’entité ont été prédites.</span><span class="sxs-lookup"><span data-stu-id="6241a-228">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="6241a-229">Remarquez également que l’icône d’état à gauche du bouton Entraîner est passée du rouge au vert.</span><span class="sxs-lookup"><span data-stu-id="6241a-229">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="6241a-230">Une fois le processus d’entraînement terminé, cliquez sur le bouton **Tester**, puis tapez **procéder au lancement de la fusée** et appuyez sur la touche Entrée :</span><span class="sxs-lookup"><span data-stu-id="6241a-230">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="6241a-232">Une fois l’énoncé de test traité, cliquez sur **Inspecter** pour voir le résultat du test :</span><span class="sxs-lookup"><span data-stu-id="6241a-232">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="6241a-233">Intention : PressButton (avec une certitude de 98,5 %)</span><span class="sxs-lookup"><span data-stu-id="6241a-233">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="6241a-234">Entité Action : procéder au</span><span class="sxs-lookup"><span data-stu-id="6241a-234">Action entity: go ahead</span></span>
* <span data-ttu-id="6241a-235">Entité Cible : lancement</span><span class="sxs-lookup"><span data-stu-id="6241a-235">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="6241a-237">Pour publier l’application, cliquez sur le bouton **Publier** en haut à droite puis, dans la fenêtre contextuelle **Choisir l’emplacement et les paramètres de publication**, sélectionnez **Production** et cliquez sur le bouton **Terminé** :</span><span class="sxs-lookup"><span data-stu-id="6241a-237">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Done** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="6241a-239">Attendez que le processus de publication se termine :</span><span class="sxs-lookup"><span data-stu-id="6241a-239">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

<span data-ttu-id="6241a-241">Accédez à la page Gérer > Paramètres d’application > **Ressources Azure**. Votre page Ressources Azure doit être similaire à ceci :</span><span class="sxs-lookup"><span data-stu-id="6241a-241">Navigate to the Manage > Application Settings > **Azure Resources** page, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-6.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="6241a-243">Connexion du projet Unity à l’application LUIS</span><span class="sxs-lookup"><span data-stu-id="6241a-243">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="6241a-244">Dans la page Gérer > Paramètres d’application > **Ressources Azure**, cliquez sur l’icône **Copier** pour copier l’**exemple de requête** :</span><span class="sxs-lookup"><span data-stu-id="6241a-244">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="6241a-246">De retour dans votre projet Unity, dans la fenêtre Hierarchy, sélectionnez l’objet **Lunarcom**, puis dans la fenêtre Inspector, localisez le composant **Lunarcom Intent Recognizer (Script)** et configurez-le de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="6241a-246">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="6241a-247">Dans le champ **LUIS Endpoint**, collez l’**exemple de requête** que vous avez copié à l’étape précédente :</span><span class="sxs-lookup"><span data-stu-id="6241a-247">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="6241a-249">Test et amélioration de la reconnaissance de l’intention</span><span class="sxs-lookup"><span data-stu-id="6241a-249">Testing and improving the intent recognition</span></span>

<span data-ttu-id="6241a-250">Pour utiliser la reconnaissance de l’intention directement dans l’éditeur Unity, vous devez autoriser votre ordinateur de développement à utiliser la dictée.</span><span class="sxs-lookup"><span data-stu-id="6241a-250">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="6241a-251">Pour vérifier ce paramètre, ouvrez **Paramètres Windows**, puis choisissez **Confidentialité** > **Voix** et vérifiez que l’option **Reconnaissance vocale en ligne** est activée :</span><span class="sxs-lookup"><span data-stu-id="6241a-251">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="6241a-253">Si vous entrez maintenant en mode Game, vous pouvez tester la reconnaissance de l’intention en commençant par appuyer sur le bouton de la fusée.</span><span class="sxs-lookup"><span data-stu-id="6241a-253">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="6241a-254">Ensuite, en supposant que votre ordinateur est doté d’un microphone, quand vous prononcez le premier exemple d’énoncé, **procéder au lancement de la fusée**, vous pouvez voir le lancement du module lunaire dans l’espace :</span><span class="sxs-lookup"><span data-stu-id="6241a-254">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="6241a-256">Testez tous les **exemples d’énoncés**, puis quelques **variations des exemples d’énoncés**, ainsi que quelques **énoncés aléatoires**.</span><span class="sxs-lookup"><span data-stu-id="6241a-256">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="6241a-257">Ensuite, revenez à <a href="https://www.luis.ai" target="_blank">LUIS</a> et accédez à la page Générer > Améliorer les performances de l’application > **Vérifier les énoncés de point de terminaison**, utilisez le bouton **bascule** pour passer de l’affichage des entités par défaut à celui des **jetons**, puis vérifiez les énoncés :</span><span class="sxs-lookup"><span data-stu-id="6241a-257">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="6241a-258">Dans la colonne **Énoncé**, modifiez et supprimez les étiquettes attribuées en fonction des besoins pour les adapter à votre intention.</span><span class="sxs-lookup"><span data-stu-id="6241a-258">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="6241a-259">Dans la colonne **Intention alignée**, vérifiez que l’intention est correcte.</span><span class="sxs-lookup"><span data-stu-id="6241a-259">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="6241a-260">Dans la colonne **Ajouter/Supprimer**, cliquez sur la coche verte pour ajouter l’énoncé ou sur le x rouge pour le supprimer.</span><span class="sxs-lookup"><span data-stu-id="6241a-260">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="6241a-261">Quand vous avez vérifié autant d’énoncés que vous le voulez, cliquez sur le bouton **Entraîner** pour entraîner de nouveau le modèle, puis sur le bouton **Publier** pour republier l’application mise à jour :</span><span class="sxs-lookup"><span data-stu-id="6241a-261">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="6241a-263">Si un énoncé de point de terminaison ne correspond pas à l’intention PressButton, mais que vous voulez que votre modèle sache que cet énoncé n’a aucune intention, vous pouvez définir l’option Intention alignée sur Aucune.</span><span class="sxs-lookup"><span data-stu-id="6241a-263">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="6241a-264">**Répétez** ce processus autant de fois que vous le souhaitez pour améliorer votre modèle d’application.</span><span class="sxs-lookup"><span data-stu-id="6241a-264">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6241a-265">Félicitations</span><span class="sxs-lookup"><span data-stu-id="6241a-265">Congratulations</span></span>

<span data-ttu-id="6241a-266">Votre projet comporte désormais des commandes vocales optimisées par l’IA, ce qui permet à votre application de reconnaître l’intention des utilisateurs même s’ils ne prononcent pas des commandes précises.</span><span class="sxs-lookup"><span data-stu-id="6241a-266">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="6241a-267">Exécutez l’application sur votre appareil pour vérifier que tout fonctionne bien.</span><span class="sxs-lookup"><span data-stu-id="6241a-267">Run the application on your device to ensure the feature is working properly.</span></span>