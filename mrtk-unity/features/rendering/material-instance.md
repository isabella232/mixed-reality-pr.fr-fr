---
title: Instance de matériau
description: Documentation sur l’instance de matériel et ses utilisations dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, MaterialInstance,
ms.openlocfilehash: ecd8f9e14564cbd03cb6faa848b06ca55a024207
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176724"
---
# <a name="material-instance"></a><span data-ttu-id="64cf6-104">Instance de matériau</span><span class="sxs-lookup"><span data-stu-id="64cf6-104">Material instance</span></span>

<span data-ttu-id="64cf6-105">Le [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportement aides dans le suivi de la durée de vie des documents d’instance et détruit automatiquement les matériaux instanciés pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64cf6-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="64cf6-106">Ce composant utilitaire peut être utilisé pour remplacer le [convertisseur. Material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ou [Renderer](https://docs.unity3d.com/ScriptReference/Renderer-materials.html). Materials.</span><span class="sxs-lookup"><span data-stu-id="64cf6-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="64cf6-107">Les [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) sont préférables à l’instanciation du matériel, mais ne sont pas toujours disponibles dans tous les scénarios.</span><span class="sxs-lookup"><span data-stu-id="64cf6-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="64cf6-108">Pourquoi l’utilisation du [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer-material.html) est-elle un problème ?</span><span class="sxs-lookup"><span data-stu-id="64cf6-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="64cf6-109">Si vous ajoutez le code ci-dessous à une scène Unity et que vous appuyez sur lire, l’utilisation de la mémoire continuera à augmenter et à grimper :</span><span class="sxs-lookup"><span data-stu-id="64cf6-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> <span data-ttu-id="64cf6-110">Le comportement de fuite ci-dessus **se bloquera** si l’exécution est trop longue.</span><span class="sxs-lookup"><span data-stu-id="64cf6-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="64cf6-111">Essayez plutôt d’utiliser le [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportement :</span><span class="sxs-lookup"><span data-stu-id="64cf6-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a><span data-ttu-id="64cf6-112">Usage</span><span class="sxs-lookup"><span data-stu-id="64cf6-112">Usage</span></span>

<span data-ttu-id="64cf6-113">Lorsque vous appelez le [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer-material.html)de l’unité, Unit (s), Unity instancie automatiquement les nouveaux matériaux.</span><span class="sxs-lookup"><span data-stu-id="64cf6-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="64cf6-114">Il incombe à l’appelant de détruire les documents lorsqu’un matériau n’est plus nécessaire ou que l’objet de jeu est détruit.</span><span class="sxs-lookup"><span data-stu-id="64cf6-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="64cf6-115">Le [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportement permet d’éviter les fuites matérielles et de préserver la cohérence des chemins d’accès au cours de la modification et de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="64cf6-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="64cf6-116">Lorsqu’un [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) ne peut pas être utilisé et qu’un matériau doit être instancié, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) peut être utilisé comme suit :</span><span class="sxs-lookup"><span data-stu-id="64cf6-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

<span data-ttu-id="64cf6-117">Si plusieurs objets ont besoin de la propriété de l’instance de matériau, il est préférable de prendre une propriété explicite pour le suivi de référence.</span><span class="sxs-lookup"><span data-stu-id="64cf6-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="64cf6-118">(Une interface facultative appelée [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) existe pour faciliter la propriété.) Voici un exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="64cf6-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

<span data-ttu-id="64cf6-119">Pour plus d’informations, consultez l’exemple d’utilisation présenté dans le [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportement.</span><span class="sxs-lookup"><span data-stu-id="64cf6-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="64cf6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64cf6-120">See also</span></span>

* [<span data-ttu-id="64cf6-121">Nuanceur standard MRTK</span><span class="sxs-lookup"><span data-stu-id="64cf6-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
