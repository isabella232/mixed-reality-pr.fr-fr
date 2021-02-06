---
title: Entrée vocale dans Unity
description: Découvrez comment Unity expose trois façons d’ajouter une entrée vocale, une reconnaissance vocale et une dictée à votre application Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrée vocale, KeywordRecognizer, GrammarRecognizer, microphone, dictée, voix, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: 7268a4df9c7fce03029937c72540ed274574067d
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606114"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="d4cff-104">Entrée vocale dans Unity</span><span class="sxs-lookup"><span data-stu-id="d4cff-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="d4cff-105">Avant de commencer, envisagez d’utiliser le plug-in Unity pour le kit de développement logiciel (SDK) cognitive Speech services.</span><span class="sxs-lookup"><span data-stu-id="d4cff-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="d4cff-106">Le plug-in offre de meilleurs résultats de précision vocale et un accès facile au décodage vocal en texte, ainsi que des fonctionnalités vocales avancées telles que la boîte de dialogue, l’interaction fondée sur l’intention, la traduction, la synthèse vocale et la reconnaissance vocale en langage naturel.</span><span class="sxs-lookup"><span data-stu-id="d4cff-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="d4cff-107">Pour commencer, consultez l' [exemple et la documentation](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span><span class="sxs-lookup"><span data-stu-id="d4cff-107">To get started, check out the [sample and documentation](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="d4cff-108">Unity expose trois façons d’ajouter une [entrée vocale](../../design/voice-input.md) à votre application Unity, les deux premières étant des types de PhraseRecognizer :</span><span class="sxs-lookup"><span data-stu-id="d4cff-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="d4cff-109">Le `KeywordRecognizer` fournit à votre application un tableau de commandes de chaîne à écouter.</span><span class="sxs-lookup"><span data-stu-id="d4cff-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="d4cff-110">Le `GrammarRecognizer` donne à votre application un fichier SRGS définissant une grammaire spécifique à écouter</span><span class="sxs-lookup"><span data-stu-id="d4cff-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="d4cff-111">Le `DictationRecognizer` permet à votre application d’écouter tout mot et de fournir à l’utilisateur une note ou un autre affichage de sa parole.</span><span class="sxs-lookup"><span data-stu-id="d4cff-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="d4cff-112">La reconnaissance de la dictée et de l’expression ne peut pas être gérée en même temps.</span><span class="sxs-lookup"><span data-stu-id="d4cff-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="d4cff-113">Si un GrammarRecognizer ou un KeywordRecognizer est actif, un DictationRecognizer ne peut pas être actif et vice versa.</span><span class="sxs-lookup"><span data-stu-id="d4cff-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="d4cff-114">Activation de la fonctionnalité de voix</span><span class="sxs-lookup"><span data-stu-id="d4cff-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="d4cff-115">La fonctionnalité **microphone** doit être déclarée pour qu’une application utilise l’entrée vocale.</span><span class="sxs-lookup"><span data-stu-id="d4cff-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="d4cff-116">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet > Player**</span><span class="sxs-lookup"><span data-stu-id="d4cff-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="d4cff-117">Sélectionner l’onglet **Windows Store**</span><span class="sxs-lookup"><span data-stu-id="d4cff-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="d4cff-118">Dans la section **paramètres de publication > fonctionnalités** , vérifiez la fonctionnalité du **microphone** .</span><span class="sxs-lookup"><span data-stu-id="d4cff-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="d4cff-119">Accorder des autorisations à l’application pour l’accès au microphone sur votre appareil HoloLens</span><span class="sxs-lookup"><span data-stu-id="d4cff-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="d4cff-120">Vous êtes invité à le faire au démarrage de l’appareil, mais si vous avez cliqué accidentellement sur « non », vous pouvez modifier les autorisations dans les paramètres de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="d4cff-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="d4cff-121">Reconnaissance d’expressions</span><span class="sxs-lookup"><span data-stu-id="d4cff-121">Phrase Recognition</span></span>

<span data-ttu-id="d4cff-122">Pour permettre à votre application d’écouter des expressions spécifiques parlées par l’utilisateur, puis de prendre des mesures, vous devez :</span><span class="sxs-lookup"><span data-stu-id="d4cff-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="d4cff-123">Spécifiez les expressions à écouter à l’aide d’un `KeywordRecognizer` ou `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="d4cff-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="d4cff-124">Gérer l' `OnPhraseRecognized` événement et entreprendre une action correspondant à l’expression reconnue</span><span class="sxs-lookup"><span data-stu-id="d4cff-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="d4cff-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="d4cff-125">KeywordRecognizer</span></span>

<span data-ttu-id="d4cff-126">**Espace de noms :** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="d4cff-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="d4cff-127">**Types :** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="d4cff-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="d4cff-128">Nous aurons besoin de quelques instructions d’utilisation pour enregistrer des séquences de touches :</span><span class="sxs-lookup"><span data-stu-id="d4cff-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="d4cff-129">Nous allons ensuite ajouter quelques champs à votre classe pour stocker le module de reconnaissance et de mot clé->dictionnaire d’actions :</span><span class="sxs-lookup"><span data-stu-id="d4cff-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="d4cff-130">Ajoutez maintenant un mot clé au dictionnaire, par exemple dans une `Start()` méthode.</span><span class="sxs-lookup"><span data-stu-id="d4cff-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="d4cff-131">Nous ajoutons le mot clé « Activate » dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="d4cff-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="d4cff-132">Créez le module de reconnaissance de mot clé et dites-lui ce que nous souhaitons reconnaître :</span><span class="sxs-lookup"><span data-stu-id="d4cff-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="d4cff-133">Inscrivez-vous maintenant pour l' `OnPhraseRecognized` événement</span><span class="sxs-lookup"><span data-stu-id="d4cff-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="d4cff-134">Voici un exemple de gestionnaire :</span><span class="sxs-lookup"><span data-stu-id="d4cff-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="d4cff-135">Enfin, commencez à reconnaître !</span><span class="sxs-lookup"><span data-stu-id="d4cff-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="d4cff-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="d4cff-136">GrammarRecognizer</span></span>

<span data-ttu-id="d4cff-137">**Espace de noms :** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="d4cff-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="d4cff-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="d4cff-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="d4cff-139">Le GrammarRecognizer est utilisé si vous spécifiez votre grammaire de reconnaissance à l’aide de SRGS.</span><span class="sxs-lookup"><span data-stu-id="d4cff-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="d4cff-140">Cela peut être utile si votre application contient plus de seulement quelques mots-clés, si vous souhaitez reconnaître des expressions plus complexes ou si vous souhaitez facilement activer et désactiver des ensembles de commandes.</span><span class="sxs-lookup"><span data-stu-id="d4cff-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="d4cff-141">Voir : [créer des grammaires à l’aide de SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) pour les informations de format de fichier.</span><span class="sxs-lookup"><span data-stu-id="d4cff-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="d4cff-142">Une fois que vous disposez de la grammaire SRGS et que celle-ci se trouve dans votre projet dans un [dossier StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="d4cff-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="d4cff-143">Créez un `GrammarRecognizer` et transmettez-lui le chemin d’accès à votre fichier SRGS :</span><span class="sxs-lookup"><span data-stu-id="d4cff-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="d4cff-144">Inscrivez-vous maintenant pour l' `OnPhraseRecognized` événement</span><span class="sxs-lookup"><span data-stu-id="d4cff-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="d4cff-145">Vous obtenez un rappel contenant les informations spécifiées dans votre syntaxe SRGS, que vous pouvez gérer de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="d4cff-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="d4cff-146">La plupart des informations importantes seront fournies dans le `semanticMeanings` tableau.</span><span class="sxs-lookup"><span data-stu-id="d4cff-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="d4cff-147">Enfin, commencez à reconnaître !</span><span class="sxs-lookup"><span data-stu-id="d4cff-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="d4cff-148">Dictation</span><span class="sxs-lookup"><span data-stu-id="d4cff-148">Dictation</span></span>

<span data-ttu-id="d4cff-149">**Espace de noms :** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="d4cff-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="d4cff-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="d4cff-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="d4cff-151">Utilisez le `DictationRecognizer` pour convertir la parole de l’utilisateur en texte.</span><span class="sxs-lookup"><span data-stu-id="d4cff-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="d4cff-152">Le DictationRecognizer expose les fonctionnalités de [dictée](../../design/voice-input.md#dictation) et prend en charge l’inscription et l’écoute des événements d’hypothèse et d’expression terminés, ce qui vous permet de fournir des commentaires à l’utilisateur pendant qu’il parle et par la suite.</span><span class="sxs-lookup"><span data-stu-id="d4cff-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="d4cff-153">`Start()` et les `Stop()` méthodes activent et désactivent respectivement la reconnaissance de la dictée.</span><span class="sxs-lookup"><span data-stu-id="d4cff-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="d4cff-154">Une fois le module de reconnaissance terminé, il doit être supprimé à l’aide `Dispose()` de pour libérer les ressources qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="d4cff-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="d4cff-155">Les ressources seront libérées automatiquement pendant la garbage collection à un coût de performances supplémentaire si elles ne sont pas libérées avant cela.</span><span class="sxs-lookup"><span data-stu-id="d4cff-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="d4cff-156">Il n’y a que quelques étapes nécessaires pour commencer à utiliser la dictée :</span><span class="sxs-lookup"><span data-stu-id="d4cff-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="d4cff-157">Créer un nouveau `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="d4cff-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="d4cff-158">Gérer les événements de dictée</span><span class="sxs-lookup"><span data-stu-id="d4cff-158">Handle Dictation events</span></span>
3. <span data-ttu-id="d4cff-159">Démarrer le DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="d4cff-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="d4cff-160">Activation de la fonctionnalité de dictée</span><span class="sxs-lookup"><span data-stu-id="d4cff-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="d4cff-161">Les fonctionnalités du client et du **microphone** **Internet** doivent être déclarées pour qu’une application utilise la dictée :</span><span class="sxs-lookup"><span data-stu-id="d4cff-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="d4cff-162">Dans l’éditeur Unity, accédez à **modifier > paramètres du projet > Player**</span><span class="sxs-lookup"><span data-stu-id="d4cff-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="d4cff-163">Sélectionner sous l’onglet **Windows Store**</span><span class="sxs-lookup"><span data-stu-id="d4cff-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="d4cff-164">Dans la section **paramètres de publication > fonctionnalités** , activez la fonctionnalité **internetclient**</span><span class="sxs-lookup"><span data-stu-id="d4cff-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="d4cff-165">Éventuellement, si vous n’avez pas déjà activé le microphone, vérifiez la fonctionnalité du **microphone** .</span><span class="sxs-lookup"><span data-stu-id="d4cff-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="d4cff-166">Accorder des autorisations à l’application pour l’accès au microphone sur votre appareil HoloLens si vous ne l’avez pas déjà fait</span><span class="sxs-lookup"><span data-stu-id="d4cff-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="d4cff-167">Vous êtes invité à le faire au démarrage de l’appareil, mais si vous avez cliqué accidentellement sur « non », vous pouvez modifier les autorisations dans les paramètres de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="d4cff-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="d4cff-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="d4cff-168">DictationRecognizer</span></span>

<span data-ttu-id="d4cff-169">Créez un DictationRecognizer de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="d4cff-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="d4cff-170">Quatre événements de dictée peuvent être souscrits et gérés pour implémenter le comportement de la dictée.</span><span class="sxs-lookup"><span data-stu-id="d4cff-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="d4cff-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="d4cff-171">**DictationResult**</span></span>

<span data-ttu-id="d4cff-172">Cet événement est déclenché après la suspension de l’utilisateur, généralement à la fin d’une phrase.</span><span class="sxs-lookup"><span data-stu-id="d4cff-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="d4cff-173">La chaîne complète reconnue est retournée ici.</span><span class="sxs-lookup"><span data-stu-id="d4cff-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="d4cff-174">Tout d’abord, abonnez-vous à l' `DictationResult` événement :</span><span class="sxs-lookup"><span data-stu-id="d4cff-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="d4cff-175">Gérez ensuite le rappel DictationResult :</span><span class="sxs-lookup"><span data-stu-id="d4cff-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="d4cff-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="d4cff-176">**DictationHypothesis**</span></span>

<span data-ttu-id="d4cff-177">Cet événement est déclenché en continu pendant que l’utilisateur parle.</span><span class="sxs-lookup"><span data-stu-id="d4cff-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="d4cff-178">À mesure que le module de reconnaissance écoute, il fournit du texte sur ce qu’il est entendu jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="d4cff-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="d4cff-179">Tout d’abord, abonnez-vous à l' `DictationHypothesis` événement :</span><span class="sxs-lookup"><span data-stu-id="d4cff-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="d4cff-180">Gérez ensuite le rappel DictationHypothesis :</span><span class="sxs-lookup"><span data-stu-id="d4cff-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="d4cff-181">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="d4cff-181">**DictationComplete**</span></span>

<span data-ttu-id="d4cff-182">Cet événement est déclenché lorsque le module de reconnaissance s’arrête, qu’il s’agisse de l’appel de Stop (), d’un délai d’attente ou d’une autre erreur.</span><span class="sxs-lookup"><span data-stu-id="d4cff-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="d4cff-183">Tout d’abord, abonnez-vous à l' `DictationComplete` événement :</span><span class="sxs-lookup"><span data-stu-id="d4cff-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="d4cff-184">Gérez ensuite le rappel DictationComplete :</span><span class="sxs-lookup"><span data-stu-id="d4cff-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="d4cff-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="d4cff-185">**DictationError**</span></span>

<span data-ttu-id="d4cff-186">Cet événement est déclenché lorsqu’une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="d4cff-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="d4cff-187">Tout d’abord, abonnez-vous à l' `DictationError` événement :</span><span class="sxs-lookup"><span data-stu-id="d4cff-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="d4cff-188">Gérez ensuite le rappel DictationError :</span><span class="sxs-lookup"><span data-stu-id="d4cff-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="d4cff-189">Une fois que vous avez souscrit et géré les événements de dictée qui vous intéressent, démarrez le module de reconnaissance de dictée pour commencer à recevoir des événements.</span><span class="sxs-lookup"><span data-stu-id="d4cff-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="d4cff-190">Si vous ne souhaitez plus conserver les DictationRecognizer, vous devez vous désabonner des événements et supprimer le DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="d4cff-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="d4cff-191">**Conseils**</span><span class="sxs-lookup"><span data-stu-id="d4cff-191">**Tips**</span></span>
* <span data-ttu-id="d4cff-192">`Start()` et les `Stop()` méthodes activent et désactivent respectivement la reconnaissance de la dictée.</span><span class="sxs-lookup"><span data-stu-id="d4cff-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="d4cff-193">Une fois le module de reconnaissance terminé, il doit être supprimé à l’aide `Dispose()` de pour libérer les ressources qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="d4cff-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="d4cff-194">Les ressources seront libérées automatiquement pendant la garbage collection à un coût de performances supplémentaire si elles ne sont pas libérées avant cela.</span><span class="sxs-lookup"><span data-stu-id="d4cff-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="d4cff-195">Les délais d’attente se produisent après un laps de temps défini.</span><span class="sxs-lookup"><span data-stu-id="d4cff-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="d4cff-196">Vous pouvez vérifier ces délais d’attente dans l' `DictationComplete` événement.</span><span class="sxs-lookup"><span data-stu-id="d4cff-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="d4cff-197">Deux délais d’attente doivent être pris en compte :</span><span class="sxs-lookup"><span data-stu-id="d4cff-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="d4cff-198">Si le module de reconnaissance démarre et n’entend aucun audio pendant les cinq premières secondes, il expire.</span><span class="sxs-lookup"><span data-stu-id="d4cff-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="d4cff-199">Si le module de reconnaissance a donné un résultat, mais émet un silence pendant 20 secondes, il expire.</span><span class="sxs-lookup"><span data-stu-id="d4cff-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="d4cff-200">Utilisation de la reconnaissance et de la dictée des expressions</span><span class="sxs-lookup"><span data-stu-id="d4cff-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="d4cff-201">Si vous souhaitez utiliser la reconnaissance d’expression et la dictée dans votre application, vous devez l’arrêter complètement avant de pouvoir démarrer l’autre.</span><span class="sxs-lookup"><span data-stu-id="d4cff-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="d4cff-202">Si vous avez plusieurs KeywordRecognizers en cours d’exécution, vous pouvez les arrêter en même temps avec :</span><span class="sxs-lookup"><span data-stu-id="d4cff-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="d4cff-203">Vous pouvez appeler `Restart()` pour restaurer tous les reconnaisseurs à leur état précédent après l’arrêt du DictationRecognizer :</span><span class="sxs-lookup"><span data-stu-id="d4cff-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="d4cff-204">Vous pouvez aussi simplement démarrer un KeywordRecognizer, qui redémarrera également le PhraseRecognitionSystem.</span><span class="sxs-lookup"><span data-stu-id="d4cff-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="d4cff-205">Entrée vocale dans le Toolkit de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="d4cff-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="d4cff-206">Vous trouverez des exemples MRTK pour une entrée vocale dans les scènes de démonstration suivantes :</span><span class="sxs-lookup"><span data-stu-id="d4cff-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="d4cff-207">Dictée</span><span class="sxs-lookup"><span data-stu-id="d4cff-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="d4cff-208">Speech</span><span class="sxs-lookup"><span data-stu-id="d4cff-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="d4cff-209">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="d4cff-209">Next Development Checkpoint</span></span>

<span data-ttu-id="d4cff-210">Si vous suivez le parcours du point de contrôle de développement Unity que nous avons disposé, vous allez maintenant découvrir les API et les fonctionnalités de la plateforme de réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="d4cff-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4cff-211">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="d4cff-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="d4cff-212">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="d4cff-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>