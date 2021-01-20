---
title: Obtention d’un HolographicSpace
description: Découvrez comment utiliser l’API HolographicSpace pour le rendu holographique et l’entrée spatiale dans vos applications de réalité mixte.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrée spatiale, rendu, chaîne de permutation, Frame holographique, boucle de mise à jour, boucle de jeu, cadre de référence, localisation, exemple de code, procédure pas à pas, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 215c3cbacd4c7975d05b3a1b3f3992c9198642f7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580913"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="8b50f-104">Obtention d’un HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="8b50f-104">Getting a HolographicSpace</span></span>

> [!NOTE]
> <span data-ttu-id="8b50f-105">Cet article s’applique aux API natives WinRT héritées.</span><span class="sxs-lookup"><span data-stu-id="8b50f-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="8b50f-106">Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="8b50f-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="8b50f-107">La classe <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> est votre portail dans le monde holographique.</span><span class="sxs-lookup"><span data-stu-id="8b50f-107">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="8b50f-108">Il contrôle le rendu immersif, fournit des données d’appareil photo et donne accès aux API de raisonnement spatial.</span><span class="sxs-lookup"><span data-stu-id="8b50f-108">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="8b50f-109">Vous allez en créer un pour le <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> de votre application UWP ou le HWND de votre application Win32.</span><span class="sxs-lookup"><span data-stu-id="8b50f-109">You'll create one for your UWP app's <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="8b50f-110">Configurer l’espace holographique</span><span class="sxs-lookup"><span data-stu-id="8b50f-110">Set up the holographic space</span></span>

<span data-ttu-id="8b50f-111">La création de l’objet espace holographique est la première étape de la création de votre application Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="8b50f-111">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="8b50f-112">Les applications Windows traditionnelles sont rendues dans une chaîne de permutation Direct3D créée pour la fenêtre principale de leur vue d’application.</span><span class="sxs-lookup"><span data-stu-id="8b50f-112">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="8b50f-113">Cette chaîne de permutation s’affiche dans une ardoise dans l’interface utilisateur holographique.</span><span class="sxs-lookup"><span data-stu-id="8b50f-113">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="8b50f-114">Pour que votre application affiche holographique plutôt qu’une ardoise 2D, créez un espace holographique pour sa fenêtre principale au lieu d’une chaîne de permutation.</span><span class="sxs-lookup"><span data-stu-id="8b50f-114">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="8b50f-115">La présentation des frames holographiques créés par cet espace holographique place votre application en mode de rendu plein écran.</span><span class="sxs-lookup"><span data-stu-id="8b50f-115">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="8b50f-116">Pour une **application UWP** à [partir du *modèle d’application holographique DirectX 11 (Windows universel)*](creating-a-holographic-directx-project.md), recherchez ce code dans la méthode **SetWindow** dans AppView. cpp :</span><span class="sxs-lookup"><span data-stu-id="8b50f-116">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="8b50f-117">Si vous générez une **application Win32** [à partir de l’exemple Win32 *BasicHologram*](creating-a-holographic-directx-project.md#creating-a-win32-project), consultez **App :: CreateWindowAndHolographicSpace** pour obtenir un exemple HWND.</span><span class="sxs-lookup"><span data-stu-id="8b50f-117">If you're building a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an HWND example.</span></span> <span data-ttu-id="8b50f-118">Vous pouvez ensuite le convertir en HWND immersif en créant un <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>associé :</span><span class="sxs-lookup"><span data-stu-id="8b50f-118">You can then convert it into an immersive HWND by creating an associated <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="8b50f-119">Une fois que vous avez obtenu un HolographicSpace pour votre CoreWindow UWP ou Win32 HWND, le HolographicSpace peut gérer les caméras holographiques, créer des systèmes de coordonnées et effectuer un rendu holographique.</span><span class="sxs-lookup"><span data-stu-id="8b50f-119">Once you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, the HolographicSpace can handle holographic cameras, create coordinate systems, and do holographic rendering.</span></span> <span data-ttu-id="8b50f-120">L’espace holographique actuel est utilisé à plusieurs endroits dans le modèle DirectX :</span><span class="sxs-lookup"><span data-stu-id="8b50f-120">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="8b50f-121">La classe **DeviceResources** doit recevoir des informations de l’objet HolographicSpace pour créer le périphérique Direct3D.</span><span class="sxs-lookup"><span data-stu-id="8b50f-121">The **DeviceResources** class needs to get some information from the HolographicSpace object to create the Direct3D device.</span></span> <span data-ttu-id="8b50f-122">Il s’agit de l’ID d’adaptateur DXGI associé à l’affichage holographique.</span><span class="sxs-lookup"><span data-stu-id="8b50f-122">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="8b50f-123">La classe <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> utilise le périphérique Direct3D 11 de votre application pour créer et gérer des ressources basées sur les appareils, telles que les mémoires tampons d’arrière-plan pour chaque caméra holographique.</span><span class="sxs-lookup"><span data-stu-id="8b50f-123">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="8b50f-124">Si vous souhaitez voir ce que fait cette fonction sous le capot, vous le trouverez dans DeviceResources. cpp.</span><span class="sxs-lookup"><span data-stu-id="8b50f-124">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="8b50f-125">La fonction **DeviceResources :: InitializeUsingHolographicSpace** montre comment obtenir l’adaptateur en recherchant le LUID, et comment choisir un adaptateur par défaut quand aucun adaptateur préféré n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="8b50f-125">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="8b50f-126">La classe principale de l’application utilise l’espace holographique de **AppView :: SetWindow** ou **App :: CreateWindowAndHolographicSpace** pour les mises à jour et le rendu.</span><span class="sxs-lookup"><span data-stu-id="8b50f-126">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="8b50f-127">Tandis que les sections ci-dessous mentionnent les noms des fonctions du modèle comme **AppView :: SetWindow** , qui supposent que vous avez démarré à partir du modèle d’application UWP holographique, les extraits de code que vous voyez s’appliqueront également sur les applications UWP et Win32.</span><span class="sxs-lookup"><span data-stu-id="8b50f-127">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="8b50f-128">Nous allons ensuite étudier le processus d’installation dont **SetHolographicSpace** est responsable dans la classe AppMain.</span><span class="sxs-lookup"><span data-stu-id="8b50f-128">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="8b50f-129">S’abonner aux événements de l’appareil photo, créer et supprimer des ressources d’appareil photo</span><span class="sxs-lookup"><span data-stu-id="8b50f-129">Subscribe to camera events, create, and remove camera resources</span></span>

<span data-ttu-id="8b50f-130">Le contenu holographique de votre application réside dans son espace holographique et est affiché par le biais d’une ou de plusieurs caméras holographiques, qui représentent différentes perspectives sur la scène.</span><span class="sxs-lookup"><span data-stu-id="8b50f-130">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras, which represent different perspectives on the scene.</span></span> <span data-ttu-id="8b50f-131">Maintenant que vous disposez de l’espace holographique, vous pouvez recevoir des données pour les caméras holographiques.</span><span class="sxs-lookup"><span data-stu-id="8b50f-131">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="8b50f-132">Votre application doit répondre aux événements **CameraAdded** en créant des ressources spécifiques à cette caméra.</span><span class="sxs-lookup"><span data-stu-id="8b50f-132">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera.</span></span> <span data-ttu-id="8b50f-133">La vue de la cible de rendu de la mémoire tampon d’arrière-plan est un exemple de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="8b50f-133">An example of such a resource is your back buffer render target view.</span></span> <span data-ttu-id="8b50f-134">Vous pouvez voir ce code dans la fonction **DeviceResources :: SetHolographicSpace** , appelée par **AppView :: SetWindow** avant que l’application crée des frames holographiques :</span><span class="sxs-lookup"><span data-stu-id="8b50f-134">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="8b50f-135">Votre application doit également répondre aux événements **CameraRemoved** en libérant les ressources qui ont été créées pour cette caméra.</span><span class="sxs-lookup"><span data-stu-id="8b50f-135">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="8b50f-136">À partir de **DeviceResources :: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="8b50f-136">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="8b50f-137">Les gestionnaires d’événements doivent effectuer des tâches pour assurer le bon déroulement du rendu holographique et le rendu de votre application.</span><span class="sxs-lookup"><span data-stu-id="8b50f-137">The event handlers must complete some work to keep holographic rendering flowing smoothly, and your app rendering at all.</span></span> <span data-ttu-id="8b50f-138">Pour plus d’informations, lisez le code et les commentaires suivants : vous pouvez rechercher **OnCameraAdded** et **OnCameraRemoved** dans votre classe principale pour comprendre comment le mappage de **m_cameraResources** est géré par **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="8b50f-138">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="8b50f-139">Pour le moment, nous nous concentrons sur AppMain et la configuration qu’il fait pour permettre à votre application de connaître les caméras holographiques.</span><span class="sxs-lookup"><span data-stu-id="8b50f-139">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="8b50f-140">Dans ce souci, il est important de prendre note des deux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b50f-140">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="8b50f-141">Pour le gestionnaire d’événements **CameraAdded** , l’application peut fonctionner de manière asynchrone pour terminer la création de ressources et le chargement de ressources pour la nouvelle caméra holographique.</span><span class="sxs-lookup"><span data-stu-id="8b50f-141">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="8b50f-142">Les applications qui prennent plus d’un cadre pour effectuer ce travail doivent demander un report et terminer le report après le chargement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8b50f-142">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously.</span></span> <span data-ttu-id="8b50f-143">Une [tâche ppl](/cpp/parallel/concrt/parallel-patterns-library-ppl) peut être utilisée pour effectuer un travail asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8b50f-143">A [PPL task](/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="8b50f-144">Votre application doit s’assurer qu’elle est prête à être rendue sur cette caméra immédiatement lorsqu’elle quitte le gestionnaire d’événements, ou lorsqu’elle termine le report.</span><span class="sxs-lookup"><span data-stu-id="8b50f-144">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="8b50f-145">Le fait de quitter le gestionnaire d’événements ou de terminer le report indique au système que votre application est maintenant prête à recevoir les images holographiques incluses dans cette caméra.</span><span class="sxs-lookup"><span data-stu-id="8b50f-145">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="8b50f-146">Lorsque l’application reçoit un événement **CameraRemoved** , elle doit libérer toutes les références à la mémoire tampon d’arrière-plan et quitter immédiatement la fonction.</span><span class="sxs-lookup"><span data-stu-id="8b50f-146">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="8b50f-147">Cela comprend les affichages de cible de rendu et toute autre ressource qui peut contenir une référence à [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="8b50f-147">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="8b50f-148">L’application doit également s’assurer que la mémoire tampon d’arrière-plan n’est pas attachée en tant que cible de rendu, comme indiqué dans **CameraResources :: ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="8b50f-148">The app must also ensure that the back buffer isn't attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="8b50f-149">Pour accélérer les choses, votre application peut libérer la mémoire tampon d’arrière-plan, puis lancer une tâche pour effectuer de façon asynchrone tout autre travail de destruction pour l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="8b50f-149">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other tear down work for the camera.</span></span> <span data-ttu-id="8b50f-150">Le modèle d’application holographique comprend une tâche PPL que vous pouvez utiliser à cet effet.</span><span class="sxs-lookup"><span data-stu-id="8b50f-150">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="8b50f-151">Si vous souhaitez déterminer à quel moment une caméra ajoutée ou supprimée s’affiche sur le frame, utilisez les propriétés **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) et [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="8b50f-151">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="8b50f-152">Créer un cadre de référence pour votre contenu holographique</span><span class="sxs-lookup"><span data-stu-id="8b50f-152">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="8b50f-153">Le contenu de votre application doit être positionné dans un [système de coordonnées spatiales](coordinate-systems-in-directx.md) pour être rendu dans le HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="8b50f-153">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="8b50f-154">Le système fournit deux principales trames de référence, que vous pouvez utiliser pour établir un système de coordonnées pour vos hologrammes.</span><span class="sxs-lookup"><span data-stu-id="8b50f-154">The system provides two primary frames of reference, which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="8b50f-155">Il existe deux types de frames de référence dans Windows holographique : les frames de référence attachés à l’appareil et les trames de référence qui restent stationnaires lorsque l’appareil passe dans l’environnement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8b50f-155">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="8b50f-156">Le modèle d’application holographique utilise un frame de référence fixe par défaut ; Il s’agit de l’une des méthodes les plus simples pour restituer des hologrammes universels.</span><span class="sxs-lookup"><span data-stu-id="8b50f-156">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="8b50f-157">Les images de référence fixes sont conçues pour stabiliser les positions près de l’emplacement actuel de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="8b50f-157">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="8b50f-158">Cela signifie que les coordonnées du périphérique peuvent dépasser légèrement par rapport à l’environnement de l’utilisateur lorsque ce dernier en apprend davantage sur l’espace qui l’entoure.</span><span class="sxs-lookup"><span data-stu-id="8b50f-158">This means that coordinates further from the device can drift slightly relative to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="8b50f-159">Il existe deux façons de créer une image de référence stationnaire : acquérir le système de coordonnées à partir de la [Phase spatiale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)ou utilisez le <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b50f-159">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="8b50f-160">Si vous créez une application Windows Mixed Reality pour des casques immersifs, le point de départ recommandé est la [Phase spatiale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage).</span><span class="sxs-lookup"><span data-stu-id="8b50f-160">If you're creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage).</span></span> <span data-ttu-id="8b50f-161">La phase spatiale fournit également des informations sur les fonctionnalités du casque immersif porté par le joueur.</span><span class="sxs-lookup"><span data-stu-id="8b50f-161">The spatial stage also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="8b50f-162">Ici, nous montrons comment utiliser le <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b50f-162">Here, we show how to use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="8b50f-163">Le localisateur spatial représente le périphérique Windows Mixed Reality et suit le mouvement de l’appareil et fournit des systèmes de coordonnées qui peuvent être compris par rapport à son emplacement.</span><span class="sxs-lookup"><span data-stu-id="8b50f-163">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="8b50f-164">À partir de **AppMain :: OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="8b50f-164">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="8b50f-165">Créez le frame de référence fixe une fois l’application lancée.</span><span class="sxs-lookup"><span data-stu-id="8b50f-165">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="8b50f-166">Cela équivaut à définir un système de coordonnées universelles, avec l’origine placée à la position de l’appareil lorsque l’application est lancée.</span><span class="sxs-lookup"><span data-stu-id="8b50f-166">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="8b50f-167">Ce frame de référence ne se déplace pas avec l’appareil.</span><span class="sxs-lookup"><span data-stu-id="8b50f-167">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="8b50f-168">À partir de **AppMain :: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="8b50f-168">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="8b50f-169">Tous les frames de référence sont alignés par gravité, ce qui signifie que l’axe des y pointe vers le haut par rapport à l’environnement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8b50f-169">All reference frames are gravity aligned, meaning that the y-axis points "up" in relation to the user's environment.</span></span> <span data-ttu-id="8b50f-170">Étant donné que Windows utilise des systèmes de coordonnées « droitiers », la direction de l’axe-z coïncide avec la direction « avant » à laquelle l’appareil est dirigé lorsque le frame de référence est créé.</span><span class="sxs-lookup"><span data-stu-id="8b50f-170">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="8b50f-171">Lorsque votre application nécessite un positionnement précis des hologrammes individuels, utilisez un <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> pour ancrer l’hologramme individuel à une position dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="8b50f-171">When your app requires precise placement of individual holograms, use a <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="8b50f-172">Par exemple, utilisez une ancre spatiale lorsque l’utilisateur indique un point qui présente un intérêt particulier.</span><span class="sxs-lookup"><span data-stu-id="8b50f-172">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="8b50f-173">Les positions d’ancrage ne dérivent pas, mais elles peuvent être ajustées.</span><span class="sxs-lookup"><span data-stu-id="8b50f-173">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="8b50f-174">Par défaut, lorsqu’un point d’ancrage est ajusté, il facilite sa position sur les différentes images après la correction.</span><span class="sxs-lookup"><span data-stu-id="8b50f-174">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="8b50f-175">Selon votre application, lorsque cela se produit, vous souhaiterez peut-être gérer la modification d’une manière différente (par exemple, en la différant jusqu’à ce que l’hologramme soit hors de l’affichage).</span><span class="sxs-lookup"><span data-stu-id="8b50f-175">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="8b50f-176">La propriété <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> et les événements <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> activent ces personnalisations.</span><span class="sxs-lookup"><span data-stu-id="8b50f-176">The <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="8b50f-177">Répondre aux événements de modification de la localisation</span><span class="sxs-lookup"><span data-stu-id="8b50f-177">Respond to locatability changed events</span></span>

<span data-ttu-id="8b50f-178">Le rendu des hologrammes à verrouillage universel requiert que l’appareil se trouve dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="8b50f-178">Rendering world-locked holograms requires the device to locate itself in the world.</span></span> <span data-ttu-id="8b50f-179">Cela n’est peut-être pas toujours possible en raison des conditions environnementales et, le cas échéant, l’utilisateur peut s’attendre à une indication visuelle de l’interruption de suivi.</span><span class="sxs-lookup"><span data-stu-id="8b50f-179">This may not always be possible because of environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="8b50f-180">Cette indication visuelle doit être rendue à l’aide de frames de référence attachés à l’appareil, plutôt que stationnaire au monde.</span><span class="sxs-lookup"><span data-stu-id="8b50f-180">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="8b50f-181">Votre application peut demander à être avertie si le suivi est interrompu pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="8b50f-181">Your app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="8b50f-182">Inscrivez-vous à l’événement LocatabilityChanged pour détecter le moment où la capacité de l’appareil à se trouver dans le monde change.</span><span class="sxs-lookup"><span data-stu-id="8b50f-182">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="8b50f-183">À partir de **AppMain :: SetHolographicSpace :**</span><span class="sxs-lookup"><span data-stu-id="8b50f-183">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="8b50f-184">Utilisez ensuite cet événement pour déterminer quand les hologrammes ne peuvent pas être rendus à l’stationnaire dans le monde.</span><span class="sxs-lookup"><span data-stu-id="8b50f-184">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b50f-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b50f-185">See also</span></span>
* [<span data-ttu-id="8b50f-186">Rendu dans DirectX</span><span class="sxs-lookup"><span data-stu-id="8b50f-186">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="8b50f-187">Systèmes de coordonnées dans DirectX</span><span class="sxs-lookup"><span data-stu-id="8b50f-187">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)