---
title: Exemples d’interaction manuelle
description: Exemples d’interaction manuelle dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, la réalité mixte, le développement, MRTK, les Interactions main, le contrôle des limites, les boutons enfoncés,
ms.openlocfilehash: 7926c8bdd525af24a26e2f4c87257dca7628956a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177440"
---
# <a name="hand-interaction-examples"></a><span data-ttu-id="82a50-104">Exemples d’interaction manuelle</span><span class="sxs-lookup"><span data-stu-id="82a50-104">Hand interaction examples</span></span>

![Exemples d’interaction manuelle 1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="82a50-106">L’exemple de scène **HandInteractionExamples** contient différents types d’interactions et de contrôles d’interface utilisateur qui mettent en évidence une entrée articulée.</span><span class="sxs-lookup"><span data-stu-id="82a50-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="82a50-107">Avec la simulation d’entrée de MRTK, vous pouvez expérimenter les interactions de suivi des mains dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="82a50-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="82a50-108">**HandInteractionExamples** Scene est inclus dans le package d’exemples de MRTK.</span><span class="sxs-lookup"><span data-stu-id="82a50-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="82a50-109">vous pouvez télécharger et importer une **réalité mixte Shared Computer Toolkit exemples** de package à l’aide de l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="82a50-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="82a50-110">dans unity, utilisez la fenêtre de menu > Gestionnaire de package > dans Project > personnalisée, puis sélectionnez **exemples de réalité mixte Shared Computer Toolkit**.</span><span class="sxs-lookup"><span data-stu-id="82a50-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="82a50-111">cliquez sur **importer dans Project** bouton en regard de **démonstrations-HandTracking**.</span><span class="sxs-lookup"><span data-stu-id="82a50-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="82a50-112">Vous pouvez trouver **HandInteractionExamples** Scene sous actifs > dossier Samples.</span><span class="sxs-lookup"><span data-stu-id="82a50-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="82a50-113">si vous n’utilisez pas l’outil de fonctionnalité de réalité mixte, vous pouvez télécharger et importer directement **Microsoft. MixedReality. Shared Computer Toolkit. unity. examples. pour unity** à partir de [la page de version de MRTK GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="82a50-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="82a50-114">Cet exemple de scène utilise *TextMesh Pro*.</span><span class="sxs-lookup"><span data-stu-id="82a50-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="82a50-115">Pour ouvrir la scène, cliquez sur *« Importer tmp Essentials »* lorsque l’invite correspondante s’affiche lors de l’importation de la scène.</span><span class="sxs-lookup"><span data-stu-id="82a50-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="82a50-116">unity importera ensuite les packages Pro TextMesh.</span><span class="sxs-lookup"><span data-stu-id="82a50-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="82a50-117">Vous pouvez rencontrer ces composants dans **HandInteractionExamples** Scene</span><span class="sxs-lookup"><span data-stu-id="82a50-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="82a50-118">Bouton sur lequel appuyer</span><span class="sxs-lookup"><span data-stu-id="82a50-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="82a50-119">Contrôle de limites</span><span class="sxs-lookup"><span data-stu-id="82a50-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="82a50-120">Manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="82a50-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="82a50-121">Tablette</span><span class="sxs-lookup"><span data-stu-id="82a50-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="82a50-122">Curseur</span><span class="sxs-lookup"><span data-stu-id="82a50-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="82a50-123">Clavier système</span><span class="sxs-lookup"><span data-stu-id="82a50-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
