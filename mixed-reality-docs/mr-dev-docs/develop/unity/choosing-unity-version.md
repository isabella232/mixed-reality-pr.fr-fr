---
title: Choix d’une version Unity et d’un plug-in XR
description: Restez à jour avec les dernières recommandations en matière de plug-in Unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: f37dbdccf175a5cea9a647f0c14b90682b19dfb3
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906854"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Choix d’une version Unity et d’un plug-in XR

Bien que nous **vous recommandons actuellement d’installer unity 2019,4 LTS et d’utiliser des XR intégrées héritées pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019,4 LTS (recommandé)

La configuration d’Unity recommandée de Microsoft pour le développement HoloLens 2 et Windows Mixed Reality est **unity 2019,4 LTS à l’aide** de la prise en charge XR intégrée héritée.

La meilleure façon d’installer et de gérer Unity consiste à utiliser <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>. Une fois l’installation terminée, ouvrez Unity Hub :

1. Sélectionnez l’onglet **installations** , puis choisissez **Ajouter** .
2. Sélectionnez Unity 2019,4 LTS, puis cliquez sur **suivant** .

![Unity Hub instal New version](images/unity-hub-img-2019.png)

3. Vérifiez les composants suivants sous **« plateformes »**
    * **Universal Windows Platform Build Support** 
    * **Windows Build Support (IL2CPP)**

![Option Universal Windows Platform Build Support d’Unity](images/Unity_Install_Option_UWP_2019.png)

4. Si vous avez installé Unity sans ces options, vous pouvez les ajouter via le menu **Ajouter des modules** dans Unity Hub :

![Option Windows Build Support d’Unity](images/Unity_Install_Option_UWP2_2019.png)

Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :

> [!div class="nextstepaction"]
> [Configurer des XR intégrées héritées](./xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.  Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.  Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.

Si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans Unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de Unity 2019 LTS à mi-2022.

## <a name="unity-20203-lts"></a>Unity 2020,3 LTS 

Si vous utilisez **unity 2020,3 LTS**, la recommandation actuelle de Microsoft est le **plug-in OpenXR de réalité mixte** le plus récent. Vous devez utiliser la version de patch Unity 2020.3.8 F1 ou une version ultérieure pour éviter les problèmes de performances connus avec les builds 2020,3 antérieures.

Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager. Cela vous permet d’écrire du code de test de positionnement une fois qui s’étend sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit.

Toutefois, il existe des problèmes connus qui affectent les projets LTS Unity 2020 :

* Le pipeline de rendu universel (URP) 10.5.0 ou antérieur présente des pénalités en matière de performances sur les appareils HoloLens 2.

Si vous choisissez de démarrer un nouveau projet dans Unity 2020 aujourd’hui, veillez à suivre les semaines à venir pour les builds Unity et les packages URP mis à jour avant d’expédier votre application.  Cela permet de s’assurer que vos utilisateurs connaissent une stabilité d’hologramme appropriée.

> [!div class="nextstepaction"]
> [Utilisation du plug-in OpenXR](./xr-project-setup.md?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021,1

Si vous essayez les builds **2021,1 premières Unity** , vous devez avancer jusqu’au **plug-in OpenXR**, car le plug-in Windows XR est déconseillé ici.  À partir de Unity 2021,2, le plug-in OpenXR sera le seul chemin pour le développement de la réalité mixte, car le plug-in Windows XR ne sera plus pris en charge.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Si vous disposez déjà d’un projet utilisant Unity 2018,4 LTS, votre moteur Unity continue d’être pris en charge pendant 2 ans après sa sortie.  Unity 2018 LTS atteindra la fin du service au printemps de 2021.