---
title: Clavier système
description: Vue d’ensemble du tableau des clés système dans MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, clavier système,
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176493"
---
# <a name="system-keyboard"></a><span data-ttu-id="3ad4d-104">Clavier système</span><span class="sxs-lookup"><span data-stu-id="3ad4d-104">System keyboard</span></span>

![Clavier système](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="3ad4d-106">Une application Unity peut appeler le clavier système à tout moment.</span><span class="sxs-lookup"><span data-stu-id="3ad4d-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="3ad4d-107">notez que le clavier système se comportera en fonction des capacités de la plateforme cible, par exemple le clavier sur HoloLens 2 prendre en charge les interactions directes, tandis que le clavier sur HoloLens (1ère génération) prendra en charge GGV (point de vue, geste et voix)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="3ad4d-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="3ad4d-108">En outre, le clavier système n’apparaît pas lors de l’exécution de la [communication à distance Unity](../tools/holographic-remoting.md) à partir de l’éditeur vers un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ad4d-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="3ad4d-109">Comment appeler le clavier système</span><span class="sxs-lookup"><span data-stu-id="3ad4d-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="3ad4d-110">Comment lire l’entrée</span><span class="sxs-lookup"><span data-stu-id="3ad4d-110">How to read the input</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a><span data-ttu-id="3ad4d-111">Exemple de clavier système</span><span class="sxs-lookup"><span data-stu-id="3ad4d-111">System keyboard example</span></span>

<span data-ttu-id="3ad4d-112">Vous pouvez voir un exemple simple d’utilisation du clavier système dans `MixedRealityKeyboard.cs` (ressources/MRTK/SDK/expérimental/features/UX/MixedRealityKeyboard. cs)</span><span class="sxs-lookup"><span data-stu-id="3ad4d-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="3ad4d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ad4d-113">See Also</span></span>

- [<span data-ttu-id="3ad4d-114">Classes d’assistance du clavier de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="3ad4d-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
