---
title: Contenu de scène de réalité mixte
description: Documentation sur le composant de contenu de scènes de réalité mixte
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 9980c01b47c3d7d451fda886b4645664f06f204da9967c186382878be947d64f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193224"
---
# <a name="mixed-reality-scene-content"></a>Contenu de scène de réalité mixte

Lors de l’ajout de MRTK à une scène, un `MixedRealitySceneContent` gameobject est créé. Cet objet sert d’emplacement dédié à la mise en place et à l’instanciation du contenu de réalité mixte pour s’assurer qu’il est mis à l’échelle de manière appropriée dans de nombreuses expériences différentes. Le gameobject a un monocomportement **MixedRealitySceneContent** équivalent, qui peut être configuré via le paramètre de **type d’alignement** . Ce paramètre peut prendre les valeurs suivantes.

* *AlignWithExperienceScale* -aligne le contenu en fonction de l' **échelle d’expérience cible** et du **décalage de contenu** définis dans l' [expérience](experience-settings.md) du profil de configuration Paramètres
* *AlignWithHeadHeight* -aligne le contenu à la position y de l’en-tête de l’utilisateur, qui est l’emplacement de l’appareil photo principal.


  ![Objet de contenu de scène de réalité mixte créé dans l’éditeur](../images/experience-settings/MixedRealitySceneContent.png)
