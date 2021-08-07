---
ms.openlocfilehash: 47dfba0fe2b64e3b7e03ae62af3de1e1e24bd70b8b1e7e6b2cb40995428dbda2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212319"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Utilisez la classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) à partir de MRTK pour Unity et définissez l' **échelle cible** sur **Room** ou **debout**:

![Fenêtre Paramètres MRTK](../../images/mrtk-target-scale.png)

MRTK doit gérer automatiquement la position du PlaySpace et de l’appareil photo, mais il est préférable de vérifier :

![MRTK playspace](../../images/mrtk-playspace.png)

1. Dans le volet **hiérarchie** , développez le gameobject **MixedRealityPlayspace** et recherchez l’objet enfant de l' **appareil photo principal** .
2. Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Définissez le mode d’origine du suivi sur [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Après avoir obtenu le sous-système, appelez [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

Et fonctionnent avec [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)d’Unity.

![XR de la plate-forme dans la hiérarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. accédez à la section **autres Paramètres** du **lecteur Windows Store Paramètres**
2. choisissez **Windows Mixed Reality** comme appareil, qui peut être listé comme **Windows holographique** dans les versions antérieures d’unity
3. Sélectionner une **réalité virtuelle prise en charge**

Étant donné que l’objet Camera principal est automatiquement marqué comme caméra, Unity alimente tous les mouvements et les translations.

>[!NOTE]
>Ces paramètres doivent être appliqués à l’appareil photo dans chaque scène de votre application.
>
>Par défaut, lorsque vous créez une nouvelle scène dans Unity, elle contient un GameObject d’appareil photo principal dans la hiérarchie qui comprend le composant Camera, mais les paramètres ci-dessous ne sont pas correctement appliqués.

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *XRDevice*

Pour une expérience à l’échelle **permanente** ou à l’échelle de l' **espace**, vous devez placer du contenu par rapport à l’étage. Vous avez raison de l’étage de l’utilisateur à l’aide de la **[Phase spatiale](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, qui représente l’origine de l’utilisateur et la limite facultative de l’espace, configurées lors de la première exécution.

Pour vous assurer que Unity fonctionne avec son système de coordonnées universel à l’étage, vous pouvez définir et tester qu’Unity utilise le type d’espace de suivi RoomScale :

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* Si SetTrackingSpaceType retourne la valeur true, Unity a correctement basculé son système de coordonnées universel pour suivre le [cadre de la phase de référence](../../../../design/coordinate-systems.md#spatial-coordinate-systems).
* Si SetTrackingSpaceType retourne la valeur false, Unity n’a pas pu basculer vers le cadre de la phase de référence, probablement parce que l’utilisateur n’a pas configuré d’étage dans son environnement. Bien qu’une valeur de retour false ne soit pas courante, elle peut se produire si l’étape est configurée dans une salle différente et que l’appareil est déplacé dans la salle actuelle sans que l’utilisateur ne configure une nouvelle étape.

Une fois que votre application a correctement défini le type d’espace de suivi RoomScale, le contenu placé sur le plan y = 0 s’affiche sur le plancher. L’origine à 0, 0 correspond à l’emplacement spécifique sur le plancher où l’utilisateur a pris la main pendant la configuration de la salle, avec-Z représentant la direction vers l’avant pendant la configuration.