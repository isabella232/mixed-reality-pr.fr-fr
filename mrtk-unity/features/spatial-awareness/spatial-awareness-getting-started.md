---
title: Bien démarrer avec la reconnaissance spatiale
description: décrit la sensibilisation spatiale dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: bbe5b923ea7da965424e7fac98adca180c6f91d0c9b4c4ca7a0477e301c362f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204326"
---
# <a name="spatial-awareness-getting-started"></a>Bien démarrer avec la reconnaissance spatiale

![Reconnaissance spatiale](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

Le système de sensibilisation spatiale offre une reconnaissance environnementale réaliste dans les applications de réalité mixte. lorsqu’elle est introduite sur Microsoft HoloLens, la sensibilisation spatiale a fourni un ensemble de mailles représentant la géométrie de l’environnement, qui permettait des interactions attrayantes entre les hologrammes et le monde réel.

> [!NOTE]
> à ce stade, la Shared Computer Toolkit de la réalité mixte n’est pas fournie avec des algorithmes de compréhension spatiale tels qu’ils ont été empaquetés à l’origine dans le HoloToolkit. La compréhension spatiale implique généralement la transformation des données de maillage spatial pour créer des données de maillage simples et/ou groupées, telles que des plans, des murs, des planchers, des plafonds, etc.

## <a name="getting-started"></a>Prise en main

l’ajout de la prise en charge de la sensibilisation spatiale requiert deux composants clés de la réalité mixte Shared Computer Toolkit : le système de sensibilisation spatiale et un fournisseur de plateforme pris en charge.

1. [Activer](#enable-the-spatial-awareness-system) le système de sensibilisation spatiale
2. [Inscrire](#register-observers) et [configurer](configuring-spatial-awareness-mesh-observer.md) un ou plusieurs observateurs spatiaux pour fournir des données de maillage
3. [Créez et déployez](#build-and-deploy) sur une plateforme qui prend en charge la sensibilisation spatiale

### <a name="enable-the-spatial-awareness-system"></a>Activer le système de sensibilisation spatiale

Le système de sensibilisation spatiale est géré par l’objet MixedRealityToolkit (ou un autre composant d' [inscription de service](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ). Suivez les étapes ci-dessous pour activer ou désactiver le *système de sensibilisation spatiale* dans le profil *MixedRealityToolkit* .

la réalité mixte Shared Computer Toolkit est fournie avec quelques profils préconfigurés par défaut. Dans certains cas, le système de sensibilisation spatiale est activé ou désactivé par défaut. L’objectif de cette préconfiguration, en particulier lorsqu’elle est désactivée, est d’éviter la surcharge visuelle du calcul et du rendu des mailles.

| Profil | Système activé par défaut |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel/profils/HoloLens1) | False |
| `DefaultHoloLens2ConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel/profils/HoloLens2) | False |
| `DefaultMixedRealityToolkitConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel/profils) | True |

1. Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie des scènes pour l’ouvrir dans le panneau Inspecteur.

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Accédez à la section *système de sensibilisation spatiale* et cochez *activer le système de sensibilisation spatiale* .

    ![Activer la sensibilisation spatiale](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Sélectionnez le type d’implémentation du système de sensibilisation spatiale souhaité. [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)Est la valeur par défaut fournie.

    ![Sélectionner l’implémentation du système de sensibilisation spatiale](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Inscrire des observateurs

les services de la réalité mixte Shared Computer Toolkit peuvent avoir des [services Fournisseur de données](../../architecture/systems-extensions-providers.md) qui complètent le service principal avec des données et des contrôles d’implémentation spécifiques à la plateforme. Par exemple, le système d’entrée de réalité mixte qui dispose de [plusieurs fournisseurs de données](../input/input-providers.md) pour accéder au contrôleur et à d’autres informations d’entrée connexes à partir de différentes API spécifiques à la plateforme.

Le système de sensibilisation spatiale est similaire dans le fait que les fournisseurs de données fournissent au système des données de maillage relatives au monde réel. Au moins un observateur spatial doit être inscrit dans le profil de sensibilisation spatiale. Les observateurs spatiaux sont généralement des composants spécifiques à la plateforme qui jouent le rôle de fournisseur pour le revêtement de différents types de données de maillage à partir d’un point de terminaison spécifique à une plateforme (par exemple, HoloLens).

1. Ouvrir ou développer le *profil système de sensibilisation spatiale*

    ![Profil système de sensibilisation spatiale](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Cliquez sur le bouton *« Ajouter un observateur spatial »*
1. Sélectionner le *type d’implémentation d’observateur spatial* souhaité

    ![Sélectionner l’implémentation de l’observateur spatial](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Modifiez les propriétés de configuration de l’observateur](configuring-spatial-awareness-mesh-observer.md) si nécessaire.

> [!NOTE]
> les utilisateurs du `DefaultMixedRealityToolkitConfigurationProfile` (ressources/MRTK/kit de développement logiciel (SDK)/profils) auront le système de sensibilisation spatiale préconfiguré pour la plateforme Windows Mixed Reality qui utilise la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe.

### <a name="build-and-deploy"></a>Générer et déployer

Une fois que le système de sensibilisation spatiale est configuré avec le (s) observateur (s) souhaité (s), le projet peut être généré et déployé sur la plateforme cible.

> [!IMPORTANT]
> si vous ciblez la plateforme Windows Mixed Reality (par exemple, HoloLens), il est important de veiller à ce que la [fonction de Perception spatiale](/windows/mixed-reality/spatial-mapping-in-unity) soit activée afin d’utiliser le système de sensibilisation spatiale sur l’appareil.

> [!WARNING]
> certaines plateformes, y compris les Microsoft HoloLens, prennent en charge l’exécution à distance à partir d’unity. Cette fonctionnalité permet un développement et des tests rapides sans nécessiter l’étape de création et de déploiement. Veillez à effectuer des tests d’acceptation finaux à l’aide d’une version générée et déployée de l’application, qui s’exécute sur le matériel et la plateforme cibles.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez effectué les procédures ci-dessus pour activer le système de sensibilisation spatiale, le système peut être configuré et contrôlé de manière plus détaillée.

Informations pour la configuration des observateurs dans Inspector :

- [Configuration des observateurs pour l’utilisation de l’appareil](configuring-spatial-awareness-mesh-observer.md)
- [Configuration des observateurs pour l’utilisation dans l’éditeur](spatial-object-mesh-observer.md)

Informations pour le contrôle et l’extension des observateurs par le biais du code :

- [Configuration des observateurs par le biais de code](usage-guide.md)
- [Création d’un observateur personnalisé](create-data-provider.md)

## <a name="see-also"></a>Voir aussi

- [Documentation sur l’API de sensibilisation spatiale](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Vue d’ensemble du mappage spatial WMR](/windows/mixed-reality/spatial-mapping)
- [Mappage spatial dans Unity WMR](/windows/mixed-reality/spatial-mapping-in-unity)
