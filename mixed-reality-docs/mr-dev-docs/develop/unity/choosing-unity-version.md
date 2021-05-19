---
title: Choix d’une version Unity et d’un plug-in XR
description: Restez à jour avec les dernières recommandations en matière de plug-in Unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: 3bdaa35f495d7a647a7cbf37ddcd4f85e96d74d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143670"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Choix d’une version Unity et d’un plug-in XR

Bien que nous **vous recommandons actuellement d’installer unity 2019,4 LTS et d’utiliser des XR intégrées héritées pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019,4 LTS (recommandé)

La configuration d’Unity recommandée de Microsoft pour le développement HoloLens 2 et Windows Mixed Reality est **unity 2019,4 LTS à l’aide** de la prise en charge XR intégrée héritée.

La meilleure façon d’installer et de gérer Unity consiste à utiliser <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>. Une fois l’installation terminée, ouvrez Unity Hub :

1. Sélectionnez l’onglet **installations** , puis choisissez **Ajouter** .
2. Sélectionnez Unity 2019,4 LTS, puis cliquez sur **suivant** .

![Unity Hub instal New version](images/unity-hub-img-01.png)

3. Vérifiez les composants suivants sous **« plateformes »**
    * **Universal Windows Platform Build Support** 
    * **Windows Build Support (IL2CPP)**

![Option Universal Windows Platform Build Support d’Unity](../images/Unity_Install_Option_UWP.png)

4. Si vous avez installé Unity sans ces options, vous pouvez les ajouter via le menu **Ajouter des modules** dans Unity Hub :

![Option Windows Build Support d’Unity](../images/Unity_Install_Option_UWP2.png)

Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :

> [!div class="nextstepaction"]
> [Configurer des XR intégrées héritées](legacy-xr-support.md)

> [!NOTE]
> Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.  Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.  Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.

Si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans Unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de Unity 2019 LTS à mi-2022.

## <a name="unity-20203-lts"></a>Unity 2020,3 LTS 

Si vous utilisez **unity 2020,3 LTS**, vous pouvez utiliser le **plug-in Windows XR** pour développer des applications HoloLens 2 et Windows Mixed Reality.

Toutefois, il existe des problèmes connus qui affectent la stabilité des hologrammes et d’autres fonctionnalités de HoloLens 2 : 

* Les applications de communication à distance des applications holographiques utilisant la cible de génération plateforme Windows universelle ne fonctionnent pas.
* Le système de travaux graphiques Unity est activé par défaut, même s’il n’est pas compatible avec les projets HoloLens.

Si vous choisissez de démarrer un nouveau projet dans Unity 2020 aujourd’hui, veillez à suivre les mois à venir pour les builds Unity mises à jour et les builds de plug-in Windows XR avant d’expédier votre application.  Cela permet de s’assurer que vos utilisateurs connaissent une stabilité d’hologramme appropriée.

> [!div class="nextstepaction"]
> [Utilisation du plug-in XR Windows](windows-xr-plugin.md)

### <a name="using-openxr"></a>Utilisation de OpenXR

Unity 2020,3 LTS prend également en charge une version préliminaire publique du plug-in **OpenXR de réalité mixte** .

Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager. Cela vous permet d’écrire du code de test de positionnement une fois qui s’étend sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit. 

Plus tard cette année, **unity 2020,3 LTS avec le plug-in OpenXR** deviendra la configuration Unity recommandée, et les futures fonctionnalités HoloLens 2 d’Unity seront exposées uniquement par le biais de ce plug-in.

> [!div class="nextstepaction"]
> [Utilisation du plug-in OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021,1

Si vous essayez les builds **2021,1 premières Unity** , vous devez avancer jusqu’au **plug-in OpenXR**, car le plug-in Windows XR est déconseillé ici.  À partir de Unity 2021,2, le plug-in OpenXR sera le seul chemin pour le développement de la réalité mixte, car le plug-in Windows XR ne sera plus pris en charge.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Si vous disposez déjà d’un projet utilisant Unity 2018,4 LTS, votre moteur Unity continue d’être pris en charge pendant 2 ans après sa sortie.  Unity 2018 LTS atteindra la fin du service au printemps de 2021.
