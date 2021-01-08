---
title: Implémenter des lanceurs d’applications 3D (applications UWP)
description: Découvrez comment créer des programmes de lancement et des logos d’applications en 3D pour des applications et des jeux UWP Windows Mixed Reality sur des casques HoloLens et VR.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icône, modélisation, lanceur, lanceur 3D, vignette, cube en direct, lien profond, secondarytile, vignette secondaire, UWP, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, XML, cadre englobant, Unity
ms.openlocfilehash: 40a68d0835ec8fb92d6417650700f41e8a31aab6
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009679"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="f353a-104">Implémenter des lanceurs d’applications 3D (applications UWP)</span><span class="sxs-lookup"><span data-stu-id="f353a-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="f353a-105">Cette fonctionnalité a été ajoutée dans le cadre de la mise à jour 2017 automne Creators (RS3) pour les casques immersifs et est prise en charge par HoloLens avec la mise à jour 2018 d’avril de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f353a-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="f353a-106">Assurez-vous que votre application cible une version du SDK Windows supérieure ou égale à 10.0.16299 sur les casques immersifs et 10.0.17125 sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f353a-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="f353a-107">Vous trouverez les SDK Windows les plus récentes [ici](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="f353a-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="f353a-108">La [base de la réalité Windows Mixed](../discover/navigating-the-windows-mixed-reality-home.md) est le point de départ où les utilisateurs se trouvent avant de lancer des applications.</span><span class="sxs-lookup"><span data-stu-id="f353a-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="f353a-109">Lors de la création d’une application UWP pour Windows Mixed Reality, par défaut, les applications sont lancées en tant qu’ardoise 2D avec le logo de leur application.</span><span class="sxs-lookup"><span data-stu-id="f353a-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="f353a-110">Lors du développement d’expériences pour Windows Mixed Reality, un lanceur 3D peut éventuellement être défini pour remplacer le lanceur 2D par défaut de votre application.</span><span class="sxs-lookup"><span data-stu-id="f353a-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="f353a-111">En règle générale, les lanceurs 3D sont recommandés pour lancer des applications immersifs qui déchargent les utilisateurs de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f353a-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home.</span></span> <span data-ttu-id="f353a-112">Le lanceur 2D par défaut est préféré lorsque l’application est activée sur place.</span><span class="sxs-lookup"><span data-stu-id="f353a-112">The default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="f353a-113">Vous pouvez également créer un [lien profond en 3D (secondaryTile)](#3d-deep-links-secondarytiles) en tant que lanceur en 3D pour le contenu d’une application UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="f353a-113">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="f353a-114">processus de création du lanceur d’applications 3D</span><span class="sxs-lookup"><span data-stu-id="f353a-114">3D app launcher creation process</span></span>

<span data-ttu-id="f353a-115">La création d’un lanceur d’applications 3D comporte trois étapes :</span><span class="sxs-lookup"><span data-stu-id="f353a-115">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="f353a-116">Conception et concept</span><span class="sxs-lookup"><span data-stu-id="f353a-116">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="f353a-117">Modélisation et exportation</span><span class="sxs-lookup"><span data-stu-id="f353a-117">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="f353a-118">Intégration dans votre application (cet article)</span><span class="sxs-lookup"><span data-stu-id="f353a-118">Integrating it into your application (this article)</span></span>

<span data-ttu-id="f353a-119">les ressources 3D à utiliser comme lanceurs pour votre application doivent être créées à l’aide des [instructions de création Windows Mixed realisation](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) pour garantir la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="f353a-119">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="f353a-120">Les ressources qui ne satisfont pas à cette spécification de création ne seront pas affichées dans la page d’hébergement de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f353a-120">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="f353a-121">Configuration du lanceur 3D</span><span class="sxs-lookup"><span data-stu-id="f353a-121">Configuring the 3D launcher</span></span>

<span data-ttu-id="f353a-122">Lorsque vous créez un projet dans Visual Studio, cela a pour effet de créer une vignette par défaut simple qui affiche le nom et le logo de votre application.</span><span class="sxs-lookup"><span data-stu-id="f353a-122">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="f353a-123">Pour remplacer cette représentation 2D par un modèle 3D personnalisé, modifiez le manifeste d’application de votre application de manière à inclure l’élément « MixedRealityModel » dans le cadre de votre définition de vignette par défaut.</span><span class="sxs-lookup"><span data-stu-id="f353a-123">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="f353a-124">Pour revenir au lanceur 2D, supprimez simplement la définition MixedRealityModel du manifeste.</span><span class="sxs-lookup"><span data-stu-id="f353a-124">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="f353a-125">XML</span><span class="sxs-lookup"><span data-stu-id="f353a-125">XML</span></span>

<span data-ttu-id="f353a-126">Tout d’abord, recherchez le manifeste du package d’application dans votre projet actuel.</span><span class="sxs-lookup"><span data-stu-id="f353a-126">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="f353a-127">Par défaut, le manifeste sera nommé Package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="f353a-127">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="f353a-128">Si vous utilisez Visual Studio, cliquez avec le bouton droit sur le manifeste dans votre afficheur de solution, puis sélectionnez **afficher la source** pour ouvrir le fichier XML à modifier.</span><span class="sxs-lookup"><span data-stu-id="f353a-128">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="f353a-129">En haut du manifeste, ajoutez le schéma uap5 et incluez-le en tant qu’espace de noms pouvant être ignoré :</span><span class="sxs-lookup"><span data-stu-id="f353a-129">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="f353a-130">Spécifiez ensuite la valeur « MixedRealityModel » dans la vignette par défaut de votre application :</span><span class="sxs-lookup"><span data-stu-id="f353a-130">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="f353a-131">L’élément MixedRealityModel accepte un chemin de fichier pointant vers une ressource 3D stockée dans votre package d’application.</span><span class="sxs-lookup"><span data-stu-id="f353a-131">The MixedRealityModel element accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="f353a-132">Actuellement, seuls les modèles 3D fournis à l’aide du format de fichier. GLB et créés par rapport aux [instructions de création de ressources 3D Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f353a-132">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="f353a-133">Les ressources doivent être stockées dans le package d’application et l’animation n’est pas prise en charge actuellement.</span><span class="sxs-lookup"><span data-stu-id="f353a-133">Assets must be stored in the app package and animation isn't currently supported.</span></span> <span data-ttu-id="f353a-134">Si le paramètre « Path » est laissé vide, Windows affiche la ardoise 2D au lieu du lanceur 3D.</span><span class="sxs-lookup"><span data-stu-id="f353a-134">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="f353a-135">**Remarque :** la ressource. GLB doit être marquée comme « contenu » dans vos paramètres de génération avant de générer et d’exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="f353a-135">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="f353a-136">![Sélectionnez le. GLB dans votre Explorateur de solutions et utilisez la section Propriétés pour le marquer comme « contenu » dans les paramètres de génération.](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="f353a-136">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="f353a-137">*Sélectionnez le. GLB dans votre Explorateur de solutions et utilisez la section Propriétés pour le marquer comme « contenu » dans les paramètres de génération.*</span><span class="sxs-lookup"><span data-stu-id="f353a-137">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="f353a-138">Rectangle englobant</span><span class="sxs-lookup"><span data-stu-id="f353a-138">Bounding box</span></span>

<span data-ttu-id="f353a-139">Un cadre englobant peut être utilisé pour ajouter éventuellement une zone de mémoire tampon supplémentaire autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f353a-139">A bounding box can be used to optionally add an extra buffer region around the object.</span></span> <span data-ttu-id="f353a-140">Le cadre englobant est spécifié à l’aide d’un point central et d’étendues, qui indiquent la distance entre le centre du rectangle englobant et ses bords le long de chaque axe.</span><span class="sxs-lookup"><span data-stu-id="f353a-140">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="f353a-141">Les unités du cadre englobant peuvent être mappées à 1 unité = 1 mètre.</span><span class="sxs-lookup"><span data-stu-id="f353a-141">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="f353a-142">Si un cadre englobant n’est pas fourni, l’un d’eux est automatiquement ajusté à la maille de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f353a-142">If a bounding box isn't provided, then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="f353a-143">Si le cadre englobant fourni est plus petit que le modèle, il sera redimensionné pour s’ajuster à la maille.</span><span class="sxs-lookup"><span data-stu-id="f353a-143">If the provided bounding box is smaller than the model, then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="f353a-144">La prise en charge de l’attribut cadre englobant sera fournie avec la mise à jour Windows RS4 en tant que propriété sur l’élément MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="f353a-144">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="f353a-145">Pour définir un cadre englobant tout d’abord en haut du manifeste de l’application, ajoutez le schéma uap6 et incluez-le en tant qu’espaces de noms pouvant être ignorés :</span><span class="sxs-lookup"><span data-stu-id="f353a-145">To define a bounding box first at the top of the app manifest add the uap6 schema and include it as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="f353a-146">Ensuite, sur le MixedRealityModel, définissez la propriété SpatialBoundingBox pour définir le cadre englobant :</span><span class="sxs-lookup"><span data-stu-id="f353a-146">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="f353a-147">Utilisation de Unity</span><span class="sxs-lookup"><span data-stu-id="f353a-147">Using Unity</span></span>

<span data-ttu-id="f353a-148">Lorsque vous utilisez Unity, le projet doit être généré et ouvert dans Visual Studio pour que le manifeste d’application puisse être modifié.</span><span class="sxs-lookup"><span data-stu-id="f353a-148">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="f353a-149">Le lanceur 3D doit être redéfini dans le manifeste lors de la génération et du déploiement d’une nouvelle solution Visual Studio à partir d’Unity.</span><span class="sxs-lookup"><span data-stu-id="f353a-149">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="f353a-150">Liens Deep 3D (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="f353a-150">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="f353a-151">Cette fonctionnalité a été ajoutée dans le cadre de la mise à jour de 2017 automne Creators Update (RS3) pour les casques immersifs (VR) et dans le cadre de la mise à jour du 2018 d’avril (RS4) pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f353a-151">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="f353a-152">Assurez-vous que votre application cible une version du SDK Windows supérieure ou égale à 10.0.16299 sur les casques immersifs (VR) et 10.0.17125 sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f353a-152">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="f353a-153">Vous trouverez les SDK Windows les plus récentes [ici](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="f353a-153">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="f353a-154">les liens secondaryTiles (3D Deep Links) fonctionnent uniquement avec les applications UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="f353a-154">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="f353a-155">Toutefois, vous pouvez créer un [lanceur d’applications en 3D](implementing-3d-app-launchers.md) pour lancer une application exclusive à partir de la page d’hébergement de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f353a-155">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="f353a-156">Vos applications 2D peuvent être améliorées pour Windows Mixed Reality en ajoutant la possibilité de placer des modèles 3D à partir de votre application dans la [page d’accueil Windows Mixed Real](../discover/navigating-the-windows-mixed-reality-home.md) comme des liens détaillés vers le contenu au sein de votre application 2D, comme des [vignettes secondaires 2D](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) dans le menu Démarrer de Windows.</span><span class="sxs-lookup"><span data-stu-id="f353a-156">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="f353a-157">Par exemple, vous pouvez créer des photosphères de 360 ° qui se lient directement à une application de visionneuse de photos 360 °, ou permettre aux utilisateurs de placer du contenu 3D à partir d’une collection de ressources qui ouvre une page de détails à propos de l’auteur.</span><span class="sxs-lookup"><span data-stu-id="f353a-157">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="f353a-158">Il s’agit simplement de quelques façons d’étendre les fonctionnalités de votre application 2D avec du contenu 3D.</span><span class="sxs-lookup"><span data-stu-id="f353a-158">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="f353a-159">Création d’un « secondaryTile » 3D</span><span class="sxs-lookup"><span data-stu-id="f353a-159">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="f353a-160">Vous pouvez placer du contenu 3D à partir de votre application à l’aide de « secondaryTiles » en définissant un modèle de réalité mixte au moment de la création.</span><span class="sxs-lookup"><span data-stu-id="f353a-160">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="f353a-161">Les modèles de réalité mixte sont créés en référençant une ressource 3D dans votre package d’application et en définissant éventuellement un cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="f353a-161">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="f353a-162">La création de « secondaryTiles » à partir d’une vue exclusive n’est pas prise en charge actuellement.</span><span class="sxs-lookup"><span data-stu-id="f353a-162">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="f353a-163">Rectangle englobant</span><span class="sxs-lookup"><span data-stu-id="f353a-163">Bounding box</span></span>

<span data-ttu-id="f353a-164">Un cadre englobant peut être utilisé pour ajouter une zone de mémoire tampon supplémentaire autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f353a-164">A bounding box can be used to add an extra buffer region around the object.</span></span> <span data-ttu-id="f353a-165">Le cadre englobant est spécifié à l’aide d’un point central et d’étendues, qui indiquent la distance entre le centre du rectangle englobant et ses bords le long de chaque axe.</span><span class="sxs-lookup"><span data-stu-id="f353a-165">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="f353a-166">Les unités du cadre englobant peuvent être mappées à 1 unité = 1 mètre.</span><span class="sxs-lookup"><span data-stu-id="f353a-166">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="f353a-167">Si un cadre englobant n’est pas fourni, l’un d’eux est automatiquement ajusté à la maille de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f353a-167">If a bounding box isn't provided, one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="f353a-168">Si le cadre englobant fourni est plus petit que le modèle, il sera redimensionné pour s’ajuster à la maille.</span><span class="sxs-lookup"><span data-stu-id="f353a-168">If the provided bounding box is smaller than the model, it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="f353a-169">Comportement d’activation</span><span class="sxs-lookup"><span data-stu-id="f353a-169">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="f353a-170">Ce composant sera pris en charge à partir de la mise à jour de Windows RS4.</span><span class="sxs-lookup"><span data-stu-id="f353a-170">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="f353a-171">Assurez-vous que votre application cible une version du SDK Windows supérieure ou égale à 10.0.17125 si vous envisagez d’utiliser cette fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="f353a-171">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="f353a-172">Vous pouvez définir le comportement d’activation d’un secondaryTile 3D afin de contrôler la manière dont il réagit lorsqu’un utilisateur le sélectionne.</span><span class="sxs-lookup"><span data-stu-id="f353a-172">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="f353a-173">Cela peut être utilisé pour placer des objets 3D dans la zone de vie de la réalité mixte, qui sont purement informatifs ou décoratifs.</span><span class="sxs-lookup"><span data-stu-id="f353a-173">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="f353a-174">Les types de comportement d’activation suivants sont pris en charge :</span><span class="sxs-lookup"><span data-stu-id="f353a-174">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="f353a-175">Par défaut : lorsqu’un utilisateur sélectionne l’secondaryTile 3D, l’application est activée</span><span class="sxs-lookup"><span data-stu-id="f353a-175">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="f353a-176">Aucun : lorsque l’utilisateur sélectionne l’secondaryTile 3D, rien ne se produit et l’application n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="f353a-176">None: When the user selects the 3D secondaryTile nothing happens and the app isn't activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="f353a-177">Obtention et mise à jour d’un « secondaryTile » existant</span><span class="sxs-lookup"><span data-stu-id="f353a-177">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="f353a-178">Les développeurs peuvent obtenir une liste de leurs vignettes secondaires existantes, y compris les propriétés qu’ils ont spécifiées précédemment.</span><span class="sxs-lookup"><span data-stu-id="f353a-178">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="f353a-179">Ils peuvent également mettre à jour les propriétés en modifiant la valeur, puis en appelant UpdateAsync ().</span><span class="sxs-lookup"><span data-stu-id="f353a-179">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="f353a-180">Vérification de la présence de l’utilisateur dans Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f353a-180">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="f353a-181">les liens en profondeur 3D (secondaryTiles) peuvent être créés uniquement lorsque la vue est affichée dans un casque Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f353a-181">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="f353a-182">Lorsque votre vue n’est pas présentée dans un casque Windows Mixed Reality, nous vous recommandons de la traiter correctement en masquant le point d’entrée ou en indiquant un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f353a-182">When your view isn't being presented in a Windows Mixed Reality headset, we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="f353a-183">Vous pouvez vérifier cela en interrogeant [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="f353a-183">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="f353a-184">Notifications de vignette</span><span class="sxs-lookup"><span data-stu-id="f353a-184">Tile notifications</span></span>

<span data-ttu-id="f353a-185">Les notifications de vignette ne prennent pas actuellement en charge l’envoi d’une mise à jour avec une ressource 3D.</span><span class="sxs-lookup"><span data-stu-id="f353a-185">Tile notifications don't currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="f353a-186">Cela signifie que les développeurs ne peuvent pas effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f353a-186">This means that developers can't do the following:</span></span>

* <span data-ttu-id="f353a-187">Notifications Push</span><span class="sxs-lookup"><span data-stu-id="f353a-187">Push Notifications</span></span>
* <span data-ttu-id="f353a-188">Interrogation périodique</span><span class="sxs-lookup"><span data-stu-id="f353a-188">Periodic Polling</span></span>
* <span data-ttu-id="f353a-189">Notifications planifiées</span><span class="sxs-lookup"><span data-stu-id="f353a-189">Scheduled Notifications</span></span>

<span data-ttu-id="f353a-190">Pour plus d’informations sur les autres fonctionnalités et attributs de vignettes et sur la façon dont ils sont utilisés pour les vignettes 2D, consultez la [documentation vignettes pour les applications UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="f353a-190">For more information on the other tiles features and attributes and how they're used for 2D tiles, see the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="f353a-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f353a-191">See also</span></span>

* <span data-ttu-id="f353a-192">[Exemple de modèle de réalité mixte](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenant un lanceur d’application 3D.</span><span class="sxs-lookup"><span data-stu-id="f353a-192">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="f353a-193">Guide de conception du lanceur d’applications 3D</span><span class="sxs-lookup"><span data-stu-id="f353a-193">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="f353a-194">Création de modèles 3D à utiliser dans la page d’hébergement Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f353a-194">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="f353a-195">Implémentation de lanceurs d’applications en 3D (applications Win32)</span><span class="sxs-lookup"><span data-stu-id="f353a-195">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="f353a-196">Exploration de la page d’accueil Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f353a-196">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
