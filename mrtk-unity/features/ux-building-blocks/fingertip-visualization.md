---
title: Visualisation du bout des doigts
description: Vue d’ensemble de la visualisation sur le doigt dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, doigt
ms.openlocfilehash: 1df1740692a2c24213f34ffa6e52c135c7e7d14f96e7d99668feab82f879f756
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193294"
---
# <a name="fingertip-visualization"></a>Visualisation du bout des doigts

![Main visualisation main](../images/fingertip/MRTK_FingertipVisualization_Main.png)

La portée de main permet à l’utilisateur de reconnaître la distance par rapport à l’objet cible. Le visuel de la forme en anneau ajuste sa taille en fonction de la distance entre le doigt et l’objet. La visualisation à l’aide de est principalement contrôlée par le `FingerCursor` (ressources/MRTK/SDK/features/UX/Prefabs/Cursors/FingerCursor. Prefab) (et le script) qui est généré en tant que curseur Prefab du *PokePointer*. Les autres composants de la visualisation incluent le script *ProximityLight* et le nuanceur *MixedRealityStandard* .

## <a name="how-to-use-the-fingertip-visualization"></a>Comment utiliser la visualisation à l’aide de

Par défaut, la visualisation de portée fonctionne dans toute scène Unity configurée pour générer un FingerCursor. La génération de FingerCursor se produit dans le *DefaultMixedRealityToolkitConfigurationProfile* sous :

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

À un niveau élevé, la visualisation de portée fonctionne en utilisant une lumière de proximité pour projeter un dégradé de couleur sur toutes les surfaces avoisinantes qui acceptent les lumières de proximité. Le curseur Finger recherche ensuite toutes les surfaces interactives avoisinantes, qui sont déterminées par `IMixedRealityNearPointer(s)` le parent, pour aligner l’anneau de doigt sur une surface lorsque le doigt se déplace vers une surface. Comme un doigt approche une surface, l’anneau de doigt est également animé de manière dynamique à l’aide des propriétés d’angle arrondi du nuanceur MixedRealityStandard.

## <a name="example-scene"></a>Exemple de scène

Vous pouvez trouver des exemples d’affichage de portée dans la plupart des scènes qui fonctionnent avec des mains articulées, mais qui est visible dans la [scène HandInteractionExample](../example-scenes/hand-interaction-examples.md).

![Affichage des États de visualisation](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Propriétés de l’inspecteur

**FingerCursor** La plupart des propriétés de curseur Finger sont héritées de la classe Cursor de base. Les propriétés importantes incluent les marges et les largeurs de surface éloignée/proche qui pilotent l’animation de sonnerie de doigt dans le nuanceur MixedRealityStandard. Pour les autres propriétés, pointez sur les info-bulles des outils de l’inspecteur.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** Les paramètres d’éclairage de proximité contrôlent l’apparence de la lumière lorsqu’elle est proche et éloignée d’une surface. Les couleurs centrale, centrale et externe contrôlent l’apparence du dégradé de la lumière et peuvent être personnalisées pour la palette de couleurs de votre application. Notez que les couleurs sont en HDR (plage dynamique élevée) pour permettre aux utilisateurs d’éclaircir la lumière de proximité aux valeurs supérieures à un. Pour les autres propriétés, pointez sur les info-bulles des outils de l’inspecteur.

**Nuanceur MixedRealityStandard** Le nuanceur MixedRealityStandard est utilisé pour de nombreux effets dans le MRTK. Les deux paramètres importants pour la visualisation de portée sont « near fondu » et « lumière de proximité ». Near fondu permet aux objets d’apparaître en fondu ou en sortie en tant qu’appareil photo ou lumière proche. Veillez à cocher la case « Light » pour permettre aux lumières de proximité de piloter le fondu (plutôt que l’appareil photo). Vous pouvez inverser les valeurs de « début de fondu » et de « fondu terminé » pour annuler un fondu. Vérifiez la « lumière de proximité » pour les surfaces que vous souhaitez éclaircir. Pour les autres propriétés, pointez sur les info-bulles des outils de l’inspecteur.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
