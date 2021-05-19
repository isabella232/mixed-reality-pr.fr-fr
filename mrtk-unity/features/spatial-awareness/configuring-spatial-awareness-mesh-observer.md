---
title: Configuration de l’observateur de maillage de reconnaissance spatiale
description: Comment configurer l’observateur de maillage spatial prêt à l’emploi dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144959"
---
# <a name="configuring-mesh-observers-for-device"></a>Configuration des observateurs de maillage pour l’appareil

Ce guide vous aidera à configurer l’observateur de maillage spatial prêt à l’emploi dans MRTK, qui prend en charge la plateforme Windows Mixed Reality (c.-à-d. HoloLens). L’implémentation par défaut fournie par le kit d’outils de réalité mixte est la classe [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) . La plupart des propriétés de cet article s’appliquent à d’autres [implémentations d’observateurs personnalisées](create-data-provider.md).

## <a name="profile-settings"></a>Paramètres du profil

Les deux éléments suivants doivent être définis en premier lors de la configuration d’un profil d’observateur de maillage spatial pour le [système de sensibilisation spatiale](spatial-awareness-getting-started.md).

1. Implémentation concrète du type observer
1. Liste des plateformes prises en charge pour l’exécution de cet observateur

> [!NOTE]
> Tous les observateurs doivent étendre l’interface [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) .

![Types de plateforme des paramètres généraux de l’observateur de maillage](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Paramètres généraux :

![Paramètres généraux de l’observateur de maille-paramètres documents](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportement de démarrage**

Le comportement de démarrage spécifie si l’observateur doit commencer à s’exécuter lors de sa première instanciation. Les deux options sont les suivantes :

* *Démarrage automatique* -la valeur par défaut à laquelle l’observateur doit commencer l’opération après l’initialisation
* *Démarrage manuel* -l’observateur attend d’être redirigé vers le démarrage

Si vous utilisez le *démarrage manuel*, l’un d’eux doit [reprendre et le suspendre au moment de l’exécution par le biais du code](usage-guide.md#starting-and-stopping-mesh-observation).

**Intervalle de mise à jour**

Durée, en secondes, entre les demandes à la plateforme pour mettre à jour les données de maillage spatiale. Les valeurs standard sont comprises dans la plage de 0,1 et 5,0 secondes.

**Est un observateur stationnaire**

Indique si l’observateur doit rester stationnaire ou s’il doit être déplacé et mis à jour avec l’utilisateur. Si la valeur est true, la *forme observateur* avec le volume défini par les *étendues d’observation* reste à l’origine au démarrage. Si la valeur est false, l’espace de l’observateur suivra la tête de l’utilisateur en tant qu’origine de la forme.

Aucune donnée de maillage n’est calculée pour toute zone physique en dehors de l’espace de l’observateur, comme défini par les propriétés suivantes : *est un observateur stationnaire*, * forme observateur * * et les *extensions d’observation*.

**Forme observateur**

La forme observateur définit le type de volume que l’observateur de maille utilisera lors de l’observation de maillages. Les options prises en charge sont les suivantes :

* *Cube aligné* sur l’axe-forme rectangulaire qui reste alignée sur les axes du système de coordonnées universelles, tel que déterminé au démarrage de l’application.
* *Cube aligné* par l’utilisateur-forme rectangulaire qui pivote pour s’aligner avec le système de coordonnées local des utilisateurs.
* *Sphere* : un volume sphérique avec un centre à l’origine de l’espace universel. La valeur X de la propriété d' *étendues d’observation* sera utilisée comme rayon de la sphère.

**Étendues d’observation**

Les extensions d’observation définissent la distance à partir du point d’observation que les mailles seront observées.

### <a name="physics-settings"></a>Paramètres physiques

![Paramètres physiques de l’observateur de maillage](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Couche physique**

Couche physique sur laquelle les objets de maillage spatial seront placés pour interagir avec les systèmes physique et RayCast Unity.

> [!NOTE]
> La boîte à outils de réalité mixte réserve la *couche 31* par défaut pour une utilisation par les observateurs de sensibilisation spatiale.

**Recalculer les normales**

Spécifie si l’observateur de maillage recalcule les normales de la maille qui suit l’observation. Ce paramètre est disponible pour garantir que les applications reçoivent des maillages qui contiennent des données normales valides sur les plateformes qui ne les retournent pas avec des mailles.

### <a name="level-of-detail-settings"></a>Niveau de paramètres de détail

![Niveau d’observateur de maillage des paramètres de détail](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Niveau de détail**

Spécifie le niveau de détail (LOD) des données de maillage spatiale. Les valeurs actuellement définies sont grossistes, fine et Custom.

* *Grossière* -place un impact plus faible sur les performances de l’application et constitue un excellent choix pour la recherche de plans/de navigation.

* Les paramètres à *moyennement* équilibrés sont souvent utiles pour les expériences qui analysent continuellement l’environnement à la fois pour les grandes fonctionnalités, les étages et les murs, ainsi que pour les détails d’occlusion.

* *En règle* générale, l’impact sur les performances de l’application est plus important et constitue une option intéressante pour les mailles d’occlusion.

* *Personnalisé* : nécessite que l’application spécifie la propriété de *compteur triangle/cubique* et permet aux applications de régler la précision par rapport à l’impact sur les performances de l’observateur de maillage spatial.

> [!NOTE]
> Il n’est pas garanti que tous les *triangles/valeurs des compteurs cubes* soient honorés par toutes les plateformes. L’expérimentation et le profilage sont fortement recommandés lors de l’utilisation d’un LOD personnalisé.

**Triangles par mètre cube**

Valide lors de l’utilisation du paramètre *personnalisé* pour la propriété **niveau de détail** et spécifie la densité du triangle pour le maillage spatial.

### <a name="display-settings"></a>Paramètres d'affichage

![Paramètres d’affichage de l’observateur de maillage](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Option d’affichage**

Spécifie le mode d’affichage des maillages spatiaux par l’observateur. Les valeurs prises en charge sont les suivantes :

* *None* -l’observateur ne rend pas le maillage
* *Visible* : les données du maillage sont visibles à l’aide du *matériau visible*
* *Occlusion* : les données de maillage seront des éléments de occultait dans la scène à l’aide du *matériau d’occlusion*

![Sélectionner l’implémentation du système de sensibilisation spatiale](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Les observateurs spatiaux peuvent être [repris/suspendus au moment de l’exécution via du code.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> Si vous affectez la valeur *None* à l' *option Display* , l’exécution de l’observateur n’est **pas** interrompue. Si vous souhaitez arrêter tous les observateurs, les applications doivent suspendre tous les observateurs via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Matériau visible**

Indique la matière à utiliser lors de la visualisation du maillage spatial.

**Matériau d’occlusion**

Indique la matière à utiliser pour faire en sorte que le maillage spatial occultait les hologrammes.

## <a name="see-also"></a>Voir aussi

* [Système de sensibilisation spatiale](spatial-awareness-getting-started.md)
* [Configuration du système de sensibilisation spatiale par le biais du code](usage-guide.md)
* [Documentation de l’API IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Documentation de l’API IMixedRealitySpatialAwarenessMeshObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Documentation de l’API BaseSpatialObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
