---
title: Tutoriels sur MRTK - 3. Configuration des profils MRTK
description: Ce cours vous montre comment configurer les profils Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, reconnaissance spatiale
ms.localizationpriority: high
ms.openlocfilehash: 48bb6aa8705c9d874e6af8867d1edbe2385cb853
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613243"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="9dab3-105">3. Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="9dab3-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="9dab3-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="9dab3-106">Overview</span></span>

<span data-ttu-id="9dab3-107">Dans ce tutoriel, vous allez voir comment personnaliser et configurer les profils MRTK.</span><span class="sxs-lookup"><span data-stu-id="9dab3-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="9dab3-108">Les <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">profils MRTK</a> sont une arborescence de profils imbriqués qui constituent les informations de configuration déterminant comment les systèmes et les fonctionnalités de MRTK doivent être initialisés.</span><span class="sxs-lookup"><span data-stu-id="9dab3-108">The <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="9dab3-109">Le profil de plus haut niveau, le profil de configuration, contient des profils imbriqués pour chacun des systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="9dab3-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="9dab3-110">Chaque profil imbriqué est conçu pour configurer le comportement de son système correspondant.</span><span class="sxs-lookup"><span data-stu-id="9dab3-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="9dab3-111">Cet exemple va vous montrer comment masquer le maillage de la reconnaissance spatiale en modifiant les paramètres de l’observateur de maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="9dab3-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="9dab3-112">Vous pouvez cependant suivre ces mêmes principes pour personnaliser des paramètres ou des valeurs dans les profils MRTK.</span><span class="sxs-lookup"><span data-stu-id="9dab3-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="9dab3-113">Comme vous en avez fait l’expérience quand vous avez déployé votre projet sur votre HoloLens 2 dans le [tutoriel précédent](mr-learning-base-02.md#congratulations), le maillage de <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">reconnaissance spatiale</a> est un ensemble de mailles représentant la géométrie de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="9dab3-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="9dab3-114">C’est une visualisation utile à voir initialement, mais elle est généralement désactivée pour éviter de distraire visuellement l’utilisateur et d’impacter les performances en raison des ressources nécessaires à son affichage.</span><span class="sxs-lookup"><span data-stu-id="9dab3-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="9dab3-115">Objectifs</span><span class="sxs-lookup"><span data-stu-id="9dab3-115">Objectives</span></span>

* <span data-ttu-id="9dab3-116">Apprendre à personnaliser et à configurer des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="9dab3-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="9dab3-117">Apprendre à masquer le maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="9dab3-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="9dab3-118">Changement de l’option d’affichage de la reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="9dab3-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="9dab3-119">Les principales étapes à suivre pour masquer le maillage de la reconnaissance spatiale sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9dab3-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="9dab3-120">Cloner le profil de configuration par défaut</span><span class="sxs-lookup"><span data-stu-id="9dab3-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="9dab3-121">Activer le système de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="9dab3-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="9dab3-122">Cloner le profil système de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="9dab3-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="9dab3-123">Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="9dab3-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="9dab3-124">Changer la visibilité du maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="9dab3-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="9dab3-125">Par défaut, les profils MRTK ne sont pas modifiables.</span><span class="sxs-lookup"><span data-stu-id="9dab3-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="9dab3-126">Il s’agit des modèles de profil par défaut que vous devez cloner avant de pouvoir les modifier.</span><span class="sxs-lookup"><span data-stu-id="9dab3-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="9dab3-127">Il existe plusieurs couches de profils imbriquées.</span><span class="sxs-lookup"><span data-stu-id="9dab3-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="9dab3-128">Par conséquent, il est courant de cloner et de modifier plusieurs profils lors de la configuration d’un ou plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="9dab3-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="9dab3-129">1. Cloner le profil de configuration par défaut</span><span class="sxs-lookup"><span data-stu-id="9dab3-129">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="9dab3-130">Le profil de configuration est le profil de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="9dab3-130">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="9dab3-131">Par conséquent, pour pouvoir modifier d’autres profils, vous devez d’abord cloner le profil de configuration.</span><span class="sxs-lookup"><span data-stu-id="9dab3-131">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="9dab3-132">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**, puis, dans la fenêtre Inspector, remplacez le profil de configuration **MixedRealityToolkit** par **DefaultHoloLens2ConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="9dab3-132">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Composant MixedRealityToolkit d’Unity avec DefaultHoloLens2ConfigurationProfile sélectionné](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="9dab3-134">Avec l’objet **MixedRealityToolkit** sélectionné, dans la fenêtre Inspector, cliquez sur le bouton **Copy & Customize** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="9dab3-134">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity - Bouton Copy & Customize](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="9dab3-136">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_HoloLens2ConfigurationProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultHololens2ConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="9dab3-136">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil de configuration](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="9dab3-138">Le profil de configuration que vous venez de créer est maintenant affecté comme profil de configuration pour votre scène :</span><span class="sxs-lookup"><span data-stu-id="9dab3-138">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé HoloLens2ConfigurationProfile appliqué](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="9dab3-140">Dans le menu Unity, sélectionnez **File** > **Save** pour enregistrer votre scène.</span><span class="sxs-lookup"><span data-stu-id="9dab3-140">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="9dab3-141">N’oubliez pas d’enregistrer votre travail tout au long des tutoriels.</span><span class="sxs-lookup"><span data-stu-id="9dab3-141">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="9dab3-142">2. Activer le système de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="9dab3-142">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="9dab3-143">Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet **Spatial Awareness**, puis cochez la case **Enable Spatial Awareness System** :</span><span class="sxs-lookup"><span data-stu-id="9dab3-143">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Composant MixedRealityToolkit d’Unity avec le système de reconnaissance spatiale activé](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="9dab3-145">Pour les projets à venir, si votre application n’a pas besoin de répondre à l’environnement ou d’interagir avec celui-ci, il est recommandé de désactiver la reconnaissance spatiale de façon à réduire le coût des performances.</span><span class="sxs-lookup"><span data-stu-id="9dab3-145">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="9dab3-146">3. Cloner le profil système de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="9dab3-146">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="9dab3-147">Sous l’onglet **Spatial Awareness**, cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="9dab3-147">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Composant Unity MixedRealityToolkit d’Unity avec l’onglet Spatial Awareness sélectionné](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="9dab3-149">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessSystemProfile** :</span><span class="sxs-lookup"><span data-stu-id="9dab3-149">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil du système de reconnaissance spatiale](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="9dab3-151">Le profil Spatial Awareness System nouvellement créé est maintenant automatiquement affecté à votre profil de configuration :</span><span class="sxs-lookup"><span data-stu-id="9dab3-151">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessSystemProfile appliqué](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="9dab3-153">4. Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="9dab3-153">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="9dab3-154">Avec l’onglet **Spatial Awareness** sélectionné, développez la section **Windows Mixed Reality Spatial Mesh Observer**, puis cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :</span><span class="sxs-lookup"><span data-stu-id="9dab3-154">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Composant MixedRealityToolkit d’Unity avec la section Windows Mixed Reality Spatial Mesh Observer développée](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="9dab3-156">Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** :</span><span class="sxs-lookup"><span data-stu-id="9dab3-156">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil Spatial Mesh Observer](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="9dab3-158">Le profil Spatial Awareness Mesh Observer nouvellement créé est maintenant automatiquement affecté à votre profil Spatial Awareness System :</span><span class="sxs-lookup"><span data-stu-id="9dab3-158">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessMeshObserverProfile appliqué](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="9dab3-160">5. Changer la visibilité du maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="9dab3-160">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="9dab3-161">Dans **Spatial Mesh Observer Settings**, configurez **Display Option** sur **Occlusion** pour rendre le maillage de mappage spatial invisible tout en le gardant fonctionnel :</span><span class="sxs-lookup"><span data-stu-id="9dab3-161">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Composant MixedRealityToolkit d’Unity avec l’option d’affichage de Spatial Mesh Observer définie sur Occlusion](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="9dab3-163">Bien que le maillage de mappage spatial ne soit pas visible, il est toujours présent et fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="9dab3-163">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="9dab3-164">Par exemple, les hologrammes qui sont derrière le maillage de mappage spatial, comme un hologramme derrière un mur physique, ne sont pas visibles.</span><span class="sxs-lookup"><span data-stu-id="9dab3-164">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="9dab3-165">Vous venez de découvrir comment modifier un paramètre dans le profil MRTK.</span><span class="sxs-lookup"><span data-stu-id="9dab3-165">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="9dab3-166">Comme vous pouvez le voir, pour personnaliser les paramètres du MRTK, vous devez d’abord créer une copie des profils par défaut.</span><span class="sxs-lookup"><span data-stu-id="9dab3-166">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="9dab3-167">Étant donné que les profils par défaut ne sont pas modifiables, vous les aurez toujours comme référence si vous voulez rétablir les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="9dab3-167">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="9dab3-168">Pour plus d’informations sur les profils MRTK et leur architecture, vous pouvez consulter le [Guide de configuration du profil MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) dans le [portail de la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9dab3-168">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="9dab3-169">Félicitations</span><span class="sxs-lookup"><span data-stu-id="9dab3-169">Congratulations</span></span>

<span data-ttu-id="9dab3-170">Dans ce tutoriel, vous avez vu comment cloner, personnaliser et configurer les profils et les paramètres MRTK.</span><span class="sxs-lookup"><span data-stu-id="9dab3-170">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9dab3-171">Tutoriel suivant : 4. Positionnement des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="9dab3-171">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
