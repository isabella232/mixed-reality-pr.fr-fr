---
title: Configuration de votre projet Unreal
description: Découvrez comment configurer votre projet avec la dernière version d’Unreal Engine et de Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, réalité mixte, développement, fonctionnalités, nouveau projet, émulateur, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 546dcbac09600402b50408e016507b4d15fac22c58be8c1b3d68331dc5320252
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225403"
---
# <a name="setting-up-your-unreal-project"></a>Configuration de votre projet Unreal

Nous vous recommandons d’installer [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou ultérieure pour tirer pleinement parti de la prise en charge intégrée d’HoloLens.

Accédez à l’onglet **Library** dans Epic Games Launcher, sélectionnez la flèche déroulante à côté de **Launch**, puis cliquez sur **Options**. Sous **Target Platforms**, sélectionnez **HoloLens 2** et cliquez sur **Apply**.
![Option HoloLens 2 dans l’installation d’Unreal](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importer Mixed Reality Toolkit pour Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte. MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales. Le toolkit vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.

Pour l’installation, nous vous recommandons de suivre la [section Bien démarrer](unreal-development-overview.md#1-getting-started) de notre [parcours de développement Unreal](unreal-development-overview.md). Si vous suivez déjà le parcours de développement Unreal, terminez le reste des étapes de configuration ci-dessous et passez aux [tutoriels Bien démarrer avec HoloLens 2](tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Image du logo Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Si vous ne souhaitez pas utiliser le MRTK pour Unreal, vous devrez générer un script pour toutes les interactions et tous les comportements.