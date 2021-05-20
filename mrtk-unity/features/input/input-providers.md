---
title: Fournisseurs d’entrée
description: Documentation sur les différents types de fournisseurs d’entrée dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145259"
---
# <a name="input-providers"></a><span data-ttu-id="bc8f2-104">Fournisseurs d’entrée</span><span class="sxs-lookup"><span data-stu-id="bc8f2-104">Input providers</span></span>

<span data-ttu-id="bc8f2-105">Les fournisseurs d’entrée sont enregistrés dans le **profil des fournisseurs de services inscrits**, qui se trouve dans le composant d’outils de réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="bc8f2-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="bc8f2-106">Il s’agit des fournisseurs d’entrée prêts à l’emploi, ainsi que des contrôleurs correspondants :</span><span class="sxs-lookup"><span data-stu-id="bc8f2-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="bc8f2-107">Fournisseur d’entrée</span><span class="sxs-lookup"><span data-stu-id="bc8f2-107">Input Provider</span></span> | <span data-ttu-id="bc8f2-108">Controllers</span><span class="sxs-lookup"><span data-stu-id="bc8f2-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="bc8f2-109">Simulation de main</span><span class="sxs-lookup"><span data-stu-id="bc8f2-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="bc8f2-110">Souris</span><span class="sxs-lookup"><span data-stu-id="bc8f2-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="bc8f2-111">OpenVR générique, baguette vive, vive Knuckles, Oculus Touch, Oculus à distance, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="bc8f2-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="bc8f2-112">Manette de jeu générique</span><span class="sxs-lookup"><span data-stu-id="bc8f2-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="bc8f2-113">Contrôleur tactile Unity</span><span class="sxs-lookup"><span data-stu-id="bc8f2-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="bc8f2-114">*Aucun*</span><span class="sxs-lookup"><span data-stu-id="bc8f2-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="bc8f2-115">WMR articulée, WMR Controller, WMR GGV (point de regard, geste et voix)</span><span class="sxs-lookup"><span data-stu-id="bc8f2-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="bc8f2-116">*Aucun*</span><span class="sxs-lookup"><span data-stu-id="bc8f2-116">*None*</span></span> |

<span data-ttu-id="bc8f2-117">Les fournisseurs de dictée et de reconnaissance vocale ne créent pas de contrôleurs, ils génèrent leurs propres événements d’entrée spécialisés directement.</span><span class="sxs-lookup"><span data-stu-id="bc8f2-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="bc8f2-118">Vous pouvez créer des fournisseurs d’entrée personnalisés en implémentant l' [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span><span class="sxs-lookup"><span data-stu-id="bc8f2-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="bc8f2-119">Pour plus d’informations, consultez [création d’un fournisseur de données de système d’entrée](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="bc8f2-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
