---
title: Autoriser les modifications d’un projet
description: Découvrez comment autoriser les modifications d’un projet par Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230763"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="927ed-104">Autoriser les modifications d’un projet</span><span class="sxs-lookup"><span data-stu-id="927ed-104">Authorizing project changes</span></span>

<span data-ttu-id="927ed-105">Avant de modifier le projet Unity, les modifications apportées aux fichiers manifeste et projet doivent être examinées et approuvées :</span><span class="sxs-lookup"><span data-stu-id="927ed-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![Demande d’autorisation](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="927ed-107">Manifeste</span><span class="sxs-lookup"><span data-stu-id="927ed-107">Manifest</span></span>

<span data-ttu-id="927ed-108">Les modifications proposées pour le manifeste peuvent être visualisées dans la colonne **Manifest** à gauche.</span><span class="sxs-lookup"><span data-stu-id="927ed-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="927ed-109">Le contenu est exactement ce qui sera écrit dans le manifeste du projet (**Packages/manifest.json**) :</span><span class="sxs-lookup"><span data-stu-id="927ed-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![Aperçu du manifeste](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="927ed-111">Fichiers à copier dans le projet</span><span class="sxs-lookup"><span data-stu-id="927ed-111">Files to be copied into the project</span></span>

<span data-ttu-id="927ed-112">La section **Files to be copied into the project** à droite liste les fichiers de package de fonctionnalités spécifiques qui seront copiés dans le projet Unity :</span><span class="sxs-lookup"><span data-stu-id="927ed-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![Aperçu du manifeste avec les fichiers à copier](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="927ed-114">Comparer les manifestes</span><span class="sxs-lookup"><span data-stu-id="927ed-114">Compare manifests</span></span>

<span data-ttu-id="927ed-115">Vous pouvez voir une comparaison côte à côte détaillée de toutes les modifications proposées en sélectionnant **Compare** :</span><span class="sxs-lookup"><span data-stu-id="927ed-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![Comparer les manifestes](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="927ed-117">Approbation des modifications</span><span class="sxs-lookup"><span data-stu-id="927ed-117">Approving changes</span></span>

<span data-ttu-id="927ed-118">Quand les modifications proposées sont approuvées, les fichiers listés sont copiés dans le projet Unity et le manifeste est mis à jour avec des références à ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="927ed-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="927ed-119">Les fichiers de package de fonctionnalités (\*.tgz) doivent être ajoutés au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="927ed-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="927ed-120">Ils sont référencés en utilisant un chemin relatif pour permettre aux équipes de développement de partager facilement les fonctionnalités et les modifications du manifeste.</span><span class="sxs-lookup"><span data-stu-id="927ed-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="927ed-121">Dans le cadre des modifications, le fichier **manifest.json** actuel est sauvegardé.</span><span class="sxs-lookup"><span data-stu-id="927ed-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="927ed-122">Quand vous visualisez les sauvegardes de manifeste, le plus ancien est appelé **manifest.json.backup**.</span><span class="sxs-lookup"><span data-stu-id="927ed-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="927ed-123">Les sauvegardes plus récentes sont annotées avec une valeur numérique, en commençant par zéro (0).</span><span class="sxs-lookup"><span data-stu-id="927ed-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="927ed-124">Revenir à l’étape précédente</span><span class="sxs-lookup"><span data-stu-id="927ed-124">Going back to the previous step</span></span>

<span data-ttu-id="927ed-125">Si vous devez apporter des modifications à vos sélections de fonctionnalités, utilisez **Go Back** pour revenir à l’étape [Importer](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="927ed-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="927ed-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="927ed-126">See also</span></span>

- [<span data-ttu-id="927ed-127">Bienvenue dans Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="927ed-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="927ed-128">Importation des packages sélectionnés</span><span class="sxs-lookup"><span data-stu-id="927ed-128">Importing selected packages</span></span>](importing-features.md)
