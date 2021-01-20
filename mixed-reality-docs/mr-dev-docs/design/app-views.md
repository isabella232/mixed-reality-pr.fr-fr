---
title: Vues d’applications
description: Découvrez comment utiliser les deux types d’affichages dans les applications Windows Mixed Reality (vues immersives et vues 2D).
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: vue immersive, vue 2D, ardoise, application, casque de la réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: b6a16fc3b1ac45d74874f37ce44a36d3e144fee8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580108"
---
# <a name="app-views"></a>Vues d’applications

Les applications Windows peuvent contenir deux types de vues : les vues **immersives** et les **vues 2D**. Les applications peuvent basculer entre les différents affichages immersif et 2D, en présentant leurs vues 2D sur une analyse sous la forme d’une fenêtre ou dans un casque comme un ardoise. Les applications qui ont au moins une vue immersive sont classées en tant qu' **applications de réalité mixte**. Les applications qui n’ont jamais de vue immersive sont des **applications 2D**.

## <a name="immersive-views"></a>Vues immersives

Dans une vue immersive, votre application peut créer des hologrammes dans l’environnement qui vous entoure ou plonger l’utilisateur dans un environnement virtuel. Quand une application dessine dans l’affichage immersif, aucune autre application ne dessine en même temps les &mdash; hologrammes de plusieurs applications ne sont pas composites ensemble. En ajustant continuellement la perspective à partir de laquelle votre [application affiche](../develop/platform-capabilities-and-apis/rendering.md) sa scène pour correspondre aux mouvements des têtes de l’utilisateur, votre application peut afficher des hologrammes [universels](coordinate-systems.md) . Les hologrammes dans le monde restent à un point fixe dans le monde réel ou peuvent afficher un monde virtuel qui conserve sa position lorsqu’un utilisateur se déplace.

![Dans une vue immersive, vous pouvez placer des hologrammes partout dans le monde.](images/designoverview-940px.jpg)<br>
*Dans une vue immersive, les hologrammes peuvent être placés dans le monde entier*

Sur [HoloLens](/hololens/hololens1-hardware), votre application affiche ses hologrammes en plus de l’environnement réel de l’utilisateur. Sur un [casque d’immersion immersif Windows Mixed Reality](../discover/immersive-headset-hardware-details.md), l’utilisateur ne peut pas voir le monde réel et, par conséquent, votre application doit rendre tout ce que l’utilisateur verra.

La [page d’accueil Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) (y compris le menu Démarrer et les hologrammes que vous avez placés autour de l’environnement) ne s’affiche pas non plus dans un affichage immersif. Sur HoloLens, Cortana relaie les notifications système qui se produisent lorsqu’une vue immersive est affichée, à laquelle l’utilisateur peut répondre avec une entrée vocale.

En mode immersif, votre application est également responsable de la gestion de toutes les entrées. L’entrée dans Windows Mixed Reality est composée [de point](gaze-and-commit.md)de présence, de [mouvement](gaze-and-commit.md#composite-gestures) (HoloLens uniquement), [voix et [contrôleurs de mouvement](motion-controllers.md) (casques immersifs uniquement).

## <a name="2d-views"></a>vues 2D

![Plusieurs vues 2D sont présentées dans la page d’hébergement de Windows Mixed Reality](images/teleportation-940px.png)<br>
*Plusieurs applications avec une vue 2D placée dans la page d’hébergement de Windows Mixed Reality*

Une application dotée d’une vue 2D apparaît dans la [page d’hébergement de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) (parfois appelée « Shell ») en tant que pièce virtuelle, rendue avec les lanceurs d’applications et autres hologrammes que l’utilisateur a placés dans son monde. L’utilisateur peut ajuster cette ardoise pour la déplacer et la mettre à l’échelle, même si elle reste à une résolution fixe, quelle que soit sa taille. Si le premier affichage de votre application est une vue 2D, votre contenu 2D remplit la même ardoise que celle utilisée pour lancer l’application.

Sur un casque de bureau, vous pouvez exécuter toutes les applications de plateforme Windows universelle (UWP) qui s’exécutent sur votre moniteur de bureau dès aujourd’hui. Ces applications affichent déjà des vues 2D aujourd’hui et leur contenu apparaît automatiquement dans un ardoise dans le monde de l’utilisateur lors de son lancement. les applications UWP 2D peuvent cibler la famille d’appareils **Windows. Universal** pour qu’elle s’exécute sur les casques de bureau et sur HoloLens en tant que tablettes.

L’une des principales utilisations des vues 2D est l’affichage d’un formulaire de saisie de texte qui utilise le clavier du système. Étant donné que l’interpréteur de commandes ne peut pas être rendu sur une vue immersive, l’application doit basculer vers une vue 2D pour afficher le clavier système. Les applications qui souhaitent accepter la saisie de texte doivent basculer vers une vue 2D avec une zone de texte. Alors que cette zone de texte a le focus, le système affiche le clavier du système, ce qui permet à l’utilisateur d’entrer du texte.

Une application peut avoir des vues 2D sur le moniteur de bureau et dans un casque attaché sur un PC de bureau. Par exemple, vous pouvez parcourir Edge sur votre moniteur de bureau à l’aide de sa vue principale 2D pour trouver une vidéo de 360 degrés. Quand vous jouez cette vidéo, Edge lance une vue immersive secondaire à l’intérieur du casque pour afficher le contenu vidéo immersif.

## <a name="see-also"></a>Voir aussi

* [Modèle d’application](app-model.md)
* [Mise à jour des applications UWP 2D pour la réalité mixte](../develop/porting-apps/building-2d-apps.md)
* [Obtention d’un HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [Exploration de la page d’accueil Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
* [Types d’applications de réalité mixte](types-of-mixed-reality-apps.md)