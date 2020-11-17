---
title: Didacticiels audio spatial-1. Ajout de données audio spatiales à votre projet
description: Ajoutez le plug-in Microsoft Spatializer à votre projet Unity pour accéder au déchargement matériel HoloLens 2 HRTF.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: fc657eb22034c1c3fd31aadedfe7b8ea7bb8447d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679708"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Ajout de données audio spatiales à votre projet Unity

Bienvenue dans le didacticiel sur l’audio spatial pour Unity sur HoloLens2. Cette séquence de didacticiel présente les éléments suivants :
* Comment utiliser le déchargement de la fonction de transfert HRTF sur HoloLens 2 dans Unity
* Comment activer le réverbe lors de l’utilisation du déchargement HRTF

Le [dépôt github Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) a un projet Unity terminé de cette séquence de didacticiels. 

Pour savoir à quoi cela sert à spatialiser des sons à l’aide des technologies Spatialization basées sur HRTF et des recommandations pour savoir quand cela peut être utile, consultez [conception de son spatial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Qu’est-ce que le déchargement HRTF ?
Le traitement de l’audio à l’aide d’algorithmes basés sur HRTF nécessite une grande quantité de calcul spécialisé. HoloLens 2 comprend un matériel dédié qui peut être utilisé pour éviter la charge du processeur d’application, ce qui « décharge » le traitement des algorithmes basés sur HRTF.  Le plug-in Microsoft Spatializer offre un moyen simple pour votre application de tirer parti du matériel HRTF dédié afin que votre application puisse utiliser davantage de processeurs d’applications pour les opérations autres que l’audio spatial.

## <a name="objectives"></a>Objectifs
Dans ce premier chapitre, vous allez :
* Créer un projet Unity et importer MRTK
* Importer le plug-in Microsoft Spatializer
* Activer le plug-in Microsoft Spatializer
* Activer l’audio spatial sur votre station de travail de développeur

## <a name="create-a-project-and-add-nuget-for-unity"></a>Créer un projet et ajouter NuGet pour Unity
Commencez avec un projet Unity vide, puis ajoutez et configurez NuGet pour Unity :
1. Téléchargez la dernière version de [NuGetForUnity. pour Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. Dans la barre de menus Unity, cliquez sur **ressources-> importer un package-> package personnalisé...** et installer le package NuGetForUnity :

![Importer un package personnalisé](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Ajouter le package Windows Mixed Reality
La prise en charge de Windows Mixed Reality dans Unity 2019 et versions ultérieures est contenue dans un package facultatif. Pour l’ajouter à votre projet, ouvrez la **fenêtre > gestionnaire de package** à partir de la barre de menus Unity :

![Menu du gestionnaire de package](images/spatial-audio/package-manager-menu.png)

Recherchez et installez le package **Windows Mixed Reality** :

![Fenêtre du gestionnaire de package](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>Installer MRTK et Microsoft Spatializer
À l’aide de NuGet pour Unity, installez les plug-ins MRTK et Microsoft Spatializer :
1. Dans la barre de menus de Unity, cliquez sur **NuGet-> gérer les packages NuGet**.

![Gérer des packages NuGet](images/spatial-audio/manage-nuget-packages.png)

2. Dans la zone de **recherche** , entrez « Microsoft. MixedReality. Toolkit » et installez le package MRTK Core : **Microsoft. MixedReality. Toolkit. Foundation**

![Package NuGet MRTK](images/spatial-audio/mrtk-nuget-package.png)

Le [package NuGet MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) contient un contexte et des détails supplémentaires.

4. Dans la zone de **recherche** , entrez « Microsoft. SpatialAudio » et installez le package Microsoft Spatializer : **Microsoft. SpatialAudio. Spatializer. Unity**

![Plug-in Spatializer NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>Configurer MRTK dans votre projet

1. Ouvrez la fenêtre Paramètres de build en accédant à **fichiers-> paramètres de build**.

2. Sélectionnez le _plateforme Windows universelle_ , puis cliquez sur **basculer la plateforme**.

3. Cliquez sur **paramètres du lecteur** dans la **fenêtre générer** pour ouvrir les propriétés des **paramètres du lecteur** dans le volet **inspecteur** .
    * Sous **paramètres de XR**, activez la case à cocher **réalité virtuelle prise en charge**
    * Sous **paramètres XR**, définissez le **mode de rendu stéréo** sur **Single-instanced**.
    * Sous **paramètres de publication**, activez la case à cocher **perception spatiale** dans la section **fonctionnalités** .

4. Dans la barre de menus, cliquez sur **Kit de pratiques de réalité mixte-> ajouter à la scène et configurer.** pour ajouter MRTK à votre scène.

Pour obtenir des conseils supplémentaires, notamment la façon de créer votre application et de la déployer sur un HoloLens 2, consultez [le chapitre 1 du module de base de l’apprentissage de RM](../../../mrlearning-base-ch1.md).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Activer le plug-in Microsoft Spatializer
Activez le plug-in **Microsoft Spatializer** . Ouvrez les **paramètres de projet Edit->-> audio**, puis remplacez le **plug-in Spatializer** par "Microsoft Spatializer". La section **audio** des **paramètres du projet** doit maintenant ressembler à ceci :

![Paramètres du projet présentant le plug-in Spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Activer l’audio spatial sur votre station de travail
Sur les versions de bureau de Windows, l’audio spatial est désactivé par défaut. Pour l’activer, cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches. Pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2, choisissez **son Spatial > Windows Sonic pour casque**.

![Paramètres audio spatiaux du Bureau](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> Ce paramètre est requis uniquement si vous envisagez de tester votre projet dans l’éditeur Unity.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Audio spatial Unity-chapitre 2](unity-spatial-audio-ch2.md)

