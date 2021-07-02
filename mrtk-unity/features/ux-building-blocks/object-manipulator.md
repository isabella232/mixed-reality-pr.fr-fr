---
title: Manipulateur d’objets
description: Comment utiliser le manipulateur d’objets dans MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Manipulation d’objets,
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176649"
---
# <a name="object-manipulator"></a><span data-ttu-id="21479-104">Manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="21479-104">Object manipulator</span></span>

![Manipulateur d’objets](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="21479-106">Le *ObjectManipulator* est le nouveau composant pour le comportement de manipulation, précédemment trouvé dans *ManipulationHandler*.</span><span class="sxs-lookup"><span data-stu-id="21479-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="21479-107">Le manipulateur d’objets apporte un certain nombre d’améliorations et de simplifications.</span><span class="sxs-lookup"><span data-stu-id="21479-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="21479-108">Ce composant remplace le gestionnaire de manipulation, qui sera déconseillé.</span><span class="sxs-lookup"><span data-stu-id="21479-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="21479-109">Le script *ObjectManipulator* rend un objet déplaçable, évolutif et rotatif à l’aide d’une ou de deux mains.</span><span class="sxs-lookup"><span data-stu-id="21479-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="21479-110">Le manipulateur d’objets peut être configuré pour contrôler la façon dont l’objet répondra à différentes entrées.</span><span class="sxs-lookup"><span data-stu-id="21479-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="21479-111">le script doit fonctionner avec la plupart des formes d’interaction, telles que HoloLens 2 articulées, HoloLens 2 rayons, HoloLens 1 point de regard, les gestes et l’entrée du contrôleur de mouvement du casque immersif.</span><span class="sxs-lookup"><span data-stu-id="21479-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="21479-112">Comment utiliser le manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="21479-112">How to use the object manipulator</span></span>

<span data-ttu-id="21479-113">Pour utiliser le manipulateur d’objets, ajoutez d’abord le `ObjectManipulator` composant script à un GameObject.</span><span class="sxs-lookup"><span data-stu-id="21479-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="21479-114">Veillez à ajouter également un conflit à l’objet, en faisant correspondre ses limites récupérables.</span><span class="sxs-lookup"><span data-stu-id="21479-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="21479-115">Pour faire en sorte que l’objet réponde à une entrée presque articulée, ajoutez `NearInteractionGrabbable` également le script.</span><span class="sxs-lookup"><span data-stu-id="21479-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="21479-116">Le comportement physique peut être activé pour le manipulateur d’objets en ajoutant un composant RigidBody à l’objet.</span><span class="sxs-lookup"><span data-stu-id="21479-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="21479-117">Le comportement physique activé par l’ajout de ce composant est abordé plus en détail dans [*physique et collisions*](#physics-and-collisions).</span><span class="sxs-lookup"><span data-stu-id="21479-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="21479-118">De même, la manipulation peut être contrainte en ajoutant des composants de [contrainte de manipulation](constraint-manager.md#transform-constraints) à l’objet.</span><span class="sxs-lookup"><span data-stu-id="21479-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="21479-119">Il s’agit de composants spéciaux qui fonctionnent avec la manipulation et modifient le comportement de manipulation d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="21479-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Utilisation du gestionnaire de manipulation dans l’éditeur Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="21479-121">Propriétés et champs de l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="21479-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="21479-122">Propriétés générales</span><span class="sxs-lookup"><span data-stu-id="21479-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="21479-123">Transformation de l’hôte</span><span class="sxs-lookup"><span data-stu-id="21479-123">Host transform</span></span>

<span data-ttu-id="21479-124">Transformation d’objet qui sera manipulée.</span><span class="sxs-lookup"><span data-stu-id="21479-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="21479-125">La valeur par défaut est l’objet du composant.</span><span class="sxs-lookup"><span data-stu-id="21479-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="21479-126">Type de manipulation</span><span class="sxs-lookup"><span data-stu-id="21479-126">Manipulation type</span></span>

<span data-ttu-id="21479-127">Spécifie si l’objet peut être manipulé à l’aide d’une main ou de deux mains.</span><span class="sxs-lookup"><span data-stu-id="21479-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="21479-128">Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="21479-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="21479-129">*Une droitier*: active une manipulation de la main si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="21479-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="21479-130">*Deux droitiers*: active deux manipulations de la main si elles sont sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="21479-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="21479-131">Autoriser la manipulation Far</span><span class="sxs-lookup"><span data-stu-id="21479-131">Allow far manipulation</span></span>

<span data-ttu-id="21479-132">Spécifie si la manipulation peut être effectuée à l’aide de l’interaction Far avec les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="21479-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="21479-133">Propriétés de manipulation à une seule main</span><span class="sxs-lookup"><span data-stu-id="21479-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="21479-134">Mode de rotation à un seul côté</span><span class="sxs-lookup"><span data-stu-id="21479-134">One hand rotation mode near</span></span>

<span data-ttu-id="21479-135">Spécifie la manière dont l’objet se comporte lorsqu’il est retiré d’une main à proximité.</span><span class="sxs-lookup"><span data-stu-id="21479-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="21479-136">Ces options ne fonctionnent que pour les mains articulées.</span><span class="sxs-lookup"><span data-stu-id="21479-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="21479-137">*Faire pivoter à propos du centre d’objets*: l’objet pivote à l’aide de la rotation de la main, mais à propos du point central de l’objet.</span><span class="sxs-lookup"><span data-stu-id="21479-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="21479-138">L’objet s’affiche pour se déplacer moins au fur et à mesure qu’il pivote, mais il peut y avoir un sentiment de déconnexion entre la main et l’objet.</span><span class="sxs-lookup"><span data-stu-id="21479-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="21479-139">Plus utile pour une interaction extrême.</span><span class="sxs-lookup"><span data-stu-id="21479-139">More useful for far interaction.</span></span>
- <span data-ttu-id="21479-140">*Faire pivoter à propos du point de manipulation*: faire pivoter un objet à la main sur le point de manipulation entre le curseur de défilement et l’index.</span><span class="sxs-lookup"><span data-stu-id="21479-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="21479-141">Elle doit ressembler à si l’objet est détenu par la main.</span><span class="sxs-lookup"><span data-stu-id="21479-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="21479-142">Mode de rotation d’un côté</span><span class="sxs-lookup"><span data-stu-id="21479-142">One hand rotation mode far</span></span>

<span data-ttu-id="21479-143">Spécifie la manière dont l’objet se comporte lorsqu’il est retiré d’une main à distance.</span><span class="sxs-lookup"><span data-stu-id="21479-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="21479-144">Ces options ne fonctionnent que pour les mains articulées.</span><span class="sxs-lookup"><span data-stu-id="21479-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="21479-145">*Faire pivoter à propos de Object Center*: faire pivoter l’objet à l’aide de la rotation de la main, mais à propos du point central de l’objet.</span><span class="sxs-lookup"><span data-stu-id="21479-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="21479-146">Utile pour l’inspection à distance sans que le centre d’objets se déplace au fur et à mesure que l’objet pivote.</span><span class="sxs-lookup"><span data-stu-id="21479-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="21479-147">*Faire pivoter à propos du point de manipulation*: faire pivoter l’objet à l’aide de la rotation de la main, mais à propos du point d’accès de Ray</span><span class="sxs-lookup"><span data-stu-id="21479-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="21479-148">Utile pour l’inspection.</span><span class="sxs-lookup"><span data-stu-id="21479-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="21479-149">Deux propriétés de manipulation de la main</span><span class="sxs-lookup"><span data-stu-id="21479-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="21479-150">Type de manipulation à deux mains</span><span class="sxs-lookup"><span data-stu-id="21479-150">Two handed manipulation type</span></span>

<span data-ttu-id="21479-151">Spécifie la manière dont deux manipulations de main peuvent transformer un objet.</span><span class="sxs-lookup"><span data-stu-id="21479-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="21479-152">Étant donné que cette propriété est un indicateur, vous pouvez sélectionner n’importe quel nombre d’options.</span><span class="sxs-lookup"><span data-stu-id="21479-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="21479-153">*Move*: le déplacement est autorisé si l’option est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="21479-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="21479-154">*Scale*: la mise à l’échelle est autorisée si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="21479-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="21479-155">*Rotate*: la rotation est autorisée si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="21479-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Gestionnaire de manipulation](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="21479-157">Contraintes</span><span class="sxs-lookup"><span data-stu-id="21479-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="21479-158">Activer les contraintes</span><span class="sxs-lookup"><span data-stu-id="21479-158">Enable constraints</span></span>

<span data-ttu-id="21479-159">Ce paramètre active le gestionnaire de [contraintes](constraint-manager.md)lié.</span><span class="sxs-lookup"><span data-stu-id="21479-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="21479-160">Les modifications de transformation sont traitées par les contraintes inscrites dans le [Gestionnaire de contraintes](constraint-manager.md)sélectionné.</span><span class="sxs-lookup"><span data-stu-id="21479-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="21479-161">Gestionnaire de contraintes</span><span class="sxs-lookup"><span data-stu-id="21479-161">Constraint manager</span></span>

<span data-ttu-id="21479-162">La liste déroulante permet de sélectionner l’un des [gestionnaires de contraintes](constraint-manager.md)attachés.</span><span class="sxs-lookup"><span data-stu-id="21479-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="21479-163">Le manipulateur d’objets s’assure qu’un [Gestionnaire de contraintes](constraint-manager.md) est attaché à tout moment.</span><span class="sxs-lookup"><span data-stu-id="21479-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="21479-164">Notez que plusieurs composants du même type s’affichent sous le même nom dans Unity.</span><span class="sxs-lookup"><span data-stu-id="21479-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="21479-165">Pour faciliter la distinction entre plusieurs gestionnaires de contraintes sur le même objet, les options disponibles présentent un indicateur sur la configuration du gestionnaire de contraintes sélectionné (sélection de contrainte manuelle ou automatique).</span><span class="sxs-lookup"><span data-stu-id="21479-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="21479-166">Atteindre le composant</span><span class="sxs-lookup"><span data-stu-id="21479-166">Go to component</span></span>

<span data-ttu-id="21479-167">La sélection du gestionnaire de contraintes est accompagnée d’un bouton *atteindre le composant* .</span><span class="sxs-lookup"><span data-stu-id="21479-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="21479-168">Ce bouton permet à l’inspecteur de faire défiler le composant sélectionné afin qu’il puisse être configuré.</span><span class="sxs-lookup"><span data-stu-id="21479-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="21479-169">Physique</span><span class="sxs-lookup"><span data-stu-id="21479-169">Physics</span></span>

<span data-ttu-id="21479-170">Paramètres dans cette section s’affichent uniquement lorsque l’objet a un composant RigidBody.</span><span class="sxs-lookup"><span data-stu-id="21479-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="21479-171">Comportement de la version</span><span class="sxs-lookup"><span data-stu-id="21479-171">Release behavior</span></span>

<span data-ttu-id="21479-172">Spécifiez les propriétés physiques qu’un objet manipulé doit conserver lors de la libération.</span><span class="sxs-lookup"><span data-stu-id="21479-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="21479-173">Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="21479-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="21479-174">*Conserver la vélocité*: lorsque l’objet est relâché, si cette option est sélectionnée, elle conserve sa vélocité linéaire.</span><span class="sxs-lookup"><span data-stu-id="21479-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="21479-175">*conserver Angular vélocité*: lorsque l’objet est relâché, si cette option est sélectionnée, elle conserve sa vélocité angulaire.</span><span class="sxs-lookup"><span data-stu-id="21479-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="21479-176">Utiliser des forces pour la manipulation proche</span><span class="sxs-lookup"><span data-stu-id="21479-176">Use forces for near manipulation</span></span>

<span data-ttu-id="21479-177">Indique si les forces physiques sont utilisées pour déplacer l’objet lors de l’exécution de la manipulation proche.</span><span class="sxs-lookup"><span data-stu-id="21479-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="21479-178">Si vous affectez la *valeur false* , l’objet sera plus directement connecté à la main des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="21479-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="21479-179">Si vous affectez la *valeur true* , vous honorerez la masse et l’inertie de l’objet, mais cela peut être semblable au fait que l’objet est connecté via un ressort.</span><span class="sxs-lookup"><span data-stu-id="21479-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="21479-180">La valeur par défaut est *false*.</span><span class="sxs-lookup"><span data-stu-id="21479-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="21479-181">Adoucissage</span><span class="sxs-lookup"><span data-stu-id="21479-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="21479-182">Lissage Far</span><span class="sxs-lookup"><span data-stu-id="21479-182">Smoothing far</span></span>

<span data-ttu-id="21479-183">Indique si le lissage indépendant de la cadence d’images est activé pour les interactions Far.</span><span class="sxs-lookup"><span data-stu-id="21479-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="21479-184">Le lissage FAR est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="21479-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="21479-185">Lissage à proximité</span><span class="sxs-lookup"><span data-stu-id="21479-185">Smoothing near</span></span>

<span data-ttu-id="21479-186">Indique si le lissage indépendant de la cadence d’images est activé pour les interactions proches.</span><span class="sxs-lookup"><span data-stu-id="21479-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="21479-187">Le lissage proche est désactivé par défaut, car l’effet peut être perçu comme étant « déconnecté » de la main.</span><span class="sxs-lookup"><span data-stu-id="21479-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="21479-188">Lissage actif</span><span class="sxs-lookup"><span data-stu-id="21479-188">Smoothing active</span></span>

<span data-ttu-id="21479-189">Obsolète et sera supprimé dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="21479-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="21479-190">Les applications doivent utiliser SmoothingFar, SmoothingNear ou une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="21479-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="21479-191">Déplacer le temps de Lerp</span><span class="sxs-lookup"><span data-stu-id="21479-191">Move lerp time</span></span>

<span data-ttu-id="21479-192">Quantité de lissage à appliquer au mouvement.</span><span class="sxs-lookup"><span data-stu-id="21479-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="21479-193">Le lissage de 0 signifie qu’il n’y a pas de lissage.</span><span class="sxs-lookup"><span data-stu-id="21479-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="21479-194">La valeur Max signifie qu’aucune modification n’est apportée à la valeur.</span><span class="sxs-lookup"><span data-stu-id="21479-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="21479-195">Faire pivoter Lerp Time</span><span class="sxs-lookup"><span data-stu-id="21479-195">Rotate lerp time</span></span>

<span data-ttu-id="21479-196">Quantité de lissage à appliquer à la rotation.</span><span class="sxs-lookup"><span data-stu-id="21479-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="21479-197">Le lissage de 0 signifie qu’il n’y a pas de lissage.</span><span class="sxs-lookup"><span data-stu-id="21479-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="21479-198">La valeur Max signifie qu’aucune modification n’est apportée à la valeur.</span><span class="sxs-lookup"><span data-stu-id="21479-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="21479-199">Mettre à l’échelle le temps Lerp</span><span class="sxs-lookup"><span data-stu-id="21479-199">Scale lerp time</span></span>

<span data-ttu-id="21479-200">Quantité de lissage à appliquer à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="21479-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="21479-201">Le lissage de 0 signifie qu’il n’y a pas de lissage.</span><span class="sxs-lookup"><span data-stu-id="21479-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="21479-202">La valeur Max signifie qu’aucune modification n’est apportée à la valeur.</span><span class="sxs-lookup"><span data-stu-id="21479-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="21479-203">Événements de manipulation</span><span class="sxs-lookup"><span data-stu-id="21479-203">Manipulation events</span></span>

<span data-ttu-id="21479-204">Le gestionnaire de manipulation fournit les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="21479-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="21479-205">*OnManipulationStarted*: déclenché lorsque la manipulation démarre.</span><span class="sxs-lookup"><span data-stu-id="21479-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="21479-206">*OnManipulationEnded*: se déclenche lorsque la manipulation se termine.</span><span class="sxs-lookup"><span data-stu-id="21479-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="21479-207">*OnHoverStarted*: se déclenche quand une main/un contrôleur pointe le manipulable, proche ou loin.</span><span class="sxs-lookup"><span data-stu-id="21479-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="21479-208">*OnHoverEnded*: se déclenche quand une main/un contrôleur ne fait pas pointer le manipulable, à proximité ou à l’extrême.</span><span class="sxs-lookup"><span data-stu-id="21479-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="21479-209">L’ordre de déclenchement des événements pour la manipulation est le suivant :</span><span class="sxs-lookup"><span data-stu-id="21479-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="21479-210">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="21479-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="21479-211">S’il n’y a aucune manipulation, vous obtiendrez toujours des événements de pointage avec l’ordre de déclenchement suivant :</span><span class="sxs-lookup"><span data-stu-id="21479-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="21479-212">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="21479-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="21479-213">Physique et collisions</span><span class="sxs-lookup"><span data-stu-id="21479-213">Physics and collisions</span></span>

<span data-ttu-id="21479-214">Le comportement physique peut être activé en ajoutant un composant RigidBody au même objet qu’un manipulateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="21479-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="21479-215">Non seulement cela permet la configuration du [comportement de mise en version](#release-behavior) ci-dessus, mais elle active également les collisions.</span><span class="sxs-lookup"><span data-stu-id="21479-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="21479-216">Sans composant RigidBody, les collisions ne se comportent pas correctement pendant la manipulation :</span><span class="sxs-lookup"><span data-stu-id="21479-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="21479-217">Les collisions entre un objet manipulé et un conflit statique (c’est-à-dire un objet avec un conflit mais sans RigidBody) ne fonctionnent pas, l’objet manipulé passe directement par le conflit statique qui n’est pas affecté.</span><span class="sxs-lookup"><span data-stu-id="21479-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="21479-218">Collisions entre un objet manipulé et un RigidBody (c.-à-d.</span><span class="sxs-lookup"><span data-stu-id="21479-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="21479-219">un objet avec à la fois un conflit et un RigidBody) entraîne une réponse de collision du RigidBody, mais la réponse est indirecte et non naturelle.</span><span class="sxs-lookup"><span data-stu-id="21479-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="21479-220">Il n’y a pas non plus de réponse de collision sur l’objet manipulé.</span><span class="sxs-lookup"><span data-stu-id="21479-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="21479-221">Quand un RigidBody est ajouté, les collisions doivent fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="21479-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="21479-222">Sans RigidBody</span><span class="sxs-lookup"><span data-stu-id="21479-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="21479-223">Avec RigidBody</span><span class="sxs-lookup"><span data-stu-id="21479-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="21479-224">Élastiques (expérimental)</span><span class="sxs-lookup"><span data-stu-id="21479-224">Elastics (Experimental)</span></span>

<span data-ttu-id="21479-225">Les élastiques peuvent être utilisés lors de la manipulation d’objets via le manipulateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="21479-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="21479-226">Notez que le [système élastiques](../experimental/elastic-system.md) est toujours dans un État expérimental.</span><span class="sxs-lookup"><span data-stu-id="21479-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="21479-227">Pour activer les élastiques, liez un composant Gestionnaire élastique existant ou créez et liez un nouveau gestionnaire élastiques à l’aide du `Add Elastics Manager` bouton.</span><span class="sxs-lookup"><span data-stu-id="21479-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="21479-228">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21479-228">See also</span></span>

- [<span data-ttu-id="21479-229">Contrôle de limites</span><span class="sxs-lookup"><span data-stu-id="21479-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="21479-230">Gestionnaire de contraintes</span><span class="sxs-lookup"><span data-stu-id="21479-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="21479-231">Fenêtre de migration</span><span class="sxs-lookup"><span data-stu-id="21479-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="21479-232">Système élastique (expérimental)</span><span class="sxs-lookup"><span data-stu-id="21479-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
