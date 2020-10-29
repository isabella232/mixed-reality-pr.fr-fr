---
title: Ancres spatiales locales dans Unreal
description: Guide d’utilisation des ancres spatiales dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, ancres spatiales
ms.openlocfilehash: d223c451cbbf0fb4e2cc1392394d2fe771ec8069
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699084"
---
# <a name="local-spatial-anchors-in-unreal"></a>Ancres spatiales locales dans Unreal

## <a name="overview"></a>Vue d’ensemble

Les ancres spatiales sont utilisées pour enregistrer les hologrammes en place dans l’espace réel entre les sessions d’application. Elles sont exposées via Unreal sous forme d’ **ARPins** et sont enregistrées dans le magasin d’ancres HoloLens, que vous allez charger dans les sessions ultérieures. Les ancres locales sont idéales comme solutions de secours lorsqu’il n’y a pas de connectivité Internet.

> [!IMPORTANT]
> Les ancres locales sont stockées sur l’appareil, alors que les ancres spatiales Azure sont stockées dans le cloud. Si vous envisagez d’utiliser les services cloud Azure pour stocker vos ancres, nous avons créé un guide qui vous aidera à intégrer [Azure Spatial Anchors](unreal-azure-spatial-anchors.md). Notez que vous pouvez avoir des ancres locales et Azure dans le même projet sans conflit.

## <a name="checking-the-anchor-store"></a>Vérification du magasin d’ancres

Avant d’enregistrer ou de charger des ancres, vous avez besoin de vérifier si le magasin d’ancres est prêt.  Tout appel d’une des fonctions d’ancrage HoloLens échoue si le magasin d’ancres n’est pas prêt.  

![Magasin d’ancres spatiales prêt](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>Enregistrement des ancres

Quand l’application a un composant qui doit être relié au monde réel, ce composant peut être enregistré dans le magasin d’ancres avec la séquence suivante : 

![Enregistrer des ancres spatiales](images/unreal-spatialanchors-save.PNG)

Décomposons cette séquence :
1. Générez un acteur à un emplacement connu.
2. Créez un **ARPin** avec cet emplacement et un nom basé sur la classe de l’acteur. 
3. Ajoutez l’acteur au **ARPin** et enregistrez le repère dans le magasin d’ancres HoloLens.  
    * Le nom d’ancre que vous choisissez doit être unique. Dans cet exemple, il s’agit de l’horodatage actuel. 

4. Si l’ancre est correctement enregistrée dans le magasin d’ancres, vous pouvez l’inspecter dans le portail d’appareil HoloLens sous **System > Map Manager > Anchor Files Saved On Device** . 

## <a name="loading-anchors"></a>Chargement des ancres

Au démarrage d’une application, vous pouvez utiliser le blueprint ci-dessous pour rétablir les composants à leurs positions d’ancrage :

![Charger des ancres spatiales](images/unreal-spatialanchors-load.PNG)

Décomposons cette séquence :
1. Effectuez une itération sur toutes les ancres du magasin d’ancres. 
2. Générez un acteur au niveau de l’identité.
3. Épinglez cet acteur au **ARPin** à partir du magasin d’ancres.  

    * Il est important de générer l’acteur au niveau de l’identité, car l’ancre est chargée de repositionner l’hologramme dans l’environnement selon l’emplacement auquel il a été enregistré. Toute transformation ajoutée ici va ajouter un décalage à l’ancre. 

L’ID de l’ancre est également demandé afin que différents acteurs puissent être générés en fonction du nom enregistré de l’ancre. 

## <a name="removing-anchors"></a>Suppression des ancres 

Lorsque vous n’avez plus besoin d’une ancre, vous pouvez l’effacer individuellement ou effacer la totalité du magasin d’ancres avec les composants **Remove ARPin from WMRAnchor Store** et **Remove All ARPins from WMRAnchor Store** .

![Supprimer des ancres spatiales](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> N’oubliez pas que les ancres spatiales sont encore en version bêta, donc n’hésitez pas à vous tenir au courant des dernières informations et fonctionnalités.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les modules de base du MRTK. À partir de là, vous pouvez passer au module suivant : 

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
