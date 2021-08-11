---
title: Fonctionnalités expérimentales
description: Document relatif aux fonctionnalités expérimentales dans MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 9b7ef7564e0e4f84ba70c034b1bcc33a29498432620a002c8509de518dde479c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228383"
---
# <a name="experimental-features"></a>Fonctionnalités expérimentales

Certaines fonctionnalités de l’équipe MRTK sur semblent avoir beaucoup de valeur initiale même si nous n’avons pas entièrement étoffer les détails. Pour ces types de fonctionnalités, nous souhaitons que la Communauté puisse les voir tôt. Dans la mesure où elles sont au début du cycle, nous les étiquetons comme expérimentales pour indiquer qu’elles sont toujours en cours d’évolution et sujettes à modification au fil du temps.

## <a name="what-to-expect-from-an-experimental-feature"></a>Ce qu’il faut attendre d’une fonctionnalité expérimentale

Si un composant est marqué comme étant expérimental, vous pouvez vous attendre à ce qui suit :

- Exemple de scène illustrant l’utilisation, située sous `MRTK/Examples/Experimental` un sous-dossier
- Les fonctionnalités expérimentales ne peuvent pas contenir de documents.
- Ils n’ont probablement pas de tests.
- Les fonctionnalités expérimentales sont sujettes à modification.

## <a name="experimental-feature-guidelines"></a>Instructions relatives aux fonctionnalités expérimentales

### <a name="experimental-code-should-live-in-a-separate-folder"></a>Le code expérimental doit résider dans un dossier distinct

Le code expérimental doit être placé dans un dossier expérimental de niveau supérieur, suivi du nom de la fonctionnalité expérimentale. Par exemple, si vous tentez de contribuer à une nouvelle fonctionnalité FooBar, placez le code dans ce qui suit :

- Exemples de scènes, scripts `MRTK/Examples/Experimental/FooBar/`
- Scripts de composant, prefabs accéder à `MRTK/SDK/Experimental/FooBar/`
- Les inspecteurs de composants vont dans `MRTK/SDK/Inspectors/Experimental/FooBar`

Si vous utilisez des sous-dossiers sous le nom de la fonctionnalité expérimentale, essayez d’effectuer une mise en miroir de la même structure de dossiers de MRTK.

Par exemple, les solveurs sont placés sous `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

Gardez les scènes dans un dossier de scène près du haut : `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> Nous n’avons pas envisagé de disposer d’un seul dossier racine expérimental et de placer des expérimentations à la place `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` . Nous avons décidé d’utiliser des dossiers à la base pour faciliter la découverte des fonctionnalités expérimentales.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>Le code expérimental doit se trouver dans un espace de noms spécial

Assurez-vous que le code expérimental se trouve dans un espace de noms expérimental qui correspond à l’emplacement non expérimental. Par exemple, si votre composant fait partie de solveurs à `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , son espace de noms doit être `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .

Pour obtenir un exemple, consultez [cette PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) .

### <a name="experimental-features-should-have-an-experimental-attribute"></a>Les fonctionnalités expérimentales doivent avoir un attribut [expérimental]

Ajoutez un `[Experimental]` attribut au-dessus de l’un de vos champs pour qu’une petite boîte de dialogue s’affiche dans l’éditeur de composant qui mentionne que votre fonctionnalité est expérimentale et sujette à des modifications importantes.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>Les menus des fonctionnalités expérimentales doivent se trouver dans le sous-menu « expérimental ».

Assurez-vous que les fonctionnalités expérimentales se trouvent sous les sous-menus « expérimentaux » lors de l’ajout de commandes aux menus de l’éditeur. Voici quelques exemples :

Ajout d’une commande de menu de niveau supérieur :

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

Ajout d’un menu de composant :

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>Documentation

Procédez comme suit pour ajouter de la documentation pour votre fonctionnalité expérimentale :

1. Toute documentation relative à une fonctionnalité expérimentale doit se trouver dans un `readme.md` fichier dans le dossier expérimental. Par exemple, MRTK/SDK/expérimental/PulseShader/Readme. MD.

1. Sous *vues d’ensemble des fonctionnalités* , ajoutez un lien dans la section *expérimental* à l’adresse [`Documentation/toc.yml`](../toc.yml) .

### <a name="minimize-impact-to-mrtk-code"></a>Réduire l’impact sur le code MRTK

Bien que votre modification MRTK puisse faire fonctionner votre expérience, elle peut avoir un impact sur d’autres personnes de la façon dont vous ne vous attendez pas.
Toute régression que vous apportez au code MRTK Core entraînerait la restauration de votre demande de tirage (pull request).

L’objectif est de ne pas modifier les dossiers autres que les dossiers expérimentaux. Voici une liste des dossiers qui peuvent avoir des modifications expérimentales :

- MRTK/SDK/expérimental
- MRTK/Kit de développement logiciel/inspecteurs/expérimental
- MRTK/examples/expérimental

Les modifications en dehors de ces dossiers doivent être traitées très attentivement. Si votre fonctionnalité expérimentale doit inclure des modifications du code MRTK Core, envisagez de fractionner les modifications apportées MRTK en une requête de tirage distincte incluant des tests et de la documentation.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>L’utilisation de votre fonctionnalité expérimentale ne doit pas avoir d’impact sur la capacité des personnes à utiliser les contrôles principaux

La plupart des gens utilisent des composants d’expérience utilisateur de base tels que le bouton ManipulationHandler et les plus fréquents. Ils n’utiliseront probablement pas votre fonctionnalité expérimentale s’ils les empêchent d’utiliser des boutons.

L’utilisation de votre composant ne doit pas rompre les boutons, ManipulationHandler, BoundingBox ou interactive.

par exemple, dans [ce PR ScrollableObjectCollection](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), l’ajout d’un ScrollableObjectCollection a entraîné l’incapacité des utilisateurs à utiliser le bouton HoloLens prefabs. Même si cela n’a pas été provoqué par un bogue dans la demande de tirage (mais a plutôt exposé un bogue existant), la demande de tirage n’a pas pu être archivée.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>Fournir un exemple de scène illustrant l’utilisation de la fonctionnalité

Les utilisateurs doivent voir comment utiliser votre fonctionnalité et comment la tester.

Fournissez un exemple sous MRTK/examples/expérimental/YOUR_FEATURE

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>Réduire les défauts visibles par l’utilisateur dans les fonctionnalités expérimentales

D’autres n’utilisent pas la fonctionnalité expérimentale si elle ne fonctionne pas, mais elle n’est pas diplômée à une fonctionnalité.

Testez votre exemple de scène sur votre plateforme cible, assurez-vous qu’elle fonctionne comme prévu. Assurez-vous que votre fonctionnalité fonctionne également dans l’éditeur, afin que les utilisateurs puissent rapidement itérer et voir votre fonctionnalité même s’ils n’ont pas la plateforme cible.

## <a name="graduating-experimental-code-into-mrtk-code"></a>Diplôme du code expérimental dans le code MRTK

Si une fonctionnalité finit par être très utilisée, nous devrions la faire passer en code MRTK principal. Pour ce faire, la fonctionnalité doit avoir des tests, de la documentation et un exemple de scène.

Lorsque vous êtes prêt à MRTK la fonctionnalité, créez un problème pour l’archivage de votre demande de tirage. La demande de tirage doit inclure tous les éléments nécessaires pour créer une fonctionnalité de base : les tests, la documentation et un exemple de scène présentant l’utilisation.

En outre, n’oubliez pas de mettre à jour les espaces de noms pour supprimer le sous-espace « expérimental ».
