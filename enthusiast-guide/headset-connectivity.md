---
title: FAQ sur la connectivité du casque
description: Dépannage avancé de la connectivité du casque Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, casque
appliesto:
- Windows 10
ms.openlocfilehash: abdd0f04443e110f1eb19a31fb3d77e2f3bde929
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434557"
---
# <a name="headset-connectivity-faqs"></a>FAQ sur la connectivité du casque

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Mon ordinateur ne dispose pas d’un port d’affichage HDMI et/ou

Vous devrez peut-être utiliser un adaptateur. Pour obtenir la liste des adaptateurs pris en charge, cliquez [ici](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) .

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Puis-je utiliser des câbles d’extension USB ou HDMI et/ou DisplayPort avec des casques Windows Mixed Reality ?
Les casques pour Windows Mixed Reality ne prennent pas officiellement en charge l’utilisation de câbles d’extension USB, HDMI ou DisplayPort. L’utilisation de ces câbles peut avoir un impact significatif sur votre expérience de réalité mixte en raison des variations de l’intégrité des signaux et de la puissance du bus entre le contrôleur USB de votre PC et le casque de la réalité mixte. Si l’affichage du casque affiche brièvement un écran bleu, puis que le portail de la réalité noire et du portail de la réalité mixte redémarre ou complète les énumérations en cours d’utilisation, ou si le son du casque est réduit ou devient incorrect, ou si le casque scintille entre le noir et l’affichage correct, essayez d’utiliser votre casque sans câbles d’extension.

## <a name="i-am-getting-a-check-your-display-cable-error"></a>J’obtiens une erreur « vérifier votre câble d’affichage »

* Si vous utilisez des adaptateurs pour connecter votre casque à votre ordinateur, assurez-vous qu’ils prennent en charge Windows Mixed Reality (l’adaptateur doit être compatible avec les 4K). Essayez également de connecter l’adaptateur au PC avant de connecter le casque à la carte.
* Essayez d’utiliser un autre port HDMI et/ou DisplayPort.
* Connectez votre casque à un DisplayPort 1,2 ou une version ultérieure, ou HDMI 1,4 ou version ultérieure. Assurez-vous que le port correspond à la carte graphique la plus avancée sur votre PC.
* Si votre ordinateur dispose de graphiques intégrés et discrets, assurez-vous que vous utilisez le port HDMI et/ou DisplayPort sur votre carte graphique active. Cela peut signifier que vous devez connecter l’affichage de votre PC à un port non HDMI.
* Si votre ordinateur dispose de graphiques intégrés et discrets, et que la carte graphique intégrée est plus ancienne et ne prend pas en charge Windows Mixed Reality, essayez de désactiver le GPU intégré.
* Connectez un moniteur PC au port HDMI et/ou DisplayPort du PC. Assurez-vous que vos pilotes graphiques sont à jour. Téléchargez et installez les versions de AMD, Nvidia ou Intel directement, car elles seront probablement plus récentes que celles publiées sur Windows Update.
* Si vous avez un moniteur externe branché dans un port HDMI, essayez de le brancher dans un DisplayPort et utilisez le port HDMI pour votre casque.
* Assurez-vous de brancher le câble HDMI de votre casque sur un port « HDMI out » sur votre ordinateur, et non sur un port « HDMI in ».
* Windows n’est peut-être pas en mesure de détecter la connexion du câble d’affichage. Ouvrez la Device Manager et vérifiez si le casque est listé sous « moniteurs ». Si ce n’est pas le cas, sélectionnez **Action > Rechercher les modifications matérielles**. 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Un message indique « placer sur votre casque », mais j’ai mon casque sur

Lorsque vous placez sur votre casque, Windows Mixed realisation peut nécessiter quelques secondes pour recharger votre espace. Si ce message ne disparaît pas, assurez-vous que l’autocollant de protection a été retiré du capteur de proximité, qui se trouve à l’intérieur du casque entre les lentilles. Si cela ne résout pas le problème, contactez le fabricant de votre casque.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Un message indique « Connectez votre casque », mais je l’ai branché sur mon casque

1. Assurez-vous que les câbles USB et HDMI et/ou DisplayPort du casque sont connectés aux ports corrects sur votre ordinateur. Voici comment identifier les ports appropriés :
    * Les ports USB 3,0 ont un logo spécial avec une marque « SS » (indiquant « supervitesse »). La pièce intérieure du port est normalement bleue, tandis que les ports USB 2,0 plus anciens sont généralement noirs ou blancs à l’intérieur.
    * Si votre ordinateur dispose de deux ports HDMI et/ou DisplayPort, utilisez celui qui se connecte à la carte graphique, et non la carte mère de l’ordinateur. Il n’est pas toujours évident de savoir qui, bien que les ports discrets se trouvent souvent dans un emplacement d’extension sur l’ordinateur. Si vous essayez d’utiliser un port et qu’il ne fonctionne pas, essayez l’autre.
2. Débranchez et branchez les câbles USB et HDMI et/ou DisplayPort à partir de votre casque pour vous assurer qu’ils sont connectés en toute sécurité. Lorsque vous branchez le câble USB, essayez de ne pas interrompre l’insertion du câble USB.
3. Ouvrez Device Manager et vérifiez que votre casque est listé sous « périphériques de réalité mixte ». Lorsque vous sélectionnez votre casque, l’état de l’appareil doit indiquer « ce périphérique fonctionne correctement ». Les points d’exclamation jaunes sur les appareils dans Device Manager indiquent des erreurs.
    * Si « capteurs Hololens » est listé avec un point d’exclamation jaune dans Device Manager, sélectionnez l’appareil. Si vous voyez un «code 10 : les pilotes de cet appareil ne sont pas installés. Il n’y a pas de pilotes compatibles pour cet appareil», [Installez manuellement le pilote du casque](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset).
    * Si vous utilisez plusieurs casques de réalité mixte sur votre ordinateur et que vous avez installé manuellement le pilote du casque de la réalité mixte, la mise à jour manuelle du pilote peut s’appliquer uniquement au casque connecté à la fois et non aux autres casques. Dans ce cas, vous verrez «code 31 : cet appareil ne fonctionne pas correctement car Windows ne peut pas charger les pilotes requis pour cet appareil. (Code 31). Le message ALPC demandé n’est plus disponible dans Device Manager. Dans **Device Manager > des appareils de réalité mixte**, cliquez avec le bouton droit sur votre casque, puis sélectionnez « désinstaller l’appareil ». Sélectionnez OK pour confirmer, puis débrancher et rebrancher votre casque.
4. Si vous voyez une énumération partielle du casque (une série de périphériques USB sont énumérés, mais rien sous les « casques de réalité mixte » dans Device Manager), essayez un concentrateur USB 3,0 en externe.
5. Accédez au site Web du fabricant du casque et mettez à jour les pilotes et le microprogramme de votre casque.
6. Connectez votre casque à un autre PC et ouvrez Device Manager. Même si ce PC n’est pas entièrement compatible avec Windows Mixed Reality, vous pouvez vérifier si votre casque est énuméré. Si votre casque n’effectue pas d’énumération sur plusieurs PC, il peut y avoir un problème matériel.

Remarque pour les utilisateurs de surface : les versions antérieures du logiciel de mise à jour du microprogramme du concentrateur de surface et du microprogramme du concentrateur USB ne sont pas compatibles avec les casques de réalité mixte. Si vous obtenez un message « Connectez votre casque » sur un PC surface, vérifiez si des appareils signalent une erreur « code 10 : l’appareil ne peut pas démarrer » dans Device Manager. Dans ce cas, [supprimez le pilote en conflit](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Vous ne devez effectuer cette opération qu’une seule fois.

Remarque pour les utilisateurs de Windows 10 N : Si votre PC exécute Windows 10 N, vous verrez une erreur « code 28 : la classe d’installation n’est pas présente ou non valide » dans Device Manager après avoir branché votre casque de réalité mixte. Les éditions N de Windows 10 ne sont pas prises en charge par Windows Mixed Reality. Pour plus d’informations, suivez ces [instructions](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) .

Ces informations sont également affichées dans un [organigramme de résolution des problèmes](headset-connectivity-flowchart.md).

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un message indique « vérifier votre câble USB » ou « vitesse USB insuffisante ».

* Assurez-vous que vous utilisez un port USB 3,0 pris en charge sur votre ordinateur :
    * Assurez-vous que le câble USB de votre casque est branché.
    * Exécutez le [portail Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) pour vous assurer que le contrôleur USB 3,0 de votre PC est pris en charge.
    * Connectez votre casque aux autres ports USB 3,0 sur votre PC. Certains PC disposent de plusieurs contrôleurs USB 3,0.
    * Déconnectez temporairement tous les périphériques USB connectés à votre ordinateur et connectez-vous uniquement à votre casque.
    * Sur les PC personnalisés, même si un port peut être marqué comme port USB 3,0, il peut être connecté à un contrôleur USB 2,0. Une fois votre casque connecté, ouvrez Device Manager, recherchez et cliquez sur l’un des appareils énumérés à partir de votre casque, puis accédez à **afficher > appareils par connexion**.
* Essayez votre casque sur un autre PC. Si cet autre PC n’est pas entièrement compatible avec Windows Mixed Reality, vérifiez Device Manager pour voir si le message « vitesse USB insuffisante » s’affiche. Si elle ne s’énumère pas correctement sur plusieurs PC, votre casque est peut-être défectueux.
* Retirez tous les extendeurs ou hubs entre le casque et l’ordinateur.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Le portail de réalité mixte n’a pas été lancé après avoir branché mon casque.

Le casque n’a peut-être pas été détecté correctement en raison d’un problème sous-jacent. Lancez le portail de réalité mixte manuellement et recherchez les messages d’erreur qui s’affichent. 

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mon casque s’est arrêté de fonctionner lorsque mon ordinateur passe en mode veille ou veille prolongée, ou lors du redémarrage de mon PC avec mon casque connecté.

1. Ouvrez Device Manager et vérifiez que votre casque est listé sous « périphériques de réalité mixte ».
2. Sélectionnez votre casque sous « appareils de réalité mixte » et vérifiez que l’état de l’appareil indique « ce périphérique fonctionne correctement ».
3. Si vous voyez une erreur « code 43 » indiquant que l’appareil a cessé de fonctionner, ou si votre casque n’est pas listé sous « appareils de réalité mixte », débranchez et rebranchez le câble USB de votre casque. Microsoft étudie un éventuel problème d’interopérabilité entre les logiciels et les pilotes, ce qui peut entraîner cette erreur. Ce problème affecte un petit nombre de PC et devrait être résolu dans une prochaine mise à jour du pilote du casque de la réalité mixte.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mon casque fait en sorte que mon PC génère une vérification de bogue (écran bleu) lorsque je mets mon PC en veille ou lorsqu’il est en mode veille prolongée.
Assurez-vous que vous êtes sur le pilote 10.0.18362.1062 ou plus récent.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Le pilote du casque n’a pas été installé automatiquement lorsque je suis connecté au casque.

Sur les nouveaux PC, ou sur les PC équipés d’une copie de Windows 10 récemment installée, le pilote de casque peut être mis en file d’attente derrière d’autres mises à jour Windows et ne peut pas être installé immédiatement. Pour l’installer manuellement :
1. Accédez à **démarrer > Device Manager** et Regardez sous « autres appareils » pour un appareil « capteurs hololens » avec un point d’exclamation jaune : ![ affichage des capteurs hololens Device Manager](images/hololenssensors.png)
2. Cliquez avec le bouton droit sur l’appareil et sélectionnez Propriétés. Si les propriétés de l’appareil lisent « les pilotes de cet appareil ne sont pas installés (code 28) », fermez la fenêtre et poursuivez. S’il existe un autre message, suivez les étapes de dépannage sur le reste de cette page.
![Code 28 des capteurs HoloLens dans Device Manager](images/code28.png)
3. Cliquez à nouveau avec le bouton droit sur l’appareil et sélectionnez « mettre à jour les pilotes... ». puis « rechercher automatiquement les mises à jour logicielles de pilotes » une fois l’appareil mis à jour, vous devriez voir votre casque répertorié sous « appareils de réalité mixte » dans Device Manager : l' ![ appareil de réalité mixte apparaît dans Device Manager](images/mixedrealitydevices.png)

Si l’installation manuelle ne fonctionne pas, ou si vous ne trouvez pas le pilote sous autres périphériques, vous devez probablement désinstaller le pilote existant et le réinstaller. Pour ce faire :
1. Accédez à **démarrer > Device Manager** et Regardez sous « appareils de réalité mixte » pour votre casque. L’état de l’appareil doit indiquer que « le périphérique fonctionne correctement ».
2. Cliquez avec le bouton droit sur l’appareil, puis sélectionnez « désinstaller l’appareil ».
3. Dans la nouvelle fenêtre contextuelle qui s’affiche, activez la case à cocher « Supprimer le logiciel du pilote pour cet appareil », puis sélectionnez « Désinstaller ».
4. Quand cela se termine, débranchez le casque de votre ordinateur et rebranchez-le. Windows Update va maintenant télécharger et installer un nouveau pilote.

Remarque : Si vous avez une édition N de Windows, vous devrez basculer vers une édition standard de Windows 10 pour utiliser Windows Mixed Reality.


