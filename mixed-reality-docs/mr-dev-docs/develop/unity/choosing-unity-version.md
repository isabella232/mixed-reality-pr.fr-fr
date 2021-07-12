---
title: Choix d’une version Unity et d’un plug-in XR
description: restez à jour avec les dernières recommandations en matière de plug-in unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603680"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Choix d’une version Unity et d’un plug-in XR

Bien que nous **vous recommandons actuellement d’installer unity 2020,3 LTS avec le dernier plug-in OpenXR de réalité mixte pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020,3 LTS (recommandé)

la configuration d’unity recommandée de Microsoft pour le développement de HoloLens 2 et d’Windows Mixed Reality est **unity 2020,3 LTS avec le dernier plug-in OpenXR de réalité mixte**. Vous **devez** utiliser la version de patch Unity 2020.3.8 F1 ou une version ultérieure pour éviter les problèmes de performances connus avec les builds 2020,3 antérieures.

> [!IMPORTANT]
> unity 2020 ne prend pas en charge le ciblage HoloLens (1er génération). Ces casques restent pris en charge dans **[unity 2019 LTS](#unity-20194-lts)** avec des XR intégrés hérités pour le cycle de vie complet de unity 2019 LTS à mi-2022.

La meilleure façon d’installer et de gérer Unity consiste à utiliser le **concentrateur Unity**:

1. Installez <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.
2. Sélectionnez l’onglet **installations** , puis choisissez **Ajouter**.
3. Sélectionnez **unity 2020,3 LTS** , puis cliquez sur **suivant**.

![Installation d’Unity Hub-nouvelle version](images/unity-hub-img-01.png)

4. Vérifiez les composants suivants sous **« plateformes »**:
    * **Universal Windows Platform Build Support**
    * **Windows Build Support (IL2CPP)**

![Option Universal Windows Platform Build Support d’Unity](../images/Unity_Install_Option_UWP.png)

5. Si vous avez déjà installé Unity sans ces options, vous pouvez les ajouter via le menu **« Ajouter des modules »** dans Unity Hub :

![Option Windows Build Support d’Unity](../images/Unity_Install_Option_UWP2.png)

Une fois Unity 2020,3 installé, commencez à créer un projet ou à mettre à niveau un projet existant à l’aide du plug-in OpenXR de la réalité mixte :

> [!div class="nextstepaction"]
> [Configurer votre projet avec le plug-in OpenXR](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> bien que nous vous recommandons d’utiliser OpenXR pour tous les nouveaux projets, unity 2020,3 LTS prend également en charge le [plug-in XR Windows](xr-project-setup.md?tabs=windowsxr). Ce plug-in est entièrement pris en charge, bien qu’il ne reçoive pas de nouvelles fonctionnalités telles que la prise en charge de comptabilité clients 4,0.

## <a name="unity-20194-lts"></a>Unity 2019,4 LTS

Si vous devez utiliser Unity 2019, vous pouvez utiliser **unity 2019 LTS avec des XR intégrées héritées**. Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :

> [!div class="nextstepaction"]
> [Configurer votre projet avec des XR intégrées héritées](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.  Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.  Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.

si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de unity 2019 LTS à mi-2022.

## <a name="unity-20212"></a>Unity 2021,2

Si vous essayez les builds **2021,2 premières Unity** , commencez avec le [**plug-in OpenXR de la réalité mixte**](xr-project-setup.md?tabs=openxr). le plug-in OpenXR est le seul chemin d’accès pour le développement de réalité mixte dans unity 2021,2 et versions ultérieures, car la version unity finale qui prend en charge le plug-in Windows XR était unity 2021,1.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Unity 2018,4 LTS a atteint la fin de la période de prise en charge de deux Long-Term ans d’Unity et ne reçoit plus de mises à jour d’Unity, bien que vos projets continuent de s’exécuter.

Si vous avez un projet Unity 2018, vous devez envisager de planifier une migration vers Unity 2020,3 LTS et le plug-in OpenXR de réalité mixte.