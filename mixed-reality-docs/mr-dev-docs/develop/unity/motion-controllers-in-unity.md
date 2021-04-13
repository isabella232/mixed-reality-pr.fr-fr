---
title: Contrôleurs de mouvement dans Unity
description: Apprenez à prendre des mesures sur votre point de regard avec l’entrée de contrôleur de mouvement à l’aide de XR et des API de bouton et d’axe courantes.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: contrôleurs de mouvement, Unity, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: d3df49c2f6c626e9f4eb47c38f4a8e61059a8438
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300474"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="29042-104">Contrôleurs de mouvement dans Unity</span><span class="sxs-lookup"><span data-stu-id="29042-104">Motion controllers in Unity</span></span>

<span data-ttu-id="29042-105">Il existe deux façons principales d’agir sur votre point [de regard](gaze-in-unity.md), les [gestes manuels](../../design/gaze-and-commit.md#composite-gestures) et les [contrôleurs de mouvement](../../design/motion-controllers.md) dans HoloLens et les HMD immersifs.</span><span class="sxs-lookup"><span data-stu-id="29042-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="29042-106">Vous accédez aux données des deux sources d’entrée spatiale via les mêmes API dans Unity.</span><span class="sxs-lookup"><span data-stu-id="29042-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="29042-107">Unity fournit deux méthodes principales pour accéder aux données d’entrée spatiale pour Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="29042-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="29042-108">Les API *d’entrée. GetButton/Input. GetAxis* courantes fonctionnent sur plusieurs kits de développement logiciel (SDK) XR, tandis que l’API *InteractionManager/GestureRecognizer* propre à Windows Mixed Reality expose l’ensemble complet des données d’entrée spatiale.</span><span class="sxs-lookup"><span data-stu-id="29042-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="29042-109">API d’entrée Unity XR</span><span class="sxs-lookup"><span data-stu-id="29042-109">Unity XR input APIs</span></span>

<span data-ttu-id="29042-110">Pour les nouveaux projets, nous vous recommandons d’utiliser les nouvelles API d’entrée XR dès le début.</span><span class="sxs-lookup"><span data-stu-id="29042-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="29042-111">Vous trouverez plus d’informations sur les [API XR ici](https://docs.unity3d.com/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="29042-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="29042-112">Bouton Unity/table de mappage des axes</span><span class="sxs-lookup"><span data-stu-id="29042-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="29042-113">Le gestionnaire d’entrée Unity pour les contrôleurs de mouvement Windows Mixed Reality prend en charge les ID de bouton et d’axe listés ci-dessous via les API *Input. GetButton/GetAxis* .</span><span class="sxs-lookup"><span data-stu-id="29042-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="29042-114">La colonne « propre à Windows MR » fait référence aux propriétés disponibles à partir du type *InteractionSourceState* .</span><span class="sxs-lookup"><span data-stu-id="29042-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="29042-115">Chacune de ces API est décrite en détail dans les sections ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="29042-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="29042-116">Les mappages de bouton/ID d’axe pour Windows Mixed Reality correspondent généralement aux ID d’axe/bouton Oculus.</span><span class="sxs-lookup"><span data-stu-id="29042-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="29042-117">Les mappages de bouton/ID d’axe pour Windows Mixed Reality diffèrent des mappages de OpenVR de deux façons :</span><span class="sxs-lookup"><span data-stu-id="29042-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="29042-118">Le mappage utilise des ID de pavé tactile distincts du stick analogique, pour prendre en charge des contrôleurs avec Thumbsticks et des pavés tactiles.</span><span class="sxs-lookup"><span data-stu-id="29042-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="29042-119">Le mappage évite de surcharger les ID de bouton A et X pour les boutons de menu afin de les rendre disponibles pour les boutons ABXY physiques.</span><span class="sxs-lookup"><span data-stu-id="29042-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="29042-120">Entrée</span><span class="sxs-lookup"><span data-stu-id="29042-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="29042-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API Unity courantes</a></span><span class="sxs-lookup"><span data-stu-id="29042-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="29042-122">(Input. GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="29042-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="29042-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API d’entrée spécifique à Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="29042-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="29042-124">XR. WSA. Entrée</span><span class="sxs-lookup"><span data-stu-id="29042-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="29042-125">Main gauche</span><span class="sxs-lookup"><span data-stu-id="29042-125">Left hand</span></span> </th><th> <span data-ttu-id="29042-126">À droite</span><span class="sxs-lookup"><span data-stu-id="29042-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="29042-127">Sélectionner le déclencheur enfoncé</span><span class="sxs-lookup"><span data-stu-id="29042-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="29042-128">Axe 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="29042-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="29042-129">Axe 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="29042-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="29042-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="29042-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-131">Sélectionner la valeur analogique du déclencheur</span><span class="sxs-lookup"><span data-stu-id="29042-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="29042-132">Axe 9</span><span class="sxs-lookup"><span data-stu-id="29042-132">Axis 9</span></span> </td><td> <span data-ttu-id="29042-133">Axe 10</span><span class="sxs-lookup"><span data-stu-id="29042-133">Axis 10</span></span> </td><td> <span data-ttu-id="29042-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="29042-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-135">Sélectionner le déclencheur partiellement enfoncé</span><span class="sxs-lookup"><span data-stu-id="29042-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="29042-136">Bouton 14 <i>(compatibilité du boîtier de</i> l’option) </span><span class="sxs-lookup"><span data-stu-id="29042-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="29042-137">Bouton 15 <i>(compatibilité du boîtier de</i> l’option) </span><span class="sxs-lookup"><span data-stu-id="29042-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="29042-138">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="29042-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-139">Bouton de menu enfoncé</span><span class="sxs-lookup"><span data-stu-id="29042-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="29042-140">Bouton 6 \*</span><span class="sxs-lookup"><span data-stu-id="29042-140">Button 6\*</span></span> </td><td> <span data-ttu-id="29042-141">Bouton 7 \*</span><span class="sxs-lookup"><span data-stu-id="29042-141">Button 7\*</span></span> </td><td> <span data-ttu-id="29042-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="29042-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-143">Bouton de préhension enfoncé</span><span class="sxs-lookup"><span data-stu-id="29042-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="29042-144">Axe 11 = 1,0 (aucune valeur analogique)</span><span class="sxs-lookup"><span data-stu-id="29042-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="29042-145">Bouton 4 <i>(compatibilité du boîtier de</i> l’option) </span><span class="sxs-lookup"><span data-stu-id="29042-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="29042-146">Axe 12 = 1,0 (aucune valeur analogique)</span><span class="sxs-lookup"><span data-stu-id="29042-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="29042-147">Bouton 5 <i>(compatibilité du boîtier de</i> l’option) </span><span class="sxs-lookup"><span data-stu-id="29042-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="29042-148">saisi</span><span class="sxs-lookup"><span data-stu-id="29042-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-149">Stick analogique X <i>(gauche :-1,0, droite : 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="29042-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="29042-150">Axe 1</span><span class="sxs-lookup"><span data-stu-id="29042-150">Axis 1</span></span> </td><td> <span data-ttu-id="29042-151">Axe 4</span><span class="sxs-lookup"><span data-stu-id="29042-151">Axis 4</span></span> </td><td> <span data-ttu-id="29042-152">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="29042-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-153">Joystick Y <i>(haut :-1,0, bas : 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="29042-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="29042-154">Axe 2</span><span class="sxs-lookup"><span data-stu-id="29042-154">Axis 2</span></span> </td><td> <span data-ttu-id="29042-155">Axe 5</span><span class="sxs-lookup"><span data-stu-id="29042-155">Axis 5</span></span> </td><td> <span data-ttu-id="29042-156">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="29042-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-157">Stick analogique appuyé</span><span class="sxs-lookup"><span data-stu-id="29042-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="29042-158">Bouton 8</span><span class="sxs-lookup"><span data-stu-id="29042-158">Button 8</span></span> </td><td> <span data-ttu-id="29042-159">Bouton 9</span><span class="sxs-lookup"><span data-stu-id="29042-159">Button 9</span></span> </td><td> <span data-ttu-id="29042-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="29042-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-161">Pavé tactile X <i>(à gauche :-1,0, droite : 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="29042-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="29042-162">Axe 17 \*</span><span class="sxs-lookup"><span data-stu-id="29042-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="29042-163">Axe 19 \*</span><span class="sxs-lookup"><span data-stu-id="29042-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="29042-164">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="29042-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-165">Pavé tactile Y <i>(haut :-1,0, bas : 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="29042-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="29042-166">Axe 18 \*</span><span class="sxs-lookup"><span data-stu-id="29042-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="29042-167">Axe 20 \*</span><span class="sxs-lookup"><span data-stu-id="29042-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="29042-168">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="29042-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-169">Pavé tactile touché</span><span class="sxs-lookup"><span data-stu-id="29042-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="29042-170">Bouton 18 \*</span><span class="sxs-lookup"><span data-stu-id="29042-170">Button 18\*</span></span> </td><td> <span data-ttu-id="29042-171">Bouton 19 \*</span><span class="sxs-lookup"><span data-stu-id="29042-171">Button 19\*</span></span> </td><td> <span data-ttu-id="29042-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="29042-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-173">Pavé tactile enfoncé</span><span class="sxs-lookup"><span data-stu-id="29042-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="29042-174">Bouton 16 \*</span><span class="sxs-lookup"><span data-stu-id="29042-174">Button 16\*</span></span> </td><td> <span data-ttu-id="29042-175">Bouton 17 \*</span><span class="sxs-lookup"><span data-stu-id="29042-175">Button 17\*</span></span> </td><td> <span data-ttu-id="29042-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="29042-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-177">pose de la poignée ou du pointeur 6DoF</span><span class="sxs-lookup"><span data-stu-id="29042-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="29042-178"><i>Poignée</i> de pose uniquement : <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="29042-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="29042-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="29042-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="29042-180"><i>Poignée</i> ou <i>pointeur</i> en tant qu’argument : SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="29042-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="29042-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="29042-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="29042-182">État du suivi</span><span class="sxs-lookup"><span data-stu-id="29042-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="29042-183"><i>Précision de la position et risque de perte de source uniquement disponible via une API spécifique à MR</i> </span><span class="sxs-lookup"><span data-stu-id="29042-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="29042-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="29042-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="29042-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. Properties. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="29042-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="29042-186">Ces ID de bouton/axe diffèrent des ID utilisés par Unity pour les OpenVR en raison de collisions dans les mappages utilisés par les boîtiers de soucodeurs, Oculus touch et OpenVR.</span><span class="sxs-lookup"><span data-stu-id="29042-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="29042-187">Poignée de pose et pose de pointage</span><span class="sxs-lookup"><span data-stu-id="29042-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="29042-188">Windows Mixed Reality prend en charge les contrôleurs de mouvement dans un large éventail de facteurs de forme.</span><span class="sxs-lookup"><span data-stu-id="29042-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="29042-189">La conception de chaque contrôleur diffère dans sa relation entre la position de l’utilisateur et la direction « avant » naturelle que les applications doivent utiliser pour pointer lors du rendu du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="29042-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="29042-190">Pour mieux représenter ces contrôleurs, il existe deux genres de poses que vous pouvez examiner pour chaque source d’interaction, le pose de la **poignée** et le **pointeur se posent**.</span><span class="sxs-lookup"><span data-stu-id="29042-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="29042-191">Les coordonnées de pose de la poignée et du pointeur sont exprimées par toutes les API Unity dans les coordonnées universelles Unity universel.</span><span class="sxs-lookup"><span data-stu-id="29042-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="29042-192">Poignée de pose</span><span class="sxs-lookup"><span data-stu-id="29042-192">Grip pose</span></span>

<span data-ttu-id="29042-193">La **poignée** représente l’emplacement de la paume des utilisateurs, qu’elle soit détectée par une carte HoloLens ou qu’elle détient un contrôleur de mouvement.</span><span class="sxs-lookup"><span data-stu-id="29042-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="29042-194">Sur les casques immersifs, le pose de la poignée est utilisé pour restituer **la main de l’utilisateur** ou **un objet détenu par l’utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="29042-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="29042-195">La poignée est également utilisée lors de la visualisation d’un contrôleur de mouvement.</span><span class="sxs-lookup"><span data-stu-id="29042-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="29042-196">Le **modèle de rendu** fourni par Windows pour un contrôleur de mouvement utilise la poignée comme son origine et le centre de la rotation.</span><span class="sxs-lookup"><span data-stu-id="29042-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="29042-197">La poignée est définie spécifiquement comme suit :</span><span class="sxs-lookup"><span data-stu-id="29042-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="29042-198">Position de la **poignée**: le centre de la poche quand il maintient le contrôleur naturellement, ajusté à gauche ou à droite pour centrer la position au sein de la poignée.</span><span class="sxs-lookup"><span data-stu-id="29042-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="29042-199">Sur le contrôleur de mouvement Windows Mixed Reality, cette position s’aligne généralement avec le bouton de saisie.</span><span class="sxs-lookup"><span data-stu-id="29042-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="29042-200">**Axe droit de l’orientation de la poignée**: lorsque vous ouvrez complètement votre main pour former une pose plate à 5 doigts, le rayon normal à votre paume (en avant à partir de la poche de gauche, en arrière depuis la paume de droite)</span><span class="sxs-lookup"><span data-stu-id="29042-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="29042-201">**Axe avant de l’orientation de la poignée**: quand vous fermez partiellement votre main (comme si vous détenir le contrôleur), le rayon qui pointe vers l’avant dans le tube formé par vos doigts non thumbs.</span><span class="sxs-lookup"><span data-stu-id="29042-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="29042-202">**Axe vers le haut de l’orientation**: l’axe vers le haut, impliqué dans les définitions Right et Forward.</span><span class="sxs-lookup"><span data-stu-id="29042-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="29042-203">Vous pouvez accéder à la poignée à l’aide de l’API d’entrée entre fournisseurs de l’unité Unity (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/rotation*) ou via l’API propre à Windows Mr (*SourceState. SourcePose. TryGetPosition/rotation*, en demandant des données de pose pour le nœud de **poignée** ).</span><span class="sxs-lookup"><span data-stu-id="29042-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="29042-204">Pose du pointeur</span><span class="sxs-lookup"><span data-stu-id="29042-204">Pointer pose</span></span>

<span data-ttu-id="29042-205">Le **pointeur de pose** représente l’extrémité du contrôleur pointant vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="29042-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="29042-206">Le pointeur fourni par le système est le mieux utilisé pour raycast lorsque vous effectuez **le rendu du modèle de contrôleur lui-même**.</span><span class="sxs-lookup"><span data-stu-id="29042-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="29042-207">Si vous effectuez le rendu d’un autre objet virtuel à la place du contrôleur, tel qu’un pistolet virtuel, vous devez faire pointer un rayon qui est le plus naturel pour cet objet virtuel, tel qu’un rayon qui traverse le canon du modèle de pistolet défini par l’application.</span><span class="sxs-lookup"><span data-stu-id="29042-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="29042-208">Étant donné que les utilisateurs peuvent voir l’objet virtuel et non le contrôleur physique, le fait de pointer avec l’objet virtuel sera probablement plus naturel pour ceux qui utilisent votre application.</span><span class="sxs-lookup"><span data-stu-id="29042-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="29042-209">Actuellement, le pointeur de pose est disponible dans Unity uniquement par le biais de l’API propre à Windows MR, *sourceState. sourcePose. TryGetPosition/rotation*, en passant *InteractionSourceNode. pointeur* comme argument.</span><span class="sxs-lookup"><span data-stu-id="29042-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="29042-210">État du suivi du contrôleur</span><span class="sxs-lookup"><span data-stu-id="29042-210">Controller tracking state</span></span>

<span data-ttu-id="29042-211">À l’instar des casques, le contrôleur de mouvement Windows Mixed Reality ne nécessite pas de configuration de capteurs de suivi externe.</span><span class="sxs-lookup"><span data-stu-id="29042-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="29042-212">Au lieu de cela, les contrôleurs sont suivis par des capteurs dans le casque lui-même.</span><span class="sxs-lookup"><span data-stu-id="29042-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="29042-213">Si l’utilisateur déplace les contrôleurs en dehors du champ de vue du casque, Windows continue à déduire les positions des contrôleurs dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="29042-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="29042-214">Lorsque le contrôleur a perdu le suivi visuel suffisamment longtemps, les positions du contrôleur sont découpées à des positions de précision approximatives.</span><span class="sxs-lookup"><span data-stu-id="29042-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="29042-215">À ce stade, le système va verrouiller le contrôleur à l’utilisateur, en effectuant le suivi de la position de l’utilisateur lors de son déplacement, tout en exposant l’orientation réelle du contrôleur à l’aide de ses capteurs d’orientation internes.</span><span class="sxs-lookup"><span data-stu-id="29042-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="29042-216">De nombreuses applications qui utilisent des contrôleurs pour pointer et activer des éléments d’interface utilisateur peuvent fonctionner normalement avec une précision approximative sans que l’utilisateur ne remarque.</span><span class="sxs-lookup"><span data-stu-id="29042-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="29042-217">La meilleure façon de vous en faire une idée est de l’essayer vous-même.</span><span class="sxs-lookup"><span data-stu-id="29042-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="29042-218">Consultez cette vidéo avec des exemples de contenu immersif qui fonctionne avec les contrôleurs de mouvement dans différents États de suivi :</span><span class="sxs-lookup"><span data-stu-id="29042-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="29042-219">Raisonnement sur le suivi de l’État explicitement</span><span class="sxs-lookup"><span data-stu-id="29042-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="29042-220">Les applications qui souhaitent traiter différemment les positions en fonction de l’état de suivi peuvent aller plus loin et inspecter les propriétés de l’état du contrôleur, telles que *SourceLossRisk* et *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="29042-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="29042-221">État du suivi</span><span class="sxs-lookup"><span data-stu-id="29042-221">Tracking state</span></span> </th><th> <span data-ttu-id="29042-222">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="29042-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="29042-223">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="29042-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="29042-224">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="29042-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="29042-225"><b>Haute précision</b> </span><span class="sxs-lookup"><span data-stu-id="29042-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="29042-226">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="29042-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="29042-227">Importante</span><span class="sxs-lookup"><span data-stu-id="29042-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="29042-228">true</span><span class="sxs-lookup"><span data-stu-id="29042-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-229"><b>Haute précision (risque de perte)</b> </span><span class="sxs-lookup"><span data-stu-id="29042-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="29042-230">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="29042-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="29042-231">Importante</span><span class="sxs-lookup"><span data-stu-id="29042-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="29042-232">true</span><span class="sxs-lookup"><span data-stu-id="29042-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-233"><b>Précision approximative</b> </span><span class="sxs-lookup"><span data-stu-id="29042-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="29042-234">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="29042-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="29042-235">Approximatif</span><span class="sxs-lookup"><span data-stu-id="29042-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="29042-236">true</span><span class="sxs-lookup"><span data-stu-id="29042-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="29042-237"><b>Aucune position</b> </span><span class="sxs-lookup"><span data-stu-id="29042-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="29042-238">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="29042-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="29042-239">Approximatif</span><span class="sxs-lookup"><span data-stu-id="29042-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="29042-240">false</span><span class="sxs-lookup"><span data-stu-id="29042-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="29042-241">Ces États de suivi du contrôleur de mouvement sont définis comme suit :</span><span class="sxs-lookup"><span data-stu-id="29042-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="29042-242">**Précision élevée :** Alors que le contrôleur de mouvement se trouve dans le champ de vision du casque, il fournit généralement des positions à grande précision, en fonction du suivi visuel.</span><span class="sxs-lookup"><span data-stu-id="29042-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="29042-243">Un contrôleur mobile qui laisse momentanément le champ de vue ou est momentanément masqué des capteurs du casque (par exemple, par l’autre côté de l’utilisateur) continue à retourner des poses de grande précision pendant une brève période, en se basant sur le suivi inertiel du contrôleur lui-même.</span><span class="sxs-lookup"><span data-stu-id="29042-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="29042-244">**Haute précision (risque de perte) :** Lorsque l’utilisateur déplace le contrôleur de mouvement au-delà du bord du champ de vue du casque, le casque ne pourra bientôt pas suivre la position du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="29042-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="29042-245">L’application sait quand le contrôleur a atteint cette limite d’aide en regardant le **SourceLossRisk** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="29042-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="29042-246">À ce stade, l’application peut choisir de suspendre les gestes de contrôleur qui nécessitent un flux constant de poses de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="29042-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="29042-247">**Précision approximative :** Lorsque le contrôleur a perdu le suivi visuel suffisamment longtemps, les positions du contrôleur sont découpées à des positions de précision approximatives.</span><span class="sxs-lookup"><span data-stu-id="29042-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="29042-248">À ce stade, le système va verrouiller le contrôleur à l’utilisateur, en effectuant le suivi de la position de l’utilisateur lors de son déplacement, tout en exposant l’orientation réelle du contrôleur à l’aide de ses capteurs d’orientation internes.</span><span class="sxs-lookup"><span data-stu-id="29042-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="29042-249">De nombreuses applications qui utilisent des contrôleurs pour pointer et activer des éléments d’interface utilisateur peuvent fonctionner normalement, tout en ayant une précision approximative, sans que l’utilisateur ne remarque.</span><span class="sxs-lookup"><span data-stu-id="29042-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="29042-250">Les applications avec des exigences d’entrée plus lourdes peuvent choisir de déterminer ce déplacement de la **haute** précision à une précision **approximative** en inspectant la propriété **PositionAccuracy** , par exemple pour accorder à l’utilisateur un hitbox plus généreux sur les cibles hors écran pendant cette période.</span><span class="sxs-lookup"><span data-stu-id="29042-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="29042-251">**Aucune position :** Alors que le contrôleur peut fonctionner à des fins de précision approximative pendant une longue période, le système sait parfois que même une position verrouillée par le corps n’est pas significative pour le moment.</span><span class="sxs-lookup"><span data-stu-id="29042-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="29042-252">Par exemple, un contrôleur qui a été activé n’a peut-être jamais été observé visuellement, ou un utilisateur peut mettre un contrôleur qui est ensuite récupéré par quelqu’un d’autre.</span><span class="sxs-lookup"><span data-stu-id="29042-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="29042-253">À ce moment-là, le système ne fournit pas de position à l’application, et *TryGetPosition* retourne la valeur false.</span><span class="sxs-lookup"><span data-stu-id="29042-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="29042-254">API Unity courantes (Input. GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="29042-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="29042-255">**Espace de noms :** *UnityEngine*, *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="29042-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="29042-256">**Types**: *Input*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="29042-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="29042-257">Unity utilise actuellement ses API *d’entrée. GetButton/Input. GetAxis* pour exposer l’entrée pour [le kit de développement logiciel (SDK) Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [le kit de développement logiciel (SDK) OpenVR et la](https://docs.unity3d.com/Manual/OpenVRControllers.html) réalité mixte Windows, y compris les contrôleurs mains et motion.</span><span class="sxs-lookup"><span data-stu-id="29042-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="29042-258">Si votre application utilise ces API pour l’entrée, elle peut facilement prendre en charge des contrôleurs de mouvement sur plusieurs kits de développement logiciel (SDK) XR, y compris Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="29042-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="29042-259">Obtention de l’état enfoncé d’un bouton logique</span><span class="sxs-lookup"><span data-stu-id="29042-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="29042-260">Pour utiliser les API d’entrée Unity générales, vous commencez généralement par associer des boutons et des axes aux noms logiques dans le [Gestionnaire d’entrée Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), en liant un bouton ou des ID d’axe à chaque nom.</span><span class="sxs-lookup"><span data-stu-id="29042-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="29042-261">Vous pouvez ensuite écrire du code qui fait référence à ce nom d’axe/bouton logique.</span><span class="sxs-lookup"><span data-stu-id="29042-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="29042-262">Par exemple, pour mapper le bouton de déclenchement du contrôleur de mouvement gauche à l’action envoyer, accédez à **modifier > paramètres du projet > entrée** dans Unity, puis développez les propriétés de la section envoyer sous axes.</span><span class="sxs-lookup"><span data-stu-id="29042-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="29042-263">Modifiez le bouton **positif** ou la propriété **ALT positive du bouton** pour lire le bouton de la manette de jeu **14**, comme suit :</span><span class="sxs-lookup"><span data-stu-id="29042-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="29042-264">![InputManager d’Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="29042-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="29042-265&quot;>*InputManager Unity*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;29042-265&quot;>*Unity InputManager*</span></span>

<span data-ttu-id=&quot;29042-266&quot;>Votre script peut ensuite Rechercher l’action envoyer à l’aide de *Input. GetButton*:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;29042-266&quot;>Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
<span data-ttu-id="29042-267">Vous pouvez ajouter des boutons logiques en modifiant la propriété **taille** sous **axes**.</span><span class="sxs-lookup"><span data-stu-id="29042-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="29042-268">Obtention directe d’un état enfoncé d’un bouton physique</span><span class="sxs-lookup"><span data-stu-id="29042-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="29042-269">Vous pouvez également accéder manuellement aux boutons à l’aide de leur nom complet, en utilisant *Input. GetKey*:</span><span class="sxs-lookup"><span data-stu-id="29042-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="29042-270">Obtention d’une main ou d’une pose de contrôleur de mouvement</span><span class="sxs-lookup"><span data-stu-id="29042-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="29042-271">Vous pouvez accéder à la position et à la rotation du contrôleur, à l’aide de *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="29042-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="29042-272">Le code ci-dessus représente la poignée du contrôleur (où l’utilisateur détient le contrôleur), qui est utile pour le rendu d’une arme ou d’un pistolet dans la main de l’utilisateur, ou un modèle du contrôleur lui-même.</span><span class="sxs-lookup"><span data-stu-id="29042-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="29042-273">La relation entre cette poignée se pose et le pointeur pose (où l’extrémité du contrôleur pointe) peut varier d’un contrôle à l’autre.</span><span class="sxs-lookup"><span data-stu-id="29042-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="29042-274">À ce stade, l’accès au pointeur du contrôleur est possible uniquement via l’API d’entrée spécifique à MR, décrite dans les sections ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="29042-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="29042-275">API spécifiques à Windows (XR. WSA. Entrée</span><span class="sxs-lookup"><span data-stu-id="29042-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="29042-276">Si votre projet utilise l’un des XR. Les API WSA, elles sont en passe en faveur du kit de développement logiciel (SDK) XR dans les futures versions Unity.</span><span class="sxs-lookup"><span data-stu-id="29042-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="29042-277">Pour les nouveaux projets, nous vous recommandons d’utiliser le kit de développement logiciel (SDK) XR dès le début.</span><span class="sxs-lookup"><span data-stu-id="29042-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="29042-278">Vous trouverez plus d’informations sur le [système d’entrée XR et les API ici](https://docs.unity3d.com/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="29042-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="29042-279">**Espace de noms :** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="29042-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="29042-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="29042-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="29042-281">Pour obtenir des informations plus détaillées sur l’entrée manuelle de Windows Mixed Reality (pour HoloLens) et les contrôleurs de mouvement, vous pouvez choisir d’utiliser les API d’entrée spatiale spécifiques à Windows sous l’espace de noms *UnityEngine. XR. WSA. Input* .</span><span class="sxs-lookup"><span data-stu-id="29042-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="29042-282">Cela vous permet d’accéder à des informations supplémentaires, telles que la précision de la position ou le genre de source, vous permettant de distinguer les mains et les contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="29042-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="29042-283">Interrogation de l’état des contrôleurs mains et motion</span><span class="sxs-lookup"><span data-stu-id="29042-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="29042-284">Vous pouvez interroger l’état de ce frame pour chaque source d’interaction (contrôleur de main ou de mouvement) à l’aide de la méthode *GetCurrentReading* .</span><span class="sxs-lookup"><span data-stu-id="29042-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="29042-285">Chaque *InteractionSourceState* que vous récupérez représente une source d’interaction à l’instant courant.</span><span class="sxs-lookup"><span data-stu-id="29042-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="29042-286">*InteractionSourceState* expose des informations telles que :</span><span class="sxs-lookup"><span data-stu-id="29042-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="29042-287">Quels sont les [types d’enfoncement](../../design/motion-controllers.md) (Select/menu///-pavé/Stick)</span><span class="sxs-lookup"><span data-stu-id="29042-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="29042-288">Autres données spécifiques aux contrôleurs de mouvement, telles que le pavé tactile et/ou les coordonnées XY et l’État touché</span><span class="sxs-lookup"><span data-stu-id="29042-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="29042-289">InteractionSourceKind à savoir si la source est une main ou un contrôleur de mouvement</span><span class="sxs-lookup"><span data-stu-id="29042-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="29042-290">Interrogation pour les poses de rendu prédits par progression</span><span class="sxs-lookup"><span data-stu-id="29042-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="29042-291">Lors de l’interrogation des données sources d’interaction à partir de mains et de contrôleurs, les poses que vous recevez sont des poses prédites pour le moment où les photons de ce frame atteindront les yeux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="29042-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="29042-292">Les poses préprédits sont préférables pour le **rendu** du contrôleur ou de l’objet détenu dans chaque frame.</span><span class="sxs-lookup"><span data-stu-id="29042-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="29042-293">Si vous ciblez une pression ou une mise en route donnée avec le contrôleur, celles-ci seront plus précises si vous utilisez les API d’événements historiques décrites ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="29042-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="29042-294">Vous pouvez également obtenir la pose de tête préprédite pour ce frame actuel.</span><span class="sxs-lookup"><span data-stu-id="29042-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="29042-295">Comme avec la source, cela est utile pour le **rendu** d’un curseur, bien que le ciblage d’une presse ou d’une version donnée soit plus précis si vous utilisez les API d’événements historiques décrites ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="29042-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="29042-296">Gestion des événements de source d’interaction</span><span class="sxs-lookup"><span data-stu-id="29042-296">Handling interaction source events</span></span>

<span data-ttu-id="29042-297">Pour gérer les événements d’entrée à mesure qu’ils se produisent avec leurs données d’historique exactes, vous pouvez gérer les événements de source d’interaction au lieu d’interroger.</span><span class="sxs-lookup"><span data-stu-id="29042-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="29042-298">Pour gérer les événements de source d’interaction :</span><span class="sxs-lookup"><span data-stu-id="29042-298">To handle interaction source events:</span></span>
* <span data-ttu-id="29042-299">Inscrivez-vous pour un événement d’entrée *InteractionManager* .</span><span class="sxs-lookup"><span data-stu-id="29042-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="29042-300">Pour chaque type d’événement d’interaction qui vous intéresse, vous devez vous y abonner.</span><span class="sxs-lookup"><span data-stu-id="29042-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="29042-301">Gérez l’événement.</span><span class="sxs-lookup"><span data-stu-id="29042-301">Handle the event.</span></span> <span data-ttu-id="29042-302">Une fois que vous êtes abonné à un événement d’interaction, vous obtiendrez le rappel le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="29042-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="29042-303">Dans l’exemple *SourcePressed* , c’est une fois que la source a été détectée et avant qu’elle soit libérée ou perdue.</span><span class="sxs-lookup"><span data-stu-id="29042-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="29042-304">Comment arrêter la gestion d’un événement</span><span class="sxs-lookup"><span data-stu-id="29042-304">How to stop handling an event</span></span>

<span data-ttu-id="29042-305">Vous devez arrêter la gestion d’un événement lorsque vous n’êtes plus intéressé par l’événement ou si vous détruisez l’objet qui s’est abonné à l’événement.</span><span class="sxs-lookup"><span data-stu-id="29042-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="29042-306">Pour arrêter la gestion de l’événement, vous devez vous désabonner de l’événement.</span><span class="sxs-lookup"><span data-stu-id="29042-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="29042-307">Liste des événements de source d’interaction</span><span class="sxs-lookup"><span data-stu-id="29042-307">List of interaction source events</span></span>

<span data-ttu-id="29042-308">Les événements de la source d’interaction disponibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="29042-308">The available interaction source events are:</span></span>
* <span data-ttu-id="29042-309">*InteractionSourceDetected* (la source devient active)</span><span class="sxs-lookup"><span data-stu-id="29042-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="29042-310">*InteractionSourceLost* (devient inactif)</span><span class="sxs-lookup"><span data-stu-id="29042-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="29042-311">*InteractionSourcePressed* (appuyez sur, appuyez sur le bouton ou sélectionnez « Sélectionner »)</span><span class="sxs-lookup"><span data-stu-id="29042-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="29042-312">*InteractionSourceReleased* (fin d’un TAP, d’un bouton relâché ou d’une fin de « SELECT »)</span><span class="sxs-lookup"><span data-stu-id="29042-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="29042-313">*InteractionSourceUpdated* (déplace ou change un État)</span><span class="sxs-lookup"><span data-stu-id="29042-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="29042-314">Les événements pour le ciblage historique posent qui correspondent le plus précisément à une pression ou à une mise en sortie</span><span class="sxs-lookup"><span data-stu-id="29042-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="29042-315">Les API d’interrogation décrites précédemment fournissent à votre application des poses préprédits.</span><span class="sxs-lookup"><span data-stu-id="29042-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="29042-316">Bien que ces éléments prédits soient les plus adaptés pour le rendu du contrôleur ou d’un objet de poche virtuel, les nouvelles poses ne sont pas optimales pour le ciblage, pour deux raisons principales :</span><span class="sxs-lookup"><span data-stu-id="29042-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="29042-317">Quand l’utilisateur appuie sur un bouton sur un contrôleur, il peut y avoir environ 20 ms de latence sans fil sur Bluetooth avant que le système ne reçoive la presse.</span><span class="sxs-lookup"><span data-stu-id="29042-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="29042-318">Ensuite, si vous utilisez une pose préprédite, il y aura une autre 10-20 ms de prédiction de transfert appliquée pour cibler le moment où les photons du frame actuel atteindront les yeux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="29042-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="29042-319">Cela signifie que l’interrogation vous donne une source de pose ou de tête qui est de 30-40 ms à partir de là où la tête et la mains de l’utilisateur ont été retirées lorsque l’appui ou la mise en place a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="29042-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="29042-320">Pour l’entrée de la main HoloLens, bien qu’il n’y ait pas de délai de transmission sans fil, il existe un délai de traitement similaire pour détecter la presse.</span><span class="sxs-lookup"><span data-stu-id="29042-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="29042-321">Pour cibler avec précision en fonction de l’intention initiale de l’utilisateur pour une presse ou un contrôleur, vous devez utiliser la base de l’historique de la source ou de l’en-tête à partir de cet événement d’entrée *InteractionSourcePressed* ou *InteractionSourceReleased* .</span><span class="sxs-lookup"><span data-stu-id="29042-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="29042-322">Vous pouvez cibler une presse ou une mise en route avec des données de pose historiques à partir de la tête de l’utilisateur ou de son contrôleur :</span><span class="sxs-lookup"><span data-stu-id="29042-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="29042-323">L’en-tête pose au moment où un mouvement ou un contrôleur s’est produit, ce qui peut être utilisé pour **cibler** pour déterminer à quoi l’utilisateur a [Gazing](../../design/gaze-and-commit.md) :</span><span class="sxs-lookup"><span data-stu-id="29042-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="29042-324">La source pose au moment où une pression du contrôleur de mouvement s’est produite, qui peut être utilisée pour le **ciblage** afin de déterminer le point de contrôle de l’utilisateur sur le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="29042-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="29042-325">Il s’agit de l’état du contrôleur qui a rencontré la presse.</span><span class="sxs-lookup"><span data-stu-id="29042-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="29042-326">Si vous effectuez le rendu du contrôleur lui-même, vous pouvez demander le point de pose plutôt que le pose de la poignée pour faire tourner le ciblage de la cible à partir de ce que l’utilisateur prendra en compte l’astuce naturelle de ce contrôleur rendu :</span><span class="sxs-lookup"><span data-stu-id="29042-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="29042-327">Exemple de gestionnaires d’événements</span><span class="sxs-lookup"><span data-stu-id="29042-327">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="29042-328">Contrôleurs de mouvement dans MRTK</span><span class="sxs-lookup"><span data-stu-id="29042-328">Motion Controllers in MRTK</span></span>

<span data-ttu-id="29042-329">Vous pouvez accéder au contrôleur de mouvement [et de mouvement](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/controllers) à partir du gestionnaire d’entrée.</span><span class="sxs-lookup"><span data-stu-id="29042-329">You can access [gesture and motion controller](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/controllers) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="29042-330">Avancer avec des tutoriels</span><span class="sxs-lookup"><span data-stu-id="29042-330">Follow along with tutorials</span></span>

<span data-ttu-id="29042-331">Des didacticiels pas à pas, avec des exemples de personnalisation plus détaillés, sont disponibles dans Mixed Reality Academy :</span><span class="sxs-lookup"><span data-stu-id="29042-331">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="29042-332">Réalité mixte - Entrées - Cours 211 : Mouvement</span><span class="sxs-lookup"><span data-stu-id="29042-332">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="29042-333">Réalité mixte - Entrées - Cours 213 : Contrôleurs de mouvement</span><span class="sxs-lookup"><span data-stu-id="29042-333">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="29042-334">[![Entrée MR 213-contrôleur de mouvement](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="29042-334">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="29042-335">*Entrée MR 213-contrôleur de mouvement*</span><span class="sxs-lookup"><span data-stu-id="29042-335">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="29042-336">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="29042-336">Next Development Checkpoint</span></span>

<span data-ttu-id="29042-337">Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="29042-337">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="29042-338">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="29042-338">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29042-339">Suivi du regard et des mains</span><span class="sxs-lookup"><span data-stu-id="29042-339">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="29042-340">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="29042-340">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29042-341">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="29042-341">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="29042-342">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="29042-342">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="29042-343">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29042-343">See also</span></span>

* [<span data-ttu-id="29042-344">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="29042-344">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="29042-345">Contrôleurs de mouvement</span><span class="sxs-lookup"><span data-stu-id="29042-345">Motion controllers</span></span>](../../design/motion-controllers.md)