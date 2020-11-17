---
title: Pointage du regard dans Unity
description: Le point de regard est un moyen principal pour les utilisateurs de cibler les hologrammes que votre application crée en réalité mixte.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: œil-point de présence, point de présence, unité, hologramme, réalité mixte, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677508"
---
# <a name="head-gaze-in-unity"></a>Tête-pointage dans Unity

Le point de [regard](../../design/gaze-and-commit.md) est un moyen principal pour les utilisateurs de cibler les [hologrammes](../../discover/hologram.md) que votre application crée en [réalité mixte](../../discover/mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implémentation de la tête en regard

D’un point de vue conceptuel, le regard de la [tête](../../design/gaze-and-commit.md) est implémenté en projetant un rayon à partir de la tête de l’utilisateur où le casque est, dans la direction vers l’avant et en déterminant ce que ce rayon entre en conflit.
Dans Unity, la position et la direction de l’en-tête de l’utilisateur sont exposées via l' [appareil photo](camera-in-unity.md)Unity principal, en particulier [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformez. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) et [UnityEngine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transformation. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

L’appel de [physique. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) génère une structure [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) qui contient des informations sur la collision, y compris le point 3D dans lequel une collision s’est produite et l’autre gameobject le rayon de la tête de regard.

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

Bien que l’exemple ci-dessus montre comment effectuer un raycast unique dans une boucle de mise à jour pour trouver la cible sur laquelle pointe l’utilisateur, il est recommandé de le faire dans un seul objet gérant le point de vue de la tête au lieu de le faire dans un objet qui peut intéresser l’objet en cours de regard. Cela permet à votre application de sauvegarder le traitement en n’exécutant qu’une seule tête de regard raycast chaque cadre.

## <a name="visualizing-head-gaze"></a>Visualisation de l’en-tête

Tout comme sur le bureau où vous utilisez un pointeur de souris pour cibler et interagir avec le contenu, vous devez implémenter un [curseur](../../design/cursors.md) qui représente le point de regard de l’utilisateur. Cela permet à l’utilisateur de faire confiance à ce qu’il est en train d’interagir avec.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Tête-pointage dans la réalité mixte Toolkit v2
Vous pouvez accéder au point de regard du [Gestionnaire d’entrée](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) dans MRTK v2.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de points de contrôle de développement Unity que nous avons élaboré, vous explorez actuellement les composants de base de MRTK. À partir de là, vous pouvez passer au composant suivant :

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
