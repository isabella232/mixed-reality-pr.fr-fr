---
title: Installation de PIX pour HoloLens 2
description: découvrez comment installer PIX pour HoloLens 2 appareils.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, capture, casque de réalité mixte, casque windows mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 2e5e66ea5a1a2b68d91213c38d88d815f54a28fa5328ab3b2d93f1e267f6f994
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217273"
---
# <a name="installing-pix-for-hololens-2"></a>Installation de PIX pour HoloLens 2

[Pix](https://devblogs.microsoft.com/pix) est un outil de réglage et de débogage des performances pour les applications DirectX 12 sur Windows. 

## <a name="setup"></a>Installation

1. prenez la version la plus récente de la [version]( https://devblogs.microsoft.com/pix/download) PIX de votre ordinateur hôte et connectez votre HoloLens 2 à votre pc via un câble USB.

2. si votre HoloLens 2 se trouve sur une [version Windows insider](https://insider.windows.com) ou si elle a une configuration qui interrompt PIX, [reflashez votre appareil](/hololens/hololens-recovery) pour effacer toutes les données.

3. Activer le **mode développeur** et le **portail des appareils**:

* ouvrez **Paramètres** à partir de la page d’hébergement de la réalité mixte :

![capture d’écran du menu conHoloLens avec le bouton paramètres mis en surbrillance](images/pix-img-01.jpg)

* Sélectionnez **mettre à jour la sécurité &**:

![capture d’écran de la fenêtre paramètres ouverte sur HoloLens avec le bouton mettre à jour et sécurité mis en surbrillance](images/pix-img-02.jpg)

* Sélectionnez **pour les développeurs**:

![Capture d’écran de la fenêtre sécurité et mises à jour ouverte avec le bouton pour les développeurs mis en surbrillance](images/pix-img-03.jpg)

* Activer l' **utilisation des fonctionnalités de développement** et **activer le portail des appareils**

![Capture d’écran de la fenêtre pour les développeurs ouverte dans paramètres avec le bouton Activer le portail pour appareils mis en surbrillance](images/pix-img-04.jpg)

![Capture d’écran de la fenêtre pour les développeurs ouverte dans les paramètres avec l’activation de l’utilisation du développement des fonctionnalités en surbrillance](images/pix-img-05.jpg)

* Lorsque l’appareil est toujours connecté, en éveil et avec l’utilisateur connecté, lancez Visual Studio.

> [!IMPORTANT]
> Assurez-vous que votre appareil n’est pas en mode veille ou en veille. si vous rencontrez des problèmes avec cette étape, reportez-vous aux instructions du portail de l' [appareil Windows](./using-the-windows-device-portal.md).

## <a name="preparing-for-deployment"></a>Préparation du déploiement

1. dans Visual Studio, définissez **ARM64** en tant que plateforme et **appareil** comme périphérique :

![Capture d’écran de la solution Visual Studio avec les paramètres de plateforme et d’appareil mis en surbrillance](images/pix-img-06.png)

2. lorsque Visual Studio vous invite à entrer un **code confidentiel** à partir de l’appareil :

![Capture d’écran de la fenêtre contextuelle de Visual Studio demandant le code confidentiel](images/pix-img-07.png)

* sélectionner **Paramètres** dans l’interpréteur de commandes
* Sélectionner **mettre à jour la sécurité &**
* Sélectionnez **pour les développeurs** et appuyez sur paire sous **découverte d’appareil** 

![Capture d’écran de la fenêtre pour les développeurs ouverte dans paramètres avec la découverte de périphérique mise en surbrillance](images/pix-img-08.jpg)

![Capture d’écran de la fenêtre contextuelle de l’appareil payant avec le code d’inscription mis en surbrillance](images/pix-img-09.jpg)

* Entrez le numéro de code confidentiel généré dans Visual Studio

3. Visual Studio déploiera l’application sur le HoloLens 2 connecté, ce qui peut prendre quelques minutes en fonction de l’application.

## <a name="launching-pix"></a>Lancement de PIX

Tout d’abord, utilisez le portail de l’appareil pour vérifier que l’application n’est pas en cours d’exécution sur le HoloLens 2. Ensuite, lancez PIX, connectez-vous à votre appareil, puis sélectionnez **page d’hébergement**:

![Capture d’écran de l’écran d’accueil de l’application PIX](images/pix-img-10.png)

* sélectionnez **Connecter** dans le menu de gauche :

![Capture d’écran du menu de gauche de l’application PIX avec le bouton de connexion mis en surbrillance](images/pix-img-11.png)

2. Dans l’onglet **ordinateur** , sélectionnez **Ajouter**, puis entrez les informations d’identification suivantes :
    * Alias : jusqu’à la discrétion de l’utilisateur
    * Nom d’hôte ou adresse IP : 127.0.0.1

3. sélectionnez **Connecter** dans le coin inférieur droit de l’onglet **ordinateur** :

![Capture d’écran de la fenêtre de connexion d’application PIX avec l’alias, le nom d’hôte, l’adresse IP et le bouton Ajouter mis en surbrillance](images/pix-img-12.png)

> [!NOTE]
> La première connexion est toujours plus lente en raison de la copie des fichiers binaires.

4. quand PIX s’est connecté au HoloLens 2, recherchez votre application dans la section **sélectionner le processus cible** sous l’onglet lancer UWP, puis sélectionnez **lancer**:

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