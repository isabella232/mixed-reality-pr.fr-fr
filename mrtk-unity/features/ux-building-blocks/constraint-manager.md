---
title: Gestionnaire de contraintes
description: Vue d’ensemble du gestionnaire de contraintes dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177550"
---
# <a name="constraint-manager"></a><span data-ttu-id="18105-104">Gestionnaire de contraintes</span><span class="sxs-lookup"><span data-stu-id="18105-104">Constraint manager</span></span>

<span data-ttu-id="18105-105">Le gestionnaire de contraintes permet d’appliquer un ensemble de composants de contrainte à une transformation.</span><span class="sxs-lookup"><span data-stu-id="18105-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="18105-106">Les composants de type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) qui sont attachés à l’objet de jeu peuvent être pris en compte.</span><span class="sxs-lookup"><span data-stu-id="18105-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="18105-107">Par défaut, le gestionnaire de contraintes collecte automatiquement tous les [composants de contrainte](#transform-constraints) attachés à l’objet de jeu et les applique aux transformations traitées.</span><span class="sxs-lookup"><span data-stu-id="18105-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="18105-108">Toutefois, les utilisateurs peuvent opter pour la configuration manuelle de la liste des contraintes appliquées et autoriser uniquement l’application d’un sous-ensemble de contraintes attachées.</span><span class="sxs-lookup"><span data-stu-id="18105-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="18105-109">Actuellement, les éléments MRTK UX suivants prennent en charge le gestionnaire de contraintes :</span><span class="sxs-lookup"><span data-stu-id="18105-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="18105-110">Contrôle de limites</span><span class="sxs-lookup"><span data-stu-id="18105-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="18105-111">Manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="18105-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="18105-112">Propriétés et champs de l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="18105-112">Inspector properties and fields</span></span>

<span data-ttu-id="18105-113">Le gestionnaire de contraintes peut être utilisé en deux modes :</span><span class="sxs-lookup"><span data-stu-id="18105-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="18105-114">Sélection de contrainte automatique</span><span class="sxs-lookup"><span data-stu-id="18105-114">Auto constraint selection</span></span>
- <span data-ttu-id="18105-115">Sélection manuelle des contraintes</span><span class="sxs-lookup"><span data-stu-id="18105-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="18105-116">Sélection de contrainte automatique</span><span class="sxs-lookup"><span data-stu-id="18105-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="18105-117">Le mode par défaut du gestionnaire de contraintes, la sélection de contrainte automatique, fournit une liste de tous les composants de contrainte attachés, ainsi que les [boutons](#go-to-component) et le [bouton Ajouter une contrainte](#add-constraint-to-game-object).</span><span class="sxs-lookup"><span data-stu-id="18105-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="18105-118">Ajouter une contrainte à un objet de jeu</span><span class="sxs-lookup"><span data-stu-id="18105-118">Add constraint to game object</span></span>

<span data-ttu-id="18105-119">Ce bouton permet d’ajouter un composant de contrainte directement à partir de l’inspecteur du gestionnaire de contraintes.</span><span class="sxs-lookup"><span data-stu-id="18105-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="18105-120">Tous les types de contrainte d’un projet doivent être visibles ici.</span><span class="sxs-lookup"><span data-stu-id="18105-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="18105-121">Pour plus d’informations, consultez [contraintes de transformation](#transform-constraints) .</span><span class="sxs-lookup"><span data-stu-id="18105-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="18105-122">Atteindre le composant</span><span class="sxs-lookup"><span data-stu-id="18105-122">Go to component</span></span>

<span data-ttu-id="18105-123">Toutes les contraintes trouvées sur l’objet sont répertoriées ici avec un bouton *atteindre le composant* .</span><span class="sxs-lookup"><span data-stu-id="18105-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="18105-124">Ce bouton permet à l’inspecteur de faire défiler le composant de contrainte sélectionné afin qu’il puisse être configuré.</span><span class="sxs-lookup"><span data-stu-id="18105-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="18105-125">Sélection manuelle des contraintes</span><span class="sxs-lookup"><span data-stu-id="18105-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="18105-126">Si le gestionnaire de contraintes est défini en mode manuel, seules les contraintes qui sont liées dans la liste de contraintes sont traitées et appliquées à la transformation.</span><span class="sxs-lookup"><span data-stu-id="18105-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="18105-127">La liste affichée affiche uniquement les contraintes sélectionnées par l’utilisateur, ainsi que les [boutons](#go-to-component) ou options permettant de supprimer ou d’ajouter des entrées.</span><span class="sxs-lookup"><span data-stu-id="18105-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="18105-128">Lorsque vous activez le mode manuel pour la première fois, le gestionnaire de contraintes remplit la liste tous les composants disponibles comme point de départ pour sélectionner les composants de contrainte attachés.</span><span class="sxs-lookup"><span data-stu-id="18105-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="18105-129">Supprimer l’entrée</span><span class="sxs-lookup"><span data-stu-id="18105-129">Remove entry</span></span>

<span data-ttu-id="18105-130">Cela supprime l’entrée de la liste sélectionnée manuellement.</span><span class="sxs-lookup"><span data-stu-id="18105-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="18105-131">Notez que cette option ne supprime pas le composant de contrainte de l’objet de jeu.</span><span class="sxs-lookup"><span data-stu-id="18105-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="18105-132">Les composants de contrainte doivent toujours être supprimés manuellement pour éviter toute rupture accidentelle d’un autre composant faisant référence à ce composant.</span><span class="sxs-lookup"><span data-stu-id="18105-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="18105-133">Ajouter une entrée</span><span class="sxs-lookup"><span data-stu-id="18105-133">Add entry</span></span>

<span data-ttu-id="18105-134">Ajouter une entrée ouvre une liste déroulante indiquant tous les composants de contrainte disponibles qui ne sont pas encore dans la liste manuelle.</span><span class="sxs-lookup"><span data-stu-id="18105-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="18105-135">En cliquant sur l’une des entrées que le composant sera ajouté à la sélection de contrainte manuelle.</span><span class="sxs-lookup"><span data-stu-id="18105-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="18105-136">Ajouter une nouvelle contrainte</span><span class="sxs-lookup"><span data-stu-id="18105-136">Add new constraint</span></span>

<span data-ttu-id="18105-137">Cette option permet d’ajouter un composant du type sélectionné à l’objet de jeu et d’ajouter le composant de contrainte nouvellement créé à la liste de contraintes manuelle.</span><span class="sxs-lookup"><span data-stu-id="18105-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="18105-138">Contraintes de transformation</span><span class="sxs-lookup"><span data-stu-id="18105-138">Transform constraints</span></span>

<span data-ttu-id="18105-139">Les contraintes peuvent être utilisées pour limiter la manipulation d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="18105-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="18105-140">Par exemple, certaines applications peuvent nécessiter une rotation, mais nécessitent également que l’objet reste debout.</span><span class="sxs-lookup"><span data-stu-id="18105-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="18105-141">Dans ce cas, un `RotationAxisConstraint` peut être ajouté à l’objet et utilisé pour limiter la rotation à la rotation de l’axe y.</span><span class="sxs-lookup"><span data-stu-id="18105-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="18105-142">MRTK fournit un certain nombre de contraintes, qui sont toutes décrites ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="18105-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="18105-143">Il est également possible de définir de nouvelles contraintes et de les utiliser pour créer des comportements de manipulation uniques qui peuvent être nécessaires pour certaines applications.</span><span class="sxs-lookup"><span data-stu-id="18105-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="18105-144">Pour ce faire, créez un script qui hérite de [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) et implémentez la `ConstraintType` propriété abstraite et la méthode abstraite `ApplyConstraint` .</span><span class="sxs-lookup"><span data-stu-id="18105-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="18105-145">Lors de l’ajout d’une nouvelle contrainte à l’objet, elle doit contraindre la manipulation de la manière définie.</span><span class="sxs-lookup"><span data-stu-id="18105-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="18105-146">Cette nouvelle contrainte doit également apparaître dans la liste déroulante gestionnaire de contraintes [automatique](#auto-constraint-selection) ou [Ajouter une entrée](#add-entry) en mode manuel.</span><span class="sxs-lookup"><span data-stu-id="18105-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="18105-147">Toutes les contraintes fournies par MRTK partagent les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="18105-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="18105-148">Type de main</span><span class="sxs-lookup"><span data-stu-id="18105-148">Hand Type</span></span>

<span data-ttu-id="18105-149">Spécifie si la contrainte est utilisée pour une main, deux types de manipulation ou les deux.</span><span class="sxs-lookup"><span data-stu-id="18105-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="18105-150">Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="18105-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="18105-151">*Une droitier*: la contrainte sera utilisée pendant une manipulation de la droitier, si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18105-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="18105-152">*Deux droitiers*: la contrainte sera utilisée pendant deux manipulations de la main, si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18105-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="18105-153">Type de proximité</span><span class="sxs-lookup"><span data-stu-id="18105-153">Proximity Type</span></span>

<span data-ttu-id="18105-154">Spécifie si la contrainte est utilisée pour les genres near ou FAR, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="18105-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="18105-155">Étant donné que cette propriété est un indicateur, les deux options peuvent être sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="18105-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="18105-156">*Near*: la contrainte sera utilisée pendant une manipulation proche si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18105-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="18105-157">*Far*: la contrainte sera utilisée lors de la manipulation Far si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18105-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="18105-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="18105-159">Lorsque cette contrainte est attachée à un objet, la rotation est limitée afin que l’objet soit toujours à la tête de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="18105-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="18105-160">Cela est utile pour les ardoises ou les panneaux.</span><span class="sxs-lookup"><span data-stu-id="18105-160">This is useful for slates or panels.</span></span> <span data-ttu-id="18105-161">Les propriétés de `FaceUserConstraint` sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="18105-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="18105-162">Facer</span><span class="sxs-lookup"><span data-stu-id="18105-162">Face away</span></span>

<span data-ttu-id="18105-163">L’objet est face à l’utilisateur si la valeur est true.</span><span class="sxs-lookup"><span data-stu-id="18105-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="18105-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="18105-165">Cette contrainte fixe la distance entre l’objet manipulé et une autre transformation d’objet au début de la manipulation.</span><span class="sxs-lookup"><span data-stu-id="18105-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="18105-166">Cela est utile pour le comportement, par exemple la résolution de la distance entre l’objet manipulé et la transformation de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="18105-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="18105-167">Les propriétés de `FixedDistanceConstraint` sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="18105-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="18105-168">Transformation de contrainte</span><span class="sxs-lookup"><span data-stu-id="18105-168">Constraint transform</span></span>

<span data-ttu-id="18105-169">Il s’agit de l’autre transformation que l’objet manipulé aura une distance fixe.</span><span class="sxs-lookup"><span data-stu-id="18105-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="18105-170">La valeur par défaut est la transformation de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="18105-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="18105-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="18105-172">Cette contrainte résout la rotation relative entre l’utilisateur et l’objet manipulé pendant qu’il est manipulé.</span><span class="sxs-lookup"><span data-stu-id="18105-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="18105-173">Cela est utile pour les ardoises ou les panneaux, car il garantit que l’objet manipulé affiche toujours la même face à l’utilisateur qu’au début de la manipulation.</span><span class="sxs-lookup"><span data-stu-id="18105-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="18105-174">Le `FixedRotationToUserConstraint` n’a pas de propriétés uniques.</span><span class="sxs-lookup"><span data-stu-id="18105-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="18105-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="18105-176">Cette contrainte résout la rotation globale de l’objet manipulé pendant qu’il est manipulé.</span><span class="sxs-lookup"><span data-stu-id="18105-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="18105-177">Cela peut être utile dans les cas où aucune rotation ne doit être concédée par une manipulation.</span><span class="sxs-lookup"><span data-stu-id="18105-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="18105-178">Le `FixedRotationToWorldConstraint` n’a pas de propriétés uniques :</span><span class="sxs-lookup"><span data-stu-id="18105-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="18105-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="18105-180">Lorsque cette contrainte est attachée à un objet, quelle que soit la portée de l’objet par rapport à l’utilisateur, elle conserve la même taille apparente pour l’utilisateur (autrement dit, elle prend la même proportion du champ de vue de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="18105-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="18105-181">Cela peut être utilisé pour s’assurer qu’un ardoise ou un panneau de texte restent lisibles lors de la manipulation.</span><span class="sxs-lookup"><span data-stu-id="18105-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="18105-182">Le `MaintainApparentSizeConstraint` n’a pas de propriétés uniques :</span><span class="sxs-lookup"><span data-stu-id="18105-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="18105-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="18105-184">Cette contrainte peut être utilisée pour résoudre les axes sur lesquels un objet manipulé peut être déplacé.</span><span class="sxs-lookup"><span data-stu-id="18105-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="18105-185">Cela peut être utile pour manipuler des objets sur la surface d’un plan ou sur une ligne.</span><span class="sxs-lookup"><span data-stu-id="18105-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="18105-186">Les propriétés de `MoveAxisConstraint` sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="18105-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="18105-187">Contrainte de mouvement</span><span class="sxs-lookup"><span data-stu-id="18105-187">Constraint on movement</span></span>

<span data-ttu-id="18105-188">Spécifie les axes sur lesquels le déplacement doit être interdit.</span><span class="sxs-lookup"><span data-stu-id="18105-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="18105-189">Par défaut, ces axes sont globaux plutôt que locaux, mais cela peut être modifié ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="18105-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="18105-190">Étant donné que cette propriété est un indicateur, vous pouvez sélectionner n’importe quel nombre d’options.</span><span class="sxs-lookup"><span data-stu-id="18105-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="18105-191">*Axe des x*: le mouvement le long de l’axe x est restreint s’il est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="18105-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="18105-192">*Axe y*: le mouvement le long de l’axe y est restreint s’il est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="18105-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="18105-193">*Axe z*: le mouvement le long de l’axe z est restreint s’il est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="18105-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="18105-194">Utiliser l’espace local pour la contrainte</span><span class="sxs-lookup"><span data-stu-id="18105-194">Use local space for constraint</span></span>

<span data-ttu-id="18105-195">Applique une contrainte relative aux axes de transformation locaux de l’objet manipulé si la valeur est true.</span><span class="sxs-lookup"><span data-stu-id="18105-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="18105-196">False par défaut.</span><span class="sxs-lookup"><span data-stu-id="18105-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="18105-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="18105-198">Cette contrainte peut être utilisée pour résoudre les axes sur lesquels un objet manipulé peut pivoter.</span><span class="sxs-lookup"><span data-stu-id="18105-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="18105-199">Cela peut être utile pour maintenir un objet manipulé à la verticale, tout en autorisant les rotations de l’axe y, par exemple.</span><span class="sxs-lookup"><span data-stu-id="18105-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="18105-200">Les propriétés de `RotationAxisConstraint` sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="18105-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="18105-201">Contrainte de rotation</span><span class="sxs-lookup"><span data-stu-id="18105-201">Constraint on rotation</span></span>

<span data-ttu-id="18105-202">Spécifie les axes à propos desquels empêcher la rotation.</span><span class="sxs-lookup"><span data-stu-id="18105-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="18105-203">Par défaut, ces axes sont globaux plutôt que locaux, mais cela peut être modifié ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="18105-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="18105-204">Étant donné que cette propriété est un indicateur, vous pouvez sélectionner n’importe quel nombre d’options.</span><span class="sxs-lookup"><span data-stu-id="18105-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="18105-205">*Axe y*: la rotation autour de l’axe des y est restreinte si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18105-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="18105-206">*Axe z*: la rotation autour de l’axe z est restreinte si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18105-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="18105-207">*Axe x*: la rotation autour de l’axe des x est restreinte si elle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="18105-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="18105-208">Utiliser l’espace local pour la contrainte</span><span class="sxs-lookup"><span data-stu-id="18105-208">Use local space for constraint</span></span>

<span data-ttu-id="18105-209">Applique une contrainte relative aux axes de transformation locaux de l’objet manipulé si la valeur est true.</span><span class="sxs-lookup"><span data-stu-id="18105-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="18105-210">False par défaut.</span><span class="sxs-lookup"><span data-stu-id="18105-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="18105-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="18105-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="18105-212">Cette contrainte permet de définir des valeurs minimales et maximales pour l’échelle de l’objet manipulé.</span><span class="sxs-lookup"><span data-stu-id="18105-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="18105-213">Cela est utile pour empêcher les utilisateurs de mettre à l’échelle un objet trop petit ou trop grand.</span><span class="sxs-lookup"><span data-stu-id="18105-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="18105-214">Les propriétés de `MinMaxScaleConstraint` sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="18105-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="18105-215">Échelle minimale</span><span class="sxs-lookup"><span data-stu-id="18105-215">Scale minimum</span></span>

<span data-ttu-id="18105-216">Valeur de mise à l’échelle minimale pendant la manipulation.</span><span class="sxs-lookup"><span data-stu-id="18105-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="18105-217">Échelle maximale</span><span class="sxs-lookup"><span data-stu-id="18105-217">Scale maximum</span></span>

<span data-ttu-id="18105-218">Valeur d’échelle maximale pendant la manipulation.</span><span class="sxs-lookup"><span data-stu-id="18105-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="18105-219">Par rapport à l’état initial</span><span class="sxs-lookup"><span data-stu-id="18105-219">Relative to initial state</span></span>

<span data-ttu-id="18105-220">Si la valeur est true, les valeurs ci-dessus seront interprétées par rapport à l’échelle initiale des objets.</span><span class="sxs-lookup"><span data-stu-id="18105-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="18105-221">Dans le cas contraire, ils seront interprétés comme des valeurs de mise à l’échelle absolue.</span><span class="sxs-lookup"><span data-stu-id="18105-221">Otherwise they will be interpreted as absolute scale values.</span></span>
