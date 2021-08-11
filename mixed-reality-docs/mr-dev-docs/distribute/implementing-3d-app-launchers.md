---
title: Implémenter des lanceurs d’applications 3D (applications UWP)
description: découvrez comment créer des lanceurs et des logos d’applications en 3d pour Windows Mixed Reality des applications et des jeux UWP sur des casques HoloLens et VR.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icône, modélisation, lanceur, lanceur 3D, vignette, cube en direct, lien profond, secondarytile, vignette secondaire, UWP, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, XML, cadre englobant, Unity
ms.openlocfilehash: b0ccff2aaba9c4693f58b134cdb3af9190b59befec0b31851273ed6a3bc1fc04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196418"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implémenter des lanceurs d’applications 3D (applications UWP)

> [!NOTE]
> cette fonctionnalité a été ajoutée dans le cadre de la mise à jour 2017 automne Creators (RS3) pour les casques immersifs et est prise en charge par HoloLens avec la mise à jour Windows 10 avril 2018. assurez-vous que votre application cible une version de la SDK Windows supérieure ou égale à 10.0.16299 sur les casques immersifs et 10.0.17125 sur HoloLens. vous trouverez les SDK Windows les plus récentes [ici](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

la [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) à la base est le point de départ où les utilisateurs se trouvent avant de lancer des applications. lors de la création d’une application UWP pour Windows Mixed Reality, par défaut, les applications sont lancées en tant qu’ardoise 2d avec le logo de leur application. lors du développement d’expériences pour Windows Mixed Reality, un lanceur 3d peut éventuellement être défini pour remplacer le lanceur 2d par défaut de votre application. en règle générale, les lanceurs 3d sont recommandés pour lancer des applications immersives qui tirent les utilisateurs de la Windows Mixed Reality. Le lanceur 2D par défaut est préféré lorsque l’application est activée sur place. Vous pouvez également créer un [lien profond en 3D (secondaryTile)](#3d-deep-links-secondarytiles) en tant que lanceur en 3D pour le contenu d’une application UWP 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>processus de création du lanceur d’applications 3D

La création d’un lanceur d’applications 3D comporte trois étapes :
1. [Conception et concept](3d-app-launcher-design-guidance.md)
2. [Modélisation et exportation](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Intégration dans votre application (cet article)

les ressources 3d à utiliser comme lanceurs pour votre application doivent être créées à l’aide des [instructions de création de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) pour garantir la compatibilité. les ressources qui ne satisfont pas à cette spécification de création ne seront pas affichées dans la Windows Mixed Reality page d’hébergement.

## <a name="configuring-the-3d-launcher"></a>Configuration du lanceur 3D

Lorsque vous créez un projet dans Visual Studio, cela a pour effet de créer une vignette par défaut simple qui affiche le nom et le logo de votre application. Pour remplacer cette représentation 2D par un modèle 3D personnalisé, modifiez le manifeste d’application de votre application de manière à inclure l’élément « MixedRealityModel » dans le cadre de votre définition de vignette par défaut. Pour revenir au lanceur 2D, supprimez simplement la définition MixedRealityModel du manifeste.

### <a name="xml"></a>XML

Tout d’abord, recherchez le manifeste du package d’application dans votre projet actuel. Par défaut, le manifeste sera nommé Package. appxmanifest. si vous utilisez Visual Studio, cliquez avec le bouton droit sur le manifeste dans votre afficheur de solution, puis sélectionnez **afficher la source** pour ouvrir le fichier xml à modifier. 

En haut du manifeste, ajoutez le schéma uap5 et incluez-le en tant qu’espace de noms pouvant être ignoré :

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Spécifiez ensuite la valeur « MixedRealityModel » dans la vignette par défaut de votre application :

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

L’élément MixedRealityModel accepte un chemin de fichier pointant vers une ressource 3D stockée dans votre package d’application. actuellement, seuls les modèles 3d fournis à l’aide du format de fichier. glb et créés sur les [instructions de création de ressources 3d Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) sont pris en charge. Les ressources doivent être stockées dans le package d’application et l’animation n’est pas prise en charge actuellement. si le paramètre « Path » est laissé vide Windows affiche la ardoise 2d au lieu du lanceur 3d. **Remarque :** la ressource. GLB doit être marquée comme « contenu » dans vos paramètres de génération avant de générer et d’exécuter votre application.


![Sélectionnez le. GLB dans votre Explorateur de solutions et utilisez la section Propriétés pour le marquer comme « contenu » dans les paramètres de génération.](images/buildsetting-content-300px.png)<br>
*Sélectionnez le. GLB dans votre Explorateur de solutions et utilisez la section Propriétés pour le marquer comme « contenu » dans les paramètres de génération.*

### <a name="bounding-box"></a>Rectangle englobant

Un cadre englobant peut être utilisé pour ajouter éventuellement une zone de mémoire tampon supplémentaire autour de l’objet. Le cadre englobant est spécifié à l’aide d’un point central et d’étendues, qui indiquent la distance entre le centre du rectangle englobant et ses bords le long de chaque axe. Les unités du cadre englobant peuvent être mappées à 1 unité = 1 mètre. Si un cadre englobant n’est pas fourni, l’un d’eux est automatiquement ajusté à la maille de l’objet. Si le cadre englobant fourni est plus petit que le modèle, il sera redimensionné pour s’ajuster à la maille.

la prise en charge de l’attribut cadre englobant est fournie avec la Windows mise à jour RS4 en tant que propriété sur l’élément MixedRealityModel. Pour définir un cadre englobant tout d’abord en haut du manifeste de l’application, ajoutez le schéma uap6 et incluez-le en tant qu’espaces de noms pouvant être ignorés :

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Ensuite, sur le MixedRealityModel, définissez la propriété SpatialBoundingBox pour définir le cadre englobant : 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Utilisation de Unity

lorsque vous utilisez unity, le projet doit être généré et ouvert dans Visual Studio pour que le manifeste de l’application puisse être modifié. 

>[!NOTE]
>le lanceur 3d doit être redéfini dans le manifeste lors de la génération et du déploiement d’une nouvelle solution Visual Studio à partir d’unity.

## <a name="3d-deep-links-secondarytiles"></a>Liens Deep 3D (secondaryTiles)

> [!NOTE]
> Cette fonctionnalité a été ajoutée dans le cadre de la mise à jour 2017 automne Creators Update (RS3) pour les casques immersifs (VR) et dans le cadre de la mise à jour du 2018 d’avril (RS4) pour HoloLens. assurez-vous que votre application cible une version de la SDK Windows supérieure ou égale à 10.0.16299 sur les casques immersifs (VR) et 10.0.17125 sur HoloLens. vous trouverez les SDK Windows les plus récentes [ici](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>les liens secondaryTiles (3D Deep Links) fonctionnent uniquement avec les applications UWP 2D. toutefois, vous pouvez créer un [lanceur d’applications en 3d](implementing-3d-app-launchers.md) pour lancer une application exclusive à partir de la Windows Mixed Reality page d’hébergement.

vos applications 2d peuvent être améliorées pour Windows Mixed Reality en ajoutant la possibilité de placer des modèles 3d à partir de votre application dans la [Windows Mixed Reality famille](../discover/navigating-the-windows-mixed-reality-home.md) en tant que liens détaillés vers le contenu au sein de votre application 2d, comme les [vignettes secondaires 2d](/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) sur le menu Démarrer de Windows. Par exemple, vous pouvez créer des photosphères de 360 ° qui se lient directement à une application de visionneuse de photos 360 °, ou permettre aux utilisateurs de placer du contenu 3D à partir d’une collection de ressources qui ouvre une page de détails à propos de l’auteur. Il s’agit simplement de quelques façons d’étendre les fonctionnalités de votre application 2D avec du contenu 3D.

### <a name="creating-a-3d-secondarytile"></a>Création d’un « secondaryTile » 3D

Vous pouvez placer du contenu 3D à partir de votre application à l’aide de « secondaryTiles » en définissant un modèle de réalité mixte au moment de la création. Les modèles de réalité mixte sont créés en référençant une ressource 3D dans votre package d’application et en définissant éventuellement un cadre englobant. 

> [!NOTE]
> La création de « secondaryTiles » à partir d’une vue exclusive n’est pas prise en charge actuellement.

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

### <a name="bounding-box"></a>Rectangle englobant

Un cadre englobant peut être utilisé pour ajouter une zone de mémoire tampon supplémentaire autour de l’objet. Le cadre englobant est spécifié à l’aide d’un point central et d’étendues, qui indiquent la distance entre le centre du rectangle englobant et ses bords le long de chaque axe. Les unités du cadre englobant peuvent être mappées à 1 unité = 1 mètre. Si un cadre englobant n’est pas fourni, l’un d’eux est automatiquement ajusté à la maille de l’objet. Si le cadre englobant fourni est plus petit que le modèle, il sera redimensionné pour s’ajuster à la maille.

### <a name="activation-behavior"></a>Comportement d’activation

> [!NOTE]
> ce composant sera pris en charge à partir de la Windows mise à jour RS4. assurez-vous que votre application cible une version du SDK Windows supérieure ou égale à 10.0.17125 si vous envisagez d’utiliser cette fonctionnalité

Vous pouvez définir le comportement d’activation d’un secondaryTile 3D afin de contrôler la manière dont il réagit lorsqu’un utilisateur le sélectionne. Cela peut être utilisé pour placer des objets 3D dans la zone de vie de la réalité mixte, qui sont purement informatifs ou décoratifs. Les types de comportement d’activation suivants sont pris en charge :
1. Par défaut : lorsqu’un utilisateur sélectionne l’secondaryTile 3D, l’application est activée
2. Aucun : lorsque l’utilisateur sélectionne l’secondaryTile 3D, rien ne se produit et l’application n’est pas activée.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Obtention et mise à jour d’un « secondaryTile » existant

Les développeurs peuvent obtenir une liste de leurs vignettes secondaires existantes, y compris les propriétés qu’ils ont spécifiées précédemment. Ils peuvent également mettre à jour les propriétés en modifiant la valeur, puis en appelant UpdateAsync ().

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Vérification de l’existence de l’utilisateur dans Windows Mixed Reality

les liens en profondeur 3d (secondaryTiles) peuvent être créés uniquement lorsque la vue est affichée dans un Windows Mixed Reality casque. lorsque votre vue n’est pas présentée dans un Windows Mixed Reality casque, nous vous recommandons de la traiter correctement en masquant le point d’entrée ou en indiquant un message d’erreur. Vous pouvez vérifier cela en interrogeant [IsCurrentViewPresentedOnHolographic ()](/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Notifications de vignette

Les notifications de vignette ne prennent pas actuellement en charge l’envoi d’une mise à jour avec une ressource 3D. Cela signifie que les développeurs ne peuvent pas effectuer les opérations suivantes :

* Notifications Push
* Interrogation périodique
* Notifications planifiées

Pour plus d’informations sur les autres fonctionnalités et attributs de vignettes et sur la façon dont ils sont utilisés pour les vignettes 2D, consultez la [documentation vignettes pour les applications UWP](/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Voir aussi

* [Exemple de modèle de réalité mixte](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenant un lanceur d’application 3D.
* [Guide de conception du lanceur d’applications 3D](3d-app-launcher-design-guidance.md)
* [création de modèles 3d à utiliser dans la Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implémentation de lanceurs d’applications en 3D (applications Win32)](implementing-3d-app-launchers-win32.md)
* [Exploration de la page d’accueil Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)