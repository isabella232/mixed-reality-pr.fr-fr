---
title: Configuration de l’appareil photo dans Unity
description: Découvrez comment configurer et utiliser la caméra principale d’Unity pour le développement de Windows Mixed realisation pour effectuer un rendu holographique.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, rendu holographique, holographique, immersif, point de focus, mémoire tampon de profondeur, orientation uniquement, positionnelle, opaque, transparent, clip, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636283"
---
# <a name="camera-setup-in-unity"></a>Configuration de l’appareil photo dans Unity

Quand vous portez un casque de réalité mixte, il devient le centre de votre monde holographique. Le composant [appareil photo](https://docs.unity3d.com/Manual/class-Camera.html) Unity gère automatiquement le rendu stéréoscopique et suit le mouvement et la rotation de votre tête. Toutefois, pour optimiser complètement la qualité visuelle et la [stabilité des hologrammes](../platform-capabilities-and-apis/hologram-stability.md), vous devez définir les paramètres de l’appareil photo décrits ci-dessous.

## <a name="hololens-vs-vr-immersive-headsets"></a>Casques et écouteurs immersifs HoloLens

Les paramètres par défaut du composant appareil photo Unity sont destinés aux applications 3D traditionnelles, qui nécessitent un arrière-plan skybox, car ils n’ont pas de monde réel.

* Quand vous exécutez sur un **[casque immersif](../../discover/immersive-headset-hardware-details.md)**, vous affichez tout ce que l’utilisateur voit, et vous souhaiterez probablement conserver le skybox.
* Toutefois, en cas d’exécution sur un **casque holographique** comme [HoloLens](/hololens/hololens2-hardware), le monde réel doit apparaître derrière tout ce que l’appareil photo rend. Définissez l’arrière-plan de la caméra sur transparent (dans HoloLens, le rendu noir est transparent) au lieu d’une texture skybox :
    1. Sélectionner la caméra principale dans le volet de la hiérarchie
    2. Dans le panneau Inspecteur, recherchez le composant Camera et modifiez la liste déroulante Clear Flags de skybox en Color unie
    3. Sélectionnez le sélecteur de couleur d’arrière-plan et modifiez les valeurs RVBA en (0, 0, 0, 0)
        1. Si vous définissez ce paramètre à partir du code, vous pouvez utiliser Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Installation de l'appareil photo

Quel que soit le type d’expérience que vous développez, la caméra principale est toujours le composant principal de rendu stéréo attaché à l’écran monté en tête de votre appareil. Il sera plus facile de présenter votre application si vous imaginez la position de départ de l’utilisateur comme (X : 0, Y : 0, Z : 0). Étant donné que la caméra principale effectue le suivi du mouvement de la tête de l’utilisateur, la position de départ de l’utilisateur peut être définie en définissant la position de départ de l’appareil photo principal.

Le choix central que vous devez faire est de savoir si vous développez pour des casques immersifs HoloLens ou VR. Une fois que vous avez terminé, passez à la section d’installation qui s’applique.

### <a name="hololens-camera-setup"></a>Configuration de l’appareil photo HoloLens

Pour les applications HoloLens, vous devez utiliser des ancres pour tous les objets que vous souhaitez verrouiller dans l’environnement de scène. Nous vous recommandons d’utiliser un espace non limité pour optimiser la stabilité et créer des ancres dans plusieurs pièces.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Configuration de l’appareil photo VR

Windows Mixed Reality prend en charge les applications à travers une large gamme d' [expériences](../../design/coordinate-systems.md#mixed-reality-experience-scales), des applications en orientation seule et à l’échelle à l’échelle jusqu’à des applications à l’échelle de la place. Sur HoloLens, vous pouvez aller plus loin et créer des applications à l’échelle mondiale qui permettent aux utilisateurs d’aller au-delà de 5 mètres, en explorant un étage entier d’un immeuble et au-delà.

La première étape de la création d’une expérience de réalité mixte dans Unity consiste à déterminer la mise à l' [échelle](../../design/coordinate-systems.md) ciblée par votre application :

* [Orientation ou à l’échelle assise](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Debout ou à l’échelle de l’espace](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [À l’échelle mondiale](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Expériences à l’échelle de l’espace ou à l’debout

> [!NOTE]
> Si vous générez pour HL2, nous vous recommandons de créer une expérience au niveau des yeux ou d’utiliser la [compréhension des scènes](../platform-capabilities-and-apis/scene-understanding-sdk.md) pour la raison de l’étage de votre scène.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Expériences assises

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Configuration de l’arrière-plan de l’appareil photo

Si vous utilisez MRTK, l’arrière-plan de l’appareil photo est automatiquement configuré et géré. Pour le kit de développement logiciel (SDK) XR ou les projets WSA hérités, nous vous recommandons de définir l’arrière-plan de l’appareil photo sur le noir Uni sur HoloLens et de conserver le skybox pour VR.

## <a name="using-multiple-cameras"></a>Utilisation de plusieurs caméras

Lorsqu’il existe plusieurs composants d’appareil photo dans la scène, Unity sait quelle caméra utiliser pour le rendu stéréoscopique en fonction de la balise MainCamera. Dans les XR hérités, elle utilise également cette balise pour synchroniser les têtes de suivi. Dans le kit de développement logiciel (SDK) XR, le suivi des têtes est piloté par un script TrackedPoseDriver attaché à l’appareil photo.

## <a name="sharing-depth-buffers"></a>Partage des mémoires tampons de profondeur

En partageant le tampon de profondeur de votre application sur Windows, chaque trame donne à votre application l’un des deux boosters de stabilité de l’hologramme, en fonction du type de casque pour lequel vous effectuez le rendu :

* Les **casques immersifs de VR** peuvent prendre en charge la reprojection de position lorsqu’un tampon de profondeur est fourni, en ajustant vos hologrammes pour la prédiction à la fois à la position et à l’orientation.
* Les **casques HoloLens** présentent différentes méthodes. HoloLens 1 sélectionne automatiquement un [point de focus](focus-point-in-unity.md) lorsqu’une mémoire tampon de profondeur est fournie, ce qui optimise la stabilité de l’hologramme le long du plan qui croise la plus grande partie du contenu. HoloLens 2 va stabiliser le contenu à l’aide [de Depth LSR (consultez la section Notes)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Utilisation des plans de découpage

Le rendu du contenu trop proche de l’utilisateur peut ne pas être à l’aise avec la réalité mixte. Vous pouvez ajuster les [plans de clip proches et Far](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) sur le composant de l’appareil photo.

1. Sélectionner la **caméra principale** dans le volet de la **hiérarchie**
2. Dans le panneau **inspecteur** , recherchez les plans de **découpage** du composant d' **appareil photo** et remplacez la valeur **0,3** de la zone de texte **near** par **0,85**. Le rendu du contenu est encore plus proche peut entraîner une gêne de l’utilisateur et doit être évité en fonction des [règles de distance de rendu](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).

## <a name="recentering-the-camera"></a>Recentrer l’appareil photo

Si vous créez une [expérience à l’échelle assise](../../design/coordinate-systems.md), vous pouvez recentrer l’origine du monde de l’unité à la position de la tête actuelle de l’utilisateur en appelant **[XR. Méthode InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** dans le XR hérité ou la méthode **[XRInputSubsystem. TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** dans le kit de développement logiciel (SDK) XR.

## <a name="teleportation"></a>Téléportation

Cette fonctionnalité est généralement réservée aux expériences VR :

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Modes de reprojection

Les casques HoloLens et immersif reprojeteront chaque image que votre application restituera pour s’ajuster pour une prédiction incorrecte de la position d’en-tête réelle de l’utilisateur lors de l’émission de photons.

Par défaut :

* Les **casques immersifs** prendront en charge la reprojection positionnelle si l’application fournit un tampon de profondeur pour un frame donné. Les casques immersifs ajustent également vos hologrammes pour une prédiction incorrecte à la fois dans la position et l’orientation. Si une mémoire tampon de profondeur n’est pas fournie, le système corrigera uniquement les prédictions incorrectes dans l’orientation.
* Les **casques holographiques** comme HoloLens 2 prennent en charge la reprojection de position, que l’application fournisse ou non sa mémoire tampon de profondeur. La reprojection positionnel est possible sans tampons de profondeur sur HoloLens, car le rendu est souvent épars avec un arrière-plan stable fourni par le monde réel.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core. À partir de là, vous pouvez passer au module suivant :

> [!div class="nextstepaction"]
> [Pointage du regard](gaze-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Stabilité des hologrammes](../platform-capabilities-and-apis/hologram-stability.md)
* [Échelle de l’expérience](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Étape spatiale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Suivi des pertes dans Unity](tracking-loss-in-unity.md)
* [Ancres spatiales](../../design/spatial-anchors.md)
* [Persistance dans Unity](persistence-in-unity.md)
* [Expériences partagées dans Unity](shared-experiences-in-unity.md)
* [Azure Spatial Anchors](/azure/spatial-anchors)
* [Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)