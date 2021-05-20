---
title: Suivi oculaire - Navigation
description: Comment utiliser le ciblage oculaire pour la navigation dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking,
ms.openlocfilehash: d966bbe1d3a256e55c62532e8101c1f2846e1136
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145270"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Navigation prise en charge par l’œil dans MRTK

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Imaginez que vous lisez des informations sur un ardoise et que vous atteignez la fin du texte affiché, le texte défile automatiquement pour afficher davantage de contenu. Ou vous pouvez effectuer un zoom sur l’emplacement de votre recherche. La carte ajuste également automatiquement le contenu pour conserver les objets intéressants dans le champ de vision. Une autre application intéressante est l’observation sans mains des hologrammes 3D en apportant automatiquement les parties de l’hologramme que vous examinez au premier plan. Voici quelques exemples qui sont décrits sur cette page dans le contexte de la navigation prise en charge par l’oeil.

Les descriptions suivantes supposent que vous êtes déjà familiarisé avec la [configuration du suivi oculaire dans votre scène MRTK](eye-tracking-basic-setup.md) et avec les principes de base de l' [accès aux données de suivi oculaire](eye-tracking-target-selection.md) dans MRTK Unity.
Les exemples présentés dans les éléments suivants font tous partie de la `EyeTrackingDemo-03-Navigation` scène (ressources/MRTK/examples/démos/EyeTracking/scènes/EyeTrackingDemo-03-navigation).

**Résumé :** Défilement automatique du texte, panoramique et zoom de l’œil sur une carte virtuelle, rotation 3D dirigée vers le regard et mains libres.

## <a name="auto-scroll"></a>Défilement automatique

Le défilement automatique permet à l’utilisateur de faire défiler des textes sans soulever de doigt.
Il vous suffit de continuer la lecture et le texte défilera automatiquement vers le haut ou vers le bas en fonction de l’endroit où l’utilisateur regarde.
Vous pouvez commencer à partir de l’exemple fourni dans `EyeTrackingDemo-03-Navigation` (ressources/MRTK/examples/démonstrations/EyeTracking/scènes).
Cet exemple utilise un composant [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) pour permettre le chargement et la mise en forme de nouveau texte de manière flexible.
Pour activer le défilement automatique, ajoutez simplement les deux scripts suivants à votre composant de conflit de la zone de texte :

### <a name="scrollrecttransf"></a>ScrollRectTransf

Pour faire défiler un [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) ou plus généralement en parlant un composant [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) , vous pouvez utiliser le script [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) .
Si vous souhaitez faire défiler une texture au lieu d’un [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html), utilisez [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) au lieu de [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf).
Dans les éléments suivants, les paramètres de [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) qui sont disponibles dans l’éditeur Unity sont expliqués plus en détail :

Paramètres | Description
:---- | :----
LimitPanning | S’il est activé, arrête le contenu défilant à ses limites.
RectTransfToNavigate | Référence au [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) dans lequel défiler.
RefToViewport | Référence au [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) parent du contenu défilant pour déterminer le décalage et la limite corrects.
AutoGazeScrollIsActive | Si cette option est activée, le texte est automatiquement défilant si l’utilisateur regarde une *région active* (par exemple, la partie supérieure et inférieure de votre volet de défilement si la vitesse de défilement verticale n’est pas égale à zéro).
ScrollSpeed_x | Si la valeur est égale à zéro, le défilement horizontal est activé. Les valeurs négatives signifient une modification du sens de défilement : de gauche à droite ou de droite à gauche.
ScrollSpeed_y | Si la valeur est égale à zéro, le défilement vertical est activé. Les valeurs négatives signifient une modification du sens de défilement : jusqu’à la baisse jusqu’à la baisse.
MinDistFromCenterForAutoScroll | Distance minimale normalisée dans x et y à partir du centre de la zone d’accès de la cible (0,0) à faire défiler. Par conséquent, les valeurs doivent être comprises entre 0 (toujours défiler) et 0,5 (pas de défilement).
UseSkimProofing | S’il est activé, il empêche les mouvements de défilement soudains quand vous recherchez rapidement. Cela peut rendre le défilement moins réactif. Il peut être réglé avec la valeur *SkimProofUpdateSpeed* .
SkimProofUpdateSpeed | Plus la valeur est faible, plus le défilement est lent après l’écumage. Valeur recommandée : 5.

![Configuration du défilement prise en charge par l’oeil dans Unity](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

L’attachement du composant _EyeTrackingTarget_ permet de gérer de manière flexible les événements liés au regard.
L’exemple de défilement montre un texte de défilement qui démarre lorsque l’utilisateur *regarde* le panneau et s’arrête lorsque l’utilisateur *regarde* son contenu.
![Configuration du défilement prise en charge par l’œil dans Unity : EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Panoramique et zoom pris en charge dans le regard

Qui n’a pas utilisé de carte virtuelle avant de rechercher sa résidence ou d’explorer les nouveaux emplacements ? Le suivi oculaire vous permet d’approfondir directement les parties qui vous intéressent et de faire un zoom avant, vous pouvez suivre facilement le cours d’une rue pour explorer votre voisinage.
Cela n’est pas seulement utile pour l’exploration des cartes géographiques, mais également pour l’extraction des détails dans des photographies, des visualisations de données ou même une image médicale en flux continu. L’utilisation de cette fonctionnalité dans votre application est simple ! Pour obtenir le contenu rendu sur une [texture]( https://docs.unity3d.com/ScriptReference/Texture.html) (par exemple, une photo, des données diffusées en continu), ajoutez simplement le script [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) .
Pour un [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) , utilisez [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf). En étendant la fonctionnalité de [défilement automatique](#auto-scroll) , nous activons essentiellement pour faire défiler à la fois verticalement et horizontalement en même temps et agrandir le contenu autour du point de focalisation actuel de l’utilisateur.

Paramètres | Description
:---- | :----
LimitPanning | S’il est activé, arrête le contenu défilant à ses limites.
HandZoomEnabledOnStartup | Indique si les gestes à la main sont automatiquement activés pour effectuer un mouvement de zoom. Vous souhaiterez peut-être la désactiver à première vue pour éviter de déclencher accidentellement des actions de zoom.
RendererOfTextureToBeNavigated | Convertisseur référencé de la texture à parcourir.
Zoom_Acceleration | Accélération de zoom définissant la pente du mappage de la fonction de vitesse logistique.
Zoom_SpeedMax | Vitesse maximale du zoom.
Zoom_MinScale | Échelle minimale de la texture pour le zoom avant, par exemple 0,5 f (la moitié de la taille d’origine).
Zoom_MaxScale | Échelle maximale de la texture pour zoom arrière, par exemple 1F (taille d’origine) ou 2.0 f (double de la taille d’origine).
Zoom_TimeInSecToZoom | Zoom chronométré : une fois déclenchée, un zoom avant/arrière est effectué pour la durée spécifiée en secondes.
Zoom_Gesture | Type de mouvement à utiliser pour effectuer un zoom avant/arrière.
--- | ---
Pan_AutoScrollIsActive | Si cette option est activée, le texte est automatiquement défilant si l’utilisateur regarde une *région active* (par exemple, la partie supérieure et inférieure de votre volet de défilement si la vitesse de défilement verticale n’est pas égale à zéro).
Pan_Speed_x | Si la valeur est égale à zéro, le défilement horizontal est activé. Les valeurs négatives signifient une modification du sens de défilement : de gauche à droite ou de droite à gauche.
Pan_Speed_y | Si la valeur est égale à zéro, le défilement vertical est activé. Les valeurs négatives signifient une modification du sens de défilement : jusqu’à la baisse jusqu’à la baisse.
Pan_MinDistFromCenter | Distance minimale normalisée dans x et y à partir du centre de la zone d’accès de la cible (0,0) à faire défiler. Par conséquent, les valeurs doivent être comprises entre 0 (toujours défiler) et 0,5 (pas de défilement).
UseSkimProofing | S’il est activé, il empêche les mouvements de défilement soudains quand vous recherchez rapidement. Cela peut rendre le défilement moins réactif. Il peut être réglé avec la valeur *SkimProofUpdateSpeed* .
SkimProofUpdateSpeed | Plus la valeur est faible, plus le défilement est lent après l’écumage. Valeur recommandée : 5.

![Configuration de panoramique et de zoom prise en charge par l’oeil dans Unity](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Rotation 3D en fonction de l’attention

Imaginez qu’il s’agit d’un objet en 3D et des parties que vous souhaitez voir de façon plus précise que si le système vous rappelle et qu’il vous informe de la rotation de l’élément.
C’est l’idée des rotations 3D basées sur l’attention qui vous permettent d’examiner tout le côté d’un hologramme sans soulever de doigt.
Pour activer ce comportement, ajoutez simplement le script [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) à la partie de votre gameobject avec un composant de [collision](https://docs.unity3d.com/ScriptReference/Collider.html) .
Vous pouvez modifier plusieurs paramètres listés ci-dessous pour limiter la vitesse et l’orientation de l’hologramme.

Comme vous pouvez l’imaginer, le fait que ce comportement soit actif à tout moment peut rapidement devenir assez gênant dans une scène encombrée.
C’est pourquoi vous souhaiterez peut-être commencer par ce comportement désactivé, puis l’activer rapidement à l’aide de commandes vocales.
En guise d’alternative, nous avons ajouté un exemple dans `EyeTrackingDemo-03-Navigation` (ressources/MRTK/examples/démonstrations/EyeTracking/scènes) pour utiliser [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) pour lequel vous pouvez sélectionner une cible ciblée et vous l’Envolez simplement par *« je suis arrivé »*.

Une fois en mode near, le mode de rotation automatique est activé automatiquement.
Dans ce mode, vous pouvez l’observer de tous les côtés, en le faisant simplement glisser et en l’examinant, en le contrainant ou en le faisant tourner et en le faisant pivoter avec votre main. Lorsque vous faites disparaître la cible (Regardez & pincez ou dites *« renvoyer »*), elle retournera à son emplacement d’origine et cessera de vous réagir à partir de Afar.

Paramètres | Description
:---- | :----
SpeedX | Vitesse de rotation horizontale.
Rapide | Vitesse de rotation verticale.
InverseX | Pour inverser le sens de rotation horizontal.
Inversée | Pour inverser la direction de rotation verticale.
RotationThreshInDegrees | Si l’angle entre « pointage vers cible » et « appareil photo vers cible » est inférieur à cette valeur, ne rien faire. Cela permet d’éviter les petites rotations instables..
MinRotX | Angle de rotation horizontal minimal. Cela permet de limiter la rotation dans différentes directions.
MaxRotX | Angle de rotation horizontal maximal. Cela permet de limiter la rotation dans différentes directions.
MinRotY | Angle de rotation verticale minimal pour limiter la rotation autour de l’axe x.
MaxRotY | Angle de rotation vertical maximal pour limiter la rotation autour de l’axe y.

![Configuration de la rotation 3D prise en charge par l’œil dans Unity](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

En résumé, les scripts ci-dessus doivent vous permettre de commencer à utiliser des regards oculaires pour diverses tâches de navigation d’entrée telles que les textes de défilement, le zoom et le panoramique des textures, ainsi que la rotation des hologrammes 3D.

### <a name="see-also"></a>Voir aussi

- [Configuration de base MRTK pour utiliser le suivi oculaire](eye-tracking-basic-setup.md)
- [Sélection de la cible prise en charge par l’œil](eye-tracking-target-selection.md)

---
[Retour à « suivi oculaire dans le MixedRealityToolkit »](eye-tracking-main.md)
