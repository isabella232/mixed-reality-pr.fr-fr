---
title: Tutoriel Azure Spatial Anchors - 1. Introduction aux tutoriels Azure Spatial Anchors
description: Suivez ce cours pour découvrir comment implémenter Azure Spatial Anchors dans une application de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens
ms.localizationpriority: high
ms.openlocfilehash: fcea8bd02c81437dd7337ee94838f44f299f1927
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353397"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="e435d-105">1. Introduction aux tutoriels Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e435d-105">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

## <a name="overview"></a><span data-ttu-id="e435d-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="e435d-106">Overview</span></span>

<span data-ttu-id="e435d-107">Bienvenue dans les tutoriels Azure Spatial Anchors !</span><span class="sxs-lookup"><span data-stu-id="e435d-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="e435d-108">Cette série de tutoriels vous apprend les notions de base d’<a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) et vous explique comment ancrer une expérience de réalité mixte complète dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="e435d-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="e435d-109">Vous verrez également comment déployer votre projet sur Android et iOS.</span><span class="sxs-lookup"><span data-stu-id="e435d-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="e435d-110">Tutoriels de cette série :</span><span class="sxs-lookup"><span data-stu-id="e435d-110">Tutorials in this series:</span></span>

1. <span data-ttu-id="e435d-111">[Introduction](mr-learning-asa-01.md) (vous êtes déjà ici)</span><span class="sxs-lookup"><span data-stu-id="e435d-111">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="e435d-112">Bien démarrer avec Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e435d-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="e435d-113">Enregistrement, récupération et partage d’ancres spatiales Azure</span><span class="sxs-lookup"><span data-stu-id="e435d-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="e435d-114">Affichage du feedback Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e435d-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="e435d-115">Azure Spatial Anchors pour Android et iOS</span><span class="sxs-lookup"><span data-stu-id="e435d-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="e435d-116">Objectifs</span><span class="sxs-lookup"><span data-stu-id="e435d-116">Objectives</span></span>

* <span data-ttu-id="e435d-117">Apprendre à créer des ancres spatiales et à les récupérer à partir d’Azure</span><span class="sxs-lookup"><span data-stu-id="e435d-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="e435d-118">Apprendre à obtenir un alignement spatial entre plusieurs sessions d’application</span><span class="sxs-lookup"><span data-stu-id="e435d-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="e435d-119">Apprendre à obtenir un alignement spatial entre plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="e435d-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="e435d-120">Apprendre à préparer, générer et déployer votre projet sur Android et iOS</span><span class="sxs-lookup"><span data-stu-id="e435d-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e435d-121">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e435d-121">Prerequisites</span></span>

* <span data-ttu-id="e435d-122">Ordinateur Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="e435d-122">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="e435d-123">SDK Windows 10 10.0.18362.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e435d-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="e435d-124">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="e435d-124">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="e435d-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019.3.15 installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté</span><span class="sxs-lookup"><span data-stu-id="e435d-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="e435d-126">Avoir suivi la section [Créer une ressource d’ancres spatiales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) du tutoriel [Démarrage rapide : Créer une application HoloLens Unity qui utilise Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="e435d-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="e435d-127">Avoir suivi la série de [tutoriels de démarrage](mr-learning-base-01.md) ou avoir une expérience de base avec Unity et MRTK</span><span class="sxs-lookup"><span data-stu-id="e435d-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="e435d-128">Si vous envisagez d’effectuer un déploiement à la fois sur Android et sur HoloLens :</span><span class="sxs-lookup"><span data-stu-id="e435d-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="e435d-129">Appareil Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">en mode développeur</a> et <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible avec ARCore</a> disposant d’une connexion USB à votre ordinateur Windows ou macOS</span><span class="sxs-lookup"><span data-stu-id="e435d-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="e435d-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019.3.15 installé et le module Android Build Support ajouté</span><span class="sxs-lookup"><span data-stu-id="e435d-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="e435d-131">Si vous envisagez d’effectuer un déploiement à la fois sur iOS et sur HoloLens :</span><span class="sxs-lookup"><span data-stu-id="e435d-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="e435d-132">Ordinateur macOS avec les dernières versions de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> et de <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installées</span><span class="sxs-lookup"><span data-stu-id="e435d-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="e435d-133">Appareil iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible avec ARKit</a> disposant d’une connexion USB à votre ordinateur macOS</span><span class="sxs-lookup"><span data-stu-id="e435d-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="e435d-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019.3.15 installé et le module iOS Build Support ajouté</span><span class="sxs-lookup"><span data-stu-id="e435d-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="e435d-135">La version de Mixed Reality Toolkit qui est recommandée pour cette série de tutoriels est MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="e435d-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="e435d-136">La version Unity recommandée pour cette série de tutoriels est Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="e435d-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="e435d-137">Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="e435d-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e435d-138">Tutoriel suivant : 2. Bien démarrer avec les ancres spatiales Azure</span><span class="sxs-lookup"><span data-stu-id="e435d-138">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
