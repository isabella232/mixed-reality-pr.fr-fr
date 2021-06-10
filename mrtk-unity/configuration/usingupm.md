---
title: Utilisation du gestionnaire de package Unity
description: Utilisation de MRTK dans le gestionnaire de package Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, packages MRTK,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345072"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a><span data-ttu-id="2a49d-104">Trousse à outils de réalité mixte et gestionnaire de packages Unity</span><span class="sxs-lookup"><span data-stu-id="2a49d-104">Mixed Reality Toolkit and Unity Package Manager</span></span>

<span data-ttu-id="2a49d-105">À partir de la version 2.5.0, à l’aide de l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), Microsoft Mixed Reality Toolkit est intégré au gestionnaire de package Unity (UPM) lors de l’utilisation d’unity 2019,4 et de versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2a49d-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="2a49d-106">Utilisation de Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="2a49d-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="2a49d-107">Comme décrit dans [Bienvenue dans l’outil de fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) , vous pouvez télécharger l’outil à l’aide de [ce lien](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="2a49d-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a49d-108">Si le manifeste du projet a une `Microsoft Mixed Reality` entrée dans la `scopedRegistries` section, il est recommandé de le supprimer.</span><span class="sxs-lookup"><span data-stu-id="2a49d-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="2a49d-109">Pour supprimer un registre avec étendue configuré, accédez à `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="2a49d-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Suppression du Registre étendu](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="2a49d-111">Les packages MRTK s’affichent sous l' `Mixed Reality Toolkit` en-tête lors de la découverte des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="2a49d-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Découvrir les fonctionnalités](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="2a49d-113">Lorsque vous sélectionnez des fonctionnalités, vous n’avez pas besoin de vous préoccuper des dépendances requises, l’outil les télécharge et les intègre automatiquement dans le projet.</span><span class="sxs-lookup"><span data-stu-id="2a49d-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Dépendances requises](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="2a49d-115">Gestion des fonctionnalités de réalité mixte avec le gestionnaire de package Unity</span><span class="sxs-lookup"><span data-stu-id="2a49d-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="2a49d-116">Une fois qu’un package de boîte à outils de réalité mixte a été ajouté au manifeste du package, il peut être géré à l’aide de l’interface utilisateur du gestionnaire de package Unity.</span><span class="sxs-lookup"><span data-stu-id="2a49d-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Package UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="2a49d-118">Si un package de boîte à outils de réalité mixte est supprimé à l’aide du gestionnaire de package Unity, il devra être rajouté à l’aide des [étapes décrites précédemment](#using-the-mixed-reality-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="2a49d-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="2a49d-119">Utilisation d’exemples d’outils de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2a49d-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="2a49d-120">Contrairement à l’utilisation de fichiers de package de ressources (. pour Unity), `com.microsoft.mixedreality.toolkit.examples` et `com.microsoft.mixedreality.toolkit.handphysicsservice` n’importent pas automatiquement les exemples de scènes et les éléments multimédias.</span><span class="sxs-lookup"><span data-stu-id="2a49d-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="2a49d-121">Pour utiliser un ou plusieurs des exemples, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2a49d-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="2a49d-122">Dans l’éditeur Unity, accédez à `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="2a49d-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="2a49d-123">Dans la liste des packages, sélectionnez `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="2a49d-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="2a49d-124">Rechercher les exemples souhaités dans la `Samples` liste</span><span class="sxs-lookup"><span data-stu-id="2a49d-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="2a49d-125">Cliquez sur `Import into Project`</span><span class="sxs-lookup"><span data-stu-id="2a49d-125">Click `Import into Project`</span></span>

![Importation d’exemples](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="2a49d-127">Lorsqu’un exemple de package est mis à jour, Unity offre la possibilité de mettre à jour les exemples importés.</span><span class="sxs-lookup"><span data-stu-id="2a49d-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="2a49d-128">La mise à jour d’un exemple importé remplace toutes les modifications apportées à cet exemple et les ressources associées.</span><span class="sxs-lookup"><span data-stu-id="2a49d-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a49d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a49d-129">See Also</span></span>

- [<span data-ttu-id="2a49d-130">Packages Toolkit de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2a49d-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)