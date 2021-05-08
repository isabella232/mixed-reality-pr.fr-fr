---
title: Texte dans Unity
description: 'Pour afficher du texte dans Unity, il existe deux types de composants de texte que vous pouvez utiliser : le texte de l’interface utilisateur et le maillage de texte 3D.'
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, conception, contrôles, police, typographie, UI, UX, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: dde8989998cf422c40ada927c0d8462cb4cd97b9
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489279"
---
# <a name="text-in-unity"></a>Texte dans Unity

Le texte est l’un des composants les plus importants des applications holographiques. Pour afficher du texte dans Unity, il existe trois types de composants de texte que vous pouvez utiliser : texte de l’interface utilisateur, maillage de texte 3D et maillage Pro. Par défaut, le texte de l’interface utilisateur et le maillage de texte 3D apparaissent flous et sont trop grands. La modification de quelques variables donne un texte plus clair et de qualité supérieure avec une taille gérable dans HoloLens. Vous pouvez obtenir une meilleure qualité de rendu en appliquant un facteur d’échelle pour obtenir des dimensions appropriées lorsque vous utilisez les composants texte de l’interface utilisateur et maillage de texte 3D.

![Comment faire du texte clair et merveilleux](images/hug-text-02-640px.png)<br>
*Texte par défaut flou dans Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Utilisation du texte 3D de Unity (maillage de texte) et du texte de l’interface utilisateur

Unity suppose que tous les nouveaux éléments ajoutés à une scène représentent une unité Unity de taille, ou une échelle de transformation de 100%. Une unité Unity se traduit par environ 1 mètre sur HoloLens. Pour les polices, le cadre englobant d’un TextMesh 3D est fourni par défaut à environ 1 mètre en hauteur.

![Utilisation des polices dans Unity](images/640px-hug-text-03.png)<br>
*Le texte 3D Unity par défaut (maillage de texte) occupe une unité Unity, qui est 1 mètre*

<br>

La plupart des concepteurs visuels utilisent des points pour définir les tailles de police dans le monde réel. Il y a environ 2835 (2 834.645666399962) points dans 1 mètre. En fonction de la conversion du système de point en 1 mètre et de la taille de police de la maille du texte par défaut de l’unité de mesure 13, la simple mathématique de 13 divisée par 2835 est égale à 0,0046 (0.004586111116), ce qui offre une bonne mise à l’échelle standard pour commencer (certains peuvent souhaiter aller jusqu’à 0,005). La mise à l’échelle de l’objet ou du conteneur de texte à ces valeurs n’autorise pas seulement la conversion de 1:1 de tailles de police dans un programme de conception, mais fournit également une norme pour vous permettre de maintenir la cohérence tout au long de votre expérience.

![Mise à l’échelle des valeurs pour le texte 3D Unity et texte de l’interface utilisateur](images/Text_In_Unity_Measurements1.png)<br>
*Mise à l’échelle des valeurs pour le texte 3D Unity et texte de l’interface utilisateur*

<br>

![Maillage de texte 3D Unity avec des valeurs optimisées](images/hug-text-05-1000px.png)<br>
*Maillage de texte 3D Unity avec des valeurs optimisées*

<br>

Quand vous ajoutez un élément de texte basé sur une interface utilisateur ou un canevas à une scène, la disparité de taille est encore plus importante. Les différences entre les deux tailles sont environ 1000%, ce qui placerait le facteur d’échelle pour les composants de texte basés sur l’interface utilisateur sur 0,00046 (0.0004586111116 est exact) ou 0,0005 pour la valeur arrondie.

![Texte de l’interface utilisateur Unity avec des valeurs optimisées](images/hug-text-04-1000px.png)<br>
*Texte de l’interface utilisateur Unity avec des valeurs optimisées*

<br>

>[!NOTE]
>La valeur par défaut de toute police peut être affectée par la taille de la texture de cette police ou la manière dont la police a été importée dans Unity. Ces tests ont été exécutés en fonction de la police Arial par défaut dans Unity, ainsi que d’une autre police importée.

## <a name="working-with-text-mesh-pro"></a>Utilisation de Text Mesh Pro

Avec le texte de la maille Pro de Unity, vous pouvez sécuriser la qualité de rendu du texte. Elle prend en charge les contours de texte nets, quelle que soit la distance à l’aide de la technique du [champ à distance signée (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) . À l’aide de la méthode de calcul que nous avons utilisée ci-dessus pour le texte 3D et le texte de l’interface utilisateur, nous pouvons trouver les valeurs de mise à l’échelle appropriées à utiliser avec les points typographiques conventionnels. Étant donné que la police par défaut de maillage de texte 3D avec la taille 36 a une taille limite de 2,5 unités Unity (2,5 m), nous pouvons utiliser une valeur de mise à l’échelle de 0,005 pour obtenir la taille en points. Dans le menu de l’interface utilisateur, le texte de maillage Pro a une taille de limite par défaut de 25 unités Unity (25 millions). Cela nous donne 0,0005 pour la valeur de mise à l’échelle.

![Mise à l’échelle des valeurs pour le texte 3D Unity et l’interface utilisateur](images/Text_In_Unity_Measurements2.png)<br>
*Mise à l’échelle des valeurs pour le texte 3D Unity et l’interface utilisateur*

## <a name="recommended-text-size"></a>Taille de texte recommandée

Comme vous pouvez vous y attendre, les tailles de type que nous utilisons sur un PC ou un appareil tablette (généralement entre 12 et 32 points) semblent petite à une distance de 2 mètres. Elle dépend des caractéristiques de chaque police, mais en général, l’angle de visualisation minimal recommandé et la hauteur de police pour la lisibilité sont autour de 0.35 °-0,4 °/12.21-13.97 mm en fonction de nos études de recherche des utilisateurs. Il s’agit d’environ 35-40 PT avec le facteur de mise à l’échelle présenté ci-dessus.

Pour l’interaction proche à 0,45 m (45 cm), l’angle d’affichage de la police et de la hauteur au minimum est de 0,4 °-0,5 °/3.14 – 3,9 mm. Il s’agit d’environ 9-12 PT avec le facteur de mise à l’échelle présenté ci-dessus.

![Contenu de plage d’interaction near et Far ](images/typography-distance-1000px.jpg)
 *dans une plage d’interaction proche et éloignée*

### <a name="the-minimum-legible-font-size"></a>Taille de police minimale lisible

| Distance | Angle d’affichage | Hauteur du texte | Taille de police |
|---------|---------|---------|---------|
| 45 cm (distance de manipulation directe) | 0,4 °-0,5 ° | 3.14 – 3,9 mm | 8,9 – 11.13 PT |
| 2 m | 0.35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |


### <a name="the-comfortably-legible-font-size"></a>Taille de police lisible

| Distance | Angle d’affichage | Hauteur du texte | Taille de police |
|---------|---------|---------|---------|
| 45 cm (distance de manipulation directe) | 0,65 °-0,8 ° | 5.1-6.3 mm | 14.47-17.8 PT |
| 2 m | 0,6 °-0,75 ° | 20.9-26.2 mm | 59.4-74.2 PT |

Segoe UI (police par défaut pour Windows) fonctionne bien dans la plupart des cas. Toutefois, évitez d’utiliser des familles de polices légères ou semi-claires en petite taille, car les traits verticaux fins vibreront et la lisibilité sera dégradée. Les polices modernes avec suffisamment d’épaisseur de trait fonctionnent bien. Par exemple, Helvetica et Arial semblent exceptionnels et sont lisibles dans HoloLens avec des pondérations standard ou en gras.

![Affichage de la ](images/Text_In_Unity_ViewingAngle.jpg)
 *distance d’affichage de l’angle, angle et hauteur du texte*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Texte avec Mixed Reality Toolkit v2

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Qualité de rendu de texte précise avec une dimension appropriée

En fonction de ces facteurs de mise à l’échelle, nous avons créé le [texte prefabs avec le texte de l’interface utilisateur et le maillage de texte 3D](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text). Les développeurs peuvent utiliser ces prefabs pour optimiser le texte et la taille de police.

![Qualité de rendu de texte précise avec une dimension appropriée](images/hug-text-06-1000px.png)<br>
*Qualité de rendu de texte précise avec une dimension appropriée*

### <a name="shader-with-occlusion-support"></a>Nuanceur avec prise en charge d’occlusion

La matière de police par défaut d’Unity ne prend pas en charge l’occlusion. Pour cette raison, le texte derrière les objets est affiché par défaut. Nous avons inclus un [nuanceur simple qui prend en charge l’occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader). L’image ci-dessous montre le texte avec les éléments de police par défaut (à gauche) et le texte avec une occlusion appropriée (à droite).

![Nuanceur avec prise en charge d’occlusion](images/hug-text-07-1000px.png)<br>
*Nuanceur avec prise en charge d’occlusion*

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core. À partir d’ici, vous pouvez passer au composant suivant :

> [!div class="nextstepaction"]
> [Entrée vocale](voice-input-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Texte Prefab dans le MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [Typographie](../../design/typography.md)
