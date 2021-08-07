---
title: Didacticiels audio spatial-1. Ajout de données audio spatiales à votre projet
description: ajoutez le plug-in Microsoft Spatializer à votre projet unity pour accéder HoloLens 2 déchargement matériel HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: 7f40e99e72a90de777e672f131afff5d05fe6416bd225c5b656678e340cc813d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211709"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Ajout de l’audio spatial à votre projet Unity

## <a name="overview"></a>Vue d’ensemble

Bienvenue dans le didacticiel sur l’audio spatial pour Unity sur HoloLens2. grâce à cette série de didacticiels, vous allez apprendre à utiliser le déchargement de la fonction de transfert HRTF sur HoloLens 2 et à activer la réaction lors de l’utilisation du déchargement HRTF.

le [référentiel de GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) dispose d’un projet unity terminé de cette séquence de didacticiels.

Pour comprendre ce que signifie l’aménagement des sons à l’aide des technologies Spatialization basées sur HRTF et des recommandations sur le moment où elles peuvent être utiles, consultez [conception spatiale du son](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Qu’est-ce que le déchargement HRTF ?

Le traitement de l’audio à l’aide d’algorithmes basés sur HRTF nécessite une grande quantité de calcul spécialisé. HoloLens 2 comprend un matériel dédié qui peut être utilisé pour éviter la charge du processeur d’application, « déchargeant » ainsi le traitement des algorithmes basés sur HRTF.  Le plug-in Microsoft Spatializer offre un moyen simple pour votre application de tirer parti du matériel HRTF dédié afin que votre application puisse utiliser davantage de processeurs d’applications pour les opérations autres que l’audio spatial.

## <a name="objectives"></a>Objectifs

* Importation et activation du plug-in Microsoft Spatializer
* Activation de l’audio spatial sur votre station de travail de développeur

## <a name="prerequisites"></a>Prérequis

* PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)
* Connaissances de base de la programmation en C++
* Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020/2019 LTS monté et le module Universal Windows Platform Build Support ajouté

Nous **vous recommandons vivement** de suivre la série des didacticiels de [prise](mr-learning-base-01.md) en main ou de bénéficier d’une expérience de base avec Unity et MRTK avant de continuer.

> [!Important]
> Cette série de tutoriels prend en charge Unity 2020 LTS (actuellement 2020.3.x) si vous utilisez Open XR ou le plug-in Windows XR, ainsi qu’Unity 2019 LTS (actuellement 2019.4.x) si vous utilisez WSA hérité ou le plug-in Windows XR. Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.

## <a name="creating-and-preparing-the-unity-project"></a>Création et préparation du projet Unity

Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.

Pour cela, suivez d’abord [Initialisation de votre projet et de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), ce qui inclut les étapes suivantes :

1. [Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *MRTK Tutorials*
2. [Changement de plateforme de génération](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importation des ressources TextMeshPro Essential](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importation de Mixed Reality Toolkit et configuration du projet Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Création et configuration de la scène](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) et donnez un nom approprié à la scène, par exemple *SpatialAudio*

Suivez ensuite les instructions relatives à la modification des options d’affichage de la [sensibilisation spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour vous assurer que le profil de configuration MRTK pour votre scène est **DefaultHoloLens2ConfigurationProfile** et modifiez les options d’affichage du maillage de la sensibilisation spatiale à **occlusion**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Ajout de Microsoft Spatializer à la Project

Téléchargez et importez Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. pour Unity </a>

>[!TIP]
> Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans [Importation des ressources du tutoriel](mr-learning-base-04.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Activer le plug-in Microsoft Spatializer

une fois que vous avez importé microsoft Spatializer dans votre projet unity, **MRTK Project fenêtre Configurator** s’affiche, utilisez la liste déroulante **Spatializer Audio** pour sélectionner le **Spatializer Microsoft**, puis cliquez sur le bouton appliquer pour appliquer le paramètre :

![configurateur MRTK Project](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

vous pouvez également activer manuellement le plug-in microsoft Spatializer : Open **Edit-> Project Paramètres->**, et changer le **plug-in Spatializer** en « Microsoft Spatializer ».

![Project Paramètres avec le plug-in spatializer](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Activer l’audio spatial sur votre station de travail

sur les versions de bureau de Windows, l’audio spatial est désactivé par défaut. Pour l’activer, cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches. pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2, choisissez le **son > Windows Sonic pour casque Spatial**.

![Paramètres audio spatiaux du Bureau](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Ce paramètre est requis uniquement si vous envisagez de tester votre projet dans l’éditeur Unity.

## <a name="congratulations"></a>Félicitations

Dans ce didacticiel, vous avez appris à importer et à activer le plug-in Microsoft Spatializer et à activer le son spatial sur votre station de travail.
Dans le didacticiel suivant, vous allez apprendre à ajouter de l’audio spatial dans le projet Unity.

> [!div class="nextstepaction"]
> [Didacticiel suivant : 2. sons d’interaction du bouton spatial](unity-spatial-audio-ch2.md)
