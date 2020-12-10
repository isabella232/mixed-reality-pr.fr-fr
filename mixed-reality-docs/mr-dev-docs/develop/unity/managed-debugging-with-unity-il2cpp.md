---
title: Débogage managé avec Unity IL2CPP
description: Cet article explique comment exécuter un débogueur géré sur votre projet UWP IL2CPP Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, débogage, il2cpp, HoloLens, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010240"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="06de1-104">Débogage managé avec Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="06de1-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="06de1-105">Procédez comme suit pour attacher un débogueur géré à votre Build IL2CPP Unity pour HoloLens et HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="06de1-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="06de1-106">Vous devez disposer d’un réseau qui prend en charge la [multidiffusion](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="06de1-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="06de1-107">Accédez à la **section paramètres de publication UWP** , puis cochez **InternetClientServer** et **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="06de1-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Fonctionnalités des paramètres de publication UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="06de1-109">Configurer les paramètres de build UWP Unity :</span><span class="sxs-lookup"><span data-stu-id="06de1-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="06de1-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="06de1-110">Development Build</span></span>
    - <span data-ttu-id="06de1-111">Débogage des scripts</span><span class="sxs-lookup"><span data-stu-id="06de1-111">Script Debugging</span></span>
    - <span data-ttu-id="06de1-112">Attendre le débogueur managé (facultatif)</span><span class="sxs-lookup"><span data-stu-id="06de1-112">Wait for Managed Debugger (optional)</span></span>

    ![Paramètres de build UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="06de1-114">Créez dans Unity.</span><span class="sxs-lookup"><span data-stu-id="06de1-114">Build in Unity.</span></span>
5. <span data-ttu-id="06de1-115">Générez et déployez à partir de la solution Visual Studio sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="06de1-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="06de1-116">Vous devez générer avec les configurations **Debug** ou **Release** .</span><span class="sxs-lookup"><span data-stu-id="06de1-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="06de1-117">La configuration **principale** désactive le profileur Unity et peut empêcher le débogage optimal.</span><span class="sxs-lookup"><span data-stu-id="06de1-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="06de1-118">Si vous le souhaitez, vérifiez **Internet (client & Server)** et les **réseaux privés (client & Server)** dans la liste des fonctionnalités dans package. appxmanifest dans la solution.</span><span class="sxs-lookup"><span data-stu-id="06de1-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="06de1-119">Assurez-vous que votre appareil est connecté au même réseau que votre ordinateur et démarrez l’application sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="06de1-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="06de1-120">Assurez-vous que l’appareil **n’est pas** connecté à votre ordinateur via USB.</span><span class="sxs-lookup"><span data-stu-id="06de1-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="06de1-121">Double-cliquez sur l’un de vos scripts dans Unity et accédez à la solution Visual Studio qui s’ouvre pour afficher et modifier.</span><span class="sxs-lookup"><span data-stu-id="06de1-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="06de1-122">Debug-> attacher le débogueur Unity.</span><span class="sxs-lookup"><span data-stu-id="06de1-122">Debug -> Attach Unity Debugger.</span></span>

    ![Attacher le débogueur Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="06de1-124">Sélectionnez votre appareil dans la liste et cliquez sur OK pour l’attacher.</span><span class="sxs-lookup"><span data-stu-id="06de1-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Liste des appareils](images/il2cpp-debugging-machines.png)
