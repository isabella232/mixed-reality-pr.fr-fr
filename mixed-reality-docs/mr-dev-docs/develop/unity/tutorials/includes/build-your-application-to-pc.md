---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392612"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. Changement de plateforme de génération

Dans le menu Unity, sélectionnez File > Build Settings pour ouvrir la fenêtre Build Settings.

Dans la fenêtre Paramètres de génération, sélectionnez les plateformes **PC, Mac & Linux Standalone**, puis cliquez sur le bouton **Changer de plateforme** pour modifier la plateforme de génération :

![Changement de plateforme de génération](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

Une fois qu’Unity a terminé le changement de plateforme, cliquez sur l’icône x pour fermer la fenêtre Paramètres de génération.

### <a name="2-set-the-project-settings"></a>2. Définir les paramètres du projet

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet** > **Gestion du plug-in XR**, assurez-vous que vous êtes sous l’onglet Windows Standalone et cochez les cases **OpenXR** et **Ensemble des fonctionnalités Windows Mixed Reality**.

![Activer OpenXR et l’ensemble des fonctionnalités Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

Dans la fenêtre Paramètres du projet, sélectionnez **OpenXR**, assurez-vous que vous êtes sous l’onglet Windows Standalone et modifiez le **Mode d’envoi en profondeur** de Aucun à **Profondeur de 16 bits**.

Sous l’onglet Profils d’interaction, ajoutez un **Profil d’interaction avec pointage du regard** et un **Profil d’interaction manuelle Microsoft** en cliquant sur le symbole +.

![Ajouter un Profil d’interaction avec pointage du regard et un Profil d’interaction manuelle Microsoft](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

Sous **Groupes de fonctionnalités Open XR** > **Toutes les fonctionnalités** > cochez la case **Communication à distance d’application holographique**.

![Activer la communication à distance d’application holographique](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

cochez ensuite la case **Windows Mixed Reality**. Sous le groupe Windows Mixed Reality, cochez la case **Communication à distance d’application holographique**.

![Activer la communication à distance d’application holographique de Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. Générer le projet Unity

Dans le menu Unity, sélectionnez File > Build Settings pour ouvrir la fenêtre Build Settings.

Dans la fenêtre Build Settings, cliquez sur le bouton ***Add Open Scenes** _ pour ajouter votre scène actuelle aux scènes. Dans la liste Build, cliquez sur le bouton _ *Générer** :

![Fenêtre Build Settings d’Unity avec une scène ajoutée](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

choisissez un emplacement approprié pour stocker votre génération, par exemple : Documents\MixedRealityLearning. Créez un dossier et donnez-lui un nom approprié, par exemple PCHolographicRemoting. Cliquez ensuite sur le bouton ***Select Folder*** pour démarrer le processus de génération :

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

Attendez qu’Unity termine le processus de génération.

![Processus de génération Unity en cours](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

double-cliquez sur le fichier Exécutable pour ouvrir l’application de communication à distance holographique PC sur votre PC.

> [!NOTE]
> En raison de problèmes connus dans la communication à distance holographique pour application PC conçue en tant que plateforme Windows universelle (UWP), nous créons l’application PC en tant que Windows Standalone pour OpenXR.


# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1. Définir les paramètres du lecteur

Dans la section **XR Settings**, cochez la case **WSA Holographic Remoting Supported** et activez la communication à distance holographique.

![Fenêtre XR Settings d’Unity avec WSA Holographic Remoting Supported activé](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Générer le projet Unity

Dans le menu Unity, sélectionnez File > Build Settings pour ouvrir la fenêtre Build Settings.

Dans la fenêtre Build Settings, cliquez sur le bouton ***Add Open Scenes** _ pour ajouter votre scène actuelle aux scènes. Dans la liste Build, cliquez sur le _ *_bouton Build_** pour ouvrir la fenêtre Build Universal Windows Platform :

![Fenêtre Build Settings d’Unity avec une scène ajoutée](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Dans la fenêtre Build Universal Windows Platform, choisissez un emplacement pour stocker votre build, par exemple Documents\MixedRealityLearning. Créez un dossier et donnez-lui un nom approprié, par exemple PCHolographicRemoting. Cliquez ensuite sur le bouton ***Select Folder*** pour démarrer le processus de génération :

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Attendez qu’Unity termine le processus de génération.

![Processus de génération Unity en cours](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Générer et déployer l’application

Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build. Naviguez dans le dossier, puis double-cliquez sur le fichier .sln pour l’ouvrir dans Visual Studio :

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Si Visual Studio vous invite à installer de nouveaux composants, prenez un moment pour vérifier que tous les composants prérequis sont installés comme spécifié dans la documentation Installer les outils.

Configurez Visual Studio pour PC en sélectionnant la configuration Release, l’architecture x64 et Ordinateur local comme cible :

![Visual Studio configuré pour la machine locale](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Cliquez sur le bouton qui indique ***Ordinateur local***. La procédure de génération et de déploiement de l’application sur votre PC démarre. L’application est installée sur votre PC par défaut.
