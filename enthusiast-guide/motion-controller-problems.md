---
title: FAQ sur le contrôleur de mouvement
description: les contrôleurs Windows Mixed Reality résolution des problèmes qui vont au-delà de notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, Support, contrôleurs de mouvement
appliesto:
- Windows 10
ms.openlocfilehash: e477ed07e20fb06e270c9a6e13e20defecfc6328896983ed12c4b79ea2197e44
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219741"
---
# <a name="motion-controller-faqs"></a>FAQ sur le contrôleur de mouvement

## <a name="what-do-the-vibrations-and-lights-mean"></a>Signification des vibrations et des lumières

L’anneau et les haptiques de la constellation LED indiquent l’état du contrôleur de mouvement.

| État    | Comportement associé à l’État | Comment passer à l’État |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Mise sous tension**               | Les LED allument et le contrôleur vibre une fois. | appuyez sur le bouton Windows du contrôleur et maintenez-le enfoncé pendant deux secondes pour activer le contrôleur.  |
| **Mise hors tension**              |  Les voyants sont éteints et le contrôleur vibre deux fois. | appuyez sur le bouton Windows du contrôleur et maintenez-le enfoncé pendant quatre secondes pour désactiver le contrôleur.   |
| **En veille**               |  Les voyants s’éteignent et clignotent toutes les trois secondes en état de veille. | Le contrôleur passe automatiquement à l’état de veille lorsqu’il est motionless pendant 30 secondes. Le contrôleur sort de veille lorsqu’il détecte motion, sauf si l’appareil n’est pas couplé avec le PC hôte. Appuyez sur le bouton pour le mettre en éveil dans ce cas. |
| **Jumelage**                |  Clignotement de LED lentement en mode de couplage, et est solide lorsque vous quittez le mode de couplage. Le contrôleur vibre une fois si le jumelage a réussi ou trois fois si le jumelage a échoué, puis expire. | Appuyez sur le bouton d’appariement et maintenez-le enfoncé pendant trois secondes.     |
| **Le contrôleur se connecte/se déconnecte du PC** |  Le contrôleur vibre une fois sur la connexion du PC ou la déconnexion. | Se produit lorsque le contrôleur se connecte correctement au PC après l’avoir mis sous tension ou si le contrôleur se déconnecte du PC en cours d’utilisation.|
| **Niveau de batterie faible**      | Les haptique sont désactivées lorsque la batterie est faible (il n’y a pas d’indication de LED). L’icône d’indicateur de batterie sur le handle de contrôleur du casque affiche 1/4 lorsque la batterie est faible. | Remplacez vos batteries. | 
| **Niveau de batterie critique** |  Le contrôleur vibre trois fois quand vous l’activez, puis le désactive automatiquement. L’icône de l’indicateur de batterie devient rouge. | Remplacez les piles. Si le problème persiste, [restaurez les paramètres d’usine de l’appareil](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>Mes contrôleurs de mouvement ne fonctionnent pas correctement

Si vos [contrôleurs de mouvement](controllers-in-wmr.md) ne fonctionnent pas, se connectent ou affichent une image des contrôleurs quand vous enportez votre casque :

1. Assurez-vous que vos contrôleurs sont activés. pour les activer, maintenez le bouton Windows enfoncé pendant deux secondes.
2. Assurez-vous que les contrôleurs sont entièrement facturés et remplacez les batteries si elles ne le sont pas.
3. Désactivez et rallumez les contrôleurs tout en les maintenant enfoncés. maintenez le bouton Windows enfoncé pendant quatre secondes pour désactiver un contrôleur. Appuyez sur la touche et maintenez-la enfoncée pendant deux secondes pour l’activer.
4. Vérifiez si vos contrôleurs de mouvement sont [correctement couplés](controllers-in-wmr.md#pair-motion-controllers).
5. Vérifier les LED des contrôleurs de mouvement : les contrôleurs allumés de façon claire sont couplés et connectés, les contrôleurs dimly lit ne sont pas connectés.
6. Accédez à **démarrer > portail de réalité mixte** sur votre ordinateur, puis sélectionnez « Menu ». Vous devez voir vos contrôleurs de mouvement listés, ainsi qu’un message d’État :
    * Prêt : les contrôleurs sont tous définis.
    * Suivi perdu : le portail de réalité mixte ne trouve pas vos contrôleurs. tenez-les devant votre casque et redémarrez-les en appuyant sur le bouton Windows pendant quatre secondes, puis de nouveau pendant deux secondes.
    * Batterie faible : remplacez les piles du contrôleur.
7. si vous utilisez une carte Bluetooth usb externe, assurez-vous qu’elle est connectée à un port usb 2,0 (ce qui n’est souvent pas toujours le noir). Elle doit également être branchée autant que possible à partir de tout autre transmetteur sans fil ou disque mémoire flash USB, y compris le connecteur USB pour votre casque. 
8. accédez à **Gestionnaire de périphériques > Bluetooth** et recherchez un adaptateur pour vérifier qu’il n’y a qu’une seule Bluetooth radio dans le PC. Si vous utilisez la configuration de l’ordinateur de bureau avec la radio intégrée, vérifiez si une antenne externe est connectée. Si aucune antenne externe n’est connectée, cela peut entraîner des problèmes de suivi. vous avez la possibilité d’utiliser une clé de Bluetooth externe (USB), de désactiver la fonctionnalité de Bluetooth interne et de réessayer le jumelage et la connexion.
9. si la fenêtre paramètres Bluetooth est ouverte en arrière-plan, de nombreux appels supplémentaires sont passés au protocole Bluetooth. Fermez-le.
10. Vérifiez le niveau de la batterie virtuelle sur le contrôleur de mouvement en activant les contrôleurs dans la réalité mixte pour voir l’icône de la batterie. Attendez environ 15 secondes avant de lire le niveau, car le niveau signalé est supérieur au niveau réel immédiatement après la connexion d’un contrôleur. Remplacez les piles si l’icône est rouge.
11. retirez Bluetooth casque et les haut-parleurs dans **Paramètres > appareils > Bluetooth & autres appareils** et éteignez les appareils. Utilisez la prise casque ou les haut-parleurs intégrés sur votre casque de réalité mixte pour une expérience audio optimale.
12. retirez les autres Bluetooth appareils qui peuvent être associés à votre PC, tels que des casques ou des boîtiers. accédez à **Paramètres > appareils > Bluetooth & autres appareils**, sélectionnez les appareils, puis « supprimer l’appareil ».
13. Débranchez le câble USB sur votre casque et rebranchez-le sur le PC pour redémarrer Windows Mixed Reality.
14. Les voyants du contrôleur clignotent lorsqu’ils sont en cours de mise à jour du microprogramme. Attendez la fin de la mise à jour et les contrôleurs doivent apparaître dans la réalité mixte.
15. Assurez-vous que votre ordinateur est connecté à un réseau Wi-Fi de 5 GHz. si votre ordinateur portable est connecté à un réseau Wi-Fi de 2,4 GHz, il partage généralement la connexion Bluetooth. cela peut avoir un impact négatif sur les performances de Wi-Fi ou de Bluetooth, en fonction de la conception du produit. Modifiez la bande par défaut à 5 GHz dans les paramètres de carte réseau. si votre réseau ne prend pas en charge 5 GHz, une clé de Bluetooth peut être utilisée à la place de la capacité de Bluetooth interne.
16. si vos paramètres de Bluetooth ont déjà des contrôleurs de mouvement couplés, Windows ne détectera pas les nouveaux périphériques tant que ceux-ci ne seront pas supprimés. Si elles ont été ajoutées à l’aide d’une clé spécifique, elles ne peuvent être supprimées qu’avec cette clé.
17. si votre PC a des Bluetooth intégrées et que vous rencontrez des problèmes de connexion, essayez d’utiliser une carte Bluetooth USB. pour ce faire, désactivez votre radio Bluetooth intégrée dans Gestionnaire de périphériques puis associez vos autres appareils Bluetooth à la nouvelle carte.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Mes contrôleurs sont instables, se bloquent ou scintillent et disparaissent en réalité mixte

* Si votre ordinateur s’exécute sur WiFi 2,4 GHz, basculez vers WiFi 5 GHz. 
* si vous utilisez une carte Bluetooth externe, assurez-vous qu’elle est connectée à un port USB 2,0 (qui est souvent, mais pas toujours, en noir), loin d’autres émetteurs sans fil ou de disques mémoire flash usb.
* exécutez l’utilitaire de résolution des problèmes de Bluetooth dans **Paramètres > Update & Security > résoudre les problèmes**> Bluetooth.

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Mon contrôleur est bloqué dans un redémarrage infini

Il s’agit d’un indicateur de batterie critique. Mettez les piles neuves dans l’appareil et, si le problème persiste, [réinitialisez les paramètres d’usine du contrôleur](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Le portail de réalité mixte fonctionne, mais mes contrôleurs sont mal suivis (vol, tremblement, etc.).

1. Les conditions d’éclairage peuvent affecter le suivi. Assurez-vous que vous n’êtes pas exposé à la lumière solaire directe et que vous avez des sources de lumière de point minimales visibles pour votre HMD (par exemple, des chaînes d’éclairages comme un arbre de Noël).
2. ces symptômes sont dus à des échecs de communication entre le contrôleur et le PC hôte, et indiquent une mauvaise qualité de lien Bluetooth. Consultez les [questions sur Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Les LED du contrôleur de mouvement ne sont pas allumées, mais les boutons et les sticks analogiques fonctionnent toujours dans le portail de réalité mixte

Le cache d’étalonnage du contrôleur de mouvement est peut-être endommagé. Pour supprimer le cache, exécutez la commande suivante dans une invite de commandes d’administrateur :

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

ce dossier n’est pas accessible dans l’explorateur de Windows et ne peut être modifié qu’à partir d’une invite de commandes d’administrateur. Une fois que vous avez supprimé le dossier, redémarrez votre PC et reconnectez vos contrôleurs de mouvement pour restaurer les fichiers d’étalonnage.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Mon contrôleur ressemble à un vive/Oculus, a une orientation étrange ou les boutons sont incorrectement mappés

Le site Web n’a probablement pas de prise en charge complète du contrôleur motion.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Mes contrôleurs de mouvement n’apparaissent pas dans les applications et jeux SteamVR

Tout d’abord, assurez-vous que les batteries de votre contrôleur sont facturées. Les contrôleurs ne fonctionneront pas si les batteries sont mortes ou morts

Si vous pouvez voir vos contrôleurs dans la maison de la falaise, mais pas dans les applications et jeux SteamVR, le pilote du modèle de contrôleur de mouvement n’est peut-être pas installé correctement. Pour vérifier que le pilote du modèle de contrôleur de mouvement est correctement installé :

1. Activez les deux contrôleurs de mouvement. Vérifiez si vos contrôleurs de mouvement sont [correctement couplés](controllers-in-wmr.md#pair-motion-controllers).
2. Accédez à **Gestionnaire de périphériques > périphériques d’interface utilisateur** et recherchez « contrôleur de mouvement ».
3. Double-cliquez sur chaque appareil « contrôleur de mouvement » et accédez à l’onglet « pilote ». Vérifiez que la version du pilote indiquée correspond à l’une de [ces versions](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history).
4. si la version du pilote ne correspond pas ou si vous ne trouvez pas d’appareil appelé « contrôleur de mouvement », exécutez Windows Update.  Cela permet de télécharger et d’installer automatiquement le pilote. si vous êtes sur un PC avec des stratégies d’entreprise ou si Windows Update n’est pas limité, vous devrez peut-être installer le pilote de modèle de contrôleur de mouvement manuellement. Pour ce faire, accédez à [cette page](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) et recherchez la version du pilote correspondant à votre matériel de contrôleur. Les instructions d’installation sont disponibles sur la page de téléchargement.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>La mise à jour du microprogramme du contrôleur prend plus de deux minutes

consultez la [section questions Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). une mauvaise qualité de lien Bluetooth est généralement à l’origine de ces problèmes.

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>J’ai inséré des piles neuves, mais le niveau de batterie virtuelle du contrôleur n’indique pas le niveau complet

Le niveau de batterie du contrôleur de mouvement est réglé pour les piles AA. Certaines batteries rechargeables de basse tension peuvent ne pas être entièrement signalées, bien qu’elles soient entièrement chargées.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Mon pavé tactile du contrôleur Samsung motion est hors-Centre ou a un point mort

Il s’agit probablement d’une erreur matérielle et vous devez revenir à votre revendeur ou fabricant d’équipement pour un remplacement ou un échange.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Comment restaurer les paramètres d’usine des contrôleurs

Restaurez-la à des conditions d’usine (vous aurez besoin de piles neuves) :

1. Débranchez et mettez hors tension les contrôleurs.
2. Ouvrez la couverture de la batterie.
3. Insérez vos nouvelles piles.
4. Appuyez sur le bouton d’appariement (l’onglet situé en bas sous les batteries) et maintenez-le enfoncé.
5. tout en maintenant le bouton de jumelage, mettez sous tension le contrôleur en appuyant sur le bouton Windows pendant cinq secondes (maintenez les deux boutons enfoncés).
6. Relâchez les boutons et attendez la mise sous tension du contrôleur. Cela prend jusqu’à 15 secondes et aucun indicateur ne s’affiche en cas de récupération de l’appareil. Si l’appareil se met immédiatement sous tension, la séquence du bouton de récupération n’a pas été inscrite et vous devez réessayer.
7. si les contrôleurs ont été appariés à votre PC, accédez à **Paramètres > Bluetooth > autres périphériques** , sélectionnez « contrôleur de mouvement » et « supprimer l’appareil » pour supprimer les associations de contrôleur des paramètres de Bluetooth.
8. [Couplez de nouveau les contrôleurs](controllers-in-wmr.md#pair-motion-controllers) au casque ou au PC.
9. Une fois connecté avec l’hôte et le casque, l’appareil est mis à jour avec le dernier microprogramme disponible.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Puis-je associer mon contrôleur Xbox à mon PC pour pouvoir l’utiliser dans le casque

vous pouvez associer un contrôleur Xbox Bluetooth pour l’utiliser avec votre casque en suivant [ces instructions](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues).

Si vous avez un contrôleur Xbox câblé, connectez-le à votre PC.

Certains jeux et applications utilisent le contrôleur Xbox différemment de celui utilisé dans la réalité mixte. Pour utiliser le contrôleur pour un jeu ou une application, sélectionnez « utiliser en tant que boîtier » dans la barre de l’application ou dites « utiliser en tant que boîtier ». Pour rebasculer le contrôleur vers la réalité mixte, sélectionnez à nouveau « utiliser en tant que boîtier », ou « utiliser avec le point de regard ». 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Comment faire paire de nouveaux contrôleurs si Windows Mixed Reality est déjà configuré sur mon PC

Si vous associez vos contrôleurs à votre casque, utilisez l’application auxiliaire (le [portail de la réalité mixte](install-windows-mixed-reality.md#launch-mixed-reality-portal) peut vous aider à trouver une application auxiliaire à lancer ou vous donner une liste des applications auxiliaires que vous pouvez sélectionner).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Comment puis-je ramener mes contrôleurs à leur jumelage

pour ramener les contrôleurs de mouvement à leur appariement de fabriques, ou pour les associer à un Windows Mixed Reality casque avec la radio intégrée Bluetooth, exécutez l’application device companion du casque et suivez les instructions pour le couplage de contrôleur de mouvement. Par exemple, l’application « Acer OJO 500 » ou l’application « Samsung HMD Odyssey + Setup » est installée automatiquement la première fois que le casque est branché.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>Mes contrôleurs de mouvement ne sont pas couplés à mon PC

* Si les contrôleurs ne sont pas activés, insérez des piles neuves. Si cela ne résout pas le problème, restaurez les paramètres d’usine de l’appareil en allumant l’appareil tout en maintenant les boutons d’appariement. Pour plus d’informations, consultez [étapes de récupération](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)de l’appareil.
* si les contrôleurs sont allumés pendant que vous utilisez une carte Bluetooth externe, assurez-vous que la carte est branchée sur un port USB 2,0 (qui est souvent, mais pas toujours, en noir), loin d’autres émetteurs sans fil ou de disques mémoire flash usb. s’il ne fonctionne toujours pas, exécutez l’utilitaire de résolution des problèmes de Bluetooth dans Paramètres > Update & Security > résoudre les problèmes > Bluetooth.
* Si vous utilisez un adaptateur Qualcomm et que le PC vient de se bloquer, redémarrez le PC.
* Essayez de redémarrer les contrôleurs de mouvement qui ne sont pas couplés, un à la fois, puis redémarrez le PC.
* Le cache du contrôleur de mouvement est peut-être endommagé. Pour résoudre ce problème, consultez les [étapes](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)ci-dessous.
* Si les étapes corrigent le problème, contactez le fabricant.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mes contrôleurs associés ne sont pas affichés dans le portail de réalité mixte

* tenez les contrôleurs devant votre casque et redémarrez-les en appuyant sur le bouton Windows pendant quatre secondes, puis de nouveau pendant deux secondes.
* Si vos contrôleurs s’affichent comme étant connectés, découplez-les et réexécutez le [processus de jumelage](controllers-in-wmr.md#pair-motion-controllers) .
* Si les voyants du contrôleur sont en cours d’activation et de désactivation à un seul quadrant de voyants, ils sont en train de mettre à jour le microprogramme. Attendez la fin de la mise à jour et les contrôleurs doivent apparaître dans la réalité mixte.
* si vous utilisez une carte Bluetooth externe, assurez-vous que la carte est connectée à un port usb 2,0 (qui est noir), loin d’autres émetteurs sans fil ou périphériques usb 3,0.
* Si le PC vient de se bloquer et qu’un adaptateur Qualcomm est utilisé, il se peut qu’une réinitialisation ne fonctionne pas. Pour résoudre ce problème, débranchez le cordon d’alimentation à l’arrière de l’ordinateur (ou, si vous êtes sur un ordinateur portable, maintenez le bouton d’alimentation enfoncé pendant 10 secondes) et redémarrez l’ordinateur.
* exécutez l’utilitaire de résolution des problèmes de Bluetooth dans **Paramètres > Update & Security > résoudre les problèmes**> Bluetooth.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>j’essaie de coupler mes contrôleurs, mais ils ne s’affichent pas dans le menu « ajouter un nouveau périphérique » dans les paramètres de Bluetooth

Vérifiez que vous n’avez pas déjà associé de contrôleurs. Si c’est le cas, supprimez-les et réessayez. Si le problème persiste, redémarrez le PC. En cas d’échec, consultez plus d' [informations sur Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Remarque : si un autre ensemble de contrôleurs de mouvement est associé à votre PC, vous devez découpler ces contrôleurs avant de les associer. Si vous avez associé un ensemble de contrôleurs de mouvement à votre PC actuel et que vous les avez couplés avec un deuxième PC, vous devez les découpler et les réassocier à l’ordinateur actuel avant de les réutiliser.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>comment savoir si j’utilise Bluetooth technologie

les contrôleurs de mouvement utilisent la même technologie de Bluetooth dans de nombreux appareils grand public et sont conçus pour fonctionner avec la fonctionnalité de Bluetooth incluse dans tout ordinateur récent. votre ordinateur doit disposer d’Bluetooth radio s’il a réussi la vérification de la compatibilité de la réalité mixte. Pour vérifier :

* Ouvrez « Gestionnaire de périphériques ».
* développez la section Bluetooth et recherchez un adaptateur.

![Capture d’écran d’un exemple de Gestionnaire de périphériques. l’adaptateur est le Bluetooth radio.](images/devicemanagerbtadapterpic.png)

si votre ordinateur n’a pas de Bluetooth, utilisez un Micro-adaptateur USB Bluetooth 4,0 basse énergie.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi ralentit sur mon Notebook quand les contrôleurs de mouvement sont activés

votre notebook peut partager son antenne Wi-Fi avec Bluetooth lorsqu’il est connecté à un point d’accès 2,4 GHz. Vérifiez Gestionnaire de périphériques si vous pouvez basculer la préférence de bande à 5 GHz. si un réseau de 5 GHz n’est pas disponible et que les performances sont gravement affectées, envisagez d’utiliser une clé de Bluetooth.

![Les paramètres de sélection de la bande wifi sont accessibles via le gestionnaire de périphériques](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>mon PC a Bluetooth technologie, mais je rencontre des problèmes avec mes contrôleurs

les contrôleurs de mouvement doivent fonctionner avec d’autres Bluetooth claviers, souris et contrôleurs de jeu. L’expérience varie en fonction du modèle de clavier, de souris ou de contrôleur de jeu que vous utilisez. Voici quelques opérations que vous pouvez effectuer pour améliorer les performances :

* si votre ordinateur a Bluetooth mais que vous rencontrez toujours des problèmes avec les contrôleurs de mouvement, envisagez de remplacer votre radio Bluetooth par une carte Bluetooth externe enfichable connectée à USB. vous ne pouvez avoir qu’une seule Bluetooth carte radio active à la fois. si vous branchez une radio externe avec une radio existante, vous devez désactiver votre Bluetooth radio existante dans Gestionnaire de périphériques. cliquez avec le bouton droit sur la carte et sélectionnez « désactiver l’appareil » et désassocier/recoupler tous vos appareils Bluetooth précédents.
* si vous utilisez une carte Bluetooth usb, connectez-la à un port usb 2,0 (les ports 2,0 sont souvent noirs et ne sont pas étiquetés « SS »), le cas échéant. Le port doit être physiquement séparé des éléments suivants :
    - le connecteur USB HMD
    - disques mémoire flash
    - disques durs
    - les récepteurs usb sans fil comme ceux des claviers/souris, branchez l’adaptateur de Bluetooth usb sur le côté opposé de l’ordinateur aussi loin que possible à partir de ces autres connecteurs.
* fermez la fenêtre paramètres de Bluetooth si elle est ouverte. le fait de le laisser ouvert en arrière-plan signifie que de nombreux appels supplémentaires sont passés au protocole Bluetooth.
* si votre casque est couplé à votre PC, utilisez la pile de pilotes Windows Bluetooth et n’installez pas de piles de pilotes Bluetooth tiers. Les logiciels tiers peuvent ne pas fonctionner correctement.
* désactivez le paramètre « afficher la notification pour se connecter à l’aide d’une paire Swift » sous « Bluetooth & d’autres appareils » pour réduire l’activité d’analyse de l’ordinateur hôte.
* si vous utilisez une carte de Bluetooth interne, assurez-vous que vous utilisez une antenne Bluetooth externe ou que vous pouvez rencontrer des problèmes de suivi. si cela ne fonctionne pas, utilisez une clé de Bluetooth externe (USB) après la désactivation du Bluetooth interne.
* l’appareil doit apparaître sous la catégorie « souris, clavier & stylet » dans les paramètres Bluetooth. S’il se trouve sous « autres appareils », découplez et couplez l’appareil.
* retirez, découplez et mettez hors tension Bluetooth casque et les haut-parleurs. Celles-ci ne sont pas prises en charge avec Windows Mixed Reality. Utilisez la prise casque ou les haut-parleurs intégrés sur votre casque de réalité mixte pour une expérience audio optimale.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>La reconnexion de mon deuxième contrôleur prend beaucoup de temps

Certaines radios Intel plus anciennes rencontrent ce problème si les contrôleurs de mouvement sont mis sous tension en même temps. Évitez d’alimenter les contrôleurs en même temps.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>ma radio Qualcomm Bluetooth ne peut pas coupler les contrôleurs après un incident de PC

Qualcomm (QCA) Bluetooth les pilotes radio avant 10.0.0.448 peuvent se retrouver dans un état incorrect après un blocage Windows. Mettez complètement le PC hors tension pour contourner ce problème.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Je rencontre un mauvais suivi de contrôleur avec la radio Marvell

accédez à **Gestionnaire de périphériques > Bluetooth > Marvell AVASTAR Bluetooth > propriétés** > le pilote et assurez-vous que vous utilisez le pilote 15.68.9210.47 ou version ultérieure.
