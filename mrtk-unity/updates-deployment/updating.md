---
title: Mise à jour
description: Documentation à migrer à partir d’une version antérieure de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742235"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="52fc7-104">Mise à jour de Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="52fc7-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="52fc7-105">Mise à niveau vers une nouvelle version de MRTK</span><span class="sxs-lookup"><span data-stu-id="52fc7-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="52fc7-106">2.3.0 à 2.4.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="52fc7-107">2.2.0 à 2.3.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="52fc7-108">2.1.0 à 2.2.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="52fc7-109">2.0.0 à 2.1.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="52fc7-110">RC2 à 2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="52fc7-111">Recherche de la version actuelle</span><span class="sxs-lookup"><span data-stu-id="52fc7-111">Finding the current version</span></span> 

<span data-ttu-id="52fc7-112">Suivez ces instructions pour déterminer quelle version du MRTK vous utilisez actuellement :</span><span class="sxs-lookup"><span data-stu-id="52fc7-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="52fc7-113">Ouvrez votre projet MRTK dans Unity</span><span class="sxs-lookup"><span data-stu-id="52fc7-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="52fc7-114">Accédez au dossier « MixedRealityToolkit » dans la fenêtre de votre projet</span><span class="sxs-lookup"><span data-stu-id="52fc7-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="52fc7-115">Ouvrez le fichier appelé « version ».</span><span class="sxs-lookup"><span data-stu-id="52fc7-115">Open the file called "Version"</span></span>

<span data-ttu-id="52fc7-116">Si le fichier et le dossier ci-dessus n’existent pas, c’est que vous utilisez une version plus récente de MRTK.</span><span class="sxs-lookup"><span data-stu-id="52fc7-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="52fc7-117">Dans ce cas, essayez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="52fc7-117">In that case, try the following:</span></span>

1. <span data-ttu-id="52fc7-118">Accédez au dossier « Mixed Reality Toolkit Foundation »</span><span class="sxs-lookup"><span data-stu-id="52fc7-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="52fc7-119">Cliquez sur l' package.jspour afficher un aperçu dans Unity ou l’ouvrir avec un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="52fc7-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="52fc7-120">Recherchez la ligne avec le mot « version : »</span><span class="sxs-lookup"><span data-stu-id="52fc7-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="52fc7-121">Mise à niveau vers une nouvelle version de MRTK</span><span class="sxs-lookup"><span data-stu-id="52fc7-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="52fc7-122">*Il est vivement recommandé d’exécuter l' [outil de migration](../features/tools/migration-window.md) après avoir mis à jour la mise à jour MRTK pour qu’il soit* mis à niveau et mis à niveau à partir de composants déconseillés et ajusté en modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="52fc7-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="52fc7-123">L’outil de migration fait partie du package d' **Outils** .</span><span class="sxs-lookup"><span data-stu-id="52fc7-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="52fc7-124">Les instructions ci-dessous décrivent le chemin de mise à niveau de 2.4.0 vers 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="52fc7-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="52fc7-125">Si votre projet se trouve sur 2.3.0 ou une version antérieure, prenez connaissance des modifications apportées [entre les versions](#updating-230-to-240) pour comprendre le chemin de mise à niveau, ou lisez les [instructions de la version](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) précédente pour effectuer une mise à niveau de version par version.</span><span class="sxs-lookup"><span data-stu-id="52fc7-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="52fc7-126">Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="52fc7-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="52fc7-127">Le moyen le plus simple de mettre à niveau MRTK vers une version plus récente MRTK consiste à utiliser l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) pour télécharger les packages les plus récents et les charger directement dans votre projet Unity.</span><span class="sxs-lookup"><span data-stu-id="52fc7-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="52fc7-128">Si le projet utilisait précédemment des fichiers de ressources Unity (. pour Unity), veuillez consulter [ces instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="52fc7-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="52fc7-129">Fichiers de ressources Unity (. pour Unity)</span><span class="sxs-lookup"><span data-stu-id="52fc7-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="52fc7-130">Un autre chemin de mise à niveau consiste à télécharger manuellement les packages MRTK Unity et à les appliquer à votre projet.</span><span class="sxs-lookup"><span data-stu-id="52fc7-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="52fc7-131">Consultez les étapes ci-dessous,</span><span class="sxs-lookup"><span data-stu-id="52fc7-131">See the steps below,</span></span>

1. <span data-ttu-id="52fc7-132">Enregistrez une copie de votre projet actuel, au cas où vous atteigniez des vigilant à tout moment dans les étapes de mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="52fc7-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="52fc7-133">Fermer Unity</span><span class="sxs-lookup"><span data-stu-id="52fc7-133">Close Unity</span></span>
1. <span data-ttu-id="52fc7-134">Dans le dossier *composants* , supprimez les dossiers **MRTK** suivants, ainsi que leurs fichiers. meta (le projet n’a peut-être pas tous les dossiers listés)</span><span class="sxs-lookup"><span data-stu-id="52fc7-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="52fc7-135">MRTK/noyau</span><span class="sxs-lookup"><span data-stu-id="52fc7-135">MRTK/Core</span></span>
    - <span data-ttu-id="52fc7-136">MRTK/exemples</span><span class="sxs-lookup"><span data-stu-id="52fc7-136">MRTK/Examples</span></span>
    - <span data-ttu-id="52fc7-137">MRTK/extensions</span><span class="sxs-lookup"><span data-stu-id="52fc7-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="52fc7-138">MRTK/fournisseurs</span><span class="sxs-lookup"><span data-stu-id="52fc7-138">MRTK/Providers</span></span>
    - <span data-ttu-id="52fc7-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="52fc7-139">MRTK/SDK</span></span>
    - <span data-ttu-id="52fc7-140">MRTK/services</span><span class="sxs-lookup"><span data-stu-id="52fc7-140">MRTK/Services</span></span>
    - <span data-ttu-id="52fc7-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="52fc7-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="52fc7-142">Si des modifications ont été apportées aux nuanceurs MRTK, créez une sauvegarde locale avant de supprimer le dossier MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="52fc7-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="52fc7-143">MRTK/outils</span><span class="sxs-lookup"><span data-stu-id="52fc7-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="52fc7-144">Ne supprimez pas le dossier **MixedRealityToolkit. generated** , ni son fichier. meta.</span><span class="sxs-lookup"><span data-stu-id="52fc7-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="52fc7-145">Supprimer le dossier de **bibliothèque**</span><span class="sxs-lookup"><span data-stu-id="52fc7-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="52fc7-146">Certains outils Unity, comme Unity collab, enregistrent les informations de configuration dans le dossier de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="52fc7-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="52fc7-147">Si vous utilisez un outil qui effectue cette opération, commencez par copier le dossier de données de l’outil à partir de la bibliothèque avant de le supprimer, puis restaurez-le après la régénération de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="52fc7-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="52fc7-148">Rouvrir le projet dans Unity</span><span class="sxs-lookup"><span data-stu-id="52fc7-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="52fc7-149">Importer les nouveaux packages Unity</span><span class="sxs-lookup"><span data-stu-id="52fc7-149">Import the new unity packages</span></span>
    - <span data-ttu-id="52fc7-150">Fondation- _importer ce package en premier_</span><span class="sxs-lookup"><span data-stu-id="52fc7-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="52fc7-151">Outils</span><span class="sxs-lookup"><span data-stu-id="52fc7-151">Tools</span></span>
    - <span data-ttu-id="52fc7-152">Facultatif Extensions</span><span class="sxs-lookup"><span data-stu-id="52fc7-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="52fc7-153">Si des extensions supplémentaires ont été installées, elles devront peut-être être réimportées.</span><span class="sxs-lookup"><span data-stu-id="52fc7-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="52fc7-154">Facultatif Illustre</span><span class="sxs-lookup"><span data-stu-id="52fc7-154">(Optional) Examples</span></span>
1. <span data-ttu-id="52fc7-155">Fermez Unity et supprimez le dossier de **bibliothèque** (lisez la remarque ci-dessous !).</span><span class="sxs-lookup"><span data-stu-id="52fc7-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="52fc7-156">Cette étape est nécessaire pour forcer Unity à actualiser sa base de données de ressources et à harmoniser les profils personnalisés existants.</span><span class="sxs-lookup"><span data-stu-id="52fc7-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="52fc7-157">Lancer Unity et pour chaque scène du projet</span><span class="sxs-lookup"><span data-stu-id="52fc7-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="52fc7-158">Supprime **MixedRealityToolkit** et **MixedRealityPlayspace**, le cas échéant, de la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="52fc7-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="52fc7-159">Cette opération supprimera la caméra principale, mais elle sera recréée à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="52fc7-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="52fc7-160">Si des propriétés de la caméra principale ont été modifiées manuellement, elles devront être réappliquées manuellement une fois la nouvelle caméra créée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="52fc7-161">Sélectionnez **MixedRealityToolkit-> ajouter à la scène et configurer**</span><span class="sxs-lookup"><span data-stu-id="52fc7-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="52fc7-162">Sélectionnez **MixedRealityToolkit-> Utilities-> mettre à jour-> les profils de mappage de contrôleur** (ne doit être effectué qu’une seule fois). cela permet de mettre à jour tous les profils de mappage de contrôleur personnalisés avec les données et les axes mis à jour, tout en laissant vos actions d’entrée personnalisées intactes.</span><span class="sxs-lookup"><span data-stu-id="52fc7-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="52fc7-163">Exécutez l' [outil de migration](../features/tools/migration-window.md) et exécutez l’outil sur le *projet complet* pour vous assurer que l’ensemble de votre code est mis à jour vers la dernière version.</span><span class="sxs-lookup"><span data-stu-id="52fc7-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="52fc7-164">La fenêtre de migration contient un certain nombre de gestionnaires de migration différents, qui doivent chacun être exécutés eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="52fc7-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="52fc7-165">Cette étape implique les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="52fc7-165">This step involves:</span></span>
   - <span data-ttu-id="52fc7-166">Sélectionnez le premier gestionnaire de migration dans la liste déroulante **Gestionnaire de migration** .</span><span class="sxs-lookup"><span data-stu-id="52fc7-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="52fc7-167">Cliquez sur le bouton « projet complet ».</span><span class="sxs-lookup"><span data-stu-id="52fc7-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="52fc7-168">Cliquez sur le bouton « Ajouter le projet complet pour la migration » (cela permet d’analyser l’ensemble du projet pour rechercher les objets à migrer).</span><span class="sxs-lookup"><span data-stu-id="52fc7-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="52fc7-169">Cliquez sur le bouton « migrer » qui doit être activé si des objets pouvant être migrés ont été trouvés.</span><span class="sxs-lookup"><span data-stu-id="52fc7-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="52fc7-170">Répétez les trois étapes précédentes pour chacun des gestionnaires de migration dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="52fc7-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="52fc7-171">(Consultez [ce problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) qui couvre le travail qui peut être effectué pour simplifier ce processus de migration dans une version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="52fc7-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="52fc7-172">Basculement depuis les fichiers de ressources Unity vers l’outil de la fonctionnalité de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="52fc7-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="52fc7-173">Passer des fichiers de ressources Unity aux packages d’outils de la fonctionnalité de réalité mixte offre un certain nombre d’avantages :</span><span class="sxs-lookup"><span data-stu-id="52fc7-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="52fc7-174">Mise à jour plus facile</span><span class="sxs-lookup"><span data-stu-id="52fc7-174">Easier updating</span></span>
- <span data-ttu-id="52fc7-175">Temps de compilation plus rapides</span><span class="sxs-lookup"><span data-stu-id="52fc7-175">Faster compile times</span></span>
- <span data-ttu-id="52fc7-176">Moins de projets dans la solution Visual Studio</span><span class="sxs-lookup"><span data-stu-id="52fc7-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="52fc7-177">La modification de l’outil de la fonctionnalité de réalité mixte nécessite un ensemble d’étapes manuelles à usage unique.</span><span class="sxs-lookup"><span data-stu-id="52fc7-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="52fc7-178">Enregistrez une copie de votre projet actuel.</span><span class="sxs-lookup"><span data-stu-id="52fc7-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="52fc7-179">Fermer Unity</span><span class="sxs-lookup"><span data-stu-id="52fc7-179">Close Unity</span></span>
1. <span data-ttu-id="52fc7-180">Dans le dossier *composants* , supprimez les dossiers **MRTK** suivants, ainsi que leurs fichiers. meta (le projet n’a peut-être pas tous les dossiers listés)</span><span class="sxs-lookup"><span data-stu-id="52fc7-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="52fc7-181">MRTK/noyau</span><span class="sxs-lookup"><span data-stu-id="52fc7-181">MRTK/Core</span></span>
    - <span data-ttu-id="52fc7-182">MRTK/exemples</span><span class="sxs-lookup"><span data-stu-id="52fc7-182">MRTK/Examples</span></span>
    - <span data-ttu-id="52fc7-183">MRTK/extensions</span><span class="sxs-lookup"><span data-stu-id="52fc7-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="52fc7-184">MRTK/fournisseurs</span><span class="sxs-lookup"><span data-stu-id="52fc7-184">MRTK/Providers</span></span>
    - <span data-ttu-id="52fc7-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="52fc7-185">MRTK/SDK</span></span>
    - <span data-ttu-id="52fc7-186">MRTK/services</span><span class="sxs-lookup"><span data-stu-id="52fc7-186">MRTK/Services</span></span>
    - <span data-ttu-id="52fc7-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="52fc7-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="52fc7-188">Si des modifications ont été apportées aux nuanceurs MRTK, créez une sauvegarde locale avant de supprimer le dossier MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="52fc7-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="52fc7-189">MRTK/outils</span><span class="sxs-lookup"><span data-stu-id="52fc7-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="52fc7-190">Ne supprimez pas le dossier **MixedRealityToolkit. generated** , ni son fichier. meta.</span><span class="sxs-lookup"><span data-stu-id="52fc7-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="52fc7-191">Supprimer le dossier de **bibliothèque**</span><span class="sxs-lookup"><span data-stu-id="52fc7-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="52fc7-192">Certains outils Unity, comme Unity collab, enregistrent les informations de configuration dans le dossier de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="52fc7-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="52fc7-193">Si vous utilisez un outil qui effectue cette opération, commencez par copier le dossier de données de l’outil à partir de la bibliothèque avant de le supprimer, puis restaurez-le après la régénération de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="52fc7-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="52fc7-194">Rouvrir le projet dans Unity</span><span class="sxs-lookup"><span data-stu-id="52fc7-194">Re-open the project in Unity</span></span>

<span data-ttu-id="52fc7-195">Une fois les étapes précédentes effectuées, exécutez l’outil de la [fonctionnalité de réalité mixte](#mixed-reality-feature-tool) et importez la version souhaitée du kit de tâches de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="52fc7-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="52fc7-196">Mise à jour de 2.3.0 vers 2.4.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="52fc7-197">[Renommages](#folder-renames-in-240) 
 de dossiers [Modifications](#api-changes-in-240) de l’API</span><span class="sxs-lookup"><span data-stu-id="52fc7-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="52fc7-198">Renommages de dossiers dans 2.4.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="52fc7-199">Les dossiers MixedRealityToolkit ont été renommés et déplacés dans une hiérarchie commune dans la version 2,4.</span><span class="sxs-lookup"><span data-stu-id="52fc7-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="52fc7-200">Si une application utilise des chemins d’accès codés en dur pour MRTK ressources, elle doit être mise à jour selon le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="52fc7-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="52fc7-201">Dossier précédent</span><span class="sxs-lookup"><span data-stu-id="52fc7-201">Previous Folder</span></span> | <span data-ttu-id="52fc7-202">Nouveau dossier</span><span class="sxs-lookup"><span data-stu-id="52fc7-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="52fc7-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="52fc7-203">MixedRealityToolkit</span></span> | <span data-ttu-id="52fc7-204">MRTK/noyau</span><span class="sxs-lookup"><span data-stu-id="52fc7-204">MRTK/Core</span></span> |
| <span data-ttu-id="52fc7-205">MixedRealityToolkit. exemples</span><span class="sxs-lookup"><span data-stu-id="52fc7-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="52fc7-206">MRTK/exemples</span><span class="sxs-lookup"><span data-stu-id="52fc7-206">MRTK/Examples</span></span> |
| <span data-ttu-id="52fc7-207">MixedRealityToolkit. extensions</span><span class="sxs-lookup"><span data-stu-id="52fc7-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="52fc7-208">MRTK/extensions</span><span class="sxs-lookup"><span data-stu-id="52fc7-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="52fc7-209">MixedRealityToolkit. Providers</span><span class="sxs-lookup"><span data-stu-id="52fc7-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="52fc7-210">MRTK/fournisseurs</span><span class="sxs-lookup"><span data-stu-id="52fc7-210">MRTK/Providers</span></span> |
| <span data-ttu-id="52fc7-211">MixedRealityToolkit. SDK</span><span class="sxs-lookup"><span data-stu-id="52fc7-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="52fc7-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="52fc7-212">MRTK/SDK</span></span> |
| <span data-ttu-id="52fc7-213">MixedRealityToolkit. services</span><span class="sxs-lookup"><span data-stu-id="52fc7-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="52fc7-214">MRTK/services</span><span class="sxs-lookup"><span data-stu-id="52fc7-214">MRTK/Services</span></span> |
| <span data-ttu-id="52fc7-215">MixedRealityToolkit. tests</span><span class="sxs-lookup"><span data-stu-id="52fc7-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="52fc7-216">MRTK/tests</span><span class="sxs-lookup"><span data-stu-id="52fc7-216">MRTK/Tests</span></span> |
| <span data-ttu-id="52fc7-217">MixedRealityToolkit. Tools</span><span class="sxs-lookup"><span data-stu-id="52fc7-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="52fc7-218">MRTK/outils</span><span class="sxs-lookup"><span data-stu-id="52fc7-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="52fc7-219">`MixedRealityToolkit.Generated`Contient les fichiers générés par le client et reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="52fc7-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="52fc7-220">Paramétrage des yeux dans 2.4.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="52fc7-221">Cette version de MRTK modifie les étapes requises pour la configuration des regards oculaires.</span><span class="sxs-lookup"><span data-stu-id="52fc7-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="52fc7-222">La case à cocher _« IsEyeTrackingEnabled »_ se trouve dans les paramètres de pointage du profil de pointeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="52fc7-223">L’activation de cette case à cocher activera le point de présence oculaire, et non le point de regard par défaut.</span><span class="sxs-lookup"><span data-stu-id="52fc7-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="52fc7-224">Pour plus d’informations sur ces modifications et pour obtenir des instructions complètes pour la configuration du suivi des yeux, consultez l’article [suivi des yeux](../features/input/eye-tracking/eye-tracking-basic-setup.md) .</span><span class="sxs-lookup"><span data-stu-id="52fc7-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="52fc7-225">Comportement du pointeur en forme d’oeil dans 2.4.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="52fc7-226">Le comportement du pointeur par défaut de l’œil oculaire a été modifié pour correspondre au comportement du pointeur par défaut de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="52fc7-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="52fc7-227">Un pointeur en forme d’oeil est automatiquement supprimé une fois qu’une main est détectée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="52fc7-228">Le pointeur vers le regard de l’œil redevient visible après avoir dit « Select ».</span><span class="sxs-lookup"><span data-stu-id="52fc7-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="52fc7-229">Pour plus d’informations sur les configurations en regard et sur la main, consultez l’article sur les [yeux et les mains](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) .</span><span class="sxs-lookup"><span data-stu-id="52fc7-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="52fc7-230">Modifications de l’API dans 2.4.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-230">API changes in 2.4.0</span></span>

<span data-ttu-id="52fc7-231">**Classes de contrôleur personnalisé**</span><span class="sxs-lookup"><span data-stu-id="52fc7-231">**Custom controller classes**</span></span>

<span data-ttu-id="52fc7-232">Les classes de contrôleur personnalisé devaient auparavant définir `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="52fc7-233">Cette méthode a été rendue obsolète dans 2,4, car le paramètre de port était redondant avec la main propre à la classe de contrôleur.</span><span class="sxs-lookup"><span data-stu-id="52fc7-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="52fc7-234">La nouvelle méthode n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="52fc7-234">The new method has no parameters.</span></span> <span data-ttu-id="52fc7-235">De plus, de nombreuses classes de contrôleur ont défini cela de la même façon ( `AssignControllerMappings(DefaultInteractions);` ), de sorte que l’appel complet a été refactorisé en `BaseController` et a fait une substitution facultative au lieu de required.</span><span class="sxs-lookup"><span data-stu-id="52fc7-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="52fc7-236">**Propriétés de regard de l’œil**</span><span class="sxs-lookup"><span data-stu-id="52fc7-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="52fc7-237">La `UseEyeTracking` propriété de l' `GazeProvider` implémentation de `IMixedRealityEyeGazeProvider` a été renommée en `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="52fc7-238">Si vous l’avez fait précédemment...</span><span class="sxs-lookup"><span data-stu-id="52fc7-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="52fc7-239">Procédez maintenant...</span><span class="sxs-lookup"><span data-stu-id="52fc7-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="52fc7-240">**Propriétés WindowsApiChecker**</span><span class="sxs-lookup"><span data-stu-id="52fc7-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="52fc7-241">Les propriétés WindowsApiChecker suivantes ont été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="52fc7-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="52fc7-242">Utilisez `IsMethodAvailable` `IsPropertyAvailable` ou `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="52fc7-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="52fc7-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="52fc7-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="52fc7-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="52fc7-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="52fc7-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="52fc7-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="52fc7-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="52fc7-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="52fc7-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="52fc7-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="52fc7-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="52fc7-249">Il n’est pas prévu d’ajouter des propriétés à WindowsApiChecker pour les futures versions de contrat d’API.</span><span class="sxs-lookup"><span data-stu-id="52fc7-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="52fc7-250">**GltfMeshPrimitiveAttributes en lecture seule**</span><span class="sxs-lookup"><span data-stu-id="52fc7-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="52fc7-251">Les attributs primitifs de maillage gltf utilisés pour être définissables, ils sont désormais en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="52fc7-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="52fc7-252">Leurs valeurs seront définies une fois lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="52fc7-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="52fc7-253">Icône de bouton personnalisé migration</span><span class="sxs-lookup"><span data-stu-id="52fc7-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="52fc7-254">Les icônes de bouton personnalisées précédemment nécessitaient l’attribution d’un nouveau matériau au convertisseur Quad du bouton.</span><span class="sxs-lookup"><span data-stu-id="52fc7-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="52fc7-255">Cela n’est plus nécessaire et nous vous recommandons de déplacer les textures d’icône personnalisées dans un IconSet.</span><span class="sxs-lookup"><span data-stu-id="52fc7-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="52fc7-256">Les matériaux et les icônes personnalisés existants sont conservés.</span><span class="sxs-lookup"><span data-stu-id="52fc7-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="52fc7-257">Toutefois, elles seront moins optimales jusqu’à leur mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="52fc7-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="52fc7-258">Pour mettre à niveau les ressources sur tous les boutons du projet au nouveau format recommandé, utilisez ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="52fc7-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="52fc7-259">(Kit d’outils de réalité mixte-utilitaires de >-fenêtre de migration de >-> sélection du gestionnaire de migration-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="52fc7-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Boîte de dialogue mettre à niveau la fenêtre](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="52fc7-261">Si aucune icône n’est trouvée dans le jeu d’icônes par défaut lors de la migration, un jeu d’icônes personnalisé est créé dans MixedRealityToolkit. generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="52fc7-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="52fc7-262">Une boîte de dialogue indiquera que cette opération a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="52fc7-262">A dialog will indicate that this has taken place.</span></span>

![Notification d’icône personnalisée](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="52fc7-264">Mise à jour de 2.2.0 vers 2.3.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="52fc7-265">Modifications d'API</span><span class="sxs-lookup"><span data-stu-id="52fc7-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="52fc7-266">Modifications de l’API dans 2.3.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-266">API changes in 2.3.0</span></span>

<span data-ttu-id="52fc7-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="52fc7-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="52fc7-268">Le champ privé ControllerPoseSynchronizer. droitier a été marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="52fc7-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="52fc7-269">Cela doit avoir un impact minimal sur les applications, car le champ n’est pas visible en dehors de sa classe.</span><span class="sxs-lookup"><span data-stu-id="52fc7-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="52fc7-270">La méthode setter de la propriété ControllerPoseSynchronizer. de la main publique a été supprimée ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="52fc7-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="52fc7-271">**MSBuild pour Unity**</span><span class="sxs-lookup"><span data-stu-id="52fc7-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="52fc7-272">Cette version de MRTK utilise une version plus récente de MSBuild pour Unity que les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="52fc7-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="52fc7-273">Pendant le chargement du projet, si la version antérieure est répertoriée dans le manifeste du gestionnaire de packages Unity, la boîte de dialogue de configuration s’affiche, avec l’option Activer MSBuild pour Unity activée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="52fc7-274">L’application effectue une mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="52fc7-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="52fc7-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="52fc7-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="52fc7-276">La classe ScriptingUtilities a été marquée comme obsolète et a été remplacée par ScriptUtilities, dans l’assembly Microsoft. MixedReality. Toolkit. Editor. Utilities.</span><span class="sxs-lookup"><span data-stu-id="52fc7-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="52fc7-277">La nouvelle classe affine le comportement précédent et ajoute la prise en charge de la suppression des définitions de script.</span><span class="sxs-lookup"><span data-stu-id="52fc7-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="52fc7-278">Bien que le code existant continue à fonctionner dans la version 2.3.0, il est recommandé de mettre à jour vers la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="52fc7-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="52fc7-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="52fc7-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="52fc7-280">Les membres lineRendererSelected et lineRendererNoTarget de la classe ShellHandRayPointer ont été remplacés par lineMaterialSelected et lineMaterialNoTarget, respectivement ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="52fc7-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="52fc7-281">Remplacez lineRendererSelected par lineMaterialSelected et/ou lineRendererNoTarget par lineMaterialNoTarget pour résoudre les erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="52fc7-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="52fc7-282">**Startupbehavior lui faisants de l’observateur spatial**</span><span class="sxs-lookup"><span data-stu-id="52fc7-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="52fc7-283">Les observateurs spatiaux basés sur la `BaseSpatialObserver` classe honorent désormais la valeur de startupbehavior lui faisant lorsqu’ils sont réactivés ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="52fc7-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="52fc7-284">Aucune modification n’est requise pour tirer parti de ce correctif.</span><span class="sxs-lookup"><span data-stu-id="52fc7-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="52fc7-285">**Prefabs de contrôle d’expérience utilisateur mis à jour pour utiliser PressableButton**</span><span class="sxs-lookup"><span data-stu-id="52fc7-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="52fc7-286">Les prefabs suivants utilisent désormais le composant PressableButton au lieu de TouchHandler pour une interaction proche ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="52fc7-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="52fc7-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="52fc7-287">AnimationButton</span></span>
- <span data-ttu-id="52fc7-288">Bouton</span><span class="sxs-lookup"><span data-stu-id="52fc7-288">Button</span></span>
- <span data-ttu-id="52fc7-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="52fc7-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="52fc7-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="52fc7-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="52fc7-291">Case à cocher</span><span class="sxs-lookup"><span data-stu-id="52fc7-291">CheckBox</span></span>
- <span data-ttu-id="52fc7-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="52fc7-292">RadialSet</span></span>
- <span data-ttu-id="52fc7-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="52fc7-293">ToggleButton</span></span>
- <span data-ttu-id="52fc7-294">Bouton bascule</span><span class="sxs-lookup"><span data-stu-id="52fc7-294">ToggleSwitch</span></span>
- <span data-ttu-id="52fc7-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="52fc7-295">UnityUIButton</span></span>
- <span data-ttu-id="52fc7-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="52fc7-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="52fc7-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="52fc7-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="52fc7-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="52fc7-298">UnityUIToggleButton</span></span>

<span data-ttu-id="52fc7-299">Le code d’application peut nécessiter une mise à jour en raison de cette modification.</span><span class="sxs-lookup"><span data-stu-id="52fc7-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="52fc7-300">**Espace de noms WindowsMixedRealityUtilities**</span><span class="sxs-lookup"><span data-stu-id="52fc7-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="52fc7-301">L’espace de noms de WindowsMixedRealityUtilities est passé de Microsoft. MixedReality. Toolkit. WindowsMixedReality. Input à Microsoft. MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="52fc7-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="52fc7-302">Mettez à jour les instructions #using pour résoudre les erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="52fc7-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="52fc7-303">Mise à jour de 2.1.0 vers 2.2.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="52fc7-304">Modifications d'API</span><span class="sxs-lookup"><span data-stu-id="52fc7-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="52fc7-305">Modifications de l’API dans 2.2.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-305">API changes in 2.2.0</span></span>

<span data-ttu-id="52fc7-306">**IMixedRealityBoundarySystem. Contains**</span><span class="sxs-lookup"><span data-stu-id="52fc7-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="52fc7-307">Cette méthode prenait auparavant un enum expérimental défini par Unity spécifique.</span><span class="sxs-lookup"><span data-stu-id="52fc7-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="52fc7-308">Elle prend désormais une énumération définie par MRTK qui est identique à l’énumération Unity.</span><span class="sxs-lookup"><span data-stu-id="52fc7-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="52fc7-309">Cette modification permet de préparer le MRTK pour les API de limite futures d’Unity.</span><span class="sxs-lookup"><span data-stu-id="52fc7-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="52fc7-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="52fc7-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="52fc7-311">Pour mieux décrire les conditions requises pour la prise en charge d’un profil, MixedRealityServiceProfileAttribute a été mis à jour pour ajouter une collection facultative de types exclus.</span><span class="sxs-lookup"><span data-stu-id="52fc7-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="52fc7-312">Dans le cadre de cette modification, la propriété ServiceType a été modifiée de type en type [] et renommée en RequiredTypes.</span><span class="sxs-lookup"><span data-stu-id="52fc7-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="52fc7-313">Une deuxième propriété, ExcludedTypes a également été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="52fc7-314">Mise à jour de 2.0.0 vers 2.1.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="52fc7-315">Modifications d'API</span><span class="sxs-lookup"><span data-stu-id="52fc7-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="52fc7-316">Modifications de profil</span><span class="sxs-lookup"><span data-stu-id="52fc7-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="52fc7-317">Modifications de l’API dans 2.1.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-317">API changes in 2.1.0</span></span>

<span data-ttu-id="52fc7-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="52fc7-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="52fc7-319">Le `BaseNearInteractionTouchable` a été modifié pour marquer la `OnValidate` méthode comme étant virtuelle.</span><span class="sxs-lookup"><span data-stu-id="52fc7-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="52fc7-320">Les classes qui étendent `BaseNearInteractionTouchable` (p. ex. `NearInteractionTouchableUnityUI` ) ont été mises à jour pour refléter cette modification.</span><span class="sxs-lookup"><span data-stu-id="52fc7-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="52fc7-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="52fc7-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="52fc7-322">La classe `ColliderNearInteractionTouchable` a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="52fc7-323">Mettez à jour les références de code à utiliser `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="52fc7-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="52fc7-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="52fc7-325">**_Ajoute_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-325">**_Added_**</span></span>

<span data-ttu-id="52fc7-326">`IMixedRealityMouseDeviceManager` a été ajouté `CursorSpeed` et les `WheelSpeed` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="52fc7-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="52fc7-327">Ces propriétés permettent aux applications de spécifier une valeur de multiplicateur par laquelle la vitesse du curseur et de la roue, respectivement, sera mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="52fc7-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="52fc7-328">Il s’agit d’une modification avec rupture qui requiert la modification des implémentations existantes du gestionnaire de périphériques de la souris.</span><span class="sxs-lookup"><span data-stu-id="52fc7-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="52fc7-329">Cette modification n’est pas à compatibilité descendante avec la version 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="52fc7-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="52fc7-330">**_Déprécié_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-330">**_Deprecated_**</span></span>

<span data-ttu-id="52fc7-331">La `MouseInputProfile` propriété a été marquée comme obsolète et sera supprimée d’une future version de Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="52fc7-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="52fc7-332">Il est recommandé que le code d’application n’utilise plus cette propriété.</span><span class="sxs-lookup"><span data-stu-id="52fc7-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="52fc7-333">**Avec interaction**</span><span class="sxs-lookup"><span data-stu-id="52fc7-333">**Interactable**</span></span>

<span data-ttu-id="52fc7-334">Les méthodes et propriétés suivantes sont dépréciées et seront supprimées d’une future version de Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="52fc7-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="52fc7-335">Il est recommandé de mettre à jour le code d’application conformément aux instructions contenues dans l’attribut Obsolete et affiché dans la console.</span><span class="sxs-lookup"><span data-stu-id="52fc7-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="52fc7-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="52fc7-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="52fc7-337">La `NearInteractionTouchableSurface` classe a été ajoutée et sert à présent de classe de base pour `NearInteractionTouchable` et `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="52fc7-338">Modifications de profil dans 2.1.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="52fc7-339">**Profil de suivi de la main**</span><span class="sxs-lookup"><span data-stu-id="52fc7-339">**Hand tracking profile**</span></span>

<span data-ttu-id="52fc7-340">Les visualisations de la maille et de la jointure de la main disposent désormais d’un éditeur et de paramètres de lecteur distincts.</span><span class="sxs-lookup"><span data-stu-id="52fc7-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="52fc7-341">Le profil de suivi de la main a été mis à jour pour permettre la définition de ces visualisations sur ; Rien, tout, éditeur ou joueur.</span><span class="sxs-lookup"><span data-stu-id="52fc7-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Modes de visualisation manuelle](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="52fc7-343">Vous devrez peut-être mettre à jour les profils de suivi de main personnalisés pour qu’ils fonctionnent correctement avec la version 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="52fc7-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="52fc7-344">Cette modification n’est pas à compatibilité descendante avec la version 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="52fc7-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="52fc7-345">**Profil de simulation d’entrée**</span><span class="sxs-lookup"><span data-stu-id="52fc7-345">**Input simulation profile**</span></span>

<span data-ttu-id="52fc7-346">Le système de simulation d’entrée a été mis à niveau, ce qui modifie certains paramètres dans le profil de simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="52fc7-347">Certaines modifications ne peuvent pas être migrées automatiquement et les utilisateurs peuvent trouver que les profils utilisent des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="52fc7-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="52fc7-348">Toutes les liaisons de bouton de clavier et de bouton de la souris dans le profil ont été remplacées par une `KeyBinding` structure générique, qui stocke le type de liaison (clé ou souris), ainsi que le code de liaison réel (respectivement le numéro de code ou de bouton de la souris).</span><span class="sxs-lookup"><span data-stu-id="52fc7-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="52fc7-349">La structure a son propre inspecteur, qui autorise l’affichage unifié et offre un outil de liaison automatique pour définir rapidement des combinaisons de touches en appuyant sur la touche correspondante au lieu de sélectionner dans une liste déroulante très volumineuse.</span><span class="sxs-lookup"><span data-stu-id="52fc7-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="52fc7-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="52fc7-350">FastControlKey</span></span>
    - <span data-ttu-id="52fc7-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="52fc7-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="52fc7-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="52fc7-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="52fc7-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="52fc7-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="52fc7-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="52fc7-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="52fc7-355">`MouseLookToggle` était précédemment inclus dans l' `MouseLookButton` enum en tant que `InputSimulationMouseButton.Focused` , il s’agit maintenant d’une option distincte.</span><span class="sxs-lookup"><span data-stu-id="52fc7-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="52fc7-356">Quand cette option est activée, l’appareil photo continue de pivoter avec la souris après avoir relâché le bouton, jusqu’à ce que la touche Échap est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="52fc7-357">`HandDepthMultiplier` la valeur par défaut a été abaissée de 0,1 à 0,03 pour tenir compte de certaines modifications apportées à la simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="52fc7-358">Si l’appareil photo bouge trop rapidement lors du défilement, essayez de réduire cette valeur.</span><span class="sxs-lookup"><span data-stu-id="52fc7-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="52fc7-359">Les touches de rotation des mains ont été supprimées, la rotation manuelle est désormais contrôlée par la souris.</span><span class="sxs-lookup"><span data-stu-id="52fc7-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="52fc7-360">Le maintien de `HandRotateButton` (Ctrl) avec la clé de manipulation gauche/droite (lshift/Space) permet la rotation manuelle.</span><span class="sxs-lookup"><span data-stu-id="52fc7-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="52fc7-361">Un nouvel axe « UpDown » a été introduit dans la liste des axes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="52fc7-362">Cela contrôle le mouvement de l’appareil photo dans la verticale et les valeurs par défaut pour les touches Q/E, ainsi que pour les boutons de déclenchement du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="52fc7-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="52fc7-363">Pour plus d’informations sur ces modifications, consultez l’article [service de simulation d’entrée](../features/input-simulation/input-simulation-service.md) .</span><span class="sxs-lookup"><span data-stu-id="52fc7-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="52fc7-364">**Profil du fournisseur de données de souris**</span><span class="sxs-lookup"><span data-stu-id="52fc7-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="52fc7-365">Le profil du fournisseur de données de la souris a été mis à jour pour exposer les nouvelles `CursorSpeed` `WheelSpeed` Propriétés et.</span><span class="sxs-lookup"><span data-stu-id="52fc7-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="52fc7-366">Les profils personnalisés existants auront automatiquement les valeurs par défaut fournies.</span><span class="sxs-lookup"><span data-stu-id="52fc7-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="52fc7-367">Lorsque le profil est enregistré, ces nouvelles valeurs sont conservées.</span><span class="sxs-lookup"><span data-stu-id="52fc7-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="52fc7-368">**Profil de mappage du contrôleur**</span><span class="sxs-lookup"><span data-stu-id="52fc7-368">**Controller mapping profile**</span></span>

<span data-ttu-id="52fc7-369">Certains axes et types d’entrée ont été mis à jour dans 2.1.0, en particulier autour de la plateforme OpenVR.</span><span class="sxs-lookup"><span data-stu-id="52fc7-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="52fc7-370">Veillez à sélectionner **MixedRealityToolkit-> Utilities-> mise à jour-> les profils de mappage de contrôleur lors de** la mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="52fc7-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="52fc7-371">Cela permet de mettre à jour tous les profils de mappage de contrôleur personnalisés avec les données et les axes mis à jour, tout en conservant les actions d’entrée personnalisées qui leur sont affectées.</span><span class="sxs-lookup"><span data-stu-id="52fc7-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="52fc7-372">Mise à jour de RC2 vers 2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="52fc7-373">Entre les versions RC2 et 2.0.0 de Microsoft Mixed Reality Toolkit, les modifications ont été apportées et peuvent avoir un impact sur les projets existants.</span><span class="sxs-lookup"><span data-stu-id="52fc7-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="52fc7-374">Ce document décrit ces modifications et explique comment mettre à jour des projets vers la version 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="52fc7-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="52fc7-375">Modifications d'API</span><span class="sxs-lookup"><span data-stu-id="52fc7-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="52fc7-376">Modifications du nom de l’assembly</span><span class="sxs-lookup"><span data-stu-id="52fc7-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="52fc7-377">Modifications de l’API dans 2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-377">API changes in 2.0.0</span></span>

<span data-ttu-id="52fc7-378">Depuis la version RC2, un certain nombre de modifications de l’API ont été apportées, notamment certaines qui peuvent altérer des projets existants.</span><span class="sxs-lookup"><span data-stu-id="52fc7-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="52fc7-379">Les sections suivantes décrivent les modifications qui se sont produites entre les versions RC2 et 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="52fc7-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="52fc7-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="52fc7-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="52fc7-381">Les propriétés publiques suivantes sur l’objet MixedRealityToolkit ont été dépréciées.</span><span class="sxs-lookup"><span data-stu-id="52fc7-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="52fc7-382">`RegisteredMixedRealityServices` ne contient plus la collection de fournisseurs de données et de services d’extensions inscrits.</span><span class="sxs-lookup"><span data-stu-id="52fc7-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="52fc7-383">Pour accéder aux services d’extension, utilisez `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="52fc7-384">Pour accéder aux fournisseurs de données, effectuez un cast de l’instance de service vers [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) et utilisez `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="52fc7-385">Utilisez [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) ou [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) à la place pour les propriétés déconseillées suivantes</span><span class="sxs-lookup"><span data-stu-id="52fc7-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="52fc7-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="52fc7-386">**CoreServices**</span></span>

<span data-ttu-id="52fc7-387">La [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) classe est le remplacement des accesseurs système statiques (ex : BoundarySystem) trouvés dans l' `MixedRealityToolkit` objet.</span><span class="sxs-lookup"><span data-stu-id="52fc7-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="52fc7-388">Les `MixedRealityToolkit` accesseurs système ont été dépréciés dans la version 2.0.0 et seront supprimés dans une prochaine version de MRTK.</span><span class="sxs-lookup"><span data-stu-id="52fc7-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="52fc7-389">L’exemple de code suivant illustre l’ancien et le nouveau modèle.</span><span class="sxs-lookup"><span data-stu-id="52fc7-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="52fc7-390">L’utilisation de la nouvelle classe CoreSystem garantit que le code de votre application n’aura pas besoin d’être mis à jour si vous modifiez l’application pour utiliser un autre bureau d’enregistrement de service (par exemple, l’un des gestionnaires de service expérimentaux).</span><span class="sxs-lookup"><span data-stu-id="52fc7-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="52fc7-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="52fc7-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="52fc7-392">Avec l’ajout de IMixedRealityRaycastProvider, le profil de configuration du système d’entrée a été modifié.</span><span class="sxs-lookup"><span data-stu-id="52fc7-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="52fc7-393">Si vous avez un profil personnalisé, vous pouvez recevoir les erreurs dans l’image suivante lorsque vous exécutez votre application.</span><span class="sxs-lookup"><span data-stu-id="52fc7-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Sélection du fournisseur Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="52fc7-395">Pour résoudre ces problème, ajoutez une instance IMixedRealityRaycastProvider à votre profil de système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Sélection du fournisseur Raycast 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="52fc7-397">**Système d’événements**</span><span class="sxs-lookup"><span data-stu-id="52fc7-397">**Event System**</span></span>

- <span data-ttu-id="52fc7-398">Les `IMixedRealityEventSystem` anciennes méthodes API `Register` et `Unregister` ont été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="52fc7-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="52fc7-399">Ils sont conservés à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="52fc7-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="52fc7-400">`InputSystemGlobalListener` a été marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="52fc7-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="52fc7-401">Ses fonctionnalités n’ont pas changé.</span><span class="sxs-lookup"><span data-stu-id="52fc7-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="52fc7-402">`BaseInputHandler` la classe de base est passée de `InputSystemGlobalListener` à `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="52fc7-403">Il s’agit d’une modification avec rupture pour tous les descendants de `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="52fc7-404">**_Motivation derrière la modification_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="52fc7-405">L’ancienne API du système `Register` d’événement et `Unregister` peut potentiellement provoquer plusieurs problèmes dans le runtime, main étant :</span><span class="sxs-lookup"><span data-stu-id="52fc7-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="52fc7-406">Si un composant s’inscrit pour des événements globaux, il recevrait des événements d’entrée globaux de *tous les* types.</span><span class="sxs-lookup"><span data-stu-id="52fc7-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="52fc7-407">Si l’un des composants d’un objet s’inscrit pour les événements d’entrée globaux, tous les composants de cet objet recevront les événements d’entrée globaux de *tous les* types.</span><span class="sxs-lookup"><span data-stu-id="52fc7-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="52fc7-408">Si deux composants sur le même objet s’inscrivent à des événements globaux, puis que l’un d’eux est désactivé dans le runtime, le deuxième cesse de recevoir des événements globaux.</span><span class="sxs-lookup"><span data-stu-id="52fc7-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="52fc7-409">Nouvelle API `RegisterHandler` et `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="52fc7-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="52fc7-410">Fournit un contrôle explicite et granulaire sur les événements d’entrée qui doivent être écoutés globalement et qui doivent être axés sur le focus.</span><span class="sxs-lookup"><span data-stu-id="52fc7-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="52fc7-411">Permet à plusieurs composants sur le même objet d’écouter les événements globaux indépendamment l’un de l’autre.</span><span class="sxs-lookup"><span data-stu-id="52fc7-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="52fc7-412">**_Procédure de migration_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-412">**_How to migrate_**</span></span>

- <span data-ttu-id="52fc7-413">Si vous avez déjà appelé l' `Register` / `Unregister` API directement, remplacez ces appels par des appels à `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="52fc7-414">Utilisez les interfaces de gestionnaire que vous implémentez en tant que paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="52fc7-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="52fc7-415">Si vous implémentez plusieurs interfaces et que plusieurs d’entre elles écoutent les événements d’entrée globaux, appelez `RegisterHandler` plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="52fc7-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="52fc7-416">Si vous héritez de `InputSystemGlobalListener` , remplacez héritage par `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="52fc7-417">Implémentez `RegisterHandlers` les `UnregisterHandlers` méthodes abstraites et.</span><span class="sxs-lookup"><span data-stu-id="52fc7-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="52fc7-418">Dans l’appel `inputSystem.RegisterHandler` d’implémentation ( `inputSystem.UnregisterHandler` ) à inscrire sur toutes les interfaces de gestionnaire pour lesquelles vous souhaitez écouter des événements globaux.</span><span class="sxs-lookup"><span data-stu-id="52fc7-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="52fc7-419">Si vous héritez de `BaseInputHandler` , implémentez `RegisterHandlers` et des `UnregisterHandlers` méthodes abstraites (comme pour `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="52fc7-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="52fc7-420">**_Exemples de migration_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-420">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="52fc7-421">**Sensibilisation spatiale**</span><span class="sxs-lookup"><span data-stu-id="52fc7-421">**Spatial Awareness**</span></span>

<span data-ttu-id="52fc7-422">Les interfaces IMixedRealitySpatialAwarenessSystem et IMixedRealitySpatialAwarenessObserver ont pris en considération plusieurs modifications avec rupture, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="52fc7-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="52fc7-423">**_Modifications_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-423">**_Changes_**</span></span>

<span data-ttu-id="52fc7-424">La ou les méthodes suivantes ont été renommées pour mieux décrire leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="52fc7-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="52fc7-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` a été renommé pour `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` clarifier son utilisation.</span><span class="sxs-lookup"><span data-stu-id="52fc7-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="52fc7-426">**_Ajouts_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-426">**_Additions_**</span></span>

<span data-ttu-id="52fc7-427">En fonction des commentaires des clients, la prise en charge de la suppression aisée des données de sensibilisation spatiale précédemment observées a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="52fc7-428">**Solveurs**</span><span class="sxs-lookup"><span data-stu-id="52fc7-428">**Solvers**</span></span>

<span data-ttu-id="52fc7-429">Certains composants du solveur et la classe SolverHandler Manager ont été modifiés pour résoudre divers bogues et pour une utilisation plus intuitive.</span><span class="sxs-lookup"><span data-stu-id="52fc7-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="52fc7-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="52fc7-431">La classe ne s’étend plus de `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="52fc7-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="52fc7-432">`TrackedObjectToReference` propriété publique dépréciée et renommée en `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="52fc7-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="52fc7-433">`TrackedObjectType` déprécie les valeurs de contrôleur gauche & droit.</span><span class="sxs-lookup"><span data-stu-id="52fc7-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="52fc7-434">Utilisez plutôt `MotionController` `HandJoint` les valeurs ou et mettez à jour la nouvelle `TrackedHandedness` propriété pour limiter le suivi à gauche ou à droite du contrôleur</span><span class="sxs-lookup"><span data-stu-id="52fc7-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="52fc7-435">**_Entre_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-435">**_InBetween_**</span></span>

- <span data-ttu-id="52fc7-436">`TrackedObjectForSecondTransform` propriété publique dépréciée et renommée en `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="52fc7-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="52fc7-437">`AttachSecondTransformToNewTrackedObject()` a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="52fc7-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="52fc7-438">Pour mettre à jour le solveur, modifiez les propriétés publiques (par exemple,</span><span class="sxs-lookup"><span data-stu-id="52fc7-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="52fc7-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="52fc7-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="52fc7-440">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="52fc7-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="52fc7-441">`MaxDistance` propriété publique dépréciée et renommée en `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="52fc7-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="52fc7-442">`CloseDistance` propriété publique dépréciée et renommée en `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="52fc7-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="52fc7-443">La valeur par défaut pour `RaycastDirectionMode` est maintenant le `TrackedTargetForward` raycasts dans la direction de la transformation cible suivie</span><span class="sxs-lookup"><span data-stu-id="52fc7-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="52fc7-444">`OrientationMode` les valeurs enum, `Vertical` et `Full` , ont été renommées en `TrackedTarget` et `SurfaceNormal` respectivement</span><span class="sxs-lookup"><span data-stu-id="52fc7-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="52fc7-445">`KeepOrientationVertical` une propriété publique a été ajoutée pour contrôler si l’orientation du GameObject associé reste verticale</span><span class="sxs-lookup"><span data-stu-id="52fc7-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="52fc7-446">**Boutons**</span><span class="sxs-lookup"><span data-stu-id="52fc7-446">**Buttons**</span></span>

- <span data-ttu-id="52fc7-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) a maintenant la `DistanceSpaceMode` valeur par défaut pour la propriété `Local` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="52fc7-448">Cela permet de mettre à l’échelle les boutons tout en les conservant</span><span class="sxs-lookup"><span data-stu-id="52fc7-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="52fc7-449">**Découpage sphère**</span><span class="sxs-lookup"><span data-stu-id="52fc7-449">**Clipping Sphere**</span></span>

<span data-ttu-id="52fc7-450">L’interface ClippingSphere a été modifiée pour refléter les API trouvées dans ClippingBox et ClippingPlane.</span><span class="sxs-lookup"><span data-stu-id="52fc7-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="52fc7-451">La propriété RADIUS de ClippingSphere est maintenant calculée implicitement en fonction de l’échelle de transformation.</span><span class="sxs-lookup"><span data-stu-id="52fc7-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="52fc7-452">Pour que les développeurs doivent spécifier le rayon du ClippingSphere dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="52fc7-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="52fc7-453">Si vous souhaitez modifier le rayon, il vous suffit de mettre à jour l’échelle de transformation de la transformation comme vous le feriez normalement.</span><span class="sxs-lookup"><span data-stu-id="52fc7-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="52fc7-454">**NearInteractionTouchable et PokePointer**</span><span class="sxs-lookup"><span data-stu-id="52fc7-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="52fc7-455">NearInteractionTouchable ne gère pas Unity Canvas qui se touchent plus tard.</span><span class="sxs-lookup"><span data-stu-id="52fc7-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="52fc7-456">La classe NearInteractionTouchableUnityUI doit être utilisée pour l’interface utilisateur touchables à l’heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="52fc7-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="52fc7-457">ColliderNearInteractionTouchable est la nouvelle classe de base pour touchables basée sur les conflits, c’est-à-dire tous les touchable, à l’exception de NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="52fc7-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="52fc7-458">BaseNearInteractionTouchable. DistFront a été déplacé et renommé en PokePointer. TouchableDistance il s’agit de la distance et de laquelle le PokePointer peut interagir avec touchables.</span><span class="sxs-lookup"><span data-stu-id="52fc7-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="52fc7-459">Précédemment, chaque touchable avait sa propre distance d’interaction maximale, mais maintenant elle est définie dans le PokePointer, ce qui permet une meilleure optimisation.</span><span class="sxs-lookup"><span data-stu-id="52fc7-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="52fc7-460">BaseNearInteractionTouchable. DistBack a été renommé en PokeThreshold, ce qui indique clairement que PokeThreshold est l’équivalent de DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="52fc7-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="52fc7-461">Un touchable est activé lorsque le PokeThreshold est franchi et libéré lorsque DebounceThreshold est franchi.</span><span class="sxs-lookup"><span data-stu-id="52fc7-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="52fc7-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="52fc7-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="52fc7-463">L' `Microsoft.MixedReality.Toolkit` espace de noms a été ajouté à `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` et `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="52fc7-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="52fc7-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="52fc7-464">**PointerClickHandler**</span></span>

<span data-ttu-id="52fc7-465">La classe `PointerClickHandler` a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="52fc7-466">Le `PointerHandler` doit être utilisé à la place, il fournit les mêmes fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="52fc7-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="52fc7-467">**Prise en charge des clickers HoloLens**</span><span class="sxs-lookup"><span data-stu-id="52fc7-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="52fc7-468">Les mappages de contrôleur de l’un des contrôleurs HoloLens sont devenus indisponibles [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) pour être non mis en mains [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) .</span><span class="sxs-lookup"><span data-stu-id="52fc7-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="52fc7-469">Pour tenir compte de cela, un programme de mise à jour automatique s’exécute la première fois que vous ouvrez votre profil ControllerMapping.</span><span class="sxs-lookup"><span data-stu-id="52fc7-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="52fc7-470">Ouvrez un profil personnalisé au moins une fois après la mise à niveau vers 2.0.0 afin de déclencher cette étape de migration ponctuelle.</span><span class="sxs-lookup"><span data-stu-id="52fc7-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="52fc7-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="52fc7-471">**InteractableHighlight**</span></span>

<span data-ttu-id="52fc7-472">La classe `InteractableHighlight` a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="52fc7-473">La `InteractableOnFocus` classe et l' `FocusInteractableStates` élément multimédia doivent être utilisés à la place.</span><span class="sxs-lookup"><span data-stu-id="52fc7-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="52fc7-474">Pour créer un `Theme` élément multimédia pour l' `InteractableOnFocus` , cliquez avec le bouton droit dans la fenêtre projet et sélectionnez *créer* un thème interactif du kit de ressources de la  >  *réalité mixte*  >    >  .</span><span class="sxs-lookup"><span data-stu-id="52fc7-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="52fc7-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="52fc7-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="52fc7-476">`HandInteractionPanZoom` a été déplacé vers l’espace de noms de l’interface utilisateur, car il ne s’agissait pas d’un composant d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52fc7-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="52fc7-477">`HandPanEventData` a également été déplacé dans cet espace de noms et simplifié pour correspondre à d’autres données d’événement d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="52fc7-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="52fc7-478">Modifications du nom de l’assembly dans 2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="52fc7-479">Dans la version 2.0.0, tous les noms d’assembly du Toolkit de réalité mixte officielle et les fichiers de définition d’assembly (. asmdef) associés ont été mis à jour pour s’adapter au modèle suivant.</span><span class="sxs-lookup"><span data-stu-id="52fc7-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="52fc7-480">Dans certains cas, plusieurs assemblys ont été fusionnés pour créer une meilleure Unity de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="52fc7-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="52fc7-481">Si votre projet utilise des fichiers. asmdef personnalisés, ceux-ci peuvent nécessiter une mise à jour.</span><span class="sxs-lookup"><span data-stu-id="52fc7-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="52fc7-482">Les tableaux suivants décrivent comment les noms de fichiers RC2. asmdef sont mappés à la version 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="52fc7-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="52fc7-483">Tous les noms d’assemblys correspondent au nom de fichier. asmdef.</span><span class="sxs-lookup"><span data-stu-id="52fc7-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="52fc7-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="52fc7-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="52fc7-485">RC2</span><span class="sxs-lookup"><span data-stu-id="52fc7-485">RC2</span></span> | <span data-ttu-id="52fc7-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="52fc7-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="52fc7-488">Microsoft. MixedReality. Toolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="52fc7-489">MixedRealityToolkit. Core. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="52fc7-490">Microsoft. MixedReality. Toolkit. Editor. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="52fc7-491">MixedRealityToolkit. Core. Definitions. Utilities. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="52fc7-492">Supprimé, utilisez Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="52fc7-493">MixedRealityToolkit. Core. extensions. EditorClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="52fc7-494">Microsoft. MixedReality. Toolkit. Editor. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="52fc7-495">MixedRealityToolkit. Core. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="52fc7-496">Microsoft. MixedReality. Toolkit. Editor. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="52fc7-497">MixedRealityToolkit. Core. Inspectors. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="52fc7-498">Microsoft. MixedReality. Toolkit. Editor. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="52fc7-499">MixedRealityToolkit. Core. UtilitiesAsync. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="52fc7-500">Microsoft. MixedReality. Toolkit. Async. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="52fc7-501">MixedRealityToolkit. Core. Utilities. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="52fc7-502">Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="52fc7-503">MixedRealityToolkit. Utilities. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="52fc7-504">Microsoft. MixedReality. Toolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="52fc7-505">MixedRealityToolkit. Utilities. Gltf. importateurs. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="52fc7-506">Microsoft. MixedReality. Toolkit. Gltf. importateurs. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="52fc7-507">**MixedRealityToolkit. Providers**</span><span class="sxs-lookup"><span data-stu-id="52fc7-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="52fc7-508">RC2</span><span class="sxs-lookup"><span data-stu-id="52fc7-508">RC2</span></span> | <span data-ttu-id="52fc7-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="52fc7-510">MixedRealityToolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="52fc7-511">Microsoft. MixedReality. Toolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="52fc7-512">MixedRealityToolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="52fc7-513">Microsoft. MixedReality. Toolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="52fc7-514">MixedRealityToolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="52fc7-515">Microsoft. MixedReality. Toolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="52fc7-516">**MixedRealityToolkit. services**</span><span class="sxs-lookup"><span data-stu-id="52fc7-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="52fc7-517">RC2</span><span class="sxs-lookup"><span data-stu-id="52fc7-517">RC2</span></span> | <span data-ttu-id="52fc7-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="52fc7-519">MixedRealityToolkit. services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="52fc7-520">Microsoft. MixedReality. Toolkit. services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="52fc7-521">MixedRealityToolkit. services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="52fc7-522">Microsoft. MixedReality. Toolkit. services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="52fc7-523">MixedRealityToolkit. services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="52fc7-524">Microsoft. MixedReality. Toolkit. services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="52fc7-525">MixedRealityToolkit. services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="52fc7-526">Microsoft. MixedReality. Toolkit. services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="52fc7-527">MixedRealityToolkit. services. InputSimulation. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="52fc7-528">Microsoft. MixedReality. Toolkit. services. InputSimulation. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="52fc7-529">MixedRealityToolkit. services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="52fc7-530">Microsoft. MixedReality. Toolkit. services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="52fc7-531">MixedRealityToolkit. services. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="52fc7-532">Microsoft. MixedReality. Toolkit. services. InputSystem. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="52fc7-533">MixedRealityToolkit. services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="52fc7-534">Microsoft. MixedReality. Toolkit. services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="52fc7-535">MixedRealityToolkit. services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="52fc7-536">Microsoft. MixedReality. Toolkit. services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="52fc7-537">MixedRealityToolkit. services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="52fc7-538">Microsoft. MixedReality. Toolkit. services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="52fc7-539">**MixedRealityToolkit. SDK**</span><span class="sxs-lookup"><span data-stu-id="52fc7-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="52fc7-540">RC2</span><span class="sxs-lookup"><span data-stu-id="52fc7-540">RC2</span></span> | <span data-ttu-id="52fc7-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="52fc7-542">MixedRealityToolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="52fc7-543">Microsoft. MixedReality. Toolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="52fc7-544">MixedRealityToolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="52fc7-545">Microsoft. MixedReality. Toolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="52fc7-546">**MixedRealityToolkit. exemples**</span><span class="sxs-lookup"><span data-stu-id="52fc7-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="52fc7-547">RC2</span><span class="sxs-lookup"><span data-stu-id="52fc7-547">RC2</span></span> | <span data-ttu-id="52fc7-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="52fc7-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="52fc7-549">MixedRealityToolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="52fc7-550">Microsoft. MixedReality. Toolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="52fc7-551">MixedRealityToolkit. examples. démonstrations. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="52fc7-552">Microsoft. MixedReality. Toolkit. demos. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="52fc7-553">MixedRealityToolkit. examples. démonstrations. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="52fc7-554">Microsoft. MixedReality. Toolkit. demos. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="52fc7-555">MixedRealityToolkit. examples. issues. Utilities. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="52fc7-556">Microsoft. MixedReality. Toolkit. demos. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="52fc7-557">MixedRealityToolkit. examples. issues. Utilities. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="52fc7-558">Microsoft. MixedReality. Toolkit. demos. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="52fc7-559">MixedRealityToolkit. examples. démos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="52fc7-560">Microsoft. MixedReality. Toolkit. demos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="52fc7-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |