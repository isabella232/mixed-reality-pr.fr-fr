---
title: Présentation des tutoriels sur les fonctionnalités multi-utilisateurs
description: Suivez ce cours pour découvrir comment implémenter des expériences multi-utilisateurs partagées dans une application HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, fonctionnalités multi-utilisateurs, Photon, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure
ms.localizationpriority: high
ms.openlocfilehash: dc8f495bc620eca3539b48f38fa15d089c0e28f4
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702458"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. Présentation des tutoriels sur les fonctionnalités multi-utilisateurs

Bienvenue dans les tutoriels sur les fonctionnalités multiutilisateurs ! Dans cette série de tutoriels, vous allez apprendre les bases de la création d’une expérience multiutilisateur à l’aide de <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN). PUN est l’une des nombreuses options de réseau que peuvent utiliser les développeurs de réalité mixte pour créer des expériences partagées.

Tutoriels de cette série :

* [Configuration de Photon Unity Networking](mr-learning-sharing-02.md)
* [Connexion de plusieurs utilisateurs](mr-learning-sharing-03.md)
* [Partage de mouvements d’objet avec plusieurs utilisateurs](mr-learning-sharing-04.md)
* [Intégration d’Azure Spatial Anchors dans une expérience partagée](mr-learning-sharing-05.md)

## <a name="objectives"></a>Objectifs

* Apprendre à créer une application PUN et y connecter votre projet Unity
* Apprendre à connecter plusieurs utilisateurs dans un environnement partagé
* Apprendre à partager les mouvements d’objets avec d’autres utilisateurs
* Apprendre à obtenir un alignement spatial entre plusieurs appareils

## <a name="prerequisites"></a>Prérequis

* Ordinateur Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)
* SDK Windows 10 (10.0.18362.0 ou version ultérieure)
* Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020 LTS installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté
* Avoir suivi la section [Créer une ressource d’ancres spatiales](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) du tutoriel [Démarrage rapide : Créer une application HoloLens Unity qui utilise Azure Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Avoir suivi la série de [tutoriels de démarrage](mr-learning-base-01.md) ou connaître les fondamentaux d’Unity et de MRTK
* Avoir suivi la série de [tutoriels sur Azure Spatial Anchors](mr-learning-asa-01.md) ou avoir déjà créé des comptes Azure Spatial Anchors
* Si vous envisagez d’effectuer un déploiement à la fois sur Android et sur HoloLens :
  * Appareil Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">en mode développeur</a> et <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible avec ARCore</a> disposant d’une connexion USB à votre ordinateur Windows ou macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020 LTS installé et le module de prise en charge du build d’Android ajouté
* Si vous envisagez d’effectuer un déploiement à la fois sur iOS et sur HoloLens :
  * Ordinateur macOS avec les dernières versions de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> et de <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installées
  * Appareil iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible avec ARKit</a> disposant d’une connexion USB à votre ordinateur macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020 LTS installé et le module de prise en charge du build d’iOS ajouté

> [!IMPORTANT]
> La version de Mixed Reality Toolkit qui est recommandée pour cette série de tutoriels est MRTK 2.7.

> [!IMPORTANT]
> La version d’Unity recommandée pour cette série de tutoriels est Unity 2020 LTS. Cela remplace toutes les exigences de version Unity énoncées dans les prérequis indiqués ci-dessus.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 2. Configuration du réseau Photon Unity](mr-learning-sharing-02.md)