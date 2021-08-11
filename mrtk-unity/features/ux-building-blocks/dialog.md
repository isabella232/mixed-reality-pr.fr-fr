---
title: Boîte de dialogue
description: Description pour les contrôles de boîte de dialogue.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 5d63fcfe79a1c3b09c78f435cec3c2155b403795993f46628cf0f5743bfd42a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203674"
---
# <a name="dialog"></a>Boîte de dialogue

![Boîte de dialogue](../images/dialog/MRTK_UX_Dialog_Main.png)

Les contrôles Dialog sont des superpositions d’interface utilisateur qui fournissent des informations d’application contextuelles. Elles exigent souvent une forme d’action de la part de l’utilisateur. Utilisez les boîtes de dialogue pour notifier les utilisateurs d’informations importantes ou pour demander une confirmation ou des informations supplémentaires avant de pouvoir effectuer une action.

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples dans la scène **DialogExample** sous : [MRTK/examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Comment utiliser le contrôle Dialog

MRTK fournit trois prefabs de dialogue :

- DialogSmall_192x96. Prefab
- DialogMedium_192x128. Prefab
- DialogLarge_192x192. Prefab

Utilisez la boîte de dialogue. Open () pour ouvrir une nouvelle boîte de dialogue. Spécifiez la boîte de dialogue Prefab, le nombre de boutons, le texte du titre, le texte du message, la distance de positionnement (proche ou loin), les variables supplémentaires). La boîte de dialogue fournit les options de la boîte de dialogue confirmation (bouton unique) et choix (deux boutons).

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Exemple d’ouverture d’une boîte de dialogue de grande taille avec un seul bouton « OK », placé à une plage d’interaction éloignée (le regard, le rayon de la main, le contrôleur de mouvement)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>Exemple d’ouverture d’une petite boîte de dialogue contenant un message de choix pour l’utilisateur, placée à proximité de la plage d’interactions (interaction directe)

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Pour plus d’informations, consultez `DialogExampleController.cs` dans la scène DialogExample. Unity.
