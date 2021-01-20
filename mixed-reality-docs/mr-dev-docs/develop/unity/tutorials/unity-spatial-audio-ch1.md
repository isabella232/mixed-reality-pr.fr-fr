---
title: Didacticiels audio spatial-1. Ajout de données audio spatiales à votre projet
description: Ajoutez le plug-in Microsoft Spatializer à votre projet Unity pour accéder au déchargement matériel HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: 1eb2913f1953e334cfe75b786f96bb51a9852fc5
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578444"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Ajout de l’audio spatial à votre projet Unity

## <a name="overview"></a>Vue d'ensemble

Bienvenue dans le didacticiel sur l’audio spatial pour Unity sur HoloLens2. Grâce à cette série de didacticiels, vous allez apprendre à utiliser le déchargement de la fonction de transfert HRTF (en anglais) sur HoloLens 2 et à activer la réaction lors de l’utilisation du déchargement HRTF.

Le [dépôt github Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) a un projet Unity terminé de cette séquence de didacticiels.

Pour comprendre ce que signifie l’aménagement des sons à l’aide des technologies Spatialization basées sur HRTF et des recommandations sur le moment où elles peuvent être utiles, consultez [conception spatiale du son](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Qu’est-ce que le déchargement HRTF ?

Le traitement de l’audio à l’aide d’algorithmes basés sur HRTF nécessite une grande quantité de calcul spécialisé. HoloLens 2 comprend un matériel dédié qui peut être utilisé pour éviter la charge du processeur d’application, ce qui « décharge » le traitement des algorithmes basés sur HRTF.  Le plug-in Microsoft Spatializer offre un moyen simple pour votre application de tirer parti du matériel HRTF dédié afin que votre application puisse utiliser davantage de processeurs d’applications pour les opérations autres que l’audio spatial.

## <a name="objectives"></a>Objectifs

* Importation et activation du plug-in Microsoft Spatializer
* Activation de l’audio spatial sur votre station de travail de développeur

## <a name="prerequisites"></a>Prérequis

* PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)
* Connaissances de base de la programmation en C++
* Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019 LTS monté et le module Universal Windows Platform Build Support ajouté

Nous **vous recommandons vivement** de suivre la série des didacticiels de [prise](mr-learning-base-01.md) en main ou de bénéficier d’une expérience de base avec Unity et MRTK avant de continuer.

> [!IMPORTANT]
>
> * La version d’Unity recommandée pour cette série de tutoriels est Unity 2019 LTS. Elle remplace toutes les versions Unity requises ou recommandées qui sont indiquées dans les prérequis ci-dessus.

## <a name="creating-and-preparing-the-unity-project"></a>Création et préparation du projet Unity

Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.

Pour cela, suivez d’abord [Initialisation de votre projet et de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), ce qui inclut les étapes suivantes :

1. [Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *MRTK Tutorials*

1. [Changement de plateforme de génération](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importation des ressources TextMeshPro Essential](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importation du Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Configuration du projet Unity](mr-learning-base-02.md#configuring-the-unity-project)

1. [Création et définition de la scène](mr-learning-base-02.md#creating-and-configuring-the-scene) et attribution d’un nom approprié à la scène, par exemple, *SpatialAudio*

Suivez ensuite les instructions relatives à la modification des options d’affichage de la [sensibilisation spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour vous assurer que le profil de configuration MRTK pour votre scène est **DefaultXRSDKConfigurationProfile** et modifiez les options d’affichage du maillage de la sensibilisation spatiale à **occlusion**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Ajout de Microsoft Spatializer au projet

Téléchargez et importez Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. pour Unity </a>

>[!TIP]
> Pour un rappel de la façon d’importer un package personnalisé Unity, vous pouvez vous référer aux instructions de [Importer le Kit de ressources de réalité mixte](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Activer le plug-in Microsoft Spatializer

Après l’importation de **Microsoft Spatializer** , vous devez l’activer. Ouvrez les **paramètres de projet Edit->-> audio**, puis remplacez le **plug-in Spatializer** par "Microsoft Spatializer".

![Paramètres du projet présentant le plug-in Spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Activer l’audio spatial sur votre station de travail

Sur les versions de bureau de Windows, l’audio spatial est désactivé par défaut. Pour l’activer, cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches. Pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2, choisissez **son Spatial > Windows Sonic pour casque**.

![Paramètres audio spatiaux du Bureau](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> Ce paramètre est requis uniquement si vous envisagez de tester votre projet dans l’éditeur Unity.

## <a name="congratulations"></a>Félicitations

Dans ce didacticiel, vous avez appris à importer et à activer le plug-in Microsoft Spatializer et à activer le son spatial sur votre station de travail.
Dans le didacticiel suivant, vous allez apprendre à ajouter de l’audio spatial dans le projet Unity.

> [!div class="nextstepaction"]
> [Didacticiel suivant : 2. sons d’interaction du bouton spatial](unity-spatial-audio-ch2.md)
