---
title: Paramètres de l’appareil photo Windows Mixed Reality
description: Documentation pour utiliser les paramètres de l’appareil photo Windows Mixed Reality dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, appareil photo,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121637"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="bb813-104">Fournisseur de paramètres d’appareil photo Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bb813-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="bb813-105">Le fournisseur de paramètres de l’appareil photo Windows Mixed Reality détermine le type d’appareil sur lequel l’application s’exécute et applique les paramètres de configuration appropriés en fonction de l’affichage (transparent ou opaque).</span><span class="sxs-lookup"><span data-stu-id="bb813-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="bb813-106">Activation du fournisseur de paramètres d’appareil photo Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bb813-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="bb813-107">Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="bb813-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="bb813-108">Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.</span><span class="sxs-lookup"><span data-stu-id="bb813-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="bb813-109">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="bb813-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="bb813-111">Dans le panneau de l’inspecteur, accédez à la section système de l’appareil photo et développez la section paramètres de l' **appareil photo** .</span><span class="sxs-lookup"><span data-stu-id="bb813-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Développez Paramètres fournisseurs](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="bb813-113">Cliquez sur **Ajouter un fournisseur de paramètres d’appareil photo** , puis développez l’entrée **nouveaux paramètres d’appareil photo** récemment ajoutés.</span><span class="sxs-lookup"><span data-stu-id="bb813-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Développer le nouveau fournisseur de paramètres](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="bb813-115">Sélectionner le fournisseur de paramètres d’appareil photo Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bb813-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Sélectionner le fournisseur de paramètres Windows Mixed Reality](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="bb813-117">Lorsque vous utilisez les profils par défaut de Microsoft Mixed Reality Toolkit, le fournisseur de paramètres d’appareil photo Windows Mixed Real est déjà activé et configuré.</span><span class="sxs-lookup"><span data-stu-id="bb813-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="bb813-118">Configuration du fournisseur de paramètres d’appareil photo Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bb813-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="bb813-119">Les paramètres de la caméra Windows Mixed Reality prennent également en charge un profil.</span><span class="sxs-lookup"><span data-stu-id="bb813-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="bb813-120">Ce profil fournit les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="bb813-120">This profile provides the following options:</span></span>

![Configuration des paramètres de l’appareil photo Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="bb813-122">Rendu de la capture de la réalité mixte à partir de la caméra photo/vidéo</span><span class="sxs-lookup"><span data-stu-id="bb813-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="bb813-123">Avec ce paramètre sur HoloLens 2, vous pouvez activer l’alignement des hologrammes dans vos captures de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="bb813-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="bb813-124">S’il est activé, la plateforme fournira un HolographicCamera supplémentaire à l’application lorsqu’une réalité mixte capture une photo ou une vidéo est prise.</span><span class="sxs-lookup"><span data-stu-id="bb813-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="bb813-125">Ce HolographicCamera fournit des matrices d’affichage correspondant à l’emplacement de la caméra photo/vidéo, et fournit des matrices de projection à l’aide du champ de vue caméra photo/vidéo.</span><span class="sxs-lookup"><span data-stu-id="bb813-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="bb813-126">Cela permet de s’assurer que les hologrammes, tels que les maillages de main, restent alignés de manière visible dans la sortie vidéo.</span><span class="sxs-lookup"><span data-stu-id="bb813-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="bb813-127">Méthode de reprojection HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bb813-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="bb813-128">Définit la méthode initiale pour la reprojection HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bb813-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="bb813-129">La recommandation par défaut consiste à utiliser la reprojection de profondeur, car toutes les parties de la scène seront stabilisées indépendamment en fonction de leur distance par rapport à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bb813-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="bb813-130">Si les hologrammes semblent toujours instables, essayez de vous assurer que tous les objets ont correctement envoyé leur profondeur au tampon de profondeur.</span><span class="sxs-lookup"><span data-stu-id="bb813-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="bb813-131">Il s’agit parfois d’un paramètre de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="bb813-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="bb813-132">Si la profondeur semble être correctement soumise et que l’instabilité est toujours présente, essayez la stabilisation autoplanaire, qui utilise la mémoire tampon de profondeur pour calculer un plan de stabilisation.</span><span class="sxs-lookup"><span data-stu-id="bb813-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="bb813-133">Si une application ne peut pas envoyer suffisamment de données de profondeur pour que l’une de ces options soit utilisable, la reprojection planaire est fournie en tant que secours.</span><span class="sxs-lookup"><span data-stu-id="bb813-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="bb813-134">Cette méthode sera basée sur les données de point de focus fournies par une application via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span><span class="sxs-lookup"><span data-stu-id="bb813-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="bb813-135">Pour mettre à jour la méthode de reprojection au moment de l’exécution, accédez à l’exemple de la `WindowsMixedRealityReprojectionUpdater` façon suivante :</span><span class="sxs-lookup"><span data-stu-id="bb813-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="bb813-136">Cela ne doit être mis à jour qu’une seule fois et la valeur est réutilisée pour tous les frames suivants.</span><span class="sxs-lookup"><span data-stu-id="bb813-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="bb813-137">Si la méthode est fréquemment mise à jour, il est recommandé de mettre en cache le résultat de `EnsureComponent` au lieu de l’appeler souvent.</span><span class="sxs-lookup"><span data-stu-id="bb813-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb813-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb813-138">See also</span></span>

- [<span data-ttu-id="bb813-139">Vue d’ensemble du système de caméras</span><span class="sxs-lookup"><span data-stu-id="bb813-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="bb813-140">Création d’un fournisseur de paramètres d’appareil photo</span><span class="sxs-lookup"><span data-stu-id="bb813-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="bb813-141">Rendu de la capture de la réalité mixte à partir de l’appareil photo PV</span><span class="sxs-lookup"><span data-stu-id="bb813-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="bb813-142">Reprojection holographique</span><span class="sxs-lookup"><span data-stu-id="bb813-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)