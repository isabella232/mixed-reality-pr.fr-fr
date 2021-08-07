---
title: Étude de cas-utilisation du son spatial dans RoboRaid
description: le son Spatial est l’une des fonctionnalités les plus intéressantes de Microsoft HoloLens, ce qui permet aux utilisateurs de découvrir ce qui se passe autour d’eux quand les objets sont hors de vue.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, son spatial, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, HoloLens, MRTK, Shared Computer Toolkit de la réalité mixte, uc
ms.openlocfilehash: f4a47fe119dffbd32d264cc8e21ae2b3ade7cfcccef8e7e18fbb4491783d0542
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208995"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Étude de cas-utilisation du son spatial dans RoboRaid

cet article décrit les défis que l’équipe d’expérience Microsoft HoloLens a rencontrés lors de la création de l’audio pour la [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) mixte de la réalité mixte.

## <a name="the-tech"></a>Le Tech

le [son Spatial](spatial-sound.md) est l’une des fonctionnalités les plus intéressantes de Microsoft HoloLens, ce qui permet aux utilisateurs de découvrir ce qui se passe autour d’eux quand les objets ne sont pas en ligne de vue.

Dans RoboRaid, l’utilisation la plus évidente et la plus claire du son spatial alerte le joueur à un problème qui se produit en dehors de la vision du périphérique. Par exemple, l’infraction peut entrer à partir de l’un des murs analysés de la pièce. Si vous n’êtes pas face à l’emplacement où il est entré, vous pouvez le manquer. Pour vous avertir de cette invasion, vous allez entendre un peu de données audio provenant de l’endroit où l’effraction est entrée, ce qui vous permet de savoir que vous devez agir rapidement pour l’arrêter.

## <a name="behind-the-scenes"></a>Dans les coulisses

créer un son spatial pour les applications de HoloLens est tellement nouveau et unique que les problèmes peuvent être difficiles à résoudre, car il n’y a pas de projets passés à référencer. Nous espérons que ces exemples de défis audio que nous avons rencontrés lors de la création de RoboRaid vous aideront à créer de l’audio pour vos propres applications.

### <a name="be-mindful-of-taxing-the-cpu"></a>Soyez attentif à l’imposition de l’UC

Le son spatial peut être exigeant sur le processeur. Pour une expérience occupée comme RoboRaid, il était essentiel de conserver le nombre d’instances de son spatial à huit à un moment donné. En règle générale, c’est aussi simple que de définir la limite des instances pour différents événements audio. Toutes les instances qui se produisent une fois la limite atteinte sont supprimées. Par exemple, lorsque drones génère, leurs screams sont limités à trois instances à un moment donné. Si l’on considère que quatre drones peuvent être générés à la fois, trois screams sont nombreux, car il n’existe aucun moyen pour votre cerveau d’effectuer le suivi de nombreux événements audio similaires. Cela a pour effet de libérer des ressources pour d’autres événements de son spatial, tels que des explosions ennemis ou des ennemis qui se préparent à prendre.

### <a name="rewarding-a-successful-dodge"></a>Récompenser une densité de réussite

le mécanicien dodging est l’un des mécanismes de jeu les plus importants dans RoboRaid, et tout ce que nous avons trouvé est véritablement propre à l’expérience HoloLens. Par conséquent, nous voulions que les densités soient très satisfaisantes pour le joueur. Nous avons obtenu le « Whizz-by » Doppler pour paraître assez tôt dans le développement. Initialement, mon plan consistait à utiliser une boucle et à la manipuler en temps réel en utilisant le volume, le tangage et le filtre. L’implémentation de ce fut très élaborée. Avant de valider des ressources pour générer cela, nous avons créé un prototype peu coûteux à l’aide d’une ressource avec l’effet Doppler intégré à juste pour déterminer son degré d’utilisation. Notre développement talentueux l’a fait pour que la WHIZZ de cette ressource soit lue exactement 0,7 seconde avant que le projectile n’ait été passé par l’oreille du joueur et que les résultats sont impressionnants ! Inutile de préciser que nous avons fossé la solution la plus complexe et implémenté le prototype.

*(Pour plus d’informations sur la création d’un élément multimédia audio avec l’effet Doppler intégré, consultez [100 Whooshes dans 2 minutes](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).)* 
<br>
![Dodging avec succès, le projectile récompense le joueur avec un son satisfaisant Whizz.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Fossés de sons inefficaces

À l’origine, nous avions voulu lire un son de l’explosion derrière le joueur une fois qu’il a correctement denser le projectile ennemi, mais nous avons décidé de l’abandonner pour plusieurs raisons. Tout d’abord, il n’a pas l’impression d’être aussi efficace que le Whizz-by SFX que nous avons utilisé pour la densité. Au moment où le projectile atteint un mur derrière vous, un autre événement s’est produit dans le jeu qui masquerait le son. Deuxièmement, nous n’avions pas de collisions à l’étage. nous ne pouvons donc pas faire fonctionner l’explosion lorsque le projectile atteint le plancher au lieu des murs. Enfin, il existait le coût de l’UC du son spatial. L’ennemi du Scorpion Elite (un qui peut être analysé à l’intérieur du mur) a une attaque spéciale qui prend en compte huit projectiles. Non seulement cela faisait une énorme pagaille dans la combinaison, mais elle a également introduit une fissure terrible, car elle a atteint l’UC trop difficile.

### <a name="communicating-a-hit"></a>Communication d’un accès

un problème intéressant que nous avons rencontré sur le HoloLens était la difficulté de communiquer efficacement avec un joueur. La réussite de l’expérience de la réalité mixte est le sentiment que le récit se passe. Cela signifie que vous devez vous croire à la lutte contre l’invasion d’un robot étranger dans votre propre salon.

Les joueurs ne pensent évidemment rien quand ils sont atteints. nous avons donc dû trouver un moyen de convaincre le joueur qu’une erreur incorrecte s’est produite. Dans les jeux conventionnels, vous pouvez voir une animation qui vous permet de savoir que votre caractère a pris un point, ou l’écran peut clignoter en rouge et votre personnage peut grunt un peu. Étant donné que ces types de signaux ne fonctionnent pas dans une expérience de réalité mixte, nous avons décidé de combiner le signal visuel avec un son exagéré qui indique que vous avez pris des dégâts. J’ai créé un grand son, et j’ai fait en sorte qu’il soit bien visible dans la combinaison. Ensuite, pour faire ressortir encore davantage, nous avons ajouté un bref signal sonore comme si un sub nucléaire était récepteur. 
<br>
![Quand un joueur atteint RoboRaid, il voit un signal visuel, mais obtient également un signal audio exagéré qui lui indique qu’il a pris des dégâts.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obtenir du gros son de petits intervenants

HoloLens les haut-parleurs sont petits et clairs pour répondre aux besoins de l’appareil. vous ne pouvez donc pas vous attendre à un trop bas de la gamme. À l’instar du développement pour les smartphones ou les périphériques de jeu de poche, les concepteurs de sons et les compositeurs doivent être attentifs au contenu de la fréquence audio. Je conçoive toujours des sons ou écrit de la musique avec une plage de fréquences complète, car le casque est une option pour les utilisateurs. toutefois, pour garantir la compatibilité avec les orateurs HoloLens, j’exécute un test occasionnellement en plaçant une égalisation dans le maître de tout dupont dans lequel je travaille. Le paramètre EQ est constitué d’un filtre passe-haut autour de 600 Hz à 700 Hz (pas trop abrupt) et d’un filtre passe-bas à environ 10 000 (abrupt). Cela devrait vous faire une idée approximative de la façon dont vos sons seront lus sur l’appareil.

Si vous utilisez des basses pour obtenir le sens de la modification de la corde dans votre musique, vous constaterez peut-être que votre musique perd complètement le sens de la racine lorsque vous appliquez ce paramètre d’égalisation. Pour remédier à cela, j’ai ajouté une autre couche aux basses qui est une octave supérieure (avec quelques harmoniques riches) et à la mélanger pour avoir une idée de la racine. Parfois, l’utilisation de la distorsion pour regrouper les harmoniques donnera suffisamment de contenu de fréquence dans la plage supérieure pour que notre cerveau pense qu’il y a quelque chose sous-jacent. Cela est vrai pour les SFX comme les impacts, les explosions ou les sons pour des moments spéciaux, tels que les super attaques d’un patron. Vous ne pouvez vraiment pas vous reposer sur le bas pour que le joueur ait un sens d’impact ou de poids. Comme pour la musique, l’utilisation de la distorsion pour vous aider à bénéficier d’une certaine facilité.

### <a name="making-your-audio-cues-stand-out"></a>Faire ressortir vos signaux audio

Naturellement, tous les membres de l’équipe voulaient Bombastic de musique, des canons bruyants et des explosions bizarres. mais ils veulent également pouvoir entendre VoiceOver ou toute autre indication audio critique pour les jeux.

Sur un jeu de console avec un intervalle de fréquence complet, vous avez plus d’options pour diviser les fréquences en fonction de l’importance du son. Pour RoboRaid, je me suis limité dans le nombre de plages de fréquences que je pourrais décourber des sons. Si vous utilisez le filtre passe-bas et que vous courbez trop à partir de l’extrémité supérieure du spectre, vous n’avez rien à laisser sur le son, car il n’y a pas beaucoup de temps d’arrêt.

Pour faire en sorte que le son RoboRaid soit aussi grand que possible sur l’appareil, nous avons dû réduire la plage dynamique de l’expérience complète et avoir fait une utilisation intensive de l’appareil en créant une hiérarchie claire de l’importance pour différents types de sons. Je définis l’ensemblance de-2 dB à-6 dB en fonction de l’importance. Personnellement, je n’aime pas bien des canards évidents dans les jeux. j’ai donc passé beaucoup de temps à régler le temps d’apparition et de sortie en fondu, ainsi que la quantité d’atténuation du volume. Nous avons configuré des bus distincts pour le son spatial, le son non spatial, le VO et le bus à l’état sec sans réverbération pour la musique. Ensuite, nous avons créé des bus haute priorité, critiques et non critiques afin que les ressources soient configurées pour accéder aux bus appropriés.

J’espère que les professionnels de l’audio sont en mesure de travailler sur leurs propres applications comme je travaillais sur RoboRaid. Je ne parviens pas à voir (et à entendre !) ce que les personnes talentueux en dehors de Microsoft vont rencontrer pour HoloLens.

## <a name="do-it-yourself"></a>Faites-le vous-même

L’une des astuces que j’ai découvertes pour faire de certains événements (par exemple, des explosions) un son « plus grand » (comme pour le remplissage de la pièce) consistait à créer une ressource mono pour le son spatial et à la mélanger avec une ressource stéréo 2D, pour la lire en 3D. Cela prend un certain réglage, car une trop grande quantité d’informations dans le contenu stéréo réduit la direction des ressources mono. Toutefois, si vous obtenez le solde juste, vous obtiendrez des sons énormes qui permettront aux joueurs d’allumer leurs têtes dans le bon sens.

Vous pouvez essayer les grands sons en utilisant les ressources audio ci-dessous :

**Scénario 1**
1. Téléchargez [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) et configurez pour lire le son spatial et l’affecter à un événement.
2. Téléchargez [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) et définissez la lecture en stéréo 2D et attribuez au même événement que ci-dessus. Étant donné que ces éléments multimédias sont normalisés en Unity, Atténuez le volume des deux ressources afin qu’elles ne soient pas découpées.
3. Lire les deux sons ensemble. Déplacez votre tête pour comprendre le son spatial.

**Scénario 2**
1. Téléchargez [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) et configurez pour lire le son spatial et l’assigner à un événement.
2. Lisez cette ressource seule et comparez-la à l’événement du scénario 1.
3. Essayez un autre équilibre entre les fichiers mono et stéréo.

## <a name="see-also"></a>Voir aussi

* [Son spatial](spatial-sound.md)
* [RoboRaid pour Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
