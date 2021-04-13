---
title: Visualisation de maillage spatial
description: Découvrez les instructions de conception et la compréhension de l’environnement physique avec la visualisation de maillage spatial dans MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Réalité mixte, HoloLens, contrôles d’interface utilisateur, interaction, interface utilisateur, expérience utilisateur, conception UX, interface utilisateur spatiale, interaction spatiale, interface utilisateur 3D, expérience utilisateur 3D, casque de la réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, kit de mise en réalité mixte
ms.openlocfilehash: 0d8d2811c2fae96f679eeb1df2f1053e7ecf5def
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300344"
---
# <a name="spatial-mesh"></a>Maillage spatial

![Maillage spatial](images/MRTK_PulseShader_SpatialMesh.gif)

Les utilisateurs apprennent comment un appareil perçoit et comprend l’environnement physique grâce à la visualisation de maillage spatial. Une visualisation de maillage spatial appropriée peut créer une expérience délicieuse et magique tout en fournissant un contexte spatial.  

## <a name="design-guideline"></a>Directives de conception

Il est important d’autoriser l’utilisateur à se concentrer et à interagir avec le contenu. La visualisation continue du maillage spatial en arrière-plan peut être gênante. Nous vous recommandons de visualiser l’environnement avec modération, qu’une seule fois au lancement initial ou lorsque l’utilisateur montre clairement qu’il souhaite voir la maille environnementale en ciblant et en appuyant sur de l’air. Vous pouvez observer ce comportement dans le portail de la réalité mixte.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualisation de maillage spatial dans MRTK (ensemble d’outils de réalité mixte) pour Unity

MRTK fournit plusieurs documents pour la visualisation de maillage spatial.

- **MRTK_Wireframe. mat, MRTK_Wireframe. mat**: matériau de maillage spatial statique par défaut, qui affiche les contours de maillage sans animation. Ce document est utile à des fins de débogage, car il affiche les géométries entières du maillage spatial. Toutefois, il n’est pas recommandé pour la production.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. mat**: ce matériau vous donne un effet d’impulsion animée sur le maillage spatial. Vous pouvez utiliser ce document pour visualiser l’environnement à un moment donné ou sur l’entrée d’air de l’utilisateur. Consultez la scène **PulseShaderExamples. Unity** pour obtenir des exemples.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* Pour plus d’informations, consultez [MRTK-spatial Awareness](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) et [MRTK-Pulse Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).

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
