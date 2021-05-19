---
title: Système de scène - Éclairage de scènes
description: Documentation sur l’éclairage dans la scène.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144414"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="f79d9-104">Opérations de scène d’éclairage</span><span class="sxs-lookup"><span data-stu-id="f79d9-104">Lighting scene operations</span></span>

<span data-ttu-id="f79d9-105">La scène d’éclairage par défaut définie dans votre profil est chargée au démarrage.</span><span class="sxs-lookup"><span data-stu-id="f79d9-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="f79d9-106">Cette scène d’éclairage reste chargée jusqu’à ce que `SetLightingScene` soit appelé.</span><span class="sxs-lookup"><span data-stu-id="f79d9-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="f79d9-107">Transitions de paramètres d’éclairage</span><span class="sxs-lookup"><span data-stu-id="f79d9-107">Lighting setting transitions</span></span>

<span data-ttu-id="f79d9-108">`transitionType` contrôle le style de la transition vers la nouvelle scène d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="f79d9-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="f79d9-109">Les styles disponibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f79d9-109">The available styles are:</span></span>

<span data-ttu-id="f79d9-110">Type</span><span class="sxs-lookup"><span data-stu-id="f79d9-110">Type</span></span> | <span data-ttu-id="f79d9-111">Description</span><span class="sxs-lookup"><span data-stu-id="f79d9-111">Description</span></span> | <span data-ttu-id="f79d9-112">Duration</span><span class="sxs-lookup"><span data-stu-id="f79d9-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="f79d9-113">None</span><span class="sxs-lookup"><span data-stu-id="f79d9-113">None</span></span> | <span data-ttu-id="f79d9-114">La scène d’éclairage précédente est déchargée, la nouvelle scène d’éclairage est chargée.</span><span class="sxs-lookup"><span data-stu-id="f79d9-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="f79d9-115">Aucune transition.</span><span class="sxs-lookup"><span data-stu-id="f79d9-115">No transition.</span></span> | <span data-ttu-id="f79d9-116">Ignoré</span><span class="sxs-lookup"><span data-stu-id="f79d9-116">Ignored</span></span>
<span data-ttu-id="f79d9-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="f79d9-117">FadeToBlack</span></span> | <span data-ttu-id="f79d9-118">La scène d’éclairage précédente disparaît en noir.</span><span class="sxs-lookup"><span data-stu-id="f79d9-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="f79d9-119">Une nouvelle scène d’éclairage est chargée, puis grisée du noir.</span><span class="sxs-lookup"><span data-stu-id="f79d9-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="f79d9-120">Utile pour les transitions lisses entre les emplacements.</span><span class="sxs-lookup"><span data-stu-id="f79d9-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="f79d9-121">Utilisé</span><span class="sxs-lookup"><span data-stu-id="f79d9-121">Used</span></span>
<span data-ttu-id="f79d9-122">Fondu enchaîné</span><span class="sxs-lookup"><span data-stu-id="f79d9-122">CrossFade</span></span> | <span data-ttu-id="f79d9-123">La scène d’éclairage précédente apparaît en fondu quand de nouvelles scènes d’éclairage sont en fondu.</span><span class="sxs-lookup"><span data-stu-id="f79d9-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="f79d9-124">Utile pour les transitions douces entre les configurations d’éclairage au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="f79d9-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="f79d9-125">Utilisé</span><span class="sxs-lookup"><span data-stu-id="f79d9-125">Used</span></span>

<span data-ttu-id="f79d9-126">Notez que certains paramètres d’éclairage ne peuvent pas être interpolés pendant les transitions.</span><span class="sxs-lookup"><span data-stu-id="f79d9-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="f79d9-127">Si vous souhaitez une transition visuelle lisse, ces paramètres devront rester cohérents entre les scènes d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="f79d9-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="f79d9-128">Paramètre</span><span class="sxs-lookup"><span data-stu-id="f79d9-128">Setting</span></span> | <span data-ttu-id="f79d9-129">Transition Smooth FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="f79d9-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="f79d9-130">Transition Smooth fondu</span><span class="sxs-lookup"><span data-stu-id="f79d9-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="f79d9-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="f79d9-131">Skybox</span></span> | <span data-ttu-id="f79d9-132">Non</span><span class="sxs-lookup"><span data-stu-id="f79d9-132">No</span></span> | <span data-ttu-id="f79d9-133">Non</span><span class="sxs-lookup"><span data-stu-id="f79d9-133">No</span></span>
<span data-ttu-id="f79d9-134">Réflexions personnalisées</span><span class="sxs-lookup"><span data-stu-id="f79d9-134">Custom Reflections</span></span> | <span data-ttu-id="f79d9-135">Non</span><span class="sxs-lookup"><span data-stu-id="f79d9-135">No</span></span> | <span data-ttu-id="f79d9-136">Non</span><span class="sxs-lookup"><span data-stu-id="f79d9-136">No</span></span>
<span data-ttu-id="f79d9-137">Ombres en temps réel Sun</span><span class="sxs-lookup"><span data-stu-id="f79d9-137">Sun light realtime shadows</span></span> | <span data-ttu-id="f79d9-138">Oui</span><span class="sxs-lookup"><span data-stu-id="f79d9-138">Yes</span></span> | <span data-ttu-id="f79d9-139">Non</span><span class="sxs-lookup"><span data-stu-id="f79d9-139">No</span></span>
