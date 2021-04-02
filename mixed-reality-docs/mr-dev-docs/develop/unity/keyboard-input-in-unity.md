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
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="b8f1a-104">Saisie au clavier dans Unity</span><span class="sxs-lookup"><span data-stu-id="b8f1a-104">Keyboard input in Unity</span></span>

<span data-ttu-id="b8f1a-105">**Espace de noms :** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="b8f1a-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="b8f1a-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="b8f1a-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="b8f1a-107">Alors que HoloLens prend en charge de nombreuses formes d’entrée, y compris les claviers Bluetooth, la plupart des applications ne peuvent pas supposer que tous les utilisateurs disposent d’un clavier physique disponible.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="b8f1a-108">Si votre application nécessite une entrée de texte, une forme de clavier à l’écran doit être fournie.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="b8f1a-109">Unity fournit la classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* pour accepter l’entrée au clavier quand aucun clavier physique n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="b8f1a-110">Comportement du clavier du système HoloLens dans Unity</span><span class="sxs-lookup"><span data-stu-id="b8f1a-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="b8f1a-111">Sur HoloLens, *TouchScreenKeyboard* utilise le clavier visuel du système et se superpose directement sur la vue volumétrique de votre application Mr.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="b8f1a-112">L’expérience est similaire à l’utilisation du clavier dans les applications intégrées de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="b8f1a-113">Notez que le clavier système se comportera conformément aux fonctionnalités de la plateforme cible, par exemple le clavier sur HoloLens 2 prend en charge les interactions directes, tandis que le clavier sur HoloLens (1re génération) prendra en charge GGV (point de vue, geste et voix).</span><span class="sxs-lookup"><span data-stu-id="b8f1a-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="b8f1a-114">En outre, le clavier système n’apparaît pas lors de l’exécution de la communication à distance Unity à partir de l’éditeur vers HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="b8f1a-115">Utilisation du clavier système dans votre application Unity</span><span class="sxs-lookup"><span data-stu-id="b8f1a-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="b8f1a-116">Déclarer le clavier</span><span class="sxs-lookup"><span data-stu-id="b8f1a-116">Declare the keyboard</span></span>

<span data-ttu-id="b8f1a-117">Dans la classe, déclarez une variable pour stocker le *TouchScreenKeyboard* et une variable qui contiendra la chaîne retournée par le clavier.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="b8f1a-118">Appeler le clavier</span><span class="sxs-lookup"><span data-stu-id="b8f1a-118">Invoke the keyboard</span></span>

<span data-ttu-id="b8f1a-119">Lorsqu’un événement se produit en demandant une entrée au clavier, utilisez ce qui suit pour afficher le clavier.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="b8f1a-120">Vous pouvez utiliser des paramètres supplémentaires passés `TouchScreenKeyboard.Open` à la fonction pour contrôler le comportement du clavier (par exemple, définir le texte de l’espace réservé ou prendre en charge la correction automatique).</span><span class="sxs-lookup"><span data-stu-id="b8f1a-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="b8f1a-121">Pour obtenir la liste complète des paramètres, reportez-vous à la [documentation de Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span><span class="sxs-lookup"><span data-stu-id="b8f1a-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="b8f1a-122">Récupérer le contenu typé</span><span class="sxs-lookup"><span data-stu-id="b8f1a-122">Retrieve typed contents</span></span>

<span data-ttu-id="b8f1a-123">Le contenu peut simplement être récupéré en appelant `keyboard.text` .</span><span class="sxs-lookup"><span data-stu-id="b8f1a-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="b8f1a-124">Vous pouvez récupérer le contenu par trame ou uniquement lorsque le clavier est fermé.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="b8f1a-125">Autres options de clavier</span><span class="sxs-lookup"><span data-stu-id="b8f1a-125">Alternative keyboard options</span></span>

<span data-ttu-id="b8f1a-126">Outre l’utilisation directe de la classe *TouchScreenKeyboard* , vous pouvez également récupérer l’entrée d’utilisateur à l’aide du champ d' *entrée UI* ou *TextMeshPro* du champ d’entrée d’Unity.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="b8f1a-127">En outre, il existe une implémentation basée sur *TouchScreenKeyboard* dans la [scène HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) de [MRTK](/windows/mixed-reality/mrtk-unity) (un exemple d’interaction du clavier est présent sur le côté gauche).</span><span class="sxs-lookup"><span data-stu-id="b8f1a-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b8f1a-128">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="b8f1a-128">Next Development Checkpoint</span></span>

<span data-ttu-id="b8f1a-129">Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des fonctionnalités de la plateforme de réalité mixte et des API.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="b8f1a-130">À partir de là, vous pouvez accéder à n’importe quelle [rubrique](unity-development-overview.md#3-advanced-features) ou passer directement au déploiement de votre application sur un appareil ou un émulateur.</span><span class="sxs-lookup"><span data-stu-id="b8f1a-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8f1a-131">Déployer sur HoloLens ou sur des casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b8f1a-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
