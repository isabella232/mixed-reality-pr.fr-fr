---
title: Comprendre les performances de la réalité mixte
description: Découvrez des informations et des détails avancés sur l’analyse et l’optimisation des performances des applications Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, performances, optimisation, UC, GPU
ms.openlocfilehash: 5012c30dce1ca4149324c916355922086a33c258
ms.sourcegitcommit: 6725b83adf13f6573faacb27db2bcaafe80df472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615125"
---
# <a name="understanding-performance-for-mixed-reality"></a>Comprendre les performances de la réalité mixte

Cet article est une introduction à la compréhension de l’importance des performances de votre application de réalité mixte.  L’expérience utilisateur peut être très détériorée si votre application n’est pas exécutée à la fréquence d’images optimale. Les hologrammes apparaissent instables et le suivi des têtes de l’environnement n’est pas exact, ce qui entraîne une mauvaise expérience de l’utilisateur. Les performances doivent être considérées comme une fonctionnalité de première classe pour le développement de la réalité mixte et non pour une tâche polonaise.

Les valeurs de fréquence d’images performante pour chaque plateforme cible sont répertoriées ci-dessous.

| Plateforme | Fréquence d’images cible |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 i/s |
| [Windows Mixed Reality ultra PC](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [PC Windows Mixed Reality](../../discover/immersive-headset-hardware-details.md) | 60 i/s |

Le cadre ci-dessous décrit les meilleures pratiques pour atteindre les fréquences d’images cibles. Nous vous recommandons de lire les [recommandations relatives aux performances de l’article Unity](../unity/performance-recommendations-for-unity.md) pour obtenir des conseils sur la mesure et l’amélioration de la fréquence d’images dans l’environnement Unity.

## <a name="understanding-performance-bottlenecks"></a>Comprendre les goulots d’étranglement des performances

Si votre application comporte une cadence de trames, la première étape consiste à analyser et à comprendre où votre application est gourmande en calculs. Deux processeurs principaux sont responsables du travail de rendu de votre scène : le processeur et le GPU, chacun gérant différents aspects de votre application de réalité mixte. Les goulots d’étranglement peuvent être les suivants : 

1. **Thread d’application-UC** -
    Responsable de votre logique d’application, y compris le traitement des entrées, des animations, de la physique et d’autres logiques d’application.
2. **Rendu thread-CPU au GPU** -responsable de l’envoi des appels de dessin au GPU. Lorsque votre application souhaite effectuer le rendu d’un objet tel qu’un cube ou un modèle, ce thread envoie une demande au GPU pour effectuer les opérations.
3. Le **GPU** , le plus souvent, gère le pipeline graphique de votre application pour transformer des données 3D (modèles, textures, etc.) en pixels. Il produit finalement une image 2D à envoyer à l’écran de votre appareil.

![Durée de vie d’un frame](images/lifetime-of-a-frame.png)

En règle générale, les applications HoloLens sont liées au GPU, mais pas toujours. Utilisez les outils et les techniques ci-dessous pour comprendre où votre application particulière est engorgée.

## <a name="how-to-analyze-your-application"></a>Comment analyser votre application

De nombreux outils vous permettent de comprendre le profil de performances et les goulots d’étranglement potentiels dans votre application de réalité mixte. 

Voici quelques outils courants pour vous aider à recueillir des informations de profilage détaillés pour votre application :
- [Analyseurs de performances graphiques Intel](https://software.intel.com/gpa)
- [Débogueurs graphiques Visual Studio](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Profileur Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Débogueur de frames Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Insights inréel](../unreal/unreal-insights.md)
- [PHOTO](https://devblogs.microsoft.com/pix/)
- [Pofiling GPU en non réel](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>Comment Profiler dans n’importe quel environnement

Une façon de déterminer si votre application est liée au GPU ou à l’UC est de réduire la résolution de la sortie de la cible de rendu. En réduisant le nombre de pixels à calculer, vous réduisez la charge du GPU. L’appareil est rendu sur une texture plus petite, puis sur un échantillon pour afficher votre image finale.

Après avoir réduit la résolution de rendu, si :
1) L’application de fréquence d’images **augmente**, vous êtes probablement **lié au GPU**
1) Fréquence d’application **inchangée**, vous êtes probablement lié à l' **UC**

>[!NOTE]
>Unity offre la possibilité de modifier facilement la résolution de la cible de rendu de votre application au moment de l’exécution via la propriété *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* . La résolution de l’image finale présentée sur l’appareil est fixe. La plateforme échantillonne la sortie de résolution inférieure pour générer une image de résolution supérieure pour le rendu sur les affichages. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Comment améliorer votre application

### <a name="cpu-performance-recommendations"></a>Recommandations sur les performances de processeur

En règle générale, la plupart des travaux dans une application de réalité mixte sur l’UC impliquent la « simulation » de la scène et le traitement de votre logique d’application. Les éléments suivants sont ciblés pour l’optimisation :

- Animations
- Physique
- Allocations de mémoire
- Algorithmes complexes (c.-à-d. cinématique inverse, recherche de chemin d’accès)

### <a name="gpu-performance-recommendations"></a>Recommandations sur les performances de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Fonctionnement de la bande passante et du taux de remplissage
Lors du rendu d’une trame sur le GPU, une application est liée par une bande passante de mémoire ou un taux de remplissage.

- La **bande passante** de la mémoire est le taux de lectures et d’écritures que le GPU peut effectuer à partir de la mémoire
    - Pour identifier les limitations de bande passante, réduisez la qualité de la texture et vérifiez si la fréquence d’images a été améliorée.
    - Dans Unity, modifiez la **qualité** de la texture dans **modifier** les paramètres du  >  **projet**  >  **[paramètres de qualité](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- Le **taux de remplissage** fait référence aux pixels qui peuvent être dessinés par seconde par le GPU.
    - Pour identifier les limitations du taux de remplissage, réduisez la résolution de l’affichage et vérifiez si les images sont améliorées. 
    - Dans Unity, utilisez la propriété *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

La bande passante de la mémoire implique généralement des optimisations pour :
1) Résolutions de texture inférieures
2) Utilisez moins de textures (normales, spéculaire, etc.)

Le taux de remplissage est axé sur la réduction du nombre d’opérations qui doivent être calculées pour un pixel final rendu, notamment :
1) Nombre d’objets à restituer/traiter
2) Nombre d’opérations par nuanceur
3) Nombre d’étapes du GPU vers le résultat final (nuanceurs Geometry, effets de la postérieure au traitement, etc.)
4) Nombre de pixels à afficher (résolution d’affichage)

#### <a name="reduce-polygon-count"></a>Réduire le nombre de polygones

Plus le nombre de polygones est élevé, plus il est important d’opérations pour le GPU, donc le fait de [réduire le nombre de polygones](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) dans votre scène réduit le temps de rendu. Il existe d’autres facteurs qui rendent l’ombrage de la géométrie cher, mais le nombre de polygones est la mesure la plus simple pour déterminer la quantité de travail nécessaire au rendu d’une scène.

#### <a name="limit-overdraw"></a>Limiter le surdessin

Un surdessin élevé se produit lorsque plusieurs objets sont rendus mais non affichés à l’écran, car ils sont masqués par un objet Boucher. Imaginez que vous examinez un mur qui contient des objets en arrière-plan. Toute la géométrie est traitée pour le rendu, mais seul le mur opaque doit être rendu, ce qui entraîne des opérations inutiles.

#### <a name="shaders"></a>Nuanceurs

Les nuanceurs sont des petits programmes qui s’exécutent sur le GPU et effectuent deux étapes importantes du rendu :
1) Détermination des vertex à dessiner et de leur emplacement dans l’espace à l’écran (le nuanceur de sommets)
    - Le nuanceur de sommets est exécuté par vertex pour chaque maille.
2) Détermination de la couleur de chaque pixel (nuanceur de pixels)
    - Le nuanceur de pixels est exécuté par pixel et est rendu par la géométrie à la texture de rendu cible.

En règle générale, les nuanceurs effectuent de nombreuses transformations et des calculs d’éclairage. Bien que les modèles d’éclairage complexes, les ombres et les autres opérations puissent générer des résultats fantastiques, ils sont également fournis avec un prix. La réduction du nombre d’opérations calculées dans les nuanceurs peut réduire considérablement le travail nécessaire pour le GPU par trame.

##### <a name="shader-coding-recommendations"></a>Recommandations en matière de codage de nuanceur

- Utiliser le filtrage bilinéaire, dans la mesure du possible
- Réorganiser les expressions pour utiliser des intrinsèques MAD pour effectuer une multiplication et un ajout en même temps
- Précalculez autant que possible sur le processeur et transmettez-les en tant que constantes au matériel.
- **Privilégier les opérations de déplacement du nuanceur de pixels vers le nuanceur de sommets**
    - En règle générale, le nombre de vertex est bien plus petit que le nombre de pixels (720p est de 921 600 pixels, 1080p correspond à 2 073 600 pixels, etc.)

#### <a name="remove-gpu-stages"></a>Supprimer les étapes du GPU

Les effets postérieurs au traitement peuvent être coûteux et augmenter le taux de remplissage de votre application, y compris les techniques d’anticrénelage telles que MSAA. Sur HoloLens, nous vous recommandons d’éviter ces techniques et d’autres étapes de nuanceur, telles que Geometry, la coque et les nuanceurs de calcul.

## <a name="memory-recommendations"></a>Recommandations sur la mémoire

Les opérations d’allocation et de désallocation de mémoire excessives peuvent entraîner des performances incohérentes, des frames figés et d’autres comportements nuisibles. Il est particulièrement important de comprendre les considérations relatives à la mémoire lors du développement dans Unity, car la gestion de la mémoire est contrôlée par le garbage collector.

#### <a name="object-pooling"></a>Mise en pool d’objets

Le mise en pool d’objets est une technique populaire pour réduire le coût des allocations et des désallocations continues d’objets. Pour la réaliser, vous devez allouer un grand pool d’objets identiques et réutiliser des instances inactives disponibles de ce pool au lieu de générer et détruire constamment des objets au fil du temps. Les pools d’objets conviennent parfaitement aux composants réutilisables qui ont une durée de vie variable pendant une application.

## <a name="see-also"></a>Voir aussi
- [Recommandations de performances pour Unity](../unity/performance-recommendations-for-unity.md)
- [Paramètres recommandés pour Unity](../unity/recommended-settings-for-unity.md)
- [Recommandations sur les performances pour Unreal](../unreal/performance-recommendations-for-unreal.md)
- [Recommandations matérielles dans Unreal](../unreal/unreal-materials.md)
- [Optimiser les modèles 3D](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Meilleures pratiques pour la conversion et l’optimisation des modèles 3D en temps réel](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)
- [Instructions relatives aux performances pour les artistes et les concepteurs pour les](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Bonnes pratiques pour les](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)
