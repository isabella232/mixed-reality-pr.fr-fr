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
# <a name="system-keyboard"></a>Clavier système

![Clavier système](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Une application Unity peut appeler le clavier système à tout moment. notez que le clavier système se comportera en fonction des capacités de la plateforme cible, par exemple le clavier sur HoloLens 2 prendre en charge les interactions directes, tandis que le clavier sur HoloLens (1ère génération) prendra en charge GGV (point de vue, geste et voix)<sup>[1](/windows/mixed-reality/gaze)</sup>. En outre, le clavier système n’apparaît pas lors de l’exécution de la [communication à distance Unity](../tools/holographic-remoting.md) à partir de l’éditeur vers un HoloLens.

## <a name="how-to-invoke-the-system-keyboard"></a>Comment appeler le clavier système

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a>Comment lire l’entrée

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

## <a name="system-keyboard-example"></a>Exemple de clavier système

Vous pouvez voir un exemple simple d’utilisation du clavier système dans `MixedRealityKeyboard.cs` (ressources/MRTK/SDK/expérimental/features/UX/MixedRealityKeyboard. cs)

## <a name="see-also"></a>Voir aussi

- [Classes d’assistance du clavier de réalité mixte](../experimental/mixed-reality-keyboard.md)
