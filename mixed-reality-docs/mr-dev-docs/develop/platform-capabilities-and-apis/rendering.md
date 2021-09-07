---
title: Rendu
description: Découvrez comment le rendu holographique permet à votre application de dessiner un hologramme dans un endroit précis dans le monde autour de l’utilisateur.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: rendu, hologramme
ms.openlocfilehash: 5bd06b9ca521e489a8944a1813b735a0fe1d60a5
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244230"
---
# <a name="holographic-rendering"></a>Rendu holographique

Le rendu holographique permet à votre application de dessiner un hologramme à un endroit précis dans le monde autour de l’utilisateur, qu’il soit placé précisément dans le monde physique ou dans un domaine virtuel que vous avez créé. [Hologrammes](../../discover/hologram.md) sont des objets de sons et de lumière. Le rendu permet à votre application d’ajouter la lumière.

## <a name="device-support"></a>Prise en charge des appareils

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Fonctionnalité</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (première génération)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
    </tr>
     <tr>
        <td>Rendu</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Rendu holographique

La clé du rendu holographique est de savoir quel type de périphérique est utilisé. les appareils avec des **affichages (voir**, par exemple [HoloLens](/hololens/hololens1-hardware)) ajoutent de la lumière au monde. Les pixels noirs sont entièrement transparents, tandis que les pixels plus clairs sont de plus en plus opaques. Étant donné que la lumière des écrans est ajoutée à la lumière du monde réel, les pixels blancs sont translucides.

Alors que le rendu stéréoscopique fournit une seule profondeur pour vos hologrammes, l’ajout d' [effets de terre](../../design/interaction-fundamentals.md) peut aider les utilisateurs à voir plus facilement l’aire de conception d’un hologramme. Une technique de mise à la terre consiste à ajouter une lueur autour d’un hologramme sur la surface adjacente, puis à effectuer le rendu d’une ombre contre cette lueur. De cette façon, votre ombre s’affiche pour soustraire la lumière de l’environnement. Le [son spatial](../../design/spatial-sound.md) est une autre indication de profondeur importante qui permet aux utilisateurs de connaître la distance et l’emplacement relatif d’un hologramme.

les appareils avec des **écrans opaques**, comme [Windows Mixed Reality des casques immersifs](../../discover/immersive-headset-hardware-details.md), bloquent le monde. Les pixels noirs sont noirs et toute autre couleur apparaît en tant que couleur pour l’utilisateur. Votre application est responsable du rendu de tout ce que l’utilisateur voit. Il est donc encore plus important de maintenir une fréquence d’actualisation constante pour que les utilisateurs bénéficient d’une expérience confortable.

## <a name="predicted-rendering-parameters"></a>Paramètres de rendu prédits

les casques de réalité mixte (HoloLens et les casques immersifs) suivent continuellement la position et l’orientation de la tête de l’utilisateur par rapport à son environnement. Au fur et à mesure que votre application commence à préparer son image suivante, le système prédit l’endroit où la tête de l’utilisateur sera à l’avenir à l’instant où le cadre apparaît sur les affichages. Sur la base de cette prédiction, le système calcule la vue et les transformations de projection à utiliser pour cette image. Votre application **doit utiliser ces transformations pour produire des résultats corrects**. Si les transformations fournies par le système ne sont pas utilisées, l’image obtenue ne s’alignera pas sur le monde réel, conduisant à la gêne de l’utilisateur.

> [!NOTE]
> Pour prédire précisément quand un nouveau Frame atteindra les affichages, le système mesure constamment la latence de bout en bout du pipeline de rendu de votre application. Tandis que le système s’ajuste à la longueur de votre pipeline de rendu, vous pouvez améliorer la stabilité de l’hologramme en gardant ce pipeline aussi rapidement que possible.

Les applications qui utilisent des techniques avancées pour augmenter la prédiction système peuvent remplacer les transformations de la vue système et de la projection. Ces applications doivent toujours utiliser les transformations fournies par le système comme base pour leurs transformations personnalisées afin de produire des résultats significatifs.

## <a name="other-rendering-parameters"></a>Autres paramètres de rendu

Lors du rendu d’un frame, le système spécifie la fenêtre d’affichage de mémoire tampon d’arrière-plan dans laquelle votre application doit être dessinée. Cette fenêtre d’affichage est souvent inférieure à la taille totale de la mémoire tampon de trame. Quelle que soit la taille de la fenêtre d’affichage, une fois que l’image est rendue par l’application, le système mise à l’échelle de l’image pour remplir l’intégralité des affichages.

Pour les applications qui ne parviennent pas à effectuer un rendu au taux de rafraîchissement requis, les [paramètres de rendu du système peuvent être configurés](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) pour réduire la sollicitation de la mémoire et le coût du rendu au détriment de l’augmentation des alias de pixels. Le format de la mémoire tampon d’arrière-plan peut également être modifié, ce qui, pour certaines applications, peut contribuer à améliorer la bande passante de mémoire et le débit de pixels.

Le rendu frustum, la résolution et la fréquence d’images dans lesquelles votre application est invitée à effectuer le rendu peuvent également changer d’une image à l’autre, et peuvent varier en fonction de l’œil gauche et du droit. Par exemple, lorsque la capture de la [réalité mixte](/hololens/holographic-photos-and-videos) (MRC) est active et que la configuration de la [vue caméra photo/vidéo](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) n’est pas activée, un œil peut être rendu avec un angle ou une résolution plus élevé.

Pour tout Frame donné, votre application *doit* être rendue à l’aide de la transformation de vue, de la transformation de projection et de la résolution de la fenêtre d’affichage fournie par le système. En outre, votre application ne doit jamais supposer qu’un paramètre de rendu ou de vue reste fixe d’une image à l’autre. Les moteurs comme Unity gèrent toutes ces transformations dans leurs propres objets Camera afin que le déplacement physique de vos utilisateurs et l’état du système soient toujours respectés. Si votre application autorise un déplacement virtuel de l’utilisateur par le biais du monde (par exemple, en utilisant le stick analogique sur un boîtier de manette), vous pouvez ajouter un objet de plateforme parente au-dessus de l’appareil photo qui le déplace. Ainsi, l’appareil photo reflète à la fois le mouvement virtuel et physique de l’utilisateur. Si votre application modifie la dimension de vue, transformation de projection ou fenêtre d’affichage fournie par le système, elle doit informer le système en appelant l' [API de remplacement](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)appropriée.

pour améliorer la stabilité de votre rendu holographique, votre application doit fournir à Windows chaque frame le tampon de profondeur utilisé pour le rendu. Si votre application fournit un tampon de profondeur, elle doit avoir des valeurs de profondeur cohérentes, en profondeur exprimées en mètres de l’appareil photo. Cela permet au système d’utiliser vos données de profondeur par pixel pour mieux stabiliser le contenu si la tête de l’utilisateur se termine légèrement par rapport à l’emplacement prédit. Si vous n’êtes pas en mesure de fournir votre tampon de profondeur, vous pouvez fournir un point de mise en évidence et normal, définissant un plan qui coupe la majeure partie de votre contenu. Si le tampon de profondeur et un plan de focus sont fournis, le système peut utiliser les deux. En particulier, il est utile de fournir à la fois le tampon de profondeur et un point de focus qui comprend un vecteur de vélocité lorsque votre application affiche des hologrammes en mouvement.

Reportez-vous à l’article [rendu dans DirectX](../native/rendering-in-directx.md) pour obtenir des informations de bas niveau sur cette rubrique.

## <a name="holographic-cameras"></a>Caméras holographiques

Windows Mixed Reality introduit le concept de **caméra holographique**. Les caméras holographiques sont similaires à l’appareil photo traditionnel qui se trouve dans les textes graphiques en 3D. ils définissent à la fois les propriétés extrinsèques (position et orientation) et les propriétés de caméra intrinsèques. (Par exemple, le champ de vue est utilisé pour afficher une scène 3D virtuelle.) Contrairement aux caméras 3D traditionnelles, l’application n’est pas en mesure de contrôler la position, l’orientation et les propriétés intrinsèques de l’appareil photo. Au lieu de cela, la position et l’orientation de la caméra holographique sont contrôlées implicitement par le mouvement de l’utilisateur. Le mouvement de l’utilisateur est relayé à l’application image par image via une transformation de vue. De même, les propriétés intrinsèques de l’appareil photo sont définies par les optiques calibrées de l’appareil et relayées par frame via la transformation de projection.

En général, votre application s’affiche pour une seule caméra stéréo. Une boucle de rendu robuste prend en charge plusieurs caméras et prend en charge les caméras mono et stéréo. Par exemple, le système peut demander à votre application de s’afficher à partir d’une autre perspective lorsque l’utilisateur active une fonctionnalité comme la [capture de réalité mixte](/hololens/holographic-photos-and-videos) (MRC), en fonction de la forme du casque. Les applications qui peuvent prendre en charge plusieurs caméras les obtiennent en [choisissant](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) le [type](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) de caméra qu’elles peuvent prendre en charge.

## <a name="volume-rendering"></a>Rendu du volume

Lors du rendu des radiographie médicaux ou des volumes d’ingénierie en 3D, les techniques de [rendu de volume](volume-rendering.md) sont souvent utilisées. Ces techniques peuvent être intéressantes en réalité mixte, où les utilisateurs peuvent visualiser naturellement ce volume à partir des angles clés, simplement en déplaçant leur tête.

## <a name="supported-resolutions-on-hololens-first-gen"></a>résolutions prises en charge sur HoloLens (première génération)

* La taille maximale de la fenêtre d’affichage est une propriété du [HolographicDisplay](/uwp/api/windows.graphics.holographic.holographicdisplay). HoloLens est défini sur la taille maximale de la fenêtre d’affichage, à savoir 720p (1268x720) par défaut.
* La taille de la fenêtre d’affichage peut être modifiée en définissant ViewportScaleFactor sur HolographicCamera. Ce facteur d’échelle est compris entre 0 et 1.
* la taille de la fenêtre d’affichage la plus faible prise en charge sur HoloLens (première génération) est de 50% de 720p, soit 360p (634x360). Il s’agit d’un ViewportScaleFactor de 0,5.
* Toute valeur inférieure à 540p n’est pas recommandée en raison de la dégradation visuelle, mais elle peut être utilisée pour identifier les goulots d’étranglement dans le taux de remplissage des pixels.

## <a name="supported-resolutions-on-hololens-2"></a>Résolutions prises en charge sur HoloLens 2

* Les tailles de cible de rendu actuelles et maximales prises en charge sont les propriétés de la configuration de la [vue](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens 2 est défini sur la taille maximale de la cible de rendu, qui est 1440x936 par défaut.
* Les applications peuvent modifier la taille des mémoires tampons cibles de rendu en appelant la méthode RequestRenderTargetSize pour demander une nouvelle taille de cible de rendu. Une nouvelle taille de cible de rendu sera choisie, qui atteint ou dépasse la taille de la cible de rendu demandée. Cette API modifie la taille de la mémoire tampon de la cible de rendu, qui nécessite une réallocation de mémoire sur le GPU. Les implications de cette méthode sont les suivantes : la taille de la cible de rendu peut être réduite pour réduire la sollicitation de la mémoire sur le GPU, et cette méthode ne doit pas être appelée à fréquence élevée.
* les applications peuvent toujours modifier la taille de la fenêtre d’affichage de la même façon que pour HoloLens 1. Aucune réallocation de mémoire n’a été ajoutée sur le GPU, il peut donc être modifié à fréquence élevée, mais ne peut pas être utilisé pour réduire la sollicitation de la mémoire sur le GPU.
* la taille de la fenêtre d’affichage la plus basse prise en charge sur HoloLens 2 est 634x412, un ViewportScaleFactor d’environ 0,44 lorsque la taille de la cible de rendu par défaut est utilisée.
* Si la taille de la cible de rendu est inférieure à la taille de la fenêtre d’affichage la plus basse prise en charge, le facteur d’échelle de la fenêtre d’affichage est ignoré.
* Toute valeur inférieure à 540p n’est pas recommandée en raison de la dégradation visuelle, mais elle peut être utilisée pour identifier les goulots d’étranglement dans le taux de remplissage des pixels.



## <a name="see-also"></a>Voir aussi
* [Stabilité des hologrammes](hologram-stability.md)
* [Rendu dans DirectX](../native/rendering-in-directx.md)