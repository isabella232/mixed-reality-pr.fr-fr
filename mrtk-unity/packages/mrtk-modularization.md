---
title: Modularisation MRTK
description: Décrit la Componentisation dans MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: eac96e309afc21f9a2b6efe9c3aef5975e4f0dff
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177009"
---
# <a name="mrtk-modularization"></a>Modularisation MRTK

l’une des nombreuses nouvelles fonctionnalités de la réalité mixte Shared Computer Toolkit v2 est l’amélioration de la création de composants. Chaque fois que cela est possible, les composants individuels sont isolés de la couche principale de la Fondation.

## <a name="minimized-dependencies"></a>Dépendances réduites

MRTK V2 a été intentionnellement développé pour être modulaire et pour réduire les dépendances entre les services système (par ex., la sensibilisation spatiale).

En raison de la nature de certains services système (par ex., les entrées et les téléportions), il existe un petit nombre de dépendances.

S’il est prévu que les services requièrent un ou plusieurs composants de fournisseur de données, il n’existe aucun lien direct entre eux. Il en va de même pour les fonctionnalités du kit de développement logiciel (par exemple, les composants de l’interface utilisateur).

## <a name="component-communication"></a>Communication des composants

Pour s’assurer qu’il n’existe aucun lien direct entre les composants, MRTK v2 utilise des interfaces pour la communication entre les services, les fournisseurs de données et le code d’application. ces interfaces sont définies dans et toutes les communications sont routées via la réalité mixte Shared Computer Toolkit composant principal.

![Utilisation du système de sensibilisation spatiale via des interfaces](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Minimisation de l’encombrement de l’importation MRTK

À ce stade, le MRTK est importé en tant que package de base unique (en ignorant pour un moment l’existence du package d’exemples, qui est un package entièrement facultatif). Il est possible de réduire l’encombrement en réduisant manuellement les fichiers importés, bien qu’il s’agisse d’un processus très manuel qui ne dispose pas d’un guide bien défini.

Il est possible de désactiver les éléments arbitraires pendant l’importation du package de Fondation. Toutefois, il n’est pas recommandé de le faire à une étape précoce du développement, car cela peut perturber les fonctionnalités. Après avoir déterminé le dernier ensemble de fonctionnalités d’une application, le nettoyage des fournisseurs et des services inutiles peut être effectué sur les dossiers suivants :

- MRTK/services
- MRTK/fournisseurs
- MRTK/Kit de développement logiciel (SDK)/fonctionnalités

> [!NOTE]
> MRTK v2. x **_requiert_** le contenu du dossier Assets/MRTK/Core.

## <a name="upcoming-features"></a>Fonctionnalités à venir

### <a name="application-architecture"></a>Architecture de l’application

Le MRTK prend en charge l’activation des applications à l’aide d’une variété d’architectures, notamment :

- [Localisateur de service MixedRealityToolkit](#mixedrealitytoolkit-service-locator)
- [Services individuels](#individual-service-components)
- [Localisateur de service personnalisé](#custom-service-locator)
- [Architecture hybride](#hybrid-architecture)

Lors de la sélection d’une architecture d’application, il est important de prendre en compte la flexibilité de conception et les performances des applications. Les architectures décrites ici ne sont pas censées être adaptées à chaque application.

#### <a name="mixedrealitytoolkit-service-locator"></a>Localisateur de service MixedRealityToolkit

Le MRTK permet (et configure automatiquement) des scènes d’application pour utiliser le [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) composant localisateur de service par défaut. Ce composant prend en charge la configuration des systèmes MRTK et des fournisseurs de données par le biais des inspecteurs de configuration et gère les durées de vie des composants et les comportements de base (par exemple, quand mettre à jour).

Tous les systèmes sont représentés dans l’inspecteur de configuration principal, qu’ils soient présents ou activés dans le projet. Pour plus d’informations, consultez le Guide de configuration de la [réalité mixte](../configuration/mixed-reality-configuration-guide.md) .

#### <a name="individual-service-components"></a>Composants de service individuels

Certains développeurs ont exprimé un souhait d’inclure des composants de service individuels dans la hiérarchie des scènes de l’application. Pour activer cette utilisation, les services doivent être encapsulés dans un bureau d’enregistrement personnalisé ou être auto-inscrits/auto-géré.

Un service à inscription automatique implémenterait [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) et s’inscrit lui-même afin que le code de l’application puisse découvrir l’instance de service par le biais d’un registre.

Un service de gestion automatique peut être implémenté en tant qu’objet singleton dans la hiérarchie de la scène. Cet objet fournit une propriété d’instance que le code de l’application pourrait utiliser pour accéder directement aux fonctionnalités du service.

#### <a name="custom-service-locator"></a>Localisateur de service personnalisé

Certains développeurs ont demandé la possibilité de créer un composant de localisateur de service personnalisé. Les localisateurs de service personnalisés implémentent l' [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface et gèrent les comportements de cycle de vie et de base des services actifs.

#### <a name="hybrid-architecture"></a>Architecture hybride

Le MRTK prend en charge une architecture hybride dans laquelle les développeurs peuvent combiner les approches précédentes si nécessaire ou souhaité. Par exemple, un développeur peut commencer par le [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localisateur de service et ajouter un service à inscription automatique.

> [!NOTE]
> Lorsque vous optez pour une architecture hybride, il est important d’être attentif à toute duplication de travail (par exemple, acquisition de données de contrôleur à partir de plusieurs composants).
