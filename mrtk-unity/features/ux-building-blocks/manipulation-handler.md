---
title: Gestionnaire de manipulation
description: Documentation sur le gestionnaire de manipulation dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Manipulation,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176633"
---
# <a name="manipulation-handler"></a><span data-ttu-id="8e762-104">Gestionnaire de manipulation</span><span class="sxs-lookup"><span data-stu-id="8e762-104">Manipulation handler</span></span>

![Gestionnaire de manipulation](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="8e762-106">Le script *ManipulationHandler* permet à un objet d’être rendu mobile, évolutif et rotatif à l’aide d’une ou de deux mains.</span><span class="sxs-lookup"><span data-stu-id="8e762-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="8e762-107">La manipulation peut être restreinte afin d’autoriser uniquement certains genres de transformations.</span><span class="sxs-lookup"><span data-stu-id="8e762-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="8e762-108">le script fonctionne avec différents types d’entrées, y compris HoloLens 2 entrée articulée, des rayons, des HoloLens (1ère génération) entrée de mouvement et une entrée de contrôleur de mouvement du casque immersif.</span><span class="sxs-lookup"><span data-stu-id="8e762-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="8e762-109">Comment utiliser le gestionnaire de manipulation</span><span class="sxs-lookup"><span data-stu-id="8e762-109">How to use the manipulation handler</span></span>

<span data-ttu-id="8e762-110">Ajoutez le `ManipulationHandler` composant script à un GameObject.</span><span class="sxs-lookup"><span data-stu-id="8e762-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="8e762-111">Veillez à ajouter également un conflit à l’objet, en faisant correspondre ses limites récupérables.</span><span class="sxs-lookup"><span data-stu-id="8e762-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="8e762-112">Pour faire en sorte que l’objet réponde à une entrée presque articulée, ajoutez `NearInteractionGrabbable` également le script.</span><span class="sxs-lookup"><span data-stu-id="8e762-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![Utilisation du gestionnaire de manipulation dans l’éditeur Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="8e762-114">Propriétés de l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="8e762-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="8e762-115">**Transformation** de l’hôte Transformation qui sera glissée.</span><span class="sxs-lookup"><span data-stu-id="8e762-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="8e762-116">La valeur par défaut est l’objet du composant.</span><span class="sxs-lookup"><span data-stu-id="8e762-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="8e762-117">**Type de manipulation** Spécifie si l’objet peut être manipulé à l’aide d’une main, de deux mains ou les deux.</span><span class="sxs-lookup"><span data-stu-id="8e762-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="8e762-118">*Une seule remise*</span><span class="sxs-lookup"><span data-stu-id="8e762-118">*One handed only*</span></span>
* <span data-ttu-id="8e762-119">*Deux mains uniquement*</span><span class="sxs-lookup"><span data-stu-id="8e762-119">*Two handed only*</span></span>
* <span data-ttu-id="8e762-120">*Un et deux droitiers*</span><span class="sxs-lookup"><span data-stu-id="8e762-120">*One and Two handed*</span></span>

<span data-ttu-id="8e762-121">**Type de manipulation à deux mains**</span><span class="sxs-lookup"><span data-stu-id="8e762-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="8e762-122">*Scale*: seule la mise à l’échelle est autorisée.</span><span class="sxs-lookup"><span data-stu-id="8e762-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="8e762-123">*Rotate*: seule la rotation est autorisée.</span><span class="sxs-lookup"><span data-stu-id="8e762-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="8e762-124">*Échelle de déplacement*: le déplacement et la mise à l’échelle sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8e762-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="8e762-125">*Move Rotate*: le déplacement et la rotation sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8e762-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="8e762-126">*Rotation* de l’échelle : la rotation et la mise à l’échelle sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="8e762-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="8e762-127">*Déplacer l’échelle de rotation*: le déplacement, la rotation et la mise à l’échelle sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8e762-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![Gestionnaire de manipulation](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="8e762-129">**Autoriser la manipulation Far** Spécifie si la manipulation peut être effectuée à l’aide de l’interaction Far avec les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="8e762-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="8e762-130">**Mode de rotation à un seul côté** Spécifie la manière dont l’objet se comporte lorsqu’il est retiré d’une main ou d’un contrôleur à proximité.</span><span class="sxs-lookup"><span data-stu-id="8e762-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="8e762-131">**Mode de rotation d’un côté** Spécifie la manière dont l’objet se comportera lorsqu’il sera retiré d’une main/d’un contrôleur à distance.</span><span class="sxs-lookup"><span data-stu-id="8e762-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="8e762-132">**Options du mode de rotation d’une main** Spécifie le mode de rotation de l’objet lorsqu’il est retiré d’une main.</span><span class="sxs-lookup"><span data-stu-id="8e762-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="8e762-133">*Conserver la rotation d’origine*: ne pivote pas l’objet tel qu’il est déplacé</span><span class="sxs-lookup"><span data-stu-id="8e762-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="8e762-134">*Conserver la rotation vers l’utilisateur*: maintient la rotation d’origine de l’objet pour l’axe X/Y à l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="8e762-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="8e762-135">La *gravité alignée maintenir la rotation sur l’utilisateur*: maintient la rotation d’origine de l’objet à l’utilisateur, mais rend l’objet vertical.</span><span class="sxs-lookup"><span data-stu-id="8e762-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="8e762-136">Utile pour les objets avec un contrôle de limites.</span><span class="sxs-lookup"><span data-stu-id="8e762-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="8e762-137">*Visage User*: garantit que l’objet est toujours face à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e762-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="8e762-138">Utile pour les ardoises/panneaux.</span><span class="sxs-lookup"><span data-stu-id="8e762-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="8e762-139">*Face à l’utilisateur*: garantit que l’objet est toujours face à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e762-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="8e762-140">Utile pour les ardoises/panneaux configurés en arrière.</span><span class="sxs-lookup"><span data-stu-id="8e762-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="8e762-141">*Faire pivoter à propos du centre d’objets*: fonctionne uniquement pour les mains/contrôleurs articulés.</span><span class="sxs-lookup"><span data-stu-id="8e762-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="8e762-142">Faire pivoter l’objet à l’aide de la rotation de la main/du contrôleur, mais à propos du point central de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8e762-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="8e762-143">Utile pour l’inspection à distance.</span><span class="sxs-lookup"><span data-stu-id="8e762-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="8e762-144">*Faire pivoter à propos du point de manipulation*: fonctionne uniquement pour les mains/contrôleurs articulés.</span><span class="sxs-lookup"><span data-stu-id="8e762-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="8e762-145">Faire pivoter l’objet comme s’il était maintenu par la main/le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="8e762-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="8e762-146">Utile pour l’inspection.</span><span class="sxs-lookup"><span data-stu-id="8e762-146">Useful for inspection.</span></span>

<span data-ttu-id="8e762-147">**Comportement** de la version Lorsqu’un objet est relâché, spécifiez son comportement de déplacement physique.</span><span class="sxs-lookup"><span data-stu-id="8e762-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="8e762-148">Nécessite un composant RigidBody pour être sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="8e762-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="8e762-149">*Nothing*</span><span class="sxs-lookup"><span data-stu-id="8e762-149">*Nothing*</span></span>
* <span data-ttu-id="8e762-150">*Tout*</span><span class="sxs-lookup"><span data-stu-id="8e762-150">*Everything*</span></span>
* <span data-ttu-id="8e762-151">*Conserver la vélocité*</span><span class="sxs-lookup"><span data-stu-id="8e762-151">*Keep Velocity*</span></span>
* <span data-ttu-id="8e762-152">*conserver Angular vélocité*</span><span class="sxs-lookup"><span data-stu-id="8e762-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="8e762-153">**Contraintes de rotation** Spécifie l’axe avec lequel l’objet pivotera lorsqu’il est interagi.</span><span class="sxs-lookup"><span data-stu-id="8e762-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="8e762-154">*Aucun*</span><span class="sxs-lookup"><span data-stu-id="8e762-154">*None*</span></span>
* <span data-ttu-id="8e762-155">*Axe X uniquement*</span><span class="sxs-lookup"><span data-stu-id="8e762-155">*X-Axis Only*</span></span>
* <span data-ttu-id="8e762-156">*Axe Y uniquement*</span><span class="sxs-lookup"><span data-stu-id="8e762-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="8e762-157">*Axe Z uniquement*</span><span class="sxs-lookup"><span data-stu-id="8e762-157">*Z-Axis Only*</span></span>

<span data-ttu-id="8e762-158">**Utiliser l’espace local pour la contrainte** Bouton bascule pour basculer entre l’application de contraintes par rapport à l’axe d’espace universel ou l’axe d’espace local.</span><span class="sxs-lookup"><span data-stu-id="8e762-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="8e762-159">**Contraintes sur le mouvement**</span><span class="sxs-lookup"><span data-stu-id="8e762-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="8e762-160">*Aucun*</span><span class="sxs-lookup"><span data-stu-id="8e762-160">*None*</span></span>
* <span data-ttu-id="8e762-161">*Corriger la distance par rapport à la tête*</span><span class="sxs-lookup"><span data-stu-id="8e762-161">*Fix distance from head*</span></span>

<span data-ttu-id="8e762-162">**Lissage actif** Spécifie si le lissage est actif.</span><span class="sxs-lookup"><span data-stu-id="8e762-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="8e762-163">**Lissage de la quantité d’une main** Quantité de lissage à appliquer au mouvement, à l’échelle et à la rotation.</span><span class="sxs-lookup"><span data-stu-id="8e762-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="8e762-164">Le lissage de 0 signifie qu’il n’y a pas de lissage.</span><span class="sxs-lookup"><span data-stu-id="8e762-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="8e762-165">La valeur Max signifie qu’aucune modification n’est apportée à la valeur.</span><span class="sxs-lookup"><span data-stu-id="8e762-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="8e762-166">Événements</span><span class="sxs-lookup"><span data-stu-id="8e762-166">Events</span></span>

<span data-ttu-id="8e762-167">Le gestionnaire de manipulation fournit les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="8e762-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="8e762-168">*OnManipulationStarted*: déclenché lorsque la manipulation démarre.</span><span class="sxs-lookup"><span data-stu-id="8e762-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="8e762-169">*OnManipulationEnded*: se déclenche lorsque la manipulation se termine.</span><span class="sxs-lookup"><span data-stu-id="8e762-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="8e762-170">*OnHoverStarted*: se déclenche quand une main/un contrôleur pointe le manipulable, proche ou loin.</span><span class="sxs-lookup"><span data-stu-id="8e762-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="8e762-171">*OnHoverEnded*: se déclenche quand une main/un contrôleur ne fait pas pointer le manipulable, à proximité ou à l’extrême.</span><span class="sxs-lookup"><span data-stu-id="8e762-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
