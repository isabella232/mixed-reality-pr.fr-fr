---
title: Vue d’ensemble du système de caméras
description: Page d’accueil du système d’appareil photo dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, appareil photo,
ms.openlocfilehash: 1dc5328f2a6390246918063b6564837f150d28d8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144475"
---
# <a name="camera-system"></a><span data-ttu-id="0dd85-104">Système de caméra</span><span class="sxs-lookup"><span data-stu-id="0dd85-104">Camera system</span></span>

<span data-ttu-id="0dd85-105">Le système de caméra permet à Microsoft Mixed Reality Toolkit de configurer et d’optimiser l’appareil photo de l’application afin de l’utiliser dans des applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="0dd85-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="0dd85-106">À l’aide du système d’appareil photo, les applications peuvent être écrites pour prendre en charge à la fois les appareils opaques (par exemple, la réalité virtuelle) et les périphériques transparents (par ex. Microsoft HoloLens) sans avoir à écrire du code pour distinguer et s’adapter à chaque type d’affichage.</span><span class="sxs-lookup"><span data-stu-id="0dd85-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="0dd85-107">Activation du système de caméra</span><span class="sxs-lookup"><span data-stu-id="0dd85-107">Enabling the camera system</span></span>

<span data-ttu-id="0dd85-108">Le système de caméra est géré par l’objet MixedRealityToolkit (ou un autre composant d’inscription de service).</span><span class="sxs-lookup"><span data-stu-id="0dd85-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="0dd85-109">Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="0dd85-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="0dd85-110">Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.</span><span class="sxs-lookup"><span data-stu-id="0dd85-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="0dd85-111">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="0dd85-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="0dd85-113">Dans le panneau de l’inspecteur, accédez à la section système de l’appareil photo et vérifiez que l’option **activer l’appareil photo** est cochée.</span><span class="sxs-lookup"><span data-stu-id="0dd85-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Activation du système de caméra](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="0dd85-115">Sélectionnez l’implémentation du système de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="0dd85-115">Select the camera system implementation.</span></span> <span data-ttu-id="0dd85-116">L’implémentation de classe par défaut fournie par le MRTK est `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="0dd85-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Sélectionner l’implémentation du système de l’appareil photo](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="0dd85-118">Sélectionner le profil de configuration souhaité</span><span class="sxs-lookup"><span data-stu-id="0dd85-118">Select the desired configuration profile</span></span>

    ![Sélectionner un profil de système d’appareil photo](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="0dd85-120">Configuration du système de caméra</span><span class="sxs-lookup"><span data-stu-id="0dd85-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="0dd85-121">Fournisseurs de paramètres</span><span class="sxs-lookup"><span data-stu-id="0dd85-121">Settings providers</span></span>

![Fournisseurs de paramètres d’appareil photo](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="0dd85-123">Les fournisseurs de paramètres d’appareil photo activent la configuration spécifique à la plateforme de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="0dd85-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="0dd85-124">Ces paramètres peuvent inclure des étapes de configuration personnalisées et/ou des composants.</span><span class="sxs-lookup"><span data-stu-id="0dd85-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="0dd85-125">Vous pouvez ajouter des fournisseurs en cliquant sur le bouton **Ajouter un fournisseur de paramètres d’appareil photo** .</span><span class="sxs-lookup"><span data-stu-id="0dd85-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="0dd85-126">Vous pouvez les supprimer en cliquant sur le **-** bouton situé à droite du nom du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0dd85-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="0dd85-127">Toutes les plateformes ne nécessitent pas de fournisseur de paramètres d’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="0dd85-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="0dd85-128">Si aucun fournisseur n’est compatible avec la plateforme sur laquelle l’application s’exécute, le kit de connaissances Microsoft Mixed Reality Toolkit applique les valeurs par défaut de base.</span><span class="sxs-lookup"><span data-stu-id="0dd85-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="0dd85-129">Paramètres d'affichage</span><span class="sxs-lookup"><span data-stu-id="0dd85-129">Display settings</span></span>

![Paramètres d’affichage de l’appareil photo](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="0dd85-131">Les paramètres d’affichage sont spécifiés pour les affichages opaques (par exemple : réalité virtuelle) et transparent (par ex. Microsoft HoloLens).</span><span class="sxs-lookup"><span data-stu-id="0dd85-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="0dd85-132">L’appareil photo est configuré au moment de l’exécution à l’aide de ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="0dd85-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="0dd85-133">**Presque clip**</span><span class="sxs-lookup"><span data-stu-id="0dd85-133">**Near Clip**</span></span>

<span data-ttu-id="0dd85-134">Le plan near clip est le plus proche, en mètres, qu’un objet virtuel peut être à l’appareil photo et qu’il est toujours rendu.</span><span class="sxs-lookup"><span data-stu-id="0dd85-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="0dd85-135">Pour un plus grand confort de l’utilisateur, il est recommandé de faire en sorte que cette valeur soit supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="0dd85-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="0dd85-136">L’image précédente contient des valeurs qui ont été jugées familières sur divers appareils.</span><span class="sxs-lookup"><span data-stu-id="0dd85-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="0dd85-137">**Clip Far**</span><span class="sxs-lookup"><span data-stu-id="0dd85-137">**Far Clip**</span></span>

<span data-ttu-id="0dd85-138">Le plan de clip FAR est le plus éloigné, en mètres, qu’un objet virtuel peut être à l’appareil photo et est toujours rendu.</span><span class="sxs-lookup"><span data-stu-id="0dd85-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="0dd85-139">Pour les appareils transparents, il est recommandé de ne pas dépasser de trop près l’espace du monde réel et de rompre les qualités immersifs de l’application.</span><span class="sxs-lookup"><span data-stu-id="0dd85-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="0dd85-140">**Effacer les indicateurs**</span><span class="sxs-lookup"><span data-stu-id="0dd85-140">**Clear Flags**</span></span>

<span data-ttu-id="0dd85-141">La valeur Clear flags indique comment l’affichage est effacé lorsqu’il est dessiné.</span><span class="sxs-lookup"><span data-stu-id="0dd85-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="0dd85-142">Pour les expériences de réalité virtuelle, cette valeur est le plus souvent définie sur skybox.</span><span class="sxs-lookup"><span data-stu-id="0dd85-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="0dd85-143">Pour les affichages transparents, il est recommandé d’affecter la valeur couleur à cette option.</span><span class="sxs-lookup"><span data-stu-id="0dd85-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="0dd85-144">**Couleur d’arrière-plan**</span><span class="sxs-lookup"><span data-stu-id="0dd85-144">**Background Color**</span></span>

<span data-ttu-id="0dd85-145">Si les indicateurs Clear ne sont pas définis sur skybox, la propriété couleur d’arrière-plan s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0dd85-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="0dd85-146">**Paramètres de qualité**</span><span class="sxs-lookup"><span data-stu-id="0dd85-146">**Quality Settings**</span></span>

<span data-ttu-id="0dd85-147">La valeur des paramètres de qualité indique la qualité graphique qu’Unity doit utiliser lors du rendu de la scène.</span><span class="sxs-lookup"><span data-stu-id="0dd85-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="0dd85-148">Le niveau de qualité est un paramètre au niveau du projet et n’est pas spécifique à un appareil photo.</span><span class="sxs-lookup"><span data-stu-id="0dd85-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="0dd85-149">Pour plus d’informations, consultez l’article sur la [qualité](https://docs.unity3d.com/Manual/class-QualitySettings.html) dans la documentation d’Unity.</span><span class="sxs-lookup"><span data-stu-id="0dd85-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dd85-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dd85-150">See also</span></span>

- [<span data-ttu-id="0dd85-151">Documentation de l’API système de l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="0dd85-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="0dd85-152">Création d’un fournisseur de paramètres d’appareil photo</span><span class="sxs-lookup"><span data-stu-id="0dd85-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
