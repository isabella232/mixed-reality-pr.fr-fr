---
title: SceneContent
description: Documentation sur le composant de contenu de scènes de réalité mixte
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647856"
---
# <a name="mixed-reality-scene-content"></a>Contenu de scène de réalité mixte

Lors de l’ajout de MRTK à une scène, un `MixedRealitySceneContent` gameobject est créé. Cet objet sert d’emplacement dédié à la mise en place et à l’instanciation du contenu de réalité mixte pour s’assurer qu’il est mis à l’échelle de manière appropriée dans de nombreuses expériences différentes. Le gameobject a un monocomportement **MixedRealitySceneContent** équivalent, qui peut être configuré via le paramètre de **type d’alignement** . Ce paramètre peut prendre les valeurs suivantes.

* *AlignWithExperienceScale* -aligne le contenu en fonction de l' **échelle d’expérience cible** et du **décalage de contenu** définis dans les [paramètres d’expérience](experience-settings.md) du profil de configuration
* *AlignWithHeadHeight* -aligne le contenu à la position y de l’en-tête de l’utilisateur, qui est l’emplacement de l’appareil photo principal.


  ![Objet de contenu de scène de réalité mixte créé dans l’éditeur](../images/experience-settings/MixedRealitySceneContent.png)