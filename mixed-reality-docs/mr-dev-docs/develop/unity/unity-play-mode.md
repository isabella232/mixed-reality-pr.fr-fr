---
title: Affichez un aperçu de votre travail avec la communication à distance holographique
description: Utilisez la communication à distance holographique en mode lecture pour afficher un aperçu des modifications apportées à votre application sur un appareil sans déployer une application.
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: unity, communication à distance, communication à distance holographique, lecteur de communication à distance holographique, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, mode de lecture unity
ms.openlocfilehash: 0c71791c80a5e84ee48241baa756064a800e5a41
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757211"
---
# <a name="preview-your-work-with-holographic-remoting"></a>Affichez un aperçu de votre travail avec la communication à distance holographique

vous pouvez utiliser la communication à distance holographique pour diffuser du contenu holographique vers votre HoloLens 2 en temps réel. C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet. 

Un moyen rapide de travailler sur votre projet Unity consiste à utiliser le « mode lecture », qui exécute votre application localement dans l’éditeur Unity sur votre PC. unity utilise la communication à distance holographique pour offrir un moyen rapide d’afficher un aperçu de votre contenu sur un appareil HoloLens réel. le Mode lecture peut également être utilisé avec un Windows Mixed Reality casque attaché à votre PC de développement.

## <a name="holographic-remoting-setup"></a>Configuration de la communication à distance holographique

1. tout d’abord, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Microsoft Store sur votre HoloLens 2
2. exécutez l’application de lecteur de communication à distance holographique sur le HoloLens 2 et vous verrez le numéro de version et l’adresse IP à laquelle se connecter.
    * V 2.4 ou version ultérieure est nécessaire pour fonctionner avec le plug-in OpenXR

    ![Capture d’écran du lecteur de communication à distance holographique en cours d’exécution dans le HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Mode de lecture Unity avec accès distant holographique

avec la communication à distance holographique, vous pouvez expérimenter votre application sur le HoloLens pendant qu’elle s’exécute dans l’éditeur unity sur votre PC. les entrées de pointage, de mouvement, de voix et de mappage spatial sont envoyées à partir de votre HoloLens sur votre PC. Les frames rendus sont ensuite renvoyés à votre HoloLens. C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet.

[!INCLUDE[](includes/unity-play-mode.md)]

La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi. Pour plus d’informations, consultez la documentation sur les [lecteurs de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Pour de meilleurs résultats, assurez-vous que votre application définit correctement le [point de focus](focus-point-in-unity.md). Cela permet à la communication à distance holographique d’adapter au mieux votre scène à la latence de votre connexion sans fil.

## <a name="see-also"></a>Voir aussi

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
