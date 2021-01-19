---
title: Codes QR dans Unreal
description: Découvrez comment configurer, utiliser et faire le suivi des codes QR dans des applications de réalité mixte Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, qr codes, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: d896af683a86a1b27e5d100df744222085574a93
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247742"
---
# <a name="qr-codes-in-unreal"></a>Codes QR dans Unreal

HoloLens 2 peut voir les codes QR dans l’espace universel à travers la webcam, qui les rend sous forme d’hologrammes à la position réelle de chaque code. HoloLens 2 peut aussi rendre des hologrammes sur plusieurs appareils à la même position pour créer une expérience partagée. Veillez à suivre les bonnes pratiques pour ajouter les codes QR à vos applications :

- Zones calmes
- Éclairage et toile de fond
- Taille, distance et position angulaire

Au moment de placer les codes QR dans votre application, portez une attention particulière aux [considérations liées à l’environnement](../../environment-considerations-for-hololens.md). Vous trouverez des informations complémentaires sur chacun de ces sujets ainsi que des instructions sur la façon de télécharger le package NuGet nécessaire dans le document [Suivi des codes QR](../platform-capabilities-and-apis/qr-code-tracking.md).

> [!CAUTION]
> Les codes QR sont les seuls types d’images qui peuvent être suivies de façon native par HoloLens ; le module intégré **UARTrackedImage** module n’est pas pris en charge sur HoloLens. Si vous avez besoin de suivre des images personnalisées, vous pouvez accéder à la [webcam](unreal-hololens-camera.md) de l’appareil et traiter les images en utilisant une bibliothèque de reconnaissance d’images de tiers. 

## <a name="enabling-qr-detection"></a>Activation de la détection QR

Étant donné que HoloLens 2 doit utiliser la webcam pour voir les codes QR, vous devez l’activer dans les paramètres du projet :
- Ouvrez **Edit > Project Settings**, accédez à la section **Platforms**, puis sélectionnez **HoloLens**.
    + Développez la section **Capabilities** et cochez **Webcam**.  
- Vous devez aussi opter pour le suivi des codes QR en [ajoutant une ressource ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>Configuration d’un code QR suivi

Les codes QR sont exposés sous forme d’image suivie par le biais du système de géométrie suivie de réalité augmentée d’Unreal. Pour que cela fonctionne, vous devez :
1. Créer un blueprint d’acteur et ajouter un composant **ARTrackableNotify** :

![Composant ARTrackableNotify QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Sélectionnez **ARTrackableNotify** et développez la section **Events** dans le panneau **Details** :

![Événements QR](images/unreal-spatialmapping-events.PNG)

3. Cliquez sur **+** à côté de **On Add Tracked Geometry** pour ajouter le nœud au graphique d’événements.
    - Vous trouverez la liste complète des événements dans l’API du composant [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).

![Ajouter un nœud à On Add Tracked Geometry](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>Utilisation d’un code QR suivi

Le graphique d’événements dans l’image suivante présente l’événement **OnUpdateTrackedImage** qui est utilisé pour afficher un point au centre d’un code QR et imprimer ses données.

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

Voici ce qui se passe :
1. Tout d’abord, l’image suivie est castée en **ARTrackedQRCode** pour vérifier que l’image mise à jour actuelle est un code QR.  
2. Les données encodées sont récupérées à partir de la variable **QRCode**. Vous pouvez obtenir l’angle supérieur gauche du code QR à partir de l’emplacement de **GetLocalToWorldTransform** et les dimensions avec **GetEstimateSize**.

Vous pouvez aussi [obtenir le système de coordonnées pour un code QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) dans le code.

## <a name="finding-the-unique-id"></a>Recherche de l’ID unique

À chaque code QR correspond un ID guid unique, que vous pouvez trouver comme ceci :
- Glissez-déposez le repère **As ARTracked QRCode** et effectuez une recherche sur l’ID unique (**Unique ID**).

![GUID QR](images/unreal-qr-guid.PNG)

Il se passe beaucoup de choses en coulisse avec les codes QR : vous n’en avez donc pas terminé. N’hésitez pas à consulter les liens ci-dessous pour en savoir plus sur la mécanique interne.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les API et fonctionnalités de la plateforme Mixed Reality. À partir de là, vous pouvez passer à la rubrique suivante :

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :

> [!div class="nextstepaction"]
> [Déploiement sur un appareil](unreal-deploying.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#3-advanced-features) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Mappage spatial](../../design/spatial-mapping.md)
* [Hologrammes](../../discover/hologram.md)
* [Systèmes de coordonnées](../../design/coordinate-systems.md)
