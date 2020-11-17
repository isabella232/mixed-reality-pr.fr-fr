---
title: Recommandations matérielles dans Unreal
description: Vue d’ensemble des matériaux dans un moteur inréel.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, développement, matériaux, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: d57689e9427ab5877e3afb49b0d19f35df6c47d2
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678938"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="3ee0a-104">Recommandations matérielles dans Unreal</span><span class="sxs-lookup"><span data-stu-id="3ee0a-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="3ee0a-105">Les matériaux peuvent créer ou rompre les performances dans un moteur inréel.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-105">Materials can make or break performance in Unreal Engine.</span></span> <span data-ttu-id="3ee0a-106">Cette page sert de démarrage rapide sur les paramètres de base que vous devez utiliser pour obtenir les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-106">This page acts as a quick-start on the basic settings you should be using in order to get the best performance.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="3ee0a-107">Utilisation de CustomizedUVs</span><span class="sxs-lookup"><span data-stu-id="3ee0a-107">Using CustomizedUVs</span></span>

<span data-ttu-id="3ee0a-108">Si vous devez fournir une mosaïque de UVs sur votre matériel, vous devez utiliser CustomizedUVs au lieu de modifier directement l’UV du nœud de texture.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-108">If you need to provide tiling of UVs on your material, you should use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="3ee0a-109">Les CustomizedUVs permettent de manipuler les UV dans les nuanceurs de vertex plutôt que dans le nuanceur de pixels.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-109">CustomizedUVs allow UV manipulation to happen in the Vertex shaders rather than Pixel shader.</span></span> 

![Paramètres de matériau inréel](images/unreal-materials-img-01c.png)

<span data-ttu-id="3ee0a-111">Vous trouverez plus d’informations sur les documents dans la [documentation du moteur inréel](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) et les exemples de pratiques recommandées dans les captures d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="3ee0a-111">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="3ee0a-112">[ ![ Paramètres de matériau recommandés ](images/unreal-materials-img-01.png) dans ](images/unreal-materials-img-01.png#lightbox)la 
 *configuration d’un matériel non recommandé*</span><span class="sxs-lookup"><span data-stu-id="3ee0a-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="3ee0a-113">[ ![ Paramètres matériels non recommandés dans ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)la 
 *configuration d’un matériau non recommandé*</span><span class="sxs-lookup"><span data-stu-id="3ee0a-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="3ee0a-114">Modifier le mode de fondu</span><span class="sxs-lookup"><span data-stu-id="3ee0a-114">Changing Blend Mode</span></span>

<span data-ttu-id="3ee0a-115">Vous devez définir le mode de fusion sur opaque, à moins qu’il y ait une bonne raison de le faire autrement.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-115">You should set blend mode to opaque unless there is a strong reason to do otherwise.</span></span> <span data-ttu-id="3ee0a-116">Les matériaux masqués et translucides sont lents.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="3ee0a-117">Vous trouverez plus d’informations sur les documents dans la [documentation du moteur inréel](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="3ee0a-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Modifier le mode de fondu](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="3ee0a-119">Mise à jour de l’éclairage pour les appareils mobiles</span><span class="sxs-lookup"><span data-stu-id="3ee0a-119">Updating lighting for mobile</span></span>

<span data-ttu-id="3ee0a-120">La précision maximale doit être désactivée.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-120">Full precision should be turned off.</span></span> <span data-ttu-id="3ee0a-121">L’éclairage lightmap peut être composé en activant des informations directionnelles.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="3ee0a-122">Quand elle est désactivée, l’éclairage de lightmaps est plat, mais moins cher.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Paramètres du matériel mobile en non réel](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="3ee0a-124">Ajustement de l’ombrage vers l’avant</span><span class="sxs-lookup"><span data-stu-id="3ee0a-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="3ee0a-125">Ces options améliorent la fidélité visuelle au détriment des performances.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="3ee0a-126">Ils doivent être désactivés pour des performances maximales.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-126">They should be turned off for maximum performance.</span></span>

![Transférer les paramètres de matériel d’ombrage dans un environnement inréel](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="3ee0a-128">Définition de la translucidité matérielle</span><span class="sxs-lookup"><span data-stu-id="3ee0a-128">Setting material translucency</span></span>

<span data-ttu-id="3ee0a-129">Indique que la matière translucide ne doit pas être affectée par la floraison ou le DDL.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="3ee0a-130">Étant donné que ces deux effets sont rares dans MR, ce paramètre doit être activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Paramètre translucidité distinct mobile dans inréel](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="3ee0a-132">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="3ee0a-132">Optional settings</span></span>

<span data-ttu-id="3ee0a-133">Les paramètres suivants peuvent améliorer les performances, mais notez qu’ils désactivent certaines fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="3ee0a-134">Utilisez ces paramètres uniquement si vous êtes sûr de ne pas avoir besoin des fonctionnalités en question.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-134">Only use these settings if you are sure you don't need the features in question.</span></span>

![Paramètres de matériau facultatifs dans inréel](images/unreal-materials-img-06.jpg)

<span data-ttu-id="3ee0a-136">Si votre matériel ne nécessite pas de réflexions ou d’éclats, la définition de cette option peut améliorer considérablement les performances.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="3ee0a-137">Dans les tests internes, il est aussi rapide que « non éclairé » tout en fournissant des informations d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-137">In internal testing, it is as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="3ee0a-138">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="3ee0a-138">Best practices</span></span>

<span data-ttu-id="3ee0a-139">Les éléments suivants ne sont pas des « paramètres » dans la mesure où il s’agit de meilleures pratiques liées aux documents.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-139">The following are not "settings" as much as they are best practices related to Materials.</span></span>

<span data-ttu-id="3ee0a-140">Lorsque vous créez des paramètres, préférez utiliser des « paramètres statiques » dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="3ee0a-141">Les commutateurs statiques peuvent être utilisés pour supprimer toute une branche d’un matériau sans coût d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="3ee0a-142">Les instances peuvent avoir des valeurs différentes, ce qui permet d’avoir une configuration de nuanceur basé sur un modèle sans perte de performances.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-142">Instances can have different values, making it possible to have a templated shader setup with no performance loss.</span></span> <span data-ttu-id="3ee0a-143">Toutefois, l’inconvénient est que cela crée de nombreuses permutations qui provoqueront un grand nombre de recompilations de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-143">The downside, however, is that this creates many permutations that will cause a lot of shader recompilation.</span></span> <span data-ttu-id="3ee0a-144">Essayez de réduire le nombre de paramètres statiques dans le matériel et le nombre de permutations des paramètres statiques réellement utilisés.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are actually used.</span></span> <span data-ttu-id="3ee0a-145">Vous trouverez plus d’informations sur le rendu des paramètres de matériau dans la [documentation du moteur inréel](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span><span class="sxs-lookup"><span data-stu-id="3ee0a-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![Meilleures pratiques pour les paramètres de matériau](images/unreal-materials-img-07.jpg)

<span data-ttu-id="3ee0a-147">Lors de la création d’instances de matériau, la préférence doit être accordée à une **constante d’instance matérielle** sur une instance de matériau dynamique.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="3ee0a-148">La **constante d’instance Material** est un matériau instancié qui effectue un calcul une seule fois, avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-148">**Material Instance Constant** is an instanced Material that calculates only once, prior to runtime.</span></span>

<span data-ttu-id="3ee0a-149">L’instance de matériau créée via le navigateur de contenu (**cliquez avec le bouton droit > créer une instance de matériau**) est une constante d’instance de matériau.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="3ee0a-150">L’instance de matériau Dynamic est créée à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="3ee0a-151">Vous trouverez plus d’informations sur les instances de matériel dans la [documentation du moteur inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span><span class="sxs-lookup"><span data-stu-id="3ee0a-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Création d’instances de matériau dans des conditions inréelles](images/unreal-materials-img-08.png)

<span data-ttu-id="3ee0a-153">Gardez un œil sur la complexité de vos matériaux/nuanceurs.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="3ee0a-154">Vous pouvez afficher le coût de votre matériel sur différentes plateformes en cliquant sur l’icône statistiques de plateforme.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="3ee0a-155">Vous pouvez également obtenir plus d’informations sur les documents dans la [documentation du moteur inréaliste](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="3ee0a-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Création de paramètres dynamiques d’instance de matériau dans des conditions non réelles](images/unreal-materials-img-09.png)

<span data-ttu-id="3ee0a-157">Vous pouvez obtenir une idée rapide de la complexité relative de votre nuanceur via le [mode d’affichage](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)de la complexité du nuanceur.</span><span class="sxs-lookup"><span data-stu-id="3ee0a-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="3ee0a-158">Raccourci clavier du mode d’affichage : Alt + 8</span><span class="sxs-lookup"><span data-stu-id="3ee0a-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="3ee0a-159">Commande de console : ViewMode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="3ee0a-159">Console command: viewmode shadercomplexity</span></span>

![Complexité de la matière dans le temps](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="3ee0a-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ee0a-161">See also</span></span>
* [<span data-ttu-id="3ee0a-162">Matériel mobile</span><span class="sxs-lookup"><span data-stu-id="3ee0a-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="3ee0a-163">Modes d’affichage</span><span class="sxs-lookup"><span data-stu-id="3ee0a-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="3ee0a-164">Instances de matériau</span><span class="sxs-lookup"><span data-stu-id="3ee0a-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
