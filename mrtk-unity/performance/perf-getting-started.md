---
title: Performances
description: Documentation pour comprendre et ajuster la conformité dans MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 50128100d058b5ec3bca7eac523c78287ce657925c3ac116e4336174e34e75c8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211177"
---
# <a name="performance"></a>Performances

## <a name="getting-started"></a>Prise en main

Le moyen le plus simple de rationaliser les performances est d’utiliser la cadence ou le nombre de fois où votre application peut afficher une image par seconde. Il est important de se conformer à la fréquence d’images cible, comme indiqué par la plateforme ciblée (c.-à-d. [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/), etc.). par exemple, sur HoloLens, la fréquence d’images cible est de 60 FPS. Les applications à fréquence faible peuvent entraîner des détériorations de l’expérience utilisateur, telles que la [stabilisation des hologrammes](../performance/hologram-stabilization.md), le suivi mondial, le suivi des mains et bien plus encore. pour aider les développeurs à suivre et à obtenir une fréquence d’images de qualité, la réalité mixte Shared Computer Toolkit fournit un large éventail d’outils et de scripts.

### <a name="visual-profiler"></a>Générateur de profils Visual

Pour effectuer un suivi continu des performances pendant la durée de vie du développement, il est vivement recommandé de toujours afficher un visuel de fréquence lors de l’exécution & le débogage d’une application. la Shared Computer Toolkit de la réalité mixte fournit l’outil de diagnostic du [profileur Visual](../features/diagnostics/using-visual-profiler.md) , qui fournit des informations en temps réel sur l’utilisation actuelle des FPS et de la mémoire dans la vue application. le profileur Visual peut être configuré via le [système de diagnostic Paramètres](../features/diagnostics/diagnostics-system-getting-started.md) sous l' [inspecteur de profils MRTK](../configuration/mixed-reality-configuration-guide.md).

En outre, il est particulièrement important d’utiliser le générateur de profils Visual pour suivre les cadences lorsqu’elles s’exécutent sur l’appareil, par opposition à l’exécution dans l’éditeur Unity ou un émulateur. Les résultats de performances les plus précis seront représentés lors de l’exécution sur l’appareil avec des [Builds de configuration de version](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019).

> [!NOTE]
> si vous générez pour Windows Mixed Reality, déployez avec les [builds de configuration maître](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Interface du profileur Visual](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>Fenêtre d’optimisation

La [fenêtre MRTK Optimize](../features/tools/optimize-window.md) offre des outils d’informations et d’automatisation pour aider les développeurs de la réalité mixte à configurer leur environnement pour les meilleurs résultats et à identifier les goulots d’étranglement potentiels dans leur scène & ressources. Certaines configurations clés dans Unity peuvent aider à fournir des résultats sensiblement plus optimisés pour les projets de réalité mixte.

En règle générale, ces paramètres impliquent des configurations de rendu idéales pour la réalité mixte. Les applications de réalité mixte sont uniques par rapport au développement graphique 3D traditionnel en ce qu’il y a deux écrans (c.-à-d. deux yeux) à rendre pour l’ensemble de la scène.

Les paramètres recommandés référencés ci-dessous peuvent être configurés automatiquement dans un projet Unity en tirant parti de la fenêtre MRTK optimize.

![MRTK optimiser la fenêtre Paramètres](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Profileur Unity

Le [profileur Unity](https://docs.unity3d.com/Manual/ProfilerWindow.html) est un outil utile pour examiner en détail les performances de l’application au niveau d’une image.

#### <a name="time-spent-on-the-cpu"></a>Temps passé sur le processeur

![Exemple de profileur Unity Graph](../features/images/performance/UnityProfilerGraph.png)

Pour conserver les fréquences d’images familières (généralement 60 images par seconde), les applications doivent atteindre une durée de trame maximale de 16,6 millisecondes du temps processeur. pour aider à identifier le coût de la fonctionnalité de MRTK, le Shared Computer Toolkit de la réalité mixte Microsoft contient un marqueur pour les chemins de code de la boucle interne (par trame). Ces marqueurs utilisent le format suivant pour aider à comprendre la fonctionnalité spécifique utilisée :

```
[MRTK] className.methodName
```

> [!Note]
> Il peut y avoir des données supplémentaires à la suite du nom de la méthode. Ce code est utilisé pour identifier les fonctionnalités exécutées de manière conditionnelle et potentiellement onéreuses qui peuvent être évitées par les petites modifications apportées au code de l’application.

![Exemple de hiérarchie du profileur Unity](../features/images/performance/UnityProfilerHierarchy.png)

Dans cet exemple, la hiérarchie a été développée pour montrer que la méthode UpdateHandData de la classe WindowsMixedRealityArticulatedHand utilise 0,44 ms du temps processeur pendant l’analyse du frame. Ces données peuvent être utilisées pour déterminer si un problème de performances est lié au code d’application ou à partir d’un autre emplacement du système.

Il est vivement recommandé aux développeurs d’instrumenter le code de l’application de la même manière. Les principaux domaines de focus pour l’instrumentation de code d’application se trouvent dans les gestionnaires d’événements, car ces méthodes sont facturées à la boucle de mise à jour MRTK à mesure que des événements sont déclenchés. Les temps de trames élevés dans la boucle de mise à jour MRTK peuvent indiquer un code coûteux dans les méthodes de gestionnaire d’événements.

## <a name="recommended-settings-for-unity"></a>Paramètres recommandés pour Unity

### <a name="single-pass-instanced-rendering"></a>Rendu d’instance Single-Pass

La configuration de rendu par défaut pour XR dans Unity est [Multi-Pass](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html). Ce paramètre indique à Unity d’exécuter l’intégralité du pipeline de rendu deux fois, une fois pour chaque œil. Cela peut être optimisé en sélectionnant [un rendu d’instance à passage unique](https://docs.unity3d.com/Manual/SinglePassInstancing.html) à la place. Cette configuration s’appuie sur les [tableaux cibles de rendu](https://en.wikipedia.org/wiki/Multiple_Render_Targets) pour pouvoir effectuer un appel de dessin unique dans la cible de [rendu](https://en.wikipedia.org/wiki/Render_Target) appropriée pour chaque œil. En outre, ce mode permet d’effectuer tout le rendu dans une seule exécution du pipeline de rendu. Par conséquent, la sélection d’un rendu d’instance à passage unique comme chemin de rendu pour une application de réalité mixte peut [gagner beaucoup de temps sur le processeur & GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) et est la configuration de rendu recommandée.

Toutefois, pour pouvoir émettre un appel de dessin unique pour chaque maille à chaque œil, l' [instanciation du GPU](https://docs.unity3d.com/Manual/GPUInstancing.html) doit être prise en charge par tous les nuanceurs. L’instanciation permet au GPU de multiplexer les appels de dessin sur les deux yeux. Les nuanceurs intégrés Unity ainsi que le [nuanceur standard MRTK](../features/rendering/mrtk-standard-shader.md) contiennent par défaut les instructions d’instanciation nécessaires dans le code du nuanceur. Si vous écrivez des nuanceurs personnalisés pour Unity, ces nuanceurs devront peut-être être mis à jour pour prendre en charge le rendu d’instance à passage unique.

#### <a name="example-code-for-custom-shader"></a>[Exemple de code pour un nuanceur personnalisé](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a>Paramètres de qualité

Unity fournit des [présélections pour contrôler la qualité](https://docs.unity3d.com/Manual/class-QualitySettings.html) du rendu pour chaque point de terminaison de plateforme. Ces paramètres prédéfinis contrôlent les fonctionnalités graphiques qui peuvent être activées, telles que les ombres, l’anticrénelage, l’éclairage global et bien plus encore. Il est recommandé de réduire ces paramètres et d’optimiser le nombre de calculs effectués lors du rendu.

*Étape 1 :* Mettre à jour les projets Unity de réalité mixte pour utiliser le paramètre de niveau de *qualité faible*  
**Modifier**  >  **Project Paramètres**, puis sélectionnez la catégorie de **qualité** > sélectionnez *faible qualité* pour la plateforme UWP.

*Étape 2 :* Pour chaque fichier de scène Unity, désactiver l' [éclairage global en temps réel](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**Fenêtre**  >  **Rendu**  >  **Paramètres**  >  d’éclairage [Décocher l' *éclairage global en temps réel*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>Partage de mémoire tampon de profondeur (HoloLens)

si vous développez pour la plate-forme Windows Mixed Reality et en particulier HoloLens, l’activation du *partage de mémoire tampon de profondeur* sous *XR Paramètres* peut aider à la [stabilisation des hologrammes](../performance/hologram-stabilization.md). Toutefois, le traitement du tampon de profondeur peut entraîner des coûts de performances, en particulier si vous utilisez un [format de profondeur 24 bits](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html). Par conséquent, il est *fortement recommandé* de configurer le tampon de profondeur sur une précision de 16 bits.

Si la [superposition](https://en.wikipedia.org/wiki/Z-fighting) se produit en raison du format binaire inférieur, vérifiez que le [plan de découpage](https://docs.unity3d.com/Manual/class-Camera.html) de l’ensemble des caméras est défini sur la valeur la plus basse possible pour l’application. Unity par défaut définit un plan de découpage Far de 1000MD. sur HoloLens, un plan de découpage lointain de 50 millions est généralement plus que suffisant pour la plupart des scénarios d’application.

> [!NOTE]
> Si vous utilisez le *format de profondeur 16 bits, les* effets requis pour la mémoire tampon des stencils ne fonctionneront pas, car [Unity ne crée pas de tampon de stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) dans ce paramètre. Si vous sélectionnez le *format de profondeur 24 bits* , vous créez généralement une mémoire tampon de stencil de 8 bits, le cas échéant sur la plateforme graphique de point de terminaison.
>
> Si vous utilisez un [composant de masque](https://docs.unity3d.com/Manual/script-Mask.html) qui requiert la mémoire tampon de stencil, envisagez d’utiliser [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) à la place, ce qui ne nécessite pas la mémoire tampon de stencil et peut donc être utilisé avec un format de *profondeur de 16 bits*.

> [!NOTE]
> pour déterminer rapidement quels objets d’une scène n’écrivent pas dans le tampon de profondeur visuellement, vous pouvez utiliser l’utilitaire de [ *tampon de profondeur de rendu*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) sous l' *éditeur Paramètres* dans le profil de Configuration MRTK.

### <a name="optimize-mesh-data"></a>Optimiser les données de maillage

Les paramètres d' [optimisation des données de maillage](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) tentent de supprimer les attributs de vertex inutilisés dans votre application. Pour ce faire, le paramètre s’exécute sur chaque passage de nuanceur dans chaque matériau de chaque maillage de la Build. Cela convient à la taille des données de jeu et aux performances d’exécution, mais peut nuire considérablement aux temps de génération.

Il est recommandé de désactiver ce paramètre pendant le développement et de le réactiver pendant la création de la build « Master ». le paramètre se trouve sous **modifier**  >  **Project Paramètres**  >  **Player**  >  **autre Paramètres**  >  **optimiser les données de maillage**.

## <a name="general-recommendations"></a>Recommandations générales

Les performances peuvent être un défi en constante évolution pour les développeurs de réalité mixte et le spectre des connaissances pour rationaliser les performances. Toutefois, il existe des recommandations générales pour comprendre comment aborder les performances d’une application.

Il est utile de simplifier l’exécution d’une application dans les éléments qui s’exécutent sur le *processeur* ou le *GPU* et, par conséquent, de déterminer si une application est limitée par l’un ou l’autre des composants.  Il peut y avoir des goulots d’étranglement qui couvrent les unités de traitement et certains scénarios uniques qui doivent être soigneusement étudiés. Toutefois, pour la prise en main, il est judicieux de comprendre où une application s’exécute le plus longtemps.

### <a name="gpu-bounded"></a>Processeur graphique limité

Étant donné que la plupart des plateformes pour les applications de réalité mixte utilisent le [rendu stéréoscopique](https://en.wikipedia.org/wiki/Stereoscopy), il est très courant de les délimiter par GPU en raison de la nature du rendu d’un écran « à deux larges ». Futhermore, les plateformes de réalité mixte mobile, telles que HoloLens ou Oculus Quest, sont limitées par le processeur de classe mobile & la puissance de traitement du GPU.

Lorsque vous vous concentrez sur le GPU, il y a généralement deux étapes importantes qu’une application doit effectuer pour chaque trame.

1. Exécuter le [nuanceur de sommets](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. Exécuter le [nuanceur de pixels](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (également appelé nuanceur de fragments)

Sans plongée dans le champ complexe de l’ordinateur Graphics & de [rendu des pipelines](https://en.wikipedia.org/wiki/Graphics_pipeline), chaque étape de nuanceur est un programme qui s’exécute sur le GPU pour produire les éléments suivants.

1. Les nuanceurs vertex transforment les vertex de maillage en coordonnées dans l’espace écran (c.-à-d. code exécuté par vertex)
2. Les nuanceurs de pixels calculent la couleur à dessiner pour un fragment de pixel et de maille donné (c.-à-d. exécution de code par pixel)

En ce qui concerne le réglage des performances, il est généralement plus fructueuse de se concentrer sur l’optimisation des opérations dans le nuanceur de pixels. Une application peut uniquement avoir à dessiner un cube qui aura uniquement 8 vertex. Toutefois, l’espace d’écran occupé par le cube est probablement de l’ordre de millions de pixels. Ainsi, la réduction du code du nuanceur de 10 opérations peut faire gagner beaucoup plus de travail s’il est réduit sur le nuanceur de pixels que le nuanceur de sommets.

C’est l’une des principales raisons pour tirer parti du [nuanceur standard MRTK](../features/rendering/mrtk-standard-shader.md) , car ce nuanceur exécute généralement beaucoup moins d’instructions par pixel & vertex que le nuanceur standard Unity, tout en obtenant des résultats esthétiques comparables.

|    Optimisations de l’UC      |             Optimisations GPU              |
|---------------------------|--------------------------------------------|
| Logique de simulation d’application      | Opérations de rendu |
| Simplifier la physique          | Réduire les calculs d’éclairage |
| Simplifier les animations       | Réduire le nombre de polygones & nombre d’objets dessinables |
| Gérer le garbage collection | Réduire le nombre d’objets transparents |
| Références du cache          | Évitez les effets de traitement/plein écran  |

### <a name="draw-call-instancing"></a>Instanciation des appels de dessin

L’une des erreurs les plus courantes dans Unity qui réduit les performances est le clonage de documents au moment de l’exécution. Si les GameObjects partagent le même matériau et/ou sont le même maillage, ils peuvent être optimisés dans des appels de dessin unique via des techniques telles que le *[traitement par lots statique](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, le *[traitement par lots dynamique](https://docs.unity3d.com/Manual/DrawCallBatching.html)* et l' *[instanciation de GPU](https://docs.unity3d.com/Manual/GPUInstancing.html)*. Toutefois, si le développeur modifie les propriétés du [matériau d’un convertisseur](https://docs.unity3d.com/ScriptReference/Renderer-material.html) lors de l’exécution, Unity crée une copie clone du matériau affecté.

Par exemple, s’il existe un cube 100 dans une scène, un développeur peut souhaiter affecter une couleur unique à chaque au moment de l’exécution. L’accès à [*renderr. Material. Color*](https://docs.unity3d.com/ScriptReference/Material-color.html) en C# permet à Unity de créer un nouveau matériau en mémoire pour ce convertisseur/gameobject particulier. Chacun des cubes 100 a son propre matériau et ne peut donc pas être fusionné dans un appel de dessin, mais au lieu de cela, il devient 100 demandes d’appel de l’UC au GPU.

Pour surmonter cet obstacle tout en affectant une couleur unique par cube, les développeurs doivent tirer parti de [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a>Outils de performances Unity

Unity fournit de superbes outils de performances intégrés à l’éditeur.

- [Profileur Unity](https://docs.unity3d.com/Manual//Profiler.html)
- [Débogueur de frames Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

Si vous évaluez le compromis approximatif des performances entre un nuanceur et un autre, il est utile de compiler chaque nuanceur et d’afficher le nombre d’opérations par étape de nuanceur. Pour ce faire, sélectionnez une [ressource de nuanceur](https://docs.unity3d.com/Manual/class-Shader.html) et cliquez sur le bouton *compiler et afficher le code* . Cela permet de compiler toutes les variantes du nuanceur et d’ouvrir Visual Studio avec les résultats. Remarque : les résultats des statistiques produits peuvent varier selon les fonctionnalités qui ont été activées sur les matériaux utilisant le nuanceur donné. Unity compile uniquement les variantes de nuanceur qui sont directement utilisées dans le projet actuel.

Exemple de statistiques de nuanceur standard Unity

![Statistiques de nuanceur standard Unity 1](../features/images/performance/UnityStandardShader-Stats.PNG)

Exemple de statistiques de nuanceur standard MRTK

![Statistiques de nuanceur standard MRTK 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>Voir aussi

### <a name="unity"></a>Unity

- [Optimisation des performances Unity pour les débutants](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Didacticiels sur l’optimisation des performances Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Meilleures pratiques pour l’optimisation Unity](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [Optimisation des performances graphiques](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [Guide pratique de l’optimisation mobile](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Paramètres recommandé pour unity](/windows/mixed-reality/recommended-settings-for-unity)
- [Comprendre les performances de la réalité mixte](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recommandations de performances pour Unity](/windows/mixed-reality/performance-recommendations-for-unity)
- [Guide de Suivi d’v nements pour Windows unity](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [Recommandations relatives aux performances](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [Outils pour les performances](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>Optimisation du maillage

- [Optimiser les modèles 3D](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Meilleures pratiques pour la conversion et l’optimisation des modèles 3D en temps réel](/dynamics365/mixed-reality/import-tool/best-practices)
