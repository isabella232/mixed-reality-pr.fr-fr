---
title: Recommandations sur les performances pour Unreal
description: Recommandations pour des performances optimales pour les applications de réalité mixte dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, performances, optimisation, paramètres, documentation
ms.openlocfilehash: a369a68f8ebf9b7084c22f0efa3bbf0bf5ecbebf
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865424"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="daa20-104">Recommandations sur les performances pour Unreal</span><span class="sxs-lookup"><span data-stu-id="daa20-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="daa20-105">Unreal Engine comporte plusieurs fonctionnalités capables d’augmenter les performances des applications, toutes basées sur la description présentée dans [Recommandations sur les performances pour la réalité mixte](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="daa20-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="daa20-106">Avant de continuer, nous vous encourageons à vous informer sur les goulots d’étranglement des applications, l’analyse et le profilage des applications de réalité mixte, ainsi que les correctifs des performances généraux.</span><span class="sxs-lookup"><span data-stu-id="daa20-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="daa20-107">Paramètres de projet Unreal recommandés</span><span class="sxs-lookup"><span data-stu-id="daa20-107">Recommended Unreal project settings</span></span>
<span data-ttu-id="daa20-108">Vous trouverez chacun des paramètres suivants dans **Edit > Project Settings**.</span><span class="sxs-lookup"><span data-stu-id="daa20-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="daa20-109">Utilisation du convertisseur VR mobile :</span><span class="sxs-lookup"><span data-stu-id="daa20-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="daa20-110">Faites défiler la page jusqu’à la section **Project**, sélectionnez **Target Hardware**, puis définissez la plateforme cible sur **Mobile/Tablet**.</span><span class="sxs-lookup"><span data-stu-id="daa20-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Définition de la cible mobile](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="daa20-112">Utilisation du renderer Forward :</span><span class="sxs-lookup"><span data-stu-id="daa20-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="daa20-113">Le renderer Forward est bien mieux adapté à la réalité mixte que le pipeline de rendu différé par défaut en raison du nombre de fonctionnalités qui peuvent être désactivées individuellement.</span><span class="sxs-lookup"><span data-stu-id="daa20-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="daa20-114">Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="daa20-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Rendu Forward](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="daa20-116">En utilisant la multivue mobile :</span><span class="sxs-lookup"><span data-stu-id="daa20-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="daa20-117">Faites défiler la page jusqu’à la section **Engine**, sélectionnez **Rendering**, développez la section **VR** et cochez les cases **Instanced Stereo** et **Mobile Multi-View**.</span><span class="sxs-lookup"><span data-stu-id="daa20-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="daa20-118">La case Mobile HDR doit être décochée.</span><span class="sxs-lookup"><span data-stu-id="daa20-118">Mobile HDR should be unchecked.</span></span>

![Paramètres de rendu VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="daa20-120">**[OpenXR uniquement]** Vérifiez que la **valeur par défaut** ou **D3D12** est la valeur de **RHI par défaut** sélectionnée :</span><span class="sxs-lookup"><span data-stu-id="daa20-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="daa20-121">La sélection de **D3D11** aura un impact négatif sur les performances en raison de la plateforme effectuant une passe de rendu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="daa20-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="daa20-122">**D3D12** doit permettre d’améliorer les performances de rendu, en plus d’éviter la passe de rendu supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="daa20-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI par défaut](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="daa20-124">Désactivation du brouillard au niveau des vertex :</span><span class="sxs-lookup"><span data-stu-id="daa20-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="daa20-125">Le brouillard au niveau des vertex applique des calculs de brouillard à chaque vertex d’un polygone, puis interpole les résultats sur la face du polygone.</span><span class="sxs-lookup"><span data-stu-id="daa20-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="daa20-126">Si votre jeu n’utilise pas de brouillard, nous vous recommandons de désactiver le brouillard au niveau des vertex pour augmenter les performances de l’ombrage.</span><span class="sxs-lookup"><span data-stu-id="daa20-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![Options de brouillard au niveau des vertex](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="daa20-128">Désactivation de l’élimination de l’occlusion :</span><span class="sxs-lookup"><span data-stu-id="daa20-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="daa20-129">Faites défiler la page jusqu’à la section **Engine**, sélectionnez **Rendering**, développez la section **Culling**, puis décochez la case **Occlusion Culling**.</span><span class="sxs-lookup"><span data-stu-id="daa20-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="daa20-130">Si vous avez besoin d’éliminer des occlusions pour une scène précise en cours de rendu, nous vous recommandons de cocher la case **Support Software Occlusion Culling** dans **Engine > Rendering**.</span><span class="sxs-lookup"><span data-stu-id="daa20-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="daa20-131">Unreal va effectuer le travail sur le processeur et éviter les requêtes d’occlusion du GPU, dont les performances sont faibles sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="daa20-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="daa20-132">L’élimination des occlusions sur le GPU d’appareils mobiles est lente.</span><span class="sxs-lookup"><span data-stu-id="daa20-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="daa20-133">En général, vous souhaitez que le GPU se charge principalement du rendu.</span><span class="sxs-lookup"><span data-stu-id="daa20-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="daa20-134">Si vous estimez que l’occlusion améliorera les performances, essayez d’activer l’occlusion logicielle à la place.</span><span class="sxs-lookup"><span data-stu-id="daa20-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="daa20-135">L’activation de l’occlusion logicielle peut nuire aux performances si vous êtes déjà lié au processeur par un grand nombre d’appels de dessin.</span><span class="sxs-lookup"><span data-stu-id="daa20-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Désactivation de l’élimination de l’occlusion](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="daa20-137">Désactivation de la passe du stencil de profondeur personnalisé :</span><span class="sxs-lookup"><span data-stu-id="daa20-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="daa20-138">La désactivation du stencil de profondeur personnalisé demande une passe supplémentaire, ce qui signifie qu’il est lent.</span><span class="sxs-lookup"><span data-stu-id="daa20-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="daa20-139">La translucidité est également lente sur Unreal.</span><span class="sxs-lookup"><span data-stu-id="daa20-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="daa20-140">Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="daa20-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Stencil de profondeur](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="daa20-142">Réduction des cartes d’ombre en cascade (CSM) :</span><span class="sxs-lookup"><span data-stu-id="daa20-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="daa20-143">Le fait de réduire le nombre de cartes d’ombre améliore les performances.</span><span class="sxs-lookup"><span data-stu-id="daa20-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="daa20-144">En règle générale, vous devez affecter la valeur 1 à la propriété, sauf si une perte de qualité est visible.</span><span class="sxs-lookup"><span data-stu-id="daa20-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![Cartes d’ombre en cascade](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="daa20-146">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="daa20-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="daa20-147">Les paramètres suivants peuvent améliorer les performances, mais au prix de la désactivation de certaines fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="daa20-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="daa20-148">Utilisez ces paramètres uniquement si vous êtes sûr que vous n’avez pas besoin des fonctionnalités en question.</span><span class="sxs-lookup"><span data-stu-id="daa20-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="daa20-149">Réduction des permutations de nuanceurs sur mobile</span><span class="sxs-lookup"><span data-stu-id="daa20-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="daa20-150">Si vos lumières ne se déplacent pas indépendamment de la caméra, vous pouvez choisir sans problème la valeur 0 pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="daa20-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="daa20-151">L’avantage principal est la possibilité pour Unreal d’éliminer plusieurs permutations de nuanceurs, accélérant ainsi la compilation des nuanceurs.</span><span class="sxs-lookup"><span data-stu-id="daa20-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Réduction des permutations de nuanceurs sur mobile](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="daa20-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daa20-153">See also</span></span>
* [<span data-ttu-id="daa20-154">Recommandations en matière de performances sur mobile pour Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="daa20-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)