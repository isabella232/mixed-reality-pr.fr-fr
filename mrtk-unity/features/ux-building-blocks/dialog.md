---
title: Boîte de dialogue
description: Description pour les contrôles de boîte de dialogue.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489189"
---
# <a name="dialog"></a><span data-ttu-id="0c900-104">Boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="0c900-104">Dialog</span></span>

![Boîte de dialogue](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="0c900-106">Les contrôles Dialog sont des superpositions d’interface utilisateur qui fournissent des informations d’application contextuelles.</span><span class="sxs-lookup"><span data-stu-id="0c900-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="0c900-107">Elles exigent souvent une forme d’action de la part de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0c900-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="0c900-108">Utilisez les boîtes de dialogue pour notifier les utilisateurs d’informations importantes ou pour demander une confirmation ou des informations supplémentaires avant de pouvoir effectuer une action.</span><span class="sxs-lookup"><span data-stu-id="0c900-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="0c900-109">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="0c900-109">Example scene</span></span>

<span data-ttu-id="0c900-110">Vous trouverez des exemples dans la scène **DialogExample** sous : [MRTK/examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span><span class="sxs-lookup"><span data-stu-id="0c900-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="0c900-111">Comment utiliser le contrôle Dialog</span><span class="sxs-lookup"><span data-stu-id="0c900-111">How to use Dialog control</span></span>

<span data-ttu-id="0c900-112">MRTK fournit trois prefabs de dialogue :</span><span class="sxs-lookup"><span data-stu-id="0c900-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="0c900-113">DialogSmall_192x96. Prefab</span><span class="sxs-lookup"><span data-stu-id="0c900-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="0c900-114">DialogMedium_192x128. Prefab</span><span class="sxs-lookup"><span data-stu-id="0c900-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="0c900-115">DialogLarge_192x192. Prefab</span><span class="sxs-lookup"><span data-stu-id="0c900-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="0c900-116">Utilisez la boîte de dialogue. Open () pour ouvrir une nouvelle boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0c900-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="0c900-117">Spécifiez la boîte de dialogue Prefab, le nombre de boutons, le texte du titre, le texte du message, la distance de positionnement (proche ou loin), les variables supplémentaires).</span><span class="sxs-lookup"><span data-stu-id="0c900-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="0c900-118">La boîte de dialogue fournit les options de la boîte de dialogue confirmation (bouton unique) et choix (deux boutons).</span><span class="sxs-lookup"><span data-stu-id="0c900-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="0c900-119">Exemple d’ouverture d’une boîte de dialogue de grande taille avec un seul bouton « OK », placé à une plage d’interaction éloignée (le regard, le rayon de la main, le contrôleur de mouvement)</span><span class="sxs-lookup"><span data-stu-id="0c900-119">Example of opening a Large dialog with a single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="0c900-120">Exemple d’ouverture d’une petite boîte de dialogue contenant un message de choix pour l’utilisateur, placée à proximité de la plage d’interactions (interaction directe)</span><span class="sxs-lookup"><span data-stu-id="0c900-120">Example of opening a Small dialog containing a choice message for the user, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="0c900-121">Pour plus d’informations, consultez `DialogExampleController.cs` dans la scène DialogExample. Unity.</span><span class="sxs-lookup"><span data-stu-id="0c900-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>
