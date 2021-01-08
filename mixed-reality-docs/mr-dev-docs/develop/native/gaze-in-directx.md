---
title: Suivre de la tête et du regard dans DirectX
description: Apprenez à demander, à utiliser et à décompresser des données Raycasting à partir du suivi des yeux et du regard dans les applications DirectX natives.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: œil-point d’interposition, point de présence, suivi de la tête, suivi des yeux, DirectX, entrée, hologrammes, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: a518e5e4153da9c58295abb257a8ed2d69145211
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009549"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="b8133-104">Entrée en regard des points de regard et de pointage dans DirectX</span><span class="sxs-lookup"><span data-stu-id="b8133-104">Head-gaze and eye-gaze input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="b8133-105">Cet article s’applique aux API natives WinRT héritées.</span><span class="sxs-lookup"><span data-stu-id="b8133-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="b8133-106">Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="b8133-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="b8133-107">Dans Windows Mixed Reality, l’entrée en regard de l’œil et de la tête est utilisée pour déterminer ce que l’utilisateur examine.</span><span class="sxs-lookup"><span data-stu-id="b8133-107">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="b8133-108">Vous pouvez utiliser les données pour piloter des modèles d’entrée principaux tels que le [point d’interposition et la validation](../../design/gaze-and-commit.md), et fournir un contexte pour différents types d’interaction.</span><span class="sxs-lookup"><span data-stu-id="b8133-108">You can use the data to drive primary input models like [head-gaze and commit](../../design/gaze-and-commit.md), and provide context for different interaction types.</span></span> <span data-ttu-id="b8133-109">Deux types de vecteurs de pointage sont disponibles par le biais de l’API : le point de regard et l’œil.</span><span class="sxs-lookup"><span data-stu-id="b8133-109">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="b8133-110">Les deux sont fournis sous la forme d’un rayon tridimensionnel avec une origine et une direction.</span><span class="sxs-lookup"><span data-stu-id="b8133-110">Both are provided as a three-dimensional ray with an origin and direction.</span></span> <span data-ttu-id="b8133-111">Les applications peuvent ensuite raycast dans leurs scènes ou dans le monde réel, et déterminer ce que l’utilisateur cible.</span><span class="sxs-lookup"><span data-stu-id="b8133-111">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="b8133-112">**Tête-** point de regard représente la direction dans laquelle la tête de l’utilisateur est pointée.</span><span class="sxs-lookup"><span data-stu-id="b8133-112">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="b8133-113">Pensez à la position et à la direction vers l’avant de l’appareil lui-même, la position étant le point central entre les deux affichages.</span><span class="sxs-lookup"><span data-stu-id="b8133-113">Think of head-gaze as the position and forward direction of the device itself, with the position as the center point between the two displays.</span></span> <span data-ttu-id="b8133-114">La tête de regard est disponible sur tous les appareils de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="b8133-114">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="b8133-115">**Eye-point de regard** représente la direction vers laquelle les yeux de l’utilisateur cherchent.</span><span class="sxs-lookup"><span data-stu-id="b8133-115">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="b8133-116">L’origine est située entre les yeux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b8133-116">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="b8133-117">Elle est disponible sur les appareils de réalité mixte qui incluent un système de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="b8133-117">It's available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="b8133-118">Les rayons de tête et de regard sont accessibles par le biais de l’API  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="b8133-118">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="b8133-119">Appelez [SpatialPointerPose :: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) pour recevoir un nouvel objet SpatialPointerPose à l’horodatage et au [système de coordonnées](coordinate-systems-in-directx.md)spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b8133-119">Call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="b8133-120">Ce SpatialPointerPose contient une origine et une direction de pointage.</span><span class="sxs-lookup"><span data-stu-id="b8133-120">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="b8133-121">Elle contient également un point d’origine et une direction de regard si le suivi oculaire est disponible.</span><span class="sxs-lookup"><span data-stu-id="b8133-121">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="b8133-122">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="b8133-122">Device support</span></span>

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="b8133-123"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="b8133-123"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="b8133-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8133-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="b8133-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b8133-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="b8133-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8133-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="b8133-127">Suivi de la tête</span><span class="sxs-lookup"><span data-stu-id="b8133-127">Head-gaze</span></span></td>
     <td><span data-ttu-id="b8133-128">✔️</span><span class="sxs-lookup"><span data-stu-id="b8133-128">✔️</span></span></td>
     <td><span data-ttu-id="b8133-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b8133-129">✔️</span></span></td>
     <td><span data-ttu-id="b8133-130">✔️</span><span class="sxs-lookup"><span data-stu-id="b8133-130">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="b8133-131">Œil-point de regard</span><span class="sxs-lookup"><span data-stu-id="b8133-131">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="b8133-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b8133-132">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="b8133-133">Utilisation de l’en-tête</span><span class="sxs-lookup"><span data-stu-id="b8133-133">Using head-gaze</span></span>

<span data-ttu-id="b8133-134">Pour accéder au point de regard, commencez par appeler  [SpatialPointerPose :: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) pour recevoir un nouvel objet SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="b8133-134">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="b8133-135">Transmettez les paramètres suivants.</span><span class="sxs-lookup"><span data-stu-id="b8133-135">Pass the following parameters.</span></span>
 - <span data-ttu-id="b8133-136">[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) qui représente le système de coordonnées souhaité pour le point de regard.</span><span class="sxs-lookup"><span data-stu-id="b8133-136">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the coordinate system you want for the head-gaze.</span></span> <span data-ttu-id="b8133-137">Elle est représentée par la variable *coordinateSystem* dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b8133-137">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="b8133-138">Pour plus d’informations, consultez notre guide de développement des [systèmes de coordonnées](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="b8133-138">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="b8133-139">[Horodateur](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) qui représente l’heure exacte de la pose demandée.</span><span class="sxs-lookup"><span data-stu-id="b8133-139">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="b8133-140">En général, vous utilisez un horodatage qui correspond à l’heure à laquelle le frame actuel sera affiché.</span><span class="sxs-lookup"><span data-stu-id="b8133-140">Typically, you'll use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="b8133-141">Vous pouvez obtenir cet horodateur d’affichage prédit à partir d’un objet  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , qui est accessible via le [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)actuel.</span><span class="sxs-lookup"><span data-stu-id="b8133-141">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="b8133-142">Cet objet HolographicFramePrediction est représenté par la variable de *prédiction* dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b8133-142">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="b8133-143">Une fois que vous avez un SpatialPointerPose valide, la position de la tête et la direction vers l’avant sont accessibles en tant que propriétés.</span><span class="sxs-lookup"><span data-stu-id="b8133-143">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="b8133-144">Le code suivant montre comment y accéder.</span><span class="sxs-lookup"><span data-stu-id="b8133-144">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="b8133-145">Utilisation des yeux</span><span class="sxs-lookup"><span data-stu-id="b8133-145">Using eye-gaze</span></span>

<span data-ttu-id="b8133-146">Pour que vos utilisateurs utilisent une entrée en regard de l’œil, chaque utilisateur doit passer par un étalonnage de l' [utilisateur de suivi oculaire](../../calibration.md) la première fois qu’il utilise l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b8133-146">For your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](../../calibration.md) the first time they use the device.</span></span> <span data-ttu-id="b8133-147">L’API Eye-regard est semblable à la tête de regard.</span><span class="sxs-lookup"><span data-stu-id="b8133-147">The eye-gaze API is similar to head-gaze.</span></span>
<span data-ttu-id="b8133-148">Elle utilise la même API [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , qui fournit une origine de rayon et une direction que vous pouvez raycast par rapport à votre scène.</span><span class="sxs-lookup"><span data-stu-id="b8133-148">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="b8133-149">La seule différence est que vous devez activer explicitement le suivi visuel avant de l’utiliser :</span><span class="sxs-lookup"><span data-stu-id="b8133-149">The only difference is that you need to explicitly enable eye tracking before using it:</span></span>
1. <span data-ttu-id="b8133-150">Demandez à l’utilisateur l’autorisation d’utiliser le suivi oculaire dans votre application.</span><span class="sxs-lookup"><span data-stu-id="b8133-150">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="b8133-151">Activez la fonctionnalité « entrée de regard » dans le manifeste de votre package.</span><span class="sxs-lookup"><span data-stu-id="b8133-151">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="b8133-152">Demande d’accès à une entrée en regard des yeux</span><span class="sxs-lookup"><span data-stu-id="b8133-152">Requesting access to eye-gaze input</span></span>

<span data-ttu-id="b8133-153">Lorsque votre application démarre, appelez [EyesPose :: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) pour demander l’accès au suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="b8133-153">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="b8133-154">Le système demande à l’utilisateur si nécessaire et retourne [GazeInputAccessStatus :: allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) une fois que l’accès a été accordé.</span><span class="sxs-lookup"><span data-stu-id="b8133-154">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="b8133-155">Il s’agit d’un appel asynchrone, ce qui nécessite un peu de gestion supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b8133-155">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="b8133-156">L’exemple suivant montre comment effectuer une opération de détachement d’un thread std :: thread pour attendre le résultat, qu’il stocke dans une variable membre appelée *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="b8133-156">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="b8133-157">Le démarrage d’un thread détaché n’est qu’une option pour gérer les appels asynchrones.</span><span class="sxs-lookup"><span data-stu-id="b8133-157">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="b8133-158">Vous pouvez également utiliser les nouvelles fonctionnalités de [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) prises en charge par C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="b8133-158">You could also use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="b8133-159">Voici un autre exemple de demande d’autorisation de l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="b8133-159">Here's another example for asking for user permission:</span></span>
-   <span data-ttu-id="b8133-160">EyesPose :: IsSupported () permet à l’application de déclencher la boîte de dialogue d’autorisation uniquement s’il existe un dispositif de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="b8133-160">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there's an eye tracker.</span></span>
-   <span data-ttu-id="b8133-161">GazeInputAccessStatus m_gazeInputAccessStatus ; Cela permet d’éviter de relancer l’invite d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="b8133-161">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="b8133-162">Déclaration de la capacité *d’entrée en regard*</span><span class="sxs-lookup"><span data-stu-id="b8133-162">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="b8133-163">Double-cliquez sur le fichier appxmanifest dans *Explorateur de solutions*.</span><span class="sxs-lookup"><span data-stu-id="b8133-163">Double-click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="b8133-164">Accédez ensuite à la section *fonctionnalités* et vérifiez la capacité *d’entrée de regard* .</span><span class="sxs-lookup"><span data-stu-id="b8133-164">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Capacité d’entrée en regard](images/gaze-input-capability.png)

<span data-ttu-id="b8133-166">Cela ajoute les lignes suivantes à la section *package* dans le fichier appxmanifest :</span><span class="sxs-lookup"><span data-stu-id="b8133-166">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="b8133-167">Obtenir le regard de l’œil</span><span class="sxs-lookup"><span data-stu-id="b8133-167">Getting the eye-gaze ray</span></span>

<span data-ttu-id="b8133-168">Une fois que vous avez reçu l’accès à ET, vous êtes libre de prendre le regard de chaque image.</span><span class="sxs-lookup"><span data-stu-id="b8133-168">Once you have received access to ET, you're free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="b8133-169">Comme avec le point de regard, récupérez [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) en appelant [SpatialPointerPose :: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) avec un horodatage et un système de coordonnées souhaités.</span><span class="sxs-lookup"><span data-stu-id="b8133-169">As with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="b8133-170">SpatialPointerPose contient un objet [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) via la propriété [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="b8133-170">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="b8133-171">Ce n’est pas NULL uniquement si le suivi oculaire est activé.</span><span class="sxs-lookup"><span data-stu-id="b8133-171">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="b8133-172">À partir de là, vous pouvez vérifier si l’utilisateur de l’appareil a un étalonnage de suivi oculaire en appelant [EyesPose :: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="b8133-172">From there, you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="b8133-173">Ensuite, utilisez la [propriété de](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) pointage pour récupérer le [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) contenant la position et la direction de l’oeil.</span><span class="sxs-lookup"><span data-stu-id="b8133-173">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="b8133-174">La propriété de pointage peut parfois avoir la valeur null. Assurez-vous de le vérifier.</span><span class="sxs-lookup"><span data-stu-id="b8133-174">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="b8133-175">Cela peut se produire si un utilisateur calibré ferme temporairement ses yeux.</span><span class="sxs-lookup"><span data-stu-id="b8133-175">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="b8133-176">L’exemple de code suivant montre comment accéder à l’œil-regard.</span><span class="sxs-lookup"><span data-stu-id="b8133-176">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a><span data-ttu-id="b8133-177">Secours lorsque le suivi oculaire n’est pas disponible</span><span class="sxs-lookup"><span data-stu-id="b8133-177">Fallback when eye tracking isn't available</span></span>

<span data-ttu-id="b8133-178">Comme mentionné dans nos [documents sur la conception des suivis oculaires](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), les concepteurs et les développeurs doivent connaître les instances où les données de suivi oculaire peuvent ne pas être disponibles.</span><span class="sxs-lookup"><span data-stu-id="b8133-178">As mentioned in our [eye tracking design docs](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), both designers and developers should be aware of instances where eye tracking data may not be available.</span></span>

<span data-ttu-id="b8133-179">Il existe plusieurs raisons pour lesquelles les données ne sont pas disponibles :</span><span class="sxs-lookup"><span data-stu-id="b8133-179">There are various reasons for data being unavailable:</span></span>
* <span data-ttu-id="b8133-180">Un utilisateur n’est pas étalonné</span><span class="sxs-lookup"><span data-stu-id="b8133-180">A user not being calibrated</span></span>
* <span data-ttu-id="b8133-181">Un utilisateur a refusé l’accès de l’application à ses données de suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="b8133-181">A user has denied the app access to his/her eye tracking data</span></span>
* <span data-ttu-id="b8133-182">Les interférences temporaires, telles que les traînées sur le Visor HoloLens ou les cheveux, boucher les yeux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b8133-182">Temporary interferences, such as smudges on the HoloLens visor or hair occluding the user's eyes.</span></span> 

<span data-ttu-id="b8133-183">Alors que certaines API ont déjà été mentionnées dans ce document, nous fournissons un résumé de la façon de détecter que le suivi oculaire est disponible en tant que référence rapide :</span><span class="sxs-lookup"><span data-stu-id="b8133-183">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="b8133-184">Vérifiez que le système prend en charge le suivi visuel.</span><span class="sxs-lookup"><span data-stu-id="b8133-184">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="b8133-185">Appelez la *méthode* suivante : [Windows. perception. People. EyesPose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="b8133-185">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="b8133-186">Vérifiez que l’utilisateur est étalonné.</span><span class="sxs-lookup"><span data-stu-id="b8133-186">Check that the user is calibrated.</span></span> <span data-ttu-id="b8133-187">Appelez la *propriété* suivante : [Windows. perception. People. EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="b8133-187">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="b8133-188">Vérifiez que l’utilisateur a donné à votre application l’autorisation d’utiliser ses données de suivi oculaire : récupérez le _« GazeInputAccessStatus »_ actuel.</span><span class="sxs-lookup"><span data-stu-id="b8133-188">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="b8133-189">Vous trouverez un exemple de la procédure à suivre pour [demander l’accès aux entrées de regard](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span><span class="sxs-lookup"><span data-stu-id="b8133-189">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="b8133-190">Vous pouvez également vérifier que vos données de suivi oculaire ne sont pas obsolètes en ajoutant un délai d’expiration entre les mises à jour reçues des données de suivi oculaire et en conversant le point de vue de la tête, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b8133-190">You may also want to check that your eye tracking data isn't stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>   
<span data-ttu-id="b8133-191">Pour plus d’informations, consultez les [considérations relatives](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) à la conception de secours.</span><span class="sxs-lookup"><span data-stu-id="b8133-191">Visit our [fallback design considerations](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="b8133-192">Corrélation du regard avec d’autres entrées</span><span class="sxs-lookup"><span data-stu-id="b8133-192">Correlating gaze with other inputs</span></span>

<span data-ttu-id="b8133-193">Il peut arriver que vous ayez besoin d’un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) qui correspond à un événement dans le passé.</span><span class="sxs-lookup"><span data-stu-id="b8133-193">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="b8133-194">Par exemple, si l’utilisateur fait un robinet d’air, votre application peut souhaiter savoir ce qu’elle recherchait.</span><span class="sxs-lookup"><span data-stu-id="b8133-194">For example, if the user does an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="b8133-195">À cet effet, l’utilisation simple de [SpatialPointerPose :: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) avec le temps de trame prédit serait inexacte en raison de la latence entre le traitement d’entrée du système et la durée d’affichage.</span><span class="sxs-lookup"><span data-stu-id="b8133-195">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="b8133-196">En outre, si vous utilisez des yeux pour le ciblage, nos yeux ont tendance à se déplacer même avant de terminer une action de validation.</span><span class="sxs-lookup"><span data-stu-id="b8133-196">Also, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="b8133-197">Il s’agit d’un problème moins grave pour une pression aérienne simple, mais il devient plus critique lors de la combinaison de longues commandes vocales avec des mouvements d’œil rapides.</span><span class="sxs-lookup"><span data-stu-id="b8133-197">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="b8133-198">L’une des façons de gérer ce scénario consiste à effectuer un appel supplémentaire à  [SpatialPointerPose :: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), à l’aide d’un horodateur historique qui correspond à l’événement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b8133-198">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="b8133-199">Toutefois, pour les entrées qui acheminent le SpatialInteractionManager, il existe une méthode plus simple.</span><span class="sxs-lookup"><span data-stu-id="b8133-199">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="b8133-200">[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) a sa propre fonction [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="b8133-200">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="b8133-201">L’appel de qui fournira un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) parfaitement corrélé sans les deviner.</span><span class="sxs-lookup"><span data-stu-id="b8133-201">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="b8133-202">Pour plus d’informations sur l’utilisation de SpatialInteractionSourceStates, jetez un coup d’œil aux [contrôleurs mains et motion dans](hands-and-motion-controllers-in-directx.md) la documentation DirectX.</span><span class="sxs-lookup"><span data-stu-id="b8133-202">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="b8133-203">Étalonnage</span><span class="sxs-lookup"><span data-stu-id="b8133-203">Calibration</span></span>

<span data-ttu-id="b8133-204">Pour que le suivi des yeux fonctionne correctement, chaque utilisateur doit passer par un étalonnage de l' [utilisateur de suivi oculaire](../../calibration.md).</span><span class="sxs-lookup"><span data-stu-id="b8133-204">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](../../calibration.md).</span></span> <span data-ttu-id="b8133-205">Cela permet à l’appareil d’ajuster le système pour une expérience d’affichage plus confortable et de meilleure qualité pour l’utilisateur et pour garantir un suivi visuel précis en même temps.</span><span class="sxs-lookup"><span data-stu-id="b8133-205">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="b8133-206">Les développeurs n’ont rien à faire à leur bout pour gérer l’étalonnage de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b8133-206">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="b8133-207">Le système s’assure que l’utilisateur est invité à étalonner l’appareil dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="b8133-207">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="b8133-208">L’utilisateur utilise l’appareil pour la première fois</span><span class="sxs-lookup"><span data-stu-id="b8133-208">The user is using the device for the first time</span></span>
* <span data-ttu-id="b8133-209">L’utilisateur a précédemment choisi le processus d’étalonnage</span><span class="sxs-lookup"><span data-stu-id="b8133-209">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="b8133-210">Le processus d’étalonnage n’a pas réussi la dernière fois que l’utilisateur a utilisé l’appareil</span><span class="sxs-lookup"><span data-stu-id="b8133-210">The calibration process didn't succeed the last time the user used the device</span></span>

<span data-ttu-id="b8133-211">Les développeurs doivent veiller à fournir une prise en charge adéquate pour les utilisateurs où les données de suivi oculaire peuvent ne pas être disponibles.</span><span class="sxs-lookup"><span data-stu-id="b8133-211">Developers should make sure to provide adequate support for users where eye tracking data may not be available.</span></span> <span data-ttu-id="b8133-212">En savoir plus sur les considérations relatives aux solutions de secours au [suivi oculaire sur HoloLens 2](../../design/eye-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="b8133-212">Learn more about considerations for fallback solutions at [Eye tracking on HoloLens 2](../../design/eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="b8133-213">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8133-213">See also</span></span>

* [<span data-ttu-id="b8133-214">Étalonnage</span><span class="sxs-lookup"><span data-stu-id="b8133-214">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="b8133-215">Systèmes de coordonnées dans DirectX</span><span class="sxs-lookup"><span data-stu-id="b8133-215">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="b8133-216">Eye-point de regard sur HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b8133-216">Eye-gaze on HoloLens 2</span></span>](../../design/eye-tracking.md)
* [<span data-ttu-id="b8133-217">Modèle d’entrée de regard et de validation</span><span class="sxs-lookup"><span data-stu-id="b8133-217">Gaze and commit input model</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="b8133-218">Mains et contrôleurs de mouvement dans DirectX</span><span class="sxs-lookup"><span data-stu-id="b8133-218">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="b8133-219">Entrée vocale dans DirectX</span><span class="sxs-lookup"><span data-stu-id="b8133-219">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
