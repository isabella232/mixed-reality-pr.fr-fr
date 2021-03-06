---
title: Appareil photo localisable dans Unity
description: Découvrez comment capturer une photo dans un fichier ou un Texture2D, comment capturer une photo et interagir avec les octets bruts, et comment capturer une vidéo.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: photo, vidéo, hololens, appareil photo, Unity, localisable, PVC, caméra vidéo photo, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, webcam, capture de photos, capture vidéo
ms.openlocfilehash: ccf0c17a5f419341e64a87fb9ef04ef0a40c2a33
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236900"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="ca911-104">Appareil photo localisable dans Unity</span><span class="sxs-lookup"><span data-stu-id="ca911-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="ca911-105">Activation de la fonctionnalité de Photo Video Camera</span><span class="sxs-lookup"><span data-stu-id="ca911-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="ca911-106">La fonctionnalité « WebCam » doit être déclarée pour qu’une application utilise l' [appareil photo](../platform-capabilities-and-apis/locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="ca911-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>
1. <span data-ttu-id="ca911-107">Dans l’éditeur Unity, accédez aux paramètres du lecteur en accédant à la page « modifier les paramètres du projet > > Player ».</span><span class="sxs-lookup"><span data-stu-id="ca911-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="ca911-108">Sélectionner l’onglet « Windows Store »</span><span class="sxs-lookup"><span data-stu-id="ca911-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="ca911-109">Dans la section « fonctionnalités de > des paramètres de publication », vérifiez les fonctionnalités de la **webcam** et du **microphone**</span><span class="sxs-lookup"><span data-stu-id="ca911-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="ca911-110">Une seule opération peut être effectuée avec la caméra à la fois.</span><span class="sxs-lookup"><span data-stu-id="ca911-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="ca911-111">Vous pouvez vérifier le mode dans lequel l’appareil photo se trouve actuellement avec UnityEngine. XR. WSA. WebCam. mode.</span><span class="sxs-lookup"><span data-stu-id="ca911-111">You can check with mode the camera is currently in with UnityEngine.XR.WSA.WebCam.Mode.</span></span> <span data-ttu-id="ca911-112">Les modes disponibles sont photo, Video ou None.</span><span class="sxs-lookup"><span data-stu-id="ca911-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="ca911-113">Capture de photos</span><span class="sxs-lookup"><span data-stu-id="ca911-113">Photo Capture</span></span>

<span data-ttu-id="ca911-114">**Espace de noms :**</span><span class="sxs-lookup"><span data-stu-id="ca911-114">**Namespace:**</span></span>  
<span data-ttu-id="ca911-115">*UnityEngine. XR. WSA. WebCam (Unity \~ 2018) UnityEngine. Windows. Webcam (unity 2019 \~ )*</span><span class="sxs-lookup"><span data-stu-id="ca911-115">*UnityEngine.XR.WSA.WebCam(Unity \~2018) UnityEngine.Windows.WebCam(Unity 2019\~)*</span></span><br>
<span data-ttu-id="ca911-116">**Type :** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="ca911-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="ca911-117">Le type *PhotoCapture* vous permet de prendre des photographies avec la caméra photo.</span><span class="sxs-lookup"><span data-stu-id="ca911-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="ca911-118">Le modèle général d’utilisation de *PhotoCapture* pour prendre une photo est le suivant :</span><span class="sxs-lookup"><span data-stu-id="ca911-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="ca911-119">Créer un objet *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="ca911-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="ca911-120">Créer un objet *CameraParameters* avec les paramètres souhaités</span><span class="sxs-lookup"><span data-stu-id="ca911-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="ca911-121">Démarrer le mode photo via *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="ca911-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="ca911-122">Prenez la photo souhaitée</span><span class="sxs-lookup"><span data-stu-id="ca911-122">Take the photo you want</span></span>
    * <span data-ttu-id="ca911-123">facultatif Interagir avec cette image</span><span class="sxs-lookup"><span data-stu-id="ca911-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="ca911-124">Arrêter le mode photo et nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="ca911-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="ca911-125">Configuration commune pour la PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="ca911-125">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="ca911-126">Pour les trois utilisations, commencez par les trois premières étapes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ca911-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="ca911-127">Commencez par créer un objet *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="ca911-127">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="ca911-128">Stockez ensuite votre objet, définissez vos paramètres et démarrez le mode photo</span><span class="sxs-lookup"><span data-stu-id="ca911-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

<span data-ttu-id="ca911-129">À la fin, vous utiliserez également le même code de nettoyage présenté ici</span><span class="sxs-lookup"><span data-stu-id="ca911-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="ca911-130">Après ces étapes, vous pouvez choisir le type de photo à capturer.</span><span class="sxs-lookup"><span data-stu-id="ca911-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="ca911-131">Capturer une photo dans un fichier</span><span class="sxs-lookup"><span data-stu-id="ca911-131">Capture a Photo to a File</span></span>

<span data-ttu-id="ca911-132">L’opération la plus simple consiste à capturer directement une photo dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="ca911-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="ca911-133">La photo peut être enregistrée au format JPG ou PNG.</span><span class="sxs-lookup"><span data-stu-id="ca911-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="ca911-134">Si vous avez correctement démarré le mode photo, prenez une photo et stockez-la sur le disque</span><span class="sxs-lookup"><span data-stu-id="ca911-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="ca911-135">Après avoir capturé la photo sur le disque, quittez le mode photo, puis nettoyez vos objets.</span><span class="sxs-lookup"><span data-stu-id="ca911-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="ca911-136">Capturer une photo sur un Texture2D</span><span class="sxs-lookup"><span data-stu-id="ca911-136">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="ca911-137">Lors de la capture de données dans un Texture2D, le processus est similaire à la capture sur le disque.</span><span class="sxs-lookup"><span data-stu-id="ca911-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="ca911-138">Suivez le processus d’installation ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ca911-138">Follow the setup process above.</span></span>

<span data-ttu-id="ca911-139">Dans *OnPhotoModeStarted*, capturez un frame en mémoire.</span><span class="sxs-lookup"><span data-stu-id="ca911-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="ca911-140">Vous appliquerez ensuite votre résultat à une texture et utiliserez le code de nettoyage commun ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ca911-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="ca911-141">Capturer une photo et interagir avec les octets bruts</span><span class="sxs-lookup"><span data-stu-id="ca911-141">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="ca911-142">Pour interagir avec les octets bruts d’un dans le frame de mémoire, suivez les mêmes étapes de configuration que ci-dessus et *OnPhotoModeStarted* comme pour la capture d’une photo sur un Texture2D.</span><span class="sxs-lookup"><span data-stu-id="ca911-142">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="ca911-143">La différence réside dans *OnCapturedPhotoToMemory* où vous pouvez récupérer les octets bruts et interagir avec eux.</span><span class="sxs-lookup"><span data-stu-id="ca911-143">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="ca911-144">Dans cet exemple, vous allez créer une *liste <Color>* qui sera traitée ou appliquée à une texture à l’aide de *setPixels ()*</span><span class="sxs-lookup"><span data-stu-id="ca911-144">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a><span data-ttu-id="ca911-145">Capture vidéo</span><span class="sxs-lookup"><span data-stu-id="ca911-145">Video Capture</span></span>

<span data-ttu-id="ca911-146">**Espace de noms :** *UnityEngine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="ca911-146">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="ca911-147">**Type :** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="ca911-147">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="ca911-148">*VideoCapture* fonctionne de la même façon que *PhotoCapture*.</span><span class="sxs-lookup"><span data-stu-id="ca911-148">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="ca911-149">Les deux seules différences sont que vous devez spécifier une valeur d’images par seconde (FPS) et vous ne pouvez enregistrer directement sur le disque qu’en tant que fichier. MP4.</span><span class="sxs-lookup"><span data-stu-id="ca911-149">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="ca911-150">Les étapes d’utilisation de *VideoCapture* sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ca911-150">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="ca911-151">Créer un objet *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="ca911-151">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="ca911-152">Créer un objet *CameraParameters* avec les paramètres souhaités</span><span class="sxs-lookup"><span data-stu-id="ca911-152">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="ca911-153">Démarrer le mode vidéo via *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="ca911-153">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="ca911-154">Démarrer l’enregistrement vidéo</span><span class="sxs-lookup"><span data-stu-id="ca911-154">Start recording video</span></span>
5. <span data-ttu-id="ca911-155">Arrêter l’enregistrement de la vidéo</span><span class="sxs-lookup"><span data-stu-id="ca911-155">Stop recording video</span></span>
6. <span data-ttu-id="ca911-156">Arrêter le mode vidéo et nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="ca911-156">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="ca911-157">Commencez par créer notre  objet VideoCapture *VideoCapture m_VideoCapture = null ;*</span><span class="sxs-lookup"><span data-stu-id="ca911-157">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="ca911-158">Ensuite, configurez les paramètres souhaités pour l’enregistrement et démarrer.</span><span class="sxs-lookup"><span data-stu-id="ca911-158">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

<span data-ttu-id="ca911-159">Une fois démarré, commencez l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ca911-159">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

<span data-ttu-id="ca911-160">Une fois l’enregistrement démarré, vous pouvez mettre à jour votre interface utilisateur ou les comportements pour activer l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="ca911-160">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="ca911-161">Ici, vous venez de consigner.</span><span class="sxs-lookup"><span data-stu-id="ca911-161">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="ca911-162">À un moment ultérieur, vous souhaiterez arrêter l’enregistrement à l’aide d’un minuteur ou d’une entrée utilisateur, par exemple.</span><span class="sxs-lookup"><span data-stu-id="ca911-162">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="ca911-163">Une fois l’enregistrement arrêté, arrêtez le mode vidéo et nettoyez vos ressources.</span><span class="sxs-lookup"><span data-stu-id="ca911-163">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a><span data-ttu-id="ca911-164">Dépannage</span><span class="sxs-lookup"><span data-stu-id="ca911-164">Troubleshooting</span></span>
* <span data-ttu-id="ca911-165">Aucune résolution n’est disponible</span><span class="sxs-lookup"><span data-stu-id="ca911-165">No resolutions are available</span></span>
    * <span data-ttu-id="ca911-166">Assurez-vous que la fonctionnalité **webcam** est spécifiée dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="ca911-166">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ca911-167">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="ca911-167">Next Development Checkpoint</span></span>

<span data-ttu-id="ca911-168">Si vous suivez le parcours du point de contrôle de développement Unity que nous avons disposé, vous êtes en train d’explorer les fonctionnalités de la plateforme de réalité mixte et les API.</span><span class="sxs-lookup"><span data-stu-id="ca911-168">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ca911-169">À partir d’ici, vous pouvez passer au sujet suivant :</span><span class="sxs-lookup"><span data-stu-id="ca911-169">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca911-170">Point de focus</span><span class="sxs-lookup"><span data-stu-id="ca911-170">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="ca911-171">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="ca911-171">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca911-172">Déployer sur HoloLens ou sur des casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ca911-172">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="ca911-173">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#3-advanced-features) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="ca911-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca911-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca911-174">See Also</span></span>
* [<span data-ttu-id="ca911-175">Appareil photo localisable</span><span class="sxs-lookup"><span data-stu-id="ca911-175">Locatable camera</span></span>](../platform-capab ilities-and-apis/locatable-camera.md)
