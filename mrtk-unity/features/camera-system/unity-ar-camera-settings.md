---
title: Paramètres de l’appareil Unity AR
description: Documentation sur l’utilisation de l’appareil photo AR dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, appareil photo,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121197"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="e53a4-104">Fournisseur de paramètres de caméra Unity AR</span><span class="sxs-lookup"><span data-stu-id="e53a4-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="e53a4-105">Le fournisseur de paramètres de l’appareil Unity AR est un composant MRTK expérimental qui permet aux applications de réalité mixte de s’exécuter sur des appareils Android et iOS.</span><span class="sxs-lookup"><span data-stu-id="e53a4-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="e53a4-106">Options du fournisseur des paramètres de l’appareil Unity AR</span><span class="sxs-lookup"><span data-stu-id="e53a4-106">Unity AR camera settings provider options</span></span>

![Configuration des paramètres de l’appareil Unity AR](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="e53a4-108">Pour obtenir un guide sur la façon d’ajouter le fournisseur à votre scène : [Comment configurer MRTK pour iOS et Android](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="e53a4-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="e53a4-109">Paramètres de suivi</span><span class="sxs-lookup"><span data-stu-id="e53a4-109">Tracking settings</span></span>

<span data-ttu-id="e53a4-110">Le fournisseur de paramètres de l’appareil Unity AR permet d’effectuer des options de configuration pour le suivi.</span><span class="sxs-lookup"><span data-stu-id="e53a4-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="e53a4-111">Ces paramètres sont spécifiques à l’implémentation du fournisseur de paramètres d’appareil photo Unity.</span><span class="sxs-lookup"><span data-stu-id="e53a4-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="e53a4-112">**Source de pose**</span><span class="sxs-lookup"><span data-stu-id="e53a4-112">**Pose Source**</span></span>

<span data-ttu-id="e53a4-113">La source de pose définit les types disponibles des poses de suivi de réalité augmentée.</span><span class="sxs-lookup"><span data-stu-id="e53a4-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="e53a4-114">En général, ces valeurs sont mappées à un composant de l’appareil sur lequel l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="e53a4-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="e53a4-115">Les options disponibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="e53a4-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="e53a4-116">Option</span><span class="sxs-lookup"><span data-stu-id="e53a4-116">Option</span></span> | <span data-ttu-id="e53a4-117">Description</span><span class="sxs-lookup"><span data-stu-id="e53a4-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e53a4-118">Center</span><span class="sxs-lookup"><span data-stu-id="e53a4-118">Center</span></span> | <span data-ttu-id="e53a4-119">L’œil central d’un appareil monté en tête.</span><span class="sxs-lookup"><span data-stu-id="e53a4-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="e53a4-120">Caméra couleur</span><span class="sxs-lookup"><span data-stu-id="e53a4-120">Color Camera</span></span> | <span data-ttu-id="e53a4-121">Caméra de couleur d’un appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="e53a4-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="e53a4-122">Head</span><span class="sxs-lookup"><span data-stu-id="e53a4-122">Head</span></span> | <span data-ttu-id="e53a4-123">L’œil-tête d’un appareil monté en tête, souvent légèrement au-dessus du centre.</span><span class="sxs-lookup"><span data-stu-id="e53a4-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="e53a4-124">Œil gauche</span><span class="sxs-lookup"><span data-stu-id="e53a4-124">Left Eye</span></span> | <span data-ttu-id="e53a4-125">L’œil gauche d’un appareil monté en tête.</span><span class="sxs-lookup"><span data-stu-id="e53a4-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="e53a4-126">Pose gauche</span><span class="sxs-lookup"><span data-stu-id="e53a4-126">Left Pose</span></span> | <span data-ttu-id="e53a4-127">Le contrôleur de gauche pose.</span><span class="sxs-lookup"><span data-stu-id="e53a4-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="e53a4-128">Œil droit</span><span class="sxs-lookup"><span data-stu-id="e53a4-128">Right Eye</span></span> | <span data-ttu-id="e53a4-129">L’œil droit d’un appareil monté en tête.</span><span class="sxs-lookup"><span data-stu-id="e53a4-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="e53a4-130">Bonne pose</span><span class="sxs-lookup"><span data-stu-id="e53a4-130">Right Pose</span></span> | <span data-ttu-id="e53a4-131">Le contrôleur de droite pose.</span><span class="sxs-lookup"><span data-stu-id="e53a4-131">The right hand controller pose.</span></span> |

<span data-ttu-id="e53a4-132">La valeur par défaut de la source de pose est **caméra de couleurs**, pour permettre un affichage transparent sur des appareils mobiles, tels qu’un téléphone ou une tablette.</span><span class="sxs-lookup"><span data-stu-id="e53a4-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="e53a4-133">**Type des suivis**</span><span class="sxs-lookup"><span data-stu-id="e53a4-133">**Tracking Type**</span></span>

<span data-ttu-id="e53a4-134">Le type de suivi définit la ou les parties de la pose qui seront utilisées pour le suivi.</span><span class="sxs-lookup"><span data-stu-id="e53a4-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="e53a4-135">Les options disponibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="e53a4-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="e53a4-136">Option</span><span class="sxs-lookup"><span data-stu-id="e53a4-136">Option</span></span> | <span data-ttu-id="e53a4-137">Description</span><span class="sxs-lookup"><span data-stu-id="e53a4-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e53a4-138">Position</span><span class="sxs-lookup"><span data-stu-id="e53a4-138">Position</span></span> | <span data-ttu-id="e53a4-139">Position de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="e53a4-139">The position of the device.</span></span> |
| <span data-ttu-id="e53a4-140">Rotation</span><span class="sxs-lookup"><span data-stu-id="e53a4-140">Rotation</span></span> | <span data-ttu-id="e53a4-141">Rotation de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="e53a4-141">The rotation of the device.</span></span> |
| <span data-ttu-id="e53a4-142">Rotation et position</span><span class="sxs-lookup"><span data-stu-id="e53a4-142">Rotation And Position</span></span> | <span data-ttu-id="e53a4-143">Position et rotation de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="e53a4-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="e53a4-144">La valeur par défaut pour le type de suivi est **rotation et position**, pour activer l’expérience de suivi la plus riche.</span><span class="sxs-lookup"><span data-stu-id="e53a4-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="e53a4-145">**Type de mise à jour**</span><span class="sxs-lookup"><span data-stu-id="e53a4-145">**Update Type**</span></span>

<span data-ttu-id="e53a4-146">Le type de mise à jour définit à quels points, pendant le traitement des trames, les données de pose sont échantillonnées.</span><span class="sxs-lookup"><span data-stu-id="e53a4-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="e53a4-147">Les options disponibles sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="e53a4-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="e53a4-148">Option</span><span class="sxs-lookup"><span data-stu-id="e53a4-148">Option</span></span> | <span data-ttu-id="e53a4-149">Description</span><span class="sxs-lookup"><span data-stu-id="e53a4-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e53a4-150">Avant le rendu</span><span class="sxs-lookup"><span data-stu-id="e53a4-150">Before Render</span></span> | <span data-ttu-id="e53a4-151">Juste avant le rendu.</span><span class="sxs-lookup"><span data-stu-id="e53a4-151">Just before rendering.</span></span> |
| <span data-ttu-id="e53a4-152">Update</span><span class="sxs-lookup"><span data-stu-id="e53a4-152">Update</span></span> | <span data-ttu-id="e53a4-153">Pendant la phase de mise à jour du frame.</span><span class="sxs-lookup"><span data-stu-id="e53a4-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="e53a4-154">Mettre à jour et avant le rendu</span><span class="sxs-lookup"><span data-stu-id="e53a4-154">Update And Before Render</span></span> | <span data-ttu-id="e53a4-155">Pendant la phase de mise à jour et juste avant le rendu.</span><span class="sxs-lookup"><span data-stu-id="e53a4-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="e53a4-156">La valeur par défaut pour le type de suivi est **Update et avant Render**, pour activer la latence de suivi la plus faible.</span><span class="sxs-lookup"><span data-stu-id="e53a4-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="e53a4-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e53a4-157">See also</span></span>

- [<span data-ttu-id="e53a4-158">Vue d’ensemble du système de caméras</span><span class="sxs-lookup"><span data-stu-id="e53a4-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="e53a4-159">Création d’un fournisseur de paramètres d’appareil photo</span><span class="sxs-lookup"><span data-stu-id="e53a4-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
