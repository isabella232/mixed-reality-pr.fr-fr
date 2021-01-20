---
title: Suivi des codes QR
description: Apprenez à détecter les codes QR, à ajouter des fonctionnalités de webcam et à gérer des systèmes de coordonnées dans des applications de réalité mixte sur HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, divertissement basé sur l’emplacement, VR arcade, arcade, immersif, QR, code QR, hololens2
ms.openlocfilehash: 08ed651deaab0c230142f45b93858f41ee300323
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583143"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="d0821-104">Suivi des codes QR</span><span class="sxs-lookup"><span data-stu-id="d0821-104">QR code tracking</span></span>

<span data-ttu-id="d0821-105">HoloLens 2 peut détecter les codes QR dans l’environnement situé autour du casque, ce qui permet d’établir un système de coordonnées à l’emplacement réel de chaque code.</span><span class="sxs-lookup"><span data-stu-id="d0821-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="d0821-106">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="d0821-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d0821-107">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="d0821-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d0821-108"><a href="/hololens/hololens1-hardware">HoloLens (première génération)</a></span><span class="sxs-lookup"><span data-stu-id="d0821-108"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d0821-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d0821-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d0821-110"><a href="../../discover/immersive-headset-hardware-details.md">Casques immersifs</a></span><span class="sxs-lookup"><span data-stu-id="d0821-110"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d0821-111">Détection du code QR</span><span class="sxs-lookup"><span data-stu-id="d0821-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="d0821-112">️</span><span class="sxs-lookup"><span data-stu-id="d0821-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d0821-113">✔️</span><span class="sxs-lookup"><span data-stu-id="d0821-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d0821-114">✔️</span><span class="sxs-lookup"><span data-stu-id="d0821-114">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="d0821-115">Le suivi du code QR avec des casques Windows Mixed Reality sur PC de bureau est pris en charge sur Windows 10 version 2004 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d0821-115">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="d0821-116">Utilisez l’API Microsoft. MixedReality. QRCodeWatcher. IsSupported () pour déterminer si la fonctionnalité est prise en charge sur l’appareil actuel.</span><span class="sxs-lookup"><span data-stu-id="d0821-116">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="d0821-117">Obtention du package QR</span><span class="sxs-lookup"><span data-stu-id="d0821-117">Getting the QR package</span></span>

<span data-ttu-id="d0821-118">Vous pouvez télécharger le package NuGet pour la détection du code QR [ici](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span><span class="sxs-lookup"><span data-stu-id="d0821-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="d0821-119">Détection des codes QR</span><span class="sxs-lookup"><span data-stu-id="d0821-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="d0821-120">Ajout de la fonctionnalité webcam</span><span class="sxs-lookup"><span data-stu-id="d0821-120">Adding the webcam capability</span></span>

<span data-ttu-id="d0821-121">Vous devez ajouter la fonctionnalité `webcam` à votre manifeste pour détecter les codes QR.</span><span class="sxs-lookup"><span data-stu-id="d0821-121">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="d0821-122">Cette fonctionnalité est requise, car les données dans les codes détectés dans l’environnement de l’utilisateur peuvent contenir des informations sensibles.</span><span class="sxs-lookup"><span data-stu-id="d0821-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="d0821-123">L’autorisation peut être demandée en appelant `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="d0821-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="d0821-124">_C#_</span><span class="sxs-lookup"><span data-stu-id="d0821-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="d0821-125">_C++_</span><span class="sxs-lookup"><span data-stu-id="d0821-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="d0821-126">Vous devez demander une autorisation avant de construire un objet QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="d0821-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="d0821-127">Si la détection du code QR requiert la `webcam` fonctionnalité, la détection se produit à l’aide des caméras de suivi de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="d0821-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="d0821-128">Cela fournit un angle de détection plus vaste et une plus grande autonomie de batterie par rapport à la détection avec l’appareil photo/vidéo (PV) de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="d0821-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="d0821-129">Détection des codes QR dans Unity</span><span class="sxs-lookup"><span data-stu-id="d0821-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="d0821-130">Vous pouvez utiliser l’API de détection du code QR dans Unity sans importer MRTK en installant le package NuGet à l’aide [de NuGet pour Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="d0821-130">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="d0821-131">Si vous souhaitez avoir une idée de son fonctionnement, téléchargez l’exemple d' [application Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span><span class="sxs-lookup"><span data-stu-id="d0821-131">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="d0821-132">L’exemple d’application contient des exemples d’affichage d’un carré holographique sur des codes QR et des données associées telles que le GUID, la taille physique, l’horodatage et les données décodées.</span><span class="sxs-lookup"><span data-stu-id="d0821-132">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="d0821-133">Détection des codes QR en C++</span><span class="sxs-lookup"><span data-stu-id="d0821-133">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="d0821-134">Obtention du système de coordonnées pour un code QR</span><span class="sxs-lookup"><span data-stu-id="d0821-134">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="d0821-135">Chaque code QR détecté expose un [système de coordonnées spatiales](../../design/coordinate-systems.md) aligné avec le code QR dans l’angle supérieur gauche du carré détection rapide dans le coin supérieur gauche :</span><span class="sxs-lookup"><span data-stu-id="d0821-135">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![Système de coordonnées du code QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="d0821-137">Lorsque vous utilisez directement le kit de développement logiciel (SDK) QR, l’axe Z pointe sur le papier (non affiché)-en cas de conversion en coordonnées Unity, l’axe Z pointe hors du papier et est droitier.</span><span class="sxs-lookup"><span data-stu-id="d0821-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="d0821-138">Le SpatialCoordinateSystem d’un code QR s’aligne comme indiqué.</span><span class="sxs-lookup"><span data-stu-id="d0821-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="d0821-139">Vous pouvez récupérer le système de coordonnées à partir de la plateforme en appelant <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview :: CreateCoordinateSystemForNode</a> et en passant le SpatialGraphNodeId du code.</span><span class="sxs-lookup"><span data-stu-id="d0821-139">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="d0821-140">Le code C++ ci-dessous montre comment créer un rectangle et le placer à l’aide du système de coordonnées du code QR :</span><span class="sxs-lookup"><span data-stu-id="d0821-140">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="d0821-141">Vous pouvez utiliser la taille physique pour créer le rectangle QR :</span><span class="sxs-lookup"><span data-stu-id="d0821-141">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="d0821-142">Le système de coordonnées peut être utilisé pour dessiner le code QR ou pour attacher des hologrammes à l’emplacement :</span><span class="sxs-lookup"><span data-stu-id="d0821-142">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="d0821-143">À l’instar de, votre *QRCodeAddedHandler* peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="d0821-143">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="d0821-144">Meilleures pratiques pour la détection du code QR</span><span class="sxs-lookup"><span data-stu-id="d0821-144">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="d0821-145">Zones calmes autour des codes QR</span><span class="sxs-lookup"><span data-stu-id="d0821-145">Quiet zones around QR Codes</span></span>

<span data-ttu-id="d0821-146">Pour être lu correctement, les codes QR nécessitent une marge autour de tous les côtés du code.</span><span class="sxs-lookup"><span data-stu-id="d0821-146">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="d0821-147">Cette marge ne doit pas contenir de contenu imprimé et doit être de quatre modules (un carré noir unique dans le code).</span><span class="sxs-lookup"><span data-stu-id="d0821-147">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="d0821-148">La [spécification QR](https://www.qrcode.com/en/howto/code.html) contient plus d’informations sur les zones silencieuses.</span><span class="sxs-lookup"><span data-stu-id="d0821-148">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="d0821-149">Éclairage et toile de fond</span><span class="sxs-lookup"><span data-stu-id="d0821-149">Lighting and backdrop</span></span>
<span data-ttu-id="d0821-150">La qualité de la détection du code QR est susceptible de varier l’éclairage et le fond.</span><span class="sxs-lookup"><span data-stu-id="d0821-150">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="d0821-151">Dans une scène avec un éclairage brillant, imprimez un code noir sur un arrière-plan gris.</span><span class="sxs-lookup"><span data-stu-id="d0821-151">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="d0821-152">Sinon, imprimez un code QR noir sur un arrière-plan blanc.</span><span class="sxs-lookup"><span data-stu-id="d0821-152">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="d0821-153">Si le fond du code est sombre, essayez un code noir en gris si votre taux de détection est faible.</span><span class="sxs-lookup"><span data-stu-id="d0821-153">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="d0821-154">Si le fond est relativement clair, un code normal devrait fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="d0821-154">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="d0821-155">Taille des codes QR</span><span class="sxs-lookup"><span data-stu-id="d0821-155">Size of QR codes</span></span>
<span data-ttu-id="d0821-156">Les appareils Windows Mixed Reality ne fonctionnent pas avec des codes QR avec des côtés inférieurs à 5 cm chacun.</span><span class="sxs-lookup"><span data-stu-id="d0821-156">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="d0821-157">Pour les codes QR entre les côtés de 5 cm et de 10 cm, vous devez être assez proche pour détecter le code.</span><span class="sxs-lookup"><span data-stu-id="d0821-157">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="d0821-158">La détection des codes à cette taille prendra également plus de temps.</span><span class="sxs-lookup"><span data-stu-id="d0821-158">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="d0821-159">La durée exacte de la détection des codes dépend non seulement de la taille des codes QR, mais aussi de la portée du code.</span><span class="sxs-lookup"><span data-stu-id="d0821-159">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="d0821-160">Le déplacement plus proche du code aidera à décaler les problèmes de taille.</span><span class="sxs-lookup"><span data-stu-id="d0821-160">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="d0821-161">Distance et position angulaire à partir du code QR</span><span class="sxs-lookup"><span data-stu-id="d0821-161">Distance and angular position from the QR code</span></span>
<span data-ttu-id="d0821-162">Les caméras de suivi peuvent uniquement détecter un certain niveau de détail.</span><span class="sxs-lookup"><span data-stu-id="d0821-162">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="d0821-163">Pour les petits codes < 10 cm sur les côtés, vous devez être assez proche.</span><span class="sxs-lookup"><span data-stu-id="d0821-163">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="d0821-164">Pour un code QR de version 1 variant de 10 cm à 25 cm de large, la distance de détection minimale est comprise entre 0,15 mètres et 0,5 mètres.</span><span class="sxs-lookup"><span data-stu-id="d0821-164">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="d0821-165">La distance de détection pour la taille augmente de façon linéaire.</span><span class="sxs-lookup"><span data-stu-id="d0821-165">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="d0821-166">La détection QR fonctionne avec une plage d’angles + = 45 deg pour garantir une résolution correcte de la détection du code.</span><span class="sxs-lookup"><span data-stu-id="d0821-166">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="d0821-167">Codes QR avec logos</span><span class="sxs-lookup"><span data-stu-id="d0821-167">QR codes with logos</span></span>
<span data-ttu-id="d0821-168">Les codes QR avec des logos n’ont pas été testés et ne sont actuellement pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d0821-168">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="d0821-169">Gestion des données de code QR</span><span class="sxs-lookup"><span data-stu-id="d0821-169">Managing QR code data</span></span>
<span data-ttu-id="d0821-170">Les appareils Windows Mixed Reality détectent les codes QR au niveau du système dans le pilote.</span><span class="sxs-lookup"><span data-stu-id="d0821-170">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="d0821-171">Lorsque l’appareil est redémarré, les codes QR détectés ont disparu et sont redétectés en tant que nouveaux objets la prochaine fois.</span><span class="sxs-lookup"><span data-stu-id="d0821-171">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="d0821-172">Nous vous recommandons de configurer votre application pour qu’elle ignore les codes QR antérieurs à un horodateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="d0821-172">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="d0821-173">Actuellement, l’API ne prend pas en charge l’effacement de l’historique du code QR.</span><span class="sxs-lookup"><span data-stu-id="d0821-173">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="d0821-174">Positionnement du code QR dans un espace</span><span class="sxs-lookup"><span data-stu-id="d0821-174">QR code placement in a space</span></span>
<span data-ttu-id="d0821-175">Pour obtenir des recommandations sur l’emplacement et le positionnement des codes QR, reportez-vous à [considérations relatives à l’environnement pour HoloLens](/hololens/hololens-environment-considerations).</span><span class="sxs-lookup"><span data-stu-id="d0821-175">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="d0821-176">Informations de référence sur l’API QR</span><span class="sxs-lookup"><span data-stu-id="d0821-176">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d0821-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0821-177">See also</span></span>
* [<span data-ttu-id="d0821-178">Systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="d0821-178">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="d0821-179"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="d0821-179"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>