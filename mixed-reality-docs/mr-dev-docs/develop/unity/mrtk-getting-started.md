---
title: Présentation de MRTK pour Unity
description: Démarrez avec tout ce que le kit Mixed Reality Toolkit multiplateforme offre aux nouveaux développeurs de réalité mixte.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, outils, SDK, HoloLens, HoloLens 2, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, multiplateforme
ms.openlocfilehash: 4c013f1fa50518404f899b4181e7c07b9e4e0e56
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581707"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="87c1f-104">Présentation de MRTK pour Unity</span><span class="sxs-lookup"><span data-stu-id="87c1f-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="87c1f-106">Qu’est-ce que le MRTK (Mixed Reality Toolkit) ?</span><span class="sxs-lookup"><span data-stu-id="87c1f-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="87c1f-107">Le MRTK est un fantastique kit d’outils open source qui existe depuis le lancement d’HoloLens.</span><span class="sxs-lookup"><span data-stu-id="87c1f-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="87c1f-108">Il ne serait pas ce qu’il est aujourd’hui sans le dur travail réalisé par notre communauté de développeurs qui y ont apporté leur contribution.</span><span class="sxs-lookup"><span data-stu-id="87c1f-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="87c1f-109">Au cours des trois dernières années, nous avons écouté les commentaires de notre communauté de développeurs et nous avons créé MRTK v2 afin de prendre en compte les problèmes majeurs qui nous ont été remontés.</span><span class="sxs-lookup"><span data-stu-id="87c1f-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="87c1f-110">MRTK pour Unity est un kit de développement multiplateforme open source pour les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="87c1f-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="87c1f-111">Le kit d’outils fournit un système d’entrée multiplateforme, des composants fondamentaux ainsi que des modules communs pour les interactions spatiales.</span><span class="sxs-lookup"><span data-stu-id="87c1f-111">The toolkit provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="87c1f-112">MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.</span><span class="sxs-lookup"><span data-stu-id="87c1f-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="87c1f-113">Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="87c1f-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="87c1f-114">Regardez la [documentation MRTK sur GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) et démarrez avec le [Guide d’installation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span><span class="sxs-lookup"><span data-stu-id="87c1f-114">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) and get started with the [installation guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="87c1f-115">Nouveautés de MRTK v2</span><span class="sxs-lookup"><span data-stu-id="87c1f-115">New with MRTK v2</span></span>

<span data-ttu-id="87c1f-116">Nous souhaitons souligner notre engagement envers ces outils de plateforme.</span><span class="sxs-lookup"><span data-stu-id="87c1f-116">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="87c1f-117">En fait, nous avons utilisé MRTK version 2 pour développer nos expériences intégrées, comme l’expérience d’installation OOBE et notre application Mixed Reality Tips.</span><span class="sxs-lookup"><span data-stu-id="87c1f-117">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="87c1f-118">Vous verrez également de nouvelles fonctionnalités d’HoloLens 2 exposées pour la première fois par le biais du MRTK, car selon nous, il s’agit de la meilleure méthode pour développer sur notre plateforme.</span><span class="sxs-lookup"><span data-stu-id="87c1f-118">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="87c1f-119">Modularité</span><span class="sxs-lookup"><span data-stu-id="87c1f-119">Modular</span></span>

<span data-ttu-id="87c1f-120">Nous avons conçu ce kit d’une façon modulaire pour que vous n’ayez pas besoin d’en utiliser tous les composants dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="87c1f-120">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="87c1f-121">Cela présente plusieurs avantages.</span><span class="sxs-lookup"><span data-stu-id="87c1f-121">There are actually a few benefits to this.</span></span>  <span data-ttu-id="87c1f-122">Votre projet conserve une taille limitée et est plus facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="87c1f-122">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="87c1f-123">De plus, comme le kit est conçu avec des objets scriptables et qu’il est basé sur une interface, vous pouvez remplacer ses composants par les vôtres, ce qui rend possible la prise en charge d’autres services, systèmes et plateformes.</span><span class="sxs-lookup"><span data-stu-id="87c1f-123">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="87c1f-124">Système multiplateforme</span><span class="sxs-lookup"><span data-stu-id="87c1f-124">Cross-platform</span></span>

<span data-ttu-id="87c1f-125">Justement, à propos des autres plateformes, le kit fournit une prise en charge multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="87c1f-125">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="87c1f-126">Cela ne signifie pas pour autant que toutes les plateformes sont prises en charge, mais nous avons fait en sorte que tout le code existant dans le kit d’outils continue de s’exécuter correctement lorsque vous basculez votre cible de build vers d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="87c1f-126">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="87c1f-127">La robustesse et l’extensibilité de la conception modulaire permettent à vos applications de prendre en charge plusieurs plateformes, parmi lesquelles ARCore, ARKit et OpenVR.</span><span class="sxs-lookup"><span data-stu-id="87c1f-127">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="87c1f-128">Performance</span><span class="sxs-lookup"><span data-stu-id="87c1f-128">Performant</span></span>

<span data-ttu-id="87c1f-129">Nous avons conçu le kit d’outils dans un souci de vous offrir des performances optimales sur les plateformes mobiles.</span><span class="sxs-lookup"><span data-stu-id="87c1f-129">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="87c1f-130">C’est un point très important, notre but étant que les outils vous facilitent la tâche, et pas qu’ils vous la compliquent.</span><span class="sxs-lookup"><span data-stu-id="87c1f-130">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="87c1f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87c1f-131">See also</span></span>

* [<span data-ttu-id="87c1f-132">Installer les outils</span><span class="sxs-lookup"><span data-stu-id="87c1f-132">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="87c1f-133">Développement avec MRTK pour Unity</span><span class="sxs-lookup"><span data-stu-id="87c1f-133">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="87c1f-134">MRTK - Guide d’installation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="87c1f-134">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="87c1f-135">Page d’accueil de la documentation MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="87c1f-135">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="87c1f-136">Portage de HoloToolkit/MRTK vers MRTK version 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="87c1f-136">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
