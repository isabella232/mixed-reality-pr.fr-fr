---
title: Détection des fonctionnalités de plateforme
description: Détails des différentes fonctionnalités prises en charge par MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, fonctionnalités,
ms.openlocfilehash: e6f5a70120b2634a4c8c75cdca3d8b369967c4b0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143862"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="8f703-104">Détection des fonctionnalités de la plateforme</span><span class="sxs-lookup"><span data-stu-id="8f703-104">Detecting platform capabilities</span></span>

<span data-ttu-id="8f703-105">Une question courante posée sur le MRTK consiste à savoir quel périphérique spécifique (par exemple, Microsoft HoloLens 2) est utilisé pour exécuter une application.</span><span class="sxs-lookup"><span data-stu-id="8f703-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="8f703-106">L’identification du matériel exact peut être difficile sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="8f703-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="8f703-107">Au lieu de cela, le MRTK offre un moyen d’identifier des fonctionnalités spécifiques au moment de l’exécution (par exemple, si le point de terminaison de l’appareil actuel prend en charge les mains articulées).</span><span class="sxs-lookup"><span data-stu-id="8f703-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="8f703-108">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="8f703-108">Capabilities</span></span>

<span data-ttu-id="8f703-109">La boîte à outils de réalité mixte fournit l' [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) énumération, qui définit un ensemble de fonctionnalités pour lesquelles une application peut interroger au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8f703-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="8f703-110">Fonctionnalités du système d’entrée</span><span class="sxs-lookup"><span data-stu-id="8f703-110">Input system capabilities</span></span>

<span data-ttu-id="8f703-111">Le système d’entrée par défaut MRTK prend en charge l’interrogation des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f703-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="8f703-112">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="8f703-112">Capability</span></span> | <span data-ttu-id="8f703-113">Description</span><span class="sxs-lookup"><span data-stu-id="8f703-113">Description</span></span> |
|---|---|
| <span data-ttu-id="8f703-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="8f703-114">ArticulatedHand</span></span> | <span data-ttu-id="8f703-115">Entrée articulée</span><span class="sxs-lookup"><span data-stu-id="8f703-115">Articulated hand input</span></span> |
| <span data-ttu-id="8f703-116">Suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="8f703-116">EyeTracking</span></span> | <span data-ttu-id="8f703-117">Ciblage en regard des yeux</span><span class="sxs-lookup"><span data-stu-id="8f703-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="8f703-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="8f703-118">GGVHand</span></span> | <span data-ttu-id="8f703-119">Entrée de mouvement de regard</span><span class="sxs-lookup"><span data-stu-id="8f703-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="8f703-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="8f703-120">MotionController</span></span> | <span data-ttu-id="8f703-121">Entrée du contrôleur de mouvement</span><span class="sxs-lookup"><span data-stu-id="8f703-121">Motion controller input</span></span> |
| <span data-ttu-id="8f703-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="8f703-122">VoiceCommand</span></span> | <span data-ttu-id="8f703-123">Commandes vocales utilisant des mots clés définis par l’application</span><span class="sxs-lookup"><span data-stu-id="8f703-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="8f703-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="8f703-124">VoiceDictation</span></span> | <span data-ttu-id="8f703-125">Dictée de voix et de texte</span><span class="sxs-lookup"><span data-stu-id="8f703-125">Voice to text dictation</span></span> |

<span data-ttu-id="8f703-126">L’exemple de code ci-dessous vérifie si le système d’entrée a chargé un fournisseur de données avec prise en charge des mains articulées.</span><span class="sxs-lookup"><span data-stu-id="8f703-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="8f703-127">Fonctionnalités de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="8f703-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="8f703-128">Le système de sensibilisation spatiale par défaut MRTK prend en charge l’interrogation des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f703-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="8f703-129">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="8f703-129">Capability</span></span> | <span data-ttu-id="8f703-130">Description</span><span class="sxs-lookup"><span data-stu-id="8f703-130">Description</span></span> |
|---|---|
| <span data-ttu-id="8f703-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="8f703-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="8f703-132">Maillages spatiaux</span><span class="sxs-lookup"><span data-stu-id="8f703-132">Spatial meshes</span></span> |
| <span data-ttu-id="8f703-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="8f703-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="8f703-134">Plans spatiaux</span><span class="sxs-lookup"><span data-stu-id="8f703-134">Spatial planes</span></span> |
| <span data-ttu-id="8f703-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="8f703-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="8f703-136">Points spatiaux</span><span class="sxs-lookup"><span data-stu-id="8f703-136">Spatial points</span></span> |

<span data-ttu-id="8f703-137">Cet exemple vérifie si le système de sensibilisation spatiale a chargé un fournisseur de données avec prise en charge des maillages spatiaux.</span><span class="sxs-lookup"><span data-stu-id="8f703-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="8f703-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f703-138">See also</span></span>

- [<span data-ttu-id="8f703-139">Documentation de l’API IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="8f703-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="8f703-140">Documentation de l’énumération MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="8f703-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
