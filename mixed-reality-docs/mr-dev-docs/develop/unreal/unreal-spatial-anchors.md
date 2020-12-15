---
title: Ancres spatiales locales dans Unreal
description: Guide d’utilisation des ancres spatiales dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, ancres spatiales, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 1c9d9fa119e57c57ab126fc26a26a35d75e07db7
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926089"
---
# <a name="local-spatial-anchors-in-unreal"></a>Ancres spatiales locales dans Unreal

Les ancres spatiales enregistrent les hologrammes en place dans l’espace réel entre les sessions d’application comme des **ARPins**. Une fois enregistrés dans le magasin d’ancres HoloLens, les ARPins peuvent être chargés dans de futures sessions et constituent une option de secours idéale en l’absence de connectivité Internet.

> [!NOTE]
> Les fonctions des ancres d’UE 4.25 sont obsolètes dans 4.26 et doivent être remplacées par des fonctions plus récentes. 

> [!IMPORTANT]
> Les ancres locales sont stockées sur l’appareil, alors que les ancres spatiales Azure sont stockées dans le cloud. Si vous envisagez d’utiliser les services cloud Azure pour stocker vos ancres, nous avons créé un guide qui vous aidera à intégrer [Azure Spatial Anchors](unreal-azure-spatial-anchors.md). Notez que vous pouvez avoir des ancres locales et Azure dans le même projet sans conflit.

## <a name="checking-the-anchor-store"></a>Vérification du magasin d’ancres

Avant d’enregistrer ou de charger des ancres, vous avez besoin de vérifier si le magasin d’ancres est prêt.  Tout appel d’une des fonctions d’ancrage HoloLens échoue si le magasin d’ancres n’est pas prêt.  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a>Enregistrement des ancres

Quand l’application a un composant que vous avez besoin de relier au monde réel, ce composant peut être enregistré dans le magasin d’ancres avec la séquence suivante : 

[!INCLUDE[](includes/tabs-sa-2.md)]

Décomposons cette séquence :
1. Générez un acteur à un emplacement connu.
2. Créez un **ARPin** avec cet emplacement et un nom basé sur la classe de l’acteur. 
3. Ajoutez l’acteur au **ARPin** et enregistrez le repère dans le magasin d’ancres HoloLens.  
    * Le nom d’ancre que vous choisissez doit être unique. Dans cet exemple, il s’agit de l’horodatage actuel. 

4. Si l’ancre est correctement enregistrée dans le magasin d’ancres, vous pouvez la voir dans le portail d’appareil HoloLens sous **System > Map Manager > Anchor Files Saved On Device**. 

## <a name="loading-anchors"></a>Chargement des ancres

Au démarrage d’une application, vous pouvez utiliser le blueprint ci-dessous pour rétablir les composants à leurs positions d’ancrage :

[!INCLUDE[](includes/tabs-sa-3.md)]

Décomposons cette séquence :
1. Effectuez une itération sur toutes les ancres du magasin d’ancres. 
2. Générez un acteur au niveau de l’identité.
3. Épinglez cet acteur au **ARPin** à partir du magasin d’ancres.  

    * Il est important de générer l’acteur au niveau de l’identité, car l’ancre est chargée de repositionner l’hologramme dans l’environnement selon l’emplacement auquel il a été enregistré. Toute transformation ajoutée ici va ajouter un décalage à l’ancre. 

L’ID de l’ancre est également demandé afin que différents acteurs puissent être générés en fonction du nom enregistré de l’ancre. 

## <a name="removing-anchors"></a>Suppression des ancres 

Lorsque vous n’avez plus besoin d’une ancre, vous pouvez l’effacer individuellement ou effacer la totalité du magasin d’ancres avec les composants **Remove ARPin from WMRAnchor Store** et **Remove All ARPins from WMRAnchor Store**.

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> N’oubliez pas que les ancres spatiales sont encore en version bêta, donc n’hésitez pas à vous tenir au courant des dernières informations et fonctionnalités.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous explorez actuellement les composants de base du MRTK. À partir d’ici, vous pouvez passer au composant suivant : 

> [!div class="nextstepaction"]
> [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Caméra HoloLens](unreal-hololens-camera.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)
* [Ancres spatiales](../../design/spatial-anchors.md)
* [Systèmes de coordonnées](../../design/coordinate-systems.md)
