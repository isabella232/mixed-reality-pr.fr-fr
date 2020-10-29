---
title: Recommandations sur les performances pour Unreal
description: Recommandations pour des performances optimales pour les applications de réalité mixte dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, performances, optimisation, paramètres, documentation
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91697236"
---
# <a name="performance-recommendations-for-unreal"></a>Recommandations sur les performances pour Unreal

## <a name="overview"></a>Vue d’ensemble

Cet article s’appuie sur les [recommandations sur les performances pour la réalité mixte](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), mais il se concentre sur des fonctionnalités propres à Unreal Engine. Avant de continuer, nous vous encourageons à vous informer sur les goulots d’étranglement des applications, l’analyse et le profilage des applications de réalité mixte, ainsi que les correctifs des performances généraux.

## <a name="recommended-unreal-project-settings"></a>Paramètres de projet Unreal recommandés
Vous trouverez chacun des paramètres suivants dans **Edit > Project Settings** .

1. Utilisation du convertisseur VR mobile :
    * Faites défiler la page jusqu’à la section **Project** , sélectionnez **Target Hardware** , puis définissez la plateforme cible sur **Mobile/Tablet** .

![Définition de la cible mobile](images/unreal/performance-recommendations-img-01.png)

2. Utilisation du renderer Forward : 
    * Cette fonctionnalité est bien meilleure pour la réalité mixte que le pipeline de rendu Deferred par défaut. Cela s’explique principalement par le nombre de fonctionnalités qui peuvent être désactivées individuellement. 
    * Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).

![Rendu Forward](images/unreal/performance-recommendations-img-04.png)

3. Désactivation du brouillard au niveau des vertex : 
    * Le brouillard au niveau des vertex applique des calculs de brouillard à chaque vertex d’un polygone, puis interpole les résultats sur la face du polygone. En l’absence de brouillard dans votre jeu, choisissez ce paramètre pour désactiver le brouillard et améliorer les performances d’ombrage.

![Options de brouillard au niveau des vertex](images/unreal/performance-recommendations-img-05.png)

4. Désactivation de l’élimination de l’occlusion :
    * Faites défiler la page jusqu’à la section **Engine** , sélectionnez **Rendering** , développez la section **Culling** , puis décochez la case **Occlusion Culling** .
        + Si vous avez besoin d’éliminer des occlusions pour une scène précise en cours de rendu, nous vous recommandons de cocher la case **Support Software Occlusion Culling** dans **Engine > Rendering** . Ceci permet à Unreal d’effectuer le travail sur le processeur et d’éviter les requêtes d’occlusion du GPU, dont les performances sont faibles sur HoloLens 2.
    * L’élimination des occlusions sur le GPU d’appareils mobiles est lente. En général, vous souhaitez que le GPU se charge principalement du rendu. Si vous estimez que l’occlusion améliorera les performances, essayez d’activer l’occlusion logicielle à la place. Notez que l’activation de l’occlusion logicielle peut nuire aux performances si vous êtes déjà lié au processeur par un grand nombre d’appels de dessin.

![Désactivation de l’élimination de l’occlusion](images/unreal/performance-recommendations-img-02.png)

    
5. Désactivation du stencil de profondeur :
    * Cette fonctionnalité nécessite une passe supplémentaire, ce qui signifie qu’elle est lente. La translucidité est également lente sur Unreal. Vous trouverez plus d’informations dans la [documentation d’Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).

![Stencil de profondeur](images/unreal/performance-recommendations-img-06.png)

6. En utilisant la multivue mobile :
    * Faites défiler la page jusqu’à la section **Engine** , sélectionnez **Rendering** , développez la section **VR** et cochez les cases **Instanced Stereo** et **Mobile Multi-View** . La case Mobile HDR doit être décochée.

![Paramètres de rendu VR](images/unreal/performance-recommendations-img-03.png)

7. Réduction des cartes d’ombre en cascade (CSM) : 
    * Le fait de réduire le nombre de cartes d’ombre améliore les performances. En général, définissez une valeur de 1 sauf si vous constatez une perte de qualité visible. 

![Cartes d’ombre en cascade](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>Paramètres facultatifs

> [!NOTE]
> Les paramètres suivants peuvent améliorer les performances, mais au prix de la désactivation de certaines fonctionnalités. Utilisez ces paramètres uniquement si vous êtes sûr que vous n’avez pas besoin des fonctionnalités en question.

1. Réduction des permutations de nuanceurs sur mobile
    * Si vos lumières ne se déplacent pas indépendamment de la caméra, vous pouvez choisir en toute sécurité la valeur 0. L’avantage principal est la possibilité pour Unreal d’éliminer plusieurs permutations de nuanceurs, accélérant ainsi la compilation des nuanceurs.

![Réduction des permutations de nuanceurs sur mobile](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>Voir aussi
* [Recommandations en matière de performances sur mobile pour Unreal Engine]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)