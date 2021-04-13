---
title: Tutoriels de démarrage - 3. Configuration des profils MRTK
description: Ce cours vous montre comment configurer les profils Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, reconnaissance spatiale
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300454"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="11791-105">3. Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="11791-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="11791-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="11791-106">Overview</span></span>

<span data-ttu-id="11791-107">Dans ce tutoriel, vous allez voir comment personnaliser et configurer les profils MRTK.</span><span class="sxs-lookup"><span data-stu-id="11791-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="11791-108">Les <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">profils MRTK</a> sont une arborescence de profils imbriqués qui constituent les informations de configuration déterminant comment les systèmes et les fonctionnalités de MRTK doivent être initialisés.</span><span class="sxs-lookup"><span data-stu-id="11791-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="11791-109">Le profil de plus haut niveau, le profil de configuration, contient des profils imbriqués pour chacun des systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="11791-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="11791-110">Chaque profil imbriqué est conçu pour configurer le comportement de son système correspondant.</span><span class="sxs-lookup"><span data-stu-id="11791-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="11791-111">Cet exemple va vous montrer comment masquer le maillage de la reconnaissance spatiale en modifiant les paramètres de l’observateur de maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="11791-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="11791-112">Vous pouvez cependant suivre ces mêmes principes pour personnaliser des paramètres ou des valeurs dans les profils MRTK.</span><span class="sxs-lookup"><span data-stu-id="11791-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="11791-113">Comme vous en avez fait l’expérience quand vous avez déployé votre projet sur votre HoloLens 2 dans le [tutoriel précédent](mr-learning-base-02.md#congratulations), le maillage de <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">reconnaissance spatiale</a> est un ensemble de mailles représentant la géométrie de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="11791-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="11791-114">C’est une visualisation utile à voir initialement, mais elle est généralement désactivée pour éviter de distraire visuellement l’utilisateur et d’impacter les performances en raison des ressources nécessaires à son affichage.</span><span class="sxs-lookup"><span data-stu-id="11791-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="11791-115">Objectifs</span><span class="sxs-lookup"><span data-stu-id="11791-115">Objectives</span></span>

* <span data-ttu-id="11791-116">Apprendre à personnaliser et à configurer des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="11791-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="11791-117">Apprendre à masquer le maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="11791-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="11791-118">Changement de l’option d’affichage de la reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="11791-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="11791-119">Les principales étapes à suivre pour masquer le maillage de la reconnaissance spatiale sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="11791-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="11791-120">Cloner le profil de configuration par défaut</span><span class="sxs-lookup"><span data-stu-id="11791-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="11791-121">Activer le système de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="11791-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="11791-122">Cloner le profil système de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="11791-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="11791-123">Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut</span><span class="sxs-lookup"><span data-stu-id="11791-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="11791-124">Changer la visibilité du maillage de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="11791-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="11791-125">Par défaut, les profils MRTK ne sont pas modifiables.</span><span class="sxs-lookup"><span data-stu-id="11791-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="11791-126">Il s’agit des modèles de profil par défaut que vous devez cloner avant de pouvoir les modifier.</span><span class="sxs-lookup"><span data-stu-id="11791-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="11791-127">Il existe plusieurs couches de profils imbriquées.</span><span class="sxs-lookup"><span data-stu-id="11791-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="11791-128">Par conséquent, il est courant de cloner et de modifier plusieurs profils lors de la configuration d’un ou plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="11791-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="11791-129">Félicitations</span><span class="sxs-lookup"><span data-stu-id="11791-129">Congratulations</span></span>

<span data-ttu-id="11791-130">Dans ce tutoriel, vous avez vu comment cloner, personnaliser et configurer les profils et les paramètres MRTK.</span><span class="sxs-lookup"><span data-stu-id="11791-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="11791-131">Tutoriel suivant : 4. Positionnement des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="11791-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)