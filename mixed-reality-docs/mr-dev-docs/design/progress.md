---
title: Affichage de la progression
description: Découvrez comment les contrôles de progression fournissent aux utilisateurs des commentaires sur l’exécution d’une opération de longue durée dans vos applications de réalité mixte.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, contrôles, interface utilisateur, expérience utilisateur, indicateur de progression, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, réalité mixte Shared Computer Toolkit
ms.openlocfilehash: 8d397f627b55409d640ac6925a72d6bf169e207c27cb2a90bcee990c7a8d7683
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207879"
---
# <a name="progress-indicator"></a>Indicateur de progression

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Un contrôle de progression fournit des commentaires qu’une opération de longue durée est en cours d’exécution. Lorsqu’un indicateur de progression est visible, les utilisateurs peuvent voir le temps d’attente et ne peuvent pas interagir avec l’application.

<br>

---

## <a name="types-of-progress"></a>Types de progression

Il est important de fournir les informations de l’utilisateur sur ce qui se passe. En réalité mixte, les utilisateurs peuvent être facilement gênés par l’environnement physique ou les objets si votre application n’a pas de commentaires visuels corrects. Pour les situations qui prennent quelques secondes, par exemple lors du chargement de données ou lors de la mise à jour d’une scène, il est judicieux d’afficher un indicateur visuel. Il existe deux options pour montrer à l’utilisateur qu’une opération est en cours d’exécution : une **barre de progression** ou un **anneau de progression**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barre de progression<br>
        Une barre de progression indique le pourcentage d’achèvement d’une tâche. Elle doit être utilisée pendant une opération dont la durée est connue (se terminer), mais sa progression ne doit pas bloquer l’interaction de l’utilisateur avec l’application.<br>
        <br>
        *Image : exemple de barre de progression dans HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Exemple de barre de progression dans HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Anneau de progression<br>
        Un anneau de progression n’a qu’un état indéterminé et doit être utilisé lorsque l’interaction avec l’utilisateur est bloquée jusqu’à ce que l’opération soit terminée.<br>
        <br>
        *Image : exemple de sonnerie de progression dans HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![exemple de sonnerie de progression sur HoloLens appareil](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Progression avec un objet personnalisé<br>
        Vous pouvez ajouter à la personnalité et à l’identité de votre application en personnalisant le contrôle de progression avec vos propres objets 2D/3D personnalisés.<br>
        <br>
        *Image : progression avec l’exemple de maille personnalisé dans HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Progression avec l’exemple de maille personnalisé dans HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Bonnes pratiques

* Couplez étroitement le [billboarding ou la balise](billboarding-and-tag-along.md) à l’affichage de la progression puisque l’utilisateur peut facilement déplacer son tête dans un espace vide et perdre le contexte. Votre application peut sembler se bloquer si l’utilisateur ne parvient pas à voir quoi que ce soit. Le billboarding et la balise sont intégrés au Prefab Progress.
* Il est toujours judicieux de fournir des informations d’État sur ce qui se passe à l’utilisateur. le prefab de progression fournit différents styles visuels, y compris le Windows la progression standard du type ring pour fournir l’état. Vous pouvez également utiliser une maille personnalisée avec une animation si vous souhaitez que le style de la progression s’aligne sur la personnalisation de votre application.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>indicateur de progression dans MRTK (Shared Computer Toolkit de la réalité mixte) pour unity

* [MRTK-indicateur de progression prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-service de transition de scène](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a>Voir aussi

* [Curseurs](cursors.md)
* [Rayon émanant de la main](point-and-commit.md)
* [Button](button.md)
* [Objet avec interaction possible](interactable-object.md)
* [Rectangle englobant et barre de l’application](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Menu de la main](hand-menu.md)
* [Menu proche](near-menu.md)
* [Collection d’objets](object-collection.md)
* [Commande vocale](voice-input.md)
* [Clavier](keyboard.md)
* [Info-bulle](tooltip.md)
* [Tablette](slate.md)
* [Curseur](slider.md)
* [Nuanceur](shader.md)
* [Billboarding et tag-along](billboarding-and-tag-along.md)
* [Affichage de la progression](progress.md)
* [Aimantation de surface](surface-magnetism.md)