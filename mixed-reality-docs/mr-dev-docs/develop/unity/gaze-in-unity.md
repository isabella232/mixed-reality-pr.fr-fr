---
title: Pointage du regard dans Unity
description: Le point de regard est un moyen principal pour les utilisateurs de cibler les hologrammes que votre application crée en réalité mixte.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: œil-point de présence, point de présence, unité, hologramme, réalité mixte, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: ca33fef5a5a761df83ed7991b366cf711a5db224
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010360"
---
# <a name="head-gaze-in-unity"></a>Tête-pointage dans Unity

Le point de [regard](../../design/gaze-and-commit.md) est le principal moyen pour les utilisateurs de cibler des [hologrammes](../../discover/hologram.md) que votre application crée en [réalité mixte](../../discover/mixed-reality.md).

## <a name="implementing-head-gaze"></a>Implémentation de la tête en regard

D’un point de vue conceptuel, vous déterminez la [tête du regard](../../design/gaze-and-commit.md) en projetant un rayon à partir du casque de l’utilisateur pour voir ce qu’il rencontre. Dans Unity, la position et la direction de l’en-tête de l’utilisateur sont exposées via l' [appareil photo](camera-in-unity.md), en particulier [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformez. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) et [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformation. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

L’appel de [physique. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) vous donne un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) contenant des informations sur la collision, y compris le point de collision 3D et l’autre gameobject le point d’accès en chef.

### <a name="example-implement-head-gaze"></a>Exemple : implémenter l’en-tête

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

### <a name="best-practices"></a>Meilleures pratiques

Bien que l’exemple ci-dessus déclenche un raycast unique à partir de la boucle de mise à jour pour trouver la cible sur laquelle pointe l’utilisateur, nous vous recommandons d’utiliser un seul objet pour gérer tous les processus de pointage en tête. La combinaison de la logique du point de vue vous permet d’économiser la puissance de traitement de votre application et de limiter vos Raycasting à un par image.

## <a name="visualizing-head-gaze"></a>Visualisation de l’en-tête

Comme avec un pointeur de souris sur un ordinateur, vous devez implémenter un [curseur](../../design/cursors.md) qui représente le point de regard de l’utilisateur. Le fait de connaître le contenu ciblé par un utilisateur augmente la confiance en ce qui concerne l’interaction avec.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Tête-regard du kit de réalité mixte 
Vous pouvez accéder au point de regard du [Gestionnaire d’entrée](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) dans MRTK.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core. À partir de là, vous pouvez passer au bloc de construction suivant :

> [!div class="nextstepaction"]
> [Mouvements et contrôleurs de mouvement](gestures-and-motion-controllers-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Appareil photo](camera-in-unity.md)
* [Curseurs](../../design/cursors.md)
* [Suivre de la tête et valider](../../design/gaze-and-commit.md)
