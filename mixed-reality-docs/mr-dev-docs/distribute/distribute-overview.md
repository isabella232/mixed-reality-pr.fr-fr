---
title: Distribution de vos applications
description: Vue d’ensemble des différentes options de distribution pour les différentes plateformes prises en charge et les magasins de publication.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, réalité mixte, casques immersifs, application, UWP, envoi, envoi, filtres, métadonnées, configuration système requise, Mots clés, wack, certification, package, AppX, merchandising
ms.openlocfilehash: 5c7a1d6e00610a4046bd71b07ca5184399c9e335
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925777"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="cac81-104">Distribution de vos applications</span><span class="sxs-lookup"><span data-stu-id="cac81-104">Distributing your apps</span></span>

![Lancher d’application 3D d’oiseau flottant dans WMR](images/distribute-hero-image.png)

<span data-ttu-id="cac81-106">La mise en œuvre de vos applications auprès de vos utilisateurs ou dans le monde entier est l’un des efforts de développement les plus importants et parfois fastidieux.</span><span class="sxs-lookup"><span data-stu-id="cac81-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="cac81-107">Nous avons simplifié le processus en un ensemble de ressources listées ci-dessous, qui dépendent toutes du scénario de distribution et de déploiement qui convient le mieux à votre équipe ou à vous-même.</span><span class="sxs-lookup"><span data-stu-id="cac81-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="cac81-108">Options de distribution</span><span class="sxs-lookup"><span data-stu-id="cac81-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="cac81-109">Si vous partagez votre application avec une autre partie, vous devez générer et fournir le fichier Appx.</span><span class="sxs-lookup"><span data-stu-id="cac81-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="cac81-110">Si vous utilisez le programme d’installation d’application, vous devez également partager le certificat avec l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cac81-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="cac81-111">Si vous partagez avec une organisation, vous avez besoin d’un compte professionnel ou scolaire et d’un accès à l’infrastructure de [gestion des appareils mobiles (MDM)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) des organisations.</span><span class="sxs-lookup"><span data-stu-id="cac81-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="cac81-112">Si vous êtes le tiers du partage, vous devez être administrateur de votre locataire et utiliser le [Centre d’administration Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) pour rendre l’application disponible.</span><span class="sxs-lookup"><span data-stu-id="cac81-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="cac81-113">Une autre option consiste à partager le fichier AppX et les dépendances de l’application avec votre utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="cac81-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="cac81-114">Si vous êtes l’utilisateur final, l’application est téléchargée automatiquement ou disponible en téléchargement une fois que vous vous êtes inscrit au locataire de l’organisation de partage.</span><span class="sxs-lookup"><span data-stu-id="cac81-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="cac81-115"><strong>Scénario</strong></span><span class="sxs-lookup"><span data-stu-id="cac81-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="cac81-116"><strong>Installation de l’appareil local</strong></span><span class="sxs-lookup"><span data-stu-id="cac81-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="cac81-117"><strong>Partager avec tout le monde</strong></span><span class="sxs-lookup"><span data-stu-id="cac81-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="cac81-118"><strong>Partager avec une organisation</strong></span><span class="sxs-lookup"><span data-stu-id="cac81-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cac81-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Programme d’installation</strong></a> de l’application (via les <a href="https://docs.microsoft.com/hololens/hololens-insider">Builds Windows Insider</a>)</span><span class="sxs-lookup"><span data-stu-id="cac81-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></a> (through <a href="https://docs.microsoft.com/hololens/hololens-insider">Windows Insider builds</a>)</span></span></td>
    <td><span data-ttu-id="cac81-120">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-120">✔️</span></span></td>
    <td><span data-ttu-id="cac81-121">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="cac81-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Portail d’entreprise</strong></a></span><span class="sxs-lookup"><span data-stu-id="cac81-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="cac81-123">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cac81-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>Installation d’application requise pour MDM</strong></a></span><span class="sxs-lookup"><span data-stu-id="cac81-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="cac81-125">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cac81-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="cac81-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="cac81-127">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-127">✔️</span></span></td>
    <td><span data-ttu-id="cac81-128">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cac81-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store pour Entreprises</strong></a></span><span class="sxs-lookup"><span data-stu-id="cac81-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="cac81-130">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cac81-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Package d’approvisionnement</strong></a></span><span class="sxs-lookup"><span data-stu-id="cac81-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="cac81-132">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-132">✔️</span></span></td>
    <td><span data-ttu-id="cac81-133">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-133">✔️</span></span></td>
    <td><span data-ttu-id="cac81-134">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="cac81-135"><a href="#additional-scenarios"><strong>Déploiement Win32 personnalisé</strong></a> (non disponible pour les appareils HoloLens-voir ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="cac81-135"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="cac81-136">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-136">✔️</span></span></td>
    <td><span data-ttu-id="cac81-137">✔️</span><span class="sxs-lookup"><span data-stu-id="cac81-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="cac81-138">Le programme d’installation de l’application n’est actuellement pas disponible pour les appareils gérés ou les appareils HoloLens (1er génération).</span><span class="sxs-lookup"><span data-stu-id="cac81-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="cac81-139">Autres cas de figure</span><span class="sxs-lookup"><span data-stu-id="cac81-139">Additional scenarios</span></span>

* <span data-ttu-id="cac81-140">Pour le déploiement d’applications Win32, y compris la transmission de vapeur et de jeu, vous pouvez produire un Win32. Fichier EXE à l’aide de la cible de build PC Standalone à partir d’Unity et envoyez vos applications normalement à la plateforme choisie.</span><span class="sxs-lookup"><span data-stu-id="cac81-140">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="cac81-141">Si vous devez installer une application HoloLens 2 alors que vous êtes hors connexion, reportez-vous aux instructions de sécurité de l’application [hololens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) ou installez l’application par le biais d’un package d’approvisionnement sans activer le mode développeur.</span><span class="sxs-lookup"><span data-stu-id="cac81-141">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="cac81-142">Vous pouvez également déployer des builds sur votre appareil et les partager avec d’autres développeurs qui ont le mode développeur activé en [déployant et déboguer avec Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) ou en [installant un package d’application avec le portail de l’appareil](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span><span class="sxs-lookup"><span data-stu-id="cac81-142">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="cac81-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cac81-143">See also</span></span>
* [<span data-ttu-id="cac81-144">Recherche, installation et désinstallation d’applications à partir du Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="cac81-144">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
