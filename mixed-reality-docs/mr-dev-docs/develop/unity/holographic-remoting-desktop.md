---
title: Communication à distance holographique dans une application de bureau
description: Découvrez comment utiliser la communication à distance holographique dans une application de bureau avec OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main, communication à distance holographique, Bureau
ms.openlocfilehash: 18557af1f08ea05715b92b5072460871bb05a329
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333413"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="26f8c-104">Communication à distance holographique dans une application de bureau</span><span class="sxs-lookup"><span data-stu-id="26f8c-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="26f8c-105">La prise en charge de l’accès distant aux applications autonomes Windows a été ajoutée dans la version du package 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="26f8c-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="26f8c-106">À partir de la version 0.1.3, cette fonctionnalité ne prend pas en charge les builds UWP.</span><span class="sxs-lookup"><span data-stu-id="26f8c-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="26f8c-107">Suivez les étapes de la configuration de la [communication à distance holographique](unity-play-mode.md#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="26f8c-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="26f8c-108">Ouvrez les **paramètres du projet de modification >**, accédez à **gestion du plug-in XR**, puis cochez la case **Windows Mixed Reality Feature Set** .</span><span class="sxs-lookup"><span data-stu-id="26f8c-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="26f8c-109">Désactivez également **l’option initialiser XR au démarrage**:</span><span class="sxs-lookup"><span data-stu-id="26f8c-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Capture d’écran du panneau Paramètres du projet ouvrir dans l’éditeur Unity avec l’option initialiser XR au démarrage désactivée](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="26f8c-111">Développez la section **fonctionnalités** sous **OpenXR** et sélectionnez **Afficher tout** .</span><span class="sxs-lookup"><span data-stu-id="26f8c-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="26f8c-112">Cochez la case **accès distant aux applications holographiques** :</span><span class="sxs-lookup"><span data-stu-id="26f8c-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec l’accès distant à l’application activé](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="26f8c-114">Ensuite, écrivez du code pour définir la configuration de communication à distance et déclencher l’initialisation XR.</span><span class="sxs-lookup"><span data-stu-id="26f8c-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="26f8c-115">L’exemple d’application distribué avec le [plug-in OpenXR de réalité mixte](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contient AppRemoting. cs, qui montre un exemple de scénario de connexion à une adresse IP spécifique au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="26f8c-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="26f8c-116">À ce stade, le déploiement de l’exemple d’application sur un ordinateur local affiche un champ d’entrée d’adresse IP avec un bouton de connexion.</span><span class="sxs-lookup"><span data-stu-id="26f8c-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="26f8c-117">Tapez une adresse IP et cliquez sur connecter pour initialiser XR et tenter de vous connecter à l’appareil cible :</span><span class="sxs-lookup"><span data-stu-id="26f8c-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Capture d’écran de l’exemple d’application affichant un exemple d’interface utilisateur de communication à distance d’application](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="26f8c-119">Pour écrire du code de connexion personnalisé, appelez `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` avec un rempli `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="26f8c-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="26f8c-120">L’exemple d’application l’expose dans l’inspecteur et montre comment renseigner l’adresse IP à partir d’un champ de texte.</span><span class="sxs-lookup"><span data-stu-id="26f8c-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="26f8c-121">L’appel de `Connect` va définir la configuration et initialiser automatiquement XR, c’est pourquoi il doit être appelé en tant que Coroutine :</span><span class="sxs-lookup"><span data-stu-id="26f8c-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="26f8c-122">Lors de l’exécution de, vous pouvez obtenir l’état actuel de la connexion avec l' `AppRemoting.TryGetConnectionState` API et éventuellement déconnecter et déinitialiser XR à l’aide de `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="26f8c-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="26f8c-123">Cela peut être utilisé pour se déconnecter et se reconnecter à un autre périphérique au cours de la même session d’application.</span><span class="sxs-lookup"><span data-stu-id="26f8c-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="26f8c-124">L’exemple d’application fournit un cube tappable qui déconnecte la session de communication à distance si elle est exploitée.</span><span class="sxs-lookup"><span data-stu-id="26f8c-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="26f8c-125">Migration à partir des API précédentes</span><span class="sxs-lookup"><span data-stu-id="26f8c-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="26f8c-126">UnityEngine. XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="26f8c-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="26f8c-127">À partir de l’exemple de code sur les [documents Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="26f8c-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="26f8c-128">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="26f8c-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="26f8c-129">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="26f8c-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="26f8c-130">[N/A : se produit automatiquement lors de l’appel de `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="26f8c-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="26f8c-131">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="26f8c-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="26f8c-132">XR. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="26f8c-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="26f8c-133">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="26f8c-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="26f8c-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` et `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="26f8c-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="26f8c-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="26f8c-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="26f8c-136">Passé `AppRemoting.Connect` par le biais du `RemotingConfiguration` struct</span><span class="sxs-lookup"><span data-stu-id="26f8c-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`