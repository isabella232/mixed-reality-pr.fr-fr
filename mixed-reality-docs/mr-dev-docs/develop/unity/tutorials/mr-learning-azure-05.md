---
title: Intégration d’Azure Bot Service avec LUIS
description: Suivez ce cours pour découvrir comment implémenter Azure Bot Service et la compréhension du langage naturel dans une application HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, hololens 2, azure bot service, luis, langage naturel, chatbot, services cloud azure, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 109befea299ba2539e3ab8ee616d3321f89660cd30a831a6833e7bbf51029f98
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206522"
---
# <a name="5-integrating-azure-bot-service"></a>5. Intégration d’Azure Bot Service

Dans ce tutoriel, vous allez apprendre à utiliser **Azure Bot Service** dans l’application de démonstration **HoloLens 2** pour ajouter LUIS (Language Understanding) et laisser le bot assister l’utilisateur lors de la recherche d’**objets suivis**. Il s’agit d’un tutoriel en deux parties. Dans la première, vous allez créer le bot avec la solution sans code [Bot Composer](/composer/introduction), et examiner la fonction Azure qui alimente le bot avec les données nécessaires. Dans la deuxième partie, vous utiliserez le **BotManager (script)** dans le projet Unity pour consommer le service bot hébergé.

## <a name="objectives"></a>Objectifs

## <a name="part-1"></a>Partie 1

* Apprendre les bases d’Azure Bot Service
* Apprendre à utiliser Bot Composer pour créer un bot
* Apprendre à utiliser une fonction Azure pour fournir des données à partir de Stockage Azure

## <a name="part-2"></a>Partie 2

* Apprendre à configurer la scène pour utiliser Azure Bot Service dans ce projet
* Apprendre à définir et rechercher des objets par le biais de la conversation avec le bot

## <a name="understanding-azure-bot-service"></a>Présentation d’Azure Bot Service

**Azure Bot Service** permet aux développeurs de créer des bots intelligents capables de maintenir une conversation naturelle avec les utilisateurs grâce à **LUIS**. Un chatbot est un excellent moyen d’étendre les façons dont un utilisateur peut interagir avec votre application. Un bot peut faire office de base de connaissances avec un [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) afin de maintenir une conversation sophistiquée grâce à la puissance de [LUIS (Language Understanding)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).

Apprenez-en davantage sur [Azure Bot Service](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).

## <a name="part-1---creating-the-bot"></a>Partie 1 : Création du bot

Avant de pouvoir utiliser le bot dans l’application Unity, vous devez le développer, lui fournir des données et l’héberger sur **Azure**.
L’objectif du bot est de pouvoir indiquer combien d’*objets suivis* sont stockés dans la base de données, de trouver un *objet suivi* d’après son nom, et de fournir à l’utilisateur certaines informations élémentaires à son sujet.

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>Présentation rapide de Tracked Objects Azure Function

Vous êtes sur le point de créer le bot, mais pour qu’il soit utile, vous devez lui donner une ressource à partir de laquelle il peut extraire des données. Étant donné que le *bot* sera capable de compter le nombre d’**objets suivis**, de rechercher des objets spécifiques en fonction de leur nom et d’en indiquer les détails, vous allez utiliser une fonction Azure simple qui a accès au **stockage Table Azure**.

Téléchargez le projet Tracked Objects Azure Function : [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) et extrayez son contenu sur votre disque dur.

Cette fonction Azure a deux actions, **Count** et **Find**, qui peuvent être appelées par le biais d’appels *GET* *HTTP* simples. Vous pouvez inspecter le code dans **Visual Studio**.

Apprenez-en davantage sur [Azure Functions](/azure/azure-functions/functions-overview).

La fonction **Count** est très simple : elle interroge à partir du **stockage Table** tous les **TrackedObjects** de la table. La fonction **Find**, quant à elle, prend un paramètre de requête *name* à partir de la requête *GET*, interroge le **stockage Table** pour obtenir un **TrackedObject** correspondant et retourne un DTO au format JSON.

Pour déployer cette **fonction Azure** directement à partir de **Visual Studio**, ouvrez le dossier AzureFunction_TrackedObjectsService téléchargé et ouvrez le fichier **.sln** avec le ![dossier AzureFunction_TrackedObjectsService](images/mr-learning-azure/tutorial5-section3-step1-1.png) de Visual Studio.

Une fois le fichier chargé dans Visual Studio, cliquez avec le bouton droit sur **Service d’objets suivis** dans l’Explorateur de solutions, puis sélectionnez ![Publier le service d’objets suivis](images/mr-learning-azure/tutorial5-section3-step1-2.png).

La fenêtre contextuelle Publier apparaît et vous demande la plateforme cible ; sélectionnez Azure, puis cliquez sur le bouton **Suivant**.

![Sélectionner la plateforme cible](images/mr-learning-azure/tutorial5-section3-step1-3.png)

Dans Cible spécifique, sélectionnez **Application de fonction Azure (Windows)** , puis cliquez sur le bouton **Suivant**.

![Sélectionner l’hôte cible](images/mr-learning-azure/tutorial5-section3-step1-4.png)

Si vous n’êtes pas connecté à Azure, connectez-vous via Visual Studio ; la fenêtre doit se présenter comme ceci :

![Sélectionner ou créer une fonction Azure](images/mr-learning-azure/tutorial5-section3-step1-5.png)

Cliquez sur le bouton Pulsation pour créer une application de fonction dans le compte Azure.

![Créer une application de fonction](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* Pour **Nom**, entrez un nom approprié pour le service, par exemple *TrackedObjectsService*.
* Pour **Type de plan**, choisissez Consommation.
* Pour **Emplacement**, choisissez un emplacement proche de l’emplacement physique des utilisateurs de votre application, par exemple *USA Ouest*.
* Pour **Groupe de ressources** et **Stockage**, choisissez respectivement le groupe et le compte de stockage Azure qui ont été créés dans les chapitres précédents.

Une fois l’application de fonction créée, cliquez sur le bouton **Terminer**.

![Terminer la création de l’application de fonction](images/mr-learning-azure/tutorial5-section3-step1-7.png)

Pour mettre à jour la chaîne de connexion, cliquez sur **3 points** sous l’onglet **hébergement**, puis sélectionnez **Gérer les paramètres Azure App Service**.

![Ouvrir Paramètres d’application](images/mr-learning-azure/tutorial5-section3-step1-8.png)

La fenêtre **Paramètres d’application** s’ouvre. Remplacez votre AzureStorageConnectionString pour les deux options **Local** et **Distant** par votre AzureStorageConnectionString. Une fois que vous avez effectué le remplacement, cliquez sur OK.

![Mettre à jour une chaîne de connexion](images/mr-learning-azure/tutorial5-section3-step1-8a.png)

À présent, cliquez sur le bouton **Publier** pour publier la fonction et attendez la publication.

Une fois la publication terminée, cliquez sur **Gérer dans le portail Azure** sous la section Actions : vous êtes alors dirigé vers la fonction spécifique dans le portail Azure. Cliquez ensuite sur **Configuration**, qui se trouve sous la section *Paramètres*. Dans les **Paramètres d’application**, vous devez fournir la *Chaîne de connexion* au **Stockage Azure** où sont stockés les **objets suivis**. Cliquez sur **Nouveau paramètre d’application** et spécifiez **AzureStorageConnectionString** comme nom. En guise de valeur, spécifiez la *Chaîne de connexion* correcte. Après cela, cliquez sur **Enregistrer**. La **fonction Azure** est prête pour le *bot* que vous allez maintenant créer.

Pour obtenir l’URL de Count et de Find, sélectionnez **Fonctions**, qui se trouve sous la section *Fonctions*. Vous pouvez voir ici les fonctions Count et Find. Sélectionnez la fonction Count, puis le bouton *Obtenir l’URL de la fonction* en haut de la page.
Suivez la même procédure pour obtenir l’URL de la fonction Find.

### <a name="creating-a-conversation-bot"></a>Création d’un chatbot

Il existe plusieurs façons de développer un chatbot basé sur Bot Framework. Dans cette leçon, vous allez utiliser l’application de bureau [Bot Framework Composer](/composer/), un concepteur visuel idéal pour le développement rapide.

Vous pouvez télécharger les dernières versions à partir du [dépôt GitHub](https://github.com/microsoft/BotFramework-Composer/releases). Il est disponible pour Windows, Mac et Linux.

Une fois **Bot Framework Composer** installé, démarrez l’application. L’interface suivante doit s’afficher :

![Accueil Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

Nous avons préparé un projet Bot Composer qui fournit les dialogues et les déclencheurs nécessaires à ce tutoriel. Téléchargez le projet Bot Framework Composer : [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) et extrayez son contenu sur votre disque dur.

Dans la barre supérieure, cliquez sur **Open** et sélectionnez le projet Bot Framework que vous avez téléchargé, nommé **TrackedObjectsBot**. Une fois le projet entièrement chargé, il est prêt à l’emploi.

![Bot Framework Composer avec le projet TrackedObjectsBot ouvert](images/mr-learning-azure/tutorial5-section4-step1-2.png)

Concentrons-nous sur le côté gauche, où vous pouvez voir le **volet des dialogues**. Vous avez un dialogue nommé **TrackedObjectsBot** sous lequel figurent plusieurs **déclencheurs**.

Apprenez-en davantage sur les [concepts de Bot Framework](/composer/concept-dialog).

Ces déclencheurs effectuent les opérations suivantes :

#### <a name="greeting"></a>Greeting

Il s’agit du point d’entrée du *chatbot* chaque fois qu’un *utilisateur* démarre une conversation.

![Déclencheur de dialogue Greeting du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

Ce dialogue est déclenché quand l’*utilisateur* demande le comptage de tous les **objets suivis**.
Voici les expressions de déclenchement :

>* count me all
>* how many are stored

![Déclencheur de dialogue AskForCount du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

Grâce à [LUIS](/composer/how-to-use-luis), l’*utilisateur* n’a pas besoin d’énoncer les expressions de cette manière exacte. La conversation est ainsi plus naturelle.

Dans ce dialogue, le *bot* communiquera également avec la fonction Azure **Count** (nous y reviendrons).

#### <a name="unknown-intent"></a>Unknown Intent

Ce dialogue est déclenché si l’entrée de l’*utilisateur* ne correspond à aucune autre condition de déclencheur. L’utilisateur est invité à reposer sa question.

![Déclencheur de dialogue Unknown Intent du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

Le dernier dialogue est plus complexe. Il implique une ramification et le stockage des données dans la *mémoire* du bot.
Il demande à l’utilisateur le *nom* de l’**objet suivi** au sujet duquel il souhaite en savoir plus, exécute une requête sur la fonction Azure **Find**, et utilise la réponse pour poursuivre la conversation.

![Déclencheur de dialogue FindEntity du projet TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

Si l’**objet suivi** est introuvable, l’utilisateur en est informé et la conversation se termine. Quand l’**objet suivi** en question est trouvé, le bot vérifie et signale quelles propriétés sont disponibles.

### <a name="adapting-the-bot"></a>Adaptation du bot

Les déclencheurs **AskingForCount** et **FindEntity** doivent communiquer avec le back-end. Cela signifie que vous devez ajouter l’URL correcte de la **fonction Azure** déployée précédemment.

Dans le volet de dialogue, cliquez sur **AskingForCount** et recherchez l’action *Send an HTTP request* (Envoyer une requête HTTP). Ici, vous pouvez voir le champ **URL**, dans lequel vous devez indiquer l’URL correcte du point de terminaison de la fonction **Count**.

![Déclencheur de dialogue AskingForCount du projet TrackedObjectsBot - Configuration de point de terminaison](images/mr-learning-azure/tutorial5-section5-step1-1.png)

Pour finir, recherchez le déclencheur **FindEntity** et l’action *Send an HTTP request*. Dans le champ **URL**, indiquez l’URL du point de terminaison de la fonction **Find**.

![Déclencheur de dialogue FindEntity du projet TrackedObjectsBot - Configuration de point de terminaison](images/mr-learning-azure/tutorial5-section5-step1-2.png)

Vous êtes maintenant prêt à déployer le bot. Bot Framework Composer étant installé, vous pouvez publier le bot directement à partir de là.

Apprenez-en davantage sur la [publication d’un bot à partir de Bot Composer](/composer/how-to-publish-bot).

> [!TIP]
> N’hésitez pas à vous amuser avec le bot en ajoutant des expressions de déclencheur ou de nouvelles réponses, ou en créant des branches de conversation.

## <a name="part-2---putting-everything-together-in-unity"></a>Partie 2 : Assemblage final dans Unity

### <a name="preparing-the-scene"></a>Préparation de la scène

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.

![Fenêtre du projet Unity avec le préfabriqué ChatBotManager sélectionné](images/mr-learning-azure/tutorial5-section6-step1-1.png)

À partir de là, déplacez le préfabriqué **ChatBotManager** dans la hiérarchie de la scène.

Une fois que vous avez ajouté le ChatBotManager à la scène, cliquez sur le composant **Chat Bot Manager**.
Dans l’inspecteur, vous verrez qu’il existe un champ vide **Direct Line Secret Key** (Clé secrète directe) que vous devez renseigner.

> [!TIP]
> Vous pouvez récupérer la *clé secrète* à partir du portail Azure en recherchant la ressource de type **Inscription de chaînes de bot** que vous avez créée dans la première partie de ce tutoriel.

![Unity avec le préfabriqué ChatBotManager nouvellement ajouté toujours sélectionné](images/mr-learning-azure/tutorial5-section6-step1-2.png)

À présent, vous allez connecter l’objet **ChatBotManager** avec le composant **ChatBotController** attaché à l’objet **ChatBotPanel**. Dans la hiérarchie, sélectionnez le **ChatBotPanel**. Vous verrez un champ vide **Chat Bot Manager**. Faites glisser l’objet **ChatBotManager** de la hiérarchie vers le champ vide **Chat Bot Manager**.

![Unity avec ChatBotPanel configuré](images/mr-learning-azure/tutorial5-section6-step1-3.png)

Ensuite, vous avez besoin d’un moyen d’ouvrir le **ChatBotPanel** afin que l’utilisateur puisse interagir avec lui. Dans la fenêtre de scène, vous avez peut-être remarqué la présence d’un bouton latéral *Chat Bot* sur l’objet **MainMenu**. Vous l’utiliserez pour résoudre ce problème.

Dans la hiérarchie, recherchez **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**, puis recherchez le script *ButtonConfigHelper* dans l’inspecteur. Vous verrez un emplacement vide sur le rappel d’événement **OnClick()** . Glissez-déposez le **ChatBotPanel** sur l’emplacement d’événement. Dans la liste déroulante, accédez à *GameObject*, sélectionnez *SetActive (bool)* dans le sous-menu et cochez la case.

![Unity avec ButtonChatBot configuré](images/mr-learning-azure/tutorial5-section6-step1-4.png)

Maintenant, le chatbot peut être démarré à partir du menu principal et la scène est prête à être utilisée.

### <a name="putting-the-bot-to-a-test"></a>Tester le bot

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>Demander la quantité d’objets suivis

Tout d’abord, nous allons demander au bot combien d’**objets suivis** sont stockés dans la base de données.

> [!NOTE]
> Cette fois, vous devez exécuter l’application à partir d’HoloLens 2, car il se peut que des services comme *Synthèse vocale* ne soient pas disponibles sur votre système.

Exécutez l’application sur votre HoloLens 2, puis cliquez sur le bouton *Chat Bot* à côté du menu principal.
Après avoir été salué par le bot, posez-lui la question **how many objects do we have?** (combien d’objets avons-nous ?).
Il doit vous indiquer la quantité et mettre fin à la conversation.

#### <a name="asking-about-a-tracked-object"></a>Poser une question sur un objet suivi

Réexécutez l’application, mais cette fois-ci demandez **find me a tracked object** (trouvez-moi un objet suivi). Le bot vous demandera le nom. Répondez « car » ou donnez le nom d’un autre *objet suivi* qui existe dans la base de données. Le bot vous indiquera des détails tels que la description, et s’il a une ancre spatiale assignée.

> [!TIP]
> Essayez de demander un **objet suivi** qui n’existe pas et découvrez comment le bot répond.

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez découvert comment utiliser Azure Bot Framework pour interagir avec l’application dans une conversation en langage naturel. Vous avez découvert comment développer votre propre bot et quels sont les différents éléments nécessaires à son fonctionnement.

## <a name="conclusion"></a>Conclusion

Tout au long de cette série de tutoriels, vous avez vu comment enrichir votre application de fonctionnalités nouvelles et passionnantes grâce aux **services cloud Azure**.
Vous pouvez désormais stocker des données et des images dans le cloud avec **Stockage Azure**, utiliser **Azure Custom Vision** pour associer des images et entraîner un modèle, placer des objets dans un contexte local avec **Azure Spatial Anchors**, et implémenter **Azure Bot Framework avec LUIS** pour ajouter un chatbot et obtenir un nouveau modèle d’interaction naturelle.