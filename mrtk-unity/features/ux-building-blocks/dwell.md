---
title: Situés
description: Interaction du logement
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Logement, Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647768"
---
# <a name="dwell"></a><span data-ttu-id="53615-104">Situés</span><span class="sxs-lookup"><span data-stu-id="53615-104">Dwell</span></span>

![Héros du logement](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="53615-106">Le point de regard et le front-tête sont très utiles dans les scénarios où les mains d’une personne sont occupées par d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="53615-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="53615-107">Cette fonctionnalité est également utile lorsque la voix n’est pas 100% fiable ou disponible en raison de contraintes environnementales ou sociales.</span><span class="sxs-lookup"><span data-stu-id="53615-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="53615-108">Les exemples de logements de MRTK illustrent différents types de composants de l’interface utilisateur avec un temps de réponse configurable et des commentaires visuels.</span><span class="sxs-lookup"><span data-stu-id="53615-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="53615-109">Pour connaître les recommandations en matière de conception, consultez la page des indications sur la [tête et le point d’intersection](/windows/mixed-reality/design/gaze-and-dwell-head) .</span><span class="sxs-lookup"><span data-stu-id="53615-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="53615-110">Scripts de logement</span><span class="sxs-lookup"><span data-stu-id="53615-110">Dwell scripts</span></span>

- <span data-ttu-id="53615-111">**DwellHandler**: ajoute une modalité de logement à la cible de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="53615-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="53615-112">**DwellStateType**: États du gestionnaire de logements.</span><span class="sxs-lookup"><span data-stu-id="53615-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="53615-113">**DwellUnityEvent**: événement Unity pour un événement de logement.</span><span class="sxs-lookup"><span data-stu-id="53615-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="53615-114">Contient la référence du pointeur.</span><span class="sxs-lookup"><span data-stu-id="53615-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="53615-115">**BaseDwellPressableButton. cs** : script qui déclenche l’événement OnClick () dans `Interactable` de PressableButtonHoloLens2 prefabs.</span><span class="sxs-lookup"><span data-stu-id="53615-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="53615-116">**ToggleDwellPressableButton. cs** : ce script modifie `_BorderWidth` la propriété du `dwellVisualImage` qui utilise le nuanceur standard MRTK.</span><span class="sxs-lookup"><span data-stu-id="53615-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="53615-117">Profils de logement</span><span class="sxs-lookup"><span data-stu-id="53615-117">Dwell profiles</span></span>
<span data-ttu-id="53615-118">Les profils de logement sont utilisés par le **Gestionnaire de logements** pour configurer les différents seuils.</span><span class="sxs-lookup"><span data-stu-id="53615-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="53615-119">**ButtonDwellProfile. Asset**</span><span class="sxs-lookup"><span data-stu-id="53615-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="53615-120">**InstandDwellProfile. Asset**</span><span class="sxs-lookup"><span data-stu-id="53615-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="53615-121">**DwellProfileWithDecay. Asset**</span><span class="sxs-lookup"><span data-stu-id="53615-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="53615-122">Prefabs</span><span class="sxs-lookup"><span data-stu-id="53615-122">Prefabs</span></span>

<span data-ttu-id="53615-123">Ces prefabs sont des variantes du bouton prefabs du style HoloLens 2 qui ont des composants supplémentaires pour prendre en charge les interactions du logement.</span><span class="sxs-lookup"><span data-stu-id="53615-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="53615-124">**PressableButtonHoloLens2_Dwell. Prefab**</span><span class="sxs-lookup"><span data-stu-id="53615-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="53615-125">**PressableButtonHoloLens2_32x96_Dwell. Prefab**</span><span class="sxs-lookup"><span data-stu-id="53615-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="53615-126">**PressableButtonHoloLens2ToggleDwell. Prefab**</span><span class="sxs-lookup"><span data-stu-id="53615-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="53615-127">**PressableButtonHoloLens2Toggle_32x96_Dwell. Prefab**</span><span class="sxs-lookup"><span data-stu-id="53615-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="53615-128">Ces prefabs ont un composant **QuadDwellVisual** supplémentaire pour visualiser l’état d’entrée du logement.</span><span class="sxs-lookup"><span data-stu-id="53615-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="53615-129">Elle est assignée à **HolographicBackPlateDwellVisual. mat** .</span><span class="sxs-lookup"><span data-stu-id="53615-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="53615-130">**ToggleDwellPressableButton. cs** met à jour la propriété **_BorderWidth** du nuanceur standard MRTK pour visualiser l’entrée du logement.</span><span class="sxs-lookup"><span data-stu-id="53615-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="53615-131">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="53615-131">Example scene</span></span>

<span data-ttu-id="53615-132">Vous trouverez des exemples dans la `DwellExample` scène.</span><span class="sxs-lookup"><span data-stu-id="53615-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="53615-133">L’exemple de scène montre à la fois des exemples volumétriques et des exemples d’interface utilisateur Unity.</span><span class="sxs-lookup"><span data-stu-id="53615-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="53615-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53615-134">See also</span></span>

- [<span data-ttu-id="53615-135">**Boutons**</span><span class="sxs-lookup"><span data-stu-id="53615-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="53615-136">**Avec interaction**</span><span class="sxs-lookup"><span data-stu-id="53615-136">**Interactable**</span></span>](interactable.md)
