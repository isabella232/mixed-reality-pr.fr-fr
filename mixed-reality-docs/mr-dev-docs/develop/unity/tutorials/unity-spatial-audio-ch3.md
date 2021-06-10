---
title: Didacticiels audio spatiaux-3. Spatialisation du contenu audio d’une vidéo
description: Importez un élément multimédia vidéo dans votre projet Unity et spatialez l’audio de la vidéo.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer, importation de vidéos, lecteur vidéo
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712877"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Spatialisation du contenu audio d’une vidéo

## <a name="overview"></a>Vue d’ensemble

Dans ce didacticiel, vous allez apprendre à spatialiser l’audio à partir d’une source vidéo et à le tester dans l’éditeur Unity et dans HoloLens 2.

## <a name="objectives"></a>Objectifs

* Importer une vidéo et ajouter un lecteur vidéo
* Lire la vidéo sur un Quadrangle
* Acheminer l’audio de la vidéo vers le Quadrangle et spatialiser l’audio

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importer une vidéo et ajouter un lecteur vidéo à la scène

Pour ce didacticiel, vous pouvez utiliser [cette vidéo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) à partir de l’exemple de projet de son spatial.

Pour importer une vidéo dans le projet Unity. dans le menu Unity, sélectionnez **Asset**  >  **Importer un nouvel élément multimédia importer un** 
 élément multimédia ![](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

Dans la fenêtre **Importer une nouvelle ressource..** ., sélectionnez le fichier **Microsoft HoloLens-spatial Sound-PTPvx7mDon4** que vous avez téléchargé, puis cliquez sur le bouton **ouvrir** pour importer la ressource dans le projet :

![Sélection de l’élément multimédia](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

L’ajustement des paramètres de qualité sur le clip vidéo peut garantir une lecture douce sur HoloLens 2. Sélectionnez le fichier vidéo dans la fenêtre **projet** et dans la fenêtre Inspecteur du fichier vidéo, **Remplacez** les paramètres pour les **applications du Windows Store** et :

* Activer le **transcodage**
* Définir le **codec** sur H264 –
* Définir le **Mode débit** sur faible
* Définir la **qualité spatiale** sur une qualité spatiale moyenne

Après ces ajustements, cliquez sur appliquer pour modifier le paramètre de qualité du clip vidéo.

![Modification des propriétés de la vidéo](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

Cliquez avec le bouton droit sur la hiérarchie, **puis sélectionnez**  >  **lecteur** vidéo vidéo pour ajouter le composant lecteur vidéo.

![Ajouter un lecteur vidéo](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Lire une vidéo sur un Quadrangle

L’objet **lecteur vidéo** a besoin d’un objet de jeu texturé pour afficher la vidéo.

Cliquez avec le bouton droit sur la hiérarchie, sélectionnez **objet 3D**  >  **quadruple** pour créer un Quad et configurer son composant **transformer** comme suit :

* **Position**: X = 0, Y = 0, Z = 2
* **Rotation** : X = 0, Y = 0, Z = 0
* **Échelle**: X = 1,28, Y = 0,72, Z = 1

![Ajouter un quadruple](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

À présent, vous devez texturer le **Quad** avec la vidéo, dans la fenêtre du **projet** , cliquer avec le bouton droit et choisir **créer**  >  une **texture** de rendu pour créer un composant de texture de rendu, entrer un nom approprié pour la texture de rendu, par exemple _texture audio spatiale_:

![Créer une texture de rendu](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

Sélectionnez la **texture de rendu** et, dans la fenêtre de l’inspecteur, définissez la propriété **Size** pour qu’elle corresponde à la résolution native de la vidéo de 1280 x 720. Ensuite, pour garantir de bonnes performances de rendu sur HoloLens 2, affectez à la propriété de la **mémoire tampon de profondeur** une **profondeur d’au moins 16 bits**.

![Propriétés de texture de rendu](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

Ensuite, utilisez la texture **audio spatiale** de rendu créée comme texture pour le **Quad**:

1. Faites glisser la **texture audio spatiale** de la fenêtre **projet** sur le **quadruple** dans la hiérarchie pour ajouter la texture de rendu au quadruple
2. Pour garantir de bonnes performances sur HoloLens 2, sélectionnez Quad dans la hiérarchie, puis dans la fenêtre Inspector du nuanceur, sélectionnez le nuanceur standard de la **réalité mixte**  >   .

![Propriétés de texture Quad](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

Pour définir le **lecteur vidéo** et **afficher la texture** pour lire le clip vidéo, sélectionnez le **lecteur vidéo** dans la **hiérarchie** et dans la fenêtre **inspecteur** .

* Définissez la propriété **clip vidéo** sur le fichier vidéo téléchargé « Microsoft HoloLens-spatial Sound-PTPvx7mDon4 »
* Cochez la case **boucle**
* Définir la **texture cible** sur la nouvelle texture **audio spatiale** de rendu

![Propriétés du lecteur vidéo](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialiser l’audio à partir de la vidéo

Dans la fenêtre hiérarchie, sélectionnez objet **quadruple** , puis dans la fenêtre de l’inspecteur, utilisez le bouton **Ajouter un composant** pour ajouter une **source audio** dans laquelle vous allez acheminer l’audio à partir de la vidéo.

Dans la **source audio**:

* Définir la **sortie** dans le **mélangeur audio spatial**
* Vérifier la zone **spatiale**
* Déplacez le curseur de **lissage spatial** sur 1 (3d)

![Inspecteur de source audio quadruple](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

Pour configurer le lecteur vidéo de façon à acheminer son audio vers la **source audio**, sélectionnez le **lecteur vidéo** dans la fenêtre hiérarchie et, dans l’objet lecteur vidéo de l’inspecteur, effectuez les modifications suivantes.

* Définir le **mode de sortie audio** sur la **source audio**
* Définir la propriété de la **source audio** sur le **quadruple**

![Source du jeu de lecteurs vidéo](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Félicitations

Dans ce didacticiel, vous avez appris à spatialiser l’audio à partir d’une source vidéo essayer votre application sur un HoloLens 2 ou dans l’éditeur Unity. Vous verrez et entendez la vidéo, et l’audio de la vidéo est spatial.

Dans le didacticiel suivant, vous allez apprendre à activer et désactiver des Spatialization au moment de l’exécution.

> [!div class="nextstepaction"]
> [Didacticiel suivant : 4. activation et désactivation de Spatialization au moment de l’exécution](unity-spatial-audio-ch4.md)
