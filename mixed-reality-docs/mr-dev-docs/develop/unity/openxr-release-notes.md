---
title: Notes de publication du plug-in Mixed Reality OpenXR
description: Restez informé des dernières notes de publication et mises à niveau vers le plug-in Mixed Reality OpenXR.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394628"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>Notes de publication du plug-in Mixed Reality OpenXR

## <a name="100---current-release"></a>1.0.0 - Version actuelle

* Correction d’un bogue où XRAnchorSubsystem démarrait toujours au lancement de l’application, peu importe si ARAnchorManager était présent.
* Correction d’un bogue où le mode de reprojection ne fonctionnait pas correctement.

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview.2 - 14/06/2021

* Dépend du plug-in 1.2.2 OpenXR d’Unity.
* Modification des fonctionnalités de communication à distance holographique dans des groupes de fonctionnalités individuels.
* Correction d’un bogue où « Appliquer les paramètres du projet HoloLens 2 » modifie l’espace de couleurs du projet. Cela n’est plus nécessaire après le plug-in Unity OpenXR 1.2.0.
* Correction d’un bogue dans lequel un appareil d’entrée se connecte sans se déconnecter après la mise en pause et la reprise de l’application.
* Ajout de la prise en charge de la détection des plug-ins et états de suivi actuels via ARSession.
* Correction d’un bogue dans lequel le préfabriqué ARFoundation « Plan AR par défaut » n’était pas visible.

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview.1 - 02/06/2021

* Prend en charge les extensions MSFT de compréhension des scènes OpenXR au lieu des extensions préliminaires.
* La détection de plan sur HoloLens 2 ne requiert plus les versions préliminaires des runtimes Mixed Reality OpenXR.

## <a name="095---2021-05-21"></a>0.9.5 - 21/05/2021

* Dépend du plug-in 1.2.0 OpenXR d’Unity
* Adapté à la nouvelle interface utilisateur des fonctionnalités (dans le plug-in OpenXR 1.2.0) pour la configuration.
* Correction d’un bogue dans lequel l’inscription du fournisseur de caméras localisables n’a pas été correctement annulée.
* Nettoyage de certaines utilisations supplémentaires de [Preserve].
* Mise à jour du nom « Contrôleur HP Reverb G2 (OpenXR) » dans l’interface utilisateur du système d’entrée.

## <a name="094---2021-05-20"></a>0.9.4 - 20/05/2021

* Dépend du plug-in 1.2.0 OpenXR d’Unity.
* Ajout d’une nouvelle API C# pour obtenir le modèle glTF du contrôleur de mouvement.
* Ajout d’une nouvelle API C# pour obtenir les configurations d’affichage activées et définir les paramètres de reprojection.
* Ajout d’une nouvelle API C# pour définir des paramètres supplémentaires pour le calcul de maillages avec XRMeshSubsystem.
* Ajout d’une nouvelle API C# pour configurer les événements de reconnaissance de mouvement et s’y abonner.
* Ajout de la boîte de dialogue de paramètres Windows->XR->Editor Remoting.
* Ajout de la prise en charge ARM pour les applications HoloLens UWP.

## <a name="093---2021-04-29"></a>0.9.3 - 29/04/2021

* Correction d’un bogue dans lequel la connexion à distance holographique n’est pas fiable
* Correction d’un bogue dans lequel les performances de rendu VR sont altérées après la mise à niveau vers le plug-in 1.1.1 OpenXR d’Unity.

## <a name="092---2021-04-21"></a>0.9.2 - 21/04/2021

* La détection de plan sur HoloLens 2 dans le plug-in version 0.9.1 fonctionne avec la version 105 du runtime préliminaire Mixed Reality OpenXR.
* La détection de plan sur HoloLens 2 dans le plug-in version 0.9.2 fonctionne avec la version 106 du runtime préliminaire Mixed Reality OpenXR.
* Suppression de certains rappels inutilisés d’InputProvider pour empêcher les appels, tels que XRInputSubsystem.* GetTrackingOriginMode (qui ne sont pas gérés par notre système d’entrée), de renvoyer des valeurs erronées.
* Fractionnement de la version déconseillée de XRAnchorStore dans son propre fichier pour éviter l’avertissement de la console Unity.

## <a name="091---2021-04-20"></a>0.9.1 - 20/04/2021

* Dépend du plug-in 1.1.1 OpenXR d’Unity.
* Ajout de la prise en charge de l’application de communication à distance holographique pour la plateforme UWP.
* Correction d’UnityException où XRAnchorStore essayait d’obtenir une instance de paramètres en dehors du thread principal.

## <a name="090---2021-03-29"></a>0.9.0 - 29/03/2021

* Ajout de la prise en charge du mappage spatial via XRMeshSubsystem et ARMeshManager.
* Ajout d’une nouvelle API C# pour recevoir des handles OpenXR afin de prendre en charge d’autres packages Unity qui utilisent des extensions OpenXR.
* Ajout d’une nouvelle API C# pour l’interopérabilité avec les API Windows.Perception pour prendre en charge d’autres packages Unity qui utilisent des API Perception WinRT.
* Suppression de profils d’interaction des fonctionnalités requises dans l’ensemble des fonctionnalités de Windows Mixed Reality afin que les développeurs puissent choisir les contrôleurs de mouvement qu’ils ont testés.
* Ajout d’un outil de validation des fonctionnalité de communication à distance de l’éditeur holographique pour aider les utilisateurs à configurer correctement la communication à distance de l’éditeur.
* Correction d’un bogue où l’éditeur Unity se bloque lors de la fermeture du mode de communication à distance de l’éditeur holographique après un échec de connexion.
* Correction d’un bogue où les textures alpha qui n’ont pas été préalablement multipliées conduisent à une altération des performances sur HoloLens 2.
* Correction d’un bogue dans lequel le suivi de la main n’était pas correctement localisé lorsque l’origine de la scène était au niveau du sol.
* Correction d’un bogue dans lequel le suivi du maillage de la main disparaît une fois la scène fermée et une nouvelle scène chargée.
* Correction d’un bogue où le fournisseur de caméras localisables n’a pas été correctement nettoyé.
* Modification de l’espace de noms de l’API XRAnchorStore en Microsoft.MixedReality.OpenXR.