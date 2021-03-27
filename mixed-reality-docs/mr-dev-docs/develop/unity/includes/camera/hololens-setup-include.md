---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636286"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Suivez ce [didacticiel pas à pas](../../tutorials/mr-learning-base-01.md) pour ajouter et configurer automatiquement la boîte à outils de réalité mixte dans votre projet Unity. Il est également possible de travailler directement avec la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) à partir de MRTK pour Unity et de définir la mise à l' **échelle cible** sur le **monde**:

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Vous pouvez utiliser [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) pour les applications HoloLens, ce qui fonctionne mieux avec les ancres et ARKit/ARCore.

![Session AR dans la hiérarchie](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> La session AR et les fonctionnalités associées nécessitent l’installation de la Fondation de base.

Il est également possible d’appliquer les modifications de la caméra manuellement sans utiliser ARSession :

1. Sélectionner la **caméra principale** dans le volet de la **hiérarchie**
1. Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**

   ![Caméra dans le volet de l’inspecteur dans Unity](../../images/maincamera-350px.png)  
   *Caméra dans le volet de l’inspecteur dans Unity*

1. Ajouter un **TrackedPoseDriver** à l' **appareil photo principal**

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Sélectionner la **caméra principale** dans le volet de la **hiérarchie**
1. Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**

   ![Caméra dans le volet de l’inspecteur dans Unity](../../images/maincamera-350px.png)  
   *Caméra dans le volet de l’inspecteur dans Unity*

1. Accéder à d' **autres paramètres** de la section paramètres du **lecteur Windows Store**
1. Choisissez **Windows Mixed realisation** comme périphérique, qui peut être listé comme **Windows holographique** dans les versions antérieures d’Unity
1. Sélectionner une **réalité virtuelle prise en charge**

Étant donné que l’objet Camera principal est automatiquement marqué comme caméra, Unity alimente tous les mouvements et les translations.

>[!NOTE]
>Ces paramètres doivent être appliqués à l’appareil photo dans chaque scène de votre application.
>
>Par défaut, lorsque vous créez une nouvelle scène dans Unity, elle contient un GameObject d’appareil photo principal dans la hiérarchie qui comprend le composant d’appareil photo, mais peut ne pas avoir les paramètres correctement appliqués.