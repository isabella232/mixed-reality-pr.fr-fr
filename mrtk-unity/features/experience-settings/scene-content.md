---
title: Contenu de scène de réalité mixte
description: Documentation sur le composant de contenu de scènes de réalité mixte
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177341"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="db787-104">Contenu de scène de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="db787-104">Mixed Reality scene content</span></span>

<span data-ttu-id="db787-105">Lors de l’ajout de MRTK à une scène, un `MixedRealitySceneContent` gameobject est créé.</span><span class="sxs-lookup"><span data-stu-id="db787-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="db787-106">Cet objet sert d’emplacement dédié à la mise en place et à l’instanciation du contenu de réalité mixte pour s’assurer qu’il est mis à l’échelle de manière appropriée dans de nombreuses expériences différentes.</span><span class="sxs-lookup"><span data-stu-id="db787-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="db787-107">Le gameobject a un monocomportement **MixedRealitySceneContent** équivalent, qui peut être configuré via le paramètre de **type d’alignement** .</span><span class="sxs-lookup"><span data-stu-id="db787-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="db787-108">Ce paramètre peut prendre les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="db787-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="db787-109">*AlignWithExperienceScale* -aligne le contenu en fonction de l' **échelle d’expérience cible** et du **décalage de contenu** définis dans l' [expérience](experience-settings.md) du profil de configuration Paramètres</span><span class="sxs-lookup"><span data-stu-id="db787-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="db787-110">*AlignWithHeadHeight* -aligne le contenu à la position y de l’en-tête de l’utilisateur, qui est l’emplacement de l’appareil photo principal.</span><span class="sxs-lookup"><span data-stu-id="db787-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![Objet de contenu de scène de réalité mixte créé dans l’éditeur](../images/experience-settings/MixedRealitySceneContent.png)
