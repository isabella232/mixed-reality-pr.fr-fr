---
title: Utilitaire de capture d’écran
description: Documentation sur l’utilisation de l’outil de capture d’écran dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f3e06258f49ca01b37872b9ee462be7fc68651f9ef379ba2d66bb4e9e2796463
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221431"
---
# <a name="screenshot-utility"></a>Utilitaire de capture d’écran

La prise de captures d’écran dans Unity pour la documentation et les images promotionnelles peut souvent être fastidieuse, et le résultat rarement convaincant. C’est là que la classe `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) entre en jeu.

La classe ScreenshotUtility vous permet de prendre des captures d’écran via des éléments de menu et des API publiques dans l’éditeur Unity. Les captures d’écran peuvent être prises dans différentes résolutions et avec des couleurs claires transparentes pour être utilisées dans la composition simple d’images. La prise de captures d’écran depuis une build autonome n’est pas prise en charge par cet outil.

## <a name="taking-screenshots"></a>Prise de captures d’écran

les captures d’écran peuvent être facilement capturées dans l’éditeur en sélectionnant la **réalité mixte**  >  **Shared Computer Toolkit** les  >  **utilitaires**  >  **prennent la capture d’écran** , puis en sélectionnant l’option souhaitée. Veillez à ce que l’onglet de la fenêtre de jeu soit visible si vous prenez la capture quand vous ne jouez pas, sinon la capture ne peut pas être enregistrée.

Par défaut, toutes les captures d’écran sont enregistrées dans le [chemin du cache temporaire](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), le chemin de la capture s’affichera dans la console Unity.

![Élément de menu de l’utilitaire de capture d’écran](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Exemple de prise de capture d’écran

La capture d’écran ci-dessous a été prise avec l’option *"4x Resolution (Transparent Background)"* . Le résultat est une image haute résolution avec les pixels normalement représentés par la couleur claire enregistrée comme pixels transparents. Cette technique permet aux développeurs de présenter leur application en magasin, ou autres médias, en superposant cette image par-dessus d’autres images.

![Exemple de capture de l’utilitaire de capture d’écran](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
