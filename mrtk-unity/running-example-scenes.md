---
title: Exemples de scènes
description: Découvrez comment acquérir et utiliser des exemples de scènes MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: boîte à outils de réalité mixte, MRTK, exemples, HoloLens, HoloLens 2, nuanceurs, info-bulles, interaction main, découpage, zones englobantes, boutons, menus main, ardoise, curseur
ms.openlocfilehash: d8d2bb40ff1c95e01cb051f36de04beb93829ba1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177477"
---
# <a name="example-scenes"></a><span data-ttu-id="e0047-104">Exemples de scènes</span><span class="sxs-lookup"><span data-stu-id="e0047-104">Example scenes</span></span>

<span data-ttu-id="e0047-105">MRTK fournit différents types d’exemples de scènes qui illustrent les fonctionnalités de MRTK et les blocs de construction pour l’expérience utilisateur spatial.</span><span class="sxs-lookup"><span data-stu-id="e0047-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="e0047-106">Des exemples de scènes de rencontre et de discernement peuvent être utiles pour comprendre les fonctionnalités et les appliquer à vos projets.</span><span class="sxs-lookup"><span data-stu-id="e0047-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="e0047-107">Comment acquérir des exemples de scènes</span><span class="sxs-lookup"><span data-stu-id="e0047-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="e0047-108">Utilisation de l’outil de fonctionnalité de réalité mixte et du gestionnaire de packages Unity</span><span class="sxs-lookup"><span data-stu-id="e0047-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="e0047-109">vous pouvez télécharger et importer une **réalité mixte Shared Computer Toolkit exemples** de package à l’aide de l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="e0047-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="e0047-110">dans unity, utilisez la **fenêtre de menu > Gestionnaire de package > dans Project > personnalisée** , puis sélectionnez **exemples de réalité mixte Shared Computer Toolkit**.</span><span class="sxs-lookup"><span data-stu-id="e0047-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="e0047-111">dans la liste sur le côté droit du panneau, cliquez sur **importer dans Project bouton en** regard des exemples de noms de scènes.</span><span class="sxs-lookup"><span data-stu-id="e0047-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="e0047-112">par exemple, vous pouvez cliquer sur **importer dans Project** bouton en regard de **démonstrations-HandTracking**.</span><span class="sxs-lookup"><span data-stu-id="e0047-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="e0047-113">Une fois importés, vous pouvez les trouver sous **ressources >** dossier d’exemples.</span><span class="sxs-lookup"><span data-stu-id="e0047-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="e0047-114">**HandInteractionExamples** Scene est un excellent point de départ pour les interactions spatiales et les blocs de construction de l’interface utilisateur de MRTK.</span><span class="sxs-lookup"><span data-stu-id="e0047-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="e0047-115">Téléchargement et importation de packages directement à partir de GitHub</span><span class="sxs-lookup"><span data-stu-id="e0047-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="e0047-116">si vous n’utilisez pas l’outil de fonctionnalité de réalité mixte, vous pouvez télécharger et importer directement **Microsoft. MixedReality. Shared Computer Toolkit. unity. examples. pour unity** à partir de [la page de version de MRTK GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="e0047-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="e0047-117">Utilisez les **ressources > importer un package > menu package personnalisé** pour importer. pour Unity.</span><span class="sxs-lookup"><span data-stu-id="e0047-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="e0047-118">Une fois importé, vous pouvez trouver des exemples de scènes sous **ressources > MRTK > exemples > démonstrations**.</span><span class="sxs-lookup"><span data-stu-id="e0047-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>
