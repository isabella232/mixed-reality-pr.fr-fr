---
title: Streaming dans Unreal
description: Guide de streaming dans Unreal vers HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, streaming, PC, application de communication à distance holographique, holographic remoting player, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 9cbde33ce7238d704d4b24b4afbed9d8306d4e4d
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609330"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="6aaae-104">Streaming dans Unreal</span><span class="sxs-lookup"><span data-stu-id="6aaae-104">Streaming in Unreal</span></span>

<span data-ttu-id="6aaae-105">Le streaming à partir d’un PC vers HoloLens offre deux avantages majeurs :</span><span class="sxs-lookup"><span data-stu-id="6aaae-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="6aaae-106">Il permet à votre application de réalité mixte de tirer parti de la puissance de calcul de vos PC.</span><span class="sxs-lookup"><span data-stu-id="6aaae-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="6aaae-107">Il permet d’accélérer l’itération du développement.</span><span class="sxs-lookup"><span data-stu-id="6aaae-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="6aaae-108">Pour commencer, vous devez télécharger [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) sur votre appareil HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6aaae-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="6aaae-109">Holographic Remoting Player permet à votre application de diffuser directement sur le lecteur de communication à distance sur votre HoloLens à partir des sources suivantes :</span><span class="sxs-lookup"><span data-stu-id="6aaae-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="6aaae-110">L’éditeur Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="6aaae-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="6aaae-111">Un exécutable Windows empaqueté</span><span class="sxs-lookup"><span data-stu-id="6aaae-111">A packaged Windows executable</span></span> 

<span data-ttu-id="6aaae-112">Lors du streaming, vous avez accès à presque toutes les mêmes fonctionnalités HoloLens que lors de l’exécution d’une application sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="6aaae-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="6aaae-113">Cela comprend notamment le [suivi de la main](unreal-hand-tracking.md) si vous êtes sur un HoloLens 2, le [mappage spatial](unreal-spatial-mapping.md) et les [ancres spatiales](unreal-spatial-anchors.md), mais pas les fonctionnalités mentionnées dans cette [liste](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="6aaae-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="6aaae-114">La qualité de streaming dépend fortement de la puissance de votre réseau Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="6aaae-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="6aaae-115">Toutes les fonctionnalités sont automatiquement activées pour le lecteur de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="6aaae-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="6aaae-116">Si vous trouvez une fonctionnalité qui nécessite l’autorisation de l’utilisateur (par exemple le suivi oculaire) à utiliser sur le streaming mais pas lors de l’exécution sur l’appareil, vérifiez que vous avez activé les fonctionnalités appropriées dans les paramètres de votre projet.</span><span class="sxs-lookup"><span data-stu-id="6aaae-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="6aaae-117">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="6aaae-117">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6aaae-118"><strong>Source</strong></span><span class="sxs-lookup"><span data-stu-id="6aaae-118"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="6aaae-119"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens première génération</strong></a></span><span class="sxs-lookup"><span data-stu-id="6aaae-119"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="6aaae-120"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="6aaae-120"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="6aaae-121"><strong>Casques immersifs</strong></span><span class="sxs-lookup"><span data-stu-id="6aaae-121"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6aaae-122">Éditeur Unreal</span><span class="sxs-lookup"><span data-stu-id="6aaae-122">Unreal editor</span></span></td>
        <td><span data-ttu-id="6aaae-123">✔️</span><span class="sxs-lookup"><span data-stu-id="6aaae-123">✔️</span></span></td>
        <td><span data-ttu-id="6aaae-124">✔️</span><span class="sxs-lookup"><span data-stu-id="6aaae-124">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="6aaae-125">Package Windows</span><span class="sxs-lookup"><span data-stu-id="6aaae-125">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6aaae-126">✔️</span><span class="sxs-lookup"><span data-stu-id="6aaae-126">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="6aaae-127">Streaming à partir de l’éditeur Unreal</span><span class="sxs-lookup"><span data-stu-id="6aaae-127">Streaming from the Unreal editor</span></span>

<span data-ttu-id="6aaae-128">En tant que développeur, vous constaterez que le streaming de l’éditeur Unreal vers votre appareil HoloLens offre de considérables avantages lors des tests ; en effet, vous n’avez plus besoin d’attendre que votre application soit générée et déployée avant d’essayer vos mises à jour.</span><span class="sxs-lookup"><span data-stu-id="6aaae-128">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="6aaae-129">Vous trouverez des instructions détaillées pour le [streaming à partir de l’éditeur Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) dans notre série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="6aaae-129">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="6aaae-130">Streaming à partir d’un exécutable Windows empaqueté</span><span class="sxs-lookup"><span data-stu-id="6aaae-130">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="6aaae-131">Dans Unreal 4.25.1 et versions ultérieures, vous pouvez diffuser votre application sur un appareil HoloLens 2 à partir d’un fichier exécutable Windows empaqueté :</span><span class="sxs-lookup"><span data-stu-id="6aaae-131">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="6aaae-132">Accédez à **File > Package Project > Windows** dans le menu de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="6aaae-132">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="6aaae-133">Choisissez un emplacement où enregistrer votre package, puis sélectionnez **Select Folder** (Sélectionner un dossier).</span><span class="sxs-lookup"><span data-stu-id="6aaae-133">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="6aaae-134">Une fois la génération du package terminée, ouvrez **Holographic Remoting Player** sur votre HoloLens 2 et prenez note de l’adresse IP.</span><span class="sxs-lookup"><span data-stu-id="6aaae-134">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="6aaae-135">Laissez **Holographic Remoting Player** ouvert et utilisez l’invite de ligne de commande pour :</span><span class="sxs-lookup"><span data-stu-id="6aaae-135">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="6aaae-136">Basculer vers le répertoire local où vous avez enregistré votre package.</span><span class="sxs-lookup"><span data-stu-id="6aaae-136">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="6aaae-137">Entrez la commande suivante : ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="6aaae-137">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="6aaae-138">Le nom de l’application dans les paramètres de votre projet doit être utilisé automatiquement pour créer le package Windows.</span><span class="sxs-lookup"><span data-stu-id="6aaae-138">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="6aaae-139">Si les noms diffèrent pour une raison ou une autre, utilisez le nom de l’exécutable Windows à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6aaae-139">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="6aaae-140">Appuyez sur Entrée ; le streaming de votre application commence.</span><span class="sxs-lookup"><span data-stu-id="6aaae-140">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="6aaae-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aaae-141">See also</span></span>

* [<span data-ttu-id="6aaae-142">Historique des versions de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="6aaae-142">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="6aaae-143">Écriture d’une application de lecteur de communication à distance holographique personnalisée</span><span class="sxs-lookup"><span data-stu-id="6aaae-143">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="6aaae-144">Établissement d’une connexion sécurisée avec la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="6aaae-144">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
