---
title: Point de focus dans Unity
description: Apprenez à ajuster manuellement la stabilité des hologrammes dans Unity en définissant le point de focalisation pour HoloLens et les casques immersif Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, point de focalisation, plan de focalisation, plan de stabilisation, point de stabilisation, reprojection, LSR, mémoire tampon de profondeur, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 16f359e1742b86c5f12c0c5965ac9e818ea76aee
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636221"
---
# <a name="focus-point-in-unity"></a>Point de focus dans Unity

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Type**: *HolographicSettings*

Utilisez le [point de focus](../platform-capabilities-and-apis/hologram-stability.md#reprojection) pour fournir à HoloLens une indication sur la manière de mieux stabiliser les hologrammes actuellement affichés.

Si vous souhaitez définir le point de focus dans Unity, vous devez définir chaque frame à l’aide de *HolographicSettings. SetFocusPointForFrame ()*. Lorsque le point de focus n’est pas défini pour un cadre, le plan de stabilisation par défaut est utilisé.

> [!NOTE]
> Par défaut, l’option « Activer le partage de tampon de profondeur » est définie pour les nouveaux projets Unity.  Avec cette option, une application Unity s’exécutant sur un casque de bureau immersif ou sur un HoloLens exécutant la mise à jour 2018 d’avril de Windows 10 (RS4) ou une version ultérieure envoie votre tampon de profondeur à Windows pour optimiser la stabilité de l’hologramme automatiquement, sans que votre application spécifie un point de focalisation :
> * Sur un casque d’un bureau immersif, cela permet une reprojection basée sur la profondeur par pixel.
> * Sur un HoloLens exécutant la mise à jour 2018 de Windows 10 avril ou une version ultérieure, le tampon de profondeur est analysé afin de choisir un plan de stabilisation optimal automatiquement.
>
> L’une ou l’autre approche devrait offrir une meilleure qualité d’image sans travail explicite de votre application pour sélectionner un point de focus pour chaque frame.  Notez que si vous fournissez un point de focalisation manuellement, cela remplacera le comportement automatique décrit ci-dessus et réduira généralement la stabilité de l’hologramme.  En règle générale, vous devez uniquement spécifier un point de focus manuel lorsque votre application s’exécute sur un HoloLens qui n’a pas encore été mis à jour vers la mise à jour 2018 d’avril de Windows 10.

### <a name="example"></a>Exemple

Il existe de nombreuses façons de définir le point de focus, comme suggéré par les surcharges disponibles sur la fonction statique *SetFocusPointForFrame* . Vous trouverez ci-dessous un exemple simple pour définir le plan de focus sur l’objet fourni pour chaque frame :

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
> Le code simple ci-dessus peut réduire la stabilité des hologrammes si l’objet ayant le focus se termine derrière l’utilisateur. Nous recommandons généralement de définir le **[partage de mémoire tampon de profondeur](camera-in-unity.md#sharing-depth-buffers)** au lieu de spécifier manuellement un point de focus.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des fonctionnalités de la plateforme de réalité mixte et des API. À partir d’ici, vous pouvez passer au sujet suivant :

> [!div class="nextstepaction"]
> [Perte de suivi](tracking-loss-in-unity.md)

Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :

> [!div class="nextstepaction"]
> [Déployer sur HoloLens ou sur des casques immersifs Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#3-advanced-features) à tout moment.

### <a name="see-also"></a>Voir aussi

* [Plan de stabilisation](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
