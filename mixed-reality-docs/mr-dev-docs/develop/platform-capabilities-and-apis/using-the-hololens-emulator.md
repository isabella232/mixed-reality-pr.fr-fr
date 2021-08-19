---
title: Utilisation de l’émulateur HoloLens
description: Découvrez comment utiliser l’émulateur HoloLens pour tester des applications de réalité mixte sur votre PC sans un appareil HoloLens physique.
author: hamalawi
ms.author: moelhama
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, émulateur
ms.openlocfilehash: e8bad509a4714d693c51682be73f1523bf05bd30
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905649"
---
# <a name="using-the-hololens-emulator"></a>Utilisation de l’émulateur HoloLens

L’émulateur HoloLens vous permet de tester des applications holographiques sur votre PC sans avoir besoin d’un appareil HoloLens physique. Il est fourni avec l’ensemble d’outils de développement HoloLens. L’émulateur utilise une machine virtuelle Hyper-V, ce qui signifie que les entrées utilisateur et environnementales qui sont lues par les capteurs HoloLens sont simulées à partir de votre clavier, de votre souris ou de votre manette Xbox. Vous n’avez même pas besoin de modifier vos projets pour qu’ils s’exécutent sur l’émulateur, car l’application ne sait pas qu’elle n’est pas exécutée sur un véritable appareil HoloLens.

Si vous devez développer des applications ou jeux avec casques immersifs de réalité mixte Windows (VR) pour les ordinateurs de bureau, essayez le [simulateur de réalité mixte Windows](using-the-windows-mixed-reality-simulator.md), qui vous permet de simuler des casques de bureau.

## <a name="hololens-2-emulator-overview"></a>Vue d’ensemble de l’émulateur HoloLens 2

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/HoloLens-2-Emulator-Overview/player?format=ny]

## <a name="installing-the-hololens-emulator"></a>Installation de l’émulateur HoloLens
Téléchargez l’émulateur HoloLens.

Versions :
* [Émulateur HoloLens 2 (Windows Holographique, version 21H1, mise à jour d’août 2021)](https://go.microsoft.com/fwlink/?linkid=2169418).
* [Émulateur HoloLens (1re génération) et modèles de projet holographiques](https://go.microsoft.com/fwlink/?linkid=2065980).

Des notes de publication et des versions antérieures de l’émulateur HoloLens sont disponibles dans la page [Archive de l’émulateur HoloLens](hololens-emulator-archive.md).

### <a name="hololens-emulator-system-requirements"></a>Configuration requise pour l’émulateur HoloLens

L’émulateur HoloLens utilise Hyper-V avec RemoteFx (émulateur 1re génération) ou GPU-PV (émulateur HoloLens 2) pour l’affichage graphique accéléré matériel. Pour utiliser l’émulateur, assurez-vous que votre PC présente la configuration matérielle suivante :
* Windows 10 Professionnel, Entreprise ou Éducation 64 bits
    >[!NOTE]
    >Windows 10 Édition familiale ne prend en charge ni Hyper-V ni l’émulateur HoloLens.  
    >L’émulateur HoloLens 2 nécessite la mise à jour de Windows 10 d’octobre 2018 ou une version ultérieure.
* Processeur 64 bits
* Processeur avec quatre cœurs (ou plusieurs processeurs avec un total de quatre cœurs)
* 8 Go de RAM minimum
* Dans le BIOS, les fonctionnalités suivantes doivent être [prises en charge et activées](/archive/blogs/iftekhar/enable-hardware-settings-in-bios-to-run-hyper-v) :
   * Virtualisation assistée par le matériel
   * Traduction d’adresse de second niveau (SLAT, Second Level Address Translation)
   * Prévention de l’exécution des données au niveau matériel (DEP, Data Execution Prevention)
* Configuration du GPU
   * DirectX 11.0 ou version ultérieure
   * Pilote graphique WDDM 1.2 ou ultérieur (1re génération)
   * Pilote graphique WDDM 2.5 (émulateur HoloLens 2)
   * L’émulateur peut éventuellement fonctionner avec un GPU non pris en charge, mais il sera plus lent

Si votre système répond à la configuration requise indiquée ci-dessus, **vérifiez que la fonctionnalité « Hyper-V » a été activée sur votre système**. Accédez à **Panneau de configuration > Programmes > Programmes et fonctionnalités > Activer ou désactiver des fonctionnalités Windows** et vérifiez que **Hyper-V** est sélectionné.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Déploiement d’applications dans l’émulateur HoloLens

1. Chargez votre solution d’application dans Visual Studio.
    >[!NOTE]
    >Si vous utilisez Unity, générez votre projet à partir de Unity, puis chargez la solution générée dans Visual Studio comme vous le faites habituellement.
2. Pour l’émulateur HoloLens (1re génération), vérifiez que cette plateforme est configurée sur **x86**. Pour l’émulateur HoloLens 2, vérifiez que la plateforme est configurée sur **x86** ou **x64**.
3. Sélectionnez la version de l’**émulateur HoloLens** à utiliser comme appareil cible pour le débogage.
4. Accédez à **Déboguer > Démarrer le débogage** ou appuyez sur **F5** pour lancer l’émulateur et déployer votre application en vue du débogage.

Le lancement de l’émulateur peut prendre une minute ou plus au premier démarrage. Nous vous recommandons de laisser l’émulateur ouvert durant votre session de débogage afin d’y déployer rapidement des applications.

## <a name="basic-emulator-input"></a>Entrées de base de l’émulateur

Le contrôle de l’émulateur s’apparente au contrôle de la plupart des jeux vidéo 3D courants. Des options d’entrée sont disponibles pour utiliser le clavier, la souris ou une manette Xbox. Vous contrôlez l’émulateur en dirigeant les actions d’un utilisateur simulé qui porte un casque HoloLens. Vos actions déplacent l’utilisateur simulé dans l’environnement. Les applications qui s’exécutent dans l’émulateur réagissent comme elles le feraient sur un appareil réel.

Le curseur sur HoloLens (1re génération) suit le mouvement et la rotation de la tête. Dans l’émulateur HoloLens 2, le curseur suit le mouvement et l’orientation de la main.

* **Marcher vers l’avant, l’arrière, la gauche et la droite** : utilisez les touches W, A, S et D du clavier, ou le stick gauche d’une manette Xbox.
* **Regarder vers le haut, le bas, la gauche et la droite** : sélectionnez et faites glisser la souris, utilisez les touches de direction du clavier ou utilisez le stick droit d’une manette Xbox.
* **Clic aérien** : cliquez avec le bouton droit de la souris, appuyez sur la touche Entrée du clavier ou utilisez le bouton A d’une manette Xbox.
* **Écarter les doigts paume vers le haut/Mouvement système** : appuyez sur la touche Windows ou la touche F2 du clavier, ou appuyez sur le bouton B d’une manette Xbox.
* **Mouvement de la main pour faire défiler** : maintenez simultanément enfoncés la touche Alt et le bouton droit de la souris et faites glisser la souris vers le haut ou le bas. Sur une manette Xbox, maintenez la gâchette droite et le bouton A enfoncés et déplacez le stick droit vers le haut et le bas.
* **Mouvement de la main et orientation** (émulateur HoloLens 2 uniquement) : maintenez la touche Alt enfoncée et faites glisser la souris vers le haut ou le bas, la gauche ou la droite pour déplacer la main. Vous pouvez également utiliser les touches de direction et Q ou E pour faire pivoter et incliner la main. Sur une manette Xbox, maintenez la gâchette gauche ou droite enfoncée et utilisez le joystick gauche pour déplacer la main vers la gauche, la droite, l’avant et l’arrière, utilisez le joystick droit pour faire pivoter la main. Utilisez les boutons haut ou bas sur le D-pad pour lever ou abaisser la main.

Vous avez un casque immersif Windows Mixed Reality ?  À compter de l’émulateur HoloLens 2 (Windows Holographique, version 2004), vous pouvez utiliser votre casque immersif et vos contrôleurs de mouvement Windows Mixed Reality pour contrôler l’émulateur HoloLens 2 et le voir en stéréoscopie.  Consultez [Utilisation d’un casque immersif et de contrôleurs de mouvement Windows Mixed Reality avec l’émulateur HoloLens 2](#using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator).

## <a name="anatomy-of-the-hololens-2-emulator"></a>Anatomie de l’émulateur HoloLens 2

### <a name="main-window"></a>Fenêtre principale

![Fenêtre principale de l’émulateur HoloLens 2](images/emulator2-900px.png)

### <a name="toolbar"></a>Barre d’outils

La barre d’outils de l’émulateur se trouve à droite de la fenêtre principale. Elle comporte les boutons suivants :
* ![Icône Fermer](images/emulator-close.png) **Fermer** : ferme l’émulateur.
* ![Icône Réduire](images/emulator-minimize.png) **Réduire** : réduit la fenêtre de l’émulateur.
* ![Icône Simulation](images/emulator-simulation-panel.png) **Panneau de configuration Simulation** : affiche ou masque le [panneau de configuration Simulation](#simulation-control-panel) pour configurer et contrôler les [entrées vers l’émulateur](#basic-emulator-input).
* ![Icône Ajuster à l’écran](images/emulator-fit.png) **Ajuster à l’écran** : adapte l’émulateur à l’écran.
* ![Icône Zoom](images/emulator-zoom.png) **Zoom** : augmente ou réduit la taille de l’émulateur.
* ![Icône Aide](images/emulator-help.png) **Aide** : ouvre l’aide de l’émulateur.
* ![Icône Ouvrir le Portail d’appareil](images/emulator-deviceportal.png) **Ouvrir le Portail d’appareil** : ouvre le Portail d’appareil Windows pour le système d’exploitation HoloLens dans l’émulateur.
* ![Icône Outils](images/emulator-tools.png) **Outils** : ouvre le volet **Outils supplémentaires**.

### <a name="simulation-control-panel"></a>Panneau de configuration Simulation

Le panneau de configuration Simulation affiche la position et l’orientation actuelles des périphériques d’interface utilisateur et des périphériques d’entrée simulés. Il permet également de configurer des entrées simulées, comme montrer ou cacher une main ou les deux mains, ainsi que des appareils utilisés pour contrôler les entrées simulées tels que le clavier, la souris et la manette de votre PC.

![Panneau de configuration Simulation](images/emulator-simulation-control-panel.png)

* Pour afficher ou masquer le panneau de simulation, sélectionnez le bouton de barre d’outils ou appuyez sur F7 sur le clavier.
* Pointez avec la souris sur un contrôle ou un champ pour afficher une info-bulle qui contient les contrôles associés du clavier, de la souris et de la manette.
* Pour montrer ou cacher une main, activez le contrôle approprié sous Main gauche ou Main droite.
* Pour contrôler la main, utilisez les touches Alt gauche ou droite du clavier, ou la gâchette gauche ou droite de la manette.
* Pour diriger toutes les entrées vers une main ou les deux mains, sélectionnez le bouton punaise sous le bouton bascule (ce qui revient à maintenir la touche Alt enfoncée pour la main).
* Pour contrôler la direction du regard, sélectionnez la punaise dans la section Yeux (ce qui revient à maintenir la touche Y du clavier enfoncée).
* Pour charger l’enregistrement d’une pièce, sélectionnez le bouton Charger dans la section Enregistrement. Pour plus d’informations, consultez [Pièces simulées](#simulated-rooms).
* Pour ajuster la vitesse de déplacement ou de rotation des périphériques d’interface utilisateur ou des périphériques d’entrée simulés en réponse à une entrée du clavier, de la souris ou d’une manette, sélectionnez l’icône d’engrenage à côté de Paramètres d’entrée et réglez les curseurs.
* Par défaut, les entrées clavier contrôlent les périphériques d’interface utilisateur simulés et les périphériques d’entrée simulés. Pour envoyer les entrées clavier de votre PC à HoloLens, décochez la case Utiliser le clavier pour la simulation. F4 est la touche de raccourci pour ce paramètre.
* Si vous voyez déjà le panneau de simulation, appuyez sur la touche F8 pour y déplacer le focus clavier.
* Pour détacher le panneau de simulation de la fenêtre de l’émulateur, sélectionnez le bouton en bas du panneau ou appuyez sur la touche F9 du clavier.  Si vous fermez la fenêtre ou réappuyez sur F9, vous revenez dans la fenêtre de l’émulateur.
* Le Panneau de configuration Simulation peut être lancé comme une application distincte. Dans ce cas, vous pouvez connecter et contrôler l’émulateur HoloLens 2, un appareil HoloLens 2 ou une simulation de réalité mixte Windows en exécutant PerceptionSimulationInput.exe à partir du dossier %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>Onglet Compte

L’onglet Compte permet de configurer l’émulateur pour la connexion avec un compte Microsoft. Cela est utile pour tester des API qui demandent à l’utilisateur de se connecter avec un compte. Après avoir activé ou désactivé cette option, vous devez fermer et redémarrer entièrement l’émulateur HoloLens pour que le paramètre de configuration prenne effet. Si cette option est activée, vous serez invité à vous connecter à chaque lancement de l’émulateur (au même titre qu’un utilisateur au premier démarrage d’HoloLens). Pour entrer vos informations d’identification à l’aide du clavier de votre PC, décochez d’abord l’option Utiliser le clavier pour la simulation dans le Panneau de configuration Simulation, ou appuyez sur la touche F4 du clavier pour activer ou désactiver le paramètre du clavier.

### <a name="optional-settings-tab"></a>Onglet Paramètres facultatifs

L’onglet Paramètres facultatifs affiche un contrôle permettant d’activer ou de désactiver l’affichage graphique accéléré matériel. L’affichage graphique accéléré matériel est utilisé par défaut s’il est pris en charge par le pilote de carte graphique de votre PC. Si le pilote de votre carte graphique ne prend pas en charge GPU-PV, cette option n’est pas proposée.

### <a name="diagnostics-tab"></a>Onglet Diagnostics

L’onglet Diagnostics affiche l’adresse IP de l’émulateur sous la forme d’un lien vers le Portail d’appareil Windows, ainsi que l’état du GPU virtuel.

### <a name="network-tab"></a>Onglet Réseau

L’onglet Réseau affiche les détails de la carte réseau de l’émulateur, ainsi que ceux de la carte réseau de l’ordinateur hôte. Pour l’émulateur HoloLens 2, cet onglet apparaît uniquement lors de l’exécution de l’émulateur sur la mise à jour de mai 2019 de Windows 10 ou une version plus récente.

### <a name="nat-configuration-tab"></a>Onglet Configuration NAT

Cet onglet apparaît uniquement lors de l’exécution de l’émulateur sur la mise à jour de mai 2019 de Windows 10 ou une version plus récente.

L’émulateur utilise la connexion réseau de votre PC et se trouve derrière un NAT.  Cet onglet vous permet de mapper les ports de votre ordinateur hôte sur l’émulateur, ce qui permet aux appareils distants de se connecter aux applications et services s’exécutant dans l’émulateur.

Par exemple, si vous souhaitez accéder au Portail d’appareil sur l’émulateur à partir d’un PC distant :

1. Ajoutez une entrée pour le port interne 80 (port sur lequel le Portail d’appareil écoute) en double-cliquant sur une ligne libre dans le tableau.  Pour d’autres applications, entrez le numéro de port sur lequel l’application écoute.
2. Choisissez n’importe quel port externe disponible.  Dans cet exemple, nous allons utiliser le port 8080 comme port externe.
3. Sélectionnez le protocole.  Le protocole par défaut est TCP.  Étant donné que le Portail d’appareil utilise le protocole TCP, nous allons garder cette valeur par défaut.
4. Cliquez sur « Appliquer les modifications » pour activer le mappage.  La valeur « Statut » passe de « En attente » à « Actif ».
5. Sur l’ordinateur distant, ouvrez un navigateur et accédez à (Adresse_IP_du_PC_exécutant_l’émulateur):8080.  L’interface du Portail d’appareil s’affiche.  L’adresse IP que vous utilisez sur un PC distant doit être celle du PC exécutant l’émulateur, et non celle de l’émulateur lui-même.  Vous pouvez récupérer l’adresse IP par le biais de différentes méthodes : l’application Paramètres sur le PC dans la catégorie « Réseau et Internet », « ipconfig » à partir d’une invite de commandes, onglet Réseau de la boîte de dialogue Outils de l’émulateur en recherchant l’entrée Carte réseau de l’ordinateur.

Notez également que si vous ajoutez un mappage de port pour le Portail d’appareil, vous pouvez contrôler l’émulateur à distance à l’aide de l’outil de contrôle de simulation de perception inclus dans l’installation de l’émulateur ou avec les API de simulation de perception en vous connectant à l’adresse IP de l’ordinateur hôte et au port externe du Portail d’appareil, comme le port 8080 dans l’exemple ci-dessus.  Quand vous utilisez le contrôle de simulation de perception pour vous connecter à l’émulateur et le contrôler à distance, spécifiez uniquement l’adresse IP du PC et le port configuré.  N’incluez pas « https:// ».

Par défaut, il n’existe aucun mappage de port.  Tous les mappages que vous configurez persistent au lancement de l’émulateur HoloLens 2 et s’activent automatiquement une fois que l’émulateur a complètement démarré.

Utilisez le bouton « Exporter » pour enregistrer vos mappages dans un fichier.  Vous pouvez ensuite partager ce fichier avec d’autres membres d’équipe qui peuvent alors utiliser le bouton « Importer » pour configurer automatiquement les mêmes mappages.

![Onglet Configuration NAT de l’émulateur HoloLens](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>Onglet Mises à jour

Cet onglet apparaît uniquement lors de l’exécution de l’émulateur sur la mise à jour de mai 2019 de Windows 10 ou une version plus récente.

Au démarrage, l’émulateur recherche les nouvelles versions.  Si une nouvelle version est disponible, l’émulateur présente une invite indiquant la version dont vous disposez, ainsi que la version disponible, et vous demandant si vous souhaitez procéder à la mise à jour.  Si vous sélectionnez « Oui », le programme d’installation de la nouvelle version est téléchargé.

L’onglet Mises à jour vous permet de contrôler si l’émulateur vérifie ou non l’existence de nouvelles versions. Pour cela, cochez ou non la case « Rechercher automatiquement les mises à jour » sous cet onglet.  Il vous permet également de voir et de télécharger d’autres versions de l’émulateur disponibles, à commencer par la mise à jour de septembre 2019.  Pour les versions autres que celle en cours d’exécution, un lien de téléchargement est fourni.  Cliquez sur ce lien pour télécharger le programme d’installation de la version correspondante.

![Onglet « Mises à jour » de l’émulateur HoloLens](images/emulator-updates-500px.png)

### <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Utilisation d’un casque immersif et de contrôleurs de mouvement Windows Mixed Reality avec l’émulateur HoloLens 2

À compter de l’émulateur HoloLens 2 (Windows Holographique, version 2004), vous pouvez utiliser un casque et des contrôleurs de mouvement Windows Mixed Reality pour voir l’émulateur HoloLens 2 et interagir avec celui-ci en stéréoscopie.  Vous pouvez ainsi faire des mouvements plus rapides et plus naturels avec votre tête et vos mains sans appareil HoloLens 2.  L’objectif n’est pas de remplacer entièrement un appareil HoloLens 2, mais de vous proposer une méthode d’interaction avec l’émulateur autre que le clavier, la souris et la manette dans une fenêtre de bureau 2D pour améliorer votre expérience.  Pour activer cette fonctionnalité :

1. Vérifiez que Windows Mixed Reality est configuré sur votre PC et que votre casque immersif Windows Mixed Reality est connecté.
2. Lancez l’émulateur HoloLens 2.
3. Ouvrez le panneau Simulation en cliquant sur le bouton de la barre d’outils ou en appuyant sur F7.
4. Faites défiler le panneau vers le bas.
5. Cochez la case « Utiliser HMD pour la simulation ».
6. Windows Mixed Reality démarre et l’affichage de l’émulateur change légèrement.  Sans casque, l’émulateur place les deux yeux au centre de la tête et n’affiche qu’un œil.  Avec un casque, l’émulateur génère une véritable sortie stéréoscopique. Un seul œil est rendu sur la fenêtre de bureau, mais les deux yeux sont rendus sur votre casque.
7. Activez éventuellement un contrôleur de mouvement ou les deux.  L’entrée du contrôleur est mappée à l’entrée de la main dans l’émulateur.  Par exemple, pour appuyer, pressez la gâchette du contrôleur de mouvement.  Pour vous déplacer, utilisez le joystick.  Pour obtenir la liste complète des contrôles, consultez [Entrées avancées dans l’émulateur HoloLens et le simulateur de réalité mixte](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)

Vous avez du mal à voir le contenu dans votre casque ?

- Si rien ne s’affiche dans le casque et dans le portail de réalité mixte, mais que vous voyez du contenu dans la fenêtre de l’émulateur HoloLens 2 sur votre bureau, vérifiez que l’accélération graphique matérielle est activée dans l’émulateur.  La prise en charge du casque immersif Windows Mixed Reality nécessite l’activation de l’accélération graphique matérielle dans l’émulateur.
- Si du contenu apparaît dans le casque, mais que les hologrammes sont flous ou que vous voyez une image double, effectuez les étapes suivantes pour ajuster l’affichage stéréoscopique pour vos yeux :

1. Désactivez temporairement « Utiliser HMD pour la simulation ».
2. Lancez l’Éditeur du Registre (regedit.exe).
3. Accédez à HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation.
4. Créez une valeur DWORD nommée « EnableEyePoseControl » égale à 1.
5. Activez « Utiliser HMD pour la simulation » dans l’émulateur.
6. Quand du contenu apparaît dans le casque, utilisez les touches de direction pour ajuster la rotation des yeux.  Maintenez la touche Alt gauche enfoncée pour ajuster l’œil gauche et maintenez la touche Alt droite enfoncée pour ajuster l’œil droit.  Utilisez « Q » et « E » pour ajuster le roulis de chaque œil (en maintenant la touche Alt appropriée enfoncée).  Utilisez les touches « + » et « - » pour ajuster la distance entre les yeux.  (Notez que les touches +/- du pavé numérique ne fonctionnent pas.  Utilisez celles du clavier principal.)
7. Quand la vue stéréoscopique semble correcte, appuyez sur « S » pour enregistrer vos changements.  La nouvelle configuration est enregistrée pour les prochains lancements de l’émulateur.
8. Si vous souhaitez abandonner vos changements et revenir à la configuration précédente, appuyez sur « L » pour charger la configuration par défaut ou précédente.
9. Remplacez la valeur de « EnableEyePoseControl » dans le Registre par 0 et désactivez/activez l’option « Utiliser HMD pour la simulation ».

Si vous avez enregistré une configuration dont vous n’avez plus besoin, vous pouvez supprimer la valeur nommée « DisplayConfiguration » à l’emplacement HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation.  Si vous utilisez actuellement le casque avec l’émulateur, vous devez désactiver l’option « Utiliser HMD pour la simulation » et la réactiver pour que ce changement prenne effet.

## <a name="anatomy-of-the-hololens-first-gen-emulator"></a>Anatomie de l’émulateur HoloLens (1re génération)

### <a name="main-window"></a>Fenêtre principale

Quand l’émulateur démarre, vous voyez une fenêtre qui présente le système d’exploitation HoloLens.

![Fenêtre principale de l’émulateur HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barre d’outils

La barre d’outils de l’émulateur se trouve à droite de la fenêtre principale. Elle comporte les boutons suivants :
* ![Icône Fermer](images/emulator-close.png) **Fermer** : ferme l’émulateur.
* ![Icône Réduire](images/emulator-minimize.png) **Réduire** : réduit la fenêtre de l’émulateur.
* ![Icône Entrées utilisateur](images/emulator-control.png) **Entrées utilisateur** : le clavier et la souris permettent de simuler les [entrées utilisateur passées à l’émulateur](#basic-emulator-input).
* ![Icône Entrées clavier et souris](images/emulator-input.png) **Entrées clavier et souris** : les entrées clavier et souris sont passées directement au système d’exploitation HoloLens en tant qu’événements clavier et souris, comme si vous aviez connecté un clavier et une souris Bluetooth.
* ![Icône Ajuster à l’écran](images/emulator-fit.png) **Ajuster à l’écran** : adapte l’émulateur à l’écran.
* ![Icône Zoom](images/emulator-zoom.png) **Zoom** : augmente ou réduit la taille de l’émulateur.
* ![Icône Aide](images/emulator-help.png) **Aide** : ouvre l’aide de l’émulateur.
* ![Icône Ouvrir le Portail d’appareil](images/emulator-deviceportal.png) **Ouvrir le Portail d’appareil** : ouvre le Portail d’appareil Windows pour le système d’exploitation HoloLens dans l’émulateur.
* ![Icône Outils](images/emulator-tools.png) **Outils** : ouvre le volet **Outils supplémentaires**.

### <a name="simulation-tab"></a>Onglet Simulation

L’onglet **Simulation** est l’onglet par défaut dans le volet **Outils supplémentaires**.

![Volet « Outils supplémentaires » de l’émulateur HoloLens](images/emulator-simulation-500px.png)

L’onglet Simulation affiche l’état actuel des capteurs simulés utilisés pour piloter le système d’exploitation HoloLens dans l’émulateur. Quand vous pointez avec la souris sur une valeur dans l’onglet Simulation, une info-bulle s’affiche pour indiquer comment contrôler cette valeur.

### <a name="room-tab"></a>Onglet Pièce

L’émulateur simule des entrées à l’échelle mondiale sous la forme d’un maillage de mappage spatial à partir de pièces simulées. Cet onglet vous permet de choisir la pièce à charger à la place de la pièce par défaut.

![Onglet « Pièces » de l’émulateur HoloLens](images/emulator-room-500px.png)

Pour plus d’informations, consultez [Pièces simulées](#simulated-rooms).

### <a name="account-tab"></a>Onglet Compte

L’onglet Compte permet de configurer l’émulateur pour la connexion avec un compte Microsoft. Cela est utile pour tester des API qui demandent à l’utilisateur de se connecter avec un compte. Si l’option est activée dans cette page, vous serez invité à vous connecter à chaque lancement de l’émulateur (au même titre qu’un utilisateur au premier démarrage d’HoloLens).

## <a name="simulated-rooms"></a>Pièces simulées

Les pièces simulées sont utiles pour tester votre application dans différents environnements. Plusieurs pièces sont fournies avec l’émulateur. Une fois que vous avez installé l’émulation, vous pouvez trouver ces pièces dans le dossier %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms. Toutes ces pièces ont été capturées dans des environnements réels à l’aide d’un système HoloLens :

* **DefaultRoom.xef** : petit salon avec un téléviseur, une table basse et deux canapés. Pièce chargée par défaut au démarrage de l’émulateur.
* **Bedroom1.xef** : petite chambre équipée d’un bureau.
* **Bedroom2.xef** : chambre contenant un grand lit double, une commode, une table de nuit et un dressing.
* **GreatRoom.xef** : vaste pièce à vivre ouverte avec salon, table à manger et cuisine.
* **LivingRoom.xef** : salon avec une cheminée, un canapé, des fauteuils et une table basse ornée d’un vase.

Vous pouvez également enregistrer vos propres pièces à utiliser dans l’émulateur à partir de la page Simulation du [Portail d’appareil Windows](using-the-windows-device-portal.md) sur votre HoloLens (1re génération).

Dans l’émulateur, vous voyez uniquement les hologrammes que vous affichez. Mais vous ne voyez pas la pièce simulée derrière les hologrammes. C’est la différence avec le véritable HoloLens, où vous voyez les deux simultanément. Si vous souhaitez voir la pièce simulée dans l’émulateur HoloLens, vous devez mettre à jour votre application pour qu’elle affiche le maillage du mappage spatial dans la scène.

## <a name="known-issues"></a>Problèmes connus

* Lors de la désinstallation de l’émulateur HoloLens 2, l’image de disque dur (Flash.vhdx) peut rester sur votre disque dur dans le dossier Windows Kits\10\Emulation\HoloLens\<build number>.  Vous pouvez supprimer ce fichier sans risque.
* L’accélération graphique matérielle peut provoquer le plantage des applications holographiques sur certains systèmes avec des graphiques AMD ou Intel.  Pour contourner ce problème, désactivez l’accélération graphique matérielle dans la fenêtre Outils de l’émulateur.
* Après l’installation des dernières mises à jour Windows en juillet 2020, l’accélération graphique matérielle de l’émulateur HoloLens (1re génération) risque de ne plus être disponible.
Le composant RemoteFX nécessaire à l’accélération graphique matérielle est déprécié et sera supprimé dans une prochaine version de Windows.  Pour réactiver l’accélération graphique matérielle, utilisez l’applet de commande PowerShell [Enable-VMRemoteFXPhysicalVideoAdapter](/powershell/module/hyper-v/enable-vmremotefxphysicalvideoadapter).  Pour plus d’informations, consultez la [documentation sur la dépréciation et la suppression de la prise en charge de RemoteFX dans Windows](https://support.microsoft.com/help/4570006/update-to-disable-and-remove-the-remotefx-vgpu-component).

## <a name="troubleshooting"></a>Résolution des problèmes

Lors de l’installation de l’émulateur, vous pouvez rencontrer un message d’erreur indiquant que vous devez utiliser *« Visual Studio 2015 Update 1 et les outils UWP version 1.2 »* . Cette erreur a trois causes possibles :
* Vous n’avez pas une version suffisamment récente de Visual Studio (Visual Studio 2019, Visual Studio 2017 ou Visual Studio 2015 Update 1 ou ultérieur). Pour corriger ce problème, installez la dernière version de Visual Studio.
* Vous avez une version récente de Visual Studio, mais vous n’avez pas installé les outils UWP. Il s’agit d’une fonctionnalité facultative pour Visual Studio. Pour HoloLens (1re génération), vous avez besoin des outils UWP pour Visual Studio 2015 ou Visual Studio 2017.

Vous pouvez également voir une erreur si vous installez l’émulateur sur une machine n’ayant pas le SKU Entreprise/Professionnel/Éducation de Windows ou sur laquelle la fonctionnalité Hyper-V n’est pas activée.
* Lisez la section ci-dessus sur la [configuration système requise](#hololens-emulator-system-requirements) pour connaître l’ensemble complet des composants requis.
* Vérifiez également que la fonctionnalité Hyper-V a été activée sur votre système.

Si votre installation s’est déroulée correctement, mais que vous ne voyez pas l’émulateur HoloLens comme option de déploiement et de débogage :
* Votre projet Visual Studio est configuré sur x86 (HoloLens 1re génération), x86 ou x64 (émulateur HoloLens 2).
* Si vous utilisez Visual Studio 2019, l’ensemble d’outils de plateforme dans votre configuration de projet est défini sur v142.

Si votre installation s’est déroulée correctement, mais que Visual Studio affiche une erreur lors de la tentative de lancement de l’émulateur HoloLens :
* Exécutez Visual Studio en tant qu’administrateur.
* Si vous n’avez jamais installé d’autre version que Visual Studio 2019, vérifiez que la valeur de Registre « KitsRoot10 » dans HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots pointe vers votre dossier Program Files 32 bits (par exemple, « C:\Program Files (x86)\Windows Kits\10 »).  Si ce n’est pas le cas, désinstallez l’émulateur HoloLens, changez la valeur de Registre pour pointer vers votre dossier Program Files 32 bits, puis réinstallez l’émulateur HoloLens.  Ce problème est résolu dans Visual Studio 2019 16.0.3.

Si l’émulateur affiche une boîte de dialogue d’erreur « Encodage en octets non valide » au lancement :
* Supprimez tous les fichiers %localappdata%\Microsoft\XDE\HCS et réessayez.

Si votre liste de cible de débogage dans Visual Studio est vide (par exemple, Démarrer est la seule option) et que vous avez suivi toutes les étapes de dépannage ci-dessus :
* Supprimez le dossier ConfigurationCache dans %localappdata%\Microsoft\VisualStudio\\<*id installation*>\CoreCon et réessayez.

Si votre système plante au démarrage de l’émulateur, désactivez l’accélération matérielle pour les graphiques de l’émulateur.
* Créez une valeur de Registre DWORD nommée « DisableGPU » dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 et définissez-la sur 1.

## <a name="see-also"></a>Voir aussi
* [Entrées avancées dans l’émulateur HoloLens et le simulateur de réalité mixte](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Archive des versions de l’émulateur HoloLens](hololens-emulator-archive.md)
* [Mappage spatial dans Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Mappage spatial dans DirectX](../../develop/native/spatial-mapping-in-directx.md)