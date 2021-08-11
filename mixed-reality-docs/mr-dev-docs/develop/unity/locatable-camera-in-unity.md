---
title: Appareil photo et caméra vidéo dans Unity
description: Découvrez comment capturer une photo dans un fichier ou un Texture2D, comment capturer une photo et interagir avec les octets bruts, et comment capturer une vidéo.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: photo, vidéo, hololens, appareil photo, Unity, localisable, PVC, caméra vidéo photo, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, webcam, capture de photos, capture vidéo
ms.openlocfilehash: 4fdf895e6b2b7ed1fc051b45b07ce49052f8a95587178caddfc71a0cfd364eee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193503"
---
# <a name="photo-video-camera-in-unity"></a>Appareil photo et caméra vidéo dans Unity

## <a name="enabling-the-capability-for-camera-access"></a>Activation de la fonctionnalité d’accès à l’appareil photo

La fonctionnalité « WebCam » doit être déclarée pour qu’une application utilise l' [appareil photo](../platform-capabilities-and-apis/locatable-camera.md).

1. dans l’éditeur unity, accédez aux paramètres du lecteur en accédant à la page modifier > Project Paramètres > player.
2. sélectionnez l’onglet « Store de Windows »
3. dans la section « Paramètres des fonctionnalités de > de publication », vérifiez les fonctionnalités de la **WebCam** et du **Microphone**

Une seule opération peut être effectuée avec la caméra à la fois. Vous pouvez vérifier le mode avec lequel l’appareil photo est actuellement dans `UnityEngine.XR.WSA.WebCam.Mode` unity 2018 et les versions antérieures ou `UnityEngine.Windows.WebCam.Mode` dans unity 2019 et versions ultérieures. Les modes disponibles sont photo, Video ou None.

## <a name="photo-capture"></a>Capture de photos

**Espace de noms (avant unity 2019) :** *UnityEngine. XR. WSA. Webcam*<br>
**Espace de noms (unity 2019 et versions ultérieures) :** *UnityEngine. Windows. WebCam*<br>
**Type :** *PhotoCapture*

Le type *PhotoCapture* vous permet de prendre des photographies avec la caméra photo. Le modèle général d’utilisation de *PhotoCapture* pour prendre une photo est le suivant :

1. Créer un objet *PhotoCapture*
2. Créer un objet *CameraParameters* avec les paramètres souhaités
3. Démarrer le mode photo via *StartPhotoModeAsync*
4. Prenez la photo souhaitée
    * facultatif Interagir avec cette image
5. Arrêter le mode photo et nettoyer les ressources

### <a name="common-set-up-for-photocapture"></a>Configuration commune pour la PhotoCapture

Pour les trois utilisations, commencez par les trois premières étapes ci-dessus.

Commencez par créer un objet *PhotoCapture*

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

Stockez ensuite votre objet, définissez vos paramètres et démarrez le mode photo

```cs
private PhotoCapture photoCaptureObject = null;

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

À la fin, vous utiliserez également le même code de nettoyage présenté ici

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

Après ces étapes, vous pouvez choisir le type de photo à capturer.

### <a name="capture-a-photo-to-a-file"></a>Capturer une photo dans un fichier

L’opération la plus simple consiste à capturer directement une photo dans un fichier. La photo peut être enregistrée au format JPG ou PNG.

Si vous avez correctement démarré le mode photo, prenez une photo et stockez-la sur le disque

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

Après avoir capturé la photo sur le disque, quittez le mode photo, puis nettoyez vos objets.

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>Capturer une photo sur un Texture2D à l’aide de l’emplacement

Lors de la capture de données dans un Texture2D, le processus est similaire à la capture sur le disque.

Suivez le processus d’installation ci-dessus.

Dans *OnPhotoModeStarted*, capturez un frame en mémoire.

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

Vous appliquerez ensuite votre résultat à une texture et utiliserez le code de nettoyage commun ci-dessus.

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

#### <a name="locatable-camera"></a>Appareil photo localisable

Pour placer cette texture dans la scène et l’afficher à l’aide des matrices de caméra localisables, ajoutez le code suivant à *OnCapturedPhotoToMemory* dans le `result.success` contrôle :

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

[Unity a fourni un exemple de code](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) pour l’application de la matrice de projection à un nuanceur spécifique sur ses forums.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Capturer une photo et interagir avec les octets bruts

Pour interagir avec les octets bruts d’un dans le frame de mémoire, suivez les mêmes étapes de configuration que ci-dessus et *OnPhotoModeStarted* comme pour la capture d’une photo sur un Texture2D. La différence réside dans *OnCapturedPhotoToMemory* où vous pouvez récupérer les octets bruts et interagir avec eux.

Dans cet exemple, vous allez créer une *liste <Color>* qui sera traitée ou appliquée à une texture à l’aide de *setPixels ()*

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

## <a name="video-capture"></a>Capture vidéo

**Espace de noms (avant unity 2019) :** *UnityEngine. XR. WSA. Webcam*<br>
**Espace de noms (unity 2019 et versions ultérieures) :** *UnityEngine. Windows. WebCam*<br>
**Type :** *VideoCapture*

*VideoCapture* fonctionne de la même façon que *PhotoCapture*. Les deux seules différences sont que vous devez spécifier une valeur d’images par seconde (FPS) et vous ne pouvez enregistrer directement sur le disque qu’en tant que fichier .mp4. Les étapes d’utilisation de *VideoCapture* sont les suivantes :

1. Créer un objet *VideoCapture*
2. Créer un objet *CameraParameters* avec les paramètres souhaités
3. Démarrer le mode vidéo via *StartVideoModeAsync*
4. Démarrer l’enregistrement vidéo
5. Arrêter l’enregistrement de la vidéo
6. Arrêter le mode vidéo et nettoyer les ressources

Commencez par créer notre  objet VideoCapture *VideoCapture m_VideoCapture = null ;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

Ensuite, configurez les paramètres souhaités pour l’enregistrement et démarrer.

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
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

Une fois démarré, commencez l’enregistrement.

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

Une fois l’enregistrement démarré, vous pouvez mettre à jour votre interface utilisateur ou les comportements pour activer l’arrêt. Ici, vous venez de consigner.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

À un moment ultérieur, vous souhaiterez arrêter l’enregistrement à l’aide d’un minuteur ou d’une entrée utilisateur, par exemple.

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

Une fois l’enregistrement arrêté, arrêtez le mode vidéo et nettoyez vos ressources.

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

## <a name="troubleshooting"></a>Dépannage

* Aucune résolution n’est disponible
  * Assurez-vous que la fonctionnalité **webcam** est spécifiée dans votre projet.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement Unity que nous avons disposé, vous êtes en train d’explorer les fonctionnalités de la plateforme de réalité mixte et les API. À partir d’ici, vous pouvez passer au sujet suivant :

> [!div class="nextstepaction"]
> [Point de focus](focus-point-in-unity.md)

Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :

> [!div class="nextstepaction"]
> [déployez sur HoloLens ou Windows Mixed Reality des casques immersifs](../platform-capabilities-and-apis/using-visual-studio.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#3-advanced-features) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Appareil photo localisable](../platform-capabilities-and-apis/locatable-camera.md)