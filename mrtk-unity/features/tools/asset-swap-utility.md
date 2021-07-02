---
title: Utilitaire d’échange de ressources
description: Documentation sur l’utilisation de l’utilitaire Asset swap dans MRTK pour Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176159"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="d2b63-104">Utilitaire d’échange de ressources</span><span class="sxs-lookup"><span data-stu-id="d2b63-104">Asset swap utility</span></span>

<span data-ttu-id="d2b63-105">La recherche et le remplacement sont omniprésents quand vous travaillez dans des outils de création de texte et de contenu.</span><span class="sxs-lookup"><span data-stu-id="d2b63-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="d2b63-106">Lorsque vous devez échanger de nombreux éléments multimédias au sein d’une scène Unity, c’est là que le [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) et l’éditeur [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) peuvent prêter une main.</span><span class="sxs-lookup"><span data-stu-id="d2b63-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="d2b63-107">L’utilitaire est inclus dans le `Microsoft.MixedReality.Toolkit.Unity.Tools` Package.</span><span class="sxs-lookup"><span data-stu-id="d2b63-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="d2b63-108">Le `AssetSwapUtility` enregistre toutes les actions de recherche et de remplacement en tant que ScriptableObject, de sorte qu’il est Trival d’échanger des « thèmes » d’échange ou d’enregistrer des « thèmes » pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d2b63-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="d2b63-109">Échange de ressources</span><span class="sxs-lookup"><span data-stu-id="d2b63-109">Swapping assets</span></span>

<span data-ttu-id="d2b63-110">La permutation des ressources est facile une fois que vous avez créé un `AssetSwapCollection` .</span><span class="sxs-lookup"><span data-stu-id="d2b63-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="d2b63-111">Nous allons illustrer l’utilisation en échangeant deux cubes rouges avec deux sphères bleues dans une scène.</span><span class="sxs-lookup"><span data-stu-id="d2b63-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="d2b63-112">Tout d’abord, ajoutez deux cubes rouges à votre scène qui utilisent le cube Unity par défaut et le `MRTK_Standard_Red` matériau.</span><span class="sxs-lookup"><span data-stu-id="d2b63-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="d2b63-113">pour créer un `AssetSwapCollection` , accédez à la **réalité mixte Shared Computer Toolkit > utilitaires > créer un regroupement d’échange de ressources**.</span><span class="sxs-lookup"><span data-stu-id="d2b63-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="d2b63-114">Avec l' `AssetSwapCollection` option remplir les propriétés comme indiqué dans l’image ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d2b63-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Collection d’échange de ressources dans l’éditeur Unity](images/asset-swap-img-01.png)

<span data-ttu-id="d2b63-116">Ensuite, sélectionnez « bleu sphères » dans la liste déroulante « Thème sélectionné » et appuyez sur « appliquer ».</span><span class="sxs-lookup"><span data-stu-id="d2b63-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="d2b63-117">Tous les cubes rouges de votre scène doivent être remplacés par des sphères bleues.</span><span class="sxs-lookup"><span data-stu-id="d2b63-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Regroupement d’échange de ressources dans l’éditeur Unity avec le thème sélectionné mis en surbrillance](images/asset-swap-img-02.png)

<span data-ttu-id="d2b63-119">Dans cet exemple, nous avons effectué un remplacement complet de la scène, mais vous pouvez remplacer certaines parties de votre scène en modifiant le « mode de sélection ».</span><span class="sxs-lookup"><span data-stu-id="d2b63-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="d2b63-120">Vous pouvez également basculer vers les cubes Red en sélectionnant « cubes rouges » dans la liste déroulante « Thème sélectionné », puis en appuyant sur « appliquer ».</span><span class="sxs-lookup"><span data-stu-id="d2b63-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b63-121">Il est possible d’échanger n’importe quel type de ressource, comme des fichiers audio, des polices, des prefabs, etc. Le `AssetSwapUtility` effectue quelques vérifications de la santé pour s’assurer que vous permutez vers des types similaires.</span><span class="sxs-lookup"><span data-stu-id="d2b63-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>
