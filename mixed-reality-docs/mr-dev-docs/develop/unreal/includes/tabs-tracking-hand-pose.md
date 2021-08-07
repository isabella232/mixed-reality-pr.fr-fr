---
ms.openlocfilehash: ec1246085989b4b157504e9b8551694d6116e6f08789fa669200e5425ef75cc6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187416"
---
# <a name="426"></a>[4.26](#tab/426)

La hiérarchie est décrite par `EHandKeypoint` enum :

![Image des options bluprint de KEYpoint de la main](../images/hand-keypoint-bp.png)

Vous pouvez obtenir toutes ces données à partir de la main d’un utilisateur à l’aide de la fonction de **données obtenir le contrôleur de mouvement** . Cette fonction retourne une structure **XRMotionControllerData** . Vous trouverez ci-dessous un exemple de script Blueprint qui analyse la structure XRMotionControllerData pour obtenir les emplacements joints et dessine un système de coordonnées de débogage à chaque emplacement de la jointure.

![Plan de la fonction d’extraction de données de regard connectée à la trace de ligne par fonction de canal](../images/unreal-hand-tracking-img-03.png)

Il est important de vérifier si la structure est valide et qu’elle est une main. Dans le cas contraire, vous risquez d’avoir un comportement indéfini dans l’accès aux positions, aux rotations et aux rayons.

# <a name="425"></a>[4.25](#tab/425)

L' `EWMRHandKeypoint` énumération décrit la hiérarchie osseuse de la main. Chaque KEYpoint est indiqué dans vos projets :

![Main KEYpoint BP](../images/hand-keypoint-bp.png)

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

Vous pouvez rechercher les valeurs numériques de chaque cas d’énumération dans la [Windows. Table perception. People. HandJointKind](/uwp/api/windows.perception.people.handjointkind) .

### <a name="supporting-hand-tracking"></a>Prise en charge du suivi des mains

Vous pouvez utiliser le suivi des mains dans les plans **en ajoutant le suivi des handles** à partir de la **> Windows Mixed Reality**:

![Suivi de main BP](../images/unreal/hand-tracking-bp.png)

Cette fonction retourne `true` si le suivi manuel est pris en charge sur l’appareil et `false` si le suivi manuel n’est pas disponible.

![Prend en charge le BP de suivi de main](../images/unreal/supports-hand-tracking-bp.png)

C++ :

Incluez `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obtenir le suivi de la main

Vous pouvez utiliser **GetHandJointTransform** pour retourner des données spatiales à partir de la main. Les données sont mises à jour chaque trame, mais si vous vous trouvez à l’intérieur d’un frame, les valeurs retournées sont mises en cache. Il n’est pas recommandé d’avoir une logique importante dans cette fonction pour des raisons de performances.

![Faire une transformation conjointe de la main](../images/unreal/get-hand-joint-transform.png)

C++ :
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Voici une répartition des paramètres de fonction de GetHandJointTransform :

* **Main** : peut être l’utilisateur à gauche ou à droite.
* **KEYpoint** : le segment de la main.
* **Transform** : coordonnées et orientation de la base du segment. Vous pouvez demander la base du segment suivant pour obtenir les données de transformation pour la fin d’un segment. Un segment de pourboire spécial offre une terminaison de distribution.
* * * Rayon : rayon de la base du segment.
* * * Valeur de retour : true si le segment est suivi dans ce frame, false si le segment n’est pas suivi.