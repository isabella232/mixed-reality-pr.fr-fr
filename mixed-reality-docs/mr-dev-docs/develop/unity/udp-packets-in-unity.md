---
title: Paquets UDP dans les applications UWP Unity
description: Découvrez comment configurer une application Unity UWP pour envoyer et recevoir des paquets UDP sur un réseau sécurisé.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, paquets UDP, Socket, serveur client, point de terminaison, mise en réseau, ordinateur distant, DatagramSocket, exemple, .net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566976"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="a6d23-104">Paquets UDP dans les applications UWP Unity</span><span class="sxs-lookup"><span data-stu-id="a6d23-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="a6d23-105">Vous pouvez configurer vos applications Unity plateforme Windows universelle (UWP) pour recevoir des paquets UDP avec l’aide d’un client et d’un serveur de socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a6d23-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="a6d23-106">Comme les sockets UDP ne maintiennent pas la connexion sur les deux points de terminaison, ils constituent une solution rapide et simple pour la mise en réseau entre les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a6d23-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="a6d23-107">Toutefois, vous êtes chargé de vérifier si les paquets sont accessibles à leur destination, car les sockets UDP ne le font pas automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a6d23-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="a6d23-108">Programme d’installation</span><span class="sxs-lookup"><span data-stu-id="a6d23-108">Setup</span></span>

<span data-ttu-id="a6d23-109">Ouvrez vos projets HoloLens manifest.jssur fichier et assurez-vous que vous avez activé :</span><span class="sxs-lookup"><span data-stu-id="a6d23-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="a6d23-110">**Internet (client & Server)**</span><span class="sxs-lookup"><span data-stu-id="a6d23-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="a6d23-111">**Réseaux privés (Client & Server)**.</span><span class="sxs-lookup"><span data-stu-id="a6d23-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="a6d23-112">Création de votre serveur et client Socket</span><span class="sxs-lookup"><span data-stu-id="a6d23-112">Build your socket client and server</span></span> 

<span data-ttu-id="a6d23-113">Suivez les instructions pour [créer un serveur et un client de socket UDP de base](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="a6d23-113">Follow the instructions for [building a basic UDP socket client and server](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="a6d23-114">Vous utiliserez la classe [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) pour envoyer et recevoir des données via UDP et former un client et un serveur Echo.</span><span class="sxs-lookup"><span data-stu-id="a6d23-114">You'll be using the [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="a6d23-115">Nous vous recommandons également de lire les autres sections de ressources de cet article, car elles s’appliquent à des cas d’usage plus complexes et personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a6d23-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="a6d23-116">Si vous avez des difficultés à envoyer des paquets UDP de PC à PC, vérifiez que votre réseau autorise ces opérations.</span><span class="sxs-lookup"><span data-stu-id="a6d23-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="a6d23-117">Si votre réseau bloque les paquets UDP de quelque façon que ce soit, votre appareil HoloLens ne sera pas en mesure de les écouter.</span><span class="sxs-lookup"><span data-stu-id="a6d23-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="a6d23-118">Vous pouvez télécharger un exemple d’application DatagramSocket UDP complet à partir du lien ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a6d23-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6d23-119">Installer les outils</span><span class="sxs-lookup"><span data-stu-id="a6d23-119">Install the tools</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="a6d23-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6d23-120">See also</span></span> 
* [<span data-ttu-id="a6d23-121">Expériences avec des hologrammes partagés et le stockage BLOB Azure/multidiffusion UDP</span><span class="sxs-lookup"><span data-stu-id="a6d23-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)