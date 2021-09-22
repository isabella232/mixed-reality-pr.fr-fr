---
title: Spectator View
description: Visualisez des hologrammes à partir d’un appareil externe pour montrer ou enregistrer une expérience de réalité mixte sur un écran externe.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, caméra, ARKit, HoloLens, réalité mixte, MixedRealityToolkit, démonstration, enregistrement
ms.openlocfilehash: f30c745154056cda6b5ccf052efbbd0bb7f094ea
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779462"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Spectator View pour HoloLens et HoloLens 2

> [!WARNING]
> Microsoft va déprécier l’exemple Spectator View en raison d’incompatibilités avec la version du package Azure Spatial Anchors SDK sur laquelle repose l’exemple. Notez également que l’exemple peut cesser de fonctionner en raison d’autres modifications dans l’environnement Unity à mesure que les clients migrent vers des builds LTS 2019 prises en charge.
>
> Bien que Microsoft n’investisse pas actuellement de ressources pour résoudre les problèmes ci-dessus, il peut être possible de supprimer la fonctionnalité Azure Spatial Anchors de l’exemple et de recourir à une autre technologie (telle que celle des codes QR) pour l’alignement.   Si des membres de la communauté envoient des PR pour résoudre ces problèmes, nous les examinerons et les accepterons pour le moment.

![Marqueur](images/SpecViewPhoneHero.jpg)

Quand nous portons un appareil HoloLens, il est facile d’oublier qu’une personne qui n’en a pas est incapable de voir les merveilles qui s’offrent à nos yeux. Spectator View permet à d’autres personnes de voir ce qu’un utilisateur HoloLens voit sur un écran 2D. Il offre un moyen rapide et économique d’enregistrer des hologrammes en HD avec des appareils mobiles, et permet de créer des enregistrements d’hologrammes de qualité avec des caméras vidéo.

## <a name="key-resources"></a>Ressources clés

* [**Spectator View sur GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Documentation sur Spectator View**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Exemples Spectator View**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Scénarios d’utilisation

* Vous pouvez enregistrer une expérience de réalité mixte à l’aide d’un appareil iPhone ou Android. Enregistrez en Full HD et appliquez un anticrénelage aux hologrammes et aux ombres. Vous disposez d’une solution de capture de vidéos d’hologrammes économique et rapide.
* Diffusez en streaming des expériences de réalité mixte en direct sur un appareil Apple TV, directement à partir de votre iPhone ou iPad, sans aucun décalage !
* Partagez l’expérience avec des invités : donnez aux personnes ne disposant pas d’un appareil HoloLens la possibilité de voir des hologrammes directement sur leur téléphone ou leur tablette.

## <a name="current-features"></a>Fonctionnalités actuelles

* Synchronisation spatiale des hologrammes pour permettre à tout le monde de voir les hologrammes exactement au même endroit.
* Prise en charge d’iOS (appareils compatibles ARKit) et d’Android (appareils compatibles ARCore).
Plusieurs invités iOS.
Enregistrement de vidéos + hologrammes + son ambiant + son des hologrammes.
Feuille de partage permettant d’enregistrer une vidéo, de l’envoyer par e-mail ou de la partager avec d’autres applications compatibles.

![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)

Le tableau suivant liste différentes fonctionnalités de Spectator View. Choisissez l’option qui correspond le mieux à vos besoins en matière d’enregistrement vidéo :

|      Fonctionnalités                                | Mobile                  |                    Caméra vidéo              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualité HD                           |         Full HD         |        Enregistrement de qualité professionnelle (varie selon la caméra vidéo)      |
| Déplacement aisé de la caméra                 |            ✔            |                      ✔                      |
| Vue externe                    |            ✔            |                      ✔                      |
| Diffusion en streaming sur des écrans           |            ✔            |                      ✔                      |
| Portable                             |            ✔            |                                             |
| Sans fil                             |            ✔            |                                             |
| Matériel supplémentaire requis         |     Téléphone Android, iPhone    | HoloLens + plateforme + trépied + caméra vidéo + PC + Unity |
| Investissement matériel                  |           Faible            |                     Élevé                    |
| Système multiplateforme                       |           Android, iOS   |                                             |
| Contenu synchronisé                 |            ✔            |                      ✔                      |
| Durée d’installation du runtime               |         Instantané          |                     Lente                    |
## <a name="see-also"></a>Voir aussi

* [MRC (Mixed Reality Capture)](/hololens/holographic-photos-and-videos) 
* [Capture de Réalité Mixte pour les développeurs](mixed-reality-capture-for-developers.md)
* [Expériences partagées dans Mixed Reality](shared-experiences-in-mixed-reality.md)