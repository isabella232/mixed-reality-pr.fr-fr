---
title: Appareil photo localisable
description: informations générales sur le HoloLens appareil photo avant, son fonctionnement et les profils et résolutions disponibles pour les développeurs.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: appareil photo, hololens, caméra couleur, frontal, hololens 2, CV, vision par ordinateur, fiduciaire, marqueurs, code QR, QR, photo, vidéo
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217095"
---
# <a name="locatable-camera"></a>Appareil photo localisable

HoloLens comprend une caméra universelle montée sur l’avant de l’appareil, ce qui permet aux applications de voir ce que l’utilisateur voit. Les développeurs ont accès à l’appareil photo et le contrôle de ce dernier, tout comme pour les caméras couleur sur les smartphones, les ordinateurs portables ou les ordinateurs de bureau. Les mêmes API Universal Windows [Media capture](/uwp/api/Windows.Media.Capture.MediaCapture) et Windows Media Foundation qui fonctionnent sur les appareils mobiles et de bureau sur HoloLens. Unity [a encapsulé ces API Windows sur les](../unity/locatable-camera-in-unity.md) fonctionnalités d’utilisation d’appareil photo abstraites sur HoloLens. Les tâches de fonctionnalités incluent la mise en place de photos et vidéos normales (avec ou sans hologrammes) et la localisation de la caméra dans et la perspective sur la scène.

## <a name="device-camera-information"></a>Informations sur l’appareil photo

### <a name="hololens-first-generation"></a>HoloLens (première génération)

* Correction de l’appareil photo/vidéo (PV) avec une balance des blancs automatique, une exposition automatique et un pipeline de traitement d’image complet.
* La lumière blanche sur la confidentialité dans le monde s’illumine quand l’appareil photo est actif
* L’appareil photo prend en charge les modes suivants (tous les modes sont des proportions 16:9) à 30, 24, 20, 15 et 5 i/s :

  |  Vidéo  |  Préversion  |  Subsist  |  Champ horizontal de l’affichage (H-angle d’affichage) |  Utilisation suggérée | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45 deg  |  (mode par défaut avec stabilisation vidéo) | 
  |  N/A |  N/A |  2048x1152 |  67 deg |  Image toujours la plus haute résolution | 
  |  1408x792 |  1408x792 |  1408x792 |  48 deg |  Résolution de suranalyse (remplissage) avant la stabilisation vidéo | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  Mode vidéo grand angle avec suranalyse | 
  |  896x504 |  896x504 |  896x504 |  48 deg |  Mode faible puissance/basse résolution pour les tâches de traitement des images | 

### <a name="hololens-2"></a>HoloLens 2

* Appareil photo/vidéo (PV) de focalisation automatique avec balance des blancs automatique, exposition automatique et pipeline de traitement d’image complet.
* La lumière blanche sur la confidentialité dans le monde s’illumine quand l’appareil photo est actif.
* HoloLens 2 prend en charge différents profils d’appareil photo. Découvrez comment [découvrir et sélectionner les fonctionnalités de l’appareil photo](/windows/uwp/audio-video-camera/camera-profiles).
* L’appareil photo prend en charge les profils et résolutions suivants (tous les modes vidéo sont des proportions 16:9) :
  
  | Profil                                         | Vidéo     | Préversion   | Subsist     | Fréquences d’images | Champ horizontal de l’affichage (H-angle d’affichage) | Utilisation suggérée                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Hérité, 0 BalancedVideoAndPhoto, 100             | 2272x1278 | 2272x1278 |           | 15,30       | 64,69                            | Enregistrement vidéo de haute qualité                |
  | Hérité, 0 BalancedVideoAndPhoto, 100             | 896x504   | 896x504   |           | 15,30       | 64,69                            | Aperçu du flux pour la capture de photos de haute qualité |
  | Hérité, 0 BalancedVideoAndPhoto, 100             |           |           | 3904x2196 |             | 64,69                            | Capture photo de haute qualité                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64,69                            | Scénarios de longue durée                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15,30       | 64,69                            | Scénarios de longue durée                     |
  | Visioconférence, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 1920 x 1080 | 1920 x 1080 | 1920 x 1080 | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 960 x 540   |           |           | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 640 x 360   |           |           | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |
  | Visioconférence, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15, 30       | 64,69                            | Vidéoconférence, scénarios de longue durée |

> [!NOTE]
> Les clients peuvent tirer parti de la capture de la [réalité mixte](/hololens/holographic-photos-and-videos) pour prendre des vidéos ou des photos de votre application, notamment des hologrammes et une stabilisation vidéo.
>
>En tant que développeur, vous devez tenir compte de certaines considérations lors de la création de votre application si vous souhaitez qu’elle apparaisse aussi bonne que possible quand un client capture du contenu. Vous pouvez également activer (et personnaliser) la capture de la réalité mixte à partir de directement dans votre application. En savoir plus sur la [capture de la réalité mixte pour les développeurs](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Localisation de l’appareil photo de l’appareil dans le monde

lorsque HoloLens prend des photos et des vidéos, les frames capturés incluent l’emplacement de la caméra dans le monde et le modèle d’objectif de l’appareil photo. Cela permet aux applications de connaître la position de la caméra dans le monde réel pour les scénarios de création d’images augmentés. Les développeurs peuvent déployer de manière créative leurs propres scénarios à l’aide de leur traitement d’image préféré ou de leurs bibliothèques de vision d’ordinateur personnalisées.

la « caméra », ailleurs dans HoloLens documentation, peut faire référence à la « caméra de jeu virtuelle » (le frustum rendu de l’application à). Sauf indication contraire, « Camera » sur cette page fait référence à la caméra de couleurs RVB réelle.

### <a name="using-unity"></a>Utilisation de Unity

Pour passer des « CameraIntrinsics » et « CameraCoordinateSystem » à votre système de coordonnées de l’application/du monde, suivez les instructions de l’article [appareil photo localisable dans Unity](../unity/locatable-camera-in-unity.md) .  CameraToWorldMatrix est automatiquement fourni par la classe PhotoCaptureFrame. vous n’avez donc pas à vous soucier des transformations CameraCoordinateSystem décrites ci-dessous.

### <a name="using-mediaframereference"></a>Utilisation de MediaFrameReference

Ces instructions s’appliquent si you’r utilise la classe [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) pour lire des images d’image à partir de l’appareil photo.

Chaque image (qu’il s’agisse d’une photo ou d’une vidéo) comprend un [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) enraciné à l’appareil photo au moment de la capture, qui est accessible à l’aide de la propriété [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) de votre [MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Chaque frame contient une description du modèle d’objectif de l’appareil photo, qui se trouve dans la propriété [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) . Ensemble, ces transformations définissent pour chaque pixel un rayon dans l’espace 3D représentant le chemin emprunté par les photons qui ont produit le pixel. Ces rayons peuvent être liés à d’autres contenus dans l’application en obtenant la transformation du système de coordonnées du cadre vers un autre système de coordonnées (par exemple, à partir d’une [image stationnaire de référence](../../design/coordinate-systems.md#stationary-frame-of-reference)). 

Chaque frame d’image fournit les éléments suivants :
* Données de pixels (au format RGB/NV12/JPEG/etc.)
* Un [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) à partir de l’emplacement de capture
* Une classe [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) contenant le mode de l’objectif de l’appareil photo

L' [exemple HolographicFaceTracking](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) illustre la manière assez simple d’interroger la transformation entre le système de coordonnées de l’appareil photo et vos propres systèmes de coordonnées de l’application.

### <a name="using-media-foundation"></a>Utilisation de Media Foundation

Si vous utilisez Media Foundation directement pour lire des images d’images à partir de l’appareil photo, vous pouvez utiliser l’attribut [MFSampleExtension_CameraExtrinsics](/windows/win32/medfound/mfsampleextension-cameraextrinsics) de chaque frame et [MFSampleExtension_PinholeCameraIntrinsics attribut](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) pour rechercher des frames de caméra par rapport aux autres systèmes de coordonnées de votre application, comme illustré dans cet exemple de code :

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>Erreur de distorsion

sur HoloLens, les flux vidéo et d’images fixes ne sont pas déformés dans le pipeline de traitement des images du système avant que les frames ne soient mis à disposition de l’application (le flux de préversion contient les trames distordues d’origine). Étant donné que seules les CameraIntrinsics sont disponibles, les applications doivent supposer que les images d’images représentent une caméra Pinhole parfaite.

sur HoloLens (première génération), la fonction d’information dans le processeur d’images peut toujours provoquer une erreur pouvant atteindre 10 pixels lors de l’utilisation de CameraIntrinsics dans les métadonnées de frame. Dans de nombreux cas d’utilisation, cette erreur n’a pas d’importance, mais si vous alignez des hologrammes sur des affiches/marqueurs réels, par exemple, et que vous remarquez une <décalage de 10 px (environ 11 mm pour les hologrammes positionnés sur 2 mètres), cette erreur de distorsion peut en être la cause. 

## <a name="locatable-camera-usage-scenarios"></a>Scénarios d’utilisation d’appareil photo localisables

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Afficher une photo ou une vidéo dans le monde où elle a été capturée

Les cadres de l’appareil photo sont fournis avec une transformation « caméra à toute la vie », qui peut être utilisée pour indiquer exactement où se trouvait l’appareil lorsque l’image a été prise. Par exemple, vous pouvez positionner une petite icône holographique à cet emplacement (CameraToWorld. MultiplyPoint (Vector3. Zero)) et même dessiner une petite flèche dans la direction vers laquelle l’appareil photo était dirigée (CameraToWorld. MultiplyVector (Vector3. Forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Étiquette/modèle/affiche/suivi d’objet

De nombreuses applications de réalité mixte utilisent une image ou un modèle visuel identifiable pour créer un point de suivi dans l’espace. Il est ensuite utilisé pour restituer des objets par rapport à ce point ou créer un emplacement connu. certaines utilisations de HoloLens incluent la recherche d’un objet réel marqué avec des appariés (par exemple, un moniteur TV avec un code QR), le placement d’hologrammes sur des personnes fiduciaires et le couplage visuel avec des appareils non HoloLens tels que des tablettes qui ont été configurés pour communiquer avec HoloLens via Wi-Fi.

Vous aurez besoin de quelques éléments pour reconnaître un modèle visuel et placer un objet dans l’espace universel des applications :
1. Boîte à outils de reconnaissance de modèle d’image, telle que le code QR, les balises AR, le Finder de visages, les traceurs de cercle, la reconnaissance optique, etc.
2. Collecter les trames d’image au moment de l’exécution et les transmettre à la couche de reconnaissance
3. Déprojetez leurs emplacements d’images dans des positions universelles ou des rayons de monde probables. 
4. Positionner vos modèles virtuels sur ces emplacements mondiaux

Liens importants de traitement d’images :
* [OpenCV](https://opencv.org/)
* [Balises QR](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Le maintien d’une fréquence d’images d’application interactive est essentiel, en particulier lors du traitement des algorithmes de reconnaissance d’images à long terme. Pour cette raison, nous utilisons généralement le modèle suivant :
1. Thread principal : gère l’objet Camera
2. Thread principal : demande de nouveaux frames (Async)
3. Thread principal : passer de nouveaux frames au thread de suivi
4. Thread de suivi : traite l’image pour collecter des points clés
5. Thread principal : déplace le modèle virtuel pour trouver les points clés trouvés
6. Thread principal : répéter à l’étape 2

Certains systèmes de marqueurs d’images ne fournissent qu’un seul emplacement de pixel (les autres fournissent la transformation complète, auquel cas cette section n’est pas nécessaire), qui équivaut à un rayon d’emplacements possibles. Pour atteindre un emplacement 3D unique, nous pouvons ensuite tirer parti de plusieurs rayons et trouver le résultat final en fonction de leur intersection approximative. Pour ce faire, procédez comme suit :
1. Obtenir une boucle qui collecte plusieurs images d’appareil photo
2. Rechercher les points de fonctionnalités associés et leurs rayons mondiaux
3. Lorsque vous disposez d’un dictionnaire de fonctionnalités, chacun avec plusieurs rayons de monde, vous pouvez utiliser le code suivant pour résoudre l’intersection de ces rayons :

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

À partir de deux ou plusieurs emplacements d’étiquette suivis, vous pouvez positionner une scène modélisée pour l’adapter au scénario actuel de l’utilisateur. Si vous ne pouvez pas supposer la gravité, vous aurez besoin de trois emplacements de balises. Dans de nombreux cas, nous utilisons un modèle de couleurs dans lequel les blancs représentent les emplacements de balises suivis en temps réel et les sphères bleues représentent les emplacements de balise modélisés. Cela permet à l’utilisateur de mesurer visuellement la qualité d’alignement. Nous supposons l’installation suivante dans toutes nos applications :
* Deux ou plusieurs emplacements de balise modélisés
* Un « espace d’étalonnage », qui, dans la scène, est le parent des balises
* Identificateur de la fonctionnalité de l’appareil photo
* Comportement, qui déplace l’espace d’étalonnage pour aligner les balises modélisées avec les balises en temps réel (nous sommes prudents de déplacer l’espace parent, pas les marqueurs modélisés eux-mêmes, car d’autres connexions sont des positions relatives à eux).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Suivre ou identifier des objets/visages à l’aide de voyants ou d’autres bibliothèques de reconnaissance

Exemples :
* Robots industriels avec del (ou codes QR pour des objets en déplacement plus lents)
* Identifier et reconnaître des objets dans la salle
* Identifiez et reconnaissez des personnes dans la salle, par exemple en plaçant des cartes de contact holographiques sur des visages

## <a name="see-also"></a>Voir aussi
* [Exemple d’appareil photo localisable](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Appareil photo localisable dans Unity](../unity/locatable-camera-in-unity.md)
* [MRC (Mixed Reality Capture)](/hololens/holographic-photos-and-videos)
* [Capture de Réalité Mixte pour les développeurs](mixed-reality-capture-for-developers.md)
* [Présentation de la capture multimédia](/windows/uwp/audio-video-camera/)
* [Exemple de suivi de visage holographique](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)