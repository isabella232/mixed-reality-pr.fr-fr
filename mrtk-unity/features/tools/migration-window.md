---
title: Fenêtre de migration
description: Documentation sur la migration vers une mise à jour dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 8e03848097c313a518f638de591f692ab71f0985
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143874"
---
# <a name="migration-window"></a><span data-ttu-id="002d9-104">Fenêtre de migration</span><span class="sxs-lookup"><span data-stu-id="002d9-104">Migration window</span></span>

<span data-ttu-id="002d9-105">À mesure que le MRTK subit des modifications, certains composants peuvent être déconseillés et les remplacements seront introduits.</span><span class="sxs-lookup"><span data-stu-id="002d9-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="002d9-106">La fenêtre de migration est un outil qui permet aux utilisateurs de migrer automatiquement un sous-ensemble de ces composants déconseillés vers les nouveaux remplacements.</span><span class="sxs-lookup"><span data-stu-id="002d9-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Fenêtre de migration](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="002d9-108">Usage</span><span class="sxs-lookup"><span data-stu-id="002d9-108">Usage</span></span>

<span data-ttu-id="002d9-109">Pour ouvrir la fenêtre, sélectionnez la fenêtre de migration utilitaires d’outils de *réalité mixte*  >    >  .</span><span class="sxs-lookup"><span data-stu-id="002d9-109">To open the window, select *Mixed Reality Toolkit* > *Utilities* > *Migration Window*.</span></span> <span data-ttu-id="002d9-110">Une fois la fenêtre de migration ouverte, les onglets de navigation du mode de sélection peuvent être activés en choisissant l’implémentation spécifique au composant du gestionnaire de migration.</span><span class="sxs-lookup"><span data-stu-id="002d9-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Modes de sélection de la migration](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="002d9-112">Mode Objet</span><span class="sxs-lookup"><span data-stu-id="002d9-112">Object mode</span></span>

<span data-ttu-id="002d9-113">La sélection de l’onglet objets Active le champ objet à l’emplacement où l’utilisateur peut glisser-déplacer des objets de jeu à partir de la scène actuellement ouverte ou prefabs à partir du dossier du projet à migrer.</span><span class="sxs-lookup"><span data-stu-id="002d9-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="002d9-114">Le fait d’appuyer sur le bouton supprimer *(-)* affiché sur le côté droit de l’objet répertorié supprime l’objet de la liste de sélection.</span><span class="sxs-lookup"><span data-stu-id="002d9-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="002d9-115">Une fois que tous les objets souhaités figurent dans la liste, le fait d’appuyer sur le bouton *migrer* applique les modifications requises par l’implémentation du gestionnaire de migration choisi à tous les composants de la sélection qui correspondent à l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="002d9-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Migration de la sélection](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="002d9-117">Mode scène</span><span class="sxs-lookup"><span data-stu-id="002d9-117">Scene mode</span></span>

<span data-ttu-id="002d9-118">Permet à l’utilisateur de faire glisser et déposer des ressources de scène contenant des objets à migrer.</span><span class="sxs-lookup"><span data-stu-id="002d9-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Sélection de scènes pour la migration](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="002d9-120">Mode projet</span><span class="sxs-lookup"><span data-stu-id="002d9-120">Project mode</span></span>

<span data-ttu-id="002d9-121">Le fait d’appuyer sur le bouton *migrer* met à jour le composant ciblé par l’implémentation du gestionnaire de migration pour tous les prefabs et scènes du projet.</span><span class="sxs-lookup"><span data-stu-id="002d9-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migration d’un projet complet](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="002d9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="002d9-123">See also</span></span>

- [<span data-ttu-id="002d9-124">Mise à jour à partir de versions antérieures</span><span class="sxs-lookup"><span data-stu-id="002d9-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="002d9-125">Versions de Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="002d9-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="002d9-126">Feuille de route MRTK</span><span class="sxs-lookup"><span data-stu-id="002d9-126">MRTK roadmap</span></span>](../../roadmap.md)
