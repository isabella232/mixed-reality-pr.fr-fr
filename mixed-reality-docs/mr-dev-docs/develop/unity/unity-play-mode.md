---
title: Mode Lecture Unity
description: Découvrez comment utiliser le mode lecture dans l’éditeur Unity pour afficher un aperçu des modifications apportées à votre application sur un appareil sans déployer une application.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, communication à distance, accès distant holographique, lecteur de communication à distance holographique, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, mode de lecture Unity
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333399"
---
# <a name="unity-play-mode"></a>Mode Lecture Unity

Un moyen rapide de travailler sur votre projet Unity consiste à utiliser le « mode lecture », qui exécute votre application localement dans l’éditeur Unity sur votre PC. Unity utilise la communication à distance holographique pour offrir un moyen rapide d’afficher un aperçu de votre contenu sur un appareil HoloLens réel. Le mode lecture peut également être utilisé avec un casque Windows Mixed Reality attaché à votre PC de développement.

## <a name="holographic-remoting-setup"></a>Configuration de la communication à distance holographique

1. Tout d’abord, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Microsoft Store sur votre HoloLens 2
2. Exécutez l’application de lecteur de communication à distance holographique sur HoloLens 2 et vous verrez le numéro de version et l’adresse IP à laquelle se connecter.
    * V 2.4 ou version ultérieure est nécessaire pour fonctionner avec le plug-in OpenXR

    ![Capture d’écran du lecteur de communication à distance holographique s’exécutant dans HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Communication à distance holographique en mode de lecture de l’éditeur Unity

La création d’un projet Unity UWP dans Visual Studio Project et son empaquetage et son déploiement sur un appareil HoloLens 2 peuvent prendre un certain temps. Une solution consiste à activer la fonctionnalité de communication à distance de l’éditeur holographique, qui vous permet de déboguer votre script C# en mode « lecture » directement sur un appareil HoloLens 2 sur votre réseau. Ce scénario évite la surcharge liée à la création et au déploiement d’un package UWP sur un appareil distant.

1. Suivez les étapes de la configuration de la [communication à distance holographique](#holographic-remoting-setup)
2. Ouvrez la communication à distance de l' **éditeur Windows > XR > OpenXR**:

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-features-img-02.png)

3. Entrez l’adresse IP obtenue à partir de l’application de communication à distance holographique, puis sélectionnez **activer l’accès distant** de l’éditeur.

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec les fonctionnalités mises en surbrillance](images/openxr-features-img-03.png)

Vous pouvez maintenant cliquer sur le bouton « lecture » pour lire votre application Unity dans l’application de communication à distance holographique sur votre HoloLens. Vous pouvez également [attacher Visual Studio à Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) pour déboguer des scripts C# en mode lecture.

> [!NOTE]
> À partir de la version 0.1.0, le runtime de communication à distance holographique ne prend pas en charge les ancres, et les fonctionnalités ARAnchorManager ne fonctionnent pas via la communication à distance.  Cette fonctionnalité est disponible dans les versions ultérieures.

## <a name="unity-play-mode-with-holographic-remoting"></a>Mode de lecture Unity avec accès distant holographique

Avec la communication à distance holographique, vous pouvez expérimenter votre application sur le HoloLens pendant qu’elle s’exécute dans l’éditeur Unity sur votre PC. L’entrée de pointage, de mouvement, de voix et de mappage spatial est envoyée de votre HoloLens à votre PC. Les frames rendus sont ensuite renvoyés à votre HoloLens. C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet.
1. Sur votre HoloLens, accédez à la **Microsoft Store** et installez l’application de **[lecteur de communication à distance holographique](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
2. Sur votre HoloLens, démarrez l’application de **lecteur de communication à distance holographique** .
3. Dans Unity, accédez au menu **fenêtre** , développez le sous-menu **XR** , puis sélectionnez **émulation holographique**.
4. Définissez le **mode d’émulation** à **distant sur appareil**.
5. Pour **ordinateur distant**, entrez l’adresse IP de votre HoloLens.
6. Sélectionnez **Connecter**. Le changement d' **État** de la connexion doit être défini sur **connecté** et l’écran s’affichera vide dans HoloLens.
7. Sélectionnez le bouton de **lecture** pour démarrer le mode lecture et tester l’application sur votre HoloLens.

La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi. Pour plus d’informations, consultez la documentation sur les [lecteurs de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Pour de meilleurs résultats, assurez-vous que votre application définit correctement le [point de focus](focus-point-in-unity.md). Cela permet à la communication à distance holographique d’adapter au mieux votre scène à la latence de votre connexion sans fil.

## <a name="see-also"></a>Voir aussi
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
