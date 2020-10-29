---
title: Suivi de la main dans Unreal
description: Explique comment utiliser le suivi des handles en mode inréel
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, suivi manuel, non réel, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, développement de jeux
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91678961"
---
# <a name="hand-tracking-in-unreal"></a>Suivi de la main dans Unreal

## <a name="overview"></a>Vue d’ensemble

Le système de suivi de la main utilise les paumes et les doigts d’une personne comme entrée. Vous pouvez connaître la position et la rotation de chaque doigt, de la totalité de la paume et même des gestes à utiliser dans votre code. 

## <a name="hand-pose"></a>Poser à la main

La pose de main vous permet d’effectuer le suivi des mains et des doigts de l’utilisateur actif et de l’utiliser comme entrée, auquel vous pouvez accéder via des plans et du C++. Vous trouverez plus de détails techniques dans l’API [Windows. perception. People. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) . L’API inréelle envoie les données sous forme de système de coordonnées, avec les battements synchronisés avec le moteur inréel.

### <a name="understanding-the-bone-hierarchy"></a>Fonctionnement de la hiérarchie osseuse

L' `EWMRHandKeypoint` énumération décrit la hiérarchie osseuse de la main. Chaque KEYpoint est indiqué dans vos projets :

![Main KEYpoint BP](images/hand-keypoint-bp.png)

L’énumération C++ complète est listée ci-dessous :
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

Vous pouvez rechercher les valeurs numériques de chaque cas d’énumération dans la table [Windows. perception. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) . La disposition complète avec les cas d’énumération correspondants est illustrée dans l’image ci-dessous :

![Squelette de main](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>Prise en charge du suivi des mains

Vous pouvez utiliser le suivi des mains dans les plans **en ajoutant le suivi de** la main à partir de la **> Windows Mixed Reality** :

![Suivi de main BP](images/unreal/hand-tracking-bp.png)

Cette fonction retourne `true` si le suivi manuel est pris en charge sur l’appareil et `false` si le suivi manuel n’est pas disponible.

![Prend en charge le BP de suivi de main](images/unreal/supports-hand-tracking-bp.png)

C++ : 

Incluez `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obtenir le suivi de la main
Vous pouvez utiliser **GetHandJointTransform** pour retourner des données spatiales à partir de la main. Les données sont mises à jour chaque trame, mais si vous vous trouvez à l’intérieur d’un frame, les valeurs retournées sont mises en cache. Il n’est pas recommandé d’avoir une logique importante dans cette fonction pour des raisons de performances. 

![Faire une transformation conjointe de la main](images/unreal/get-hand-joint-transform.png)
 
C++ :
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Répartition des paramètres de fonction :

* **Main** : la partie gauche ou la droite de l’utilisateur
* **KEYpoint** : le segment de la main. 
* **Transform** : coordonnées et orientation de la base du segment. Vous pouvez demander la base du segment suivant pour obtenir les données de transformation pour la fin d’un segment. Un segment de pourboire spécial offre une terminaison de distribution. 
* **Rayon** : rayon de la base du segment.
* **Valeur de retour** : true si le segment est suivi dans ce frame, false si le segment n’est pas suivi.

## <a name="hand-live-link-animation"></a>Animation de lien dynamique à la main
Les poses de main sont exposées à l’animation à l’aide du [plug-in Live Link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Si les plug-ins Windows Mixed Reality et Live Link sont activés : 
1. Sélectionnez **fenêtre > lien dynamique** pour ouvrir la fenêtre de l’éditeur de liens actifs. 
2. Cliquer sur **source** et activer la source de suivi de la **main Windows Mixed Reality**

![Source de la liaison dynamique](images/unreal/live-link-source.png)
 
Une fois que vous avez activé la source et ouvert un élément multimédia d’animation, développez la section **animation** dans l’onglet Aperçu de la **scène** . vous voyez également d’autres options (les détails sont dans la documentation sur les liens dynamiques inactifs, car le plug-in est en version bêta, le processus peut changer plus tard).

![Animation des liens dynamiques](images/unreal/live-link-animation.png)
 
La hiérarchie d’animation manuelle est la même que dans `EWMRHandKeypoint` . L’animation peut être reciblée à l’aide de **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :

![Animation de lien dynamique 2](images/unreal/live-link-animation2.png)
 
Elle peut également être sous-classée dans l’éditeur :

![Remappage de liaison dynamique](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>Accès aux données de maillage de la main

![Maille manuelle](images/unreal/hand-mesh.png)

Avant de pouvoir accéder aux données de maillage manuel, vous devez :
- Sélectionnez votre ressource **ARSessionConfig** , développez les **paramètres AR-> World Mapping** Settings, puis cochez la case **générer des données de maillage à partir de la géométrie suivie** . 

Voici les paramètres de maillage par défaut :

1.  Utiliser les données de maillage pour l’occlusion
2.  Générer une collision pour les données de maillage
3.  Générer un maillage de navigation pour les données de maillage
4.  Rendu des données de maillage dans le paramètre filaire – débogage qui affiche le maillage généré

Ces valeurs de paramètre sont utilisées comme maillage de mappage spatial et par défaut. Vous pouvez les modifier à tout moment dans des plans ou du code pour n’importe quelle maille.

### <a name="c-api-reference"></a>Informations de référence sur l’API C++ 
Utilisez `EEARObjectClassification` pour rechercher des valeurs de maillage de main dans tous les objets suivis.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

Les délégués suivants sont appelés lorsque le système détecte tout objet suivi, y compris un maillage de main. 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Assurez-vous que vos gestionnaires de délégués suivent la signature de la fonction ci-dessous :

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Vous pouvez accéder aux données de maillage par le biais des  `UARTrackedGeometry::GetUnderlyingMesh` éléments suivants :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>Informations de référence sur l’API Blueprint

Pour travailler avec les maillages de main dans les plans :
1. Ajouter un composant **ARTrackableNotify** à un acteur Blueprint

![Notification ARTrackable](images/unreal/ar-trackable-notify.png)
 
2. Accédez au panneau des **Détails** et développez la section **événements** . 

![ARTrackable Notify 2](images/unreal/ar-trackable-notify2.png)
 
3. Remplacer sur l’ajout/la mise à jour/suppression de la géométrie suivie avec les nœuds suivants dans votre graphique d’événements :

![Sur ARTrackable Notify](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Rayons de main

Vous pouvez utiliser un Ray comme dispositif de pointage à la fois dans le C++ et dans les plans, ce qui expose l’API [Windows. UI. Input. spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .

Il est important de mentionner que, étant donné que les résultats de toutes les fonctions changent chaque image, elles sont toutes rendues accessibles. Pour plus d’informations sur les fonctions pures et impures ou pouvant être appelées, consultez Guide de l’utilisateur Blueprint sur les [fonctions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

Pour utiliser des rayons de main dans des plans, recherchez l’une des actions sous **Windows Mixed Reality HMD** :

![Rayons main BP](images/unreal/hand-rays-bp.png)
 
Pour y accéder en C++, incluez- `WindowsMixedRealityFunctionLibrary.h` le au début de votre fichier de code appelant.

### <a name="enum"></a>Énumération
Vous avez également accès aux cas d’entrée sous **EHMDInputControllerButtons** , qui peuvent être utilisés dans les projets :

![Boutons du contrôleur d’entrée](images/unreal/input-controller-buttons.png)

Pour accéder en C++, utilisez la `EHMDInputControllerButtons` classe enum :
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Voici une répartition des deux cas d’énumération applicables :
* **Select** -User a déclenché l’événement Select. 
    * L’événement peut être déclenché dans HoloLens 2 par pression aérienne, pointage en regard et validation, ou en disant « sélectionner » avec l' [entrée vocale](unreal-voice-input.md) activée. 
* Événement **de préhension déclenché** par l’utilisateur. 
    * Cet événement peut être déclenché dans HoloLens 2 en fermant les doigts de l’utilisateur sur un hologramme. 

Vous pouvez accéder à l’état de suivi de votre maille de main en C++ via l' `EHMDTrackingStatus` énumération illustrée ci-dessous :

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Voici une répartition des deux cas d’énumération applicables :
* **NotTracked** – la main n’est pas visible
* **Suivi** : la main est entièrement suivie

### <a name="struct"></a>Structure
Le struct PointerPoseInfo peut vous donner des informations sur les données suivantes :
* **Origin** : origine de la main
* **Direction** : direction de la main
* **Haut** -vecteur de la main
* **Orientation** -Quaternion d’orientation 
* **État du suivi** – État du suivi actuel

Vous pouvez y accéder par le biais de plans, comme indiqué ci-dessous :

![Informations de pose du pointeur BP](images/unreal/pointer-pose-info-bp.png)

Ou avec C++ :

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Fonctions

Toutes les fonctions listées ci-dessous peuvent être appelées sur chaque trame, ce qui permet une surveillance continue. 

1. Obtenir les informations sur les **poses du pointeur** retourne des informations complètes sur la direction du rayon de la main dans le frame actuel. 

Blueprint

![Obtient les informations de pose du pointeur](images/unreal/get-pointer-pose-info.png)

C++ : 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Est saisi** retourne la valeur true si la main est prélevée dans le frame actuel.

Blueprint

![Est saisi BP](images/unreal/is-grasped-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. **Select enfoncée** retourne la valeur true si l’utilisateur a déclenché SELECT dans le frame actuel.

Blueprint

![Est sélectionner un fond de panier appuyé](images/unreal/is-select-pressed-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. L' **utilisateur clique sur un bouton** retourne la valeur true si l’événement ou le bouton est déclenché dans le frame actuel.

Blueprint

![Clic sur le bouton de la BP](images/unreal/is-button-clicked-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. L' **État du suivi des contrôleurs** retourne l’état de suivi dans le frame actuel.

Blueprint

![Obtient l’état du suivi du contrôleur BP](images/unreal/get-controller-tracking-status-bp.png)

C++ :
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>Mouvements

Hololens 2 peut suivre les gestes spatiaux, ce qui signifie que vous pouvez capturer ces mouvements comme entrée. Vous trouverez plus d’informations sur les gestes dans le document sur l' [utilisation de base de HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

Vous pouvez trouver la fonction Blueprint dans sous **Windows Mixed Real Input spatial** , et la fonction C++ en ajoutant `WindowsMixedRealitySpatialInputFunctionLibrary.h` dans votre fichier de code appelant.

![Capturer les gestes](images/unreal/capture-gestures.png)

### <a name="enum"></a>Énumération
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Blueprint 

![Type de mouvement](images/unreal/gesture-type.png)

C++ :
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Fonction
Vous pouvez activer et désactiver la capture de mouvement avec la `CaptureGestures` fonction. Lorsqu’un mouvement activé déclenche des événements d’entrée, la fonction retourne `true` si la capture de mouvement a réussi, et en `false` cas d’erreur.

Blueprint

![Capturer les gestes BP](images/unreal/capture-gestures-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

Voici quelques-uns des principaux événements que vous pouvez trouver dans les plans et C++ : ![ événements clés](images/unreal/key-events.png)

![Événements clés 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours du point de contrôle de développement inréel que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction MRTK Core. À partir de là, vous pouvez passer au bloc de construction suivant : 

> [!div class="nextstepaction"]
> [Ancres spatiales locales](unreal-spatial-anchors.md)

Ou accédez aux API et fonctionnalités de la plateforme de réalité mixte :

> [!div class="nextstepaction"]
> [Caméra HoloLens](unreal-hololens-camera.md)

Vous pouvez toujours revenir aux [points de contrôle de développement inréels](unreal-development-overview.md#2-core-building-blocks) à tout moment.