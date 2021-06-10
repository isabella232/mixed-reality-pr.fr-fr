---
title: Affichage de la progression
description: Découvrez comment les contrôles de progression fournissent aux utilisateurs des commentaires sur l’exécution d’une opération de longue durée dans vos applications de réalité mixte.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, contrôles, UI, UX, indicateur de progression, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, kit de temps de réalité mixte
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600548"
---
# <a name="progress-indicator"></a><span data-ttu-id="3d162-104">Indicateur de progression</span><span class="sxs-lookup"><span data-stu-id="3d162-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="3d162-105">Un contrôle de progression fournit des commentaires qu’une opération de longue durée est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3d162-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="3d162-106">Lorsqu’un indicateur de progression est visible, les utilisateurs peuvent voir le temps d’attente et ne peuvent pas interagir avec l’application.</span><span class="sxs-lookup"><span data-stu-id="3d162-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="3d162-107">Types de progression</span><span class="sxs-lookup"><span data-stu-id="3d162-107">Types of progress</span></span>

<span data-ttu-id="3d162-108">Il est important de fournir les informations de l’utilisateur sur ce qui se passe.</span><span class="sxs-lookup"><span data-stu-id="3d162-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="3d162-109">En réalité mixte, les utilisateurs peuvent être facilement gênés par l’environnement physique ou les objets si votre application n’a pas de commentaires visuels corrects.</span><span class="sxs-lookup"><span data-stu-id="3d162-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="3d162-110">Pour les situations qui prennent quelques secondes, par exemple lors du chargement de données ou lors de la mise à jour d’une scène, il est judicieux d’afficher un indicateur visuel.</span><span class="sxs-lookup"><span data-stu-id="3d162-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="3d162-111">Il existe deux options pour montrer à l’utilisateur qu’une opération est en cours d’exécution : une **barre de progression** ou un **anneau de progression**.</span><span class="sxs-lookup"><span data-stu-id="3d162-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="3d162-112">Barre de progression</span><span class="sxs-lookup"><span data-stu-id="3d162-112">Progress bar</span></span><br>
        <span data-ttu-id="3d162-113">Une barre de progression indique le pourcentage d’achèvement d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="3d162-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="3d162-114">Elle doit être utilisée pendant une opération dont la durée est connue (se terminer), mais sa progression ne doit pas bloquer l’interaction de l’utilisateur avec l’application.</span><span class="sxs-lookup"><span data-stu-id="3d162-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="3d162-115">*Image : exemple de barre de progression dans HoloLens*</span><span class="sxs-lookup"><span data-stu-id="3d162-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3d162-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3d162-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3d162-117">![Exemple de barre de progression dans HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="3d162-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="3d162-118">Anneau de progression</span><span class="sxs-lookup"><span data-stu-id="3d162-118">Progress ring</span></span><br>
        <span data-ttu-id="3d162-119">Un anneau de progression n’a qu’un état indéterminé et doit être utilisé lorsque l’interaction avec l’utilisateur est bloquée jusqu’à ce que l’opération soit terminée.</span><span class="sxs-lookup"><span data-stu-id="3d162-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="3d162-120">*Image : exemple de sonnerie de progression dans HoloLens*</span><span class="sxs-lookup"><span data-stu-id="3d162-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3d162-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3d162-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3d162-122">![Exemple de sonnerie de progression sur un appareil HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="3d162-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="3d162-123">Progression avec un objet personnalisé</span><span class="sxs-lookup"><span data-stu-id="3d162-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="3d162-124">Vous pouvez ajouter à la personnalité et à l’identité de votre application en personnalisant le contrôle de progression avec vos propres objets 2D/3D personnalisés.</span><span class="sxs-lookup"><span data-stu-id="3d162-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="3d162-125">*Image : progression avec un exemple de maillage personnalisé dans HoloLens*</span><span class="sxs-lookup"><span data-stu-id="3d162-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3d162-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3d162-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3d162-127">![Progression avec l’exemple de maille personnalisé dans HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="3d162-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="3d162-128">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="3d162-128">Best practices</span></span>

* <span data-ttu-id="3d162-129">Couplez étroitement le [billboarding ou la balise](billboarding-and-tag-along.md) à l’affichage de la progression puisque l’utilisateur peut facilement déplacer son tête dans un espace vide et perdre le contexte.</span><span class="sxs-lookup"><span data-stu-id="3d162-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="3d162-130">Votre application peut sembler se bloquer si l’utilisateur ne parvient pas à voir quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="3d162-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="3d162-131">Le billboarding et la balise sont intégrés au Prefab Progress.</span><span class="sxs-lookup"><span data-stu-id="3d162-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="3d162-132">Il est toujours judicieux de fournir des informations d’État sur ce qui se passe à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3d162-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="3d162-133">Le Prefab de progression fournit différents styles visuels, y compris la progression de type Ring Windows standard pour la fourniture de l’État.</span><span class="sxs-lookup"><span data-stu-id="3d162-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="3d162-134">Vous pouvez également utiliser une maille personnalisée avec une animation si vous souhaitez que le style de la progression s’aligne sur la personnalisation de votre application.</span><span class="sxs-lookup"><span data-stu-id="3d162-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="3d162-135">Indicateur de progression dans MRTK (ensemble d’outils de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="3d162-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="3d162-136">MRTK-indicateur de progression prefabs</span><span class="sxs-lookup"><span data-stu-id="3d162-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="3d162-137">MRTK-service de transition de scène</span><span class="sxs-lookup"><span data-stu-id="3d162-137">MRTK - Scene transition service</span></span>](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a><span data-ttu-id="3d162-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d162-138">See also</span></span>

* [<span data-ttu-id="3d162-139">Curseurs</span><span class="sxs-lookup"><span data-stu-id="3d162-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="3d162-140">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="3d162-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="3d162-141">Button</span><span class="sxs-lookup"><span data-stu-id="3d162-141">Button</span></span>](button.md)
* [<span data-ttu-id="3d162-142">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="3d162-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3d162-143">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="3d162-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="3d162-144">Manipulation</span><span class="sxs-lookup"><span data-stu-id="3d162-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3d162-145">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="3d162-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="3d162-146">Menu proche</span><span class="sxs-lookup"><span data-stu-id="3d162-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="3d162-147">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="3d162-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3d162-148">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="3d162-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="3d162-149">Clavier</span><span class="sxs-lookup"><span data-stu-id="3d162-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="3d162-150">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="3d162-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="3d162-151">Tablette</span><span class="sxs-lookup"><span data-stu-id="3d162-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="3d162-152">Curseur</span><span class="sxs-lookup"><span data-stu-id="3d162-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="3d162-153">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="3d162-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="3d162-154">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="3d162-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="3d162-155">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="3d162-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="3d162-156">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="3d162-156">Surface magnetism</span></span>](surface-magnetism.md)