---
title: Processus de création des ressources
description: Aide sur la création de ressources pour les expériences de réalité mixte.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: actif, création, processus, budget, polygones, textures, nuanceurs, performances, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, kit de ressources de réalité mixte, ressources
ms.openlocfilehash: 2089ac7a870d9b4b13d314774d6d6124b78bb15c
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847553"
---
# <a name="asset-creation-process"></a>Processus de création des ressources

Windows Mixed Reality s’appuie sur les dizaines d’investissements réalisés par Microsoft dans DirectX. Toutes les expériences et compétences des développeurs avec la création de graphiques 3D continuent à être utiles avec HoloLens.

Les ressources que vous créez pour un projet sont disponibles dans de nombreux formulaires et formes. Elles peuvent être composées d’une série de textures/images, de sons, de vidéos, de modèles 3D et d’animations. Nous ne pouvons pas commencer à couvrir tous les outils qui sont disponibles pour créer les différents types de ressources utilisés dans un projet. Pour cet article, nous allons nous concentrer sur les méthodes de création de ressources en 3D.

![Concept, création, intégration et déroulement des itérations](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Processus de conception, de création, d’intégration et d’itération*

## <a name="things-to-consider"></a>Points importants à prendre en compte

Quand vous examinez l’expérience, vous tentez de la créer, pensez-y comme un **budget** que vous pouvez consacrer à essayer de créer la meilleure expérience. Il n’existe pas nécessairement de limites imposées sur le nombre de **polygones** ou de **types de matériau** que vous pouvez utiliser dans vos ressources. Considérez-le comme un ensemble de compromis budgété.

Vous trouverez ci-dessous un exemple de budget pour votre expérience. Les performances ne sont pas un point de défaillance unique, mais une mort par mille morceaux.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Éléments multimédias</b></th><th style="text-align:right;"> UC</th><th> GPU</th><th> Mémoire</th>
</tr><tr>
<td> Polygones</td><td> 0 %</td><td> 5 %</td><td> 10 %</td>
</tr><tr>
<td> Textures</td><td> 5 %</td><td> 15 %</td><td>25 %</td>
</tr><tr>
<td> Nuanceurs</td><td> 15 %</td><td> 35 %</td><td> 0 %</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Physique</td><td> 5 %</td><td> 15 %</td><td> 0 %</td>
</tr><tr>
<td> Éclairage en temps réel</td><td> 10 %</td><td> 0 %</td><td> 0 %</td>
</tr><tr>
<td> Média (audio/vidéo)</td><td> -</td><td> 15 %</td><td> 25 %</td>
</tr><tr>
<td> Script/logique</td><td> 25 %</td><td> 0 %</td><td> 5 %</td>
</tr><tr>
<td> Surcharge générale</td><td> 5 %</td><td> 5 %</td><td> 5 %</td>
</tr><tr>
<td> <b>Total</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Nombre total de ressources**
* Combien de ressources sont actives dans la scène ?

**Complexité des ressources**
* Combien de triangles/polygones ?
* Quel est le degré de complexité du nuanceur ? Quand vous utilisez la boîte à outils de la réalité mixte, il est recommandé d’utiliser le [nuanceur standard Mixed Reality Toolkit standard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) pour réduire la complexité des nuanceurs.

Les développeurs et les artistes doivent prendre en compte les fonctionnalités de l’appareil et du moteur graphique. Microsoft HoloLens dispose de toutes les fonctionnalités de calcul et de graphique intégrées à l’appareil. Il partage les fonctionnalités que les développeurs trouveraient sur une plate-forme mobile.

Le processus de création de ressources est le même si votre expérience cible un [appareil holographique ou un appareil immersif](../discover/mixed-reality.md#the-mixed-reality-spectrum). La principale chose à noter est la capacité et l’échelle de l’appareil. Vous pouvez voir le monde réel dans la réalité mixte, afin de conserver la mise à l’échelle appropriée en fonction de l’expérience.

## <a name="authoring-assets"></a>Création de ressources

Nous allons commencer par les moyens d’obtenir des ressources pour votre projet :
1. Création de ressources (outils de création et capture d’objets)
2. Achats d’actifs (achat de ressources en ligne)
3. Portage des ressources (en tenant des ressources existantes)
4. Externalisation des ressources (importation de ressources de tiers)

### <a name="creating-assets"></a>Création de ressources

**Outils de création**<br>
Tout d’abord, vous pouvez créer vos propres ressources de différentes façons. les artistes 3D utilisent divers outils et applications pour créer des modèles, qui se composent de **maillages**, de **textures** et de **matériaux**. Il est ensuite enregistré dans un format de fichier qui peut être importé ou utilisé par le moteur graphique utilisé par l’application, par exemple **. FBX** ou **. OBJ**. Tout outil qui génère un modèle pris en charge par le moteur graphique que vous avez choisi fonctionnera sur **HoloLens**. Parmi les artistes en 3D, beaucoup choisissent d’utiliser les [Maya de Autodesk, car ils peuvent utiliser HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) pour transformer la façon dont les ressources sont créées. Si vous souhaitez obtenir un résultat rapide, vous pouvez également utiliser le [Générateur 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) fourni avec Windows pour l’exportation. OBJ à utiliser dans votre application.

**Capture d’objets**<br>
Il y a également la possibilité de capturer des objets en 3D. La capture d’objets inanimés en 3D et leur modification avec le logiciel de création de contenu numérique sont de plus en plus populaires avec la hausse de l’impression en 3D. À l’aide du capteur **Kinect 2** et du [Générateur 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) , vous pouvez utiliser la fonctionnalité de capture pour créer des ressources à partir d’objets réels. Il s’agit également d’une [suite d’outils](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) permettant de faire de même avec **Photogrammetry** en traitant plusieurs images pour combiner et fusionner les textures.

### <a name="purchasing-assets"></a>Achats d’actifs

Une autre option idéale consiste à acheter des ressources pour votre expérience. Il existe une multitude d’actifs disponibles par le biais de services tels que le [magasin d’actifs Unity](https://www.assetstore.unity3d.com/) ou [Turbosquid](https://www.turbosquid.com/) .

Lorsque vous achetez des ressources auprès d’un tiers, vous devez toujours vérifier les propriétés suivantes :
* **Quel est le nombre de poly ?**
  * Est-il adapté à votre budget ?
* **Existe-t-il des niveaux de détail (LODs) pour le modèle ?**
  * Un niveau de détail des modèles vous permet de mettre à l’échelle les détails d’un modèle pour des performances optimales.
* **Le fichier source est-il disponible ?**
  * Non inclus dans le [magasin d’actifs Unity](https://www.assetstore.unity3d.com/) , mais toujours inclus avec des services tels que [Turbosquid](https://www.turbosquid.com/).
  * Sans le fichier source, vous ne pouvez pas modifier la ressource.
  * Assurez-vous que le fichier source fourni peut être importé par vos outils 3D.
* **Savoir ce que vous obtenez**
  * Les animations sont-elles fournies ?
  * Veillez à consulter la liste de contenu de l’élément multimédia que vous achetez.

### <a name="porting-assets"></a>Portage de ressources

Dans certains cas, vous allez créer des ressources existantes qui ont été créées à l’origine pour d’autres appareils et différentes applications. Dans la plupart des cas, ces ressources peuvent être converties en formats compatibles avec le moteur graphique utilisé par leur application.

Lorsque vous portez des ressources à utiliser dans votre application HoloLens, vous pouvez poser les questions suivantes :
* **Pouvez-vous importer directement ou doit être converti vers un autre format ?** Vérifiez le format que vous importez avec le moteur graphique que vous utilisez.
* **Si la conversion vers un format compatible est-elle perdue ?** Parfois, les détails peuvent être perdus ou les importations peuvent entraîner des artefacts qui doivent être nettoyés dans un outil de création 3D.
* **Quel est le nombre de polygones/polygones de l’élément multimédia ?** En fonction du budget de votre application, vous pouvez utiliser des [Simplygon](https://www.simplygon.com/) ou des outils similaires pour décimer (réduire de manière manuelle ou manuelle le chiffrement poly) la ressource d’origine pour l’adapter au budget de vos applications.

### <a name="outsourcing-assets"></a>Ressources en External

Une autre option pour les projets plus volumineux qui requièrent plus de ressources que votre équipe est équipée pour la création consiste à externaliser la création d’actifs. Le processus d’externalisation consiste à trouver le Studio ou l’Agence approprié qui est spécialisé dans l’externalisation des ressources. Il peut s’agir de l’option la plus coûteuse, mais également de la plus souple dans ce que vous recevez.
* **Définissez clairement ce que vous demandez**
  * Fournir autant de détails que possible
  * Images du concept avant, latéral et arrière
  * Illustration de référence présentant un élément multimédia en contexte
  * Mise à l’échelle de l’objet (généralement spécifiée en centimètres)
* **Fournir un budget**
  * Plage de nombres poly
  * Nombre de textures
  * Type de nuanceur (pour Unity et HoloLens, vous devez toujours d’abord par défaut les nuanceurs mobiles)
* **Comprendre les coûts**
  * Quelle est la stratégie d’externalisation pour les demandes de modification ?

L’externalisation peut fonctionner correctement en fonction de la chronologie de vos projets, mais elle nécessite plus de supervision pour garantir que vous disposez des ressources dont vous avez besoin pour la première fois.
