---
ms.openlocfilehash: 924190e10de100fc84795344a6cf676f318d04cec26793af96d03a3cb7cb5f78
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212219"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La [boîte de dialogue de configuration de MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) tente de définir des paramètres de mémoire tampon de profondeur pour le kit de développement logiciel (SDK) XR et le WSA hérité, mais il est judicieux de vérifier ces onglets et de vérifier les paramètres dans Unity.

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Pour définir si votre application Unity fournit une mémoire tampon de profondeur pour Windows :

1. accédez à **modifier**  >  **Project Paramètres**  >  **gestion du Plug-in XR** et assurez-vous que l’élément de menu est développé.
2. cliquez sur l’élément de menu correspondant au runtime XR que vous avez choisi, Windows Mixed Reality ou OpenXR. en outre, assurez-vous que la plateforme de génération correcte est sélectionnée, sous la forme d’onglets pour Windows autonome et plateforme Windows universelle sont disponibles.
3. Pour activer et configurer :
    1. Pour OpenXR, sélectionnez un format de profondeur ou « aucun » dans la liste déroulante **mode de soumission de profondeur** .
    2. pour Windows Mixed Reality, activez ou désactivez la case à cocher **mémoire tampon de profondeur partagée** . Ensuite, sélectionnez un format dans la liste déroulante format de la **mémoire tampon de profondeur** .

![Windows Paramètres de profondeur du plug-in XR ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR paramètres de profondeur](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Il est généralement recommandé d’utiliser des mémoires tampons de profondeur 16 bits pour améliorer les performances. Toutefois, si vous utilisez le format de profondeur 16 bits, les effets requis pour la mémoire tampon des stencils (comme certains panneaux défilant de l’interface utilisateur Unity) ne fonctionneront pas, car [Unity ne crée pas de tampon de stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) dans ce paramètre. Si vous sélectionnez le *format de profondeur 24 bits* , vous créez généralement une [mémoire tampon de stencil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , le cas échéant, sur la plateforme graphique de point de terminaison.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Pour définir si votre application Unity fournit une mémoire tampon de profondeur pour Windows :

1. accédez à **Edit**  >  **Project Paramètres**  >  **Player**  >  **plateforme Windows universelle onglet**  >  **XR Paramètres**.
2. développez l’élément **SDK Windows Mixed Reality** .
3. Activez ou désactivez la case à cocher **activer le partage de tampons de profondeur** . L’option Activer le partage de tampons de profondeur est activée par défaut dans les nouveaux projets, mais elle a peut-être été désactivée par défaut dans les projets plus anciens.

![Paramètres de profondeur des XR hérités](../../images/wmr-depth.png)

une mémoire tampon de profondeur peut améliorer la qualité visuelle tant que Windows pouvez mapper avec précision les valeurs de profondeur par pixel normalisées dans votre mémoire tampon de profondeur à des distances exprimées en mètres, à l’aide des plans proches et éloignés que vous avez définis dans unity sur la caméra principale. Si votre rendu passe les valeurs de profondeur des poignées de manière classique, vous devez généralement être précis ici, bien que le rendu translucide passe l’écriture dans le tampon de profondeur pendant que l’affichage aux pixels de couleur existants peut confondre la reprojection.  Si vous savez que vos passes de rendu conservent un grand nombre de pixels de profondeur finale avec des valeurs de profondeur inexactes, vous obtiendrez probablement une meilleure qualité visuelle en désactivant l’option « Activer le partage de mémoire tampon de profondeur ».

> [!NOTE]
> Il est généralement recommandé d’utiliser des mémoires tampons de profondeur 16 bits pour améliorer les performances. Toutefois, si vous utilisez le format de profondeur 16 bits, les effets requis pour la mémoire tampon des stencils (comme certains panneaux défilant de l’interface utilisateur Unity) ne fonctionneront pas, car [Unity ne crée pas de tampon de stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) dans ce paramètre. Si vous sélectionnez le *format de profondeur 24 bits* , vous créez généralement une [mémoire tampon de stencil de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) , le cas échéant, sur la plateforme graphique de point de terminaison.