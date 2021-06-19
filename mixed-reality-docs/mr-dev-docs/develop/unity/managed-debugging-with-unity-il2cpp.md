---
title: Débogage managé avec Unity
description: Cet article explique comment exécuter un débogueur géré sur votre projet UWP IL2CPP Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, débogage, il2cpp, HoloLens, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, UWP
ms.openlocfilehash: 48f5fbd4b2ac217a3f840117595aa36fb3d7c10e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394503"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="14c91-104">Débogage managé avec Unity</span><span class="sxs-lookup"><span data-stu-id="14c91-104">Managed debugging with Unity</span></span>

<span data-ttu-id="14c91-105">Procédez comme suit pour attacher un débogueur géré à votre Build IL2CPP Unity pour HoloLens et HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="14c91-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="14c91-106">Vous devez disposer d’un réseau qui prend en charge la [multidiffusion](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="14c91-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="14c91-107">Accédez à la **section paramètres de publication UWP** , puis cochez **InternetClientServer** et **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="14c91-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Fonctionnalités des paramètres de publication UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="14c91-109">Configurer les paramètres de build UWP Unity :</span><span class="sxs-lookup"><span data-stu-id="14c91-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="14c91-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="14c91-110">Development Build</span></span>
    - <span data-ttu-id="14c91-111">Débogage des scripts</span><span class="sxs-lookup"><span data-stu-id="14c91-111">Script Debugging</span></span>
    - <span data-ttu-id="14c91-112">Attendre le débogueur managé (facultatif)</span><span class="sxs-lookup"><span data-stu-id="14c91-112">Wait for Managed Debugger (optional)</span></span>

    ![Paramètres de build UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="14c91-114">Créez dans Unity.</span><span class="sxs-lookup"><span data-stu-id="14c91-114">Build in Unity.</span></span>
5. <span data-ttu-id="14c91-115">Générez et déployez à partir de la solution Visual Studio sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="14c91-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="14c91-116">Vous devez générer avec les configurations **Debug** ou **Release** .</span><span class="sxs-lookup"><span data-stu-id="14c91-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="14c91-117">La configuration **principale** désactive le profileur Unity et peut empêcher le débogage optimal.</span><span class="sxs-lookup"><span data-stu-id="14c91-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="14c91-118">Si vous le souhaitez, vérifiez **Internet (client & Server)** et les **réseaux privés (client & Server)** dans la liste des fonctionnalités dans package. appxmanifest dans la solution.</span><span class="sxs-lookup"><span data-stu-id="14c91-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="14c91-119">Assurez-vous que votre appareil est connecté au même réseau que votre ordinateur et démarrez l’application sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="14c91-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="14c91-120">Assurez-vous que l’appareil **n’est pas** connecté à votre ordinateur via USB.</span><span class="sxs-lookup"><span data-stu-id="14c91-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="14c91-121">Double-cliquez sur l’un de vos scripts dans Unity et accédez à la solution Visual Studio qui s’ouvre pour afficher et modifier.</span><span class="sxs-lookup"><span data-stu-id="14c91-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="14c91-122">Debug-> attacher le débogueur Unity.</span><span class="sxs-lookup"><span data-stu-id="14c91-122">Debug -> Attach Unity Debugger.</span></span>

    ![Attacher le débogueur Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="14c91-124">Sélectionnez votre appareil dans la liste et cliquez sur OK pour l’attacher.</span><span class="sxs-lookup"><span data-stu-id="14c91-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Liste des appareils](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a><span data-ttu-id="14c91-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14c91-126">See also</span></span> 

* [<span data-ttu-id="14c91-127">Débogage C#</span><span class="sxs-lookup"><span data-stu-id="14c91-127">C# debugging</span></span>](/visualstudio/get-started/csharp/tutorial-debugger)
