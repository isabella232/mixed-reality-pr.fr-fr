---
title: À propos de maquette
description: Présentation de maquette et de ses fonctionnalités.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935532"
---
# <a name="about-maquette"></a><span data-ttu-id="ba8e3-104">À propos de maquette</span><span class="sxs-lookup"><span data-stu-id="ba8e3-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="ba8e3-105">![Présentation du logo ](../images/MaquetteIcon.png) MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="ba8e3-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="ba8e3-106">Maquette intègre le JavaScript standard ECMA 5,1 pour permettre l’investissement de l’interactivité dans les scènes maquette et les objets qui peuvent être modifiés et exécutés à partir de VSCode.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="ba8e3-107">Les propriétés des objets sont exposées pour la lecture et le paramétrage à partir d’un script, de méthodes d’objet appelées, ainsi que d’événements système et d’objets.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="ba8e3-108">Le script peut également interagir avec maquette lui-même par le biais d’objets système accessibles via le script.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="ba8e3-109">Les différents contrôles d’interface utilisateur avec lesquels l’utilisateur peut interagir font partie du système.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="ba8e3-110">Ils peuvent être ajoutés lors de la création dans maquette ou créés et gérés à partir d’un script.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="ba8e3-111">Les événements d’interaction utilisateur avec ces éléments (entrée de données, clics, etc.) sont également exposés au script en tant qu’événements.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="ba8e3-112">Grâce à ces ajouts, il est possible de créer des scènes simples ou complexes, des expériences à la visualisation des données à des explorations de scénarios utilisateur de réalité mixte pour réaliser des expériences complètes dans AR ou VR.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="ba8e3-113">vidéo 60 second’ish</span><span class="sxs-lookup"><span data-stu-id="ba8e3-113">60 second'ish video</span></span>
* <span data-ttu-id="ba8e3-114">Carte de titre d’entrée</span><span class="sxs-lookup"><span data-stu-id="ba8e3-114">Entry Title Card</span></span>
  * <span data-ttu-id="ba8e3-115">Création d’un contenu de réalité mixte interactif dans maquette</span><span class="sxs-lookup"><span data-stu-id="ba8e3-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="ba8e3-116">Script/interactivité/système d’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="ba8e3-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="ba8e3-117">Les écrans de bienvenue de VO d’équipe ou de vidéo ?</span><span class="sxs-lookup"><span data-stu-id="ba8e3-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="ba8e3-118">raisons</span><span class="sxs-lookup"><span data-stu-id="ba8e3-118">explaining:</span></span>
  * <span data-ttu-id="ba8e3-119">raisonnement derrière l’écriture de scripts pour permettre la création de contenu RM interactif</span><span class="sxs-lookup"><span data-stu-id="ba8e3-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="ba8e3-120">toucher sur la façon dont il peut être utilisé dans les traits de pinceau très larges</span><span class="sxs-lookup"><span data-stu-id="ba8e3-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="ba8e3-121">Scripting des Vingette en action</span><span class="sxs-lookup"><span data-stu-id="ba8e3-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="ba8e3-122">Composition, boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="ba8e3-122">Composing dialog box</span></span>
  * <span data-ttu-id="ba8e3-123">Création d’une application à partir du plan (démonstration de l’application de cuisine)</span><span class="sxs-lookup"><span data-stu-id="ba8e3-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="ba8e3-124">Composer dans le modèle Photogrammetry</span><span class="sxs-lookup"><span data-stu-id="ba8e3-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="ba8e3-125">Interaction avec le Guide de dépannage</span><span class="sxs-lookup"><span data-stu-id="ba8e3-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="ba8e3-126">Vue d’écran du débogage des scripts dans VSCode</span><span class="sxs-lookup"><span data-stu-id="ba8e3-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="ba8e3-127">Obtention de l’accès au script à partir d’un objet dans la scène</span><span class="sxs-lookup"><span data-stu-id="ba8e3-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="ba8e3-128">Etc...</span><span class="sxs-lookup"><span data-stu-id="ba8e3-128">Etc...</span></span>
* <span data-ttu-id="ba8e3-129">Carte de titre résumé à la fin</span><span class="sxs-lookup"><span data-stu-id="ba8e3-129">Summary Title card at end</span></span>
  * <span data-ttu-id="ba8e3-130">Lien vers maquette</span><span class="sxs-lookup"><span data-stu-id="ba8e3-130">Link to Maquette</span></span>
  * <span data-ttu-id="ba8e3-131">Où accéder à la prise en main des scripts</span><span class="sxs-lookup"><span data-stu-id="ba8e3-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="ba8e3-132">Annonces/État/communauté</span><span class="sxs-lookup"><span data-stu-id="ba8e3-132">Announcements/status/community</span></span>
  * <span data-ttu-id="ba8e3-133">Regardez par avance pour voir ce que vous pouvez faire/soumissions ( ?)</span><span class="sxs-lookup"><span data-stu-id="ba8e3-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="ba8e3-134">Commentaires et comment nous pouvons vous servir mieux</span><span class="sxs-lookup"><span data-stu-id="ba8e3-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="ba8e3-135">Prise en main</span><span class="sxs-lookup"><span data-stu-id="ba8e3-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="ba8e3-136">Exemples et exemples d’applications</span><span class="sxs-lookup"><span data-stu-id="ba8e3-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="ba8e3-137">Support</span><span class="sxs-lookup"><span data-stu-id="ba8e3-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="ba8e3-138">Envoyez-nous des commentaires</span><span class="sxs-lookup"><span data-stu-id="ba8e3-138">Send us feedback</span></span>

<span data-ttu-id="ba8e3-139">Nous sommes impatients de vous entendre sur vos expériences et résultats.</span><span class="sxs-lookup"><span data-stu-id="ba8e3-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="ba8e3-140">Les commentaires, suggestions et rapports de bogues sont toujours les bienvenus !</span><span class="sxs-lookup"><span data-stu-id="ba8e3-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="ba8e3-141"><lien ? ></span><span class="sxs-lookup"><span data-stu-id="ba8e3-141"><Link?></span></span>