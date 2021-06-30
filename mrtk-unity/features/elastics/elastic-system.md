---
title: Système élastique
description: Documentation relative à la simulation des élastiques dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, ElasticsSystem,
ms.openlocfilehash: 1f90864ee6d3b6756b863de600ade8423a44cacc
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121237"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="729b7-104">Système élastique (expérimental)</span><span class="sxs-lookup"><span data-stu-id="729b7-104">Elastic system (experimental)</span></span>

![Système élastique](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="729b7-106">MRTK est fourni avec un système de simulation élastique qui inclut une large gamme de sous-classes extensibles et flexibles, qui offre des liaisons pour les ressorts de Quaternion à quatre dimensions, les ressorts de volume 3D et les systèmes à ressort linéaires simples.</span><span class="sxs-lookup"><span data-stu-id="729b7-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="729b7-107">Actuellement, les composants MRTK suivants prenant en charge le [Gestionnaire élastique](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) peuvent tirer parti des fonctionnalités élastiques :</span><span class="sxs-lookup"><span data-stu-id="729b7-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="729b7-108">Contrôle de limites</span><span class="sxs-lookup"><span data-stu-id="729b7-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="729b7-109">Manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="729b7-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="729b7-110">Gestionnaire élastiques</span><span class="sxs-lookup"><span data-stu-id="729b7-110">Elastics manager</span></span>

![System2 élastique](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="729b7-112">Le gestionnaire élastique traite les transformations transmises et les alimente dans le système élastique.</span><span class="sxs-lookup"><span data-stu-id="729b7-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="729b7-113">L’activation des élastiques pour les composants personnalisés peut être effectuée en deux étapes :</span><span class="sxs-lookup"><span data-stu-id="729b7-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="729b7-114">Appel de la méthode Initialize au démarrage de la manipulation, mise à jour du système avec la transformation hôte actuelle.</span><span class="sxs-lookup"><span data-stu-id="729b7-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="729b7-115">Interrogation de ApplyHostTransform chaque fois qu’un calcul élastique doit être effectué sur la transformation cible mise à jour.</span><span class="sxs-lookup"><span data-stu-id="729b7-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="729b7-116">Notez que les élastiques continuent de simuler une fois les manipulations terminées (par le biais de la boucle de mise à jour élastiques Manager).</span><span class="sxs-lookup"><span data-stu-id="729b7-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="729b7-117">Pour bloquer le comportement, les [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) de mise à jour automatique élastiques peuvent avoir la valeur false.</span><span class="sxs-lookup"><span data-stu-id="729b7-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="729b7-118">Par défaut, le composant de gestionnaire élastiques, lorsqu’il est ajouté à un objet de jeu, n’a pas de élastiques activés pour les types de transformations.</span><span class="sxs-lookup"><span data-stu-id="729b7-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="729b7-119">Le champ `Manipulation types using elastic feedback` doit être activé pour des types de transformation spécifiques afin de créer des étendues et des configurations élastiques pour le type sélectionné.</span><span class="sxs-lookup"><span data-stu-id="729b7-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="729b7-120">Configurations élastiques</span><span class="sxs-lookup"><span data-stu-id="729b7-120">Elastics configurations</span></span>

<span data-ttu-id="729b7-121">Comme pour les [configurations de contrôle de limites, le](../ux-building-blocks/bounds-control.md#configuration-objects)gestionnaire élastique est fourni avec un ensemble d’objets de configuration qui peuvent être stockés en tant qu’objets pouvant faire l’objet d’un script et partagés entre différentes instances ou prefabs.</span><span class="sxs-lookup"><span data-stu-id="729b7-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="729b7-122">Les configurations peuvent être partagées et liées en tant que fichiers de ressources pouvant faire l’élément d’un script ou imbriqués dans prefabs.</span><span class="sxs-lookup"><span data-stu-id="729b7-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="729b7-123">D’autres configurations peuvent également être définies directement sur l’instance sans liaison à une ressource scriptable externe ou imbriquée.</span><span class="sxs-lookup"><span data-stu-id="729b7-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="729b7-124">L’inspecteur du gestionnaire élastiques indique si une configuration est partagée ou inline dans le cadre de l’instance actuelle en présentant un message dans l’inspecteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="729b7-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="729b7-125">En outre, les instances partagées ne peuvent pas être modifiées directement dans la fenêtre de propriétés du gestionnaire élastiques elle-même, mais à la place, la ressource à laquelle elle est liée doit être directement modification pour éviter toute modification accidentelle des configurations partagées.</span><span class="sxs-lookup"><span data-stu-id="729b7-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="729b7-126">Le gestionnaire élastique offre des options d’objets de configuration pour les types de transformation suivants, chacun représenté par un [objet de configuration élastique](#elastic-configuration-object):</span><span class="sxs-lookup"><span data-stu-id="729b7-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="729b7-127">Élastique de translation</span><span class="sxs-lookup"><span data-stu-id="729b7-127">Translation Elastic</span></span>
- <span data-ttu-id="729b7-128">Élastique de rotation</span><span class="sxs-lookup"><span data-stu-id="729b7-128">Rotation Elastic</span></span>
- <span data-ttu-id="729b7-129">Élastique d’échelle</span><span class="sxs-lookup"><span data-stu-id="729b7-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="729b7-130">Objet de configuration élastique</span><span class="sxs-lookup"><span data-stu-id="729b7-130">Elastic configuration object</span></span>

<span data-ttu-id="729b7-131">Une configuration élastique définit les propriétés d’un système différentiel d’oscillateur harmonique amorti.</span><span class="sxs-lookup"><span data-stu-id="729b7-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="729b7-132">Les propriétés suivantes peuvent être ajustées, mais elles sont déjà fournies avec un ensemble de valeurs par défaut dans MRTK :</span><span class="sxs-lookup"><span data-stu-id="729b7-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="729b7-133">**Masse**: masse de l’élément de l’oscillateur simulé.</span><span class="sxs-lookup"><span data-stu-id="729b7-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="729b7-134">**HandK**: constante Spring à la main.</span><span class="sxs-lookup"><span data-stu-id="729b7-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="729b7-135">**EndK**: constante Spring Cap end.</span><span class="sxs-lookup"><span data-stu-id="729b7-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="729b7-136">**SnapK**: constante de ressort de point d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="729b7-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="729b7-137">**Faites glisser**: facteur de glissement/amortisseur, proportionnel à la vélocité.</span><span class="sxs-lookup"><span data-stu-id="729b7-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="729b7-138">Étendues élastiques</span><span class="sxs-lookup"><span data-stu-id="729b7-138">Elastics extents</span></span>

<span data-ttu-id="729b7-139">Les paramètres d’étendues élastiques varient selon le type de manipulation.</span><span class="sxs-lookup"><span data-stu-id="729b7-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="729b7-140">La translation et l’échelle sont représentées par les [Extensions élastiques de volume](#volume-elastic-extent) et la rotation est représentée par une [extension élastique Quaternion](#quaternion-elastic-extent).</span><span class="sxs-lookup"><span data-stu-id="729b7-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="729b7-141">Étendue élastique en volume</span><span class="sxs-lookup"><span data-stu-id="729b7-141">Volume elastic extent</span></span>

<span data-ttu-id="729b7-142">Les étendues de volume définissent un espace à trois dimensions dans lequel l’oscillateur d’harmonique humide est libre de se déplacer.</span><span class="sxs-lookup"><span data-stu-id="729b7-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Limites d’étirement de volume élastique](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="729b7-144">**StretchBounds**: représente les limites inférieures de l’espace élastique.</span><span class="sxs-lookup"><span data-stu-id="729b7-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="729b7-145">**UseBounds**: indique si les limites d’étirement doivent être respectées par le système.</span><span class="sxs-lookup"><span data-stu-id="729b7-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="729b7-146">Si la valeur est true, lorsque l’itération actuelle de la position cible se trouve en dehors des limites d’étirement, l’effort de fin sera appliqué.</span><span class="sxs-lookup"><span data-stu-id="729b7-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="729b7-147">**Points d’ancrage**: points à l’intérieur de l’espace auquel le système doit s’aligner.</span><span class="sxs-lookup"><span data-stu-id="729b7-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="729b7-148">**RepeatSnapPoints**: répète les points d’alignement à l’infini.</span><span class="sxs-lookup"><span data-stu-id="729b7-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="729b7-149">Les points d’ancrage existants serviront de modulo dans lequel les points d’alignement réels sont mappés sur les multiples entiers les plus proches de chaque point d’alignement.</span><span class="sxs-lookup"><span data-stu-id="729b7-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="729b7-150">**SnapRadius**: distance à laquelle les points d’ancrage commencent à forcer le ressort.</span><span class="sxs-lookup"><span data-stu-id="729b7-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Grille d’accrochage de volume élastique](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="729b7-152">Étendue élastique Quaternion</span><span class="sxs-lookup"><span data-stu-id="729b7-152">Quaternion elastic extent</span></span>

<span data-ttu-id="729b7-153">Les extensions de Quaternion définissent un espace de rotation à quatre dimensions dans lequel l’oscillateur harmonique amorti est libre de pivoter.</span><span class="sxs-lookup"><span data-stu-id="729b7-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Exemple de rotation élastique](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="729b7-155">**Points d’ancrage**: Euler angles auxquels le système doit s’aligner.</span><span class="sxs-lookup"><span data-stu-id="729b7-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="729b7-156">**RepeatSnapPoints**: répète les points d’alignement.</span><span class="sxs-lookup"><span data-stu-id="729b7-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="729b7-157">Les points d’ancrage existants serviront de modulo dans lequel les points d’alignement réels sont mappés sur les multiples entiers les plus proches de chaque point d’alignement.</span><span class="sxs-lookup"><span data-stu-id="729b7-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="729b7-158">**SnapRadius**: angle d’arc à partir duquel les points d’ancrage commencent à forcer le printemps en degrés Euler.</span><span class="sxs-lookup"><span data-stu-id="729b7-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="729b7-159">Exemple de scène élastique</span><span class="sxs-lookup"><span data-stu-id="729b7-159">Elastics example scene</span></span>

<span data-ttu-id="729b7-160">Vous trouverez des exemples de configurations élastiques dans la `ElasticSystemExample` scène.</span><span class="sxs-lookup"><span data-stu-id="729b7-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Exemple de scène élastique](../images/elastics/Elastics_Example_Scene.png)
