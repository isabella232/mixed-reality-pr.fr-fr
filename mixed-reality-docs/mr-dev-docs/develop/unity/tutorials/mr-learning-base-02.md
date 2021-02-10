---
title: Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 82551257339d41940075ee06a6e6937624b83900
ms.sourcegitcommit: 08503cada8a29a34bcbd9fd955cb23adfe9b60a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99627850"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Initialisation de votre projet et déploiement de votre première application

Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Mixed Reality Toolkit)</a> et à importer MRTK. Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2. Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens. En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.

## <a name="objectives"></a>Objectifs

* Apprendre à configurer Unity pour le développement HoloLens
* Apprendre à créer et déployer votre application sur HoloLens
* Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur un appareil HoloLens 2

## <a name="creating-the-unity-project"></a>Création du projet Unity

Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :

![Unity Hub avec le bouton New mis en évidence](images/mr-learning-base/base-02-section1-step1-1.png)

Dans la liste déroulante, sélectionnez la **version** Unity spécifiée dans les [prérequis](mr-learning-base-01.md#prerequisites) :

![Unity Hub avec la liste déroulante du sélecteur de version NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.

Dans la fenêtre Créer un projet :

* Vérifiez que **Modèles** est défini sur **3D**
* Entrez un **Nom du projet** approprié, par exemple _Tutoriels MRTK_
* Choisissez un **Emplacement** approprié pour stocker votre projet, par exemple _D:\MixedRealityLearning_
* Cliquez sur le bouton **Créer** pour créer et lancer votre nouveau projet Unity

![Unity Hub avec la fenêtre Create a new project renseignée](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Quand vous utilisez Windows, il existe une limite de 255 caractères pour MAX_PATH. Par conséquent, vous devez enregistrer le projet Unity près de la racine du lecteur.

Attendez qu’Unity crée le projet :

![Création du nouveau projet Unity en cours](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Changement de plateforme de génération

Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :

![Unity - Build Settings... Chemin du menu](images/mr-learning-base/base-02-section2-step1-1.png)

Dans la fenêtre Paramètres de build, sélectionnez **Plateforme Windows universelle** , puis cliquez sur le bouton **Switch Platform** (Changer de plateforme) :

![Fenêtre Build Setting d’Unity avec UWP sélectionné comme nouvelle plateforme, qui était auparavant Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

Attendez qu’Unity termine le changement de plateforme :

![Unity - Changement de plateforme en cours](images/mr-learning-base/base-02-section2-step1-3.png)

Quand Unity a terminé le changement de plateforme, cliquez sur l’icône **x** rouge pour fermer la fenêtre Paramètres de build :

![Fenêtre Build d’Unity avec l’icône Fermer mise en évidence](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>Importation des ressources TextMeshPro Essential

Dans le menu Unity, sélectionnez **Window** > **TextMeshPro** > **Import TMP Essential Resources** pour ouvrir la fenêtre Import Unity Package :

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK. Vous pouvez ignorer cette étape si vous ne prévoyez pas d’utiliser des éléments de l’interface utilisateur de MRTK dans votre projet.

## <a name="importing-the-mixed-reality-toolkit"></a>Importation du Mixed Reality Toolkit

Pour importer le Mixed Reality Toolkit dans le projet Unity, vous devez utiliser [Mixed Reality Feature Tool](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) qui permet aux développeurs de découvrir, mettre à jour et ajouter des packages de fonctionnalités Mixed Reality dans des projets Unity. Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.

Téléchargez la dernière version du Mixed Reality Feature Tool dans le [Centre de téléchargement Microsoft](https://aka.ms/MRFeatureTool). Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre Bureau.

> [!NOTE]
> Avant de pouvoir exécuter le Mixed Reality Feature Tool, installez le [runtime .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0).

> [!NOTE]
> Actuellement, le Mixed Reality Feature Tool s’exécute uniquement sur Windows. Pour MacOS, suivez la [procédure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) pour télécharger et importer le Mixed Reality Toolkit dans le projet Unity.

Ouvrez le fichier exécutable **MixedRealityFeatureTool** dans le dossier téléchargé pour lancer le Mixed Reality Feature Tool.  

![Ouverture de MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

Une fois que vous avez ouvert **MixedRealityFeatureTool**, cliquez sur Start pour commencer à utiliser l’outil.

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

Les fonctionnalités sont regroupées par catégorie pour faciliter leur recherche. Cliquez sur la liste déroulante **Mixed Reality Toolkit** pour trouver les packages qui lui sont associés.

![Fenêtre MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-3.png)

Cochez la case correspondant à **Mixed Reality Toolkit Foundation**, puis cliquez sur la liste déroulante à côté pour sélectionner la version MRTK requise. Pour cette série de tutoriels, sélectionnez **2.5.3**. Cliquez ensuite sur le bouton **Get features** pour télécharger les packages sélectionnés.

![Sélection de Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-4.png)

Le package sélectionné **Mixed Reality Toolkit Foundation 2.5.3** est présenté, ainsi que son package de dépendance **Mixed Reality Toolkit Standard Assets 2.5.3** dans la fenêtre **Import Features**.

Vous devez également définir l’emplacement du projet Unity cible pour fournir le **chemin du projet**. Cliquez sur les **trois points** à côté du chemin du projet et accédez à votre dossier de projet dans l’Explorateur, par exemple _D:\MixedRealityLearning\Tutoriels MRTK_.

> [!NOTE]
> La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier. Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.

Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.

![Validation de Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-5.png)

Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.

![Approbation de Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-6.png)

## <a name="configuring-the-unity-project"></a>Configuration du projet Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Appliquer les paramètres du configurateur de projet MRTK

Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher. Si ce n’est pas le cas, vous pouvez ouvrir manuellement en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :

![Chemin du menu Configure Unity Project d’Unity](images/mr-learning-base/base-02-section5-step1-1.png)

Dans la fenêtre MRTK Project Configurator, développez la section **Modify Configurations**, vérifiez que toutes les options sont cochées, puis cliquez sur le bouton **Apply** pour appliquer les paramètres :

![Fenêtre MRTK Project Configurator d’Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :

> * Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin. Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) de la documentation sur les [performances](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) de MRTK.
> * Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale. Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.

### <a name="2-configure-additional-project-settings"></a>2. Configurer des paramètres de projet supplémentaires

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :

Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, cochez la case **Virtual Reality Supported**, cliquez sur l’icône **+** et sélectionnez Windows Mixed Reality pour ajouter le SDK Windows Mixed Reality :

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](images/mr-learning-base/base-02-section5-step2-4.png)

Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître. Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement dans le menu Unity en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**.

Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet. Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée. Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.

Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, puis utilisez la liste déroulante **Depth Format** pour sélectionner **16-bit depth** :

![Unity - 16 Depth activé](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet. Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> de la documentation sur les <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">performances</a> de MRTK.

Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :

![Fenêtre Publishing Settings d’Unity avec le nom du package configuré](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Le « Package name » est l’identificateur unique de l’application. Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.

> [!TIP]
> « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.

## <a name="creating-and-configuring-the-scene"></a>Création et configuration de la scène

Dans le menu Unity, sélectionnez **File** > **New Scene** pour créer une scène :

![Unity - New Scene - Chemin du menu](images/mr-learning-base/base-02-section6-step1-1.png)

Dans le menu Unity, sélectionnez **Mixed Reality Toolkit** > **Add to Scene and Configure...** pour ajouter le MRTK à votre scène actuelle :

![Unity - Add to Scene and Configure... Chemin du menu](images/mr-learning-base/base-02-section6-step1-2.png)

Une fois l’objet **MixedRealityToolkit** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, vérifiez que le profil de configuration **MixedRealityToolkit** est défini sur **DefaultMixedRealityToolkitConfigurationProfile** :

![Composant MixedRealityToolkit d’Unity avec DefaultMixedRealityTookitConfigurationProfile sélectionné](images/mr-learning-base/base-02-section6-step1-3.png)

Dans le menu Unity, sélectionnez **Fichier** > **Enregistrer sous...** pour ouvrir la fenêtre Save Scene (Enregistrer la scène) :

![Unity - Save As... Chemin du menu](images/mr-learning-base/base-02-section6-step1-4.png)

Dans la fenêtre Enregistrer la scène, accédez au dossier **Scènes** de votre projet, donnez à votre scène un nom approprié, par exemple _Démarrage_, puis cliquez sur le bouton **Enregistrer** pour enregistrer la scène :

![Fenêtre d’invite Save d’Unity pour enregistrer la scène](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>Génération de votre application sur votre HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Générer le projet Unity

Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build.

Dans la fenêtre Paramètres de build, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste **Scenes In Build** (Scènes dans la génération), puis cliquez sur le bouton **Générer** pour ouvrir la fenêtre de génération d’applications de plateforme Windows universelle :

![Fenêtre Build Settings d’Unity avec UWP sélectionné](images/mr-learning-base/base-02-section7-step1-1.png)

Dans la fenêtre de génération d’applications de plateforme Windows universelle, choisissez un emplacement approprié pour stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _GettingStarted_, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération :

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](images/mr-learning-base/base-02-section7-step1-2.png)

Attendez qu’Unity termine le processus de génération :

![Processus de génération Unity en cours](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Générer et déployer l’application

Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build. Naviguez dans le dossier, puis double-cliquez sur le fichier solution pour l’ouvrir dans Visual Studio :

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .

Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible :

![Visual Studio configuré pour le déploiement sur HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.

> [!NOTE]
> En général, pour HoloLens, vous allez générer pour l’architecture ARM. Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio. La solution de contournement recommandée est de générer pour ARM64. Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.

> [!NOTE]
> Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP. Pour cela, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.

Connectez votre HoloLens à votre ordinateur, puis sélectionnez **Déboguer** > **Démarrer sans débogage** pour générer et déployer sur votre appareil :

![Visual Studio - Chemin du menu Démarrer sans débogage](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> Avant d’effectuer la génération sur votre appareil, celui-ci doit être en mode développeur et associé à votre ordinateur de développement. Vous pouvez effectuer ces deux étapes en suivant [ces instructions](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).

L’utilisation de Démarrer sans débogage démarre automatiquement l’application sur votre appareil sans le débogueur Visual Studio attaché.

Sélectionnez **Générer > Déployer la solution** pour déployer sur votre appareil sans que l’application ne démarre automatiquement.

> [!NOTE]
>Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **Toggle Diagnostics**. Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances. Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Félicitations

Vous avez maintenant déployé votre première application HoloLens. À mesure que vous vous déplacez, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens. En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application. Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK. Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 3. Configuration des profils MRTK](mr-learning-base-03.md)
