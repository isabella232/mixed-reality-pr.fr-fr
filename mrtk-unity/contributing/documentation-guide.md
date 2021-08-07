---
title: Conseils sur la documentation
description: instructions et normes de la documentation pour MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: aa583876d4ca9e115d4ea4507638eebab838207230693cb7c24b781d8f0b020b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210718"
---
# <a name="documentation-guidelines"></a>Conseils sur la documentation

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

ce document décrit les directives et les normes de la réalité mixte Shared Computer Toolkit (MRTK). Cela fournit une introduction aux aspects techniques de l’écriture et de la génération de documentation, pour mettre en évidence des pièges courants et pour décrire le style d’écriture recommandé.

La page elle-même est supposée servir d’exemple. elle utilise donc le style prévu et les fonctionnalités de balisage les plus courantes de la documentation.

- [Source](#source-documentation)
- [Procédure](#how-to-documentation)
- [Concevez](#design-documentation)
- [Remarques sur les performances](#performance-notes)
- [Dernières modifications](#breaking-changes)

---

## <a name="functionality-and-markup"></a>Fonctionnalités et balises

Cette section décrit les fonctionnalités fréquemment nécessaires. Pour voir comment ils fonctionnent, examinez le code source de la page.

1. Listes numérotées
   1. Listes numérotées imbriquées avec au moins 3 espaces vides de début
   1. Le nombre réel dans le code n’est pas pertinent. l’analyse s’occupe de définir le numéro d’élément correct.

- Listes de points à puces
  - Listes de points à puces imbriquées
- Texte en **gras** avec \* \* double astérisque\*\*
-  *texte* en italique avec un trait de \_ soulignement \_ ou \* un astérisque\*
- Texte `highlighted as code` dans une phrase \` en utilisant des guillemets\`
- Liens vers les pages docs [instructions de documentation MRTK](documentation-guide.md)
- Liens vers des [ancres dans une page](#style); les points d’ancrage sont formés en remplaçant les espaces par des tirets et en les convertissant en minuscules

Pour les exemples de code, nous utilisons les blocs avec trois battements \` \` \` et spécifiez *CSharp* comme langage pour la mise en surbrillance de la syntaxe :

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Quand vous mentionnez du code dans une phrase `use a single backtick` .

### <a name="todos"></a>Éléments TODO

Évitez d’utiliser éléments todo dans docs, car ces éléments todo (comme le code éléments TODO) ont tendance à s’accumuler et à obtenir des informations sur la façon dont elles doivent être mises à jour et pourquoi la perte est perdue.

Si vous devez absolument ajouter un TODO, procédez comme suit :

1. Présentez un nouveau problème sur GitHub décrivant le contexte derrière le TODO et fournissez suffisamment d’informations en arrière-plan qu’un autre contributeur serait en mesure de comprendre, puis de traiter le TODO.
2. Référencez l’URL du problème dans le todo dans la documentation.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>Sections en surbrillance

Pour mettre en surbrillance des points spécifiques sur le lecteur, utilisez *> [!NOTE]* , *> [!WARNING]* et *> [!IMPORTANT]* pour produire les styles suivants. Il est recommandé d’utiliser des notes pour les points généraux et les points d’avertissement/importants uniquement pour des cas spéciaux pertinents.

> [!NOTE]
> Exemple de note

> [!WARNING]
> Exemple d’avertissement

> [!IMPORTANT]
> Exemple de commentaire important

## <a name="page-layout"></a>Mise en page

### <a name="introduction"></a>Introduction

La partie juste après le titre du chapitre principal doit servir d’brève introduction à ce qu’est le chapitre. N’effectuez pas cette opération trop longue, à la place, ajoutez des sous-titres. Celles-ci permettent de lier des sections et peuvent être enregistrées en tant que signets.

### <a name="main-body"></a>Corps principal

Utilisez des titres à deux et trois niveaux pour structurer le reste.

**Mini sections**

Utilisez une ligne de texte en gras pour les blocs qui doivent ressortir. Nous pouvons le remplacer par des titres à quatre niveaux à un moment donné.

### <a name="see-also-section"></a>Section « Voir aussi »

La plupart des pages doivent se terminer par un chapitre appelé *Voir aussi*. Ce chapitre est simplement une liste à puces de liens vers les pages associées à cette rubrique. Ces liens peuvent également apparaître dans le texte de la page, le cas échéant, mais cela n’est pas obligatoire. De même, le texte de la page peut contenir des liens vers des pages qui ne sont pas liées à la rubrique principale, celles-ci ne doivent pas être incluses dans la liste *Voir aussi* . Consultez le [chapitre « Voir aussi » de cette page](#see-also) comme exemple pour le choix des liens.

## <a name="table-of-contents-toc"></a>Table des matières (TOC)

Les fichiers TOC sont utilisés pour générer les barres de navigation dans la documentation MRTK github.io.
Chaque fois qu’un nouveau fichier de documentation est ajouté, assurez-vous qu’il existe une entrée pour ce fichier dans l’un des fichiers toc. yml du dossier de documentation. Seuls les articles figurant dans les fichiers de la table des matières s’affichent dans la barre de navigation des documents du développeur. Il peut y avoir un fichier toc pour chaque sous-dossier du dossier de la documentation qui peut être lié à n’importe quel fichier TOC existant pour l’ajouter en tant que sous-section à la partie correspondante de la navigation.

## <a name="style"></a>Style

### <a name="writing-style"></a>Style d’écriture

Règle générale : essayez d’utiliser un **son professionnel**. Cela signifie généralement qu’il faut éviter un « ton de conversation ». Essayez également d’éviter hyperbolique et sensationalism.

1. N’essayez pas d’être amusant.
2. Ne jamais écrire’I'
3. Évitez « nous ». Cela peut généralement être facilement reformulé en utilisant’MRTK’à la place. Exemple : « nous prenons en charge cette fonctionnalité »-> « MRTK prend en charge cette fonctionnalité » ou « les fonctionnalités suivantes sont prises en charge... ».
4. De même, essayez d’éviter’vous'. Exemple : « avec cette simple modification, votre nuanceur devient configurable ! » -> « les nuanceurs peuvent être configurables avec un minimum d’effort ».
5. N’utilisez pas’expressions mal écrit'.
6. Évitez tout son intérêt, nous n’avons pas besoin de vendre quoi que ce soit.
7. De même, évitez d’être trop spectaculaire. Les points d’exclamation sont rarement nécessaires.

### <a name="capitalization"></a>Mise en majuscules

- Utilisez la **casse en phrases pour les titres**. Par exemple, Mettez en majuscule la première lettre et les noms, mais rien d’autre.
- Utilisez l’anglais normal pour tout le reste. Cela signifie que vous **ne devez pas mettre en majuscules les mots arbitraires**, même s’ils contiennent une signification particulière dans ce contexte. Préférer le *texte en italique* pour la mise en surbrillance de certains mots, [voir ci-dessous](#emphasis-and-highlighting).
- Lorsqu’un lien est incorporé dans une phrase (qui est la méthode recommandée), le nom du chapitre standard utilise toujours des majuscules, ce qui rompt la règle d’aucune mise en majuscule arbitraire dans le texte. Par conséquent, utilisez un nom de lien personnalisé pour corriger la casse. À titre d’exemple, voici un lien vers la documentation relative au [contrôle des limites](../features/ux-building-blocks/bounds-control.md) .
- Mettez les noms en majuscules, par exemple *Unity*.
- Ne pas mettre en majuscules « éditeur » lors de l’écriture de l' *éditeur Unity*.

### <a name="emphasis-and-highlighting"></a>Mise en évidence et mise en surbrillance

Il existe deux façons de mettre en évidence ou de mettre en évidence des mots, de les mettre en gras ou de les mettre en italique. Le texte en gras a pour effet que le **texte en gras** s’affiche et, par conséquent, peut être facilement remarqué tout en superposant un morceau de texte ou même simplement en faisant défiler une page. Le gras est parfait pour mettre en évidence les expressions que les gens doivent mémoriser. Toutefois, **utilisez rarement du texte en gras**, car il est généralement gênant.

Il est souvent nécessaire de regrouper un objet qui appartient logiquement ou de mettre en surbrillance un terme spécifique, car il a une signification particulière. Ces éléments n’ont pas besoin de sortir du texte global. Utilisez du texte en italique comme *méthode légère* pour mettre en surbrillance un événement.

De même, lorsqu’un nom de fichier, un chemin d’accès ou une entrée de menu est mentionné dans le texte, préférez le rendre italique pour le regrouper logiquement, sans gêner l’opération.

En général, essayez d' **éviter la mise en surbrillance du texte inutile**. Les termes spéciaux peuvent être mis en surbrillance une seule fois pour que le lecteur puisse les prendre en compte, ne pas répéter la mise en surbrillance dans tout le texte, lorsqu’il n’a plus besoin d’être utilisé et qu’il ne fait que

### <a name="mentioning-menu-entries"></a>Mention des entrées de menu

quand vous mentionnez une entrée de menu qu’un utilisateur doit cliquer, la convention actuelle est la suivante : *Project > des fichiers > créer une feuille de >*

### <a name="links"></a>Liens

Insérez autant de liens utiles à d’autres pages que possible, mais chaque lien une seule fois. Supposons qu’un lecteur clique sur chaque lien de la page et réfléchisse à la gêne qu’il aurait, si la même page s’ouvre 20 fois.

Préférer les liens incorporés dans une phrase :

- Incorrect : les indications sont utiles. Pour plus d’informations, consultez [ce chapitre](../contributing/documentation-guide.md) .
- BONNE : [les indications](documentation-guide.md) sont utiles.

Évitez les liens externes, ils peuvent devenir obsolètes ou contenir du contenu protégé par des droits d’auteur.

Lorsque vous ajoutez un lien, déterminez s’il doit également être listé dans la section [Voir aussi](#see-also) . De même, vérifiez si un lien vers la nouvelle page doit être ajouté à la page liée.

### <a name="images--screenshots"></a>Images/captures d’écran

**Utilisez des captures d’écran avec modération.** La gestion des images dans la documentation est beaucoup de travail, les petites modifications de l’interface utilisateur peuvent faire échouer de nombreuses captures d’écran. Les règles suivantes réduisent les tâches de maintenance :

1. N’utilisez pas de captures d’écran pour les éléments qui peuvent être décrits dans le texte. En particulier, n’encadrez **jamais une grille des propriétés** dans le seul but d’illustrer les noms et les valeurs des propriétés.
2. N’incluez pas dans une capture d’écran des éléments qui ne sont pas pertinents à ce qui est affiché. Par exemple, lorsqu’un effet de rendu est affiché, effectuez une capture d’écran de la fenêtre d’affichage, mais excluez toute interface utilisateur autour de celle-ci. En présentant une certaine interface utilisateur, essayez de déplacer des fenêtres autour de ce que seule cette partie importante se trouve dans l’image.
3. Lorsque vous incluez l’interface utilisateur de capture d’écran, Affichez uniquement les parties importantes. Par exemple, lorsque vous parlez de boutons dans une barre d’outils, créez une petite image qui affiche les boutons de barre d’outils importants, mais excluez tout autour de celle-ci.
4. Utilisez uniquement des images faciles à reproduire. Cela signifie que vous ne dessinez pas de marqueurs ou de surbrillance dans des captures d’écran. Tout d’abord, il n’y a pas de règles cohérentes quant à la façon dont elles doivent s’afficher. Deuxièmement, la reproduction d’une telle capture d’écran est un effort supplémentaire. Au lieu de cela, décrivez les parties importantes du texte. Il existe des exceptions à cette règle, mais elles sont rares.
5. Évidemment, il est bien plus facile de recréer une image GIF animée. Attendez-vous à la recréer jusqu’à la fin de l’heure, ou attendez-vous à ce que les gens la lèvent, s’ils ne souhaitent pas passer ce temps.
6. Laissez le nombre d’images dans un article faible. Souvent, une bonne méthode consiste à créer une capture d’écran globale d’un outil, qui affiche tout, puis à décrire le reste dans le texte. Cela facilite le remplacement de la capture d’écran si nécessaire.

Autres aspects :

- L’interface utilisateur de l’éditeur pour les captures d’écran doit utiliser l’éditeur de thème gris clair, car tous les utilisateurs n’ont pas accès au thème sombre et nous aimerions que les choses restent aussi cohérentes que possible.
- La largeur de l’image par défaut est de 500 pixels, car elle s’affiche bien sur la plupart des analyses. Essayez de ne pas en faire un trop grand nombre. la largeur de 800 pixels doit être la valeur maximale.
- Utilisez les png pour les captures d’écran de l’interface utilisateur.
- Utilisez des captures d’écran pour la fenêtre d’affichage 3D : png ou JPGs. Privilégier la qualité par rapport à la compression.

### <a name="list-of-component-properties"></a>Liste des propriétés du composant

Quand vous documentez une liste de propriétés, utilisez le texte en gras pour mettre en surbrillance le nom de la propriété, puis les sauts de ligne et le texte normal pour les décrire. N’utilisez pas de sous-chapitres ou de listes à puces.

En outre, n’oubliez pas de terminer toutes les phrases avec un point.

## <a name="page-completion-checklist"></a>Liste de vérification de l’exécution de la page

1. Vérifiez que les instructions de ce document ont été suivies.
1. Parcourez la structure du document et regardez si le nouveau document peut être mentionné sous la section [Voir aussi](#see-also) d’autres pages.
1. Si elle est disponible, ayez une personne ayant connaissance de la rubrique preuve de l’exactitude technique pour obtenir de l’aide.
1. Demander à quelqu’un de lire la page pour le style et la mise en forme. Il peut s’agir d’une personne ne connaissant pas la rubrique, qui est également une bonne idée d’obtenir des commentaires sur la compréhension de la documentation.

## <a name="source-documentation"></a>Documentation source

La documentation de l’API sera générée automatiquement à partir des fichiers sources MRTK. Pour faciliter cette tâche, les fichiers sources doivent contenir les éléments suivants :

- [Blocs de résumé de classe, de structure et d’énumération](#class-struct-enum-summary-blocks)
- [Propriétés, méthodes, blocs de synthèse d’événements](#property-method-event-summary-blocks)
- [Version d’introduction des fonctionnalités et dépendances](#feature-introduction-version-and-dependencies)
- [Champs sérialisés](#serialized-fields)
- [Valeurs d’énumération](#enumeration-values)

Outre les éléments ci-dessus, le code doit être correctement mis en commentaire pour permettre la maintenance, les correctifs de bogues et la facilité de personnalisation.

### <a name="class-struct-enum-summary-blocks"></a>Blocs de résumé de classe, de structure et d’énumération

Si une classe, un struct ou un enum est ajouté à MRTK, son objectif doit être décrit. Cela permet de prendre la forme d’un bloc de résumé au-dessus de la classe.

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

S’il existe des dépendances au niveau de la classe, elles doivent être documentées dans un bloc notes, immédiatement sous le résumé.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Les requêtes de tirage soumises sans synthèses pour les classes, structures ou énumérations ne sont pas approuvées.

### <a name="property-method-event-summary-blocks"></a>Propriétés, méthodes, blocs de synthèse d’événements

Les propriétés, les méthodes et les événements (PMEs) ainsi que les champs doivent être documentés avec des blocs de synthèse, quelle que soit la visibilité du code (public, privé, protégé et interne). L’outil de génération de documentation est responsable du filtrage et de la publication des fonctionnalités publiques et protégées uniquement.

Remarque : un bloc de résumé n’est **pas** requis pour les méthodes Unity (par exemple, éveillé, Start, Update).

La documentation PME est **requise** pour l’approbation d’une demande de tirage (pull request).

Dans le cadre d’un bloc de résumé des PME, le sens et l’objectif des paramètres et des données retournées sont requis.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Version d’introduction des fonctionnalités et dépendances

Dans le cadre de la documentation Résumé de l’API, vous trouverez des informations sur la version de MRTK dans laquelle la fonctionnalité a été introduite et toutes les dépendances doivent être documentées dans un bloc notes.

Les dépendances doivent inclure des dépendances d’extension et/ou de plateforme.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Champs sérialisés

Il est recommandé d’utiliser l’attribut ToolTip de Unity pour fournir une documentation d’exécution pour les champs d’un script dans l’inspecteur.

Afin que les options de configuration soient incluses dans la documentation de l’API, les scripts sont requis pour inclure *au moins* le contenu de l’info-bulle dans un bloc de résumé.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Valeurs d’énumération

Lors de la définition et de l’énumération, le code doit également documenter la signification des valeurs enum à l’aide d’un bloc Summary. Les blocs notes peuvent éventuellement être utilisés pour fournir des détails supplémentaires afin d’améliorer la compréhension.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Documentation de procédures

de nombreux utilisateurs du Shared Computer Toolkit de la réalité mixte n’ont peut-être pas besoin d’utiliser la documentation de l’API. Ces utilisateurs tirent parti de nos prefabs et scripts prédéfinis et réutilisables pour créer leurs expériences.

Chaque domaine de fonctionnalité contient un ou plusieurs fichiers de démarque (. MD) qui décrivent un niveau relativement élevé, ce qui est fourni. En fonction de la taille et/ou de la complexité d’un domaine de fonctionnalité donné, il peut être nécessaire de disposer de fichiers supplémentaires, jusqu’à un par fonctionnalité fournie.

Quand une fonctionnalité est ajoutée (ou que l’utilisation est modifiée), vous devez fournir une documentation de vue d’ensemble.

Dans le cadre de cette documentation, des sections de procédures, y compris des illustrations, doivent être fournies pour aider les clients à découvrir une fonctionnalité ou un concept dans la prise en main.

## <a name="design-documentation"></a>Documentation de conception

La réalité mixte offre la possibilité de créer des mondes entièrement nouveaux. Une partie de cette fonction est susceptible d’impliquer la création de ressources personnalisées à utiliser avec MRTK. Pour que cela soit aussi gratuit que possible pour les clients, les composants doivent fournir une documentation de conception décrivant les mises en forme ou autres exigences relatives aux ressources artistiques.

Voici quelques exemples où la documentation de conception peut être utile :

- Modèles de curseur
- Visualisations de mappages spatiaux
- Fichiers d’effet audio

Ce type de documentation est **fortement** recommandé et **peut** être demandé dans le cadre de la révision d’une demande de tirage (pull request).

Cela peut être différent de la recommandation de conception sur le site de [développement MS](/windows/mixed-reality/design)

## <a name="performance-notes"></a>Remarques sur les performances

Certaines fonctionnalités importantes sont coûteuses en matière de performances. Ce code dépend souvent de la façon dont il est configuré.

Par exemple :

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

Les remarques sur les performances sont recommandées pour les composants lourds UC et/ou GPU et **peuvent** être demandées dans le cadre d’une révision de demande de tirage. Toutes les notes de performance applicables doivent être incluses dans la documentation de l’API **et** de la présentation.

## <a name="breaking-changes"></a>Changements cassants

La documentation sur les modifications importantes consiste à se composer d’un [fichier](../contributing/breaking-changes.md) de niveau supérieur qui établit des liens vers les Breaking-Changes.MD individuels de chaque domaine de fonctionnalité.

Les fichiers breaking-changes.md de la zone de fonctionnalités doivent contenir la liste de toutes les modifications avec rupture connues pour une version donnée **, ainsi que** l’historique des modifications importantes par rapport aux versions précédentes.

Par exemple :

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

Les informations contenues dans les fichiers breaking-changes.md au niveau de la fonctionnalité seront regroupées dans les notes de publication de chaque nouvelle version de MRTK.

Toute modification avec rupture qui fait partie d’une modification **doit** être documentée dans le cadre d’une demande de tirage (pull request).

## <a name="tools-for-editing-markdown"></a>Outils pour la modification de la démarque

[Visual Studio Code](https://code.visualstudio.com/) est un outil formidable pour la modification des fichiers de démarque qui font partie de la documentation de MRTK.

Lors de l’écriture de la documentation, l’installation des deux extensions suivantes est également fortement recommandée :

- Extension docs de la démarque pour Visual Studio Code-utilisez Alt + M pour afficher un menu d’options de création de documents.

- Vérificateur orthographique de code : les mots mal orthographiés sont soulignés. Cliquez avec le bouton droit sur un mot mal orthographié pour le modifier ou enregistrez-le dans le dictionnaire.

Ces deux packages sont fournis dans le Pack de création docs publié de Microsoft.

## <a name="see-also"></a>Voir aussi

- [Exemple de lien « Voir aussi » pour la documentation](https://www.microsoft.com)
