---
title: Système de scène - Bien démarrer
description: Page d’accueil du système de scène avec MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144299"
---
# <a name="scene-system-overview"></a><span data-ttu-id="757d4-104">Vue d’ensemble du système de scène</span><span class="sxs-lookup"><span data-stu-id="757d4-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="757d4-105">Quand utiliser le système de scène</span><span class="sxs-lookup"><span data-stu-id="757d4-105">When to use the scene system</span></span>

<span data-ttu-id="757d4-106">Si votre projet est constitué d’une seule scène, le système de scène n’est probablement pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="757d4-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="757d4-107">Elle est particulièrement utile quand une ou plusieurs des conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="757d4-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="757d4-108">Votre projet comporte plusieurs scènes.</span><span class="sxs-lookup"><span data-stu-id="757d4-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="757d4-109">Vous êtes utilisé pour le chargement d’une scène unique, mais vous n’aimez pas la manière dont il détruit l’instance MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="757d4-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="757d4-110">Vous souhaitez disposer d’un moyen simple de charger plusieurs scènes pour créer votre expérience.</span><span class="sxs-lookup"><span data-stu-id="757d4-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="757d4-111">Vous souhaitez disposer d’un moyen simple pour effectuer le suivi des opérations de chargement en cours ou un moyen simple de contrôler l’activation de scènes pour plusieurs scènes en cours de chargement à la fois.</span><span class="sxs-lookup"><span data-stu-id="757d4-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="757d4-112">Vous souhaitez garantir la cohérence et la prédiction de l’éclairage dans toutes vos scènes.</span><span class="sxs-lookup"><span data-stu-id="757d4-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="757d4-113">Ressources système de scène</span><span class="sxs-lookup"><span data-stu-id="757d4-113">Scene System Resources</span></span>

<span data-ttu-id="757d4-114">Par défaut, le système de scène utilise une paire d’objets de scène (DefaultManagerScene et DefaultLighting Scene).</span><span class="sxs-lookup"><span data-stu-id="757d4-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="757d4-115">Si l’une de ces scènes est introuvable, un message s’affiche dans l’inspecteur de profil du système de scène.</span><span class="sxs-lookup"><span data-stu-id="757d4-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Message de ressources par défaut](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="757d4-117">! Observe Si le projet utilise un gestionnaire personnalisé et des scènes d’éclairage, ce message peut être ignoré en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="757d4-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="757d4-118">Les sections suivantes décrivent maintenant comment résoudre ce message, en fonction de la méthode utilisée pour importer le Toolkit de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="757d4-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="757d4-119">Gestionnaire de package Unity (UPM)</span><span class="sxs-lookup"><span data-stu-id="757d4-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="757d4-120">Dans les packages UPM de la boîte à outils de réalité mixte, les ressources système de scène sont empaquetées comme un exemple.</span><span class="sxs-lookup"><span data-stu-id="757d4-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="757d4-121">En raison de l’immuable des packages UPM, Unity n’est pas en mesure d’ouvrir le fichier de scène nécessaire, sauf s’ils sont importés explicitement dans le projet.</span><span class="sxs-lookup"><span data-stu-id="757d4-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="757d4-122">Pour importer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="757d4-122">To import use the following steps:</span></span>

- <span data-ttu-id="757d4-123">Sélectionner le  >  **Gestionnaire de package** Windows</span><span class="sxs-lookup"><span data-stu-id="757d4-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="757d4-124">Sélectionner **Mixed Reality Toolkit Foundation**</span><span class="sxs-lookup"><span data-stu-id="757d4-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="757d4-125">Localiser les **ressources système** de la scène dans la section **exemples**</span><span class="sxs-lookup"><span data-stu-id="757d4-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importer des ressources système de scène](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="757d4-127">Sélectionner **Importer**</span><span class="sxs-lookup"><span data-stu-id="757d4-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="757d4-128">Fichiers de ressources (. pour Unity)</span><span class="sxs-lookup"><span data-stu-id="757d4-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="757d4-129">Si le dossier SceneSystemResources a été supprimé ou a été désélectionné lors de l’importation, il peut être récupéré en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="757d4-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="757d4-130">Sélectionner le package  >    >  **personnalisé** du package d’importation de ressources</span><span class="sxs-lookup"><span data-stu-id="757d4-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="757d4-131">Ouvrir le package **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="757d4-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="757d4-132">S’assurer que les options **services/SceneSystem/SceneSystemResources** et toutes les options enfants sont sélectionnées</span><span class="sxs-lookup"><span data-stu-id="757d4-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Réimporter les ressources système de la scène](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="757d4-134">Sélectionner **Importer**</span><span class="sxs-lookup"><span data-stu-id="757d4-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="757d4-135">Comment utiliser le système de scène</span><span class="sxs-lookup"><span data-stu-id="757d4-135">How to use the scene system</span></span>

- [<span data-ttu-id="757d4-136">Types de scènes</span><span class="sxs-lookup"><span data-stu-id="757d4-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="757d4-137">Chargement de scènes de contenu</span><span class="sxs-lookup"><span data-stu-id="757d4-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="757d4-138">Surveillance du chargement du contenu</span><span class="sxs-lookup"><span data-stu-id="757d4-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="757d4-139">Chargement de scène d’éclairage</span><span class="sxs-lookup"><span data-stu-id="757d4-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="757d4-140">Paramètres de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="757d4-140">Editor settings</span></span>

<span data-ttu-id="757d4-141">Par défaut, le système de scène applique plusieurs comportements dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="757d4-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="757d4-142">Si vous trouvez l’un de ces comportements, vous pouvez le désactiver dans la section paramètres de l' **éditeur** de votre profil système de scène.</span><span class="sxs-lookup"><span data-stu-id="757d4-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="757d4-143">`Editor Manage Build Settings:` Si la valeur est true, le service met automatiquement à jour vos paramètres de build, garantissant ainsi que toutes les scènes de gestion, d’éclairage et de contenu sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="757d4-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="757d4-144">Désactivez cette opération si vous souhaitez un contrôle total sur les paramètres de Build.</span><span class="sxs-lookup"><span data-stu-id="757d4-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="757d4-145">`Editor Enforce Scene Order:` Si la valeur est true, le service s’assure que la scène Manager est affichée en premier dans la hiérarchie de la scène, suivie de Lighting, puis du contenu.</span><span class="sxs-lookup"><span data-stu-id="757d4-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="757d4-146">Désactivez cette opération si vous souhaitez un contrôle total sur la hiérarchie des scènes.</span><span class="sxs-lookup"><span data-stu-id="757d4-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="757d4-147">`Editor Manage Loaded Scenes:` Si la valeur est true, le service s’assure que le gestionnaire, le contenu et les scènes d’éclairage sont toujours chargés.</span><span class="sxs-lookup"><span data-stu-id="757d4-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="757d4-148">Désactivez si vous souhaitez un contrôle total sur les scènes chargées dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="757d4-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="757d4-149">`Editor Enforce Lighting Scene Types:` Si la valeur est true, le service garantit que seuls les composants liés à l’éclairage définis dans `PermittedLightingSceneComponentTypes` sont autorisés dans les scènes d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="757d4-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="757d4-150">Désactivez si vous souhaitez un contrôle total sur le contenu des scènes d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="757d4-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Paramètres de l’éditeur système de scène](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
