---
title: Outil d’utilisation des fonctionnalités d’entrée
description: Documentation InputFeatureUsage Tool dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 9d5e80ee5f31086b12ec2b82ab2368361fb738e03ea7fe5cf02ba0b4bd22c0b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189432"
---
# <a name="input-feature-usage-tool"></a>Outil d’utilisation des fonctionnalités d’entrée

L’outil InputFeatureUsage est un outil d’exécution (sur un appareil ou dans l’éditeur) qui permet aux développeurs de déterminer rapidement le InputFeatureUsages Unity disponible pour une source d’entrée détectée (par exemple, un contrôleur de mouvement ou une main articulée).

> [!NOTE]
> Cette scène fonctionne uniquement sur Unity 2019,3 ou une version ultérieure.

Cet outil est très utile lors du développement de la prise en charge d’un nouveau contrôleur matériel. Elle peut également aider à confirmer un problème de mappage de contrôle soupçonné dans la classe de prise en charge pour un contrôleur existant.

![Outil InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Utilisation de l’outil InputFeatureUsage

Pour commencer à utiliser l’outil InputFeatureUsage, accédez à **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** et ouvrez la scène **InputFeatureUsageTool** . Une fois la scène chargée, le projet peut être exécuté dans l’éditeur, à l’aide du mode lecture ou créé et exécuté sur un appareil.

Pour examiner les mappages d’Unity pour un contrôleur :

- Connecter le contrôleur
- Appuyez sur chaque bouton et déplacez chaque axe
- Notez les utilisations des fonctionnalités dans l’affichage
- Mettre à jour les mappages de contrôle dans le fournisseur de données du système d’entrée pour le contrôleur

> [!NOTE]
> l’outil InputFeatureUsage ne fait pas appel aux composants Shared Computer Toolkit de la réalité mixte Microsoft. Il communique directement avec Unity pour déterminer et afficher les utilisations des fonctionnalités.

### <a name="panels"></a>Panneaux

Les panneaux affichent l’état actuel de tous les InputFeatureUsages signalés sur toutes les sources d’entrée Unity détectées.

Le plus petit volet situé dans la partie supérieure répertorie les noms de toutes les sources détectées.

## <a name="see-also"></a>Voir aussi

- [Création d’un fournisseur de données de système d’entrée](../input/create-data-provider.md)
- [Outil de mappage de contrôleur](controller-mapping-tool.md)
