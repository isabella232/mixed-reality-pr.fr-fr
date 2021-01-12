---
title: Intégration d’Azure Bot Service avec LUIS
description: Suivez ce cours pour découvrir comment implémenter Azure Bot Service et la compréhension du langage naturel dans une application HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, hololens 2, azure bot service, luis, langage naturel, chatbot, services cloud azure, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 70d136467bc677c028614429e6e197ce25b30327
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008249"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="ab8b0-104">5. Intégration d’Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="ab8b0-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="ab8b0-105">Dans ce tutoriel, vous allez apprendre à utiliser **Azure Bot Service** dans l’application de démonstration **HoloLens 2** pour ajouter LUIS (Language Understanding) et laisser le bot assister l’utilisateur lors de la recherche d’**objets suivis**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="ab8b0-106">Il s’agit d’un tutoriel en deux parties. Dans la première, vous allez créer le bot avec la solution sans code [Bot Composer](https://docs.microsoft.com/composer/introduction), et examiner la fonction Azure qui alimente le bot avec les données nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="ab8b0-107">Dans la deuxième partie, vous utiliserez le **BotManager (script)** dans le projet Unity pour consommer le service bot hébergé.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="ab8b0-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ab8b0-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="ab8b0-109">Partie 1</span><span class="sxs-lookup"><span data-stu-id="ab8b0-109">Part 1</span></span>

* <span data-ttu-id="ab8b0-110">Apprendre les bases d’Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="ab8b0-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="ab8b0-111">Apprendre à utiliser Bot Composer pour créer un bot</span><span class="sxs-lookup"><span data-stu-id="ab8b0-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="ab8b0-112">Apprendre à utiliser une fonction Azure pour fournir des données à partir de Stockage Azure</span><span class="sxs-lookup"><span data-stu-id="ab8b0-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="ab8b0-113">Partie 2</span><span class="sxs-lookup"><span data-stu-id="ab8b0-113">Part 2</span></span>

* <span data-ttu-id="ab8b0-114">Apprendre à configurer la scène pour utiliser Azure Bot Service dans ce projet</span><span class="sxs-lookup"><span data-stu-id="ab8b0-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="ab8b0-115">Apprendre à définir et rechercher des objets par le biais de la conversation avec le bot</span><span class="sxs-lookup"><span data-stu-id="ab8b0-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="ab8b0-116">Présentation d’Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="ab8b0-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="ab8b0-117">**Azure Bot Service** permet aux développeurs de créer des bots intelligents capables de maintenir une conversation naturelle avec les utilisateurs grâce à **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="ab8b0-118">Un chatbot est un excellent moyen d’étendre les façons dont un utilisateur peut interagir avec votre application.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="ab8b0-119">Un bot peut faire office de base de connaissances avec un [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) afin de maintenir une conversation sophistiquée grâce à la puissance de [LUIS (Language Understanding)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="ab8b0-120">Apprenez-en davantage sur [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="ab8b0-121">Partie 1 : Création du bot</span><span class="sxs-lookup"><span data-stu-id="ab8b0-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="ab8b0-122">Avant de pouvoir utiliser le bot dans l’application Unity, vous devez le développer, lui fournir des données et l’héberger sur **Azure**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="ab8b0-123">L’objectif du bot est de pouvoir indiquer combien d’*objets suivis* sont stockés dans la base de données, de trouver un *objet suivi* d’après son nom, et de fournir à l’utilisateur certaines informations élémentaires à son sujet.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="ab8b0-124">Présentation rapide de Tracked Objects Azure Function</span><span class="sxs-lookup"><span data-stu-id="ab8b0-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="ab8b0-125">Vous êtes sur le point de créer le bot, mais pour qu’il soit utile, vous devez lui donner une ressource à partir de laquelle il peut extraire des données.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="ab8b0-126">Étant donné que le *bot* sera capable de compter le nombre d’**objets suivis**, de rechercher des objets spécifiques en fonction de leur nom et d’en indiquer les détails, vous allez utiliser une fonction Azure simple qui a accès au **stockage Table Azure**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="ab8b0-127">Téléchargez le projet Tracked Objects Azure Function : [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) et extrayez son contenu sur votre disque dur.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="ab8b0-128">Cette fonction Azure a deux actions, **Count** et **Find**, qui peuvent être appelées par le biais d’appels *GET* *HTTP* simples.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="ab8b0-129">Vous pouvez inspecter le code dans **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="ab8b0-130">Apprenez-en davantage sur [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="ab8b0-131">La fonction **Count** est très simple : elle interroge à partir du **stockage Table** tous les **TrackedObjects** de la table.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="ab8b0-132">La fonction **Find**, quant à elle, prend un paramètre de requête *name* à partir de la requête *GET*, interroge le **stockage Table** pour obtenir un **TrackedObject** correspondant et retourne un DTO au format JSON.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="ab8b0-133">Vous pouvez déployer cette **fonction Azure** directement à partir de **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-133">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="ab8b0-134">Vous trouverez toutes les informations relatives au déploiement de fonction Azure [ici](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-134">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true).</span></span>

<span data-ttu-id="ab8b0-135">Une fois le déploiement terminé, dans le **portail Azure**, ouvrez la ressource correspondante et cliquez sur **Configuration** dans la section *Paramètres*.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-135">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="ab8b0-136">Dans les **Paramètres d’application**, vous devez fournir la *Chaîne de connexion* au **Stockage Azure** où sont stockés les **objets suivis**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-136">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="ab8b0-137">Cliquez sur **Nouveau paramètre d’application** et spécifiez **AzureStorageConnectionString** comme nom. En guise de valeur, spécifiez la *Chaîne de connexion* correcte.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-137">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="ab8b0-138">Après cela, cliquez sur **Enregistrer**. La **fonction Azure** est prête pour le *bot* que vous allez maintenant créer.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-138">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="ab8b0-139">Création d’un chatbot</span><span class="sxs-lookup"><span data-stu-id="ab8b0-139">Creating a conversation Bot</span></span>

<span data-ttu-id="ab8b0-140">Il existe plusieurs façons de développer un chatbot basé sur le Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-140">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="ab8b0-141">Dans cette leçon, vous allez utiliser l’application de bureau [Bot Framework Composer](https://docs.microsoft.com/composer/), un concepteur visuel idéal pour le développement rapide.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-141">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="ab8b0-142">Vous pouvez télécharger les dernières versions à partir du [dépôt GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-142">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="ab8b0-143">Il est disponible pour Windows, Mac et Linux.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-143">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="ab8b0-144">Une fois **Bot Framework Composer** installé, démarrez l’application. L’interface suivante doit s’afficher :</span><span class="sxs-lookup"><span data-stu-id="ab8b0-144">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Accueil Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="ab8b0-146">Nous avons préparé un projet Bot Composer qui fournit les dialogues et les déclencheurs nécessaires à ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-146">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="ab8b0-147">Téléchargez le projet Bot Framework Composer : [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) et extrayez son contenu sur votre disque dur.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-147">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="ab8b0-148">Dans la barre supérieure, cliquez sur **Open** et sélectionnez le projet Bot Framework que vous avez téléchargé, nommé **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-148">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="ab8b0-149">Une fois le projet entièrement chargé, il est prêt à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-149">After the project is fully loaded, you should see the project ready.</span></span>

![Bot Framework Composer avec le projet TrackedObjectsBot ouvert](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="ab8b0-151">Concentrons-nous sur le côté gauche, où vous pouvez voir le **volet des dialogues**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-151">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="ab8b0-152">Vous avez un dialogue nommé **TrackedObjectsBot** sous lequel figurent plusieurs **déclencheurs**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-152">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="ab8b0-153">Apprenez-en davantage sur les [concepts de Bot Framework](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-153">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="ab8b0-154">Ces déclencheurs effectuent les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab8b0-154">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="ab8b0-155">Greeting</span><span class="sxs-lookup"><span data-stu-id="ab8b0-155">Greeting</span></span>

<span data-ttu-id="ab8b0-156">Il s’agit du point d’entrée du *chatbot* chaque fois qu’un *utilisateur* démarre une conversation.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-156">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Déclencheur de dialogue Greeting du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="ab8b0-158">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="ab8b0-158">AskingForCount</span></span>

<span data-ttu-id="ab8b0-159">Ce dialogue est déclenché quand l’*utilisateur* demande le comptage de tous les **objets suivis**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-159">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="ab8b0-160">Voici les expressions de déclenchement :</span><span class="sxs-lookup"><span data-stu-id="ab8b0-160">These are the trigger phrases:</span></span>

>* <span data-ttu-id="ab8b0-161">count me all</span><span class="sxs-lookup"><span data-stu-id="ab8b0-161">count me all</span></span>
>* <span data-ttu-id="ab8b0-162">how many are stored</span><span class="sxs-lookup"><span data-stu-id="ab8b0-162">how many are stored</span></span>

![Déclencheur de dialogue AskForCount du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="ab8b0-164">Grâce à [LUIS](https://docs.microsoft.com/composer/how-to-use-luis), l’*utilisateur* n’a pas besoin d’énoncer les expressions de cette manière exacte. La conversation est ainsi plus naturelle.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-164">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="ab8b0-165">Dans ce dialogue, le *bot* communiquera également avec la fonction Azure **Count** (nous y reviendrons).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-165">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="ab8b0-166">Unknown Intent</span><span class="sxs-lookup"><span data-stu-id="ab8b0-166">Unknown Intent</span></span>

<span data-ttu-id="ab8b0-167">Ce dialogue est déclenché si l’entrée de l’*utilisateur* ne correspond à aucune autre condition de déclencheur. L’utilisateur est invité à reposer sa question.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-167">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Déclencheur de dialogue Unknown Intent du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="ab8b0-169">FindEntity</span><span class="sxs-lookup"><span data-stu-id="ab8b0-169">FindEntity</span></span>

<span data-ttu-id="ab8b0-170">Le dernier dialogue est plus complexe. Il implique une ramification et le stockage des données dans la *mémoire* du bot.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-170">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="ab8b0-171">Il demande à l’utilisateur le *nom* de l’**objet suivi** au sujet duquel il souhaite en savoir plus, exécute une requête sur la fonction Azure **Find**, et utilise la réponse pour poursuivre la conversation.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-171">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![Déclencheur de dialogue FindEntity du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="ab8b0-173">Si l’**objet suivi** est introuvable, l’utilisateur en est informé et la conversation se termine.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-173">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="ab8b0-174">Quand l’**objet suivi** en question est trouvé, le bot vérifie et signale quelles propriétés sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-174">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="ab8b0-175">Adaptation du bot</span><span class="sxs-lookup"><span data-stu-id="ab8b0-175">Adapting the Bot</span></span>

<span data-ttu-id="ab8b0-176">Les déclencheurs **AskingForCount** et **FindEntity** doivent communiquer avec le back-end. Cela signifie que vous devez ajouter l’URL correcte de la **fonction Azure** déployée précédemment.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-176">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="ab8b0-177">Dans le volet de dialogue, cliquez sur **AskingForCount** et recherchez l’action *Send an HTTP request* (Envoyer une requête HTTP). Ici, vous pouvez voir le champ **URL**, dans lequel vous devez indiquer l’URL correcte du point de terminaison de la fonction **Count**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-177">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Déclencheur de dialogue AskingForCount du projet TrackedObjectsBot - Configuration de point de terminaison](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="ab8b0-179">Pour finir, recherchez le déclencheur **FindEntity** et l’action *Send an HTTP request*. Dans le champ **URL**, indiquez l’URL du point de terminaison de la fonction **Find**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-179">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Déclencheur de dialogue FindEntity du projet TrackedObjectsBot - Configuration de point de terminaison](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="ab8b0-181">Vous êtes maintenant prêt à déployer le bot.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-181">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="ab8b0-182">Bot Framework Composer étant installé, vous pouvez publier le bot directement à partir de là.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-182">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="ab8b0-183">Apprenez-en davantage sur la [publication d’un bot à partir de Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-183">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="ab8b0-184">N’hésitez pas à vous amuser avec le bot en ajoutant des expressions de déclencheur ou de nouvelles réponses, ou en créant des branches de conversation.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-184">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="ab8b0-185">Partie 2 : Assemblage final dans Unity</span><span class="sxs-lookup"><span data-stu-id="ab8b0-185">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="ab8b0-186">Préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="ab8b0-186">Preparing the scene</span></span>

<span data-ttu-id="ab8b0-187">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-187">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Fenêtre du projet Unity avec le préfabriqué ChatBotManager sélectionné](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="ab8b0-189">À partir de là, déplacez le préfabriqué **ChatBotManager** dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-189">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="ab8b0-190">Une fois que vous avez ajouté le ChatBotManager à la scène, cliquez sur le composant **Chat Bot Manager**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-190">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="ab8b0-191">Dans l’inspecteur, vous verrez qu’il existe un champ vide **Direct Line Secret Key** (Clé secrète directe) que vous devez renseigner.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-191">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="ab8b0-192">Vous pouvez récupérer la *clé secrète* à partir du portail Azure en recherchant la ressource de type **Inscription de chaînes de bot** que vous avez créée dans la première partie de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-192">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity avec le préfabriqué ChatBotManager nouvellement ajouté toujours sélectionné](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="ab8b0-194">À présent, vous allez connecter l’objet **ChatBotManager** avec le composant **ChatBotController** attaché à l’objet **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-194">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="ab8b0-195">Dans la hiérarchie, sélectionnez le **ChatBotPanel**. Vous verrez un champ vide **Chat Bot Manager**. Faites glisser l’objet **ChatBotManager** de la hiérarchie vers le champ vide **Chat Bot Manager**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-195">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity avec ChatBotPanel configuré](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="ab8b0-197">Ensuite, vous avez besoin d’un moyen d’ouvrir le **ChatBotPanel** afin que l’utilisateur puisse interagir avec lui.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-197">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="ab8b0-198">Dans la fenêtre de scène, vous avez peut-être remarqué la présence d’un bouton latéral *Chat Bot* sur l’objet **MainMenu**. Vous l’utiliserez pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-198">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="ab8b0-199">Dans la hiérarchie, recherchez **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**, puis recherchez le script *ButtonConfigHelper* dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-199">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="ab8b0-200">Vous verrez un emplacement vide sur le rappel d’événement **OnClick()** .</span><span class="sxs-lookup"><span data-stu-id="ab8b0-200">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="ab8b0-201">Glissez-déposez le **ChatBotPanel** sur l’emplacement d’événement. Dans la liste déroulante, accédez à *GameObject*, sélectionnez *SetActive (bool)* dans le sous-menu et cochez la case.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-201">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity avec ButtonChatBot configuré](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="ab8b0-203">Maintenant, le chatbot peut être démarré à partir du menu principal et la scène est prête à être utilisée.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-203">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="ab8b0-204">Tester le bot</span><span class="sxs-lookup"><span data-stu-id="ab8b0-204">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="ab8b0-205">Demander la quantité d’objets suivis</span><span class="sxs-lookup"><span data-stu-id="ab8b0-205">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="ab8b0-206">Tout d’abord, nous allons demander au bot combien d’**objets suivis** sont stockés dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-206">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="ab8b0-207">Cette fois, vous devez exécuter l’application à partir d’HoloLens 2, car il se peut que des services comme *Synthèse vocale* ne soient pas disponibles sur votre système.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-207">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="ab8b0-208">Exécutez l’application sur votre HoloLens 2, puis cliquez sur le bouton *Chat Bot* à côté du menu principal.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-208">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="ab8b0-209">Après avoir été salué par le bot, posez-lui la question **how many objects do we have?** (combien d’objets avons-nous ?).</span><span class="sxs-lookup"><span data-stu-id="ab8b0-209">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="ab8b0-210">Il doit vous indiquer la quantité et mettre fin à la conversation.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-210">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="ab8b0-211">Poser une question sur un objet suivi</span><span class="sxs-lookup"><span data-stu-id="ab8b0-211">Asking about a tracked object</span></span>

<span data-ttu-id="ab8b0-212">Réexécutez l’application, mais cette fois-ci demandez **find me a tracked object** (trouvez-moi un objet suivi). Le bot vous demandera le nom. Répondez « car » ou donnez le nom d’un autre *objet suivi* qui existe dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-212">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="ab8b0-213">Le bot vous indiquera des détails tels que la description, et s’il a une ancre spatiale assignée.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-213">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="ab8b0-214">Essayez de demander un **objet suivi** qui n’existe pas et découvrez comment le bot répond.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-214">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ab8b0-215">Félicitations</span><span class="sxs-lookup"><span data-stu-id="ab8b0-215">Congratulations</span></span>

<span data-ttu-id="ab8b0-216">Dans ce tutoriel, vous avez découvert comment utiliser Azure Bot Framework pour interagir avec l’application dans une conversation en langage naturel.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-216">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="ab8b0-217">Vous avez découvert comment développer votre propre bot et quels sont les différents éléments nécessaires à son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-217">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="ab8b0-218">Conclusion</span><span class="sxs-lookup"><span data-stu-id="ab8b0-218">Conclusion</span></span>

<span data-ttu-id="ab8b0-219">Tout au long de cette série de tutoriels, vous avez vu comment enrichir votre application de fonctionnalités nouvelles et passionnantes grâce aux **services cloud Azure**.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-219">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="ab8b0-220">Vous pouvez désormais stocker des données et des images dans le cloud avec **Stockage Azure**, utiliser **Azure Custom Vision** pour associer des images et entraîner un modèle, placer des objets dans un contexte local avec **Azure Spatial Anchors**, et implémenter **Azure Bot Framework avec LUIS** pour ajouter un chatbot et obtenir un nouveau modèle d’interaction naturelle.</span><span class="sxs-lookup"><span data-stu-id="ab8b0-220">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
