---
title: Installation de PIX pour HoloLens 2
description: Découvrez comment installer PIX pour les appareils HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, capture, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615329"
---
# <a name="installing-pix-for-hololens-2"></a>Installation de PIX pour HoloLens 2

[Pix](https://devblogs.microsoft.com/pix) est un outil de réglage et de débogage des performances pour les applications DirectX 12 sur Windows. 

## <a name="setup"></a>Installation

1. Prenez la version la plus récente de la [version]( https://devblogs.microsoft.com/pix/download) pix de votre ordinateur hôte et connectez votre HoloLens 2 à votre PC via un câble USB.

2. Si votre HoloLens 2 est sur une [version de Windows Insider](https://insider.windows.com) ou si elle a une configuration qui interrompt pix,  [relancez votre appareil](https://docs.microsoft.com/hololens/hololens-recovery) pour effacer toutes les données.

3. Activer le **mode développeur** et le **portail des appareils**:

* Ouvrir les **paramètres** à partir de l’interpréteur de commandes :

![Capture d’écran du menu HoloLens avec le bouton paramètres mis en surbrillance](images/pix-img-01.jpg)

* Sélectionnez **mettre à jour la sécurité &**:

![Capture d’écran de la fenêtre Paramètres ouverte sur HoloLens avec le bouton mettre à jour et sécurité mis en surbrillance](images/pix-img-02.jpg)

* Cliquez **pour les développeurs**:

![Capture d’écran de la fenêtre sécurité et mises à jour ouverte avec le bouton pour les développeurs mis en surbrillance](images/pix-img-03.jpg)

* Activer l' **utilisation des fonctionnalités de développement** et **activer le portail des appareils**

![Capture d’écran de la fenêtre pour les développeurs ouverte dans paramètres avec le bouton Activer le portail pour appareils mis en surbrillance](images/pix-img-04.jpg)

![Capture d’écran de la fenêtre pour les développeurs ouverte dans les paramètres avec l’activation de l’utilisation du développement des fonctionnalités en surbrillance](images/pix-img-05.jpg)

* Lorsque l’appareil est toujours connecté, en éveil et avec l’utilisateur connecté, lancez Visual Studio.

> [!IMPORTANT]
> Assurez-vous que votre appareil n’est pas en mode veille ou en veille. Si vous rencontrez des problèmes avec cette étape, reportez-vous aux [instructions du portail d’appareils Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).

## <a name="preparing-for-deployment"></a>Préparation du déploiement

1. Dans Visual Studio, définissez **ARM64** en tant que plateforme et **appareil** comme périphérique :

![Capture d’écran de la solution Visual Studio avec les paramètres de plateforme et d’appareil mis en surbrillance](images/pix-img-06.png)

2. Lorsque Visual Studio vous invite à entrer un **code confidentiel** sur l’appareil :

![Capture d’écran de la fenêtre contextuelle de Visual Studio demandant le code confidentiel](images/pix-img-07.png)

* Sélectionner des **paramètres** à partir de l’interpréteur de commandes
* Sélectionner **mettre à jour la sécurité &**
* Cliquez **pour développeurs** et appuyez sur paire sous **découverte d’appareil** 

![Capture d’écran de la fenêtre pour les développeurs ouverte dans paramètres avec la découverte de périphérique mise en surbrillance](images/pix-img-08.jpg)

![Capture d’écran de la fenêtre contextuelle de l’appareil payant avec le code d’inscription mis en surbrillance](images/pix-img-09.jpg)

* Entrer le numéro de code confidentiel généré dans Visual Studio

3. Visual Studio déploie l’application sur le HoloLens 2 connecté, ce qui peut prendre quelques minutes en fonction de l’application.

## <a name="launching-pix"></a>Lancement de PIX

Tout d’abord, utilisez le portail de l’appareil pour vérifier que l’application n’est pas en cours d’exécution sur HoloLens 2. Ensuite, lancez PIX, connectez-vous à votre appareil, puis cliquez sur **page d’hébergement**:

![Capture d’écran de l’écran d’accueil de l’application PIX](images/pix-img-10.png)

* Sélectionnez **se connecter** dans le menu de gauche :

![Capture d’écran du menu de gauche de l’application PIX avec le bouton de connexion mis en surbrillance](images/pix-img-11.png)

2. Dans l’onglet **ordinateur** , cliquez sur **Ajouter** et entrez les informations d’identification suivantes :
    * Alias : jusqu’à la discrétion de l’utilisateur
    * Nom d’hôte ou adresse IP : 127.0.0.1

3. Cliquez sur **se connecter** dans le coin inférieur droit de l’onglet **ordinateur** :

![Capture d’écran de la fenêtre de connexion d’application PIX avec l’alias, le nom d’hôte, l’adresse IP et le bouton Ajouter mis en surbrillance](images/pix-img-12.png)

> [!NOTE]
> La première connexion est toujours plus lente en raison de la copie des fichiers binaires.

4. Quand PIX s’est connecté à HoloLens 2, recherchez votre application dans la section **Sélectionner le processus cible** de l’onglet lancer UWP, puis cliquez sur **lancer**:

![Capture d’écran de l’application PIX avec la fenêtre Sélectionner le processus cible et le bouton de lancement mis en surbrillance](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU capturé

1. Démarrez la capture GPU en cliquant sur **photo** dans la section **capture GPU** :

![Capture d’écran de l’application PIX avec le panneau de connexion du PC ouvert avec la capture GPU mise en surbrillance](images/pix-img-14.png)

2. Ouvrez la capture pour l’analyse en cliquant sur la capture d’écran générée dans le panneau **capture GPU** :

![Capture d’écran de l’application PIX avec la section de capture GPU ouverte avec le panneau de capture GPU mis en surbrillance](images/pix-img-15.png)

3. Appuyez sur **Démarrer** pour commencer l’analyse :

![Capture d’écran de l’application PIX bouton Démarrer mis en surbrillance](images/pix-img-16.png)

> [!IMPORTANT]
> Si vous collectez des données de minutage après avoir effectué une capture GPU, vous devrez redémarrer le casque. Il s’agit d’un redémarrage unique de l’appareil, qui est requis pour la collecte des données de minutage.

PIX est maintenant prêt à être utilisé.

## <a name="see-also"></a>Voir aussi
* [Page d’accueil PIX](https://devblogs.microsoft.com/pix)