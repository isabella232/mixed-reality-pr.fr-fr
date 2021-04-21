---
title: Configuration de Mixed Reality Feature Tool
description: Découvrez comment télécharger et installer des packages Mixed Reality Unity à partir de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731946"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="59423-104">Configuration de Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="59423-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="59423-105">Quand vous utilisez Mixed Reality Feature Tool, vous avez accès à trois catégories de paramètres différentes, que vous pouvez personnaliser à volonté :</span><span class="sxs-lookup"><span data-stu-id="59423-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="59423-106">Paramètres de téléchargement</span><span class="sxs-lookup"><span data-stu-id="59423-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="59423-107">Paramètres de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="59423-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="59423-108">Paramètres d’importation</span><span class="sxs-lookup"><span data-stu-id="59423-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="59423-109">Paramètres de téléchargement</span><span class="sxs-lookup"><span data-stu-id="59423-109">Download settings</span></span>

![Paramètres de téléchargement](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="59423-111">Remplacer les fichiers de packages existants</span><span class="sxs-lookup"><span data-stu-id="59423-111">Overwrite existing package files</span></span>

<span data-ttu-id="59423-112">L’activation de ce paramètre fait que les fichiers de package sont téléchargés chaque fois qu’ils sont acquis.</span><span class="sxs-lookup"><span data-stu-id="59423-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="59423-113">**Nous vous recommandons de laisser cette option désactivée pour réduire l’utilisation de la bande passante réseau**</span><span class="sxs-lookup"><span data-stu-id="59423-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="59423-114">Par défaut, les fichiers de package précédemment acquis ne sont pas retéléchargés.</span><span class="sxs-lookup"><span data-stu-id="59423-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="59423-115">Package cache</span><span class="sxs-lookup"><span data-stu-id="59423-115">Package cache</span></span>

<span data-ttu-id="59423-116">Changez ce paramètre pour mettre à jour l’emplacement de téléchargement des packages de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="59423-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="59423-117">Ce paramètre est **en lecture seule** dans cette version.</span><span class="sxs-lookup"><span data-stu-id="59423-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="59423-118">Les versions ultérieures peuvent rendre ce paramètre configurable.</span><span class="sxs-lookup"><span data-stu-id="59423-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="59423-119">Paramètres de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="59423-119">Feature settings</span></span>

![Paramètres de fonctionnalité](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="59423-121">Show preview releases</span><span class="sxs-lookup"><span data-stu-id="59423-121">Show preview releases</span></span>

<span data-ttu-id="59423-122">Activez ce paramètre pour acquérir les préversions.</span><span class="sxs-lookup"><span data-stu-id="59423-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="59423-123">Par défaut, les préversions ne sont pas listées dans Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="59423-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="59423-124">Une préversion est indiquée par la mention **« -preview »** dans la version du package.</span><span class="sxs-lookup"><span data-stu-id="59423-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="59423-125">Show early access program features</span><span class="sxs-lookup"><span data-stu-id="59423-125">Show early access program features</span></span>

<span data-ttu-id="59423-126">Activez ce paramètre pour acquérir les fonctionnalités de programmes inscrits accessibles en avant-première.</span><span class="sxs-lookup"><span data-stu-id="59423-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="59423-127">Par défaut, les fonctionnalités accessibles en avant-première ne sont pas listées dans Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="59423-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="59423-128">Si vous activez `Show early access program features` sans `Show preview releases`, les packages accessibles en avant-première peuvent ne pas apparaître dans la découverte.</span><span class="sxs-lookup"><span data-stu-id="59423-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="59423-129">Paramètres d’importation</span><span class="sxs-lookup"><span data-stu-id="59423-129">Import settings</span></span>

![Paramètres d’importation](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="59423-131">Replace existing package files</span><span class="sxs-lookup"><span data-stu-id="59423-131">Replace existing package files</span></span>

<span data-ttu-id="59423-132">Par défaut, Mixed Reality Feature Tool supprime les copies précédentes des packages importés pour réduire la taille du fichier et les traitements inutiles.</span><span class="sxs-lookup"><span data-stu-id="59423-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="59423-133">Décochez ce paramètre pour conserver toutes les versions</span><span class="sxs-lookup"><span data-stu-id="59423-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="59423-134">Project relative import path</span><span class="sxs-lookup"><span data-stu-id="59423-134">Project relative import path</span></span>

<span data-ttu-id="59423-135">Changez ce paramètre pour mettre à jour le chemin du dossier du projet où les packages de fonctionnalités sont copiés lors de l’importation.</span><span class="sxs-lookup"><span data-stu-id="59423-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="59423-136">Par exemple, si le dossier du projet est **C:\GalaxyExplorer**, le chemin d’importation complet est **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="59423-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="59423-137">Ce paramètre est **en lecture seule** dans cette version.</span><span class="sxs-lookup"><span data-stu-id="59423-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="59423-138">Les versions ultérieures peuvent rendre ce paramètre configurable.</span><span class="sxs-lookup"><span data-stu-id="59423-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="59423-139">Paramètres d’accès en avant-première</span><span class="sxs-lookup"><span data-stu-id="59423-139">Early Access settings</span></span>

![Paramètres d’accès en avant-première](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="59423-141">Ask for confirmation before removing an early access program</span><span class="sxs-lookup"><span data-stu-id="59423-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="59423-142">Ce paramètre détermine si une invite doit être affichée chaque fois qu’un programme accessible en avant-première est supprimé.</span><span class="sxs-lookup"><span data-stu-id="59423-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="59423-143">My previews</span><span class="sxs-lookup"><span data-stu-id="59423-143">My previews</span></span>

<span data-ttu-id="59423-144">Liste des programmes inscrits accessibles en avant-première.</span><span class="sxs-lookup"><span data-stu-id="59423-144">The list of registered early access programs.</span></span> <span data-ttu-id="59423-145">Utilisez `Add` , `Edit` et `Remove` pour gérer la collection de programmes inscrits.</span><span class="sxs-lookup"><span data-stu-id="59423-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="59423-146">Paramètres de diagnostic</span><span class="sxs-lookup"><span data-stu-id="59423-146">Diagnostic settings</span></span>

![Paramètres de diagnostic](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="59423-148">Fichier journal</span><span class="sxs-lookup"><span data-stu-id="59423-148">Log file</span></span>

<span data-ttu-id="59423-149">Affiche le chemin au fichier journal de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="59423-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="59423-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59423-150">See also</span></span>

- [<span data-ttu-id="59423-151">Bienvenue dans Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="59423-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)