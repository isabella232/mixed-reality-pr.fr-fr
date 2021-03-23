---
title: Configuration de Mixed Reality Feature Tool
description: Découvrez comment télécharger et installer des packages Mixed Reality Unity à partir de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99243930"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="93e49-104">Configuration de Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="93e49-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="93e49-105">Quand vous utilisez Mixed Reality Feature Tool, vous avez accès à trois catégories de paramètres différentes, que vous pouvez personnaliser à volonté :</span><span class="sxs-lookup"><span data-stu-id="93e49-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="93e49-106">Paramètres de téléchargement</span><span class="sxs-lookup"><span data-stu-id="93e49-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="93e49-107">Paramètres de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="93e49-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="93e49-108">Paramètres d’importation</span><span class="sxs-lookup"><span data-stu-id="93e49-108">Import settings</span></span>](#import-settings)

![Paramètres](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="93e49-110">Paramètres de téléchargement</span><span class="sxs-lookup"><span data-stu-id="93e49-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="93e49-111">Remplacer les fichiers de packages existants</span><span class="sxs-lookup"><span data-stu-id="93e49-111">Overwrite existing package files</span></span>

<span data-ttu-id="93e49-112">L’activation de ce paramètre fait que les fichiers de package sont téléchargés chaque fois qu’ils sont acquis.</span><span class="sxs-lookup"><span data-stu-id="93e49-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="93e49-113">**Nous vous recommandons de laisser cette option désactivée pour réduire l’utilisation de la bande passante réseau**</span><span class="sxs-lookup"><span data-stu-id="93e49-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="93e49-114">Par défaut, les fichiers de package précédemment acquis ne sont pas retéléchargés.</span><span class="sxs-lookup"><span data-stu-id="93e49-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="93e49-115">Package cache</span><span class="sxs-lookup"><span data-stu-id="93e49-115">Package cache</span></span>

<span data-ttu-id="93e49-116">Changez ce paramètre pour mettre à jour l’emplacement de téléchargement des packages de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="93e49-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="93e49-117">Ce paramètre est **en lecture seule** dans cette version.</span><span class="sxs-lookup"><span data-stu-id="93e49-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="93e49-118">Les versions ultérieures peuvent rendre ce paramètre configurable.</span><span class="sxs-lookup"><span data-stu-id="93e49-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="93e49-119">Paramètres de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="93e49-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="93e49-120">Include preview releases</span><span class="sxs-lookup"><span data-stu-id="93e49-120">Include preview releases</span></span>

<span data-ttu-id="93e49-121">Activez ce paramètre pour acquérir les préversions.</span><span class="sxs-lookup"><span data-stu-id="93e49-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="93e49-122">Par défaut, les préversions ne sont pas montrées dans Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="93e49-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="93e49-123">Une préversion est indiquée par la mention **« -preview »** dans la version du package.</span><span class="sxs-lookup"><span data-stu-id="93e49-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="93e49-124">Paramètres d’importation</span><span class="sxs-lookup"><span data-stu-id="93e49-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="93e49-125">Replace existing package files</span><span class="sxs-lookup"><span data-stu-id="93e49-125">Replace existing package files</span></span>

<span data-ttu-id="93e49-126">Par défaut, Mixed Reality Feature Tool supprime les copies précédentes des packages importés pour réduire la taille du fichier et les traitements inutiles.</span><span class="sxs-lookup"><span data-stu-id="93e49-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="93e49-127">Décochez ce paramètre pour conserver toutes les versions</span><span class="sxs-lookup"><span data-stu-id="93e49-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="93e49-128">Project relative import path</span><span class="sxs-lookup"><span data-stu-id="93e49-128">Project relative import path</span></span>

<span data-ttu-id="93e49-129">Changez ce paramètre pour mettre à jour le chemin du dossier du projet où les packages de fonctionnalités sont copiés lors de l’importation.</span><span class="sxs-lookup"><span data-stu-id="93e49-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="93e49-130">Par exemple, si le dossier du projet est **C:\GalaxyExplorer**, le chemin d’importation complet est **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="93e49-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="93e49-131">Ce paramètre est **en lecture seule** dans cette version.</span><span class="sxs-lookup"><span data-stu-id="93e49-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="93e49-132">Les versions ultérieures peuvent rendre ce paramètre configurable.</span><span class="sxs-lookup"><span data-stu-id="93e49-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="93e49-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93e49-133">See also</span></span>

- [<span data-ttu-id="93e49-134">Bienvenue dans Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="93e49-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)