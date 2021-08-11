---
title: Vue d’ensemble des exemples de suivi oculaire
description: Exemple pour générer eyetracking dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking,
ms.openlocfilehash: 32ae64a470572dda71578948d5091887bea9e0e084d97ede7f2f14af596b5a6b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223216"
---
# <a name="eye-tracking-examples-overview"></a>Vue d’ensemble des exemples de suivi oculaire

Cette rubrique explique comment prendre rapidement en main le suivi oculaire dans MRTK en vous appuyant sur les exemples de suivi oculaire MRTK (ressources/MRTK/exemples/démonstrations/EyeTracking).
Ces exemples vous permettent de découvrir l’une de nos nouvelles fonctionnalités de saisie magique : le **suivi oculaire**!
La démonstration comprend divers cas d’usage, allant des activations basées sur les yeux implicites à la manière de combiner en toute transparence les informations sur ce que vous examinez avec la **voix** et **les entrées.**
Cela permet aux utilisateurs de sélectionner et de déplacer rapidement et facilement le contenu holographique dans leur vue simplement en regardant une cible et en disant _« Sélectionner »_ ou en effectuant un mouvement manuel.
Les démonstrations incluent également un exemple de défilement orienté vers le regard, panoramique et zoom du texte et des images sur un ardoise.
Enfin, un exemple est fourni pour l’enregistrement et la visualisation de l’attention visuelle de l’utilisateur sur un ardoise 2D.
Dans la section suivante, vous trouverez plus d’informations sur la façon dont chacun des différents exemples du package d’exemples de suivi oculaire MRTK (ressources/MRTK/examples/démos/EyeTracking) comprend :

![Liste des scènes de suivi oculaire](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

La section suivante est une vue d’ensemble rapide des scènes de démonstration du suivi des yeux.
Les scènes de démonstration de suivi oculaire MRTK sont [chargées](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)de manière additive, que nous expliquerons ci-dessous comment configurer.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Vue d’ensemble des exemples de démonstrations de suivi oculaire

### <a name="eye-supported-target-selection"></a>[**Sélection de la cible prise en charge par l’œil**](../input/eye-tracking/eye-tracking-target-selection.md)

Ce didacticiel présente la facilité d’accès aux données de regard oculaire pour sélectionner des cibles.
Il comprend un exemple de commentaires subtils et puissants pour fournir à l’utilisateur la certitude qu’une cible est ciblée sans être écrasante.
En outre, il existe un exemple simple de notifications intelligentes qui disparaissent automatiquement après la lecture.

**Résumé**: sélections de cibles rapides et faciles à l’aide d’une combinaison d’yeux, de voix et d’entrées de main.

### <a name="eye-supported-navigation"></a>[**Navigation prise en charge par l’œil**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine que vous lisez des informations sur un affichage distant ou sur un lecteur e-lecteur et que vous atteignez la fin du texte affiché, le texte défile automatiquement pour afficher davantage de contenu.
Ou comment faire un zoom direct direct vers l’emplacement de votre recherche ?
Voici quelques-uns des exemples présentés dans ce didacticiel sur la navigation prise en charge par les yeux.
En outre, il existe un exemple de rotation mains libres d’hologrammes 3D en les faisant pivoter automatiquement en fonction de votre focus actuel.

**Résumé**: défilement, panoramique, zoom, rotation 3D à l’aide d’une combinaison d’yeux, de voix et d’entrées de main.

### <a name="eye-supported-positioning"></a>[**Positionnement de la prise en charge oculaire**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

Ce didacticiel présente un scénario d’entrée appelé [Put-It-](https://youtu.be/CbIn8p4_4CQ) le retour à la recherche à partir du MIT Media Lab au début des années 1980, avec les entrées de l’œil, de la main et de la voix.
L’idée est simple : Tirez parti de vos yeux pour la sélection et le positionnement rapides des cibles.
Examinez simplement un hologramme et dites « _Placer_», regardez où vous souhaitez le placer et dites-le _« là ! »_.
Pour un positionnement plus précis de votre hologramme, vous pouvez utiliser des entrées supplémentaires de vos mains, de vos voix ou de vos contrôleurs.

**Résumé**: positionnement des hologrammes à l’aide des yeux, des entrées vocales et de la main (*glisser-déplacer*). Curseurs pris en charge par l’œil utilisant des yeux et des mains.

### <a name="visualization-of-visual-attention"></a>**Visualisation de l’attention visuelle**

Les données basées sur l’emplacement des utilisateurs constituent un outil très puissant pour évaluer l’utilisation d’une conception et identifier les problèmes dans les flux de travail efficaces.
Ce didacticiel présente les différentes visualisations de suivi oculaire et la façon dont elles s’adaptent aux différents besoins.
Nous fournissons des exemples de base pour la journalisation et le chargement des données de suivi visuel et des exemples pour la visualisation.

**Résumé**: carte à attention à deux dimensions (cartes thermiques) sur les ardoises. Enregistrement & relecture des données de suivi oculaire.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Configuration des exemples de suivi oculaire MRTK

### <a name="prerequisites"></a>Prérequis

notez que l’utilisation des exemples de suivi oculaire sur l’appareil requiert une HoloLens 2 et un exemple de package d’application généré avec la fonctionnalité « en entrée de regard » sur le AppXManifest du package.

Pour pouvoir utiliser ces exemples de suivi oculaire sur un appareil, veillez à suivre [ces étapes](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) avant de créer l’application dans Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Chargez EyeTrackingDemo-00-RootScene. Unity

*EyeTrackingDemo-00-RootScene* est la scène de base (_racine_) qui contient tous les composants MRTK principaux.
Il s’agit de la scène que vous devez charger en premier et à partir de laquelle vous allez exécuter les démonstrations de suivi oculaire.
Il comprend un menu de scène graphique qui vous permet de basculer facilement entre les différents exemples de suivi oculaire qui seront chargés de manière [additive](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).

![Menu Scene dans l’exemple de suivi oculaire](../images/eye-tracking/mrtk_et_scenemenu.jpg)

La scène racine comprend quelques composants principaux qui sont conservés dans les scènes chargées de manière additive, telles que les profils configurés par MRTK et l’appareil photo de scène.
Le _MixedRealityBasicSceneSetup_ (voir la capture d’écran ci-dessous) comprend un script qui chargera automatiquement la scène référencée au démarrage.
Par défaut, il s’agit de _EyeTrackingDemo-02-TargetSelection_.  

![Exemple de script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. Ajout de scènes au menu Générer

pour charger des scènes additives pendant l’exécution, vous devez d’abord ajouter ces scènes à votre _Paramètres de build-> scènes dans_ le menu générer.
Il est important que la scène racine s’affiche comme la première scène de la liste :

![menu générer Paramètres scène pour les exemples de suivi oculaire](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. lire les exemples de suivi oculaire dans l’éditeur Unity

après avoir ajouté les scènes de suivi oculaire à la Paramètres de génération et à charger _EyeTrackingDemo-00-RootScene_, il y a une dernière chose à vérifier : le script _« OnLoadStartScene »_ attaché au _MixedRealityBasicSceneSetup_ GameObject est-il activé ? Cela permet d’informer la scène racine de la scène de démonstration à charger en premier.

![Exemple pour le script OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

Allons-y ! Appuyez sur _« Play »_!
Vous devriez voir plusieurs gemmes apparaître et le menu scène en haut.

![Exemple de capture d’écran de la cible ET sélectionner une scène](../images/eye-tracking/mrtk_et_targetselect.png)

Vous devez également noter un petit cercle translucide au centre de votre vue de jeu.
Cela agit comme un indicateur (curseur) de la _simulation de regard_: appuyez simplement sur le _bouton droit_ de la souris et déplacez la souris pour modifier sa position.
Quand le curseur pointe sur les gemmes, vous remarquerez qu’il sera aligné sur le centre de la gemme actuellement affichée.
C’est un excellent moyen de tester si des événements sont déclenchés comme prévu lors de la _« recherche »_ sur une cible.
Sachez _que le point de contrôle_ de la souris est un complément plutôt médiocre à nos mouvements d’oeil rapides et involontaires.
toutefois, il est parfait pour tester les fonctionnalités de base avant d’effectuer une itération sur la conception en la déployant sur l’appareil HoloLens 2.
Retour à notre exemple de scène de suivi oculaire : la gemme pivote tant qu’elle est examinée et peut être détruite en « regardant » sur celle-ci et...

- En appuyant sur _entrée_ (ce qui simule « Select »)
- Dire _« Select »_ dans votre microphone
- Tout en appuyant sur l' _espace_ pour afficher l’entrée simulée, cliquez sur le bouton gauche de la souris pour effectuer un pincement simulé

Nous décrivons plus en détail comment vous pouvez obtenir ces interactions dans notre didacticiel sur la [**sélection de cibles prises en charge**](../input/eye-tracking/eye-tracking-target-selection.md) par les yeux.

Lorsque vous déplacez le curseur vers la barre de menus supérieure de la scène, vous remarquerez que l’élément actuellement mis en surbrillance sera légèrement surligné.
Vous pouvez sélectionner l’élément actuellement mis en surbrillance à l’aide de l’une des méthodes de validation décrites ci-dessus (par exemple, en appuyant sur _entrée_).
De cette façon, vous pouvez basculer entre les différents exemples de scènes de suivi oculaire.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. Comment tester des sous-scènes spécifiques

Lorsque vous travaillez sur un scénario spécifique, vous pouvez ne pas souhaiter parcourir le menu scène à chaque fois.
Au lieu de cela, vous souhaiterez peut-être commencer directement à partir de la scène sur laquelle vous travaillez quand vous appuyez sur le bouton de _lecture_ .
Aucun problème non plus ! Voici ce que vous pouvez faire :

1. Charger la scène _racine_
2. Dans la scène _racine_ , désactivez le script _'OnLoadStartScene'_
3. _Glissez_ -déplacez une des scènes de test de suivi oculaire décrites ci-dessous (ou toute autre scène) dans votre affichage _hiérarchique_ , comme indiqué dans la capture d’écran ci-dessous.

    ![Exemple de scène additive](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Appuyez sur _Play_

notez que le chargement de la sous-scène comme celle-ci n’est pas persistant : cela signifie que si vous déployez votre application sur l’appareil HoloLens 2, elle ne chargera que la scène racine (en supposant qu’elle apparaît en haut de votre Paramètres de Build).
En outre, lorsque vous partagez votre projet avec d’autres personnes, les sous-scènes ne sont pas chargées automatiquement.

---

Maintenant que vous savez comment faire fonctionner les exemples de suivi oculaire MRTK, commençons par examiner plus en détail comment sélectionner des hologrammes avec vos yeux : [sélection de cible prise en charge](../input/eye-tracking/eye-tracking-target-selection.md)par l’œil.

---
[Retour à « suivi oculaire dans le MixedRealityToolkit »](../input/eye-tracking/eye-tracking-Main.md)
