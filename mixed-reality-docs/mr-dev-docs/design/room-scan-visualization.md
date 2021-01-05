---
title: Visualisation du balayage d’une pièce
description: Les applications qui requièrent le mappage spatial utilisent l’appareil pour collecter des données dans le temps et entre les sessions.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, modèles d’application, conception, HoloLens, Scan Room, mappage spatial, maille, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, HoloLens
ms.openlocfilehash: f4ec072c8fde8d3e7e390bd837116a8262bac38b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848252"
---
# <a name="room-scan-visualization"></a>Visualisation du balayage d’une pièce

Les applications qui requièrent un mappage spatial s’appuient sur l’appareil pour collecter des données au fil du temps et entre les sessions. L’exhaustivité et la qualité des données de mappage dépendent de nombreux facteurs, notamment la quantité d’exploration effectuée par l’utilisateur, le temps écoulé depuis l’exploration et si les objets tels que les meubles et les portes ont été déplacés depuis que l’appareil a analysé la zone.

Pour garantir l’utilité des données de mappage spatiale, les développeurs d’applications disposent de plusieurs options :
* S’appuyer sur ce qui a déjà été collecté. Ces données peuvent être incomplètes au départ.
* Demandez à l’utilisateur d’utiliser le geste fleuri pour accéder à la page d’hébergement Windows Mixed Reality, puis explorez la zone qu’il souhaite utiliser pour l’expérience. Ils peuvent utiliser l’utilisation de l’air pour confirmer que toutes les zones nécessaires sont connues de l’appareil.
* Créez une expérience d’exploration personnalisée dans leur propre application.

Dans tous ces cas, les données réelles recueillies lors de l’exploration sont stockées par le système et l’application n’a pas besoin de le faire.

## <a name="device-support"></a>Prise en charge des appareils

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Fonctionnalité</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
    </tr>
     <tr>
        <td>Visualisation du balayage d’une pièce</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Création d’une expérience d’analyse personnalisée

Les applications peuvent analyser les données de mappage spatiale au début de l’expérience afin de déterminer si elles souhaitent que l’utilisateur effectue des étapes supplémentaires pour améliorer son exhaustivité et sa qualité. Si l’analyse indique que la qualité doit être améliorée, les développeurs doivent fournir une visualisation à superposer au monde pour indiquer :
* La quantité totale de volume total des utilisateurs avoisinants doit faire partie de l’expérience
* Emplacement où l’utilisateur doit accéder à l’amélioration des données

Les utilisateurs ne savent pas ce qui effectue une « bonne » analyse. Ils doivent être affichés ou informés des éléments à rechercher s’ils sont invités à évaluer une analyse, à la distance, à la distance par rapport aux murs réels, etc. Le développeur doit implémenter une boucle de commentaires qui comprend l’actualisation des données de mappage spatiale pendant la phase d’analyse ou d’exploration.

Dans de nombreux cas, il est préférable d’indiquer à l’utilisateur ce qu’il doit faire pour obtenir la qualité d’analyse nécessaire. Par exemple, Regardez le plafond, regardez derrière le mobilier, et ainsi de suite.

## <a name="cached-versus-continuous-spatial-mapping"></a>Mise en cache et mappage spatial continu

Les données de mappage spatiale sont les applications de source de données les plus lourdes pouvant être consommées. Pour éviter des problèmes de performances, tels que des images ignorées ou des interruptions, la consommation de ces données doit être effectuée avec précaution.

L’analyse active au cours d’une expérience peut être à la fois bénéfique et néfaste. vous devrez donc décider de la méthode à utiliser en fonction de l’expérience.

### <a name="cached-spatial-mapping"></a>Mappage spatial mis en cache

Si des données de mappage spatiale sont mises en cache, l’application prend généralement un instantané des données de mappage spatiale et utilise cet instantané pendant l’expérience.

**Avantages**
* Réduction de la surcharge sur le système pendant que l’expérience s’exécute et entraîne des gains de performances spectaculaires en matière d’alimentation, de température et d’UC.
* Une implémentation plus simple de l’expérience principale, car elle n’est pas interrompue par les modifications apportées aux données spatiales.
* Un coût unique à un moment donné sur tout traitement de la publication des données spatiales à des fins physiques, graphiques et autres.

**Inconvénients**
* Le déplacement d’objets ou de personnes réels n’est pas reflété par les données mises en cache. par exemple, l’application peut considérer une porte ouverte lorsqu’elle est maintenant fermée.
* Potentiellement plus de mémoire d’application pour gérer la version mise en cache des données.

Une bonne casse pour cette méthode est un environnement contrôlé ou un jeu en haut de la table.

### <a name="continuous-spatial-mapping"></a>Mappage spatial continu

Certaines applications peuvent reposer sur poursuivre l’analyse pour actualiser les données de mappage spatiale.

**Avantages**
* Vous n’avez pas besoin de créer une expérience d’analyse ou d’exploration distincte dans votre application.
* Le déplacement d’objets réels peut être reflété par le jeu, bien qu’avec un certain délai.

**Inconvénients**
* Plus grande complexité dans l’implémentation de l’expérience principale.
* Surcharge potentielle due au graphique supplémentaire et au traitement physique, puisque les modifications doivent être ingérées de manière incrémentielle par ces systèmes.
* Impact plus élevé, thermique et processeur.

Un bon cas pour cette méthode est celui où les hologrammes sont censés interagir avec les objets mobiles, par exemple, une voiture holographique dont les lecteurs sont susceptibles d’être amenés dans une porte, selon qu’elle est ouverte ou fermée.

## <a name="see-also"></a>Voir aussi

* [Mappage spatial](spatial-mapping.md)
* [Systèmes de coordonnées](coordinate-systems.md)
* [Conception du son spatial](spatial-sound-design.md)
