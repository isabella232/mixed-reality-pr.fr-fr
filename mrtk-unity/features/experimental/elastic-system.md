---
title: Système élastique
description: Documentation relative à la simulation des élastiques dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, ElasticsSystem,
ms.openlocfilehash: e34b9ea68bfbdc7b7f285686565a1e049ba58ad8677b16e915a2db8272ec1cbe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217900"
---
# <a name="elastic-system"></a>Système élastique

![Système élastique](../images/elastics/Elastics_Main1.gif)

MRTK est fourni avec un système de simulation élastique qui inclut une large gamme de sous-classes extensibles et flexibles, qui offre des liaisons pour les ressorts de Quaternion à quatre dimensions, les ressorts de volume 3D et les systèmes à ressort linéaires simples.

Actuellement, les composants MRTK suivants prenant en charge le [Gestionnaire élastique](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) peuvent tirer parti des fonctionnalités élastiques :

- [Contrôle des limites](../ux-building-blocks/bounds-control.md)
- [Manipulateur d’objets](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Gestionnaire élastiques

![System2 élastique](../images/elastics/Elastics_Main.gif)

Le gestionnaire élastique traite les transformations transmises et les alimente dans le système élastique.

L’activation des élastiques pour les composants personnalisés peut être effectuée en deux étapes :

1. Appel de la méthode Initialize au démarrage de la manipulation, mise à jour du système avec la transformation hôte actuelle.
1. Interrogation de ApplyHostTransform chaque fois qu’un calcul élastique doit être effectué sur la transformation cible mise à jour.

Notez que les élastiques continuent de simuler une fois les manipulations terminées (par le biais de la boucle de mise à jour élastiques Manager). Pour bloquer le comportement, les [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) de mise à jour automatique élastiques peuvent avoir la valeur false.

Par défaut, le composant de gestionnaire élastiques, lorsqu’il est ajouté à un objet de jeu, n’a pas de élastiques activés pour les types de transformations.
Le champ `Manipulation types using elastic feedback` doit être activé pour des types de transformation spécifiques afin de créer des étendues et des configurations élastiques pour le type sélectionné.

### <a name="elastics-configurations"></a>Configurations élastiques

Comme pour les [configurations de contrôle de limites, le](../ux-building-blocks/bounds-control.md#configuration-objects)gestionnaire élastique est fourni avec un ensemble d’objets de configuration qui peuvent être stockés en tant qu’objets pouvant faire l’objet d’un script et partagés entre différentes instances ou prefabs. Les configurations peuvent être partagées et liées en tant que fichiers de ressources pouvant faire l’élément d’un script ou imbriqués dans prefabs. D’autres configurations peuvent également être définies directement sur l’instance sans liaison à une ressource scriptable externe ou imbriquée.

L’inspecteur du gestionnaire élastiques indique si une configuration est partagée ou inline dans le cadre de l’instance actuelle en présentant un message dans l’inspecteur de propriété. En outre, les instances partagées ne peuvent pas être modifiées directement dans la fenêtre de propriétés du gestionnaire élastiques elle-même, mais à la place, la ressource à laquelle elle est liée doit être directement modification pour éviter toute modification accidentelle des configurations partagées.

Le gestionnaire élastique offre des options d’objets de configuration pour les types de transformation suivants, chacun représenté par un [objet de configuration élastique](#elastic-configuration-object):

- Élastique de translation
- Élastique de rotation
- Élastique d’échelle

#### <a name="elastic-configuration-object"></a>Objet de configuration élastique

Une configuration élastique définit les propriétés d’un système différentiel d’oscillateur harmonique amorti.
Les propriétés suivantes peuvent être ajustées, mais elles sont déjà fournies avec un ensemble de valeurs par défaut dans MRTK :

- **Masse**: masse de l’élément de l’oscillateur simulé.
- **HandK**: constante Spring à la main.
- **EndK**: constante Spring Cap end.
- **SnapK**: constante de ressort de point d’ancrage.
- **Faites glisser**: facteur de glissement/amortisseur, proportionnel à la vélocité.

### <a name="elastics-extents"></a>Étendues élastiques

Les paramètres d’étendues élastiques varient selon le type de manipulation. La translation et l’échelle sont représentées par les [Extensions élastiques de volume](#volume-elastic-extent) et la rotation est représentée par une [extension élastique Quaternion](#quaternion-elastic-extent).

#### <a name="volume-elastic-extent"></a>Étendue élastique en volume

Les étendues de volume définissent un espace à trois dimensions dans lequel l’oscillateur d’harmonique humide est libre de se déplacer.

![Limites d’étirement de volume élastique](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds**: représente les limites inférieures de l’espace élastique.
- **UseBounds**: indique si les limites d’étirement doivent être respectées par le système. Si la valeur est true, lorsque l’itération actuelle de la position cible se trouve en dehors des limites d’étirement, l’effort de fin sera appliqué.
- **Points d’ancrage**: points à l’intérieur de l’espace auquel le système doit s’aligner.
- **RepeatSnapPoints**: répète les points d’alignement à l’infini. Les points d’ancrage existants serviront de modulo dans lequel les points d’alignement réels sont mappés sur les multiples entiers les plus proches de chaque point d’alignement.
- **SnapRadius**: distance à laquelle les points d’ancrage commencent à forcer le ressort.

![Grille d’accrochage de volume élastique](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Étendue élastique Quaternion

Les extensions de Quaternion définissent un espace de rotation à quatre dimensions dans lequel l’oscillateur harmonique amorti est libre de pivoter.

![Exemple de rotation élastique](../images/elastics/Elastics_Rotation.gif)

- **Points d’ancrage**: Euler angles auxquels le système doit s’aligner.
- **RepeatSnapPoints**: répète les points d’alignement. Les points d’ancrage existants serviront de modulo dans lequel les points d’alignement réels sont mappés sur les multiples entiers les plus proches de chaque point d’alignement.
- **SnapRadius**: angle d’arc à partir duquel les points d’ancrage commencent à forcer le printemps en degrés Euler.

## <a name="elastics-example-scene"></a>Exemple de scène élastique

Vous trouverez des exemples de configurations élastiques dans la `ElasticSystemExample` scène.

![Exemple de scène élastique](../images/elastics/Elastics_Example_Scene.png)
