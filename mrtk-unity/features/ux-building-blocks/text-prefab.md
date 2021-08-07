---
title: Préfabriqué de texte
description: Vue d’ensemble de TextPrefab dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, TMP,
ms.openlocfilehash: 1969bc9e3054fec509e9f7d536cbfe4b97e43563e26ba5476601e78e65ad24f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209056"
---
# <a name="text-prefab"></a>Préfabriqué de texte

Ces prefabs sont optimisés pour la qualité de rendu dans Windows Mixed Reality. pour plus d’informations, consultez le [texte de l’instruction unity](/windows/mixed-reality/text-in-unity) sur Microsoft Windows Centre de développement.

## <a name="prefabs"></a>Prefabs

### <a name="3dtextprefab"></a>3DTextPrefab

Prefab de texte 3D (éléments multimédias/MRTK/Kit de développement logiciel/StandardAssets/Prefabs/texte) avec un facteur de mise à l’échelle optimisé à une distance de 2 mètres. (Veuillez lire les instructions ci-dessous)

### <a name="uitextprefab"></a>UITextPrefab

Prefab de texte de l’interface utilisateur (éléments multimédias/MRTK/Kit de développement logiciel/StandardAssets/Prefabs/Text) avec le facteur d’échelle optimisé à une distance de 2 mètres. (Veuillez lire les instructions ci-dessous)

## <a name="fonts"></a>Polices

polices Open source (assets/MRTK/Core/StandardAssets/fonts) incluses dans la réalité mixte Shared Computer Toolkit.

> [!IMPORTANT]
> Text Prefab utilise la police Open source’Selawik'. Pour utiliser le texte Prefab avec une autre police, importez le fichier de polices et suivez les instructions ci-dessous. L’exemple ci-dessous montre comment utiliser la police « Segoe UI » avec du texte Prefab.

![Importation d’Segoe UI fichier de police](../images/text-prefab/TextPrefabInstructions01.png)

1. Affectez une texture de police à la matière 3DTextSegoeUI. mat.

    ![Affecter une texture de police](../images/text-prefab/TextPrefabInstructions02.png)

1. Sur 3DTextSegoeUI. mat, sélectionnez le nuanceur Custom/3DTextShader. Shader.

    ![Assignation du nuanceur](../images/text-prefab/TextPrefabInstructions03.png)

1. Assignez Segoe UI la police et le matériau 3DTextSegoeUI aux composants de texte dans le prefabs.

    ![Attribution d’un fichier de polices et d’un matériau](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Utilisation des polices dans Unity

Lorsque vous ajoutez un nouveau TextMesh 3D à une scène dans Unity, deux problèmes sont visibles. Un, la police est très grande et deux, la police semble très floue. Il est également intéressant de noter que la valeur de la taille de police par défaut est définie sur zéro dans l’inspecteur. Le remplacement de cette valeur zéro par 13 n’affiche aucune différence de taille, car 13 est en fait la valeur par défaut.

Unity suppose que tous les nouveaux éléments ajoutés à une scène ont une taille de 1 unité Unity, ou une échelle de transformation 100%, qui se traduit par environ 1 mètre sur la HoloLens. Dans le cas des polices, le cadre englobant d’un TextMesh 3D est fourni, par défaut à environ 1 mètre en hauteur.

### <a name="font-scale-and-font-sizes"></a>Échelle de police et tailles de police

La plupart des concepteurs visuels utilisent des points pour définir les tailles de police dans le monde réel, ainsi que leurs programmes de conception. Il y a environ 2835 (2 834.645666399962) points dans 1 mètre. En fonction de la conversion du système en point à 1 mètre et de la taille de police TextMesh par défaut de l’unité Unity de 13, la simple mathématique de 13 divisée par 2835 est égale à 0,0046 (0.004586111116) fournit une bonne échelle standard pour commencer, même si certaines peuvent souhaiter aller jusqu’à 0,005.

Dans les deux cas, la mise à l’échelle de l’objet ou du conteneur de texte à ces valeurs n’autorise pas uniquement la conversion de 1:1 de tailles de police d’un programme de conception, mais fournit également une norme pour assurer la cohérence dans toute l’application ou le jeu.

### <a name="ui-text"></a>Texte d'interface utilisateur

Quand vous ajoutez un élément de texte basé sur une interface utilisateur ou un canevas à une scène, la disparité de taille est encore plus importante. Les différences entre les deux tailles sont d’environ 1000%, ce qui fait passer le facteur d’échelle pour les composants de texte basés sur l’interface utilisateur à 0,00046 (0.0004586111116 est exact) ou 0,0005 pour la valeur arrondie.

**Exclusion de responsabilité**: la valeur par défaut de toute police peut être appliquée par la taille de la texture de cette police ou la manière dont la police a été importée dans Unity. Ces tests ont été exécutés en fonction de la police Arial par défaut dans Unity, ainsi que d’une autre police importée.

![Taille de police avec facteurs de mise à l’échelle](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik. mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

Matériel pour 3DTextPrefab avec prise en charge de l’occlusion. Nécessite 3DTextShader. Shader

![Matériau de police par défaut et matériau 3DTextSegoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader. Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

Nuanceur pour 3DTextPrefab avec prise en charge de l’occlusion.
