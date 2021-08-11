---
title: Partage de mouvements d’objet avec plusieurs utilisateurs
description: Suivez ce cours pour découvrir comment partager des mouvements d’objets avec plusieurs utilisateurs dans une application HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, fonctionnalités multi-utilisateurs, Photon, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure
ms.localizationpriority: high
ms.openlocfilehash: c9a37dd94083b796da6d5fba2727d739112e411b494af5882ad08525e733a722
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200786"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Partage de mouvements d’objet avec plusieurs utilisateurs

Dans ce tutoriel, vous allez apprendre à partager les mouvements d’objets pour que tous les participants d’une expérience partagée puissent collaborer et voir leurs interactions.

## <a name="objectives"></a>Objectifs

* Configurer votre projet pour partager les mouvements d’objets
* Apprendre à créer une application collaborative multiutilisateur simple

## <a name="preparing-the-scene"></a>Préparation de la scène

Dans cette section, vous allez préparer la scène en ajoutant le préfabriqué du tutoriel.

Dans la fenêtre Hierarchy, développez l’objet **MixedRealityPlayspace** et sélectionnez l’objet enfant **Main Camera**, puis dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **AR Camera Manager (Script)** à l’objet **Main Camera** :

![Unity avec le composant AR Camera Manager partiellement configuré](images/mr-learning-sharing/sharing-04-section1-step1-0.png)

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, puis faites glisser le préfabriqué **TableAnchor** sur l’objet **SharedPlayground** dans la fenêtre Hierarchy afin de l’ajouter à votre scène en tant qu’enfant de l’objet SharedPlayground :

![Unity avec le préfabriqué nouvellement ajouté TableAnchor sélectionné](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

Dans la fenêtre Hierarchy, assurez-vous que l’objet **MixedRealityPlayspace** est développé et que l’objet **TableAnchor** est sélectionné. Faites glisser le composant **Main Camera** dans le champ **Camera** du composant **AR Session Origin** de **TableAnchor**:

![Unity avec l’affectation de Main Camera d’AR Session Origin configurée](images/mr-learning-sharing/sharing-04-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Configuration de PUN pour instancier les objets

Dans cette section, vous allez configurer le projet de façon à utiliser l’expérience Rover Explorer créée pendant les [tutoriels de démarrage](mr-learning-base-01.md) et définir où il sera instancié.

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.

Dans la fenêtre Hierarchy, développez l’objet **NetworkLobby** et sélectionnez l’objet enfant **NetworkRoom**. Ensuite, dans la fenêtre Inspector, localisez le composant **Photon Room (Script)** et configurez-le comme suit :

* Dans le champ **Rover Explorer Prefab**, attribuez le préfabriqué **RoverExplorer_Complete_Variant** à partir du dossier Resources.

![Unity avec le composant Photon Room partiellement configuré](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

L’objet enfant **NetworkRoom** étant toujours sélectionné, dans la fenêtre Hierarchy, développez l’objet **TableAnchor**. Ensuite, dans la fenêtre Inspector, localisez le composant **Photon Room (Script)** et configurez-le comme suit :

* Affectez au champ **Rover Explorer Location** l’objet enfant TableAnchor > **Table** à partir de la fenêtre Hierarchy.

![Unity avec le composant Photon Room configuré](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Essai de l’expérience avec le mouvement d’objet partagé

Vous pouvez à présent générer le projet Unity et le déployer sur votre HoloLens. De retour dans Unity, si vous appuyez sur le bouton Play pour passer en mode Game pendant que l’application s’exécute sur votre HoloLens, vous voyez l’objet se déplacer dans Unity quand vous le déplacez dans HoloLens :

![Animation montrant Unity avec des objets en réseau](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Félicitations

Vous venez de configurer votre projet pour synchroniser les mouvements d’objet afin que les utilisateurs puissent voir les objets se déplacer quand d’autres utilisateurs les déplacent. Dans le tutoriel suivant, vous allez implémenter une fonctionnalité afin d’aligner l’expérience dans le monde physique. Cela permettra de s’assurer que les utilisateurs se voient les uns les autres à leur emplacement physique réel, et que les objets apparaissent dans la même position physique et la même rotation pour tous les utilisateurs.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 5. Intégration d’ancres spatiales Azure dans une expérience partagée](mr-learning-sharing-05.md)
