---
title: Ajout d’un mode hors connexion pour la traduction locale de la reconnaissance vocale
description: Suivez ce cours pour découvrir comment ajouter le mode hors connexion pour la traduction par reconnaissance vocale locale dans les applications de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, reconnaissance vocale, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: db495d6cdfa99721e68b4004535a5411bde9b17d
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010079"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="59350-104">2. Ajout d’un mode hors connexion pour la traduction de parole en texte locale</span><span class="sxs-lookup"><span data-stu-id="59350-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="59350-105">Dans ce tutoriel, vous allez ajouter la capacité d’exécuter des commandes en utilisant la reconnaissance vocale Azure, ce qui va vous permettre de déclencher une action en fonction du mot ou de l’expression que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="59350-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="59350-106">Objectifs</span><span class="sxs-lookup"><span data-stu-id="59350-106">Objectives</span></span>

* <span data-ttu-id="59350-107">Découvrir comment la reconnaissance vocale Azure peut être utilisée pour exécuter des commandes</span><span class="sxs-lookup"><span data-stu-id="59350-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="59350-108">Instructions</span><span class="sxs-lookup"><span data-stu-id="59350-108">Instructions</span></span>

<span data-ttu-id="59350-109">Dans la fenêtre Hierachy, sélectionnez l’objet **Lunarcom** puis, dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Lunarcom Wake Word Recognizer (Script)** à l’objet Lunarcom et configurez-le de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="59350-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="59350-110">Dans le champ **Wake Word**, entrez une expression appropriée, par exemple, _Activer le terminal_.</span><span class="sxs-lookup"><span data-stu-id="59350-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="59350-111">Dans le champ **Dismiss Word**, entrez une expression appropriée, par exemple, _Désactiver le terminal_.</span><span class="sxs-lookup"><span data-stu-id="59350-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Éditeur Unity avec le composant de script Lunarcom Wake Word Recognizer mis en évidence](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="59350-113">Le composant Lunarcom Wake Word Recognizer (Script) ne fait pas partie de MRTK.</span><span class="sxs-lookup"><span data-stu-id="59350-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="59350-114">Il a été fourni avec les ressources de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="59350-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="59350-115">Si vous entrez maintenant en mode Game, comme dans le tutoriel précédent, le panneau du terminal est activé par défaut, mais vous pouvez maintenant le désactiver en prononçant la valeur de Dismiss Word, **Désactiver le terminal** :</span><span class="sxs-lookup"><span data-stu-id="59350-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![Éditeur Unity en mode lecture avec la fonctionnalité de reconnaissance vocale en cours d’utilisation](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="59350-117">Et réactivez-le en prononçant la valeur de Wake Word, à savoir **Activer le terminal** :</span><span class="sxs-lookup"><span data-stu-id="59350-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![Éditeur Unity en mode lecture avec le terminal actif](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="59350-119">L’application a besoin de se connecter à Azure, donc vérifiez que votre ordinateur/appareil est connecté à Internet.</span><span class="sxs-lookup"><span data-stu-id="59350-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="59350-120">Si vous prévoyez d’être souvent dans l’impossibilité de vous connecter à Azure, vous pouvez aussi implémenter des commandes vocales à l’aide de MRTK en suivant les instructions données dans [Utilisation des commandes vocales](mr-learning-base-09.md).</span><span class="sxs-lookup"><span data-stu-id="59350-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="59350-121">Félicitations</span><span class="sxs-lookup"><span data-stu-id="59350-121">Congratulations</span></span>

<span data-ttu-id="59350-122">Vous avez implémenté des commandes vocales Azure.</span><span class="sxs-lookup"><span data-stu-id="59350-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="59350-123">Exécutez l’application sur votre appareil pour vérifier que tout fonctionne bien.</span><span class="sxs-lookup"><span data-stu-id="59350-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="59350-124">Dans le tutoriel suivant, vous allez apprendre à traduire la parole en utilisant la traduction vocale Azure.</span><span class="sxs-lookup"><span data-stu-id="59350-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="59350-125">Tutoriel suivant : 3. Ajout du composant de traduction vocale Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="59350-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
