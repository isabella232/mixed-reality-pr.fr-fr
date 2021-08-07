---
title: Guide de conception de lanceur d’applications 3D
description: Un lanceur d’applications 3D est un objet « physique » dans la maison de réalité mixte de l’utilisateur qu’il peut sélectionner pour lancer une application.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, lanceur d’applications en 3d, casque immersif, cube en direct, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, UWP, Win32, éclairage, couleur
ms.openlocfilehash: 2d93930d63b251aa91d77c96b4d5250baba54c51de50388f690b3588b1580761
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188487"
---
# <a name="3d-app-launcher-design-guidance"></a>Guide de conception de lanceur d’applications 3D

lorsque vous placez sur un casque Windows Mixed Reality immersif, vous entrez la Windows Mixed Reality page d’hébergement. La maison est visualisée sous la forme d’une maison sur une falaise placée par des montagnes et de l’eau, mais vous pouvez [choisir d’autres environnements et même créer les vôtres](../design/add-custom-home-environments.md). Au sein de l’espace de la famille, un utilisateur est libre de réorganiser et d’organiser les objets et applications 3D dont il se soucie. Un **lanceur d’applications 3D** est un objet « physique » dans la maison de réalité mixte de l’utilisateur qu’il peut sélectionner pour lancer une application.

![Exemple : lanceur d’applications 3D avec un oiseau flottant](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Exemple de lanceur d’application 3D d’oiseau flottant (application fictive)*

## <a name="3d-app-launcher-creation-process"></a>processus de création du lanceur d’applications 3D

La création d’un lanceur d’applications 3D comporte trois étapes :

1. Conception et concept (cet article)
2. [Modélisation et exportation](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Intégration dans votre application :
    * [Applications UWP](implementing-3d-app-launchers.md)
    * [Applications Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Principes de conception

### <a name="fantastic-yet-familiar"></a>Fantastique, encore familier

l’environnement de Windows Mixed Reality dans lequel votre lanceur d’applications se trouve est une partie familière, une partie fantastique/science-fi. Les meilleurs lanceurs suivent les règles de ce monde. Pensez à la façon dont vous pouvez prendre un objet représentatif familier de votre application, mais pliez certaines règles de réalité réelle. La magie se produira.

### <a name="intuitive"></a>Peu

Lorsque vous examinez le lanceur d’applications, son objectif est de lancer votre application. il doit être évident et ne devrait pas provoquer de confusion. Par exemple, assurez-vous que votre lanceur est un représentant évident et évident de votre application qu’il ne sera pas confondu avec un morceau de décor dans la maison de la falaise. Votre lanceur d’applications doit inviter des personnes à les toucher/sélectionner.

![Exemple : nouveau lanceur d’applications de note 3D](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Exemple de lanceur d’application 3D note (application fictive)*

### <a name="home-scale"></a>Échelle personnelle

les lanceurs d’applications 3D qui vivent dans la maison de la falaise et leur taille par défaut doivent avoir un sens avec les autres objets « physiques » de l’espace. Si vous placez votre lanceur à côté, par exemple, d’une usine de maison ou de meubles, vous devez vous sentir à la maison, à la taille. Un bon point de départ consiste à voir comment il s’agit de 30 centimètres cubes, mais n’oubliez pas que les utilisateurs peuvent le mettre à l’échelle s’ils le souhaitent.

### <a name="own-able"></a>En toute possession

Le lanceur d’application doit ressembler à un objet qu’une personne peut avoir dans son espace. Elles seront virtuellement entourées de ces éléments, de sorte que le lanceur doit avoir le même aspect que quelque chose que l’utilisateur a été jugé suffisamment souhaitable pour se rendre à la recherche et rester à proximité.

![Exemple : lanceur d’applications Astro Warp 3D](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Exemple de lanceur d’application Astro Warp 3D (application fictive)*

### <a name="recognizable"></a>Reconnaissable

Votre lanceur d’applications 3D doit instantanément exprimer « la personnalisation de votre application » aux personnes qui l’affichent. Si votre application contient un caractère en étoile ou un objet particulièrement identifiable, nous vous recommandons de l’utiliser en tant que partie significative de votre conception. Dans un monde de réalité mixte, un objet attire davantage l’intérêt des utilisateurs qu’un seul logo. Les objets reconnaissables communiquent la personnalisation rapidement et clairement.

### <a name="volumetric"></a>Dosage

Votre application mérite plus que simplement placer votre logo sur un plan plat et l’appeler une journée. Votre lanceur doit ressembler à un objet physique passionnant et 3D dans l’espace de l’utilisateur. Une bonne approche consiste à imaginer que votre application allait avoir une info-bulle dans la parade du jour de Thanksgiving de Macy. Demandez-vous ce que les gens étaient vraiment en mesure de tomber dans la rue ? Que feriez-vous de tous les angles d’affichage ?

:::row:::
    :::column:::
        ![](images/20171016-140436-mixedreality-640px.jpg) *Logo* logo uniquement
    :::column-end:::
    :::column:::
        ![Plus reconnaissable avec un caractère ](images/20171016-140557-mixedreality-640px.jpg) *plus reconnaissable avec un caractère*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Une approche plate, pas étonnamment surprenant, est une approche plate plate ](images/20171016-155101-mixedreality-640px.jpg) *, pas étonnamment surprenant, à plat*
    :::column-end:::
    :::column:::
        ![L’approche volumétrique illustre mieux l’approche volumétrique de votre application et ](images/20171016-161407-mixedreality-640px.jpg) *améliore votre application*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>Astuces pour les bons modèles 3d

* Lors de la planification de dimensions pour votre lanceur d’applications, prenez un cube de 30 cm environ. Par conséquent, un ratio de taille de 1:1:1.
* Les modèles doivent être sous les polygones 10 000. [En savoir plus sur le nombre de triangles et les niveaux de détail (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Testez sur un casque immersif.
* Créez des détails dans la géométrie de votre modèle, dans la mesure du possible, ne vous fiez pas aux textures pour des détails.
* Créez une géométrie fermée « eau serrée ». Aucun trou n’est modélisé dans.
* Utilisez des matériaux naturels dans votre objet. Imagine l’informatique dans le monde réel.
* Assurez-vous que votre modèle lit bien des distances et des tailles différentes.
* Lorsque votre modèle est prêt à l’emploi, lisez les [instructions relatives](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)à l’exportation de ressources.

![Modèle avec des détails subtils dans la texture](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modèle avec des détails subtils dans la texture*

### <a name="what-to-avoid"></a>À éviter

* N’utilisez pas de détails à contraste élevé ni de modèles et de textures de petite taille, occupés.
* N’utilisez pas de géométrie fine : elle ne fonctionne pas bien à distance et fera mal l’alias.
* Ne laissez pas les parties de votre modèle s’étendre trop au-delà du ratio de taille de 1:1:1. Il va créer des problèmes de mise à l’échelle.

![Évitez les grands contrastes, les petits modèles occupés](images/20171013-143603-mixedreality-640px.jpg)<br>
*Évitez les modèles à contraste élevé, les petits et les plus occupés*

## <a name="how-to-handle-type"></a>Comment gérer le type

* Nous vous recommandons d’utiliser votre type de lancement d’application 1/3 (ou plus). Le type est l’élément principal qui donne aux gens une idée que votre lanceur est, en fait, un lanceur, ce qui est intéressant s’il est substantiel.
* Évitez de rendre le type Super étendu : essayez de le conserver dans les limites des dimensions principales des lanceurs d’applications (plus ou moins).
* Le type plat peut fonctionner, mais il peut être difficile à afficher à partir de certains angles et dans certains environnements. Vous pouvez envisager de placer un objet solide ou un fond en arrière-plan pour faciliter cette opération.
* L’ajout d’une dimension à votre type semble agréable en 3D. L’ombrage des côtés du type d’une couleur plus sombre peut contribuer à la lisibilité.

:::row:::
    :::column:::
        ![Le type plat sans fond peut être difficile à afficher à partir de certains angles et dans certains environnements, ](images/flattype-640px.png) *le type plat sans fond peut être difficile à afficher à partir de certains angles et dans certains environnements*
    :::column-end:::
    :::column:::
        ![Le type avec une zone de fond intégrée peut fonctionner correctement ](images/flattypeandbkg-640px.png) *avec un fond intégré qui peut fonctionner correctement*
    :::column-end:::
    :::column:::
        ![Le type extrudé peut fonctionner correctement si vous ombrer les côtés le ](images/20171016-160221-mixedreality-640px.jpg) *type extrudé peut fonctionner correctement si vous Nuancez les côtés*
    :::column-end:::
:::row-end:::

**Tapez les couleurs qui fonctionnent**

* Blancs
* Noir
* Couleur semi-saturée vive

![Tapez les couleurs qui fonctionnent.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Tapez les couleurs qui fonctionnent*

### <a name="colors-to-avoid"></a>Couleurs à éviter

Les couleurs de type qui sont à l’origine des problèmes sont les suivantes :

* Mi-tons
* Gris
* Couleurs sursaturées ou couleurs désaturées

![Tapez les couleurs qui provoquent des problèmes.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Couleurs de type qui provoquent des problèmes*

## <a name="lighting"></a>Éclairage

L’éclairage de votre lanceur d’applications provient de l’environnement de la maison de la falaise. Veillez à tester votre lanceur à plusieurs endroits de la maison, afin qu’il soit parfait dans le ciel et dans les ombres. La bonne nouvelle, c’est que si vous avez suivi les autres conseils de conception de ce document, votre lanceur doit être en bonne forme pour la plupart des éclairages de la maison de la falaise.

Les bonnes places pour tester la manière dont votre lanceur regarde dans les différentes lumières de l’environnement sont le Studio, la salle de support, n’importe où et sur le patio Back (la zone concrète avec la pelouse). Un autre bon test consiste à le placer en demi-feu et demi-ombre et à voir à quoi il ressemble.

![Assurez-vous que votre lanceur semble parfait en clair et dans les ombres.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Assurez-vous que votre lanceur semble parfait dans le ciel et dans les ombres*

## <a name="texturing"></a>Texturation

### <a name="authoring-your-textures"></a>Création de vos Textures

Le format de fin de votre lanceur d’application 3D est un fichier. GLB, qui est créé à l’aide du pipeline PBR (rendu physique). Il peut s’agir d’un processus délicat. à présent, nous vous conseillons d’employer un artiste technique si vous ne l’avez pas déjà fait. Si vous êtes un peu vos propres méthodes-er, prenez le temps de [Rechercher et d’apprendre la terminologie du PBR](https://wiki.polycount.com/wiki/PBR) et ce qui se passe en coulisse avant de commencer vous aidera à éviter les erreurs courantes. 

![Exemple : nouvelle application de note](images/pbr-freshnote1-640px-500px.png)<br>
*Exemple de lanceur d’application 3D note (application fictive)*

### <a name="recommended-authoring-tool"></a>Outil de création recommandé

Nous vous recommandons d’utiliser l’outil de création de [substance](https://www.allegorithmic.com/products/substance-painter) par Allegorithmic pour créer votre fichier final. Si vous n’êtes pas familiarisé avec la création de nuanceurs PBR dans l’outil de création de substance, voici un [didacticiel](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(Vous pouvez également utiliser la [couche 3D](https://3dcoat.com/home/), [Quixel suite 2](https://quixel.se/suite2/)ou [marmoset Toolbag](https://www.marmoset.co/toolbag/) si vous êtes plus familiarisé avec l’un d’eux).

### <a name="best-practices"></a>Bonnes pratiques

* Si votre objet de lanceur d’application a été créé pour le PBR, il doit être facile de le convertir pour l’environnement de la maison de la falaise.
* Notre nuanceur attend un flot de travail Metal/grossiste : le nuanceur PBR non réel est une fac-similé de fermeture.
* Lorsque vous exportez vos Textures, gardez à l’esprit les [tailles de texture recommandées](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .
* Veillez à créer vos objets pour l’éclairage en temps réel, à savoir :
  * Évitez les ombres cuites, ou les ombres peintes
  * Éviter l’éclairage cuit dans les textures
  * Utilisez l’un des packages de création de matériel PBR pour obtenir les mappages appropriés générés pour notre nuanceur

## <a name="see-also"></a>Voir aussi

* [Créer des modèles 3D à utiliser dans la réalité mixte](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implémenter des lanceurs d’applications 3D (applications UWP)](implementing-3d-app-launchers.md)
* [Implémenter des lanceurs d’applications 3D (applications Win32)](implementing-3d-app-launchers-win32.md)
