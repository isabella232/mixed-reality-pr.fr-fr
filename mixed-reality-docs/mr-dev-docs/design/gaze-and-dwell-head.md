---
title: Suivre de la tête et stabiliser
description: Prise en main d’une vue d’ensemble du modèle d’entrée du point de vue et du point d’entrée, y compris les scénarios courants et les principes de conception.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: mi-vie mixte, point de vue, interaction, conception, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, Shared Computer Toolkit de réalité mixte, expérience utilisateur, indications, mode liste
ms.openlocfilehash: e069b0815f69848b7632cb7b1b85d85f328441b7156ae22ffe097fedc3ed6fc1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223618"
---
# <a name="head-gaze-and-dwell"></a>Suivre de la tête et stabiliser

Quand les mains sont occupées avec des outils et des pièces, les mouvements peuvent être fastidieux, voire impossibles. Les commandes vocales, à l’image des mouvements, peuvent être incertaines dans des contextes donnés, par exemple dans des conditions très bruyantes. En outre, l’utilisation de la voix pour contrôler les ordinateurs n’est pas universellement courante, mais elle est certainement en train de s’intensifier ! Le modèle Suivre de la tête et stabiliser offre le mécanisme le plus familier et le plus facile à maîtriser pour travailler sur HoloLens tête relevée et mains libres. De plus, ce modèle est fiable à 100 % ; il n’est pas sensible aux interférences sonores et ne demande pas le silence dans l’environnement.

## <a name="scenarios"></a>Scénarios

Le point de regard et le front-tête est parfait dans les scénarios où les mains d’une personne sont occupées par d’autres tâches. Cette fonctionnalité est également utile lorsque la voix n’est pas 100% fiable ou disponible en raison de contraintes environnementales ou sociales. Un bon exemple est une personne portant un appareil HoloLens pour superposer des informations de référence tout en réparant un moteur de voiture. Ses mains sont occupées par des outils ou supportent son corps quand elle se penche dans le compartiment du moteur. L’espace du garage est bruyant, les coups et bourdonnement constants des outils rendant difficile l’utilisation de commandes vocales. le point de regard et le point de vue permet à la personne qui utilise le HoloLens de parcourir en toute confiance son document de référence sans interrompre son flux de travail. 

## <a name="device-support"></a>Prise en charge des appareils

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modèle d’entrée</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
    </tr>
     <tr>
        <td>Suivre de la tête et stabiliser</td>
        <td>✔️ Recommandé</td>
        <td>✔️ Recommandé</td>
        <td>✔️ Recommandé</td>
    </tr>
</table>


## <a name="design-principles"></a>Principes de conception

**Éviter le « pointage du regard comme une arme »**

Pour être intuitif, le modèle Suivre de la tête et stabiliser nécessite un retour visuel, mais trop de retour peut engendrer de l’anxiété. Les commentaires doivent permettre à un utilisateur de savoir ce qu’il cible, mais pas de le sélectionner à son intention. Lors de la lecture de texte, d’icônes et d’étiquettes, vous devez fournir aux utilisateurs l’heure d’absorber les informations avant de les sélectionner.
    
**Rechercher la vitesse idéale**
    
Les interactions avec stabilisation peuvent avoir différentes durées en fonction de l’impact de la navigation : les fonctions plus fréquemment utilisées bénéficient généralement de temps de remplissage plus rapides, tandis que les fonctions plus conséquentes peuvent bénéficier de temps de remplissage plus longs. Quand vous utilisez un effet de remplissage pour afficher ces durées, les courbes d’animation de la couleur de remplissage peuvent engendrer un sentiment positif de temps de remplissage plus rapides. Vous devez envisager de laisser à l’utilisateur la possibilité de choisir la vitesse de remplissage (rapide, moyenne, lente).
    
**Éviter l’effet yo-yo**

L’effet yo-yo est un modèle de déplacement de la tête qui se produit lorsque les contrôles placement du contenu et point-Orient/logement forcent les utilisateurs à effectuer des recherches à plusieurs reprises. Par exemple, un point de la liste avec le bouton de tête et de pointage en haut en bas de la liste donne une boucle de-regarde vers le bas, recherche les résultats, regarde jusqu’à l’arrière, et ainsi de suite. Le modèle résultant n’est pas à l’aise. nous vous recommandons donc de placer les contrôles de navigation dans un emplacement centralisé qui nécessite moins d’arrière-plan. Le positionnement des boutons de logement en fonction de leurs effets devient important pour le confort.
s
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>Recommandations et bonnes pratiques pour l’expérience utilisateur

### <a name="target-sizes"></a>Taille des cibles

Pour être facilement accessibles, les cibles du point de vue et du regard doivent être suffisamment grandes pour regarder confortablement et maintenir une tête stable sur la cible pour le temps imparti. Nous vous recommandons une taille de cible minimale de 2 degrés pour obtenir l’expérience la plus confortable. 

### <a name="visual-feedback"></a>Retour visuel

Quand vous utilisez un remplissage radial pour représenter la durée de stabilisation, démarrez à partir du centre du bouton. Une réponse cohérente est plus claire que toutes les directions différentes sur les différents boutons. 

  * Toutefois, cette règle peut être interrompue pour les interactions directionnelles (par exemple, navigation vers le haut/vers le haut/gauche/droite, etc.). Par exemple, Microsoft Dynamics 365 Guides fait une exception pour SUIVANT/PRECEDENT qui correspond aux remplissages gauche et droite.
  * Envisagez d’inverser le remplissage radial à partir de l’extérieur, pour des scénarios tels que le basculement d’un bouton. Le sentiment inverse d’appui sur un bouton est un schéma visuel agréable à conserver. 

### <a name="progressive-disclosure"></a>Affichage progressif

L’affichage progressif consiste à n’afficher que les informations pertinentes à chaque étape d’une interaction. Pour le son, cela signifie que la cible du logement est révélée en surbrillance (par exemple, dans un contrôle de liste).

 ### <a name="oversized-targets"></a>Cibles trop grandes

La région de stabilisation peut être plus grande que l’icône à l’état inactif pour faciliter son utilisation, comme le bouton Précédent dans Microsoft Dynamics 365 Guides.

### <a name="prevent-flickering-with-delayed-feedback"></a>Éviter le scintillement avec un retour décalé

Utilisez un court délai avant de démarrer le retour visuel afin d’éviter le scintillement quand l’utilisateur passe au-dessus d’une cible de stabilisation.
* Pour les boutons qui sont interactifs fréquemment, conservez le délai pour que l’application soit réactive.
* Pour les boutons qui sont interactifs rarement, un délai plus long peut être approprié pour éviter que l’interface twitchy.

<br>

---

## <a name="ui-patterns"></a>Schémas de l’interface utilisateur

### <a name="high-frequency-buttons"></a>Boutons à haute fréquence

:::row:::
    :::column:::
        Les boutons à fréquence élevée sont des boutons utilisés couramment dans une application. Les boutons Suivant et Précédent dans Microsoft Dynamics 365 Guides constituent un bon exemple.<br>
        <br>
        **Recommandations**<br>
  * Les boutons à fréquence élevée doivent être volumineux, plus faciles à toucher avec le regard
  * Restez près de la hauteur pour éviter les tensions ergonomiques.<br>
        <br>
*Image : Microsoft Dynamics 365 Guides bouton suivant*
    :::column-end:::
        :::column:::
       ![bouton suivant de Microsoft Dynamics 365 Guides](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Boutons à fréquence faible

Les boutons à basse fréquence sont des boutons qui ne sont pas interactifs avec comme régulièrement dans l’application. À titre d’exemple, citons un bouton permettant d’accéder à un menu de paramètres ou d’effacer la totalité du travail.

* Dans la mesure du possible, maintenez ces boutons hors du chemin emprunté par les suivis de la tête afin d’éviter une activation accidentelle. 

<br>

---

### <a name="confirmations"></a>Confirmations

:::row:::
    :::column:::
        Lorsqu’une action a un impact significatif, comme le chargement de l’argent, la suppression d’un travail ou le démarrage d’un processus long, il est utile de confirmer qu’une personne est censée sélectionner un bouton.<br>
        <br>
        **Recommandations**<br>
  * Afficher la surbrillance de la sélection sur le bouton principal
  * Révéler la cible de stabilisation en même temps que la surbrillance de la sélection
  * Pour le bouton secondaire, révéler la cible de stabilisation en fonction du suivi de la tête<br>
        <br>
*Image : boîte de dialogue de confirmation de Microsoft Dynamics 365 Guides*
    :::column-end:::
        :::column:::
       ![boîte de dialogue de Confirmation de Microsoft Dynamics 365 Guides](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Boutons bascule

Les boutons bascule nécessitent une logique nuancée pour fonctionner correctement. Quand une personne se trouve sur un bouton bascule et l’active, elle doit quitter le bouton, puis revenir au redémarrage de la logique du logement. Il est important que les boutons bascule présentent l’état actif et inactif. 

<br>

---

### <a name="list-views"></a>Affichages de liste

:::row:::
    :::column:::
        Les affichages de liste présentent un défi particulier pour les entrées de point de vue et de point d’entrée. Les utilisateurs peuvent analyser le contenu sans avoir à vous Tiptoe autour des cibles du logement.<br>
        <br>
**Recommandations**<br>
  * Faites en sorte que la totalité de la ligne surbrille quand la tête est en regard, mais ne commence pas, sauf si le point de regard se trouve sur la cible d’un logement spécifique.
  * Affichez uniquement la cible d’un logement lorsque la ligne est mise en surbrillance pour réduire le bruit visuel.
  * Soyez clair et cohérent avec la position des cibles du logement.
  * N’affichez pas toutes les cibles de logement à la fois pour éviter l’interface utilisateur répétitive.
  * Réutilisez le même modèle aussi souvent que possible pour établir une familiarité avec l’expérience utilisateur.<br>
        <br>
*Image : liste de Dynamics 365 Guides Microsoft*
    :::column-end:::
        :::column:::
       ![liste des Dynamics 365 Guides Microsoft](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Voir aussi

* [Pointer et valider](gaze-and-commit.md)
* [Mains : Manipulation directe](direct-manipulation.md)
* [Mains : Mouvements](gaze-and-commit.md#composite-gestures)
* [Mains : Pointer et valider](point-and-commit.md)
* [Interactions instinctuelles](interaction-fundamentals.md)
* [Entrée vocale](voice-input.md)