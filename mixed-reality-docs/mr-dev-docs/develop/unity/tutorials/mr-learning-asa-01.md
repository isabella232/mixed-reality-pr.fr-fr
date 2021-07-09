---
title: Introduction aux tutoriels Azure Spatial Anchors
description: Suivez ce cours pour découvrir comment implémenter Azure Spatial Anchors dans une application de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, ios, android, Windows 10, ARCore, macOS, prise en charge de build Android, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 2d664c79c0e2d111dc4a0b7b449399682cda1f06
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403450"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1. Introduction aux tutoriels Azure Spatial Anchors

Bienvenue dans les tutoriels Azure Spatial Anchors ! Cette série de tutoriels vous apprend les notions de base d’<a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) et vous explique comment ancrer une expérience de réalité mixte complète dans le monde réel. Vous verrez également comment déployer votre projet sur Android et iOS.

Tutoriels de cette série :

1. [Introduction](mr-learning-asa-01.md) (vous êtes déjà ici)
2. [Bien démarrer avec Azure Spatial Anchors](mr-learning-asa-02.md)
3. [Enregistrement, récupération et partage d’ancres spatiales Azure](mr-learning-asa-03.md)
4. [Affichage du feedback Azure Spatial Anchors](mr-learning-asa-04.md)
5. [Azure Spatial Anchors pour Android et iOS](mr-learning-asa-05.md)

## <a name="objectives"></a>Objectifs

* Apprendre à créer des ancres spatiales et à les récupérer à partir d’Azure
* Apprendre à obtenir un alignement spatial entre plusieurs sessions d’application
* Apprendre à obtenir un alignement spatial entre plusieurs appareils
* Apprendre à préparer, générer et déployer votre projet sur Android et iOS

## <a name="prerequisites"></a>Prérequis

* Ordinateur Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)
* SDK Windows 10 10.0.18362.0 ou ultérieur
* Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020/2019 LTS installé et le module de prise en charge de build de la plateforme Windows universelle ajouté
* Avoir suivi la section [Créer une ressource d’ancres spatiales](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) du tutoriel [Démarrage rapide : Créer une application HoloLens Unity qui utilise Azure Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Avoir suivi la série de [tutoriels de démarrage](mr-learning-base-01.md) ou avoir une expérience de base avec Unity et MRTK
* Si vous envisagez d’effectuer un déploiement à la fois sur Android et sur HoloLens :
  * Appareil Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">en mode développeur</a> et <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible avec ARCore</a> disposant d’une connexion USB à votre ordinateur Windows ou macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020/2019 LTS installé et le module de prise en charge du build d’Android ajouté
* Si vous envisagez d’effectuer un déploiement à la fois sur iOS et sur HoloLens :
  * Ordinateur macOS avec les dernières versions de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> et de <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installées
  * Appareil iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible avec ARKit</a> disposant d’une connexion USB à votre ordinateur macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020/2019 LTS installé et le module de prise en charge du build d’iOS ajouté

> [!Important]
> Cette série de tutoriels prend en charge Unity 2020 LTS (actuellement 2020.3.x) si vous utilisez Open XR ou Plug-in XR Windows, ainsi qu’Unity 2019 LTS (actuellement 2019.4.x) si vous utilisez WSA hérité. Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 2. Bien démarrer avec les ancres spatiales Azure](mr-learning-asa-02.md)
