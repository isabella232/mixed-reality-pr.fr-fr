---
title: simulateur de HoloLens avancée Emulator et de réalité mixte
description: instructions détaillées pour l’utilisation du clavier, de la souris et du contrôleur Xbox pour simuler l’entrée pour le HoloLens Emulator et Windows Mixed Reality simulator.
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens, Emulator, Simulation, Windows Mixed Reality, casque de réalité mixte, casque Windows Mixed reality, casque de réalité virtuelle
ms.openlocfilehash: a4e66b2738d5f89949b14fd6f901e2b30dc38cd9e02072f640345d374b9eb9fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217125"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrées avancées dans l’émulateur HoloLens et le simulateur de réalité mixte

la plupart des utilisateurs de l’émulateur devront uniquement utiliser les contrôles d’entrée de base pour le [HoloLens Emulator](using-the-hololens-emulator.md#basic-emulator-input) ou le [simulateur Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Les informations ci-dessous sont destinées aux utilisateurs expérimentés qui ont trouvé besoin de simuler des types d’entrée plus complexes.

## <a name="concepts"></a>Concepts

pour commencer à contrôler l’entrée virtuelle dans le HoloLens Emulator et Windows Mixed Reality simulator, vous devez d’abord comprendre quelques concepts.

Motion fait référence au contrôle et à la modification de la position et de l’orientation d’un événement dans la scène. Pour un objet contrôlable ciblé, motion est contrôlé avec la rotation et la translation (mouvement) sur trois axes.
* **Lacet**: tournez à gauche ou à droite.
* Pas de **hauteur**: activer ou désactiver.
* **Roll**: Roll-to-Side.
* **X**: déplacer vers la gauche ou vers la droite.
* **Y**: monter ou descendre.
* **Z**: déplacer vers l’avant ou vers l’arrière.

Les entrées de contrôle de mouvement et de mouvement sont mappées étroitement aux appareils physiques :
* **Action**: simule l’action d’appui sur le index au curseur ou en tirant le bouton d’action d’un contrôleur. Par exemple, l’entrée d’action peut être utilisée pour simuler le mouvement d’appui sur l’air, pour faire défiler le contenu et pour appuyer et maintenir.
* **[](../../design/system-gesture.md#bloom)geste ou page d’habitation/**: l’HoloLens le geste/le mouvement du système ou le bouton d’hébergement d’un contrôleur est utilisé pour revenir à l’interpréteur de commandes et pour déclencher des actions système.

Les mains ont une représentation riche en HoloLens 2.  En plus de faire l’objet d’un suivi/non suivi et d’être utilisable pour la conduite de mouvements, les mains disposent désormais d’un modèle de squelette articulé qui leur est adapté et exposé au développeur.  Le modèle squelette a 26 points suivis à chaque main.  
* **Joint**: l’une des 20 positions suivies pour une main donnée suivie avec un point associé dans l’espace 3D.
* **Pose**: collection complète de tous les joints dans une main, 26 jointures. 

Nous n’exposent actuellement pas de contrôle direct de la position conjointe individuelle via l’émulateur, mais vous pouvez les définir via l’API de simulation. Nous avons un ensemble de poses représentatifs utiles que l’émulateur vous permet de basculer entre.

Vous pouvez également contrôler l’état de l’entrée de capteur simulé :
* **Réinitialisation**: retourne tous les capteurs simulés à leurs valeurs par défaut.  à partir de la Emulator HoloLens 2, une réinitialisation peut être limitée à une ou deux mains. Faites appel à la ou aux main (s) souhaitée (s) à l’aide des touches de modification ou des boutons (gauche et/ou droit Alt, ou le pare-chocs gauche et/ou droit sur le boîtier de l’option).
* **Suivi**: parcourt les modes de suivi positionnel, y compris :
  * **Valeur par défaut**: le système d’exploitation choisit le mode de suivi le plus approprié en fonction des demandes effectuées sur le système.
   * **Orientation**: force le suivi de l’orientation uniquement, quelle que soit la demande du système.
   * **Positional**: force le suivi positionnel, quelle que soit la demande du système.

## <a name="types-of-input"></a>Types d’entrée

Le tableau suivant montre comment chaque type d’entrée est mappé au clavier, à la souris et au contrôleur Xbox. Chaque type a un mappage différent selon le mode de contrôle d’entrée. Vous trouverez plus d’informations sur les modes de contrôle d’entrée plus loin dans ce document.

| Entrée |  Clavier |  Souris |  Contrôleur Xbox | 
|----------|----------|----------|----------|
|  Lacet |  Flèches gauche/droite |  Faire glisser vers la gauche/droite |  Stick à droite gauche/droite | 
|  Inclinaison |  Flèches haut/bas |  Faire glisser vers le haut/vers le haut |  Joystick droit vers le haut/vers le haut | 
|  Group |  Q/E |  |  DPad gauche/droite | 
|  X |  A/D |  |  Stick analogique gauche vers la gauche/droite | 
|  O |  PG. suiv/PG. suiv |  |  DPad vers le haut/vers le haut | 
|  Z |  W/S |  |  Joystick gauche vers le haut/vers le haut | 
|  Action |  Entrée ou espace |  Bouton droit |  Un bouton ou un déclencheur | 
|  Fleuri/système |  touche F2 ou Windows |  |  Bouton B | 
|  Bouton de poignée du contrôleur/à la main |  G  |  |  | 
|  Bouton de menu contrôleur |  M  |  |  | 
|  Pavé tactile du contrôleur |  U  |  |  | 
|  Appuyez sur le contrôleur Touchpad |  P  |  |  | 
|  Pression du joystick du contrôleur |  K  |  |  | 
|  État du suivi du contrôleur de gauche |  F9 |  |  | 
|  État du suivi du contrôleur approprié |  F10 |  |  | 
|  Poser la main | 7 |  |  |
|  Main « Open » (valeur par défaut) | 8 |  |  |
|  Pose de la main | 9 |  |  |
|  Main « pincer » | 0 |  |  |
|  Réinitialiser |  Touche Échap |  |  Bouton Démarrer | 
|  Suivi |  T ou F3 |  |  Bouton X | 


Remarque : les boutons de contrôleur peuvent être ciblés sur une main ou un contrôleur, ou sur l’autre à l’aide des modificateurs de ciblage de la main.

## <a name="targeting"></a>Ciblage 

Certains des concepts d’entrée ci-dessus sont autonomes.  Action, fleuri/System, Reset et Tracking sont des concepts complets, qui ne sont pas nécessaires et qui ne sont pas affectés par, tous les modificateurs supplémentaires pour le ciblage.  Les autres concepts peuvent être appliqués à une ou plusieurs cibles. Nous avons introduit des moyens de spécifier la cible à laquelle votre commande doit être appliquée.  Dans tous les cas, il est possible de spécifier par le biais de l’interface utilisateur ou par le biais de l’appui sur le clavier, l’objet à cibler.  Dans certains cas, il est également possible de spécifier directement avec le contrôleur Xbox. 

Le tableau suivant décrit les options de ciblage et la manière d’activer chacune d’elles.

| Object | Modificateur de clavier | Modificateur de contrôleur | Emulator Modificateur d’interface utilisateur |
|----------|----------|----------|----------|
| Corps | (par défaut) | (par défaut) | (par défaut) |
| Head | Contenir H | (Non disponible) | (Non disponible) |
| Main gauche/contrôleur | Maintenir le bouton gauche ALT | Bouton conserver l’épaule gauche | Left-Hand punaise | 
| Main droite/contrôleur | Maintenir le bouton droit Alt | Bouton de maintien de l’épaule de droite | Right-Hand punaise |
| Yeux | Conserver Y | (Non disponible) | Punaise yeux |
  
Le tableau suivant montre comment chaque modificateur cible mappe chacun des concepts d’entrée de déplacement de base

| Entrée | Valeur par défaut (corps) |  Main/contrôleur (maintenez la touche Alt enfoncée, maintenez le bouton d’épauler du boîtier ou la punaise de l’interface utilisateur) |  En-tête (Hold H)  |  Yeux (maintenir Y ou basculer l’UI punaise) |
|----------|----------|----------|----------|----------|
|  Lacet |  Transformer le corps vers la gauche/droite |  Déplacer la main vers la gauche/droite |  Activer l’en-tête gauche/droite | Yeux oculaires gauche/droite |
|  Inclinaison |  Activer/désactiver la tête |  Monter/descendre |  Activer/désactiver la tête | Point de regard des yeux | 
|  Group |  Tête de roulement gauche/droite |  |  Tête de roulement gauche/droite | (Aucune action) |
|  X |  Corps de la diapositive vers la gauche/droite |  Déplacer la main/le contrôleur vers la gauche/droite |  Activer l’en-tête gauche/droite | (Aucune action) |
|  O |  Déplacer le corps vers le haut/vers le haut |  Monter/descendre dans la main/le contrôleur |  Activer/désactiver la tête | (Aucune action) |
|  Z |  Déplacer le corps vers l’avant/vers l’arrière |  Déplacer vers l’avant/à l’arrière du contrôleur |  Activer/désactiver la tête | (Aucune action) |
 
 
## <a name="controlling-an-app"></a>Contrôle d’une application

L’ensemble de contrôles suivant est suggéré pour une utilisation quotidienne :

|  Opération |  Clavier et souris |  Contrôleur | 
|----------|----------|----------|
|  Corps X |  A/D |  Stick analogique gauche vers la gauche/droite | 
|  Corps Y |  PG. suiv/PG. suiv |  DPad vers le haut/vers le haut | 
|  Corps Z |  W/S |  Joystick gauche vers le haut/vers le haut | 
|  Lacet de corps |  Faire glisser la souris vers la gauche/droite |  Stick à droite gauche/droite | 
|  Lacet tête |  H + faire glisser la souris vers la gauche/droite |  H (on Keyboard) + Joystick droit gauche/droite | 
|  Hauteur des têtes |  Faire glisser la souris vers le haut/vers le haut |  Joystick droit vers le haut/vers le haut | 
|  Rouleau de tête |  Q/E |  DPad gauche/droite | 
|  Main/contrôleur X |  Alt + A/D |  Épaule + Stick à gauche gauche/droite | 
|  Main/contrôleur Y |  Alt + Pg. suiv/PG. suiv |  Épaule + DPad haut/PG. | 
|  Main/contrôleur Z |  Alt + W/S |  Épauler + joystick gauche vers le haut/vers le haut | 
|  Lacet main/Controller |  Alt + faire glisser la souris vers la gauche/droite |  Épaule + joystick droit gauche/droite | 
|  Hauteur de la main/du contrôleur |  Alt + faire glisser la souris vers le haut/vers le haut |  Haut/bouton de l’épaule + droite | 
|  Rouleau de main/contrôleur |  Alt + Q/E |  Épaule + DPad gauche/droite | 
|  Action |  Bouton droit de la souris |  Déclencheur | 
|  Fleuri/système/page d’hébergement |  touche F2 ou Windows |  Bouton B | 
|  Réinitialiser |  Caractère d'échappement |  Bouton Démarrer | 
|  Suivi |  T |  Bouton X | 
|  Défilement |  Alt + bouton droit de la souris + faire glisser la souris vers le haut/vers le haut |  Épaule + déclencheur + joystick droit vers le haut/vers le haut | 
|  Déplacer/faire pivoter plus rapidement | Touche Maj de gauche ou de droite | Appuyez sur le joystick droit et maintenez-le enfoncé |
|  Déplacer/faire pivoter lentement | Touche CTRL de gauche ou de droite | Appuyez sur le stick analogique gauche et maintenez-le enfoncé |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Utilisation d’un casque immersif et de contrôleurs de mouvement Windows Mixed Reality avec l’émulateur HoloLens 2

lorsque vous utilisez un Windows Mixed Reality casque immersif avec le HoloLens 2 Emulator, le mouvement et la rotation sont automatiquement mappés au mouvement et à la rotation du casque.  La position et l’orientation du contrôleur de mouvement sont automatiquement mappées à la position et à l’orientation de la main dans l’émulateur.  Le tableau ci-dessous répertorie les actions supplémentaires disponibles lors de l’utilisation d’un contrôleur de mouvement.

> [!NOTE]
> Quand vous utilisez un casque, les contrôles standard du clavier, de la souris et du boîtier sont ignorés automatiquement.

|  Opération |  Action |  Notes | 
|----------|----------|----------|
|  Corps X |  Stick analogique gauche/droite |   | 
|  Corps Z |  Stick analogique avant/arrière |   | 
|  Corps Y |  /Down de page de clavier | assurez-vous que Windows Mixed Reality a le focus.  appuyez sur Win + Y si le focus se trouve sur le bureau de Windows pour ramener le focus sur Windows Mixed Reality. |
|  Yeux regarder à gauche/à droite |  DPad gauche/droite | |
|  Recherche de yeux vers le haut/vers le haut | DPad vers le haut/vers le haut | |
|  Taper | Déclencheur | |
|  Pincer/comprendre | Bouton de poignée | |
|  Mouvement système | Bouton Menu | |
|  Rétablir la position | Clic Stick | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Raccourcis clavier du panneau de configuration de la perception

Vous pouvez accéder au panneau de configuration de la simulation de perception et activer ou désactiver les périphériques d’entrée de PC avec les raccourcis clavier suivants.

| Opération | Raccourci | Description/remarques |
|-----------|----------|-------------|
| Activer/désactiver le clavier pour la simulation | F4 | lorsque cette option est désactivée, l’entrée au clavier est insérée dans l’application HoloLens ou Windows Mixed Reality. |
| Activer l’utilisation de la souris pour la simulation | F5 | lorsqu’elle est désactivée, l’entrée de la souris passe à l’environnement de réalité mixte (Windows Mixed Reality uniquement) |
| Activer/désactiver le boîtier d’activation pour la simulation | F6 | Lorsqu’elle est désactivée, l’entrée du boîtier est ignorée par la simulation |
| Afficher ou masquer le panneau de configuration | F7 | |
| Définir le focus clavier sur le panneau de configuration | F8 | Si le panneau n’est pas actuellement visible, il est affiché en premier. |
| Ancrer ou détacher le panneau vers/depuis la fenêtre du portail de l’émulateur ou de la réalité mixte | F9 | Si la fenêtre est fermée lorsqu’elle est désancrée, elle est ancrée et masquée. |

## <a name="see-also"></a>Voir aussi
* [Installer les outils](../install-the-tools.md)
* [Utilisation de l’émulateur HoloLens](using-the-hololens-emulator.md)
* [Utilisation du simulateur Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
