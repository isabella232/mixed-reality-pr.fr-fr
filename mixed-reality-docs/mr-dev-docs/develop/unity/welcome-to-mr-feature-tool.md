---
title: Bienvenue dans Mixed Reality Feature Tool
description: Découvrez les principes de base de Mixed Reality Feature Tool pour le développement HoloLens et VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772412"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="c02f9-104">Bienvenue dans Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="c02f9-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Image de la bannière de Mixed Reality Feature Tool](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="c02f9-106">Pour le moment, Mixed Reality Feature Tool est disponible seulement pour Unity.</span><span class="sxs-lookup"><span data-stu-id="c02f9-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="c02f9-107">Si vous développez dans Unreal, reportez-vous à la documentation sur l’[installation des outils](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c02f9-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="c02f9-108">Mixed Reality Feature Tool est un nouveau moyen pour les développeurs de découvrir, de mettre à jour et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity.</span><span class="sxs-lookup"><span data-stu-id="c02f9-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="c02f9-109">Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="c02f9-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="c02f9-110">Si vous n’avez peut-être jamais travaillé avec un fichier manifeste auparavant, sachez qu’il s’agit d’un fichier JSON contenant tous vos packages de projet.</span><span class="sxs-lookup"><span data-stu-id="c02f9-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="c02f9-111">Une fois que vous avez validé les packages souhaités, Mixed Reality Feature Tool les télécharge dans le projet de votre choix.</span><span class="sxs-lookup"><span data-stu-id="c02f9-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="c02f9-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c02f9-112">System requirements</span></span>

<span data-ttu-id="c02f9-113">Pour pouvoir exécuter Mixed Reality Feature Tool, voici ce dont vous avez besoin :</span><span class="sxs-lookup"><span data-stu-id="c02f9-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="c02f9-114">Runtime .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c02f9-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="c02f9-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c02f9-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="c02f9-116">Mixed Reality Feature Tool fonctionne actuellement seulement sur Windows, mais la prise en charge de MacOS sera bientôt disponible !</span><span class="sxs-lookup"><span data-stu-id="c02f9-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="c02f9-117">Téléchargement</span><span class="sxs-lookup"><span data-stu-id="c02f9-117">Download</span></span>

<span data-ttu-id="c02f9-118">Une fois que votre environnement est configuré :</span><span class="sxs-lookup"><span data-stu-id="c02f9-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="c02f9-119">[Téléchargez la dernière version de Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c02f9-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="c02f9-120">Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c02f9-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="c02f9-121">Nous vous recommandons de créer un raccourci vers le fichier exécutable pour un accès plus rapide.</span><span class="sxs-lookup"><span data-stu-id="c02f9-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="c02f9-122">Si vous n’avez jamais utilisé le Gestionnaire de package Unity, suivez nos [instructions UPM](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span><span class="sxs-lookup"><span data-stu-id="c02f9-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="c02f9-123">Changements dans cette version</span><span class="sxs-lookup"><span data-stu-id="c02f9-123">Changes in this release</span></span>

<span data-ttu-id="c02f9-124">La version bêta 1.0.2103 comprend les correctifs suivants :</span><span class="sxs-lookup"><span data-stu-id="c02f9-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="c02f9-125">Améliorations de la détection d’erreurs de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="c02f9-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="c02f9-126">Mises à jour sur la façon dont les manifestes sont écrits pour éviter l’échec de la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c02f9-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="c02f9-127">L’échappement a été supprimé des chemins d’accès des fichiers dans le manifeste du projet.</span><span class="sxs-lookup"><span data-stu-id="c02f9-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="c02f9-128">Les fonctionnalités suivantes ont été ajoutées dans cette version :</span><span class="sxs-lookup"><span data-stu-id="c02f9-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="c02f9-129">Le catalogue de fonctionnalités est maintenant mis en cache.</span><span class="sxs-lookup"><span data-stu-id="c02f9-129">The feature catalog is now cached.</span></span> <span data-ttu-id="c02f9-130">Pour rechercher de nouvelles fonctionnalités et mises à jour, utilisez le bouton Actualiser dans Découverte.</span><span class="sxs-lookup"><span data-stu-id="c02f9-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="c02f9-131">Déplacez la sélection de projet de l’étape Importation avant la Découverte.</span><span class="sxs-lookup"><span data-stu-id="c02f9-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="c02f9-132">Les packages disponibles sont filtrés par la version Unity spécifiée du projet.</span><span class="sxs-lookup"><span data-stu-id="c02f9-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="c02f9-133">L’affichage Découverte montre maintenant les packages actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="c02f9-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="c02f9-134">1. Mise en route</span><span class="sxs-lookup"><span data-stu-id="c02f9-134">1. Getting started</span></span>

<span data-ttu-id="c02f9-135">Lancez Mixed Reality Feature Tool à partir du fichier exécutable, qui affiche la page de démarrage lors du premier lancement :</span><span class="sxs-lookup"><span data-stu-id="c02f9-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Mise en route](images/FeatureToolStart.png)

<span data-ttu-id="c02f9-137">Dans la page de démarrage, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="c02f9-137">From the start page, you can:</span></span>

* <span data-ttu-id="c02f9-138">[Configurer](configuring-feature-tool.md) les paramètres de l’outil en utilisant le bouton avec l’**icône d’engrenage**</span><span class="sxs-lookup"><span data-stu-id="c02f9-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="c02f9-139">Utiliser le bouton avec le **point d’interrogation** pour lancer le navigateur web par défaut et afficher notre documentation</span><span class="sxs-lookup"><span data-stu-id="c02f9-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="c02f9-140">Sélectionner **Start** pour commencer la découverte des packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c02f9-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="c02f9-141">2. Sélection de votre projet Unity</span><span class="sxs-lookup"><span data-stu-id="c02f9-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="c02f9-142">Pour vous assurer que toutes les fonctionnalités découvertes sont prises en charge sur la version d’Unity de votre projet, la première étape consiste à faire pointer Mixed Reality Feature Tool sur votre projet à l’aide du bouton représentant des **points de suspension** (à droite du champ de chemin d’accès au projet).</span><span class="sxs-lookup"><span data-stu-id="c02f9-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the right of the project path field).</span></span>

![Sélectionnez le projet Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="c02f9-144">La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="c02f9-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="c02f9-145">Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.</span><span class="sxs-lookup"><span data-stu-id="c02f9-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="c02f9-146">Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="c02f9-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c02f9-147">Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity.</span><span class="sxs-lookup"><span data-stu-id="c02f9-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="c02f9-148">Le dossier doit contenir les dossiers `Assets`, `Packages` et `Project Settings`.</span><span class="sxs-lookup"><span data-stu-id="c02f9-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="c02f9-149">3. Découverte et acquisition de packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c02f9-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="c02f9-150">La version bêta 1.0.2103 met désormais en cache le contenu du catalogue de fonctionnalités à chaque accès au serveur.</span><span class="sxs-lookup"><span data-stu-id="c02f9-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="c02f9-151">Cette modification permet un accès rapide aux fonctionnalités disponibles, au détriment de l’affichage des dernières données absolues.</span><span class="sxs-lookup"><span data-stu-id="c02f9-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="c02f9-152">Pour mettre à jour le catalogue, utilisez le bouton **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="c02f9-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="c02f9-153">Les fonctionnalités sont regroupées par catégorie pour faciliter les recherches.</span><span class="sxs-lookup"><span data-stu-id="c02f9-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="c02f9-154">Par exemple, la catégorie **Mixed Reality Toolkit** vous permet de choisir parmi plusieurs fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="c02f9-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Découverte et acquisition](images/FeatureToolDiscovery.png)

<span data-ttu-id="c02f9-156">Lorsque Mixed Reality Feature Tool reconnaît des fonctionnalités précédemment importées, il affiche un message de notification pour chaque fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="c02f9-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![Notification de fonctionnalité importée](images/feature-tool-imported-note.png)


<span data-ttu-id="c02f9-158">Une fois que vous avez effectué vos choix, sélectionnez **Get features** pour récupérer tous les packages nécessaires auprès du catalogue.</span><span class="sxs-lookup"><span data-stu-id="c02f9-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="c02f9-159">Pour plus d’informations, consultez [Découverte et acquisition des fonctionnalités](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="c02f9-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="c02f9-160">4. Importation de packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c02f9-160">4. Importing feature packages</span></span>

<span data-ttu-id="c02f9-161">Après l’acquisition, l’ensemble complet des packages est présenté ainsi qu’une liste des dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="c02f9-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="c02f9-162">Si vous avez besoin de modifier des sélections de fonctionnalités ou de packages, c’est le moment :</span><span class="sxs-lookup"><span data-stu-id="c02f9-162">If you need to change any feature or package selections, this is the time:</span></span>

![Importation de packages](images/FeatureToolImport.png)

<span data-ttu-id="c02f9-164">Nous vous recommandons vivement d’utiliser le bouton **Validate** pour vérifier que le projet Unity peut importer correctement les fonctionnalités sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="c02f9-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="c02f9-165">Après la validation, vous voyez une boîte de dialogue contextuelle avec un message indiquant la réussite ou bien une liste des problèmes identifiés.</span><span class="sxs-lookup"><span data-stu-id="c02f9-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="c02f9-166">Sélectionnez **Import**  pour continuer.</span><span class="sxs-lookup"><span data-stu-id="c02f9-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="c02f9-167">Une fois que vous avez cliqué sur le bouton **Import**, si des problèmes subsistent, vous voyez un simple message.</span><span class="sxs-lookup"><span data-stu-id="c02f9-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="c02f9-168">La recommandation est de cliquer sur No et d’utiliser le bouton **Validate** pour visualiser et résoudre les problèmes.</span><span class="sxs-lookup"><span data-stu-id="c02f9-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="c02f9-169">Pour plus d’informations, consultez [Importation des fonctionnalités](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="c02f9-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="c02f9-170">5. Examen et approbation des modifications de projet</span><span class="sxs-lookup"><span data-stu-id="c02f9-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="c02f9-171">La dernière étape consiste à examiner et à approuver les modifications proposées dans le manifeste et les fichiers de projet :</span><span class="sxs-lookup"><span data-stu-id="c02f9-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="c02f9-172">Les modifications proposées pour le manifeste s’affichent à gauche.</span><span class="sxs-lookup"><span data-stu-id="c02f9-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="c02f9-173">Les fichiers à ajouter au projet sont listés à droite.</span><span class="sxs-lookup"><span data-stu-id="c02f9-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="c02f9-174">Le bouton **Compare** permet l’affichage côte à côte du manifeste actuel et des modifications proposées.</span><span class="sxs-lookup"><span data-stu-id="c02f9-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Autorisation](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="c02f9-176">Pour plus d’informations, consultez [Examen et approbation des modifications du projet](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="c02f9-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="c02f9-177">6. Projet mis à jour</span><span class="sxs-lookup"><span data-stu-id="c02f9-177">6. Project updated</span></span>

<span data-ttu-id="c02f9-178">Une fois les modifications proposées approuvées, votre projet Unity cible est mis à jour de façon à référencer les fonctionnalités de réalité mixte sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="c02f9-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![Projet mis à jour](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="c02f9-180">Le dossier **Packages** du projet Unity contient maintenant un sous-dossier **MixedReality** avec le ou les fichiers de package de fonctionnalités, et le manifeste contient la ou les références appropriées.</span><span class="sxs-lookup"><span data-stu-id="c02f9-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="c02f9-181">Revenez à Unity, attendez que les nouvelles fonctionnalités sélectionnées se chargent, puis commencez à créer !</span><span class="sxs-lookup"><span data-stu-id="c02f9-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="c02f9-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c02f9-182">See also</span></span>

- [<span data-ttu-id="c02f9-183">Configuration de Feature Tool</span><span class="sxs-lookup"><span data-stu-id="c02f9-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="c02f9-184">Découverte et acquisition</span><span class="sxs-lookup"><span data-stu-id="c02f9-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="c02f9-185">Visualisation des détails des packages de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c02f9-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="c02f9-186">Importation des packages sélectionnés</span><span class="sxs-lookup"><span data-stu-id="c02f9-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="c02f9-187">Examen et approbation des modifications du projet</span><span class="sxs-lookup"><span data-stu-id="c02f9-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)