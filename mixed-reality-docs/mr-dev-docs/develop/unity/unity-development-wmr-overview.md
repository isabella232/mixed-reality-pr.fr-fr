---
title: Développement Unity pour VR
description: Prise en main de la création d’applications de réalité mixte dans Unity pour les casques immersifs VR et Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, portage, fonctionnalité, caméra, simulation, émulation, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, qu’est-ce que la réalité virtuelle, qu’est-ce que la réalité augmentée, MRTK, mixed reality toolkit, entrée vocale, caméra localisable, émulateur, Azure, tutoriels
ms.openlocfilehash: edd75def71ad31a1d29a480d0b2a7f7ffbd8c037
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226428"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="b06e5-104">Développement Unity pour VR et Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b06e5-104">Unity development for VR and Windows Mixed Reality</span></span>

![Logo de bannière Unity](../images/unity_logo_banner.png)

<span data-ttu-id="b06e5-106">Si vous débutez avec Unity, nous vous recommandons d’explorer les [tutoriels](https://unity3d.com/learn/tutorials) de niveau débutant sur la plateforme Unity Learn avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b06e5-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="b06e5-107">Vous pouvez également consulter les [forums de réalité mixte Unity](https://forum.unity3d.com/forums/hololens.102/) afin d’entrer en contact avec la communauté en ligne qui crée des applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="b06e5-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="b06e5-108">Vous pourriez y trouver des ressources ou solutions très intéressantes.</span><span class="sxs-lookup"><span data-stu-id="b06e5-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="b06e5-109">Quand vous êtes prêt à prendre en main MRTK, passez en revue les points de contrôle de développement ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b06e5-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b06e5-110">Consultez nos **[guides de portage](../porting-apps/porting-overview.md)** si vous avez un projet Unity existant que vous voulez porter sur un casque immersif Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b06e5-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="b06e5-111">Points de contrôle de développement</span><span class="sxs-lookup"><span data-stu-id="b06e5-111">Development checkpoints</span></span>

<span data-ttu-id="b06e5-112">Utilisez les points de contrôle suivants pour intégrer vos jeux et applications Unity dans le monde de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="b06e5-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="b06e5-113">1. Mise en route</span><span class="sxs-lookup"><span data-stu-id="b06e5-113">1. Getting started</span></span>

<span data-ttu-id="b06e5-114">Vous devrez modifier manuellement un petit ensemble de paramètres Unity pour le développement Windows Mixed Reality et VR.</span><span class="sxs-lookup"><span data-stu-id="b06e5-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR developoment.</span></span> <span data-ttu-id="b06e5-115">Ceux-ci sont divisés en deux catégories : par projet et par scène.</span><span class="sxs-lookup"><span data-stu-id="b06e5-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="b06e5-116">À la fin de cette section, vous disposerez des outils et des paramètres de projet pour commencer à créer vos propres applications.</span><span class="sxs-lookup"><span data-stu-id="b06e5-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="b06e5-117">Point de contrôle</span><span class="sxs-lookup"><span data-stu-id="b06e5-117">Checkpoint</span></span>  |  <span data-ttu-id="b06e5-118">Résultat</span><span class="sxs-lookup"><span data-stu-id="b06e5-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="b06e5-119">Installer les outils les plus récents</span><span class="sxs-lookup"><span data-stu-id="b06e5-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="b06e5-120">Téléchargez et installez le dernier package Unity et configurez votre projet pour la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="b06e5-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="b06e5-121">Configuration de votre projet pour WMR</span><span class="sxs-lookup"><span data-stu-id="b06e5-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="b06e5-122">Découvrez comment créer des applications qui restituent du contenu numérique sur des périphériques d‘affichage holographiques et VR</span><span class="sxs-lookup"><span data-stu-id="b06e5-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="b06e5-123">2. Fonctionnalités principales</span><span class="sxs-lookup"><span data-stu-id="b06e5-123">2. Core building blocks</span></span>

<span data-ttu-id="b06e5-124">Après avoir démarré un nouveau projet immersif, vous aurez besoin de quelques composants de base pour développer des applications immersives.</span><span class="sxs-lookup"><span data-stu-id="b06e5-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="b06e5-125">Tous les composants principaux pour les applications de réalité mixte sont exposés de manière cohérente avec les autres API Unity.</span><span class="sxs-lookup"><span data-stu-id="b06e5-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="b06e5-126">Vous n’aurez peut-être pas besoin de tous les composants à la fois, mais nous vous recommandons de les explorer dès le départ.</span><span class="sxs-lookup"><span data-stu-id="b06e5-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="b06e5-127">Après avoir exploré les composants de base listés ci-dessous, vous disposerez d’une boîte à outils riche en fonctionnalités, que vous pourrez intégrer dans un projet VR.</span><span class="sxs-lookup"><span data-stu-id="b06e5-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="b06e5-128">3. Fonctionnalités avancées</span><span class="sxs-lookup"><span data-stu-id="b06e5-128">3. Advanced features</span></span>

<span data-ttu-id="b06e5-129">D’autres fonctionnalités clés jouant un rôle dans les applications immersives sont disponibles via des API Unity sans aucun package ou configuration supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b06e5-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="b06e5-130">Après avoir exploré les fonctionnalités plus avancées offertes par Unity, vous serez en mesure de créer des applications VR complexes et plus approfondies.</span><span class="sxs-lookup"><span data-stu-id="b06e5-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="b06e5-131">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="b06e5-131">Feature</span></span>  |  <span data-ttu-id="b06e5-132">Fonctions</span><span class="sxs-lookup"><span data-stu-id="b06e5-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="b06e5-133">Perte de suivi</span><span class="sxs-lookup"><span data-stu-id="b06e5-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="b06e5-134">Gérez des scénarios dans lesquels votre appareil ne peut pas se trouver dans l’espace universel des applications.</span><span class="sxs-lookup"><span data-stu-id="b06e5-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="b06e5-135">Saisie au clavier</span><span class="sxs-lookup"><span data-stu-id="b06e5-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="b06e5-136">Bénéficiez d’une entrée à partir de claviers réels et de réalité mixte dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="b06e5-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="b06e5-137">4. Déploiement sur un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="b06e5-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="b06e5-138">Une fois que votre projet Unity holographique est prêt à être testé, l’étape suivante consiste à exporter et à créer une solution Visual Studio Unity.</span><span class="sxs-lookup"><span data-stu-id="b06e5-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="b06e5-139">Avec cette solution Visual Studio, vous pouvez exécuter votre application sur des appareils réels ou simulés.</span><span class="sxs-lookup"><span data-stu-id="b06e5-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="b06e5-140">À la fin de cette section, vous serez en mesure de déployer votre application sur un appareil ou un émulateur adapté à vos besoins de développement.</span><span class="sxs-lookup"><span data-stu-id="b06e5-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="b06e5-141">Casque immersif Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b06e5-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="b06e5-142">Simulateur de casque immersif Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b06e5-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="b06e5-143">Quelle est l’étape suivante ?</span><span class="sxs-lookup"><span data-stu-id="b06e5-143">What's next?</span></span>

<span data-ttu-id="b06e5-144">Le travail d’un développeur n’est jamais terminé, en particulier lorsqu’il s’agit d’apprendre un nouvel outil ou kit SDK.</span><span class="sxs-lookup"><span data-stu-id="b06e5-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="b06e5-145">Les sections suivantes peuvent vous amener dans des domaines qui vont au-delà de la documentation niveau débutant que vous connaissez déjà, et vous fournir des ressources utiles si vous êtes bloqué.</span><span class="sxs-lookup"><span data-stu-id="b06e5-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="b06e5-146">Notez que ces rubriques et ressources ne sont pas listées dans un ordre séquentiel particulier. N’hésitez donc pas à vous y plonger et à les explorer !</span><span class="sxs-lookup"><span data-stu-id="b06e5-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="b06e5-147">Portage</span><span class="sxs-lookup"><span data-stu-id="b06e5-147">Porting</span></span>

<span data-ttu-id="b06e5-148">Si vous voulez effectuer le portage d’applications existantes, consultez les articles ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="b06e5-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="b06e5-149">Portage d’applications VR sur Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b06e5-149">Porting VR apps to Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project)
* [<span data-ttu-id="b06e5-150">Mise à jour des applications SteamVR pour Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b06e5-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)

### <a name="additional-resources"></a><span data-ttu-id="b06e5-151">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b06e5-151">Additional resources</span></span>

<span data-ttu-id="b06e5-152">Avant de vous lancer dans le monde de la réalité mixte, nous vous recommandons de consulter la documentation supplémentaire ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b06e5-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="b06e5-153">Guide pour les passionnés de RV</span><span class="sxs-lookup"><span data-stu-id="b06e5-153">VR enthusiast guide</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="b06e5-154">Magasin de ressources Unity</span><span class="sxs-lookup"><span data-stu-id="b06e5-154">Unity Asset Store</span></span>](https://www.assetstore.unity3d.com)

## <a name="see-also"></a><span data-ttu-id="b06e5-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b06e5-155">See also</span></span> 

* [<span data-ttu-id="b06e5-156">Paramètres recommandés pour Unity</span><span class="sxs-lookup"><span data-stu-id="b06e5-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="b06e5-157">Recommandations de performances pour Unity</span><span class="sxs-lookup"><span data-stu-id="b06e5-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="b06e5-158">Exportation et création de solutions Unity Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b06e5-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="b06e5-159">Bonnes pratiques sur l’utilisation d’Unity et de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b06e5-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
