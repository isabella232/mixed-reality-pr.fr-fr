---
title: Choix d’une version Unity et d’un plug-in XR
description: Restez à jour avec les dernières recommandations en matière de plug-in Unity et XR pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938116"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="2c3a8-104">Choix d’une version Unity et d’un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="2c3a8-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="2c3a8-105">Bien que nous **vous recommandons actuellement d’installer unity 2019,4 LTS et d’utiliser des XR intégrées héritées pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="2c3a8-106">Unity 2019,4 LTS (recommandé)</span><span class="sxs-lookup"><span data-stu-id="2c3a8-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="2c3a8-107">La configuration d’Unity recommandée de Microsoft pour le développement HoloLens 2 et Windows Mixed Reality est **unity 2019,4 LTS à l’aide** de la prise en charge XR intégrée héritée.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="2c3a8-108">La meilleure façon d’installer et de gérer Unity consiste à utiliser <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="2c3a8-109">Une fois l’installation terminée, ouvrez Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="2c3a8-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="2c3a8-110">Sélectionnez l’onglet **installations** , puis choisissez **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="2c3a8-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="2c3a8-111">Sélectionnez Unity 2019,4 LTS, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="2c3a8-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity Hub instal New version](images/unity-hub-img-01.png)

3. <span data-ttu-id="2c3a8-113">Vérifiez les composants suivants sous **« plateformes »**</span><span class="sxs-lookup"><span data-stu-id="2c3a8-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="2c3a8-114">**plateforme Windows universelle la prise en charge de la Build**</span><span class="sxs-lookup"><span data-stu-id="2c3a8-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="2c3a8-115">**Prise en charge de Windows Build (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="2c3a8-115">**Windows Build Support (IL2CPP)**</span></span>

![Option Unity plateforme Windows universelle support Build](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="2c3a8-117">Si vous avez installé Unity sans ces options, vous pouvez les ajouter via le menu **Ajouter des modules** dans Unity Hub :</span><span class="sxs-lookup"><span data-stu-id="2c3a8-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Option de support Windows Build Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="2c3a8-119">Pour vous familiariser avec les XR intégrées héritées dans Unity 2019,4 LTS, cliquez ici :</span><span class="sxs-lookup"><span data-stu-id="2c3a8-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c3a8-120">Configurer des XR intégrées héritées</span><span class="sxs-lookup"><span data-stu-id="2c3a8-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="2c3a8-121">Unity a déconseillé sa prise en charge XR intégrée existante à partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="2c3a8-122">Alors que Unity 2019 offre une nouvelle infrastructure de plug-in XR, Microsoft ne recommande pas actuellement ce chemin dans Unity 2019 en raison d’incompatibilités entre les ancres spatiales Azure et de la version 2 de la base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="2c3a8-123">Dans Unity 2020, les ancres spatiales Azure sont prises en charge dans l’infrastructure de plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="2c3a8-124">Si vous développez des applications pour HoloLens (1re génération), ces casques restent pris en charge dans Unity 2019 LTS avec des XR intégrés hérités pour le cycle de vie complet de Unity 2019 LTS à mi-2022.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="2c3a8-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="2c3a8-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="2c3a8-126">Si vous utilisez **unity 2020,3 LTS**, vous pouvez utiliser le **plug-in Windows XR** pour développer des applications HoloLens 2 et Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="2c3a8-127">Toutefois, il existe des problèmes connus qui affectent la stabilité des hologrammes et d’autres fonctionnalités de HoloLens 2 :</span><span class="sxs-lookup"><span data-stu-id="2c3a8-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="2c3a8-128">La soumission de mémoire tampon de profondeur a régressé dans les builds 2020 Unity récente, ce qui entraîne une sérieuse instabilité de l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-128">Depth buffer submission has regressed in recent Unity 2020 builds, which results in severe hologram instability.</span></span>
* <span data-ttu-id="2c3a8-129">Les applications de communication à distance des applications holographiques utilisant la cible de génération plateforme Windows universelle ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-129">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="2c3a8-130">Le système de travaux graphiques Unity est activé par défaut, même s’il n’est pas compatible avec les projets HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-130">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="2c3a8-131">Si vous choisissez de démarrer un nouveau projet dans Unity 2020 aujourd’hui, veillez à suivre les mois à venir pour les builds Unity mises à jour et les builds de plug-in Windows XR avant d’expédier votre application.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-131">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="2c3a8-132">Cela permet de s’assurer que vos utilisateurs connaissent une stabilité d’hologramme appropriée.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-132">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c3a8-133">Utilisation du plug-in XR Windows</span><span class="sxs-lookup"><span data-stu-id="2c3a8-133">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="2c3a8-134">Utilisation de OpenXR</span><span class="sxs-lookup"><span data-stu-id="2c3a8-134">Using OpenXR</span></span>

<span data-ttu-id="2c3a8-135">Unity 2020,3 LTS prend également en charge une version préliminaire publique du plug-in **OpenXR de réalité mixte** .</span><span class="sxs-lookup"><span data-stu-id="2c3a8-135">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="2c3a8-136">Le plug-in OpenXR de réalité mixte prend entièrement en charge les implémentations de 4,0 base de ARPlaneManager et de ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-136">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="2c3a8-137">Cela vous permet d’écrire du code de test de positionnement une fois qui s’étend sur les téléphones et tablettes HoloLens 2 et ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-137">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="2c3a8-138">Plus tard cette année, **unity 2020,3 LTS avec le plug-in OpenXR** deviendra la configuration Unity recommandée, et les futures fonctionnalités HoloLens 2 d’Unity seront exposées uniquement par le biais de ce plug-in.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-138">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>  <span data-ttu-id="2c3a8-139">Vous pouvez démarrer votre projet ici pour l’instant. Toutefois, si votre projet cible HoloLens 2, vous rencontrerez actuellement la stabilité de l’hologramme Unity 2020 et d’autres problèmes répertoriés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-139">You can start your project here for now - however, if your project targets HoloLens 2, you will currently encounter the Unity 2020 hologram stability and other issues listed above.</span></span>  <span data-ttu-id="2c3a8-140">Veillez à consulter les mois à venir pour les builds Unity mises à jour et les builds de plug-in OpenXR avant d’expédier votre application.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-140">Be sure to check back in the coming months for updated Unity builds and OpenXR plugin builds before shipping your app.</span></span>  <span data-ttu-id="2c3a8-141">Cela permet de s’assurer que vos utilisateurs connaissent une stabilité d’hologramme appropriée.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-141">This will ensure that your users experience proper hologram stability.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c3a8-142">Utilisation du plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="2c3a8-142">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="2c3a8-143">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="2c3a8-143">Unity 2021.1</span></span>

<span data-ttu-id="2c3a8-144">Si vous essayez les builds **2021,1 premières Unity** , vous devez avancer jusqu’au **plug-in OpenXR**, car le plug-in Windows XR est déconseillé ici.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-144">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="2c3a8-145">À partir de Unity 2021,2, le plug-in OpenXR sera le seul chemin pour le développement de la réalité mixte, car le plug-in Windows XR ne sera plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-145">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="2c3a8-146">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="2c3a8-146">Unity 2018.4 LTS</span></span>

<span data-ttu-id="2c3a8-147">Si vous disposez déjà d’un projet utilisant Unity 2018,4 LTS, votre moteur Unity continue d’être pris en charge pendant 2 ans après sa sortie.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-147">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="2c3a8-148">Unity 2018 LTS atteindra la fin du service au printemps de 2021.</span><span class="sxs-lookup"><span data-stu-id="2c3a8-148">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
