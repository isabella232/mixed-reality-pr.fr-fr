---
title: Observateur de maillage des objets dans l’espace
description: Documentation sur l’observateur de maillage spatial dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144449"
---
# <a name="configuring-mesh-observers-for-the-editor"></a>Configuration des observateurs de maillage pour l’éditeur

Un moyen pratique de fournir des données de maillage d’environnement dans l’éditeur Unity consiste à utiliser la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe. L' *Observateur d’objets spatiaux* est un fournisseur de données d’éditeur uniquement pour le [système de sensibilisation spatiale](spatial-awareness-getting-started.md) qui permet d’importer des données de modèle 3D pour représenter un maillage spatial. Une utilisation courante de l' *Observateur de maillage d’objets spatiaux* consiste à importer des données analysées par le biais d’un Microsoft HoloLens pour tester la façon dont une expérience s’adapte aux différents environnements à partir d’Unity.

## <a name="getting-started"></a>Prise en main

Ce guide vous aidera à configurer un *Observateur de maillage d’objets spatiaux*. Il existe trois étapes clés pour activer cette fonctionnalité.

1. Ajouter un *Observateur de maillage d’objets spatiaux* au profil de système de sensibilisation spatiale
1. Définir l’objet de données de maillage de l’environnement
1. [Configurer le reste des propriétés de profil de l’observateur de maillage](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>Configurer un profil d' *Observateur d’objets spatiaux*

1. Sélectionnez le profil de configuration de la *réalité mixte* souhaitée ou sélectionnez l’objet de la *boîte à outils de réalité mixte* dans Scene
1. Ouvrir ou développer l’onglet *système de sensibilisation spatiale*
1. Cliquez sur le bouton *« Ajouter un observateur spatial »*

    ![Ajouter un observateur spatial](../images/spatial-awareness/AddObserver.png)

1. Sélectionner le type de *SpatialObjectMeshObserver*

    ![Sélectionner l’observateur de maillage d’objet spatial](../images/spatial-awareness/SelectObjectObserver.png)

1. Sélectionnez l' *objet de maillage spatial* souhaité. Par défaut, l’observateur est configuré avec un exemple de modèle. Ce modèle a été créé à l’aide d’un Microsoft HoloLens, mais il est possible de [créer un nouvel objet de maillage d’analyse](#acquiring-environment-scans).
1. [Configurer le reste des propriétés de profil de l’observateur de maillage](configuring-spatial-awareness-mesh-observer.md)

    ![Sélectionner l’objet de maillage](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Notes de profil de l’observateur d’objets spatiaux

Étant donné que l' *Observateur d’objets spatiaux* charge des données à partir d’un modèle 3D, il n’honore pas certains des paramètres d’observateur de maillage standard qui sont présentés ci-dessous.

**Intervalle de mise à jour**

L'  *Observateur d’objets spatiaux* envoie tous les maillages à une application lorsque le modèle est chargé. Il ne simule pas les deltas horaires entre les mises à jour. Une application peut recevoir à nouveau les événements de maillage en appelant [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) et [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .

**Est un observateur stationnaire**

L' *Observateur de maillage d’objets spatiaux* considère que tous les objets de maillage 3D sont stationnaires et ignore l’origine.

**Forme et étendues de l’observateur**

L'  *Observateur d’objets spatiaux* envoie l’intégralité du maillage 3D à l’application. La forme et les étendues de l’observateur ne sont pas prises en compte.

**Niveau de détail et triangles/compteur cubique**

L’observateur ne tente pas de trouver des LODs de modèle 3D lors de l’envoi des maillages à l’application.

## <a name="acquiring-environment-scans"></a>Acquisition d’analyses d’environnement

Cette section décrit des informations supplémentaires pour créer et rassembler des fichiers *objets de maillage spatial* à utiliser avec l' *Observateur de maillage d’objets spatiaux*.

### <a name="windows-device-portal"></a>Portail d’appareil Windows

Le [portail de périphériques Windows](/windows/mixed-reality/using-the-windows-device-portal) peut être utilisé pour télécharger le maillage spatial, sous forme de fichier. obj, à partir d’un appareil Microsoft HoloLens.

1. Analyse en parcourant et en affichant simplement l’environnement souhaité à l’aide d’un HoloLens
1. Se connecter au HoloLens à l’aide du portail de périphériques Windows
1. Accéder à la page de la *vue 3D*
1. Cliquez sur le bouton *mettre à jour* sous la section *mappage spatial* .
1. Cliquez sur le bouton *Enregistrer* sous la section *mappage spatial* pour enregistrer le fichier OBJ sur le PC.

> [!NOTE]
> **Fichiers HoloToolkit. Room**
>
> De nombreux développeurs auront précédemment utilisé HoloToolkit pour analyser les environnements et créer des fichiers. Room. La boîte à outils de réalité mixte prend désormais en charge l’importation de ces fichiers en tant que GameObjects dans Unity et les utilise en tant qu' *objets de maillage spatial* dans l’observateur.

## <a name="see-also"></a>Voir aussi

- [Profils](../profiles/profiles.md)
- [Guide de configuration du profil du Toolkit de réalité mixte](../../configuration/mixed-reality-configuration-guide.md)
- [Prise en main de la sensibilisation spatiale](spatial-awareness-getting-started.md)
- [Configuration des observateurs de maillage sur l’appareil](configuring-spatial-awareness-mesh-observer.md)
- [Configuration des observateurs de maillage par le biais de code](usage-guide.md)
- [Utilisation du portail d’appareil Windows](/windows/mixed-reality/using-the-windows-device-portal)