---
title: Création d’un projet DirectX holographique
description: découvrez comment créer une application DirectX holographique basée sur le modèle d’application Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, application holographique, nouvelle application, application UWP, application de modèle, hologrammes, nouveau projet, procédure pas à pas, téléchargement, exemple de code, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 7de7d73ec1e5fd8abde6d4822c86628e090fdf0cf89769fc9ef21311ff1aff15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200153"
---
# <a name="creating-a-holographic-directx-project"></a>Création d’un projet DirectX holographique

> [!NOTE]
> Cet article s’applique aux API natives WinRT héritées.  Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](openxr-getting-started.md)**.

une application holographique que vous créez pour un HoloLens sera une <a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank">application plateforme Windows universelle (UWP)</a>.  si vous ciblez des casques de Windows Mixed Reality de bureau, vous pouvez créer une application UWP ou une application Win32.

Le modèle application UWP holographique DirectX 11 ressemble davantage au modèle application UWP DirectX 11. Le modèle comprend une boucle de programme, une classe **DeviceResources** pour gérer le périphérique et le contexte Direct3D et une classe de convertisseur de contenu simplifiée. Il possède également un <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, comme n’importe quelle autre application UWP.

Toutefois, l’application de réalité mixte possède des fonctionnalités supplémentaires qui ne sont pas présentes dans une application standard Direct3D UWP. le modèle d’application Windows Mixed Reality peut :
* Gérer les ressources d’appareil Direct3D associées aux appareils photo holographiques.
* Récupérez les mémoires tampons d’arrière-plan de l’appareil photo. Dans le cas de directement Direct3D 12, créez des ressources de mémoire tampon d’arrière-plan holographique et gérez les durées de vie des ressources.
* Gérer les entrées de [regard](../../design/gaze-and-commit.md) et reconnaître un [geste](../../design/gaze-and-commit.md#composite-gestures).
* Passez en mode de rendu stéréo plein écran.

## <a name="how-do-i-get-started"></a>Comment faire pour démarrer ?

installez d’abord [les outils](../install-the-tools.md)en suivant les instructions de téléchargement de Visual Studio 2019 et des modèles d’application Windows Mixed Reality. les modèles d’application de réalité mixte sont disponibles sur la place de marché Visual Studio en tant que [téléchargement web](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX), ou en les installant en tant qu’extension par le biais de l’interface utilisateur Visual Studio.

vous êtes maintenant prêt à créer votre application de Windows Mixed Reality DirectX 11. Remarque : pour supprimer l’exemple de contenu, commentez la directive de préprocesseur **DRAW_SAMPLE_CONTENT** dans *pch. h*.

## <a name="creating-a-uwp-project"></a>Création d’un projet UWP

Une fois les outils installés,] (.. /install-the-tools.md) vous pouvez ensuite créer un projet UWP DirectX UWP.

pour créer un nouveau projet dans Visual Studio 2019 :
1. Démarrez **Visual Studio**.
2. dans la section **Prise en main** à droite, sélectionnez **créer un nouveau projet**.
3. dans les menus déroulants de la boîte de dialogue **créer un nouveau projet** , sélectionnez **C++**, **Windows Mixed Reality** et **UWP**.
4. sélectionnez **application holographique DirectX 11 (Universal Windows) (C++/WinRT)**.
   ![capture d’écran du modèle de projet d’application UWP DirectX 11 C++/WinRT dans Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *modèle de projet d’application UWP DirectX 11 C++/WinRT pour holographique dans Visual Studio 2019*
   >[!IMPORTANT]
   >Assurez-vous que le nom du modèle de projet comprend « (C++/WinRT) ».  Si ce n’est pas le cas, une version antérieure des modèles de projet holographique est installée.  pour accéder aux derniers modèles de projet, [installez-les](../install-the-tools.md) en tant qu’extension de Visual Studio 2019.
5. Sélectionnez **Suivant**.
5. renseignez les zones de texte nom et **emplacement** du **Project** , puis sélectionnez **créer**. Le projet d’application holographique est créé.
6. pour le ciblage du développement uniquement HoloLens 2, assurez-vous que la version **cible** et la **version minimale** sont définies sur **Windows 10, version 1903**.  si vous ciblez également des HoloLens (1re génération) ou des casques Windows Mixed Reality de bureau, vous pouvez définir la **version minimale** sur **Windows 10, version 1809**. Cela nécessite des <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">vérifications adaptatives de version</a> dans votre code lors de l’utilisation de nouvelles fonctionnalités de HoloLens 2.
   ![capture d’écran de la définition de Windows 10, version 1903 en tant que versions cible et minimale](images/new-uwp-project.png)<br>
   *définition de **Windows 10, version 1903** en tant que versions cible et minimale*
   >[!IMPORTANT]
   >si vous ne voyez pas **Windows 10, version 1903** , vous ne disposez pas du dernier kit de développement logiciel (SDK) Windows 10 installé.  pour que cette option s’affiche, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">installez la version 10.0.18362.0 ou ultérieure du kit de développement logiciel (SDK) Windows 10</a>.

pour créer un nouveau projet dans Visual Studio 2017 :
1. Démarrez **Visual Studio**.
2. dans le menu **fichier** , pointez sur **nouveau** , puis sélectionnez **Project** dans le menu contextuel. La boîte de dialogue **Nouveau projet** s’affiche.
3. Développez **installé** sur la gauche, puis développez le nœud **Visual C++** Language.
4. accédez au **Windows nœud holographique universal >** et sélectionnez **application holographique DirectX 11 (universal Windows) (C++/WinRT)**.
   ![capture d’écran du modèle de projet d’application UWP DirectX 11 C++/WinRT dans Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *modèle de projet d’application UWP DirectX 11 C++/WinRT pour holographique dans Visual Studio 2017*
   >[!IMPORTANT]
   >Assurez-vous que le nom du modèle de projet comprend « (C++/WinRT) ».  Si ce n’est pas le cas, une version antérieure des modèles de projet holographique est installée.  pour accéder aux derniers modèles de projet, [installez-les](../install-the-tools.md) en tant qu’extension de Visual Studio 2017.
5. Renseignez les zones de texte **nom** et **emplacement** , puis sélectionnez ou appuyez sur **OK**. Le projet d’application holographique est créé.
6. pour le ciblage du développement uniquement HoloLens 2, assurez-vous que la version **cible** et la **version minimale** sont définies sur **Windows 10, version 1903**.  si vous ciblez également des HoloLens (1re génération) ou des casques Windows Mixed Reality de bureau, vous pouvez définir la **version minimale** sur **Windows 10, version 1809**. Cela nécessite des <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">vérifications adaptatives de version</a> dans votre code lors de l’utilisation de nouvelles fonctionnalités de HoloLens 2.
   ![capture d’écran de la définition de Windows 10, version 1903 en tant que versions cible et minimale](images/new-uwp-project.png)<br>
   *définition de **Windows 10, version 1903** en tant que versions cible et minimale*
   >[!IMPORTANT]
   >si vous ne voyez pas **Windows 10, version 1903** , vous ne disposez pas du dernier kit de développement logiciel (SDK) Windows 10 installé.  pour que cette option s’affiche, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">installez la version 10.0.18362.0 ou ultérieure du kit de développement logiciel (SDK) Windows 10</a>.

le modèle génère un projet à l’aide de <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c++/WinRT</a>, une projection de langage c++ 17 des api Windows Runtime qui prend en charge tous les compilateurs c++ 17 conformes aux normes.  Le projet montre comment créer un cube universel qui est placé à 2 mètres de l’utilisateur. L' [utilisateur peut appuyer ou appuyer sur un](../../design/gaze-and-commit.md#composite-gestures) bouton du contrôleur pour placer le cube dans une autre position spécifiée par le point de [regard](../../design/gaze-and-commit.md)de l’utilisateur. Vous pouvez modifier ce projet pour créer une application de réalité mixte.

Vous pouvez également créer un nouveau projet à l’aide du modèle de projet holographique **Visual C#** , qui est basé sur SharpDX.  si votre projet C# holographique n’a pas démarré à partir du modèle d’application holographique Windows, vous devez copier le fichier ms. fxcompile. targets à partir d’un projet de modèle Windows Mixed Reality C# et l’importer dans votre fichier. csproj pour compiler les fichiers HLSL que vous ajoutez à votre projet. un modèle Direct3D 12 est également fourni dans l’extension Windows Mixed Reality des modèles d’application à Visual Studio.

pour plus d’informations sur la façon de créer et de déployer l’exemple sur votre HoloLens, sur un PC avec un appareil immersif ou sur un émulateur, consultez [utilisation de Visual Studio pour déployer et déboguer](../platform-capabilities-and-apis/using-visual-studio.md) .

Le reste des instructions ci-dessous suppose que vous utilisez C++ pour créer votre application.

### <a name="uwp-app-entry-point"></a>Point d’entrée de l’application UWP

Votre application UWP holographique démarre dans la fonction **wWinMain** dans AppView. cpp. La fonction **wWinMain** crée le <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> de l’application et démarre le <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> avec celle-ci.

À partir de **AppView. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

à partir de là, la classe AppView gère l’interaction avec Windows événements d’entrée de base, les événements CoreWindow et la messagerie, etc. Il créera également le HolographicSpace utilisé par votre application.

## <a name="creating-a-win32-project"></a>Création d’un projet Win32

Le moyen le plus simple de commencer à créer un projet holographique Win32 consiste à adapter l' <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">exemple Win32 *BasicHologram*</a>.

cet exemple Win32 utilise <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c++/WinRT</a>, une projection de langage c++ 17 des api Windows Runtime qui prend en charge tout compilateur c++ 17 conforme aux normes.  Le projet montre comment créer un cube universel qui est placé à 2 mètres de l’utilisateur. L’utilisateur peut appuyer sur un bouton du contrôleur pour placer le cube à une position différente spécifiée par le [regard](../../design/gaze-and-commit.md)de l’utilisateur. Vous pouvez modifier ce projet pour créer une application de réalité mixte.

### <a name="win32-app-entry-point"></a>Point d’entrée de l’application Win32

Votre application holographique Win32 démarre dans la fonction **wWinMain** dans AppMain. cpp. La fonction **wWinMain** crée le HWND de l’application et démarre sa boucle de messages.

À partir de **AppMain. cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

À partir de là, la classe AppMain gère l’interaction avec les messages de fenêtre de base, et ainsi de suite. Il créera également le HolographicSpace utilisé par votre application.

## <a name="render-holographic-content"></a>Afficher le contenu holographique

Le dossier de **contenu** du projet contient des classes pour le rendu des hologrammes dans l' [espace holographique](getting-a-holographicspace.md). L’hologramme par défaut dans le modèle est un cube à rotation qui est placé à 2 mètres de l’utilisateur. Le dessin de ce cube est implémenté dans **SpinningCubeRenderer. cpp**, qui possède les principales méthodes suivantes :

|  Méthode  |  Explication | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Charge les nuanceurs et crée la maille du cube. | 
|  `PositionHologram` |  Place l’hologramme à l’emplacement spécifié par le <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>fourni. | 
|  `Update` |  Fait pivoter le cube et définit la matrice du modèle. | 
|  `Render` |  Génère le rendu d’un frame à l’aide des nuanceurs vertex et de pixels. | 

Le sous-dossier **nuanciers** contient quatre implémentations de nuanceur par défaut :

|  Nuanceur  |  Explication | 
|----------|----------|
|  `GeometryShader.hlsl` |  Un transfert qui laisse la géométrie non modifiée. | 
|  `PixelShader.hlsl` |  Transmet les données de couleur. Les données de couleur sont interpolées et affectées à un pixel à l’étape de pixellisation. | 
|  `VertexShader.hlsl` |  Nuanceur simple pour le traitement des vertex sur le GPU. | 
|  `VPRTVertexShader.hlsl` |  nuanceur Simple pour le traitement des vertex sur le GPU, qui est optimisé pour le rendu stéréo Windows Mixed Reality. | 

`VertexShaderShared.hlsl` contient le code commun partagé entre `VertexShader.hlsl` et `VPRTVertexShader.hlsl` .

Remarque : le modèle d’application Direct3D 12 comprend également `ViewInstancingVertexShader.hlsl` . Cette variante utilise des fonctionnalités facultatives D3D12 pour rendre les images stéréo plus efficaces.

Les nuanceurs se compilent lorsque le projet est généré, puis chargés dans la méthode **SpinningCubeRenderer :: CreateDeviceDependentResources** .

## <a name="interact-with-your-holograms"></a>Interagissez avec vos hologrammes

L’entrée utilisateur est traitée dans la classe **SpatialInputHandler** , qui obtient une instance <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> et s’abonne à l’événement <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> . Cela permet de détecter le mouvement d’appui sur l’air et d’autres événements d’entrée spatiale.

## <a name="update-holographic-content"></a>Mettre à jour le contenu holographique

Votre application de réalité mixte est mise à jour dans une boucle de jeu, qui est implémentée par défaut dans la méthode de **mise à jour** dans `AppMain.cpp` . La méthode **Update** met à jour les objets de scène, comme le cube en rotation, et retourne un objet <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> qui est utilisé pour obtenir des matrices de projection et d’affichage à jour et pour présenter la chaîne de permutation.

La méthode **Render** dans `AppMain.cpp` prend le <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> et restitue le frame actuel sur chaque caméra holographique, en fonction de l’état actuel de l’application et du positionnement spatial.

## <a name="notes"></a>Notes

le modèle d’application Windows Mixed Reality prend désormais en charge la compilation avec l’indicateur d’atténuation Spectre activé (/Qspectre). veillez à installer la version Spectre-atténuée des bibliothèques runtime de Microsoft Visual C++ (MSVC) avant de compiler une configuration avec atténuation Spectre activée. pour installer les bibliothèques C++ atténuées par Spectre, lancez le Visual Studio Installer et sélectionnez **modifier**. Accédez à **composants individuels** et recherchez « spectre ». sélectionnez les zones correspondant aux plateformes cibles et à la version de MSVC dont vous avez besoin pour compiler le code atténué Spectre pour, puis cliquez sur **modifier** pour commencer l’installation.

## <a name="see-also"></a>Voir aussi
* [Obtention d’un HolographicSpace](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Rendu dans DirectX](rendering-in-directx.md)
* [Utilisation de Visual Studio pour le déploiement et le débogage](../platform-capabilities-and-apis/using-visual-studio.md)
* [Utilisation de l’émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Utilisation de code XAML avec les applications DirectX holographiques](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)