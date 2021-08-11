---
title: Fenêtre d’optimisation
description: Fenêtre d’optimisation de la documentation dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f87b0742afcf2c270d1060742ad0945132b4998cc055b1908b8a1ef17c9a0fe4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199723"
---
# <a name="optimize-window"></a>Fenêtre d’optimisation

La fenêtre MRTK Optimize est un utilitaire qui permet d’automatiser et d’informer le processus de configuration d’un projet de réalité mixte pour des [performances](../../performance/perf-getting-started.md) optimales dans Unity. Cet outil se concentre généralement sur les configurations de rendu qui, lorsqu’elles sont définies sur la présélection appropriée, peuvent réduire les millisecondes de traitement.

> [!NOTE]
> Pour ouvrir la **fenêtre optimiser** , accédez à la   >    >  **fenêtre optimisation** des utilitaires de réalité mixte à partir du menu de la barre supérieure de l’éditeur Unity.

La *cible de build active* est la [plateforme de génération actuellement ciblée](https://docs.unity3d.com/Manual/BuildSettings.html) par le projet pour la compilation.

La *cible de performance* indique à l’outil d’optimisation le type de points de terminaison d’appareil à cibler.

- Les *casques AR* sont des appareils mobiles, tels que les HoloLens
- *VR standalone* est un appareil mobile, tel que Oculus Go ou Quest
- *VR* est un appareil alimenté par PC, tel que le format Samsung Odyssey, le rift Oculus ou le HTC, etc.

![Cible de performance de la fenêtre d’optimisation MRTK](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Définition des optimisations

L’onglet optimisation des paramètres couvre certaines des configurations de rendu importantes pour un projet Unity. Cette section peut vous aider à automatiser et à vous informer des paramètres à modifier pour obtenir les résultats les plus performants.

Une icône de coche verte signifie qu’une valeur optimale a été configurée dans le projet/la scène pour ce paramètre particulier. Une icône d’avertissement jaune indique que la configuration actuelle peut être améliorée. En cliquant sur le bouton associé dans une section donnée, vous configurez automatiquement ce paramètre dans le projet Unity/Scene sur une valeur plus optimale.

![MRTK optimiser la fenêtre Paramètres](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Rendu d’instance à passe unique

Le [rendu d’instance à passage unique](https://docs.unity3d.com/Manual/SinglePassInstancing.html) est le chemin de rendu le plus efficace pour les applications de réalité mixte. Cette configuration garantit que le pipeline de rendu n’est exécuté qu’une seule fois pour les yeux et que les appels de dessin sont instanciés sur les deux yeux.

### <a name="depth-buffer-sharing"></a>Partage de mémoire tampon de profondeur

Pour améliorer la [stabilisation des hologrammes](../../performance/hologram-Stabilization.md), les développeurs peuvent partager le tampon de profondeur de l’application, ce qui donne aux plateformes des informations sur l’emplacement et les hologrammes à stabiliser dans la scène rendue.

### <a name="depth-buffer-format"></a>Format de mémoire tampon de profondeur

En outre, pour les *casques AR*, il est recommandé d’utiliser un format de profondeur 16 bits lors de l’activation du partage de tampons de profondeur par rapport à 24 bits. Cela signifie une précision inférieure, mais économise les performances. Si la [superposition](https://en.wikipedia.org/wiki/Z-fighting) se produit parce qu’il y a moins de précision dans le calcul de la profondeur pour les pixels, il est recommandé de déplacer le [plan de découpage](https://docs.unity3d.com/Manual/class-Camera.html) le plus proche de l’appareil photo (par ex. 50 millions au lieu de 1000MD).

> [!NOTE]
> Si vous utilisez le *format de profondeur 16 bits, les* effets requis pour la mémoire tampon des stencils ne fonctionneront pas, car [Unity ne crée pas de tampon de stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) dans ce paramètre. Si vous sélectionnez le *format de profondeur 24 bits* , vous créez généralement une [mémoire tampon de stencil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html), le cas échéant sur la plateforme graphique de point de terminaison.
>
> Si vous utilisez un [composant de masque](https://docs.unity3d.com/Manual/script-Mask.html) qui requiert la mémoire tampon de stencil, envisagez d’utiliser [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) à la place, ce qui ne nécessite pas la mémoire tampon de stencil et peut donc être utilisé avec un format de *profondeur de 16 bits*.

### <a name="real-time-global-illumination"></a>Éclairage global en temps réel

L' [éclairage global](https://docs.unity3d.com/Manual/GIIntro.html) en temps réel dans Unity peut fournir des résultats esthétiques fantastiques, mais à un coût très élevé. L’éclairage global de l’éclairage est très onéreux en réalité mixte. il est donc recommandé de désactiver cette fonctionnalité en cours de développement.

> [!NOTE]
> Les paramètres d’éclairage globaux dans Unity sont définis par scène et pas une seule fois pour l’ensemble du projet.

## <a name="scene-analysis"></a>Analyse des scènes

L’onglet *analyse des scènes* est conçu pour informer les développeurs sur les éléments actuellement dans la scène qui auront probablement le plus d’impact sur les performances.

![MRTK optimiser la fenêtre Paramètres analyse des scènes](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Analyse de l’éclairage

Cette section examine le nombre de lumières actuellement présentes dans la scène, ainsi que les voyants qui doivent désactiver les ombres. Le cast instantané est une opération très coûteuse.

### <a name="polygon-count-analysis"></a>Analyse du nombre de polygones

L’outil fournit également des statistiques sur le nombre de polygones. Il peut être très utile d’identifier rapidement les GameObjects qui ont la plus grande complexité de polygones dans une scène donnée à cibler pour les optimisations.

### <a name="unity-ui-raycast-analysis"></a>Analyse raycast de l’interface utilisateur Unity

Les opérations raycast Graphics sont effectuées par pointeur dans MRTK pour déterminer si des éléments d’interface utilisateur Unity sont activés. Ces raycasts peuvent être très onéreux et contribuer à l’amélioration des performances. les éléments d’interface utilisateur qui n’ont pas besoin d’être retournés dans les résultats doivent être désactivés en tant que cibles raycast. Chaque élément [graphique](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) a une [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) propriété. Cet outil recherche des éléments d’interface utilisateur de texte dont cette propriété est activée et peut donc être désactivée.

## <a name="shader-analysis"></a>Analyse des nuanceurs

Le [nuanceur standard Unity](https://docs.unity3d.com/Manual/shader-StandardShader.html) peut produire des résultats visuels de très grande qualité pour les jeux, mais il n’est généralement pas mieux adapté aux besoins de performances des applications de réalité mixte, en particulier puisque ces applications sont généralement limitées par le GPU. Par conséquent, il est recommandé aux développeurs d’utiliser le [nuanceur MRTK standard](../rendering/mrtk-standard-shader.md) pour équilibrer l’esthétique & les fonctionnalités graphiques avec les performances.

l’onglet *analyse des nuanceurs* analyse le dossier de ressources du projet actif pour rechercher les matériaux à l’aide du nuanceur Standard unity ou si vous le souhaitez, tous les matériaux qui n’utilisent pas de réalité mixte Shared Computer Toolkit les nuanceurs fournis. Une fois découverts, les développeurs peuvent convertir tous les documents ou les convertir individuellement à l’aide des boutons appropriés.

![MRTK optimiser la fenêtre Paramètres analyse du nuanceur](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Voir aussi

- [Performances](../../performance/perf-getting-started.md)
- [Stabilisation d’hologramme](../../performance/hologram-stabilization.md)
