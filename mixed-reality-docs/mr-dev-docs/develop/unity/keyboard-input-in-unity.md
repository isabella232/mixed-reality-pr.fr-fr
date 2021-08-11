---
title: Saisie au clavier dans Unity
description: Unity fournit la classe TouchScreenKeyboard pour accepter l’entrée au clavier quand aucun clavier physique n’est disponible.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: clavier, entrée, unity, touchscreenkeyboard, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, HoloLens, HoloLens 2
ms.openlocfilehash: a7bd392036ca548fdd1f25581c8fc1910308909253f9c8df763e2039a32d3e9a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203851"
---
# <a name="keyboard-input-in-unity"></a>Saisie au clavier dans Unity

**Espace de noms :** *UnityEngine*<br>
 **Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

même si HoloLens prend en charge de nombreuses formes d’entrée, y compris les claviers Bluetooth, la plupart des applications ne peuvent pas supposer que tous les utilisateurs disposent d’un clavier physique disponible. Si votre application nécessite une entrée de texte, une forme de clavier à l’écran doit être fournie.

Unity fournit la classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* pour accepter l’entrée au clavier quand aucun clavier physique n’est disponible.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>HoloLens le comportement du clavier système dans unity

sur HoloLens, *TouchScreenKeyboard* utilise le clavier visuel du système et se superpose directement sur la vue volumétrique de votre application MR. L’expérience est similaire à l’utilisation du clavier dans les applications intégrées de HoloLens. notez que le clavier système se comportera en fonction des capacités de la plateforme cible, par exemple le clavier sur HoloLens 2 prendre en charge les interactions directes, tandis que le clavier sur HoloLens (1ère génération) prendra en charge GGV (point de vue, geste et voix). En outre, le clavier système n’apparaît pas lors de l’exécution de la communication à distance Unity à partir de l’éditeur vers un HoloLens.

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
> [déployez sur HoloLens ou Windows Mixed Reality des casques immersifs](../platform-capabilities-and-apis/using-visual-studio.md)
