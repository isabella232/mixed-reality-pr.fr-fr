---
title: Exécution des exemples de scènes
description: Découvrez comment acquérir et utiliser des exemples de scènes MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: boîte à outils de réalité mixte, MRTK, exemples, HoloLens, HoloLens 2, nuanceurs, info-bulles, interaction manuelle, découpage, zones englobantes, boutons, menus main, ardoise, curseur
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911861"
---
# <a name="example-scenes"></a><span data-ttu-id="095c7-104">Exemples de scènes</span><span class="sxs-lookup"><span data-stu-id="095c7-104">Example scenes</span></span>

<span data-ttu-id="095c7-105">MRTK fournit différents types d’exemples de scènes qui illustrent les fonctionnalités de MRTK et les blocs de construction pour l’expérience utilisateur spatial.</span><span class="sxs-lookup"><span data-stu-id="095c7-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="095c7-106">Des exemples de scènes de rencontre et de discernement peuvent être utiles pour comprendre les fonctionnalités et les appliquer à vos projets.</span><span class="sxs-lookup"><span data-stu-id="095c7-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="095c7-107">Comment acquérir des exemples de scènes</span><span class="sxs-lookup"><span data-stu-id="095c7-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="095c7-108">Utilisation de l’outil de fonctionnalité de réalité mixte et du gestionnaire de packages Unity</span><span class="sxs-lookup"><span data-stu-id="095c7-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="095c7-109">Vous pouvez télécharger et importer des exemples de package de la **boîte à outils de réalité mixte** via l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="095c7-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="095c7-110">Dans Unity, utilisez la **fenêtre de menu > gestionnaire de Package > dans Project > personnalisée** , puis sélectionnez **exemples d’outils de réalité mixte**.</span><span class="sxs-lookup"><span data-stu-id="095c7-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="095c7-111">Dans la liste sur le côté droit du panneau, cliquez sur le bouton **importer dans le projet** en regard des exemples de noms de scènes.</span><span class="sxs-lookup"><span data-stu-id="095c7-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="095c7-112">Par exemple, vous pouvez cliquer sur le bouton **importer dans le projet** en regard de **démonstrations-HandTracking**.</span><span class="sxs-lookup"><span data-stu-id="095c7-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="095c7-113">Une fois importés, vous pouvez les trouver sous **ressources >** dossier d’exemples.</span><span class="sxs-lookup"><span data-stu-id="095c7-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="095c7-114">**HandInteractionExamples** Scene est un excellent point de départ pour les interactions spatiales et les blocs de construction de l’interface utilisateur de MRTK.</span><span class="sxs-lookup"><span data-stu-id="095c7-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="095c7-115">Téléchargement et importation de packages directement à partir de GitHub</span><span class="sxs-lookup"><span data-stu-id="095c7-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="095c7-116">Si vous n’utilisez pas l’outil de fonctionnalité de réalité mixte, vous pouvez télécharger et importer directement **Microsoft. MixedReality. Toolkit. Unity. examples. pour Unity** à partir de [la page de publication de MRTK GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="095c7-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="095c7-117">Utilisez les **ressources > importer un package > menu package personnalisé** pour importer. pour Unity.</span><span class="sxs-lookup"><span data-stu-id="095c7-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="095c7-118">Une fois importé, vous pouvez trouver des exemples de scènes sous **ressources > MRTK > exemples > démonstrations**.</span><span class="sxs-lookup"><span data-stu-id="095c7-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>