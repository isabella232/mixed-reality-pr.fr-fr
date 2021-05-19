---
title: Nuanceur animé
description: Description sur les nuanceurs d’impulsions dans MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: e03c021689b6701b86ae25ba9fa253ece1368428
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144943"
---
# <a name="pulse-shader"></a><span data-ttu-id="a5d5d-104">Nuanceur d’impulsions</span><span class="sxs-lookup"><span data-stu-id="a5d5d-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="a5d5d-106">Utilisez le nuanceur d’impulsions pour animer un effet d’impulsion visuelle sur la reconstruction de la surface, un maillage manuel articulé ou tout autre maillage.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="a5d5d-107">Nuanceur et matériau</span><span class="sxs-lookup"><span data-stu-id="a5d5d-107">Shader and material</span></span>

<span data-ttu-id="a5d5d-108">Les documents suivants utilisent **SR_Triangles** nuanceur.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="a5d5d-109">Vous pouvez configurer diverses options, telles que la couleur de remplissage, la couleur de ligne et la couleur de l’impulsion.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="a5d5d-110">**MRTK_Pulse_SpatialMeshBlue. mat**</span><span class="sxs-lookup"><span data-stu-id="a5d5d-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="a5d5d-111">**MRTK_Pulse_SpatialMeshPurple. mat**</span><span class="sxs-lookup"><span data-stu-id="a5d5d-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="a5d5d-112">**MRTK_Pulse_ArticulatedHandMeshBlue. mat**</span><span class="sxs-lookup"><span data-stu-id="a5d5d-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="a5d5d-113">**MRTK_Pulse_ArticulatedHandMeshPurple. mat**</span><span class="sxs-lookup"><span data-stu-id="a5d5d-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="a5d5d-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="a5d5d-114">Prerequisites</span></span>

<span data-ttu-id="a5d5d-115">Pour l’exemple de maillage spatial, assurez-vous que MRTK_Pulse_ArticulatedHandMeshBlue. mat ou MRTK_Pulse_ArticulatedHandMeshPurple. mat est affecté sous paramètres MRTK-> la sensibilisation spatiale-> paramètres d’affichage-> matériau visible.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="a5d5d-116">Pour l’exemple de maille, assurez-vous que MRTK_Pulse_SpatialMeshBlue. mat ou MRTK_Pulse_SpatialMeshPurple. mat est affecté dans ArticulatedHandMesh. Prefab, qui doit lui-même être affecté dans les paramètres MRTK-> le suivi de la main > d’entrée-> mailler à la main Prefab.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="a5d5d-117">Fonctionnement</span><span class="sxs-lookup"><span data-stu-id="a5d5d-117">How it works</span></span>

<span data-ttu-id="a5d5d-118">Le nuanceur de maille main utilise UVs pour mapper l’impulsion le long de la maille et pour faire disparaître le poignet.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="a5d5d-119">Le nuanceur de reconstruction de surface utilise les positions de vertex pour mapper l’impulsion.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="a5d5d-120">Exemple de maillage spatial-PulseShaderSpatialMeshExample. Unity</span><span class="sxs-lookup"><span data-stu-id="a5d5d-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="a5d5d-121">À l’instar de l’interface de l’interpréteur de commandes HoloLens 2, vous pouvez pointer et appuyer avec la main pour générer un effet d’impulsion sur le maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="a5d5d-122">L’exemple de scène contient un objet ExampleSpatialMesh qui est une maille spatiale de test pour le mode de jeu Unity.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="a5d5d-123">Cet objet sera désactivé et masqué sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="a5d5d-124">Le script **PulseShaderSpatialMeshHandler. cs** génère l’effet d’impulsion sur le maillage spatial à la position du point d’accès si `PulseOnSelect` a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="a5d5d-125">La  `Auto Pulse` propriété peut également avoir la valeur true dans le matériel lui-même pour une animation répétée.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="a5d5d-126">Dans l’exemple de scène, ce script est attaché au Prefab PulseShaderSpatialMeshParent.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="a5d5d-127">Ce Prefab est référencé sous le profil de sensibilisation spatiale via la propriété Runtime spatial Mesh Prefab.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="a5d5d-128">Pendant l’exécution, le Prefab PulseShaderSpatialMeshParent et est instancié et ajouté à la hiérarchie spatiale (uniquement sur l’appareil, ce comportement ne peut pas être observé dans l’éditeur).</span><span class="sxs-lookup"><span data-stu-id="a5d5d-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="a5d5d-129">Exemple de maille manuelle-PulseShaderHandMeshExample. Unity</span><span class="sxs-lookup"><span data-stu-id="a5d5d-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="a5d5d-130">Cet exemple de scène illustre la visualisation du maillage à la main à l’aide du nuanceur Pulse.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="a5d5d-131">Quand une main est détectée par l’appareil HoloLens, l’animation d’impulsions est déclenchée une seule fois.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="a5d5d-132">Cette rétroaction visuelle peut augmenter la confiance de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="a5d5d-133">Le script **PulseShaderHandMeshHandler. cs** génère un effet d’impulsion sur le matériau affecté.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="a5d5d-134">Par défaut, l’option « impulsion en main détectée » est cochée.</span><span class="sxs-lookup"><span data-stu-id="a5d5d-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
