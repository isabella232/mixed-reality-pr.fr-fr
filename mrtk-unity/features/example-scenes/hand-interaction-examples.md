---
title: Exemples d’interaction des mains
description: Exemples d’interaction manuelle dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, interactions main, contrôle des limites, boutons enfoncés,
ms.openlocfilehash: 229933dfd2414e485da6c1a77a2ffb08c9982249
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908402"
---
# <a name="hand-interaction-examples-scene"></a><span data-ttu-id="52f15-104">Scène d’exemples d’interaction manuelle</span><span class="sxs-lookup"><span data-stu-id="52f15-104">Hand interaction examples scene</span></span>

![Exemples d’interaction manuelle 1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="52f15-106">L’exemple de scène **HandInteractionExamples** contient différents types d’interactions et de contrôles d’interface utilisateur qui mettent en évidence une entrée articulée.</span><span class="sxs-lookup"><span data-stu-id="52f15-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="52f15-107">Avec la simulation d’entrée de MRTK, vous pouvez expérimenter les interactions de suivi des mains dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="52f15-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="52f15-108">**HandInteractionExamples** Scene est inclus dans le package d’exemples de MRTK.</span><span class="sxs-lookup"><span data-stu-id="52f15-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="52f15-109">Vous pouvez télécharger et importer des exemples de package de la **boîte à outils de réalité mixte** via l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="52f15-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="52f15-110">Dans Unity, utilisez la fenêtre de menu > gestionnaire de package > dans Project > personnalisée, puis sélectionnez **exemples d’outils de réalité mixte**.</span><span class="sxs-lookup"><span data-stu-id="52f15-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="52f15-111">Cliquez sur le bouton **importer dans le projet** en regard de **démonstrations-HandTracking**.</span><span class="sxs-lookup"><span data-stu-id="52f15-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="52f15-112">Vous pouvez trouver **HandInteractionExamples** Scene sous actifs > dossier Samples.</span><span class="sxs-lookup"><span data-stu-id="52f15-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="52f15-113">Si vous n’utilisez pas l’outil de fonctionnalité de réalité mixte, vous pouvez télécharger et importer directement **Microsoft. MixedReality. Toolkit. Unity. examples. pour Unity** à partir de [la page de publication de MRTK GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="52f15-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="52f15-114">Cet exemple de scène utilise *TextMesh Pro*.</span><span class="sxs-lookup"><span data-stu-id="52f15-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="52f15-115">Pour ouvrir la scène, cliquez sur *« Importer tmp Essentials »* lorsque l’invite correspondante s’affiche lors de l’importation de la scène.</span><span class="sxs-lookup"><span data-stu-id="52f15-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="52f15-116">Unity va ensuite importer les packages TextMesh Pro.</span><span class="sxs-lookup"><span data-stu-id="52f15-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="52f15-117">Vous pouvez rencontrer ces composants dans **HandInteractionExamples** Scene</span><span class="sxs-lookup"><span data-stu-id="52f15-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="52f15-118">Bouton sur lequel appuyer</span><span class="sxs-lookup"><span data-stu-id="52f15-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="52f15-119">Contrôle de limites</span><span class="sxs-lookup"><span data-stu-id="52f15-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="52f15-120">Manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="52f15-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="52f15-121">Tablette</span><span class="sxs-lookup"><span data-stu-id="52f15-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="52f15-122">Curseur</span><span class="sxs-lookup"><span data-stu-id="52f15-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="52f15-123">Clavier système</span><span class="sxs-lookup"><span data-stu-id="52f15-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
