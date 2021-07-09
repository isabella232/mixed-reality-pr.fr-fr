---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392612"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="075a1-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="075a1-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="075a1-102">1. Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="075a1-102">1. Switching Build Platform</span></span>

<span data-ttu-id="075a1-103">Dans le menu Unity, sélectionnez File > Build Settings pour ouvrir la fenêtre Build Settings.</span><span class="sxs-lookup"><span data-stu-id="075a1-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="075a1-104">Dans la fenêtre Paramètres de génération, sélectionnez les plateformes **PC, Mac & Linux Standalone**, puis cliquez sur le bouton **Changer de plateforme** pour modifier la plateforme de génération :</span><span class="sxs-lookup"><span data-stu-id="075a1-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![Changement de plateforme de génération](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="075a1-106">Une fois qu’Unity a terminé le changement de plateforme, cliquez sur l’icône x pour fermer la fenêtre Paramètres de génération.</span><span class="sxs-lookup"><span data-stu-id="075a1-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="075a1-107">2. Définir les paramètres du projet</span><span class="sxs-lookup"><span data-stu-id="075a1-107">2. Set the project settings</span></span>

<span data-ttu-id="075a1-108">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet** > **Gestion du plug-in XR**, assurez-vous que vous êtes sous l’onglet Windows Standalone et cochez les cases **OpenXR** et **Ensemble des fonctionnalités Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="075a1-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![Activer OpenXR et l’ensemble des fonctionnalités Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="075a1-110">Dans la fenêtre Paramètres du projet, sélectionnez **OpenXR**, assurez-vous que vous êtes sous l’onglet Windows Standalone et modifiez le **Mode d’envoi en profondeur** de Aucun à **Profondeur de 16 bits**.</span><span class="sxs-lookup"><span data-stu-id="075a1-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="075a1-111">Sous l’onglet Profils d’interaction, ajoutez un **Profil d’interaction avec pointage du regard** et un **Profil d’interaction manuelle Microsoft** en cliquant sur le symbole +.</span><span class="sxs-lookup"><span data-stu-id="075a1-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![Ajouter un Profil d’interaction avec pointage du regard et un Profil d’interaction manuelle Microsoft](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="075a1-113">Sous **Groupes de fonctionnalités Open XR** > **Toutes les fonctionnalités** > cochez la case **Communication à distance d’application holographique**.</span><span class="sxs-lookup"><span data-stu-id="075a1-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![Activer la communication à distance d’application holographique](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="075a1-115">cochez ensuite la case **Windows Mixed Reality**. Sous le groupe Windows Mixed Reality, cochez la case **Communication à distance d’application holographique**.</span><span class="sxs-lookup"><span data-stu-id="075a1-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![Activer la communication à distance d’application holographique de Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="075a1-117">3. Générer le projet Unity</span><span class="sxs-lookup"><span data-stu-id="075a1-117">3. Build the Unity Project</span></span>

<span data-ttu-id="075a1-118">Dans le menu Unity, sélectionnez File > Build Settings pour ouvrir la fenêtre Build Settings.</span><span class="sxs-lookup"><span data-stu-id="075a1-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="075a1-119">Dans la fenêtre Build Settings, cliquez sur le bouton \***Add Open Scenes** _ pour ajouter votre scène actuelle aux scènes.</span><span class="sxs-lookup"><span data-stu-id="075a1-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="075a1-120">Dans la liste Build, cliquez sur le bouton _ \*Générer\*\* :</span><span class="sxs-lookup"><span data-stu-id="075a1-120">In the Build list, then click the _ *Build*\* button:</span></span>

![Fenêtre Build Settings d’Unity avec une scène ajoutée](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="075a1-122">choisissez un emplacement approprié pour stocker votre génération, par exemple : Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="075a1-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="075a1-123">Créez un dossier et donnez-lui un nom approprié, par exemple PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="075a1-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="075a1-124">Cliquez ensuite sur le bouton ***Select Folder*** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="075a1-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="075a1-126">Attendez qu’Unity termine le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="075a1-126">Wait for Unity to finish the build process.</span></span>

![Processus de génération Unity en cours](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="075a1-128">double-cliquez sur le fichier Exécutable pour ouvrir l’application de communication à distance holographique PC sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="075a1-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="075a1-129">En raison de problèmes connus dans la communication à distance holographique pour application PC conçue en tant que plateforme Windows universelle (UWP), nous créons l’application PC en tant que Windows Standalone pour OpenXR.</span><span class="sxs-lookup"><span data-stu-id="075a1-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="075a1-130">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="075a1-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="075a1-131">1. Définir les paramètres du lecteur</span><span class="sxs-lookup"><span data-stu-id="075a1-131">1. Set the player settings</span></span>

<span data-ttu-id="075a1-132">Dans la section **XR Settings**, cochez la case **WSA Holographic Remoting Supported** et activez la communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="075a1-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Fenêtre XR Settings d’Unity avec WSA Holographic Remoting Supported activé](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="075a1-134">2. Générer le projet Unity</span><span class="sxs-lookup"><span data-stu-id="075a1-134">2. Build the Unity Project</span></span>

<span data-ttu-id="075a1-135">Dans le menu Unity, sélectionnez File > Build Settings pour ouvrir la fenêtre Build Settings.</span><span class="sxs-lookup"><span data-stu-id="075a1-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="075a1-136">Dans la fenêtre Build Settings, cliquez sur le bouton \***Add Open Scenes** _ pour ajouter votre scène actuelle aux scènes.</span><span class="sxs-lookup"><span data-stu-id="075a1-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="075a1-137">Dans la liste Build, cliquez sur le _ *_bouton Build_*\* pour ouvrir la fenêtre Build Universal Windows Platform :</span><span class="sxs-lookup"><span data-stu-id="075a1-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Fenêtre Build Settings d’Unity avec une scène ajoutée](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="075a1-139">Dans la fenêtre Build Universal Windows Platform, choisissez un emplacement pour stocker votre build, par exemple Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="075a1-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="075a1-140">Créez un dossier et donnez-lui un nom approprié, par exemple PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="075a1-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="075a1-141">Cliquez ensuite sur le bouton ***Select Folder*** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="075a1-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="075a1-143">Attendez qu’Unity termine le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="075a1-143">Wait for Unity to finish the build process.</span></span>

![Processus de génération Unity en cours](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="075a1-145">3. Générer et déployer l’application</span><span class="sxs-lookup"><span data-stu-id="075a1-145">3. Build and deploy the application</span></span>

<span data-ttu-id="075a1-146">Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build.</span><span class="sxs-lookup"><span data-stu-id="075a1-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="075a1-147">Naviguez dans le dossier, puis double-cliquez sur le fichier .sln pour l’ouvrir dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="075a1-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="075a1-149">Si Visual Studio vous invite à installer de nouveaux composants, prenez un moment pour vérifier que tous les composants prérequis sont installés comme spécifié dans la documentation Installer les outils.</span><span class="sxs-lookup"><span data-stu-id="075a1-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="075a1-150">Configurez Visual Studio pour PC en sélectionnant la configuration Release, l’architecture x64 et Ordinateur local comme cible :</span><span class="sxs-lookup"><span data-stu-id="075a1-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Visual Studio configuré pour la machine locale](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="075a1-152">Cliquez sur le bouton qui indique ***Ordinateur local***.</span><span class="sxs-lookup"><span data-stu-id="075a1-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="075a1-153">La procédure de génération et de déploiement de l’application sur votre PC démarre.</span><span class="sxs-lookup"><span data-stu-id="075a1-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="075a1-154">L’application est installée sur votre PC par défaut.</span><span class="sxs-lookup"><span data-stu-id="075a1-154">The application will be installed in your PC by default.</span></span>
