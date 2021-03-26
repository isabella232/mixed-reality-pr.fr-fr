---
title: Entrée vocale dans Unity
description: Découvrez comment Unity expose trois façons d’ajouter une entrée vocale, une reconnaissance vocale et une dictée à votre application Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrée vocale, KeywordRecognizer, GrammarRecognizer, microphone, dictée, voix, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: c062289a1a26365528a86761b6b68a9a24041f7c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550379"
---
# <a name="voice-input-in-unity"></a>Entrée vocale dans Unity

> [!CAUTION]
> Avant de commencer, envisagez d’utiliser le plug-in Unity pour le kit de développement logiciel (SDK) cognitive Speech services. Le plug-in offre de meilleurs résultats de précision vocale et un accès facile au décodage vocal en texte, ainsi que des fonctionnalités vocales avancées telles que la boîte de dialogue, l’interaction fondée sur l’intention, la traduction, la synthèse vocale et la reconnaissance vocale en langage naturel. Pour commencer, consultez l' [exemple et la documentation](/azure/cognitive-services/speech-service/quickstart-csharp-unity).

Unity expose trois façons d’ajouter une [entrée vocale](../../design/voice-input.md) à votre application Unity, les deux premières étant des types de PhraseRecognizer :
* Le `KeywordRecognizer` fournit à votre application un tableau de commandes de chaîne à écouter.
* Le `GrammarRecognizer` donne à votre application un fichier SRGS définissant une grammaire spécifique à écouter
* Le `DictationRecognizer` permet à votre application d’écouter tout mot et de fournir à l’utilisateur une note ou un autre affichage de sa parole.

> [!NOTE]
> La reconnaissance de la dictée et de l’expression ne peut pas être gérée en même temps. Si un GrammarRecognizer ou un KeywordRecognizer est actif, un DictationRecognizer ne peut pas être actif et vice versa.

## <a name="enabling-the-capability-for-voice"></a>Activation de la fonctionnalité de voix

La fonctionnalité **microphone** doit être déclarée pour qu’une application utilise l’entrée vocale.
1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet > Player**
2. Sélectionner l’onglet **Windows Store**
3. Dans la section **paramètres de publication > fonctionnalités** , vérifiez la fonctionnalité du **microphone** .
4. Accorder des autorisations à l’application pour l’accès au microphone sur votre appareil HoloLens
    * Vous êtes invité à le faire au démarrage de l’appareil, mais si vous avez cliqué accidentellement sur « non », vous pouvez modifier les autorisations dans les paramètres de l’appareil.

## <a name="phrase-recognition"></a>Reconnaissance d’expressions

Pour permettre à votre application d’écouter des expressions spécifiques parlées par l’utilisateur, puis de prendre des mesures, vous devez :
1. Spécifiez les expressions à écouter à l’aide d’un `KeywordRecognizer` ou `GrammarRecognizer`
2. Gérer l' `OnPhraseRecognized` événement et entreprendre une action correspondant à l’expression reconnue

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Espace de noms :** *UnityEngine. Windows. Speech*<br>
**Types :** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Nous aurons besoin de quelques instructions d’utilisation pour enregistrer des séquences de touches :

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Nous allons ensuite ajouter quelques champs à votre classe pour stocker le module de reconnaissance et de mot clé->dictionnaire d’actions :

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Ajoutez maintenant un mot clé au dictionnaire, par exemple dans une `Start()` méthode. Nous ajoutons le mot clé « Activate » dans cet exemple :

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Créez le module de reconnaissance de mot clé et dites-lui ce que nous souhaitons reconnaître :

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Inscrivez-vous maintenant pour l' `OnPhraseRecognized` événement

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Voici un exemple de gestionnaire :

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

Enfin, commencez à reconnaître !

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Espace de noms :** *UnityEngine. Windows. Speech*<br>
**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Le GrammarRecognizer est utilisé si vous spécifiez votre grammaire de reconnaissance à l’aide de SRGS. Cela peut être utile si votre application contient plus de seulement quelques mots-clés, si vous souhaitez reconnaître des expressions plus complexes ou si vous souhaitez facilement activer et désactiver des ensembles de commandes. Voir : [créer des grammaires à l’aide de SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) pour les informations de format de fichier.

Une fois que vous disposez de la grammaire SRGS et que celle-ci se trouve dans votre projet dans un [dossier StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Créez un `GrammarRecognizer` et transmettez-lui le chemin d’accès à votre fichier SRGS :

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Inscrivez-vous maintenant pour l' `OnPhraseRecognized` événement

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Vous obtenez un rappel contenant les informations spécifiées dans votre syntaxe SRGS, que vous pouvez gérer de manière appropriée. La plupart des informations importantes seront fournies dans le `semanticMeanings` tableau.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Enfin, commencez à reconnaître !

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Dictation

**Espace de noms :** *UnityEngine. Windows. Speech*<br>
**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Utilisez le `DictationRecognizer` pour convertir la parole de l’utilisateur en texte. Le DictationRecognizer expose les fonctionnalités de [dictée](../../design/voice-input.md#dictation) et prend en charge l’inscription et l’écoute des événements d’hypothèse et d’expression terminés, ce qui vous permet de fournir des commentaires à l’utilisateur pendant qu’il parle et par la suite. `Start()` et les `Stop()` méthodes activent et désactivent respectivement la reconnaissance de la dictée. Une fois le module de reconnaissance terminé, il doit être supprimé à l’aide `Dispose()` de pour libérer les ressources qu’il utilise. Les ressources seront libérées automatiquement pendant la garbage collection à un coût de performances supplémentaire si elles ne sont pas libérées avant cela.

Il n’y a que quelques étapes nécessaires pour commencer à utiliser la dictée :
1. Créer un nouveau `DictationRecognizer`
2. Gérer les événements de dictée
3. Démarrer le DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Activation de la fonctionnalité de dictée

Les fonctionnalités du client et du **microphone** **Internet** doivent être déclarées pour qu’une application utilise la dictée :
1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet > Player**
2. Sélectionner sous l’onglet **Windows Store**
3. Dans la section **paramètres de publication > fonctionnalités** , activez la fonctionnalité **internetclient**
    * Éventuellement, si vous n’avez pas déjà activé le microphone, vérifiez la fonctionnalité du **microphone** .
4. Accorder des autorisations à l’application pour l’accès au microphone sur votre appareil HoloLens si vous ne l’avez pas déjà fait
    * Vous êtes invité à le faire au démarrage de l’appareil, mais si vous avez cliqué accidentellement sur « non », vous pouvez modifier les autorisations dans les paramètres de l’appareil.

### <a name="dictationrecognizer"></a>DictationRecognizer

Créez un DictationRecognizer de la manière suivante :

```
dictationRecognizer = new DictationRecognizer();
```

Quatre événements de dictée peuvent être souscrits et gérés pour implémenter le comportement de la dictée.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

Cet événement est déclenché après la suspension de l’utilisateur, généralement à la fin d’une phrase. La chaîne complète reconnue est retournée ici.

Tout d’abord, abonnez-vous à l' `DictationResult` événement :

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Gérez ensuite le rappel DictationResult :

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Cet événement est déclenché en continu pendant que l’utilisateur parle. À mesure que le module de reconnaissance écoute, il fournit du texte sur ce qu’il est entendu jusqu’à présent.

Tout d’abord, abonnez-vous à l' `DictationHypothesis` événement :

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Gérez ensuite le rappel DictationHypothesis :

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Cet événement est déclenché lorsque le module de reconnaissance s’arrête, qu’il s’agisse de l’appel de Stop (), d’un délai d’attente ou d’une autre erreur.

Tout d’abord, abonnez-vous à l' `DictationComplete` événement :

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Gérez ensuite le rappel DictationComplete :

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Cet événement est déclenché lorsqu’une erreur se produit.

Tout d’abord, abonnez-vous à l' `DictationError` événement :

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Gérez ensuite le rappel DictationError :

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Une fois que vous avez souscrit et géré les événements de dictée qui vous intéressent, démarrez le module de reconnaissance de dictée pour commencer à recevoir des événements.

```
dictationRecognizer.Start();
```

Si vous ne souhaitez plus conserver les DictationRecognizer, vous devez vous désabonner des événements et supprimer le DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Conseils**
* `Start()` et les `Stop()` méthodes activent et désactivent respectivement la reconnaissance de la dictée.
* Une fois le module de reconnaissance terminé, il doit être supprimé à l’aide `Dispose()` de pour libérer les ressources qu’il utilise. Les ressources seront libérées automatiquement pendant la garbage collection à un coût de performances supplémentaire si elles ne sont pas libérées avant cela.
* Les délais d’attente se produisent après un laps de temps défini. Vous pouvez vérifier ces délais d’attente dans l' `DictationComplete` événement. Deux délais d’attente doivent être pris en compte :
   1. Si le module de reconnaissance démarre et n’entend aucun audio pendant les cinq premières secondes, il expire.
   2. Si le module de reconnaissance a donné un résultat, mais émet un silence pendant 20 secondes, il expire.

## <a name="using-both-phrase-recognition-and-dictation"></a>Utilisation de la reconnaissance et de la dictée des expressions

Si vous souhaitez utiliser la reconnaissance d’expression et la dictée dans votre application, vous devez l’arrêter complètement avant de pouvoir démarrer l’autre. Si vous avez plusieurs KeywordRecognizers en cours d’exécution, vous pouvez les arrêter en même temps avec :

```
PhraseRecognitionSystem.Shutdown();
```

Vous pouvez appeler `Restart()` pour restaurer tous les reconnaisseurs à leur état précédent après l’arrêt du DictationRecognizer :

```
PhraseRecognitionSystem.Restart();
```

Vous pouvez aussi simplement démarrer un KeywordRecognizer, qui redémarrera également le PhraseRecognitionSystem.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrée vocale dans le Toolkit de réalité mixte

Vous trouverez des exemples MRTK pour une entrée vocale dans les scènes de démonstration suivantes :
* [Dictée](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Speech](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement Unity que nous avons disposé, vous allez maintenant découvrir les API et les fonctionnalités de la plateforme de réalité mixte :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.