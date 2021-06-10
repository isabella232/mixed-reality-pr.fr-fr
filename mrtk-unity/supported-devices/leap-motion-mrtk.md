---
title: Leap Motion dans MRTK
description: Documentation à configurer pour le mouvement LEAP
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, mouvement LEAP,
ms.openlocfilehash: 8ef5d26512d50a93691932789e84c099c6246bc3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543235"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="36b68-104">Comment configurer le suivi des mouvements LEAP (par Ultraleap) dans MRTK</span><span class="sxs-lookup"><span data-stu-id="36b68-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="36b68-105">Un [contrôleur de mouvement LEAP](https://www.ultraleap.com/product/leap-motion-controller/) est requis pour utiliser ce fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="36b68-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="36b68-106">Le Fournisseur de données de mouvement LEAP active le suivi articulé pour VR et peut être utile pour le prototypage rapide dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="36b68-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="36b68-107">Le fournisseur de données peut être configuré pour utiliser le contrôleur de mouvement LEAP monté sur un casque ou placé sur un bureau.</span><span class="sxs-lookup"><span data-stu-id="36b68-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="36b68-109">Ce fournisseur peut être utilisé dans l’éditeur et sur l’appareil sur la plateforme autonome.</span><span class="sxs-lookup"><span data-stu-id="36b68-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="36b68-110">Il peut également être utilisé dans l’éditeur sur la plateforme UWP, mais pas dans une génération UWP.</span><span class="sxs-lookup"><span data-stu-id="36b68-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="36b68-111">Version de MRTK</span><span class="sxs-lookup"><span data-stu-id="36b68-111">MRTK Version</span></span> | <span data-ttu-id="36b68-112">Versions des modules Unity de mouvement LEAP prises en charge</span><span class="sxs-lookup"><span data-stu-id="36b68-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="36b68-113">2.6. x</span><span class="sxs-lookup"><span data-stu-id="36b68-113">2.6.x</span></span> | <span data-ttu-id="36b68-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="36b68-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="36b68-115">2.7. x</span><span class="sxs-lookup"><span data-stu-id="36b68-115">2.7.x</span></span>| <span data-ttu-id="36b68-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="36b68-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="36b68-117">Utilisation du suivi des mouvements LEAP (par Ultraleap) dans MRTK</span><span class="sxs-lookup"><span data-stu-id="36b68-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="36b68-118">Importation de MRTK et des modules Unity de mouvement LEAP</span><span class="sxs-lookup"><span data-stu-id="36b68-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="36b68-119">Installer le dernier [Kit de développement logiciel (SDK) LEAP](https://developer.leapmotion.com/releases/?category=orion) le plus récent s’il n’est pas déjà installé</span><span class="sxs-lookup"><span data-stu-id="36b68-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="36b68-120">Importez le package **Microsoft. MixedReality. Toolkit. Foundation** dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="36b68-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="36b68-121">Téléchargez et importez la dernière version des [modules Unity LEAP](https://developer.leapmotion.com/unity) dans le projet</span><span class="sxs-lookup"><span data-stu-id="36b68-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="36b68-122">Importer uniquement le package de **base** dans les modules Unity</span><span class="sxs-lookup"><span data-stu-id="36b68-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="36b68-123">Intégrer les modules LEAP Motion Unity avec MRTK</span><span class="sxs-lookup"><span data-stu-id="36b68-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="36b68-124">Une fois que les modules Unity se trouvent dans le projet, accédez à **Mixed Reality Toolkit**  >  **LEAP Motion**  >  **intégrer les modules Unity de mouvement LEAP**</span><span class="sxs-lookup"><span data-stu-id="36b68-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="36b68-125">L’intégration des modules Unity à MRTK ajoute 10 définitions d’assembly au projet et ajoute des références à la définition d’assembly **Microsoft. MixedReality. Toolkit. Providers. LeapMotion** .</span><span class="sxs-lookup"><span data-stu-id="36b68-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="36b68-126">Vérifiez que Visual Studio est fermé.</span><span class="sxs-lookup"><span data-stu-id="36b68-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="36b68-128">Ajout de la Fournisseur de données de mouvement LEAP</span><span class="sxs-lookup"><span data-stu-id="36b68-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="36b68-129">Créer une nouvelle scène Unity</span><span class="sxs-lookup"><span data-stu-id="36b68-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="36b68-130">Ajoutez MRTK à la scène en accédant à **Mixed Reality Toolkit**  >  **Add to Scene et configure**</span><span class="sxs-lookup"><span data-stu-id="36b68-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="36b68-131">Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="36b68-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="36b68-133">Sélectionner le profil de configuration **d’entrée**</span><span class="sxs-lookup"><span data-stu-id="36b68-133">Select the **Input** Configuration Profile</span></span>

    ![Profil de configuration d’entrée 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="36b68-135">Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.</span><span class="sxs-lookup"><span data-stu-id="36b68-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="36b68-137">Ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **Ajouter des fournisseur de données** en haut, un nouveau fournisseur de données sera ajouté à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="36b68-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="36b68-138">Ouvrez le nouveau fournisseur de données et définissez le **type** sur **Microsoft. MixedReality. Toolkit. LeapMotion. Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="36b68-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Fournisseur de données d’ajout LEAP](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="36b68-140">Sélectionnez **clone** pour modifier les paramètres de mouvement LEAP par défaut.</span><span class="sxs-lookup"><span data-stu-id="36b68-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="36b68-142">Le Fournisseur de données de mouvement LEAP contient la `LeapControllerOrientation` propriété qui correspond à l’emplacement du contrôleur de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="36b68-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="36b68-143">`LeapControllerOrientation.Headset` indique que le contrôleur est monté sur un casque.</span><span class="sxs-lookup"><span data-stu-id="36b68-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="36b68-144">`LeapControllerOrientation.Desk` indique que le contrôleur est placé à plat sur le bureau.</span><span class="sxs-lookup"><span data-stu-id="36b68-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="36b68-145">La valeur par défaut est `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="36b68-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="36b68-146">Chaque orientation de contrôleur contient des propriétés de décalage :</span><span class="sxs-lookup"><span data-stu-id="36b68-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="36b68-147">Les propriétés de décalage d’orientation du **casque** reflètent les propriétés de décalage dans le composant LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="36b68-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="36b68-148">Le `LeapVRDeviceOffsetMode` a trois options : par défaut, décalage manuel de l’en-tête et transformation.</span><span class="sxs-lookup"><span data-stu-id="36b68-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="36b68-149">Si le mode de décalage est défini par défaut, aucun décalage n’est appliqué au contrôleur de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="36b68-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="36b68-150">Le mode de décalage manuel en tête permet la modification de trois propriétés : `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` et `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="36b68-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="36b68-151">Les valeurs des propriétés de décalage de l’axe sont ensuite appliquées au placement du contrôleur par défaut.</span><span class="sxs-lookup"><span data-stu-id="36b68-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="36b68-152">Le mode de décalage de transformation contient la `LeapVRDeviceOrigin` propriété de transformation qui spécifie une nouvelle origine pour le contrôleur de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="36b68-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="36b68-153">L’orientation du **Bureau** contient la `LeapControllerOffset` propriété qui définit la position d’ancrage des aiguilles du bureau.</span><span class="sxs-lookup"><span data-stu-id="36b68-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="36b68-154">Le décalage est calculé par rapport à la position de la caméra principale et la valeur par défaut est (0,-0,2, 0,35) pour s’assurer que les mains s’affichent au premier plan et en vue de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="36b68-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="36b68-155">Les propriétés de décalage dans le profil sont appliquées une fois au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="36b68-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="36b68-156">Pour modifier les valeurs lors de l’exécution, procurez-vous le fournisseur de service de mouvement LEAP à partir de la Gestionnaire de périphériques de mouvement LEAP :</span><span class="sxs-lookup"><span data-stu-id="36b68-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="36b68-157">`EnterPinchDistance` et `ExitPinchDistance` sont les seuils de distance pour la détection de mouvement pincement/taraudage.</span><span class="sxs-lookup"><span data-stu-id="36b68-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="36b68-158">Le mouvement de pincement est calculé en mesurant la distance entre l’info-bulle de l’index et la pointe du curseur.</span><span class="sxs-lookup"><span data-stu-id="36b68-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="36b68-159">Pour déclencher un événement lors de l’entrée vers le dessous, la valeur par défaut `EnterPinchDistance` est 0,02.</span><span class="sxs-lookup"><span data-stu-id="36b68-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="36b68-160">Pour déclencher un événement lors de l’entrée vers le haut (en quittant le pincement), la distance par défaut entre l’info-bulle de l’index et l’info-bulle est 0,05.</span><span class="sxs-lookup"><span data-stu-id="36b68-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="36b68-161">`LeapControllerOrientation`: Casque (par défaut)</span><span class="sxs-lookup"><span data-stu-id="36b68-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="36b68-162">`LeapControllerOrientation`: Bureau</span><span class="sxs-lookup"><span data-stu-id="36b68-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="36b68-167">Test de la Fournisseur de données de mouvement LEAP</span><span class="sxs-lookup"><span data-stu-id="36b68-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="36b68-168">Une fois que le Fournisseur de données de mouvement LEAP a été ajouté au profil de système d’entrée, appuyez sur Play, déplacez votre main devant le contrôleur de mouvement LEAP. vous devriez voir la représentation conjointe de la main.</span><span class="sxs-lookup"><span data-stu-id="36b68-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="36b68-169">Génération de votre projet</span><span class="sxs-lookup"><span data-stu-id="36b68-169">Building your project</span></span>
    - <span data-ttu-id="36b68-170">Accédez à **fichier > paramètres de build**</span><span class="sxs-lookup"><span data-stu-id="36b68-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="36b68-171">Seules les builds autonomes sont prises en charge si vous utilisez la Fournisseur de données de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="36b68-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="36b68-172">Pour obtenir des instructions sur l’utilisation d’un casque Windows Mixed Reality pour des builds autonomes, consultez la page [création et déploiement de MRTK sur des casques WMR (autonomes)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span><span class="sxs-lookup"><span data-stu-id="36b68-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="36b68-173">Obtention des articulations de la main</span><span class="sxs-lookup"><span data-stu-id="36b68-173">Getting the hand joints</span></span>

<span data-ttu-id="36b68-174">L’obtention de jointures à l’aide de la Fournisseur de données de mouvement LEAP est identique à la récupération conjointe de la main pour un MRTK articulé.</span><span class="sxs-lookup"><span data-stu-id="36b68-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="36b68-175">Pour plus d’informations, consultez [suivi manuel](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="36b68-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="36b68-176">Avec MRTK dans une scène Unity et le mouvement LEAP Fournisseur de données ajouté comme Fournisseur de données d’entrée dans le profil de système d’entrée, créez un objet de jeu vide et attachez l’exemple de script suivant.</span><span class="sxs-lookup"><span data-stu-id="36b68-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="36b68-177">Ce script est un exemple simple de la façon dont vous pouvez récupérer la pose de l’articulation de Palm dans une main de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="36b68-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="36b68-178">Une sphère suit la main gauche, tandis qu’un cube suit la main à droite.</span><span class="sxs-lookup"><span data-stu-id="36b68-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="36b68-179">Astuce du flux de travail de l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="36b68-179">Unity editor workflow tip</span></span>

<span data-ttu-id="36b68-180">L’utilisation de la Fournisseur de données de mouvement LEAP ne nécessite pas de casque de VR.</span><span class="sxs-lookup"><span data-stu-id="36b68-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="36b68-181">Les modifications apportées à une application MRTK peuvent être testées dans l’éditeur avec les aiguilles de l’avant sans casque.</span><span class="sxs-lookup"><span data-stu-id="36b68-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="36b68-182">Les mains des mouvements LEAPS s’affichent dans l’éditeur, sans un casque de VR branché.</span><span class="sxs-lookup"><span data-stu-id="36b68-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="36b68-183">Si le `LeapControllerOrientation` est défini sur **casque**, le contrôleur de mouvement LEAP devra être maintenu d’une main à l’autre.</span><span class="sxs-lookup"><span data-stu-id="36b68-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="36b68-184">Si l’appareil photo est déplacé à l’aide de clés WASD dans l’éditeur et que le `LeapControllerOrientation` **casque** est, les mains ne suivent pas l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="36b68-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="36b68-185">Les mains suivent uniquement le mouvement de l’appareil photo si un casque VR est branché alors que le `LeapControllerOrientation` est défini comme **casque**.</span><span class="sxs-lookup"><span data-stu-id="36b68-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="36b68-186">Les aiguilles du Bond suivent le mouvement de l’appareil photo dans l’éditeur si le `LeapControllerOrientation` est défini sur **Bureau**.</span><span class="sxs-lookup"><span data-stu-id="36b68-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="36b68-187">Suppression du mouvement LEAP du projet</span><span class="sxs-lookup"><span data-stu-id="36b68-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="36b68-188">Accéder aux modules d'  >    >  **Unity de mouvement LEAP séparés** par le mouvement de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="36b68-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="36b68-189">Permettre à l’actualisation Unity en tant que références dans le fichier **Microsoft. MixedReality. Toolkit. Providers. LeapMotion. asmdef** est modifié dans cette étape</span><span class="sxs-lookup"><span data-stu-id="36b68-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="36b68-190">Fermer Unity</span><span class="sxs-lookup"><span data-stu-id="36b68-190">Close Unity</span></span>
1. <span data-ttu-id="36b68-191">Fermez Visual Studio, s’il est ouvert</span><span class="sxs-lookup"><span data-stu-id="36b68-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="36b68-192">Ouvrez l’Explorateur de fichiers et accédez à la racine du projet MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="36b68-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="36b68-193">Supprimer le répertoire **UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="36b68-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="36b68-194">Supprimer le répertoire **UnityProjectName/Assets/plugin/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="36b68-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="36b68-195">Supprimer le fichier **UnityProjectName/Assets/plugin/LeapMotion. meta**</span><span class="sxs-lookup"><span data-stu-id="36b68-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="36b68-196">Rouvrir Unity</span><span class="sxs-lookup"><span data-stu-id="36b68-196">Reopen Unity</span></span>

<span data-ttu-id="36b68-197">Dans Unity 2018,4, vous remarquerez peut-être que des erreurs subsistent dans la console après la suppression de la bibliothèque et des ressources de noyau de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="36b68-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="36b68-198">Si les erreurs sont consignées après la réouverture, redémarrez Unity.</span><span class="sxs-lookup"><span data-stu-id="36b68-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="36b68-199">Erreurs courantes</span><span class="sxs-lookup"><span data-stu-id="36b68-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="36b68-200">Le mouvement LEAP n’a pas été intégré à MRTK</span><span class="sxs-lookup"><span data-stu-id="36b68-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="36b68-201">Pour tester si les modules Unity de mouvement LEAP sont intégrés à MRTK :</span><span class="sxs-lookup"><span data-stu-id="36b68-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="36b68-202">Accédez à la boîte à outils de la **réalité mixte > utilitaires > l’état d’intégration de la vérification >**</span><span class="sxs-lookup"><span data-stu-id="36b68-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="36b68-203">Une fenêtre contextuelle s’affiche avec un message indiquant si les modules d’unité de mouvement LEAP sont intégrés à MRTK.</span><span class="sxs-lookup"><span data-stu-id="36b68-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="36b68-204">Si le message indique que les ressources n’ont pas été intégrées :</span><span class="sxs-lookup"><span data-stu-id="36b68-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="36b68-205">S’assurer que les modules Unity de mouvement LEAP se trouvent dans le projet</span><span class="sxs-lookup"><span data-stu-id="36b68-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="36b68-206">Assurez-vous que la version ajoutée est prise en charge, consultez le tableau en haut de la page pour connaître les versions prises en charge.</span><span class="sxs-lookup"><span data-stu-id="36b68-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="36b68-207">Essayez le **Kit d’outils de réalité mixte > utilitaires > le mouvement leap > intégrer les modules Unity de mouvement LEAP**</span><span class="sxs-lookup"><span data-stu-id="36b68-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="36b68-208">Échec de la copie des HLAPI multijoueur de l’assembly</span><span class="sxs-lookup"><span data-stu-id="36b68-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="36b68-209">Cette erreur peut être consignée lors de l’importation des ressources principales de l’Unity de mouvement LEAP :</span><span class="sxs-lookup"><span data-stu-id="36b68-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="36b68-210">**Solution**</span><span class="sxs-lookup"><span data-stu-id="36b68-210">**Solution**</span></span>

- <span data-ttu-id="36b68-211">Une solution à bref terme consiste à redémarrer Unity.</span><span class="sxs-lookup"><span data-stu-id="36b68-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="36b68-212">Pour plus d’informations, consultez le [problème 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .</span><span class="sxs-lookup"><span data-stu-id="36b68-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="36b68-213">Exemple de scène de mouvement LEAP</span><span class="sxs-lookup"><span data-stu-id="36b68-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="36b68-214">L’exemple de scène utilise le profil DefaultLeapMotionConfiguration et détermine si le projet Unity a été configuré correctement pour utiliser le Fournisseur de données de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="36b68-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="36b68-215">L’exemple de scène est contenu dans le package **Microsoft. MixedReality. Toolkit. examples** dans le répertoire **MRTK/examples/démos/HandTracking/** .</span><span class="sxs-lookup"><span data-stu-id="36b68-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="36b68-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36b68-216">See also</span></span>

- [<span data-ttu-id="36b68-217">Fournisseurs d’entrée</span><span class="sxs-lookup"><span data-stu-id="36b68-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="36b68-218">Suivi de la main</span><span class="sxs-lookup"><span data-stu-id="36b68-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
