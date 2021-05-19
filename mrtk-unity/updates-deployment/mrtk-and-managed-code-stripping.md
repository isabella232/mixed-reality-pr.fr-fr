---
title: MRTK et suppression du code managé
description: Suppression de code dans MRTK et Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143734"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="0cf4f-104">Suppression du code managé MRTK et Unity</span><span class="sxs-lookup"><span data-stu-id="0cf4f-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="0cf4f-105">Lors de l’utilisation du backend de script IL2CPP d’Unity (facultatif dans Unity 2018,4, requis dans 2019 et versions ultérieures), l' [élimination du code managé](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) se produit.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="0cf4f-106">L’éditeur de liens Unity effectue ce processus afin de réduire la taille binaire et de réduire les temps de génération.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="0cf4f-107">La boîte à outils de réalité mixte utilise un fichier, `link.xml` , pour influencer la manière dont l’éditeur de liens d’Unity traite les ASSEMBLYS MRTK.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="0cf4f-108">Ce fichier, décrit dans la documentation complète de [Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), fournit à l’éditeur de liens des instructions sur la façon de conserver le code lorsque son utilisation ne peut pas être déduite (par exemple, utilisée par réflexion).</span><span class="sxs-lookup"><span data-stu-id="0cf4f-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="0cf4f-109">En tant que plateforme flexible et personnalisable, MRTK crée le `link.xml` fichier dans `Assets/MixedRealityToolkit.Generated` à l’importation, s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="0cf4f-110">Les fichiers de link.xml préexistants ne sont pas remplacés.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="0cf4f-111">Il est recommandé `link.xml` `link.xml.meta` d’ajouter le contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="0cf4f-112">Les développeurs doivent être libres de personnaliser `Assets/MixedRealityToolkit.Generated/link.xml` pour répondre aux besoins du projet.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="0cf4f-113">Par défaut, le fichier link.xml créé par MRTK conserve l’intégralité des assemblys présentés dans les données suivantes.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

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

<span data-ttu-id="0cf4f-114">Pour plus d’informations sur le format de fichier link.xml, reportez-vous à la documentation Unity.</span><span class="sxs-lookup"><span data-stu-id="0cf4f-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cf4f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cf4f-115">See also</span></span>

- [<span data-ttu-id="0cf4f-116">Unity : suppression du code managé</span><span class="sxs-lookup"><span data-stu-id="0cf4f-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="0cf4f-117">Unity : lier un fichier XML</span><span class="sxs-lookup"><span data-stu-id="0cf4f-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
