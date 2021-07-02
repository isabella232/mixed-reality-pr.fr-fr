---
title: Primitive de découpage
description: Documentation sur les primitives de découpage avec des exemples dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, primitive de découpage,
ms.openlocfilehash: c3331084f87ccc57208426910d84ed7bef457bc1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176742"
---
# <a name="clipping-primitive"></a><span data-ttu-id="612b7-104">Primitive de découpage</span><span class="sxs-lookup"><span data-stu-id="612b7-104">Clipping primitive</span></span>

<span data-ttu-id="612b7-105">Les [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportements permettent un [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) découpage de forme performant, et avec la possibilité de spécifier le côté de la primitive à découper (à l’intérieur ou à l’extérieur) lorsqu’il est utilisé avec les nuanceurs MRTK.</span><span class="sxs-lookup"><span data-stu-id="612b7-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![gizmos de découpage primitif](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="612b7-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Utilisez des instructions [clip/ignorer](https://developer.download.nvidia.com/cg/clip.html) dans les nuanceurs et désactivez la capacité de l’unité à traiter les convertisseurs découpés par lots.</span><span class="sxs-lookup"><span data-stu-id="612b7-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="612b7-108">Tenez compte de ces implications en matière de performances lors de l’utilisation de primitives de découpage.</span><span class="sxs-lookup"><span data-stu-id="612b7-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="612b7-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) et [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) peuvent être utilisés pour contrôler facilement les propriétés de la primitive de découpage.</span><span class="sxs-lookup"><span data-stu-id="612b7-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="612b7-110">Utilisez ces composants avec les nuanceurs suivants pour tirer parti des scénarios de découpage.</span><span class="sxs-lookup"><span data-stu-id="612b7-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="612b7-111">*Shared Computer Toolkit de la réalité mixte/d'*</span><span class="sxs-lookup"><span data-stu-id="612b7-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="612b7-112">*Shared Computer Toolkit de la réalité mixte/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="612b7-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="612b7-113">*Shared Computer Toolkit de la réalité mixte/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="612b7-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="612b7-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="612b7-114">Examples</span></span>

<span data-ttu-id="612b7-115">Les scènes **ClippingExamples** et **MaterialGallery** illustrent l’utilisation des [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportements, et sont disponibles à l’adresse suivante : MRTK/examples/démos/StandardShader/scenes/</span><span class="sxs-lookup"><span data-stu-id="612b7-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="612b7-116">Utilisation avancée</span><span class="sxs-lookup"><span data-stu-id="612b7-116">Advanced Usage</span></span>

<span data-ttu-id="612b7-117">Par défaut, seul un [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer.html) peut être détouré à la fois.</span><span class="sxs-lookup"><span data-stu-id="612b7-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="612b7-118">Si votre projet nécessite plusieurs [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) pour influencer un [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer.html)  , l’exemple de code ci-dessous montre comment y parvenir.</span><span class="sxs-lookup"><span data-stu-id="612b7-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="612b7-119">Le fait [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) de disposer de plusieurs images de [rendu](https://docs.unity3d.com/ScriptReference/Renderer.html) augmente les instructions de nuanceur de pixels et influe sur les performances.</span><span class="sxs-lookup"><span data-stu-id="612b7-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="612b7-120">Profilez ces modifications dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="612b7-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="612b7-121">*Comment faire en sorte que deux [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) images d’un rendu différent. Par exemple [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) , et [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) en même temps :*</span><span class="sxs-lookup"><span data-stu-id="612b7-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="612b7-122">La modification ci-dessus entraînera une heure de compilation du nuanceur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="612b7-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="612b7-123">*Comment faire en sorte que deux du même [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip soient rendus. Par exemple, deux [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) en même temps :*</span><span class="sxs-lookup"><span data-stu-id="612b7-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

<span data-ttu-id="612b7-124">Enfin, ajoutez un [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) composant et SecondClippingBox à votre scène et spécifiez le même convertisseur pour les deux zones.</span><span class="sxs-lookup"><span data-stu-id="612b7-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="612b7-125">Le convertisseur doit maintenant être coupé par les deux zones simultanément.</span><span class="sxs-lookup"><span data-stu-id="612b7-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="612b7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="612b7-126">See also</span></span>

- [<span data-ttu-id="612b7-127">Nuanceur standard MRTK</span><span class="sxs-lookup"><span data-stu-id="612b7-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
