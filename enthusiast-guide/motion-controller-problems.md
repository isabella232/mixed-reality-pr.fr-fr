---
title: FAQ sur le contrôleur de mouvement
description: Résolution des problèmes avancés de Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, contrôleurs de mouvement
appliesto:
- Windows 10
ms.openlocfilehash: 2a45f16cfbe62cb1263fcb1a1e7f5c76ea0b9268
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680355"
---
# <a name="motion-controller-faqs"></a>FAQ sur le contrôleur de mouvement

## <a name="general-questions"></a>Questions générales

### <a name="what-do-the-vibrations-and-lights-mean"></a>Que signifient les vibrations et les feux ?

L’anneau et les haptiques de la constellation LED indiquent l’état du contrôleur de mouvement.

| State    | Comportement associé à l’État | Comment passer à l’État | 
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Mise sous tension**               | Les LED allument et le contrôleur vibre une fois. | Appuyez sur le bouton Windows du contrôleur et maintenez-le enfoncé pendant deux secondes pour activer le contrôleur.  | 
| **Mise hors tension**              |  Les voyants sont éteints et le contrôleur vibre deux fois. | Appuyez sur le bouton Windows du contrôleur et maintenez-le enfoncé pendant quatre secondes pour désactiver le contrôleur.   |
| **En état de veille**               |  Les voyants s’éteignent et clignotent toutes les trois secondes en état de veille. | Le contrôleur passe automatiquement à l’état de veille lorsqu’il est motionless pendant 30 secondes. Le contrôleur sort de veille lorsqu’il détecte motion, sauf si l’appareil n’est pas couplé avec le PC hôte. Appuyez sur le bouton pour le mettre en éveil dans ce cas. |
| **Jumelage**                |  Clignotement de LED lentement en mode de couplage, et est solide lorsque vous quittez le mode de couplage. Le contrôleur vibre une fois si le jumelage a réussi ou trois fois si le jumelage a échoué, puis expire. | Appuyez sur le bouton d’appariement et maintenez-le enfoncé pendant trois secondes.     |
| **Le contrôleur se connecte/se déconnecte du PC** |  Le contrôleur vibre une fois sur la connexion du PC ou la déconnexion. | Cela se produit lorsque le contrôleur se connecte correctement au PC après l’avoir mis sous tension ou si le contrôleur se déconnecte du PC en cours d’utilisation.|
| **Niveau de batterie faible**      | Les haptique sont désactivées lorsque la batterie est faible (il n’y a pas d’indication de LED). L’icône d’indicateur de batterie sur le handle de contrôleur du casque affiche 1/4 lorsque la batterie est faible. | Remplacez vos batteries. | 
| **Niveau de batterie critique** |  Le contrôleur vibre trois fois quand vous l’activez, puis le désactive automatiquement. L’icône de l’indicateur de batterie devient rouge. | Remplacez les piles. Si le problème persiste, [restaurez les paramètres d’usine de l’appareil](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

### <a name="my-motion-controllers-arent-working-properly"></a>Mes contrôleurs de mouvement ne fonctionnent pas correctement.

Si vos [contrôleurs de mouvement](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) ne fonctionnent pas, si vous ne vous connectez pas ou si vous ne voyez pas d’image des contrôleurs quand vous enportez votre casque, procédez comme suit :
1. Assurez-vous que vos contrôleurs sont activés. Pour les activer, appuyez sur le bouton Windows et maintenez-le enfoncé pendant deux secondes.
2. Assurez-vous que les contrôleurs sont entièrement chargés et remplacez les batteries si ce n’est pas le cas.
3. Désactivez et rallumez les contrôleurs tout en les maintenant enfoncés. Appuyez sur le bouton Windows et maintenez-le enfoncé pendant quatre secondes pour désactiver un contrôleur, puis appuyez dessus et maintenez-le enfoncé pendant deux secondes pour le mettre sous tension. 
4. Si vos contrôleurs sont associés à votre PC, accédez à **paramètres > appareils > Bluetooth & autres périphériques** , ou si vos contrôleurs sont associés à votre casque, accédez à **Device Manager > appareils d’interface utilisateur > contrôleur de mouvement** . Assurez-vous que les contrôleurs sont répertoriés comme associés. Si ce n’est pas le cas, [couplez-les](motion-controller-problems.md#how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc). 
5. Assurez-vous que les contrôleurs de mouvement s’affichent sous la forme « connecté ». « Jumelé » ne signifie pas nécessairement que les contrôleurs sont connectés au PC. Les contrôleurs doivent apparaître sous la catégorie « souris, clavier & stylet ». Les contrôleurs de mouvement sous « autres appareils » ont échoué au processus de jumelage et ne fonctionnent pas. Vérifier les LED des contrôleurs de mouvement : les contrôleurs allumés de façon claire sont couplés et connectés, les contrôleurs dimly lit ne sont pas connectés.
6. Accédez à **démarrer > portail de réalité mixte** sur votre ordinateur, puis sélectionnez « Menu ». Vous devez voir vos contrôleurs de mouvement listés, ainsi qu’un message d’État :
    * Prêt : les contrôleurs sont tous définis.
    * Suivi perdu : le portail de réalité mixte ne trouve pas vos contrôleurs. Tenez-les devant votre casque et redémarrez-les en appuyant sur le bouton Windows pendant quatre secondes, puis de nouveau pendant deux secondes.
    * Batterie faible : remplacez les piles du contrôleur.
7. Si vous utilisez une carte Bluetooth USB externe, assurez-vous qu’elle est connectée à un port USB 2,0 (ils sont souvent, mais pas toujours noirs). Elle doit également être branchée autant que possible à partir de tout autre transmetteur sans fil ou disque mémoire flash USB, y compris le connecteur USB pour votre casque. 
8. Pour vérifier qu’il n’y a qu’une seule radio Bluetooth dans le PC, accédez à **Device Manager > Bluetooth** et recherchez une carte. Si vous utilisez la configuration de l’ordinateur de bureau avec la radio intégrée, vérifiez si une antenne externe est connectée. Si aucune antenne externe n’est connectée, cela peut entraîner des problèmes de suivi. Vous avez la possibilité d’utiliser une clé Bluetooth externe (USB), de désactiver la fonctionnalité Bluetooth interne et de réessayer le jumelage et la connexion.
9. Si la fenêtre Paramètres Bluetooth est ouverte en arrière-plan, de nombreux appels supplémentaires sont effectués au protocole Bluetooth. Fermez-le.
10. Vérifiez le niveau de la batterie virtuelle sur le contrôleur de mouvement en activant les contrôleurs dans la réalité mixte pour voir l’icône de la batterie. Attendez environ 15 secondes avant de lire le niveau, car le niveau signalé est supérieur au niveau réel immédiatement après la connexion d’un contrôleur. Remplacez les piles si l’icône est rouge. 
11. Retirez les écouteurs et les haut-parleurs Bluetooth dans **paramètres > appareils > Bluetooth & d’autres appareils** et éteignez les appareils. Utilisez la prise casque ou les haut-parleurs intégrés sur votre casque de réalité mixte pour une expérience audio optimale.
12. Retirez les autres périphériques Bluetooth qui peuvent être associés à votre ordinateur, tels que les casques ou les boîtiers. Accédez à **paramètres > appareils > Bluetooth & autres appareils** , sélectionnez les appareils, puis « supprimer l’appareil ».
13. Débranchez le câble USB sur votre casque et rebranchez-le sur le PC pour redémarrer Windows Mixed Reality.
14. Les voyants du contrôleur clignotent lorsqu’ils sont en cours de mise à jour du microprogramme. Attendez la fin de la mise à jour et les contrôleurs doivent apparaître dans la réalité mixte.
15. Assurez-vous que votre ordinateur est connecté à un réseau Wi-Fi de 5 GHz. Si votre ordinateur portable est connecté à un réseau WiFi 2,4 GHz, il partage généralement la connexion Bluetooth. Cela peut avoir un impact négatif sur les performances WiFi ou Bluetooth, en fonction de la conception du produit. Remplacez la bande par défaut par 5 GHz dans les paramètres de carte réseau. Si votre réseau ne prend pas en charge 5 GHz, une clé Bluetooth peut être utilisée à la place de la fonctionnalité Bluetooth interne.
16. Si vos paramètres Bluetooth ont déjà des contrôleurs de mouvement couplés, Windows ne découvre pas les nouveaux périphériques tant que ceux-ci n’ont pas été supprimés (s’ils ont été ajoutés à l’aide d’une clé spécifique, ils peuvent uniquement être supprimés avec cette clé).
17. Si votre PC intègre Bluetooth et que vous rencontrez des problèmes de connexion, essayez d’utiliser une carte Bluetooth USB. Pour ce faire, désactivez votre radio Bluetooth intégrée dans Device Manager puis couplez vos autres appareils Bluetooth avec la nouvelle carte.

### <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Les contrôleurs sont instables, sont bloqués, ou scintillent et disparaissent en réalité mixte. 

* Si votre ordinateur s’exécute sur un WiFi 2,4 GHz, basculez vers le WiFi 5 GHz. 
* Si vous utilisez un adaptateur Bluetooth externe, assurez-vous qu’il est connecté à un port USB 2,0 (qui est souvent, mais pas toujours, en noir), à l’écart des autres émetteurs sans fil ou des disques mémoire flash USB. 
* Exécutez l’utilitaire de résolution des problèmes Bluetooth dans **paramètres > mettre à jour & Security > résoudre les problèmes > Bluetooth** . 

### <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Mon contrôleur est bloqué dans un redémarrage infini.

Il s’agit d’un indicateur de batterie critique. Mettez les piles neuves dans l’appareil et, si le problème persiste, [réinitialisez les paramètres d’usine du contrôleur](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).

### <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Le portail de réalité mixte fonctionne, mais mes contrôleurs effectuent un suivi médiocre (volant, tremblement, etc.).

1. Les conditions d’éclairage peuvent affecter le suivi. Assurez-vous que vous n’êtes pas exposé à la lumière solaire directe et que vous n’avez pas une grande quantité de sources de lumière visible pour votre HMD (par exemple, des chaînes d’éclairages comme un arbre de Noël). 
2. Ces symptômes sont généralement dus à des défaillances de communication entre le contrôleur et le PC hôte, et indiquent une qualité de liaison Bluetooth médiocre. Consultez les [questions sur Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Les LED du contrôleur de mouvement ne sont pas allumés, mais les boutons et les sticks analogiques fonctionnent toujours dans le portail de réalité mixte.

Le cache d’étalonnage du contrôleur de mouvement est peut-être endommagé. Pour supprimer le cache, exécutez la commande suivante dans une invite de commandes d’administrateur :

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Ce dossier n’est pas accessible dans l’Explorateur Windows et ne peut être modifié qu’à partir d’une invite de commandes d’administrateur. Après avoir supprimé le dossier, redémarrez votre PC et reconnectez vos contrôleurs de mouvement pour restaurer les fichiers d’étalonnage.

### <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Mon contrôleur ressemble à une vive/Oculus, a une orientation étrange ou les boutons sont incorrectement mappés.

Le site Web n’a probablement pas de prise en charge complète du contrôleur motion.

### <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Les contrôleurs de mouvement ne s’affichent pas dans les applications et jeux SteamVR.

Tout d’abord, assurez-vous que les batteries de votre contrôleur sont facturées. Les contrôleurs ne fonctionneront pas si les batteries sont mortes ou morts. 

Si vous pouvez voir vos contrôleurs dans la maison de la falaise, mais pas dans les applications et jeux SteamVR, le pilote du modèle de contrôleur de mouvement n’est peut-être pas installé correctement. Pour vérifier que le pilote du modèle de contrôleur de mouvement est correctement installé :
1. Activez les deux contrôleurs de mouvement. Si vos contrôleurs sont associés à votre PC, accédez à **paramètres > appareils > Bluetooth & autres périphériques** , ou si vos contrôleurs sont associés à votre casque, accédez à **Device Manager > appareils d’interface utilisateur > contrôleur de mouvement** . Assurez-vous qu’ils s’affichent comme étant « connectés ». Si elles n’apparaissent pas ou s’affichent comme étant « jumelées », [couplez-les](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Accédez à **Device Manager > Bluetooth** et recherchez « contrôleur de mouvement ».
3. Sélectionnez l’appareil, puis accédez à **afficher > appareils par connexion** .
4. Accédez à **paramètres système > appareils > Bluetooth & autres périphériques > autres périphériques** pour voir s’ils sont visibles. Il y aura deux appareils « Bluetooth HID device », et sous chaque périphérique Bluetooth HID doit être un appareil nommé « contrôleur de mouvement » (avec des icônes grises) dans le même nœud que le contrôleur de mouvement.
5. Double-cliquez sur chaque appareil « contrôleur de mouvement » et accédez à l’onglet « pilote ». Vérifiez que la version du pilote indiquée correspond à l’une de [ces versions](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history).
6. Si ce n’est pas le cas, exécutez Windows Update, qui télécharge et installe automatiquement le pilote. Si vous êtes sur un PC avec des stratégies d’entreprise ou si Windows Update n’est pas limité, vous devrez peut-être installer le pilote de modèle de contrôleur de mouvement manuellement. Pour ce faire, accédez à [cette page](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) et recherchez la version du pilote correspondant à votre version de Windows 10. Les instructions d’installation sont disponibles sur la page de téléchargement.

### <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>La mise à jour du microprogramme du contrôleur prend beaucoup plus de deux minutes.

Consultez la [section questions Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Une mauvaise qualité de liaison Bluetooth est généralement à l’origine de ces problèmes.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Je viens d’insérer des piles neuves, mais le niveau de batterie virtuelle du contrôleur n’indique pas un niveau complet.

Le niveau de batterie du contrôleur de mouvement est réglé pour les piles AA. Certaines batteries rechargeables de basse tension peuvent ne pas être entièrement signalées, bien qu’elles soient entièrement chargées.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Mon pavé tactile du contrôleur Samsung motion est hors-Centre ou a un point mort.

Il s’agit probablement d’une erreur matérielle et vous devez revenir à votre revendeur ou fabricant d’équipement pour un remplacement ou un échange.

### <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Comment puis-je restaurer les contrôleurs sur les paramètres d’usine ?

Restaurez-la à des conditions d’usine (vous aurez besoin de piles neuves) :
1. Débranchez et mettez hors tension les contrôleurs.
2. Ouvrez la couverture de la batterie.
3. Insérez vos nouvelles piles.
4. Appuyez sur le bouton d’appariement (l’onglet situé en bas sous les batteries) et maintenez-le enfoncé.
5. Tout en maintenant le bouton de jumelage, mettez sous tension le contrôleur en appuyant sur le bouton Windows pendant cinq secondes (maintenez les deux boutons enfoncés).
6. Relâchez les boutons et attendez la mise sous tension du contrôleur. Cela prend jusqu’à 15 secondes et aucun indicateur ne s’affiche en cas de récupération de l’appareil. Si l’appareil s’allume immédiatement sur la version du bouton, la séquence du bouton de récupération n’a pas été inscrite et vous devez réessayer.
7. Si les contrôleurs ont été appariés à votre PC, accédez à **paramètres > Bluetooth > autres périphériques** , puis sélectionnez « contrôleur de mouvement » et « supprimer l’appareil » pour supprimer les associations de contrôleur des paramètres Bluetooth. 
8. [Couplez de nouveau les contrôleurs](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc) au casque ou au PC.
9. Une fois connecté avec l’hôte et le casque, l’appareil est mis à jour avec le dernier microprogramme disponible.

### <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Puis-je associer mon contrôleur Xbox à mon PC pour pouvoir l’utiliser dans le casque ?

Vous pouvez associer un contrôleur Xbox Bluetooth pour l’utiliser avec votre casque en suivant [ces instructions](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues). 

Si vous avez un contrôleur Xbox câblé, connectez-le à votre PC.

Certains jeux et applications utilisent le contrôleur Xbox différemment de celui utilisé dans la réalité mixte. Pour utiliser le contrôleur pour un jeu ou une application, sélectionnez « utiliser en tant que boîtier » dans la barre de l’application ou dites « utiliser en tant que boîtier ». Pour rebasculer le contrôleur vers la réalité mixte, sélectionnez à nouveau « utiliser en tant que boîtier », ou « utiliser avec le point de regard ». 



## <a name="if-your-motion-controllers-are-paired-to-your-headset"></a>Si vos contrôleurs de mouvement sont couplés à votre casque :

### <a name="should-i-pair-my-controllers-to-a-windows-mixed-reality-headset-that-has-built-in-bluetooth-radio"></a>Dois-je coupler mes contrôleurs à un casque Windows Mixed realer disposant d’une radio Bluetooth intégrée ?

Certains casques Windows mixtes de réalité, y compris Acer OJO 500 et Samsung Odyssey +, disposent de radios Bluetooth intégrées pour une utilisation avec les contrôleurs de mouvement. Les contrôleurs de mouvement fournis avec ces casques sont précouplés au casque en usine et n’exigent pas que votre ordinateur dispose d’une radio Bluetooth distincte. Ces contrôleurs de mouvement _peuvent_ être associés manuellement à la radio Bluetooth de votre PC, par exemple, pour une utilisation avec des casques Windows Mixed realisation qui n’ont pas de radio Bluetooth intégrées. 

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Comment faire associer de nouveaux contrôleurs si Windows Mixed Reality est déjà configuré sur mon ordinateur ?
Si vous associez vos contrôleurs à votre casque, utilisez l’application auxiliaire (le [portail de la réalité mixte](install-windows-mixed-reality.md#launch-mixed-reality-portal) peut vous aider à trouver une application auxiliaire à lancer ou vous donner une liste des applications auxiliaires que vous pouvez sélectionner).

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mes contrôleurs associés ne sont pas affichés dans le portail de la réalité mixte. 

* Tenez les contrôleurs devant votre casque et redémarrez-les en appuyant sur le bouton Windows pendant quatre secondes, puis de nouveau pendant deux secondes. 
* Si vous voyez « contrôleur de mouvement » dans **Device Manager > périphériques d’interface utilisateur** , repassez le processus de jumelage. 
* Si les voyants du contrôleur sont en cours de cycle, en allumant un quadrant d’éclairages à la fois, puis en les éteignant, ils sont en train de mettre à jour le microprogramme. Attendez la fin de la mise à jour et les contrôleurs doivent apparaître dans la réalité mixte. 
* Si vous utilisez une carte Bluetooth externe, assurez-vous que la carte est connectée à un port USB 2,0 (qui est souvent, mais pas toujours, en noir), loin d’autres émetteurs sans fil ou périphériques USB 3,0. 
* Si le PC vient de se bloquer et qu’un adaptateur Qualcomm est utilisé, il se peut qu’une réinitialisation ne fonctionne pas. Pour résoudre ce problème, débranchez le cordon d’alimentation à l’arrière de l’ordinateur (ou, si vous êtes sur un ordinateur portable, maintenez le bouton d’alimentation enfoncé pendant 10 secondes) et redémarrez l’ordinateur. 
* Exécutez l’utilitaire de résolution des problèmes Bluetooth dans **paramètres > mettre à jour & Security > résoudre les problèmes > Bluetooth** .  

### <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Comment puis-je ramener mes contrôleurs à leur appariement de fabrique ?

Pour ramener les contrôleurs de mouvement à leur appariement de fabriques, ou pour les associer à un casque Windows Mixed Reality avec une radio Bluetooth intégrée, exécutez l’application compagnon de l’appareil du casque (par exemple, l’application « Acer OJO 500 » ou l’application «Samsung HMD



## <a name="if-your-motion-controllers-are-paired-to-your-pc"></a>**Si vos contrôleurs de mouvement sont associés à votre PC :**

### <a name="my-motion-controllers-are-not-pairing"></a>Mes contrôleurs de mouvement ne sont pas couplés. 

* Si les contrôleurs ne sont pas activés, insérez des piles neuves. Si cela ne résout pas le problème, restaurez les paramètres d’usine de l’appareil en allumant l’appareil tout en maintenant les boutons d’appariement. Pour plus d’informations, consultez les [étapes de récupération](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) de l’appareil. 
* Si les contrôleurs sont allumés et que vous utilisez un adaptateur Bluetooth externe, assurez-vous que la carte est connectée à un port USB 2,0 (qui est souvent, mais pas toujours, en noir), à l’écart des autres émetteurs sans fil ou des disques mémoire flash USB. S’il ne fonctionne toujours pas, exécutez l’utilitaire de résolution des problèmes Bluetooth dans paramètres > mettre à jour & sécurité > résoudre les problèmes > Bluetooth. 
* Si vous utilisez un adaptateur Qualcomm et que le PC vient de se bloquer, redémarrez le PC. 
* Essayez de redémarrer les contrôleurs de mouvement qui ne sont pas couplés, un à la fois, puis redémarrez le PC. 
* Le cache du contrôleur de mouvement est peut-être endommagé. Pour résoudre ce problème, consultez les [étapes](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)ci-dessous. 
* Si aucune de ces étapes ne résout le problème, contactez le fabricant. 

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mes contrôleurs associés ne sont pas affichés dans le portail de la réalité mixte. 

* Tenez les contrôleurs devant votre casque et redémarrez-les en appuyant sur le bouton Windows pendant quatre secondes, puis de nouveau pendant deux secondes. 
* Si vos contrôleurs s’affichent comme étant connectés dans **paramètres > Bluetooth & d’autres appareils** , découplez-les et repassez le processus de jumelage. 
* Si les voyants du contrôleur sont en cours de cycle, en allumant un quadrant d’éclairages à la fois, puis en les éteignant, ils sont en train de mettre à jour le microprogramme. Attendez la fin de la mise à jour et les contrôleurs doivent apparaître dans la réalité mixte. 
* Si vous utilisez une carte Bluetooth externe, assurez-vous que la carte est connectée à un port USB 2,0 (généralement noir), loin d’autres émetteurs sans fil ou périphériques USB 3,0. 
* Si le PC vient de se bloquer et qu’un adaptateur Qualcomm est utilisé, il se peut qu’une réinitialisation ne fonctionne pas. Pour résoudre ce problème, débranchez le cordon d’alimentation à l’arrière de l’ordinateur (ou, si vous êtes sur un ordinateur portable, maintenez le bouton d’alimentation enfoncé pendant 10 secondes) et redémarrez l’ordinateur. 
* Exécutez l’utilitaire de résolution des problèmes Bluetooth dans **paramètres > mettre à jour & Security > résoudre les problèmes > Bluetooth** .  

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>J’essaie de coupler mes contrôleurs, mais ils ne s’affichent pas dans le menu « Ajouter un nouveau périphérique » dans les paramètres Bluetooth.

Vérifiez que vous n’avez pas déjà associé de contrôleurs. Si c’est le cas, supprimez-les et réessayez. Si le problème persiste, redémarrez le PC. En cas d’échec, consultez plus d' [informations sur Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Comment faire associer de nouveaux contrôleurs si Windows Mixed Reality est déjà configuré sur mon ordinateur ?

1. Insérez deux piles AA dans chaque contrôleur. N’effectuez pas encore le recouvrement de la batterie.
2. Appuyez sur le bouton Windows et maintenez-le enfoncé pendant deux secondes pour activer chaque contrôleur. Ils s’allumeront quand ils allumeront.
3. Mettez les contrôleurs en mode d’appariement. Le bouton d’appariement se trouve à l’intérieur du compartiment de la batterie (consultez cette [image](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc)). Appuyez et maintenez-la enfoncée jusqu’à ce que le contrôleur clignote.
4. Accédez à **paramètres > appareils > bluetooth & autres appareils** , puis à **Ajouter Bluetooth ou un autre appareil > Bluetooth** . Lorsque les contrôleurs s’affichent, sélectionnez-les pour les associer.

Remarque : si un autre ensemble de contrôleurs de mouvement est associé à votre PC, vous devez découpler ces contrôleurs avant de les associer. Si vous avez associé un ensemble de contrôleurs de mouvement à votre PC actuel et que vous les avez couplés avec un deuxième PC, vous devez les découpler et les réassocier à l’ordinateur actuel avant de les réutiliser.

### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Comment puis-je savoir si j’utilise la technologie Bluetooth ?

Les contrôleurs de mouvement utilisent la même technologie Bluetooth que sur de nombreux appareils grand public et sont conçus pour fonctionner avec la fonctionnalité Bluetooth incluse dans tout ordinateur récent. Votre ordinateur doit avoir une radio Bluetooth si la vérification de la compatibilité avec la réalité mixte a réussi. Pour vérifier : 
* Ouvrez « Device Manager ». 
* Développez la section Bluetooth et recherchez un adaptateur. 

![Capture d’écran d’un exemple de Device Manager. L’adaptateur est la radio Bluetooth.](images/devicemanagerbtadapterpic.png) 

Si votre ordinateur n’est pas équipé de Bluetooth, l’un des dongles recommandés est le [micro-adaptateur USB Bluetooth 4,0 basse énergie](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom).

### <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Le Wi-Fi ralentit sur mon Notebook quand les contrôleurs de mouvement sont activés.

Votre Notebook peut partager son antenne Wi-Fi avec Bluetooth lorsqu’il est connecté à un point d’accès 2,4 GHz. Vérifiez Device Manager si vous pouvez basculer la préférence de bande à 5 GHz. Si un réseau de 5 GHz n’est pas disponible et que les performances sont gravement affectées, envisagez d’utiliser une clé Bluetooth.

![Les paramètres de sélection de la bande wifi sont accessibles via le gestionnaire de périphériques](images/wifi5ghz.png)

### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>Mon ordinateur possède une technologie Bluetooth, mais je rencontre des problèmes avec mes contrôleurs.

Les contrôleurs de mouvement doivent fonctionner avec d’autres claviers, souris et contrôleurs de jeu Bluetooth, mais l’expérience varie en fonction du modèle de clavier, de souris ou de contrôleur de jeu que vous utilisez. Voici quelques opérations que vous pouvez effectuer pour améliorer les performances :
* Si votre ordinateur possède le Bluetooth, mais que vous rencontrez toujours des problèmes avec les contrôleurs de mouvement, envisagez de remplacer votre radio Bluetooth par une carte Bluetooth externe enfichable connectée à l’USB. Vous ne pouvez avoir qu’une seule carte radio Bluetooth active à la fois. Si vous branchez une radio externe en plus d’une radio existante, vous devez désactiver votre radio Bluetooth existante dans Device Manager (cliquez avec le bouton droit sur la carte et sélectionnez « Désactiver l’appareil ») et désassocier/recoupler tous vos périphériques Bluetooth précédents.
* Si vous utilisez une carte Bluetooth USB, connectez-la à un port USB 2,0 (les ports 2,0 sont souvent noirs et ne sont pas étiquetés « SS »), le cas échéant. Le port doit être physiquement séparé des éléments suivants :
    - le connecteur USB HMD
    - disques mémoire flash
    - disques durs
    - les récepteurs USB sans fil comme ceux des claviers/souris, branchez l’adaptateur Bluetooth USB sur le côté opposé de l’ordinateur aussi loin que possible à partir de ces autres connecteurs.
* Fermez la fenêtre Paramètres Bluetooth si elle est ouverte. Le fait de le laisser ouvert en arrière-plan signifie qu’un grand nombre d’appels supplémentaires sont effectués au protocole Bluetooth.
* Si votre casque est couplé à votre PC, utilisez la pile de pilotes Bluetooth de Windows et n’installez pas de piles de pilotes Bluetooth tierces. Les logiciels tiers peuvent ne pas fonctionner correctement.
* Désactivez le paramètre « afficher la notification pour se connecter à l’aide d’une paire SWIFT » sous « Bluetooth & autres appareils » pour réduire l’activité d’analyse de l’ordinateur hôte.
* Si vous utilisez une carte Bluetooth interne, assurez-vous que vous utilisez une antenne Bluetooth externe ou que vous rencontrez des problèmes de suivi. Si cela ne fonctionne pas, utilisez une clé Bluetooth externe (USB) après la désactivation du Bluetooth interne.
* L’appareil doit apparaître sous la catégorie « souris, clavier & stylet » dans les paramètres Bluetooth. S’il se trouve sous « autres appareils », découplez et couplez l’appareil.
* Retirez, découplez et mettez hors tension les écouteurs et les haut-parleurs Bluetooth. Celles-ci ne sont pas prises en charge avec Windows Mixed Reality. Utilisez la prise casque ou les haut-parleurs intégrés sur votre casque de réalité mixte pour une expérience audio optimale.

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>La reconnexion de mon deuxième contrôleur prend beaucoup de temps.

Certaines radios Intel plus anciennes rencontrent ce problème si les contrôleurs de mouvement sont mis sous tension en même temps. Évitez d’alimenter les contrôleurs en même temps.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Ma radio Qualcomm Bluetooth ne peut pas coupler les contrôleurs après un incident de PC.

Les pilotes radio Qualcomm (QCA) Bluetooth antérieurs à 10.0.0.448 peuvent finir en mauvais état après un incident Windows. Mettez complètement le PC hors tension pour contourner ce problème. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Je rencontre un mauvais suivi de contrôleur avec la radio Marvell.

Accédez à **Device Manager > > de la carte radio Bluetooth Marvell AVASTAR > propriétés > pilote** et assurez-vous que vous utilisez le pilote 15.68.9210.47 ou version ultérieure.
