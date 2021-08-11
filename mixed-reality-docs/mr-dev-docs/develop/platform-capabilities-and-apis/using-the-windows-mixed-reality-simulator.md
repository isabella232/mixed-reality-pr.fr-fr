---
title: Utilisation du simulateur Windows Mixed Reality
description: le simulateur Windows Mixed Reality vous permet de tester des applications de réalité mixte sur votre ordinateur sans Windows Mixed Reality de casque immersif.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, simulateur, test
ms.openlocfilehash: 0a6ff0cb0cd893c40e354c0590437201fb97e75c67421a638e47897b19a8f688
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220931"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Utilisation du simulateur Windows Mixed Reality

le simulateur Windows Mixed Reality vous permet de tester des applications de réalité mixte sur votre ordinateur sans Windows Mixed Reality de casque immersif. Le simulateur est disponible avec le Windows 10 Creators Update. le simulateur est semblable au [Emulator HoloLens](using-the-hololens-emulator.md), bien que le simulateur n’utilise pas de machine virtuelle. les applications simulées s’exécutent dans votre session utilisateur de bureau Windows 10, comme si vous utilisiez un casque immersif. Les entrées humaines et environnementales lues par les capteurs sur un casque immersif sont à la place simulées à l’aide de votre clavier, de votre souris ou de votre contrôleur Xbox. Les applications n’ont pas besoin d’être modifiées pour s’exécuter dans le simulateur et ne savent pas qu’elles ne s’exécutent pas sur un casque immersif.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>activation du simulateur Windows Mixed Reality

1. **activez le mode développeur** à partir de la mise à jour et de la sécurité de Paramètres > > pour les développeurs
2. Lancer le **portail de réalité mixte** à partir du Bureau
3. S’il s’agit de la première fois que vous lancez le portail, vous devez suivre le processus d’installation
   1. Sélectionnez **prise en main**
   2. Sélectionnez **J’accepte** pour accepter le contrat
   3. Sélectionnez **configurer pour la simulation (pour les développeurs)** pour poursuivre l’installation sans appareil physique
   4. Sélectionnez **configurer** pour confirmer votre choix
4. Sélectionnez le bouton **pour les développeurs** sur le côté gauche du portail de réalité mixte
5. Activer le basculement de la simulation **sur activé**
   * L’activation de la simulation installe et active le contrôleur 6-DDL simulé à gauche par défaut.  avant la mise à jour de la Windows 10 mai 2019, l’installation d’un contrôleur 6-ddl simulé nécessite des autorisations d’administrateur.  Acceptez la boîte de dialogue contrôle de compte d’utilisateur, le cas échéant.

Vous devez maintenant être en cours d’exécution avec la simulation !

si vous souhaitez désactiver le mode développeur dans Paramètres, vous devez d’abord activer le basculement de la Simulation sur **désactivé** dans la section **pour les développeurs** du portail de la réalité mixte.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Déploiement d’applications dans le simulateur de réalité mixte

étant donné que le simulateur s’exécute sur votre ordinateur local sans ordinateur virtuel, vous pouvez déployer vos applications de Windows universels sur l' **ordinateur local** lors du débogage.

## <a name="basic-simulator-input"></a>Entrée du simulateur de base

le contrôle du simulateur est similaire à de nombreux jeux vidéo en 3d courants et à l' [émulateur HoloLens](using-the-hololens-emulator.md). Les options d’entrée sont disponibles par le biais du clavier, de la souris ou d’une manette Xbox.

Vous contrôlez le simulateur en dirigeant les actions d’un utilisateur simulé qui porte un casque immersif. Vos actions déplacent l’utilisateur simulé et entraînent des interactions avec les applications qui répondent comme elles le feraient sur un casque immersif.
* **Marcher vers l’avant, l’arrière, la gauche et la droite** : utilisez les touches W, A, S et D du clavier, ou le stick gauche d’une manette Xbox.
* **Recherchez, bas, gauche et droit** , puis faites glisser la souris, utilisez les touches de direction de votre clavier ou le levier droit sur un contrôleur Xbox.
* **Bouton d’action Appuyez** sur le contrôleur-cliquez avec le bouton droit sur la souris, appuyez sur la touche entrée de votre clavier ou utilisez le bouton A sur un contrôleur Xbox.
* **appuyez sur le bouton de démarrage du contrôleur** -appuyez sur la touche Windows ou F2 de votre clavier, ou appuyez sur le bouton B sur un contrôleur Xbox.
* **Déplacement du contrôleur pour le défilement** : maintenez la touche Alt et le bouton droit de la souris, puis faites glisser la souris vers le haut/vers le haut. Sur une manette Xbox, maintenez la gâchette droite et le bouton A enfoncés et déplacez le stick droit vers le haut et le bas.

## <a name="tracked-controllers"></a>Contrôleurs suivis

Le simulateur de réalité mixte peut simuler jusqu’à deux contrôleurs de mouvement suivis. Activez-les à l’aide des commutateurs bascule dans le portail de la réalité mixte. Chaque contrôleur simulé a :
* Position et orientation dans l’espace
* Bouton Accueil
* Bouton Menu
* Bouton de poignée
* Pavé tactile
* Stick
* Niveau de la batterie

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de points de contrôle de développement Unreal que nous avons élaboré, vous êtes actuellement au cœur de la phase de déploiement. À partir de là, vous pouvez passer à la rubrique suivante ou passer directement à la [section](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) ajout de services avancés.

> [!div class="nextstepaction"]
> [Services avancés](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Voir aussi
* [Utilisation de l’émulateur HoloLens](using-the-hololens-emulator.md)
* [Entrée de simulateur de réalité mixte avancée](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mappage spatial dans Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Mappage spatial dans DirectX](../../develop/native/spatial-mapping-in-directx.md)
