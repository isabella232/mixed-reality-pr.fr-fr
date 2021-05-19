---
title: Système de scène - Types de scènes
description: Documentation sur différents types de scènes dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144569"
---
# <a name="scene-types"></a>Types de scènes

Les scènes ont été divisées en trois types, et chaque type a une fonction différente.

![Système de scène dans la hiérarchie](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>Scènes du contenu

Il s’agit des scènes que vous utilisez pour gérer. N’importe quel type de contenu peut être stocké dans ceux-ci, et ils peuvent être chargés ou déchargés dans n’importe quelle combinaison.

Les scènes de contenu sont activées par défaut. Toutes les scènes incluses dans le tableau de votre profil `Content Scenes` peuvent être chargées/déchargées par le service.

___

## <a name="manager-scenes"></a>Scènes du gestionnaire

Une seule scène avec une instance MixedRealityToolkit requise. Cette scène sera chargée en premier au lancement et restera chargée pendant la durée de vie de l’application. La scène Manager peut également héberger d’autres objets qui ne doivent jamais être détruits. Il s’agit de l’alternative préférée à DontDestroyOnLoad.

Pour activer cette fonctionnalité, archivez `Use Manager Scene` votre profil et faites glisser un objet de scène dans le `Manager Scene` champ.

___

## <a name="lighting-scenes"></a>Scènes d’éclairage

Ensemble de scènes qui stockent des informations d’éclairage et des objets d’éclairage. Un seul peut être chargé à la fois et leurs paramètres peuvent être mélangés pendant les charges pour des transitions d’éclairage lisse.

Les paramètres d’éclairage de Unity (lumière ambiante, skyboxes, etc.) peuvent être difficiles à gérer lors de l’utilisation d’un chargement additif, car ils sont liés à des scènes individuelles et le comportement de remplacement n’est pas simple. En pratique, cela peut entraîner des confusions lorsque des ressources sont créées dans des conditions d’éclairage qui n’obtiennent pas au moment de l’exécution.

![Paramètres d’éclairage du système de scène](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

Le système de scène utilise des scènes d’éclairage pour s’assurer que ces paramètres restent cohérents, quelles que soient les scènes chargées ou actives, en mode édition et en mode lecture.

Pour activer cette fonctionnalité, archivez `Use Lighting Scene` votre profil et remplissez le `Lighting Scenes` tableau.

### <a name="cached-lighting-settings"></a>Paramètres d’éclairage mis en cache

Votre profil stocke des copies mises en cache des paramètres d’éclairage conservés dans vos scènes d’éclairage. Si ces paramètres changent dans vos scènes d’éclairage, vous devrez mettre à jour votre cache pour vous assurer que l’éclairage s’affiche comme prévu en mode lecture. Votre profil affiche un avertissement quand il soupçonne que vos paramètres mis en cache sont obsolètes. Cliquez sur `Update Cached Lighting Settings` charge chacune de vos scènes d’éclairage, extrayez leurs paramètres, puis stockez-les dans votre profil.

![Paramètres d’éclairage mis en cache du système de scène](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Comportement de l’éditeur

L’un des avantages de l’utilisation des scènes d’éclairage est de savoir que votre contenu est correctement allumé lors de la modification. À cette fin, le service Scene garde une scène d’éclairage chargée à tout moment et copie les paramètres d’éclairage de cette scène sur la scène active actuelle.\*

Vous pouvez modifier la scène d’éclairage chargée en ouvrant l' [inspecteur de service](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) du système de scène. En mode édition, vous pouvez passer instantanément d’une scène d’éclairage à une autre. En mode lecture, vous pouvez afficher un aperçu des transitions.

![Inspecteur de système de scène](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Remarque : en général, la scène active détermine vos paramètres d’éclairage dans l’éditeur. Toutefois, nous choisissons de ne pas utiliser cette fonctionnalité pour appliquer les paramètres d’éclairage, car la scène active est également l’endroit où les objets nouvellement créés sont placés par défaut, et les scènes d’éclairage sont uniquement autorisées à contenir des composants d’éclairage. Au lieu de cela, les paramètres actuels de la scène d’éclairage sont automatiquement copiés dans les paramètres de la scène active. N’oubliez pas que cela entraînera le Surécriture des paramètres d’éclairage de votre scène de contenu.*
