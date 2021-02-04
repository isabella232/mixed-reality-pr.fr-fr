---
title: Importation des fonctionnalités
description: Découvrez comment importer et installer des fonctionnalités à partir de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243914"
---
# <a name="importing-features"></a><span data-ttu-id="94bcc-104">Importation des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="94bcc-104">Importing features</span></span>

<span data-ttu-id="94bcc-105">Une fois que vos fonctionnalités ont été téléchargées, elles peuvent être passées en revue et importées dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="94bcc-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="94bcc-106">À cette étape, la fenêtre de votre application doit ressembler à l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="94bcc-106">At this step, your application window should look like the following image:</span></span>

![Importation des fonctionnalités](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="94bcc-108">Features list</span><span class="sxs-lookup"><span data-stu-id="94bcc-108">Features list</span></span>

<span data-ttu-id="94bcc-109">La liste **Features** contient la collection de packages sélectionnés lors de la découverte.</span><span class="sxs-lookup"><span data-stu-id="94bcc-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="94bcc-110">Chaque fonctionnalité peut être sélectionnée ou désélectionnée avant d’être importée.</span><span class="sxs-lookup"><span data-stu-id="94bcc-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="94bcc-111">Vous pouvez consulter les détails des packages en utilisant le lien **Details** montré ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="94bcc-111">Package details can be viewed using the **Details** link shown below</span></span>

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="94bcc-113">Liste des dépendances requises</span><span class="sxs-lookup"><span data-stu-id="94bcc-113">Required dependencies list</span></span>

<span data-ttu-id="94bcc-114">La liste **Required dependencies** contient les packages requis par une ou plusieurs des fonctionnalités sélectionnées pour fonctionner.</span><span class="sxs-lookup"><span data-stu-id="94bcc-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="94bcc-115">Cette liste contient également les dépendances des dépendances.</span><span class="sxs-lookup"><span data-stu-id="94bcc-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="94bcc-116">Chaque dépendance peut être sélectionnée ou désélectionnée avant d’être importée.</span><span class="sxs-lookup"><span data-stu-id="94bcc-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="94bcc-117">Vous pouvez consulter les détails des packages en utilisant le lien **Details** montré ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="94bcc-117">Package details can be viewed using the **Details** link shown below</span></span>

![Liste des dépendances](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="94bcc-119">La désélection des dépendances requises entraîne une ou plusieurs erreurs de dépendances manquantes lors du chargement du projet dans Unity.</span><span class="sxs-lookup"><span data-stu-id="94bcc-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="94bcc-120">Ces fonctionnalités ne seront pas utilisables dans le projet.</span><span class="sxs-lookup"><span data-stu-id="94bcc-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="94bcc-121">Spécification du chemin du projet Unity</span><span class="sxs-lookup"><span data-stu-id="94bcc-121">Specifying the Unity project path</span></span>

<span data-ttu-id="94bcc-122">Avant de pouvoir importer des fonctionnalités dans le projet, vous devez inscrire le chemin auprès de Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="94bcc-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![Définition du chemin du projet](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="94bcc-124">Validation des sélections</span><span class="sxs-lookup"><span data-stu-id="94bcc-124">Validating selections</span></span>

<span data-ttu-id="94bcc-125">Nous vous recommandons fortement de valider les sélections de fonctionnalités avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="94bcc-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="94bcc-126">Cette étape va détecter tous les problèmes susceptibles d’empêcher la réussite du développement des projets.</span><span class="sxs-lookup"><span data-stu-id="94bcc-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![Problèmes de validation](images/ValidationIssues.png)

<span data-ttu-id="94bcc-128">Mixed Reality Feature Tool fournit deux résolutions de problème automatiques (décrites dans les sections suivantes), et la possibilité d’annuler et de résoudre les problèmes manuellement.</span><span class="sxs-lookup"><span data-stu-id="94bcc-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94bcc-129">Mixed Reality Feature Tool ne peut pas résoudre automatiquement les problèmes liés aux versions requises d’Unity.</span><span class="sxs-lookup"><span data-stu-id="94bcc-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="94bcc-130">Ces problèmes doivent être traités manuellement en mettant à niveau la version de Unity utilisée par le projet, ou en désactivant la ou les fonctionnalités nécessitant une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="94bcc-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="94bcc-131">Une version ultérieure de Mixed Reality Feature Tool fournira un meilleur filtrage des fonctionnalités en fonction de la version d’Unity utilisée par le projet.</span><span class="sxs-lookup"><span data-stu-id="94bcc-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="94bcc-132">Activer les dépendances</span><span class="sxs-lookup"><span data-stu-id="94bcc-132">Enable dependencies</span></span>

<span data-ttu-id="94bcc-133">Le bouton **Enable dependencies** va resélectionner automatiquement les dépendances manquantes.</span><span class="sxs-lookup"><span data-stu-id="94bcc-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="94bcc-134">C’est vrai pour les dépendances qui ont été explicitement sélectionnées (qui apparaissent dans la liste **Features**) et pour celles qui ont été sélectionnées implicitement en fonction des exigences des fonctionnalités sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="94bcc-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="94bcc-135">Désactiver des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="94bcc-135">Disable features</span></span>

<span data-ttu-id="94bcc-136">Le fait de sélectionner **Disable features** désélectionne automatiquement les fonctionnalités qui dépendent d’une ou de plusieurs des dépendances qui ont été désactivées.</span><span class="sxs-lookup"><span data-stu-id="94bcc-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="94bcc-137">C’est vrai pour les packages de dépendances implicitement sélectionnés et pour les fonctionnalités explicitement sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="94bcc-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="94bcc-138">Importation en cours</span><span class="sxs-lookup"><span data-stu-id="94bcc-138">Importing</span></span>

<span data-ttu-id="94bcc-139">Sélectionnez **Import** pour ajouter vos fonctionnalités sélectionnées et pour donner une [approbation finale](reviewing-changes.md) avant de mettre à jour votre projet cible.</span><span class="sxs-lookup"><span data-stu-id="94bcc-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94bcc-140">Si un problème de validation persiste lors de l’importation, un message d’avertissement s’affiche.</span><span class="sxs-lookup"><span data-stu-id="94bcc-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="94bcc-141">Il est recommandé de sélectionner No, de cliquer sur **Validate** et de résoudre les problèmes présentés.</span><span class="sxs-lookup"><span data-stu-id="94bcc-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Continuer avec les problèmes de validation](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="94bcc-143">Revenir à l’étape précédente</span><span class="sxs-lookup"><span data-stu-id="94bcc-143">Going back to the previous step</span></span>

<span data-ttu-id="94bcc-144">Dans **Import features**, Mixed Reality Feature Tool permet de revenir en arrière jusqu’au la [découverte](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="94bcc-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="94bcc-145">Sélectionnez **Go back** pour télécharger d’autres packages de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="94bcc-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="94bcc-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94bcc-146">See also</span></span>

- [<span data-ttu-id="94bcc-147">Bienvenue dans Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="94bcc-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="94bcc-148">Découverte et acquisition</span><span class="sxs-lookup"><span data-stu-id="94bcc-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="94bcc-149">Visualisation des détails des packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="94bcc-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="94bcc-150">Examen et approbation des modifications du projet</span><span class="sxs-lookup"><span data-stu-id="94bcc-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)