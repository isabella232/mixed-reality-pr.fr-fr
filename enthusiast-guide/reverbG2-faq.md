---
title: FAQ sur les réverbérations HP G2
description: Questions fréquentes sur l’utilisation du casque de réverbération HP G2
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, performances
appliesto:
- Windows 10
ms.openlocfilehash: 82f9accc8e24574faf7c826aff1908bea7350b08
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049471"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>Forum aux questions sur les réverbérations HP G2

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>Y a-t-il un ordre spécifique que je dois suivre pour connecter les câbles du casque à un PC

HP recommande :

- Connectez d’abord le câble à 6 mètres au casque avant de vous connecter au PC ou à l’alimentation.
- Laissez le câble à 6 mètres connecté au casque après l’installation initiale.
- Lorsque le casque n’est pas utilisé, déconnectez l’adaptateur d’alimentation du câble à 6 mètres.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>Que dois-je faire pour obtenir une image plus claire ?

Voici quelques opérations que vous pouvez essayer si vous estimez que votre affichage semble un peu flou :

- Assurez-vous que votre casque est bien en tête pour que vos yeux soient centrés sur les lentilles.
- Essayez d’ajuster l’IPD (distance interpupillary). Notez que la réverbération G2 utilise une IPD matérielle. Pour le modifier, recherchez l’ajustement IPD sur votre casque.
- Si vous avez besoin de lunettes ou de contacts, ceux-ci sont toujours requis.
- Vérifiez vos lentilles si elles doivent être nettoyées (en tissu microfiber uniquement – aucun fluide).
- En raison de la conception avancée du casque, il peut y avoir des fantômes d’image mineurs au cours des premières minutes lors du démarrage de l’appareil alors que les écrans plats ont la possibilité de chauffer.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>J’obtiens une erreur 7-14 «un problème s’est produit lors de la connexion au casque

Si vous constatez une erreur 7-14 « une erreur s’est produite », procédez comme suit :

- Assurez-vous que les pilotes les plus récents sont installés.
- Essayez de brancher le câble sur un port USB-3,0 différent.
- Utilisez le C USB sur un adaptateur inclus pour essayer d’autres ports.

Essayez de brancher le câble sur un autre concentrateur USB.  

> [!NOTE]
> HP recommande d’utiliser uniquement des contrôleurs USB intégrés à la carte mère avec des appareils G2 de réverbération.
> Si vous ne parvenez pas à vous connecter à votre appareil, contactez le [support technique HP](https://support.hp.com/us-en)

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>J’obtiens une erreur 13-14 « une erreur s’est produite » lorsque mon PC sort de la veille prolongée (S4)

Parfois, pendant le processus de reprise, la carte vidéo ne peut pas établir de connexion. par conséquent, le fait de déconnecter le type C de votre PC et de le rebrancher peut vous aider à établir une connexion.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>Le portail de réalité mixte indique « Impossible d’exécuter une réalité mixte sur ce casque », mais cela fonctionnait correctement avec mon casque WMR précédent

Cela peut se produire si votre réverbération HP G2 requiert un PC plus puissant pour garantir une expérience optimale. Pour plus d’informations, consultez la [Configuration minimale requise](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) pour les PC

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Il semble que mon affichage à gauche soit étiré, et l’affichage à droite est décentré et demi-noir

Cela peut se produire lorsque votre casque n’est pas en cours d’exécution à la résolution native. En raison de la nature des affichages haute résolution dans le HMD de réverbération HP G2, tous les systèmes ne seront pas en mesure d’afficher la résolution native. Un correctif est disponible dans un futur Windows Update qui traitera le problème de rendu lorsque le casque n’est pas à la résolution native.

Il existe plusieurs raisons pour lesquelles votre système ne peut pas être rendu à la résolution native :

- Le DisplayPort sur le système n’est peut-être pas compatible avec 1,3 ou ne prend peut-être pas en charge les 4 couloirs.
- Si vous utilisez un adaptateur, il est possible qu’il ne soit pas compatible avec HBR3 ou qu’il ne prenne pas en charge les 4 couloirs.
- Si votre système possède un GPU hybride, cela peut limiter la bande passante disponible pour le DisplayPort.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>Pourquoi mes modèles de contrôleur de mouvement HP ne s’illustrent pas correctement dans un jeu

Si de nombreux jeux fonctionnent immédiatement avec les contrôleurs de mouvement HP, certains jeux ont des dépendances avec les fonctionnalités des contrôleurs existants et peuvent donc présenter des problèmes :

- Modèle incorrect affiché : la résolution requiert une mise à jour du jeu. En règle générale, cela ne bloque pas les fonctionnalités du jeu, mais peut entraîner des confusions, voire des artefacts visuels.
- Dépendance sur le pavé tactile ou plus généralement sur la disposition d’entrée du contrôleur. SteamVR permet de créer des liaisons personnalisées pour aider à contourner ce type de problème :
    - Windows Mixed Reality for SteamVR comprend des liaisons personnalisées pour certains jeux. Ces liaisons sont utilisées automatiquement lorsque le jeu est démarré et aucune action de l’utilisateur n’est nécessaire.