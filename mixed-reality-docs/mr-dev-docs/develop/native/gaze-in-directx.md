---
title: Suivre de la tête et du regard dans DirectX
description: Apprenez à demander, à utiliser et à décompresser des données Raycasting à partir du suivi des yeux et du regard dans les applications DirectX natives.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: œil-point d’interposition, point de présence, suivi de la tête, suivi des yeux, DirectX, entrée, hologrammes, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 0e32c9f24b56d938b5c6f9cbdf28e9959b190abc22591a26d1dfcfa0af2f5f4d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193204"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Entrée en regard des points de regard et de pointage dans DirectX

> [!NOTE]
> Cet article s’applique aux API natives WinRT héritées.  Pour les nouveaux projets d’application native, nous vous recommandons d’utiliser l' **[API OpenXR](openxr-getting-started.md)**.

dans Windows Mixed Reality, l’entrée en regard de l’œil et de la tête est utilisée pour déterminer ce que l’utilisateur examine. Vous pouvez utiliser les données pour piloter des modèles d’entrée principaux tels que le [point d’interposition et la validation](../../design/gaze-and-commit.md), et fournir un contexte pour différents types d’interaction. Deux types de vecteurs de pointage sont disponibles par le biais de l’API : le point de regard et l’œil.  Les deux sont fournis sous la forme d’un rayon tridimensionnel avec une origine et une direction. Les applications peuvent ensuite raycast dans leurs scènes ou dans le monde réel, et déterminer ce que l’utilisateur cible.

**Tête-** point de regard représente la direction dans laquelle la tête de l’utilisateur est pointée. Pensez à la position et à la direction vers l’avant de l’appareil lui-même, la position étant le point central entre les deux affichages. La tête de regard est disponible sur tous les appareils de réalité mixte.

**Eye-point de regard** représente la direction vers laquelle les yeux de l’utilisateur cherchent. L’origine est située entre les yeux de l’utilisateur.  Elle est disponible sur les appareils de réalité mixte qui incluent un système de suivi oculaire.

Les rayons de tête et de regard sont accessibles par le biais de l’API  [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) . Appelez [SpatialPointerPose :: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) pour recevoir un nouvel objet SpatialPointerPose à l’horodatage et au [système de coordonnées](coordinate-systems-in-directx.md)spécifiés. Ce SpatialPointerPose contient une origine et une direction de pointage. Elle contient également un point d’origine et une direction de regard si le suivi oculaire est disponible.

### <a name="device-support"></a>Prise en charge des appareils

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Fonctionnalité</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
</tr>
<tr>
     <td>Suivi de la tête</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Œil-point de regard</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Utilisation de l’en-tête

Pour accéder au point de regard, commencez par appeler  [SpatialPointerPose :: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) pour recevoir un nouvel objet SpatialPointerPose. Transmettez les paramètres suivants.
 - [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) qui représente le système de coordonnées souhaité pour le point de regard. Elle est représentée par la variable *coordinateSystem* dans le code suivant. Pour plus d’informations, consultez notre guide de développement des [systèmes de coordonnées](coordinate-systems-in-directx.md) .
 - [Horodateur](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) qui représente l’heure exacte de la pose demandée.  En général, vous utilisez un horodatage qui correspond à l’heure à laquelle le frame actuel sera affiché. Vous pouvez obtenir cet horodateur d’affichage prédit à partir d’un objet  [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , qui est accessible via le [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)actuel.  Cet objet HolographicFramePrediction est représenté par la variable de *prédiction* dans le code suivant.

 Une fois que vous avez un SpatialPointerPose valide, la position de la tête et la direction vers l’avant sont accessibles en tant que propriétés.  Le code suivant montre comment y accéder.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Utilisation des yeux

Pour que vos utilisateurs utilisent une entrée en regard de l’œil, chaque utilisateur doit passer par un étalonnage de l' [utilisateur de suivi oculaire](/hololens/hololens-calibration) la première fois qu’il utilise l’appareil. L’API Eye-regard est semblable à la tête de regard.
Elle utilise la même API [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , qui fournit une origine de rayon et une direction que vous pouvez raycast par rapport à votre scène.  La seule différence est que vous devez activer explicitement le suivi visuel avant de l’utiliser :
1. Demandez à l’utilisateur l’autorisation d’utiliser le suivi oculaire dans votre application.
2. Activez la fonctionnalité « entrée de regard » dans le manifeste de votre package.

### <a name="requesting-access-to-eye-gaze-input"></a>Demande d’accès à une entrée en regard des yeux

Lorsque votre application démarre, appelez [EyesPose :: RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) pour demander l’accès au suivi oculaire. Le système demande à l’utilisateur si nécessaire et retourne [GazeInputAccessStatus :: allowed](/uwp/api/windows.ui.input.gazeinputaccessstatus) une fois que l’accès a été accordé. Il s’agit d’un appel asynchrone, ce qui nécessite un peu de gestion supplémentaire. L’exemple suivant montre comment effectuer une opération de détachement d’un thread std :: thread pour attendre le résultat, qu’il stocke dans une variable membre appelée *m_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
Le démarrage d’un thread détaché n’est qu’une option pour gérer les appels asynchrones. Vous pouvez également utiliser les nouvelles fonctionnalités de [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) prises en charge par C++/WinRT.
Voici un autre exemple de demande d’autorisation de l’utilisateur :
-   EyesPose :: IsSupported () permet à l’application de déclencher la boîte de dialogue d’autorisation uniquement s’il existe un dispositif de suivi oculaire.
-   GazeInputAccessStatus m_gazeInputAccessStatus ; Cela permet d’éviter de relancer l’invite d’autorisation.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>Déclaration de la capacité *d’entrée en regard*

Double-cliquez sur le fichier appxmanifest dans *Explorateur de solutions*.  Accédez ensuite à la section *fonctionnalités* et vérifiez la capacité *d’entrée de regard* . 

![Capacité d’entrée en regard](images/gaze-input-capability.png)

Cela ajoute les lignes suivantes à la section *package* dans le fichier appxmanifest :
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Obtenir le regard de l’œil

Une fois que vous avez reçu l’accès à ET, vous êtes libre de prendre le regard de chaque image.
Comme avec le point de regard, récupérez [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) en appelant [SpatialPointerPose :: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) avec un horodatage et un système de coordonnées souhaités. SpatialPointerPose contient un objet [EyesPose](/uwp/api/windows.perception.people.eyespose) via la propriété [Eyes](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) . Ce n’est pas NULL uniquement si le suivi oculaire est activé. À partir de là, vous pouvez vérifier si l’utilisateur de l’appareil a un étalonnage de suivi oculaire en appelant [EyesPose :: IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Ensuite, utilisez la [propriété de](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) pointage pour récupérer le [SpatialRay](/uwp/api/windows.perception.spatial.spatialray) contenant la position et la direction de l’oeil. La propriété de pointage peut parfois avoir la valeur null. Assurez-vous de le vérifier. Cela peut se produire si un utilisateur calibré ferme temporairement ses yeux.

L’exemple de code suivant montre comment accéder à l’œil-regard.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>Secours lorsque le suivi oculaire n’est pas disponible

Comme mentionné dans nos [documents sur la conception des suivis oculaires](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), les concepteurs et les développeurs doivent connaître les instances où les données de suivi oculaire peuvent ne pas être disponibles.

Il existe plusieurs raisons pour lesquelles les données ne sont pas disponibles :
* Un utilisateur n’est pas étalonné
* Un utilisateur a refusé l’accès de l’application à ses données de suivi oculaire
* les interférences temporaires, telles que les traînées sur le visière de HoloLens ou les cheveux, en obturant les yeux de l’utilisateur. 

Alors que certaines API ont déjà été mentionnées dans ce document, nous fournissons un résumé de la façon de détecter que le suivi oculaire est disponible en tant que référence rapide : 

* Vérifiez que le système prend en charge le suivi visuel. appelez la *méthode* suivante : [Windows. Perception. People. EyesPose. IsSupported ()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Vérifiez que l’utilisateur est étalonné. appelez la *propriété* suivante : [Windows. Perception. People. EyesPose. IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* Vérifiez que l’utilisateur a donné à votre application l’autorisation d’utiliser ses données de suivi oculaire : récupérez le _« GazeInputAccessStatus »_ actuel. Vous trouverez un exemple de la procédure à suivre pour [demander l’accès aux entrées de regard](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input). 

Vous pouvez également vérifier que vos données de suivi oculaire ne sont pas obsolètes en ajoutant un délai d’expiration entre les mises à jour reçues des données de suivi oculaire et en conversant le point de vue de la tête, comme indiqué ci-dessous.   
Pour plus d’informations, consultez les [considérations relatives](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) à la conception de secours.

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Corrélation du regard avec d’autres entrées

Il peut arriver que vous ayez besoin d’un [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) qui correspond à un événement dans le passé. Par exemple, si l’utilisateur fait un robinet d’air, votre application peut souhaiter savoir ce qu’elle recherchait. À cet effet, l’utilisation simple de [SpatialPointerPose :: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) avec le temps de trame prédit serait inexacte en raison de la latence entre le traitement d’entrée du système et la durée d’affichage. En outre, si vous utilisez des yeux pour le ciblage, nos yeux ont tendance à se déplacer même avant de terminer une action de validation. Il s’agit d’un problème moins grave pour une pression aérienne simple, mais il devient plus critique lors de la combinaison de longues commandes vocales avec des mouvements d’œil rapides. L’une des façons de gérer ce scénario consiste à effectuer un appel supplémentaire à  [SpatialPointerPose :: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), à l’aide d’un horodateur historique qui correspond à l’événement d’entrée.  

Toutefois, pour les entrées qui acheminent le SpatialInteractionManager, il existe une méthode plus simple. [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) a sa propre fonction [TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) . L’appel de qui fournira un [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) parfaitement corrélé sans les deviner. Pour plus d’informations sur l’utilisation de SpatialInteractionSourceStates, jetez un coup d’œil aux [contrôleurs mains et motion dans](hands-and-motion-controllers-in-directx.md) la documentation DirectX.

<br>

## <a name="calibration"></a>Étalonnage

Pour que le suivi des yeux fonctionne correctement, chaque utilisateur doit passer par un étalonnage de l' [utilisateur de suivi oculaire](/hololens/hololens-calibration). Cela permet à l’appareil d’ajuster le système pour une expérience d’affichage plus confortable et de meilleure qualité pour l’utilisateur et pour garantir un suivi visuel précis en même temps. Les développeurs n’ont rien à faire à leur bout pour gérer l’étalonnage de l’utilisateur. Le système s’assure que l’utilisateur est invité à étalonner l’appareil dans les circonstances suivantes :
* L'utilisateur se sert de l'appareil pour la première fois.
* L'utilisateur a précédemment refusé le processus d'étalonnage.
* Le processus d'étalonnage n'a pas abouti la dernière fois que l'utilisateur s'est servi de l'appareil.

Les développeurs doivent veiller à fournir une prise en charge adéquate pour les utilisateurs où les données de suivi oculaire peuvent ne pas être disponibles. En savoir plus sur les considérations relatives aux solutions de secours au [suivi oculaire sur HoloLens 2](../../design/eye-tracking.md).

<br>

## <a name="see-also"></a>Voir aussi

* [Étalonnage](/hololens/hololens-calibration)
* [Systèmes de coordonnées dans DirectX](coordinate-systems-in-directx.md)
* [Œil-regard HoloLens 2](../../design/eye-tracking.md)
* [Modèle d’entrée de regard et de validation](../../design/gaze-and-commit.md)
* [Mains et contrôleurs de mouvement dans DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrée vocale dans DirectX](voice-input-in-directx.md)