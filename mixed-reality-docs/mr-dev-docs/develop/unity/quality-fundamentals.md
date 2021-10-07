---
title: Bases de la qualité
description: Découvrez les principes de base de la conception d’applications de réalité mixte.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: notions de base sur la qualité, étude de cas, projet, exemple, MRTK, réalité mixte Shared Computer Toolkit, unity, exemples d’applications, exemples d’applications, open source, Microsoft Store, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 69c6a55b95937c0c6af4920f6ffe0929eebe76ee
ms.sourcegitcommit: 82f7db75d8ecc7ac89c76b0db504126cbcb8f16d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129647529"
---
# <a name="quality-fundamentals"></a>Bases de la qualité

les notions de base de la qualité sont une application HoloLens 2 qui illustre les principes fondamentaux de la création d’une expérience de réalité mixte.  Au lieu d’apprendre à se familiariser avec les problèmes de qualité dans la réalité mixte, nous pouvons maintenant rencontrer des problèmes et des solutions d’environnement, de conception et de performances communs, en sélectionnant les options fournies dans l’application.

Pour télécharger et installer l’application, accédez à la page de téléchargement de l’application :

> [!div class="nextstepaction"]
> [Bases de la qualité](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Page d’accueil des notions de base de la qualité](images\qf-homepage.jpg)

Dans cet exemple d’application, nous allons découvrir les éléments suivants :

>[!div class = "checklist"]
> * [e/s de périphérique et environnement](#device-io-and-environment): comment les facteurs environnementaux peuvent affecter les performances de HoloLens.
> * [Ancres spatiales](#anchor-fundamentals): alignement des hologrammes sur un espace physique à l’aide d’ancres spatiales.
> * [Stabilité et fidélité holographiques](#stability-and-fidelity): Explorez les techniques pour aider à améliorer la stabilité et la fidélité des hologrammes.
> * [notions de base des ressources 3D](#3d-asset-fundamentals): optimisation des ressources 3D pour maintenir une fidélité visuelle élevée. 

## <a name="device-io-and-environment"></a>E/s de périphérique et environnement

Démarrez l’application de notions de base de la qualité sur HoloLens. Une fois la page d’accueil de l’application affichée, sélectionnez **e/s de périphérique et environnement**.  nous allons découvrir comment les capteurs HoloLens et l’environnement environnant affectent le mappage spatial, le suivi et le placement des hologrammes. 

### <a name="surfaces"></a>Surfaces

les miroirs ou les surfaces avec des finitions mises en miroir peuvent confondre les capteurs HoloLens sur la forme de l’objet.  Les objets reflétés sur la surface peuvent être interprétés par l’appareil comme un environnement changeant, ce qui peut entraîner la perte du suivi de l’appareil.  si les surfaces en miroir sont à l’origine de problèmes pour HoloLens, envisagez d’ajouter un écran ou des aveugles fermables.

pour plus d’informations, consultez [surfaces in a space](/hololens/hololens-environment-considerations#surfaces-in-a-space) dans [HoloLens considérations relatives](/hololens/hololens-environment-considerations)à l’environnement.

### <a name="lighting"></a>Éclairage

les performances de HoloLens peuvent être affectées par des conditions d’éclairage très basses ou très brillantes.  les capteurs de suivi sur le HoloLens besoin d’environ 500-1000 lux de lumière pour fonctionner de façon optimale. Vous pouvez utiliser une application luxmeter ou mobile pour mesurer la quantité de lumière dans votre espace.

pour plus d’informations, consultez [éclairage](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) dans [HoloLens considérations relatives](/hololens/hololens-environment-considerations)à l’environnement.

## <a name="anchor-fundamentals"></a>Notions de base de l’ancre

Pour découvrir comment utiliser des ancres spatiales pour aligner des hologrammes sur un espace physique, sélectionnez **ancrer Fundametals** sur la page d’accueil de l’application.

Dans cette partie de l’application, nous allons explorer les scénarios utilisateur suivants :

>[!div class = "checklist"]
> * Ce qui se passe quand aucune ancre n’est appliquée à un objet.
> * Lorsque plusieurs ancres spatiales sont utilisées pour un groupe d’objets.
> * Partage d’une ancre spatiale entre plusieurs collaborateurs à l’aide d’un code QR.
> * Emplacement d’ancrage pour les objets de très grande taille dans un espace.

Pour plus d’informations, consultez [ancres spatiales](../../design/spatial-anchors.md) dans la documentation relative à la [réalité mixte](../../design/spatial-anchors.md) .

## <a name="stability-and-fidelity"></a>Stabilité et fidélité

Sur la page d’accueil de l’application, sélectionnez **stabilité et fidélité** pour découvrir comment améliorer la stabilité des hologrammes.

Nous allons explorer les concepts clés suivants :

>[!div class = "checklist"]
> * [Fréquence d’images](#frame-rate).
> * [Reprojection en phase tardive (LSR)](#late-stage-reprojection-lsr).
> * [Z-combat](#z-fighting).
> * [Anticrénelage](#anti-aliasing).

### <a name="frame-rate"></a>Fréquence d’images

Pour offrir la meilleure expérience d’hologramme possible, les développeurs d’applications doivent conserver 60 images par seconde (FPS).  Dans cette partie de l’application, basculez entre les différentes options de comptage des triangles pour découvrir la différence avec les différentes fréquences d’images.

![Optimisation du nombre de triangles](images\qf-triangle-count-optimization.png)

Pour plus d’informations, consultez [fréquence d’images](../platform-capabilities-and-apis/hologram-stability.md#frame-rate) dans l’article sur la stabilité des [hologrammes](../platform-capabilities-and-apis/hologram-stability.md) .

### <a name="late-stage-reprojection-lsr"></a>Reprojection en phase tardive (LSR)

La reprojection est utilisée pour stabiliser les hologrammes à mesure que les utilisateurs se déplacent dans leur espace.  Essayez les différentes options de reprojection fournies par cette partie de l’application pour voir la différence de qualité de l’hologramme.

![Essayez les différentes options de reprojection pour découvrir la différence.](images\qf-lsr-modes.jpg)

Pour plus d’informations, consultez [reprojection](../platform-capabilities-and-apis/hologram-stability.md#reprojection) dans l’article sur la [stabilité des hologrammes](../platform-capabilities-and-apis/hologram-stability.md) .

### <a name="z-fighting"></a>Z-fighting

Z-combat se produit lorsque l’application de réalité mixte ne peut pas déterminer quel objet est devant l’autre.  Vous remarquerez le scintillement des objets holographiques lorsqu’ils luttent contre la même valeur de profondeur z.  Observez les effets de la lutte z dans l’application en modifiant l’emplacement d’un objet holographique, le logo sur une bicyclette dans ce cas.

![Découvrez z-combat avec les placements d’objets.](images\qf-z-fighting.jpg)

Pour plus d’informations sur la lutte z, consultez [activer le partage de mémoire tampon de profondeur](./recommended-settings-for-unity.md#enable-depth-buffer-sharing) dans l’article [paramètres recommandés pour Unity](./recommended-settings-for-unity.md) .

### <a name="anti-aliasing"></a>Anticrénelage

L’anticrénelage est une technique utilisée pour lisser les bords en escalier sur les lignes courbées et les diagonales dans les hologrammes.  Dans cette partie de l’application, observez les effets de l’alias sur le texte affiché et les rayons de bicyclette.  

## <a name="3d-asset-fundamentals"></a>notions de base des ressources 3D

Sur la page d’accueil de l’application, sélectionnez notions de base de la **ressource 3D** pour découvrir comment optimiser les ressources 3D pour respecter les exigences de fréquence d’images tout en conservant une haute fidélité visuelle.

Nous allons explorer les concepts clés suivants :

>[!div class = "checklist"]
> * [Nombre de triangles](#triangle-count).
> * [Passes de nuanceur](#shader-passes).
> * [Appels de dessin](#draw-calls).
> * [Final](#finale).

### <a name="triangle-count"></a>Nombre de triangles

Sélectionnez le nombre et la complexité des modèles de bicyclettes pour découvrir la différence visuelle en fonction des FPS.

![Choisissez des options de comptage des triangles différentes pour voir les effets sur la fréquence d’images.](images\qf-3d-asset-visible-triangles.jpg)

Pour plus d’informations, consultez [processus de création](../../design/asset-creation-process.md)d’un élément multimédia.

### <a name="shader-passes"></a>Passes de nuanceur

Sélectionnez le nombre de vélos et les différentes options de nuanceur pour connaître la différence visuelle basée sur FPS.

![Choisissez différentes options de nuanceur pour voir les effets sur la fréquence d’images.](images\qf-3d-asset-shader-complexity.jpg)

Pour plus d’informations, consultez [nuanceur standard MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).

### <a name="draw-calls"></a>Appels de dessin

Les appels de dessin sont des appels gourmands en ressources vers la carte graphique.  Dans cette partie de l’application, observez la différence visuelle en premier, car le nombre d’appels de dessin a un impact sur FPS.

![Les appels de dessin doivent être optimisés pour améliorer les performances.](images\qf-3d-asset-draw-calls.jpg)

Consultez [recommandations relatives aux performances de l’UC au GPU](./performance-recommendations-for-unity.md#cpu-to-gpu-performance-recommendations).

### <a name="finale"></a>Fin

Ici, nous pouvons explorer le nombre de bicyclettes entièrement optimisées qui peuvent être affichées et le niveau de fidélité possible en fonction des techniques d’optimisation.

![Techniques d’optimisation utilisées.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Étapes suivantes

Explorez d’autres exemples de scénarios de réalité mixte :

   > [!div class="nextstepaction"]
   > [Exemples d’applications et de fonctionnalités](../features-and-samples.md)