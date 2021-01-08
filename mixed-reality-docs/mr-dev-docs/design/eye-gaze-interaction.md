---
title: Interaction par pointage du regard
description: En savoir plus sur les interactions avec les yeux et les regards sur HoloLens 2, ainsi que les nouveaux niveaux de contexte et de compréhension humaine s’ils vous permettent de bénéficier d’expériences holographiques.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Suivi oculaire, réalité mixte, entrée, point de présence oculaire, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de la réalité mixte, conception, interactions
ms.openlocfilehash: b5091b92fd048f72184212401d54ad0b7353875c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008579"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interaction Eye-orientée vers le regard de HoloLens 2

![Démonstration du suivi oculaire dans MRTK](images/mrtk_et_scenemenu.jpg)

L’une de nos nouvelles fonctionnalités passionnantes sur HoloLens 2 est le suivi oculaire. Sur notre [suivi oculaire sur la page HoloLens 2](eye-tracking.md) , nous avons mentionné la nécessité pour chaque utilisateur de passer par un [étalonnage](https://docs.microsoft.com/hololens/hololens-calibration), de fournir des conseils pour les développeurs et de mettre en surbrillance les cas d’utilisation pour le suivi oculaire. L’entrée Eye-pointage est toujours un nouveau type d’entrée utilisateur et il y a beaucoup à apprendre. 

Bien que l’entrée Eye-pointage soit uniquement utilisée au sein de notre expérience d’interpréteur de commandes holographique (l’interface utilisateur que vous voyez quand vous démarrez votre HoloLens 2), plusieurs applications, telles que la « structure de travail [hololens »](https://www.microsoft.com/p/mr-playground/9nb31lh723s2), illustrent de superbes exemples sur la façon dont les entrées de regard oculaire peuvent être ajoutées à la magie de votre expérience holographique.
Sur cette page, nous aborderons les considérations relatives à la conception pour l’intégration de l’entrée de regard pour interagir avec vos applications holographiques.

Vous en apprendrez davantage sur les principaux avantages et les défis uniques qui accompagnent les entrées de regard. Sur la base de ces informations, nous fournissons plusieurs recommandations de conception pour vous aider à créer des interfaces utilisateur compatibles avec le regard. 

## <a name="device-support"></a>Prise en charge des appareils

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Fonctionnalité</strong></td>
     <td><a href="../hololens-hardware-details.md"><strong>HoloLens (1ère génération)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
</tr>
<tr>
     <td>Œil-point de regard</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>


## <a name="eye-gaze-input-design-guidelines"></a>Conseils pour la conception d’entrées de regard

La création d’une interaction qui tire parti du ciblage visuel à déplacement rapide peut être difficile. Dans cette section, nous résumerons les principaux avantages et défis à prendre en compte lors de la conception de votre application. 

### <a name="benefits-of-eye-gaze-input"></a>Avantages de l’entrée en regard des yeux

- **Pointage à haute vitesse.** Le muscle oculaire est le muscle le plus rapide dans le corps humain. 

- **Faible effort.** Pratiquement aucun mouvement physique n’est nécessaire. 

- **Implicite.** Souvent décrits par les utilisateurs comme « sens de lecture », les informations relatives aux mouvements oculaires d’un utilisateur permettent au système de savoir à quelle cible l’utilisateur envisage de s’impliquer. 

- **Autre canal d’entrée.** L’œil-point de vue peut fournir une entrée de prise en charge puissante pour les entrées de main et vocales, basées sur des années d’expérience des utilisateurs en fonction de leur coordination manuelle.

- **Attention visuelle.** Un autre avantage important est la possibilité de déduire ce à quoi un utilisateur fait attention. Cela peut aider dans différents domaines d’application, allant de l’évaluation plus efficace de conceptions différentes à l’aide d’interfaces utilisateur plus intelligentes et de signaux sociaux améliorés pour la communication à distance.

Pour résumer, l’utilisation de la forme œil-point d’entrée offre un signal d’entrée contextuel rapide et sans effort. Cela est puissant lorsqu’il est combiné à d’autres entrées, telles que la *voix* et l’entrée *manuelle* , pour confirmer l’intention de l’utilisateur.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Défis de l’entrée

Bien qu’il soit possible d’utiliser le point de regard pour créer des expériences utilisateur satisfaisantes, ce qui vous permet de vous sentir comme un superhéros, il est également important de savoir ce qu’il n’est pas judicieux de prendre en compte. La liste suivante présente certains *défis* à prendre en compte et comment les résoudre quand vous travaillez avec des entrées de regard : 

- **Votre regard est « Always on »** Le moment où vous ouvrez vos couvercles oculaires, vos yeux commencent que sur les choses de l’environnement. En réagissant à chaque aspect que vous effectuez et en émettant accidentellement des actions, parce que vous avez examiné un peu trop de temps, vous risquez d’avoir une expérience insuffisante.
Nous vous recommandons de combiner le regard des yeux avec une *commande vocale*, un *mouvement manuel*, un *clic sur le bouton* ou un logement étendu pour déclencher la sélection d’une cible (pour plus d’informations, consultez [Eye-point de vue et validation](gaze-and-commit-eyes.md)).
Cette solution permet également à un mode dans lequel l’utilisateur peut effectuer des recherches librement sans être submergé par le déclenchement involontaire d’un événement. Ce problème doit également être pris en compte lors de la conception de commentaires visuels et auditifs lors de la recherche d’une cible.
Essayez de ne pas saturer l’utilisateur avec des effets de fenêtres instantanées ou des sons de survol. La subtilité est essentielle. Nous aborderons quelques-unes des meilleures pratiques ci-dessous pour aborder les [recommandations de conception](eye-gaze-interaction.md#design-recommendations).

- **Observation et contrôle** Imaginez que vous souhaitez redresser précisément une photographie sur votre mur. Vous regardez les bords de la photo et ce qui se trouve à proximité pour voir si elle est bien alignée. Imaginez maintenant comment procéder lorsque vous souhaitez utiliser le point de vue de l’œil pour déplacer l’image. Difficile, n’est-ce pas ? Cela décrit le double rôle de regard pour les entrées et les contrôles. 

- **Conserver avant de cliquer :** Pour les sélections de cibles rapides, la recherche a montré que le point de regard de l’utilisateur peut se déplacer avant de conclure un clic manuel (par exemple, un robinet air). Portez une attention particulière à la synchronisation du signal rapide oeil-point-Orient avec une entrée de contrôle plus lente (par exemple, voix, mains, contrôleur).

- **Petites cibles :** Savez-vous le sentiment quand vous essayez de lire du texte qui est un peu trop petit pour le lire confortablement ? Ce sentiment de distraction sur vos yeux peut vous amener à vous sentir fatigué et à être usé, car vous essayez de réajuster vos yeux pour mieux vous concentrer.
C’est un sentiment que vous pouvez appeler dans vos utilisateurs en les forçant à sélectionner des cibles qui sont trop petites dans votre application à l’aide d’un ciblage oculaire.
Durant la conception, si vous souhaitez créer une expérience utilisateur agréable et confortable, nous vous recommandons de privilégier des cibles ayant un angle de vue d’au moins 2°, sinon plus de préférence.

- **Mouvements de regard en œil irrégulier** Nos yeux effectuent des mouvements rapides de la fixation à la fixation. Si vous examinez un enregistrement des mouvements oculaires, vous pouvez voir qu’ils sont irréguliers. Vos yeux se déplacent rapidement et dans des passages spontanés par rapport aux mouvements du point de vue de la *main* ou du *regard* .  

- **Suivi de la fiabilité :** La précision du suivi des yeux peut être légèrement dégradée lorsque vos yeux évoluent en fonction des nouvelles conditions.
Même si cela ne doit pas nécessairement affecter la conception de votre application, car la précision doit être comprise dans la limite de 2 °, il peut être nécessaire que l’utilisateur l’étalonne à nouveau. 


## <a name="design-recommendations"></a>Recommandations de conception
La liste suivante répertorie les recommandations de conception spécifiques en fonction des avantages et des défis décrits pour les entrées de regard :

1. **L’œil-point de regard n’est pas le même que le regard de tête :**
    - **Déterminez si les mouvements oculaires rapides mais irréguliers s’adaptent à votre tâche d’entrée :** Si nos mouvements oculaires rapides et irréguliers sont très utiles pour sélectionner rapidement des cibles dans notre champ de vue, il est moins applicable aux tâches qui nécessitent des trajectoires d’entrée lisses (par exemple, les annotations de dessin ou de cercle). Dans ce cas, le pointage à la main ou avec la tête est préférable.
  
    - **Évitez de joindre un texte directement à l’oeil de l’utilisateur (par exemple, un curseur ou un curseur).**
Avec les curseurs, cela peut entraîner un effet « curseur Fleeing » en raison de légères décalages dans le signal de point de regard projeté. Avec un curseur, il peut entrer en conflit avec le double rôle de contrôle du curseur avec vos yeux, tout en souhaitant vérifier si l’objet se trouve à l’emplacement approprié. Pour l’exemple du curseur, il est plus judicieux d’utiliser une combinaison œil-regard avec les gestes manuels. Cela signifie que l’utilisateur peut basculer rapidement et facilement entre de nombreux curseurs, en augmentant leur main et en pinceant leur curseur et leur doigt pour les saisir et les déplacer. Quand le pincement est relâché, le curseur cesse de se déplacer. Les utilisateurs peuvent devenir submergés et perturbés, en particulier si le signal n’est pas précis pour cet utilisateur. 
  
2. **Combinez les yeux avec d’autres entrées :** L’intégration du suivi oculaire avec d’autres entrées, telles que les gestes à main, les commandes vocales ou les enfoncements de bouton, offre plusieurs avantages :
    - **Autoriser l’observation gratuite :** Étant donné que le rôle principal de nos yeux est d’observer notre environnement, il est important que les utilisateurs soient autorisés à regarder sans déclencher les commentaires ou les actions (visuel, audit, etc.). 
    La combinaison du suivi oculaire et d’un autre contrôle d’entrée permet une transition sans heurts entre l’observation du suivi oculaire et les modes de contrôle d’entrée.
  
    - **Fournisseur de contexte puissant :** À l’aide d’informations sur l’emplacement et le rôle de l’utilisateur, tout en disant une commande vocale ou en utilisant un mouvement manuel, vous permet de canaliser en toute transparence l’entrée dans le champ de la vue. Par exemple : _« Placez_ -le » pour sélectionner et positionner rapidement et de façon Fluent un hologramme sur la scène en regardant une cible et sa destination prévue. 

    - **Nécessité de synchroniser les entrées multimodales :** La combinaison rapide de mouvements oculaires avec des entrées plus complexes, telles que des commandes vocales longues ou des gestes de main, présente le risque que l’utilisateur continue à rechercher avant la fin et la reconnaissance de la commande d’entrée supplémentaire. Si vous créez vos propres contrôles d’entrée (par exemple, des mouvements de main personnalisés), veillez à consigner le début de cette entrée ou la durée approximative pour la corréler avec ce qu’un utilisateur a regardé dans le passé.
    
3. **Commentaires subtils pour l’entrée de suivi oculaire :** Il est utile de fournir des commentaires lorsqu’une cible est examinée pour indiquer que le système fonctionne comme prévu, mais qu’il doit rester discret. Cela peut inclure une fusion lente, des surbrillances visuelles ou des comportements de cible subtils, tels que des mouvements lents, tels que l’amélioration de la taille cible. Cela indique que le système a détecté correctement que l’utilisateur examine une cible sans inutilement interrompre le flux de travail actuel de l’utilisateur. 

4. **Évitez d’appliquer des mouvements oculaires innaturels comme entrée :** Ne forcez pas les utilisateurs à utiliser des mouvements oculaires spécifiques (mouvements de regard) pour déclencher des actions dans votre application.

5. **Compte pour les imprécisions :** Nous distingueons deux types d’imprécisions, qui sont perceptibles pour les utilisateurs : décalage et instabilité. Le moyen le plus simple de traiter un décalage consiste à fournir des cibles suffisamment volumineuses pour interagir avec. Il est recommandé d’utiliser un angle visuel supérieur à 2 ° comme référence. Par exemple, votre miniature est d’environ 2 ° dans l’angle visuel lorsque vous étirez votre bras. Il en résulte les conseils d’aide suivants :
    - Ne forcez pas les utilisateurs à sélectionner des cibles minuscules. La recherche a montré que si les cibles sont suffisamment volumineuses et que le système est bien conçu, les utilisateurs décrivent leurs interactions sans effort et magiques. Si les cibles deviennent trop petites, les utilisateurs décrivent l’expérience comme étant fatigante et frustrante.
  
<br>

Cette page vous a fourni une bonne présentation pour vous aider à comprendre les regards oculaires en tant qu’entrée dans la réalité mixte. Pour commencer à développer, consultez les informations sur les [yeux](https://aka.ms/mrtk-eyes) et les [yeux dans DirectX](../develop/native/gaze-in-directx.md).


## <a name="see-also"></a>Voir aussi
* [Confort](comfort.md)
* [Œil-point de regard sur DirectX](../develop/native/gaze-in-directx.md)
* [Œil-point d’interfaut](https://aka.ms/mrtk-eyes)
* [Suivi oculaire sur HoloLens 2](eye-tracking.md)
* [Pointer et valider](gaze-and-commit.md)
* [Pointer du regard et fixer](gaze-and-dwell.md)
* [Entrée vocale](../out-of-scope/voice-design.md)
