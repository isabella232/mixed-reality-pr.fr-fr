---
title: MRTK et suppression du code managé
description: Suppression de code dans MRTK et Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 8b8e0f4488a6e955e599084c0b59d8c80f553a78
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176292"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK et suppression du code managé

Lors de l’utilisation du backend de script IL2CPP d’Unity (facultatif dans Unity 2018,4, requis dans 2019 et versions ultérieures), l' [élimination du code managé](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) se produit.
L’éditeur de liens Unity effectue ce processus afin de réduire la taille binaire et de réduire les temps de génération.

la réalité mixte Shared Computer Toolkit utilise un fichier, `link.xml` , pour influencer la manière dont l’éditeur de liens d’unity traite les assemblys MRTK. Ce fichier, décrit dans la documentation complète de [Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), fournit à l’éditeur de liens des instructions sur la façon de conserver le code lorsque son utilisation ne peut pas être déduite (par exemple, utilisée par réflexion).

En tant que plateforme flexible et personnalisable, MRTK crée le `link.xml` fichier dans `Assets/MixedRealityToolkit.Generated` à l’importation, s’il n’existe pas. Les fichiers de link.xml préexistants ne sont pas remplacés. Il est recommandé `link.xml` `link.xml.meta` d’ajouter le contrôle de version. Les développeurs doivent être libres de personnaliser `Assets/MixedRealityToolkit.Generated/link.xml` pour répondre aux besoins du projet.

Par défaut, le fichier link.xml créé par MRTK conserve l’intégralité des assemblys présentés dans les données suivantes.

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

Pour plus d’informations sur le format de fichier link.xml, reportez-vous à la documentation Unity.

## <a name="see-also"></a>Voir aussi

- [Unity : suppression du code managé](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity : lier un fichier XML](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
