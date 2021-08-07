---
title: Exploration de la page d’accueil Windows Mixed Reality
description: découvrez comment accéder à la page d’Windows Mixed Reality sur HoloLens et Windows Mixed Reality casques.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, système d’exploitation, plateforme, maison, maison, accueil, environnement, démarrer, menu Démarrer, menu Accueil, pin, application, lancer des applications, placer des applications, téléporter, déplacer, naviguer, casque de réalité mixte, casque de réalité virtuelle, présentation de la réalité virtuelle
ms.openlocfilehash: 39ca5e974e242019d7eb14fba0362151213c6558cce7f13328390712b3642901
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190273"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Exploration de la page d’accueil Windows Mixed Reality

tout comme l’expérience Windows PC commence par le bureau, Windows Mixed Reality commence par la page d’hébergement. la Windows Mixed Reality à la résidence utilise notre capacité innée pour comprendre et parcourir les emplacements 3d. avec HoloLens, votre foyer est votre espace physique, mais avec des casques immersifs, votre foyer est une place virtuelle.

votre foyer est également l’emplacement où vous allez utiliser le menu Démarrer pour ouvrir et placer des applications et du contenu. Vous pouvez remplir votre foyer avec du contenu de réalité mixte et utiliser plusieurs applications en même temps. Les choses que vous placez dans votre foyer restent là, même si vous redémarrez votre appareil.

## <a name="start-menu"></a>Menu Démarrer

![Menu Démarrer sur Microsoft HoloLens](images/start-500px.png)

le menu Démarrer se compose des éléments suivants :
* Informations système (État du réseau, pourcentage de batterie, heure actuelle et volume)
* Cortana (sur les casques immersifs, une vignette de démarrage ; sur HoloLens, en haut du début)
* Applications épinglées
* Bouton toutes les applications (signe plus)
* Boutons photo et vidéo pour la capture de la [réalité mixte](/hololens/holographic-photos-and-videos)

Basculez entre les vues applications épinglées et toutes les applications en sélectionnant les boutons plus ou moins. pour ouvrir le menu Démarrer sur HoloLens, utilisez le geste de fleur. sur un casque immersif, appuyez sur le bouton Windows sur votre contrôleur.

## <a name="launching-apps"></a>Lancement d’applications

Pour lancer une application, sélectionnez-la au démarrage. le menu Démarrer disparaît et l’application s’ouvre en mode placement, sous la forme d’une fenêtre 2d ou d’un [modèle 3d](../distribute/implementing-3d-app-launchers.md).

Pour exécuter l’application, vous devez la placer dans votre foyer :
1. Utilisez votre point d’interposition [ou contrôleur](../design/gaze-and-commit.md) pour positionner l’application là où vous le souhaitez. Elle s’ajuste automatiquement (en taille et en position) pour se conformer à l’espace où vous la placez.
2. placez l’application à l’aide de la pression aérienne (HoloLens) ou du bouton de sélection (casques immersifs). pour annuler et rétablir l’menu Démarrer, utilisez le geste de touche ou le bouton Windows.

les [applications 2D](../develop/porting-apps/building-2d-apps.md), créées pour un ordinateur de bureau, un appareil mobile ou une Xbox, peuvent être modifiées pour s’exécuter en tant qu’applications immersives de réalité mixte à l’aide de l' [API HolographicSpace](/uwp/api/Windows.Graphics.Holographic.HolographicSpace). Une application immersive fait sortir l’utilisateur de son lieu de départ et d’une expérience immersive. les utilisateurs peuvent retourner chez eux avec le geste (HoloLens) ou en appuyant sur le bouton Windows de leur contrôleur (casques immersifs).

Les applications peuvent également être lancées via une API app-to-App ou via Cortana.

![applications dans le Windows Mixed Reality](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Déplacement et ajustement d’applications

Sélectionnez **ajuster** dans la barre de l’application pour afficher les contrôles permettant de déplacer, de mettre à l’échelle et de faire pivoter le contenu de réalité mixte. Lorsque vous avez terminé, sélectionnez **terminé**.

![La ardoise du magasin en mode ajustement (cadre bleu). Remarque : la barre d’application (haut) a changé pour inclure les boutons « terminé » et « supprimer ».](images/adjust-500px.png)

Différentes applications peuvent avoir d’autres options dans la barre des applications. par exemple, Microsoft Edge a des options de *défilement*, de *glisser-déplacer* et de *Zoom* . 

![Barre d’application pour les applications 2D s’exécutant sur HoloLens](images/holobar-500px.png)

Le bouton **précédent** permet de revenir aux écrans affichés précédemment dans l’application. Elle s’arrête lorsque vous atteignez le début des expériences affichées dans l’application et n’accède pas à d’autres applications.

## <a name="getting-around-your-home"></a>L’approche de votre foyer

avec **HoloLens**, vous vous déplacez dans l’espace physique pour vous déplacer dans votre foyer.

Avec les **casques immersifs**, vous pouvez vous familiariser avec vos PlaySpace pour vous déplacer dans une zone similaire dans le monde virtuel. Pour vous déplacer sur des distances plus longues, utilisez le stick analogique sur votre contrôleur pour « parcourir » virtuellement, ou vous pouvez utiliser la *téléportage* pour passer immédiatement plus de distances.

![télélocalisation dans la Windows Mixed Reality](images/teleportation-500px.png)

**Pour vous téléporter :**
1. Affichez le réticule de téléportation.
   * À l’aide de [contrôleurs de mouvement](../design/motion-controllers.md): Appuyez sur le stick analogique et maintenez-le à cette position.
   * À l’aide d’un contrôleur Xbox : Appuyez sur le stick analogique gauche vers l’avant et maintenez-le à cette position.
   * À l’aide de la souris, cliquez avec le bouton droit sur le bouton de la souris (et utilisez la roulette de défilement pour faire pivoter la direction de votre choix lorsque vous vous reportez).
2. Placez le réticule là où vous souhaitez vous téléporter.
   * À l’aide de [contrôleurs de mouvement](../design/motion-controllers.md): Inclinez le contrôleur (sur lequel vous conservez le stick analogique) pour déplacer le réticule.
   * À l’aide d’un contrôleur Xbox : utilisez votre point de [regard](../design/gaze-and-commit.md) pour déplacer le réticule.
   * À l’aide d’une souris : déplacez votre souris pour déplacer le réticule.
3. Relâchez le bouton pour vous téléporter où le réticule a été placé.

**Pour « parcourir » virtuellement :**
* À l’aide de [contrôleurs de mouvement](../design/motion-controllers.md): cliquez sur le stick analogique et maintenez-le enfoncé, puis déplacez le stick analogique dans le sens où vous souhaitez « parcourir ».
* À l’aide d’un contrôleur Xbox : cliquez sur le stick analogique gauche et maintenez-le enfoncé, puis déplacez le stick analogique dans le sens où vous souhaitez « parcourir ».

## <a name="immersive-headset-input-support"></a>Prise en charge des entrées du casque immersif

[Windows Mixed Reality les casques immersifs](immersive-headset-hardware-details.md) prennent en charge plusieurs types d’entrée pour naviguer dans la Windows Mixed Reality. HoloLens ne prend pas en charge les entrées d’accessoire pour la navigation, car vous vous familiarisez physiquement avec votre environnement. toutefois, HoloLens [prend en charge les entrées](hardware-accessories.md) pour l’interaction avec les applications.

### <a name="motion-controllers"></a>Contrôleurs de mouvement

la meilleure expérience en matière de Windows Mixed Reality sera avec les [contrôleurs de mouvement](../design/motion-controllers.md) Windows Mixed Reality qui prennent en charge six degrés de liberté en utilisant uniquement les capteurs de votre casque. aucun appareil photo ou marqueur externe n’est nécessaire.

Commandes de navigation bientôt disponibles.

### <a name="gamepad"></a>Boîtier de commande
* **Stick analogique gauche :**
  * Appuyez sur le stick analogique gauche et maintenez-le enfoncé pour faire apparaître le réticule de [téléportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .
  * Appuyez sur le stick analogique à gauche, à droite ou à gauche pour déplacer les petits incréments vers la gauche, vers la droite ou vers l’arrière.
  * Cliquez sur le stick analogique gauche et maintenez-le enfoncé, puis déplacez le stick analogique dans le sens où vous souhaitez [virtuellement « parcourir ».](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Appuyez sur le **Stick à droite** vers la gauche ou vers la droite pour faire pivoter la direction que vous avez dirigée de 45 degrés.
* Le fait **d'** appuyer sur le bouton A sélectionne et agit comme le mouvement [air appuyé](../design/gaze-and-commit.md#composite-gestures) .
* le fait d’appuyer sur le bouton du **repère** affiche le [menu Démarrer](navigating-the-windows-mixed-reality-home.md#start-menu) et agit comme le geste de [fleur](../design/system-gesture.md#bloom) .
* Le fait d’appuyer sur les **déclencheurs de gauche et de droite** vous permet d’effectuer un zoom avant et arrière sur une application de bureau 2D avec laquelle vous interagissez à l’origine.

### <a name="keyboard-and-mouse"></a>Clavier et souris

**Remarque :** utilisez **Windows touche + Y** pour faire basculer la souris entre le bureau de votre PC et la page d’Windows Mixed Reality.

dans la page d’Windows Mixed Reality :
* Le fait d’appuyer sur le bouton gauche de la souris sélectionne et agit comme le mouvement d’appui **à** l' [air](../design/gaze-and-commit.md#composite-gestures) .
* En maintenant le bouton droit de la souris **, vous** Affichez le réticule de [téléportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .
* le fait d’appuyer sur la touche **Windows** sur le clavier affiche le [Menu démarrer](navigating-the-windows-mixed-reality-home.md#start-menu) et agit comme le geste [fleuri](../design/system-gesture.md#bloom) .
* Quand vous [Gazing](../design/gaze-and-commit.md) dans une application de bureau 2D, vous pouvez **Cliquer** avec le bouton droit pour sélectionner, **cliquer avec le bouton droit** pour afficher les menus contextuels et utiliser la **roulette de défilement** pour faire défiler (comme sur le Bureau de votre PC).

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana) est votre assistant personnel dans Windows Mixed Reality, tout comme sur un PC et un téléphone. HoloLens possède un microphone intégré, mais les casques immersifs peuvent nécessiter du matériel supplémentaire. utilisez Cortana pour ouvrir des applications, redémarrer votre appareil, rechercher des éléments en ligne et bien plus encore. les développeurs peuvent également choisir d' [intégrer des Cortana](https://dev.windows.com/cortana) à leurs expériences.

Vous pouvez également utiliser des commandes vocales pour vous familiariser avec votre foyer. Par exemple, pointez sur un bouton (en utilisant du [regard](../design/gaze-and-commit.md) ou un contrôleur, en fonction de l’appareil) et dites « sélectionner ». D’autres commandes vocales incluent « Go, », « large », « Small », « Close » et « me suis ».

## <a name="store-settings-and-system-apps"></a>stocker, Paramètres et applications système

Windows Mixed Reality dispose de plusieurs applications intégrées, telles que :
* **Microsoft Store** pour accéder aux applications et aux jeux
* **Hub de commentaires** pour envoyer des commentaires sur les applications système et système
* **Paramètres** pour configurer les paramètres système ([y compris la mise en réseau](/hololens/hololens-network) et les mises à jour système)
* **Microsoft Edge** pour parcourir les sites web
* **Photos** pour afficher et partager des Photos et des vidéos
* **étalonnage** (HoloLens uniquement) pour ajuster l’expérience HoloLens à l’utilisateur actuel
* **apprenez les gestes** (HoloLens) ou les **Découvrir la réalité mixte** (casques immersifs) pour en savoir plus sur l’utilisation de votre appareil
* **visionneuse 3D** pour décorer votre monde avec du contenu de réalité mixte
* **Portail de réalité mixte** (Desktop) pour la configuration et la gestion de votre casque immersif et la diffusion en continu d’un aperçu instantané de votre vue dans le casque pour que d’autres utilisateurs puissent les voir.
* **Films et TV** pour visionner des vidéos 360 et les derniers films et émissions TV
* **Cortana** pour tous les besoins de votre assistant virtuel
* **Bureau** (casques immersifs) pour afficher votre moniteur de bureau dans un casque immersif
* **Explorateur de fichiers** Accéder aux fichiers et aux dossiers situés sur votre appareil

## <a name="see-also"></a>Voir aussi
* [Vues d’applications](../design/app-views.md)
* [Contrôleurs de mouvement](../design/motion-controllers.md)
* [Accessoires matériels](hardware-accessories.md)
* [Considérations relatives à l’environnement pour HoloLens](/hololens/hololens-environment-considerations)
* [Implémentation des lanceurs d’applications 3D](../distribute/implementing-3d-app-launchers.md)
* [création de modèles 3d à utiliser dans la Windows Mixed Reality](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)