---
title: Utilisation de SteamVR avec Windows Mixed Reality
description: découvrez comment configurer et jouer des jeux SteamVR sur Windows Mixed Reality casques et contrôleurs avec des pc compatibles.
author: qianw211
ms.author: v-qianwen
ms.date: 9/23/2021
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, jeux, SteamVR, Steam, configuration système requise
ms.openlocfilehash: b06c5e0b9918a5277a2c31e391dbdbc1ef740110
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436713"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Utilisation de SteamVR avec Windows Mixed Reality

Windows Mixed Reality pour SteamVR permet aux utilisateurs d’exécuter des expériences SteamVR sur Windows Mixed Reality des casques immersifs. après l’installation du Windows Mixed Reality pour SteamVR, les utilisateurs peuvent lancer leurs applications SteamVR favorites à partir de leur bureau ou de la bibliothèque de vapeur et les lire directement sur leur casque Windows.

## <a name="get-your-pc-ready"></a>Préparez votre ordinateur

* vérifiez que vous n’avez aucune mise à jour en attente : sélectionnez **démarrer > Paramètres > mettre à jour & sécurité > Windows Update**. Si des mises à jour sont disponibles, sélectionnez **Installer maintenant**. Si aucune mise à jour n’est disponible, sélectionnez **Rechercher les mises à jour**, puis installez-en d’autres.
* Les exigences du PC varient pour les applications et le contenu sur la vapeur. Consultez la configuration minimale requise par titre. Un PC doté d’une carte graphique GTX 1070 (ou équivalente) et d’un processeur Intel® Core™ i7 doit offrir une bonne expérience pour un large éventail de titres.
* configurez [Windows Mixed Reality](set-up-windows-mixed-reality.md) si vous ne l’avez pas déjà fait. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>configurer Windows Mixed Reality pour SteamVR

1. [Téléchargez et installez SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. Quand vous êtes prêt, démarrez SteamVR. Le didacticiel SteamVR doit démarrer automatiquement.

> **Remarque :** Pour un dépannage avancé de votre configuration SteamVR, vérifiez que les composants logiciels suivants sont installés :
> 1. Installez [Steam](http://store.steampowered.com/about/) et **Connectez** -vous ou **créez un nouveau compte.**
> 2. Installez [SteamVR](https://store.steampowered.com/app/250820/SteamVR/). Une fois votre casque branché, lancez la vapeur. vous devriez voir une boîte de dialogue vous invitant à installer SteamVR. Suivez les invites de la boîte de dialogue pour l’installer.
    * Si vous ne voyez pas la fenêtre contextuelle, installez SteamVR en accédant à la section *Outils* de votre *bibliothèque*. Recherchez SteamVR dans la liste, puis cliquez avec le bouton droit et sélectionnez *installer le jeu*.
> 3. installez [Windows Mixed Reality pour SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>configurer Windows Mixed Reality pour SteamVR dans un environnement sans accès à internet

**Stockage des médias nécessaires sur un dispositif de stockage portable**
1. installez [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) et [Windows Mixed Reality pour SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) comme indiqué ci-dessus à l’aide de [vapeur](http://store.steampowered.com/about/) sur un PC disposant d’un accès internet complet.
2. Dans Steam, ouvrez la section Bibliothèque et recherchez la partie intitulée « outils ».
3. Une fois SteamVR installé, cliquez avec le bouton droit sur l’entrée « SteamVR » et dans le menu contextuel qui s’est produit, cliquez sur l’entrée « propriétés ».
4. Une nouvelle fenêtre avec plusieurs onglets s’ouvre. Sélectionnez l’onglet « fichiers locaux », puis cliquez sur le bouton « Parcourir les fichiers locaux ».
5. Le répertoire contenant le runtime SteamVR s’ouvre. Copiez l’intégralité du répertoire (nommé SteamVR) sur un support portable de votre choix (par exemple, un lecteur USB).
6. faites la même chose avec Windows Mixed Reality pour SteamVR et toutes les applications compatibles SteamVR que vous souhaitez installer sur le PC cible.

**Exécuter SteamVR sur le PC cible**
1. Une fois le périphérique de stockage portable branché sur le PC cible, déplacez les dossiers SteamVR, MixedRealityVRDriver et autres vers un emplacement pratique sur le PC cible.
![SteamVR et Windows Mixed Reality pour SteamVR installés sur le PC cible](images/steamvr-install-files.png)

2. En veillant à ce que SteamVR et MixedRealityVRDriver se trouvent dans le même dossier, ouvrez une invite de commandes. Dans le cadre de cet exemple, nous allons supposer que le dossier conteneur se trouve sur *C:\SteamVRInstall*. Dans ce cas, dans l’invite de commandes, vous devez exécuter :
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
(notez que si vous exécutez une version 32 bits de Windows, la `win64` partie du chemin d’accès ci-dessus doit être à la `win32` place.)

cela permettra au runtime de rechercher le Windows Mixed Reality pour le pilote SteamVR dans votre installation personnalisée.

4. Pour exécuter SteamVR, vous devez double-cliquer sur le fichier « vrstartup.exe » situé dans *SteamVR\bin\win64\vrstartup.exe* ou *SteamVR\bin\win32\vrstartup.exe* si le PC cible exécute une version 32 bits de Windows.

[Pour plus d’informations et pour résoudre les problèmes, consultez la page de documentation Steamworks](https://partner.steamgames.com/doc/features/steamvr/enterprise#2).

## <a name="play-steamvr-games"></a>Jouer à des jeux SteamVR

1. Connecter votre casque sur votre ordinateur et allumez vos contrôleurs de mouvement.
2. une fois que la Windows Mixed Reality de la page d’hébergement a été chargée et que vos contrôleurs sont visibles, ouvrez l’application de vapeur sur votre bureau.
3. Utilisez l’application Steam pour lancer un jeu SteamVR à partir de votre bibliothèque de vapeur.

**Conseil**: pour lancer des jeux SteamVR sans sortir votre casque, utilisez l’application de bureau (**Démarrez > Desktop**) pour afficher et interagir avec votre PC de bureau à l’intérieur de Windows Mixed Reality.

## <a name="using-motion-controllers-with-steamvr"></a>Utilisation de contrôleurs de mouvement avec SteamVR

Vous utiliserez vos contrôleurs de mouvement différemment dans différents jeux. Voici quelques notions de base pour vous aider à démarrer :

* Pour ouvrir le tableau de bord de la vapeur, appuyez sur le bouton droit de droite ou de gauche.
* pour quitter un jeu SteamVR et revenir à la page d’hébergement Windows Mixed Reality, appuyez sur le bouton Windows.

## <a name="changing-the-resolution"></a>Modification de la résolution

vous pouvez ajuster le curseur résolution d’Application dans la fenêtre SteamVR-> Paramètres-> Applications à tout moment si vous souhaitez jouer à des jeux à une résolution supérieure. * * Quand vous utilisez un multiplicateur de résolution plus élevé, vous pouvez vous attendre à ce que le jeu augmente la charge sur votre PC. Si vous augmentez le multiplicateur et que vous voyez les performances dégradées, réajustez le curseur sur le niveau par défaut et redémarrez le jeu pour vous assurer que la modification prend effet.![Ajuster la résolution de l’application](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Utilisation de plusieurs casques

Si vous êtes passionné par VR, vous pouvez utiliser régulièrement plusieurs écouteurs de VR sur le même PC. si c’est le cas, quand un Windows Mixed Reality casque est branché, les jeux SteamVR sont toujours lancés sur le Windows Mixed Reality casque. si vous souhaitez lancer des jeux SteamVR sur un autre casque, veillez à débrancher tout d’abord le Windows Mixed Reality casque avant de continuer.

## <a name="preview-programs"></a>Programmes d’évaluation

nous mettons à la sortie des mises à jour régulières pour améliorer les performances, la fiabilité et l’expérience globale de l’utilisation de SteamVR sur Windows Mixed Reality des casques immersifs. Si aucun de ces programmes de préversion n’est requis, nous vous encourageons à les joindre Si vous souhaitez obtenir des mises à jour plus rapidement et plus fréquemment (et nous faire part de vos commentaires sur ces mises à jour !).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality pour SteamVR Beta

Windows Mixed Reality pour SteamVR est le composant que vous installez à partir du magasin à vapeur qui permet à SteamVR de fonctionner avec votre casque Windows Mixed Reality.  Nous publions régulièrement des mises à jour pour ce « pont » et la vapeur les installe automatiquement.

Si vous souhaitez obtenir des mises à jour plus fréquemment, nous vous encourageons à participer à notre version bêta publique.  Les mises à jour vont d’abord à notre audience bêta et nous utilisons leurs commentaires pour vérifier que les mises à jour sont de haute qualité avant de les publier pour tous les utilisateurs.  Si vous n’êtes pas dans notre programme bêta, vous obtiendrez tous les mêmes correctifs et fonctionnalités, mais une fois qu’ils ont été testés par nos utilisateurs de la version bêta.

Pour rejoindre :

  1. Dans Steam, utilisez la liste déroulante dans le menu **bibliothèque** pour filtrer sur **logiciel**.
  2. dans la liste, cliquez avec le bouton droit sur **Windows Mixed Reality pour SteamVR** et sélectionnez **propriétés**.
  3. Sélectionnez l’onglet **versions bêta** .
  4. Choisissez **« bêta-public bêta »** et sélectionnez **Fermer** pour confirmer. Le champ Code d’accès bêta doit rester vide.
  
### <a name="steamvr-beta"></a>SteamVR bêta

SteamVR est construit et libéré par vanne et est courant sur tous les casques SteamVR.  Il suit un modèle similaire de publication des mises à jour pour les membres de la version bêta avant la publication sur tous les utilisateurs.

Pour rejoindre :

  1. Dans Steam, utilisez la liste déroulante dans le menu **bibliothèque** pour filtrer sur **Outils**.
  2. Dans la liste, cliquez avec le bouton droit sur **SteamVR** et sélectionnez **Propriétés**.
  3. Sélectionnez l’onglet **versions bêta** .
  4. Choisissez **« bêta-public bêta »** et sélectionnez **Fermer** pour confirmer.  Le champ Code d’accès bêta doit rester vide. ![ Basculer vers la version bêta de SteamVR dans la boîte de dialogue des propriétés de SteamVR](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Programme Windows Insider

Windows Mixed Reality fait partie de Windows 10 et Windows 11.  De nombreux correctifs et fonctionnalités qui affectent les utilisateurs de SteamVR sont fournis avec le système d’exploitation Windows.  si vous souhaitez essayer les dernières versions de Windows 10 et Windows 11 preview, nous vous invitons à participer au [programme Windows insider](https://insider.windows.com).

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Activation de la reprojection de mouvement pour les applications SteamVR

Windows Mixed Reality pour SteamVR dispose d’une fonctionnalité expérimentale de reprojection de mouvement pour rendre la reprojection 90 FPS plus lisse.

lorsque la reprojection de mouvement est activée, tous les jeux de vapeur VR s’affichent avec une fréquence d’images de 1/2 (45 fps au lieu de 90 fps), tandis que Windows Mixed Reality pour SteamVR utilise des vecteurs de mouvement générés par le GPU pour extrapoler le cadre suivant. Pour les jeux SteamVR qui atteignent de manière fiable 60 FPS + sur un PC donné, cela devrait entraîner une expérience solide de 90 FPS avec des artefacts occasionnels, tout en maintenant une expérience confortable.

Les modes de reprojection de mouvement disponibles sont les suivants :

* **paramètre SteamVR par application**: vous permet de contrôler la reprojection de mouvement via l’interface utilisateur SteamVR Paramètres. vous pouvez ensuite ouvrir SteamVR Paramètres, accéder à video > Per-Application Paramètres vidéo et sélectionner une option pour le « lissage de mouvement ».
* **Auto**: permet d’activer automatiquement la reprojection de mouvement lorsqu’un jeu est trop lent pour gérer 90 images/s. Lorsqu’un jeu commence à gérer 90 FPS ou démarre un rendu à moins de 45 FPS, la reprojection de mouvement est désactivée. La reprojection asynchrone asynchrone est toujours activée.
* **Motion Vector**: force l’application à toujours s’exécuter à demi-fréquence avec la reprojection de vecteur de mouvement.
* **None**: désactive la reprojection de mouvement.

**Artifacts visuel attendu** 

1. Lorsque vous utilisez une résolution d’application supérieure à 150%, vous pouvez constater un flou. Lors de l’utilisation de la reprojection de mouvement, nous vous recommandons d’utiliser une valeur inférieure à 150%.
2. Des bords ou du texte de contraste aigus, en particulier sur des HUDs ou des menus en jeu, peuvent paraître temporairement déformés ou déformés en raison de la désocclusion.
3. SteamVR et de nombreux autres jeux qui n’atteignent pas de manière fiable 50-60 FPS sur votre PC continueront d’avoir une expérience médiocre avec ce mode.
4. Certains jeux ont été signalés pour s’exécuter à une vitesse de 50% ou avec une latence accrue (décalage). signalez ces jeux à l’aide des instructions [Hub de commentaires Windows](filing-feedback.md) ci-dessous.

Au départ, nous disposons d’une prise en charge expérimentale des GPU NVidia de génération récente. Nous continuons à itérer et à améliorer notre prise en charge de la reprojection de mouvement sur plus de GPU, et nous sommes impatients d’entendre vos commentaires.

**GPU pris en charge :** Nvidia GeForce GTX1060, AMD RX470 ou ultérieur, avec Windows Mixed Reality pilotes graphiques compatibles compatibles installés.

Pour activer la reprojection de mouvement :

1. assurez-vous d’avoir choisi le **Windows Mixed Reality pour la version bêta de SteamVR** en suivant les instructions ci-dessus.
2. Ouvrez le tableau de bord SteamVR.
3. sélectionnez le bouton sur le côté gauche avec le logo Windows Mixed Reality pour ouvrir **Windows Mixed Reality pour SteamVR** Paramètres.
4. Dans l’interface utilisateur qui s’affiche, sélectionnez l’onglet Graphics.
5. Sélectionnez « auto » pour le « mode de reprojection de mouvement de l’application SteamVR par défaut » pour activer la reprojection automatique du mouvement.

![Activer LSR & LSR indicateur avec SettingsUX](images/settingsux-enable-lsr.gif)

**Indicateur de reprojection de mouvement**

L’indicateur de reprojection de mouvement permet de diagnostiquer les problèmes liés à la fonctionnalité de reprojection de mouvement automatique expérimental. Quand la valeur est true, un indicateur s’affiche dans l’angle supérieur gauche de l’affichage de votre casque lors de la reprojection de mouvement automatique. La couleur et la position de cet indicateur correspondent au mode de reprojection de mouvement actuel. consultez le diagramme ci-dessous pour obtenir des exemples.

![Indicateur mvLSR](images/mvLSRIndicator.png)

Vert = la reprojection de mouvement est désactivée, car l’application peut s’afficher à une cadence complète.

Cyan = la reprojection de mouvement est activée, car l’application est liée à l’UC.

Blue = la reprojection de mouvement est activée, car l’application est liée au GPU.

Rouge = la reprojection de mouvement est désactivée, car l’application s’exécute à moins de la demi-fréquence d’images ; essayez de réduire le Super-échantillonnage s’il est activé.

Vert + Cyan + bleu = la reprojection de mouvement est en mode demi-fréquence ou la reprojection de mouvement demandée par l’application.

## <a name="sharing-feedback-on-steamvr"></a>Partage de commentaires sur SteamVR

vos commentaires sont précieux lorsqu’il s’agit d’améliorer l’expérience Windows Mixed Reality SteamVR. envoyez tous les commentaires et bogues par le biais du [Hub de commentaires Windows](filing-feedback.md). Suivez ces suggestions pour nous aider à tirer le meilleur parti de vos commentaires :

1. Dans le hub de commentaires, indiquez que vous signalez un nouveau problème dans le « quel type de commentaire est-il ? » dans la partie supérieure.
2. Sélectionnez la catégorie de **réalité mixte** et la sous-catégorie **applications** .
3. Placez le mot « SteamVR » dans le résumé du problème. Cela nous aide à trouver vos commentaires.
4. Décrivez le jeu SteamVR ou l’application que vous utilisiez lorsque vous rencontrerez le problème.
5. Envisagez de joindre un rapport du système SteamVR à vos commentaires. Cela fournit plus de journaux qui peuvent nous aider à diagnostiquer votre problème.
    1. Dans la fenêtre SteamVR (les petites fenêtres qui affichent l’état de votre contrôleur), sélectionnez sur le titre pour ouvrir le menu.
    2. Sélectionnez « créer un rapport système ».
    3. Enregistrer dans le fichier.
    4. Attachez le fichier généré à votre entrée de hub de commentaires directement.
6. Si vos commentaires sont sur les performances de SteamVR, collectez un suivi des performances de la réalité mixte : 
    1. Sélectionnez le bouton **recréer mon problème** .
    2. Dans la liste déroulante en regard de « inclure les données à propos de », sélectionnez performances de la **réalité mixte**.
    3. Assurez-vous que le jeu est en cours d’exécution et sélectionnez **Démarrer la capture**.
    4. Passez quelques secondes à jouer le jeu pour capturer la trace. Ne capturez pas le suivi pendant plus de 10-15 secondes, ou il sera trop volumineux pour être envoyé.
    5. Sélectionnez **arrêter la capture**.
7. Sélectionnez **Envoyer** une fois que vous avez terminé le reste des champs.

Si vous avez des questions ou des commentaires à partager, vous pouvez également nous contacter sur notre [Forum de vapeur](http://steamcommunity.com/app/719950/discussions/).

## <a name="see-also"></a>Voir aussi

* [Résolution des problèmes de SteamVR avec Windows Mixed Reality](steamvr-questions.md)
* [Utilisation de jeux et d’applications dans Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Utilisation de contrôleurs HP dans Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Utilisation de contrôleurs HP dans des conditions inréelles](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [Envoyer des bogues et des commentaires](filing-feedback.md)
