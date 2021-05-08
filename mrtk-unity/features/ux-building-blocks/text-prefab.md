---
title: TextPrefab
description: Vue d’ensemble de TextPrefab dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489289"
---
# <a name="text-prefab"></a><span data-ttu-id="89542-104">Prefab texte</span><span class="sxs-lookup"><span data-stu-id="89542-104">Text prefab</span></span>

<span data-ttu-id="89542-105">Ces prefabs sont optimisés pour la qualité de rendu dans Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="89542-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="89542-106">Pour plus d’informations, consultez le [texte de l’instruction Unity](/windows/mixed-reality/text-in-unity) sur le centre de développement Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="89542-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="89542-107">Prefabs</span><span class="sxs-lookup"><span data-stu-id="89542-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="89542-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="89542-108">3DTextPrefab</span></span>

<span data-ttu-id="89542-109">Prefab de texte 3D (éléments multimédias/MRTK/Kit de développement logiciel/StandardAssets/Prefabs/texte) avec un facteur de mise à l’échelle optimisé à une distance de 2 mètres.</span><span class="sxs-lookup"><span data-stu-id="89542-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="89542-110">(Veuillez lire les instructions ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="89542-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="89542-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="89542-111">UITextPrefab</span></span>

<span data-ttu-id="89542-112">Prefab de texte de l’interface utilisateur (éléments multimédias/MRTK/Kit de développement logiciel/StandardAssets/Prefabs/Text) avec le facteur d’échelle optimisé à une distance de 2 mètres.</span><span class="sxs-lookup"><span data-stu-id="89542-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="89542-113">(Veuillez lire les instructions ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="89542-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="89542-114">Polices</span><span class="sxs-lookup"><span data-stu-id="89542-114">Fonts</span></span>

<span data-ttu-id="89542-115">Polices Open source (Assets/MRTK/Core/StandardAssets/Fonts) incluses dans le kit de ressources de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="89542-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89542-116">Text Prefab utilise la police Open source’Selawik'.</span><span class="sxs-lookup"><span data-stu-id="89542-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="89542-117">Pour utiliser le texte Prefab avec une autre police, importez le fichier de polices et suivez les instructions ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="89542-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="89542-118">L’exemple ci-dessous montre comment utiliser la police « Segoe UI » avec du texte Prefab.</span><span class="sxs-lookup"><span data-stu-id="89542-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![Importation d’Segoe UI fichier de police](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="89542-120">Affectez une texture de police à la matière 3DTextSegoeUI. mat.</span><span class="sxs-lookup"><span data-stu-id="89542-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![Affecter une texture de police](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="89542-122">Sur 3DTextSegoeUI. mat, sélectionnez le nuanceur Custom/3DTextShader. Shader.</span><span class="sxs-lookup"><span data-stu-id="89542-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![Assignation du nuanceur](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="89542-124">Assignez Segoe UI la police et le matériau 3DTextSegoeUI aux composants de texte dans le prefabs.</span><span class="sxs-lookup"><span data-stu-id="89542-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![Attribution d’un fichier de polices et d’un matériau](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="89542-126">Utilisation des polices dans Unity</span><span class="sxs-lookup"><span data-stu-id="89542-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="89542-127">Lorsque vous ajoutez un nouveau TextMesh 3D à une scène dans Unity, deux problèmes sont visibles.</span><span class="sxs-lookup"><span data-stu-id="89542-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="89542-128">Un, la police est très grande et deux, la police semble très floue.</span><span class="sxs-lookup"><span data-stu-id="89542-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="89542-129">Il est également intéressant de noter que la valeur de la taille de police par défaut est définie sur zéro dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="89542-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="89542-130">Le remplacement de cette valeur zéro par 13 n’affiche aucune différence de taille, car 13 est en fait la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="89542-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="89542-131">Unity suppose que tous les nouveaux éléments ajoutés à une scène ont une taille de 1 unité Unity, ou une échelle de transformation 100%, qui se traduit par environ 1 mètre sur le HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89542-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="89542-132">Dans le cas des polices, le cadre englobant d’un TextMesh 3D est fourni, par défaut à environ 1 mètre en hauteur.</span><span class="sxs-lookup"><span data-stu-id="89542-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="89542-133">Échelle de police et tailles de police</span><span class="sxs-lookup"><span data-stu-id="89542-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="89542-134">La plupart des concepteurs visuels utilisent des points pour définir les tailles de police dans le monde réel, ainsi que leurs programmes de conception.</span><span class="sxs-lookup"><span data-stu-id="89542-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="89542-135">Il y a environ 2835 (2 834.645666399962) points dans 1 mètre.</span><span class="sxs-lookup"><span data-stu-id="89542-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="89542-136">En fonction de la conversion du système en point à 1 mètre et de la taille de police TextMesh par défaut de l’unité Unity de 13, la simple mathématique de 13 divisée par 2835 est égale à 0,0046 (0.004586111116) fournit une bonne échelle standard pour commencer, même si certaines peuvent souhaiter aller jusqu’à 0,005.</span><span class="sxs-lookup"><span data-stu-id="89542-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="89542-137">Dans les deux cas, la mise à l’échelle de l’objet ou du conteneur de texte à ces valeurs n’autorise pas uniquement la conversion de 1:1 de tailles de police d’un programme de conception, mais fournit également une norme pour assurer la cohérence dans toute l’application ou le jeu.</span><span class="sxs-lookup"><span data-stu-id="89542-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="89542-138">Texte d'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="89542-138">UI Text</span></span>

<span data-ttu-id="89542-139">Quand vous ajoutez un élément de texte basé sur une interface utilisateur ou un canevas à une scène, la disparité de taille est encore plus importante.</span><span class="sxs-lookup"><span data-stu-id="89542-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="89542-140">Les différences entre les deux tailles sont d’environ 1000%, ce qui fait passer le facteur d’échelle pour les composants de texte basés sur l’interface utilisateur à 0,00046 (0.0004586111116 est exact) ou 0,0005 pour la valeur arrondie.</span><span class="sxs-lookup"><span data-stu-id="89542-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="89542-141">**Exclusion de responsabilité**: la valeur par défaut de toute police peut être appliquée par la taille de la texture de cette police ou la manière dont la police a été importée dans Unity.</span><span class="sxs-lookup"><span data-stu-id="89542-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="89542-142">Ces tests ont été exécutés en fonction de la police Arial par défaut dans Unity, ainsi que d’une autre police importée.</span><span class="sxs-lookup"><span data-stu-id="89542-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![Taille de police avec facteurs de mise à l’échelle](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="89542-144">Text3DSelawik. mat</span><span class="sxs-lookup"><span data-stu-id="89542-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="89542-145">Matériel pour 3DTextPrefab avec prise en charge de l’occlusion.</span><span class="sxs-lookup"><span data-stu-id="89542-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="89542-146">Nécessite 3DTextShader. Shader</span><span class="sxs-lookup"><span data-stu-id="89542-146">Requires 3DTextShader.shader</span></span>

![Matériau de police par défaut et matériau 3DTextSegoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="89542-148">Text3DShader. Shader</span><span class="sxs-lookup"><span data-stu-id="89542-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="89542-149">Nuanceur pour 3DTextPrefab avec prise en charge de l’occlusion.</span><span class="sxs-lookup"><span data-stu-id="89542-149">Shader for 3DTextPrefab with occlusion support.</span></span>