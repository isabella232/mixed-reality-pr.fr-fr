---
title: FAQ WebVR
description: Restez à jour grâce à la résolution des problèmes de réalité mixte pour les applications Web qui vont au-delà de notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, WebVR
ms.openlocfilehash: dc7a0b28e19f4f1fc029489aae2ea375e43b8d3b
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008659"
---
# <a name="webvr-faqs"></a>FAQ WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Pourquoi ne puis-je pas voir mes contrôleurs lors de l’affichage du contenu VR depuis Edge

Tous les contenus WebVR ne sont pas créés pour prendre en charge les contrôleurs de mouvement. WebVR permet aux développeurs de contenu de prendre en charge différents types d’entrée, tels que les contrôleurs de jeu ou les contrôleurs de mouvement. Si vous ne voyez pas vos contrôleurs sur un site, cela signifie probablement que le contrôleur de mouvement n’est pas pris en charge.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Pourquoi ne puis-je pas utiliser la souris dans une vue WebVR immersif

L’utilisation d’une souris est une fonctionnalité facultative de la spécification WebVR. Tous les navigateurs ne prennent pas en charge cette fonctionnalité, et tous les contenus WebVR ne sont pas créés pour prendre en charge l’entrée de la souris. WebVR permet aux développeurs de contenu de prendre en charge différents types d’entrée, tels que la souris, le clavier, les contrôleurs de jeu ou les contrôleurs de mouvement. Le comportement d’entrée de la souris varie selon le navigateur. Au sein de Microsoft Edge, les auteurs de sites Web doivent s’assurer qu’ils acceptent « pointerlock » lors de la présentation du casque pour que l’entrée de la souris fonctionne.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Pourquoi ne puis-je pas afficher les vidéos de 360 degrés de YouTube/Facebook/Vimeo/du gardien, etc., depuis Edge en VR

Une spécification WebVR permet aux sites Web de lancer des expériences VR directement à partir du navigateur. Les auteurs de ces sites Web n’ont pas implémenté cette spécification pour l’instant. Il peut y avoir des applications téléchargeables sur certaines plateformes, qui permettent d’afficher le contenu VR de ces fournisseurs.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Pourquoi ne puis-je pas entrer VR à partir de Firefox ou chrome

WebVR est uniquement pris en charge par les appareils Windows Mixed Reality dans Edge pour l’instant.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Lorsque j’entre VR à partir d’un site Web, pourquoi un écran vide s’affiche-t-il dans mon casque ?

Le site Web n’a peut-être pas implémenté la prise en charge de plusieurs machines GPU (y compris les ordinateurs portables GPU hybrides). Essayez d’effectuer les opérations suivantes :

* Rechargez la page.
* Sur les ordinateurs de bureau, connectez le casque à la même carte graphique que le moniteur qui affiche Microsoft Edge. Branchez-les tous les deux dans la carte graphique plus puissante, et non dans la carte graphique intégrée.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Lorsque je quitte VR en regardant une vidéo à partir de Edge, le son continue de fonctionner, mais la fenêtre du bord est grisée

Il s’agit d’un problème connu lors de l’exécution de WebVR à partir de Edge dans la maison de la falaise de la réalité mixte. Pour le résoudre, appuyez sur Échap sur le clavier au lieu du bouton Windows pour quitter l’expérience WebVR, ou activez la fenêtre grisée du bord en la sélectionnant, puis arrêtez la vidéo.

## <a name="can-i-use-webvr-on-the-hololens"></a>Puis-je utiliser WebVR sur le HoloLens

Microsoft n’a pas annoncé de WebVR sur le HoloLens à ce stade.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Pourquoi ma vue est-elle au niveau étage lors de l’affichage du contenu WebVR à partir de Edge ?

Le site Web ne prend pas correctement en charge les casques Windows Mixed Reality. Pour contourner ce problème :

1. Placez le casque à l’étage de votre espace.
2. Accédez à la page WebVR à l’aide de Microsoft Edge sur votre bureau (pas dans la réalité mixte).
3. Sélectionnez « entrer VR ».
4. Attendez cinq à 10 secondes pour que l’expérience soit entièrement entrée en mode immersif.
5. Placez sur le casque.

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>L’affichage est à faible résolution dans certaines expériences WebVR

Ces sites Web ne prennent pas correctement en charge les casques haute résolution. Pour contourner ce problème :

* Si vous lancez WebVR à partir du Bureau (et non dans la maison de la falaise de la réalité mixte), assurez-vous que la fenêtre est agrandie avant de sélectionner « Enter VR ».
* Évitez de redimensionner la fenêtre Microsoft Edge une fois que vous avez entré VR.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Pourquoi l’affichage immersif WebVR se termine-t-il lorsque je modifie les onglets du navigateur ?

Ce comportement est normal. Pour des raisons de sécurité, seul l’onglet actif du navigateur peut accéder aux casques connectés.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Pourquoi ne puis-je pas entendre l’audio sur une expérience WebVR particulière

Le site Web utilise peut-être le format de fichier audio OGG, que Microsoft Edge ne prend pas actuellement en charge.

Vous pouvez signaler des sites rompus directement à l’équipe du navigateur Microsoft Edge dans le [suivi des problèmes](https://developer.microsoft.com/microsoft-edge/platform/issues/)ou via Twitter à l’aide de [#EdgeBug mot-dièse](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Pourquoi les commentaires haptique ne fonctionnent pas dans WebVR avec les contrôleurs de mouvement

Microsoft Edge ne prend pas en charge les haptique sur les extensions d’API du boîtier WebVR.