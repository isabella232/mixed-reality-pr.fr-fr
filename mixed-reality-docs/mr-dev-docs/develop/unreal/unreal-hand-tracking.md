---
title: Suivi de la main dans Unreal
description: Découvrez comment utiliser les entrées de suivi manuel, les maillages de pose et de main, ainsi que les animations de liens dynamiques dans les applications de réalité mixte.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, suivi manuel, non réel, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: ea4ba3ad5905e899eae474e4d571585fef77c0c2
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117653"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="6e002-104">Suivi de la main dans Unreal</span><span class="sxs-lookup"><span data-stu-id="6e002-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="6e002-105">Le système de suivi de la main utilise les paumes et les doigts d’une personne comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6e002-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="6e002-106">Les données sur la position et la rotation de chaque doigt, le Palm entier et les gestes manuel sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="6e002-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="6e002-107">À partir de 4,26, le suivi manuel est basé sur le plug-in HeadMountedDisplay et utilise une API commune sur l’ensemble des plateformes et appareils XR.</span><span class="sxs-lookup"><span data-stu-id="6e002-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="6e002-108">Les fonctionnalités sont les mêmes pour les systèmes Windows Mixed Reality et OpenXR.</span><span class="sxs-lookup"><span data-stu-id="6e002-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="6e002-109">Poser à la main</span><span class="sxs-lookup"><span data-stu-id="6e002-109">Hand pose</span></span>

<span data-ttu-id="6e002-110">La pose de main vous permet de suivre et d’utiliser les mains et les doigts de vos utilisateurs comme entrée, qui sont accessibles à la fois dans les plans et C++.</span><span class="sxs-lookup"><span data-stu-id="6e002-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="6e002-111">L’API inréelle envoie les données sous forme de système de coordonnées, avec les battements synchronisés avec le moteur inréel.</span><span class="sxs-lookup"><span data-stu-id="6e002-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![Squelette de main](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="6e002-113">Animation de lien dynamique à la main</span><span class="sxs-lookup"><span data-stu-id="6e002-113">Hand Live Link Animation</span></span>

<span data-ttu-id="6e002-114">Les poses de main sont exposées à l’animation à l’aide du [plug-in Live Link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="6e002-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="6e002-115">Si les plug-ins Windows Mixed Reality et Live Link sont activés :</span><span class="sxs-lookup"><span data-stu-id="6e002-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="6e002-116">Sélectionnez **fenêtre > lien dynamique** pour ouvrir la fenêtre de l’éditeur de liens actifs.</span><span class="sxs-lookup"><span data-stu-id="6e002-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="6e002-117">Sélectionner la **source** et activer la source de suivi de la **main Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="6e002-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Source de la liaison dynamique](images/unreal/live-link-source.png)

<span data-ttu-id="6e002-119">Une fois que vous avez activé la source et ouvert une ressource d’animation, développez la section **animation** sous l’onglet Aperçu de la **scène** . vous pouvez également voir d’autres options.</span><span class="sxs-lookup"><span data-stu-id="6e002-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Animation des liens dynamiques](images/unreal/live-link-animation.png)

<span data-ttu-id="6e002-121">La hiérarchie d’animation manuelle est la même que dans `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="6e002-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="6e002-122">L’animation peut être reciblée à l’aide de **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span><span class="sxs-lookup"><span data-stu-id="6e002-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Animation de lien dynamique 2](images/unreal/live-link-animation2.png)

<span data-ttu-id="6e002-124">Elle peut également être sous-classée dans l’éditeur :</span><span class="sxs-lookup"><span data-stu-id="6e002-124">It can also be subclassed in the editor:</span></span>

![Remappage de liaison dynamique](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="6e002-126">Maille manuelle</span><span class="sxs-lookup"><span data-stu-id="6e002-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="6e002-127">Maille de main en tant que géométrie suivie</span><span class="sxs-lookup"><span data-stu-id="6e002-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e002-128">L’obtention de maillages de main en tant que géométrie suivie dans OpenXR vous oblige à appeler **Set use main Mesh** avec la **géométrie de suivi activée**.</span><span class="sxs-lookup"><span data-stu-id="6e002-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="6e002-129">Pour activer ce mode, vous devez appeler **Set use main Mesh** avec **Geometry de suivi activé**:</span><span class="sxs-lookup"><span data-stu-id="6e002-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![Plan de la lecture de début d’événement connecté pour définir la fonction de maillage à la main avec le mode de géométrie de suivi activé](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="6e002-131">Il n’est pas possible d’activer les deux modes en même temps.</span><span class="sxs-lookup"><span data-stu-id="6e002-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="6e002-132">Si vous en activez un, l’autre est automatiquement désactivée.</span><span class="sxs-lookup"><span data-stu-id="6e002-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="6e002-133">Accès aux données de maillage de la main</span><span class="sxs-lookup"><span data-stu-id="6e002-133">Accessing Hand Mesh Data</span></span>

![Maille manuelle](images/unreal/hand-mesh.png)

<span data-ttu-id="6e002-135">Avant de pouvoir accéder aux données de maillage manuel, vous devez :</span><span class="sxs-lookup"><span data-stu-id="6e002-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="6e002-136">Sélectionnez votre ressource **ARSessionConfig** , développez les **paramètres AR-> World Mapping** Settings, puis cochez la case **générer des données de maillage à partir de la géométrie suivie**.</span><span class="sxs-lookup"><span data-stu-id="6e002-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="6e002-137">Voici les paramètres de maillage par défaut :</span><span class="sxs-lookup"><span data-stu-id="6e002-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="6e002-138">Utiliser les données de maillage pour l’occlusion</span><span class="sxs-lookup"><span data-stu-id="6e002-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="6e002-139">Générer une collision pour les données de maillage</span><span class="sxs-lookup"><span data-stu-id="6e002-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="6e002-140">Générer un maillage de navigation pour les données de maillage</span><span class="sxs-lookup"><span data-stu-id="6e002-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="6e002-141">Rendu des données de maillage dans le paramètre filaire – débogage qui affiche le maillage généré</span><span class="sxs-lookup"><span data-stu-id="6e002-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="6e002-142">Ces valeurs de paramètre sont utilisées comme maillage de mappage spatial et par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e002-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="6e002-143">Vous pouvez les modifier à tout moment dans des plans ou du code pour n’importe quelle maille.</span><span class="sxs-lookup"><span data-stu-id="6e002-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="6e002-144">Informations de référence sur l’API C++</span><span class="sxs-lookup"><span data-stu-id="6e002-144">C++ API Reference</span></span>
<span data-ttu-id="6e002-145">Utilisez `EEARObjectClassification` pour rechercher des valeurs de maillage de main dans tous les objets suivis.</span><span class="sxs-lookup"><span data-stu-id="6e002-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="6e002-146">Les délégués suivants sont appelés lorsque le système détecte tout objet suivi, y compris un maillage de main.</span><span class="sxs-lookup"><span data-stu-id="6e002-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="6e002-147">Assurez-vous que vos gestionnaires de délégués suivent la signature de la fonction ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="6e002-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="6e002-148">Vous pouvez accéder aux données de maillage par le biais des  `UARTrackedGeometry::GetUnderlyingMesh` éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6e002-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="6e002-149">Informations de référence sur l’API Blueprint</span><span class="sxs-lookup"><span data-stu-id="6e002-149">Blueprint API Reference</span></span>

<span data-ttu-id="6e002-150">Pour travailler avec des maillages de main dans des plans :</span><span class="sxs-lookup"><span data-stu-id="6e002-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="6e002-151">Ajouter un composant **ARTrackableNotify** à un acteur Blueprint</span><span class="sxs-lookup"><span data-stu-id="6e002-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Notification ARTrackable](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="6e002-153">Accédez au panneau des **Détails** et développez la section **événements** .</span><span class="sxs-lookup"><span data-stu-id="6e002-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![ARTrackable Notify 2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="6e002-155">Remplacer sur l’ajout/la mise à jour/suppression de la géométrie suivie avec les nœuds suivants dans votre graphique d’événements :</span><span class="sxs-lookup"><span data-stu-id="6e002-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Sur ARTrackable Notify](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="6e002-157">Visualisation de maillage manuel dans OpenXR</span><span class="sxs-lookup"><span data-stu-id="6e002-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="6e002-158">La méthode recommandée pour visualiser le maillage direct consiste à utiliser le plug-in XRVisualization de Epic avec le [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="6e002-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="6e002-159">Ensuite, dans l’éditeur de modèle, vous devez utiliser la fonction de **maille Set use main** du [plug-in OpenXR de Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal) avec l' **option XRVisualization activée** comme paramètre :</span><span class="sxs-lookup"><span data-stu-id="6e002-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![Plan de la lecture de début d’événement connecté pour définir la fonction de maillage à la main avec le mode xrvisualization activé](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="6e002-161">Pour gérer le processus de rendu, vous devez utiliser le **contrôleur de mouvement de rendu** de XRVisualization :</span><span class="sxs-lookup"><span data-stu-id="6e002-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![Plan de la fonction de données d’obtenir le contrôleur de mouvement connecté à la fonction de contrôle de mouvement de rendu](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="6e002-163">Résultat :</span><span class="sxs-lookup"><span data-stu-id="6e002-163">The result:</span></span>

![Image de la main numérique superposée sur une main humaine réelle](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="6e002-165">Si vous avez besoin de quelque chose de plus compliqué, par exemple en dessinant une maille avec un nuanceur personnalisé, vous devez obtenir les maillages sous la forme d’une géométrie suivie.</span><span class="sxs-lookup"><span data-stu-id="6e002-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="6e002-166">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="6e002-166">Hand rays</span></span>

<span data-ttu-id="6e002-167">La mise en place de la main fonctionne pour les interactions proches comme la saisie d’objets ou la pression sur les boutons.</span><span class="sxs-lookup"><span data-stu-id="6e002-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="6e002-168">Toutefois, vous devez parfois travailler avec des hologrammes éloignés de vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6e002-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="6e002-169">Cela peut être accompli avec des rayons de main, qui peuvent être utilisés comme périphériques de pointage à la fois dans le C++ et dans les plans.</span><span class="sxs-lookup"><span data-stu-id="6e002-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="6e002-170">Vous pouvez dessiner un rayon de votre main à un point éloigné et, avec une certaine aide du suivi de rayon inréel, sélectionner un hologramme qui n’est normalement pas accessible.</span><span class="sxs-lookup"><span data-stu-id="6e002-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="6e002-171">Étant donné que tous les résultats de fonction changent chaque frame, ils sont tous rendus accessibles.</span><span class="sxs-lookup"><span data-stu-id="6e002-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="6e002-172">Pour plus d’informations sur les fonctions pures et impures ou pouvant être appelées, consultez le Guide de l’utilisateur Blueprint sur les [fonctions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="6e002-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="6e002-173">Mouvements</span><span class="sxs-lookup"><span data-stu-id="6e002-173">Gestures</span></span>

<span data-ttu-id="6e002-174">HoloLens 2 effectue le suivi des mouvements spatiaux, ce qui signifie que vous pouvez capturer ces mouvements comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6e002-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="6e002-175">Le suivi des mouvements est basé sur un modèle d’abonnement.</span><span class="sxs-lookup"><span data-stu-id="6e002-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="6e002-176">Vous devez utiliser la fonction « configurer les gestes » pour indiquer à l’appareil les gestes que vous souhaitez suivre.  Vous trouverez plus d’informations sur les gestes dans le document sur l' [utilisation de base de HoloLens 2](/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="6e002-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="6e002-177">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="6e002-177">Next Development Checkpoint</span></span>

<span data-ttu-id="6e002-178">Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="6e002-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="6e002-179">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="6e002-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6e002-180">Ancres spatiales locales</span><span class="sxs-lookup"><span data-stu-id="6e002-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="6e002-181">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="6e002-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6e002-182">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="6e002-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="6e002-183">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="6e002-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>