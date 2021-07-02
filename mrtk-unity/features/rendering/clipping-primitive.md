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
# <a name="clipping-primitive"></a>Primitive de découpage

Les [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportements permettent un [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) découpage de forme performant, et avec la possibilité de spécifier le côté de la primitive à découper (à l’intérieur ou à l’extérieur) lorsqu’il est utilisé avec les nuanceurs MRTK.

![gizmos de découpage primitif](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Utilisez des instructions [clip/ignorer](https://developer.download.nvidia.com/cg/clip.html) dans les nuanceurs et désactivez la capacité de l’unité à traiter les convertisseurs découpés par lots. Tenez compte de ces implications en matière de performances lors de l’utilisation de primitives de découpage.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) et [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) peuvent être utilisés pour contrôler facilement les propriétés de la primitive de découpage. Utilisez ces composants avec les nuanceurs suivants pour tirer parti des scénarios de découpage.

- *Shared Computer Toolkit de la réalité mixte/d'*
- *Shared Computer Toolkit de la réalité mixte/TextMeshPro*
- *Shared Computer Toolkit de la réalité mixte/Text3DShader*

## <a name="examples"></a>Exemples

Les scènes **ClippingExamples** et **MaterialGallery** illustrent l’utilisation des [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportements, et sont disponibles à l’adresse suivante : MRTK/examples/démos/StandardShader/scenes/

## <a name="advanced-usage"></a>Utilisation avancée

Par défaut, seul un [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer.html) peut être détouré à la fois. Si votre projet nécessite plusieurs [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) pour influencer un [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer.html)  , l’exemple de code ci-dessous montre comment y parvenir.

> [!NOTE]
> Le fait [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) de disposer de plusieurs images de [rendu](https://docs.unity3d.com/ScriptReference/Renderer.html) augmente les instructions de nuanceur de pixels et influe sur les performances. Profilez ces modifications dans votre projet.

*Comment faire en sorte que deux [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) images d’un rendu différent. Par exemple [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) , et [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) en même temps :*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> La modification ci-dessus entraînera une heure de compilation du nuanceur supplémentaire.

*Comment faire en sorte que deux du même [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip soient rendus. Par exemple, deux [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) en même temps :*

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

Enfin, ajoutez un [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) composant et SecondClippingBox à votre scène et spécifiez le même convertisseur pour les deux zones. Le convertisseur doit maintenant être coupé par les deux zones simultanément.

## <a name="see-also"></a>Voir aussi

- [Nuanceur standard MRTK](mrtk-standard-shader.md)
