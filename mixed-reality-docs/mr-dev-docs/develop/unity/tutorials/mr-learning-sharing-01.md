---
title: Présentation des tutoriels sur les fonctionnalités multi-utilisateurs
description: Suivez ce cours pour découvrir comment implémenter des expériences multi-utilisateurs partagées dans une application HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, fonctionnalités multi-utilisateurs, Photon, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure
ms.localizationpriority: high
ms.openlocfilehash: c18bd7c10ed042278053a51c2d1894564000dfe2
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699018"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a><span data-ttu-id="dbebb-104">1. Présentation des tutoriels sur les fonctionnalités multi-utilisateurs</span><span class="sxs-lookup"><span data-stu-id="dbebb-104">1. Introduction to the Multi-user capabilities tutorials</span></span>

<span data-ttu-id="dbebb-105">Bienvenue dans les tutoriels sur les fonctionnalités multiutilisateurs !</span><span class="sxs-lookup"><span data-stu-id="dbebb-105">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="dbebb-106">Dans cette série de tutoriels, vous allez apprendre les bases de la création d’une expérience multiutilisateur à l’aide de <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span><span class="sxs-lookup"><span data-stu-id="dbebb-106">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="dbebb-107">PUN est l’une des nombreuses options de réseau que peuvent utiliser les développeurs de réalité mixte pour créer des expériences partagées.</span><span class="sxs-lookup"><span data-stu-id="dbebb-107">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="dbebb-108">Tutoriels de cette série :</span><span class="sxs-lookup"><span data-stu-id="dbebb-108">Tutorials in this series:</span></span>

* [<span data-ttu-id="dbebb-109">Configuration de Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="dbebb-109">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="dbebb-110">Connexion de plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="dbebb-110">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="dbebb-111">Partage de mouvements d’objet avec plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="dbebb-111">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="dbebb-112">Intégration d’Azure Spatial Anchors dans une expérience partagée</span><span class="sxs-lookup"><span data-stu-id="dbebb-112">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="dbebb-113">Objectifs</span><span class="sxs-lookup"><span data-stu-id="dbebb-113">Objectives</span></span>

* <span data-ttu-id="dbebb-114">Apprendre à créer une application PUN et y connecter votre projet Unity</span><span class="sxs-lookup"><span data-stu-id="dbebb-114">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="dbebb-115">Apprendre à connecter plusieurs utilisateurs dans un environnement partagé</span><span class="sxs-lookup"><span data-stu-id="dbebb-115">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="dbebb-116">Apprendre à partager les mouvements d’objets avec d’autres utilisateurs</span><span class="sxs-lookup"><span data-stu-id="dbebb-116">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="dbebb-117">Apprendre à obtenir un alignement spatial entre plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="dbebb-117">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbebb-118">Prérequis</span><span class="sxs-lookup"><span data-stu-id="dbebb-118">Prerequisites</span></span>

* <span data-ttu-id="dbebb-119">Ordinateur Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="dbebb-119">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="dbebb-120">SDK Windows 10 (10.0.18362.0 ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="dbebb-120">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="dbebb-121">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="dbebb-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="dbebb-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019 LTS installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté</span><span class="sxs-lookup"><span data-stu-id="dbebb-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="dbebb-123">Avoir suivi la section [Créer une ressource d’ancres spatiales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) du tutoriel [Démarrage rapide : Créer une application HoloLens Unity qui utilise Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="dbebb-123">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="dbebb-124">Avoir suivi la série de [tutoriels de démarrage](mr-learning-base-01.md) ou connaître les fondamentaux d’Unity et de MRTK</span><span class="sxs-lookup"><span data-stu-id="dbebb-124">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="dbebb-125">Avoir suivi la série de [tutoriels sur Azure Spatial Anchors](mr-learning-asa-01.md) ou avoir déjà créé des comptes Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="dbebb-125">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="dbebb-126">Si vous envisagez d’effectuer un déploiement à la fois sur Android et sur HoloLens :</span><span class="sxs-lookup"><span data-stu-id="dbebb-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="dbebb-127">Appareil Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">en mode développeur</a> et <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible avec ARCore</a> disposant d’une connexion USB à votre ordinateur Windows ou macOS</span><span class="sxs-lookup"><span data-stu-id="dbebb-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="dbebb-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019 LTS installé et le module Android Build Support ajouté</span><span class="sxs-lookup"><span data-stu-id="dbebb-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="dbebb-129">Si vous envisagez d’effectuer un déploiement à la fois sur iOS et sur HoloLens :</span><span class="sxs-lookup"><span data-stu-id="dbebb-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="dbebb-130">Ordinateur macOS avec les dernières versions de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> et de <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installées</span><span class="sxs-lookup"><span data-stu-id="dbebb-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="dbebb-131">Appareil iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible avec ARKit</a> disposant d’une connexion USB à votre ordinateur macOS</span><span class="sxs-lookup"><span data-stu-id="dbebb-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="dbebb-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019 LTS installé et le module iOS Build Support ajouté</span><span class="sxs-lookup"><span data-stu-id="dbebb-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="dbebb-133">La version de Mixed Reality Toolkit qui est recommandée pour cette série de tutoriels est MRTK 2.5.1.</span><span class="sxs-lookup"><span data-stu-id="dbebb-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.1.</span></span>

> [!CAUTION]
> <span data-ttu-id="dbebb-134">La version recommandée d’Unity pour cette série de tutoriels est Unity 2019 LTS. Ceci remplace toutes les exigences de version d’Unity mentionnées dans les prérequis figurant dans les liens ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="dbebb-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbebb-135">Tutoriel suivant : 2. Configuration du réseau Photon Unity</span><span class="sxs-lookup"><span data-stu-id="dbebb-135">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
