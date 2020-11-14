---
title: Surfaces
description: Surfaces est un exemple d’application open source des laboratoires de conception de la réalité mixte de Microsoft. Il explore comment nous pouvons créer une sensation tactile avec un suivi visuel, audio et entièrement articulé.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, mrtk, design, exemple d’application, contrôles
ms.openlocfilehash: 1c6cb4579bbd3d6124cf36b21226ffa803f39f00
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573183"
---
# <a name="surfaces"></a><span data-ttu-id="ade5e-105">Surfaces</span><span class="sxs-lookup"><span data-stu-id="ade5e-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="ade5e-106">Cet article présente un exemple exploratoire que nous avons créé dans les [laboratoires de conception de réalité mixte](https://github.com/Microsoft/MRDesignLabs_Unity), un endroit où nous partageons nos connaissances et des suggestions concernant le développement d’applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ade5e-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="ade5e-107">Nos articles et code liés à la conception évoluent à mesure que nous effectuons de nouvelles découvertes.</span><span class="sxs-lookup"><span data-stu-id="ade5e-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="ade5e-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  est un exemple d’application open source des laboratoires de conception de la réalité mixte de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ade5e-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="ade5e-109">Il explore comment nous pouvons créer une sensation tactile avec un suivi visuel, audio et entièrement articulé.</span><span class="sxs-lookup"><span data-stu-id="ade5e-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surfaces](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="ade5e-111">Vidéo de démonstration</span><span class="sxs-lookup"><span data-stu-id="ade5e-111">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="ade5e-112">Enregistré avec HoloLens 2 à l’aide de la capture de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="ade5e-112">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="ade5e-113">À propos de l’application</span><span class="sxs-lookup"><span data-stu-id="ade5e-113">About the app</span></span>
<span data-ttu-id="ade5e-114">Surfaces montre comment utiliser le système d’entrée et les blocs de construction de MRTK (Mixed Reality Toolkit) pour créer une expérience d’application pour HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ade5e-114">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="ade5e-115">Dans ce projet, vous trouverez les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="ade5e-115">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="ade5e-116">Utilisez le [système d’entrée](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)de MRTK, en particulier le suivi de la main/du joint.</span><span class="sxs-lookup"><span data-stu-id="ade5e-116">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="ade5e-117">Utilisez le [nuanceur standard](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) de MRTK pour obtenir des graphiques performants.</span><span class="sxs-lookup"><span data-stu-id="ade5e-117">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="ade5e-118">Vous pouvez utiliser les composants de ce projet pour créer vos propres expériences d’application de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ade5e-118">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="ade5e-119">Monsieur dev Days 2020-en savoir plus sur l’application de surfaces MR</span><span class="sxs-lookup"><span data-stu-id="ade5e-119">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="ade5e-120">Apprentissages de l’application de surfaces MR</span><span class="sxs-lookup"><span data-stu-id="ade5e-120">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="ade5e-121">Lars Simkins, concepteur Senior derrière l’application MRDL surfaces, discute de la conception de l’application et des points essentiels.</span><span class="sxs-lookup"><span data-stu-id="ade5e-121">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="ade5e-122">Dépôt de projet sur GitHub</span><span class="sxs-lookup"><span data-stu-id="ade5e-122">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="ade5e-123">Télécharger l’application à partir de Microsoft Store dans HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ade5e-123">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="ade5e-124">(L’application est uniquement disponible sur HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="ade5e-124">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="ade5e-125">À propos de l’auteur</span><span class="sxs-lookup"><span data-stu-id="ade5e-125">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ade5e-126"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="ade5e-126"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="ade5e-127">Concepteur d’expérience utilisateur @Microsoft</span><span class="sxs-lookup"><span data-stu-id="ade5e-127">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="ade5e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ade5e-128">See also</span></span>

* <span data-ttu-id="ade5e-129">[Hub d’exemples MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="ade5e-129">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="ade5e-130">[Surfaces](sampleapp-surfaces.md) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="ade5e-130">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="ade5e-131">Tableau périodique des éléments 2.0</span><span class="sxs-lookup"><span data-stu-id="ade5e-131">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="ade5e-132">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="ade5e-132">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
