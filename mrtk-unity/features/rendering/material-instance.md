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
# <a name="material-instance"></a>Instance de matériau

Le [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportement aides dans le suivi de la durée de vie des documents d’instance et détruit automatiquement les matériaux instanciés pour l’utilisateur. Ce composant utilitaire peut être utilisé pour remplacer le [convertisseur. Material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ou [Renderer](https://docs.unity3d.com/ScriptReference/Renderer-materials.html). Materials.

> [!NOTE]
> Les [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) sont préférables à l’instanciation du matériel, mais ne sont pas toujours disponibles dans tous les scénarios.

Pourquoi l’utilisation du [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer-material.html) est-elle un problème ? Si vous ajoutez le code ci-dessous à une scène Unity et que vous appuyez sur lire, l’utilisation de la mémoire continuera à augmenter et à grimper :

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
> Le comportement de fuite ci-dessus **se bloquera** si l’exécution est trop longue.

Essayez plutôt d’utiliser le [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportement :

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

## <a name="usage"></a>Usage

Lorsque vous appelez le [convertisseur](https://docs.unity3d.com/ScriptReference/Renderer-material.html)de l’unité, Unit (s), Unity instancie automatiquement les nouveaux matériaux. Il incombe à l’appelant de détruire les documents lorsqu’un matériau n’est plus nécessaire ou que l’objet de jeu est détruit. Le [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) comportement permet d’éviter les fuites matérielles et de préserver la cohérence des chemins d’accès au cours de la modification et de l’exécution.

Lorsqu’un [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) ne peut pas être utilisé et qu’un matériau doit être instancié, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) peut être utilisé comme suit :

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

Si plusieurs objets ont besoin de la propriété de l’instance de matériau, il est préférable de prendre une propriété explicite pour le suivi de référence. (Une interface facultative appelée [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) existe pour faciliter la propriété.) Voici un exemple d’utilisation :

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

Pour plus d’informations, consultez l’exemple d’utilisation présenté dans le [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportement.

## <a name="see-also"></a>Voir aussi

* [Nuanceur standard MRTK](mrtk-standard-shader.md)
