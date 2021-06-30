---
title: Configuration des diagnostics
description: Documentation sur la configuration des diagnostics dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 211ee2ed06ba9b13bd90169bcc7ee50da4594034
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121797"
---
# <a name="configuring-the-diagnostics-system"></a>Configuration du système de diagnostic

## <a name="general-settings"></a>Paramètres généraux :

![Paramètres généraux des diagnostics](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>Activer la journalisation documentée

Indique si la journalisation MRTK détaillée est activée. La valeur par défaut est false, mais peut être activée pour effectuer des suivis détaillés permettant à l’équipe MRTK de déboguer/explorer les problèmes. Par exemple, lors de l’enregistrement d’un problème, l’attachement des journaux du lecteur Unity (à partir de l’éditeur ou du lecteur) peut aider à réduire la source des bogues et des problèmes.

Notez que cette option est indépendante du fait que le système de diagnostics soit activé ou non, ce qui s’affiche sous le système de diagnostics, car il s’agit d’une option de journalisation, mais qui, au final, fonctionne à un niveau supérieur, car il affecte la journalisation sur l’ensemble du code base MRTK.

### <a name="show-diagnostics"></a>Afficher les diagnostics

Indique si le système de diagnostics doit afficher ou non les options de diagnostic configurées.

Lorsque cette option est désactivée, toutes les options de diagnostic configurées sont masquées.

## <a name="profiler-settings"></a>Paramètres du profileur

![Paramètres du profileur de diagnostic](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>Afficher le profileur

Indique si le générateur de profils visuels doit être affiché.

### <a name="frame-sample-rate"></a>Taux d’échantillonnage de trame

Durée, en secondes, de collecte des frames pour le calcul de la fréquence d’images. La plage est comprise entre 0 et 5 secondes.

### <a name="window-anchor"></a>Ancre de fenêtre

À quelle partie du port d’affichage la fenêtre du profileur doit-elle être ancrée. La valeur par défaut est Lower Center.

### <a name="window-offset"></a>Décalage de la fenêtre

Décalage, à partir du centre du port d’affichage, pour placer le générateur de profils Visual. Le décalage sera dans le sens de la propriété d’ancrage de la *fenêtre* .

### <a name="window-scale"></a>Échelle de fenêtre

Multiplicateur de taille appliqué à la fenêtre du profileur. Par exemple, si vous définissez la valeur sur 2, la taille de la fenêtre sera double.

### <a name="window-follow-speed"></a>Fenêtre suivre la vitesse

Vitesse à laquelle déplacer la fenêtre du profileur pour maintenir la visibilité dans le port d’affichage.

## <a name="programmatically-controlling-the-diagnostics-system"></a>Contrôle du système de diagnostics par programmation

Il est également possible d’activer ou de désactiver la visibilité du système de diagnostic et du profileur au moment de l’exécution. Par exemple, le code ci-dessous masque le système de diagnostic et le profileur.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>Voir aussi

- [Système de diagnostic](diagnostics-system-getting-started.md)
- [Utilisation du générateur de profils Visual](using-visual-profiler.md)
