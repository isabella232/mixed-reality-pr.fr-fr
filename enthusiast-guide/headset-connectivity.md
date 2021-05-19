---
title: FAQ sur la connectivité du casque
description: 'Connectivité du casque : Dépannage de la connectivité du casque Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.'
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, casque
appliesto:
- Windows 10
ms.openlocfilehash: 2d46275fd86eedbe93a81bc97c156f29794e8c42
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143235"
---
# <a name="headset-connectivity-faqs"></a>FAQ sur la connectivité du casque

## <a name="my-headset-will-not-wake-up"></a>Mon casque ne sort pas de veille

Si votre casque est en veille et que le fait de cliquer sur le bouton Wake up ne fonctionne pas, redémarrez votre PC.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Mon ordinateur ne dispose pas d’un port d’affichage HDMI et/ou

Vous devrez peut-être utiliser un adaptateur. Pour obtenir la liste des adaptateurs pris en charge, cliquez [ici](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) .

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Puis-je utiliser des câbles d’extension USB ou HDMI et/ou DisplayPort avec des casques Windows de réalité mixte

Les casques pour Windows Mixed Reality ne prennent pas officiellement en charge l’utilisation de câbles d’extension USB, HDMI ou DisplayPort. Si vous utilisez ces câbles, l’expérience de la réalité mixte peut être affectée en raison des variations de l’intégrité des signaux et de la puissance du bus entre le contrôleur USB de votre PC et le casque de la réalité mixte. Essayez d’utiliser votre casque sans câble d’extension dans les cas suivants :

* L’affichage du casque affiche brièvement un écran bleu, puis le portail noir et de réalité mixte redémarre ou complète les énumérations en cours d’utilisation
* L’audio du casque diminue ou devient indisponible
* Le casque scintille entre le noir et l’affichage correct

## <a name="i-am-getting-a-check-your-display-cable-error"></a>J’obtiens une erreur « vérifier votre câble d’affichage »

* Si vous utilisez des adaptateurs pour connecter votre casque à votre ordinateur, assurez-vous qu’ils prennent en charge Windows Mixed Reality et qu’ils sont compatibles avec 4K. Essayez également de connecter l’adaptateur au PC avant de connecter le casque à la carte.
* Essayez d’utiliser un autre port HDMI ou DisplayPort.
* Connectez votre casque à un DisplayPort 1,2 ou une version ultérieure, ou HDMI 1,4 ou version ultérieure. Assurez-vous que le port correspond à la carte graphique la plus avancée sur votre PC.
* Si votre ordinateur dispose de graphiques intégrés et discrets, assurez-vous que vous utilisez le port HDMI ou DisplayPort sur votre carte graphique active. Cela peut signifier que vous devez connecter l’affichage de votre PC à un port non HDMI.
* Si votre ordinateur dispose de graphiques intégrés et discrets, et que les graphiques intégrés sont plus anciens et ne prennent pas en charge Windows Mixed Reality, essayez de désactiver le GPU intégré.
* Connectez un moniteur PC au port HDMI ou DisplayPort de votre PC. Assurez-vous que vos pilotes graphiques sont à jour. Téléchargez et installez les pilotes directement à partir de AMD, Nvidia ou Intel, car ils seront probablement plus récents que ce qui est publié dans Windows Update.
* Si vous avez un moniteur externe branché dans un port HDMI, essayez de le brancher dans un DisplayPort et utilisez le port HDMI pour votre casque.
* Assurez-vous de brancher le câble HDMI de votre casque sur un port « HDMI out » sur votre ordinateur, et non sur un port « HDMI in ».
* Windows n’est peut-être pas en mesure de détecter la connexion du câble d’affichage. Ouvrez la Gestionnaire de périphériques et vérifiez si le casque est listé sous « moniteurs ». Si ce n’est pas le cas, sélectionnez **Action > Rechercher les modifications matérielles**.

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Un message indique « placer sur votre casque », mais j’ai mon casque sur

Lorsque vous placez sur votre casque, Windows Mixed realisation peut nécessiter quelques secondes pour recharger votre espace. Si ce message ne disparaît pas, assurez-vous que l’autocollant de protection a été retiré du capteur de proximité à l’intérieur du casque entre les lentilles. Si le problème persiste, contactez le fabricant de votre casque.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Un message indique « Connectez votre casque », mais je l’ai branché sur mon casque

- Assurez-vous que les câbles USB et HDMI ou DisplayPort du casque sont connectés aux ports corrects sur votre ordinateur. Voici comment identifier les ports corrects :

    - Les ports USB 3,0 ont un logo spécial avec une marque « SS » (indiquant « supervitesse »). La pièce intérieure du port est normalement bleue, mais les ports USB 2,0 plus anciens sont généralement noirs ou blancs à l’intérieur.
    - Si votre ordinateur dispose de deux ports HDMI ou DisplayPort, utilisez celui qui se connecte à la carte graphique, et non la carte mère de l’ordinateur. Ce n’est pas toujours évident, ce qui, bien que les ports discrets se trouvent souvent dans un emplacement d’extension sur l’ordinateur. Si vous essayez d’utiliser un port et qu’il ne fonctionne pas, essayez l’autre.

- Débranchez et branchez les câbles USB et HDMI ou DisplayPort à partir de votre casque pour vous assurer qu’ils sont connectés en toute sécurité. Lorsque vous branchez le câble USB, essayez de ne pas interrompre l’insertion du câble USB.
- Essayez un concentrateur USB 3,0 en externe si vous voyez une énumération partielle du casque, par exemple, une série de périphériques USB sont énumérés, mais rien ne sous les « casques de réalité mixte » dans Gestionnaire de périphériques.
- Accédez au site Web du fabricant du casque et mettez à jour les pilotes et le microprogramme de votre casque.
- Connectez votre casque à un autre PC et ouvrez Gestionnaire de périphériques. Même si ce PC n’est pas entièrement compatible avec Windows Mixed Reality, vous pouvez vérifier si votre casque est énuméré. Si votre casque n’est pas énuméré sur plusieurs PC, il peut y avoir un problème matériel.

> [!NOTE]
> Pour les utilisateurs de surface : les versions antérieures du logiciel de mise à jour du microprogramme du concentrateur de surface et du microprogramme du concentrateur USB ne sont pas compatibles avec les casques de réalité mixte. Si vous recevez un message « Connectez votre casque » sur un PC surface, vérifiez si des appareils signalent une erreur « code 10 : l’appareil ne peut pas démarrer » dans Gestionnaire de périphériques. Dans ce cas, [supprimez le pilote en conflit](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Vous ne devez effectuer cette opération qu’une seule fois.

Remarque pour les utilisateurs de Windows 10-N : Si votre PC exécute Windows 10 N, l’erreur « code 28 : la classe d’installation n’est pas présente ou n’est pas valide » s’affiche dans Gestionnaire de périphériques après avoir branché votre casque de réalité mixte. Les éditions N de Windows 10 ne sont pas prises en charge par Windows Mixed Reality. Pour plus d’informations, suivez ces [instructions](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) .

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un message indique « vérifier votre câble USB » ou « vitesse USB insuffisante »

* Assurez-vous que vous utilisez un port USB 3,0 pris en charge sur votre ordinateur :

    * Assurez-vous que le câble USB de votre casque est branché.
    * Exécutez le [portail Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) pour vous assurer que le contrôleur USB 3,0 de votre PC est pris en charge.
    * Connectez votre casque aux autres ports USB 3,0 sur votre PC. Certains PC disposent de plusieurs contrôleurs USB 3,0.
    * Déconnectez temporairement tous les périphériques USB connectés à votre ordinateur et connectez-vous uniquement à votre casque.
    * Sur les PC personnalisés, même si un port peut être marqué comme port USB 3,0, il peut être connecté à un contrôleur USB 2,0. Une fois votre casque connecté, ouvrez Gestionnaire de périphériques, localisez et cliquez une seule fois sur les appareils énumérés à partir de votre casque, puis accédez à **afficher > appareils par connexion**.
* Essayez votre casque sur un autre PC. Si cet autre PC n’est pas entièrement compatible avec Windows Mixed Reality, vérifiez Gestionnaire de périphériques pour voir si le message « vitesse USB insuffisante » s’affiche. S’il n’est pas répertorié correctement sur plusieurs PC, votre casque est peut-être défectueux.
* Retirez tous les extendeurs ou hubs entre le casque et l’ordinateur.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Le portail de réalité mixte n’a pas été lancé après avoir branché mon casque

Votre casque n’a peut-être pas été détecté correctement en raison d’un problème sous-jacent. Lancez le portail de réalité mixte manuellement et recherchez les messages d’erreur qui s’affichent.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mon casque s’est arrêté de fonctionner quand mon ordinateur passe en mode veille ou veille prolongée, ou quand mon ordinateur est en train de redémarrer avec mon casque connecté

1. Ouvrez Gestionnaire de périphériques et vérifiez que votre casque est listé sous « périphériques de réalité mixte ».
2. Sélectionnez votre casque sous « appareils de réalité mixte » et vérifiez que l’état de l’appareil indique « ce périphérique fonctionne correctement ».
3. Si vous voyez une erreur « code 43 » indiquant que l’appareil a cessé de fonctionner, ou si votre casque n’est pas listé sous « appareils de réalité mixte », débranchez et rebranchez le câble USB de votre casque. Microsoft étudie un problème potentiel d’interopérabilité des logiciels/pilotes, ce qui peut entraîner cette erreur. Ce problème affecte un petit nombre de PC et devrait être résolu dans une prochaine mise à jour du pilote du casque de la réalité mixte.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mon casque fait en sorte que mon PC génère une vérification de bogue (écran bleu) lorsque je mets mon PC en veille ou lorsqu’il est en mode veille prolongée.

Assurez-vous que vous êtes sur le pilote 10.0.19041.2034 ou plus récent.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Le pilote du casque n’a pas été installé automatiquement lorsque je suis connecté au casque

Sur les nouveaux PC, ou sur les PC équipés d’une copie de Windows 10 récemment installée, le pilote de casque peut être mis en file d’attente derrière d’autres mises à jour Windows et ne peut pas être installé immédiatement.

1. Accédez à **démarrer > gestionnaire de périphériques** et Regardez sous « appareils de réalité mixte » pour votre casque. L’état de l’appareil doit indiquer que « le périphérique fonctionne correctement ».
2. Cliquez avec le bouton droit sur l’appareil et sélectionnez « mettre à jour le pilote ».

Si cela n’a pas fonctionné, essayez de désinstaller le pilote :

1. Accédez à **démarrer > gestionnaire de périphériques** et Regardez sous « appareils de réalité mixte » pour votre casque. L’état de l’appareil doit indiquer que « le périphérique fonctionne correctement ».
2. Cliquez avec le bouton droit sur l’appareil, puis sélectionnez « désinstaller l’appareil ».
3. Dans la nouvelle fenêtre contextuelle qui s’affiche, activez la case à cocher « Supprimer le logiciel du pilote pour cet appareil », puis sélectionnez « Désinstaller ».
4. Quand cela se termine, débranchez le casque de votre ordinateur et rebranchez-le. Windows Update va maintenant télécharger et installer un nouveau pilote.

Remarque : Si vous avez une édition N de Windows, vous devez basculer vers une édition standard de Windows 10 pour utiliser Windows Mixed Reality.