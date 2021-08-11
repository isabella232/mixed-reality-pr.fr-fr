---
title: Communication à distance holographique dans Unity
description: Découvrez comment utiliser la communication à distance holographique dans une application de bureau et le mode de lecture Unity avec OpenXR.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, réalité mixte, MRTK, réalité mixte Shared Computer Toolkit, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, mise en route, communication à distance holographique, bureau
ms.openlocfilehash: 0b18bf4a187190da3ef9d17fd87f2c42feaa271210345330887ce618b49a0442
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192191"
---
# <a name="holographic-remoting-in-unity"></a>Communication à distance holographique dans Unity

> [!NOTE]
> Windows La prise en charge de l’accès distant des applications autonomes a été ajoutée à la version du package 0.1.3.
> À partir de la version 0.1.3, cette fonctionnalité ne prend pas en charge les builds UWP.

[Apprenez les bases de la communication à distance holographique.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

vous pouvez utiliser la communication à distance holographique pour diffuser du contenu holographique vers votre HoloLens 2 en temps réel. C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet. 

Avant de commencer, il est important de comprendre vos deux options principales dans Unity :
* **Communication à distance holographique en mode de lecture Unity**: exécutez votre application localement dans l’éditeur Unity sur votre ordinateur en mode lecture pour offrir un moyen rapide d’afficher un aperçu de votre contenu sur un HoloLens 2. le Mode lecture peut également être utilisé avec un Windows Mixed Reality casque attaché à votre PC de développement.
* **Communication à distance holographique à partir d’un fichier de build Unity**: exécutez votre application à partir d’une application distante holographique d’Unity que vous avez exportée sur votre bureau vers votre HoloLens 2. Cela peut être utile si votre application a des ressources ou des modèles haute résolution. le processeur graphique de votre ordinateur de bureau gère le rendu avant qu’il n’ait été reHoloLens 2.

## <a name="holographic-remoting-setup"></a>Configuration de la communication à distance holographique

quel que soit l’itinéraire utilisé avec la communication à distance holographique, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Microsoft Store sur votre HoloLens 2.

une fois le téléchargement terminé, exécutez l’application de lecteur de communication à distance holographique sur votre HoloLens 2 et vous verrez le numéro de version et l’adresse IP auxquels vous souhaitez vous connecter. **Vous aurez besoin de v 2.4 ou version ultérieure pour pouvoir utiliser le plug-in OpenXR**.

![Capture d’écran du lecteur de communication à distance holographique en cours d’exécution dans le HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Mode de lecture Unity avec accès distant holographique

[!INCLUDE[](includes/unity-play-mode.md)]

La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi. Pour plus d’informations, consultez la documentation sur les [lecteurs de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Pour de meilleurs résultats, assurez-vous que votre application définit correctement le [point de focus](focus-point-in-unity.md). Cela permet à la communication à distance holographique d’adapter votre scène à la latence de votre connexion sans fil.

## <a name="holographic-remoting-from-a-remote-application"></a>Communication à distance holographique à partir d’une application distante

1. dans la barre de menus, sélectionnez **modifier > Project Paramètres**.
1. Dans la colonne de gauche, sélectionnez **gestion du plug-in XR**.
1. dans la section **gestion du Plug-in XR** , sélectionnez **Microsoft HoloLens groupe de fonctionnalités** et groupe de fonctionnalités d' **application distante d’accès distant holographique**.
1. Désélectionnez **Initialize XR au démarrage**:

    ![Capture d’écran du panneau Paramètres du projet ouvrir dans l’éditeur Unity avec l’option initialiser XR au démarrage désactivée](images/001-openxr-features.png)

1. Écrivez du code pour définir la configuration de communication à distance et déclencher l’initialisation XR. L’exemple d’application distribué avec le [plug-in OpenXR de réalité mixte](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) contient AppRemoting. cs, qui montre un exemple de scénario de connexion à une adresse IP spécifique au moment de l’exécution. À ce stade, le déploiement de l’exemple d’application sur un ordinateur local affiche un champ d’entrée d’adresse IP avec un bouton de connexion. si vous tapez une adresse IP et cliquez sur Connecter initialisez XR et tentez de vous connecter à l’appareil cible :

    ![Capture d’écran de l’exemple d’application affichant un exemple d’interface utilisateur de communication à distance d’application](images/openxr-sample-app-remoting.png)

1. Pour écrire du code de connexion personnalisé, appelez `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` avec un rempli `RemotingConfiguration` . L’exemple d’application l’expose dans l’inspecteur et montre comment renseigner l’adresse IP à partir d’un champ de texte. L’appel de `Connect` va définir la configuration et initialiser automatiquement XR, c’est pourquoi il doit être appelé en tant que Coroutine :

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Lors de l’exécution de, vous pouvez obtenir l’état actuel de la connexion avec l' `AppRemoting.TryGetConnectionState` API et éventuellement déconnecter et déinitialiser XR à l’aide de `AppRemoting.Disconnect()` . Cela peut être utilisé pour se déconnecter et se reconnecter à un autre périphérique au cours de la même session d’application. L’exemple d’application fournit un cube tappable qui déconnecte la session de communication à distance si elle est exploitée.

### <a name="migration-from-previous-apis"></a>Migration à partir des API précédentes

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. WSA. HolographicRemoting

À partir de l’exemple de code sur les [documents Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):

| XR. WSA. HolographicRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A : se produit automatiquement lors de l’appel de `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. WindowsMR. WindowsMRRemoting

| XR. WindowsMR.WindowsMRRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` et `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Passé `AppRemoting.Connect` par le biais du `RemotingConfiguration` struct |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="see-also"></a>Voir aussi

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Didacticiel : prise en main de la communication à distance holographique de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Didacticiel : création d’une application PC de communication à distance holographique](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
