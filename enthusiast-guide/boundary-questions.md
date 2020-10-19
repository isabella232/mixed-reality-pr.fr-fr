---
title: FAQ sur les limites
description: Résolution des problèmes avancés de Windows Mixed Reality pour les questions de limite qui vont au-delà de notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, limite
appliesto:
- Windows 10
ms.openlocfilehash: 9ddf9c7f7c5f36567e6968f619dabead9107731d
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174393"
---
# <a name="boundary-faqs"></a>FAQ sur les limites

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>Qu’est-ce qu’une limite et pourquoi dois-je en créer une ?

Une limite définit la zone que vous pouvez déplacer dans tout en portant votre casque Windows Mixed Reality. Il est important de créer une limite pour vous aider à éviter les obstacles que vous ne pouvez pas voir dans le casque. La limite ressemble à un contour blanc à l’intérieur de la réalité mixte et s’affiche lorsque vous y arrivez. Quand vous le voyez, ralentissez vos mouvements et évitez de franchir la limite ou d’étendre vos membres au-delà.

La zone à l’intérieur de la limite doit être libre de mobilier, des luminaires faiblement suspendus, des ventilateurs de plafond, etc. vous ne serez pas en mesure de vous heurter à quoi que ce soit. En [savoir plus sur l’intégrité et la sécurité dans Windows Mixed Reality](wmr-health-safety-comfort.md).

## <a name="how-do-i-create-a-boundary"></a>Comment faire créer une limite ?

Quand vous configurez votre casque pour la première fois, l’application d’installation (portail de réalité mixte) vous guide tout au long des étapes de création d’une limite. Toutefois, vous pouvez en créer un à tout moment :

1. Sélectionnez **démarrer > portail de réalité mixte** sur votre bureau.
2. Ouvrez « menu ».
3. Sélectionnez « configurer la limite de la salle de configuration » pour créer une nouvelle limite.

Si quelqu’un d’autre utilise votre casque, assurez-vous qu’ils comprennent la limite et comment l’utiliser. Si vous déplacez votre casque vers un nouvel emplacement, vous devez configurer une nouvelle limite qui fonctionne pour cet espace.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>J’obtiens un message d’erreur lorsque j’essaie de créer une limite

* Ne vous trouvez pas trop près d’un mur ou d’une autre obstruction lors de la création d’une limite.
* Veillez à conserver votre casque à la hauteur de la taille et à faire face à votre ordinateur pendant que vous tracez la limite.
* Assurez-vous que le capteur n’est pas bloqué et qu’il y a suffisamment de lumière.
* L’espace que vous tracez doit être supérieur à trois mètres carrés.
* L’espace ne doit pas être trop grand ou trop complexe. Collez-vous à une forme géométrique simple sans grand nombre de torsions et de virages.
* Ne vous contentez pas de traverser votre propre chemin d’accès lorsque vous effectuez le suivi.
* Si vous êtes bloqué dans un coin, recommencez.

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>Le système ne trouve pas la limite et je suis présenté avec l’interface utilisateur du programme d’installation

Cela signifie que le système de suivi n’a pas pu reconnaître votre environnement. Si vous êtes dans un nouvel environnement, vous devez configurer la [limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary).
Si vous avez déjà utilisé l’appareil dans cet environnement et configuré une limite :

* Assurez-vous que la salle a suffisamment de lumière.
* Vérifiez que vous avez porté l’appareil et recherché dans la pièce. L’appareil doit observer votre environnement pour savoir où il se trouve. S’il est assis sur un bureau ou une table, il ne trouve pas vos limites.
* Débranchez l’appareil, fermez Windows Mixed Reality et rebranchez-le.
* Si un événement de l’environnement a changé, l’appareil peut ne plus le reconnaître. Configurez une nouvelle limite.

Si ces étapes ne résolvent pas le problème, supprimez les données de votre environnement et réinstallez la limite.

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>Le système me présente avec l’interface utilisateur qui me demande de choisir la configuration pour toutes les expériences ou assis/debout, et je vois mes limites

La recherche des limites de l’appareil prend trop de temps. Vous pouvez contourner ce message en choisissant l’option permettant d’utiliser une limite et vous serez dirigé vers votre page d’hébergement de la réalité Windows Mixed avec vos limites présentes.

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>Je vois souvent un message indiquant « j’ai perdu mes limites »

Le système de suivi fait un suivi du temps et de l’identification de votre environnement. Dans cet État, l’appareil ne peut plus afficher vos limites et le casque bascule sur 3DOF pour vous permettre de vous tenir au fait de l’univers réel jusqu’à ce qu’il trouve à nouveau vos limites. Pour résoudre ce problème :

1. Assurez-vous que la salle a suffisamment de lumière.
2. Réexécutez le programme d’installation si vous avez récemment redécoré ou remodelé la salle.
3. Débranchez l’appareil, fermez Windows Mixed Reality et rebranchez-le.
4. Effacez les données de votre environnement et réinstallez l’appareil.
5. Si le message persiste, contactez le support technique.

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>Un message indique que la limite est introuvable. Que dois-je faire ?

Windows Mixed Reality peut avoir des difficultés à identifier vos limites existantes. Vous pouvez créer une nouvelle limite ou vous pouvez utiliser votre appareil en mode « assiste et debout ».

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Un message indique « perte de suivi » ou « nous n’avons pas de limite pour cet espace »

Vous devez créer une nouvelle limite. Pour ce faire :

1. Sélectionnez **démarrer > portail de réalité mixte**.
2. Ouvrez « menu ».
3. Sélectionnez « configurer la limite de la salle de configuration ».

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>La limite est toujours visible. Comment faire disparaître ?

La limite s’affiche lorsque vous y êtes proche. Si votre limite comprend des sections qui ont une forme étroite ou irrégulière, vous pouvez vous y retrouver et la faire apparaître, plus souvent que vous le souhaitez. Pour résoudre ce problème, essayez de recréer votre limite à l’aide d’une forme plus grande et plus normale. Pour ce faire :

1. Sélectionnez **démarrer > portail de réalité mixte**.
2. Ouvrez « menu ».
3. Sélectionnez « configurer la limite de la salle de configuration ».

## <a name="can-i-turn-off-the-boundary-temporarily"></a>Puis-je désactiver temporairement la limite ?

* Sélectionnez **démarrer > portail de réalité mixte**.
* Ouvrez « menu ».
* Transformez « limite » en « désactivé ». Veillez à rester à un seul endroit lorsque la limite est désactivée.

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Comment faire choisir entre « assis et debout » et « toutes les expériences » ?

Si vous choisissez « assis et debout » lors de l’installation du casque ou ultérieurement, vous utiliserez votre casque sans limite. Cela signifie que vous devez rester en un seul endroit lors de l’utilisation du casque, afin de pouvoir éviter les obstacles physiques et le déclenchement des dangers. Vous pouvez vous asseoir ou vous déplacer, mais vous ne pourrez pas vous déplacer. Gardez à l’esprit que les obstacles peuvent être liés à la surcharge et à vous.

Certaines applications peuvent être conçues pour fonctionner avec une limite. vous ne pourrez peut-être pas les utiliser ou ne pas avoir la même expérience, si vous les utilisez sans limite.

Si vous choisissez « toutes les expériences », vous configurerez une limite et pourrez utiliser les applications et les expériences qui fonctionnent avec une limite, ainsi que celles qui n’en ont pas besoin.

## <a name="see-also"></a>Voir aussi

* [Demander à la communauté](https://answers.microsoft.com)
* [Contactez-nous pour obtenir de l’aide](https://support.microsoft.com/contactus/)