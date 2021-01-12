---
title: Tutoriels sur MRTK - 2. Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859528"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Initialisation de votre projet et déploiement de votre première application

## <a name="overview"></a>Vue d’ensemble

Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Mixed Reality Toolkit)</a> et à importer MRTK. Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2. Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens. En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.

## <a name="objectives"></a>Objectifs

* Apprendre à configurer Unity pour le développement HoloLens.
* Apprendre à créer et déployer votre application sur HoloLens.
* Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur votre appareil HoloLens 2.

## <a name="creating-the-unity-project"></a>Création du projet Unity

1. Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :

![Unity Hub avec la flèche bas du bouton « Nouveau » en surbrillance](images/mr-learning-base/base-02-section1-step1-1.png)

2. Dans le menu déroulant, sélectionnez la version Unity spécifiée dans les [Prérequis](mr-learning-base-01.md#prerequisites) :

![Sélectionner la version Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.

3. Dans la fenêtre **Créer un projet**, procédez comme suit :

    * Vérifiez que **Modèles** est défini sur **3D**.
    * Dans la zone **Nom du projet** , entrez un nom approprié pour votre projet (par exemple, « Tutoriels MRTK »).
    * Cliquez sur le bouton à trois points en regard d’**Emplacement**, puis accédez au dossier dans lequel vous souhaitez enregistrer votre projet.

> [!CAUTION]
> Quand vous utilisez Windows, il existe une limite de 255 caractères pour MAX_PATH. Dès lors, vous devez enregistrer le projet Unity près de la racine du lecteur.

    * Cliquez sur le bouton **Créer**. Cela permet de créer et de lancer votre nouveau projet Unity.

![Unity Hub avec la fenêtre « Créer un projet » renseignée](images/mr-learning-base/base-02-section1-step1-3.png)

La barre d’état vous renseigne sur votre progression.

![La barre de progression Unity vous renseigne sur l’état de création de votre projet.](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Changement de plateforme de génération

1. Dans la barre de menus, sélectionnez **Fichier** > **Paramètres de build...**

![Unity - Build Settings... Chemin du menu](images/mr-learning-base/base-02-section2-step1-1.png)

2. Dans la fenêtre **Paramètres de build**, sélectionnez **Plateforme Windows universelle**, puis cliquez sur le bouton **Changer de plateforme** :

![Fenêtre Build Setting d’Unity avec UWP sélectionné comme nouvelle plateforme, qui était auparavant Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

3. Attendez qu’Unity termine le changement de plateforme, puis fermez la fenêtre **Paramètres de build**.

## <a name="importing-the-textmeshpro-essential-resources"></a>Importation des ressources TextMeshPro Essential

Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK. Si vous ne prévoyez pas d’utiliser des éléments de l’interface utilisateur de MRTK dans votre projet, vous pouvez ignorer cette étape.

1. Dans la barre de menus, sélectionnez **Fenêtre** > **TextMeshPro** > **Importer les ressources essentielles TMP**.

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. Dans la fenêtre **Importer un package Unity**, cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>Importation du Mixed Reality Toolkit

1. Téléchargez le package personnalisé Unity :

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. Dans la barre de menus, sélectionnez **Ressources** > **Importer un package** > **Package personnalisé...** .
3. Dans la boîte de dialogue **Importer un package...** , accédez à l’emplacement du package que vous venez de télécharger, sélectionnez-le, puis cliquez sur le bouton **Ouvrir** .
4. Dans la fenêtre **Importer un package Unity**, cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources.

## <a name="selecting-mrtk-and-project-settings"></a>Sélection de MRTK et des paramètres de projet

Une fois qu’Unity a fini d’importer le package de la section précédente, la fenêtre **MRTK Project Configurator** doit s’afficher. Si ce n’est pas le cas, vous pouvez ouvrir manuellement en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :

![Chemin du menu Configure Unity Project d’Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. Dans la fenêtre **MRTK Project Configurator**, développez la section **Modifier les configurations**, si nécessaire, puis vérifiez que toutes les options sont sélectionnées.

![Fenêtre Unity MRTK Project Configurator avec la section Modifier les configurations affichée](images/mr-learning-base/base-02-section5-step1-2.png)

2. Pour appliquer les paramètres, cliquez sur le bouton **Appliquer**.

![Bouton Appliquer de MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> Vous utilisez le XR hérité intégré à Unity au lieu du nouveau système de plug-ins XR, car le nouveau système n’est pas entièrement compatible avec les [versions recommandées d’Unity et de MRTK](mr-learning-base-01.md#prerequisites) pour cette série de tutoriels. Si des avertissements relatifs au XR intégré déconseillé s’affichent, vous pouvez les ignorer.

> [!TIP]
> L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :
>
> * Enable legacy XR : Active VR pour le projet.
> * Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin. Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) de la documentation sur les [performances](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) de MRTK.
> * Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale. Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.

3. Dans la barre de menus, sélectionnez **Modifier** > **Paramètres du projet...** .

4. Dans la fenêtre **Paramètres du projet**, sélectionnez **Lecteur**, cliquez sur la liste déroulante **Paramètres XR**, puis activez la case à cocher en regard de **Réalité virtuelle prise en charge** :

![Paramètres XR Unity avec l’option Réalité virtuelle prise en charge affichée](images/mr-learning-base/base-02-section5-step2-2.png)

Cela importe le kit de développement logiciel (SDK) Windows Mixed Reality :

![Paramètres XR Unity avec les kits de développement logiciel (SDK) de réalité virtuelle affichés](images/mr-learning-base/mixed-reality-sdk.png)

Une fois qu’Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre **MRTK Project Configurator** doit réapparaître. Si ce n’est pas le cas, sélectionnez **Mixed Reality Toolkit** > **Utilitaires** > **Configurer un projet Unity** pour l’ouvrir.

5. Dans la fenêtre **MRTK Project Configurator**, cliquez sur la liste déroulante **Audio Spatializer**, puis sélectionnez **MS HRTF Spatializer**.

![Paramètres du projet avec les options Audio Spatializer affichées](images/mr-learning-base/base-02-section5-step2-3.png)

6. Cliquez sur le bouton **Appliquer**. La fenêtre **MRTK Project Configurator** se ferme.

    > [!TIP]
    > La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet. Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée. Pour plus d’informations sur ce sujet, vous pouvez consulter les tutoriels d’audio spatiale.

7. Dans la fenêtre **Paramètre du projet**, cliquez sur la liste déroulante **Format de profondeur**, puis sélectionnez **Profondeur de 16 bits** :

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Paramètres XR d’Unity avec une profondeur de 16 bits sélectionnée.":::

    > [!TIP]
    > La réduction du format de profondeur à 16 bits est facultative, mais peut contribuer à améliorer les performances graphiques dans votre projet. Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) de la documentation sur les [performances](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) de MRTK.

8. Cliquez sur la liste déroulante **Paramètres de publication** puis, dans la zone **Nom du package**, entrez un nom approprié (par exemple, « MRTK-Tutorials-Getting-Started »).

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Fenêtre Paramètres de publication d’Unity avec le nom du package configuré.":::

    **Nom du package et nom du produit**

    - Le « Package name » est l’identificateur unique de l’application. Vous devez créer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.
    - « Product Name » est le nom affiché dans le menu Démarrer de HoloLens. Pour faciliter la localisation de l’application pendant le développement, vous pouvez ajouter un trait de soulignement devant le nom afin qu’il apparaisse en haut du classement.

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Paramètres du projet Unity avec le nom du produit configuré.":::

9. Fermez la fenêtre **Paramètres du projet**.

## <a name="creating-and-configuring-the-scene"></a>Création et configuration de la scène

1. Dans la barre de menus, sélectionnez **Fichier** > **Nouvelle scène**.
2. Pour ajouter le MRTK à la scène, dans la barre de menus, sélectionnez **Mixed Reality Toolkit** > **Ajouter à la scène et configurer...** .

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity - Ajouter à la scène et configurer... Chemin du menu.":::

3. Dans la fenêtre **Hiérarchie**, vérifiez que **MixedRealityToolkit** est sélectionné.

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Vérifiez que MixedRealityTookit est sélectionné.":::

4. Dans la section **MixedRealityToolkit** de la fenêtre **Inspector**, vérifiez que le profil de configuration est définir sur **DefaultMixedRealityToolkitConfigurationProfile** :

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Composant MixedRealityToolkit d’Unity avec DefaultMixedRealityTookitConfigurationProfile sélectionné.":::

    > [!IMPORTANT]
    > En général, vous allez utiliser DefaultHoloLens2ConfigurationProfile lors du développement pour HoloLens. Toutefois, pour ce tutoriel, vous utiliserez DefaultMixedRealityToolkitConfigurationProfile. Dans le tutoriel suivant, [Configuration des profils MRTK](mr-learning-base-03.md), vous utiliserez DefaultHoloLens2ConfigurationProfile.

5. Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer sous...** .
6. Dans la boîte de dialogue **Enregistrer la scène**, accédez au dossier **Scènes** de votre projet. Dans la zone **Nom du fichier**, donnez à votre scène un nom approprié (par exemple, « \_GettingStarted\_ »), puis cliquez sur le bouton **Enregistrer**.

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Fenêtre d’invite Enregistrer d’Unity pour enregistrer la scène.":::

## <a name="building-and-deploying-to-your-hololens-2"></a>Génération et déploiement sur votre HoloLens 2

> Avant toute génération sur votre appareil, vérifiez ce qui suit :
- Votre appareil est en mode développeur.
- Votre appareil est couplé à votre ordinateur de développement. Si ce n’est pas le cas, la boîte de dialogue suivante s’affiche dans Visual Studio lors du processus de génération :

![Entrée du code PIN pour le couplage d’appareils](images/mr-learning-base/pin-request.png)

 Pour en savoir plus sur ces deux étapes, consultez [Utilisation de Visual Studio pour le déploiement et le débogage](../../platform-capabilities-and-apis/using-visual-studio.md).

1. Dans la barre de menus, sélectionnez **Fichier** > **Paramètres de build...** .
2. Dans la fenêtre **Paramètres de build**, cliquez sur le bouton **Ajouter des scènes ouvertes** pour ajouter votre scène actuelle à la liste **Scènes de la build**.

![Ajouter votre scène actuelle à la liste « Scènes de la build »](images/mr-learning-base/base-02-section7-step1-1.png)

3. Cliquez sur le bouton **Créer**.

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Cliquez sur le bouton Créer.":::

4. Dans la boîte de dialogue **Build - Plateforme Windows universelle**, sélectionnez un emplacement approprié où stocker votre build (vous pouvez, par exemple, créer un dossier « Builds » dans votre dossier « Tutoriels MRTK »). Créez un dossier et attribuez-lui un nom approprié (par exemple, « GettingStarted »), sélectionnez le dossier, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Fenêtre de génération Unity avec votre dossier de build affiché.":::

    Une barre d’état s’affiche pour vous informer de la progression de la génération.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Processus de génération Unity en cours.":::

    > [!TIP]
    > Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).

5. Une fois le processus de génération terminé, dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez stocké la build, puis double-cliquez sur le fichier de solution pour l’ouvrir dans Visual Studio :

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Explorateur Windows avec le fichier de solution Visual Studio nouvellement créé sélectionné.":::

    > [!NOTE]
    > Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .

6. Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible.

    > [!TIP]
    > Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configuré pour le déploiement sur HoloLens 2.":::

    > [!NOTE]
    > En général, pour HoloLens, vous allez générer pour l’architecture ARM. Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio. La solution de contournement recommandée est de générer pour ARM64. Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.

    > [!NOTE]
    > Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP. Pour ce faire, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.

7. Connectez votre HoloLens à votre ordinateur, puis effectuez l’une des opérations suivantes :
- Pour générer l’application, déployez-la dans votre HoloLens et démarrez-la automatiquement sans que le débogueur Visual Studio ne soit attaché. Dans la barre de menus, sélectionnez **Débogage** > **Exécuter sans débogage**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio - Chemin du menu Démarrer sans débogage.":::

- Pour générer et déployer l’application dans votre HoloLens sans qu’elle démarre automatiquement, dans la barre de menus, sélectionnez **Build > Déployer la solution**.

    > [!NOTE]
    >Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **Toggle Diagnostics**. Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances. Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Félicitations

Vous avez maintenant déployé votre première application HoloLens. À mesure que vous vous déplacez, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens. En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application. Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK. Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 3. Configuration des profils MRTK](mr-learning-base-03.md)
