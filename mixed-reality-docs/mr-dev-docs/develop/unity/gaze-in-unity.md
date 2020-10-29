---
title: Pointage du regard dans Unity
description: Le point de regard est un moyen principal pour les utilisateurs de cibler les hologrammes que votre application crée en réalité mixte.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: oeil-point de regard, point de regard, Unity, hologramme, réalité mixte
ms.openlocfilehash: 8c1a6cb0847cd0e6e776c6d4e1f7c1efdc126279
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679774"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="becda-104">Tête-pointage dans Unity</span><span class="sxs-lookup"><span data-stu-id="becda-104">Head-gaze in Unity</span></span>

<span data-ttu-id="becda-105">Le point de [regard](../../design/gaze-and-commit.md) est un moyen principal pour les utilisateurs de cibler les [hologrammes](../../discover/hologram.md) que votre application crée en [réalité mixte](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="becda-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="becda-106">Implémentation de la tête en regard</span><span class="sxs-lookup"><span data-stu-id="becda-106">Implementing head-gaze</span></span>

<span data-ttu-id="becda-107">D’un point de vue conceptuel, le regard de la [tête](../../design/gaze-and-commit.md) est implémenté en projetant un rayon à partir de la tête de l’utilisateur où le casque est, dans la direction vers l’avant et en déterminant ce que ce rayon entre en conflit.</span><span class="sxs-lookup"><span data-stu-id="becda-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="becda-108">Dans Unity, la position et la direction de l’en-tête de l’utilisateur sont exposées via l' [appareil photo](camera-in-unity.md)Unity principal, en particulier [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformez. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) et [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformation. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="becda-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="becda-109">L’appel de [physique. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) génère une structure [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) qui contient des informations sur la collision, y compris le point 3D dans lequel une collision s’est produite et l’autre gameobject le rayon de la tête de regard.</span><span class="sxs-lookup"><span data-stu-id="becda-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="becda-110">Exemple : implémenter l’en-tête</span><span class="sxs-lookup"><span data-stu-id="becda-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="becda-111">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="becda-111">Best practices</span></span>

<span data-ttu-id="becda-112">Bien que l’exemple ci-dessus montre comment effectuer un raycast unique dans une boucle de mise à jour pour trouver la cible sur laquelle pointe l’utilisateur, il est recommandé de le faire dans un seul objet gérant le point de vue de la tête au lieu de le faire dans un objet qui peut intéresser l’objet en cours de regard.</span><span class="sxs-lookup"><span data-stu-id="becda-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="becda-113">Cela permet à votre application de sauvegarder le traitement en n’exécutant qu’une seule tête de regard raycast chaque cadre.</span><span class="sxs-lookup"><span data-stu-id="becda-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="becda-114">Visualisation de l’en-tête</span><span class="sxs-lookup"><span data-stu-id="becda-114">Visualizing head-gaze</span></span>

<span data-ttu-id="becda-115">Tout comme sur le bureau où vous utilisez un pointeur de souris pour cibler et interagir avec le contenu, vous devez implémenter un [curseur](../../design/cursors.md) qui représente le point de regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="becda-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="becda-116">Cela permet à l’utilisateur de faire confiance à ce qu’il est en train d’interagir avec.</span><span class="sxs-lookup"><span data-stu-id="becda-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="becda-117">Tête-pointage dans la réalité mixte Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="becda-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="becda-118">Vous pouvez accéder au point de regard du [Gestionnaire d’entrée](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) dans MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="becda-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="becda-119">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="becda-119">Next Development Checkpoint</span></span>

<span data-ttu-id="becda-120">Si vous suivez le parcours du point de contrôle de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="becda-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="becda-121">À partir de là, vous pouvez passer au bloc de construction suivant :</span><span class="sxs-lookup"><span data-stu-id="becda-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="becda-122">Mouvements et contrôleurs de mouvement</span><span class="sxs-lookup"><span data-stu-id="becda-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="becda-123">Ou accédez aux API et fonctionnalités de la plateforme de réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="becda-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="becda-124">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="becda-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="becda-125">Vous pouvez toujours revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="becda-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="becda-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="becda-126">See also</span></span>
* [<span data-ttu-id="becda-127">Appareil photo</span><span class="sxs-lookup"><span data-stu-id="becda-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="becda-128">Curseurs</span><span class="sxs-lookup"><span data-stu-id="becda-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="becda-129">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="becda-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
