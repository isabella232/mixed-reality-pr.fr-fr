---
title: Eye-tracking
description: en savoir plus sur le suivi oculaire pour les HoloLens 2 et les nouveaux niveaux de compréhension humaine, s’ils vous permettent d’obtenir des expériences holographiques.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: suivi oculaire, réalité mixte, entrée, point de regard, étalonnage, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, Shared Computer Toolkit de réalité mixte, intention, actions
ms.openlocfilehash: ce8ffcb6b8b59b6b0484ba4b3db256a8df5810ea2719416bea9e3f4366ad6afe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214140"
---
# <a name="eye-tracking-on-hololens-2"></a>Eye-tracking sur HoloLens 2

![Démonstration du suivi oculaire dans MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 permet à un nouveau niveau de contexte et de compréhension humaine au sein de l’expérience holographique en offrant aux développeurs la possibilité d’utiliser des informations sur ce que l’utilisateur examine. Cette page explique comment les développeurs peuvent tirer parti du suivi oculaire pour divers cas d’usage, et ce qu’il faut rechercher lors de la conception d’interactions utilisateur en regard de regard. 

L’API de suivi oculaire a été conçue en tenant compte de la confidentialité d’un utilisateur, ce qui évite de transmettre des informations identifiables, en particulier toute biométrie. Pour les applications pouvant suivre le suivi oculaire, l’utilisateur doit accorder à l’application l’autorisation d’utiliser les informations de suivi oculaire.

### <a name="device-support"></a>Prise en charge des appareils

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Fonctionnalité</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></td>
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

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Démonstration des concepts d’élaboration du suivi de la tête et du suivi oculaire

Si vous souhaitez voir les concepts d’élaboration du suivi de la tête et du suivi oculaire en action, consultez notre démonstration vidéo **Conception d’hologrammes - Suivi de la tête et suivi oculaire** ci-dessous. Une fois que vous avez terminé, poursuivez pour obtenir une présentation plus détaillée relative à des rubriques spécifiques.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Cette vidéo a été extraite de l’application HoloLens 2 « Conception d’hologrammes ». Téléchargez-la et profitez de l’expérience complète [ici](https://aka.ms/dhapp).*

## <a name="calibration"></a>Étalonnage 

Pour que le suivi des yeux fonctionne correctement, chaque utilisateur doit passer par un [étalonnage d’utilisateur de suivi oculaire](/hololens/hololens-calibration) pour lequel l’utilisateur doit examiner un ensemble de cibles holographiques. Cela permet à l’appareil d’ajuster le système pour une expérience d’affichage plus confortable et de meilleure qualité pour l’utilisateur et pour garantir un suivi visuel précis en même temps. 

Le suivi oculaire doit fonctionner pour la plupart des utilisateurs, mais il existe de rares cas où un utilisateur ne peut pas l’étalonner correctement. L’étalonnage peut échouer pour diverses raisons, y compris mais sans s’y limiter : 
* L'utilisateur a précédemment refusé le processus d'étalonnage.
* L’utilisateur a été distrait et n’a pas suivi les objectifs d’étalonnage
* L’utilisateur dispose de certains types de lentilles et de lunettes de contact que le système ne prend pas encore en charge. 
* L’utilisateur a une certaine physiologie oculaire, des conditions oculaires ou avait une chirurgie oculaire, que le système ne prend pas encore en charge  
* facteurs externes inhibant le suivi des yeux fiables, tels que les taches sur le visière de HoloLens ou les lunettes, le soleil direct et les occlusions dus aux cheveux en face des yeux

Les développeurs doivent veiller à fournir une prise en charge adéquate pour les utilisateurs pour lesquels les données de suivi oculaire peuvent ne pas être disponibles (qui ne peuvent pas être correctement étalonnes). Nous avons fourni des recommandations pour les solutions de secours dans la section en bas de cette page. 

Pour en savoir plus sur l’étalonnage et sur la façon de garantir une expérience sans heurts, consultez notre page d’étalonnage de l' [utilisateur de suivi oculaire](/hololens/hololens-calibration) .

<br>

## <a name="available-eye-tracking-data"></a>Données de suivi oculaire disponibles

avant de passer en revue les cas d’utilisation spécifiques pour les entrées de regard oculaire, nous souhaitons rapidement souligner les fonctionnalités fournies par l' [API de suivi des HoloLens 2 oculaire](/uwp/api/windows.perception.people.eyespose) . Les développeurs accèdent à un seul point d’accès en regard (origine du regard et direction) à environ _30 i/s (30 Hz)_.
Pour plus d’informations sur la façon d’accéder aux données de suivi oculaire, reportez-vous à nos guides pour les développeurs sur l’utilisation des [yeux dans DirectX](../develop/native/gaze-in-directx.md) et [Eye-pointer sur Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main).

Le point de regard prédit est approximativement de 1,5 degrés d’angle visuel autour de la cible réelle (Voir l’illustration ci-dessous). Les développeurs doivent prévoir une marge autour de cette valeur de limite inférieure (par exemple, 2.0-3 degrés peut se traduire par une expérience bien plus confortable). Nous verrons comment aborder la sélection de petites cibles plus en détail ci-dessous. Pour que l’eye-tracking fonctionne avec précision, chaque utilisateur doit effectuer un étalonnage. 

![Taille optimale de la cible à une distance de 2 mètres](images/gazetargeting-size-1000px.jpg)<br>
*Taille de cible optimale à une distance de 2 mètres*

<br>

## <a name="use-cases"></a>Cas d'utilisation

L’eye-tracking permet aux applications de savoir où l’utilisateur regarde en temps réel. les cas d’usage suivants décrivent certaines interactions possibles avec le suivi oculaire sur HoloLens 2 dans la réalité mixte.
Ces cas d’usage ne font pas encore partie de l’expérience d’interpréteur de commandes holographique (c’est-à-dire, l’interface que vous voyez quand vous démarrez votre HoloLens 2).
vous pouvez essayer certaines d’entre elles dans le Shared Computer Toolkit de la [réalité mixte](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main), qui fournit plusieurs exemples intéressants et puissants pour l’utilisation du suivi oculaire, tels que les sélections de cibles rapides et faciles à utiliser par l’œil, et le défilement automatique du texte en fonction de ce que l’utilisateur examine. 

### <a name="user-intent"></a>Intention de l'utilisateur

Des informations sur l’emplacement et le rôle d’un utilisateur fournissent un **contexte puissant pour d’autres entrées**, telles que la voix, les mains et les contrôleurs.
Cela peut être utile pour diverses tâches.
Par exemple, cette opération peut être effectuée rapidement et facilement **sur la** scène en regardant un hologramme et en disant *« Sélectionner »* (voir également le point d’insertion et de [validation](gaze-and-commit.md)) ou *« Placer cela... »*, puis passer à l’endroit où l’utilisateur veut placer l’hologramme et dire *«... là»*. Vous trouverez des exemples à ce sujet dans [Mixed Reality Toolkit - Sélection d’une cible à l’aide du regard](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) et [Mixed Reality Toolkit - Positionnement d’une cible à l’aide du regard](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-positioning).

En outre, un exemple d’intention de l’utilisateur peut inclure des informations sur ce que les utilisateurs cherchent pour améliorer l’engagement avec des agents virtuels et des hologrammes interactifs. Par exemple, les agents virtuels peuvent adapter les options disponibles et leur comportement, en fonction du contenu actuellement affiché. 

### <a name="implicit-actions"></a>Actions implicites

La catégorie des actions implicites est étroitement liée à l’intention de l’utilisateur.
L’idée est que les hologrammes ou les éléments d’interface utilisateur réagissent de manière instinctuale, qui peut ne pas avoir l’impression que l’utilisateur interagit avec le système, mais plutôt que le système et l’utilisateur sont synchronisés. Par exemple, le **défilement automatique orienté vers le regard** de l’utilisateur peut lire un texte long, qui commence à faire défiler automatiquement une fois que l’utilisateur accède au bas de la zone de texte pour que l’utilisateur reste dans le sens de la lecture, sans soulever de doigt.  
Un aspect clé de cela est que la vitesse de défilement s’adapte à la vitesse de lecture de l’utilisateur.
Un autre exemple est un **Zoom et un panoramique pris en charge par l’œil,** où l’utilisateur peut sembler se plonger exactement sur ce qui lui est consacré. Le déclenchement et le contrôle de la vitesse de zoom peuvent être contrôlés par une entrée vocale ou manuelle, ce qui est important pour fournir à l’utilisateur le sentiment de contrôle tout en évitant d’être submergé. Nous parlerons de ces considérations de conception plus en détail ci-dessous. Une fois le zoom avant effectué, l’utilisateur peut suivre facilement, par exemple, le cours d’une rue pour explorer son voisinage en utilisant le regard.
Vous trouverez des démonstrations de ces types d’interaction dans l’exemple [Mixed Reality Toolkit - Navigation à l’aide du regard](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation).

D’autres cas d’usage pour les _actions implicites_ peuvent inclure :
- **Notifications intelligentes :** Vous vous êtes sans doute en désdans les notifications qui s’affichent directement là où vous êtes en train de regarder ? En tenant compte de ce à quoi un utilisateur fait attention, vous pouvez améliorer cette expérience en décalant les notifications à partir de l’endroit où l’utilisateur est actuellement Gazing. Cela limite les distractions et les ignore automatiquement une fois que l’utilisateur a terminé la lecture. 
- **hologrammes précis :** Hologrammes qui réagissent légèrement en cas de regard. Cela peut aller d’un léger éclat aux éléments de l’interface utilisateur, une fleur très lente à un chien virtuel qui commence à regarder l’utilisateur et wagging sa queue. Cette interaction peut fournir un sens intéressant de la connectivité et de la satisfaction dans votre application.

### <a name="attention-tracking"></a>Suivi de l’attention

Les informations sur l’emplacement ou le contenu des utilisateurs peuvent être un outil très puissant. Il peut aider à évaluer la convivialité des conceptions et à identifier les problèmes dans les workflows afin de les rendre plus efficaces.
La visualisation et l’analyse du suivi oculaire sont une pratique courante dans différents domaines d’application. avec HoloLens 2, nous fournissons une nouvelle dimension à cette compréhension, car les hologrammes 3d peuvent être placés dans des contextes réels et évalués en conséquence. la [Shared Computer Toolkit de réalité mixte](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) fournit des exemples de base pour la journalisation et le chargement des données de suivi visuel et comment les visualiser.
Microsoft s’attache à faciliter l’innovation tout en veillant à ce que les utilisateurs bénéficient d’une expérience éclairée et transparente quant à l’utilisation de leurs informations de suivi visuel.  Nous travaillons avec nos développeurs et nos équipes d’expérience utilisateur pour fournir des conseils à des tiers afin de s’assurer que les expériences sont centrées autour de l’utilisateur.  

Autres applications possibles dans ce domaine : 
-   **Œil à distance-visualisation du regard :** Yeux à distance-visualisations de regard : visualiser ce que les collaborateurs distants examinent, pour pouvoir fournir des commentaires immédiats et faciliter le traitement des informations plus précises.
-   **Études de recherche des utilisateurs :** Le suivi de l’attention peut aider les chercheurs à obtenir plus d’informations sur la façon dont les utilisateurs perçoivent et accèdent à l’environnement naturel, sans interférer, pour concevoir davantage de instinctual humains-Computer-interactions. Le suivi oculaire peut fournir des informations qui ne sont pas directement articulées par les participants à l’étude, qui peuvent être facilement manquées par le chercheur. 
-   **Surveillance des formations et des performances :** Pratiquez et optimisez l’exécution des tâches en identifiant plus efficacement les goulots d’étranglement dans le workflow d’exécution. Le suivi oculaire peut fournir des informations concrètes, en temps réel et objectives pour contribuer à l’amélioration de la formation, de la productivité et de la sécurité dans l’espace de travail. 
-   **Conception des évaluations, du marketing et des recherches de consommateurs :** Le suivi oculaire permet aux entreprises commerciales d’effectuer des études de marketing et de consommation dans des environnements réels ou d’analyser ce qui capture l’attention d’un utilisateur pour améliorer la conception du produit ou de l’espace. 

### <a name="other-use-cases"></a>Autres cas d’usage

- **Jeux :** Avez-vous déjà souhaité des superalimentations ? Voilà votre chance ! Vous pouvez faire en lévitation les hologrammes. Prenez des poutres laser de vos yeux, essayez-les dans [RoboRaid pour HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Transformez des ennemis en pierres ou figez-les. Utilisez votre vision à rayons X pour explorer des bâtiments. La seule limite, c’est votre imagination !
ATTENTION : pour en savoir plus, consultez nos [instructions relatives à la conception d’entrées](eye-gaze-interaction.md)orientées regard.

- **Avatars expressifs :** Le suivi des yeux permet d’obtenir des avatars 3D plus expressifs en utilisant des données de suivi visuel actif pour animer les yeux de l’avatar qui indiquent ce que l’utilisateur examine. 

- **Entrée de texte :** Le suivi oculaire peut être utilisé comme alternative pour une entrée de texte à faible effort, en particulier lorsque la parole ou les mains sont peu pratiques à utiliser. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Utilisation de l’œil en regard de l’interaction

La création d’une interaction qui tire parti du ciblage visuel à déplacement rapide peut être difficile.
D’un côté, les yeux se déplacent tellement vite que vous devez être attentif à l’utilisation des entrées de regard, car sinon les utilisateurs peuvent se rendre compte de l’expérience insurmontable ou gênante. En revanche, vous pouvez également créer des expériences véritablement magiques qui exciteront vos utilisateurs ! Pour vous aider, consultez notre présentation des principaux avantages, défis et recommandations en matière de conception pour [une interaction](eye-gaze-interaction.md)avec les yeux. 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>Solutions de secours lorsque le suivi oculaire n’est pas disponible

Dans de rares cas, les données de suivi oculaire peuvent ne pas être disponibles.
Cela peut être dû à différentes raisons, parmi lesquelles les plus courantes sont répertoriées ci-dessous :
* Le système n’a pas pu [étalonner l’utilisateur](/hololens/hololens-calibration).
* L’utilisateur a ignoré l' [étalonnage](/hololens/hololens-calibration).   
* L’utilisateur est étalonné, mais il a décidé de ne pas accorder à votre application l’autorisation d’utiliser ses données de suivi visuel.    
* L’utilisateur dispose de lunettes uniques ou d’une condition oculaire que le système ne prend pas encore en charge. 
* facteurs externes qui empêchent le suivi des yeux fiables, tels que les taches sur le visière de HoloLens ou les lunettes, le soleil direct et les occlusions en raison des cheveux devant les yeux.

Les développeurs doivent s’assurer qu’il existe une prise en charge de secours appropriée pour ces utilisateurs. Sur la page [suivi des yeux dans DirectX](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) , nous expliquons les API requises pour détecter si les données de suivi visuel sont disponibles. 

Alors que certains utilisateurs peuvent avoir des axent décidés de révoquer, d’accéder à leurs données de suivi visuel et d’avoir le compromis entre une expérience utilisateur insuffisante et la confidentialité de ne pas fournir l’accès à leurs données de suivi visuel, dans certains cas cela peut ne pas être intentionnel. Si votre application utilise le suivi oculaire et qu’il s’agit d’une partie importante de l’expérience, nous vous recommandons de le communiquer clairement à l’utilisateur.   

En informant la raison pour laquelle le suivi oculaire est essentiel pour votre application (peut-être même répertorier certaines fonctionnalités améliorées) pour tirer le meilleur parti de votre application, peut aider l’utilisateur à mieux comprendre ce qu’il abandonne. Aidez l’utilisateur à identifier la raison pour laquelle le suivi oculaire peut ne pas fonctionner (sur la base des vérifications ci-dessus) et propose des suggestions pour résoudre rapidement les problèmes potentiels. 

Par exemple, si vous pouvez détecter que le système prend en charge le suivi oculaire, l’utilisateur est étalonné et lui a donné son autorisation, mais aucune donnée de suivi oculaire n’est reçue, alors cela peut pointer vers d’autres problèmes tels que les traînées ou les yeux bloqués. 

Il existe des cas rares d’utilisateurs pour lesquels le suivi oculaire peut ne pas fonctionner. Par conséquent, n’hésitez pas à le faire en autorisant à ignorer ou même à désactiver les rappels pour activer le suivi visuel dans votre application.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Revenir en arrière pour les applications en utilisant les yeux en forme de point d’entrée principal

Si votre application utilise le point d’entrée de l’œil pour sélectionner rapidement des hologrammes dans la scène, mais que les données de suivi oculaire ne sont pas disponibles, nous vous recommandons de revenir à la tête de regard et de commencer à montrer le curseur en tête. Nous vous recommandons d’utiliser un délai d’expiration (par exemple, 500 – 1500 ms) pour déterminer s’il faut basculer ou non. Cette action empêche l’affichage des curseurs à chaque fois que le système risque de perdre brièvement le suivi en raison de mouvements rapides ou de clins d’œil et de clignotements. si vous êtes un développeur unity, le secours automatique à la tête de regard est déjà géré dans la réalité mixte Shared Computer Toolkit. Si vous êtes un développeur DirectX, vous devez gérer ce commutateur vous-même.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Revenir à d’autres applications spécifiques au suivi des yeux

Votre application peut utiliser des yeux oculaires de manière unique et adaptée aux yeux. Par exemple, animer les yeux d’un avatar ou pour attirer l’attention cartes thermiques en utilisant des informations précises sur l’attention visuelle. Dans ce cas, il n’y a pas de secours clair. Si le suivi oculaire n’est pas disponible, vous devrez peut-être désactiver ces fonctionnalités.
Là encore, nous vous recommandons de communiquer clairement à l’utilisateur qui ne sait pas que la fonctionnalité ne fonctionne pas.

<br>

Cette page vous a espérons vous fournir une bonne vue d’ensemble pour vous aider à comprendre le rôle du suivi visuel et des entrées de regard pour HoloLens 2. Pour commencer à développer, consultez nos informations sur le rôle de l' [oeil pour l’interaction avec les hologrammes](eye-gaze-interaction.md), le [point de regard sur Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) et les [yeux dans DirectX](../develop/native/gaze-in-directx.md).

## <a name="see-also"></a>Voir aussi

* [Étalonnage](/hololens/hololens-calibration)
* [Confort](comfort.md)
* [Interaction par pointage du regard](eye-gaze-interaction.md)
* [Œil-point de regard sur DirectX](../develop/native/gaze-in-directx.md)
* [oeil-point d’interfaut (Shared Computer Toolkit de la réalité mixte)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [Pointer et valider](gaze-and-commit.md)
* [Entrée vocale](../out-of-scope/voice-design.md)