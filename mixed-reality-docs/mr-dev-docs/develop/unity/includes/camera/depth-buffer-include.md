---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110631362"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La [boîte de dialogue de configuration de MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) tente de définir des paramètres de mémoire tampon de profondeur pour le kit de développement logiciel (SDK) XR et le WSA hérité, mais il est judicieux de vérifier ces onglets et de vérifier les paramètres dans Unity.

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Pour définir si votre application Unity fournira un tampon de profondeur à Windows :

1. Accédez à **modifier**  >  les **paramètres du projet**  >  **XR gestion du plug-in** et vérifiez que l’élément de menu est développé.
2. Cliquez sur l’élément de menu correspondant au runtime XR que vous avez choisi, Windows Mixed Reality ou OpenXR. En outre, assurez-vous que la plateforme de génération correcte est sélectionnée, sous forme d’onglets pour Windows standalone et plateforme Windows universelle sont disponibles.
3. Pour activer et configurer :
    1. Pour OpenXR, sélectionnez un format de profondeur ou « aucun » dans la liste déroulante **mode de soumission de profondeur** .
    2. Pour Windows Mixed Reality, cochez ou décochez la case **Shared Depth buffer** . Ensuite, sélectionnez un format dans la liste déroulante format de la **mémoire tampon de profondeur** .

![Paramètres de profondeur du plug-in Windows XR paramètres de ](../../images/xrsdk-winxr-depth.png)
 ![ profondeur OpenXR](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Il est généralement recommandé d’utiliser des mémoires tampons de profondeur 16 bits pour améliorer les performances. Toutefois, si vous utilisez le format de profondeur 16 bits, les effets requis pour la mémoire tampon des stencils (comme certains panneaux défilant de l’interface utilisateur Unity) ne fonctionneront pas, car [Unity ne crée pas de tampon de stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) dans ce paramètre. Si vous sélectionnez le *format de profondeur 24 bits* , vous créez généralement une [mémoire tampon de stencil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , le cas échéant, sur la plateforme graphique de point de terminaison.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Pour définir si votre application Unity fournira un tampon de profondeur à Windows :

1. Accédez à **modifier** les  >  **paramètres du projet**  >  **lecteur**  >  **plateforme Windows universelle onglet**  >  **paramètres XR**.
2. Développez l’élément du **Kit de développement logiciel (SDK) Windows Mixed Reality** .
3. Activez ou désactivez la case à cocher **activer le partage de tampons de profondeur** . L’option Activer le partage de tampons de profondeur est activée par défaut dans les nouveaux projets, mais elle a peut-être été désactivée par défaut dans les projets plus anciens.

![Paramètres de profondeur des XR hérités](../../images/wmr-depth.png)

Une mémoire tampon de profondeur peut améliorer la qualité visuelle tant que Windows peut mapper avec précision les valeurs de profondeur par pixel normalisées dans votre tampon de profondeur à des distances exprimées en mètres, à l’aide des plans proches et éloignés que vous avez définis dans Unity sur la caméra principale. Si votre rendu passe les valeurs de profondeur des poignées de manière classique, vous devez généralement être précis ici, bien que le rendu translucide passe l’écriture dans le tampon de profondeur pendant que l’affichage aux pixels de couleur existants peut confondre la reprojection.  Si vous savez que vos passes de rendu conservent un grand nombre de pixels de profondeur finale avec des valeurs de profondeur inexactes, vous obtiendrez probablement une meilleure qualité visuelle en désactivant l’option « Activer le partage de mémoire tampon de profondeur ».

> [!NOTE]
> Il est généralement recommandé d’utiliser des mémoires tampons de profondeur 16 bits pour améliorer les performances. Toutefois, si vous utilisez le format de profondeur 16 bits, les effets requis pour la mémoire tampon des stencils (comme certains panneaux défilant de l’interface utilisateur Unity) ne fonctionneront pas, car [Unity ne crée pas de tampon de stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) dans ce paramètre. Si vous sélectionnez le *format de profondeur 24 bits* , vous créez généralement une [mémoire tampon de stencil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , le cas échéant, sur la plateforme graphique de point de terminaison.