---
title: Recommandations matérielles dans Unreal
description: Vue d’ensemble des matériaux dans un moteur inréel.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, développement, matériaux, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 11c10577bd3946facb96fd77b09265ab5ca26f24
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609570"
---
# <a name="material-recommendations-in-unreal"></a>Recommandations matérielles dans Unreal

Les documents que vous utilisez peuvent affecter directement la manière dont vos projets s’exécutent dans un moteur inréel. Cette page fait office de démarrage rapide pour les paramètres de base que vous devez utiliser pour obtenir des performances optimales de vos applications de réalité mixte.

## <a name="using-customizeduvs"></a>Utilisation de CustomizedUVs

Si vous devez fournir une mosaïque UV sur votre matériau, utilisez CustomizedUVs au lieu de modifier directement l’UV du nœud de la texture. CustomizedUVs vous permettent de manipuler des UVs dans les nuanceurs de vertex plutôt que dans le nuanceur de pixels.

![Paramètres de matériau inréel](images/unreal-materials-img-01c.png)

Vous trouverez des détails sur le matériel dans la [documentation du moteur inréaliste](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) et les exemples de pratiques recommandées dans les captures d’écran ci-dessous :

[ ![ Paramètres de matériau recommandés ](images/unreal-materials-img-01.png) dans ](images/unreal-materials-img-01.png#lightbox)la 
 *configuration d’un matériel non recommandé*

[ ![ Paramètres matériels non recommandés dans ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)la 
 *configuration d’un matériau non recommandé*

## <a name="changing-blend-mode"></a>Modifier le mode de fondu

Nous vous recommandons de définir le mode de fusion sur opaque, à moins qu’il y ait une bonne raison de le faire autrement. Les matériaux masqués et translucides sont lents. Vous trouverez plus d’informations sur les documents dans la [documentation du moteur inréel](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Modifier le mode de fondu](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Mise à jour de l’éclairage pour les appareils mobiles

La précision maximale doit être désactivée. L’éclairage lightmap peut être composé en activant des informations directionnelles. Quand elle est désactivée, l’éclairage de lightmaps est plat, mais moins cher.

![Paramètres du matériel mobile en non réel](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Ajustement de l’ombrage vers l’avant

Ces options améliorent la fidélité visuelle au détriment des performances. Ils doivent être désactivés pour des performances maximales.

![Transférer les paramètres de matériel d’ombrage dans un environnement inréel](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Définition de la translucidité matérielle

Indique que la matière translucide ne doit pas être affectée par la floraison ou le DDL. Étant donné que ces deux effets sont rares dans MR, ce paramètre doit être activé par défaut.

![Paramètre translucidité distinct mobile dans inréel](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Paramètres facultatifs

Les paramètres suivants peuvent améliorer les performances, mais notez qu’ils désactivent certaines fonctionnalités. Utilisez ces paramètres uniquement si vous êtes sûr que vous n’avez pas besoin des fonctionnalités en question.

![Paramètres de matériau facultatifs dans inréel](images/unreal-materials-img-06.jpg)

Si votre matériel ne nécessite pas de réflexions ou d’éclats, la définition de cette option peut améliorer considérablement les performances. Dans les tests internes, il est aussi rapide que « non éclairé » tout en fournissant des informations d’éclairage.

## <a name="best-practices"></a>Meilleures pratiques

Les éléments suivants ne sont pas des « paramètres » dans la mesure où ils sont les meilleures pratiques liées aux documents.

Lorsque vous créez des paramètres, préférez utiliser des « paramètres statiques » dans la mesure du possible. Les commutateurs statiques peuvent être utilisés pour supprimer toute une branche d’un matériau sans coût d’exécution. Les instances peuvent avoir des valeurs différentes, ce qui rend possible la configuration d’un nuanceur basé sur un modèle sans perte de performances. L’inconvénient, c’est que plusieurs permutations sont créées, ce qui entraîne la recompilation du nuanceur. Essayez de réduire le nombre de paramètres statiques dans le matériel et le nombre de permutations des paramètres statiques utilisés. Vous trouverez plus d’informations sur le rendu des paramètres de matériau dans la [documentation du moteur inréel](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).

![Meilleures pratiques pour les paramètres de matériau](images/unreal-materials-img-07.jpg)

Lors de la création d’instances de matériau, la préférence doit être accordée à une **constante d’instance matérielle** sur une instance de matériau dynamique. La **constante d’instance Material** est un matériau instancié qui calcule une seule fois avant l’exécution.

L’instance de matériau créée via le navigateur de contenu (**cliquez avec le bouton droit > créer une instance de matériau**) est une constante d’instance de matériau. L’instance de matériau Dynamic est créée à l’aide de code. Vous trouverez plus d’informations sur les instances de matériel dans la [documentation du moteur inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).

![Création d’instances de matériau dans des conditions inréelles](images/unreal-materials-img-08.png)

Gardez un œil sur la complexité de vos matériaux/nuanceurs. Vous pouvez afficher le coût de votre matériel sur différentes plateformes en cliquant sur l’icône statistiques de plateforme. Vous pouvez également obtenir plus d’informations sur les documents dans la [documentation du moteur inréaliste](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Création de paramètres dynamiques d’instance de matériau dans des conditions non réelles](images/unreal-materials-img-09.png)

Vous pouvez obtenir une idée rapide de la complexité relative de votre nuanceur via le [mode d’affichage](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)de la complexité du nuanceur.

* Raccourci clavier du mode d’affichage : Alt + 8
* Commande de console : ViewMode shadercomplexity

![Complexité de la matière dans le temps](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Voir aussi
* [Matériel mobile](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Modes d’affichage](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Instances de matériau](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
