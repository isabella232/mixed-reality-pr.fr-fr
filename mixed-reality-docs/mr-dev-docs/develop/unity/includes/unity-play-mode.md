---
ms.openlocfilehash: f579cb73389d23be5959d212d4243361f00a27b8475ce74a16acc2bffa7a192b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192180"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. sur votre HoloLens, accédez à la **Microsoft Store** et installez l’application de **[lecteur de communication à distance holographique](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. sur votre HoloLens, démarrez l’application de **lecteur de communication à distance holographique** .
1. dans unity, accédez au menu **edition** , puis sélectionnez **Project Paramètres**.
1. Sélectionnez **gestion du plug-in XR**.
1. vérifiez que l’onglet **autonome Windows** est sélectionné, recherchez **OpenXR** et **Windows Mixed Reality ensemble de fonctionnalités** dans la liste, puis cochez les cases correspondantes.
1. Ensuite, accédez au menu **fenêtre** , développez le sous-menu **XR** , puis sélectionnez la communication à distance de l' **éditeur OpenXR**.

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../images/openxr-features-img-02.png)

1. Cliquez sur **activer l’accès distant** de l’éditeur.

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec les fonctionnalités mises en surbrillance](../images/openxr-features-img-03.png)

1. Si le bouton **activer les dépendances manquantes** s’affiche, cliquez sur également. La zone d’erreur au-dessus du bouton décrit les fonctionnalités qu’elle active et pourquoi.
1. Pour **nom d’hôte distant**, entrez l’adresse IP de votre HoloLens.
   1. Modifiez les autres paramètres en fonction des besoins.
   1. L’éditeur essaiera de se connecter une fois que le mode de lecture est démarré.
1. Sélectionnez le bouton de **lecture** pour démarrer le mode lecture et tester l’application sur votre HoloLens. pour déboguer des scripts C# en mode lecture, [attachez Visual Studio à unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

> [!NOTE]
> À partir de la version 0.1.0, le runtime de communication à distance holographique ne prend pas en charge les ancres, et les fonctionnalités ARAnchorManager ne fonctionnent pas via la communication à distance.  Cette fonctionnalité est disponible dans les versions ultérieures.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

1. sur votre HoloLens, accédez à la **Microsoft Store** et installez l’application de **[lecteur de communication à distance holographique](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. sur votre HoloLens, démarrez l’application de **lecteur de communication à distance holographique** .
1. dans unity, accédez au menu **edition** , puis sélectionnez **Project Paramètres**.
1. Sélectionnez **gestion du plug-in XR**.
1. vérifiez que l’onglet **PC, Mac & Linux autonome** est sélectionné, recherchez **Windows Mixed Reality** dans la liste et cochez sa case.
1. ensuite, accédez au menu **fenêtre** , développez le sous-menu **XR** , puis sélectionnez **Windows la communication à distance du plug-in XR**.
1. Définissez le **mode d’émulation** à **distant sur appareil**.
1. Pour **ordinateur distant**, entrez l’adresse IP de votre HoloLens.
1. Pour vous connecter, effectuez l’une des opérations suivantes :
   1. pour vous connecter manuellement, désactivez la case à cocher **Connecter en lecture**, puis sélectionnez **Connecter**. Vous devez voir l’état de la **connexion** basculer sur **connecté** et voir l’écran vide dans le HoloLens.
   1. pour vous connecter automatiquement, cochez **Connecter**. L’éditeur essaiera de se connecter une fois que le mode de lecture est démarré.
1. Sélectionnez le bouton de **lecture** pour démarrer le mode lecture et tester l’application sur votre HoloLens. pour déboguer des scripts C# en mode lecture, [attachez Visual Studio à unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

1. sur votre HoloLens, accédez à la **Microsoft Store** et installez l’application de **[lecteur de communication à distance holographique](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. sur votre HoloLens, démarrez l’application de **lecteur de communication à distance holographique** .
1. Dans Unity, accédez au menu **fenêtre** , développez le sous-menu **XR** , puis sélectionnez **émulation holographique** (marquée comme dépréciée dans Unity 2019).
1. Définissez le **mode d’émulation** à **distant sur appareil**.
1. définissez la Version de l' **appareil** en fonction de si vous utilisez une HoloLens de première génération ou une HoloLens 2.
1. Pour **ordinateur distant**, entrez l’adresse IP de votre HoloLens.
1. Sélectionnez **Connecter**. Vous devez voir l’état de la **connexion** basculer sur **connecté** et voir l’écran vide dans le HoloLens.
1. Sélectionnez le bouton de **lecture** pour démarrer le mode lecture et tester l’application sur votre HoloLens. pour déboguer des scripts C# en mode lecture, [attachez Visual Studio à unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).
