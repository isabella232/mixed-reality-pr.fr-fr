---
title: Tablette
description: Documentation sur la ardoise dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, ardoise,
ms.openlocfilehash: 6bc1f18c71367ce05aadae0ff3f8aa51fd17d10c943022525fc5043d8d7989a2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224022"
---
# <a name="slate"></a>Tablette

![Tablette](../images/slate/MRTK_Slate_Main.png)

Le Prefab ardoise offre un contrôle de style de fenêtre fine permettant d’afficher le contenu 2D, par exemple du texte brut ou des articles, y compris des médias. Il offre une barre de titre, ainsi que des fonctionnalités de *suivi* et de *fermeture* . Vous pouvez faire défiler la fenêtre de contenu via une entrée articulée.

## <a name="how-to-use-a-slate-control"></a>Utilisation d’un contrôle ardoise

Un contrôle ardoise est composé des éléments suivants :

* **TitleBar**: barre de titre entière au-dessus de la tablette.
* **Title**: zone de titre sur le côté gauche de la barre de titre.
* **Boutons**: zone de bouton à droite de la barre de titre.
* **Replaque**: le côté arrière de la tablette.
* **ContentQuad**: le contenu est affecté en tant que matériau. L’exemple utilise un exemple de matériau « PanContent ».

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>Contrôle des limites

Un contrôle ardoise contient un script de contrôle de limites pour la mise à l’échelle et la rotation. Pour plus d’informations sur le contrôle des limites, consultez la page [contrôle des limites](bounds-control.md) .

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>Boutons

Un ardoise standard offre deux boutons comme valeur par défaut en haut à droite de la barre de titre :

* **Suivre**: bascule les composants du solveur orbital pour que l’objet ardoise suive l’utilisateur.
* **Fermer**: désactive l’objet de la ardoise.

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>scripts ;

En général, le `NearInteractionTouchable.cs` script doit être attaché à tout objet destiné à recevoir des événements tactiles à partir du `IMixedRealityTouchHandler` .

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs` Ce script gère l’entrée articulée pour toucher et déplacer le contenu sur le *ContentQuad* de la ardoise.

* `HandInteractionPanZoom.cs`: En plus de l’interaction de panoramique, ce script prend en charge le zoom à deux mains.

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
