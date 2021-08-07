---
title: Didacticiels audio spatiaux-2. Spatialisation des sons d’interaction avec les boutons
description: Ajoutez un bouton à votre projet et spatialez les sons d’interaction du bouton.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer, prefabs, courbe de volume
ms.openlocfilehash: e0f916ecf8cd8da81e0738b082021c76c55a7f2031517a37b959575e1b21ce16
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209836"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Spatialisation des sons d’interaction avec les boutons

## <a name="overview"></a>Vue d’ensemble

Dans ce didacticiel, vous allez apprendre à spatialiser les sons d’interaction du bouton et à utiliser un clip audio pour tester l’interaction de bouton spatiale.  

## <a name="objectives"></a>Objectifs

* Ajouter et spatialiser le bouton de clic

## <a name="add-a-button"></a>Ajouter un bouton

pour ajouter le bouton prefab, dans la fenêtre **Project** , sélectionnez **Packages** , puis tapez « PressableButtonHoloLens2 » dans la barre de recherche.

![Bouton Prefab dans les ressources](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

Le bouton Prefab est l’entrée représentée par une icône bleue. Cliquez et faites glisser le Prefab **PressableButtonHoloLens2** dans la hiérarchie. L’objet **PressableButtonHoloLens2** étant toujours sélectionné, dans la fenêtre de l’inspecteur, configurez le composant **transformer** comme suit :

* **Position**: X = 0, Y =-0,4, Z = 2
* **Rotation** : X = 0, Y = 0, Z = 0
* **Scale** : X = 1, Y = 1, Z = 1

![Transformation de bouton](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **PressableButtonHoloLens2** , puis effectuer un zoom légèrement en arrière :

## <a name="spatialize-button-feedback"></a>Commentaires sur le bouton spatial

Dans cette étape, vous allez spatialiser les commentaires audio pour le bouton. Pour obtenir des suggestions de conception associées, consultez [conception de son spatial](../../../design/spatial-sound-design.md).

dans la fenêtre **Mixer audio** , vous allez définir des destinations appelées **Mixer des groupes**, pour la lecture audio à partir de composants **sources audio** .

pour ouvrir la fenêtre de **Mixer audio** , dans le menu unity, sélectionnez audio audio **windows**  >    >  **Mixer**: ![ ouvrir la fenêtre de Mixer audio](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 créez un **Mixer** en cliquant sur le signe « + » en regard de **mixages** , puis entrez un nom approprié pour le Mixer par exemple, _Mixer Audio Spatial_. Le nouveau mélangeur inclura un **groupe** par défaut nommé **maître**.

![panneau Mixer avec le premier mélangeur](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> Tant que la réverbération n’est pas activée dans le [cinquième chapitre : l’utilisation de la réverbération pour ajouter de la distance à l’audio spatial](unity-spatial-audio-ch5.md), le compteur de volume du mélangeur n’affiche pas l’activité des sons joués par Microsoft Spatializer

Dans la fenêtre hiérarchie, sélectionnez le **PressableButtonHoloLens2** puis, dans la fenêtre de l’inspecteur, recherchez le composant **source audio** et configurez le composant audio source comme suit :

1. pour la propriété **sortie** , cliquez sur le sélecteur et choisissez le **Mixer** que vous avez créé.
2. Cochez la case **spatialiser** .
3. Déplacez le curseur de **lissage spatial** vers 3D (1).

![Source audio du bouton](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> Si vous déplacez le **lissage spatial** sur 1 (3d) sans activer la case à cocher **spatialiser** , Unity utilise son Spatializer panoramique, au lieu du **Spatializer Microsoft** avec HRTFs.

## <a name="adjust-the-volume-curve"></a>Ajuster la courbe du volume

Par défaut, Unity atténue les sons spatiaux au fur et à mesure qu’ils s’éloignent de l’écouteur. Lorsque cette atténuation est appliquée à des sons d’interaction, l’interface peut devenir plus difficile à utiliser.

Pour désactiver cette atténuation, vous devez ajuster la courbe de **volume** dans le composant **source audio** .

dans la fenêtre hiérarchie, sélectionnez le **PressableButtonHoloLens2** puis, dans la fenêtre de l’inspecteur, accédez à **Source audio**  >  **3d audio Paramètres** et configurez comme suit :

1. Définissez la propriété **volume Rolloff** sur Linear Rolloff
2. Faites glisser le point de terminaison sur la courbe de **volume** (la courbe rouge) de « 0 » sur l’axe y jusqu’à « 1 »
3. Pour ajuster la forme de la courbe de **volume** à plat, faites glisser le contrôle de forme de courbe blanche pour qu’il soit parallèle à l’axe X.

![Paramètres audio de bouton 3D](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>Test du son spatial

Pour tester le son spatial dans l’éditeur Unity, vous devez ajouter un clip audio dans le composant **source audio** avec l’option de **boucle** archivée sur l’objet **PressableButtonHoloLens2** .

En mode lecture, déplacez l’objet **PressableButtonHoloLens2** de gauche à droite et comparez avec et sans audio spatial activé sur votre station de travail. Vous pouvez également modifier les paramètres de la source audio pour les tests en procédant comme suit :

* Déplacement de la propriété de **lissage spatial** entre 0-1 (2D non spatial et 3D spatialic)
* Vérification et désactivation de la propriété **spatial**

Essayez l’application sur HoloLens 2. Dans l’application, vous pouvez cliquer sur le bouton et entendre les sons d’interaction du bouton spatial.

> [!TIP]
> Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Félicitations

Dans ce didacticiel, vous avez appris à spatialiser les sons d’interaction du bouton et à utiliser un clip audio pour tester l’interaction des boutons spatiales. Dans le didacticiel suivant, vous allez apprendre à spatialiser l’audio à partir d’une source vidéo.

> [!div class="nextstepaction"]
> [Didacticiel suivant : 3. Universion audio à partir d’une vidéo](unity-spatial-audio-ch3.md)
