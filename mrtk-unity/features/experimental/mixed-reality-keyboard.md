---
title: Clavier de réalité mixte
description: Description de l’utilisation du clavier de réalité mixte
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143398"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Classes d’aide au clavier de la réalité mixte et du clavier HoloLens

MRTK fournit plusieurs composants d’assistance expérimentales pour vous aider à lancer et à lire du texte à partir du [clavier système](../ux-building-blocks/system-keyboard.md).

Notez que le clavier système se comportera conformément aux fonctionnalités de la plateforme cible, par exemple le clavier sur HoloLens 2 prend en charge les interactions directes, tandis que le clavier sur HoloLens (1re génération) prendra en charge GGV<sup>[1](/windows/mixed-reality/gaze)</sup>. En outre, le clavier système n’apparaît pas lors de l’exécution de la [communication à distance Unity](../tools/holographic-remoting.md) à partir de l’éditeur vers HoloLens.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) est un composant qui fournit des méthodes pour lancer et fermer un clavier système, ainsi que pour interagir avec le texte entré par le clavier.  

### <a name="how-to-use"></a>Utilisation

1. Attachez le [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) composant à n’importe quel objet.
2. Appelez `Show()` `Hide()` pour afficher et masquer le clavier, et pour gérer `OnShowKeyboard` les `OnHideKeyboard` événements, et `OnCommitText` à gérer lorsque le clavier est affiché, masqué et lorsque la touche entrée est enfoncée.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Champs d’entrée TMP_KeyboardInputField et UI_KeyboardInputField

Les [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes et sont des composants qui peuvent être ajoutés aux champs d’entrée de texte pour appeler automatiquement le clavier système lorsque l’utilisateur clique dessus et mettre à jour le contenu du champ d’entrée de texte à mesure que l’utilisateur entre du texte.

### <a name="how-to-use"></a>Procédure d'utilisation

1. Créez un champ d’entrée pour UnityUI ou TextMeshPro.
2. Ajoutez le [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) composant ou correspondant [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) à l’objet de jeu de champs d’entrée.

Prefabs pour les champs d’entrée UnityUI et les champs d’entrée TextMeshPro (TMPro) sont disponibles à l’adresse « Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs »

Voici un exemple de la façon dont le pour utiliser TMP_KeyboardInputField et UI_KeyboardInputField se trouve à l’adresse « Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity »