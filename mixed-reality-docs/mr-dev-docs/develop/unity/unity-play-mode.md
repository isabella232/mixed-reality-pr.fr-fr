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
# <a name="unity-play-mode"></a><span data-ttu-id="9c31a-104">Mode Lecture Unity</span><span class="sxs-lookup"><span data-stu-id="9c31a-104">Unity Play Mode</span></span>

<span data-ttu-id="9c31a-105">Un moyen rapide de travailler sur votre projet Unity consiste à utiliser le « mode lecture », qui exécute votre application localement dans l’éditeur Unity sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="9c31a-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="9c31a-106">Unity utilise la communication à distance holographique pour offrir un moyen rapide d’afficher un aperçu de votre contenu sur un appareil HoloLens réel.</span><span class="sxs-lookup"><span data-stu-id="9c31a-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="9c31a-107">Le mode lecture peut également être utilisé avec un casque Windows Mixed Reality attaché à votre PC de développement.</span><span class="sxs-lookup"><span data-stu-id="9c31a-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="9c31a-108">Configuration de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="9c31a-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="9c31a-109">Tout d’abord, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Microsoft Store sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9c31a-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="9c31a-110">Exécutez l’application de lecteur de communication à distance holographique sur HoloLens 2 et vous verrez le numéro de version et l’adresse IP à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="9c31a-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="9c31a-111">V 2.4 ou version ultérieure est nécessaire pour fonctionner avec le plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="9c31a-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Capture d’écran du lecteur de communication à distance holographique s’exécutant dans HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="9c31a-113">Mode de lecture Unity avec accès distant holographique</span><span class="sxs-lookup"><span data-stu-id="9c31a-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="9c31a-114">Avec la communication à distance holographique, vous pouvez expérimenter votre application sur le HoloLens pendant qu’elle s’exécute dans l’éditeur Unity sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="9c31a-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="9c31a-115">L’entrée de pointage, de mouvement, de voix et de mappage spatial est envoyée de votre HoloLens à votre PC.</span><span class="sxs-lookup"><span data-stu-id="9c31a-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="9c31a-116">Les frames rendus sont ensuite renvoyés à votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9c31a-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="9c31a-117">C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet.</span><span class="sxs-lookup"><span data-stu-id="9c31a-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="9c31a-118">La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="9c31a-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="9c31a-119">Pour plus d’informations, consultez la documentation sur les [lecteurs de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) .</span><span class="sxs-lookup"><span data-stu-id="9c31a-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="9c31a-120">Pour de meilleurs résultats, assurez-vous que votre application définit correctement le [point de focus](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="9c31a-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="9c31a-121">Cela permet à la communication à distance holographique d’adapter au mieux votre scène à la latence de votre connexion sans fil.</span><span class="sxs-lookup"><span data-stu-id="9c31a-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c31a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c31a-122">See Also</span></span>

* [<span data-ttu-id="9c31a-123">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="9c31a-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
