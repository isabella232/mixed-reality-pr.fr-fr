---
title: Créer des modèles 3D à utiliser dans la page d’accueil
description: exigences relatives aux ressources et aide à la création de modèles 3d à utiliser dans le Windows Mixed Reality à la page d’habitation sur les casques HoloLens et immersifs (VR).
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, modélisation, Guide de modélisation, besoins en ressources, instructions de création, lanceur, lanceur 3D, texture, matériaux, complexité, triangles, maillage, polygones, polynombre, limites, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 9fdd485c67a757d40b049c08f114ce9982aafc27e9103c4b31c21fd8af08d186
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207679"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Créer des modèles 3D à utiliser dans la page d’accueil

la [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) à la base est le point de départ où les utilisateurs se trouvent avant de lancer des applications. lorsque vous concevez votre application pour Windows Mixed Reality casques, utilisez un [modèle 3d en tant que lanceur d’applications](implementing-3d-app-launchers.md) et placez [des liens profond en 3d dans la Windows Mixed Reality page d’origine](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles). cet article décrit les instructions pour la création de modèles 3d compatibles avec la Windows Mixed Reality page d’hébergement.

## <a name="asset-requirements-overview"></a>Présentation des exigences relatives aux ressources

lors de la création de modèles 3d pour Windows Mixed Reality, toutes les ressources doivent remplir les conditions suivantes : 
1. L' [exportation](#exporting-models) des ressources doit être fournie au format de fichier. GLB (binaire glTF)
2. La [modélisation](#modeling-guidelines) des ressources doit être inférieure à 10 Ko, ne pas comporter plus de 64 nœuds et des sous-maillages 32 par LOD
3. [Matériaux](#material-guidelines) -les textures ne peuvent pas être supérieures à 4096 x 4096 et la plus petite carte MIP ne doit pas être supérieure à 4 sur l’une ou l’autre des dimensions
4. [Animation](#animation-guidelines) : les animations ne peuvent pas dépasser 20 minutes à 30 i/s (images clés 36 000) et doivent contenir <= 8192 sommets cibles Morph
5. [Optimisation](#optimizations) -les ressources doivent être optimisées à l’aide de [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). *requis sur les versions de système d’exploitation Windows <= 1709** et recommandé sur les versions de système d’exploitation Windows >= 1803

le reste de cet article fournit une vue d’ensemble détaillée de ces exigences et des recommandations supplémentaires pour garantir que vos modèles fonctionnent bien avec la Windows Mixed Reality page d’hébergement. 

## <a name="detailed-guidance"></a>Conseils détaillés

### <a name="exporting-models"></a>Exportation de modèles

la Windows Mixed Reality la page d’hébergement s’attend à ce que les ressources 3d soient remises à l’aide du format de fichier. glb avec les images incorporées et les données binaires. GLB est la version binaire du format glTF, qui est une norme ouverte libre Royalty pour la remise de ressources en 3D gérée par le groupe Khronos. comme glTF évolue comme une norme industrielle pour le contenu 3d interopérable, Microsoft prend en charge le format entre les applications Windows et les expériences. Si vous n’avez pas créé de ressource glTF avant de pouvoir trouver la [liste des exportateurs et convertisseurs pris en charge](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) sur la page GitHub glTF Working Group.  

### <a name="modeling-guidelines"></a>Instructions de modélisation

Windows s’attend à ce que les ressources soient générées à l’aide des instructions de modélisation suivantes pour garantir la compatibilité avec l’expérience d’hébergement de la réalité mixte. Quand vous modélisez dans votre programme de votre choix, gardez à l’esprit les recommandations et limitations suivantes :
1. L’axe vers le haut doit être défini sur « Y ».
2. L’élément multimédia doit être orienté vers l’avant vers l’axe Z positif.
3. Toutes les ressources doivent être construites sur le plan de sol à l’origine de la scène (0, 0, 0)
4. Les unités de travail doivent être définies sur des compteurs et des ressources afin que les ressources puissent être créées à l’échelle mondiale
5. Vous n’avez pas besoin de combiner tous les maillages, mais cela est recommandé si vous ciblez des appareils à ressources restreintes.
6. Tous les maillages doivent partager un matériau, avec un seul jeu de textures utilisé pour l’ensemble de l’élément multimédia
7. UVs doit être disposé dans une disposition carrée de l’espace 0-1. Évitez les textures en mosaïque bien qu’elles soient autorisées.
8. Plusieurs UVs ne sont pas pris en charge
9. Les matériaux recto-verso ne sont pas pris en charge

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Nombres et niveaux de détails des triangles (LODs)

la Windows Mixed Reality la page d’hébergement ne prend pas en charge les modèles avec plus de 10 000 triangles. Il est recommandé de facettiser vos mailles avant de les exporter pour vous assurer qu’elles ne dépassent pas ce nombre. Windows RM prend également en charge les niveaux de détail Geometry facultatifs (LODs) pour garantir une expérience performante et de haute qualité. [Le WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) vous permet de combiner 3 versions de votre modèle en un seul modèle. glb. Windows détermine le LOD à afficher en fonction de la quantité d’écran occupée par le modèle. Seuls 3 niveaux de LOD sont pris en charge avec les nombres de triangles recommandés suivants :
<br>

|  Niveau LOD  |  Nombre de triangles recommandé  |  Nombre maximal de triangles | 
|------|------|------|
|  LOD 0 |  10 000 |  10 000 | 
|  LOD 1 |  5 000  |  10 000 | 
|  LOD 2 |  2 500  |  10 000 | 

### <a name="node-counts-and-submesh-limits"></a>Nombres de nœuds et limites de sous-maillage

la Windows Mixed Reality la page d’hébergement ne prend pas en charge les modèles avec plus de 64 nœuds ou des sous-maillages 32 par LOD. Les nœuds sont un concept de la [spécification glTF](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) qui définit les objets de la scène. Les sous-maillages sont définis dans le tableau de [primitives](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) sur le maillage de l’objet. 

|  Fonctionnalité |  Description  |  Max pris en charge | Documentation |
|------|------|------|------|
|  Nœuds |  Objets dans la scène glTF |  64 par LOD | [Cette](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Sous-maillages |  Somme des primitives sur tous les maillages |  32 par LOD | [Cette](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Instructions relatives aux matériaux

Les textures doivent être préparées à l’aide d’un flux de travail d’irrégularité du métal PBR. Commencez par créer un ensemble complet de textures, notamment Albedo, normal, occlusion, métallique et rugueuse. Windows Mixed Reality prend en charge les textures avec des résolutions allant jusqu’à 4096x4096, mais il est recommandé de créer chez 512 x 512. Les textures doivent être créées à des résolutions par multiples de 4. Il s’agit d’une condition requise pour le format de compression appliqué aux textures dans les étapes d’exportation décrites ci-dessous. Lors de la génération de mappages MIP ou d’une texture, le MIP le plus bas doit être un maximum de 4 x 4.
<br>

|  Taille de texture recommandée  |  Taille maximale de la texture | MIP le plus bas
|----|----|----|
|  512 x 512  |  4096x4096 | 4x4 max.|

### <a name="albedo-base-color-map"></a>Carte Albedo (couleur de base)

Couleur brute sans informations d’éclairage. Cette carte contient également les informations de réflectivité et de diffusion pour le métal (blanc dans les cartes métalliques) et l’isolateur (noir dans les surfaces métalliques) respectivement.

### <a name="normal"></a>Normal

Carte normale d’espace tangente

### <a name="roughness-map"></a>Carte d’irrégularité

Décrit le microsurface de l’objet. Le blanc 1,0 est un espace blanc grossier de 0,0. Ce mappage donne la plus grande partie à la ressource, car elle décrit véritablement la surface. Par exemple, éraflures, empreintes digitales, taches, Grime, etc.

### <a name="ambient-occlusion-map"></a>Carte d’occlusion ambiante

Carte de mise à l’échelle des valeurs indiquant les zones de bloqués Light, qui bloque les réflexions

### <a name="metallic-map"></a>Carte métallique

Indique au nuanceur s’il s’agit d’un métal ou non. RAW Metal = 1,0 blanc non Metal = 0,0 noir. Il peut y avoir des valeurs de gris transitoires qui indiquent un sujet couvrant le métal brut tel que le saleté, mais en général, cette carte doit être en noir et blanc uniquement.

## <a name="optimizations"></a>Optimisations

Windows Mixed Reality la page d’hébergement offre une série d’optimisations par-dessus les spécifications de base glTF définies à l’aide d’extensions personnalisées. ces optimisations sont requises sur les versions Windows <= 1709 et recommandées sur les versions plus récentes de Windows. vous pouvez facilement optimiser n’importe quel modèle glTF 2,0 à l’aide de l' [Windows Mixed Reality le convertisseur de ressources disponible sur GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Cet outil effectuera les optimisations de l’empaquetage et des optimisations de texture, comme indiqué ci-dessous. Pour une utilisation générale, nous vous recommandons d’utiliser WindowsMRAssetConverter, mais si vous avez besoin de davantage de contrôle sur l’expérience et que vous souhaitez créer votre propre pipeline d’optimisation, vous pouvez vous référer à la spécification détaillée ci-dessous.  

> [!NOTE]
> Pour obtenir une liste définitive des possibilités offertes par les limites du modèle, reportez-vous à l’article sur l' [optimisation du modèle 3D](/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) à utiliser dans les applications Dynamics 365.

### <a name="materials"></a>Matériaux

pour améliorer le temps de chargement des ressources dans les environnements de réalité mixte Windows MR prend en charge le rendu des textures DDS compressées compressées en fonction du schéma de distribution des textures défini dans cette section. Les textures DDS sont référencées à l’aide de l' [extension MSFT_texture_dds](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). La compression des textures est fortement recommandée. 

#### <a name="hololens"></a>HoloLens

les expériences de réalité mixte basées sur HoloLens attendent que les textures soient emballées à l’aide d’une configuration à 2 textures à l’aide de la spécification de compression suivante :
<br>

|  Propriété glTF  |  Texture  |  Schéma d’emballage | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rouge (R), vert (G), bleu (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), rugosité (B), métal (A) | 


Lorsque vous compressez les textures DDS, la compression suivante est attendue sur chaque carte :
<br>

|  Texture  |  Compression attendue | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Casques immersifs (VR)

les expériences de Windows Mixed Reality basées sur PC pour les casques immersifs s’attendent à ce que les textures soient emballées à l’aide d’une configuration à 3 textures à l’aide des spécifications de compression suivantes :

##### <a name="windows-os--1803"></a>Windows >DU SYSTÈME D’EXPLOITATION = 1803

<br>

|  Propriété glTF  |  Texture  |  Schéma d’emballage | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rouge (R), vert (G), bleu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R), ébauche (G), métal (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Lorsque vous compressez les textures DDS, la compression suivante est attendue sur chaque carte :
<br>

|  Texture  |  Compression attendue | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows <DU SYSTÈME D’EXPLOITATION = 1709
<br>

|  Propriété glTF  |  Texture  |  Schéma d’emballage | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rouge (R), vert (G), bleu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Rugosité (R), métal (G), occlusion (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Lorsque vous compressez les textures DDS, la compression suivante est attendue sur chaque carte :
<br>

|  Texture  |  Compression attendue | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Ajout de Mesh LODs

Windows MR utilise un nœud Geometry LODs pour restituer des modèles 3D à différents niveaux de détail en fonction de la couverture à l’écran. Bien que cette fonctionnalité ne soit techniquement pas nécessaire, elle est recommandée pour toutes les ressources. actuellement Windows prend en charge 3 niveaux de détail. Le LOD par défaut est 0, ce qui représente la meilleure qualité. Les autres LODs sont numérotés séquentiellement, par exemple 1, 2 et sont progressivement plus bas en qualité. le [convertisseur d’éléments de Windows Mixed Reality](https://github.com/Microsoft/glTF-Toolkit/releases) prend en charge la génération de ressources qui répondent à cette spécification lod en acceptant plusieurs modèles glTF et en les fusionnant dans une seule ressource avec des niveaux lod valides. Le tableau suivant présente le classement LOD attendu et les cibles de triangle :
<br>

|  Niveau LOD  |  Nombre de triangles recommandé  |  Nombre maximal de triangles | 
|-------|-------|-------|
|  LOD 0 |  10 000 |  10 000 | 
|  LOD 1 |  5 000  |  10 000 | 
|  LOD 2 |  2 500  |  10 000 | 

Lorsque vous utilisez LODs, spécifiez toujours 3 niveaux de LOD. Un LODs manquant entraîne le non-rendu du modèle de manière inattendue, car le système LOD passe au niveau de LOD manquant. glTF 2,0 ne prend pas actuellement en charge LODs dans le cadre de la spécification de base. LODs doit être défini à l’aide de l' [extension MSFT_LOD](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Couverture de l’écran

les LODs sont affichés dans Windows Mixed Reality en fonction d’un système piloté par la valeur de la couverture d’écran définie sur chaque LOD. Les objets qui consomment actuellement une plus grande partie de l’espace d’écran sont affichés à un niveau plus élevé de LOD. La couverture d’écran ne fait pas partie de la spécification Core glTF 2,0 et doit être spécifiée à l’aide de MSFT_ScreenCoverage dans la section « Extras » de l' [extension MSFT_lod](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Niveau LOD  |  Plage recommandée  |  Plage par défaut | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  0,5 | 
|  LOD 1 |  Moins de 50%-20%  |  0,2 | 
|  LOD 2 |  Moins de 20%-1%  |  0,01 | 
|  LOD 4  |  Moins de 1%  |  - | 

## <a name="animation-guidelines"></a>Instructions d’animation

> [!NOTE]
> cette fonctionnalité a été ajoutée dans le cadre de [Windows 10 mise à jour 2018 d’avril](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018). dans les versions antérieures de Windows ces animations ne sont pas lues, elles continueront à se charger si elles sont créées conformément aux instructions de cet article.  

la page d’hébergement de la réalité mixte prend en charge les objets glTF animés sur des casques HoloLens et immersifs (VR). Si vous souhaitez déclencher des animations sur votre modèle, vous devez utiliser l’extension de la carte d’animation au format glTF. Cette extension vous permet de déclencher des animations dans le modèle glTF en fonction de la présence de l’utilisateur dans le monde, par exemple déclencher une animation lorsque l’utilisateur est proche de l’objet ou qu’il l’examine. Si vous glTF objet contient des animations, mais ne définit pas les déclencheurs, les animations ne sont pas lues. La section ci-dessous décrit un flux de travail pour l’ajout de ces déclencheurs à n’importe quel objet glTF animé.

### <a name="tools"></a>Outils

Tout d’abord, téléchargez les outils suivants si vous ne les avez pas déjà. Ces outils facilitent l’ouverture de tout modèle glTF, la préversion, la modification et l’enregistrement d’une sauvegarde en tant que glTF ou. glb :
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Outils glTF pour Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Ouverture et aperçu du modèle

Commencez par ouvrir le modèle glTF dans VSCode en faisant glisser le fichier. glTF dans la fenêtre de l’éditeur. Si vous disposez d’un fichier. GLB au lieu d’un fichier. glTF, vous pouvez l’importer dans VSCode à l’aide du module complémentaire outils glTF que vous avez téléchargé. Accédez à « View-> Command palette », puis commencez à taper « glTF » dans la palette de commandes et sélectionnez « glTF : import from GLB », qui contiendra un sélecteur de fichier pour importer un fichier. GLB avec. 

Une fois que vous avez ouvert votre modèle glTF, vous devez voir le JSON dans la fenêtre de l’éditeur. Vous pouvez également afficher un aperçu du modèle dans une visionneuse 3D en direct à l’aide du en cliquant avec le bouton droit sur le nom de fichier et en sélectionnant le raccourci de commande « glTF : Preview 3D Model » dans le menu contextuel. 

### <a name="adding-the-triggers"></a>Ajout des déclencheurs

Les déclencheurs d’animation sont ajoutés au modèle JSON glTF à l’aide de l’extension de mappage d’animation. l’extension de mappage d’animation est documentée publiquement [ici sur GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (remarque : il s’agit d’une extension de brouillon). Pour ajouter l’extension à votre modèle, faites défiler jusqu’à la fin du fichier glTF dans l’éditeur et ajoutez le bloc « extensionsUsed » et « extensions » à votre fichier s’ils n’existent pas déjà. Dans la section « extensionsUsed », vous allez ajouter une référence à l’extension « EXT_animation_map » et dans le bloc « extensions », vous ajouterez vos mappages aux animations dans le modèle.

Comme indiqué [dans la spécification](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) , vous définissez ce qui déclenche l’animation à l’aide de la chaîne « sémantique » sur une liste d' « animations », qui est un tableau d’index d’animation. Dans l’exemple ci-dessous, nous avons spécifié l’animation à lire lorsque l’utilisateur est Gazing au niveau de l’objet :

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
la sémantique de déclenchement de l’animation suivante est prise en charge par la Windows Mixed Reality page d’hébergement.  
* « ALWAYs » : boucler constamment une animation
* « DÉTENU » : en boucle pendant toute la durée d’un objet.
* « Point de regard » : en boucle pendant qu’un objet est consulté
* « PROXIMITE » : en boucle alors qu’une visionneuse est proche d’un objet
* « POINTing » : en boucle pendant qu’un utilisateur pointe sur un objet

### <a name="saving-and-exporting"></a>Enregistrement et exportation

Une fois que vous avez apporté les modifications à votre modèle glTF, vous pouvez l’enregistrer directement en tant que glTF. Vous pouvez également cliquer avec le bouton droit sur le nom du fichier dans l’éditeur et sélectionner « glTF : exporter vers GLB (fichier binaire) » pour exporter un. glb. 

### <a name="restrictions"></a>Restrictions

Les animations ne peuvent pas dépasser 20 minutes et ne peuvent pas contenir plus de 36 000 images clés (20 minutes à 30 i/s). En outre, lorsque vous utilisez des animations basées sur une cible morphe, vous ne dépassez pas 8192 sommets de cible morphe ou moins. si vous dépassez ces nombres, la ressource animée sera non prise en charge dans la Windows Mixed Reality page d’origine. 

|Fonctionnalité|Maximale|
|-----|-----|
|Duration|20 minutes|
|Images clés|36 000| 
|Vertex cible Morph|8 192|

## <a name="gltf-implementation-notes"></a>Remarques sur l’implémentation de glTF

Windows RM ne prend pas en charge le retournement de géométrie à l’aide d’échelles négatives. La géométrie avec des échelles négatives entraîne probablement des artefacts visuels.

la ressource glTF doit pointer vers la scène par défaut à l’aide de l’attribut scene à afficher par Windows MR. en outre, le Windows le chargeur glTF MR avant le [Windows 10 mise à jour 2018 d’avril](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) **nécessite** des accesseurs :
* Doit avoir des valeurs min et max.
* Le type scalaire doit être componentType UNSIGNED_SHORT (5123) ou UNSIGNED_INT (5125).
* Le type VEC2 et VEC3 doit être componentType FLOAT (5126).

Les propriétés de matériau suivantes sont utilisées à partir de Core glTF 2,0 Spec, mais pas obligatoire :
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture : doit pointer vers une texture stockée dans DDS.
* emissiveTexture : doit pointer vers une texture stockée dans DDS.
* emissiveFactor
* alphaMode

Les propriétés de matériau suivantes sont ignorées à partir des spécifications principales :
* Tous les UVs
* metalRoughnessTexture : doit utiliser à la place la compression de texture optimisée Microsoft définie ci-dessous
* normalTexture : doit utiliser à la place la compression de texture optimisée Microsoft définie ci-dessous
* normalScale
* occlusionTexture : doit utiliser à la place la compression de texture optimisée Microsoft définie ci-dessous
* occlusionStrength

Windows RM ne prend pas en charge les lignes et les points en mode primitifs. 

Un seul attribut de vertex UV est pris en charge.

## <a name="more-resources"></a>Plus de ressources

* [exportateurs et convertisseurs glTF](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Shared Computer Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [Spécification glTF 2,0](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Spécification de l’extension Microsoft glTF LOD](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Spécification des extensions de la compression de texture PC Mixed Real](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Spécification des extensions de compression de texture de réalité mixte](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Spécification des extensions glTF textures Microsoft DDS](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Voir aussi

* [Implémenter des lanceurs d’applications 3D (applications UWP)](implementing-3d-app-launchers.md)
* [Implémenter des lanceurs d’applications 3D (applications Win32)](implementing-3d-app-launchers-win32.md)
* [Exploration de la page d’accueil Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)