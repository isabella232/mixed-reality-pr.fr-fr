---
title: Utilisation de WebVR avec Windows Mixed Reality
description: découvrez les principes fondamentaux de WebVR, comment l’utiliser avec des Microsoft Edge sur des casques Windows Mixed Reality et des problèmes de dépannage courants.
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, WebVR, Edge, Microsoft Edge, navigation web
ms.openlocfilehash: f61fff3c8d5083236c10d79d3824c489111f8d2be2138984f5613f295849bdf2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214123"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Utilisation de WebVR avec Windows Mixed Reality

>[!IMPORTANT]
>La plupart des navigateurs Web modernes ont déconseillé la prise en charge de WebVR en faveur de WebXR, la nouvelle norme pour la création d’expériences Web immersifs pour les casques VR. installez [le nouveau Microsoft Edge pour la](using-microsoft-edge.md) prise en charge de WebXR.

## <a name="what-is-webvr"></a>Qu’est-ce que WebVR

[WebVR](https://webvr.info) est une spécification ouverte qui vous permet d’expérimenter VR directement à partir d’un navigateur. Si un site Web implémente la prise en charge de WebVR et fournit du contenu 3D, il peut afficher le contenu immersif dans le casque, avec le consentement de l’utilisateur.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Quelle est la différence entre WebVR et la navigation sur le Web en VR ?

WebVR est une technologie qui permet à un auteur de site Web d’ajouter des fonctionnalités VR à une page. L’API WebVR est utilisée par une page pour afficher le contenu 3D (par exemple, une vidéo de 360 degrés, un modèle 3D ou un jeu 3D) à l’intégralité de votre casque. **Exemple :** Affichage d’une vidéo 360 sur [CNN.com/VR](http://cnn.com/vr). Si une page prend en charge WebVR, elle ajoute un bouton ou un autre élément d’interface utilisateur que vous pouvez sélectionner pour entrer VR.

La navigation sur le Web en VR signifie que vous utilisez le navigateur Edge pendant que vous enportez votre casque, en tant qu’ardoise d’application 2D dans le Cliffhouse.

## <a name="do-all-websites-support-webvr"></a>Prendre en charge tous les sites Web WebVR

Non. Les auteurs de sites Web doivent s’abonner à l’utilisation de WebVR et créer des sites optimisés pour des navigateurs, des casques et des contrôleurs spécifiques. Certains contenus WebVR sont optimisés pour les appareils mobile VR uniquement. En outre, gardez à l’esprit que les sites Web doivent créer et fournir explicitement du contenu WebVR. Le nombre de sites dont le contenu est compatible WebVR augmente chaque jour.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Puis-je utiliser mon vive/Oculus, etc. pour afficher le contenu de WebVR dans Microsoft Edge

Non. un casque Windows Mixed Reality est requis pour utiliser WebVR dans Edge. Toutefois, vous pouvez accéder au contenu de WebVR dans un autre navigateur. consultez la liste complète des appareils et navigateurs compatibles à l’adresse suivante : [WebVR. Rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Où puis-je trouver la documentation du développeur WebVR

La documentation du développeur se trouve ici : [WebVR Developer documentation](/microsoft-edge/webvr/).

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>J’ai trouvé un site Web avec WebVR qui ne fonctionne pas dans Windows Mixed Reality. Que dois-je faire

vous pouvez signaler des sites rompus directement à l’équipe Microsoft Edge browser dans le [suivi des problèmes](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)ou via twitter à l’aide de [#EdgeBug mot-dièse](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

vous pouvez également consigner les bogues à l’aide de l’application Hub de commentaires Windows sous la catégorie :

Microsoft Edge-> des problèmes de site web

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>Qu’est-ce qu’une bonne page pour tester si WebVR fonctionne

Consultez les [exemples webvr.info](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Comment faire configurer WebVR

pour expérimenter du contenu WebVR sur un casque Windows Mixed Reality (à l’aide de matériel ou de simulation), vous devez :

1. Vérifiez que votre casque est connecté.
2. lancez Microsoft Edge, sur le bureau ou dans la réalité mixte.
3. Accédez à une page WebVR activée.
4. Sélectionnez le bouton ENTER VR dans la page (l’emplacement et la représentation visuelle de ce bouton peuvent varier selon le site Web). Il peut ressembler à ceci : \
   ![Image de lunettes](images/75px-enter-vr.png)
5. La première fois que vous essayez d’entrer VR sur un domaine spécifique, le navigateur vous demande le consentement d’utiliser la vue immersive, sélectionnez Oui : ![Interface utilisateur de consentement affichée lors de la première tentative d’entrée de VR sur un domaine particulier](images/1053px-Webvr-consent-ui.png)
6. Votre casque doit commencer à afficher le contenu WebVR.

## <a name="see-also"></a>Voir aussi

* [Résolution des problèmes de > WebVR](webvr-questions.md)
* [Comment accéder à votre première expérience WebVR](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Utilisation de jeux et d’applications dans Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Votre foyer de réalité mixte](your-mixed-reality-home.md)
* [Système de suivi](tracking-system.md)
* [Contrôleurs de mouvement](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Envoi de commentaires](filing-feedback.md)