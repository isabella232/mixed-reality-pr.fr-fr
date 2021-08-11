---
title: Utilisation du profileur visuel
description: documentation relative à l’utilisation de Visual Profiler dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 5db2094b5d7354e02a9e2f06c50e4d564ea7d8d259ce31ad5a11f49a71e27839
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190929"
---
# <a name="using-the-visual-profiler"></a>Utilisation du profileur visuel

Le VisualProfiler fournit une vue en toute simplicité et en application des performances d’une application de réalité mixte. le profileur est pris en charge sur toutes les plateformes Shared Computer Toolkit de réalité mixte, y compris :

- Microsoft HoloLens (1re génération)
- Microsoft HoloLens 2
- Casques immersifs Windows Mixed Reality
- OpenVR

Lors du développement d’une application, concentrez-vous sur plusieurs parties de la scène, car le profileur visuel affiche les données relatives à la vue actuelle.

> [!IMPORTANT]
> Concentrez-vous sur certaines parties de la scène avec des objets complexes, des effets de particules ou une activité. Ces facteurs contribuent souvent à réduire les performances des applications et à offrir une expérience utilisateur moins que idéale.

## <a name="visual-profiler-interface"></a>Interface du profileur Visual

![Interface du profileur Visual](../images/diagnostics/VisualProfiler.png)

L’interface du profileur Visual comprend les composants suivants :

- [Fréquence d’images](#frame-rate)
- [Heure du frame](#frame-time)
- [Graph de frame](#frame-graph)
- [Utilisation de la mémoire](#memory-utilization)

### <a name="frame-rate"></a>Fréquence d’images

Dans le coin supérieur gauche de l’interface se trouve la fréquence d’images, mesurée en images par seconde. Pour optimiser l’expérience utilisateur et le confort, cette valeur doit être aussi élevée que possible.

La configuration matérielle et la plateforme spécifique jouent un rôle significatif dans la fréquence d’images maximale réalisable. Les valeurs cibles courantes sont les suivantes :

- Microsoft HoloLens : 60
- Windows Mixed Reality Ultra : 90

> [!NOTE]
> en raison de la [limitation de la fréquence d’images sur HoloLens lorsque la valeur de l’option MRC par défaut est active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), le profileur visual est masqué lors de la capture des vidéos et des photos. Ce paramètre peut être remplacé dans le profil du système de diagnostic.

### <a name="frame-time"></a>Durée de frame

À droite de la fréquence d’images se trouve le temps d’image, en millisecondes, passé sur le processeur. Pour atteindre les fréquences d’images cibles mentionnées précédemment, une application peut consacrer la durée suivante par image :

- 60 FPS : 16,6 ms
- 90 FPS : 11,1 ms

L’heure du GPU est prévue pour être ajoutée dans une version ultérieure.

### <a name="frame-graph"></a>Graphique de frame

Le graphique de Frame fournit un affichage graphique de l’historique de la fréquence d’images de l’application.

![Graph de frame manqué du profileur Visual](../images/diagnostics/VisualProfilerMissedFrames.png)

Lorsque vous utilisez l’application, recherchez les trames manquées qui indiquent que l’application n’atteint pas sa fréquence d’images cible et peut nécessiter un travail d’optimisation.

### <a name="memory-utilization"></a>Utilisation de la mémoire

L’affichage de l’utilisation de la mémoire permet de comprendre facilement comment la vue actuelle influe sur la consommation de mémoire d’une application.

![Graph de mémoire du profileur Visual](../images/diagnostics/VisualProfilerMemory.png)

Lorsque vous utilisez l’application, recherchez l’utilisation totale de la mémoire. Les indicateurs clés incluent l’approche de la limite de la mémoire et des modifications rapides de l’utilisation.

## <a name="customizing-the-visual-profiler"></a>Personnalisation du générateur de profils Visual

L’apparence et le comportement de Visual Profiler sont personnalisables via le profil de système de diagnostic. Pour plus d’informations, consultez [configuration du système de diagnostics](configuring-diagnostics.md) .

## <a name="see-also"></a>Voir aussi

- [Système de diagnostic](diagnostics-system-getting-started.md)
- [Configuration du système de diagnostic](configuring-diagnostics.md)
