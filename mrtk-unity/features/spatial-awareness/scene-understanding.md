---
title: Compréhension des scènes
description: décrit la compréhension des scènes dans MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, compréhension des scènes
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143879"
---
# <a name="scene-understanding"></a><span data-ttu-id="71a93-104">Compréhension des scènes</span><span class="sxs-lookup"><span data-stu-id="71a93-104">Scene Understanding</span></span>

<span data-ttu-id="71a93-105">La compréhension de la [scène](/windows/mixed-reality/scene-understanding) retourne une représentation sémantique des entités de scène ainsi que leurs formes géométriques sur __hololens 2__ (la 1re génération de hololens n’est pas prise en charge).</span><span class="sxs-lookup"><span data-stu-id="71a93-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="71a93-106">Voici quelques cas d’utilisation attendus de cette technologie :</span><span class="sxs-lookup"><span data-stu-id="71a93-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="71a93-107">Placer des objets sur la surface la plus proche d’un certain type (par exemple, un mur et un plancher)</span><span class="sxs-lookup"><span data-stu-id="71a93-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="71a93-108">Construire NAV-maille pour les jeux de style plateforme</span><span class="sxs-lookup"><span data-stu-id="71a93-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="71a93-109">Fournir une géométrie conviviale du moteur physique sous forme de quatre cœurs</span><span class="sxs-lookup"><span data-stu-id="71a93-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="71a93-110">Accélérez le développement en évitant d’avoir à écrire des algorithmes similaires</span><span class="sxs-lookup"><span data-stu-id="71a93-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="71a93-111">La compréhension des scènes est disponible sous la forme d’une fonctionnalité __expérimentale__ démarrant à partir de MRTK 2,6.</span><span class="sxs-lookup"><span data-stu-id="71a93-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="71a93-112">Il est intégré à MRTK en tant qu' [Observateur spatial](spatial-awareness-getting-started.md#register-observers) appelé [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="71a93-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="71a93-113">La compréhension des scènes fonctionne avec le pipeline XR hérité et le pipeline du kit de développement logiciel (SDK) XR.</span><span class="sxs-lookup"><span data-stu-id="71a93-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="71a93-114">Dans les deux cas, `WindowsSceneUnderstandingObserver` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="71a93-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="71a93-115">Vue d’ensemble de l’observateur</span><span class="sxs-lookup"><span data-stu-id="71a93-115">Observer overview</span></span>

<span data-ttu-id="71a93-116">Lorsque vous y êtes invité, le [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) retournera [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) avec des attributs utiles pour que l’application comprenne son environnement.</span><span class="sxs-lookup"><span data-stu-id="71a93-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="71a93-117">La fréquence d’observation, le type d’objet retourné (par exemple, Wall, Floor) et d’autres comportements observateur dépendent de la configuration de l’observateur via le profil.</span><span class="sxs-lookup"><span data-stu-id="71a93-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="71a93-118">Par exemple, si le masque d’occlusion est souhaité, l’observateur doit être configuré pour générer des Quad.</span><span class="sxs-lookup"><span data-stu-id="71a93-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="71a93-119">La scène observée peut être enregistrée en tant que fichier sérialisé pouvant être chargée ultérieurement pour recréer la scène en mode de lecture de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="71a93-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="71a93-120">Programme d’installation</span><span class="sxs-lookup"><span data-stu-id="71a93-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71a93-121">La compréhension de la scène est uniquement prise en charge sur HoloLens 2 et Unity 2019,4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="71a93-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="71a93-122">Vérifiez que la plateforme est définie sur UWP dans les paramètres de génération.</span><span class="sxs-lookup"><span data-stu-id="71a93-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="71a93-123">Procurez-vous le package de compréhension de scène via l’outil de la [fonctionnalité de réalité mixte](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="71a93-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="71a93-124">Utilisation de la compréhension des scènes</span><span class="sxs-lookup"><span data-stu-id="71a93-124">Using Scene Understanding</span></span>

<span data-ttu-id="71a93-125">La façon la plus rapide de prendre en main la compréhension des scènes consiste à consulter l’exemple de scène.</span><span class="sxs-lookup"><span data-stu-id="71a93-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="71a93-126">Exemple de scène de vision</span><span class="sxs-lookup"><span data-stu-id="71a93-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="71a93-127">Dans Unity, utilisez l’Explorateur de projets pour ouvrir le fichier de scène dans `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` et appuyez sur Play !</span><span class="sxs-lookup"><span data-stu-id="71a93-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71a93-128">Lors de l’utilisation de l’outil de fonctionnalité de réalité mixte ou de l’importation via UPM, importez l’exemple de démonstrations-SpatialAwareness avant d’importer l’exemple expérimental-SceneUnderstanding en raison d’un problème de dépendance.</span><span class="sxs-lookup"><span data-stu-id="71a93-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="71a93-129">Pour plus d’informations, consultez [ce problème GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) .</span><span class="sxs-lookup"><span data-stu-id="71a93-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="71a93-130">La scène illustre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="71a93-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="71a93-131">Visualisation des objets de scène observés avec l’interface utilisateur de l’application pour la configuration de l’observateur</span><span class="sxs-lookup"><span data-stu-id="71a93-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="71a93-132">Exemple de `DemoSceneUnderstandingController` script qui montre comment modifier les paramètres observateur et écouter les événements pertinents</span><span class="sxs-lookup"><span data-stu-id="71a93-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="71a93-133">Enregistrement des données de scène sur un appareil pour un développement hors connexion</span><span class="sxs-lookup"><span data-stu-id="71a93-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="71a93-134">Chargement des données de scène précédemment enregistrées (fichiers. bytes) pour prendre en charge le flux de travail de développement dans l’éditeur</span><span class="sxs-lookup"><span data-stu-id="71a93-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="71a93-135">L’exemple de scène est basé sur le pipeline XR hérité.</span><span class="sxs-lookup"><span data-stu-id="71a93-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="71a93-136">Si vous utilisez le pipeline du kit de développement logiciel (SDK) XR, vous devez modifier les profils en conséquence.</span><span class="sxs-lookup"><span data-stu-id="71a93-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="71a93-137">Le profil de système de sensibilisation spatiale fourni ( `DemoSceneUnderstandingSystemProfile` ) et la scène comprenant les profils d’observateur ( `DefaultSceneUnderstandingObserverProfile` et `DemoSceneUnderstandingObserverProfile` ) fonctionnent pour les deux pipelines.</span><span class="sxs-lookup"><span data-stu-id="71a93-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="71a93-138">Configuration du service Observateur</span><span class="sxs-lookup"><span data-stu-id="71a93-138">Configuring the observer service</span></span>

<span data-ttu-id="71a93-139">Sélectionnez l’objet de jeu « MixedRealityToolkit » et vérifiez l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="71a93-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![emplacement de compréhension de la scène dans la hiérarchie](../images/spatial-awareness/MRTKHierarchy.png)

![Emplacement MRTK dans Inspector](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="71a93-142">Ces options permettent de configurer le `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="71a93-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="71a93-143">Exemple de script</span><span class="sxs-lookup"><span data-stu-id="71a93-143">Example script</span></span>

<span data-ttu-id="71a93-144">L’exemple de script _DemoSceneUnderstandingController. cs_ illustre les principaux concepts de l’utilisation du service de vision de scène.</span><span class="sxs-lookup"><span data-stu-id="71a93-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="71a93-145">Abonnement à des événements de compréhension de scène</span><span class="sxs-lookup"><span data-stu-id="71a93-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="71a93-146">Gestion des événements de compréhension de scène</span><span class="sxs-lookup"><span data-stu-id="71a93-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="71a93-147">Configuration de `WindowsSceneUnderstandingObserver` au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="71a93-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="71a93-148">Les basculements sur le panneau de la scène modifient le comportement de Scene Understanding observer en appelant des fonctions publiques de cet exemple de script.</span><span class="sxs-lookup"><span data-stu-id="71a93-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="71a93-149">L’activation d' *instancier Prefabs*, démontrera la création d’objets qui se dimensionnent pour s’adapter à tous les [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), rassemblés correctement sous un objet parent.</span><span class="sxs-lookup"><span data-stu-id="71a93-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![options du contrôleur de démonstration](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="71a93-151">Notes d’application générées</span><span class="sxs-lookup"><span data-stu-id="71a93-151">Built app notes</span></span>

<span data-ttu-id="71a93-152">Générez et déployez sur HoloLens en mode standard.</span><span class="sxs-lookup"><span data-stu-id="71a93-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="71a93-153">Une fois exécuté, un certain nombre de boutons doivent s’afficher pour jouer avec les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="71a93-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="71a93-154">Notez qu’il existe un certain nombre de requêtes pour l’observateur.</span><span class="sxs-lookup"><span data-stu-id="71a93-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="71a93-155">Une configuration incorrecte d’un résultat de requête d’extraction dans votre charge utile d’événement ne contient pas les données attendues.</span><span class="sxs-lookup"><span data-stu-id="71a93-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="71a93-156">Par exemple, si l’un ne demande pas de quad, aucune texture de masque d’occlusion n’est alors présente.</span><span class="sxs-lookup"><span data-stu-id="71a93-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="71a93-157">De la même manière, aucun maillage universel ne s’affiche si l’observateur n’est pas configuré pour demander des maillages.</span><span class="sxs-lookup"><span data-stu-id="71a93-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="71a93-158">Le `DemoSceneUnderstandingController` script prend en charge certaines de ces dépendances, mais pas toutes.</span><span class="sxs-lookup"><span data-stu-id="71a93-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="71a93-159">Les fichiers de scène enregistrés sont accessibles via le portail de l' [appareil](/windows/mixed-reality/using-the-windows-device-portal) à l’adresse `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="71a93-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="71a93-160">Ces fichiers de scène peuvent être utilisés dans l’éditeur en les spécifiant dans le profil d’observateur trouvé dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="71a93-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Emplacement du fichier d’octets dans le portail de l’appareil](../images/spatial-awareness/BytesInDevicePortal.png)

![Octets de scène sérialisés dans l’observateur](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="71a93-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71a93-163">See Also</span></span>

* [<span data-ttu-id="71a93-164">Vue d’ensemble du mappage spatial WMR</span><span class="sxs-lookup"><span data-stu-id="71a93-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="71a93-165">Vue d’ensemble du mappage spatial WMR</span><span class="sxs-lookup"><span data-stu-id="71a93-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)