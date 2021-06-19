---
ms.openlocfilehash: 40d24083ec83b9d6faebc00cf801d1f6f55fddd7
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392290"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. Sur votre HoloLens, accédez à la **Microsoft Store** et installez l’application de **[lecteur de communication à distance holographique](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. Sur votre HoloLens, démarrez l’application de **lecteur de communication à distance holographique** .
1. Dans Unity, accédez au menu **Edition** , puis sélectionnez **paramètres du projet**.
1. Sélectionnez **gestion du plug-in XR**.
1. Vérifiez que l’onglet **autonome Windows** est sélectionné, recherchez **OpenXR** et la **fonctionnalité Windows Mixed Reality définie** dans la liste, puis cochez les cases correspondantes.
1. Ensuite, accédez au menu **fenêtre** , développez le sous-menu **XR** , puis sélectionnez la communication à distance de l' **éditeur OpenXR**.

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](../images/openxr-features-img-02.png)

1. Cliquez sur **activer l’accès distant** de l’éditeur.

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec les fonctionnalités mises en surbrillance](../images/openxr-features-img-03.png)

1. Si le bouton **activer les dépendances manquantes** s’affiche, cliquez sur également. La zone d’erreur au-dessus du bouton décrit les fonctionnalités qu’elle active et pourquoi.
1. Pour **nom d’hôte distant**, entrez l’adresse IP de votre HoloLens.
   1. Modifiez les autres paramètres en fonction des besoins.
   1. L’éditeur essaiera de se connecter une fois que le mode de lecture est démarré.
1. Sélectionnez le bouton de **lecture** pour démarrer le mode lecture et tester l’application sur votre HoloLens. Pour déboguer des scripts C# en mode lecture, [attachez Visual Studio à Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

> [!NOTE]
> À partir de la version 0.1.0, le runtime de communication à distance holographique ne prend pas en charge les ancres, et les fonctionnalités ARAnchorManager ne fonctionnent pas via la communication à distance.  Cette fonctionnalité est disponible dans les versions ultérieures.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

1. Sur votre HoloLens, accédez à la **Microsoft Store** et installez l’application de **[lecteur de communication à distance holographique](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. Sur votre HoloLens, démarrez l’application de **lecteur de communication à distance holographique** .
1. Dans Unity, accédez au menu **Edition** , puis sélectionnez **paramètres du projet**.
1. Sélectionnez **gestion du plug-in XR**.
1. Vérifiez que l’onglet **autonome Windows** est sélectionné, recherchez **Windows Mixed Reality** dans la liste et cochez sa case.
1. Ensuite, accédez au menu **fenêtre** , développez le sous-menu **XR** , puis sélectionnez **accès distant du plug-in Windows XR**.
1. Définissez le **mode d’émulation** à **distant sur appareil**.
1. Pour **ordinateur distant**, entrez l’adresse IP de votre HoloLens.
1. Pour vous connecter, effectuez l’une des opérations suivantes :
   1. Pour vous connecter manuellement, désactivez **se connecter à la lecture**, puis sélectionnez **se connecter**. Le changement d' **État** de la connexion doit être défini sur **connecté** et l’écran s’affichera vide dans HoloLens.
   1. Pour vous connecter automatiquement, activez la case à cocher **se connecter en lecture**. L’éditeur essaiera de se connecter une fois que le mode de lecture est démarré.
1. Sélectionnez le bouton de **lecture** pour démarrer le mode lecture et tester l’application sur votre HoloLens. Pour déboguer des scripts C# en mode lecture, [attachez Visual Studio à Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

1. Sur votre HoloLens, accédez à la **Microsoft Store** et installez l’application de **[lecteur de communication à distance holographique](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
1. Sur votre HoloLens, démarrez l’application de **lecteur de communication à distance holographique** .
1. Dans Unity, accédez au menu **fenêtre** , développez le sous-menu **XR** , puis sélectionnez **émulation holographique** (marquée comme dépréciée dans Unity 2019).
1. Définissez le **mode d’émulation** à **distant sur appareil**.
1. Définissez la version de l' **appareil** en fonction de si vous utilisez un hololens de première génération ou un hololens 2.
1. Pour **ordinateur distant**, entrez l’adresse IP de votre HoloLens.
1. Sélectionnez **Se connecter**. Le changement d' **État** de la connexion doit être défini sur **connecté** et l’écran s’affichera vide dans HoloLens.
1. Sélectionnez le bouton de **lecture** pour démarrer le mode lecture et tester l’application sur votre HoloLens. Pour déboguer des scripts C# en mode lecture, [attachez Visual Studio à Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).
