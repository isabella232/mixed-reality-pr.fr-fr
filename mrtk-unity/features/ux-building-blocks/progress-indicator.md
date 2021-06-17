---
title: ProgressIndicator
description: Vue d’ensemble de l’indicateur de progression dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110125"
---
# <a name="progress-indicators"></a><span data-ttu-id="ba900-104">Indicateurs de progression</span><span class="sxs-lookup"><span data-stu-id="ba900-104">Progress Indicators</span></span>

![Indicateurs de progression](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="ba900-106">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="ba900-106">Example scene</span></span>

<span data-ttu-id="ba900-107">Vous trouverez des exemples d’utilisation des indicateurs de progression dans la `ProgressIndicatorExamples` scène.</span><span class="sxs-lookup"><span data-stu-id="ba900-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="ba900-108">Cette scène montre chacun des indicateurs de progression prefabs inclus dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="ba900-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="ba900-109">Il montre également comment utiliser des indicateurs de progression conjointement à certaines tâches asynchrones courantes telles que le chargement de scènes.</span><span class="sxs-lookup"><span data-stu-id="ba900-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="ba900-110">Exemple : ouvrir, mettre à jour & fermer un indicateur de progression</span><span class="sxs-lookup"><span data-stu-id="ba900-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="ba900-111">Les indicateurs de progression implémentent l' [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span><span class="sxs-lookup"><span data-stu-id="ba900-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="ba900-112">Cette interface peut être récupérée à partir d’un GameObject à l’aide de `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="ba900-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="ba900-113">Les `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` méthodes et retournent des [tâches](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="ba900-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="ba900-114">Nous vous recommandons d’attendre ces tâches dans une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="ba900-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="ba900-115">L’indicateur de progression par défaut de MRTK prefabs doit être inactif lorsqu’il est placé dans une scène.</span><span class="sxs-lookup"><span data-stu-id="ba900-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="ba900-116">Lorsque leurs `IProgressIndicator.OpenAsync()` méthodes sont appelées, les indicateurs de progression activent et désactivent automatiquement leur Gameobjects.</span><span class="sxs-lookup"><span data-stu-id="ba900-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="ba900-117">(Ce modèle n’est pas une exigence de l’interface IProgressIndicator.)</span><span class="sxs-lookup"><span data-stu-id="ba900-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="ba900-118">Affectez à la propriété de l’indicateur `Progress` une valeur de 0-1 pour mettre à jour sa progression affichée.</span><span class="sxs-lookup"><span data-stu-id="ba900-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="ba900-119">Définissez sa `Message` propriété pour mettre à jour son message affiché.</span><span class="sxs-lookup"><span data-stu-id="ba900-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="ba900-120">Différentes implémentations peuvent afficher ce contenu de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="ba900-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="ba900-121">États des indicateurs</span><span class="sxs-lookup"><span data-stu-id="ba900-121">Indicator states</span></span>

<span data-ttu-id="ba900-122">La propriété d’un indicateur `State` détermine les opérations qui sont valides.</span><span class="sxs-lookup"><span data-stu-id="ba900-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="ba900-123">L’appel d’une méthode non valide entraîne généralement le signalement d’une erreur par l’indicateur et aucune action.</span><span class="sxs-lookup"><span data-stu-id="ba900-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="ba900-124">État</span><span class="sxs-lookup"><span data-stu-id="ba900-124">State</span></span> | <span data-ttu-id="ba900-125">Opérations valides</span><span class="sxs-lookup"><span data-stu-id="ba900-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="ba900-126">`AwaitTransitionAsync()` peut être utilisé pour s’assurer qu’un indicateur est entièrement ouvert ou fermé avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="ba900-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
