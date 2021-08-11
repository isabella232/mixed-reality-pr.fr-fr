---
title: Distribution de vos applications
description: Vue d’ensemble des différentes options de distribution pour les différentes plateformes prises en charge et les magasins de publication.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, réalité mixte, casques immersifs, application, uwp, envoi, envoi, filtres, métadonnées, configuration système requise, mots clés, wack, certification, package, appx, merchandising
ms.openlocfilehash: 7d4fbc1a7a5767ad8276017c7cdc38e9bb436bc83b12a4d8caeb9a8d84f1caca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198781"
---
# <a name="distributing-your-apps"></a>Distribution de vos applications

![Lancher d’application 3D d’oiseau flottant dans WMR](images/distribute-hero-image.png)

La mise en œuvre de vos applications auprès de vos utilisateurs ou dans le monde entier est l’un des efforts de développement les plus importants et parfois fastidieux. Nous avons simplifié le processus en un ensemble de ressources, qui dépendent du scénario de distribution et de déploiement qui convient le mieux à votre équipe ou à vous-même.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Options de distribution

> [!IMPORTANT]
> * Si vous partagez votre application avec une autre partie, vous devez générer et fournir le fichier Appx. 
>     * Si vous utilisez le programme d’installation d’application, vous devez également partager le certificat avec l’utilisateur.
> 
> * Si vous partagez avec une organisation, vous avez besoin d’un compte professionnel ou scolaire et d’un accès à l’infrastructure de [gestion des appareils mobiles (MDM)](/hololens/hololens-enroll-mdm) des organisations.  
>    * si vous êtes le tiers du partage, vous devez être administrateur de votre locataire et utiliser le [centre d’administration Microsoft Endpoint Manager](/mem/intune/apps/apps-deploy) pour rendre l’application disponible. Une autre option consiste à partager le fichier AppX et les dépendances de l’application avec votre utilisateur final.
>    * Si vous êtes l’utilisateur final, l’application est téléchargée automatiquement ou disponible en téléchargement une fois que vous vous êtes inscrit au locataire de l’organisation de partage. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Scénario</strong></td>
    <td><strong>Installations de l’appareil local</strong></td>
    <td><strong>Partager avec tout le monde</strong></td>
    <td><strong>Partager avec une organisation</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Programme d’installation d’application</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>MDM-Portail d’entreprise</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>Installation d’application requise pour MDM</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store pour Entreprises</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-provisioning-package"><strong>Package de provisionnement</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>déploiement Win32 personnalisé</strong></a> (non disponible pour HoloLens appareils-voir ci-dessous)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> le programme d’installation de l’application n’est actuellement pas disponible pour les appareils gérés ou les appareils HoloLens (1er génération).

## <a name="other-scenarios"></a>Autres scénarios

* Vous pouvez produire un fichier de .EXE Win32 à l’aide de la cible de build PC Standalone à partir d’Unity pour le déploiement d’applications Win32, y compris la vapeur et les Game Pass. Une fois que vous disposez de la .EXE, vous pouvez soumettre vos applications comme d’habitude à la plateforme que vous avez choisie. 

* si vous devez installer une application HoloLens 2 lorsque vous êtes hors connexion, reportez-vous aux instructions de [HoloLens 2 sécurisées hors connexion](/hololens/hololens-common-scenarios-offline-secure) ou installez l’application via un Package d’approvisionnement sans activer le mode développeur.

* vous pouvez également déployer des builds sur votre appareil et les partager avec d’autres développeurs qui ont le Mode développeur activé en [déployant et en déboguant avec Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) ou en [installant un package d’application avec le portail de l’appareil](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>Voir aussi
* [Recherche, installation et désinstallation d’applications à partir du Microsoft Store](/hololens/holographic-store-apps)