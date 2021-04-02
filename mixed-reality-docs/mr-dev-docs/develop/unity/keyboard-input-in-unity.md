---
title: Saisie au clavier dans Unity
description: Unity fournit la classe TouchScreenKeyboard pour accepter l’entrée au clavier quand aucun clavier physique n’est disponible.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: clavier, entrée, Unity, touchscreenkeyboard, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, HoloLens, HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098271"
---
# <a name="keyboard-input-in-unity"></a>Saisie au clavier dans Unity

**Espace de noms :** *UnityEngine*<br>
 **Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Alors que HoloLens prend en charge de nombreuses formes d’entrée, y compris les claviers Bluetooth, la plupart des applications ne peuvent pas supposer que tous les utilisateurs disposent d’un clavier physique disponible. Si votre application nécessite une entrée de texte, une forme de clavier à l’écran doit être fournie.

Unity fournit la classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* pour accepter l’entrée au clavier quand aucun clavier physique n’est disponible.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportement du clavier du système HoloLens dans Unity

Sur HoloLens, *TouchScreenKeyboard* utilise le clavier visuel du système et se superpose directement sur la vue volumétrique de votre application Mr. L’expérience est similaire à l’utilisation du clavier dans les applications intégrées de HoloLens. Notez que le clavier système se comportera conformément aux fonctionnalités de la plateforme cible, par exemple le clavier sur HoloLens 2 prend en charge les interactions directes, tandis que le clavier sur HoloLens (1re génération) prendra en charge GGV (point de vue, geste et voix). En outre, le clavier système n’apparaît pas lors de l’exécution de la communication à distance Unity à partir de l’éditeur vers HoloLens.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Utilisation du clavier système dans votre application Unity

### <a name="declare-the-keyboard"></a>Déclarer le clavier

Dans la classe, déclarez une variable pour stocker le *TouchScreenKeyboard* et une variable qui contiendra la chaîne retournée par le clavier.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Appeler le clavier

Lorsqu’un événement se produit en demandant une entrée au clavier, utilisez ce qui suit pour afficher le clavier.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

Vous pouvez utiliser des paramètres supplémentaires passés `TouchScreenKeyboard.Open` à la fonction pour contrôler le comportement du clavier (par exemple, définir le texte de l’espace réservé ou prendre en charge la correction automatique). Pour obtenir la liste complète des paramètres, reportez-vous à la [documentation de Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).

### <a name="retrieve-typed-contents"></a>Récupérer le contenu typé

Le contenu peut simplement être récupéré en appelant `keyboard.text` . Vous pouvez récupérer le contenu par trame ou uniquement lorsque le clavier est fermé.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Autres options de clavier

Outre l’utilisation directe de la classe *TouchScreenKeyboard* , vous pouvez également récupérer l’entrée d’utilisateur à l’aide du champ d' *entrée UI* ou *TextMeshPro* du champ d’entrée d’Unity. En outre, il existe une implémentation basée sur *TouchScreenKeyboard* dans la [scène HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) de [MRTK](/windows/mixed-reality/mrtk-unity) (un exemple d’interaction du clavier est présent sur le côté gauche).

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des fonctionnalités de la plateforme de réalité mixte et des API. À partir de là, vous pouvez accéder à n’importe quelle [rubrique](unity-development-overview.md#3-advanced-features) ou passer directement au déploiement de votre application sur un appareil ou un émulateur.

> [!div class="nextstepaction"]
> [Déployer sur HoloLens ou sur des casques immersifs Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
