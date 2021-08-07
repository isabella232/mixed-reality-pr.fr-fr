---
title: Tableau périodique des éléments
description: Découvrez comment disposer un tableau d’objets dans l’espace 3D avec différents types de surface à l’aide d’une collection d’objets avec la table périodique de l’exemple d’application d’éléments.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, exemple d’application, contrôles, MRTK, Shared Computer Toolkit de réalité mixte, unity, exemples d’applications, exemples d’applications, open source, Microsoft Store, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: aab6789939823b8c6e200bb5456118002b848e3c2f166abe50d4788ac8e7430d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211884"
---
# <a name="periodic-table-of-the-elements"></a>Tableau périodique des éléments
![Table period de l’application Elements](../images/MRDL_PeriodicTable_HL1.jpg)

>[!NOTE]
>Cet article présente un exemple exploratoire que nous avons créé dans les [laboratoires de conception de réalité mixte](https://github.com/Microsoft/MRDesignLabs_Unity), un endroit où nous partageons nos connaissances et des suggestions concernant le développement d’applications de réalité mixte. Nos articles et code liés à la conception évoluent à mesure que nous effectuons de nouvelles découvertes.

>[!NOTE]
>cet exemple d’application a été conçu pour HoloLens 1ère génération. consultez [la Table périodique des éléments 2,0](periodic-table-of-the-elements-2.md) pour HoloLens 2 version.

[La table périodique des éléments](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) est un exemple d’application open source des laboratoires de conception de la réalité mixte de Microsoft. Découvrez comment disposer un tableau d’objets dans l’espace 3D avec différents types de surface à l’aide d’une **[collection d’objets](../../design/object-collection.md)**. Découvrez également comment créer des objets interactifs qui répondent aux entrées standard de HoloLens. Vous pouvez utiliser les composants de ce projet pour créer votre propre expérience d’application de réalité mixte.


## <a name="demo-video"></a>Vidéo de démonstration 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

enregistré avec HoloLens 2 à l’aide de la Capture de réalité mixte

## <a name="about-the-app"></a>À propos de l’application

La table périodique des éléments visualise les éléments chimiques et chacune de leurs propriétés dans un espace 3D. il intègre les interactions de base de HoloLens telles que le robinet et le robinet d’air. Les utilisateurs peuvent en savoir plus sur les éléments avec des modèles 3D animés. Ils peuvent comprendre visuellement le shell électron d’un élément et son noyau, qui est composé de protons et de neutrons.

## <a name="background"></a>Contexte

une fois que j’ai rencontré HoloLens, je savais que je voulais expérimenter une application de table périodique en réalité mixte. Étant donné que chaque élément a de nombreux points de données qui s’affichent avec du texte, j’ai pensé qu’il serait intéressant d’explorer la composition typographique dans un espace 3D. Donner aux utilisateurs la possibilité de visualiser le modèle d’électrons de l’élément était une autre partie intéressante de ce projet.

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

l’objet pouvant être [interagi](../../design/interactable-object.md) est un objet, qui peut répondre aux entrées de base HoloLens. Il est fourni en tant que Prefab/script, que vous pouvez facilement appliquer à n’importe quel objet. Par exemple, vous pouvez rendre une tasse de café dans votre scène interactive et répondre à des entrées telles que le pointage, le toucher, la navigation et les gestes de manipulation. [En savoir plus](../../design/interactable-object.md)

![objet nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Collection d’objets

La [collection d’objets](../../design/object-collection.md) est un objet, qui vous permet de disposer plusieurs objets dans différentes formes. Il prend en charge les plans, les cylindres, les sphères et les nuages de points. Vous pouvez configurer des propriétés supplémentaires telles que le rayon, le nombre de lignes et l’espacement. [En savoir plus](../../design/object-collection.md)

![Collection d’objets](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Détails techniques

Vous pouvez trouver des scripts et des prefabs pour la table périodique de l’application des éléments sur les laboratoires de conception de la [réalité mixte GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Portage de l’histoire de HoloLens 2

lisez l’article sur la façon dont la Table périodique de l’application d’éléments a été mise à jour avec les interactions instinctual de HoloLens 2.

[Tableau périodique des éléments 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>À propos de l’auteur

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Parc Yoon</b></a><br>Concepteur d’expérience utilisateur @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Voir aussi

* [Hub d’exemples MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(téléchargement à partir du Microsoft Store dans HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tableau périodique des éléments 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)