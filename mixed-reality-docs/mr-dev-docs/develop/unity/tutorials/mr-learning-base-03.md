---
title: Tutoriels de démarrage - 3. Configuration des profils MRTK
description: Ce cours vous montre comment configurer les profils Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, reconnaissance spatiale
ms.localizationpriority: high
ms.openlocfilehash: 0a8beb647516ebcb5bc07cb58d0193e8fe71e9fc
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101760015"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Configuration des profils MRTK

## <a name="overview"></a>Vue d’ensemble

Dans ce tutoriel, vous allez voir comment personnaliser et configurer les profils MRTK.

Les <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">profils MRTK</a> sont une arborescence de profils imbriqués qui constituent les informations de configuration déterminant comment les systèmes et les fonctionnalités de MRTK doivent être initialisés. Le profil de plus haut niveau, le profil de configuration, contient des profils imbriqués pour chacun des systèmes principaux. Chaque profil imbriqué est conçu pour configurer le comportement de son système correspondant.

Cet exemple va vous montrer comment masquer le maillage de la reconnaissance spatiale en modifiant les paramètres de l’observateur de maillage spatial. Vous pouvez cependant suivre ces mêmes principes pour personnaliser des paramètres ou des valeurs dans les profils MRTK.

Comme vous en avez fait l’expérience quand vous avez déployé votre projet sur votre HoloLens 2 dans le [tutoriel précédent](mr-learning-base-02.md#congratulations), le maillage de <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">reconnaissance spatiale</a> est un ensemble de mailles représentant la géométrie de l’environnement. C’est une visualisation utile à voir initialement, mais elle est généralement désactivée pour éviter de distraire visuellement l’utilisateur et d’impacter les performances en raison des ressources nécessaires à son affichage.

## <a name="objectives"></a>Objectifs

* Apprendre à personnaliser et à configurer des profils MRTK
* Apprendre à masquer le maillage de reconnaissance spatiale

## <a name="changing-the-spatial-awareness-display-option"></a>Changement de l’option d’affichage de la reconnaissance spatiale

Les principales étapes à suivre pour masquer le maillage de la reconnaissance spatiale sont les suivantes :

1. Cloner le profil de configuration par défaut
2. Activer le système de reconnaissance spatiale
3. Cloner le profil système de reconnaissance spatiale par défaut
4. Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut
5. Changer la visibilité du maillage de reconnaissance spatiale

> [!NOTE]
> Par défaut, les profils MRTK ne sont pas modifiables. Il s’agit des modèles de profil par défaut que vous devez cloner avant de pouvoir les modifier. Il existe plusieurs couches de profils imbriquées. Par conséquent, il est courant de cloner et de modifier plusieurs profils lors de la configuration d’un ou plusieurs paramètres.

### <a name="1-clone-the-default-configuration-profile"></a>1. Cloner le profil de configuration par défaut

> [!NOTE]
> Le profil de configuration est le profil de plus haut niveau. Par conséquent, pour pouvoir modifier d’autres profils, vous devez d’abord cloner le profil de configuration.

Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**, puis, dans la fenêtre Inspector, remplacez le profil de configuration **MixedRealityToolkit** par **DefaultHoloLens2ConfigurationProfile** :

![Composant MixedRealityToolkit d’Unity avec DefaultHoloLens2ConfigurationProfile sélectionné](images/mr-learning-base/base-03-section1-step1-1.png)

Avec l’objet **MixedRealityToolkit** sélectionné, dans la fenêtre Inspector, cliquez sur le bouton **Copy & Customize** pour ouvrir la fenêtre Clone Profile :

![Composant MixedRealityToolkit d’Unity - Bouton Copy & Customize](images/mr-learning-base/base-03-section1-step1-2.png)

Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_HoloLens2ConfigurationProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultHololens2ConfigurationProfile** :

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil de configuration](images/mr-learning-base/base-03-section1-step1-3.png)

Le profil de configuration que vous venez de créer est maintenant affecté comme profil de configuration pour votre scène :

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé HoloLens2ConfigurationProfile appliqué](images/mr-learning-base/base-03-section1-step1-4.png)

Dans le menu Unity, sélectionnez **File** > **Save** pour enregistrer votre scène.

> [!TIP]
> N’oubliez pas d’enregistrer votre travail tout au long des tutoriels.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Activer le système de reconnaissance spatiale

Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet **Spatial Awareness**, puis cochez la case **Enable Spatial Awareness System** :

![Composant MixedRealityToolkit d’Unity avec le système de reconnaissance spatiale activé](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Pour les projets à venir, si votre application n’a pas besoin de répondre à l’environnement ou d’interagir avec celui-ci, il est recommandé de désactiver la reconnaissance spatiale de façon à réduire le coût des performances.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Cloner le profil système de reconnaissance spatiale par défaut

Sous l’onglet **Spatial Awareness**, cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :

![Composant Unity MixedRealityToolkit d’Unity avec l’onglet Spatial Awareness sélectionné](images/mr-learning-base/base-03-section1-step3-1.png)

Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessSystemProfile** :

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil du système de reconnaissance spatiale](images/mr-learning-base/base-03-section1-step3-2.png)

Le profil Spatial Awareness System nouvellement créé est maintenant automatiquement affecté à votre profil de configuration :

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessSystemProfile appliqué](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut

Avec l’onglet **Spatial Awareness** sélectionné, développez la section **Windows Mixed Reality Spatial Mesh Observer**, puis cliquez sur le bouton **Clone** pour ouvrir la fenêtre Clone Profile :

![Composant MixedRealityToolkit d’Unity avec la section Windows Mixed Reality Spatial Mesh Observer développée](images/mr-learning-base/base-03-section1-step4-1.png)

Dans la fenêtre Clone Profile, en regard de **Profile Name**, entrez un nom de profil adapté comme _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, puis cliquez sur le bouton **Clone** pour créer une copie modifiable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** :

![MixedRealityToolkit d’Unity - Fenêtre contextuelle de clonage du profil Spatial Mesh Observer](images/mr-learning-base/base-03-section1-step4-2.png)

Le profil Spatial Awareness Mesh Observer nouvellement créé est maintenant automatiquement affecté à votre profil Spatial Awareness System :

![Composant MixedRealityToolkit d’Unity avec le profil personnalisé nouvellement créé MixedRealitySpatialAwarenessMeshObserverProfile appliqué](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Changer la visibilité du maillage de reconnaissance spatiale

Dans **Spatial Mesh Observer Settings**, configurez **Display Option** sur **Occlusion** pour rendre le maillage de mappage spatial invisible tout en le gardant fonctionnel :

![Composant MixedRealityToolkit d’Unity avec l’option d’affichage de Spatial Mesh Observer définie sur Occlusion](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Bien que le maillage de mappage spatial ne soit pas visible, il est toujours présent et fonctionnel. Par exemple, les hologrammes qui sont derrière le maillage de mappage spatial, comme un hologramme derrière un mur physique, ne sont pas visibles.

Vous venez de découvrir comment modifier un paramètre dans le profil MRTK. Comme vous pouvez le voir, pour personnaliser les paramètres du MRTK, vous devez d’abord créer une copie des profils par défaut. Étant donné que les profils par défaut ne sont pas modifiables, vous les aurez toujours comme référence si vous voulez rétablir les paramètres par défaut. Pour plus d’informations sur les profils MRTK et leur architecture, vous pouvez consulter le [Guide de configuration du profil MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) dans le [portail de la documentation MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez vu comment cloner, personnaliser et configurer les profils et les paramètres MRTK.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 4. Positionnement des objets dans la scène](mr-learning-base-04.md)
