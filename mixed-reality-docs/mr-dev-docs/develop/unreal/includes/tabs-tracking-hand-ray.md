---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187423"
---
# <a name="426"></a>[4.26](#tab/426)

Pour obtenir les données des rayons de la main, vous devez utiliser la fonction de données obtenir le contrôleur de mouvement de la section précédente. La structure retournée contient deux paramètres que vous pouvez utiliser pour créer un rayon **et une** **rotation AIM**. Ces paramètres forment un rayon dirigé par votre coude. Vous devez les prendre et trouver un hologramme pointé par.

Voici un exemple qui montre comment déterminer si un rayon de main atteint un widget et comment définir un résultat d’accès personnalisé :

![Plan de la fonction de données de l’extraction de contrôle de mouvement](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

pour utiliser des rayons de main dans des plans, recherchez l’une des actions sous **Windows Mixed Reality HMD**:

![Rayons main BP](../images/unreal/hand-rays-bp.png)

Pour y accéder en C++, incluez- `WindowsMixedRealityFunctionLibrary.h` le au début de votre fichier de code appelant.

### <a name="enum"></a>Enum

Vous avez également accès aux cas d’entrée sous **EHMDInputControllerButtons**, qui peuvent être utilisés dans les projets :

![Boutons du contrôleur d’entrée](../images/unreal/input-controller-buttons.png)

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
    * déclenché dans HoloLens 2 par pression aérienne, pointage en regard et validation, ou en disant « sélectionner » avec [entrée vocale](../unreal-voice-input.md) activée.
* Événement **de préhension déclenché** par l’utilisateur.
    * déclenché dans HoloLens 2 en fermant les doigts de l’utilisateur sur un hologramme.

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

Vous pouvez accéder au struct PointerPoseInfo par le biais de plans, comme indiqué ci-dessous :

![Informations de pose du pointeur BP](../images/unreal/pointer-pose-info-bp.png)

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

![Obtient les informations de pose du pointeur](../images/unreal/get-pointer-pose-info.png)

C++ :
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Est saisi** retourne la valeur true si la main est prélevée dans le frame actuel.

Blueprint

![Est saisi BP](../images/unreal/is-grasped-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Select enfoncée** retourne la valeur true si l’utilisateur a déclenché SELECT dans le frame actuel.

Blueprint

![Est sélectionner un fond de panier appuyé](../images/unreal/is-select-pressed-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. L' **utilisateur clique sur un bouton** retourne la valeur true si l’événement ou le bouton est déclenché dans le frame actuel.

Blueprint

![Clic sur le bouton de la BP](../images/unreal/is-button-clicked-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. L' **État du suivi des contrôleurs** retourne l’état de suivi dans le frame actuel.

Blueprint

![Obtient l’état du suivi du contrôleur BP](../images/unreal/get-controller-tracking-status-bp.png)

C++ :
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```