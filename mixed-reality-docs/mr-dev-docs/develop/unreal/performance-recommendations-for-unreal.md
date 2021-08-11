---
title: Recommandations sur les performances pour Unreal
description: Découvrez comment obtenir les meilleures performances de vos applications de réalité mixte avec nos paramètres de projet Unreal recommandés.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, performances, optimisation, paramètres, documentation
ms.openlocfilehash: 83d3f5ba95f313f286d6d5266c846a7c2dd6d84ce8685bdb3783fa5109645eb5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216442"
---
# <a name="performance-recommendations-for-unreal"></a>Recommandations sur les performances pour Unreal

Unreal Engine comporte plusieurs fonctionnalités capables d’augmenter les performances des applications, toutes basées sur la description présentée dans [Recommandations sur les performances pour la réalité mixte](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Avant de continuer, nous vous encourageons à vous informer sur les goulots d’étranglement des applications, l’analyse et le profilage des applications de réalité mixte, ainsi que les correctifs des performances généraux.

## <a name="recommended-unreal-project-settings"></a>Paramètres de projet Unreal recommandés

Vous trouverez chacun des paramètres suivants dans **Edit > Project Settings**.

1. Utilisation du convertisseur VR mobile :
    * Faites défiler la page jusqu’à la section **Project**, sélectionnez **Target Hardware**, puis définissez la plateforme cible sur **Mobile/Tablet**.

![Définition de la cible mobile](images/unreal/performance-recommendations-img-01.png)

2. Utilisation du renderer Forward : 
    * Le renderer Forward est bien mieux adapté à la réalité mixte que le pipeline de rendu différé par défaut en raison du nombre de fonctionnalités qui peuvent être désactivées individuellement. 
    * Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).

![Rendu Forward](images/unreal/performance-recommendations-img-04.png)

3. En utilisant la multivue mobile :
    * Faites défiler la page jusqu’à la section **Engine**, sélectionnez **Rendering**, développez la section **VR** et cochez les cases **Instanced Stereo** et **Mobile Multi-View**. La case Mobile HDR doit être décochée.

![Paramètres de rendu VR](images/unreal/performance-recommendations-img-03.png)

4. **[OpenXR uniquement]** Vérifiez que la **valeur par défaut** ou **D3D12** est la valeur de **RHI par défaut** sélectionnée :
    * La sélection de **D3D11** aura un impact négatif sur les performances en raison de la plateforme effectuant une passe de rendu supplémentaire. **D3D12** doit permettre d’améliorer les performances de rendu, en plus d’éviter la passe de rendu supplémentaire.

![RHI par défaut](images/unreal/performance-recommendations-img-09.png)

5. Désactivation du brouillard au niveau des vertex : 
    * Le brouillard au niveau des vertex applique des calculs de brouillard à chaque vertex d’un polygone, puis interpole les résultats sur la face du polygone. Si votre jeu n’utilise pas de brouillard, nous vous recommandons de désactiver le brouillard au niveau des vertex pour augmenter les performances de l’ombrage.

![Options de brouillard au niveau des vertex](images/unreal/performance-recommendations-img-05.png)

6. Désactivation de l’élimination de l’occlusion :
    * Faites défiler la page jusqu’à la section **Engine**, sélectionnez **Rendering**, développez la section **Culling**, puis décochez la case **Occlusion Culling**.
        + Si vous avez besoin d’éliminer des occlusions pour une scène précise en cours de rendu, nous vous recommandons de cocher la case **Support Software Occlusion Culling** dans **Engine > Rendering**. Unreal va effectuer le travail sur le processeur et éviter les requêtes d’occlusion du GPU, dont les performances sont faibles sur HoloLens 2.
    * L’élimination des occlusions sur le GPU d’appareils mobiles est lente. En général, vous souhaitez que le GPU se charge principalement du rendu. Si vous estimez que l’occlusion améliorera les performances, essayez d’activer l’occlusion logicielle à la place. 

> [!NOTE]
> L’activation de l’occlusion logicielle peut nuire aux performances si vous êtes déjà lié au processeur par un grand nombre d’appels de dessin.

![Désactivation de l’élimination de l’occlusion](images/unreal/performance-recommendations-img-02.png)

7. Désactivation de la passe du stencil de profondeur personnalisé :
    * La désactivation du stencil de profondeur personnalisé demande une passe supplémentaire, ce qui signifie qu’il est lent. La translucidité est également lente sur Unreal. Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).

![Stencil de profondeur](images/unreal/performance-recommendations-img-06.png)

8. Réduction des cartes d’ombre en cascade (CSM) : 
    * Le fait de réduire le nombre de cartes d’ombre améliore les performances. En règle générale, vous devez affecter la valeur 1 à la propriété, sauf si une perte de qualité est visible. 

![Cartes d’ombre en cascade](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>Paramètres facultatifs

> [!NOTE]
> Les paramètres suivants peuvent améliorer les performances, mais au prix de la désactivation de certaines fonctionnalités. Utilisez ces paramètres uniquement si vous êtes sûr que vous n’avez pas besoin des fonctionnalités en question.

1. Réduction des permutations de nuanceurs sur mobile
    * Si vos lumières ne se déplacent pas indépendamment de la caméra, vous pouvez choisir sans problème la valeur 0 pour la propriété. L’avantage principal est la possibilité pour Unreal d’éliminer plusieurs permutations de nuanceurs, accélérant ainsi la compilation des nuanceurs.

![Réduction des permutations de nuanceurs sur mobile](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>Voir aussi

* [Recommandations en matière de performances sur mobile pour Unreal Engine]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)