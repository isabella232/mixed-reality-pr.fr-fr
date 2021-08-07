---
title: Visualisation de maillage spatial
description: Découvrez les instructions de conception et la compréhension de l’environnement physique avec la visualisation de maillage spatial dans MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: réalité mixte, HoloLens, contrôles d’interface utilisateur, interaction, interface utilisateur, expérience utilisateur, conception ux, interface utilisateur spatiale, interaction spatiale, interface utilisateur 3d, expérience utilisateur 3d, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, réalité mixte Shared Computer Toolkit
ms.openlocfilehash: 7fcba586f55e6131235d031327da131aa8ba6c97958e4ac282a8f8d048d37992
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216281"
---
# <a name="spatial-mesh"></a>Maillage spatial

![Maillage spatial](images/MRTK_PulseShader_SpatialMesh.gif)

Les utilisateurs apprennent comment un appareil perçoit et comprend l’environnement physique grâce à la visualisation de maillage spatial. Une visualisation de maillage spatial appropriée peut créer une expérience délicieuse et magique tout en fournissant un contexte spatial.  

## <a name="design-guideline"></a>Directives de conception

Il est important d’autoriser l’utilisateur à se concentrer et à interagir avec le contenu. La visualisation continue du maillage spatial en arrière-plan peut être gênante. Nous vous recommandons de visualiser l’environnement avec modération, qu’une seule fois au lancement initial ou lorsque l’utilisateur montre clairement qu’il souhaite voir la maille environnementale en ciblant et en appuyant sur de l’air. Vous pouvez observer ce comportement dans le portail de la réalité mixte.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>visualisation de maillage Spatial dans MRTK (Shared Computer Toolkit de réalité mixte) pour unity

MRTK fournit plusieurs documents pour la visualisation de maillage spatial.

- **MRTK_Wireframe. mat, MRTK_Wireframe. mat**: matériau de maillage spatial statique par défaut, qui affiche les contours de maillage sans animation. Ce document est utile à des fins de débogage, car il affiche les géométries entières du maillage spatial. Toutefois, il n’est pas recommandé pour la production.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. mat**: ce matériau vous donne un effet d’impulsion animée sur le maillage spatial. Vous pouvez utiliser ce document pour visualiser l’environnement à un moment donné ou sur l’entrée d’air de l’utilisateur. Consultez la scène **PulseShaderExamples. Unity** pour obtenir des exemples.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* Pour plus d’informations, consultez [MRTK-spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) et [MRTK-Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).

<br>

---

## <a name="see-also"></a>Voir aussi

* [Curseurs](cursors.md)
* [Rayon émanant de la main](point-and-commit.md)
* [Button](button.md)
* [Objet avec interaction possible](interactable-object.md)
* [Rectangle englobant et barre de l’application](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Menu de la main](hand-menu.md)
* [Menu proche](near-menu.md)
* [Collection d’objets](object-collection.md)
* [Commande vocale](voice-input.md)
* [Clavier](keyboard.md)
* [Info-bulle](tooltip.md)
* [Tablette](slate.md)
* [Curseur](slider.md)
* [Nuanceur](shader.md)
* [Billboarding et tag-along](billboarding-and-tag-along.md)
* [Affichage de la progression](progress.md)
* [Aimantation de surface](surface-magnetism.md)