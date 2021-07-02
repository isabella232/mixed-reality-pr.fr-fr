---
title: Nuanceur standard MRTK
description: Documentation de MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, nuanceur de matériau
ms.openlocfilehash: 0a92388bc9be7c11967501709031f559f17f8966
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176442"
---
# <a name="mrtk-standard-shader"></a>Nuanceur standard MRTK

![Exemples de nuanceur standard](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

le système MRTK Standard shading utilise un nuanceur unique et flexible qui permet d’obtenir des éléments visuels similaires au nuanceur Standard de unity, d’implémenter des principes de [Système Fluent Design](https://www.microsoft.com/design/fluent/) et de rester performant sur des appareils de réalité mixte.

## <a name="example-scenes"></a>Exemples de scènes

Vous trouverez les exemples de matériel de nuanceur dans la scène **MaterialGallery** sous `MRTK/Examples/Demos/StandardShader/Scenes/` . Toutes les matières de cette scène utilisent le nuanceur MRTK/standard.

![Galerie de matériaux](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

Vous pouvez trouver une scène de comparaison pour comparer et tester le nuanceur MRTK/standard par rapport à l’exemple de nuanceur Unity/standard dans la scène **StandardMaterialComparison** sous `MRTK/Examples/Demos/StandardShader/Scenes/` .

![Comparaison de matériaux](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Architecture

Le système d’ombrage MRTK/standard est un « nuanceur uber » qui utilise la [fonctionnalité de variante de programme de nuanceur d’Unity](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) pour générer automatiquement le code de nuanceur optimal basé sur les propriétés de matériau. Lorsqu’un utilisateur sélectionne des propriétés de matériau dans l’inspecteur de matériau, il n’a d’incidence que sur les performances pour les fonctionnalités qu’il a activées.

## <a name="material-inspector"></a>Inspecteur de matériau

Un inspecteur de matériau personnalisé existe pour le nuanceur MRTK/standard appelé [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) . L’inspecteur active/désactive automatiquement les fonctionnalités du nuanceur, en fonction de la sélection de l’utilisateur et de aides dans la configuration de l’état de rendu. Pour plus d’informations sur chaque fonctionnalité **, placez le curseur sur chaque propriété de l’éditeur Unity pour une info-bulle.**

![Inspecteur de matériau](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

La première partie de l’inspecteur contrôle l’état de rendu de la matière. Le *mode de rendu* détermine quand et comment un matériau sera rendu. L’objectif du nuanceur MRTK/standard est de mettre en miroir les [modes de rendu disponibles dans le nuanceur Unity/standard](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html). Le nuanceur MRTK/standard comprend également un mode de rendu *additif* et un mode de rendu *personnalisé* pour le contrôle utilisateur complet.

| Mode de rendu |         Description                                                       |
|----------------|---------------------------------------------------------------------------|
| Opaque         | Valeurs Adapté aux objets solides normaux sans zones transparentes.    |
| Tour         | Autorise la création d’effets transparents qui ont des bords fixes entre les zones opaques et transparentes. Dans ce mode, il n’y a pas de zones semi-transparentes, la texture est soit 100% opaque, soit invisible. Cela est utile lors de l’utilisation de la transparence pour créer la forme des matériaux, tels que la végétation. |
| Fondu           | Permet aux valeurs de transparence de faire disparaître complètement un objet, y compris les surbrillances spéculaires ou les réflexions qu’il peut avoir. Ce mode est utile si vous souhaitez animer un objet en fondu ou en sortie. Il n’est pas adapté au rendu de matériaux transparents réalistes tels que le plastique ou le verre en clair, car les reflets et les surbrillances sont également délavés. |
| Transparent    | Adapté au rendu de matériaux transparents réalistes tels que le plastique clair ou le verre. Dans ce mode, le matériel lui-même prend des valeurs de transparence (en fonction du canal alpha de la texture et de l’alpha de la couleur de teinte). Toutefois, les reflets et les surbrillances d’éclairage restent visibles en toute clarté, comme c’est le cas avec les véritables matériaux transparents. |
| Additive       | Active un mode de fusion additif qui additionne la couleur de pixel précédente avec la couleur de pixel actuelle. Il s’agit du mode de transparence par défaut pour éviter les problèmes de tri de la transparence.     |
| Custom         | Permet de contrôler manuellement tous les aspects du mode de rendu. Pour une utilisation avancée uniquement.   |

![Modes de rendu](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Mode d’élimination |             Description                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Désactivé       | Désactive l’élimination des visages. L’élimination doit être définie sur OFF uniquement lorsqu’un maillage à deux côtés est requis.                                                                                        |
| Front     | Active l’élimination des faces avant.                                                                                                                                                        |
| Précédent      | Valeurs Active l' [élimination des faces arrière](https://en.wikipedia.org/wiki/Back-face_culling). L’élimination des faces arrière doit être activée aussi souvent que possible pour améliorer les performances de rendu. |

## <a name="performance"></a>Performances

L’un des principaux avantages de l’utilisation du nuanceur standard MRTK sur le nuanceur standard Unity est le niveau de performance. Le nuanceur standard MRTK est extensible pour utiliser uniquement les fonctionnalités activées. Toutefois, le nuanceur standard MRTK a également été écrit pour fournir des résultats esthétiques comparables au nuanceur standard Unity, mais à un coût nettement inférieur. Une méthode simple pour comparer les performances des nuanceurs consiste à utiliser le nombre d’opérations qui doivent être effectuées sur le GPU. Bien entendu, l’ampleur des calculs peut fluctuer selon les fonctionnalités activées et les autres configurations de rendu. Toutefois, en général, le nuanceur standard MRTK effectue un calcul beaucoup moins important que le nuanceur standard Unity.

Exemple de statistiques de nuanceur standard Unity

![Statistiques de nuanceur standard Unity](../images/performance/UnityStandardShader-Stats.PNG)

Exemple de statistiques de nuanceur standard MRTK

![Statistiques de nuanceur standard MRTK](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Ces résultats peuvent être générés en sélectionnant et en affichant une [ressource de nuanceur](https://docs.unity3d.com/Manual/class-Shader.html) dans l’inspecteur Unity, puis en cliquant sur le bouton *compiler et afficher le code* .

## <a name="lighting"></a>Éclairage

MRTK/standard utilise une approximation simple pour l’éclairage. Étant donné que ce nuanceur ne calcule pas l’exactitude physique et la conservation de l’énergie, il s’affiche rapidement et efficacement. Blinn-Phong est la technique d’éclairage principale qui est mélangée avec la Fresnel et l’éclairage à base d’image pour atteindre un éclairage physique approximatif. Le nuanceur prend en charge les techniques d’éclairage suivantes :

### <a name="directional-light"></a>Lumière directionnelle

Le nuanceur respecte la direction, la couleur et l’intensité de la première lumière directionnelle dans la scène (si elle est activée). Les lumières de point dynamique, les éclairages ponctuels ou tout autre éclairage Unity ne sont pas pris en compte dans l’éclairage en temps réel.

### <a name="spherical-harmonics"></a>Harmoniques sphériques

Le nuanceur utilise des sondes légères pour rapprocher les lumières de la scène à l’aide d' [harmoniques sphériques](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html), si elles sont activées. Les calculs d’harmoniques sphériques sont effectués par vertex pour réduire le coût de calcul.

### <a name="lightmapping"></a>Lightmapping

Pour l’éclairage statique, le nuanceur respecte lightmaps généré par le [système Lightmapping](https://docs.unity3d.com/Manual/Lightmapping.html)Unity. Marquez simplement le convertisseur comme static (ou lightmap static) pour utiliser lightmaps.

### <a name="hover-light"></a>Pointage

* Voir [point pointé](hover-light.md)

### <a name="proximity-light"></a>Lumière de proximité

* Voir la [lumière de proximité](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Prise en charge du pipeline de rendu scriptable léger

Le MRTK contient un chemin de mise à niveau pour permettre aux développeurs d’utiliser le pipeline de rendu scriptable léger d’Unity (LWRP) avec des nuanceurs MRTK. Testé dans Unity 2019.1.1 F1 et le package léger RP 5.7.2. pour obtenir des instructions sur la prise en main de LWRP, consultez [cette page](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).

pour effectuer la mise à niveau de MRTK, sélectionnez : **Shared Computer Toolkit de la réalité mixte-> utilitaires-> mettre à niveau MRTK nuanceur Standard pour le pipeline de rendu léger**

![mise à niveau lwrp](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Une fois la mise à niveau effectuée, le nuanceur MRTK/standard est modifié et tout matériau magenta (erreur de nuanceur) doit être corrigé. Pour vérifier que la mise à niveau s’est correctement déroulée, consultez la console pour : **ressources mises à niveau/MixedRealityToolkit/StandardAssets/shaders/MixedRealityStandard. Shader à utiliser avec le pipeline de rendu léger.**

## <a name="ugui-support"></a>Support UGUI

Le système d’ombrage standard MRTK fonctionne avec le [système d’interface utilisateur](https://docs.unity3d.com/Manual/UISystem.html)intégré de Unity. Sur les composants de l’interface utilisateur Unity, la matrice de unity_ObjectToWorld n’est pas la matrice de transformation de la transformation locale sur laquelle se trouve le composant graphique, mais celle de sa zone de dessin parente. De nombreux effets de nuanceur MRTK/standard requièrent une mise à l’échelle des objets. Pour résoudre ce problème, le [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) stocke les informations de mise à l’échelle dans les attributs de canal UV lors de la construction du maillage de l’interface utilisateur.

Notez que, lors de l’utilisation d’un composant d’image Unity, il est recommandé de spécifier « None (sprite) » pour l’image source afin d’empêcher l’interface utilisateur Unity de générer des vertex supplémentaires.

Un canevas dans le MRTK demande l’ajout d’un lorsqu’un [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) élément est requis :

![effet de maillage de l’échelle](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Combinateur de texture

Pour améliorer la parité avec le nuanceur standard par pixel, les valeurs de lissage, de douceur, de émissif et d’occlusion peuvent toutes être contrôlées via la [compression de canal](http://wiki.polycount.com/wiki/ChannelPacking). Par exemple :

![exemple de carte de canal](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Lorsque vous utilisez la compression de canal, il vous suffit d’échantillonner et de charger une seule texture en mémoire au lieu de quatre. Lorsque vous écrivez vos cartes de texture dans un programme comme une substance ou Photoshop, vous pouvez les emporter comme suit :

| Canal | Propriété             |
|---------|----------------------|
| Rouge     | Calculée             |
| Vert   | Occlusion            |
| Bleu    | Émission (nuances de gris) |
| Alpha   | Fluidité           |

Vous pouvez utiliser l’outil combinateur de texture MRTK. pour ouvrir l’outil, sélectionnez : **Shared Computer Toolkit de la réalité mixte-> utilitaires-> combinateur de Texture** qui ouvre la fenêtre suivante :

![exemple de combinateur de texture](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Cette fenêtre peut être remplie automatiquement en sélectionnant un nuanceur standard Unity et en cliquant sur « remplir automatiquement à partir d’un matériau standard ». Ou vous pouvez spécifier manuellement une texture (ou une valeur constante) par canal rouge, vert, bleu ou alpha. La combinaison de texture est accélérée GPU et ne nécessite pas que la texture d’entrée soit accessible par le processeur.

## <a name="additional-feature-documentation"></a>Documentation supplémentaire sur les fonctionnalités

Vous trouverez ci-dessous des informations supplémentaires sur quelques détails sur les fonctionnalités disponibles avec le nuanceur MRTK/standard.

### <a name="primitive-clipping"></a>Découpage primitif

![découpage primitif](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* Consultez la [primitive de découpage](clipping-primitive.md)

### <a name="mesh-outlines"></a>Contours de maillage

De nombreuses techniques de contour de maille sont effectuées à l’aide d’une technique de [validation de traitement](https://docs.unity3d.com/Manual/PostProcessingOverview.html) . Le traitement de la publication fournit des contours de grande qualité, mais peut être prohibitif sur de nombreux appareils de réalité mixte. Vous pouvez trouver une scène illustrant l’utilisation des contours de maillage dans la scène  **OutlineExamples** sous `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) et [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) peuvent être utilisés pour restituer un contour autour d’un convertisseur de maillage. L’activation de ce composant introduit une passe de rendu supplémentaire de l’objet en cours de présentation, mais est conçu pour exécuter efficacement sur les appareils de réalité mixte mobile et n’utilise pas de processus de publication. Les limitations de cet effet incluent le non-fonctionnement des objets qui ne sont pas étanches (ou doivent être deux faces) et les problèmes de tri de profondeur peuvent se produire sur les objets qui se chevauchent.

Les comportements de plan sont conçus pour être utilisés conjointement avec le nuanceur MRTK/standard. Les matériaux de contour sont généralement une couleur de non éclairé solide, mais peuvent être configurés pour obtenir un grand nombre d’effets. La configuration par défaut d’un matériau en mode plan est la suivante :

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. Écriture de profondeur-doit être désactivée pour que les matériaux de contour s’assurent que le plan n’empêche pas d’autres objets de s’afficher.
2. Extrusion de vertex : doit être activé pour restituer le plan.
3. Utiliser des normales régulières : ce paramètre est facultatif pour certains maillages. L’extrusion se produit en déplaçant un sommet perpendiculairement à un sommet, sur certaines mailles extrudées le long des normales par défaut entraînent des discontinuités dans le contour. Pour corriger ces discontinuités, vous pouvez cocher cette case pour utiliser un autre ensemble de normales lissées générée par [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) est un composant qui peut être utilisé pour générer automatiquement des normales lissées sur une maille. Cette méthode regroupe les vertex d’une maille qui partagent le même emplacement dans l’espace, puis calcule la moyenne des normales de ces sommets. Ce processus crée une copie de la maille sous-jacente et doit être utilisé uniquement lorsque cela est nécessaire.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. Normaliser les normales générées via [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) .
2. Normals utilisés par défaut, notez les artefacts autour des angles du cube.

### <a name="stencil-testing"></a>Test de stencil

Prise en charge des tests de stencil configurables pour obtenir un grand nombre d’effets. Tels que les portails :

![test de stencil](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Prise en charge des couleurs d’instance

La prise en charge des couleurs instanciées pour fournir des milliers d’instances GPU maille des propriétés de matériau uniques :

![Propriétés d’instance](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Mappage triplanaire

Le mappage triplanaire est une technique qui permet de texturer un maillage par programmation. Souvent utilisées dans le terrain, les mailles sans UVs ou les formes difficiles à désencapsuler. Cette implémentation prend en charge la projection de l’espace universel ou local, la spécification du lissage de fusion et la prise en charge normale des cartes. Notez que chaque texture utilisée nécessite 3 échantillons de texture. Utilisez-la avec modération dans des situations de performances critiques.

![triplanaire](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Extrusion de vertex

Extrusion de vertex dans l’espace universel. Utile pour la visualisation des volumes englobants extrudés ou des transitions entrantes/sortantes.

![mise à l’échelle normale de la carte 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Divers

Case à cocher pour contrôler les optimisations de Albedo. En tant qu’optimisation, les opérations Albedo sont désactivées quand aucune texture Albedo n’est spécifiée. Cela est utile pour contrôler le [chargement de textures distantes](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html).

Cochez simplement cette case :

![assignation albedo](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

Les textures de découpage par pixel, l’anticrénelage basé sur les périphéries locales et la mise à l’échelle normale des mappages sont prises en charge.

![mise à l’échelle normale de la carte 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Voir aussi

* [Avec interaction](../ux-building-blocks/interactable.md)
* [Lumière lointaine](hover-light.md)
* [Lumière proche](proximity-light.md)
* [Primitive de découpage](clipping-primitive.md)
