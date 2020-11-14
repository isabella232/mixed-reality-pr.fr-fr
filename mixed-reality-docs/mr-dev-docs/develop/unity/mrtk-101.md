---
title: MRTK 101 - Guide pratique pour utiliser Mixed Reality Toolkit d’Unity pour les interactions spatiales courantes (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Guide pratique pour utiliser Mixed Reality Toolkit avec Unity pour les interactions de base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, conception, exemple d’application, contrôles
ms.localizationpriority: high
ms.openlocfilehash: d10de5c9f16e0caa289d5110647b4c45a8a8fcf9
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386264"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>MRTK 101 : Guide pratique pour utiliser Mixed Reality Toolkit d’Unity pour les interactions spatiales courantes
![MRTK](images/MRTK101/MRTK101Cover.png)

Découvrez comment utiliser MRTK pour obtenir certains des modèles d’interaction les plus largement utilisés dans le domaine de la réalité mixte.

- Comment simuler des interactions d’entrée dans l’éditeur Unity ?
- Comment saisir et déplacer un objet ?
- Comment redimensionner un objet ?
- Comment déplacer ou faire pivoter un objet avec précision ?
- Comment faire en sorte qu’un objet réponde à des événements d’entrée ?
- Comment ajouter un retour visuel ?
- Comment ajouter un retour audio ?
- Comment utiliser des préfabriqués de bouton de style HoloLens 2 ?
- Comment faire en sorte qu’un objet vous suive ?
- Comment faire en sorte qu’un objet se mette en face de vous ?

> [!NOTE]
> Cet article a été mis à jour de façon à refléter les modifications apportées à la [publication de MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)

Tout le contenu de cette page peut être testé dans l’éditeur Unity avec la simulation d’entrée de MRTK. Si vous n’en disposez pas, suivez le [Guide d’installation de MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) pour installer la dernière version de MRTK.

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>Comment simuler des interactions d’entrée dans l’éditeur Unity ?
MRTK prend en charge la simulation d’une entrée dans l’éditeur. Exécutez simplement votre scène en cliquant sur le bouton de lecture dans Unity. Utilisez ces touches pour simuler une entrée.
Appuyez sur les touches W, A, S, D pour déplacer la caméra.
Maintenez le bouton droit de la souris enfoncé et déplacez la souris pour regarder autour de vous.
Pour faire apparaître les mains simulées, appuyez sur la barre d’espace (avec la main droite) ou sur la touche Maj gauche (avec la main gauche). Pour garder les mains simulées dans la vue, appuyez sur la touche T ou Y. Pour faire pivoter les mains simulées, appuyez sur Q ou E (horizontal)/R ou F (vertical).

- [En savoir plus sur la simulation d’entrée dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a>Comment saisir et déplacer un objet ?
Pour rendre un objet saisissable, affectez ces deux scripts : **ObjectManipulator.cs** et **NearInteractionGrabbable.cs** (pour une entrée par saisie directe avec le suivi de la main articulée). ObjectManipulator prend en charge les interactions proches et éloignées. Avec Hololens 2, vous pouvez saisir et déplacer un objet avec une entrée par suivi de la main articulée (interaction proche), avec un rayon émanant de la main (interaction éloignée), avec le faisceau du contrôleur de mouvement (interaction éloignée), avec le curseur oculaire HoloLens et le clic aérien (interaction éloignée).

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>Comment redimensionner un objet ?
**ObjectManipulator.cs** prend en charge la rotation/mise à l’échelle à deux mains. Cela fonctionne avec divers types d’entrée : suivi de la main articulée avec HoloLens 2, pointage du regard + mouvement avec HoloLens 1 et contrôleur de mouvement du casque immersif de Windows Mixed Reality.

- [En savoir plus sur Object Manipulator dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Comment déplacer ou faire pivoter un objet avec précision ?
Affectez **BoundsControl.cs** à un objet pour utiliser un cadre englobant qui constitue l’interface pour la mise à l’échelle et la rotation d’un objet. Par défaut, il présente les poignées et les lignes bleues de style HoloLens 1. Pour utiliser des poignées animées de proximité de style HoloLens 2, vous devez affecter des préfabriqués et des matériaux. 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [En savoir plus sur le contrôle des limites dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>Comment faire en sorte qu’un objet réponde à des événements d’entrée ?
Affectez **PointerHandler.cs** à un objet. Dans l’inspecteur, vous allez pouvoir utiliser des événements OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Pour utiliser ces événements dans un script, implémentez **IMixedRealityPointerHandler**.

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [En savoir plus sur le système d’entrée dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Comment ajouter un retour visuel ?
Affectez **Interactable.cs** à un objet. Dans l’inspecteur, ajoutez l’objet cible et créez un thème. À l’aide des profils de thème d’Interactable, vous pouvez facilement ajouter un retour visuel à tous les états d’interaction d’entrée disponibles.

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable fournit divers types de thèmes, notamment le thème du nuanceur, qui vous permet de contrôler les propriétés du nuanceur par état d’interaction.

- [En savoir plus sur Interactable dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Un autre module important pour le feedback visuel est le **nuanceur MRTK standard**. Avec le nuanceur MRTK standard, vous pouvez facilement ajouter des effets de retour visuel comme une lumière de survol et une lumière de proximité. Étant donné que le nuanceur MRTK standard effectue beaucoup moins de calcul que le nuanceur Unity standard, vous pouvez ainsi créer une expérience performante.

Créez un matériau et sélectionnez le nuanceur « Mixed Reality Toolkit > Standard ». Ou vous pouvez choisir l’un des matériaux existants qui utilisent le nuanceur MRTK standard.

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [En savoir plus sur le nuanceur MRTK standard dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Comment ajouter un retour audio ?
Ajoutez **AudioSource** à un objet. Ensuite, dans les scripts qui exposent des événements d’entrée (par exemple Interactable.cs ou PointerHandler.cs), affectez l’objet avec AudioSource à l’événement et sélectionnez **AudioSource.PlayOneShot()** . Vous pouvez utiliser vos clips audio ou en choisir un à partir des ressources audio de MRTK.

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>Comment utiliser des préfabriqués de bouton de style HoloLens 2 ?
MRTK fournit divers types de boutons de style shell (système d’exploitation) HoloLens 2. Il offre des feedbacks visuels sophistiqués, comme la lumière de proximité, le cadre de compression et un effet d’ondulation à la surface du bouton qui améliorent la confiance de l’utilisateur.

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

Il vous suffit de glisser-déposer un des **préfabriqués de boutons sur lequel appuyer de style HoloLens 2** dans votre scène. Le préfabriqué utilise Interactable.cs, décrit ci-dessus. Vous pouvez utiliser des événements exposés comme OnClick() dans Interactable pour déclencher des actions.

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [En savoir plus sur les préfabriqués de bouton dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>Comment faire en sorte qu’un objet vous suive ?
Affectez le script **RadialView.cs** ou **Follow.cs** à un objet. Il fait partie de la série de scripts Solver qui vous permet d’obtenir divers types de positionnement des objets dans l’espace 3D. **SolverHandler.cs** est ajouté automatiquement.
Voici un exemple de configuration de RadialView pour obtenir un comportement de suivi tardif, à l’instar du menu Démarrer dans le shell HoloLens. Vous pouvez spécifier la distance minimale/maximale et les degrés d’affichage minimaux/maximaux. L’exemple ci-dessous montre le positionnement de l’objet dans une plage comprise entre 0,4 et 0,8 mètre à 15 °. Ajustez les valeurs de délai Lerp pour accélérer ou ralentir la mise à jour de la position.

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [En savoir plus sur Solver dans la documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>Comment faire en sorte qu’un objet se mette en face de vous ?
Affectez le script **Billboard.cs** à un objet. L’objet vous fera toujours face, quelle que soit votre position. Vous pouvez spécifier l’option d’axe pivot.

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Vous êtes prêt à créer des expériences étonnantes pour la réalité mixte ? Consultez les pages ci-dessous pour en savoir plus sur MRTK et la réalité mixte.

## <a name="about-the-author"></a>À propos de l’auteur

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Concepteur d’expérience utilisateur @Microsoft</td>
</tr>
</table>

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de points de contrôle de développement Unity que nous avons élaboré, vous explorez actuellement les composants de base de MRTK. À partir de là, vous pouvez passer au composant suivant : 

> [!div class="nextstepaction"]
> [Appareil photo](camera-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [MRTK - Guide d’installation (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Mixed Reality Toolkit - Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portail de la documentation MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Instructions de portage de HoloToolkit vers MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
