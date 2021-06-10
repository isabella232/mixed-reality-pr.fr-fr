---
title: Couleurs, éclairage et matériaux
description: La conception de contenu pour la réalité mixte nécessite une attention particulière à la couleur, à l’éclairage et à la documentation pour toutes les ressources visuelles.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, Color, Light, Materials, mixed realing casque, Windows Mixed Reality casque, Virtual realer casque, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 2e1626e72d49107c2a83bf1123b306d3ee5c8640
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600358"
---
# <a name="color-light-and-materials"></a>Couleurs, éclairage et matériaux

![Couleur, lumière et matériaux](images/RemoteRendering.jpg)

La conception de contenu pour la réalité mixte nécessite une attention particulière à la couleur, à l’éclairage et à la documentation de toutes vos ressources virtuelles. Des fins esthétiques peuvent inclure l’utilisation de la lumière et du matériau pour définir la tonalité d’un environnement immersif, tandis que les objectifs fonctionnels peuvent inclure des couleurs de frappe pour alerter les utilisateurs d’une action imminente. Chacune de ces décisions doit être pesée par rapport aux opportunités et contraintes de l’appareil cible de votre expérience.

Vous trouverez ci-dessous des instructions spécifiques au rendu des ressources sur les casques immersifs et holographiques. Un grand nombre d’entre eux sont étroitement liés à d’autres domaines techniques et une liste de sujets connexes est disponible dans la section [Voir aussi](color-light-and-materials.md#see-also) à la fin de cet article.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Rendu sur des appareils immersifs et holographiques

Le contenu rendu dans les casques immersifs s’affiche visuellement différent par rapport au contenu rendu dans les casques holographiques. Bien que les casques immersifs affichent généralement le contenu comme vous le feriez sur un écran 2D, les casques holographiques tels que les HoloLens utilisent des couleurs séquentielles, voir les affichages RGB pour afficher les hologrammes.

Prenez toujours le temps de tester vos expériences holographiques dans un casque holographique. L’apparence du contenu, même s’il est conçu spécifiquement pour les appareils holographiques, variera en fonction des analyses secondaires, des instantanés et de la vue spectateur. N’oubliez pas de vous familiariser avec les expériences d’un appareil, de tester l’éclairage des hologrammes et d’observer tous les côtés (ainsi que d’un niveau supérieur ou inférieur) de votre contenu. Veillez à tester avec une plage de paramètres de luminosité sur l’appareil. Il est peu probable que tous les utilisateurs partagent une valeur par défaut supposée et un ensemble diversifié de conditions d’éclairage.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Notions de base du rendu sur les appareils holographiques

* Les **appareils holographiques ont des affichages** supplémentaires : les hologrammes sont créés en ajoutant de la lumière à la lumière à partir du monde réel : le blanc s’affiche vivement, tandis que le noir apparaît en transparence.

* **L’impact des couleurs varie en fonction de l’environnement de l’utilisateur** : il existe de nombreuses conditions d’éclairage différentes dans la salle d’un utilisateur. Créez du contenu avec des niveaux de contraste appropriés pour faciliter la clarté.

* **Évitez l’éclairage dynamique** : les hologrammes qui sont allumés uniformément dans les expériences holographiques sont les plus efficaces. L’éclairage dynamique est susceptible de dépasser les capacités des appareils mobiles. Lorsque l’éclairage dynamique est requis, il est recommandé d’utiliser le [nuanceur standard Mixed Reality Toolkit standard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md). 

## <a name="designing-with-color"></a>Conception avec couleur

En raison de la nature des affichages additifs, certaines couleurs peuvent apparaître différentes sur les affichages holographiques. Certaines couleurs s’affichent dans les environnements d’éclairage, tandis que d’autres sont moins impactables. Les couleurs froides ont tendance à être remplacées en arrière-plan, tandis que les couleurs chaudes sautent au premier plan. Tenez compte de ces facteurs lorsque vous explorez les couleurs dans vos expériences :

* **Rendu des couleurs claires** -blanc semble lumineux et doit être utilisé avec modération. Dans la plupart des cas, envisagez une valeur blanche autour de R 235 G 235 B 235. Les grandes zones lumineuses peuvent entraîner une gêne pour l’utilisateur. Pour la boîte de l’interface utilisateur, il est recommandé d’utiliser des couleurs sombres.

* **Rendu des couleurs sombres** -en raison de la nature des affichages additifs, les couleurs sombres apparaissent transparentes. Un objet noir Uni n’est pas différent du monde réel. Voir canal alpha ci-dessous. Pour obtenir l’apparence de « noir », essayez une valeur RVB grise très sombre, telle que 16, 16, 16.

* **Uniformité des couleurs** -en général, les hologrammes sont rendues suffisamment brillants pour maintenir l’uniformité des couleurs, quel que soit l’arrière-plan. Les grandes zones peuvent devenir nettes. Évitez les grandes zones de couleur lumineuse et unie.

* La **gamme** -HoloLens bénéficie d’une « gamme étendue » de couleurs, conceptuellement similaire à Adobe RGB. Par conséquent, certaines couleurs peuvent afficher différentes qualités et représentations dans l’appareil.

* **Gamma** : la luminosité et le contraste de l’image rendue varient en fonction des appareils immersifs et holographiques. Ces différences d’appareils semblent souvent faire apparaître des zones sombres de couleur et des ombres, plus ou moins lumineuses.

* **Séparation** des couleurs : également appelée « répartition des couleurs » ou « frange des couleurs », la séparation des couleurs se produit le plus souvent avec des hologrammes mobiles (y compris le curseur) quand un utilisateur effectue le suivi des objets avec leurs yeux.

## <a name="technical-considerations"></a>Considérations techniques

* **Alias** : Tenez compte des alias, des étapes en escalier ou des « étapes d’escalier » où le bord de la géométrie d’un hologramme répond au monde réel. L’utilisation de textures avec des détails élevés peut aggraver cet effet. Les textures doivent être mappées et le filtrage activé. Envisagez de faire déborder les bords des hologrammes ou d’ajouter une texture qui crée une bordure noire autour des objets. Évitez la géométrie fine lorsque cela est possible.

* **Canal alpha** : vous devez effacer votre canal alpha pour qu’il soit entièrement transparent pour les parties où vous n’affichez pas d’hologramme. Si vous laissez la valeur alpha non définie, les artefacts visuels sont pris en charge lors de la création d’images/de vidéos à partir de l’appareil ou de la vue spectateur.

* **Adoucissement des textures** : dans la mesure où la lumière est additive dans les affichages holographiques, il est préférable d’éviter les grandes zones de couleur lumineuse et unie, car elles ne produisent souvent pas l’effet visuel souhaité.

## <a name="design-guidelines-for-holographic-display"></a>Instructions de conception pour l’affichage holographique

![Occlusion des couleurs et des mains](images/color_handocclusion.jpg)

Lorsque vous concevez du contenu pour des affichages holographiques, vous devez prendre en compte plusieurs éléments pour obtenir la meilleure expérience possible. Pour obtenir des instructions et des recommandations, consultez [conception de contenu pour l’affichage holographique](designing-content-for-holographic-display.md) .

## <a name="storytelling-with-light-and-color"></a>Narration avec lumière et couleur

Le clair et la couleur permettent de faire apparaître vos hologrammes plus naturellement dans l’environnement d’un utilisateur et offrent des conseils et de l’aide pour l’utilisateur. Pour les expériences holographiques, tenez compte de ces facteurs lorsque vous explorez l’éclairage et la couleur :

:::row:::
    :::column:::
* **Vignette** : l’effet « vignette » sur les matériaux obscurcis peut aider à attirer l’attention de l’utilisateur sur le centre du champ de l’affichage. Cet effet assombrit le matériau de l’hologramme à un rayon à partir du vecteur de pointage de l’utilisateur. Cela est également efficace lorsque l’utilisateur affiche des hologrammes à partir d’un angle oblique ou parcourant.

* **Accentuation** : attirez l’attention sur les objets ou les points d’interaction en contrastant les couleurs, la luminosité et l’éclairage. Pour plus d’informations sur les méthodes d’éclairage dans le récits, consultez [pixels cinématographiques-approche d’éclairage pour les images informatiques](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Image : utilisation de la couleur pour mettre en évidence les éléments de narration, présentés ici dans une scène à partir de [fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*
    :::column-end:::
        :::column:::
        ![Utilisation de la couleur pour mettre en évidence les éléments de narration, indiqués ici dans une scène à partir de fragments.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Matériaux

:::row:::
    :::column:::
Les matériaux sont des éléments essentiels pour créer des hologrammes réalistes. En fournissant des caractéristiques visuelles appropriées, vous pouvez créer des objets holographiques attrayants qui peuvent être correctement mélangés avec l’environnement physique. Les matériaux sont également importants pour fournir des commentaires visuels sur les différents types d’interactions utilisateur en entrée.  

[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fournit un nuanceur standard MRTK avec diverses options d’effet visuel qui peuvent être utilisées pour les commentaires visuels. Par exemple, vous pouvez utiliser la propriété « proximite Light » pour fournir un effet d’éclairage lorsque le doigt de l’utilisateur approche la surface de l’objet. En savoir plus sur le [nuanceur standard MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *Boucle vidéo : exemple de retour visuel basé sur la proximité d’un cadre* 
     ![ englobant Commentaires visuels à proximité](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Voir aussi
* [Conception de contenu pour un affichage holographique](designing-content-for-holographic-display.md)
* [Séparation des couleurs](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Hologrammes](../discover/hologram.md)
* [Langue de design Microsoft-couleur](https://www.microsoft.com/design/color)
* [plateforme Windows universelle couleur](/windows/uwp/style/color)