---
title: Vue d’ensemble de l’architecture
description: Vue d’ensemble de l’architecture de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, Architecture MRTK,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281918"
---
# <a name="architecture-overview"></a><span data-ttu-id="49590-104">Vue d’ensemble de l’architecture</span><span class="sxs-lookup"><span data-stu-id="49590-104">Architecture overview</span></span>

<span data-ttu-id="49590-105">Pour une introduction générale au contenu de MRTK, les informations d’architecture contenues dans ce document vous aideront à comprendre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="49590-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="49590-106">Grandes parties de MRTK et leur mode de connexion</span><span class="sxs-lookup"><span data-stu-id="49590-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="49590-107">Les concepts introduits par MRTK peuvent ne pas exister dans vanille Unity</span><span class="sxs-lookup"><span data-stu-id="49590-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="49590-108">Fonctionnement de certains des systèmes plus grands (tels que l’entrée)</span><span class="sxs-lookup"><span data-stu-id="49590-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="49590-109">Cette section n’est pas destinée à vous apprendre à effectuer des tâches, mais plutôt à la façon dont ces tâches sont structurées et pourquoi.</span><span class="sxs-lookup"><span data-stu-id="49590-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="49590-110">Nombreux publics, un seul Toolkit</span><span class="sxs-lookup"><span data-stu-id="49590-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="49590-111">MRTK n’a pas d’audience unique et uniforme.</span><span class="sxs-lookup"><span data-stu-id="49590-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="49590-112">Elle a été écrite pour prendre en charge des cas d’utilisation allant de la première hackathons à des individus développant des expériences complexes et partagées pour l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="49590-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="49590-113">Du code et des API ont peut-être été écrits et optimisés pour l’un des autres (par exemple, certaines parties du MRTK semblent plus optimisées pour une « configuration en un clic »), mais il est important de noter que certaines d’entre elles sont plus nombreuses pour des raisons d’historique et de réapprovisionnement.</span><span class="sxs-lookup"><span data-stu-id="49590-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="49590-114">À mesure que MRTK évolue, les fonctionnalités générées doivent être conçues pour être mises à l’échelle pour prendre en charge la plage de cas d’usage.</span><span class="sxs-lookup"><span data-stu-id="49590-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="49590-115">MRTK a également besoin d’une mise à l’échelle normale pour les expériences VR et AR.</span><span class="sxs-lookup"><span data-stu-id="49590-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="49590-116">il devrait être facile de créer des applications qui se déploient correctement dans un comportement lors du déploiement sur un HoloLens 2 ou un HoloLens 1, et il est préférable de créer des applications ciblant OpenVR et WMR (et d’autres plateformes).</span><span class="sxs-lookup"><span data-stu-id="49590-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="49590-117">Alors que l’équipe peut parfois concentrer une itération particulière sur un système ou une plateforme spécifique, l’objectif à long terme est de créer un large éventail de prise en charge pour chaque fois que des utilisateurs créent des expériences de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="49590-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="49590-118">Répartition générale</span><span class="sxs-lookup"><span data-stu-id="49590-118">High level breakdown</span></span>

<span data-ttu-id="49590-119">Le MRTK est à la fois un ensemble d’outils permettant d’obtenir rapidement les expériences de la réalité mixte (MR), ainsi qu’une infrastructure d’application avec des opinions sur son propre Runtime, sur la façon dont il doit être étendu et sur la façon dont il doit être configuré.</span><span class="sxs-lookup"><span data-stu-id="49590-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="49590-120">À un niveau élevé, les MRTK peuvent être décomposées des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="49590-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![Diagramme de vue d’ensemble de l’architecture](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="49590-122">Le MRTK contient également un autre ensemble d’utilitaires de poche qui n’ont pas de dépendances au reste du MRTK (pour en répertorier quelques-uns : outils de génération, solveurs, influenceurs audio, utilitaires de lissage et convertisseurs de ligne).</span><span class="sxs-lookup"><span data-stu-id="49590-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="49590-123">Le reste de la documentation sur l’architecture sera créé de bas en haut, en partant de l’infrastructure et du runtime, en progressant vers des systèmes plus intéressants et complexes, tels que l’entrée.</span><span class="sxs-lookup"><span data-stu-id="49590-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="49590-124">Consultez la table des matières pour continuer avec la vue d’ensemble de l’architecture.</span><span class="sxs-lookup"><span data-stu-id="49590-124">Please see the table of contents to continue with the architectural overview.</span></span>
