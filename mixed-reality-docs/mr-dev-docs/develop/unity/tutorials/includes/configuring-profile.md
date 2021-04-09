---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097351"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="e60ba-101">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="e60ba-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="e60ba-102">1. Cloner le profil de configuration par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="e60ba-103">Le profil de configuration est le profil de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="e60ba-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="e60ba-104">Par conséquent, pour pouvoir modifier d’autres profils, vous devez d’abord cloner le profil de configuration.</span><span class="sxs-lookup"><span data-stu-id="e60ba-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="e60ba-105">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit** puis, dans la fenêtre Inspector, vérifiez que le profil de configuration **MixedRealityToolkit** est défini sur **DefaultXRSDKConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![Composant MixedRealityToolkit d’Unity avec DefaultHoloLens2ConfigurationProfile sélectionné](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="e60ba-107">Avec l’objet **MixedRealityToolkit** sélectionné, dans la fenêtre Inspector, cliquez sur le bouton **Copy & Customize** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity - Bouton Copy & Customize](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="e60ba-109">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_XRSDKConfigurationProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultXRSDKConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil de configuration](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="e60ba-111">Le profil de configuration que vous venez de créer est maintenant affecté comme profil de configuration pour votre scène :</span><span class="sxs-lookup"><span data-stu-id="e60ba-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé HoloLens2ConfigurationProfile appliqué](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="e60ba-113">Dans le menu Unity, sélectionnez **File** > **Save** pour enregistrer votre scène.</span><span class="sxs-lookup"><span data-stu-id="e60ba-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="e60ba-114">N’oubliez pas d’enregistrer votre travail tout au long des tutoriels.</span><span class="sxs-lookup"><span data-stu-id="e60ba-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="e60ba-115">2. Activer le système de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="e60ba-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="e60ba-116">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet **Spatial Awareness**, puis cochez la case **Enable Spatial Awareness System** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Composant MixedRealityToolkit d’Unity avec le système de reconnaissance spatiale activé](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="e60ba-118">Pour les projets à venir, si votre application n’a pas besoin de répondre à l’environnement ou d’interagir avec celui-ci, il est recommandé de désactiver la reconnaissance spatiale de façon à réduire le coût des performances.</span><span class="sxs-lookup"><span data-stu-id="e60ba-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="e60ba-119">3. Cloner le profil système de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="e60ba-120">Sous l’onglet **Spatial Awareness**, cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Composant Unity MixedRealityToolkit d’Unity avec l’onglet Spatial Awareness sélectionné](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="e60ba-122">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultXRSDKSpatialAwarenessSystemProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil du système de reconnaissance spatiale](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="e60ba-124">Le profil Spatial Awareness System nouvellement créé est maintenant automatiquement affecté à votre profil de configuration :</span><span class="sxs-lookup"><span data-stu-id="e60ba-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessSystemProfile appliqué](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="e60ba-126">4. Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="e60ba-127">Avec l’onglet **Spatial Awareness** sélectionné, développez la section **XR SDK Windows Mixed Reality Spatial Mesh Observer**, puis cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity avec la section Windows Mixed Reality Spatial Mesh Observer développée](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="e60ba-129">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil Spatial Mesh Observer](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="e60ba-131">Le profil Spatial Awareness Mesh Observer nouvellement créé est maintenant automatiquement affecté à votre profil Spatial Awareness System :</span><span class="sxs-lookup"><span data-stu-id="e60ba-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessMeshObserverProfile appliqué](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="e60ba-133">5. Changer la visibilité du maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="e60ba-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="e60ba-134">Dans **Spatial Mesh Observer Settings**, configurez **Display Option** sur **Occlusion** pour rendre le maillage de mappage spatial invisible tout en le gardant fonctionnel :</span><span class="sxs-lookup"><span data-stu-id="e60ba-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Composant MixedRealityToolkit d’Unity avec l’option d’affichage de Spatial Mesh Observer définie sur Occlusion](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="e60ba-136">Bien que le maillage de mappage spatial ne soit pas visible, il est toujours présent et fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="e60ba-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="e60ba-137">Par exemple, les hologrammes qui sont derrière le maillage de mappage spatial, comme un hologramme derrière un mur physique, ne sont pas visibles.</span><span class="sxs-lookup"><span data-stu-id="e60ba-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="e60ba-138">Vous venez de découvrir comment modifier un paramètre dans le profil MRTK.</span><span class="sxs-lookup"><span data-stu-id="e60ba-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="e60ba-139">Comme vous pouvez le voir, pour personnaliser les paramètres du MRTK, vous devez d’abord créer une copie des profils par défaut.</span><span class="sxs-lookup"><span data-stu-id="e60ba-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="e60ba-140">Étant donné que les profils par défaut ne sont pas modifiables, vous les aurez toujours comme référence si vous voulez rétablir les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="e60ba-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="e60ba-141">Pour plus d’informations sur les profils MRTK et leur architecture, vous pouvez consulter le [Guide de configuration du profil MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="e60ba-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="e60ba-142">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="e60ba-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="e60ba-143">1. Cloner le profil de configuration par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="e60ba-144">Le profil de configuration est le profil de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="e60ba-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="e60ba-145">Par conséquent, pour pouvoir modifier d’autres profils, vous devez d’abord cloner le profil de configuration.</span><span class="sxs-lookup"><span data-stu-id="e60ba-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="e60ba-146">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit** puis, dans la fenêtre Inspector, vérifiez que le profil de configuration **MixedRealityToolkit** est défini sur **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil OpenXR par défaut sélectionné](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="e60ba-148">Avec l’objet **MixedRealityToolkit** sélectionné, dans la fenêtre Inspector, cliquez sur le bouton **Copy & Customize** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity - Bouton Copy & Customize pour le profil OpenXR](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="e60ba-150">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_OpenXRConfigurationProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil de configuration pour le profil OpenXR](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="e60ba-152">Le profil de configuration que vous venez de créer est maintenant affecté comme profil de configuration pour votre scène :</span><span class="sxs-lookup"><span data-stu-id="e60ba-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé OpenXR appliqué](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="e60ba-154">Dans le menu Unity, sélectionnez **File** > **Save** pour enregistrer votre scène.</span><span class="sxs-lookup"><span data-stu-id="e60ba-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="e60ba-155">N’oubliez pas d’enregistrer votre travail tout au long des tutoriels.</span><span class="sxs-lookup"><span data-stu-id="e60ba-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="e60ba-156">2. Activer le système de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="e60ba-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="e60ba-157">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet **Spatial Awareness**, puis cochez la case **Enable Spatial Awareness System** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Composant MixedRealityToolkit d’Unity avec le système de reconnaissance spatiale activé](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="e60ba-159">Pour les projets à venir, si votre application n’a pas besoin de répondre à l’environnement ou d’interagir avec celui-ci, il est recommandé de désactiver la reconnaissance spatiale de façon à réduire le coût des performances.</span><span class="sxs-lookup"><span data-stu-id="e60ba-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="e60ba-160">3. Cloner le profil système de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="e60ba-161">Sous l’onglet **Spatial Awareness**, cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Composant Unity MixedRealityToolkit d’Unity avec l’onglet Spatial Awareness sélectionné](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="e60ba-163">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme GettingStarted_OpenXRSpatialAwarenessSystemProfile, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultXRSDKSpatialAwarenessSystemProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil du système de reconnaissance spatiale](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="e60ba-165">Le profil Spatial Awareness System nouvellement créé est maintenant automatiquement affecté à votre profil de configuration :</span><span class="sxs-lookup"><span data-stu-id="e60ba-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessSystemProfile appliqué](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="e60ba-167">4. Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="e60ba-168">Avec l’onglet **Spatial Awareness** sélectionné, développez la section **XR SDK Windows Mixed Reality Spatial Mesh Observer**, puis cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity avec la section Windows Mixed Reality Spatial Mesh Observer développée](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="e60ba-170">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil Spatial Mesh Observer](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="e60ba-172">Le profil Spatial Awareness Mesh Observer nouvellement créé est maintenant automatiquement affecté à votre profil Spatial Awareness System :</span><span class="sxs-lookup"><span data-stu-id="e60ba-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessMeshObserverProfile appliqué](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="e60ba-174">5. Changer la visibilité du maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="e60ba-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="e60ba-175">Dans **Spatial Mesh Observer Settings**, configurez **Display Option** sur **Occlusion** pour rendre le maillage de mappage spatial invisible tout en le gardant fonctionnel :</span><span class="sxs-lookup"><span data-stu-id="e60ba-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Composant MixedRealityToolkit d’Unity avec l’option d’affichage de Spatial Mesh Observer définie sur Occlusion](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="e60ba-177">Bien que le maillage de mappage spatial ne soit pas visible, il est toujours présent et fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="e60ba-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="e60ba-178">Par exemple, les hologrammes qui sont derrière le maillage de mappage spatial, comme un hologramme derrière un mur physique, ne sont pas visibles.</span><span class="sxs-lookup"><span data-stu-id="e60ba-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="e60ba-179">Vous venez de découvrir comment modifier un paramètre dans le profil MRTK.</span><span class="sxs-lookup"><span data-stu-id="e60ba-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="e60ba-180">Comme vous pouvez le voir, pour personnaliser les paramètres du MRTK, vous devez d’abord créer une copie des profils par défaut.</span><span class="sxs-lookup"><span data-stu-id="e60ba-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="e60ba-181">Étant donné que les profils par défaut ne sont pas modifiables, vous les aurez toujours comme référence si vous voulez rétablir les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="e60ba-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="e60ba-182">Pour plus d’informations sur les profils MRTK et leur architecture, vous pouvez consulter le [Guide de configuration du profil MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="e60ba-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="e60ba-183">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="e60ba-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="e60ba-184">1. Cloner le profil de configuration par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="e60ba-185">Le profil de configuration est le profil de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="e60ba-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="e60ba-186">Par conséquent, pour pouvoir modifier d’autres profils, vous devez d’abord cloner le profil de configuration.</span><span class="sxs-lookup"><span data-stu-id="e60ba-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="e60ba-187">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**, puis, dans la fenêtre Inspector, remplacez le profil de configuration **MixedRealityToolkit** par **DefaultHoloLens2ConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Composant MixedRealityToolkit d’Unity avec DefaultHoloLens2ConfigurationProfile sélectionné](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="e60ba-189">Avec l’objet **MixedRealityToolkit** sélectionné, dans la fenêtre Inspector, cliquez sur le bouton **Copy & Customize** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity - Bouton Copy & Customize](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="e60ba-191">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_HoloLens2ConfigurationProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultHololens2ConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil de configuration](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="e60ba-193">Le profil de configuration que vous venez de créer est maintenant affecté comme profil de configuration pour votre scène :</span><span class="sxs-lookup"><span data-stu-id="e60ba-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé HoloLens2ConfigurationProfile appliqué](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="e60ba-195">Dans le menu Unity, sélectionnez **File** > **Save** pour enregistrer votre scène.</span><span class="sxs-lookup"><span data-stu-id="e60ba-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="e60ba-196">N’oubliez pas d’enregistrer votre travail tout au long des tutoriels.</span><span class="sxs-lookup"><span data-stu-id="e60ba-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="e60ba-197">2. Activer le système de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="e60ba-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="e60ba-198">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet **Spatial Awareness**, puis cochez la case **Enable Spatial Awareness System** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Composant MixedRealityToolkit d’Unity avec le système de reconnaissance spatiale activé](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="e60ba-200">Pour les projets à venir, si votre application n’a pas besoin de répondre à l’environnement ou d’interagir avec celui-ci, il est recommandé de désactiver la reconnaissance spatiale de façon à réduire le coût des performances.</span><span class="sxs-lookup"><span data-stu-id="e60ba-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="e60ba-201">3. Cloner le profil système de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="e60ba-202">Sous l’onglet **Spatial Awareness**, cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Composant Unity MixedRealityToolkit d’Unity avec l’onglet Spatial Awareness sélectionné](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="e60ba-204">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessSystemProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil du système de reconnaissance spatiale](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="e60ba-206">Le profil Spatial Awareness System nouvellement créé est maintenant automatiquement affecté à votre profil de configuration :</span><span class="sxs-lookup"><span data-stu-id="e60ba-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessSystemProfile appliqué](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="e60ba-208">4. Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="e60ba-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="e60ba-209">Avec l’onglet **Spatial Awareness** sélectionné, développez la section **Windows Mixed Reality Spatial Mesh Observer**, puis cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="e60ba-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity avec la section Windows Mixed Reality Spatial Mesh Observer développée](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="e60ba-211">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** :</span><span class="sxs-lookup"><span data-stu-id="e60ba-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil Spatial Mesh Observer](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="e60ba-213">Le profil Spatial Awareness Mesh Observer nouvellement créé est maintenant automatiquement affecté à votre profil Spatial Awareness System :</span><span class="sxs-lookup"><span data-stu-id="e60ba-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessMeshObserverProfile appliqué](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="e60ba-215">5. Changer la visibilité du maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="e60ba-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="e60ba-216">Dans **Spatial Mesh Observer Settings**, configurez **Display Option** sur **Occlusion** pour rendre le maillage de mappage spatial invisible tout en le gardant fonctionnel :</span><span class="sxs-lookup"><span data-stu-id="e60ba-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Composant MixedRealityToolkit d’Unity avec l’option d’affichage de Spatial Mesh Observer définie sur Occlusion](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="e60ba-218">Bien que le maillage de mappage spatial ne soit pas visible, il est toujours présent et fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="e60ba-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="e60ba-219">Par exemple, les hologrammes qui sont derrière le maillage de mappage spatial, comme un hologramme derrière un mur physique, ne sont pas visibles.</span><span class="sxs-lookup"><span data-stu-id="e60ba-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="e60ba-220">Vous venez de découvrir comment modifier un paramètre dans le profil MRTK.</span><span class="sxs-lookup"><span data-stu-id="e60ba-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="e60ba-221">Comme vous pouvez le voir, pour personnaliser les paramètres du MRTK, vous devez d’abord créer une copie des profils par défaut.</span><span class="sxs-lookup"><span data-stu-id="e60ba-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="e60ba-222">Étant donné que les profils par défaut ne sont pas modifiables, vous les aurez toujours comme référence si vous voulez rétablir les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="e60ba-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="e60ba-223">Pour plus d’informations sur les profils MRTK et leur architecture, vous pouvez consulter le [Guide de configuration du profil MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="e60ba-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
