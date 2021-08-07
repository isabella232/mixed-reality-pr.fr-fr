---
title: Obtention d’un HolographicSpace
description: Découvrez comment utiliser l’API HolographicSpace pour le rendu holographique et l’entrée spatiale dans vos applications de réalité mixte.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrée spatiale, rendu, chaîne de permutation, frame holographique, boucle de mise à jour, boucle de jeu, frame de référence, localisabilité, exemple de code, procédure pas à pas, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 986ccdc6e81d1ac7c7b401a427da548218a68eb0352a0057bf7d7aba3c1d6d6a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212167"
---
# <a name="getting-a-holographicspace"></a>Obtention d’un HolographicSpace

> [!NOTE]
> Cet article s’applique aux API natives WinRT héritées.  Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](openxr-getting-started.md)**.

La classe <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> est votre portail dans le monde holographique. Il contrôle le rendu immersif, fournit des données d’appareil photo et donne accès aux API de raisonnement spatial. Vous allez en créer un pour le <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> de votre application UWP ou le HWND de votre application Win32.

## <a name="set-up-the-holographic-space"></a>Configurer l’espace holographique

la création de l’objet espace holographique est la première étape de la création de votre application Windows Mixed Reality. les applications Windows traditionnelles sont rendues dans une chaîne de permutation Direct3D créée pour la fenêtre principale de leur vue d’application. Cette chaîne de permutation s’affiche dans une ardoise dans l’interface utilisateur holographique. Pour que votre application affiche holographique plutôt qu’une ardoise 2D, créez un espace holographique pour sa fenêtre principale au lieu d’une chaîne de permutation. La présentation des frames holographiques créés par cet espace holographique place votre application en mode de rendu plein écran.

pour une **application UWP** à [partir du *modèle d’application holographique DirectX 11 (Universal Windows)*](creating-a-holographic-directx-project.md), recherchez ce code dans la méthode **SetWindow** dans AppView. cpp :

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Si vous générez une **application Win32** [à partir de l’exemple Win32 *BasicHologram*](creating-a-holographic-directx-project.md#creating-a-win32-project), consultez **App :: CreateWindowAndHolographicSpace** pour obtenir un exemple HWND. Vous pouvez ensuite le convertir en HWND immersif en créant un <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>associé :

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

Une fois que vous avez obtenu un HolographicSpace pour votre CoreWindow UWP ou Win32 HWND, le HolographicSpace peut gérer les caméras holographiques, créer des systèmes de coordonnées et effectuer un rendu holographique. L’espace holographique actuel est utilisé à plusieurs endroits dans le modèle DirectX :
* La classe **DeviceResources** doit recevoir des informations de l’objet HolographicSpace pour créer le périphérique Direct3D. Il s’agit de l’ID d’adaptateur DXGI associé à l’affichage holographique. La classe <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> utilise le périphérique Direct3D 11 de votre application pour créer et gérer des ressources basées sur les appareils, telles que les mémoires tampons d’arrière-plan pour chaque caméra holographique. Si vous souhaitez voir ce que fait cette fonction sous le capot, vous le trouverez dans DeviceResources. cpp.
* La fonction **DeviceResources :: InitializeUsingHolographicSpace** montre comment obtenir l’adaptateur en recherchant le LUID, et comment choisir un adaptateur par défaut quand aucun adaptateur préféré n’est spécifié.
* La classe principale de l’application utilise l’espace holographique de **AppView :: SetWindow** ou **App :: CreateWindowAndHolographicSpace** pour les mises à jour et le rendu.

>[!NOTE]
>Tandis que les sections ci-dessous mentionnent les noms des fonctions du modèle comme **AppView :: SetWindow** , qui supposent que vous avez démarré à partir du modèle d’application UWP holographique, les extraits de code que vous voyez s’appliqueront également sur les applications UWP et Win32.

Nous allons ensuite étudier le processus d’installation dont **SetHolographicSpace** est responsable dans la classe AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>S’abonner aux événements de l’appareil photo, créer et supprimer des ressources d’appareil photo

Le contenu holographique de votre application réside dans son espace holographique et est affiché par le biais d’une ou de plusieurs caméras holographiques, qui représentent différentes perspectives sur la scène. Maintenant que vous disposez de l’espace holographique, vous pouvez recevoir des données pour les caméras holographiques.

Votre application doit répondre aux événements **CameraAdded** en créant des ressources spécifiques à cette caméra. La vue de la cible de rendu de la mémoire tampon d’arrière-plan est un exemple de cette ressource. Vous pouvez voir ce code dans la fonction **DeviceResources :: SetHolographicSpace** , appelée par **AppView :: SetWindow** avant que l’application crée des frames holographiques :

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Votre application doit également répondre aux événements **CameraRemoved** en libérant les ressources qui ont été créées pour cette caméra.

À partir de **DeviceResources :: SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Les gestionnaires d’événements doivent effectuer des tâches pour assurer le bon déroulement du rendu holographique et le rendu de votre application. Pour plus d’informations, lisez le code et les commentaires suivants : vous pouvez rechercher **OnCameraAdded** et **OnCameraRemoved** dans votre classe principale pour comprendre comment le mappage de **m_cameraResources** est géré par **DeviceResources**.

Pour le moment, nous nous concentrons sur AppMain et la configuration qu’il fait pour permettre à votre application de connaître les caméras holographiques. Dans ce souci, il est important de prendre note des deux conditions suivantes :

1. Pour le gestionnaire d’événements **CameraAdded** , l’application peut fonctionner de manière asynchrone pour terminer la création de ressources et le chargement de ressources pour la nouvelle caméra holographique. Les applications qui prennent plus d’un cadre pour effectuer ce travail doivent demander un report et terminer le report après le chargement asynchrone. Une [tâche ppl](/cpp/parallel/concrt/parallel-patterns-library-ppl) peut être utilisée pour effectuer un travail asynchrone. Votre application doit s’assurer qu’elle est prête à être rendue sur cette caméra immédiatement lorsqu’elle quitte le gestionnaire d’événements, ou lorsqu’elle termine le report. Le fait de quitter le gestionnaire d’événements ou de terminer le report indique au système que votre application est maintenant prête à recevoir les images holographiques incluses dans cette caméra.

2. Lorsque l’application reçoit un événement **CameraRemoved** , elle doit libérer toutes les références à la mémoire tampon d’arrière-plan et quitter immédiatement la fonction. Cela comprend les affichages de cible de rendu et toute autre ressource qui peut contenir une référence à [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). L’application doit également s’assurer que la mémoire tampon d’arrière-plan n’est pas attachée en tant que cible de rendu, comme indiqué dans **CameraResources :: ReleaseResourcesForBackBuffer**. Pour accélérer les choses, votre application peut libérer la mémoire tampon d’arrière-plan, puis lancer une tâche pour effectuer de façon asynchrone tout autre travail de destruction pour l’appareil photo. Le modèle d’application holographique comprend une tâche PPL que vous pouvez utiliser à cet effet.

>[!NOTE]
>Si vous souhaitez déterminer à quel moment une caméra ajoutée ou supprimée s’affiche sur le frame, utilisez les propriétés **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) et [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Créer un cadre de référence pour votre contenu holographique

Le contenu de votre application doit être positionné dans un [système de coordonnées spatiales](coordinate-systems-in-directx.md) pour être rendu dans le HolographicSpace. Le système fournit deux principales trames de référence, que vous pouvez utiliser pour établir un système de coordonnées pour vos hologrammes.

il existe deux types de frames de référence dans Windows holographique : les frames de référence attachés à l’appareil et les trames de référence qui restent stationnaires lorsque l’appareil passe dans l’environnement de l’utilisateur. Le modèle d’application holographique utilise un frame de référence fixe par défaut ; Il s’agit de l’une des méthodes les plus simples pour restituer des hologrammes universels.

Les images de référence fixes sont conçues pour stabiliser les positions près de l’emplacement actuel de l’appareil. Cela signifie que les coordonnées du périphérique peuvent dépasser légèrement par rapport à l’environnement de l’utilisateur lorsque ce dernier en apprend davantage sur l’espace qui l’entoure. Il existe deux façons de créer une image de référence stationnaire : acquérir le système de coordonnées à partir de la [Phase spatiale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)ou utilisez le <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>par défaut. si vous créez une application Windows Mixed Reality pour des casques immersifs, le point de départ recommandé est la [phase spatiale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage). La phase spatiale fournit également des informations sur les fonctionnalités du casque immersif porté par le joueur. Ici, nous montrons comment utiliser le <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>par défaut.

le localisateur spatial représente le périphérique Windows Mixed Reality et suit le mouvement de l’appareil et fournit des systèmes de coordonnées qui peuvent être compris par rapport à son emplacement.

À partir de **AppMain :: OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Créez le frame de référence fixe une fois l’application lancée. Cela équivaut à définir un système de coordonnées universelles, avec l’origine placée à la position de l’appareil lorsque l’application est lancée. Ce frame de référence ne se déplace pas avec l’appareil.

À partir de **AppMain :: SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Tous les frames de référence sont alignés par gravité, ce qui signifie que l’axe des y pointe vers le haut par rapport à l’environnement de l’utilisateur. étant donné que Windows utilise des systèmes de coordonnées « droitiers », la direction de l’axe – z coïncide avec la direction « avant » à laquelle l’appareil est dirigé lorsque le frame de référence est créé.

>[!NOTE]
>Lorsque votre application nécessite un positionnement précis des hologrammes individuels, utilisez un <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> pour ancrer l’hologramme individuel à une position dans le monde réel. Par exemple, utilisez une ancre spatiale lorsque l’utilisateur indique un point qui présente un intérêt particulier. Les positions d’ancrage ne dérivent pas, mais elles peuvent être ajustées. Par défaut, lorsqu’un point d’ancrage est ajusté, il facilite sa position sur les différentes images après la correction. Selon votre application, lorsque cela se produit, vous souhaiterez peut-être gérer la modification d’une manière différente (par exemple, en la différant jusqu’à ce que l’hologramme soit hors de l’affichage). La propriété <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> et les événements <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> activent ces personnalisations.

## <a name="respond-to-locatability-changed-events"></a>Répondre aux événements de modification de la localisation

Le rendu des hologrammes à verrouillage universel requiert que l’appareil se trouve dans le monde entier. Cela n’est peut-être pas toujours possible en raison des conditions environnementales et, le cas échéant, l’utilisateur peut s’attendre à une indication visuelle de l’interruption de suivi. Cette indication visuelle doit être rendue à l’aide de frames de référence attachés à l’appareil, plutôt que stationnaire au monde.

Votre application peut demander à être avertie si le suivi est interrompu pour une raison quelconque. Inscrivez-vous à l’événement LocatabilityChanged pour détecter le moment où la capacité de l’appareil à se trouver dans le monde change. À partir de **AppMain :: SetHolographicSpace :**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Utilisez ensuite cet événement pour déterminer quand les hologrammes ne peuvent pas être rendus à l’stationnaire dans le monde.

## <a name="see-also"></a>Voir aussi
* [Rendu dans DirectX](rendering-in-directx.md)
* [Systèmes de coordonnées dans DirectX](coordinate-systems-in-directx.md)