---
title: Outil d’utilisation des fonctionnalités d’entrée
description: Documentation InputFeatureUsage Tool dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176126"
---
# <a name="input-feature-usage-tool"></a><span data-ttu-id="07453-104">Outil d’utilisation des fonctionnalités d’entrée</span><span class="sxs-lookup"><span data-stu-id="07453-104">Input feature usage tool</span></span>

<span data-ttu-id="07453-105">L’outil InputFeatureUsage est un outil d’exécution (sur un appareil ou dans l’éditeur) qui permet aux développeurs de déterminer rapidement le InputFeatureUsages Unity disponible pour une source d’entrée détectée (par exemple, un contrôleur de mouvement ou une main articulée).</span><span class="sxs-lookup"><span data-stu-id="07453-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="07453-106">Cette scène fonctionne uniquement sur Unity 2019,3 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="07453-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="07453-107">Cet outil est très utile lors du développement de la prise en charge d’un nouveau contrôleur matériel.</span><span class="sxs-lookup"><span data-stu-id="07453-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="07453-108">Elle peut également aider à confirmer un problème de mappage de contrôle soupçonné dans la classe de prise en charge pour un contrôleur existant.</span><span class="sxs-lookup"><span data-stu-id="07453-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Outil InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="07453-110">Utilisation de l’outil InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="07453-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="07453-111">Pour commencer à utiliser l’outil InputFeatureUsage, accédez à **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** et ouvrez la scène **InputFeatureUsageTool** .</span><span class="sxs-lookup"><span data-stu-id="07453-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="07453-112">Une fois la scène chargée, le projet peut être exécuté dans l’éditeur, à l’aide du mode lecture ou créé et exécuté sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="07453-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="07453-113">Pour examiner les mappages d’Unity pour un contrôleur :</span><span class="sxs-lookup"><span data-stu-id="07453-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="07453-114">Connecter le contrôleur</span><span class="sxs-lookup"><span data-stu-id="07453-114">Connect the controller</span></span>
- <span data-ttu-id="07453-115">Appuyez sur chaque bouton et déplacez chaque axe</span><span class="sxs-lookup"><span data-stu-id="07453-115">Press each button and move each axis</span></span>
- <span data-ttu-id="07453-116">Notez les utilisations des fonctionnalités dans l’affichage</span><span class="sxs-lookup"><span data-stu-id="07453-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="07453-117">Mettre à jour les mappages de contrôle dans le fournisseur de données du système d’entrée pour le contrôleur</span><span class="sxs-lookup"><span data-stu-id="07453-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="07453-118">l’outil InputFeatureUsage ne fait pas appel aux composants Shared Computer Toolkit de la réalité mixte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="07453-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="07453-119">Il communique directement avec Unity pour déterminer et afficher les utilisations des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="07453-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="07453-120">Panneaux</span><span class="sxs-lookup"><span data-stu-id="07453-120">Panels</span></span>

<span data-ttu-id="07453-121">Les panneaux affichent l’état actuel de tous les InputFeatureUsages signalés sur toutes les sources d’entrée Unity détectées.</span><span class="sxs-lookup"><span data-stu-id="07453-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="07453-122">Le plus petit volet situé dans la partie supérieure répertorie les noms de toutes les sources détectées.</span><span class="sxs-lookup"><span data-stu-id="07453-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="07453-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07453-123">See also</span></span>

- [<span data-ttu-id="07453-124">Création d’un fournisseur de données de système d’entrée</span><span class="sxs-lookup"><span data-stu-id="07453-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="07453-125">Outil de mappage de contrôleur</span><span class="sxs-lookup"><span data-stu-id="07453-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
