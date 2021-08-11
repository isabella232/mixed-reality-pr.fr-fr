---
title: Suivi des codes QR
description: Apprenez à détecter les codes QR, à ajouter des fonctionnalités de webcam et à gérer des systèmes de coordonnées dans des applications de réalité mixte sur HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: VR, LBE, divertissement basé sur l’emplacement, VR arcade, arcade, immersif, QR, code QR, hololens2
ms.openlocfilehash: f6d2f224b9f477cf78ba4f0a5b6ce362f629d06988e966d71ed03bc48eda41d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193708"
---
# <a name="qr-code-tracking"></a>Suivi des codes QR

HoloLens 2 peut détecter les codes QR dans l’environnement situé autour du casque, ce qui permet d’établir un système de coordonnées à l’emplacement réel de chaque code. Une fois que vous avez activé la webcam de votre appareil, vous pouvez reconnaître les codes QR dans les dernières versions de vos projets inréel ou Unity. Avant de passer en production, nous vous recommandons de suivre les [meilleures pratiques](#best-practices-for-qr-code-detection) que nous avons présentées à la fin de l’article.

## <a name="device-support"></a>Prise en charge des appareils

<table>
<tr>
<th>Fonctionnalité</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (première génération)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Casques immersifs</a></th>
</tr><tr>
<td> Détection du code QR</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>le suivi du code QR avec des casques Windows Mixed Reality immersifs sur les ordinateurs de bureau est pris en charge sur Windows 10 Version 2004 et versions ultérieures. Utilisez l’API Microsoft. MixedReality. QRCodeWatcher. IsSupported () pour déterminer si la fonctionnalité est prise en charge sur l’appareil actuel.

## <a name="getting-the-qr-package"></a>Obtention du package QR

vous pouvez télécharger le package NuGet pour la détection du code QR [ici](https://nuget.org/Packages/Microsoft.MixedReality.QR).

## <a name="using-openxr"></a>Utilisation de OpenXR

Lorsque vous utilisez le plug-in OpenXR, récupérez le [ `SpatialGraphNodeId` à partir de l’API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) et utilisez l' `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API pour localiser le code QR.

pour référence, nous disposons d’un [exemple de projet de suivi QR sur GitHub](https://github.com/yl-msft/QRTracking) avec une explication plus détaillée de l' [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="detecting-qr-codes"></a>Détection des codes QR

### <a name="adding-the-webcam-capability"></a>Ajout de la fonctionnalité webcam

Vous devez ajouter la fonctionnalité `webcam` à votre manifeste pour détecter les codes QR. Cette fonctionnalité est requise, car les données dans les codes détectés dans l’environnement de l’utilisateur peuvent contenir des informations sensibles.

L’autorisation peut être demandée en appelant `QRCodeWatcher.RequestAccessAsync()` :

_C#_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

Vous devez demander une autorisation avant de construire un objet QRCodeWatcher.

Si la détection du code QR requiert la `webcam` fonctionnalité, la détection se produit à l’aide des caméras de suivi de l’appareil. Cela fournit un angle de détection plus vaste et une plus grande autonomie de batterie par rapport à la détection avec l’appareil photo/vidéo (PV) de l’appareil.

### <a name="detecting-qr-codes-in-unity"></a>Détection des codes QR dans Unity

vous pouvez utiliser l’API de détection du code QR dans unity sans importer MRTK en installant le package NuGet à l’aide [de NuGet pour unity](https://github.com/GlitchEnzo/NuGetForUnity). Si vous souhaitez avoir une idée de son fonctionnement, téléchargez l’exemple d' [application Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes). L’exemple d’application contient des exemples d’affichage d’un carré holographique sur des codes QR et des données associées telles que le GUID, la taille physique, l’horodatage et les données décodées.

### <a name="detecting-qr-codes-in-c"></a>Détection des codes QR en C++

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Obtention du système de coordonnées pour un code QR

Chaque code QR détecté expose un [système de coordonnées spatiales](../../design/coordinate-systems.md) aligné avec le code QR dans l’angle supérieur gauche du carré détection rapide dans le coin supérieur gauche :  

![Système de coordonnées du code QR](images/Qr-coordinatesystem.png) 

Lorsque vous utilisez directement le kit de développement logiciel (SDK) QR, l’axe Z pointe sur le papier (non affiché)-en cas de conversion en coordonnées Unity, l’axe Z pointe hors du papier et est droitier.

Le SpatialCoordinateSystem d’un code QR s’aligne comme indiqué. Vous pouvez récupérer le système de coordonnées à partir de la plateforme en appelant <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview :: CreateCoordinateSystemForNode</a> et en passant le SpatialGraphNodeId du code.

Le code C++ ci-dessous montre comment créer un rectangle et le placer à l’aide du système de coordonnées du code QR :

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

Vous pouvez utiliser la taille physique pour créer le rectangle QR :

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

Le système de coordonnées peut être utilisé pour dessiner le code QR ou pour attacher des hologrammes à l’emplacement :

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

À l’instar de, votre *QRCodeAddedHandler* peut ressembler à ceci :

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>Meilleures pratiques pour la détection du code QR

### <a name="quiet-zones-around-qr-codes"></a>Zones calmes autour des codes QR

Pour être lu correctement, les codes QR nécessitent une marge autour de tous les côtés du code. Cette marge ne doit pas contenir de contenu imprimé et doit être de quatre modules (un carré noir unique dans le code). 

La [spécification QR](https://www.qrcode.com/en/howto/code.html) contient plus d’informations sur les zones silencieuses.

### <a name="lighting-and-backdrop"></a>Éclairage et toile de fond
La qualité de la détection du code QR est susceptible de varier l’éclairage et le fond. 

Dans une scène avec un éclairage brillant, imprimez un code noir sur un arrière-plan gris. Sinon, imprimez un code QR noir sur un arrière-plan blanc.

Si le fond du code est sombre, essayez un code noir en gris si votre taux de détection est faible. Si le fond est relativement clair, un code normal devrait fonctionner correctement.

### <a name="size-of-qr-codes"></a>Taille des codes QR
les appareils Windows Mixed Reality ne fonctionnent pas avec les codes QR avec des côtés inférieurs à 5 cm chacun.

Pour les codes QR entre les côtés de 5 cm et de 10 cm, vous devez être assez proche pour détecter le code. La détection des codes à cette taille prendra également plus de temps. 

La durée exacte de la détection des codes dépend non seulement de la taille des codes QR, mais aussi de la portée du code. Le déplacement plus proche du code aidera à décaler les problèmes de taille.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Distance et position angulaire à partir du code QR
Les caméras de suivi peuvent uniquement détecter un certain niveau de détail. Pour les petits codes < 10 cm sur les côtés, vous devez être assez proche. Pour un code QR de version 1 variant de 10 cm à 25 cm de large, la distance de détection minimale est comprise entre 0,15 mètres et 0,5 mètres. 

La distance de détection pour la taille augmente de façon linéaire, mais dépend également de la version QR ou de la taille du module. Plus la version est élevée, plus les modules sont petits, ce qui ne peut être détecté qu’à partir d’une position plus proche. Vous pouvez également essayer les codes Micro QR si vous souhaitez que la distance de détection soit plus longue. La détection QR fonctionne avec une plage d’angles + = 45 deg pour garantir une résolution correcte de la détection du code.

> [!IMPORTANT]
> Veillez à toujours avoir un contraste suffisant et une bordure appropriée.

### <a name="qr-codes-with-logos"></a>Codes QR avec logos
Les codes QR avec des logos n’ont pas été testés et ne sont actuellement pas pris en charge.

### <a name="managing-qr-code-data"></a>Gestion des données de code QR
Windows Mixed Reality appareils détectent les codes QR au niveau du système dans le pilote. Lorsque l’appareil est redémarré, les codes QR détectés ont disparu et sont redétectés en tant que nouveaux objets la prochaine fois.

Nous vous recommandons de configurer votre application pour qu’elle ignore les codes QR antérieurs à un horodateur spécifique. Actuellement, l’API ne prend pas en charge l’effacement de l’historique du code QR.

### <a name="qr-code-placement-in-a-space"></a>Positionnement du code QR dans un espace
Pour obtenir des recommandations sur l’emplacement et le positionnement des codes QR, reportez-vous à [considérations relatives à l’environnement pour HoloLens](/hololens/hololens-environment-considerations).

## <a name="qr-api-reference"></a>Informations de référence sur l’API QR

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>Voir aussi
* [Systèmes de coordonnées](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>