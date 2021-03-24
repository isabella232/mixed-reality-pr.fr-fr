---
title: Expérience GT40 Ford
description: Suivez la procédure d’exploration de la création de l’application de réalité mixte Ford GT40 avec MRTK pour HoloLens 2 en tout temps.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, réalité mixte, déployer sur un appareil, PC, documentation, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
appliesto:
- HoloLens 2
ms.openlocfilehash: ca577bdc5bc30aebf80c9888345eb0e2d5c3ce6d
ms.sourcegitcommit: cc9d90b046a9fce792058fea25ae13a9186e43e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "105008924"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>La création de l’expérience GT40 Ford

*«Pre-MRTK, développement pour HoloLens 2 à l’aide d’inréel était un peu fastidieux, car toutes les interactions spatiales devaient être codées manuellement, en C++. Le MRTK pour le non-réalisation d’un grand nombre de ces mêmes tâches est trivial. Je dirais que le temps nécessaire pour le prototype initial est réduit de moitié.»* -José Rodriguez, développeur de logiciels

*« L’expérience GT40 de Ford est la preuve qu’une application de haute fidélité HoloLens 2 peut être exécutée en quelques mois seulement, avec un budget modeste, tout en continuant à fournir des résultats extrêmement percutants ».*  -Daniel Cheetham, responsable de l’innovation, bonne fin

À l’aide de la boîte à outils de la réalité mixte (MRTK) pour les environnements de production créatifs inhabituels, la bonne fin a fourni une expérience HoloLens 2 qui offre un nouveau point de vue sur la GT40 Ford, la voiture légendaires. course qui Ferrari aux 24 heures du Mans.

À l’aide d’une gamme d’interactions spatiales naturelles et intuitives, les utilisateurs peuvent explorer la beauté, les performances et l’ingénierie de GT40's, tout cela qui tire parti de la fidélité visuelle élevée fournie par le moteur inréel. Le développement de logiciels pour l’ensemble du projet a été effectué par un développeur unique en moins de trois mois, rendu possible par MRTK pour l’environnement de conception et de script visuel.

> [!div class="nextstepaction"]
> [Télécharger l’application GT40 Ford](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

![Image du héros GT40 Ford](images/ford-gt40-hero.jpg)

## <a name="the-ask"></a>La demande

Bonne fin est l’une des principales sociétés de production créatives au monde, avec une base de clients qui comprend, Ford, Microsoft, Nike, Netflix, Vodafone et d’autres noms de ménage. L’entreprise s’est lancée comme une Agence haute qualité photo-Touch, qui a été débranchée dans un film et un CGI avant d’étendre son dévouement à l’excellence dans le cadre immersif de la conception et de l’interaction spatiales 3D.

Dans la mi-2020, Microsoft se approchait de la fin de la création d’une application de démonstration qui pourrait vous aider à présenter les possibilités offertes par le nouveau kit d’outils de réalité mixte (MRTK) pour Unreal, qui s’appuie sur la prise en charge de HoloLens 2 dans le moteur inréaliste. À ce stade, l’entreprise avait déjà deux projets inexistants de la fonction HoloLens 2 sous sa ceinture. Ils étaient tous les deux destinés à une société de vente mondialement reconnue, qui choisissait de la réalité sur HoloLens 2 pour un outil de vente R&D/B2B interne pour sa fidélité visuelle élevée, en fonction des besoins afin de mieux illustrer les produits haut de gamme de ce client.

Bien que la solution elle-même soit laissée à la bonne fin, elle devait répondre à quelques recommandations clés. Tout d’abord, il devait se concentrer sur un scénario d’entreprise pour illustrer l’utilité de l’environnement de la norme HoloLens 2 en dehors du secteur du jeu. Deuxièmement, il devait être uniquement destiné aux appareils, ce qui signifie qu’il pourrait servir de démonstration autonome, sans avoir besoin d’une connexion réseau et d’une puissance de traitement externe pour obtenir les fréquences d’images cibles et la qualité visuelle. Troisièmement, il doit mélanger la plage d’interactions intuitives prises en charge par le MRTK dans une expérience transparente et naturelle. Enfin, la solution proposée doit présenter la fidélité visuelle inhérente et d’autres avantages du moteur inréel, tels que l’efficacité des nuanceurs. 

Compte tenu de ces instructions, nous sommes ravis de vous faire découvrir les possibilités, avec l’idée d’une expérience de réalité mixte qui utilisait l’interaction spatiale pour communiquer la valeur d’un produit de qualité et de qualité. Après avoir pris en compte une gamme d’objets qui comprenait des montres, des appareils photo, des voitures et des jets privés, heureux Finish a finalement décidé sur le GT40 Ford, une légende d’automobile qui a atteint notoriety dans 1966 quand Ford a Ferrari les 24 heures du Mans, comme le montre le 2019 exceptionnelles film Ford et Ferrari. 

Lors de l’acquisition de Ford, un client de bonne finition existant, la société a décidé de fournir un nouveau point de vue sur l’icône d’automobile classique.

## <a name="the-solution"></a>La solution

Le travail a commencé le 7 mai 2020. Après avoir obtenu les fichiers de modèle GT40, un artiste 3D a passé trois semaines d’optimisation des modèles de polygones, le mappage UV, le redessin des cartes de texture et le condensation de ces cartes en autant de textures que possible. Un artiste technique A travaillé en parallèle pour évaluer la sortie de l’artiste 3D, déterminer les tailles de texture optimales en fonction de la fréquence d’images cible, et déterminer la meilleure façon d’appliquer des nuanceurs personnalisés dans des conditions exceptionnelles. Tout ce travail de préproduction a été effectué pour optimiser l’expérience sur l’appareil.

Le directeur créatif Alex Lambert a entré l’image après la fin du travail de préproduction. Il a commencé par regarder Ford et Ferrari, en pensant à la manière d’assembler une narration autour des scénarios et des interactions. Il a également collecté des références visuelles pour l’artiste de l’interface utilisateur, telles que des images du tableau de bord GT40 et des visuels du Mans Racetrack, et des enregistrements audio collectés du GT40 en action pour le concepteur de sons.

Avec les ressources de pré-production définies et optimisées en main, freelance Software Developer José Rodriguez a été inscrit pour les réunir. Rodriguez avait été le développeur sur les deux précédents projets de HoloLens 2, qui étaient heureux, avant la sortie du MRTK pour le non réel.

La valeur fournie par le MRTK pour les inréels est devenue évidente, ce qui aide Rodriguez à remettre un prototype initial en une semaine. Il a implémenté trois scénarios uniques, un pour chacun des aspects clés du GT40 que Lambert avait identifié : sa beauté, ses performances et son ingénierie. Pour chaque scénario, Rodriguez a utilisé le MRTK pour intégrer les ressources 3D optimisées de la phase de préproduction dans une plage d’interactions spatiales. 

Avec le MRTK pour Unreal, Rodriguez a créé chaque scénario à l’aide du concepteur d’interface utilisateur de Visual Unreal Motion Graphics (UMG) au lieu d’avoir à implémenter tout en C++. [Outils d’expérience utilisateur pour](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)le non réel, le plug-in qui contient des blocs de construction d’expérience utilisateur et des composants au sein du MRTK, lui a donné des [plans inréelss](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) pour la simulation d’entrée, les interactions visuelles des scripts, les boutons de presse, la manipulation d’images en 3D, le magnétisme de surface, etc.

« Pre-MRTK, développement pour HoloLens 2 à l’aide d’inréel était un peu fastidieux, car toutes les interactions spatiales devaient être codées à la main, en C++ », déclare Rodriguez. «Le MRTK pour inréel fait beaucoup de ces mêmes tâches de façon triviale. Je dirais que le temps nécessaire pour le prototype initial est réduit de moitié.»

Avec un prototype en main, l’équipe a commencé des itérations hebdomadaires pour affiner l’expérience. « C’est quand la fonctionnalité de capture de la réalité mixte et le portail de l’appareil Windows sont devenus très utiles » rappelle Lambert. «J’ai utilisé ceux-ci pour capturer mes évaluations de conception, diffuser mes commentaires à d’autres utilisateurs et collaborer sur les modifications. L’isolation telle que celle-ci aurait été impossible sans ces outils.»

![Application GT40 Ford de l’éditeur incorrecte exécutée avec des composants de roue disposés en séquence](images/ford-gt40-img-04.JPG)

Comme Lambert a demandé des modifications, telles que le repositionnement des éléments de l’interface utilisateur ou la modification du comportement d’un bouton, Rodriguez les a implémentées. Alors que certaines modifications nécessitaient de petites modifications de code, la plupart étaient gérées dans le concepteur visuel inréel. « J’ai été surpris de la rapidité de l’itération », déclare Rodriguez. «Aucune heure n’a été perdue. Je fais une modification dans le concepteur, puis j’appuie sur lire pour l’afficher immédiatement sur l’appareil. Le MRTK a vraiment rationalisé mon travail.»

Rodriguez rappelle également que les outils de développement prêts pour la production étaient impressionnés. « Nous sommes parvenus progressivement à partir du prototype initial jusqu’à la production finale, sans avoir à revenir en arrière et à réimplémenter ou à optimiser les éléments du code », il dit.  

## <a name="the-final-build"></a>Build finale

Bonne fin production de l’expérience GT40 de Ford pour HoloLens 2 le 28 juillet 2020, ce qui a pour effet d’offrir un nouveau point de vue sur la voiture de course légendaires.. L’expérience démarre avec un écran d’accueil, puis guide l’utilisateur pour configurer un point d’ancrage en saisissant le logo Ford et en le plaçant sur une surface plate telle qu’une table ou un bureau. 

### <a name="beauty"></a>Soins

Le segment de **beauté** fait passer l’utilisateur à un configurateur GT40, qui affiche le GT40 sur un socle rotatif, de la même manière qu’une voiture physique peut être affichée dans un salon automobile. L’utilisateur peut appliquer différentes options de roulette, choisir parmi différents modèles de couleurs, ouvrir et fermer les portes et le Trunk (ou démarrer, lorsqu’ils l’appellent au Royaume-Uni). Tout au long de l’expérience de beauté, l’utilisateur peut sélectionner la voiture et la manipuler librement pour une présentation détaillée.

![GIF animé du configurateur GT40 exécuté sur un appareil](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Performances

Le segment de **performance** présente la vitesse et la durabilité GT40's. Le VoiceOver commence par décrire comment la voiture a été développée et placée dans son aspect au Kingman, à l’Arizona, à l’Arizona, avec des visuels 3D montrant le GT40 en mouvement sur la piste de test. Comme l’introduction au segment de performance conclut, le VoiceOver invite l’utilisateur à « appuyer sur le bouton le Mans pour atteindre le Racetrack ».

![GIF animé de l’application de vitesse et durabilité GT40 s’exécutant sur un appareil](images/ford-gt40-img-06.gif)

La deuxième partie du segment de performance présente les GT40 dans la plage des conditions que les pilotes peuvent rencontrer au cours des 24 heures du Mans, qui est conservé annuellement au circuit de la Sarthe près du Mans, France. Une vue 3D montre la voiture en mouvement sur la piste le Mans, avec des boutons permettant de rendre la voiture plus rapide ou plus lente. Images de l’indicateur de vitesse analogique GT40's et du tachymètre au-dessus de la vue Racetrack, avec davantage de données de télémétrie de course affichées en arrière-plan. L’utilisateur peut basculer entre les affichages jour et nuit et entre les conditions de conduite sèche et humide, ce qui fournit une perspective réaliste et réaliste de l’expérience de Ken miles et des autres pilotes GT40 dans la course réelle.

### <a name="engineering"></a>Ingénierie

Le segment d' **ingénierie** de l’expérience de Ford GT40 présente l’une des innovations d’ingénierie qui ont aidé Ford à remporter la course : la possibilité de changer les rotors de freins et les pad en moins d’une minute, par rapport aux 20-30 minutes nécessaires à toutes les autres équipes. À l’aide de mouvements intuitifs, l’utilisateur peut manipuler un modèle 3D détaillé de la roue GT40 et de l’ensemble de freins. Pour développer l’assembly, l’utilisateur choisit une clé Lug, l’aligne sur le verrou central sur la roue, la désactive dans le sens inverse, puis l’éloigne de la roue. D’autres mouvements sont utilisés pour supprimer les rotors et les patins de freins usés, les remplacer par de nouveaux, réduire l’assembly et sécuriser le verrou central. En arrière-plan, un minuteur affiche la durée écoulée, ce qui permet à l’utilisateur de voir s’il peut terminer le processus aussi rapidement que l’équipe pit du Mans.

![GIF animé de l’expérience d’ingénierie GT40 en cours d’exécution sur un appareil](images/ford-gt40-img-07.gif)

L’expérience GT40 de Ford peut être [téléchargée à partir du Microsoft Store](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab), ce qui permet à toute personne disposant d’un HoloLens 2 d’explorer la manière dont la fin de la procédure a été renouvelée pour légendaires. course car.

### <a name="getting-impressive-visual-fidelity"></a>Obtenir une fidélité visuelle impressionnante

Alors que la plage d’interactions spatiales prise en charge par l’expérience GT40 de Ford est impressionnante, la créativité et la fidélité visuelle que l’expérience offre est ce qui en fait la brillance. Grâce à son optimisation des modèles 3D et à l’utilisation de nuanceurs personnalisés inréels, nous avons atteint sa cible de 60 images par seconde, même si le segment de performance de l’application approche de 315 000 polygones. 

« Je suis vraiment heureux de savoir comment nous avons pu rassembler un ensemble d’interactions fluides et intuitives dans une narration cohérente et attrayante », déclare Lambert. «En clair, la puissance du moteur inréel sur HoloLens 2 ouvre un nouveau monde d’opportunités pour des expériences de réalité mixte étonnantes et étonnantes. La fidélité visuelle non compromise n’est pas toujours l’objectif final pour les applications d’entreprise sur HoloLens 2, mais quand c’est le cas, la prise en charge de non-réelle sur HoloLens 2 devient inestimable.»

### <a name="rapid-solution-delivery"></a>Livraison rapide des solutions

Aussi impressionnant que l’expérience de l’utilisateur final Ford GT40, c’est la rapidité avec laquelle il est possible de la livrer, avec la totalité du projet, de la préproduction à la livraison finale, en moins de 12 semaines. En résumé, le projet a consommé 1088 heures d’effort, décomposées comme suit : Creative Director (80 heures), UX Designer (56 heures), UI Designer (40 hours), Sound Designer (40 heures), 3D/Technical Artist (328 hours), Software Developer (408 hours), Technical Director (40 hours), Producer (56 hours) et Quality assurance (40 heures).

« Globalement, nous sommes parvenus à nos estimations de projet d’origine », déclare Daniel Cheetham, directeur de l’innovation à la bonne fin, qui dirige la Division interactive de l’entreprise. « L’expérience GT40 de Ford est la preuve qu’une application de haute fidélité HoloLens 2 peut être exécutée en quelques mois seulement, avec un budget modeste, tout en continuant à fournir des résultats extrêmement percutants ». 

Du point de vue du développement, en se basant sur son expérience précédente avec la version non réelle de HoloLens 2, Rodriguez estime que le MRTK pour les périodes inréelless a réduit la durée et l’effort total requis de la moitié de sa partie. Il note également comment le MRTK peut aider les développeurs qui n’ont jamais travaillé avec HoloLens 2 à commencer. «Lorsque d’autres développeurs disent qu’ils sont intéressés par la réalité mixte, je les encourage à simplement les entrer, à installer la pile de développement HoloLens 2 et à MRTK, et à y accéder. MRTK facilite la création d’une application, et l’éditeur visuel peu réel fonctionne si bien que vous n’avez même pas besoin d’un appareil HoloLens 2 pour commencer. Ce n’est pas tout à fait compliqué, tout fonctionne.

### <a name="potential-azure-service-enhancements"></a>Améliorations potentielles du service Azure

Lambert voit plusieurs façons d’utiliser les services de réalité mixte Azure pour améliorer l’expérience GT40 de Ford, par exemple en utilisant des ancres spatiales Azure pour fournir une expérience multi-utilisateur ancrée dans le monde réel. « Du point de vue créatif, les ancres spatiales Azure ouvrent une gamme de possibilités entièrement nouvelles grâce à la capacité qu’elles offrent pour mapper, conserver et restaurer le contenu 3D ou les centres d’intérêt dans notre monde physique », il dit.

Lambert explique également comment utiliser le rendu distant Azure ou la diffusion en continu de l’application à partir d’Azure pour atteindre les fréquences d’images souhaitées lors de l’utilisation de modèles 3D plus détaillés et complexes. « Nous avons dû implémenter certains nuanceurs personnalisés très optimisés dans le cadre de la cible de l’appareil, 60 images par seconde ». « Avec le rendu à distance Azure, nous pourrions faire beaucoup plus, et le faire beaucoup plus facilement, sans autant de travail requis pour optimiser les modèles de polygone, redessiner les cartes de texture, etc. ».

### <a name="endless-new-possibilities"></a>Nouvelles possibilités infinies

Alors, quelle est la prochaine étape pour la bonne fin ? Les commentaires de Ford sur l’expérience GT40 de Ford ont été très positifs, ce qui a conduit à des discussions plus poussées entre la satisfaction et la satisfaction sur les futurs projets HoloLens 2. En dehors de sa relation avec Ford, la bonne fin est le démarrage d’un nouveau projet sur HoloLens 2, où le MRTK pour le non réel est un bloc de construction fondamental pour la plupart de l’expérience utilisateur. 

« Nous avons toujours géré une approche indépendante de la technologie pour chaque nouveau projet, en proposant tout ensemble d’outils idéal pour aider le client à atteindre les résultats souhaités », déclare Cheetham. « Cela dit, HoloLens 2 est apparu comme la norme Gold de facto pour la réalité mixte, en particulier dans l’entreprise, les têtes et les épaules qui se trouvent au-dessus de toutes les autres options en termes de fonctionnalités d’appareil et de l’omniprésence de l’écosystème de prise en charge. »

Selon Cheetham, le pandémie global a été un nouvel intérêt énorme pour la réalité mixte, parmi les clients potentiels. « Nous sommes plus occupés que jamais, avec environ 50% des clients potentiels ouverts à discuter d’une option de réalité mixte », il dit. «La clé est d’aider les utilisateurs à essayer. Vous pouvez les informer de la réalité mixte tout le jour, mais lorsque vous les transmettez à un contrôleur HoloLens 2 pour vous familiariser avec eux-mêmes, ils ont immédiatement la même façon qu’il peut s’agir d’un changeur. La prise en charge d’un moteur inréel dans HoloLens 2 n’augmente que la valeur que nous pouvons offrir, ce qui nous permet de fournir des expériences visuellement étonnantes qui garantissent la satisfaction des clients les plus exigeants.

## <a name="try-it-out"></a>Essayez !

> [!div class="nextstepaction"]
> [Télécharger l’application GT40 Ford](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Consultez notre [Introduction au développement de la réalité mixte sur HoloLens 2](../development.md) ou [MRTK pour](https://github.com/microsoft/MixedRealityToolkit-Unreal) github.

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->