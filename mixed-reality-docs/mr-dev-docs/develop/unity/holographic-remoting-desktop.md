---
title: Communication à distance holographique dans une application de bureau
description: Découvrez comment utiliser la communication à distance holographique dans une application de bureau avec OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main, communication à distance holographique, Bureau
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624318"
---
# <a name="holographic-remoting-in-desktop-app"></a>Communication à distance holographique dans une application de bureau

> [!NOTE]
> La prise en charge de l’accès distant aux applications autonomes Windows a été ajoutée dans la version du package 0.1.3.
> À partir de la version 0.1.3, cette fonctionnalité ne prend pas en charge les builds UWP.

1. Suivez les étapes de la configuration de la [communication à distance holographique](openxr-supported-features.md#holographic-remoting-setup)
2. Ouvrez les **paramètres du projet de modification >**, accédez à **gestion du plug-in XR**, puis cochez la case **Windows Mixed Reality Feature Set** . Désactivez également **l’option initialiser XR au démarrage**:

    ![Capture d’écran du panneau Paramètres du projet ouvrir dans l’éditeur Unity avec l’option initialiser XR au démarrage désactivée](images/openxr-features-img-02-app.png)

3. Développez la section **fonctionnalités** sous **OpenXR** et sélectionnez **Afficher tout** .
4. Cochez la case **accès distant aux applications holographiques** :

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec l’accès distant à l’application activé](images/openxr-features-img-03-app.png)

5. Ensuite, écrivez du code pour définir la configuration de communication à distance et déclencher l’initialisation XR. L’exemple d’application distribué avec le [plug-in OpenXR de réalité mixte](openxr-getting-started.md#hololens-2-samples) contient AppRemoting.cs, qui montre un exemple de scénario de connexion à une adresse IP spécifique au moment de l’exécution. À ce stade, le déploiement de l’exemple d’application sur un ordinateur local affiche un champ d’entrée d’adresse IP avec un bouton de connexion. Tapez une adresse IP et cliquez sur connecter pour initialiser XR et tenter de vous connecter à l’appareil cible :

    ![Capture d’écran de l’exemple d’application affichant un exemple d’interface utilisateur de communication à distance d’application](images/openxr-sample-app-remoting.png)

6. Pour écrire du code de connexion personnalisé, appelez `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` avec un rempli `RemotingConfiguration` . L’exemple d’application l’expose dans l’inspecteur et montre comment renseigner l’adresse IP à partir d’un champ de texte. L’appel de `Connect` va définir la configuration et initialiser automatiquement XR, c’est pourquoi il doit être appelé en tant que Coroutine :

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Lors de l’exécution de, vous pouvez obtenir l’état actuel de la connexion avec l' `AppRemoting.TryGetConnectionState` API et éventuellement déconnecter et déinitialiser XR à l’aide de `AppRemoting.Disconnect()` . Cela peut être utilisé pour se déconnecter et se reconnecter à un autre périphérique au cours de la même session d’application. L’exemple d’application fournit un cube tappable qui déconnecte la session de communication à distance si elle est exploitée.

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