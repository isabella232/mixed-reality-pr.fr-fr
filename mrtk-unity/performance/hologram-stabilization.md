---
title: Stabilisation d’hologramme
description: Performances des hologrammes dans des conditions d’environnement et de fréquence d’images différentes.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, suivi de l’environnement, TMP,
ms.openlocfilehash: 7aab167f2d850a4bca88a2cc40aae4f3cc50fb4b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176484"
---
# <a name="hologram-stabilization"></a>Stabilisation d’hologramme

## <a name="performance"></a>Performances

Pour que la plateforme et le périphérique de réalité mixte sous-jacents produisent les meilleurs résultats, il est important d’effectuer des fréquences d’images. La fréquence d’images cible (par exemple : 60 FPS ou 90 FPS) varie selon les plateformes et les appareils. Toutefois, les applications de réalité mixte qui respectent la fréquence d’images comporteront des hologrammes stables, ainsi qu’un suivi efficace des têtes, le suivi des mains et bien plus encore.  

## <a name="environment-tracking"></a>Suivi de l’environnement

Le rendu holographique stable s’appuie fortement sur le suivi des poses par la plateforme & appareil. Unity restitue la scène chaque image de la caméra est estimée et fournie par la plateforme sous-jacente. Si ce suivi ne suit pas correctement le mouvement de la tête réelle, les hologrammes apparaîtront mal. ceci est particulièrement évident et important pour les appareils AR comme les HoloLens où les utilisateurs peuvent associer des hologrammes virtuels au monde réel. Les performances sont significatives pour le suivi de la tête fiable, mais il peut également y avoir d' [autres fonctionnalités importantes](/windows/mixed-reality/environment-considerations-for-hololens). Les types d’éléments d’environnement qui ont un impact sur l’expérience utilisateur dépendent des spécificités de la plateforme ciblée.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

la plateforme Windows Mixed Reality fournit des [documents de référence](/windows/mixed-reality/hologram-stability) pour la stabilisation des hologrammes sur la plateforme. Toutefois, il existe un certain nombre d’outils clés que les développeurs peuvent utiliser pour améliorer l’expérience visuelle des hologrammes pour les utilisateurs.

### <a name="depth-buffer-sharing"></a>Partage de mémoire tampon de profondeur

Les développeurs Unity ont la possibilité de partager le tampon de profondeur de l’application avec la plateforme. Cela fournit des informations, où des hologrammes existent pour un frame actuel, que la plateforme peut utiliser pour stabiliser des hologrammes via un processus d’assistance matérielle appelé reprojection Late-Stage.

#### <a name="late-stage-reprojection"></a>Reprojection à l’étape tardive

à la fin du rendu d’un frame, la plateforme Windows Mixed Reality prend les cibles de rendu de profondeur & de couleur générées par l’application et transforme la sortie finale de l’écran en compte pour tout déplacement de tête depuis la dernière prédiction de pose. L’exécution de la boucle de jeu d’une application prend du temps. Par exemple, à 60 FPS, cela signifie que l’application prend ~ 16.667 ms pour afficher un frame. Même si cela peut sembler un rien de temps, la position et l’orientation de l’utilisateur changent en fonction de nouvelles matrices de projection pour l’appareil photo en cours de rendu. La reprojection en phase tardive transforme les pixels de l’image finale pour tenir compte de cette nouvelle perspective.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>Plan de stabilisation par pixel et LSR

en fonction du point de terminaison de l’appareil et de la version du système d’exploitation exécuté sur un appareil Windows Mixed Reality, l’algorithme de reprojection Late-Stage sera effectué par pixel ou par le biais d’un [plan de stabilisation](/windows/mixed-reality/hologram-stability#stabilization-plane).

##### <a name="per-pixel-depth-based"></a>Basé sur la profondeur par pixel

La reprojection basée sur la profondeur par pixel implique l’utilisation de la mémoire tampon de profondeur pour modifier la sortie de l’image par pixel et ainsi stabiliser les hologrammes à différentes distances. Par exemple, une sphère 1m peut être devant un pilier qui est en millions de mètres. Les pixels représentant la sphère auront une transformation différente des pixels éloignés représentant le pilier si l’utilisateur a légèrement incliné son tête. La reprojection par pixel prendra en compte cette différence de distance à chaque pixel pour une reprojection plus précise.

##### <a name="stabilization-plane"></a>Plan de stabilisation

S’il n’est pas possible de créer une mémoire tampon de profondeur exacte à partager avec la plateforme, une autre forme de LSR utilise un plan de stabilisation. Tous les hologrammes d’une scène recevront une certaine stabilisation, mais les hologrammes se trouvant dans le plan souhaité recevront la stabilisation matérielle maximale. Le point et la normale du plan peuvent être fournis à la plateforme via l’API *HolographicSettings. SetFocusPointForFrame* [fournie par Unity](/windows/mixed-reality/focus-point-in-unity).

#### <a name="depth-buffer-format"></a>Format de mémoire tampon de profondeur

si le ciblage HoloLens pour le développement, il est fortement recommandé d’utiliser le format de mémoire tampon de profondeur de 16 bits par rapport à 24 bits. Cela permet d’économiser énormément de performances, bien que les valeurs de profondeur présentent moins de précision. Pour compenser la précision inférieure et éviter la [lutte z](https://en.wikipedia.org/wiki/Z-fighting), il est recommandé de réduire le [plan de découpage éloigné](https://docs.unity3d.com/Manual/class-Camera.html) de la valeur par défaut de 1000MD définie par Unity.

> [!NOTE]
> Si vous utilisez le *format de profondeur 16 bits, les* effets requis pour la mémoire tampon des stencils ne fonctionneront pas, car [Unity ne crée pas de tampon de stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) dans ce paramètre. Si vous sélectionnez le *format de profondeur 24 bits* , vous créez généralement une [mémoire tampon de stencil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html), le cas échéant sur la plateforme graphique de point de terminaison.

#### <a name="depth-buffer-sharing-in-unity"></a>Partage de mémoire tampon de profondeur dans Unity

Pour pouvoir utiliser des LSR à base de profondeur, les développeurs doivent effectuer deux étapes importantes.

1. sous **modifier**  >  **Project Paramètres**  >  **Player**  >  **XR Paramètres** kits de développement logiciel (  >  **sdk) Virtual realisation** > activer le **partage de mémoire tampon de profondeur**
    1. si vous ciblez HoloLens, il est recommandé de sélectionner également le **format de profondeur 16 bits** .
1. Lors du rendu de couleur à l’écran, afficher la profondeur également

Les [GameObjects opaques](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) dans Unity sont généralement écrits automatiquement en profondeur. Toutefois, les objets de texte transparent & n’écrivent généralement pas en profondeur par défaut. en cas d’utilisation du nuanceur Standard MRTK ou de la Pro maille de texte, cela peut être facilement résolu.

> [!NOTE]
> pour déterminer rapidement quels objets d’une scène n’écrivent pas dans le tampon de profondeur visuellement, vous pouvez utiliser l’utilitaire de [ *tampon de profondeur de rendu*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) sous l' *éditeur Paramètres* dans le profil de Configuration MRTK.

##### <a name="transparent-mrtk-standard-shader"></a>Nuanceur transparent MRTK standard

Pour les matériaux transparents à l’aide du [nuanceur standard MRTK](../features/rendering/MRTK-standard-shader.md), sélectionnez le matériau pour l’afficher dans la fenêtre de l' *inspecteur* . Cliquez ensuite sur le bouton *corriger maintenant* pour convertir la matière en écriture en profondeur (c.-à-d. Z-écrire sur).

Avant

![Mémoire tampon de profondeur avant correction du nuanceur standard MRTK](../features/images/performance/DepthBufferFixNow_Before.PNG)

Après

![Nuanceur standard MRTK fixe du tampon de profondeur](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Maille de texte Pro

pour Pro objets de maillage de texte, sélectionnez le GameObject TMP pour l’afficher dans l’inspecteur. Sous le composant matériau, faites basculer le nuanceur pour la documentation affectée afin d’utiliser le nuanceur MRTK TextMeshPro.

![correction du tampon de la profondeur du maillage de texte Pro](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>Nuanceur personnalisé

Si vous écrivez un nuanceur personnalisé, ajoutez l' [indicateur ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) au début de la définition du bloc de *passe* pour configurer le nuanceur à écrire dans la mémoire tampon de profondeur.

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>Enstockages opaques

Si les méthodes ci-dessus ne fonctionnent pas pour un scénario donné (par exemple, à l’aide de l’interface utilisateur Unity), il est possible d’écrire un autre objet dans le tampon de profondeur. Un exemple courant consiste à utiliser le texte de l’interface utilisateur Unity sur un panneau flottant dans une scène. En rendant le panneau opaque ou au moins écrit en profondeur, le texte & le panneau sera stabilisé par la plateforme, car leurs valeurs z sont tellement proches les unes des autres.

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens)

En plus de vous assurer que les configurations correctes sont respectées pour garantir la stabilité visuelle, il est important de s’assurer que les hologrammes restent stables à leurs emplacements physiques corrects. Pour informer la plateforme des emplacements importants dans un espace physique, les développeurs peuvent tirer parti de [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) sur GameObjects qui doivent rester dans un même emplacement. Un [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) est un composant ajouté à un gameobject qui prend un contrôle absolu sur la transformation de cet objet.

les appareils tels que les HoloLensnt constamment analyser et apprendre à propos de l’environnement. ainsi, à mesure que le HoloLens effectue le suivi du mouvement & position dans l’espace, ses estimations sont mises à jour et le [système de coordonnées unity est ajusté](/windows/mixed-reality/coordinate-systems-in-unity). par exemple, si un GameObject est placé 1m à partir de l’appareil photo au démarrage, étant donné que le HoloLens effectue le suivi de l’environnement, il peut réaliser le point physique où se trouve le GameObject est en fait 1.1 m. Cela entraînerait la dérive de l’hologramme. L’application d’un WorldAnchor à un GameObject permet à l’ancre de contrôler la transformation de l’objet afin que l’objet reste à l’emplacement physique correct (c.-à-d. Mettez à jour vers la version 1.1 m à la place de 1m au moment de l’exécution). Pour conserver les [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) entre les sessions d’application, les développeurs peuvent utiliser le [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) pour [enregistrer et charger WorldAnchors](/windows/mixed-reality/persistence-in-unity).

> [!NOTE]
> Une fois qu’un composant WorldAnchor a été ajouté à un GameObject, il n’est pas possible de modifier la transformation de ce GameObject (c.-à-d. transformation. position = x). Un développeur doit supprimer le WorldAnchor pour modifier la transformation.

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

Si vous souhaitez une alternative à l’utilisation manuelle des ancres, consultez les outils de verrouillage Microsoft World. 

> [!div class="nextstepaction"]
> [Installer avec l’outil de fonctionnalité MR](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>Voir aussi

- [Performances](../performance/perf-getting-started.md)
- [Considérations relatives à l’environnement pour HoloLens](/windows/mixed-reality/environment-considerations-for-hololens)
- [Windows Mixed Reality de stabilité des hologrammes](/windows/mixed-reality/hologram-stability)
- [Point de focus dans Unity](/windows/mixed-reality/focus-point-in-unity)
- [Systèmes de coordonnées dans Unity](/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistance dans Unity](/windows/mixed-reality/persistence-in-unity)
- [Comprendre les performances de la réalité mixte](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recommandations de performances pour Unity](/windows/mixed-reality/performance-recommendations-for-unity)
