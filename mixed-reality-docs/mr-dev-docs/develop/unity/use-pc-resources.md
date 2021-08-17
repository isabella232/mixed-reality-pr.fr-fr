---
title: Utilisez les ressources du PC pour alimenter votre application avec la communication à distance holographique
description: utilisez les ressources du PC au lieu de vous appuyer sur la puissance de traitement intégrée du HoloLens pour alimenter votre application avec la communication à distance holographique
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, réalité mixte, MRTK, réalité mixte Shared Computer Toolkit, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main, communication à distance holographique, bureau, préversion, débogage
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203838"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>Utilisez les ressources du PC pour alimenter votre application avec la communication à distance holographique

Cet article explique le cas d’usage suivant pour la communication à distance holographique :

-  **vous souhaitez que les ressources d’un PC alimentent votre application au lieu de s’appuyer sur les ressources intégrées HoloLens**: vous pouvez créer et générer une application qui dispose d’une fonctionnalité de communication à distance holographique. l’utilisateur rencontre l’application sur le HoloLens, mais l’application s’exécute sur un pc, ce qui permet à l’application de tirer parti des ressources plus puissantes du PC. Cela peut s’avérer particulièrement utile si votre application a des ressources ou des modèles haute résolution et que vous ne souhaitez pas que la fréquence d’images souffre. Nous appelons cette _application distante holographique de communication à distance_. les entrées de l’HoloLens--le point d’interrogation, le mouvement, la voix et le mappage spatial sont envoyés au PC, où le contenu est affiché dans une vue immersive virtuelle. Les frames rendus sont ensuite envoyés au HoloLens.

ce type de communication à distance holographique est également disponible pour les WMRs Windows Mixed Reality d’écouteurs immersifs (). Cela peut être utile si, par exemple, votre casque WMR est connecté à un PC sac à dos et que vous souhaitez diffuser votre application à partir d’un PC plus puissant sur le PC de sac à dos.

Pour en savoir plus sur la communication à distance holographique, consultez [vue d’ensemble de la communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Notez que vous pouvez également utiliser la communication à distance holographique si [vous souhaitez afficher un aperçu et déboguer votre application pendant le processus de développement](preview-and-debug-your-app.md).

## <a name="set-up-holographic-remoting"></a>Configurer la communication à distance holographique

pour utiliser la communication à distance holographique, vous devez installer l’application de [lecteur de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) à partir du Microsoft Store sur votre HoloLens 2. Comme expliqué ci-dessous, une fois que vous avez téléchargé et exécuté l’application, vous voyez le numéro de version et l’adresse IP auxquels vous souhaitez vous connecter. **Vous aurez besoin de v 2.4 ou version ultérieure pour pouvoir utiliser le plug-in OpenXR**.

La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi. Pour plus d’informations, consultez l’article du joueur de communication à distance holographique ci-dessus.

![Capture d’écran du lecteur de communication à distance holographique en cours d’exécution dans le HoloLens](images/openxr-features-img-01.png)

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

## <a name="migrate-from-previous-holographic-remoting-apis"></a>Migrer à partir d’API de communication à distance holographique précédentes

Pour en savoir plus sur la communication à distance holographique, consultez [vue d’ensemble de la communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-overview.md)

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
* [Afficher un aperçu et déboguer votre application avec la communication à distance holographique et le mode lecture](preview-and-debug-your-app.md)
* [Didacticiel : prise en main de la communication à distance holographique de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Didacticiel : création d’une application PC de communication à distance holographique](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
