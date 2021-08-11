---
title: Info-bulle
description: Vue d’ensemble de l’info-bulle dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, info-bulle,
ms.openlocfilehash: af848db0962948b1f2ada73066c4ae90730b09a99dea231ebf468a05441b85ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193250"
---
# <a name="tooltip"></a>Info-bulle

![Info-bulle main](../images/tooltip/MRTK_Tooltip_Main.png)

Les info-bulles sont généralement utilisées pour transmettre un indicateur ou des informations supplémentaires lors d’une inspection plus approfondie d’un objet. Les info-bulles peuvent être utilisées pour annoter des objets dans l’environnement physique.

## <a name="how-to-use-a-tooltip"></a>Utilisation d’une info-bulle

Une info-bulle peut être ajoutée directement à la hiérarchie et ciblée sur un objet.

Pour utiliser cette méthode, ajoutez simplement un objet de jeu et l’une des info-bulles prefabs (éléments multimédias/MRTK/Kit de développement logiciel/fonctionnalités/UX/Prefabs/info-bulles) à la hiérarchie de la scène. Dans le volet de l’inspecteur de Prefab, développez le [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script. Sélectionnez un état de Conseil et configurez l’info-bulle.  Entrez le texte correspondant à l’info-bulle dans le champ de texte. Développez le [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) script et faites glisser l’objet qui doit contenir l’info-bulle de la hiérarchie dans le champ nommé *target*. L’info-bulle est alors attachée à l’objet.
![Connecteur d’info-bulle](../images/tooltip/MRTK_Tooltip_Connector.png)

Cette utilisation suppose une info-bulle qui affiche toujours ou qui est affichée/masquée par le biais d’un script en modifiant la propriété état de l’info-bulle du composant ToolTip.

## <a name="dynamically-spawning-tooltips"></a>Génération dynamique d’info-bulles

Une info-bulle peut être ajoutée dynamiquement à un objet au moment de l’exécution et prédéfinie pour afficher et masquer sur un TAP ou sur le focus. Ajoutez simplement le [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script à n’importe quel objet de jeu. Des retards d’apparition et de disparition peuvent être définis dans l’inspecteur de scripts, ainsi qu’une durée de vie afin que l’info-bulle disparaisse après une durée définie. Les info-bulles sont également des propriétés de style, telles que les visuels d’arrière-plan du script de génération. Par défaut, l’info-bulle est ancrée à l’objet avec le script du spawn. Vous pouvez modifier cette valeur en affectant un GameObject au champ d’ancrage.

## <a name="example-scene"></a>Exemple de scène

Dans les exemples de scènes (ressources/MRTK/exemples/démonstrations/UX/info-bulles/scènes), vous pourrez trouver divers exemples d’info-bulles.

![Exemples d’info-bulle](../images/tooltip/MRTK_Tooltip_Examples.png)
