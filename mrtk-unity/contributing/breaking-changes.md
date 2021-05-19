---
title: Dernières modifications
description: stratégie concernant les modifications avec rupture dans MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 5f48503c4d28316cad49fbdf8bc163399ca9f7ad
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143493"
---
# <a name="breaking-changes"></a>Changements cassants

Les consommateurs du MRTK dépendent de la présence d’une surface d’API de version à version stable, afin qu’ils puissent prendre des mises à jour du MRTK sans avoir à modifier à chaque fois les modifications importantes.

Cette page décrit notre stratégie actuelle concernant les modifications avec rupture dans le MRTK, ainsi que des objectifs à long terme sur la façon dont nous pouvons mieux gérer le compromis entre la faible modification et la possibilité de faire des modifications techniques à long terme pour le code.

## <a name="what-is-a-breaking-change"></a>Qu’est-ce qu’une modification avec rupture ?

Une modification est une modification avec rupture si elle répond à l’une des conditions de la [liste a](#list-a) et remplit toutes les conditions de la [liste B](#list-b)

### <a name="list-a"></a>Liste A

- L’ajout, la suppression ou la mise à jour d’un membre ou d’une fonction d’une interface (ou la suppression ou le changement de nom de l’interface entière).
- Suppression, mise à jour (modification du type/de la définition, création d’une variable privée ou interne) de tout membre ou fonction membre protégé ou public de la classe. (ou suppression/renommage de la classe entière).
- Modification de l’ordre des événements déclenchés par une classe.
- Renommer un SerializedField privé (sans balise FormerlySerializedAs correspondante) ou une propriété publique sur un ScriptableObject (en particulier les modifications apportées aux profils).
- Modification du type d’un champ sur un ScriptableObject (en particulier les modifications apportées aux profils).
- Mises à jour de l’espace de noms ou asmdefs d’une classe ou d’une interface.
- Suppression d’un Prefab ou d’une suppression d’un script sur l’objet de niveau supérieur d’un Prefab.

### <a name="list-b"></a>Liste B

- L’élément multimédia en question se trouve dans le package de base (c’est-à-dire dans l’un des dossiers suivants) :

  - MRTK/noyau
  - MRTK/fournisseurs/
  - MRTK/services/
  - MRTK/SDK/
  - MRTK/extensions

- La ressource en question n’appartient pas à l’espace de noms expérimental.

> [!IMPORTANT]
> Tout élément multimédia qui se trouve dans le package d’exemples (c’est-à-dire une partie du MRTK/des exemples/dossier) est susceptible de changer à tout moment, à mesure que des ressources sont conçues pour être copiées et affichées par les consommateurs comme « implémentations de référence », mais ne font pas partie de l’ensemble principal d’API et de ressources. Les éléments multimédias de l’espace de noms expérimental (ou plus généralement, les fonctionnalités marquées comme expérimentales) sont publiés avant la fin de la diligence (tests, itérations d’expérience utilisateur, documentation) et publiés plus tôt pour obtenir des commentaires plus tôt.  Toutefois, étant donné qu’ils n’ont pas de test et de documentation, et parce que nous n’avons probablement pas pris en compte toutes les interactions et conceptions, nous les publions dans un État où le public devrait supposer qu’ils peuvent et seront modifiés (c’est-à-dire être modifiés, supprimés complètement, etc.).
>
> Pour plus d’informations, consultez [fonctionnalités expérimentales](../contributing/experimental-features.md) .

Comme la surface d’exposition pour les modifications avec rupture est très importante, il est important de noter que l’utilisation d’une règle absolue indiquant « aucune modification avec rupture » serait impossible : il peut y avoir des problèmes qui peuvent être résolus uniquement dans un raisonnable à l’aide d’une modification avec rupture. En d’autres termes, le seul moyen d’avoir « aucune modification avec rupture » consiste à n’avoir aucune modification.

Notre stratégie permanente consiste à éviter d’effectuer des modifications avec rupture si possible, et uniquement si la modification accumulerait une valeur importante au client ou à la structure à long terme.

## <a name="what-to-do-about-breaking-changes"></a>Que faire concernant les modifications avec rupture

S’il est possible d’effectuer une opération sans modification avec rupture et sans compromettre la structure à long terme et la viabilité de la fonctionnalité, n’effectuez pas la modification avec rupture. S’il n’y a pas d’autre façon, la stratégie actuelle consiste à évaluer chaque modification avec rupture, afin de comprendre si l’avantage de prendre la modification compense le coût pour le consommateur d’absorber la modification. Discussion sur ce qui vaut la peine de faire et ce qui n’est généralement pas le cas pour la demande de tirage ou la discussion sur l’émission.

Ce qui peut se produire ici se trouve dans plusieurs compartiments :

### <a name="the-breaking-change-adds-value-but-could-be-written-in-a-way-that-isnt-breaking"></a>La modification avec rupture ajoute de la valeur, mais elle peut être écrite d’une manière qui n’est pas endommagée

Par exemple, [cette](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4882) demande de tirage a ajouté une nouvelle fonctionnalité qui a été initialement écrite de telle sorte qu’elle modifie une interface existante, mais qui a été réécrite là où la fonctionnalité a été décomposée comme sa propre interface. C’est généralement le meilleur résultat possible. N’essayez pas de forcer une modification dans un formulaire sans rupture si cela compromettrait la viabilité à long terme ou la structure de la fonctionnalité.

### <a name="the-breaking-change-adds-sufficient-value-to-the-customer-that-its-worth-doing"></a>La modification avec rupture ajoute une valeur suffisante au client qu’il convient de faire.

Documentez les modifications avec rupture et fournissez la meilleure solution possible (par exemple, des étapes normatives pour la migration, ou mieux encore pour les outils qui migreront automatiquement le client). Chaque version peut contenir un petit nombre de modifications à l’arrêt. celles-ci doivent toujours être documentées dans les documents tels qu’ils ont été effectués dans [ce PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4858). S’il existe déjà un guide de migration 2. x. x → 2. x +1. x + 1, ajoutez des instructions ou des outils à ce document. S’il n’existe pas, créez-le.

### <a name="the-breaking-change-adds-value-but-the-customer-pain-would-be-too-high"></a>La modification avec rupture ajoute de la valeur, mais la difficulté du client est trop élevée

Les types de modifications avec rupture ne sont pas tous créés de la même façon : certains sont beaucoup plus pénibles, en fonction de notre expérience et en fonction des expériences client. Par exemple, les modifications apportées aux interfaces peuvent être pénibles, mais si la modification avec rupture est une modification dans laquelle un client est peu susceptible d’avoir été étendu/implémenté par le passé (le système de visualisation de diagnostic, par exemple), le coût réel est probablement faible à rien. Toutefois, si la modification est le type d’un champ sur un ScriptableObject (par exemple, sur l’un des profils de base du MRTK), cela risque de provoquer de gros problèmes au niveau du client. Les clients ont déjà cloné le profil par défaut, la fusion et la mise à jour des profils peuvent être extrêmement difficiles à effectuer manuellement (par exemple, via un éditeur de texte pendant la fusion), et la recopie du profil par défaut et la reconfiguration de tous les éléments à la main sont extrêmement susceptibles d’entraîner des régressions difficiles à déboguer.

Ces modifications doivent être replacées sur l’étagère jusqu’à ce qu’il existe une branche qui permet d’apporter des modifications importantes (avec une valeur significative qui donne aux clients une raison de mettre à niveau). Une telle branche n’existe pas actuellement. Dans le cadre de nos prochaines réunions de planification des itérations, nous examinerons l’ensemble des modifications/problèmes qui étaient « trop cassés » pour voir si nous avons atteint une masse critique afin de rendre possible un ensemble de modifications en même temps. Notez qu’il est dangereux de lancer une branche « tout est autorisé » sans diligence en raison des ressources d’ingénierie limitées dont nous disposons, et du fait que nous aurions dû fractionner les tests et la validation sur ces deux. Il doit y avoir un objectif clair et une date de début et de fin bien communiquée de ce type de branche lorsqu’il existe.

## <a name="long-term-management-of-breaking-changes"></a>Gestion à long terme des modifications avec rupture

À long terme, nous devrions chercher à réduire l’étendue de la modification avec rupture en accroissant l’ensemble des conditions dans la [liste B](#list-b). La transmission de l’ensemble des éléments de la [liste A](#list-a) sera toujours techniquement déconseillée pour l’ensemble de fichiers et de ressources que nous jugeons dans la « surface de l’API publique ». La façon dont nous pouvons obtenir un peu plus de liberté pour l’itération (c’est-à-dire modifier les détails de l’implémentation interne, permettre une refactorisation et un partage plus faciles du code entre plusieurs classes, etc.) est d’être plus explicite en ce qui concerne les portions du code qui sont officielles, plutôt que les détails de l’implémentation.

Une chose que nous avons déjà fait est de présenter le concept d’une fonctionnalité « expérimentale » (elle appartient à l’espace de noms expérimental, elle n’a peut-être pas de test/documentation et est publiquement délivrée, mais peut être supprimée et mise à jour sans avertissement). Cela a pour effet d’ajouter de nouvelles fonctionnalités plus tôt pour obtenir des commentaires antérieurs, mais qui ne sont pas immédiatement liés à sa surface API (car nous n’avons peut-être pas complètement pensé à la surface de l’API).

### <a name="other-examples-of-things-that-could-help-in-the-future"></a>Autres exemples de choses susceptibles de vous aider dans le futur

- Utilisation du [mot clé Internal](/dotnet/csharp/language-reference/keywords/internal).
  Cela nous permettrait d’avoir du code partagé dans nos propres assemblys (pour réduire la duplication du code) sans rendre les éléments publics aux consommateurs externes.
- Création d’un espace de noms « interne » (par exemple, Microsoft. MixedReality. Toolkit. Internal. Utilities), où nous documentons publiquement que tout ce qui se trouve dans cet espace de noms interne est susceptible d’être modifié à tout moment et peut être supprimé, etc. Cela est similaire à la façon dont les bibliothèques d’en-têtes C++ utilisent les espaces de noms :: Internal pour masquer leurs détails d’implémentation.