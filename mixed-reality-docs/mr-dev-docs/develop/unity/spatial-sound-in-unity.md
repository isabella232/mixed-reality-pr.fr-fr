---
title: Son spatial dans Unity
description: Découvrez comment lire et atténuer les sons spatiaux d’un point 3D spécifique dans votre scène Unity avec des exemples.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, son spatial, HRTF, taille de la salle, casque de la réalité mixte, casque Windows Mixed realisation, casque de la réalité virtuelle, MRTK, boîte à outils de la réalité mixte, Spatializer, réverbération
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009269"
---
# <a name="spatial-sound-in-unity"></a>Son spatial dans Unity

Cette page contient des liens vers des ressources pour le son spatial dans Unity.

## <a name="spatializer-options"></a>Options de Spatializer

Les options Spatializer pour les applications de réalité mixte sont les suivantes :
* Unity fournit le *Spatializer MS HRTF* dans le cadre du package facultatif *Windows Mixed Reality* .
  * S’exécute sur le processeur dans une architecture à source unique à coût plus élevé.
  * Fourni pour la compatibilité descendante avec les applications HoloLens d’origine.
* *Microsoft Spatializer* est disponible dans le [dépôt github Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Utilise une architecture à plusieurs sources à moindre coût.
  * Déchargée sur un accélérateur matériel sur le HoloLens 2. 

Pour les nouvelles applications, nous vous recommandons *Microsoft Spatializer*.

## <a name="enable-spatialization"></a>Activer Spatialization

Utilisez [NuGet pour Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) pour installer _Microsoft. SpatialAudio. Spatializer. Unity_ et choisissez **Microsoft Spatializer** dans les paramètres audio de votre projet. Ensuite :
* Attacher une **source audio** à un objet dans la hiérarchie
* Cochez la case **Enable Spatialization**
* Déplacez le curseur de **lissage spatial** sur « 1 »
* Assurez-vous que l’audio spatial est activé sur votre station de travail de développeur. 
    * Cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches et assurez-vous que le son spatial est défini sur une valeur autre que « désactivé ». 
    * Choisissez **Windows Sonic pour casque** pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2.

>[!NOTE]
>Si vous recevez une erreur dans Unity sur l’impossibilité de charger le plug-in Microsoft. SpatialAudio. Spatializer. Unity, car l’une de ses dépendances est manquante, vérifiez que vous disposez de la dernière version du [Microsoft Visual C++ redistribuable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installé sur votre ordinateur.

Pour plus d’informations, consultez :
* [Dépôt GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Didacticiel Spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentation de la source audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentation Spatializer de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atténuation basée sur la distance

La dégradation basée sur les distances par défaut d’Unity a une distance minimale de 1 mètre et une distance maximale de 500 mètres, avec un Rolloff logarithmique. Ces paramètres peuvent fonctionner pour votre scénario, ou vous pouvez constater que les sources s’atténuent trop rapidement ou trop lentement. Pour plus d’informations, consultez :
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

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte. À partir de là, vous pouvez passer au module suivant :

> [!div class="nextstepaction"]
> [Texte](text-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Conception audio en réalité mixte](../../design/spatial-sound-design.md)
* [Didacticiel Spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
