---
title: Bienvenue dans Mixed Reality Feature Tool
description: Découvrez les principes de base de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570252"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="c38d4-104">Bienvenue dans Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="c38d4-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Image de la bannière de Mixed Reality Feature Tool](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="c38d4-106">Pour le moment, Mixed Reality Feature Tool est disponible seulement pour Unity.</span><span class="sxs-lookup"><span data-stu-id="c38d4-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="c38d4-107">Si vous développez dans Unreal, reportez-vous à la documentation sur l’[installation des outils](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c38d4-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="c38d4-108">Mixed Reality Feature Tool est un nouveau moyen pour les développeurs de découvrir, de mettre à jour et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity.</span><span class="sxs-lookup"><span data-stu-id="c38d4-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="c38d4-109">Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="c38d4-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="c38d4-110">Si vous n’avez peut-être jamais travaillé avec un fichier manifeste auparavant, sachez qu’il s’agit d’un fichier JSON contenant tous vos packages de projet.</span><span class="sxs-lookup"><span data-stu-id="c38d4-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="c38d4-111">Une fois que vous avez validé les packages souhaités, Mixed Reality Feature Tool les télécharge dans le projet de votre choix.</span><span class="sxs-lookup"><span data-stu-id="c38d4-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="c38d4-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c38d4-112">System requirements</span></span>

<span data-ttu-id="c38d4-113">Pour pouvoir exécuter Mixed Reality Feature Tool, voici ce dont vous avez besoin :</span><span class="sxs-lookup"><span data-stu-id="c38d4-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="c38d4-114">Runtime .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c38d4-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="c38d4-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c38d4-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="c38d4-116">Mixed Reality Feature Tool fonctionne actuellement seulement sur Windows, mais la prise en charge de MacOS sera bientôt disponible !</span><span class="sxs-lookup"><span data-stu-id="c38d4-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="c38d4-117">Téléchargement</span><span class="sxs-lookup"><span data-stu-id="c38d4-117">Download</span></span> 

<span data-ttu-id="c38d4-118">Une fois que votre environnement est configuré :</span><span class="sxs-lookup"><span data-stu-id="c38d4-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="c38d4-119">[Téléchargez la dernière version de Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c38d4-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="c38d4-120">Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c38d4-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="c38d4-121">Nous vous recommandons de créer un raccourci vers le fichier exécutable pour un accès plus rapide.</span><span class="sxs-lookup"><span data-stu-id="c38d4-121">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="c38d4-122">1. Mise en route</span><span class="sxs-lookup"><span data-stu-id="c38d4-122">1. Getting started</span></span>

<span data-ttu-id="c38d4-123">Lancez Mixed Reality Feature Tool à partir du fichier exécutable, qui affiche la page de démarrage lors du premier lancement :</span><span class="sxs-lookup"><span data-stu-id="c38d4-123">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Mise en route](images/FeatureToolStart.png)

<span data-ttu-id="c38d4-125">Dans la page de démarrage, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="c38d4-125">From the start page, you can:</span></span>

* <span data-ttu-id="c38d4-126">[Configurer](configuring-feature-tool.md) les paramètres de l’outil en utilisant le bouton avec l’**icône d’engrenage**</span><span class="sxs-lookup"><span data-stu-id="c38d4-126">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="c38d4-127">Utiliser le bouton avec le **point d’interrogation** pour lancer le navigateur web par défaut et afficher notre documentation</span><span class="sxs-lookup"><span data-stu-id="c38d4-127">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="c38d4-128">Sélectionner **Start** pour commencer la découverte des packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c38d4-128">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="c38d4-129">2. Découverte et acquisition de packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c38d4-129">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="c38d4-130">Le catalogue des packages de fonctionnalités est récupéré dès que vous appuyez sur Start.</span><span class="sxs-lookup"><span data-stu-id="c38d4-130">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="c38d4-131">Les fonctionnalités sont regroupées par catégorie pour faciliter les recherches.</span><span class="sxs-lookup"><span data-stu-id="c38d4-131">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="c38d4-132">Par exemple, la catégorie **Mixed Reality Toolkit** vous permet de choisir parmi plusieurs fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="c38d4-132">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Découverte et acquisition](images/FeatureToolDiscovery.png)

<span data-ttu-id="c38d4-134">Une fois que vous avez effectué vos choix, sélectionnez **Get features** pour récupérer tous les packages nécessaires auprès du catalogue.</span><span class="sxs-lookup"><span data-stu-id="c38d4-134">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="c38d4-135">Pour plus d’informations, consultez [Découverte et acquisition des fonctionnalités](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="c38d4-135">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="c38d4-136">3. Importation de packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c38d4-136">3. Importing feature packages</span></span>

<span data-ttu-id="c38d4-137">Après l’acquisition, l’ensemble complet des packages est présenté ainsi qu’une liste des dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="c38d4-137">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="c38d4-138">Si vous avez besoin de modifier des sélections de fonctionnalités ou de packages, c’est le moment :</span><span class="sxs-lookup"><span data-stu-id="c38d4-138">If you need to change any feature or package selections, this is the time:</span></span>

![Importation de packages](images/FeatureToolImport.png)

<span data-ttu-id="c38d4-140">Nous vous recommandons vivement d’utiliser le bouton **Validate** pour vérifier que le projet Unity peut importer correctement les fonctionnalités sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="c38d4-140">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="c38d4-141">Après la validation, vous voyez une boîte de dialogue contextuelle avec un message indiquant la réussite ou bien une liste des problèmes identifiés.</span><span class="sxs-lookup"><span data-stu-id="c38d4-141">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="c38d4-142">Vous devez également définir l’emplacement du projet Unity cible avant d’importer.</span><span class="sxs-lookup"><span data-stu-id="c38d4-142">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="c38d4-143">Utilisez le bouton avec les **points de suspension** à gauche du champ du chemin du projet pour le désigner.</span><span class="sxs-lookup"><span data-stu-id="c38d4-143">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="c38d4-144">Quand vous avez fini de naviguer dans votre système de fichiers, ouvrez le dossier contenant votre projet Unity cible.</span><span class="sxs-lookup"><span data-stu-id="c38d4-144">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="c38d4-145">La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="c38d4-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="c38d4-146">Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.</span><span class="sxs-lookup"><span data-stu-id="c38d4-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="c38d4-147">Sélectionnez **Import**  pour continuer.</span><span class="sxs-lookup"><span data-stu-id="c38d4-147">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="c38d4-148">Une fois que vous avez cliqué sur le bouton **Import**, si des problèmes subsistent, vous voyez un simple message.</span><span class="sxs-lookup"><span data-stu-id="c38d4-148">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="c38d4-149">La recommandation est de cliquer sur No et d’utiliser le bouton **Validate** pour visualiser et résoudre les problèmes.</span><span class="sxs-lookup"><span data-stu-id="c38d4-149">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="c38d4-150">Pour plus d’informations, consultez [Importation des fonctionnalités](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="c38d4-150">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="c38d4-151">4. Examen et approbation des modifications du projet</span><span class="sxs-lookup"><span data-stu-id="c38d4-151">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="c38d4-152">La dernière étape consiste à examiner et à approuver les modifications proposées dans le manifeste et les fichiers de projet :</span><span class="sxs-lookup"><span data-stu-id="c38d4-152">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="c38d4-153">Les modifications proposées pour le manifeste s’affichent à gauche.</span><span class="sxs-lookup"><span data-stu-id="c38d4-153">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="c38d4-154">Les fichiers à ajouter au projet sont listés à droite.</span><span class="sxs-lookup"><span data-stu-id="c38d4-154">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="c38d4-155">Le bouton **Compare** permet l’affichage côte à côte du manifeste actuel et des modifications proposées.</span><span class="sxs-lookup"><span data-stu-id="c38d4-155">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Autorisation](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="c38d4-157">Pour plus d’informations, consultez [Examen et approbation des modifications du projet](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="c38d4-157">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="c38d4-158">5. Projet mis à jour</span><span class="sxs-lookup"><span data-stu-id="c38d4-158">5. Project updated</span></span>

<span data-ttu-id="c38d4-159">Quand les modifications proposées sont approuvées, votre projet Unity cible est mis à jour de façon à référencer les fonctionnalités de réalité mixte sélectionnées :</span><span class="sxs-lookup"><span data-stu-id="c38d4-159">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![Projet mis à jour](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="c38d4-161">Le dossier **Packages** du projet Unity contient maintenant un sous-dossier **MixedReality** avec le ou les fichiers de package de fonctionnalités, et le manifeste contient la ou les références appropriées.</span><span class="sxs-lookup"><span data-stu-id="c38d4-161">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="c38d4-162">Revenez à Unity, attendez que les nouvelles fonctionnalités sélectionnées se chargent, puis commencez à créer !</span><span class="sxs-lookup"><span data-stu-id="c38d4-162">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="c38d4-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c38d4-163">See also</span></span>

- [<span data-ttu-id="c38d4-164">Configuration de Feature Tool</span><span class="sxs-lookup"><span data-stu-id="c38d4-164">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="c38d4-165">Découverte et acquisition</span><span class="sxs-lookup"><span data-stu-id="c38d4-165">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="c38d4-166">Visualisation des détails des packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c38d4-166">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="c38d4-167">Importation des packages sélectionnés</span><span class="sxs-lookup"><span data-stu-id="c38d4-167">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="c38d4-168">Examen et approbation des modifications du projet</span><span class="sxs-lookup"><span data-stu-id="c38d4-168">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
