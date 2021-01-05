---
title: FAQ sur les réverbérations HP G2
description: Questions fréquentes sur l’utilisation du casque de réverbération HP G2
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, performances
appliesto:
- Windows 10
ms.openlocfilehash: 55baf3f076b8cf0f815f899658b3bbe61292e267
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725900"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>Forum aux questions sur les réverbérations HP G2

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>Y a-t-il un ordre spécifique que je dois suivre pour connecter les câbles du casque à un PC

HP recommande :

- Connectez d’abord le câble à 6 mètres au casque avant de vous connecter au PC ou à l’alimentation.
- Laissez le câble à 6 mètres connecté au casque après l’installation initiale.
- Lorsque le casque n’est pas utilisé, déconnectez l’adaptateur d’alimentation du câble à 6 mètres.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>Que dois-je faire pour obtenir une image plus claire ?

Voici quelques opérations que vous pouvez essayer si vous estimez que votre affichage semble un peu flou :

- Assurez-vous que votre casque se trouve correctement et que vos yeux sont centrés sur les objectifs.
- Essayez d’ajuster l’IPD (distance interpupillary). La réverbération G2 utilise une IPD matérielle. Pour le modifier, recherchez l’ajustement IPD sur votre casque.
- Si vous avez besoin de lunettes ou de contacts, vous devez les utiliser lors de l’utilisation de l’appareil.
- Vérifiez que vos lentilles sont propres (chiffon Microfiber uniquement-aucun fluide).
- En raison de la conception avancée du casque, il peut y avoir des images fantômes mineures lors du démarrage de l’appareil à froid jusqu’à ce que les écrans montent en charge.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>J’obtiens une erreur 7-14 «un problème s’est produit lors de la connexion au casque

Le code d’erreur 7-14 signifie que certains des composants USB2 requis n’ont pas été trouvés.  En raison du câble très long de la réverbération de HP G2, certaines des tolérances pour les signaux USB sont plus strictes.  Cela signifie qu’un port sur votre ordinateur peut fonctionner plus efficacement qu’un autre.

Si vous constatez une erreur 7-14 « un problème est survenu », procédez comme suit :

- Assurez-vous que les pilotes les plus récents sont installés pour votre casque et votre contrôleur USB.
- Vérifiez que vous utilisez un pilote USB Microsoft. Il doit y avoir un « Microsoft » dans le nom de l’appareil « contrôleur hôte eXtensible ».
- Essayez de brancher le câble sur un port USB-3,0 différent sur votre ordinateur. (Essayez le type USB-C et tapez-A ports)
- Utilisez le C USB inclus sur un adaptateur pour essayer d’autres ports.
- Essayez de brancher le casque sur votre ordinateur via un concentrateur USB.

> [!NOTE]
> HP recommande d’utiliser uniquement des contrôleurs USB intégrés à la carte mère avec des appareils G2 de réverbération.
> Si vous ne parvenez pas à vous connecter à votre appareil, contactez le [support technique HP](https://support.hp.com/us-en)

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>J’obtiens une erreur 13-14 « une erreur s’est produite » lorsque mon PC sort de la veille prolongée (S4)

Parfois, pendant le processus de reprise, la carte vidéo ne peut pas établir de connexion. par conséquent, le fait de déconnecter le type C de votre PC et de le rebrancher peut vous aider à établir une connexion.

## <a name="my-hp-motion-controller-joystick-will-sometimes-stick-to-one-side"></a>Ma manette de jeu HP Motion Controller peut parfois se trouver sur un côté

Ce problème est résolu en déappuyant entièrement sur la manette de jeu jusqu’à ce qu’elle se déplace librement.

## <a name="others-state-i-am-loud-or-that-my-audio-is-clipping-while-i-am-using-the-microphone-with-some-applications"></a>Les autres États sont bruyants ou que mon audio est tronqué pendant que j’utilise le microphone avec certaines applications

Les niveaux de volume en entrée sont automatiquement définis sur 100% lorsque le microphone de réverbes HP G2 est reconnu pour la première fois par un PC Windows. En raison des microtéléphones de reréverbération G2's de haute qualité, la sensibilité d’entrée est beaucoup plus élevée que les paramètres Windows 10 par défaut. Nous vous recommandons de définir le niveau d’entrée du microphone G2 de réverbération à partir de 50% et de monter en puissance. Un paramètre optimal est spécifique à l’utilisateur, en particulier lors de l’utilisation d’applications qui n’ont pas de paramètre de microphone « gain automatique ». Des exemples d’applications qui ont un « gain automatique » sont Skype, zoom, équipes et Cisco WebEx, mais pas toutes les applications de réseaux sociaux ou de radiodiffusion ne disposent pas de cette fonctionnalité.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>Le portail de réalité mixte indique « Impossible d’exécuter une réalité mixte sur ce casque », mais cela fonctionnait correctement avec mon casque WMR précédent

Cela peut se produire si votre réverbération HP G2 requiert un PC plus puissant pour garantir une expérience optimale. Pour plus d’informations, consultez la [Configuration minimale requise](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) pour les PC

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Il semble que mon affichage à gauche soit étiré, et l’affichage à droite est décentré et demi-noir

Cela peut se produire lorsque votre casque n’est pas en cours d’exécution à la résolution native. En raison de la nature des affichages haute résolution dans le HMD de réverbération HP G2, tous les systèmes ne peuvent pas restituer la résolution native. Un correctif est disponible dans un futur Windows Update qui traitera le problème de rendu lorsque le casque n’est pas à la résolution native.

Il existe plusieurs raisons pour lesquelles votre système ne peut pas être rendu à la résolution native :

- Le DisplayPort sur le système n’est peut-être pas compatible avec 1,3 ou ne prend peut-être pas en charge les quatre couloirs.
- Si vous utilisez un adaptateur, il est possible qu’il ne soit pas compatible avec HBR3 ou qu’il ne prenne pas en charge les quatre couloirs.
- Si votre système possède un GPU hybride, cela peut limiter la bande passante disponible pour le DisplayPort.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>Pourquoi mes modèles de contrôleur de mouvement HP ne s’illustrent pas correctement dans un jeu

Bien que la plupart des jeux n’affichent pas les contrôleurs ou n’utilisent pas les modèles installés par le pilote, certains jeux utilisent leurs propres versions des modèles de contrôleur, soit pour les personnaliser, soit pour afficher une aide contextuelle pour les entrées disponibles. En règle générale, cela ne bloque pas les fonctionnalités des jeux, mais peut entraîner des confusions, voire des artefacts visuels. Cela ne peut être corrigé qu’avec une mise à jour du jeu lui-même.

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>Mes jeux SteamVR ne semblent pas fonctionner correctement avec les contrôleurs de mouvement HP

Alors que les développeurs travaillent à mettre à jour leurs jeux pour la compatibilité avec HP Motion Controller, nous avons fourni des liaisons de contrôleur personnalisées pour la plupart des jeux les plus populaires sur la vapeur. Avec « Windows Mixed Reality for SteamVR » entièrement mis à jour vers la version 1.2.444, ces liaisons doivent être récupérées automatiquement lorsque votre jeu est en cours d’exécution. Toutefois, si votre jeu ne semble pas inscrire vos actions pour l’instant, vous pouvez rechercher manuellement des profils de liaison personnalisés à l’aide du menu des paramètres SteamVR.
Pour

- Ouvrez le menu SteamVR en appuyant sur le bouton de menu du contrôleur de mouvement approprié
- Sélectionnez l’icône « Paramètres » dans le coin inférieur droit du menu SteamVR
- Sélectionnez l’onglet « contrôleurs ».
- Sélectionnez l’option gérer les liaisons de contrôleur.

À partir de là, vous pouvez modifier la liaison de votre contrôleur actif en « personnalisé », ce qui permet d’ouvrir l’option permettant d’essayer les liaisons de jeux de la communauté partagée.
Si aucune liaison de jeu personnalisée n’a encore été partagée pour ce jeu (ou si vous n’êtes pas satisfait de celles que vous avez essayées), vous pouvez également créer vos propres liaisons de jeu personnalisées et même aider le reste de la communauté en les partageant après quelques sessions de jeu.