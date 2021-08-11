---
title: Paquets UDP dans les applications UWP Unity
description: Découvrez comment configurer une application Unity UWP pour envoyer et recevoir des paquets UDP sur un réseau sécurisé.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, paquets UDP, Socket, serveur client, point de terminaison, mise en réseau, ordinateur distant, DatagramSocket, exemple, .net
ms.openlocfilehash: a24498384ccb2018f62f00523bf33764d2ef7c019dec0cfd8fc70d86b55a81bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192555"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Paquets UDP dans les applications UWP Unity

vous pouvez configurer vos applications unity plateforme Windows universelle (UWP) pour recevoir des paquets udp avec l’aide d’un client et d’un serveur de socket udp. Comme les sockets UDP ne maintiennent pas la connexion sur les deux points de terminaison, ils constituent une solution rapide et simple pour la mise en réseau entre les ordinateurs distants. Toutefois, vous êtes chargé de vérifier si les paquets sont accessibles à leur destination, car les sockets UDP ne le font pas automatiquement.

## <a name="setup"></a>Installation

ouvrez vos projets HoloLens manifest.jsdans le fichier et assurez-vous que vous avez activé :
* **Internet (client & Server)** 
* **Réseaux privés (Client & Server)**.

## <a name="build-your-socket-client-and-server"></a>Création de votre serveur et client Socket 

Suivez les instructions pour [créer un serveur et un client de socket UDP de base](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server). Vous utiliserez la classe [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) pour envoyer et recevoir des données via UDP et former un client et un serveur Echo. Nous vous recommandons également de lire les autres sections de ressources de cet article, car elles s’appliquent à des cas d’usage plus complexes et personnalisés. 

> [!IMPORTANT]
> Si vous avez des difficultés à envoyer des paquets UDP de PC à PC, vérifiez que votre réseau autorise ces opérations. si votre réseau bloque les paquets UDP de quelque façon que ce soit, votre appareil HoloLens ne sera pas en mesure de les écouter.

Vous pouvez télécharger un exemple d’application DatagramSocket UDP complet à partir du lien ci-dessous :

> [!div class="nextstepaction"]
> [Installer les outils](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Voir aussi 
* [expériences avec Hologrammes partagé et Azure Blob Stockage la multidiffusion/UDP](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)