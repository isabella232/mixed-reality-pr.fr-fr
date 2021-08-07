---
title: Pointage du regard
description: Docummentation sur les types de regards MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, point de regard
ms.openlocfilehash: a9d97ef73a7014a46001cbd42281c5ab28f6cf425dfd7605ce5b3c8c7fc45198
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208430"
---
# <a name="gaze"></a>Pointage du regard

Le point de [regard](/windows/mixed-reality/gaze) est une forme d’entrée qui interagit avec le monde en fonction de l’endroit où l’utilisateur regarde. Le point de regard existe dans deux versions différentes

## <a name="head-gaze"></a>Suivi de la tête

Ce type de point de regard est basé sur la direction que le tête/caméra examine. Le point de regard est actif sur les systèmes qui ne prennent pas en charge les yeux oculaires, ou dans les cas où le matériel peut prendre en charge un point de regard oculaire, mais le jeu d' [autorisations et le programme d’installation](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) appropriés n’ont pas été exécutés.

le point de regard de la tête est généralement associé à des interactions de style HoloLens 1 impliquant la recherche d’un objet en le plaçant au centre du cadre holographique, puis en effectuant le mouvement d’appui sur l’air.

## <a name="eye-gaze"></a>Suivre du regard

Ce type de regard est basé sur l’endroit où les yeux de l’utilisateur cherchent. Le point de présence oculaire n’est présent que sur les systèmes qui prennent en charge le suivi oculaire. Pour plus d’informations sur l’utilisation de l’œil, consultez la documentation sur le [suivi visuel](eye-tracking/eye-tracking-main.md) .

## <a name="gazeprovider"></a>GazeProvider

La fonctionnalité de pointage (à la fois en tête et en œil) est fournie par le [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider). Ce fournisseur peut être configuré dans la section du *pointeur* du profil de système d’entrée :

![Point d’entrée de configuration de regard](../images/input/GazeConfigurationEntrypoint.png)

Comme les autres sources d’entrée, le fournisseur de regard interagit avec les objets de la scène à l’aide d’un pointeur [(consultez ce document pour plus d’informations sur les pointeurs)](../../architecture/controllers-pointers-and-focus.md).
Dans le cas du fournisseur de regard, son pointeur est implémenté via `InternalGazePointer` et n’est pas configuré par le biais d’un profil.

Il est possible de remplacer le stock GazeProvider par une autre implémentation en modifiant le *type de fournisseur de regard* pour référencer une autre classe qui implémente [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) et [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).
Il est généralement recommandé d’utiliser le stock GazeProvider (et les problèmes de classement dans lors de la recherche de bogues), car la réimplémentation du GazeProvider est non triviale.

### <a name="alternative-platform-provided-gaze-poses"></a>Autres poses de regard fournis par la plateforme

Par défaut, le GazeProvider MRTK utilise le centre du cadre de l’appareil photo comme origine du regard. certaines plateformes, comme Windows Mixed Reality sur HoloLens 2, fournissent une variante de regard définie. Cela est géré par le biais du `Use Head Gaze Override` paramètre dans les paramètres du point de regard. Lorsque cette option est activée, l’autre remplacement de point d’arrêt est utilisé. Lorsque cette option est désactivée, l’origine du centre de frames par défaut est utilisée. en particulier, pour HoloLens 2, l’angle de regard sera augmenté de plusieurs degrés pour prendre en compte le confort de l’utilisateur lors de l’utilisation de son chef pour le ciblage.

## <a name="usage"></a>Utilisation

### <a name="how-get-the-current-gaze-target"></a>Obtention de la cible du regard en cours

Cet exemple montre comment récupérer l’objet de jeu actuel ciblé par le point de regard de l’utilisateur.

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>Obtention de l’origine et de la direction du regard en cours

Cet exemple montre comment faire en sorte que le Vector3 représente la direction du point de vue de l’utilisateur et de l’origine (le point à partir duquel le sens se passe).

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
