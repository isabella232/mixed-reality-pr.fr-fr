---
title: Créer une application PC de communication à distance holographique
description: Suivez ce cours pour découvrir comment créer une application pour PC afin d’effectuer à distance une expérience de réalité mixte depuis votre PC vers HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, communication à distance holographique sur PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 19c10ad0cdad70b38663f9da0f7d2a1f1702d94d
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757231"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Création d’une application PC de communication à distance holographique

Dans ce tutoriel, vous allez apprendre à créer une application PC qui utilise la communication à distance holographique pour streamer votre travail en cours vers le HoloLens et le voir sans avoir à le créer en premier.

[Apprenez les bases de la communication à distance holographique.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

## <a name="objectives"></a>Objectifs

* Configurer Unity pour la communication à distance holographique
* Apprendre à créer et déployer l’application avec Visual Studio
* Développement d’une application de communication à distance holographique et la connecter à HoloLens

## <a name="configuring-the-capabilities"></a>Configuration des fonctionnalités

Dans la fenêtre **Paramètres du projet**, développez les **Paramètres de publication**, faites défiler jusqu’à la section Fonctionnalités et cochez la case des fonctionnalités affichées ci-dessous en plus des fonctionnalités existantes.

* Serveur client Internet
* Serveur client de réseau privé

![activation des fonctionnalités](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>Générer votre application pour PC

Vous pouvez à présent générer votre application de communication à distance holographique sur votre PC. Suivez les étapes ci-dessous et apportez ces modifications pour générer cette application sur votre PC.

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>Test d’une application de communication à distance holographique

Pour connecter votre application PC à votre HoloLens 2, effectuez les étapes suivantes :

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Installer l’application Remoting Player sur l’appareil HoloLens 2

* Sur votre HoloLens 2, accédez à l’application Store et recherchez « **Remoting Player** ».
* Sélectionnez l’application **Remoting Player**.
* Appuyez sur **Install** pour télécharger et installer l’application.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Connecter l’application PC de communication à distance holographique à Remoting Player

* Démarrez **Remoting Player** sur votre HoloLens.
* Notez l’**adresse IP** d’HoloLens. Celle-ci apparaît sous la forme d’un hologramme dès le lancement de **Remoting Player**.
* Ouvrez l’application PC de communication à distance holographique sur votre PC.
* Une fois l’application lancée, entrez l’**adresse IP** , puis cliquez sur le bouton **Connect** pour vous connecter.

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez appris à créer une application PC de communication à distance holographique et à la connecter à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte. Une fois l’application PC de communication à distance holographique connectée à HoloLens, l’expérience de réalité mixte est diffusée en streaming sur votre appareil HoloLens 2.
