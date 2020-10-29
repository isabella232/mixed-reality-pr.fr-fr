---
title: FAQ sur l’installation
description: Dépannage avancé de Windows Mixed Reality pour les questions de configuration qui vont au-delà de notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, installation, Windows Mixed Reality, portail Windows Mixed Reality
appliesto:
- Windows 10
ms.openlocfilehash: 2e079cae16a20a4e0a2e6c967ecedef1950ded57
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680318"
---
# <a name="setup-faqs"></a>FAQ sur l’installation 

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>Le portail de réalité mixte ne s’ouvre pas lorsque je branche mon casque.

Portail de réalité mixte, l’application qui vous guide à travers le programme d’installation de Windows Mixed Reality est conçue pour s’ouvrir automatiquement lorsque vous branchez un casque compatible. S’il ne s’ouvre pas, accédez à démarrer et tapez « portail de réalité mixte » dans la zone de recherche pour ouvrir l’application. Si vous ne trouvez pas de portail de réalité mixte, cela peut signifier que vous devez effectuer une [mise à jour vers la dernière version de Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Comment faire choisir entre « assis et debout » et « toutes les expériences » ?

Si vous choisissez « assis et debout », lors de l’installation du casque ou plus tard, vous utiliserez votre casque sans limite. Vous pouvez vous asseoir en position ou en haut, mais vous devrez sinon rester à un même endroit, car vous n’aurez pas de limite pour vous aider à éviter les obstacles physiques. Certaines applications peuvent être conçues pour fonctionner avec une limite. vous ne pourrez peut-être pas les utiliser ou vous n’aurez peut-être pas la même expérience si vous les utilisez sans limite. Consultez [« qu’est-ce qu’une limite et pourquoi dois-je en créer une ? »](boundary-questions.md#whats-a-boundary-and-why-should-i-create-one).

Si vous choisissez « toutes les expériences », vous configurez une limite et vous pouvez utiliser les applications et les expériences qui fonctionnent avec une limite, ainsi que celles qui n’en ont pas besoin. 

## <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-to-windows-mixed-reality-home"></a>L’apprentissage de la réalité mixte n’a pas été exécuté lors du premier lancement et je me suis rendu à la page d’hébergement Windows Mixed Reality.

Vous pouvez réexécuter l’expérience d’apprentissage en suivant les [étapes de réexécution](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 

## <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>Mes contrôleurs ne s’affichent pas dans ma page d’hébergement Windows Mixed Reality.

Assurez-vous que vos contrôleurs possèdent des piles complètes et qu’ils sont correctement couplés à l’aide de Bluetooth. Essayez de mettre les contrôleurs hors tension et à l’aide du bouton Windows. Si vous ne voyez toujours pas vos contrôleurs, essayez de procéder à l’annulation de l’appariement et à la nouvelle association de chaque contrôleur : 
* Si votre casque intègre une radio, utilisez l’application auxiliaire fournie avec le casque pour découpler, puis associez à nouveau les contrôleurs (le portail de réalité mixte peut vous aider à trouver l’application complémentaire appropriée). 
* Si les contrôleurs sont couplés au PC, accédez à **appareils > Bluetooth > paramètres** pour annuler le couplage et associez à nouveau vos contrôleurs. 

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>L’étage de ma page d’hébergement Windows Mixed Reality ne semble pas être à la bonne hauteur.

Sélectionnez **démarrer > réglage du plancher** , qui sera lancé une fois que vous aurez placé l’application dans le monde entier, pour apporter des modifications tout en portant votre casque. Dans cette application, vous serez invité à utiliser le pavé tactile (contrôleur de mouvement) ou le panneau de direction (boîtier de commande) pour ajuster la hauteur du plancher. Lorsque l’étage est correct, utilisez le bouton Windows pour revenir à votre page d’hébergement.

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>Je ne peux pas afficher un aperçu de ce que je vois dans mon casque sur mon bureau.

Le portail Windows Mixed Reality a un bouton de **lecture** en bas de l’écran qui vous permet d’afficher un aperçu de ce que vous voyez dans votre casque sur l’écran de votre bureau. Pour des raisons de performances, cette fonctionnalité est disponible uniquement sur les PC exécutant Windows Mixed Reality ultra (90Hz).

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>J’obtiens un message d’erreur « un problème est survenu » ou je rencontre des problèmes dans le portail de réalité mixte
Pour obtenir plus d’informations sur un code d’erreur spécifique, consultez [cette page](error-codes.md). Vous pouvez également essayer d’effectuer les opérations suivantes :

Redémarrez Windows Mixed Reality :
1. Déconnectez les deux câbles du casque de votre PC.
2. Redémarrez votre PC.
3. Reconnectez votre casque.

Assurez-vous que votre PC reconnaît votre casque :
1. Sélectionnez Démarrer.
2. Tapez « Device Manager » dans la zone de recherche et sélectionnez-le dans la liste. 
3. Développez « appareils de réalité mixte » et vérifiez si votre casque est listé. 

S’il n’est pas listé :
1. Branchez le casque sur les différents ports du PC, le cas échéant.
2. Recherchez les dernières mises à jour logicielles à partir de Windows Update.
3. Désinstallez et réinstallez Windows Mixed Reality :
    1. Déconnectez les deux câbles du casque de votre PC.
    2. Sélectionnez **paramètres > réalité mixte > désinstaller** .
    3. Si vos contrôleurs de mouvement sont associés à votre PC, sélectionnez **paramètres > appareils > Bluetooth & autres périphériques** pour les découpler. Sélectionnez chaque contrôleur et « supprimer l’appareil ». Si vos contrôleurs sont associés à votre casque, vous pouvez ignorer cette étape.
    4. Reconnectez votre casque à votre ordinateur pour réinstaller Windows Mixed Reality.

## <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>Je ne peux pas diriger d’entrée (contrôleurs, boîtier de roulette, souris/clavier) dans Windows Mixed Reality.

Lorsque vous placez sur votre casque, l’entrée doit être automatiquement basculée vers votre expérience de réalité mixte via le capteur de présence de votre casque. Une barre bleue doit apparaître sur votre bureau :

![Bureau Windows avec entrée dirigée vers le casque](images/1050px-windowsy.png)

Si l’entrée n’est pas automatiquement activée, vous avez peut-être désactivé le basculement d’entrée automatique dans **paramètres > la réalité mixte > l’affichage du casque > le basculement d’entrée** . Vous pouvez toujours taper **touche Windows + Y** sur votre clavier pour basculer manuellement l’entrée sur votre casque ou revenir sur le bureau.

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>Pendant le démarrage de la réalité mixte, je suis coincé à l’extrémité de la tête, puis à l’étage.

Cette étape permet à votre casque de reconnaître votre espace et de restaurer un étage virtuel et une limite existants. Lorsque vous placez sur votre casque, le processus d’analyse peut prendre jusqu’à 10 secondes. Une fois l’opération terminée, vous serez dans la page d’hébergement Windows Mixed Reality ou vous serez invité à configurer à nouveau votre limite.

Si le processus d’analyse prend plus de 10 secondes, il peut y avoir un problème avec le capteur de proximité dans le casque :
1. Vérifiez que la vignette a été retirée du capteur de proximité. Le capteur de proximité se trouve à l’intérieur du casque, à peu près là où se trouve le centre de votre stress.
2. Vérifiez que votre capteur de proximité bascule entre les entrées sur votre casque : avec votre doigt, recouvrez et dévoilez le capteur de proximité plusieurs fois pour vérifier que l’entrée bascule sur le casque. Vous devez voir la bannière de **touche Windows + Y** en haut de votre PC. Vous pouvez basculer manuellement l’entrée sur le casque à tout moment en tapant la **touche Windows + Y** sur votre clavier.

## <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Mon contrôleur Xbox ne fonctionne pas avec Windows Mixed Reality.

* Assurez-vous que votre contrôleur est allumé, entièrement débité et connecté au PC.
* Remplacez les piles du contrôleur.
* Si vous utilisez un contrôleur Bluetooth, accédez à **paramètres > appareils > Bluetooth & d’autres périphériques** sur votre ordinateur et assurez-vous qu’ils sont associés (ils doivent être listés sur la page).
