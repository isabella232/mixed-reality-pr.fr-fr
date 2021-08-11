---
title: Connexion de plusieurs utilisateurs
description: Suivez ce cours pour découvrir comment connecter plusieurs utilisateurs dans une application de réalité mixte HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, fonctionnalités multi-utilisateurs, Photon, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure
ms.localizationpriority: high
ms.openlocfilehash: ba8a29844489a9153f970f6e39ff2022701c845711ffd9abc232d8da8eeb2e32
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200731"
---
# <a name="3-connecting-multiple-users"></a>3. Connexion de plusieurs utilisateurs

Dans ce tutoriel, vous allez apprendre à connecter plusieurs utilisateurs dans le cadre d’une expérience partagée en direct. À la fin du tutoriel, vous pourrez exécuter l’application sur plusieurs appareils et chaque utilisateur pourra voir l’avatar d’autres utilisateurs se déplacer en temps réel.

## <a name="objectives"></a>Objectifs

* Découvrir comment connecter plusieurs utilisateurs dans un environnement partagé

## <a name="preparing-the-scene"></a>Préparation de la scène

Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutoriels.MultiUserCapabilities** > **Prefabs**, puis cliquez et faites glisser les préfabriqués suivants dans la fenêtre Hierarchy pour les ajouter à votre scène :

* Préfabriqué **NetworkLobby**
* Préfabriqué **SharedPlayground**

![Unity avec les préfabriqués nouvellement ajoutés NetworkLobby et SharedPlayground sélectionnés](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, puis faites glisser le préfabriqué suivant dans la fenêtre Hierarchy pour l’ajouter à votre scène :

* Préfabriqué **DebugWindow**

![Unity avec le préfabriqué nouvellement ajouté DebugWindow sélectionné](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Configuration de PUN pour instancier le préfabriqué utilisateur

Dans cette section, vous allez configurer le projet pour qu’il utilise le préfabriqué PhotonUser.

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.

Dans la fenêtre Hierarchy, développez l’objet **NetworkLobby** et sélectionnez l’objet enfant **NetworkRoom**. Ensuite, dans la fenêtre Inspector, localisez le composant **Photon Room (Script)** et configurez-le comme suit :

* Affectez au champ **Photon User Prefab** le préfabriqué **PhotonUser** du dossier Resources.

![Unity avec le composant Photon Room partiellement configuré](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Essai de l’expérience avec plusieurs utilisateurs

Vous pouvez à présent générer le projet Unity et le déployer sur votre HoloLens. De retour dans Unity, passez au mode Game pendant que l’application s’exécute sur votre HoloLens : vous voyez l’avatar de l’utilisateur HoloLens se déplacer quand vous bougez la tête (HoloLens) :

![Animation montrant Unity avec des utilisateurs en réseau](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> L’application doit se connecter à Photon : vérifiez donc que votre ordinateur/appareil est connecté à Internet.

## <a name="congratulations"></a>Félicitations

Votre projet est désormais configuré pour permettre à plusieurs utilisateurs de se connecter à la même expérience et de voir leurs mouvements. Dans le tutoriel suivant, vous allez implémenter des fonctionnalités pour partager les mouvements d’objets avec plusieurs appareils.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 4. Partage de mouvements d’objet avec plusieurs utilisateurs](mr-learning-sharing-04.md)
