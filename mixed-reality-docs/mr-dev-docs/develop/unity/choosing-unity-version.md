---
title: Choix d’une version Unity et d’un plug-in XR
description: Restez à jour avec les dernières recommandations en matière de plug-in Unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080696"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Choix d’une version Unity et d’un plug-in XR

Bien que nous **vous recommandons actuellement d’installer unity 2020,3 LTS avec le dernier plug-in OpenXR de réalité mixte pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020,3 LTS (recommandé)

La configuration d’Unity recommandée de Microsoft pour le développement HoloLens 2 et Windows Mixed Reality est **unity 2020,3 LTS avec le plug-in OpenXR de réalité mixte le plus récent**. Vous devez utiliser la version de patch Unity 2020.3.8 F1 ou une version ultérieure pour éviter les problèmes de performances connus avec les builds 2020,3 antérieures.

> [!IMPORTANT]
> Unity 2020 ne prend pas en charge le ciblage HoloLens (1re génération). Ces casques restent pris en charge dans **[unity 2019 LTS](#unity-20194-lts)** avec des XR intégrés hérités pour le cycle de vie complet de unity 2019 LTS à mi-2022.
>
> [!NOTE]
> Le rendu à distance Azure n’a pas encore fourni une version mise à jour prenant en charge Unity 2020.
>
> Si votre projet Unity utilise le rendu distant Azure, nous vous recommandons de ne pas mettre à niveau votre projet vers Unity 2020 jusqu’à ce qu’un package mis à jour soit disponible.

<a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a> est le meilleur moyen d’installer et de gérer Unity. Une fois l’installation terminée, ouvrez Unity Hub :

1. Sélectionnez l’onglet **installations** , puis choisissez **Ajouter** .
2. Sélectionnez Unity 2020,3 LTS, puis cliquez sur **suivant** .

![Unity Hub instal New version](images/unity-hub-img-01.png)

3. Vérifiez les composants suivants sous **« plateformes »**
    * **Universal Windows Platform Build Support**
    * **Windows Build Support (IL2CPP)**

![Option Universal Windows Platform Build Support d’Unity](../images/Unity_Install_Option_UWP.png)

4. Si vous avez installé Unity sans ces options, vous pouvez les ajouter via le menu **Ajouter des modules** dans Unity Hub :

![Option Windows Build Support d’Unity](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [Utilisation du plug-in OpenXR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> Bien que nous vous recommandons d’utiliser OpenXR pour tous les nouveaux projets, Unity 2020,3 LTS prend également en charge le [plug-in XR de Windows](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr). Ce plug-in est entièrement pris en charge, bien qu’il ne reçoive pas de nouvelles fonctionnalités telles que la prise en charge de comptabilité clients 4,0.

## <a name="unity-20194-lts"></a>Unity 2019,4 LTS

Si vous devez utiliser Unity 2019, vous pouvez utiliser **unity 2019 LTS avec des XR intégrées héritées**. Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :

> [!div class="nextstepaction"]
> [Configurer des XR intégrées héritées](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.  Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.  Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.

Si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans Unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de Unity 2019 LTS à mi-2022.

## <a name="unity-20211"></a>Unity 2021,1

Si vous essayez les builds **2021,1 premières Unity** , vous devez avancer jusqu’au **plug-in OpenXR**, car le plug-in Windows XR est déconseillé ici.  À partir de Unity 2021,2, le plug-in OpenXR sera le seul chemin pour le développement de la réalité mixte, car le plug-in Windows XR ne sera plus pris en charge.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Si vous disposez déjà d’un projet utilisant Unity 2018,4 LTS, votre moteur Unity continue d’être pris en charge pendant 2 ans après sa sortie.  Unity 2018 LTS atteindra la fin du service au printemps de 2021.
