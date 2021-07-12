---
title: Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176023"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Initialisation de votre projet et déploiement de votre première application

Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement MRTK (Mixed Reality Toolkit) et à importer MRTK. Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2. Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens. En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.

## <a name="objectives"></a>Objectifs

* Apprendre à configurer Unity pour le développement HoloLens
* Apprendre à créer et déployer votre application sur HoloLens
* Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur un appareil HoloLens 2

### <a name="steps-overview"></a>Vue d’ensemble des étapes
:::row:::
    :::column:::
       ![Étape 1 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step1.png) **1. Créer un nouveau projet Unity**
    :::column-end:::
    :::column:::
       ![Étape 2 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step2.png) **2. Importer MRTK dans le projet**
    :::column-end:::
    :::column:::
       ![Étape 3 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step3.png) **3. Configurer une nouvelle scène avec MRTK**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![Étape 4 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step4.png) **4. Créer un projet Unity**
    :::column-end:::
    :::column:::
       ![Étape 5 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step5.png) **5. Créer un projet UWP**
    :::column-end:::
    :::column:::
       ![Étape 6 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step6.png) **6. Exécuter un project sur l’appareil**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>Création du projet Unity

Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

Dans la liste déroulante, sélectionnez la **version** Unity spécifiée dans les [prérequis](mr-learning-base-01.md#prerequisites) :

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.

Dans la fenêtre Créer un projet :

* Vérifiez que **Modèles** est défini sur **3D**
* Entrez un **Nom du projet** approprié, par exemple _Tutoriels MRTK_
* Choisissez un **Emplacement** approprié pour stocker votre projet, par exemple _D:\MixedRealityLearning_
* Cliquez sur le bouton **Créer** pour créer et lancer votre nouveau projet Unity

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> Quand vous utilisez Windows, il existe une limite de 255 caractères pour MAX_PATH. Par conséquent, vous devez enregistrer le projet Unity près de la racine du lecteur.

Attendez qu’Unity crée le projet :

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>Changement de plateforme de génération

Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :

![Unity - Build Settings... Chemin du menu](images/mr-learning-base/base-02-section2-step1-1.png)

Dans la fenêtre Build Settings, sélectionnez **Universal Windows Platform**, puis :

1. Définissez **Target device** sur **HoloLens**.
2. Définissez **Architecture** sur **ARM 64**. 
3. Définissez **Build Type** sur **D3D Project**.
4. Définissez **Target SDK Version** sur **Latest Installed**
5. Définissez **Minimum Platform Version** sur **10.0.1024.0**
6. Définissez **Visual Studio Version** sur **Latest Installed**
7. Définissez **Build and Run on** sur **USB Device**
8. Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.
9. Appuyer sur le bouton Switch Platform

![Paramètres de build Unity avec les paramètres Universal Windows Platform définis](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Attendez qu’Unity termine le changement de plateforme :

![Unity - Changement de plateforme en cours](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

Une fois qu’Unity a terminé le changement de plateforme, cliquez sur l’icône **x** pour fermer la fenêtre Paramètres de génération.

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>Importation de Mixed Reality Toolkit et configuration du projet Unity

Pour importer le Mixed Reality Toolkit dans le projet Unity, vous devez utiliser [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) qui permet aux développeurs de découvrir, mettre à jour et ajouter des packages de fonctionnalités Mixed Reality dans des projets Unity. Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.

Téléchargez la dernière version du Mixed Reality Feature Tool dans le [Centre de téléchargement Microsoft](https://aka.ms/MRFeatureTool). Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre Bureau.

> [!NOTE]
> Avant de pouvoir exécuter le Mixed Reality Feature Tool, vous devez installer le [runtime .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer).

Ouvrez le fichier exécutable **MixedRealityFeatureTool** dans le dossier téléchargé pour lancer le Mixed Reality Feature Tool.  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Création de la scène et configuration de MRTK

Dans le menu Unity, sélectionnez **Fichier** > **Nouvelle scène** :

![Unity - New Scene - Chemin du menu](images/mr-learning-base/base-02-section6-step1-1.png)

Dans la fenêtre **Nouvelle scène**, sélectionnez **De base (intégré)** , puis cliquez sur **Créer** pour créer une scène :

![Nouvelle fenêtre de scène Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> La capture d’écran ci-dessus provient de Unity version 2020, si vous utilisez Unity 2019, lorsque vous cliquez sur **Créer**, une nouvelle scène vide sera créée.

Dans le menu Unity, sélectionnez **Mixed Reality** > **Kit de ressources** > **Ajouter à la scène et configurer...** pour ajouter le MRTK à votre scène actuelle :

![Unity - Add to Scene and Configure... Chemin du menu](images/mr-learning-base/base-02-section6-step1-2.png)

Une fois l’objet **MixedRealityToolkit** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, vérifiez que le profil de configuration **MixedRealityToolkit** est défini sur **DefaultMixedRealityToolkitConfigurationProfile** :

![Composant MixedRealityToolkit d’Unity avec DefaultMixedRealityTookitConfigurationProfile sélectionné](images/mr-learning-base/base-02-section6-step1-3.png)

Dans le menu Unity, sélectionnez **Fichier** > **Enregistrer sous...** pour ouvrir la fenêtre Save Scene (Enregistrer la scène) :

![Unity - Save As... Chemin du menu](images/mr-learning-base/base-02-section6-step1-4.png)

Enregistrez la scène dans votre projet sous **Ressource** > **Scènes**.

![Fenêtre d’invite Save d’Unity pour enregistrer la scène](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>Ajout d’une interaction manuelle à un objet

Dans le menu Unity, sélectionnez **GameObject** > **Objet 3D** > **Cube** pour ajouter un objet Cube à la scène.

![Ajout d’un cube à la scène](images/mr-learning-base/base-02-section8-step1-1.png)

Cliquez sur l’objet **Cube** dans la fenêtre Hiérarchie, puis, dans la fenêtre de l’inspecteur, configurez son composant **Transform** comme suit

* **Position** : X = 0, Y = 0,1, Z = 0,5
* **Rotation** : X = 0, Y = 0, Z = 0
* **Échelle** : X = 0,1, Y = 0,1, Z = 0,1

1 unité Unity équivaut à 1 mètre. Nous avons mis à jour la taille du cube pour qu’il fasse 10x10x10 cm, placé à 50 cm depuis la position du casque (0,0,0). 10cm sous le niveau de l’œil pour une interaction confortable. 

Si vous utilisez l’échelle par défaut (1,1,1), le cube est trop volumineux. Si vous utilisez la position par défaut (0,0,0), le cube est placé à la même position que votre casque et vous ne pouvez pas le voir tant que vous n’avez pas effectué un déplacement vers l’arrière.

![Ajustement des informations de transformation](images/mr-learning-base/base-02-section8-step1-1b.png)

Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **Cube**, puis faire un léger zoom avant. Vous pouvez utiliser la touche F pour effectuer un zoom et vous focaliser sur l’objet.

Pour interagir avec un objet et le saisir avec des mouvements captés des mains, l’objet doit comporter :
 * Composant Collider, tel que **Box Collider** (le cube de Unity a déjà un type de Collider par défaut)
 * Le composant **Object Manipulator (Script)**
 * Composant **NearInteractionGrabbable(Script)**

Le script **ObjectManipulator** de MRTK permet de déplacer, de modifier et de faire pivoter un objet à l’aide d’une ou deux mains. Ce script prend en charge le modèle d’entrée de manipulation directe, car il permet à l’utilisateur de toucher des hologrammes directement avec ses mains.

Toujours avec le **cube** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, cliquez sur le bouton **Add Component**, puis recherchez et sélectionnez le script **Object Manipulator** pour ajouter le script Object Manipulator à l’objet Cube.

![Ajout d’un manipulateur d’objet au cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

Répétez la même procédure pour ajouter un **script Near Interaction Grabbable** au cube.

![Ajout d’un script Near Interaction Grabbable au cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> Quand vous ajoutez un Object Manipulator (Script), dans ce cas, le Constraint Manager (Script) est ajouté automatiquement, car Object Manipulator (Script) en dépend.

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>Test de votre application dans l’éditeur Unity avec la simulation d’entrée MRTK

Avec la simulation d’entrée de MRTK, vous pouvez tester divers types d’interactions dans l’éditeur Unity sans développement ni déploiement sur un appareil. Cela vous permet d’itérer rapidement vos idées dans le processus de conception et de développement. Utilisez les raccourcis clavier et souris pour contrôler les entrées simulées.

Cliquez sur le bouton de lecture pour accéder au mode de lecture. Maintenez la touche **Décalage vers la gauche** ou **Espace** pour faire apparaître le contrôleur (mains simulées), le déplacement de la souris déplace le contrôleur et peut également être déplacé plus ou moins près de la caméra à l’aide de la roulette de la souris. Une fois que le pointeur se trouve sur le cube, appuyez de façon prolongée sur le **bouton gauche de la souris** pour saisir l’objet Cube.

* Appuyez sur les touches **W, A, S, D, Q, E** pour déplacer la caméra.
* Maintenez le **bouton droit de la souris** enfoncé et déplacez la souris pour regarder autour de vous.
* Pour faire apparaître les mains simulées, appuyez sur la **barre d’espace (droite)** ou sur la **touche Maj de gauche**
* Appuyez sur les touches **T** ou **Y** pour que les mains simulées restent affichées
* Pour faire pivoter des mains simulées, maintenez la touche **Ctrl** enfoncée et déplacez la souris

![Mode jeu](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a>Génération de votre application sur votre HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Générer le projet Unity

Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build.

Dans la fenêtre Paramètres de build, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste **Scenes In Build** (Scènes dans la génération), puis cliquez sur le bouton **Générer** pour ouvrir la fenêtre de génération d’applications de plateforme Windows universelle :

![Fenêtre Build Settings d’Unity avec UWP sélectionné](images/mr-learning-base/base-02-section9-step1-1.png)

Dans la fenêtre de génération d’applications de plateforme Windows universelle, choisissez un emplacement approprié pour stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _GettingStarted_, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération :

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](images/mr-learning-base/base-02-section9-step1-2.png)

Attendez qu’Unity termine le processus de génération :

![Processus de génération Unity en cours](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Générer et déployer l’application

Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build. Naviguez dans le dossier, puis double-cliquez sur le fichier solution pour l’ouvrir dans Visual Studio :

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .

Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible :

![Visual Studio configuré pour le déploiement sur HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.

> [!NOTE]
> En général, pour HoloLens, vous allez générer pour l’architecture ARM. Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio. La solution de contournement recommandée est de générer pour ARM64. Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.

> [!NOTE]
> Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP. Pour cela, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.

Connectez votre HoloLens à votre ordinateur, puis sélectionnez **Déboguer** > **Démarrer sans débogage** pour générer et déployer sur votre appareil :

![Visual Studio - Chemin du menu Démarrer sans débogage](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> Avant d’effectuer la génération sur votre appareil, celui-ci doit être en mode développeur et associé à votre ordinateur de développement. Vous pouvez effectuer ces deux étapes en suivant [ces instructions](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).

L’utilisation de Démarrer sans débogage démarre automatiquement l’application sur votre appareil sans le débogueur Visual Studio attaché.

Sélectionnez **Générer > Déployer la solution** pour déployer sur votre appareil sans que l’application ne démarre automatiquement.

> [!NOTE]
>Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **« Toggle Diagnostics »** . Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances. Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Félicitations

Vous avez maintenant déployé votre première application HoloLens. Une fois l’application ouverte, vous devez voir un objet Cube devant vous, et vous devez pouvoir interagir avec lui en le déplaçant. Lorsque vous vous déplacez, vous devez également voir un maillage de mappage spatial couvrant les surfaces perçues par le HoloLens. En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application. Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK. Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 3. Configuration des profils MRTK](mr-learning-base-03.md)
