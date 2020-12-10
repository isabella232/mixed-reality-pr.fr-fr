---
title: Tableau périodique des éléments
description: La table périodique des éléments est un exemple d’application open source des laboratoires de conception de la réalité mixte de Microsoft. Découvrez comment composer un tableau d’objets dans l’espace 3D avec différents types de surface à l’aide d’une collection d’objets.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, exemple d’application, contrôles, MRTK, kit de préversion de réalité mixte, Unity, exemples d’applications, exemples d’applications, open source, Microsoft Store, HoloLens, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: a4099c889fee886e63d3a8b773398a250621f26e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010180"
---
# <a name="periodic-table-of-the-elements"></a>Tableau périodique des éléments

>[!NOTE]
>Cet article présente un exemple exploratoire que nous avons créé dans les [laboratoires de conception de réalité mixte](https://github.com/Microsoft/MRDesignLabs_Unity), un endroit où nous partageons nos connaissances et des suggestions concernant le développement d’applications de réalité mixte. Nos articles et code liés à la conception évoluent à mesure que nous effectuons de nouvelles découvertes.

[La table périodique des éléments](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) est un exemple d’application open source des laboratoires de conception de la réalité mixte de Microsoft. Découvrez comment disposer un tableau d’objets dans l’espace 3D avec différents types de surface à l’aide d’une **[collection d’objets](../../design/object-collection.md)**. Découvrez également comment créer des objets interactifs qui répondent aux entrées standard de HoloLens. Vous pouvez utiliser les composants de ce projet pour créer votre propre expérience d’application de réalité mixte.

![Table period de l’application Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>Vidéo de démonstration 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Enregistré avec HoloLens 2 à l’aide de la capture de réalité mixte

## <a name="about-the-app"></a>À propos de l’application

La table périodique des éléments visualise les éléments chimiques et chacune de leurs propriétés dans un espace 3D. Il intègre les interactions de base de HoloLens, telles que le toucher et l’air. Les utilisateurs peuvent en savoir plus sur les éléments avec des modèles 3D animés. Ils peuvent comprendre visuellement le shell électron d’un élément et son noyau, qui est composé de protons et de neutrons.

## <a name="background"></a>Arrière-plan

Une fois que je me suis familiarisé avec HoloLens, je savais que je voulais expérimenter une application de table périodique en réalité mixte. Étant donné que chaque élément a de nombreux points de données qui s’affichent avec du texte, j’ai pensé qu’il serait intéressant d’explorer la composition typographique dans un espace 3D. Donner aux utilisateurs la possibilité de visualiser le modèle d’électrons de l’élément était une autre partie intéressante de ce projet.

## <a name="design"></a>Conception

Pour la vue par défaut de la table périodique, j’ai imaginé des cases tridimensionnelles qui contiennent le modèle d’électrons de chaque élément. La surface de chaque zone est translucide afin que l’utilisateur puisse obtenir une idée approximative du volume de l’élément. Lorsque vous appuyez sur le regard et l’air, l’utilisateur peut ouvrir une vue détaillée de chaque élément. Pour effectuer la transition entre la vue de table et l’affichage détaillé en douceur et en naturel, j’ai fait de la même façon que l’interaction physique d’une ouverture de Box dans la vie réelle.

![Concevoir l’esquisse](images/640px-sketch20170406.jpg)<br>
*Concevoir des croquis*

En mode Détails, je voulais visualiser les informations de chaque élément avec un rendu impeccable du texte dans l’espace 3D. Le modèle d’électrons 3D animé est affiché dans la zone centrale et peut être affiché à partir de différents angles.

![Interaction](images/640px-periodictable-interaction.jpg)

![Prototypes](images/640px-periodictable-prototypes.jpg)<br>
*Prototypes d’interaction*

L’utilisateur peut modifier le type de surface par air en appuyant sur les boutons situés en bas du tableau : il peut basculer entre les plans, les cylindres, les sphères et les nuages de points.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Contrôles et modèles communs utilisés dans cette application

### <a name="interactable-object-button"></a>Objet interagiable (bouton)

L’objet qui peut être [interagi](../../design/interactable-object.md) est un objet, qui peut répondre aux entrées HoloLens de base. Il est fourni en tant que Prefab/script, que vous pouvez facilement appliquer à n’importe quel objet. Par exemple, vous pouvez rendre une tasse de café dans votre scène interactive et répondre à des entrées telles que le pointage, le toucher, la navigation et les gestes de manipulation. [En savoir plus](../../design/interactable-object.md)

![objet nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Collection d’objets

La [collection d’objets](../../design/object-collection.md) est un objet, qui vous permet de disposer plusieurs objets dans différentes formes. Il prend en charge les plans, les cylindres, les sphères et les nuages de points. Vous pouvez configurer des propriétés supplémentaires telles que le rayon, le nombre de lignes et l’espacement. [En savoir plus](../../design/object-collection.md)

![Collection d’objets](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Détails techniques

Vous trouverez scripts and prefabs pour la table Periodic de l’application Elements sur le GitHub de conception de la [réalité mixte](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Portage de l’histoire pour HoloLens 2

Lisez l’article sur la façon dont la table périodique de l’application d’éléments a été mise à jour avec les interactions instinctual de HoloLens 2.

[Tableau périodique des éléments 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>À propos de l’auteur

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Concepteur d’expérience utilisateur @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Voir aussi

* [Hub d’exemples MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tableau périodique des éléments 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)