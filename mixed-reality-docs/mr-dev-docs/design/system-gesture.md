---
title: Mouvement associé au menu Démarrer
description: découvrez comment utiliser le geste démarrer pour appeler le Menu démarrer sur HoloLens et Windows Mixed Reality des casques immersifs.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: réalité mixte, gestes, interaction, conception, casque de réalité mixte, casque windows mixed realisation, casque de réalité virtuelle, HoloLens, MRTK, Shared Computer Toolkit de réalité mixte, fleuri
ms.openlocfilehash: f3ad9309c7232f20a25060b1d98d7374272ceea00f24be18d7263b8ec7002fb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213738"
---
# <a name="start-gesture"></a>Mouvement associé au menu Démarrer

Le mouvement de début est un mouvement manuel utilisé pour appeler le menu Démarrer. cela revient à appuyer sur la touche Windows sur les claviers, le bouton xbox sur les contrôleurs xbox ou le bouton Windows sur les contrôleurs de mouvement du casque immersif. Portez une attention particulière aux gestes système réservés sur chaque appareil de réalité mixte pour éviter les conflits lors de la conception d’interactions.

## <a name="device-support"></a>Prise en charge des appareils

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Fonctionnalité</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
    </tr>
     <tr>
        <td>Bourgeon</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Bouton de poignet</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Pince œil et poignet</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Bourgeon

nous avons conçu « fleuri » pour afficher le menu démarrer dans HoloLens (1ère génération), qui est un geste symbolique imitant une fleur florale. Il est propre à l’interaction à l’aide des pieds de page, facile à utiliser et facile à rappeler. Pour utiliser le geste, tenez votre main avec votre paume, puis ouvrez votre main en répartissant vos doigts.

:::row:::
    :::column:::
        ![Fermeture de la fleur](images/bloom-close.png)<br>
        **Étape 1 : palmier avec les doigts**<br>
    :::column-end:::
    :::column:::
        ![Ouverture de fleurs](images/bloom-open.png)<br>
        **Étape 2 : créer une planche à portée de main**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Mouvement associé au menu Démarrer

dans HoloLens 2, nous avons remplacé le geste fleuri par un bouton de poignet virtuel qui est plus instinctual pour les utilisateurs. En présentant les utilisateurs du bouton sur le poignet, ils peuvent accéder de manière intuitive et appuyer dessus.

:::row:::
    :::column:::
        ![Bouton de poignet prêt](images/wrist-button-ready.png)<br>
        **Étape 1 : palmier pour montrer le bouton de poignet**<br>
    :::column-end:::
    :::column:::
        ![Appui sur le bouton du poignet](images/wrist-button-press.png)<br>
        **Étape 2 : Appuyez sur le bouton du poignet**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Mouvement d’une main associé au menu Démarrer

> [!IMPORTANT]
> Pour que le mouvement associé au menu Démarrer fonctionne :
>
> 1. Vous devez installer la mise à jour de novembre 2019 (Build 18363.1039) ou ultérieure.
> 1. Vos yeux doivent être étalonnés sur l’appareil pour permettre le bon fonctionnement du suivi visuel. Si vous ne voyez pas les points en orbite autour de l’icône Démarrer lorsque le regardez, cela signifie que vos yeux ne sont pas étalonnés sur l’appareil.

Vous pouvez également utiliser le mouvement Start avec une seule main. Tenez votre main avec votre paume et regardez l' **icône de démarrage** sur votre poignet interne. **Sans quitter l’icône des yeux**, resserrez le pouce et l’index.<br>
:::row:::
    :::column:::
        ![Bouton de poignet prêt](images/wrist-button-ready.png)<br>
        **Étape 1 : palmier pour montrer le bouton de poignet**<br>
    :::column-end:::
    :::column:::
        ![Pince à bouton de poignet](images/wrist-button-pinch.png)<br>
        **Étape 2 : attirez le regard sur le bouton, puis pincez**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Voir aussi

* [Interactions instinctuelles](interaction-fundamentals.md)
* [Œil-point de regard](eye-tracking.md)
* [Entrée vocale](voice-input.md)