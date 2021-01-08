---
title: Rendu dans DirectX
description: Apprenez à mettre à jour et à restituer le contenu dans les applications DirectX pour Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, rendu, 3D Graphics, HolographicFrame, boucle de rendu, boucle de mise à jour, procédure pas à pas, exemple de code, Direct3D
ms.openlocfilehash: aafead61b45550f499405ae63bda7d7f8e79d224
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006719"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="2f040-104">Rendu dans DirectX</span><span class="sxs-lookup"><span data-stu-id="2f040-104">Rendering in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="2f040-105">Cet article s’applique aux API natives WinRT héritées.</span><span class="sxs-lookup"><span data-stu-id="2f040-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="2f040-106">Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="2f040-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="2f040-107">Windows Mixed Reality est basé sur DirectX pour produire des expériences graphiques riches et 3D pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="2f040-107">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="2f040-108">L’abstraction de rendu se trouve juste au-dessus de DirectX, ce qui permet aux applications de déterminer la position et l’orientation des observateurs de scène holographique prédits par le système.</span><span class="sxs-lookup"><span data-stu-id="2f040-108">The rendering abstraction sits just above DirectX, which lets apps reason about the position and orientation of holographic scene observers predicted by the system.</span></span> <span data-ttu-id="2f040-109">Le développeur peut ensuite localiser ses hologrammes en fonction de chaque caméra, ce qui permet à l’application de rendre ces hologrammes dans différents systèmes de coordonnées spatiales à mesure que l’utilisateur se déplace.</span><span class="sxs-lookup"><span data-stu-id="2f040-109">The developer can then locate their holograms based on each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="2f040-110">Remarque : cette procédure pas à pas décrit le rendu holographique dans Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="2f040-110">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="2f040-111">Un modèle d’application Direct3D 12 Windows Mixed Reality est également fourni avec l’extension de modèles d’application de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="2f040-111">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="2f040-112">Mettre à jour pour le frame actuel</span><span class="sxs-lookup"><span data-stu-id="2f040-112">Update for the current frame</span></span>

<span data-ttu-id="2f040-113">Pour mettre à jour l’état de l’application pour les hologrammes, une fois par Frame, l’application effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f040-113">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="2f040-114">Obtenir un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> à partir du système de gestion de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="2f040-114">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="2f040-115">Mettez à jour la scène avec la prédiction actuelle de l’emplacement de la vue de la caméra lorsque le rendu est terminé.</span><span class="sxs-lookup"><span data-stu-id="2f040-115">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="2f040-116">Notez qu’il peut y avoir plusieurs caméras pour la scène holographique.</span><span class="sxs-lookup"><span data-stu-id="2f040-116">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="2f040-117">Pour afficher les vues d’appareil photo holographique, une fois par Frame, l’application :</span><span class="sxs-lookup"><span data-stu-id="2f040-117">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="2f040-118">Pour chaque caméra, affichez la scène du frame actuel, à l’aide de la vue caméra et des matrices de projection du système.</span><span class="sxs-lookup"><span data-stu-id="2f040-118">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="2f040-119">Créer un nouveau Frame holographique et obtenir sa prédiction</span><span class="sxs-lookup"><span data-stu-id="2f040-119">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="2f040-120">Le <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> contient des informations dont l’application a besoin pour mettre à jour et restituer le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="2f040-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs to update and render the current frame.</span></span> <span data-ttu-id="2f040-121">L’application commence chaque nouveau frame en appelant la méthode **CreateNextFrame** .</span><span class="sxs-lookup"><span data-stu-id="2f040-121">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="2f040-122">Lorsque cette méthode est appelée, les prédictions sont effectuées à l’aide des dernières données de capteur disponibles et encapsulées dans l’objet **CurrentPrediction** .</span><span class="sxs-lookup"><span data-stu-id="2f040-122">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="2f040-123">Un nouvel objet Frame doit être utilisé pour chaque frame rendu, car il n’est valide que pour un instant donné.</span><span class="sxs-lookup"><span data-stu-id="2f040-123">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="2f040-124">La propriété **CurrentPrediction** contient des informations telles que la position de la caméra.</span><span class="sxs-lookup"><span data-stu-id="2f040-124">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="2f040-125">Les informations sont extrapolées au moment précis où le cadre est supposé être visible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f040-125">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="2f040-126">Le code suivant est extrait de **AppMain :: Update**:</span><span class="sxs-lookup"><span data-stu-id="2f040-126">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="2f040-127">Traiter les mises à jour de l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="2f040-127">Process camera updates</span></span>

<span data-ttu-id="2f040-128">Les mémoires tampons d’arrière-plan peuvent passer d’une image à l’autres.</span><span class="sxs-lookup"><span data-stu-id="2f040-128">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="2f040-129">Votre application doit valider la mémoire tampon d’arrière-plan pour chaque caméra, puis libérer et recréer des vues de ressources et des tampons de profondeur en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="2f040-129">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="2f040-130">Notez que l’ensemble des poses dans la prédiction est la liste faisant autorité des caméras utilisées dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="2f040-130">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="2f040-131">En règle générale, vous utilisez cette liste pour effectuer une itération sur l’ensemble d’appareils photo.</span><span class="sxs-lookup"><span data-stu-id="2f040-131">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="2f040-132">À partir de **AppMain :: Update**:</span><span class="sxs-lookup"><span data-stu-id="2f040-132">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="2f040-133">À partir de **DeviceResources :: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="2f040-133">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="2f040-134">Obtenir le système de coordonnées à utiliser comme base pour le rendu</span><span class="sxs-lookup"><span data-stu-id="2f040-134">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="2f040-135">Windows Mixed Reality permet à votre application de créer différents [systèmes de coordonnées](coordinate-systems-in-directx.md), comme des frames de référence attachés et stationnaires pour le suivi des emplacements dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="2f040-135">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md), like attached and stationary reference frames for tracking locations in the physical world.</span></span> <span data-ttu-id="2f040-136">Votre application peut ensuite utiliser ces systèmes de coordonnées pour savoir où afficher les hologrammes de chaque image.</span><span class="sxs-lookup"><span data-stu-id="2f040-136">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="2f040-137">Lors de la demande de coordonnées à partir d’une API, vous transmettez toujours le <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dans lequel vous souhaitez que ces coordonnées soient exprimées.</span><span class="sxs-lookup"><span data-stu-id="2f040-137">When requesting coordinates from an API, you'll always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="2f040-138">À partir de **AppMain :: Update**:</span><span class="sxs-lookup"><span data-stu-id="2f040-138">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="2f040-139">Ces systèmes de coordonnées peuvent ensuite être utilisés pour générer des matrices de vue stéréo lors du rendu du contenu de votre scène.</span><span class="sxs-lookup"><span data-stu-id="2f040-139">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="2f040-140">À partir de **CameraResources :: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="2f040-140">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="2f040-141">Traiter le point de regard et l’entrée de mouvement</span><span class="sxs-lookup"><span data-stu-id="2f040-141">Process gaze and gesture input</span></span>

<span data-ttu-id="2f040-142">Les entrées en point de [regard](gaze-in-directx.md) et en [main](hands-and-motion-controllers-in-directx.md) ne sont pas basées sur le temps et n’ont pas besoin d’être mises à jour dans la fonction **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="2f040-142">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input aren't time-based and don't have to update in the **StepTimer** function.</span></span> <span data-ttu-id="2f040-143">Toutefois, cette entrée est une information dont l’application a besoin pour examiner chaque frame.</span><span class="sxs-lookup"><span data-stu-id="2f040-143">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="2f040-144">Mettre à jour le processus basé sur le temps</span><span class="sxs-lookup"><span data-stu-id="2f040-144">Process time-based updates</span></span>

<span data-ttu-id="2f040-145">Toute application de rendu en temps réel a besoin d’un moyen de traiter des mises à jour basées sur le temps : le modèle d’application holographique Windows utilise une implémentation de **StepTimer** , similaire à la StepTimer fournie dans le modèle d’application UWP DirectX 11.</span><span class="sxs-lookup"><span data-stu-id="2f040-145">Any real-time rendering app will need some way to process time-based updates - the Windows Holographic app template uses a **StepTimer** implementation, similar to the StepTimer provided in the DirectX 11 UWP app template.</span></span> <span data-ttu-id="2f040-146">Cet exemple de classe d’assistance StepTimer peut fournir des mises à jour à l’étape fixe, des mises à jour à l’étape variable et le mode par défaut est des étapes à durée variable.</span><span class="sxs-lookup"><span data-stu-id="2f040-146">This StepTimer sample helper class can provide fixed time-step updates, variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="2f040-147">Pour le rendu holographique, nous avons choisi de ne pas placer trop de temps dans la fonction de minuteur, car vous pouvez le configurer pour qu’il soit une étape fixe.</span><span class="sxs-lookup"><span data-stu-id="2f040-147">For holographic rendering, we've chosen not to put too much into the timer function because you can configure it to be a fixed time step.</span></span> <span data-ttu-id="2f040-148">Elle peut être appelée plusieurs fois par trame, ou pas du tout, pour certains frames, et nos mises à jour de données holographiques doivent se produire une fois par frame.</span><span class="sxs-lookup"><span data-stu-id="2f040-148">It might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="2f040-149">À partir de **AppMain :: Update**:</span><span class="sxs-lookup"><span data-stu-id="2f040-149">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="2f040-150">Positionner et faire pivoter des hologrammes dans votre système de coordonnées</span><span class="sxs-lookup"><span data-stu-id="2f040-150">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="2f040-151">Si vous utilisez un système de coordonnées unique, étant donné que le modèle utilise le **SpatialStationaryReferenceFrame**, ce processus n’est pas différent de celui utilisé dans les graphiques 3D.</span><span class="sxs-lookup"><span data-stu-id="2f040-151">If you're operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="2f040-152">Ici, nous allons faire pivoter le cube et définir la matrice du modèle en fonction de la position dans le système de coordonnées stationnaire.</span><span class="sxs-lookup"><span data-stu-id="2f040-152">Here, we rotate the cube and set the model matrix based on the position in the stationary coordinate system.</span></span>

<span data-ttu-id="2f040-153">À partir de **SpinningCubeRenderer :: Update**:</span><span class="sxs-lookup"><span data-stu-id="2f040-153">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="2f040-154">**Remarque sur les scénarios avancés :** Le cube en rotation est un exemple simple de positionnement d’un hologramme dans une seule image de référence.</span><span class="sxs-lookup"><span data-stu-id="2f040-154">**Note about advanced scenarios:** The spinning cube is a simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="2f040-155">Il est également possible d' [utiliser simultanément plusieurs SpatialCoordinateSystems](coordinate-systems-in-directx.md) dans le même frame rendu.</span><span class="sxs-lookup"><span data-stu-id="2f040-155">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="2f040-156">Mettre à jour les données de mémoire tampon constante</span><span class="sxs-lookup"><span data-stu-id="2f040-156">Update constant buffer data</span></span>

<span data-ttu-id="2f040-157">Les transformations de modèle pour le contenu sont mises à jour comme d’habitude.</span><span class="sxs-lookup"><span data-stu-id="2f040-157">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="2f040-158">À ce stade, vous aurez des transformations valides calculées pour le système de coordonnées dans lequel vous allez être rendu.</span><span class="sxs-lookup"><span data-stu-id="2f040-158">By now, you'll have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="2f040-159">À partir de **SpinningCubeRenderer :: Update**:</span><span class="sxs-lookup"><span data-stu-id="2f040-159">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="2f040-160">Qu’en est-il des transformations de vue et de projection ?</span><span class="sxs-lookup"><span data-stu-id="2f040-160">What about view and projection transforms?</span></span> <span data-ttu-id="2f040-161">Pour des résultats optimaux, nous voulons attendre que nous ayons terminés pour nos appels de dessin avant de les obtenir.</span><span class="sxs-lookup"><span data-stu-id="2f040-161">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="2f040-162">Restituer le frame actuel</span><span class="sxs-lookup"><span data-stu-id="2f040-162">Render the current frame</span></span>

<span data-ttu-id="2f040-163">Le rendu sur Windows Mixed Reality n’est pas très différent du rendu sur un affichage mono 2D, mais il existe quelques différences :</span><span class="sxs-lookup"><span data-stu-id="2f040-163">Rendering on Windows Mixed Reality isn't much different from rendering on a 2D mono display, but there are a few differences:</span></span>
* <span data-ttu-id="2f040-164">Les prédictions de frame holographique sont importantes.</span><span class="sxs-lookup"><span data-stu-id="2f040-164">Holographic frame predictions are important.</span></span> <span data-ttu-id="2f040-165">Plus la prédiction est proche de la présentation de votre cadre, plus vos hologrammes seront performants.</span><span class="sxs-lookup"><span data-stu-id="2f040-165">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="2f040-166">Windows Mixed realisation contrôle les vues de la caméra.</span><span class="sxs-lookup"><span data-stu-id="2f040-166">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="2f040-167">Affichez-les à chaque fois que le frame holographique vous les présentera ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="2f040-167">Render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="2f040-168">Nous vous recommandons d’effectuer un rendu stéréo à l’aide d’un dessin instancié sur un tableau cible de rendu.</span><span class="sxs-lookup"><span data-stu-id="2f040-168">We recommend doing stereo rendering using instanced drawing to a render target array.</span></span> <span data-ttu-id="2f040-169">Le modèle d’application holographique utilise l’approche recommandée de dessin instancié dans un tableau cible de rendu, qui utilise une vue de la cible du rendu sur un **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="2f040-169">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="2f040-170">Si vous souhaitez effectuer un rendu sans utiliser l’instanciation stéréo, vous devez créer deux RenderTargetViews non-tableau, un pour chaque œil.</span><span class="sxs-lookup"><span data-stu-id="2f040-170">If you want to render without using stereo instancing, you'll need to create two non-array RenderTargetViews, one for each eye.</span></span> <span data-ttu-id="2f040-171">Chaque RenderTargetViews fait référence à l’un des deux secteurs du **Texture2DArray** fourni à l’application à partir du système.</span><span class="sxs-lookup"><span data-stu-id="2f040-171">Each RenderTargetViews references one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="2f040-172">Cela n’est pas recommandé, car il est généralement plus lent que d’utiliser l’instanciation.</span><span class="sxs-lookup"><span data-stu-id="2f040-172">This isn't recommended, as it's typically slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="2f040-173">Recevoir une prédiction HolographicFrame mise à jour</span><span class="sxs-lookup"><span data-stu-id="2f040-173">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="2f040-174">La mise à jour de la prédiction de frame améliore l’efficacité de la stabilisation d’image.</span><span class="sxs-lookup"><span data-stu-id="2f040-174">Updating the frame prediction enhances the effectiveness of image stabilization.</span></span> <span data-ttu-id="2f040-175">Vous bénéficiez d’un positionnement plus précis des hologrammes en raison du temps plus réduit entre la prédiction et le moment où le cadre est visible pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f040-175">You get more accurate positioning of holograms because of the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="2f040-176">Dans l’idéal, mettez à jour votre prédiction de frame juste avant le rendu.</span><span class="sxs-lookup"><span data-stu-id="2f040-176">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="2f040-177">Rendre sur chaque caméra</span><span class="sxs-lookup"><span data-stu-id="2f040-177">Render to each camera</span></span>

<span data-ttu-id="2f040-178">Effectue une boucle sur l’ensemble de la caméra dans la prédiction et effectue un rendu sur chaque caméra de cet ensemble.</span><span class="sxs-lookup"><span data-stu-id="2f040-178">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="2f040-179">**Configurer votre passe de rendu**</span><span class="sxs-lookup"><span data-stu-id="2f040-179">**Set up your rendering pass**</span></span>

<span data-ttu-id="2f040-180">Windows Mixed Reality utilise le rendu stéréoscopique pour améliorer l’illusion de la profondeur et pour afficher stereoscopically, de sorte que les affichages gauche et droit sont actifs.</span><span class="sxs-lookup"><span data-stu-id="2f040-180">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="2f040-181">Avec le rendu stéréoscopique, il existe un décalage entre les deux affichages, que le cerveau peut rapprocher comme profondeur réelle.</span><span class="sxs-lookup"><span data-stu-id="2f040-181">With stereoscopic rendering, there's an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="2f040-182">Cette section traite du rendu stéréoscopique à l’aide de l’instanciation, à l’aide du code du modèle d’application holographique Windows.</span><span class="sxs-lookup"><span data-stu-id="2f040-182">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="2f040-183">Chaque caméra possède sa propre cible de rendu (mémoire tampon d’arrière-plan), ainsi que les matrices de vue et de projection, dans l’espace holographique.</span><span class="sxs-lookup"><span data-stu-id="2f040-183">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="2f040-184">Votre application doit créer d’autres ressources basées sur la caméra, telles que le tampon de profondeur, en fonction de la caméra.</span><span class="sxs-lookup"><span data-stu-id="2f040-184">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="2f040-185">Dans le modèle d’application holographique Windows, nous fournissons une classe d’assistance pour regrouper ces ressources dans DX :: CameraResources.</span><span class="sxs-lookup"><span data-stu-id="2f040-185">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="2f040-186">Commencez par configurer les vues de la cible de rendu :</span><span class="sxs-lookup"><span data-stu-id="2f040-186">Start by setting up the render target views:</span></span>

<span data-ttu-id="2f040-187">À partir de **AppMain :: Render**:</span><span class="sxs-lookup"><span data-stu-id="2f040-187">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="2f040-188">**Utiliser la prédiction pour obtenir les matrices de vue et de projection pour l’appareil photo**</span><span class="sxs-lookup"><span data-stu-id="2f040-188">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="2f040-189">Les matrices de vue et de projection pour chaque caméra holographique changent avec chaque trame.</span><span class="sxs-lookup"><span data-stu-id="2f040-189">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="2f040-190">Actualisez les données dans la mémoire tampon constante pour chaque caméra holographique.</span><span class="sxs-lookup"><span data-stu-id="2f040-190">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="2f040-191">Procédez ainsi après avoir mis à jour la prédiction et avant d’effectuer des appels de dessin pour cette caméra.</span><span class="sxs-lookup"><span data-stu-id="2f040-191">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="2f040-192">À partir de **AppMain :: Render**:</span><span class="sxs-lookup"><span data-stu-id="2f040-192">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="2f040-193">Ici, nous montrons comment les matrices sont acquises à partir de la pose de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="2f040-193">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="2f040-194">Au cours de ce processus, nous obtenons également la fenêtre d’affichage actuelle de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="2f040-194">During this process, we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="2f040-195">Notez la manière dont nous fournissons un système de coordonnées : il s’agit du même système de coordonnées que celui utilisé pour comprendre le point de vue, et c’est celui que nous avons utilisé pour positionner le cube en rotation.</span><span class="sxs-lookup"><span data-stu-id="2f040-195">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="2f040-196">À partir de **CameraResources :: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="2f040-196">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="2f040-197">La fenêtre d’affichage doit être définie pour chaque image.</span><span class="sxs-lookup"><span data-stu-id="2f040-197">The viewport should be set each frame.</span></span> <span data-ttu-id="2f040-198">Votre nuanceur vertex (au moins) doit généralement accéder aux données de la vue ou de la projection.</span><span class="sxs-lookup"><span data-stu-id="2f040-198">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="2f040-199">À partir de **CameraResources :: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="2f040-199">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="2f040-200">**Rendre à la mémoire tampon d’arrière-plan de l’appareil photo et valider la mémoire tampon de profondeur**:</span><span class="sxs-lookup"><span data-stu-id="2f040-200">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="2f040-201">Il est judicieux de vérifier que **TryGetViewTransform** a réussi avant d’essayer d’utiliser les données de la vue ou de la projection, car si le système de coordonnées n’est pas localisable (par exemple, si le suivi a été interrompu), votre application ne peut pas s’afficher avec elle pour ce frame.</span><span class="sxs-lookup"><span data-stu-id="2f040-201">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system isn't locatable (for example, tracking was interrupted) your app can't render with it for that frame.</span></span> <span data-ttu-id="2f040-202">Le modèle appelle uniquement **Render** sur le cube tournant si la classe **CameraResources** indique une mise à jour réussie.</span><span class="sxs-lookup"><span data-stu-id="2f040-202">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="2f040-203">Windows Mixed Reality intègre des fonctionnalités pour la [stabilisation d’image](../platform-capabilities-and-apis/hologram-stability.md) afin de garder les hologrammes positionnés là où un développeur ou un utilisateur les place dans le monde.</span><span class="sxs-lookup"><span data-stu-id="2f040-203">Windows Mixed Reality includes features for [image stabilization](../platform-capabilities-and-apis/hologram-stability.md) to keep holograms positioned where a developer or user puts them in the world.</span></span> <span data-ttu-id="2f040-204">La stabilisation d’image permet de masquer la latence inhérente à un pipeline de rendu pour garantir la meilleure expérience holographique pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="2f040-204">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users.</span></span> <span data-ttu-id="2f040-205">Un point de concentration peut être spécifié pour améliorer encore davantage la stabilisation de l’image, ou une mémoire tampon de profondeur peut être fournie pour calculer la stabilisation des images optimisées en temps réel.</span><span class="sxs-lookup"><span data-stu-id="2f040-205">A focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="2f040-206">Pour de meilleurs résultats, votre application doit fournir un tampon de profondeur à l’aide de l’API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> .</span><span class="sxs-lookup"><span data-stu-id="2f040-206">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="2f040-207">La réalité mixte Windows peut ensuite utiliser les informations géométriques de la mémoire tampon de profondeur pour optimiser la stabilisation de l’image en temps réel.</span><span class="sxs-lookup"><span data-stu-id="2f040-207">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="2f040-208">Le modèle d’application holographique Windows valide la mémoire tampon de profondeur de l’application par défaut, ce qui contribue à optimiser la stabilité des hologrammes.</span><span class="sxs-lookup"><span data-stu-id="2f040-208">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="2f040-209">À partir de **AppMain :: Render**:</span><span class="sxs-lookup"><span data-stu-id="2f040-209">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="2f040-210">Windows traitera votre texture de profondeur sur le GPU. il doit donc être possible d’utiliser votre mémoire tampon de profondeur comme ressource de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2f040-210">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="2f040-211">Le ID3D11Texture2D que vous créez doit être dans un format non typé et doit être lié en tant que vue de ressource de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2f040-211">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="2f040-212">Voici un exemple de création d’une texture de profondeur qui peut être validée pour la stabilisation d’image.</span><span class="sxs-lookup"><span data-stu-id="2f040-212">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="2f040-213">Code pour la **création de ressources de mémoire tampon de profondeur pour CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="2f040-213">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="2f040-214">**Dessiner du contenu holographique**</span><span class="sxs-lookup"><span data-stu-id="2f040-214">**Draw holographic content**</span></span>

<span data-ttu-id="2f040-215">Le modèle d’application holographique Windows restitue le contenu en stéréo à l’aide de la technique recommandée de dessin de la géométrie d’instance vers un Texture2DArray de taille 2.</span><span class="sxs-lookup"><span data-stu-id="2f040-215">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="2f040-216">Examinons la partie instanciation de ce et son fonctionnement sur Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2f040-216">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="2f040-217">À partir de **SpinningCubeRenderer :: Render**:</span><span class="sxs-lookup"><span data-stu-id="2f040-217">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="2f040-218">Chaque instance accède à une matrice de projection/vue différente de la mémoire tampon constante.</span><span class="sxs-lookup"><span data-stu-id="2f040-218">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="2f040-219">Voici la structure de mémoire tampon constante, qui est simplement un tableau de deux matrices.</span><span class="sxs-lookup"><span data-stu-id="2f040-219">Here's the constant buffer structure, which is just an array of two matrices.</span></span>

<span data-ttu-id="2f040-220">À partir de **VertexShaderShared. HLSL**, inclus par **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="2f040-220">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="2f040-221">L’index du tableau cible du rendu doit être défini pour chaque pixel.</span><span class="sxs-lookup"><span data-stu-id="2f040-221">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="2f040-222">Dans l’extrait de code suivant, output. viewId est mappé à la sémantique **SV_RenderTargetArrayIndex** .</span><span class="sxs-lookup"><span data-stu-id="2f040-222">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="2f040-223">Cela nécessite la prise en charge d’une fonctionnalité Direct3D 11,3 facultative, qui permet de définir la sémantique d’index du tableau cible de rendu à partir d’une étape de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2f040-223">This requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="2f040-224">À partir de **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="2f040-224">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="2f040-225">À partir de **VertexShaderShared. HLSL**, inclus par **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="2f040-225">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="2f040-226">Si vous souhaitez utiliser vos techniques de dessin d’instances existantes avec cette méthode de dessin vers un tableau de cibles de rendu stéréo, dessinez deux fois le nombre d’instances que vous avez normalement.</span><span class="sxs-lookup"><span data-stu-id="2f040-226">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, draw twice the number of instances you normally have.</span></span> <span data-ttu-id="2f040-227">Dans le nuanceur, divisez **Input. instId** par 2 pour obtenir l’ID d’instance d’origine, qui peut être indexé dans (par exemple) une mémoire tampon de données par objet : `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="2f040-227">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="2f040-228">Remarque importante à propos du rendu du contenu stéréo sur HoloLens</span><span class="sxs-lookup"><span data-stu-id="2f040-228">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="2f040-229">Windows Mixed Reality prend en charge la possibilité de définir l’index du tableau cible de rendu à partir d’une étape de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2f040-229">Windows Mixed Reality supports the ability to set the render target array index from any shader stage.</span></span> <span data-ttu-id="2f040-230">Normalement, il s’agit d’une tâche qui ne peut être effectuée que dans l’étape de nuanceur Geometry en raison de la façon dont la sémantique est définie pour Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="2f040-230">Normally, this is a task that could only be done in the geometry shader stage because of the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="2f040-231">Ici, nous présentons un exemple complet montrant comment configurer un pipeline de rendu uniquement avec les étapes du nuanceur de vertex et de pixels définies.</span><span class="sxs-lookup"><span data-stu-id="2f040-231">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="2f040-232">Le code du nuanceur est décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2f040-232">The shader code is as described above.</span></span>

<span data-ttu-id="2f040-233">À partir de **SpinningCubeRenderer :: Render**:</span><span class="sxs-lookup"><span data-stu-id="2f040-233">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="2f040-234">Remarque importante à propos du rendu sur des appareils non-HoloLens</span><span class="sxs-lookup"><span data-stu-id="2f040-234">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="2f040-235">La définition de l’index du tableau cible du rendu dans le nuanceur vertex nécessite que le pilote Graphics prenne en charge une fonctionnalité Direct3D 11,3 facultative, que HoloLens prend en charge.</span><span class="sxs-lookup"><span data-stu-id="2f040-235">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="2f040-236">Votre application peut implémenter simplement cette technique pour le rendu, et toutes les spécifications seront respectées pour s’exécuter sur Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2f040-236">Your app may can safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="2f040-237">Il se peut que vous souhaitiez utiliser également l’émulateur HoloLens, qui peut être un puissant outil de développement pour votre application holographique et prendre en charge les appareils de casque immersif Windows Mixed Real qui sont attachés à des PC Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2f040-237">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="2f040-238">La prise en charge du chemin de rendu non-HoloLens-pour l’ensemble de la réalité mixte Windows est également intégrée au modèle d’application Windows holographique.</span><span class="sxs-lookup"><span data-stu-id="2f040-238">Support for the non-HoloLens rendering path - for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="2f040-239">Dans le code du modèle, vous trouverez du code pour permettre à votre application holographique de s’exécuter sur le GPU sur votre PC de développement.</span><span class="sxs-lookup"><span data-stu-id="2f040-239">In the template code, you'll find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="2f040-240">Voici comment la classe **DeviceResources** vérifie cette prise en charge facultative des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="2f040-240">Here's how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="2f040-241">À partir de **DeviceResources :: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="2f040-241">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="2f040-242">Pour prendre en charge le rendu sans cette fonctionnalité facultative, votre application doit utiliser un nuanceur Geometry pour définir l’index du tableau cible du rendu.</span><span class="sxs-lookup"><span data-stu-id="2f040-242">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="2f040-243">Cet extrait de code est ajouté *après* **VSSetConstantBuffers** et *avant* **PSSetShader** dans l’exemple de code présenté dans la section précédente qui explique comment afficher la stéréo sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2f040-243">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="2f040-244">À partir de **SpinningCubeRenderer :: Render**:</span><span class="sxs-lookup"><span data-stu-id="2f040-244">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="2f040-245">**Remarque HLSL**: dans ce cas, vous devez également charger un nuanceur de sommets légèrement modifié qui transmet l’index du tableau cible du rendu au nuanceur Geometry à l’aide d’une sémantique de nuanceur toujours autorisée, telle que TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="2f040-245">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="2f040-246">Le nuanceur Geometry n’a pas à effectuer de travail. le nuanceur Geometry de modèle transmet toutes les données, à l’exception de l’index du tableau cible de rendu qui est utilisé pour définir la sémantique SV_RenderTargetArrayIndex.</span><span class="sxs-lookup"><span data-stu-id="2f040-246">The geometry shader doesn't have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="2f040-247">Code du modèle d’application pour **GeometryShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="2f040-247">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint instId         : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint rtvId          : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="2f040-248">Présent</span><span class="sxs-lookup"><span data-stu-id="2f040-248">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="2f040-249">Activer le frame holographique pour présenter la chaîne de permutation</span><span class="sxs-lookup"><span data-stu-id="2f040-249">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="2f040-250">Avec Windows Mixed Reality, le système contrôle la chaîne de permutation.</span><span class="sxs-lookup"><span data-stu-id="2f040-250">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="2f040-251">Le système gère ensuite la présentation des trames sur chaque caméra holographique pour garantir une expérience utilisateur de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="2f040-251">The system then manages presenting frames to each holographic camera to ensure a high-quality user experience.</span></span> <span data-ttu-id="2f040-252">Il fournit également une fenêtre d’affichage qui met à jour chaque image, pour chaque caméra, afin d’optimiser les aspects du système, tels que la stabilisation d’image ou la capture de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="2f040-252">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="2f040-253">Ainsi, une application holographique utilisant DirectX **n’appelle pas** la chaîne de permutation DXGI.</span><span class="sxs-lookup"><span data-stu-id="2f040-253">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="2f040-254">Au lieu de cela, vous utilisez la classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> pour présenter toutes les chaînes d’échange d’un frame une fois que vous avez terminé de le dessiner.</span><span class="sxs-lookup"><span data-stu-id="2f040-254">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="2f040-255">À partir de **DeviceResources ::P renvoyé**:</span><span class="sxs-lookup"><span data-stu-id="2f040-255">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="2f040-256">Par défaut, cette API attend que le frame se termine avant de retourner.</span><span class="sxs-lookup"><span data-stu-id="2f040-256">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="2f040-257">Les applications holographiques doivent attendre la fin de la trame précédente avant de commencer à travailler sur un nouveau Frame, car cela réduit la latence et permet d’obtenir de meilleurs résultats des prédictions de frame holographique.</span><span class="sxs-lookup"><span data-stu-id="2f040-257">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="2f040-258">Il ne s’agit pas d’une règle difficile, et si vous avez des frames qui prennent plus d’une actualisation de l’écran pour le rendu, vous pouvez désactiver cette attente en passant le paramètre HolographicFramePresentWaitBehavior à <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="2f040-258">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="2f040-259">Dans ce cas, vous utiliserez probablement un thread de rendu asynchrone pour maintenir une charge continue sur le GPU.</span><span class="sxs-lookup"><span data-stu-id="2f040-259">In this case, you would likely use an asynchronous rendering thread to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="2f040-260">La fréquence d’actualisation de l’appareil HoloLens est de 60 Hz, où une image a une durée d’environ 16 ms.</span><span class="sxs-lookup"><span data-stu-id="2f040-260">The refresh rate of the HoloLens device is 60 hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="2f040-261">Les appareils de casque immersif peuvent aller de 60 Hz à 90 Hz. lors de l’actualisation de l’affichage à 90 Hz, chaque trame aura une durée d’environ 11 ms.</span><span class="sxs-lookup"><span data-stu-id="2f040-261">Immersive headset devices can range from 60 hz to 90 hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="2f040-262">Gérer les scénarios DeviceLost en collaboration avec HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="2f040-262">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="2f040-263">En général, les applications DirectX 11 veulent vérifier le HRESULT retourné par la fonction DXGI de la **chaîne d’échange** pour déterminer s’il y a eu une erreur **DeviceLost** .</span><span class="sxs-lookup"><span data-stu-id="2f040-263">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="2f040-264">La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> gère cela pour vous.</span><span class="sxs-lookup"><span data-stu-id="2f040-264">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="2f040-265">Examinez le <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> retourné pour déterminer si vous devez libérer et recréer les ressources basées sur l’appareil et l’appareil Direct3D.</span><span class="sxs-lookup"><span data-stu-id="2f040-265">Inspect the returned <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="2f040-266">Si le périphérique Direct3D a été perdu et que vous l’avez recréé, vous devez indiquer à <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> de commencer à utiliser le nouvel appareil.</span><span class="sxs-lookup"><span data-stu-id="2f040-266">If the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="2f040-267">La chaîne de permutation sera recréée pour cet appareil.</span><span class="sxs-lookup"><span data-stu-id="2f040-267">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="2f040-268">À partir de **DeviceResources :: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="2f040-268">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="2f040-269">Une fois votre Frame présenté, vous pouvez revenir à la boucle principale du programme et l’autoriser à passer à l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="2f040-269">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="2f040-270">PC graphiques hybrides et applications de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2f040-270">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="2f040-271">**Les** PC Windows 10 Creators Update peuvent être configurés avec des GPU discrets et intégrés.</span><span class="sxs-lookup"><span data-stu-id="2f040-271">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="2f040-272">Avec ces types d’ordinateurs, Windows choisit la carte à laquelle le casque est connecté.</span><span class="sxs-lookup"><span data-stu-id="2f040-272">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="2f040-273">Les applications doivent s’assurer que le périphérique DirectX qu’il crée utilise le même adaptateur.</span><span class="sxs-lookup"><span data-stu-id="2f040-273">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="2f040-274">La plupart des exemples de code Direct3D généraux illustrent la création d’un périphérique DirectX à l’aide de la carte matérielle par défaut, qui, sur un système hybride, peut être différent de celui utilisé pour le casque.</span><span class="sxs-lookup"><span data-stu-id="2f040-274">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="2f040-275">Pour contourner les problèmes, utilisez <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> à partir de <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () ou <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId ().</span><span class="sxs-lookup"><span data-stu-id="2f040-275">To work around any issues, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="2f040-276">Cette adapterId peut ensuite être utilisée pour sélectionner le bon DXGIAdapter à l’aide de IDXGIFactory4. EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="2f040-276">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="2f040-277">À partir de **DeviceResources :: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="2f040-277">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="2f040-278">Code pour **mettre à jour DeviceResources :: CreateDeviceResources pour utiliser IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="2f040-278">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="2f040-279">**Graphiques et Media Foundation hybrides**</span><span class="sxs-lookup"><span data-stu-id="2f040-279">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="2f040-280">L’utilisation de Media Foundation sur des systèmes hybrides peut entraîner des problèmes où la vidéo ne s’affiche pas ou la texture vidéo est endommagée, car Media Foundation utilise par défaut un comportement système.</span><span class="sxs-lookup"><span data-stu-id="2f040-280">Using Media Foundation on hybrid systems may cause issues where video won't render or video texture are corrupt because Media Foundation is defaulting to a system behavior.</span></span> <span data-ttu-id="2f040-281">Dans certains scénarios, la création d’un ID3D11Device distinct est nécessaire pour prendre en charge le Multi-Threading et les indicateurs de création corrects sont définis.</span><span class="sxs-lookup"><span data-stu-id="2f040-281">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="2f040-282">Lors de l’initialisation du ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT indicateur doit être défini dans le cadre du D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="2f040-282">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="2f040-283">Une fois l’appareil et le contexte créés, appelez <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> pour activer le multithreading.</span><span class="sxs-lookup"><span data-stu-id="2f040-283">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="2f040-284">Pour associer l’appareil à <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, utilisez la fonction <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager :: ResetDevice</a> .</span><span class="sxs-lookup"><span data-stu-id="2f040-284">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="2f040-285">Code pour **associer un ID3D11Device à IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="2f040-285">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="2f040-286">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f040-286">See also</span></span>
* [<span data-ttu-id="2f040-287">Systèmes de coordonnées dans DirectX</span><span class="sxs-lookup"><span data-stu-id="2f040-287">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="2f040-288">Utilisation de l’émulateur HoloLens</span><span class="sxs-lookup"><span data-stu-id="2f040-288">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
