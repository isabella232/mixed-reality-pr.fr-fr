---
title: Outil de mappage de contrôleur
description: Documentation sur l’outil de mappage de contrôleur dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176168"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="967c0-104">Outil de mappage de contrôleur</span><span class="sxs-lookup"><span data-stu-id="967c0-104">Controller mapping tool</span></span>

<span data-ttu-id="967c0-105">L’outil de mappage de contrôleur est un outil d’exécution (sur un appareil ou dans l’éditeur) qui permet aux développeurs de déterminer rapidement l’axe d’entrée Unity et les mappages de boutons pour un contrôleur matériel (par exemple, le contrôleur de mouvement).</span><span class="sxs-lookup"><span data-stu-id="967c0-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="967c0-106">Cet outil est très utile lors du développement de la prise en charge d’un nouveau contrôleur matériel.</span><span class="sxs-lookup"><span data-stu-id="967c0-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="967c0-107">Elle peut également aider à confirmer un problème de mappage de contrôle soupçonné dans la classe de prise en charge pour un contrôleur existant.</span><span class="sxs-lookup"><span data-stu-id="967c0-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Outil de mappage de contrôleur](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="967c0-109">Utilisation de l’outil de mappage de contrôleur</span><span class="sxs-lookup"><span data-stu-id="967c0-109">Using the controller mapping tool</span></span>

<span data-ttu-id="967c0-110">Pour commencer à utiliser l’outil de mappage de contrôleur, accédez à **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** et ouvrez la scène **ControllerMappingTool** .</span><span class="sxs-lookup"><span data-stu-id="967c0-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="967c0-111">Une fois la scène chargée, le projet peut être exécuté dans l’éditeur, à l’aide du mode lecture ou créé et exécuté sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="967c0-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="967c0-112">Pour examiner les mappages d’Unity pour un contrôleur :</span><span class="sxs-lookup"><span data-stu-id="967c0-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="967c0-113">Connecter le contrôleur</span><span class="sxs-lookup"><span data-stu-id="967c0-113">Connect the controller</span></span>
- <span data-ttu-id="967c0-114">Appuyez sur chaque bouton et déplacez chaque axe</span><span class="sxs-lookup"><span data-stu-id="967c0-114">Press each button and move each axis</span></span>
- <span data-ttu-id="967c0-115">Notez les mappages dans l’affichage</span><span class="sxs-lookup"><span data-stu-id="967c0-115">Note the mappings in the display</span></span>
- <span data-ttu-id="967c0-116">Mettre à jour les mappages de contrôle dans le fournisseur de données du système d’entrée pour le contrôleur</span><span class="sxs-lookup"><span data-stu-id="967c0-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="967c0-117">l’outil de mappage de contrôleur ne fait pas appel aux composants Shared Computer Toolkit de la réalité mixte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="967c0-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="967c0-118">Il communique directement avec Unity pour déterminer et afficher les mappages de contrôle.</span><span class="sxs-lookup"><span data-stu-id="967c0-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="967c0-119">Tous les contrôles sont affichés</span><span class="sxs-lookup"><span data-stu-id="967c0-119">All controls display</span></span>

<span data-ttu-id="967c0-120">Le panneau d’affichage volumineux signale l’état de tous les axes et boutons d’entrée Unity définis (par ex., l’axe 10, le bouton 3).</span><span class="sxs-lookup"><span data-stu-id="967c0-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="967c0-121">Ce panneau fournit une vue complète de l’état du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="967c0-121">This panel provides a complete view of the state of the controller.</span></span>

![Tous les contrôles sont affichés](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="967c0-123">Affichage des contrôles actifs</span><span class="sxs-lookup"><span data-stu-id="967c0-123">Active controls display</span></span>

<span data-ttu-id="967c0-124">Le panneau d’affichage plus petit et étroit affiche les axed d’entrée Unity et les boutons qui sont dans un état actif (par exemple, un bouton est enfoncé).</span><span class="sxs-lookup"><span data-stu-id="967c0-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="967c0-125">L’affichage des contrôles actifs fournit une vue de synthèse facile à lire de l’état du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="967c0-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![Affichage des contrôles actifs](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="967c0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="967c0-127">See also</span></span>

- [<span data-ttu-id="967c0-128">Création d’un fournisseur de données de système d’entrée</span><span class="sxs-lookup"><span data-stu-id="967c0-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="967c0-129">Outil InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="967c0-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
