---
title: Prise en main du système de scène
description: Page d’accueil du système de scène avec MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 16adf431498f8146ca2cc60565e59dc8ae03fd92
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177576"
---
# <a name="scene-system-getting-started"></a><span data-ttu-id="893ee-104">Prise en main du système de scène</span><span class="sxs-lookup"><span data-stu-id="893ee-104">Scene system getting started</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="893ee-105">Quand utiliser le système de scène</span><span class="sxs-lookup"><span data-stu-id="893ee-105">When to use the scene system</span></span>

<span data-ttu-id="893ee-106">Si votre projet est constitué d’une seule scène, le système de scène n’est probablement pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="893ee-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="893ee-107">Elle est particulièrement utile quand une ou plusieurs des conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="893ee-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="893ee-108">Votre projet comporte plusieurs scènes.</span><span class="sxs-lookup"><span data-stu-id="893ee-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="893ee-109">Vous êtes utilisé pour le chargement d’une scène unique, mais vous n’aimez pas la manière dont il détruit l’instance MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="893ee-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="893ee-110">Vous souhaitez disposer d’un moyen simple de charger plusieurs scènes pour créer votre expérience.</span><span class="sxs-lookup"><span data-stu-id="893ee-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="893ee-111">Vous souhaitez disposer d’un moyen simple pour effectuer le suivi des opérations de chargement en cours ou un moyen simple de contrôler l’activation de scènes pour plusieurs scènes en cours de chargement à la fois.</span><span class="sxs-lookup"><span data-stu-id="893ee-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="893ee-112">Vous souhaitez garantir la cohérence et la prédiction de l’éclairage dans toutes vos scènes.</span><span class="sxs-lookup"><span data-stu-id="893ee-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="893ee-113">Ressources système de scène</span><span class="sxs-lookup"><span data-stu-id="893ee-113">Scene System Resources</span></span>

<span data-ttu-id="893ee-114">Par défaut, le système de scène utilise une paire d’objets de scène (DefaultManagerScene et DefaultLighting Scene).</span><span class="sxs-lookup"><span data-stu-id="893ee-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="893ee-115">Si l’une de ces scènes est introuvable, un message s’affiche dans l’inspecteur de profil du système de scène.</span><span class="sxs-lookup"><span data-stu-id="893ee-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Message de ressources par défaut](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="893ee-117">! Observe Si le projet utilise un gestionnaire personnalisé et des scènes d’éclairage, ce message peut être ignoré en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="893ee-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="893ee-118">les sections suivantes décrivent maintenant comment résoudre ce message, en fonction de la méthode utilisée pour importer la réalité mixte Shared Computer Toolkit.</span><span class="sxs-lookup"><span data-stu-id="893ee-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="893ee-119">Gestionnaire de package unity (UPM)</span><span class="sxs-lookup"><span data-stu-id="893ee-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="893ee-120">dans la réalité mixte Shared Computer Toolkit les packages UPM, les ressources système de scène sont empaquetées comme un exemple.</span><span class="sxs-lookup"><span data-stu-id="893ee-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="893ee-121">En raison de l’immuable des packages UPM, Unity n’est pas en mesure d’ouvrir le fichier de scène nécessaire, sauf s’ils sont importés explicitement dans le projet.</span><span class="sxs-lookup"><span data-stu-id="893ee-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="893ee-122">Pour importer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="893ee-122">To import use the following steps:</span></span>

- <span data-ttu-id="893ee-123">sélectionner une **fenêtre**  >  **Gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="893ee-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="893ee-124">sélectionner la **réalité mixte Shared Computer Toolkit Foundation**</span><span class="sxs-lookup"><span data-stu-id="893ee-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="893ee-125">Localiser les **ressources système** de la scène dans la section **exemples**</span><span class="sxs-lookup"><span data-stu-id="893ee-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importer des ressources système de scène](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="893ee-127">Sélectionner **Importer**</span><span class="sxs-lookup"><span data-stu-id="893ee-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="893ee-128">Fichiers de ressources (. pour Unity)</span><span class="sxs-lookup"><span data-stu-id="893ee-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="893ee-129">Si le dossier SceneSystemResources a été supprimé ou a été désélectionné lors de l’importation, il peut être récupéré en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="893ee-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="893ee-130">Sélectionner le package  >    >  **personnalisé** du package d’importation de ressources</span><span class="sxs-lookup"><span data-stu-id="893ee-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="893ee-131">ouvrez **Microsoft. MixedReality. Shared Computer Toolkit.** Package de base</span><span class="sxs-lookup"><span data-stu-id="893ee-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="893ee-132">S’assurer que les options **services/SceneSystem/SceneSystemResources** et toutes les options enfants sont sélectionnées</span><span class="sxs-lookup"><span data-stu-id="893ee-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Réimporter les ressources système de la scène](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="893ee-134">Sélectionner **Importer**</span><span class="sxs-lookup"><span data-stu-id="893ee-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="893ee-135">Comment utiliser le système de scène</span><span class="sxs-lookup"><span data-stu-id="893ee-135">How to use the scene system</span></span>

- [<span data-ttu-id="893ee-136">Types de scènes</span><span class="sxs-lookup"><span data-stu-id="893ee-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="893ee-137">Chargement de scènes de contenu</span><span class="sxs-lookup"><span data-stu-id="893ee-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="893ee-138">Surveillance du chargement du contenu</span><span class="sxs-lookup"><span data-stu-id="893ee-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="893ee-139">Chargement de scène d’éclairage</span><span class="sxs-lookup"><span data-stu-id="893ee-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="893ee-140">Paramètres de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="893ee-140">Editor settings</span></span>

<span data-ttu-id="893ee-141">Par défaut, le système de scène applique plusieurs comportements dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="893ee-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="893ee-142">si vous trouvez l’un de ces comportements, vous pouvez le désactiver dans la section Paramètres de l' **éditeur** de votre profil système de scène.</span><span class="sxs-lookup"><span data-stu-id="893ee-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="893ee-143">`Editor Manage Build Settings:` Si la valeur est true, le service met automatiquement à jour vos paramètres de build, garantissant ainsi que toutes les scènes de gestion, d’éclairage et de contenu sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="893ee-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="893ee-144">Désactivez cette opération si vous souhaitez un contrôle total sur les paramètres de Build.</span><span class="sxs-lookup"><span data-stu-id="893ee-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="893ee-145">`Editor Enforce Scene Order:` Si la valeur est true, le service s’assure que la scène Manager est affichée en premier dans la hiérarchie de la scène, suivie de Lighting, puis du contenu.</span><span class="sxs-lookup"><span data-stu-id="893ee-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="893ee-146">Désactivez cette opération si vous souhaitez un contrôle total sur la hiérarchie des scènes.</span><span class="sxs-lookup"><span data-stu-id="893ee-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="893ee-147">`Editor Manage Loaded Scenes:` Si la valeur est true, le service s’assure que le gestionnaire, le contenu et les scènes d’éclairage sont toujours chargés.</span><span class="sxs-lookup"><span data-stu-id="893ee-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="893ee-148">Désactivez si vous souhaitez un contrôle total sur les scènes chargées dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="893ee-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="893ee-149">`Editor Enforce Lighting Scene Types:` Si la valeur est true, le service garantit que seuls les composants liés à l’éclairage définis dans `PermittedLightingSceneComponentTypes` sont autorisés dans les scènes d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="893ee-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="893ee-150">Désactivez si vous souhaitez un contrôle total sur le contenu des scènes d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="893ee-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Paramètres de l’éditeur système de scène](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
