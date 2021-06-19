---
title: Mode Lecture Unity
description: Découvrez comment utiliser le mode lecture dans l’éditeur Unity pour afficher un aperçu des modifications apportées à votre application sur un appareil sans déployer une application.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, communication à distance, accès distant holographique, lecteur de communication à distance holographique, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, mode de lecture Unity
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392289"
---
# <a name="unity-play-mode"></a>Mode Lecture Unity

Un moyen rapide de travailler sur votre projet Unity consiste à utiliser le « mode lecture », qui exécute votre application localement dans l’éditeur Unity sur votre PC. Unity utilise la communication à distance holographique pour offrir un moyen rapide d’afficher un aperçu de votre contenu sur un appareil HoloLens réel. Le mode lecture peut également être utilisé avec un casque Windows Mixed Reality attaché à votre PC de développement.

## <a name="holographic-remoting-setup"></a>Configuration de la communication à distance holographique

1. Tout d’abord, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Microsoft Store sur votre HoloLens 2
2. Exécutez l’application de lecteur de communication à distance holographique sur HoloLens 2 et vous verrez le numéro de version et l’adresse IP à laquelle se connecter.
    * V 2.4 ou version ultérieure est nécessaire pour fonctionner avec le plug-in OpenXR

    ![Capture d’écran du lecteur de communication à distance holographique s’exécutant dans HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Mode de lecture Unity avec accès distant holographique

Avec la communication à distance holographique, vous pouvez expérimenter votre application sur le HoloLens pendant qu’elle s’exécute dans l’éditeur Unity sur votre PC. L’entrée de pointage, de mouvement, de voix et de mappage spatial est envoyée de votre HoloLens à votre PC. Les frames rendus sont ensuite renvoyés à votre HoloLens. C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet.

[!INCLUDE[](includes/unity-play-mode.md)]

La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi. Pour plus d’informations, consultez la documentation sur les [lecteurs de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Pour de meilleurs résultats, assurez-vous que votre application définit correctement le [point de focus](focus-point-in-unity.md). Cela permet à la communication à distance holographique d’adapter au mieux votre scène à la latence de votre connexion sans fil.

## <a name="see-also"></a>Voir aussi

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
