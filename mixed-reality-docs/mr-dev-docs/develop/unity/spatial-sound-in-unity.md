---
title: Son spatial dans Unity
description: Découvrez comment lire et atténuer les sons spatiaux d’un point 3D spécifique dans votre scène Unity avec des exemples.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: unity, son spatial, HRTF, taille de la salle, casque de la réalité mixte, casque windows mixed realisation, casque de la réalité virtuelle, MRTK, Shared Computer Toolkit de la réalité mixte, spatializer, réverbération
ms.openlocfilehash: e6e56732a888fd096335a114fceba557519b01bf8df84a7670b9265f46c75a34
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228225"
---
# <a name="spatial-sound-in-unity"></a>Son spatial dans Unity

Cette page contient des liens vers des ressources pour le son spatial dans Unity.

## <a name="spatializer-options"></a>Options de Spatializer

Les options Spatializer pour les applications de réalité mixte sont les suivantes :
* unity fournit le *Spatializer MS HRTF* dans le cadre de l' *Windows Mixed Reality* package facultatif.
  * S’exécute sur le processeur dans une architecture à source unique à coût plus élevé.
  * fourni pour la compatibilité descendante avec les applications de HoloLens d’origine.
* *microsoft Spatializer* est disponible dans le [référentiel microsoft Spatializer GitHub](https://github.com/microsoft/spatialaudio-unity).
  * Utilise une architecture à plusieurs sources à moindre coût.
  * Déchargée sur un accélérateur matériel sur le HoloLens 2. 

Pour les nouvelles applications, nous vous recommandons *Microsoft Spatializer*.

## <a name="enable-spatialization"></a>Activer Spatialization

utilisez [NuGet pour unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) pour installer _microsoft. SpatialAudio. Spatializer. unity_ et choisissez **microsoft Spatializer** dans les paramètres audio de votre projet. Ensuite :
* Attacher une **source audio** à un objet dans la hiérarchie
* Cochez la case **Enable Spatialization**
* Déplacez le curseur de **lissage spatial** sur « 1 »
* Assurez-vous que l’audio spatial est activé sur votre station de travail de développeur. 
    * Cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches et assurez-vous que le son spatial est défini sur une valeur autre que « désactivé ». 
    * choisissez **Windows Sonic pour casque** pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2.

>[!NOTE]
>si vous recevez une erreur dans unity sur l’impossibilité de charger le plug-in Microsoft. SpatialAudio. Spatializer. unity, car l’une de ses dépendances est manquante, vérifiez que vous disposez de la dernière version du [Microsoft Visual C++ redistribuable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installé sur votre ordinateur.

Pour plus d'informations, consultez les pages suivantes :
* [dépôt GitHub Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Didacticiel Spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentation de la source audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentation Spatializer de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atténuation basée sur la distance

La dégradation basée sur les distances par défaut d’Unity a une distance minimale de 1 mètre et une distance maximale de 500 mètres, avec un Rolloff logarithmique. Ces paramètres peuvent fonctionner pour votre scénario, ou vous pouvez constater que les sources s’atténuent trop rapidement ou trop lentement. Pour plus d'informations, consultez les pages suivantes :
* [Conception audio en réalité mixte](../../design/spatial-sound-design.md) pour les paramètres recommandés.
* [Documentation de la source audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) pour obtenir des instructions sur la définition de ces courbes.

## <a name="reverb"></a>Réverbération

Le _Spatializer Microsoft_ désactive les effets postérieurs à Spatializer par défaut. Pour activer la réverbération et d’autres effets pour les sources spatiales :
* Attacher le composant de niveau d’envoi de l' **effet de salle** à chaque source
* Ajustez la courbe de niveau d’envoi pour chaque source, afin de contrôler le gain sur le son renvoyé au graphique pour le traitement des effets

Pour plus d’informations, consultez [le chapitre 5 du didacticiel Spatializer](tutorials/unity-spatial-audio-ch5.md) .

## <a name="unity-spatial-sound-examples"></a>Exemples de sons spatiaux Unity

Pour obtenir des exemples de son spatial dans Unity, consultez :
* [Démonstrations MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Exemple de projet Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte. À partir d’ici, vous pouvez passer au composant suivant :

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Conception audio en réalité mixte](../../design/spatial-sound-design.md)
* [Didacticiel Spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
