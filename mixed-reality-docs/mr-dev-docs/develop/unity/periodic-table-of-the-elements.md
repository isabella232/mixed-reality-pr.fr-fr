---
title: Tableau périodique des éléments
description: Découvrez comment disposer un tableau d’objets dans l’espace 3D avec différents types de surface à l’aide d’une collection d’objets avec la table périodique de l’exemple d’application d’éléments.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, exemple d’application, contrôles, MRTK, kit de préversion de réalité mixte, Unity, exemples d’applications, exemples d’applications, open source, Microsoft Store, HoloLens, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743416"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="3a59c-104">Tableau périodique des éléments</span><span class="sxs-lookup"><span data-stu-id="3a59c-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="3a59c-105">Cet article présente un exemple exploratoire que nous avons créé dans les [laboratoires de conception de réalité mixte](https://github.com/Microsoft/MRDesignLabs_Unity), un endroit où nous partageons nos connaissances et des suggestions concernant le développement d’applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="3a59c-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="3a59c-106">Nos articles et code liés à la conception évoluent à mesure que nous effectuons de nouvelles découvertes.</span><span class="sxs-lookup"><span data-stu-id="3a59c-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="3a59c-107">[La table périodique des éléments](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) est un exemple d’application open source des laboratoires de conception de la réalité mixte de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3a59c-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="3a59c-108">Découvrez comment disposer un tableau d’objets dans l’espace 3D avec différents types de surface à l’aide d’une **[collection d’objets](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="3a59c-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="3a59c-109">Découvrez également comment créer des objets interactifs qui répondent aux entrées standard de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3a59c-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="3a59c-110">Vous pouvez utiliser les composants de ce projet pour créer votre propre expérience d’application de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="3a59c-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Table period de l’application Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="3a59c-112">Vidéo de démonstration</span><span class="sxs-lookup"><span data-stu-id="3a59c-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="3a59c-113">Enregistré avec HoloLens 2 à l’aide de la capture de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="3a59c-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="3a59c-114">À propos de l’application</span><span class="sxs-lookup"><span data-stu-id="3a59c-114">About the app</span></span>

<span data-ttu-id="3a59c-115">La table périodique des éléments visualise les éléments chimiques et chacune de leurs propriétés dans un espace 3D.</span><span class="sxs-lookup"><span data-stu-id="3a59c-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="3a59c-116">Il intègre les interactions de base de HoloLens, telles que le toucher et l’air.</span><span class="sxs-lookup"><span data-stu-id="3a59c-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="3a59c-117">Les utilisateurs peuvent en savoir plus sur les éléments avec des modèles 3D animés.</span><span class="sxs-lookup"><span data-stu-id="3a59c-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="3a59c-118">Ils peuvent comprendre visuellement le shell électron d’un élément et son noyau, qui est composé de protons et de neutrons.</span><span class="sxs-lookup"><span data-stu-id="3a59c-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="3a59c-119">Arrière-plan</span><span class="sxs-lookup"><span data-stu-id="3a59c-119">Background</span></span>

<span data-ttu-id="3a59c-120">Une fois que je me suis familiarisé avec HoloLens, je savais que je voulais expérimenter une application de table périodique en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="3a59c-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="3a59c-121">Étant donné que chaque élément a de nombreux points de données qui s’affichent avec du texte, j’ai pensé qu’il serait intéressant d’explorer la composition typographique dans un espace 3D.</span><span class="sxs-lookup"><span data-stu-id="3a59c-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="3a59c-122">Donner aux utilisateurs la possibilité de visualiser le modèle d’électrons de l’élément était une autre partie intéressante de ce projet.</span><span class="sxs-lookup"><span data-stu-id="3a59c-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="3a59c-123">Conception</span><span class="sxs-lookup"><span data-stu-id="3a59c-123">Design</span></span>

<span data-ttu-id="3a59c-124">Pour la vue par défaut de la table périodique, j’ai imaginé des cases tridimensionnelles qui contiennent le modèle d’électrons de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="3a59c-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="3a59c-125">La surface de chaque zone est translucide afin que l’utilisateur puisse obtenir une idée approximative du volume de l’élément.</span><span class="sxs-lookup"><span data-stu-id="3a59c-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="3a59c-126">Lorsque vous appuyez sur le regard et l’air, l’utilisateur peut ouvrir une vue détaillée de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="3a59c-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="3a59c-127">Pour effectuer la transition entre la vue de table et l’affichage détaillé en douceur et en naturel, j’ai fait de la même façon que l’interaction physique d’une ouverture de Box dans la vie réelle.</span><span class="sxs-lookup"><span data-stu-id="3a59c-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="3a59c-128">![Concevoir l’esquisse](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="3a59c-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="3a59c-129">*Concevoir des croquis*</span><span class="sxs-lookup"><span data-stu-id="3a59c-129">*Design sketches*</span></span>

<span data-ttu-id="3a59c-130">En mode Détails, je voulais visualiser les informations de chaque élément avec un rendu impeccable du texte dans l’espace 3D.</span><span class="sxs-lookup"><span data-stu-id="3a59c-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="3a59c-131">Le modèle d’électrons 3D animé est affiché dans la zone centrale et peut être affiché à partir de différents angles.</span><span class="sxs-lookup"><span data-stu-id="3a59c-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interaction](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="3a59c-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="3a59c-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="3a59c-134">*Prototypes d’interaction*</span><span class="sxs-lookup"><span data-stu-id="3a59c-134">*Interaction prototypes*</span></span>

<span data-ttu-id="3a59c-135">L’utilisateur peut modifier le type de surface par air en appuyant sur les boutons situés en bas du tableau : il peut basculer entre les plans, les cylindres, les sphères et les nuages de points.</span><span class="sxs-lookup"><span data-stu-id="3a59c-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="3a59c-136">Contrôles et modèles communs utilisés dans cette application</span><span class="sxs-lookup"><span data-stu-id="3a59c-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="3a59c-137">Objet interagiable (bouton)</span><span class="sxs-lookup"><span data-stu-id="3a59c-137">Interactable object (button)</span></span>

<span data-ttu-id="3a59c-138">L’objet qui peut être [interagi](../../design/interactable-object.md) est un objet, qui peut répondre aux entrées HoloLens de base.</span><span class="sxs-lookup"><span data-stu-id="3a59c-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="3a59c-139">Il est fourni en tant que Prefab/script, que vous pouvez facilement appliquer à n’importe quel objet.</span><span class="sxs-lookup"><span data-stu-id="3a59c-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="3a59c-140">Par exemple, vous pouvez rendre une tasse de café dans votre scène interactive et répondre à des entrées telles que le pointage, le toucher, la navigation et les gestes de manipulation.</span><span class="sxs-lookup"><span data-stu-id="3a59c-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="3a59c-141">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="3a59c-141">Learn more</span></span>](../../design/interactable-object.md)

![objet nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="3a59c-143">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="3a59c-143">Object collection</span></span>

<span data-ttu-id="3a59c-144">La [collection d’objets](../../design/object-collection.md) est un objet, qui vous permet de disposer plusieurs objets dans différentes formes.</span><span class="sxs-lookup"><span data-stu-id="3a59c-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="3a59c-145">Il prend en charge les plans, les cylindres, les sphères et les nuages de points.</span><span class="sxs-lookup"><span data-stu-id="3a59c-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="3a59c-146">Vous pouvez configurer des propriétés supplémentaires telles que le rayon, le nombre de lignes et l’espacement.</span><span class="sxs-lookup"><span data-stu-id="3a59c-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="3a59c-147">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="3a59c-147">Learn more</span></span>](../../design/object-collection.md)

![Collection d’objets](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="3a59c-149">Détails techniques</span><span class="sxs-lookup"><span data-stu-id="3a59c-149">Technical details</span></span>

<span data-ttu-id="3a59c-150">Vous trouverez scripts and prefabs pour la table Periodic de l’application Elements sur le GitHub de conception de la [réalité mixte](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="3a59c-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="3a59c-151">Portage de l’histoire pour HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3a59c-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="3a59c-152">Lisez l’article sur la façon dont la table périodique de l’application d’éléments a été mise à jour avec les interactions instinctual de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3a59c-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="3a59c-153">Tableau périodique des éléments 2.0</span><span class="sxs-lookup"><span data-stu-id="3a59c-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="3a59c-154">À propos de l’auteur</span><span class="sxs-lookup"><span data-stu-id="3a59c-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="3a59c-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="3a59c-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="3a59c-156">Concepteur d’expérience utilisateur @Microsoft</span><span class="sxs-lookup"><span data-stu-id="3a59c-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="3a59c-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a59c-157">See also</span></span>

* <span data-ttu-id="3a59c-158">[Hub d’exemples MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="3a59c-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="3a59c-159">[Surfaces](sampleapp-surfaces.md) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="3a59c-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="3a59c-160">Tableau périodique des éléments 2.0</span><span class="sxs-lookup"><span data-stu-id="3a59c-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="3a59c-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="3a59c-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)