---
title: Point de focus dans Unity
description: Réglage manuel de la stabilité des hologrammes dans Unity en définissant le point de focus
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, point de focalisation, plan de focalisation, plan de stabilisation, point de stabilisation, reprojection, LSR, mémoire tampon de profondeur, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: d2708dcf39f1d2c67ab1abf69f8330f9dd536ab0
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010270"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="33752-104">Point de focus dans Unity</span><span class="sxs-lookup"><span data-stu-id="33752-104">Focus point in Unity</span></span>

<span data-ttu-id="33752-105">**Espace de noms :** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="33752-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="33752-106">**Type**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="33752-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="33752-107">Utilisez le [point de focus](../platform-capabilities-and-apis/hologram-stability.md#reprojection) pour fournir à HoloLens une indication sur la manière de mieux stabiliser les hologrammes actuellement affichés.</span><span class="sxs-lookup"><span data-stu-id="33752-107">Use the [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) to provide HoloLens with a hint about how to best stabilize the holograms currently being displayed.</span></span>

<span data-ttu-id="33752-108">Si vous souhaitez définir le point de focus dans Unity, vous devez définir chaque frame à l’aide de *HolographicSettings. SetFocusPointForFrame ()*.</span><span class="sxs-lookup"><span data-stu-id="33752-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="33752-109">Lorsque le point de focus n’est pas défini pour un cadre, le plan de stabilisation par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="33752-109">When the Focus Point isn't set for a frame, the default stabilization plane is used.</span></span>

> [!NOTE]
> <span data-ttu-id="33752-110">Par défaut, l’option « Activer le partage de tampon de profondeur » est définie pour les nouveaux projets Unity.</span><span class="sxs-lookup"><span data-stu-id="33752-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="33752-111">Avec cette option, une application Unity s’exécutant sur un casque de bureau immersif ou sur un HoloLens exécutant la mise à jour 2018 d’avril de Windows 10 (RS4) ou une version ultérieure envoie votre tampon de profondeur à Windows pour optimiser la stabilité de l’hologramme automatiquement, sans que votre application spécifie un point de focalisation :</span><span class="sxs-lookup"><span data-stu-id="33752-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="33752-112">Sur un casque d’un bureau immersif, cela permet une reprojection basée sur la profondeur par pixel.</span><span class="sxs-lookup"><span data-stu-id="33752-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="33752-113">Sur un HoloLens exécutant la mise à jour 2018 de Windows 10 avril ou une version ultérieure, le tampon de profondeur est analysé afin de choisir un plan de stabilisation optimal automatiquement.</span><span class="sxs-lookup"><span data-stu-id="33752-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="33752-114">L’une ou l’autre approche devrait offrir une meilleure qualité d’image sans travail explicite de votre application pour sélectionner un point de focus pour chaque frame.</span><span class="sxs-lookup"><span data-stu-id="33752-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="33752-115">Notez que si vous fournissez un point de focalisation manuellement, cela remplacera le comportement automatique décrit ci-dessus et réduira généralement la stabilité de l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="33752-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="33752-116">En règle générale, vous devez uniquement spécifier un point de focus manuel lorsque votre application s’exécute sur un HoloLens qui n’a pas encore été mis à jour vers la mise à jour 2018 d’avril de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="33752-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="33752-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="33752-117">Example</span></span>

<span data-ttu-id="33752-118">Il existe de nombreuses façons de définir le point de focus, comme suggéré par les surcharges disponibles sur la fonction statique *SetFocusPointForFrame* .</span><span class="sxs-lookup"><span data-stu-id="33752-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="33752-119">Vous trouverez ci-dessous un exemple simple pour définir le plan de focus sur l’objet fourni pour chaque frame :</span><span class="sxs-lookup"><span data-stu-id="33752-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> <span data-ttu-id="33752-120">Le code simple ci-dessus peut réduire la stabilité des hologrammes si l’objet ayant le focus se termine derrière l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="33752-120">The simple code above may reduce hologram stability if the focused object ends up behind the user.</span></span> <span data-ttu-id="33752-121">Nous recommandons généralement de définir le **[partage de mémoire tampon de profondeur](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** au lieu de spécifier manuellement un point de focus.</span><span class="sxs-lookup"><span data-stu-id="33752-121">We generally recommend setting **[Enable Depth Buffer Sharing](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="33752-122">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="33752-122">Next Development Checkpoint</span></span>

<span data-ttu-id="33752-123">Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des fonctionnalités de la plateforme de réalité mixte et des API.</span><span class="sxs-lookup"><span data-stu-id="33752-123">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="33752-124">À partir de là, vous pouvez passer à la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="33752-124">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="33752-125">Perte de suivi</span><span class="sxs-lookup"><span data-stu-id="33752-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="33752-126">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="33752-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="33752-127">Déployer sur HoloLens ou sur des casques immersifs Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="33752-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="33752-128">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#3-platform-capabilities-and-apis) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="33752-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="33752-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33752-129">See also</span></span>
* [<span data-ttu-id="33752-130">Plan de stabilisation</span><span class="sxs-lookup"><span data-stu-id="33752-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
