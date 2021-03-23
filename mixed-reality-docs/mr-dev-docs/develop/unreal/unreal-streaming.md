---
title: Streaming dans Unreal
description: Découvrez comment diffuser en continu vos applications Unreal vers HoloLens 2, y compris les limitations et les options de ligne de commande pour le streaming.
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, streaming, PC, application de communication à distance holographique, holographic remoting player, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: bbae1170850ec4bbb41bc9274223d19102adddae
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98580332"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="848a5-104">Streaming dans Unreal</span><span class="sxs-lookup"><span data-stu-id="848a5-104">Streaming in Unreal</span></span>

<span data-ttu-id="848a5-105">Le streaming à partir d’un PC vers HoloLens offre deux avantages majeurs :</span><span class="sxs-lookup"><span data-stu-id="848a5-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="848a5-106">Il permet à votre application de réalité mixte de tirer parti de la puissance de calcul de vos PC.</span><span class="sxs-lookup"><span data-stu-id="848a5-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="848a5-107">Il permet d’accélérer l’itération du développement.</span><span class="sxs-lookup"><span data-stu-id="848a5-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="848a5-108">Pour commencer, vous devez télécharger [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) sur votre appareil HoloLens.</span><span class="sxs-lookup"><span data-stu-id="848a5-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="848a5-109">Holographic Remoting Player permet à votre application de diffuser directement sur le lecteur de communication à distance sur votre HoloLens à partir des sources suivantes :</span><span class="sxs-lookup"><span data-stu-id="848a5-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="848a5-110">L’éditeur Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="848a5-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="848a5-111">Un exécutable Windows empaqueté</span><span class="sxs-lookup"><span data-stu-id="848a5-111">A packaged Windows executable</span></span> 

<span data-ttu-id="848a5-112">Lors du streaming, vous avez accès à presque toutes les mêmes fonctionnalités HoloLens que lors de l’exécution d’une application sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="848a5-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="848a5-113">Cela comprend notamment le [suivi de la main](unreal-hand-tracking.md) si vous êtes sur un HoloLens 2, le [mappage spatial](unreal-spatial-mapping.md) et les [ancres spatiales](unreal-spatial-anchors.md), mais pas les fonctionnalités mentionnées dans cette [liste](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="848a5-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="848a5-114">La qualité de streaming dépend fortement de la puissance de votre réseau Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="848a5-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="848a5-115">Toutes les fonctionnalités sont automatiquement activées pour le lecteur de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="848a5-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="848a5-116">Si vous trouvez une fonctionnalité qui nécessite l’autorisation de l’utilisateur (par exemple le suivi oculaire) à utiliser sur le streaming mais pas lors de l’exécution sur l’appareil, vérifiez que vous avez activé les fonctionnalités appropriées dans les paramètres de votre projet.</span><span class="sxs-lookup"><span data-stu-id="848a5-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="848a5-117">Limitations de streaming</span><span class="sxs-lookup"><span data-stu-id="848a5-117">Streaming limitations</span></span>

<span data-ttu-id="848a5-118">Les maillages de la main, la caméra HoloLens et le clavier système ne sont pas disponibles en streaming.</span><span class="sxs-lookup"><span data-stu-id="848a5-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="848a5-119">Notez que les entrées vocales pour les applications envoyées en streaming peuvent être obtenues via le microphone du PC à partir duquel vous procédez au streaming.</span><span class="sxs-lookup"><span data-stu-id="848a5-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="848a5-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="848a5-120">OpenXR</span></span>

<span data-ttu-id="848a5-121">Unreal 4.26 exécuté sur OpenXR prend en charge le streaming vers les versions 2.4.0+ du lecteur Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="848a5-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="848a5-122">Le streaming OpenXR dans 2.4.0 ne prend pas en charge le mappage spatial ni les ancres spatiales.</span><span class="sxs-lookup"><span data-stu-id="848a5-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="848a5-123">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="848a5-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="848a5-124"><strong>Source</strong></span><span class="sxs-lookup"><span data-stu-id="848a5-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="848a5-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens première génération</strong></a></span><span class="sxs-lookup"><span data-stu-id="848a5-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="848a5-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="848a5-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="848a5-127"><strong>Casques immersifs</strong></span><span class="sxs-lookup"><span data-stu-id="848a5-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="848a5-128">Éditeur Unreal</span><span class="sxs-lookup"><span data-stu-id="848a5-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="848a5-129">✔️</span><span class="sxs-lookup"><span data-stu-id="848a5-129">✔️</span></span></td>
        <td><span data-ttu-id="848a5-130">✔️</span><span class="sxs-lookup"><span data-stu-id="848a5-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="848a5-131">Package Windows</span><span class="sxs-lookup"><span data-stu-id="848a5-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="848a5-132">✔️</span><span class="sxs-lookup"><span data-stu-id="848a5-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="848a5-133">Streaming à partir de l’éditeur Unreal</span><span class="sxs-lookup"><span data-stu-id="848a5-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="848a5-134">En tant que développeur, vous constaterez que le streaming de l’éditeur Unreal vers votre appareil HoloLens offre de considérables avantages lors des tests ; en effet, vous n’avez plus besoin d’attendre que votre application soit générée et déployée avant d’essayer vos mises à jour.</span><span class="sxs-lookup"><span data-stu-id="848a5-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="848a5-135">Vous trouverez des instructions détaillées pour le [streaming à partir de l’éditeur Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) dans notre série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="848a5-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="848a5-136">Streaming à partir d’un exécutable Windows empaqueté</span><span class="sxs-lookup"><span data-stu-id="848a5-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="848a5-137">Dans Unreal 4.25.1 et versions ultérieures, vous pouvez diffuser votre application sur un appareil HoloLens 2 à partir d’un fichier exécutable Windows empaqueté :</span><span class="sxs-lookup"><span data-stu-id="848a5-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="848a5-138">Accédez à **File > Package Project > Windows** dans le menu de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="848a5-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="848a5-139">Choisissez un emplacement où enregistrer votre package, puis sélectionnez **Select Folder** (Sélectionner un dossier).</span><span class="sxs-lookup"><span data-stu-id="848a5-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="848a5-140">Une fois la génération du package terminée, ouvrez **Holographic Remoting Player** sur votre HoloLens 2 et prenez note de l’adresse IP.</span><span class="sxs-lookup"><span data-stu-id="848a5-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="848a5-141">Laissez **Holographic Remoting Player** ouvert et utilisez l’invite de ligne de commande pour :</span><span class="sxs-lookup"><span data-stu-id="848a5-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="848a5-142">Basculer vers le répertoire local où vous avez enregistré votre package.</span><span class="sxs-lookup"><span data-stu-id="848a5-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="848a5-143">Entrez la commande suivante : `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="848a5-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="848a5-144">Le nom de l’application dans les paramètres de votre projet doit être utilisé automatiquement pour créer le package Windows.</span><span class="sxs-lookup"><span data-stu-id="848a5-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="848a5-145">Si les noms diffèrent pour une raison ou une autre, utilisez le nom de l’exécutable Windows à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="848a5-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="848a5-146">Appuyez sur Entrée ; le streaming de votre application commence.</span><span class="sxs-lookup"><span data-stu-id="848a5-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="848a5-147">Options de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="848a5-147">Command line options</span></span>

<span data-ttu-id="848a5-148">Vous trouverez dans le tableau ci-dessous d’autres options de ligne de commande pour le streaming à partir de chaque plateforme dans Unreal Engine 4.26+.</span><span class="sxs-lookup"><span data-stu-id="848a5-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="848a5-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="848a5-149">See also</span></span>

* [<span data-ttu-id="848a5-150">Historique des versions de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="848a5-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="848a5-151">Écriture d’une application de lecteur de communication à distance holographique personnalisée</span><span class="sxs-lookup"><span data-stu-id="848a5-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="848a5-152">Établissement d’une connexion sécurisée avec la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="848a5-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)