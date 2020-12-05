---
title: Recommandations matérielles dans Unreal
description: Vue d’ensemble des matériaux dans un moteur inréel.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, développement, matériaux, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 11c10577bd3946facb96fd77b09265ab5ca26f24
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609570"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="d7956-104">Recommandations matérielles dans Unreal</span><span class="sxs-lookup"><span data-stu-id="d7956-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="d7956-105">Les documents que vous utilisez peuvent affecter directement la manière dont vos projets s’exécutent dans un moteur inréel.</span><span class="sxs-lookup"><span data-stu-id="d7956-105">The materials you use can directly affect how well your projects run in Unreal Engine.</span></span> <span data-ttu-id="d7956-106">Cette page fait office de démarrage rapide pour les paramètres de base que vous devez utiliser pour obtenir des performances optimales de vos applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="d7956-106">This page acts as a quick-start for the basic settings you should be using to get the best performance out of your mixed reality applications.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="d7956-107">Utilisation de CustomizedUVs</span><span class="sxs-lookup"><span data-stu-id="d7956-107">Using CustomizedUVs</span></span>

<span data-ttu-id="d7956-108">Si vous devez fournir une mosaïque UV sur votre matériau, utilisez CustomizedUVs au lieu de modifier directement l’UV du nœud de la texture.</span><span class="sxs-lookup"><span data-stu-id="d7956-108">If you need to provide UV tiling on your material, use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="d7956-109">CustomizedUVs vous permettent de manipuler des UVs dans les nuanceurs de vertex plutôt que dans le nuanceur de pixels.</span><span class="sxs-lookup"><span data-stu-id="d7956-109">CustomizedUVs let you manipulate UVs in the Vertex shaders rather than the Pixel shader.</span></span>

![Paramètres de matériau inréel](images/unreal-materials-img-01c.png)

<span data-ttu-id="d7956-111">Vous trouverez des détails sur le matériel dans la [documentation du moteur inréaliste](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) et les exemples de pratiques recommandées dans les captures d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d7956-111">You can find material details in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="d7956-112">[ ![ Paramètres de matériau recommandés ](images/unreal-materials-img-01.png) dans ](images/unreal-materials-img-01.png#lightbox)la 
 *configuration d’un matériel non recommandé*</span><span class="sxs-lookup"><span data-stu-id="d7956-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="d7956-113">[ ![ Paramètres matériels non recommandés dans ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)la 
 *configuration d’un matériau non recommandé*</span><span class="sxs-lookup"><span data-stu-id="d7956-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="d7956-114">Modifier le mode de fondu</span><span class="sxs-lookup"><span data-stu-id="d7956-114">Changing Blend Mode</span></span>

<span data-ttu-id="d7956-115">Nous vous recommandons de définir le mode de fusion sur opaque, à moins qu’il y ait une bonne raison de le faire autrement.</span><span class="sxs-lookup"><span data-stu-id="d7956-115">We recommend setting the blend mode to opaque unless there's a strong reason to do otherwise.</span></span> <span data-ttu-id="d7956-116">Les matériaux masqués et translucides sont lents.</span><span class="sxs-lookup"><span data-stu-id="d7956-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="d7956-117">Vous trouverez plus d’informations sur les documents dans la [documentation du moteur inréel](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="d7956-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Modifier le mode de fondu](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="d7956-119">Mise à jour de l’éclairage pour les appareils mobiles</span><span class="sxs-lookup"><span data-stu-id="d7956-119">Updating lighting for mobile</span></span>

<span data-ttu-id="d7956-120">La précision maximale doit être désactivée.</span><span class="sxs-lookup"><span data-stu-id="d7956-120">Full precision should be turned off.</span></span> <span data-ttu-id="d7956-121">L’éclairage lightmap peut être composé en activant des informations directionnelles.</span><span class="sxs-lookup"><span data-stu-id="d7956-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="d7956-122">Quand elle est désactivée, l’éclairage de lightmaps est plat, mais moins cher.</span><span class="sxs-lookup"><span data-stu-id="d7956-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Paramètres du matériel mobile en non réel](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="d7956-124">Ajustement de l’ombrage vers l’avant</span><span class="sxs-lookup"><span data-stu-id="d7956-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="d7956-125">Ces options améliorent la fidélité visuelle au détriment des performances.</span><span class="sxs-lookup"><span data-stu-id="d7956-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="d7956-126">Ils doivent être désactivés pour des performances maximales.</span><span class="sxs-lookup"><span data-stu-id="d7956-126">They should be turned off for maximum performance.</span></span>

![Transférer les paramètres de matériel d’ombrage dans un environnement inréel](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="d7956-128">Définition de la translucidité matérielle</span><span class="sxs-lookup"><span data-stu-id="d7956-128">Setting material translucency</span></span>

<span data-ttu-id="d7956-129">Indique que la matière translucide ne doit pas être affectée par la floraison ou le DDL.</span><span class="sxs-lookup"><span data-stu-id="d7956-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="d7956-130">Étant donné que ces deux effets sont rares dans MR, ce paramètre doit être activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="d7956-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Paramètre translucidité distinct mobile dans inréel](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="d7956-132">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="d7956-132">Optional settings</span></span>

<span data-ttu-id="d7956-133">Les paramètres suivants peuvent améliorer les performances, mais notez qu’ils désactivent certaines fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d7956-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="d7956-134">Utilisez ces paramètres uniquement si vous êtes sûr que vous n’avez pas besoin des fonctionnalités en question.</span><span class="sxs-lookup"><span data-stu-id="d7956-134">Only use these settings if you're sure you don't need the features in question.</span></span>

![Paramètres de matériau facultatifs dans inréel](images/unreal-materials-img-06.jpg)

<span data-ttu-id="d7956-136">Si votre matériel ne nécessite pas de réflexions ou d’éclats, la définition de cette option peut améliorer considérablement les performances.</span><span class="sxs-lookup"><span data-stu-id="d7956-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="d7956-137">Dans les tests internes, il est aussi rapide que « non éclairé » tout en fournissant des informations d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="d7956-137">In internal testing, it's as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="d7956-138">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="d7956-138">Best practices</span></span>

<span data-ttu-id="d7956-139">Les éléments suivants ne sont pas des « paramètres » dans la mesure où ils sont les meilleures pratiques liées aux documents.</span><span class="sxs-lookup"><span data-stu-id="d7956-139">The following aren't "settings" as much as they're best practices related to Materials.</span></span>

<span data-ttu-id="d7956-140">Lorsque vous créez des paramètres, préférez utiliser des « paramètres statiques » dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="d7956-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="d7956-141">Les commutateurs statiques peuvent être utilisés pour supprimer toute une branche d’un matériau sans coût d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d7956-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="d7956-142">Les instances peuvent avoir des valeurs différentes, ce qui rend possible la configuration d’un nuanceur basé sur un modèle sans perte de performances.</span><span class="sxs-lookup"><span data-stu-id="d7956-142">Instances can have different values, making it possible to have a templated shader set up with no performance loss.</span></span> <span data-ttu-id="d7956-143">L’inconvénient, c’est que plusieurs permutations sont créées, ce qui entraîne la recompilation du nuanceur.</span><span class="sxs-lookup"><span data-stu-id="d7956-143">The downside, is that several permutations are created that will cause shader recompilation.</span></span> <span data-ttu-id="d7956-144">Essayez de réduire le nombre de paramètres statiques dans le matériel et le nombre de permutations des paramètres statiques utilisés.</span><span class="sxs-lookup"><span data-stu-id="d7956-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are used.</span></span> <span data-ttu-id="d7956-145">Vous trouverez plus d’informations sur le rendu des paramètres de matériau dans la [documentation du moteur inréel](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span><span class="sxs-lookup"><span data-stu-id="d7956-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![Meilleures pratiques pour les paramètres de matériau](images/unreal-materials-img-07.jpg)

<span data-ttu-id="d7956-147">Lors de la création d’instances de matériau, la préférence doit être accordée à une **constante d’instance matérielle** sur une instance de matériau dynamique.</span><span class="sxs-lookup"><span data-stu-id="d7956-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="d7956-148">La **constante d’instance Material** est un matériau instancié qui calcule une seule fois avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d7956-148">**Material Instance Constant** is an instanced Material that calculates only once before runtime.</span></span>

<span data-ttu-id="d7956-149">L’instance de matériau créée via le navigateur de contenu (**cliquez avec le bouton droit > créer une instance de matériau**) est une constante d’instance de matériau.</span><span class="sxs-lookup"><span data-stu-id="d7956-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="d7956-150">L’instance de matériau Dynamic est créée à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="d7956-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="d7956-151">Vous trouverez plus d’informations sur les instances de matériel dans la [documentation du moteur inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span><span class="sxs-lookup"><span data-stu-id="d7956-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Création d’instances de matériau dans des conditions inréelles](images/unreal-materials-img-08.png)

<span data-ttu-id="d7956-153">Gardez un œil sur la complexité de vos matériaux/nuanceurs.</span><span class="sxs-lookup"><span data-stu-id="d7956-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="d7956-154">Vous pouvez afficher le coût de votre matériel sur différentes plateformes en cliquant sur l’icône statistiques de plateforme.</span><span class="sxs-lookup"><span data-stu-id="d7956-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="d7956-155">Vous pouvez également obtenir plus d’informations sur les documents dans la [documentation du moteur inréaliste](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="d7956-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Création de paramètres dynamiques d’instance de matériau dans des conditions non réelles](images/unreal-materials-img-09.png)

<span data-ttu-id="d7956-157">Vous pouvez obtenir une idée rapide de la complexité relative de votre nuanceur via le [mode d’affichage](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)de la complexité du nuanceur.</span><span class="sxs-lookup"><span data-stu-id="d7956-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="d7956-158">Raccourci clavier du mode d’affichage : Alt + 8</span><span class="sxs-lookup"><span data-stu-id="d7956-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="d7956-159">Commande de console : ViewMode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="d7956-159">Console command: viewmode shadercomplexity</span></span>

![Complexité de la matière dans le temps](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="d7956-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7956-161">See also</span></span>
* [<span data-ttu-id="d7956-162">Matériel mobile</span><span class="sxs-lookup"><span data-stu-id="d7956-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="d7956-163">Modes d’affichage</span><span class="sxs-lookup"><span data-stu-id="d7956-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="d7956-164">Instances de matériau</span><span class="sxs-lookup"><span data-stu-id="d7956-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
