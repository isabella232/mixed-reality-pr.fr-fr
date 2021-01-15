---
title: Distribution de vos applications
description: Vue d’ensemble des différentes options de distribution pour les différentes plateformes prises en charge et les magasins de publication.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, réalité mixte, casques immersifs, application, UWP, envoi, envoi, filtres, métadonnées, configuration système requise, Mots clés, wack, certification, package, AppX, merchandising
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215974"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="5cef2-104">Distribution de vos applications</span><span class="sxs-lookup"><span data-stu-id="5cef2-104">Distributing your apps</span></span>

![Lancher d’application 3D d’oiseau flottant dans WMR](images/distribute-hero-image.png)

<span data-ttu-id="5cef2-106">La mise en œuvre de vos applications auprès de vos utilisateurs ou dans le monde entier est l’un des efforts de développement les plus importants et parfois fastidieux.</span><span class="sxs-lookup"><span data-stu-id="5cef2-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="5cef2-107">Nous avons simplifié le processus en un ensemble de ressources, qui dépendent du scénario de distribution et de déploiement qui convient le mieux à votre équipe ou à vous-même.</span><span class="sxs-lookup"><span data-stu-id="5cef2-107">We've simplified the process into a set of resources, which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="5cef2-108">Options de distribution</span><span class="sxs-lookup"><span data-stu-id="5cef2-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="5cef2-109">Si vous partagez votre application avec une autre partie, vous devez générer et fournir le fichier Appx.</span><span class="sxs-lookup"><span data-stu-id="5cef2-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="5cef2-110">Si vous utilisez le programme d’installation d’application, vous devez également partager le certificat avec l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5cef2-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="5cef2-111">Si vous partagez avec une organisation, vous avez besoin d’un compte professionnel ou scolaire et d’un accès à l’infrastructure de [gestion des appareils mobiles (MDM)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) des organisations.</span><span class="sxs-lookup"><span data-stu-id="5cef2-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="5cef2-112">Si vous êtes le tiers du partage, vous devez être administrateur de votre locataire et utiliser le [Centre d’administration Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) pour rendre l’application disponible.</span><span class="sxs-lookup"><span data-stu-id="5cef2-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="5cef2-113">Une autre option consiste à partager le fichier AppX et les dépendances de l’application avec votre utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="5cef2-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="5cef2-114">Si vous êtes l’utilisateur final, l’application est téléchargée automatiquement ou disponible en téléchargement une fois que vous vous êtes inscrit au locataire de l’organisation de partage.</span><span class="sxs-lookup"><span data-stu-id="5cef2-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="5cef2-115"><strong>Scénario</strong></span><span class="sxs-lookup"><span data-stu-id="5cef2-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="5cef2-116"><strong>Installations de l’appareil local</strong></span><span class="sxs-lookup"><span data-stu-id="5cef2-116"><strong>Local device installs</strong></span></span></td>
    <td><span data-ttu-id="5cef2-117"><strong>Partager avec tout le monde</strong></span><span class="sxs-lookup"><span data-stu-id="5cef2-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="5cef2-118"><strong>Partager avec une organisation</strong></span><span class="sxs-lookup"><span data-stu-id="5cef2-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="5cef2-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Programme d’installation d’application</strong></span><span class="sxs-lookup"><span data-stu-id="5cef2-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="5cef2-120">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-120">✔️</span></span></td>
    <td><span data-ttu-id="5cef2-121">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="5cef2-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Portail d’entreprise</strong></a></span><span class="sxs-lookup"><span data-stu-id="5cef2-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="5cef2-123">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="5cef2-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>Installation d’application requise pour MDM</strong></a></span><span class="sxs-lookup"><span data-stu-id="5cef2-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="5cef2-125">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="5cef2-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="5cef2-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="5cef2-127">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-127">✔️</span></span></td>
    <td><span data-ttu-id="5cef2-128">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="5cef2-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store pour Entreprises</strong></a></span><span class="sxs-lookup"><span data-stu-id="5cef2-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="5cef2-130">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="5cef2-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Package d’approvisionnement</strong></a></span><span class="sxs-lookup"><span data-stu-id="5cef2-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="5cef2-132">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-132">✔️</span></span></td>
    <td><span data-ttu-id="5cef2-133">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-133">✔️</span></span></td>
    <td><span data-ttu-id="5cef2-134">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="5cef2-135"><a href="#other-scenarios"><strong>Déploiement Win32 personnalisé</strong></a> (non disponible pour les appareils HoloLens-voir ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="5cef2-135"><a href="#other-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="5cef2-136">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-136">✔️</span></span></td>
    <td><span data-ttu-id="5cef2-137">✔️</span><span class="sxs-lookup"><span data-stu-id="5cef2-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="5cef2-138">Le programme d’installation de l’application n’est actuellement pas disponible pour les appareils gérés ou les appareils HoloLens (1er génération).</span><span class="sxs-lookup"><span data-stu-id="5cef2-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="other-scenarios"></a><span data-ttu-id="5cef2-139">Autres scénarios</span><span class="sxs-lookup"><span data-stu-id="5cef2-139">Other scenarios</span></span>

* <span data-ttu-id="5cef2-140">Vous pouvez produire un Win32. Fichier EXE à l’aide de la cible de build PC standalone d’Unity pour le déploiement d’applications Win32, y compris la transmission de vapeur et de jeu.</span><span class="sxs-lookup"><span data-stu-id="5cef2-140">You can produce a Win32 .EXE file using the PC Standalone build target from Unity for Win32 application deployment, including Steam and Game Pass.</span></span> <span data-ttu-id="5cef2-141">Une fois que vous avez le. EXE, vous pouvez soumettre vos applications comme d’habitude à la plateforme que vous avez choisie.</span><span class="sxs-lookup"><span data-stu-id="5cef2-141">Once you have the .EXE, you can submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="5cef2-142">Si vous devez installer une application HoloLens 2 alors que vous êtes hors connexion, reportez-vous aux instructions [Secure de hololens 2 hors connexion](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) ou installez l’application via un package d’approvisionnement sans activer le mode développeur.</span><span class="sxs-lookup"><span data-stu-id="5cef2-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or install the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="5cef2-143">Vous pouvez également déployer des builds sur votre appareil et les partager avec d’autres développeurs qui ont le mode développeur activé en [déployant et déboguer avec Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) ou en [installant un package d’application avec le portail de l’appareil](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span><span class="sxs-lookup"><span data-stu-id="5cef2-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="5cef2-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cef2-144">See also</span></span>
* [<span data-ttu-id="5cef2-145">Recherche, installation et désinstallation d’applications à partir du Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="5cef2-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

