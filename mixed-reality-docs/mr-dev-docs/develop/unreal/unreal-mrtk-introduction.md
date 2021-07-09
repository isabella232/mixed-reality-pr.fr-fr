---
title: Présentation de MRTK pour Unreal
description: Commencez à utiliser tout ce que Mixed Reality Toolkit offre aux nouveaux développeurs de réalité mixte.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, outils, SDK, HoloLens, HoloLens 2, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, multiplateforme
ms.openlocfilehash: 3d46b92dbf3182ca5a50a8e106d2b947e4f7120f
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394283"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="3815b-104">Présentation de MRTK pour Unreal</span><span class="sxs-lookup"><span data-stu-id="3815b-104">Introducing MRTK for Unreal</span></span>

![Image de bannière MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="3815b-106">Qu’est-ce que le MRTK (Mixed Reality Toolkit) ?</span><span class="sxs-lookup"><span data-stu-id="3815b-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="3815b-107">Le MRTK est un fantastique kit d’outils open source qui existe depuis le lancement d’HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3815b-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="3815b-108">Il ne serait pas ce qu’il est aujourd’hui sans le dur travail réalisé par notre communauté de développeurs qui y ont apporté leur contribution.</span><span class="sxs-lookup"><span data-stu-id="3815b-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="3815b-109">Le Mixed Reality Toolkit pour Unreal (MRTK-Unreal) est un ensemble de composants sous forme de plug-ins, d’exemples et de documentations, conçus pour aider à développer des applications de réalité mixte avec Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="3815b-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="3815b-110">Actuellement, la boîte à outils se compose des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3815b-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="3815b-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), qui fournit du code, des blueprints et des exemples pour implémenter des fonctionnalités de l’expérience utilisateur pour les applications HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3815b-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="3815b-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), qui permet d’améliorer la fidélité visuelle des applications de réalité mixte tout en restant dans les budgets de performances.</span><span class="sxs-lookup"><span data-stu-id="3815b-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<span data-ttu-id="3815b-113">Regardez la [documentation MRTK sur GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) et démarrez avec les guides d’installation de [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) ou de [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).</span><span class="sxs-lookup"><span data-stu-id="3815b-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="3815b-114">Modularité</span><span class="sxs-lookup"><span data-stu-id="3815b-114">Modular</span></span>

<span data-ttu-id="3815b-115">Nous avons conçu MRTK Unreal d’une façon modulaire : vous ne devez donc pas prendre tous les composants du kit d’outils dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="3815b-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="3815b-116">Vous pouvez choisir les plug-ins dont vous avez besoin, puis les ajouter ou les supprimer à votre convenance.</span><span class="sxs-lookup"><span data-stu-id="3815b-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="3815b-117">Cette approche permet de réduire la taille des projets et de faciliter leur gestion.</span><span class="sxs-lookup"><span data-stu-id="3815b-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="3815b-118">Performance</span><span class="sxs-lookup"><span data-stu-id="3815b-118">Performant</span></span>

<span data-ttu-id="3815b-119">Nous avons conçu le MRTK Unreal dans le souci de vous offrir des performances optimales sur les plateformes mobiles.</span><span class="sxs-lookup"><span data-stu-id="3815b-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="3815b-120">C’est un point très important, notre but étant que les outils vous facilitent la tâche, et pas qu’ils vous la compliquent.</span><span class="sxs-lookup"><span data-stu-id="3815b-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="project-setup"></a><span data-ttu-id="3815b-121">Configuration du projet</span><span class="sxs-lookup"><span data-stu-id="3815b-121">Project setup</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3815b-122">Télécharger Unreal Engine et MRTK</span><span class="sxs-lookup"><span data-stu-id="3815b-122">Download Unreal Engine and MRTK</span></span>](unreal-project-setup.md)

## <a name="see-also"></a><span data-ttu-id="3815b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3815b-123">See also</span></span>

* [<span data-ttu-id="3815b-124">Installer les outils</span><span class="sxs-lookup"><span data-stu-id="3815b-124">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="3815b-125">Développement avec MRTK pour Unreal</span><span class="sxs-lookup"><span data-stu-id="3815b-125">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="3815b-126">UX Tools - Guide d’installation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3815b-126">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="3815b-127">Page d’accueil de la documentation UX Tools (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3815b-127">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="3815b-128">Graphics Tools - Guide d’installation (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3815b-128">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="3815b-129">Page d’accueil de la documentation Graphics Tools (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3815b-129">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)