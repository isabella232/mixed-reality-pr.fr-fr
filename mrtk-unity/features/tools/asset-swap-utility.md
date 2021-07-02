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
# <a name="asset-swap-utility"></a>Utilitaire d’échange de ressources

La recherche et le remplacement sont omniprésents quand vous travaillez dans des outils de création de texte et de contenu. Lorsque vous devez échanger de nombreux éléments multimédias au sein d’une scène Unity, c’est là que le [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) et l’éditeur [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) peuvent prêter une main. L’utilitaire est inclus dans le `Microsoft.MixedReality.Toolkit.Unity.Tools` Package.

Le `AssetSwapUtility` enregistre toutes les actions de recherche et de remplacement en tant que ScriptableObject, de sorte qu’il est Trival d’échanger des « thèmes » d’échange ou d’enregistrer des « thèmes » pour une utilisation ultérieure.

## <a name="swapping-assets"></a>Échange de ressources

La permutation des ressources est facile une fois que vous avez créé un `AssetSwapCollection` . Nous allons illustrer l’utilisation en échangeant deux cubes rouges avec deux sphères bleues dans une scène. Tout d’abord, ajoutez deux cubes rouges à votre scène qui utilisent le cube Unity par défaut et le `MRTK_Standard_Red` matériau.

pour créer un `AssetSwapCollection` , accédez à la **réalité mixte Shared Computer Toolkit > utilitaires > créer un regroupement d’échange de ressources**. Avec l' `AssetSwapCollection` option remplir les propriétés comme indiqué dans l’image ci-dessous :

![Collection d’échange de ressources dans l’éditeur Unity](images/asset-swap-img-01.png)

Ensuite, sélectionnez « bleu sphères » dans la liste déroulante « Thème sélectionné » et appuyez sur « appliquer ». Tous les cubes rouges de votre scène doivent être remplacés par des sphères bleues.

![Regroupement d’échange de ressources dans l’éditeur Unity avec le thème sélectionné mis en surbrillance](images/asset-swap-img-02.png)

Dans cet exemple, nous avons effectué un remplacement complet de la scène, mais vous pouvez remplacer certaines parties de votre scène en modifiant le « mode de sélection ». Vous pouvez également basculer vers les cubes Red en sélectionnant « cubes rouges » dans la liste déroulante « Thème sélectionné », puis en appuyant sur « appliquer ».

> [!NOTE]
> Il est possible d’échanger n’importe quel type de ressource, comme des fichiers audio, des polices, des prefabs, etc. Le `AssetSwapUtility` effectue quelques vérifications de la santé pour s’assurer que vous permutez vers des types similaires.
