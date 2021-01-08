---
title: Entrée vocale en non réel
description: Découvrez comment configurer et utiliser les entrées vocales, les mappages vocaux et la reconnaissance dans des applications de réalité mixte non réelles pour les appareils HoloLens 2.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, non réel, moteur 4, UE4, HoloLens 2, voix, entrée vocale, reconnaissance vocale, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010069"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="74ce1-104">Entrée vocale en non réel</span><span class="sxs-lookup"><span data-stu-id="74ce1-104">Voice Input in Unreal</span></span>

<span data-ttu-id="74ce1-105">Les entrées vocales en temps réel vous permettent d’interagir avec un hologramme sans avoir à utiliser des mouvements manuels et n’est pris en charge que pour HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="74ce1-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="74ce1-106">L’entrée vocale sur HoloLens 2 est alimentée par le même moteur qui prend en charge la reconnaissance vocale dans toutes les autres applications universelles Windows, mais inréelles utilise un moteur plus limité pour traiter l’entrée vocale.</span><span class="sxs-lookup"><span data-stu-id="74ce1-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="74ce1-107">Cela limite les fonctionnalités d’entrée vocale dans les mappages de reconnaissance vocale prédéfinis, qui sont traités dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="74ce1-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="74ce1-108">Activation de la reconnaissance vocale</span><span class="sxs-lookup"><span data-stu-id="74ce1-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="74ce1-109">Pour activer la reconnaissance vocale sur HoloLens :</span><span class="sxs-lookup"><span data-stu-id="74ce1-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="74ce1-110">Sélectionnez **paramètres du projet > plateforme > HoloLens > fonctionnalités** et activer le **microphone**.</span><span class="sxs-lookup"><span data-stu-id="74ce1-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="74ce1-111">Activez la reconnaissance vocale dans **paramètres > confidentialité > voix** et sélectionnez **anglais**.</span><span class="sxs-lookup"><span data-stu-id="74ce1-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="74ce1-112">La reconnaissance vocale fonctionne toujours dans la langue d’affichage Windows configurée dans l’application **paramètres** .</span><span class="sxs-lookup"><span data-stu-id="74ce1-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="74ce1-113">Il est recommandé d’activer également la **reconnaissance vocale en ligne** pour une qualité de service optimale.</span><span class="sxs-lookup"><span data-stu-id="74ce1-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Paramètres de reconnaissance vocale Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="74ce1-115">Une boîte de dialogue s’affiche lorsque l’application commence par vous demander si vous souhaitez activer le microphone.</span><span class="sxs-lookup"><span data-stu-id="74ce1-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="74ce1-116">Si vous sélectionnez **Oui** , l’entrée vocale démarre dans l’application.</span><span class="sxs-lookup"><span data-stu-id="74ce1-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="74ce1-117">L’entrée vocale ne nécessite pas d’API Windows Mixed Reality spéciales. Il repose sur l’API existante de mappage [d’entrée](https://docs.unrealengine.com/Gameplay/Input/index.html) de moteur non réel.</span><span class="sxs-lookup"><span data-stu-id="74ce1-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="74ce1-118">Ajout de mappages vocaux</span><span class="sxs-lookup"><span data-stu-id="74ce1-118">Adding Speech Mappings</span></span>

<span data-ttu-id="74ce1-119">La connexion vocale à l’action est une étape importante lors de l’utilisation de l’entrée vocale.</span><span class="sxs-lookup"><span data-stu-id="74ce1-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="74ce1-120">Ces mappages surveillent l’application pour les mots clés vocaux qu’un utilisateur peut prononcer, puis déclenchent une action liée.</span><span class="sxs-lookup"><span data-stu-id="74ce1-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="74ce1-121">Vous pouvez trouver des mappages de reconnaissance vocale en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="74ce1-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="74ce1-122">Sélectionnez **modifier > paramètres du projet**, faites défiler jusqu’à la section **moteur** , puis cliquez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="74ce1-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="74ce1-123">Pour ajouter un nouveau mappage de reconnaissance vocale pour une commande de saut :</span><span class="sxs-lookup"><span data-stu-id="74ce1-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="74ce1-124">Sélectionnez l' **+** icône en regard d' **éléments de tableau** et remplissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="74ce1-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="74ce1-125">**jumpWord** pour le nom de l' **action**</span><span class="sxs-lookup"><span data-stu-id="74ce1-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="74ce1-126">**raccourci** pour le **mot clé Speech**</span><span class="sxs-lookup"><span data-stu-id="74ce1-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="74ce1-127">Vous pouvez utiliser n’importe quel mot ou phrase (s) en anglais comme mot clé.</span><span class="sxs-lookup"><span data-stu-id="74ce1-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Paramètres d’entrée du moteur UE4](images/unreal/engine-input.png)

<span data-ttu-id="74ce1-129">Les mappages vocaux peuvent être utilisés en tant que composants d’entrée comme les mappages d’action ou d’axe ou en tant que nœuds de plan dans le graphique d’événements.</span><span class="sxs-lookup"><span data-stu-id="74ce1-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="74ce1-130">Par exemple, vous pouvez lier la commande Jump pour imprimer deux journaux différents selon le moment où le mot est parlé :</span><span class="sxs-lookup"><span data-stu-id="74ce1-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="74ce1-131">Double-cliquez sur un plan pour l’ouvrir dans le **graphique des événements**.</span><span class="sxs-lookup"><span data-stu-id="74ce1-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="74ce1-132">**Cliquez avec le bouton droit** et recherchez le **nom d’action** de votre mappage de reconnaissance vocale (dans le cas présent **jumpWord**), puis appuyez sur **entrée** pour ajouter un nœud **d’action d’entrée** au graphique.</span><span class="sxs-lookup"><span data-stu-id="74ce1-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="74ce1-133">Faites glisser et déposez le code PIN **appuyé** pour imprimer le nœud de **chaîne** comme indiqué dans l’image ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="74ce1-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="74ce1-134">Vous pouvez faire en sorte que le code confidentiel **libéré** soit vide. il n’exécutera rien pour les mappages vocaux.</span><span class="sxs-lookup"><span data-stu-id="74ce1-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Action simple pour la voix](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="74ce1-136">Lisez l’application, disons le mot **Jump** et regardez la console pour imprimer les journaux !</span><span class="sxs-lookup"><span data-stu-id="74ce1-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="74ce1-137">C’est tout ce dont vous avez besoin pour commencer à ajouter des entrées vocales à vos applications HoloLens en toute situation.</span><span class="sxs-lookup"><span data-stu-id="74ce1-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="74ce1-138">Vous trouverez plus d’informations sur la reconnaissance vocale et l’interactivité dans les liens ci-dessous, et veillez à réfléchir à l’expérience que vous créez pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="74ce1-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="74ce1-139">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="74ce1-139">Next Development Checkpoint</span></span>

<span data-ttu-id="74ce1-140">Si vous suivez le parcours de développement inréel que nous avons mis à disposition, vous êtes ensuite en train d’explorer les fonctionnalités de la plateforme de réalité mixte et les API :</span><span class="sxs-lookup"><span data-stu-id="74ce1-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="74ce1-141">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="74ce1-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="74ce1-142">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="74ce1-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="74ce1-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74ce1-143">See also</span></span>
* [<span data-ttu-id="74ce1-144">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="74ce1-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="74ce1-145">Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="74ce1-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="74ce1-146">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="74ce1-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

