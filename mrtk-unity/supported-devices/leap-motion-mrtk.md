---
title: Utilisation de Leap Motion
description: Documentation à configurer pour le mouvement LEAP
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, mouvement Leap,
ms.openlocfilehash: 3ddf039f8409022d8aa2e425c46cd4d47ede16a0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176511"
---
# <a name="using-leap-motion"></a><span data-ttu-id="45038-104">Utilisation de Leap Motion</span><span class="sxs-lookup"><span data-stu-id="45038-104">Using Leap Motion</span></span>

<span data-ttu-id="45038-105">Un [contrôleur de mouvement LEAP](https://www.ultraleap.com/product/leap-motion-controller/) est requis pour utiliser ce fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="45038-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="45038-106">le Fournisseur de données de mouvement Leap active le suivi articulé pour VR et peut être utile pour le prototypage rapide dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="45038-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="45038-107">Le fournisseur de données peut être configuré pour utiliser le contrôleur de mouvement LEAP monté sur un casque ou placé sur un bureau.</span><span class="sxs-lookup"><span data-stu-id="45038-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="45038-109">Ce fournisseur peut être utilisé dans l’éditeur et sur l’appareil sur la plateforme autonome.</span><span class="sxs-lookup"><span data-stu-id="45038-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="45038-110">Il peut également être utilisé dans l’éditeur sur la plateforme UWP, mais pas dans une génération UWP.</span><span class="sxs-lookup"><span data-stu-id="45038-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="45038-111">Version de MRTK</span><span class="sxs-lookup"><span data-stu-id="45038-111">MRTK Version</span></span> | <span data-ttu-id="45038-112">Versions des modules Unity de mouvement LEAP prises en charge</span><span class="sxs-lookup"><span data-stu-id="45038-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="45038-113">2.6. x</span><span class="sxs-lookup"><span data-stu-id="45038-113">2.6.x</span></span> | <span data-ttu-id="45038-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="45038-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="45038-115">2.7. x</span><span class="sxs-lookup"><span data-stu-id="45038-115">2.7.x</span></span>| <span data-ttu-id="45038-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="45038-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="45038-117">Utilisation du suivi des mouvements LEAP (par Ultraleap) dans MRTK</span><span class="sxs-lookup"><span data-stu-id="45038-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="45038-118">Importation de MRTK et des modules Unity de mouvement LEAP</span><span class="sxs-lookup"><span data-stu-id="45038-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="45038-119">Installer le dernier [Kit de développement logiciel (SDK) LEAP](https://developer.leapmotion.com/releases/?category=orion) le plus récent s’il n’est pas déjà installé</span><span class="sxs-lookup"><span data-stu-id="45038-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="45038-120">importez le **Microsoft. MixedReality. Shared Computer Toolkit.** Package de base dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="45038-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="45038-121">Téléchargez et importez la dernière version des [modules Unity LEAP](https://developer.leapmotion.com/unity) dans le projet</span><span class="sxs-lookup"><span data-stu-id="45038-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="45038-122">Importer uniquement le package de **base** dans les modules Unity</span><span class="sxs-lookup"><span data-stu-id="45038-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="45038-123">Intégrer les modules LEAP Motion Unity avec MRTK</span><span class="sxs-lookup"><span data-stu-id="45038-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="45038-124">une fois les modules unity dans le projet, accédez à la **réalité mixte Shared Computer Toolkit** les  >    >  **modules unity de mouvement leap**</span><span class="sxs-lookup"><span data-stu-id="45038-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="45038-125">l’intégration des Modules unity à MRTK ajoute 10 définitions d’assembly au projet et ajoute des références à **Microsoft. MixedReality. Shared Computer Toolkit. Définition d’assembly Providers. LeapMotion** .</span><span class="sxs-lookup"><span data-stu-id="45038-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="45038-126">Vérifiez que Visual Studio est fermé.</span><span class="sxs-lookup"><span data-stu-id="45038-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="45038-128">ajout de la Fournisseur de données de mouvement Leap</span><span class="sxs-lookup"><span data-stu-id="45038-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="45038-129">Créer une nouvelle scène Unity</span><span class="sxs-lookup"><span data-stu-id="45038-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="45038-130">ajoutez MRTK à la scène en accédant à la **réalité mixte Shared Computer Toolkit**  >  **ajouter à la scène et configurer**</span><span class="sxs-lookup"><span data-stu-id="45038-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="45038-131">Sélectionnez l’objet de jeu MixedRealityToolkit dans la hiérarchie, puis sélectionnez **copier et personnaliser** pour cloner le profil de réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="45038-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="45038-133">Sélectionner le profil de configuration **d’entrée**</span><span class="sxs-lookup"><span data-stu-id="45038-133">Select the **Input** Configuration Profile</span></span>

    ![Profil de configuration d’entrée 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="45038-135">Sélectionnez **clone** dans le profil de système d’entrée pour permettre la modification.</span><span class="sxs-lookup"><span data-stu-id="45038-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="45038-137">ouvrez la section **fournisseurs de données d’entrée** , sélectionnez **ajouter des Fournisseur de données** en haut, un nouveau fournisseur de données sera ajouté à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="45038-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="45038-138">ouvrez le nouveau fournisseur de données et définissez le **Type** sur **Microsoft. MixedReality. Shared Computer Toolkit. LeapMotion. Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="45038-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Fournisseur de données d’ajout Leap](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="45038-140">Sélectionnez **clone** pour modifier les paramètres de mouvement LEAP par défaut.</span><span class="sxs-lookup"><span data-stu-id="45038-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="45038-142">le Fournisseur de données de mouvement leap contient la `LeapControllerOrientation` propriété qui correspond à l’emplacement du contrôleur de mouvement leap.</span><span class="sxs-lookup"><span data-stu-id="45038-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="45038-143">`LeapControllerOrientation.Headset` indique que le contrôleur est monté sur un casque.</span><span class="sxs-lookup"><span data-stu-id="45038-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="45038-144">`LeapControllerOrientation.Desk` indique que le contrôleur est placé à plat sur le bureau.</span><span class="sxs-lookup"><span data-stu-id="45038-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="45038-145">La valeur par défaut est `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="45038-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="45038-146">Chaque orientation de contrôleur contient des propriétés de décalage :</span><span class="sxs-lookup"><span data-stu-id="45038-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="45038-147">Les propriétés de décalage d’orientation du **casque** reflètent les propriétés de décalage dans le composant LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="45038-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="45038-148">Le `LeapVRDeviceOffsetMode` a trois options : par défaut, décalage manuel de l’en-tête et transformation.</span><span class="sxs-lookup"><span data-stu-id="45038-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="45038-149">Si le mode de décalage est défini par défaut, aucun décalage n’est appliqué au contrôleur de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="45038-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="45038-150">Le mode de décalage manuel en tête permet la modification de trois propriétés : `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` et `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="45038-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="45038-151">Les valeurs des propriétés de décalage de l’axe sont ensuite appliquées au placement du contrôleur par défaut.</span><span class="sxs-lookup"><span data-stu-id="45038-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="45038-152">Le mode de décalage de transformation contient la `LeapVRDeviceOrigin` propriété de transformation qui spécifie une nouvelle origine pour le contrôleur de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="45038-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="45038-153">L’orientation du **Bureau** contient la `LeapControllerOffset` propriété qui définit la position d’ancrage des aiguilles du bureau.</span><span class="sxs-lookup"><span data-stu-id="45038-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="45038-154">Le décalage est calculé par rapport à la position de la caméra principale et la valeur par défaut est (0,-0,2, 0,35) pour s’assurer que les mains s’affichent au premier plan et en vue de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="45038-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="45038-155">Les propriétés de décalage dans le profil sont appliquées une fois au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="45038-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="45038-156">Pour modifier les valeurs lors de l’exécution, procurez-vous le fournisseur de service de mouvement LEAP à partir de la Gestionnaire de périphériques de mouvement LEAP :</span><span class="sxs-lookup"><span data-stu-id="45038-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="45038-157">`EnterPinchDistance` et `ExitPinchDistance` sont les seuils de distance pour la détection de mouvement pincement/taraudage.</span><span class="sxs-lookup"><span data-stu-id="45038-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="45038-158">Le mouvement de pincement est calculé en mesurant la distance entre l’info-bulle de l’index et la pointe du curseur.</span><span class="sxs-lookup"><span data-stu-id="45038-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="45038-159">Pour déclencher un événement lors de l’entrée vers le dessous, la valeur par défaut `EnterPinchDistance` est 0,02.</span><span class="sxs-lookup"><span data-stu-id="45038-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="45038-160">Pour déclencher un événement lors de l’entrée vers le haut (en quittant le pincement), la distance par défaut entre l’info-bulle de l’index et l’info-bulle est 0,05.</span><span class="sxs-lookup"><span data-stu-id="45038-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="45038-161">`LeapControllerOrientation`: Casque (par défaut)</span><span class="sxs-lookup"><span data-stu-id="45038-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="45038-162">`LeapControllerOrientation`: Bureau</span><span class="sxs-lookup"><span data-stu-id="45038-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="45038-167">test de la Fournisseur de données de mouvement Leap</span><span class="sxs-lookup"><span data-stu-id="45038-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="45038-168">une fois que le Fournisseur de données de mouvement Leap a été ajouté au profil de système d’entrée, appuyez sur play, déplacez votre main devant le contrôleur de mouvement leap. vous devriez voir la représentation conjointe de la main.</span><span class="sxs-lookup"><span data-stu-id="45038-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="45038-169">Génération de votre projet</span><span class="sxs-lookup"><span data-stu-id="45038-169">Building your project</span></span>
    - <span data-ttu-id="45038-170">accédez à **fichier > générer Paramètres**</span><span class="sxs-lookup"><span data-stu-id="45038-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="45038-171">seules les builds autonomes sont prises en charge si vous utilisez la Fournisseur de données de mouvement Leap.</span><span class="sxs-lookup"><span data-stu-id="45038-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="45038-172">pour obtenir des instructions sur l’utilisation d’un Windows Mixed Reality casque pour les builds autonomes, consultez la page [création et déploiement de MRTK sur des casques WMR (autonomes)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span><span class="sxs-lookup"><span data-stu-id="45038-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="45038-173">Obtention des articulations de la main</span><span class="sxs-lookup"><span data-stu-id="45038-173">Getting the hand joints</span></span>

<span data-ttu-id="45038-174">l’obtention de jointures à l’aide de la Fournisseur de données de mouvement Leap est identique à la récupération conjointe de la main pour un MRTK articulé.</span><span class="sxs-lookup"><span data-stu-id="45038-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="45038-175">Pour plus d’informations, consultez [suivi manuel](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="45038-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="45038-176">avec MRTK dans une scène unity et le mouvement Leap Fournisseur de données ajouté comme Fournisseur de données d’entrée dans le profil de système d’entrée, créez un objet de jeu vide et attachez l’exemple de script suivant.</span><span class="sxs-lookup"><span data-stu-id="45038-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="45038-177">Ce script est un exemple simple de la façon dont vous pouvez récupérer la pose de l’articulation de Palm dans une main de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="45038-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="45038-178">Une sphère suit la main gauche, tandis qu’un cube suit la main à droite.</span><span class="sxs-lookup"><span data-stu-id="45038-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="45038-179">Astuce du flux de travail de l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="45038-179">Unity editor workflow tip</span></span>

<span data-ttu-id="45038-180">l’utilisation de la Fournisseur de données de mouvement Leap ne nécessite pas de casque de VR.</span><span class="sxs-lookup"><span data-stu-id="45038-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="45038-181">Les modifications apportées à une application MRTK peuvent être testées dans l’éditeur avec les aiguilles de l’avant sans casque.</span><span class="sxs-lookup"><span data-stu-id="45038-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="45038-182">Les mains des mouvements LEAPS s’affichent dans l’éditeur, sans un casque de VR branché.</span><span class="sxs-lookup"><span data-stu-id="45038-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="45038-183">Si le `LeapControllerOrientation` est défini sur **casque**, le contrôleur de mouvement LEAP devra être maintenu d’une main à l’autre.</span><span class="sxs-lookup"><span data-stu-id="45038-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="45038-184">Si l’appareil photo est déplacé à l’aide de clés WASD dans l’éditeur et que le `LeapControllerOrientation` **casque** est, les mains ne suivent pas l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="45038-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="45038-185">Les mains suivent uniquement le mouvement de l’appareil photo si un casque VR est branché alors que le `LeapControllerOrientation` est défini comme **casque**.</span><span class="sxs-lookup"><span data-stu-id="45038-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="45038-186">Les aiguilles du Bond suivent le mouvement de l’appareil photo dans l’éditeur si le `LeapControllerOrientation` est défini sur **Bureau**.</span><span class="sxs-lookup"><span data-stu-id="45038-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="45038-187">Suppression du mouvement LEAP de la Project</span><span class="sxs-lookup"><span data-stu-id="45038-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="45038-188">accédez à la **réalité mixte Shared Computer Toolkit**  >    >  **Modules d’unity de mouvement leap distincts**</span><span class="sxs-lookup"><span data-stu-id="45038-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="45038-189">autorisez l’actualisation unity en tant que références dans **Microsoft. MixedReality. Shared Computer Toolkit. Le fichier Providers. LeapMotion. asmdef** est modifié dans cette étape</span><span class="sxs-lookup"><span data-stu-id="45038-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="45038-190">Fermer Unity</span><span class="sxs-lookup"><span data-stu-id="45038-190">Close Unity</span></span>
1. <span data-ttu-id="45038-191">fermer Visual Studio, s’il est ouvert</span><span class="sxs-lookup"><span data-stu-id="45038-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="45038-192">Ouvrez l’Explorateur de fichiers et accédez à la racine du projet MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="45038-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="45038-193">Supprimer le répertoire **UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="45038-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="45038-194">Supprimer le répertoire **UnityProjectName/Assets/plugin/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="45038-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="45038-195">Supprimer le fichier **UnityProjectName/Assets/plugin/LeapMotion. meta**</span><span class="sxs-lookup"><span data-stu-id="45038-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="45038-196">Rouvrir Unity</span><span class="sxs-lookup"><span data-stu-id="45038-196">Reopen Unity</span></span>

<span data-ttu-id="45038-197">Dans Unity 2018,4, vous remarquerez peut-être que des erreurs subsistent dans la console après la suppression de la bibliothèque et des ressources de noyau de mouvement LEAP.</span><span class="sxs-lookup"><span data-stu-id="45038-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="45038-198">Si les erreurs sont consignées après la réouverture, redémarrez Unity.</span><span class="sxs-lookup"><span data-stu-id="45038-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="45038-199">Erreurs courantes</span><span class="sxs-lookup"><span data-stu-id="45038-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="45038-200">Le mouvement LEAP n’a pas été intégré à MRTK</span><span class="sxs-lookup"><span data-stu-id="45038-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="45038-201">Pour tester si les modules Unity de mouvement LEAP sont intégrés à MRTK :</span><span class="sxs-lookup"><span data-stu-id="45038-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="45038-202">accédez à la **réalité mixte Shared Computer Toolkit > utilitaires > Motion Motion > vérifier l’état d’intégration**</span><span class="sxs-lookup"><span data-stu-id="45038-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="45038-203">Une fenêtre contextuelle s’affiche avec un message indiquant si les modules d’unité de mouvement LEAP sont intégrés à MRTK.</span><span class="sxs-lookup"><span data-stu-id="45038-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="45038-204">Si le message indique que les ressources n’ont pas été intégrées :</span><span class="sxs-lookup"><span data-stu-id="45038-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="45038-205">S’assurer que les modules Unity de mouvement LEAP se trouvent dans le projet</span><span class="sxs-lookup"><span data-stu-id="45038-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="45038-206">Assurez-vous que la version ajoutée est prise en charge, consultez le tableau en haut de la page pour connaître les versions prises en charge.</span><span class="sxs-lookup"><span data-stu-id="45038-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="45038-207">essayez la Shared Computer Toolkit de la **réalité mixte > utilitaires > le mouvement leap > intégrer les Modules unity de mouvement leap**</span><span class="sxs-lookup"><span data-stu-id="45038-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="45038-208">Échec de la copie des HLAPI multijoueur de l’assembly</span><span class="sxs-lookup"><span data-stu-id="45038-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="45038-209">Cette erreur peut être consignée lors de l’importation des ressources principales de l’Unity de mouvement LEAP :</span><span class="sxs-lookup"><span data-stu-id="45038-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="45038-210">**Solution**</span><span class="sxs-lookup"><span data-stu-id="45038-210">**Solution**</span></span>

- <span data-ttu-id="45038-211">Une solution à bref terme consiste à redémarrer Unity.</span><span class="sxs-lookup"><span data-stu-id="45038-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="45038-212">Pour plus d’informations, consultez le [problème 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) .</span><span class="sxs-lookup"><span data-stu-id="45038-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="45038-213">Exemple de scène de mouvement LEAP</span><span class="sxs-lookup"><span data-stu-id="45038-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="45038-214">l’exemple de scène utilise le profil DefaultLeapMotionConfiguration et détermine si le projet unity a été configuré correctement pour utiliser le Fournisseur de données de mouvement Leap.</span><span class="sxs-lookup"><span data-stu-id="45038-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="45038-215">l’exemple de scène est contenu dans **Microsoft. MixedReality. Shared Computer Toolkit. Exemples** de package dans le répertoire **MRTK/examples/démos/HandTracking/** .</span><span class="sxs-lookup"><span data-stu-id="45038-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="45038-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45038-216">See also</span></span>

- [<span data-ttu-id="45038-217">Fournisseurs d’entrée</span><span class="sxs-lookup"><span data-stu-id="45038-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="45038-218">Suivi de la main</span><span class="sxs-lookup"><span data-stu-id="45038-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
