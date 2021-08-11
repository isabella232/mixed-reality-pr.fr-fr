---
title: Mise à niveau de projets dans Unreal
description: Restez informé des étapes de mise à niveau de version, des modifications de l’API et des dépréciations pour vos projets Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, portage, mise à niveau
ms.openlocfilehash: 88b3f12bf32c81e39e622a7766119ca4d1b087f80cfc774148853926b6446dbc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197197"
---
# <a name="upgrading-projects-in-unreal"></a>Mise à niveau de projets dans Unreal

Lors de la mise à jour vers une nouvelle version d’Unreal, les fonctions dépréciées apparaissent sous forme d’avertissements lors de la compilation des blueprints ou de l’empaquetage du projet.  Une fonction est dépréciée quand une nouvelle fonction a été ajoutée et doit être utilisée à la place. 

## <a name="426-upgrades"></a>Mises à niveau de 4.26
 
Dans la version 4.26, toutes les plateformes AR et VR ont été refactorisées de façon à ajouter des interfaces communes et à garder le code d’application indépendant des plateformes, si bien que vous risquez de voir plus d’avertissements que d’habitude.  La mise à jour vers les nouvelles API est recommandée pour que le projet puisse être porté plus facilement vers d’autres plateformes.

Les messages d’avertissement montrent quelle fonction a été dépréciée et indiquent la fonction à utiliser à la place.  Toutes les fonctions dépréciées vont continuer de fonctionner pour cette version, mais elles peuvent ne pas fonctionner dans des versions futures.  Les fonctions dépréciées ne sont plus listées lors de la recherche de fonctions dans un blueprint.

![Blueprint de la fonction Créer un ARPin nommé](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>Dépréciations de la version 4.25

| Fonction dépréciée | Nouvelle fonction |
| --- | --- |
| CreateNamedARPin | ![Blueprint de la fonction Épingler un composant](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Blueprint de la fonction Charger des ARPins à partir du magasin local](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Blueprint de la fonction Enregistrer un ARPin dans le magasin local](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Blueprint de la fonction Supprimer un ARPin du magasin local](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Blueprint de la fonction Activer XRCamera](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Blueprint de la fonction Redimensionner XRCamera](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![Blueprint de la fonction Activer/désactiver ARCapture pour démarrer la capture avec la caméra](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![Blueprint de la fonction Activer/désactiver ARCapture pour arrêter la capture avec la caméra](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![Blueprint de la fonction Activer/désactiver ARCapture pour démarrer la capture de code QR](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![Blueprint de la fonction Activer/désactiver ARCapture pour arrêter la capture de code QR](images/unreal-porting-img-11.png) |
| Le mappage spatial démarrait auparavant automatiquement dans 4.25, mais il doit maintenant être activé/désactivé dans 4.26. | ![Blueprint de la fonction Activer/désactiver ARCapture pour activer le mappage spatial](images/unreal-porting-img-12.png) |
| ShowKeyboard | Supprimé dans 4.26, car le clavier s’affiche automatiquement quand un widget de texte reçoit le focus. |
| HideKeyboard | Supprimé dans 4.26, car le clavier est masqué automatiquement quand un widget de texte n’a plus le focus. |
| SupportsHandTracking | ![Blueprint de la propriété de prise en charge du suivi des mains](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![Blueprint de la propriété IsDisplayOpaque](images/unreal-porting-img-14.png) |
| GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus | ![Blueprint de la fonction Obtenir les données du contrôleur de mouvement](images/unreal-porting-img-15.png) |
| GetVersionString | ![Blueprint de la fonction Obtenir la chaîne de version](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![Blueprint de la propriété IsTrackingAvailable](images/unreal-porting-img-17.png) |
| IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed | Utilisez le système d’action d’entrée d’Unreal. |
| SetFocusPointForFrame | Supprimé dans 4.26  Était utilisé pour la reprojection lors de la communication à distance, qui prend désormais en charge la reprojection de profondeur. |

## <a name="426-changes"></a>Modifications de 4.26

La modification la plus importante est que **Start in VR** dans **Edit > Project Settings > Project > Description > Settings** est obligatoire pour démarrer le plug-in Windows Mixed Reality. Sans ce paramètre, vous ne verrez pas vos hologrammes sur l’appareil.
