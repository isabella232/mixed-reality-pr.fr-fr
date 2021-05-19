---
title: Image holographique
description: Découvrez comment les utilisateurs voient le monde de la réalité mixte via le cadre holographique et comment mieux concevoir l’expérience.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, cadre holographique, champ de vision, angle de la réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de réalité mixte, interactions, navigation, menu
ms.openlocfilehash: fee6af6370f9f3d166768144e689e09fd3fda2db
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143251"
---
# <a name="holographic-frame"></a>Image holographique

Les utilisateurs voient le monde de la réalité mixte par le biais d’une fenêtre d’affichage rectangulaire alimentée par leur casque. Sur l’appareil HoloLens, cette zone rectangulaire est appelée « image holographique » et permet aux utilisateurs de voir le contenu numérique superposé au monde réel qui les entoure. La conception d’expériences optimisées pour le frame holographique crée des opportunités, atténue les défis et améliore l’expérience utilisateur des applications de réalité mixte.

## <a name="designing-for-content"></a>Conception pour le contenu

Souvent, les concepteurs estiment que la nécessité de limiter l’étendue de leur expérience à ce que l’utilisateur peut voir immédiatement, en sacrifiant l’échelle du monde réel, pour s’assurer que l’utilisateur voit un objet dans son intégralité. De même, les concepteurs avec des applications complexes surchargent souvent le frame holographique avec du contenu, insurmontent les utilisateurs avec des interactions difficiles et des interfaces encombrées. Les concepteurs créant du contenu de réalité mixte n’ont pas besoin de limiter l’expérience de l’utilisateur directement devant l’utilisateur et dans leur vue immédiate. Si le monde physique autour de l’utilisateur est mappé, toutes ces surfaces doivent être considérées comme un canevas potentiel pour le contenu numérique et les interactions. La conception correcte des interactions et du contenu au sein d’une expérience devrait inciter l’utilisateur à se déplacer dans son espace, à orienter son attention sur le contenu de la clé et à mieux voir le potentiel de la réalité mixte.

La technique la plus importante pour encourager le déplacement et l’exploration au sein d’une application est peut-être de **permettre aux utilisateurs de s’adapter à l’expérience**. Donnez aux utilisateurs une période de temps « sans tâche » avec l’appareil. Cela peut être aussi simple que de placer un objet dans l’espace et de permettre aux utilisateurs de le déplacer ou de présenter une présentation de l’expérience. Cette fois-ci, il ne doit pas y avoir de tâches critiques ou de mouvements spécifiques tels que l’air. L’objectif est de permettre aux utilisateurs d’afficher le contenu via l’appareil avant d’exiger l’interactivité ou la progression de l’application. Ceci est particulièrement important pour les utilisateurs de première heure, car ils se sentent à l’aise pour voir le contenu via le cadre holographique et la nature des hologrammes.

### <a name="large-objects"></a>Objets volumineux

Souvent, le contenu qu’une expérience appelle, en particulier le contenu réel, est plus grand que le cadre holographique. Les objets qui ne peuvent pas s’ajuster dans le cadre holographique doivent être réduits pour s’ajuster à leur première introduction (à une échelle inférieure ou à distance). La clé est de **permettre aux utilisateurs de voir la taille complète de l’objet** avant que l’échelle ne submerge le cadre. Par exemple, un éléphant holographique doit s’afficher entièrement dans le cadre. Cela permet aux utilisateurs de former une compréhension spatiale de la forme globale de l’animal, avant de le dimensionner à la mise à l' [échelle du monde réel](scale.md) près de l’utilisateur.

Avec la taille totale de l’objet à l’esprit, les utilisateurs ont l’attente de l’emplacement et de la recherche de parties spécifiques de cet objet. Dans le cas d’une expérience avec du contenu immersif, il est utile de pouvoir faire référence à la taille complète de ce contenu. Par exemple, si l’expérience implique de se déplacer autour d’un modèle d’une maison virtuelle, il est utile de disposer d’une version de l’expérience de la maison de poupée plus petite pour identifier l’endroit où elles se trouvent à l’intérieur de la maison.

Pour obtenir un exemple de conception d’objets volumineux, consultez [Volvo Cars](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Nombreux objets

Les expériences de nombreux objets ou composants doivent envisager l’utilisation de l’espace complet autour de l’utilisateur pour éviter d’encombrer le cadre holographique directement devant l’utilisateur. Nous vous recommandons de ralentir l’introduction du contenu dans une expérience, en particulier avec les expériences qui envisagent de servir de nombreux objets à l’utilisateur. La clé est de **permettre aux utilisateurs de comprendre la disposition du contenu** dans l’expérience, ce qui leur permet d’obtenir une compréhension spatiale de ce qui les entoure en tant que mises à jour du contenu.

Une technique pour y parvenir consiste à fournir des points persistants (également appelés « points de repère ») dans l’expérience qui ancre le contenu au monde réel. Par exemple, un repère peut être un objet physique dans le monde réel, tel qu’un tableau où du contenu numérique apparaît ou un objet numérique, tel qu’un ensemble d’écrans numériques où le contenu apparaît fréquemment. Les objets peuvent également être placés à la périphérie du cadre holographique pour inciter l’utilisateur à accéder au contenu de la clé. La découverte de contenu au-delà de la périphérie peut être facilitée par les [directeurs d’attention](holographic-frame.md#attention-directors).

Placer des objets dans la périphérie peut inciter les utilisateurs à se pencher sur le côté et cela peut être aidé par les directeurs d’attention, comme décrit ci-dessous. Pour plus d’informations sur les considérations relatives aux cadres holographiques, consultez la documentation [Comfort](comfort.md#holographic-frame-considerations) .

<br>

---

## <a name="interaction-considerations"></a>Considérations relatives aux interactions

Comme pour le contenu, les interactions dans une expérience de réalité mixte n’ont pas besoin d’être limitées à ce que l’utilisateur peut voir immédiatement. Les interactions peuvent être effectuées n’importe où dans l’espace réel autour de l’utilisateur. Ces interactions peuvent aider les utilisateurs à se déplacer et à explorer les expériences.

### <a name="attention-directors"></a>Directeurs d’attention

L’indication des points d’intérêt ou des interactions clés peut être cruciale pour la progression des utilisateurs via une expérience. L’attention de l’utilisateur et le déplacement du cadre holographique peuvent être orientés de manière subtile ou lourde. N’oubliez pas d’équilibrer les directeurs d’attention avec des périodes d’exploration gratuite en réalité mixte (en particulier au début d’une expérience) afin d’éviter d’allonger l’utilisateur. En général, il existe deux types de directeurs d’attention :
* **Directeurs visuels :** Le moyen le plus simple d’informer l’utilisateur qu’il doit se déplacer dans une direction spécifique est de fournir une indication visuelle. Cela peut être effectué à l’aide d’un effet visuel (par exemple, un chemin d’accès que l’utilisateur peut suivre dans la partie suivante de l’expérience) ou même en tant que flèches directionnelles simples. Tout indicateur visuel doit être mis à la terre au sein de l’environnement de l’utilisateur, et non « attaché » au frame holographique ou au curseur.
* **Directeurs audio :** le [son spatial](spatial-sound-design.md) peut fournir un moyen puissant pour établir des objets dans une scène. Vous pouvez avertir les utilisateurs des objets qui entrent dans une expérience ou attirer l’attention sur un point spécifique dans l’espace en déplaçant la vue de l’utilisateur vers des objets clés. L’utilisation de directeurs audio pour guider l’attention de l’utilisateur peut être plus subtile et moins intrusive que les directeurs visuels. Dans certains cas, il peut être préférable de commencer par un directeur audio, puis de passer à un directeur visuel si l’utilisateur ne reconnaît pas la pile. Les directeurs audio peuvent également être associés à des directeurs visuels pour une plus grande importance.

### <a name="commanding-navigation-and-menus"></a>Commandes, navigation et menus

Dans l’idéal, les interfaces dans la réalité mixte sont couplées étroitement avec le contenu numérique qu’elles contrôlent. En tant que tels, les menus 2D flottants ne sont souvent pas idéaux pour l’interaction et peuvent être difficiles à utiliser dans le cadre holographique. Pour les expériences qui requièrent des éléments d’interface tels que des menus ou des champs de texte, envisagez d’utiliser une [méthode de balisage](billboarding-and-tag-along.md) pour suivre le frame holographique après un bref délai. Évitez de verrouiller du contenu dans le cadre comme un affichage de tête, car il peut être démonté pour l’utilisateur et briser le sens de l’immersion pour d’autres objets numériques de la scène.

Vous pouvez également placer des éléments d’interface directement sur le contenu spécifique qu’ils contrôlent, ce qui permet aux interactions de se produire naturellement autour de l’espace physique de l’utilisateur. Par exemple, divisez un menu complexe en plusieurs parties distinctes, chaque bouton ou groupe de contrôles étant attaché à l’objet spécifique affecté par l’interaction. Pour aller plus loin dans ce concept, envisagez d’utiliser des [objets](interactable-object.md)interactifs.

### <a name="gaze-and-gaze-targeting"></a>Cible du regard et du regard

Le cadre holographique présente un outil permettant au développeur de déclencher des interactions et de déterminer où se trouve l’attention d’un utilisateur. Le point de [regard](gaze-and-commit.md) est l’une des [interactions clés sur HoloLens](interaction-fundamentals.md), où le point de regard peut être couplé à des [gestes](gaze-and-commit.md#composite-gestures) (par exemple, une pression aérienne) ou une [voix](voice-input.md) (permettant des interactions plus courtes et plus naturelles). Ainsi, le frame holographique fait à la fois un espace pour observer le contenu numérique et interagir avec lui. Si l’expérience nécessite l’interaction avec plusieurs objets autour de l’espace de l’utilisateur (par exemple, la sélection de plusieurs objets autour de l’espace de l’utilisateur avec le point de vue + geste), envisagez de placer ces objets dans l’affichage de l’utilisateur ou de limiter le nombre de mouvements de tête nécessaires pour promouvoir le confort de l' [utilisateur](comfort.md).

Vous pouvez également utiliser le point de regard pour suivre l’attention des utilisateurs via une expérience et voir quels objets ou parties de la scène l’utilisateur a payé le plus d’attention. Cela peut être particulièrement utile pour déboguer une expérience, permettant à des outils analytiques comme cartes thermiques de voir où les utilisateurs passent le plus de temps ou qui manquent certains objets ou interactions. Le suivi du regard peut également fournir un outil puissant pour les animateurs dans les expériences (Voir l’exemple [de cuisine de Lowe](holographic-frame.md#lowes-kitchen) ).

Si vous souhaitez voir les concepts de conception des suivis des yeux et des yeux en action, consultez notre démonstration [conception d’hologrammes-TETE Tracking and Eye Tracking (]() en anglais) ci-dessous :

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<br>

---

## <a name="performance"></a>Performances

L’utilisation correcte du cadre holographique est fondamentale pour les expériences de [qualité des performances](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) . L’un des défis techniques (et pratiques) courants consiste à surcharger le frame de l’utilisateur avec du contenu numérique, ce qui entraîne une dégradation des performances de rendu. Envisagez plutôt d’utiliser l’espace complet de l’utilisateur pour organiser le contenu numérique, à l’aide des techniques décrites ci-dessus, afin de réduire la charge de rendu et de garantir une qualité d’affichage optimale.

Le contenu numérique dans le cadre holographique du HoloLens peut également être associé au plan de [stabilisation](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) pour optimiser les performances et la stabilité de l' [hologramme](../develop/platform-capabilities-and-apis/hologram-stability.md).

<br>

---

## <a name="examples"></a>Exemples

### <a name="volvo-cars"></a>Volvo Cars

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Dans l’expérience de salle de présentation de Volvo Cars, les clients sont invités à se familiariser avec les nouvelles fonctionnalités d’une voiture dans une expérience HoloLens guidée par Volvo Associate. Volvo a fait face à un défi avec le cadre holographique : une voiture pleine taille est trop grande pour être placée juste à côté d’un utilisateur. La solution consistait à commencer l’expérience avec un repère physique, une table centrale dans la salle de exposition, avec un modèle numérique plus petit de la voiture placé en haut de la table. Cela permet de s’assurer que l’utilisateur voit la totalité de la voiture lorsqu’elle est introduite, ce qui permet d’obtenir une compréhension spatiale une fois que la voiture atteint sa mise à l’échelle réelle plus tard dans l’expérience.

L’expérience de Volvo utilise également des directeurs visuels, créant ainsi un effet visuel long du modèle de voiture à petite échelle sur la table à un mur dans la salle de salon. Cela donne un effet « fenêtre magique », montrant la vue complète de la voiture à distance, illustrant des fonctionnalités supplémentaires de la voiture à l’échelle du monde réel. Le mouvement de la tête est horizontal, sans interaction directe de l’utilisateur (en recueillant les signaux visuellement et à partir de la narration de l’expérience de Volvo Associate).

<br>

---

### <a name="lowes-kitchen"></a>Cuisine de Lowe

Une expérience de magasin de Lowe invite les clients à effectuer une maquette à l’échelle complète d’une cuisine pour présenter diverses opportunités de remodelage comme indiqué par le HoloLens. La cuisine dans le magasin fournit un fond physique pour les objets numériques, un canevas vide d’appliances, des plans de travail et des armoires pour l’expérience de réalité mixte à dérouler.

Les surfaces physiques jouent le rôle d’éléments de repère statiques pour que l’utilisateur soit à l’origine de l’expérience, car l’Association d’un Lowe guide l’utilisateur à travers différentes options de produit et se termine. De cette façon, l’Association peut diriger oralement l’attention de l’utilisateur vers le « réfrigérateur » ou le centre de la cuisine pour présenter le contenu numérique.

![L’Association d’un Lowe utilise une tablette pour guider les clients dans le processus HoloLens.](images/loweskitchen-750px.jpg)<br>
*L’Association d’un Lowe utilise une tablette pour guider les clients dans le processus HoloLens.*

L’expérience de l’utilisateur est gérée, en partie, par une expérience de tablette contrôlée par l’Association de Lowe. Dans ce cas, une partie du rôle de l’Association serait également de limiter les déplacements excessifs, en dirigeant leur attention en douceur sur les points d’intérêt de la cuisine. L’expérience de tablette fournit également l’Association de Lowe à des données en regard sous la forme d’une vue carte thermique de la cuisine, en aidant à comprendre où l’utilisateur s’occupait (par exemple, dans une zone spécifique de cabinet) pour lui fournir plus précisément des instructions de remodelage.

Pour un examen approfondi de l’expérience de cuisine de Lowe, consultez le [discours de Microsoft à l’allumage de l’allumage 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragments

Dans les fragments de jeu HoloLens, vous vivez de l’espace est transformé en scène de criminalité virtuelle montrant des indices et des preuves, ainsi qu’une salle de réunion virtuelle, où vous communiquez avec des caractères qui se trouvent sur vos chaises et qui se penchent sur vos murs.

![Les fragments ont été conçus pour s’exécuter dans le Bureau d’un utilisateur, avec des caractères qui interagissent avec des objets et des surfaces réels.](images/fragments-750px.jpg)<br>
*Les fragments ont été conçus pour être ajoutés au bureau d’un utilisateur, avec des caractères qui interagissent avec des objets et des surfaces réels.*

Lorsque les utilisateurs commencent à démarrer l’expérience, ils reçoivent une courte période d’ajustement avec peu ou pas d’interaction. Au lieu de cela, ils sont encouragés à se pencher et à s’orienter et à s’assurer que la salle est correctement mappée pour le contenu interactif du jeu.

Tout au long de l’expérience, les caractères deviennent des points de référence et jouent le rôle de directeurs visuels (mouvements d’en-tête entre les caractères, pour l’apparence ou le mouvement vers des zones d’intérêt). Le jeu s’appuie également sur des signaux visuels plus importants lorsqu’un utilisateur met trop de temps à trouver un objet ou un événement et utilise une utilisation intensive du son spatial (surtout avec des voix de caractères lors de la saisie d’une scène).

<br>

---

### <a name="destination-mars"></a>Destination : mars

Dans la destination : l’expérience mars dans le [Centre d’espace Kennedy de NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), les visiteurs ont été invités dans un voyage immersif à la surface de mars, guidé par la représentation virtuelle de légendaires. astronautes.

![Un bourdonnement d’une vague virtuelle devient le point focal pour les utilisateurs dans la destination : mars.](images/destinationmars-750px.png)<br>
*Un bourdonnement d’une vague virtuelle devient le point focal pour les utilisateurs dans la destination : mars.*

Comme une expérience immersive, ces utilisateurs ont été encouragés à se pencher, en déplaçant leur tête dans toutes les directions pour voir le paysage Martian virtuel. Bien que pour garantir le confort des utilisateurs, le discours d’Aldrin et la présence virtuelle ont fourni un point focal tout au long de l’expérience. Cet enregistrement virtuel de l’oreille (créé par les [Studios de capture de réalité mixte de Microsoft](https://www.microsoft.com/mixed-reality/capture-studios)) s’approche de la taille réelle, dans le coin de la salle, permettant aux utilisateurs de le voir dans une vue presque complète. La narration de l’oreille a dirigé les utilisateurs à se concentrer sur les différents points de l’environnement (par exemple, un ensemble de roches Martians sur le plancher ou une montagne à distance) avec des changements de scènes spécifiques ou des objets qu’il introduit.

![Les narrateurs virtuels s’allumeront pour suivre le déplacement d’un utilisateur, créant ainsi un point focal puissant tout au long de l’expérience.](images/gazereset-750px.png)<br>
*Les narrateurs virtuels s’allumeront pour suivre le déplacement d’un utilisateur, créant ainsi un point focal puissant tout au long de l’expérience.*

La représentation réaliste de l’oreille a fourni un point focal puissant, complet avec des techniques subtiles pour que l’utilisateur ait l’impression de s’y faire, en parlant. Quand l’utilisateur se déplace sur l’expérience, il passe à votre seuil avant de revenir à un État neutre si l’utilisateur se déplace trop loin au-delà de sa périphérie. Si l’utilisateur regarde complètement l’oreille (par exemple, pour regarder quelque part dans la scène), puis revenir à l’oreille, la position directionnelle du narrateur sera de nouveau axée sur l’utilisateur. Les techniques telles que celle-ci fournissent un bon sens d’immersion et créent un point focal dans le cadre holographique, réduisant ainsi le déplacement excessif et promouvant le confort de l' [utilisateur](comfort.md).

## <a name="see-also"></a>Voir aussi
* [Interactions instinctuelles](interaction-fundamentals.md)
* [Confort](comfort.md)
* [Mise à l’échelle](scale.md)
* [Suivre de la tête et stabiliser](gaze-and-dwell.md)
* [Stabilité des hologrammes](../develop/platform-capabilities-and-apis/hologram-stability.md)
