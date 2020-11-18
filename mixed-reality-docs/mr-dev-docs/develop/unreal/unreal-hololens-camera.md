---
title: Appareil photo/vidéo HoloLens dans Unreal
description: Guide d’utilisation de l’appareil photo/vidéo HoloLens dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, caméra, appareil photo/vidéo, capture de Réalité Mixte
ms.openlocfilehash: 6302a64fcde2a16b6ae1cb570215629a3e6ea9e5
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573233"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="598c9-104">Appareil photo/vidéo HoloLens dans Unreal</span><span class="sxs-lookup"><span data-stu-id="598c9-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="598c9-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="598c9-105">Overview</span></span>

<span data-ttu-id="598c9-106">HoloLens propose un appareil photo/vidéo qui est utilisé pour la capture de Réalité Mixte, et qui peut également être utilisé par une application pour accéder à des visuels du monde réel.</span><span class="sxs-lookup"><span data-stu-id="598c9-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="598c9-107">L’appareil photo/vidéo n’est pas pris en charge avec la communication à distance holographique, mais il est possible d’utiliser une webcam connectée à votre PC pour simuler la fonctionnalité d’appareil photo/vidéo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="598c9-107">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="598c9-108">Affichage à partir de l’appareil photo/vidéo pour la capture de Réalité Mixte</span><span class="sxs-lookup"><span data-stu-id="598c9-108">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="598c9-109">Cela nécessite **Unreal Engine 4.25** ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="598c9-109">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="598c9-110">Le système et les enregistreurs personnalisés créent des captures de Réalité Mixte en combinant l’appareil photo/vidéo à des hologrammes affichés par l’application immersive.</span><span class="sxs-lookup"><span data-stu-id="598c9-110">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="598c9-111">Par défaut, la capture de Réalité Mixte utilise la sortie holographique de l’œil droit.</span><span class="sxs-lookup"><span data-stu-id="598c9-111">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="598c9-112">Si une application immersive choisit de s’[afficher à partir de l’appareil photo/vidéo](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), alors cette sortie sera utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="598c9-112">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="598c9-113">Cela améliore le mappage entre le monde réel et les hologrammes dans la vidéo MRC.</span><span class="sxs-lookup"><span data-stu-id="598c9-113">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="598c9-114">Pour choisir le rendu à partir de l’appareil photo/vidéo :</span><span class="sxs-lookup"><span data-stu-id="598c9-114">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="598c9-115">Appelez **SetEnabledMixedRealityCamera** et **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="598c9-115">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="598c9-116">Utilisez les valeurs de taille **Size X** et **Size Y** pour définir les dimensions de la vidéo.</span><span class="sxs-lookup"><span data-stu-id="598c9-116">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Troisième caméra](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="598c9-118">Unreal va ensuite gérer les requêtes de capture de Réalité Mixte pour effectuer le rendu du point de vue de l’appareil photo/vidéo.</span><span class="sxs-lookup"><span data-stu-id="598c9-118">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="598c9-119">C’est seulement quand la [capture de Réalité Mixte](../../mixed-reality-capture.md) est déclenchée qu’il est demandé à l’application de s’afficher du point de vue de l’appareil photo/vidéo.</span><span class="sxs-lookup"><span data-stu-id="598c9-119">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="598c9-120">Utilisation de l’appareil photo/vidéo</span><span class="sxs-lookup"><span data-stu-id="598c9-120">Using the PV Camera</span></span>

<span data-ttu-id="598c9-121">La texture de la webcam peut être récupérée dans le jeu au moment de l’exécution. Toutefois, vous devez l’activer dans l’éditeur **Edit > Project Settings** (Modifier > Paramètres du projet) :</span><span class="sxs-lookup"><span data-stu-id="598c9-121">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="598c9-122">Accédez à **Platforms > HoloLens > Capabilities** (Plateformes > HoloLens > Fonctionnalités), puis cochez **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="598c9-122">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="598c9-123">Utilisez la fonction **StartCameraCapture** pour utiliser la webcam au moment de l’exécution, et la fonction **StopCameraCapture** pour arrêter l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="598c9-123">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Démarrer/Arrêter la caméra](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="598c9-125">Affichage d’une image</span><span class="sxs-lookup"><span data-stu-id="598c9-125">Rendering an image</span></span>
<span data-ttu-id="598c9-126">Pour afficher l’image de l’appareil photo :</span><span class="sxs-lookup"><span data-stu-id="598c9-126">To render the camera image:</span></span>
1. <span data-ttu-id="598c9-127">Créez une instance de matériau dynamique basée sur un matériau du projet, nommé **PVCamMat** dans la capture d’écran ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="598c9-127">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="598c9-128">Définissez l’instance de matériau dynamique sur une variable **Material Instance Dynamic Object Reference**.</span><span class="sxs-lookup"><span data-stu-id="598c9-128">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="598c9-129">Définissez le matériau de l’objet de la scène qui affichera le flux de l’appareil sur cette nouvelle instance de matériau dynamique.</span><span class="sxs-lookup"><span data-stu-id="598c9-129">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="598c9-130">Démarrez un minuteur qui sera utilisé pour lier l’image de l’appareil au matériau.</span><span class="sxs-lookup"><span data-stu-id="598c9-130">Start a timer that will be used to bind the camera image to the material.</span></span>

![Rendu de la caméra](images/unreal-camera-render.PNG)

4. <span data-ttu-id="598c9-132">Créez une fonction pour ce minuteur, dans ce cas **MaterialTimer**, puis appelez **GetARCameraImage** pour obtenir la texture à partir de la webcam.</span><span class="sxs-lookup"><span data-stu-id="598c9-132">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="598c9-133">Si la texture est correcte, définissez un paramètre de texture dans le nuanceur de cette image.</span><span class="sxs-lookup"><span data-stu-id="598c9-133">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="598c9-134">Sinon, redémarrez le minuteur de matériau.</span><span class="sxs-lookup"><span data-stu-id="598c9-134">Otherwise, start the material timer again.</span></span>

![Texture de la caméra à partir de la webcam](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="598c9-136">Vérifiez que le matériau comprend un paramètre correspondant au nom situé dans **SetTextureParameterValue**, qui est lié à une entrée de couleur.</span><span class="sxs-lookup"><span data-stu-id="598c9-136">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="598c9-137">Sans cela, l’image de l’appareil photo/vidéo ne pourra pas être affichée correctement.</span><span class="sxs-lookup"><span data-stu-id="598c9-137">Without this, the camera image can't be properly displayed.</span></span>

![Texture de la caméra](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="598c9-139">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="598c9-139">Next Development Checkpoint</span></span>

<span data-ttu-id="598c9-140">Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les API et fonctionnalités de la plateforme Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="598c9-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="598c9-141">À partir de là, vous pouvez passer à la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="598c9-141">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="598c9-142">Codes QR</span><span class="sxs-lookup"><span data-stu-id="598c9-142">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="598c9-143">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="598c9-143">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="598c9-144">Déploiement sur un appareil</span><span class="sxs-lookup"><span data-stu-id="598c9-144">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="598c9-145">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="598c9-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="598c9-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="598c9-146">See also</span></span>
* [<span data-ttu-id="598c9-147">Appareil photo localisable</span><span class="sxs-lookup"><span data-stu-id="598c9-147">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="598c9-148">Capture de Réalité Mixte pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="598c9-148">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
