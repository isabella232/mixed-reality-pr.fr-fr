---
title: Outil de mappage de contrôleur
description: Documentation sur l’outil de mappage de contrôleur dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f00dc01555ef158dab21334761bd23ef6a70dba4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144087"
---
# <a name="controller-mapping-tool"></a>Outil de mappage de contrôleur

L’outil de mappage de contrôleur est un outil d’exécution (sur un appareil ou dans l’éditeur) qui permet aux développeurs de déterminer rapidement l’axe d’entrée Unity et les mappages de boutons pour un contrôleur matériel (par exemple, le contrôleur de mouvement).

Cet outil est très utile lors du développement de la prise en charge d’un nouveau contrôleur matériel. Elle peut également aider à confirmer un problème de mappage de contrôle soupçonné dans la classe de prise en charge pour un contrôleur existant.

![Outil de mappage de contrôleur](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Utilisation de l’outil de mappage de contrôleur

Pour commencer à utiliser l’outil de mappage de contrôleur, accédez à **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** et ouvrez la scène **ControllerMappingTool** . Une fois la scène chargée, le projet peut être exécuté dans l’éditeur, à l’aide du mode lecture ou créé et exécuté sur un appareil.

Pour examiner les mappages d’Unity pour un contrôleur :

- Connecter le contrôleur
- Appuyez sur chaque bouton et déplacez chaque axe
- Notez les mappages dans l’affichage
- Mettre à jour les mappages de contrôle dans le fournisseur de données du système d’entrée pour le contrôleur

> [!NOTE]
> L’outil de mappage de contrôleur n’utilise pas les composants de Microsoft Mixed Reality Toolkit. Il communique directement avec Unity pour déterminer et afficher les mappages de contrôle.

### <a name="all-controls-display"></a>Tous les contrôles sont affichés

Le panneau d’affichage volumineux signale l’état de tous les axes et boutons d’entrée Unity définis (par ex., l’axe 10, le bouton 3). Ce panneau fournit une vue complète de l’état du contrôleur.

![Tous les contrôles sont affichés](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Affichage des contrôles actifs

Le panneau d’affichage plus petit et étroit affiche les axed d’entrée Unity et les boutons qui sont dans un état actif (par exemple, un bouton est enfoncé). L’affichage des contrôles actifs fournit une vue de synthèse facile à lire de l’état du contrôleur.

![Affichage des contrôles actifs](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Voir aussi

- [Création d’un fournisseur de données de système d’entrée](../input/create-data-provider.md)
- [Outil InputFeatureUsage](input-feature-usage-tool.md)
