---
title: Recommandations sur les performances pour Unreal
description: Recommandations pour des performances optimales pour les applications de réalité mixte dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, performances, optimisation, paramètres, documentation
ms.openlocfilehash: 21bd3ee9fb7db23eab9365e41adfd0033aa0046e
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549125"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="81edc-104">Recommandations sur les performances pour Unreal</span><span class="sxs-lookup"><span data-stu-id="81edc-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="81edc-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="81edc-105">Overview</span></span>

<span data-ttu-id="81edc-106">Cet article s’appuie sur les [recommandations sur les performances pour la réalité mixte](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), mais il se concentre sur des fonctionnalités propres à Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="81edc-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="81edc-107">Avant de continuer, nous vous encourageons à vous informer sur les goulots d’étranglement des applications, l’analyse et le profilage des applications de réalité mixte, ainsi que les correctifs des performances généraux.</span><span class="sxs-lookup"><span data-stu-id="81edc-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="81edc-108">Paramètres de projet Unreal recommandés</span><span class="sxs-lookup"><span data-stu-id="81edc-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="81edc-109">Vous trouverez chacun des paramètres suivants dans **Edit > Project Settings**.</span><span class="sxs-lookup"><span data-stu-id="81edc-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="81edc-110">Utilisation du convertisseur VR mobile :</span><span class="sxs-lookup"><span data-stu-id="81edc-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="81edc-111">Faites défiler la page jusqu’à la section **Project**, sélectionnez **Target Hardware**, puis définissez la plateforme cible sur **Mobile/Tablet**.</span><span class="sxs-lookup"><span data-stu-id="81edc-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Définition de la cible mobile](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="81edc-113">Utilisation du renderer Forward :</span><span class="sxs-lookup"><span data-stu-id="81edc-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="81edc-114">Cette fonctionnalité est bien meilleure pour la réalité mixte que le pipeline de rendu Deferred par défaut.</span><span class="sxs-lookup"><span data-stu-id="81edc-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="81edc-115">Cela s’explique principalement par le nombre de fonctionnalités qui peuvent être désactivées individuellement.</span><span class="sxs-lookup"><span data-stu-id="81edc-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="81edc-116">Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="81edc-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Rendu Forward](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="81edc-118">En utilisant la multivue mobile :</span><span class="sxs-lookup"><span data-stu-id="81edc-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="81edc-119">Faites défiler la page jusqu’à la section **Engine**, sélectionnez **Rendering**, développez la section **VR** et cochez les cases **Instanced Stereo** et **Mobile Multi-View**.</span><span class="sxs-lookup"><span data-stu-id="81edc-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="81edc-120">La case Mobile HDR doit être décochée.</span><span class="sxs-lookup"><span data-stu-id="81edc-120">Mobile HDR should be unchecked.</span></span>

![Paramètres de rendu VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="81edc-122">Vérifiez que la **valeur par défaut** ou **D3D12** est la valeur de **RHI par défaut** sélectionnée lors de l’utilisation d’OpenXR.</span><span class="sxs-lookup"><span data-stu-id="81edc-122">Ensure **Default** or **D3D12** is the selected **Default RHI** when using OpenXR.</span></span>
    * <span data-ttu-id="81edc-123">La sélection de **D3D11** aura un impact négatif sur les performances en raison de la plateforme effectuant une passe de rendu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="81edc-123">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="81edc-124">**D3D12** doit permettre d’améliorer les performances de rendu, en plus d’éviter la passe de rendu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="81edc-124">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI par défaut](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="81edc-126">Désactivation du brouillard au niveau des vertex :</span><span class="sxs-lookup"><span data-stu-id="81edc-126">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="81edc-127">Le brouillard au niveau des vertex applique des calculs de brouillard à chaque vertex d’un polygone, puis interpole les résultats sur la face du polygone.</span><span class="sxs-lookup"><span data-stu-id="81edc-127">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="81edc-128">En l’absence de brouillard dans votre jeu, choisissez ce paramètre pour désactiver le brouillard et améliorer les performances d’ombrage.</span><span class="sxs-lookup"><span data-stu-id="81edc-128">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Options de brouillard au niveau des vertex](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="81edc-130">Désactivation de l’élimination de l’occlusion :</span><span class="sxs-lookup"><span data-stu-id="81edc-130">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="81edc-131">Faites défiler la page jusqu’à la section **Engine**, sélectionnez **Rendering**, développez la section **Culling**, puis décochez la case **Occlusion Culling**.</span><span class="sxs-lookup"><span data-stu-id="81edc-131">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="81edc-132">Si vous avez besoin d’éliminer des occlusions pour une scène précise en cours de rendu, nous vous recommandons de cocher la case **Support Software Occlusion Culling** dans **Engine > Rendering**.</span><span class="sxs-lookup"><span data-stu-id="81edc-132">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="81edc-133">Ceci permet à Unreal d’effectuer le travail sur le processeur et d’éviter les requêtes d’occlusion du GPU, dont les performances sont faibles sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="81edc-133">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="81edc-134">L’élimination des occlusions sur le GPU d’appareils mobiles est lente.</span><span class="sxs-lookup"><span data-stu-id="81edc-134">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="81edc-135">En général, vous souhaitez que le GPU se charge principalement du rendu.</span><span class="sxs-lookup"><span data-stu-id="81edc-135">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="81edc-136">Si vous estimez que l’occlusion améliorera les performances, essayez d’activer l’occlusion logicielle à la place.</span><span class="sxs-lookup"><span data-stu-id="81edc-136">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="81edc-137">Notez que l’activation de l’occlusion logicielle peut nuire aux performances si vous êtes déjà lié au processeur par un grand nombre d’appels de dessin.</span><span class="sxs-lookup"><span data-stu-id="81edc-137">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Désactivation de l’élimination de l’occlusion](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="81edc-139">Désactivation de la passe du stencil de profondeur personnalisé :</span><span class="sxs-lookup"><span data-stu-id="81edc-139">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="81edc-140">Cette fonctionnalité nécessite une passe supplémentaire, ce qui signifie qu’elle est lente.</span><span class="sxs-lookup"><span data-stu-id="81edc-140">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="81edc-141">La translucidité est également lente sur Unreal.</span><span class="sxs-lookup"><span data-stu-id="81edc-141">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="81edc-142">Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="81edc-142">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Stencil de profondeur](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="81edc-144">Réduction des cartes d’ombre en cascade (CSM) :</span><span class="sxs-lookup"><span data-stu-id="81edc-144">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="81edc-145">Le fait de réduire le nombre de cartes d’ombre améliore les performances.</span><span class="sxs-lookup"><span data-stu-id="81edc-145">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="81edc-146">En général, définissez une valeur de 1 sauf si vous constatez une perte de qualité visible.</span><span class="sxs-lookup"><span data-stu-id="81edc-146">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Cartes d’ombre en cascade](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="81edc-148">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="81edc-148">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="81edc-149">Les paramètres suivants peuvent améliorer les performances, mais au prix de la désactivation de certaines fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="81edc-149">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="81edc-150">Utilisez ces paramètres uniquement si vous êtes sûr que vous n’avez pas besoin des fonctionnalités en question.</span><span class="sxs-lookup"><span data-stu-id="81edc-150">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="81edc-151">Réduction des permutations de nuanceurs sur mobile</span><span class="sxs-lookup"><span data-stu-id="81edc-151">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="81edc-152">Si vos lumières ne se déplacent pas indépendamment de la caméra, vous pouvez choisir en toute sécurité la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="81edc-152">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="81edc-153">L’avantage principal est la possibilité pour Unreal d’éliminer plusieurs permutations de nuanceurs, accélérant ainsi la compilation des nuanceurs.</span><span class="sxs-lookup"><span data-stu-id="81edc-153">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Réduction des permutations de nuanceurs sur mobile](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="81edc-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81edc-155">See also</span></span>
* [<span data-ttu-id="81edc-156">Recommandations en matière de performances sur mobile pour Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="81edc-156">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)