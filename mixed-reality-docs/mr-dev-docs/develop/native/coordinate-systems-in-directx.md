---
title: Systèmes de coordonnées dans DirectX
description: En savoir plus sur les systèmes de coordonnées dans DirectX et la réalité mixte avec des localisateurs spatiaux, des frames de référence et des ancres spatiales.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Réalité mixte, localisateur spatial, frame de référence spatiale, système de coordonnées spatiales, étape spatiale, exemple de code, stabilisation d’image, ancrage spatial, magasin d’ancrage spatial, perte de suivi, procédure pas à pas, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 055eff0bb04228cb0a19b9ea208bfc9c00ce2dbe
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006859"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="54ca2-104">Systèmes de coordonnées dans DirectX</span><span class="sxs-lookup"><span data-stu-id="54ca2-104">Coordinate systems in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="54ca2-105">Cet article s’applique aux API natives WinRT héritées.</span><span class="sxs-lookup"><span data-stu-id="54ca2-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="54ca2-106">Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="54ca2-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="54ca2-107">Les [systèmes de coordonnées](../../design/coordinate-systems.md) constituent la base de la compréhension spatiale offerte par les API Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="54ca2-107">[Coordinate systems](../../design/coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="54ca2-108">Les appareils en VR ou monolocal d’aujourd’hui établissent un système de coordonnées principal pour leur espace suivi.</span><span class="sxs-lookup"><span data-stu-id="54ca2-108">Today's seated VR or single-room VR devices establish one primary coordinate system for their tracked space.</span></span> <span data-ttu-id="54ca2-109">Les appareils de réalité mixte, tels que HoloLens, sont conçus pour les environnements non définis volumineux, avec la découverte des appareils et l’apprentissage de son environnement à mesure que l’utilisateur parcourt.</span><span class="sxs-lookup"><span data-stu-id="54ca2-109">Mixed Reality devices like HoloLens are designed for large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="54ca2-110">L’appareil s’adapte à l’amélioration continue des connaissances sur les salles de l’utilisateur, mais génère des systèmes de coordonnées qui modifient leur relation les uns par rapport aux autres pendant la durée de vie des applications.</span><span class="sxs-lookup"><span data-stu-id="54ca2-110">The device adapts to continually improving knowledge about the user's rooms, but results in coordinate systems that change their relationship to one another over the apps lifetime.</span></span> <span data-ttu-id="54ca2-111">Windows Mixed Reality prend en charge un large éventail d’appareils, allant des casques immersifs intégrés à des châssis de référence universels.</span><span class="sxs-lookup"><span data-stu-id="54ca2-111">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="54ca2-112">Les extraits de code de cet article illustrent actuellement l’utilisation de C++/CX au lieu des/WinRT C++ conformes à C + +17, tels qu’ils sont utilisés dans le [modèle de projet holographique c++](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="54ca2-112">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="54ca2-113">Les concepts sont équivalents pour un projet C++/WinRT, bien que vous deviez traduire le code.</span><span class="sxs-lookup"><span data-stu-id="54ca2-113">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="54ca2-114">Systèmes de coordonnées spatiales dans Windows</span><span class="sxs-lookup"><span data-stu-id="54ca2-114">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="54ca2-115">Le type de cœur utilisé pour la raison des systèmes de coordonnées réels dans Windows est le <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="54ca2-115">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="54ca2-116">Une instance de ce type représente un système de coordonnées arbitraire, fournissant une méthode permettant d’obtenir des données de matrice de transformation que vous pouvez utiliser pour transformer deux systèmes de coordonnées sans comprendre les détails de chacun d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="54ca2-116">An instance of this type represents an arbitrary coordinate system, providing a method for getting transformation matrix data that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="54ca2-117">Les méthodes qui retournent des informations spatiales acceptent un paramètre SpatialCoordinateSystem pour vous permettre de choisir le système de coordonnées dans lequel elles sont les plus utiles pour que ces coordonnées soient retournées.</span><span class="sxs-lookup"><span data-stu-id="54ca2-117">Methods that return spatial information will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="54ca2-118">Les informations spatiales sont représentées par des points, des rayons ou des volumes dans l’environnement de l’utilisateur, et les unités de ces coordonnées sont toujours exprimées en mètres.</span><span class="sxs-lookup"><span data-stu-id="54ca2-118">Spatial information is represented as points, rays, or volumes in the user's surroundings, and the units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="54ca2-119">Un SpatialCoordinateSystem a une relation dynamique avec d’autres systèmes de coordonnées, y compris ceux qui représentent la position de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="54ca2-119">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="54ca2-120">À tout moment, l’appareil peut localiser certains systèmes de coordonnées et pas d’autres.</span><span class="sxs-lookup"><span data-stu-id="54ca2-120">At any point, the device can locate some coordinate systems and not others.</span></span> <span data-ttu-id="54ca2-121">Pour la plupart des systèmes de coordonnées, votre application doit être prête à gérer les périodes pendant lesquelles elles sont introuvables.</span><span class="sxs-lookup"><span data-stu-id="54ca2-121">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="54ca2-122">Votre application ne doit pas créer de SpatialCoordinateSystems directement, mais elle doit être utilisée via les API de perception.</span><span class="sxs-lookup"><span data-stu-id="54ca2-122">Your application shouldn't create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="54ca2-123">Il existe trois sources principales de systèmes de coordonnées dans les API de perception, chacune d’elles étant mappée à un concept décrit dans la page des [systèmes de coordonnées](../../design/coordinate-systems.md) :</span><span class="sxs-lookup"><span data-stu-id="54ca2-123">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](../../design/coordinate-systems.md) page:</span></span>
* <span data-ttu-id="54ca2-124">Pour obtenir une image de référence fixe, créez un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> ou obtenez-en un à partir du <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>actuel.</span><span class="sxs-lookup"><span data-stu-id="54ca2-124">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="54ca2-125">Pour obtenir une ancre spatiale, créez un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="54ca2-125">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="54ca2-126">Pour obtenir un cadre de référence attaché, créez un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="54ca2-126">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="54ca2-127">Tous les systèmes de coordonnées retournés par ces objets sont droitiers, avec + y vers le haut, + x vers la droite et + z vers l’arrière.</span><span class="sxs-lookup"><span data-stu-id="54ca2-127">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="54ca2-128">Vous pouvez vous souvenir de la direction vers laquelle pointe l’axe z positif en pointant les doigts de votre gauche ou de droite dans la direction x positive et en les plaçant dans la direction y positive.</span><span class="sxs-lookup"><span data-stu-id="54ca2-128">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="54ca2-129">La direction vers laquelle votre Thumb pointe, que ce soit vers vous ou en dehors, est la direction dans laquelle les points positifs de l’axe z pour ce système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="54ca2-129">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="54ca2-130">L’illustration suivante montre ces deux systèmes de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="54ca2-130">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="54ca2-131">![Systèmes de coordonnées à gauche et à droite](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="54ca2-131">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="54ca2-132">*Systèmes de coordonnées à gauche et à droite*</span><span class="sxs-lookup"><span data-stu-id="54ca2-132">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="54ca2-133">Utilisez la classe <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> pour créer une image jointe ou stationnaire de référence au démarrage dans un SpatialCoordinateSystem en fonction de la position HoloLens.</span><span class="sxs-lookup"><span data-stu-id="54ca2-133">Use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference to bootstrap into a SpatialCoordinateSystem based on the HoloLens position.</span></span> <span data-ttu-id="54ca2-134">Passez à la section suivante pour en savoir plus sur ce processus.</span><span class="sxs-lookup"><span data-stu-id="54ca2-134">Continue to the next section to learn more about this process.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="54ca2-135">Placer des hologrammes dans le monde à l’aide d’une étape spatiale</span><span class="sxs-lookup"><span data-stu-id="54ca2-135">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="54ca2-136">Le système de coordonnées pour les casques immersifs immersifs de la réalité Windows mixed est accessible à l’aide de la propriété statique <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference :: Current</a> .</span><span class="sxs-lookup"><span data-stu-id="54ca2-136">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="54ca2-137">Cette API fournit les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="54ca2-137">This API provides:</span></span>

* <span data-ttu-id="54ca2-138">Système de coordonnées</span><span class="sxs-lookup"><span data-stu-id="54ca2-138">A coordinate system</span></span>
* <span data-ttu-id="54ca2-139">Informations indiquant si le joueur est assis ou mobile</span><span class="sxs-lookup"><span data-stu-id="54ca2-139">Information about whether the player is seated or mobile</span></span>
* <span data-ttu-id="54ca2-140">Limite d’une zone sécurisée pour se déplacer si le joueur est mobile</span><span class="sxs-lookup"><span data-stu-id="54ca2-140">The boundary of a safe area for walking around if the player is mobile</span></span>
* <span data-ttu-id="54ca2-141">Indique si le casque est directionnel.</span><span class="sxs-lookup"><span data-stu-id="54ca2-141">An indication of whether the headset is directional.</span></span> 
* <span data-ttu-id="54ca2-142">Gestionnaire d’événements pour les mises à jour de la phase spatiale.</span><span class="sxs-lookup"><span data-stu-id="54ca2-142">An event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="54ca2-143">Tout d’abord, nous obtenons la phase spatiale et m’abonnons aux mises à jour :</span><span class="sxs-lookup"><span data-stu-id="54ca2-143">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="54ca2-144">Code pour **l’initialisation de la phase spatiale**</span><span class="sxs-lookup"><span data-stu-id="54ca2-144">Code for **Spatial stage initialization**</span></span>

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

<span data-ttu-id="54ca2-145">Dans la méthode OnCurrentChanged, votre application doit inspecter la phase spatiale et mettre à jour l’expérience du joueur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-145">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience.</span></span> <span data-ttu-id="54ca2-146">Dans cet exemple, nous fournissons une visualisation de la limite de la phase et de la position de départ spécifiée par l’utilisateur, ainsi que de la plage de la vue et de la plage de propriétés de déplacement de l’étape.</span><span class="sxs-lookup"><span data-stu-id="54ca2-146">In this example, we provide a visualization of the stage boundary and the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="54ca2-147">Nous revenons également à notre propre système de coordonnées stationnaires, lorsqu’une étape ne peut pas être fournie.</span><span class="sxs-lookup"><span data-stu-id="54ca2-147">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="54ca2-148">Code pour la **mise à jour de la phase spatiale**</span><span class="sxs-lookup"><span data-stu-id="54ca2-148">Code for **Spatial stage update**</span></span>

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

<span data-ttu-id="54ca2-149">L’ensemble des vertex qui définissent les limites de l’étape sont fournis dans l’ordre des aiguilles d’une montre.</span><span class="sxs-lookup"><span data-stu-id="54ca2-149">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="54ca2-150">Le shell Windows Mixed Reality dessine une clôture à la limite lorsque l’utilisateur l’approche, mais vous pouvez souhaiter triangulairer la zone à votre propre usage.</span><span class="sxs-lookup"><span data-stu-id="54ca2-150">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it, but you may want to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="54ca2-151">L’algorithme suivant peut être utilisé pour triangulairer la phase.</span><span class="sxs-lookup"><span data-stu-id="54ca2-151">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="54ca2-152">Code pour **triangulaire de la phase spatiale**</span><span class="sxs-lookup"><span data-stu-id="54ca2-152">Code for **Spatial stage triangularization**</span></span>

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="54ca2-153">Placez des hologrammes dans le monde à l’aide d’un cadre stationnaire de référence</span><span class="sxs-lookup"><span data-stu-id="54ca2-153">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="54ca2-154">La classe [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) représente une image de référence qui [reste stationnaire](../../design/coordinate-systems.md#stationary-frame-of-reference) par rapport à l’environnement de l’utilisateur au fur et à mesure que l’utilisateur se déplace.</span><span class="sxs-lookup"><span data-stu-id="54ca2-154">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](../../design/coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="54ca2-155">Ce cadre de référence établit une priorité pour maintenir les coordonnées stables près de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="54ca2-155">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="54ca2-156">L’une des principales utilisation d’un SpatialStationaryFrameOfReference consiste à agir comme système de coordonnées universelles sous-jacent dans un moteur de rendu lors du rendu d’hologrammes.</span><span class="sxs-lookup"><span data-stu-id="54ca2-156">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="54ca2-157">Pour obtenir un SpatialStationaryFrameOfReference, utilisez la classe [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) et appelez [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="54ca2-157">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="54ca2-158">À partir du code du modèle d’application holographique Windows :</span><span class="sxs-lookup"><span data-stu-id="54ca2-158">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="54ca2-159">Les frames de référence stationnaires sont conçus pour fournir une position la mieux adaptée par rapport à l’espace global.</span><span class="sxs-lookup"><span data-stu-id="54ca2-159">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="54ca2-160">Les positions individuelles dans ce frame de référence sont autorisées à dériver légèrement.</span><span class="sxs-lookup"><span data-stu-id="54ca2-160">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="54ca2-161">Cela est normal, car l’appareil en apprend davantage sur l’environnement.</span><span class="sxs-lookup"><span data-stu-id="54ca2-161">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="54ca2-162">Lorsque le positionnement précis des hologrammes individuels est requis, un SpatialAnchor doit être utilisé pour ancrer l’hologramme individuel à une position dans le monde réel (par exemple, un point que l’utilisateur indique d’avoir un intérêt particulier).</span><span class="sxs-lookup"><span data-stu-id="54ca2-162">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="54ca2-163">Les positions d’ancrage ne dérivent pas, mais peuvent être corrigées ; le point d’ancrage utilise la position corrigée à partir de l’image suivante, une fois la correction effectuée.</span><span class="sxs-lookup"><span data-stu-id="54ca2-163">Anchor positions don't drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="54ca2-164">Placer des hologrammes dans le monde à l’aide d’ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="54ca2-164">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="54ca2-165">Les [ancres spatiales](../../design/coordinate-systems.md#spatial-anchors) sont un excellent moyen de placer des hologrammes à un endroit précis dans le monde réel, le système garantissant que l’ancre reste en place au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="54ca2-165">[Spatial anchors](../../design/coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="54ca2-166">Cette rubrique explique comment créer et utiliser une ancre, et comment utiliser les données d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="54ca2-166">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="54ca2-167">Vous pouvez créer un SpatialAnchor à n’importe quelle position et orientation dans le SpatialCoordinateSystem de votre choix.</span><span class="sxs-lookup"><span data-stu-id="54ca2-167">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="54ca2-168">L’appareil doit être en mesure de localiser ce système de coordonnées pour le moment et le système ne doit pas avoir atteint sa limite d’ancrages spatiaux.</span><span class="sxs-lookup"><span data-stu-id="54ca2-168">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="54ca2-169">Une fois défini, le système de coordonnées d’un SpatialAnchor s’ajuste continuellement pour conserver la position et l’orientation précises de son emplacement initial.</span><span class="sxs-lookup"><span data-stu-id="54ca2-169">Once defined, the coordinate system of a SpatialAnchor adjusts continually to keep the precise position and orientation of its initial location.</span></span> <span data-ttu-id="54ca2-170">Vous pouvez ensuite utiliser ce SpatialAnchor pour afficher des hologrammes qui seront corrigés dans l’environnement de l’utilisateur à cet emplacement exact.</span><span class="sxs-lookup"><span data-stu-id="54ca2-170">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="54ca2-171">Les effets des ajustements qui maintiennent l’ancre sont agrandis à mesure que la distance entre l’ancrage augmente.</span><span class="sxs-lookup"><span data-stu-id="54ca2-171">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="54ca2-172">Vous devez éviter de rendre le contenu relatif à une ancre qui est supérieure à environ 3 mètres de l’origine de cette ancre.</span><span class="sxs-lookup"><span data-stu-id="54ca2-172">You should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="54ca2-173">La propriété [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) obtient un système de coordonnées qui vous permet de placer du contenu par rapport à l’ancre, avec une accélération appliquée lorsque l’appareil ajuste l’emplacement précis de l’ancre.</span><span class="sxs-lookup"><span data-stu-id="54ca2-173">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="54ca2-174">Utilisez la propriété [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) et l’événement [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) correspondant pour gérer ces réglages vous-même.</span><span class="sxs-lookup"><span data-stu-id="54ca2-174">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="54ca2-175">Conserver et partager des ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="54ca2-175">Persist and share spatial anchors</span></span>

<span data-ttu-id="54ca2-176">Vous pouvez conserver un SpatialAnchor localement à l’aide de la classe [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) , puis le récupérer dans une session d’application future sur le même appareil HoloLens.</span><span class="sxs-lookup"><span data-stu-id="54ca2-176">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="54ca2-177">En utilisant des <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a>, vous pouvez créer une ancre Cloud durable à partir d’un SpatialAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="54ca2-177">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="54ca2-178">En partageant une ancre spatiale commune sur plusieurs appareils, chaque utilisateur peut voir le contenu rendu relatif à cette ancre dans le même emplacement physique en temps réel.</span><span class="sxs-lookup"><span data-stu-id="54ca2-178">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location in real time.</span></span> 

<span data-ttu-id="54ca2-179">Vous pouvez également utiliser des <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour la persistance des hologrammes asynchrones sur les appareils HoloLens, iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="54ca2-179">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="54ca2-180">En partageant une ancre spatiale Cloud durable, plusieurs appareils peuvent observer le même hologramme persistant dans le temps, même si ces appareils ne sont pas présents simultanément.</span><span class="sxs-lookup"><span data-stu-id="54ca2-180">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="54ca2-181">Pour commencer à créer des expériences partagées dans votre application HoloLens, essayez le démarrage rapide de 5 minutes d' <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">ancrage spatial Azure HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="54ca2-181">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="54ca2-182">Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">créer et localiser des ancres sur HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="54ca2-182">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="54ca2-183">Les procédures pas à pas sont également disponibles pour <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android et iOS</a> , ce qui vous permet de partager les mêmes ancres sur tous les appareils.</span><span class="sxs-lookup"><span data-stu-id="54ca2-183">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="54ca2-184">Créer des SpatialAnchors pour le contenu holographique</span><span class="sxs-lookup"><span data-stu-id="54ca2-184">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="54ca2-185">Pour cet exemple de code, nous avons modifié le modèle d’application holographique Windows pour créer des ancres lorsque le geste **appuyé** est détecté.</span><span class="sxs-lookup"><span data-stu-id="54ca2-185">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="54ca2-186">Le cube est ensuite placé au point d’ancrage pendant la passe de rendu.</span><span class="sxs-lookup"><span data-stu-id="54ca2-186">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="54ca2-187">Étant donné que plusieurs ancres sont prises en charge par la classe d’assistance, nous pouvons placer autant de cubes que nous voulons utiliser cet exemple de code !</span><span class="sxs-lookup"><span data-stu-id="54ca2-187">Since multiple anchors are supported by the helper class, we can place as many cubes as we want to use this code sample!</span></span>

> [!NOTE]
> <span data-ttu-id="54ca2-188">Les ID des ancres sont des éléments que vous contrôlez dans votre application.</span><span class="sxs-lookup"><span data-stu-id="54ca2-188">The IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="54ca2-189">Dans cet exemple, nous avons créé un modèle d’affectation de noms qui est séquentiel en fonction du nombre d’ancres actuellement stockées dans la collection d’ancres de l’application.</span><span class="sxs-lookup"><span data-stu-id="54ca2-189">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="54ca2-190">Charger et mettre en cache de façon asynchrone SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="54ca2-190">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="54ca2-191">Voyons comment écrire une classe SampleSpatialAnchorHelper qui permet de gérer cette persistance, notamment :</span><span class="sxs-lookup"><span data-stu-id="54ca2-191">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="54ca2-192">Stockage d’une collection d’ancres en mémoire, indexées par une clé Platform :: String.</span><span class="sxs-lookup"><span data-stu-id="54ca2-192">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="54ca2-193">Chargement des ancres à partir du SpatialAnchorStore du système, qui est conservé distinct de la collection en mémoire locale.</span><span class="sxs-lookup"><span data-stu-id="54ca2-193">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="54ca2-194">Enregistrement de la collection en mémoire locale des ancres dans le SpatialAnchorStore quand l’application choisit de le faire.</span><span class="sxs-lookup"><span data-stu-id="54ca2-194">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="54ca2-195">Voici comment enregistrer des objets [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) dans [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="54ca2-195">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="54ca2-196">Lorsque la classe démarre, nous recherchons le SpatialAnchorStore de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="54ca2-196">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="54ca2-197">Cela implique des e/s système, car l’API charge le magasin d’ancrage, et cette API est rendue asynchrone afin que les e/s soient non bloquantes.</span><span class="sxs-lookup"><span data-stu-id="54ca2-197">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

<span data-ttu-id="54ca2-198">Vous disposez d’un SpatialAnchorStore que vous pouvez utiliser pour enregistrer les ancres.</span><span class="sxs-lookup"><span data-stu-id="54ca2-198">You'll be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="54ca2-199">Il s’agit d’un IMapView qui associe des valeurs de clés qui sont des chaînes, avec des valeurs de données qui sont SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="54ca2-199">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="54ca2-200">Dans notre exemple de code, nous le stockons dans une variable membre de classe privée qui est accessible par le biais d’une fonction publique de notre classe d’assistance.</span><span class="sxs-lookup"><span data-stu-id="54ca2-200">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="54ca2-201">N’oubliez pas de raccorder les événements de suspension/reprise pour enregistrer et charger le magasin d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="54ca2-201">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="54ca2-202">Enregistrer le contenu dans le magasin d’ancrage</span><span class="sxs-lookup"><span data-stu-id="54ca2-202">Save content to the anchor store</span></span>

<span data-ttu-id="54ca2-203">Lorsque le système interrompt votre application, vous devez enregistrer vos ancres spatiales dans le magasin d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="54ca2-203">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="54ca2-204">Vous pouvez également choisir d’enregistrer les ancres dans le magasin d’ancrage à d’autres moments, car vous en aurez besoin pour l’implémentation de votre application.</span><span class="sxs-lookup"><span data-stu-id="54ca2-204">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="54ca2-205">Lorsque vous êtes prêt à essayer d’enregistrer les ancres en mémoire dans le SpatialAnchorStore, vous pouvez parcourir votre collection et essayer d’enregistrer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="54ca2-205">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="54ca2-206">Charger le contenu à partir du magasin d’ancrage lorsque l’application reprend</span><span class="sxs-lookup"><span data-stu-id="54ca2-206">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="54ca2-207">Vous pouvez restaurer les ancres enregistrées dans le AnchorStore en les transférant du IMapView du magasin d’ancrage à votre propre base de données en mémoire de SpatialAnchors lorsque votre application reprend ou à tout moment.</span><span class="sxs-lookup"><span data-stu-id="54ca2-207">You can restore saved anchors in the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors when your app resumes or at any time.</span></span>

<span data-ttu-id="54ca2-208">Pour restaurer les ancres à partir du SpatialAnchorStore, restaurez chacune d’elles qui vous intéresse à votre propre collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="54ca2-208">To restore anchors from the SpatialAnchorStore, restore each one that you're interested in to your own in-memory collection.</span></span>

<span data-ttu-id="54ca2-209">Vous avez besoin de votre propre base de données en mémoire de SpatialAnchors pour associer des chaînes au SpatialAnchors que vous créez.</span><span class="sxs-lookup"><span data-stu-id="54ca2-209">You need your own in-memory database of SpatialAnchors to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="54ca2-210">Dans notre exemple de code, nous choisissons d’utiliser un Windows :: Foundation :: Collections :: IMap pour stocker les ancres, ce qui facilite l’utilisation de la même clé et de la même valeur de données pour SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="54ca2-210">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="54ca2-211">Une ancre qui est restaurée peut ne pas être localisable immédiatement.</span><span class="sxs-lookup"><span data-stu-id="54ca2-211">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="54ca2-212">Par exemple, il peut s’agir d’une ancre dans une salle distincte ou dans une construction différente.</span><span class="sxs-lookup"><span data-stu-id="54ca2-212">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="54ca2-213">Les ancres récupérées à partir du AnchorStore doivent être testées en vue de leur localisation avant de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="54ca2-213">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="54ca2-214">Dans cet exemple de code, nous récupérons toutes les ancres du AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="54ca2-214">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="54ca2-215">Ce n’est pas une condition requise. votre application peut tout aussi bien sélectionner et choisir un certain sous-ensemble d’ancres à l’aide de valeurs de clés de chaîne qui sont significatives pour votre implémentation.</span><span class="sxs-lookup"><span data-stu-id="54ca2-215">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="54ca2-216">Effacer le magasin d’ancrage, si nécessaire</span><span class="sxs-lookup"><span data-stu-id="54ca2-216">Clear the anchor store, when needed</span></span>

<span data-ttu-id="54ca2-217">Parfois, vous devez effacer l’état de l’application et écrire de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="54ca2-217">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="54ca2-218">Voici comment procéder avec [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="54ca2-218">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="54ca2-219">À l’aide de la classe d’assistance, il est presque inutile d’encapsuler la fonction Clear.</span><span class="sxs-lookup"><span data-stu-id="54ca2-219">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="54ca2-220">Nous choisissons cette opération dans notre exemple d’implémentation, car la responsabilité de la propriétaire de l’instance SpatialAnchorStore est attribuée à notre classe d’assistance.</span><span class="sxs-lookup"><span data-stu-id="54ca2-220">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="54ca2-221">Exemple : Association de systèmes de coordonnées d’ancrage à des systèmes de coordonnées de cadre de référence stationnaire</span><span class="sxs-lookup"><span data-stu-id="54ca2-221">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="54ca2-222">Supposons que vous disposiez d’une ancre et que vous vouliez associer un nom du système de coordonnées de votre ancre au SpatialStationaryReferenceFrame que vous utilisez déjà pour votre autre contenu.</span><span class="sxs-lookup"><span data-stu-id="54ca2-222">Let's say you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame you’re already using for your other content.</span></span> <span data-ttu-id="54ca2-223">Vous pouvez utiliser [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) pour obtenir une transformation du système de coordonnées de l’ancre à celle du cadre de référence fixe :</span><span class="sxs-lookup"><span data-stu-id="54ca2-223">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to get a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

<span data-ttu-id="54ca2-224">Ce processus est utile de deux manières :</span><span class="sxs-lookup"><span data-stu-id="54ca2-224">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="54ca2-225">Elle vous indique si les deux frames de référence peuvent être compris entre eux, et ;</span><span class="sxs-lookup"><span data-stu-id="54ca2-225">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="54ca2-226">Si c’est le cas, il vous fournit une transformation pour passer directement d’un système de coordonnées à l’autre.</span><span class="sxs-lookup"><span data-stu-id="54ca2-226">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="54ca2-227">Avec ces informations, vous comprenez la relation spatiale entre les objets entre les deux frames de référence.</span><span class="sxs-lookup"><span data-stu-id="54ca2-227">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="54ca2-228">Pour le rendu, vous pouvez souvent obtenir de meilleurs résultats en regroupant des objets en fonction de leur frame de référence ou de leur ancre d’origine.</span><span class="sxs-lookup"><span data-stu-id="54ca2-228">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="54ca2-229">Effectuez une passe de dessin distincte pour chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="54ca2-229">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="54ca2-230">Les matrices de vue sont plus précises pour les objets avec des transformations de modèle créées initialement à l’aide du même système de coordonnées.</span><span class="sxs-lookup"><span data-stu-id="54ca2-230">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="54ca2-231">Créer des hologrammes à l’aide d’une image de référence associée à un appareil</span><span class="sxs-lookup"><span data-stu-id="54ca2-231">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="54ca2-232">Il peut arriver que vous souhaitiez afficher un hologramme qui [reste attaché](../../design/coordinate-systems.md#attached-frame-of-reference) à l’emplacement de l’appareil, par exemple un panneau avec des informations de débogage ou un message d’information lorsque l’appareil est uniquement en mesure de déterminer son orientation et non sa position dans l’espace.</span><span class="sxs-lookup"><span data-stu-id="54ca2-232">There are times when you want to render a hologram that [remains attached](../../design/coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="54ca2-233">Pour ce faire, nous utilisons un cadre de référence attaché.</span><span class="sxs-lookup"><span data-stu-id="54ca2-233">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="54ca2-234">La classe SpatialLocatorAttachedFrameOfReference définit des systèmes de coordonnées, qui sont relatifs à l’appareil plutôt qu’au monde réel.</span><span class="sxs-lookup"><span data-stu-id="54ca2-234">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems, which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="54ca2-235">Ce cadre a un titre fixe par rapport à l’environnement de l’utilisateur qui pointe dans la direction vers laquelle l’utilisateur était confronté lorsque le frame de référence a été créé.</span><span class="sxs-lookup"><span data-stu-id="54ca2-235">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="54ca2-236">À partir de là, toutes les orientations dans ce frame de référence sont relatives à cet en-tête fixe, même lorsque l’utilisateur fait pivoter l’appareil.</span><span class="sxs-lookup"><span data-stu-id="54ca2-236">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="54ca2-237">Pour HoloLens, l’origine du système de coordonnées de ce frame se trouve au centre de rotation de la tête de l’utilisateur, de sorte que sa position n’est pas affectée par la rotation de la tête.</span><span class="sxs-lookup"><span data-stu-id="54ca2-237">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="54ca2-238">Votre application peut spécifier un décalage par rapport à ce point pour positionner les hologrammes devant l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-238">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="54ca2-239">Pour obtenir un SpatialLocatorAttachedFrameOfReference, utilisez la classe SpatialLocator et appelez CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="54ca2-239">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="54ca2-240">Cela s’applique à toute la plage d’appareils Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="54ca2-240">This applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="54ca2-241">Utiliser un cadre de référence attaché à l’appareil</span><span class="sxs-lookup"><span data-stu-id="54ca2-241">Use a reference frame attached to the device</span></span>

<span data-ttu-id="54ca2-242">Ces sections décrivent ce que nous avons modifié dans le modèle d’application holographique Windows pour activer un cadre de référence associé à un appareil à l’aide de cette API.</span><span class="sxs-lookup"><span data-stu-id="54ca2-242">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="54ca2-243">Cet hologramme « attaché » fonctionne avec les hologrammes fixes ou ancrés, et peut également être utilisé lorsque l’appareil est momentanément incapable de trouver sa position dans le monde.</span><span class="sxs-lookup"><span data-stu-id="54ca2-243">This "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="54ca2-244">Tout d’abord, nous avons modifié le modèle pour stocker un SpatialLocatorAttachedFrameOfReference au lieu d’un SpatialStationaryFrameOfReference :</span><span class="sxs-lookup"><span data-stu-id="54ca2-244">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="54ca2-245">À partir de **HolographicTagAlongSampleMain. h**:</span><span class="sxs-lookup"><span data-stu-id="54ca2-245">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="54ca2-246">À partir de **HolographicTagAlongSampleMain. cpp**:</span><span class="sxs-lookup"><span data-stu-id="54ca2-246">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="54ca2-247">Au cours de la mise à jour, nous obtenons désormais le système de coordonnées à l’horodatage obtenu à l’aide de la prédiction de cadre.</span><span class="sxs-lookup"><span data-stu-id="54ca2-247">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="54ca2-248">Obtenir une pose de pointeur spatial et suivre le point de regard de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="54ca2-248">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="54ca2-249">Nous souhaitons que notre exemple d’hologramme suive le [regard](../../design/gaze-and-commit.md)de l’utilisateur, de la même façon que le shell holographique peut suivre le regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-249">We want our example hologram to follow the user's [gaze](../../design/gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="54ca2-250">Pour cela, nous devons obtenir le SpatialPointerPose à partir du même horodatage.</span><span class="sxs-lookup"><span data-stu-id="54ca2-250">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="54ca2-251">Ce SpatialPointerPose contient les informations nécessaires pour positionner l’hologramme en fonction de l' [en-tête actuel de l’utilisateur](gaze-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="54ca2-251">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="54ca2-252">Pour le confort de l’utilisateur, nous utilisons l’interpolation linéaire (« Lerp ») pour lisser le changement de position sur une période donnée.</span><span class="sxs-lookup"><span data-stu-id="54ca2-252">For user comfort, we use linear interpolation ("lerp") to smooth the change in position over a period of time.</span></span> <span data-ttu-id="54ca2-253">L’utilisateur est plus à l’aise avec le verrouillage de l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="54ca2-253">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="54ca2-254">Lerping la position de la balise, le long de l’hologramme, nous permet également de stabiliser l’hologramme en amortissant le mouvement.</span><span class="sxs-lookup"><span data-stu-id="54ca2-254">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement.</span></span> <span data-ttu-id="54ca2-255">Si ce n’est pas le cas, l’utilisateur voit la gigue d’hologramme en raison de ce qui est normalement considéré comme étant des mouvements imperceptibles de la tête de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-255">If we didn't do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="54ca2-256">À partir de **StationaryQuadRenderer ::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="54ca2-256">From **StationaryQuadRenderer::PositionHologram**:</span></span>

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
><span data-ttu-id="54ca2-257">Dans le cas d’un panneau de débogage, vous pouvez choisir de repositionner l’hologramme sur le côté afin qu’il n’obstrue pas votre affichage.</span><span class="sxs-lookup"><span data-stu-id="54ca2-257">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it doesn't obstruct your view.</span></span> <span data-ttu-id="54ca2-258">Voici un exemple de ce que vous pouvez faire.</span><span class="sxs-lookup"><span data-stu-id="54ca2-258">Here's an example of how you might do that.</span></span>

<span data-ttu-id="54ca2-259">Pour **StationaryQuadRenderer ::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="54ca2-259">For **StationaryQuadRenderer::PositionHologram**:</span></span>

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="54ca2-260">Faire pivoter l’hologramme pour faire face à l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="54ca2-260">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="54ca2-261">Ce n’est pas suffisant pour positionner l’hologramme, qui est dans ce cas un quadruple. Nous devons également faire pivoter l’objet pour faire face à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-261">It isn't enough to position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="54ca2-262">Cette rotation se produit dans l’espace universel, car ce type de billboarding permet à l’hologramme de conserver une partie de l’environnement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-262">This rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="54ca2-263">L’affichage de l’espace d’affichage n’est pas aussi agréable, car l’hologramme est verrouillé à l’orientation de l’affichage ; dans ce cas, vous devez également interpoler entre les matrices de vue de gauche et de droite pour acquérir une transformation d’affichage de l’espace d’affichage qui n’interrompt pas le rendu stéréo.</span><span class="sxs-lookup"><span data-stu-id="54ca2-263">View-space billboarding isn't as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices to acquire a view-space billboard transform that doesn't disrupt stereo rendering.</span></span> <span data-ttu-id="54ca2-264">Ici, nous allons faire pivoter sur les axes X et Z pour faire face à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-264">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="54ca2-265">À partir de **StationaryQuadRenderer :: Update**:</span><span class="sxs-lookup"><span data-stu-id="54ca2-265">From **StationaryQuadRenderer::Update**:</span></span>

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a><span data-ttu-id="54ca2-266">Rendre l’hologramme attaché</span><span class="sxs-lookup"><span data-stu-id="54ca2-266">Render the attached hologram</span></span>

<span data-ttu-id="54ca2-267">Pour cet exemple, nous choisissons également d’afficher l’hologramme dans le système de coordonnées du SpatialLocatorAttachedReferenceFrame, où nous avons positionné l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="54ca2-267">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="54ca2-268">(Si nous avions décidé d’effectuer le rendu à l’aide d’un autre système de coordonnées, nous aurions besoin d’acquérir une transformation du système de coordonnées de l’appareil de référence associé à l’appareil vers ce système de coordonnées.)</span><span class="sxs-lookup"><span data-stu-id="54ca2-268">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="54ca2-269">À partir de **HolographicTagAlongSampleMain :: Render**:</span><span class="sxs-lookup"><span data-stu-id="54ca2-269">From **HolographicTagAlongSampleMain::Render**:</span></span>

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

<span data-ttu-id="54ca2-270">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="54ca2-270">That's it!</span></span> <span data-ttu-id="54ca2-271">L’hologramme va à présent « débusquer » une position qui est de 2 mètres devant la direction du regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ca2-271">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="54ca2-272">Cet exemple charge également du contenu supplémentaire. consultez StationaryQuadRenderer. cpp.</span><span class="sxs-lookup"><span data-stu-id="54ca2-272">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="54ca2-273">Gestion des pertes de suivi</span><span class="sxs-lookup"><span data-stu-id="54ca2-273">Handling tracking loss</span></span>

<span data-ttu-id="54ca2-274">Lorsque l’appareil ne peut pas se trouver dans le monde entier, l’application rencontre une « perte de suivi ».</span><span class="sxs-lookup"><span data-stu-id="54ca2-274">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="54ca2-275">Les applications Windows Mixed Reality doivent être en mesure de gérer ces interruptions du système de suivi positionnel.</span><span class="sxs-lookup"><span data-stu-id="54ca2-275">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="54ca2-276">Ces interruptions peuvent être observées et les réponses créées à l’aide de l’événement LocatabilityChanged sur le SpatialLocator par défaut.</span><span class="sxs-lookup"><span data-stu-id="54ca2-276">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="54ca2-277">À partir de **AppMain :: SetHolographicSpace :**</span><span class="sxs-lookup"><span data-stu-id="54ca2-277">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="54ca2-278">Lorsque votre application reçoit un événement LocatabilityChanged, elle peut modifier le comportement en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="54ca2-278">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="54ca2-279">Par exemple, dans l’État PositionalTrackingInhibited, votre application peut suspendre une opération normale et afficher un message d’avertissement [sur l’hologramme](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) qui affiche un message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="54ca2-279">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="54ca2-280">Le modèle d’application holographique Windows est fourni avec un gestionnaire LocatabilityChanged déjà créé pour vous.</span><span class="sxs-lookup"><span data-stu-id="54ca2-280">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="54ca2-281">Par défaut, il affiche un avertissement dans la console de débogage lorsque le suivi positionnel n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="54ca2-281">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="54ca2-282">Vous pouvez ajouter du code à ce gestionnaire pour fournir une réponse en fonction des besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="54ca2-282">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="54ca2-283">À partir de **AppMain. cpp :**</span><span class="sxs-lookup"><span data-stu-id="54ca2-283">From **AppMain.cpp:**</span></span>

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a><span data-ttu-id="54ca2-284">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="54ca2-284">Spatial mapping</span></span>

<span data-ttu-id="54ca2-285">Les API de [mappage spatial](spatial-mapping-in-directx.md) utilisent des systèmes de coordonnées pour obtenir des transformations de modèle pour les maillages de surface.</span><span class="sxs-lookup"><span data-stu-id="54ca2-285">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="54ca2-286">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54ca2-286">See also</span></span>
* [<span data-ttu-id="54ca2-287">Systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="54ca2-287">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="54ca2-288">Ancres spatiales</span><span class="sxs-lookup"><span data-stu-id="54ca2-288">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* <span data-ttu-id="54ca2-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="54ca2-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="54ca2-290">Suivre de la tête et du regard dans DirectX</span><span class="sxs-lookup"><span data-stu-id="54ca2-290">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="54ca2-291">Mains et contrôleurs de mouvement dans DirectX</span><span class="sxs-lookup"><span data-stu-id="54ca2-291">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="54ca2-292">Mappage spatial dans DirectX</span><span class="sxs-lookup"><span data-stu-id="54ca2-292">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
