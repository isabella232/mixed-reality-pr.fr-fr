---
title: Compréhension des scènes
description: décrit la compréhension des scènes dans MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, compréhension des scènes
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143879"
---
# <a name="scene-understanding"></a>Compréhension des scènes

La compréhension de la [scène](/windows/mixed-reality/scene-understanding) retourne une représentation sémantique des entités de scène ainsi que leurs formes géométriques sur __hololens 2__ (la 1re génération de hololens n’est pas prise en charge).

Voici quelques cas d’utilisation attendus de cette technologie :
* Placer des objets sur la surface la plus proche d’un certain type (par exemple, un mur et un plancher)
* Construire NAV-maille pour les jeux de style plateforme
* Fournir une géométrie conviviale du moteur physique sous forme de quatre cœurs
* Accélérez le développement en évitant d’avoir à écrire des algorithmes similaires

La compréhension des scènes est disponible sous la forme d’une fonctionnalité __expérimentale__ démarrant à partir de MRTK 2,6. Il est intégré à MRTK en tant qu' [Observateur spatial](spatial-awareness-getting-started.md#register-observers) appelé [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . La compréhension des scènes fonctionne avec le pipeline XR hérité et le pipeline du kit de développement logiciel (SDK) XR. Dans les deux cas, `WindowsSceneUnderstandingObserver` est utilisé.

## <a name="observer-overview"></a>Vue d’ensemble de l’observateur

Lorsque vous y êtes invité, le [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) retournera [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) avec des attributs utiles pour que l’application comprenne son environnement. La fréquence d’observation, le type d’objet retourné (par exemple, Wall, Floor) et d’autres comportements observateur dépendent de la configuration de l’observateur via le profil. Par exemple, si le masque d’occlusion est souhaité, l’observateur doit être configuré pour générer des Quad. La scène observée peut être enregistrée en tant que fichier sérialisé pouvant être chargée ultérieurement pour recréer la scène en mode de lecture de l’éditeur.

## <a name="setup"></a>Programme d’installation

> [!IMPORTANT]
> La compréhension de la scène est uniquement prise en charge sur HoloLens 2 et Unity 2019,4 et versions ultérieures.

1. Vérifiez que la plateforme est définie sur UWP dans les paramètres de génération.
1. Procurez-vous le package de compréhension de scène via l’outil de la [fonctionnalité de réalité mixte](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Utilisation de la compréhension des scènes

La façon la plus rapide de prendre en main la compréhension des scènes consiste à consulter l’exemple de scène.

### <a name="scene-understanding-sample-scene"></a>Exemple de scène de vision

Dans Unity, utilisez l’Explorateur de projets pour ouvrir le fichier de scène dans `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` et appuyez sur Play !

> [!IMPORTANT]
> Lors de l’utilisation de l’outil de fonctionnalité de réalité mixte ou de l’importation via UPM, importez l’exemple de démonstrations-SpatialAwareness avant d’importer l’exemple expérimental-SceneUnderstanding en raison d’un problème de dépendance. Pour plus d’informations, consultez [ce problème GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) .

La scène illustre les éléments suivants :

* Visualisation des objets de scène observés avec l’interface utilisateur de l’application pour la configuration de l’observateur
* Exemple de `DemoSceneUnderstandingController` script qui montre comment modifier les paramètres observateur et écouter les événements pertinents
* Enregistrement des données de scène sur un appareil pour un développement hors connexion
* Chargement des données de scène précédemment enregistrées (fichiers. bytes) pour prendre en charge le flux de travail de développement dans l’éditeur

> [!NOTE] 
> L’exemple de scène est basé sur le pipeline XR hérité. Si vous utilisez le pipeline du kit de développement logiciel (SDK) XR, vous devez modifier les profils en conséquence. Le profil de système de sensibilisation spatiale fourni ( `DemoSceneUnderstandingSystemProfile` ) et la scène comprenant les profils d’observateur ( `DefaultSceneUnderstandingObserverProfile` et `DemoSceneUnderstandingObserverProfile` ) fonctionnent pour les deux pipelines.

#### <a name="configuring-the-observer-service"></a>Configuration du service Observateur

Sélectionnez l’objet de jeu « MixedRealityToolkit » et vérifiez l’inspecteur.

![emplacement de compréhension de la scène dans la hiérarchie](../images/spatial-awareness/MRTKHierarchy.png)

![Emplacement MRTK dans Inspector](../images/spatial-awareness/MRTKLocation.png)

Ces options permettent de configurer le `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Exemple de script

L’exemple de script _DemoSceneUnderstandingController. cs_ illustre les principaux concepts de l’utilisation du service de vision de scène.

* Abonnement à des événements de compréhension de scène
* Gestion des événements de compréhension de scène
* Configuration de `WindowsSceneUnderstandingObserver` au moment de l’exécution

Les basculements sur le panneau de la scène modifient le comportement de Scene Understanding observer en appelant des fonctions publiques de cet exemple de script.

L’activation d' *instancier Prefabs*, démontrera la création d’objets qui se dimensionnent pour s’adapter à tous les [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), rassemblés correctement sous un objet parent.

![options du contrôleur de démonstration](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Notes d’application générées

Générez et déployez sur HoloLens en mode standard. Une fois exécuté, un certain nombre de boutons doivent s’afficher pour jouer avec les fonctionnalités.

Notez qu’il existe un certain nombre de requêtes pour l’observateur. Une configuration incorrecte d’un résultat de requête d’extraction dans votre charge utile d’événement ne contient pas les données attendues. Par exemple, si l’un ne demande pas de quad, aucune texture de masque d’occlusion n’est alors présente. De la même manière, aucun maillage universel ne s’affiche si l’observateur n’est pas configuré pour demander des maillages. Le `DemoSceneUnderstandingController` script prend en charge certaines de ces dépendances, mais pas toutes.

Les fichiers de scène enregistrés sont accessibles via le portail de l' [appareil](/windows/mixed-reality/using-the-windows-device-portal) à l’adresse `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Ces fichiers de scène peuvent être utilisés dans l’éditeur en les spécifiant dans le profil d’observateur trouvé dans l’inspecteur.

![Emplacement du fichier d’octets dans le portail de l’appareil](../images/spatial-awareness/BytesInDevicePortal.png)

![Octets de scène sérialisés dans l’observateur](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Voir aussi

* [Vue d’ensemble du mappage spatial WMR](/windows/mixed-reality/scene-understanding)
* [Vue d’ensemble du mappage spatial WMR](/windows/mixed-reality/scene-understanding-sdk)