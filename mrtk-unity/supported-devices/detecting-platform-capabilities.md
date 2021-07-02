---
title: Détection des fonctionnalités de la plateforme
description: Détails des différentes fonctionnalités prises en charge par MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, fonctionnalités,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175522"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="097da-104">Détection des fonctionnalités de la plateforme</span><span class="sxs-lookup"><span data-stu-id="097da-104">Detecting platform capabilities</span></span>

<span data-ttu-id="097da-105">une question courante posée sur le MRTK consiste à savoir quel périphérique spécifique (par exemple, Microsoft HoloLens 2) est utilisé pour exécuter une application.</span><span class="sxs-lookup"><span data-stu-id="097da-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="097da-106">L’identification du matériel exact peut être difficile sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="097da-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="097da-107">Au lieu de cela, le MRTK offre un moyen d’identifier des fonctionnalités spécifiques au moment de l’exécution (par exemple, si le point de terminaison de l’appareil actuel prend en charge les mains articulées).</span><span class="sxs-lookup"><span data-stu-id="097da-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="097da-108">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="097da-108">Capabilities</span></span>

<span data-ttu-id="097da-109">la Shared Computer Toolkit de réalité mixte fournit l' [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) énumération, qui définit un ensemble de fonctionnalités pour lesquelles une application peut interroger au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="097da-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="097da-110">Fonctionnalités du système d’entrée</span><span class="sxs-lookup"><span data-stu-id="097da-110">Input system capabilities</span></span>

<span data-ttu-id="097da-111">Le système d’entrée par défaut MRTK prend en charge l’interrogation des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="097da-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="097da-112">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="097da-112">Capability</span></span> | <span data-ttu-id="097da-113">Description</span><span class="sxs-lookup"><span data-stu-id="097da-113">Description</span></span> |
|---|---|
| <span data-ttu-id="097da-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="097da-114">ArticulatedHand</span></span> | <span data-ttu-id="097da-115">Entrée articulée</span><span class="sxs-lookup"><span data-stu-id="097da-115">Articulated hand input</span></span> |
| <span data-ttu-id="097da-116">Suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="097da-116">EyeTracking</span></span> | <span data-ttu-id="097da-117">Ciblage en regard des yeux</span><span class="sxs-lookup"><span data-stu-id="097da-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="097da-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="097da-118">GGVHand</span></span> | <span data-ttu-id="097da-119">Entrée de mouvement de regard</span><span class="sxs-lookup"><span data-stu-id="097da-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="097da-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="097da-120">MotionController</span></span> | <span data-ttu-id="097da-121">Entrée du contrôleur de mouvement</span><span class="sxs-lookup"><span data-stu-id="097da-121">Motion controller input</span></span> |
| <span data-ttu-id="097da-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="097da-122">VoiceCommand</span></span> | <span data-ttu-id="097da-123">Commandes vocales utilisant des mots clés définis par l’application</span><span class="sxs-lookup"><span data-stu-id="097da-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="097da-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="097da-124">VoiceDictation</span></span> | <span data-ttu-id="097da-125">Dictée de voix et de texte</span><span class="sxs-lookup"><span data-stu-id="097da-125">Voice to text dictation</span></span> |

<span data-ttu-id="097da-126">L’exemple de code ci-dessous vérifie si le système d’entrée a chargé un fournisseur de données avec prise en charge des mains articulées.</span><span class="sxs-lookup"><span data-stu-id="097da-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="097da-127">Fonctionnalités de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="097da-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="097da-128">Le système de sensibilisation spatiale par défaut MRTK prend en charge l’interrogation des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="097da-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="097da-129">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="097da-129">Capability</span></span> | <span data-ttu-id="097da-130">Description</span><span class="sxs-lookup"><span data-stu-id="097da-130">Description</span></span> |
|---|---|
| <span data-ttu-id="097da-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="097da-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="097da-132">Maillages spatiaux</span><span class="sxs-lookup"><span data-stu-id="097da-132">Spatial meshes</span></span> |
| <span data-ttu-id="097da-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="097da-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="097da-134">Plans spatiaux</span><span class="sxs-lookup"><span data-stu-id="097da-134">Spatial planes</span></span> |
| <span data-ttu-id="097da-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="097da-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="097da-136">Points spatiaux</span><span class="sxs-lookup"><span data-stu-id="097da-136">Spatial points</span></span> |

<span data-ttu-id="097da-137">Cet exemple vérifie si le système de sensibilisation spatiale a chargé un fournisseur de données avec prise en charge des maillages spatiaux.</span><span class="sxs-lookup"><span data-stu-id="097da-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="097da-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="097da-138">See also</span></span>

- [<span data-ttu-id="097da-139">Documentation de l’API IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="097da-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="097da-140">Documentation de l’énumération MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="097da-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
