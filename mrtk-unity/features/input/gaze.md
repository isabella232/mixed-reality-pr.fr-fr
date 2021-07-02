---
title: Pointage du regard
description: Docummentation sur les types de regards MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, point de regard
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176915"
---
# <a name="gaze"></a><span data-ttu-id="0b4db-104">Pointage du regard</span><span class="sxs-lookup"><span data-stu-id="0b4db-104">Gaze</span></span>

<span data-ttu-id="0b4db-105">Le point de [regard](/windows/mixed-reality/gaze) est une forme d’entrée qui interagit avec le monde en fonction de l’endroit où l’utilisateur regarde.</span><span class="sxs-lookup"><span data-stu-id="0b4db-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="0b4db-106">Le point de regard existe dans deux versions différentes</span><span class="sxs-lookup"><span data-stu-id="0b4db-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="0b4db-107">Suivi de la tête</span><span class="sxs-lookup"><span data-stu-id="0b4db-107">Head gaze</span></span>

<span data-ttu-id="0b4db-108">Ce type de point de regard est basé sur la direction que le tête/caméra examine.</span><span class="sxs-lookup"><span data-stu-id="0b4db-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="0b4db-109">Le point de regard est actif sur les systèmes qui ne prennent pas en charge les yeux oculaires, ou dans les cas où le matériel peut prendre en charge un point de regard oculaire, mais le jeu d' [autorisations et le programme d’installation](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) appropriés n’ont pas été exécutés.</span><span class="sxs-lookup"><span data-stu-id="0b4db-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="0b4db-110">le point de regard de la tête est généralement associé à des interactions de style HoloLens 1 impliquant la recherche d’un objet en le plaçant au centre du cadre holographique, puis en effectuant le mouvement d’appui sur l’air.</span><span class="sxs-lookup"><span data-stu-id="0b4db-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="0b4db-111">Suivre du regard</span><span class="sxs-lookup"><span data-stu-id="0b4db-111">Eye gaze</span></span>

<span data-ttu-id="0b4db-112">Ce type de regard est basé sur l’endroit où les yeux de l’utilisateur cherchent.</span><span class="sxs-lookup"><span data-stu-id="0b4db-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="0b4db-113">Le point de présence oculaire n’est présent que sur les systèmes qui prennent en charge le suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="0b4db-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="0b4db-114">Pour plus d’informations sur l’utilisation de l’œil, consultez la documentation sur le [suivi visuel](eye-tracking/eye-tracking-main.md) .</span><span class="sxs-lookup"><span data-stu-id="0b4db-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="0b4db-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="0b4db-115">GazeProvider</span></span>

<span data-ttu-id="0b4db-116">La fonctionnalité de pointage (à la fois en tête et en œil) est fournie par le [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span><span class="sxs-lookup"><span data-stu-id="0b4db-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="0b4db-117">Ce fournisseur peut être configuré dans la section du *pointeur* du profil de système d’entrée :</span><span class="sxs-lookup"><span data-stu-id="0b4db-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![Point d’entrée de configuration de regard](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="0b4db-119">Comme les autres sources d’entrée, le fournisseur de regard interagit avec les objets de la scène à l’aide d’un pointeur [(consultez ce document pour plus d’informations sur les pointeurs)](../../architecture/controllers-pointers-and-focus.md).</span><span class="sxs-lookup"><span data-stu-id="0b4db-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="0b4db-120">Dans le cas du fournisseur de regard, son pointeur est implémenté via `InternalGazePointer` et n’est pas configuré par le biais d’un profil.</span><span class="sxs-lookup"><span data-stu-id="0b4db-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="0b4db-121">Il est possible de remplacer le stock GazeProvider par une autre implémentation en modifiant le *type de fournisseur de regard* pour référencer une autre classe qui implémente [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) et [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span><span class="sxs-lookup"><span data-stu-id="0b4db-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="0b4db-122">Il est généralement recommandé d’utiliser le stock GazeProvider (et les problèmes de classement dans lors de la recherche de bogues), car la réimplémentation du GazeProvider est non triviale.</span><span class="sxs-lookup"><span data-stu-id="0b4db-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="0b4db-123">Autres poses de regard fournis par la plateforme</span><span class="sxs-lookup"><span data-stu-id="0b4db-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="0b4db-124">Par défaut, le GazeProvider MRTK utilise le centre du cadre de l’appareil photo comme origine du regard.</span><span class="sxs-lookup"><span data-stu-id="0b4db-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="0b4db-125">certaines plateformes, comme Windows Mixed Reality sur HoloLens 2, fournissent une variante de regard définie.</span><span class="sxs-lookup"><span data-stu-id="0b4db-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="0b4db-126">Cela est géré par le biais du `Use Head Gaze Override` paramètre dans les paramètres du point de regard.</span><span class="sxs-lookup"><span data-stu-id="0b4db-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="0b4db-127">Lorsque cette option est activée, l’autre remplacement de point d’arrêt est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0b4db-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="0b4db-128">Lorsque cette option est désactivée, l’origine du centre de frames par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0b4db-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="0b4db-129">en particulier, pour HoloLens 2, l’angle de regard sera augmenté de plusieurs degrés pour prendre en compte le confort de l’utilisateur lors de l’utilisation de son chef pour le ciblage.</span><span class="sxs-lookup"><span data-stu-id="0b4db-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="0b4db-130">Usage</span><span class="sxs-lookup"><span data-stu-id="0b4db-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="0b4db-131">Obtention de la cible du regard en cours</span><span class="sxs-lookup"><span data-stu-id="0b4db-131">How get the current gaze target</span></span>

<span data-ttu-id="0b4db-132">Cet exemple montre comment récupérer l’objet de jeu actuel ciblé par le point de regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0b4db-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

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

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="0b4db-133">Obtention de l’origine et de la direction du regard en cours</span><span class="sxs-lookup"><span data-stu-id="0b4db-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="0b4db-134">Cet exemple montre comment faire en sorte que le Vector3 représente la direction du point de vue de l’utilisateur et de l’origine (le point à partir duquel le sens se passe).</span><span class="sxs-lookup"><span data-stu-id="0b4db-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
