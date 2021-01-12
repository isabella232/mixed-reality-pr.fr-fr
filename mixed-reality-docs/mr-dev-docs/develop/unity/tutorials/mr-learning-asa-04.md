---
title: Affichage du feedback Azure Spatial Anchors
description: Suivez ce cours pour découvrir comment afficher le feedback Azure Spatial Anchors dans une application de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, sessions, éléments de feedback
ms.localizationpriority: high
ms.openlocfilehash: 05e418b84f3370274433c4cc21f0122f3475301c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008329"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="ce6af-104">4. Affichage du feedback Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ce6af-104">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="ce6af-105">Dans ce tutoriel, vous allez voir comment fournir aux utilisateurs un feedback sur la découverte des ancres, leurs événements et leur état à l’aide d’Azure Spatial Anchors (ASA).</span><span class="sxs-lookup"><span data-stu-id="ce6af-105">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="ce6af-106">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ce6af-106">Objectives</span></span>

* <span data-ttu-id="ce6af-107">Apprendre à configurer un panneau d’interface utilisateur qui affiche des informations essentielles sur la session ASA en cours</span><span class="sxs-lookup"><span data-stu-id="ce6af-107">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="ce6af-108">Connaître les éléments de feedback que le SDK ASA met à la disposition des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="ce6af-108">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="ce6af-109">Apprendre à configurer un panneau de feedback ASA</span><span class="sxs-lookup"><span data-stu-id="ce6af-109">Setting up ASA feedback panel</span></span>

<span data-ttu-id="ce6af-110">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **Instructions** > **TextContent**.</span><span class="sxs-lookup"><span data-stu-id="ce6af-110">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="ce6af-111">Sélectionnez **3D Object** > **Text - TextMeshPro** pour créer un objet de texte TextMeshPro en tant qu’enfant de l’objet Instructions > TextContent :</span><span class="sxs-lookup"><span data-stu-id="ce6af-111">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![Unity avec l’objet TextMeshPro nouvellement créé sélectionné](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="ce6af-113">Pour faciliter l’utilisation de votre scène, désactivez <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> pour l’objet ParentAnchor en cliquant sur l’icône œil à gauche de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ce6af-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="ce6af-114">Ceci masque l’objet dans la fenêtre Scene sans changer sa visibilité dans le jeu.</span><span class="sxs-lookup"><span data-stu-id="ce6af-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="ce6af-115">Attribuez à l’objet Text (TMP) que vous venez de créer le nom de **Feedback**, puis, dans la fenêtre Inspector, modifiez sa position et sa taille de manière à ce qu’il soit placé bien en dessous du texte d’instruction, par exemple :</span><span class="sxs-lookup"><span data-stu-id="ce6af-115">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="ce6af-116">Remplacez la valeur **Pos Y** du composant Rect Transform par -0.24.</span><span class="sxs-lookup"><span data-stu-id="ce6af-116">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="ce6af-117">Remplacez la valeur **Width** du composant Rect Transform par 0.555.</span><span class="sxs-lookup"><span data-stu-id="ce6af-117">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="ce6af-118">Remplacez la valeur **Height** du composant Rect Transform par 0.1.</span><span class="sxs-lookup"><span data-stu-id="ce6af-118">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="ce6af-119">Choisissez ensuite les propriétés de police de sorte que le texte s’ajuste correctement dans la zone de texte, par exemple :</span><span class="sxs-lookup"><span data-stu-id="ce6af-119">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="ce6af-120">Pour le composant TextMeshPro - Text, configurez la valeur de **Font Style** sur Bold.</span><span class="sxs-lookup"><span data-stu-id="ce6af-120">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="ce6af-121">Pour le composant TextMeshPro - Text, configurez la valeur de **Font Size** sur 0.17.</span><span class="sxs-lookup"><span data-stu-id="ce6af-121">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="ce6af-122">Pour le composant TextMeshPro - Text, configurez la valeur de **Alignment** sur Center et Middle.</span><span class="sxs-lookup"><span data-stu-id="ce6af-122">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![Unity avec un objet Feedback configuré](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="ce6af-124">Dans la fenêtre Hierarchy, sélectionnez l’objet **Feedback**, puis, dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Anchor Feedback Script (Script)** et le configurer de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ce6af-124">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="ce6af-125">Affectez l’objet **Feedback** au champ **Feedback Text** du composant **Anchor Feedback Script (Script)** .</span><span class="sxs-lookup"><span data-stu-id="ce6af-125">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![Unity avec le composant Anchor Feedback Script configuré](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="ce6af-127">Félicitations</span><span class="sxs-lookup"><span data-stu-id="ce6af-127">Congratulations</span></span>

<span data-ttu-id="ce6af-128">Dans ce tutoriel, vous avez vu comment créer un panneau d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ce6af-128">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="ce6af-129">Celui-ci affiche l’état actuel de l’expérience Azure Spatial Anchors pour fournir aux utilisateurs du feedback en temps réel.</span><span class="sxs-lookup"><span data-stu-id="ce6af-129">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce6af-130">Tutoriel suivant : 5. Azure Spatial Anchors pour Android et iOS</span><span class="sxs-lookup"><span data-stu-id="ce6af-130">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
