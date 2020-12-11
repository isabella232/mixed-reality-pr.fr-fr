---
title: Ancres spatiales locales dans Unreal
description: Guide d’utilisation des ancres spatiales dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, ancres spatiales, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: b517b1d89ddf7a35864db45a17336f4493816526
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609630"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="d0959-104">Ancres spatiales locales dans Unreal</span><span class="sxs-lookup"><span data-stu-id="d0959-104">Local Spatial Anchors in Unreal</span></span>

<span data-ttu-id="d0959-105">Les ancres spatiales enregistrent les hologrammes en place dans l’espace réel entre les sessions d’application comme des **ARPins**.</span><span class="sxs-lookup"><span data-stu-id="d0959-105">Spatial anchors save holograms in real-world space between application sessions as **ARPin** s.</span></span> <span data-ttu-id="d0959-106">Une fois enregistrés dans le magasin d’ancres HoloLens, les ARPins peuvent être chargés dans de futures sessions et constituent une option de secours idéale en l’absence de connectivité Internet.</span><span class="sxs-lookup"><span data-stu-id="d0959-106">Once saved in the HoloLens' anchor store, ARPin's can be loaded in future sessions and are an ideal fallback option when there's no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="d0959-107">Les fonctions des ancres d’UE 4.25 sont obsolètes dans 4.26 et doivent être remplacées par des fonctions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="d0959-107">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d0959-108">Les ancres locales sont stockées sur l’appareil, alors que les ancres spatiales Azure sont stockées dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="d0959-108">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="d0959-109">Si vous envisagez d’utiliser les services cloud Azure pour stocker vos ancres, nous avons créé un guide qui vous aidera à intégrer [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="d0959-109">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="d0959-110">Notez que vous pouvez avoir des ancres locales et Azure dans le même projet sans conflit.</span><span class="sxs-lookup"><span data-stu-id="d0959-110">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="d0959-111">Vérification du magasin d’ancres</span><span class="sxs-lookup"><span data-stu-id="d0959-111">Checking the anchor store</span></span>

<span data-ttu-id="d0959-112">Avant d’enregistrer ou de charger des ancres, vous avez besoin de vérifier si le magasin d’ancres est prêt.</span><span class="sxs-lookup"><span data-stu-id="d0959-112">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="d0959-113">Tout appel d’une des fonctions d’ancrage HoloLens échoue si le magasin d’ancres n’est pas prêt.</span><span class="sxs-lookup"><span data-stu-id="d0959-113">Calling any of the HoloLens anchor functions before the anchor store is ready won't succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="d0959-114">Enregistrement des ancres</span><span class="sxs-lookup"><span data-stu-id="d0959-114">Saving anchors</span></span>

<span data-ttu-id="d0959-115">Quand l’application a un composant que vous avez besoin de relier au monde réel, ce composant peut être enregistré dans le magasin d’ancres avec la séquence suivante :</span><span class="sxs-lookup"><span data-stu-id="d0959-115">Once the application has a component you need to pin to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="d0959-116">Décomposons cette séquence :</span><span class="sxs-lookup"><span data-stu-id="d0959-116">Breaking this down:</span></span>
1. <span data-ttu-id="d0959-117">Générez un acteur à un emplacement connu.</span><span class="sxs-lookup"><span data-stu-id="d0959-117">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="d0959-118">Créez un **ARPin** avec cet emplacement et un nom basé sur la classe de l’acteur.</span><span class="sxs-lookup"><span data-stu-id="d0959-118">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="d0959-119">Ajoutez l’acteur au **ARPin** et enregistrez le repère dans le magasin d’ancres HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d0959-119">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="d0959-120">Le nom d’ancre que vous choisissez doit être unique. Dans cet exemple, il s’agit de l’horodatage actuel.</span><span class="sxs-lookup"><span data-stu-id="d0959-120">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="d0959-121">Si l’ancre est correctement enregistrée dans le magasin d’ancres, vous pouvez la voir dans le portail d’appareil HoloLens sous **System > Map Manager > Anchor Files Saved On Device**.</span><span class="sxs-lookup"><span data-stu-id="d0959-121">If the anchor is successfully saved to the anchor store, you can see it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="d0959-122">Chargement des ancres</span><span class="sxs-lookup"><span data-stu-id="d0959-122">Loading anchors</span></span>

<span data-ttu-id="d0959-123">Au démarrage d’une application, vous pouvez utiliser le blueprint ci-dessous pour rétablir les composants à leurs positions d’ancrage :</span><span class="sxs-lookup"><span data-stu-id="d0959-123">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="d0959-124">Décomposons cette séquence :</span><span class="sxs-lookup"><span data-stu-id="d0959-124">Breaking this down:</span></span>
1. <span data-ttu-id="d0959-125">Effectuez une itération sur toutes les ancres du magasin d’ancres.</span><span class="sxs-lookup"><span data-stu-id="d0959-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="d0959-126">Générez un acteur au niveau de l’identité.</span><span class="sxs-lookup"><span data-stu-id="d0959-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="d0959-127">Épinglez cet acteur au **ARPin** à partir du magasin d’ancres.</span><span class="sxs-lookup"><span data-stu-id="d0959-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="d0959-128">Il est important de générer l’acteur au niveau de l’identité, car l’ancre est chargée de repositionner l’hologramme dans l’environnement selon l’emplacement auquel il a été enregistré.</span><span class="sxs-lookup"><span data-stu-id="d0959-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="d0959-129">Toute transformation ajoutée ici va ajouter un décalage à l’ancre.</span><span class="sxs-lookup"><span data-stu-id="d0959-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="d0959-130">L’ID de l’ancre est également demandé afin que différents acteurs puissent être générés en fonction du nom enregistré de l’ancre.</span><span class="sxs-lookup"><span data-stu-id="d0959-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="d0959-131">Suppression des ancres</span><span class="sxs-lookup"><span data-stu-id="d0959-131">Removing anchors</span></span> 

<span data-ttu-id="d0959-132">Lorsque vous n’avez plus besoin d’une ancre, vous pouvez l’effacer individuellement ou effacer la totalité du magasin d’ancres avec les composants **Remove ARPin from WMRAnchor Store** et **Remove All ARPins from WMRAnchor Store**.</span><span class="sxs-lookup"><span data-stu-id="d0959-132">When you're done with an anchor, you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="d0959-133">N’oubliez pas que les ancres spatiales sont encore en version bêta, donc n’hésitez pas à vous tenir au courant des dernières informations et fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d0959-133">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d0959-134">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="d0959-134">Next Development Checkpoint</span></span>

<span data-ttu-id="d0959-135">Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous explorez actuellement les composants de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="d0959-135">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="d0959-136">À partir d’ici, vous pouvez passer au composant suivant :</span><span class="sxs-lookup"><span data-stu-id="d0959-136">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="d0959-137">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d0959-137">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="d0959-138">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="d0959-138">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d0959-139">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="d0959-139">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="d0959-140">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="d0959-140">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0959-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0959-141">See also</span></span>
* [<span data-ttu-id="d0959-142">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d0959-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="d0959-143">Ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="d0959-143">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="d0959-144">Systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="d0959-144">Coordinate systems</span></span>](../../design/coordinate-systems.md)
