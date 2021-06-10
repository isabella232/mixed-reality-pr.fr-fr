---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748503"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Utilisez la classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) à partir de MRTK pour Unity et définissez l' **échelle cible** sur **assis**:

![Fenêtre Paramètres MRTK](../../images/mrtk-target-scale.png)

MRTK doit gérer automatiquement la position du PlaySpace et de l’appareil photo, mais il est préférable de vérifier :

![MRTK playspace](../../images/mrtk-playspace.png)

1. Dans le volet **hiérarchie** , développez le gameobject **MixedRealityPlayspace** et recherchez l’objet enfant de l' **appareil photo principal** .
2. Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Définissez le mode d’origine du suivi sur [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Après avoir obtenu le sous-système, appelez [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

Et fonctionnent avec [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)d’Unity.

![XR de la plate-forme dans la hiérarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Accéder à d' **autres paramètres** de la section paramètres du **lecteur Windows Store**
2. Choisissez **Windows Mixed realisation** comme périphérique, qui peut être listé comme **Windows holographique** dans les versions antérieures d’Unity
3. Sélectionner une **réalité virtuelle prise en charge**

Étant donné que l’objet Camera principal est automatiquement marqué comme caméra, Unity alimente tous les mouvements et les translations.

>[!NOTE]
>Ces paramètres doivent être appliqués à l’appareil photo dans chaque scène de votre application.
>
>Par défaut, lorsque vous créez une nouvelle scène dans Unity, elle contient un GameObject d’appareil photo principal dans la hiérarchie qui comprend le composant Camera, mais les paramètres ci-dessous ne sont pas correctement appliqués.

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *XRDevice*

Pour créer une expérience d' **orientation uniquement** ou de mise à l' **échelle assise**, vous devez définir Unity sur le type d’espace de suivi fixe. Espace de suivi fixe définit le système de coordonnées universelles de l’unité pour suivre le [cadre stationnaire de référence](../../../../design/coordinate-systems.md#spatial-coordinate-systems). Dans le mode de suivi fixe, le contenu placé dans l’éditeur juste devant l’emplacement par défaut de l’appareil photo (Forward is-Z) s’affiche devant l’utilisateur au lancement de l’application.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *InputTracking*

Pour une expérience purement en **orientation uniquement** telle qu’une visionneuse vidéo de 360 degrés (où les mises à jour de la tête de position dépasseraient l’illusion), vous pouvez définir [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) sur true :

```cs
InputTracking.disablePositionalTracking = true;
```

Pour une expérience de mise à l' **échelle assiste**, pour permettre à l’utilisateur de recentrer plus tard l’origine assise, vous pouvez appeler [XR. Méthode InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

Si vous créez une [expérience à l’échelle assise](../../../../design/coordinate-systems.md), vous pouvez recentrer l’origine du monde de l’unité à la position de la tête actuelle de l’utilisateur en appelant **[XR. Méthode InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .