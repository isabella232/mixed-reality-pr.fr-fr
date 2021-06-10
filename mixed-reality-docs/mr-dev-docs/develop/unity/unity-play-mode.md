---
title: Mode Lecture Unity
description: Découvrez comment utiliser le mode lecture dans l’éditeur Unity pour afficher un aperçu des modifications apportées à votre application sur un appareil sans déployer une application.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, communication à distance, accès distant holographique, lecteur de communication à distance holographique, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, mode de lecture Unity
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547097"
---
# <a name="unity-play-mode"></a><span data-ttu-id="b48bb-104">Mode Lecture Unity</span><span class="sxs-lookup"><span data-stu-id="b48bb-104">Unity Play Mode</span></span>

<span data-ttu-id="b48bb-105">Un moyen rapide de travailler sur votre projet Unity consiste à utiliser le « mode lecture », qui exécute votre application localement dans l’éditeur Unity sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="b48bb-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="b48bb-106">Unity utilise la communication à distance holographique pour offrir un moyen rapide d’afficher un aperçu de votre contenu sur un appareil HoloLens réel.</span><span class="sxs-lookup"><span data-stu-id="b48bb-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="b48bb-107">Le mode lecture peut également être utilisé avec un casque Windows Mixed Reality attaché à votre PC de développement.</span><span class="sxs-lookup"><span data-stu-id="b48bb-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="b48bb-108">Configuration de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="b48bb-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="b48bb-109">Tout d’abord, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Microsoft Store sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b48bb-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="b48bb-110">Exécutez l’application de lecteur de communication à distance holographique sur HoloLens 2 et vous verrez le numéro de version et l’adresse IP à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="b48bb-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="b48bb-111">V 2.4 ou version ultérieure est nécessaire pour fonctionner avec le plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="b48bb-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Capture d’écran du lecteur de communication à distance holographique s’exécutant dans HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="b48bb-113">Communication à distance holographique en mode de lecture de l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="b48bb-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="b48bb-114">La création d’un projet Unity UWP dans Visual Studio Project et son empaquetage et son déploiement sur un appareil HoloLens 2 peuvent prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="b48bb-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="b48bb-115">Une solution consiste à activer la fonctionnalité de communication à distance de l’éditeur holographique, qui vous permet de déboguer votre script C# en mode « lecture » directement sur un appareil HoloLens 2 sur votre réseau.</span><span class="sxs-lookup"><span data-stu-id="b48bb-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="b48bb-116">Ce scénario évite la surcharge liée à la création et au déploiement d’un package UWP sur un appareil distant.</span><span class="sxs-lookup"><span data-stu-id="b48bb-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="b48bb-117">Suivez les étapes de la configuration de la [communication à distance holographique](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="b48bb-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="b48bb-118">Ouvrez la communication à distance de l' **éditeur Windows > XR > OpenXR**:</span><span class="sxs-lookup"><span data-stu-id="b48bb-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-features-img-02.png)

3. <span data-ttu-id="b48bb-120">Entrez l’adresse IP obtenue à partir de l’application de communication à distance holographique, puis sélectionnez **activer l’accès distant** de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b48bb-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec les fonctionnalités mises en surbrillance](images/openxr-features-img-03.png)

<span data-ttu-id="b48bb-122">Vous pouvez maintenant cliquer sur le bouton « lecture » pour lire votre application Unity dans l’application de communication à distance holographique sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b48bb-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="b48bb-123">Vous pouvez également [attacher Visual Studio à Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) pour déboguer des scripts C# en mode lecture.</span><span class="sxs-lookup"><span data-stu-id="b48bb-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="b48bb-124">À partir de la version 0.1.0, le runtime de communication à distance holographique ne prend pas en charge les ancres, et les fonctionnalités ARAnchorManager ne fonctionnent pas via la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="b48bb-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="b48bb-125">Cette fonctionnalité est disponible dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="b48bb-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="b48bb-126">Mode de lecture Unity avec accès distant holographique</span><span class="sxs-lookup"><span data-stu-id="b48bb-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="b48bb-127">Avec la communication à distance holographique, vous pouvez expérimenter votre application sur le HoloLens pendant qu’elle s’exécute dans l’éditeur Unity sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="b48bb-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="b48bb-128">L’entrée de pointage, de mouvement, de voix et de mappage spatial est envoyée de votre HoloLens à votre PC.</span><span class="sxs-lookup"><span data-stu-id="b48bb-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="b48bb-129">Les frames rendus sont ensuite renvoyés à votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b48bb-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="b48bb-130">C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet.</span><span class="sxs-lookup"><span data-stu-id="b48bb-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="b48bb-131">La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="b48bb-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="b48bb-132">Pour plus d’informations, consultez la documentation sur les [lecteurs de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) .</span><span class="sxs-lookup"><span data-stu-id="b48bb-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="b48bb-133">Pour de meilleurs résultats, assurez-vous que votre application définit correctement le [point de focus](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="b48bb-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="b48bb-134">Cela permet à la communication à distance holographique d’adapter au mieux votre scène à la latence de votre connexion sans fil.</span><span class="sxs-lookup"><span data-stu-id="b48bb-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="b48bb-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b48bb-135">See Also</span></span>

* [<span data-ttu-id="b48bb-136">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="b48bb-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
