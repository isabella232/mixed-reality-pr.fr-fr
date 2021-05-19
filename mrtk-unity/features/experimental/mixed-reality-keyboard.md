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
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="7a766-104">Classes d’aide au clavier de la réalité mixte et du clavier HoloLens</span><span class="sxs-lookup"><span data-stu-id="7a766-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="7a766-105">MRTK fournit plusieurs composants d’assistance expérimentales pour vous aider à lancer et à lire du texte à partir du [clavier système](../ux-building-blocks/system-keyboard.md).</span><span class="sxs-lookup"><span data-stu-id="7a766-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="7a766-106">Notez que le clavier système se comportera conformément aux fonctionnalités de la plateforme cible, par exemple le clavier sur HoloLens 2 prend en charge les interactions directes, tandis que le clavier sur HoloLens (1re génération) prendra en charge GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="7a766-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="7a766-107">En outre, le clavier système n’apparaît pas lors de l’exécution de la [communication à distance Unity](../tools/holographic-remoting.md) à partir de l’éditeur vers HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7a766-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="7a766-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="7a766-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="7a766-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) est un composant qui fournit des méthodes pour lancer et fermer un clavier système, ainsi que pour interagir avec le texte entré par le clavier.</span><span class="sxs-lookup"><span data-stu-id="7a766-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="7a766-110">Utilisation</span><span class="sxs-lookup"><span data-stu-id="7a766-110">How to Use</span></span>

1. <span data-ttu-id="7a766-111">Attachez le [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) composant à n’importe quel objet.</span><span class="sxs-lookup"><span data-stu-id="7a766-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="7a766-112">Appelez `Show()` `Hide()` pour afficher et masquer le clavier, et pour gérer `OnShowKeyboard` les `OnHideKeyboard` événements, et `OnCommitText` à gérer lorsque le clavier est affiché, masqué et lorsque la touche entrée est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="7a766-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="7a766-113">Champs d’entrée TMP_KeyboardInputField et UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="7a766-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="7a766-114">Les [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes et sont des composants qui peuvent être ajoutés aux champs d’entrée de texte pour appeler automatiquement le clavier système lorsque l’utilisateur clique dessus et mettre à jour le contenu du champ d’entrée de texte à mesure que l’utilisateur entre du texte.</span><span class="sxs-lookup"><span data-stu-id="7a766-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="7a766-115">Procédure d'utilisation</span><span class="sxs-lookup"><span data-stu-id="7a766-115">How to use</span></span>

1. <span data-ttu-id="7a766-116">Créez un champ d’entrée pour UnityUI ou TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="7a766-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="7a766-117">Ajoutez le [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) composant ou correspondant [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) à l’objet de jeu de champs d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7a766-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="7a766-118">Prefabs pour les champs d’entrée UnityUI et les champs d’entrée TextMeshPro (TMPro) sont disponibles à l’adresse « Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs »</span><span class="sxs-lookup"><span data-stu-id="7a766-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="7a766-119">Voici un exemple de la façon dont le pour utiliser TMP_KeyboardInputField et UI_KeyboardInputField se trouve à l’adresse « Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity »</span><span class="sxs-lookup"><span data-stu-id="7a766-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>