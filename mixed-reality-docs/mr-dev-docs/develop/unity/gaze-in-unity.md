---
title: Pointage du regard dans Unity
description: Apprenez à utiliser l’entrée de regard comme méthode principale permettant aux utilisateurs de cibler les hologrammes que votre application crée en réalité mixte.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: œil-point de présence, point de présence, unité, hologramme, réalité mixte, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: 7602eb27da19dc77e4eab1c1a428dc9a1cf8b252
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759685"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="70129-104">Tête-pointage dans Unity</span><span class="sxs-lookup"><span data-stu-id="70129-104">Head-gaze in Unity</span></span>

<span data-ttu-id="70129-105">Le point de [regard](../../design/gaze-and-commit.md) est le principal moyen pour les utilisateurs de cibler des [hologrammes](../../discover/hologram.md) que votre application crée en [réalité mixte](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="70129-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="70129-106">Implémentation de la tête en regard</span><span class="sxs-lookup"><span data-stu-id="70129-106">Implementing head-gaze</span></span>

<span data-ttu-id="70129-107">D’un point de vue conceptuel, vous déterminez la [tête du regard](../../design/gaze-and-commit.md) en projetant un rayon à partir du casque de l’utilisateur pour voir ce qu’il rencontre.</span><span class="sxs-lookup"><span data-stu-id="70129-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="70129-108">Dans Unity, la position et la direction de l’en-tête de l’utilisateur sont exposées via l' [appareil photo](camera-in-unity.md), en particulier [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformez. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) et [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformation. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="70129-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="70129-109">L’appel de [physique. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) vous donne un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) contenant des informations sur la collision, y compris le point de collision 3D et l’autre gameobject le point d’accès en chef.</span><span class="sxs-lookup"><span data-stu-id="70129-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="70129-110">Exemple : implémenter l’en-tête</span><span class="sxs-lookup"><span data-stu-id="70129-110">Example: Implement head-gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="70129-111">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="70129-111">Best practices</span></span>

<span data-ttu-id="70129-112">Bien que l’exemple ci-dessus déclenche un raycast unique à partir de la boucle de mise à jour pour trouver la cible sur laquelle pointe l’utilisateur, nous vous recommandons d’utiliser un seul objet pour gérer tous les processus de pointage en tête.</span><span class="sxs-lookup"><span data-stu-id="70129-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="70129-113">La combinaison de la logique du point de vue vous permet d’économiser la puissance de traitement de votre application et de limiter vos Raycasting à un par image.</span><span class="sxs-lookup"><span data-stu-id="70129-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="70129-114">Visualisation de l’en-tête</span><span class="sxs-lookup"><span data-stu-id="70129-114">Visualizing head-gaze</span></span>

<span data-ttu-id="70129-115">Comme avec un pointeur de souris sur un ordinateur, vous devez implémenter un [curseur](../../design/cursors.md) qui représente le point de regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="70129-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="70129-116">Le fait de connaître le contenu ciblé par un utilisateur augmente la confiance en ce qui concerne l’interaction avec.</span><span class="sxs-lookup"><span data-stu-id="70129-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="70129-117">Tête-regard du kit de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="70129-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="70129-118">Vous pouvez accéder au point de regard du [Gestionnaire d’entrée](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) dans MRTK.</span><span class="sxs-lookup"><span data-stu-id="70129-118">You can access head-gaze from the [Input Manager](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="70129-119">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="70129-119">Next Development Checkpoint</span></span>

<span data-ttu-id="70129-120">Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="70129-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="70129-121">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="70129-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="70129-122">Contrôleurs de mouvement</span><span class="sxs-lookup"><span data-stu-id="70129-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="70129-123">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="70129-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="70129-124">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="70129-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="70129-125">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="70129-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="70129-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70129-126">See also</span></span>
* [<span data-ttu-id="70129-127">Appareil photo</span><span class="sxs-lookup"><span data-stu-id="70129-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="70129-128">Curseurs</span><span class="sxs-lookup"><span data-stu-id="70129-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="70129-129">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="70129-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
