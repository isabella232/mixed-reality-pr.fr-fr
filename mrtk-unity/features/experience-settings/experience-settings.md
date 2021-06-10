---
title: ExperienceSettings
description: Documentation sur les différents paramètres d’expérience pour MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647836"
---
# <a name="experience-settings"></a><span data-ttu-id="dd75e-104">Paramètres d’expérience</span><span class="sxs-lookup"><span data-stu-id="dd75e-104">Experience Settings</span></span>

<span data-ttu-id="dd75e-105">L’un des défis liés à la création d’une interface utilisateur pour la réalité mixte est l’alignement sur différentes expériences.</span><span class="sxs-lookup"><span data-stu-id="dd75e-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="dd75e-106">Avec MRTK, vous pouvez définir le `Target Experience Scale` et le `Content Offset` pour votre scène, configurer les éléments suivants pour qu’ils se comportent correctement pour l’échelle cible.</span><span class="sxs-lookup"><span data-stu-id="dd75e-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="dd75e-107">Contenu de scène de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="dd75e-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="dd75e-108">Système de limites</span><span class="sxs-lookup"><span data-stu-id="dd75e-108">Boundary System</span></span>

  ![Paramètres d’expérience dans le profil de configuration MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="dd75e-110">Mise à l’échelle de l’expérience cible</span><span class="sxs-lookup"><span data-stu-id="dd75e-110">Target Experience Scale</span></span>

<span data-ttu-id="dd75e-111">L' **échelle de l’expérience cible** spécifie l’environnement pour lequel l’expérience est conçue.</span><span class="sxs-lookup"><span data-stu-id="dd75e-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="dd75e-112">Elle peut prendre les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="dd75e-112">It can take on the following values.</span></span>

* <span data-ttu-id="dd75e-113">*OrientationOnly* : expérience qui utilise uniquement l’orientation du casque et qui est alignée sur la gravité.</span><span class="sxs-lookup"><span data-stu-id="dd75e-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="dd75e-114">L’origine du système de coordonnées est au niveau de la tête.</span><span class="sxs-lookup"><span data-stu-id="dd75e-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="dd75e-115">*Assis* -expérience conçue pour une utilisation assise.</span><span class="sxs-lookup"><span data-stu-id="dd75e-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="dd75e-116">L’origine du système de coordonnées est au niveau du plancher.</span><span class="sxs-lookup"><span data-stu-id="dd75e-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="dd75e-117">En *position permanente* , une expérience conçue pour une utilisation stationnaire.</span><span class="sxs-lookup"><span data-stu-id="dd75e-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="dd75e-118">L’origine du système de coordonnées est au niveau du plancher.</span><span class="sxs-lookup"><span data-stu-id="dd75e-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="dd75e-119">*Salle* -expérience conçue pour prendre en charge le mouvement dans une salle.</span><span class="sxs-lookup"><span data-stu-id="dd75e-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="dd75e-120">L’origine du système de coordonnées est au niveau du plancher.</span><span class="sxs-lookup"><span data-stu-id="dd75e-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="dd75e-121">Une expérience *mondiale* conçue pour utiliser et se déplacer dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="dd75e-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="dd75e-122">L’origine du système de coordonnées est au niveau de la tête.</span><span class="sxs-lookup"><span data-stu-id="dd75e-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="dd75e-123">Décalage du contenu</span><span class="sxs-lookup"><span data-stu-id="dd75e-123">Content Offset</span></span>

<span data-ttu-id="dd75e-124">Ce paramètre spécifie la hauteur au-dessus du plancher pour décaler le [contenu de scènes de réalité mixte](scene-content.md) quand le **type d’alignement** est défini pour s' **aligner avec l’échelle de l’expérience**</span><span class="sxs-lookup"><span data-stu-id="dd75e-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>