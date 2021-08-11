---
title: Présentation des tutoriels MRTK
description: Ce cours montre comment utiliser Mixed Reality Toolkit (MRTK) pour créer une application de réalité mixte à partir de rien.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, solveurs, suivi oculaire, commandes vocales
ms.localizationpriority: high
ms.openlocfilehash: e8eb878e7ab2fecf27defc5f28e045c4d4768682e95a3a42cda7f324a21617e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224785"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1. Présentation des tutoriels MRTK

Bienvenue dans la série des tutoriels de démarrage ! Dans ces tutoriels, vous allez découvrir Mixed Reality Toolkit (MRTK), ainsi que les fonctionnalités qu’il propose. Vous allez également créer une expérience de réalité mixte dans laquelle l’utilisateur pourra explorer un hologramme modélisé d’après le rover Curiosity de la NASA. À la fin de cette série, vous aurez une vision claire de MRTK et de la façon dont il peut accélérer votre processus de développement.

Les tutoriels de cette série se suivent, il est donc important de respecter l’ordre indiqué :

1. [Introduction](mr-learning-base-01.md) (vous êtes déjà ici)
2. [Initialisation de votre projet et déploiement de votre première application](mr-learning-base-02.md)
3. [Configuration des profils MRTK](mr-learning-base-03.md)
4. [Positionnement des objets dans la scène](mr-learning-base-04.md)
5. [Création de contenu dynamique avec des solveurs](mr-learning-base-05.md)
6. [Création d’interfaces utilisateur](mr-learning-base-06.md)
7. [Interaction avec les objets 3D](mr-learning-base-07.md)
8. [Utilisation du suivi oculaire](mr-learning-base-08.md)
9. [Utilisation des commandes vocales](mr-learning-base-09.md)

## <a name="objectives"></a>Objectifs

* Apprendre à configurer Unity pour MRTK
* Apprendre à créer et à déployer des applications sur votre appareil
* Apprendre à utiliser certaines des fonctionnalités clés de MRTK
* Créer une expérience de réalité mixte complète

## <a name="prerequisites"></a>Prérequis

* PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)
* [SDK Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou ultérieur
* Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020.3 LTS ou Unity 2019.4 LTS installé (**OpenXR requiert la version 2020.3.8 ou une version ultérieure pour éviter les bogues**)

Quand vous installez Unity, vérifiez les composants suivants sous **Platforms**.

* **Universal Windows Platform Build Support**
* **Windows Build Support (IL2CPP)**

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

Si vous avez installé Unity sans ces options, vous pouvez les ajouter par le biais du menu **Add Modules** dans Unity Hub.

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> La version de MRTK recommandée pour cette série de tutoriels est MRTK 2.7.2

> [!Important]
> Cette série de tutoriels prend en charge Unity 2020 LTS (actuellement 2020.3.x) si vous utilisez Open XR ou le plug-in Windows XR, ainsi qu’Unity 2019 LTS (actuellement 2019.4.x) si vous utilisez WSA hérité ou le plug-in Windows XR. Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 2. Initialisation de votre projet et déploiement de votre première application](mr-learning-base-02.md)
