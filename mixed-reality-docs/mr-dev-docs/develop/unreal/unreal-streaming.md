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
ms.openlocfilehash: 4b3be99f699c7c1d40d3ea98aacecde6f60e4d2db759448f84c820a43d89bb0a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218854"
---
# <a name="streaming-in-unreal"></a>Streaming dans Unreal

Le streaming à partir d’un PC vers HoloLens offre deux avantages majeurs : 
* Il permet à votre application de réalité mixte de tirer parti de la puissance de calcul de vos PC. 
* Il permet d’accélérer l’itération du développement. 

Pour commencer, vous devez télécharger [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) sur votre appareil HoloLens. Holographic Remoting Player permet à votre application de diffuser directement sur le lecteur de communication à distance sur votre HoloLens à partir des sources suivantes :

* L’éditeur Unreal Engine
* Un exécutable Windows empaqueté 

Lors du streaming, vous avez accès à presque toutes les mêmes fonctionnalités HoloLens que lors de l’exécution d’une application sur un appareil. Cela comprend notamment le [suivi de la main](unreal-hand-tracking.md) si vous êtes sur un HoloLens 2, le [mappage spatial](unreal-spatial-mapping.md) et les [ancres spatiales](unreal-spatial-anchors.md), mais pas les fonctionnalités mentionnées dans cette [liste](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md). 

> [!NOTE]
> * La qualité de streaming dépend fortement de la puissance de votre réseau Wi-Fi.
> * Toutes les fonctionnalités sont automatiquement activées pour le lecteur de communication à distance holographique. Si vous trouvez une fonctionnalité qui nécessite l’autorisation de l’utilisateur (par exemple le suivi oculaire) à utiliser sur le streaming mais pas lors de l’exécution sur l’appareil, vérifiez que vous avez activé les fonctionnalités appropriées dans les paramètres de votre projet.

### <a name="streaming-limitations"></a>Limitations de streaming

Les maillages de la main, la caméra HoloLens et le clavier système ne sont pas disponibles en streaming. Notez que les entrées vocales pour les applications envoyées en streaming peuvent être obtenues via le microphone du PC à partir duquel vous procédez au streaming.

#### <a name="openxr"></a>OpenXR

Unreal 4.26 exécuté sur OpenXR prend en charge le streaming vers les versions 2.4.0+ du lecteur Holographic Remoting Player. Le streaming OpenXR dans 2.4.0 ne prend pas en charge le mappage spatial ni les ancres spatiales. 

## <a name="device-support"></a>Prise en charge des appareils

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Source</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens première génération</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Casques immersifs</strong></td>
    </tr>
     <tr>
        <td>Éditeur Unreal</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Package Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming à partir de l’éditeur Unreal

En tant que développeur, vous constaterez que le streaming de l’éditeur Unreal vers votre appareil HoloLens offre de considérables avantages lors des tests ; en effet, vous n’avez plus besoin d’attendre que votre application soit générée et déployée avant d’essayer vos mises à jour.

Vous trouverez des instructions détaillées pour le [streaming à partir de l’éditeur Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) dans notre série de tutoriels.

## <a name="streaming-from-a-packaged-windows-executable"></a>Streaming à partir d’un exécutable Windows empaqueté

Dans Unreal 4.25.1 et versions ultérieures, vous pouvez diffuser votre application sur un appareil HoloLens 2 à partir d’un fichier exécutable Windows empaqueté : 

1. Accédez à **File > Package Project > Windows** dans le menu de l’éditeur. 
    * Choisissez un emplacement où enregistrer votre package, puis sélectionnez **Select Folder** (Sélectionner un dossier).

2. Une fois la génération du package terminée, ouvrez **Holographic Remoting Player** sur votre HoloLens 2 et prenez note de l’adresse IP. 
3. Laissez **Holographic Remoting Player** ouvert et utilisez l’invite de ligne de commande pour : 
    * Basculer vers le répertoire local où vous avez enregistré votre package.
    * Entrez la commande suivante : `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`

> [!NOTE]
> Le nom de l’application dans les paramètres de votre projet doit être utilisé automatiquement pour créer le package Windows. Si les noms diffèrent pour une raison ou une autre, utilisez le nom de l’exécutable Windows à l’invite de commandes.

Appuyez sur Entrée ; le streaming de votre application commence.

### <a name="command-line-options"></a>Options de ligne de commande

Vous trouverez dans le tableau ci-dessous d’autres options de ligne de commande pour le streaming à partir de chaque plateforme dans Unreal Engine 4.26+. 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a>Voir aussi

* [Historique des versions de la communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [Écriture d’une application de lecteur de communication à distance holographique personnalisée](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [Établissement d’une connexion sécurisée avec la communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)