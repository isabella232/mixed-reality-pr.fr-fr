---
title: Indicateur de progression
description: Vue d’ensemble de l’indicateur de progression dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: b5147e5c592b80ab100a7cf7ce2487d971299832fec11f7ca57b1fdeef530900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202583"
---
# <a name="progress-indicator"></a>Indicateur de progression

![Indicateurs de progression](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples d’utilisation des indicateurs de progression dans la `ProgressIndicatorExamples` scène. Cette scène montre chacun des indicateurs de progression prefabs inclus dans le kit de développement logiciel (SDK). Il montre également comment utiliser des indicateurs de progression conjointement à certaines tâches asynchrones courantes telles que le chargement de scènes.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>Exemple : ouvrir, mettre à jour & fermer un indicateur de progression

Les indicateurs de progression implémentent l' [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface. Cette interface peut être récupérée à partir d’un GameObject à l’aide de `GetComponent` .

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

Les `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` méthodes et retournent des [tâches](xref:System.Threading.Tasks.Task). Nous vous recommandons d’attendre ces tâches dans une méthode Async.

L’indicateur de progression par défaut de MRTK prefabs doit être inactif lorsqu’il est placé dans une scène. Lorsque leurs `IProgressIndicator.OpenAsync()` méthodes sont appelées, les indicateurs de progression activent et désactivent automatiquement leur Gameobjects. (Ce modèle n’est pas une exigence de l’interface IProgressIndicator.)

Affectez à la propriété de l’indicateur `Progress` une valeur de 0-1 pour mettre à jour sa progression affichée. Définissez sa `Message` propriété pour mettre à jour son message affiché. Différentes implémentations peuvent afficher ce contenu de différentes façons.

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>États des indicateurs

La propriété d’un indicateur `State` détermine les opérations qui sont valides. L’appel d’une méthode non valide entraîne généralement le signalement d’une erreur par l’indicateur et aucune action.

État | Opérations valides
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` peut être utilisé pour s’assurer qu’un indicateur est entièrement ouvert ou fermé avant de l’utiliser.

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
