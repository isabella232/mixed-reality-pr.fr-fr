---
title: Intégration d’Azure Custom Vision
description: Suivez ce cours pour découvrir comment implémenter Azure Custom Vision dans une application de réalité mixte HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, hololens 2, azure custom vision, azure cognitive services, services cloud azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7624ed28c337f3621a29f15f1ab3b0e98aeb89db
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224229"
---
# <a name="3-integrating-azure-custom-vision"></a>3. Intégration d’Azure Custom Vision

Dans ce tutoriel, vous allez apprendre à utiliser **Azure Custom Vision**. Vous allez charger un ensemble de photos pour l’associer à un *objet suivi*, les charger sur le service **Custom Vision** et démarrer le processus d’entraînement. Ensuite, vous utiliserez le service pour détecter l’*objet suivi* en capturant des photos à partir du flux de la webcam.

## <a name="objectives"></a>Objectifs

* Apprendre les bases d’Azure Custom Vision
* Apprendre à configurer la scène pour utiliser Custom Vision dans ce projet
* Apprendre à intégrer les images de chargement, d’entraînement et de détection

## <a name="understanding-azure-custom-vision"></a>Présentation d’Azure Custom Vision

**Azure Custom Vision** fait partie de la famille **Cognitive Services** et est utilisé pour l’entraînement des classifieurs d’images. Le classifieur d’images est un service IA qui utilise le modèle entraîné pour appliquer des étiquettes correspondantes. Cette fonctionnalité de classification sera utilisée par notre application pour détecter les *objets suivis*.

Apprenez-en davantage sur [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).

## <a name="preparing-azure-custom-vision"></a>Préparation d’Azure Custom Vision

Avant de commencer, vous devez créer un projet Custom Vision ; le moyen le plus rapide consiste à utiliser le portail web.

Suivez ce [tutoriel de démarrage rapide](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) pour configurer votre compte et votre projet jusqu’à la section *Charger et étiqueter des images*.

> [!WARNING]
> Pour entraîner un modèle, vous devez avoir au moins deux étiquettes et cinq images par étiquette. Pour utiliser cette application, vous devez créer au moins une étiquette avec cinq images, afin que le processus d’entraînement n’échoue pas par la suite.

## <a name="preparing-the-scene"></a>Préparation de la scène

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.

![Unity avec la fenêtre Project montrant le chemin vers le préfabriqué ObjectDetectionManager](images/mr-learning-azure/tutorial3-section4-step1-1.png)

À partir de là, faites glisser le préfabriqué **ObjectDetectionManager** dans la hiérarchie de la scène.

![Unity avec les champs de configuration du composant de script ObjectDetectionManager affichés dans Inspector](images/mr-learning-azure/tutorial3-section4-step1-2.png)

Dans la fenêtre de hiérarchie, recherchez l’objet **ObjectDetectionManager** et sélectionnez-le.
Le préfabriqué **ObjectDetectionManager** contient le composant **ObjectDetectionManager (script)** et, comme vous pouvez le voir dans la fenêtre de l’inspecteur, il dépend des paramètres Azure et des paramètres du projet.

## <a name="retrieving-azure-api-resource-credentials"></a>Récupération des informations d’identification de la ressource API Azure

Les informations d’identification nécessaires pour les paramètres d’**ObjectDetectionManager (script)** peuvent être récupérées à partir du portail Azure et du portail Custom Vision.

### <a name="retrieving-azure-settings-credentials"></a>Récupération des informations d’identification des paramètres Azure

Recherchez la ressource Custom Vision de type **Cognitive Services** que vous avez créée dans la section *Préparation de la scène* de ce tutoriel (sélectionnez les noms des ressources Custom Vision qui se terminent par *-Prediction*). Cliquez sur *Vue d’ensemble* ou sur *Clés et point de terminaison* pour récupérer les informations d’identification nécessaires.

### <a name="retrieving-project-settings-credentials"></a>Récupération des informations d’identification des paramètres du projet

Dans le tableau de bord [Custom Vision](https://www.customvision.ai/projects), ouvrez le projet que vous avez créé pour ce tutoriel, puis cliquez en haut à droite de la page sur l’icône d’engrenage pour ouvrir la page Paramètres. Dans la section de droite *Resources*, vous trouverez les informations d’identification nécessaires.

Le composant **ObjectDetectionManager (script)** étant maintenant configuré correctement, recherchez l’objet **SceneController** dans la hiérarchie de la scène et sélectionnez-le.

![Unity avec les champs de configuration du composant de script SceneController affichés dans Inspector](images/mr-learning-azure/tutorial3-section4-step1-3.png)

Vous constatez que le champ *Object Detection Manager* (Gestionnaire de détection d’objets) dans le composant **SceneController** est vide. Faites glisser l’**ObjectDetectionManager** de la hiérarchie vers ce champ et enregistrez la scène.

![Unity avec le composant de script SceneController configuré](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>Capturer et charger des images

Exécutez la scène, cliquez sur **Set Object** (Définir l’objet), puis tapez le nom de l’un des **objets suivis** que vous avez créés dans la [leçon précédente](mr-learning-azure-02.md). Cliquez à présent sur le bouton **Computer Vision** qui figure en bas de la **fiche d’objet**.

Une nouvelle fenêtre s’ouvre, dans laquelle vous devez prendre six photos pour entraîner le modèle à la reconnaissance d’image. Cliquez sur le bouton **Camera** et effectuez un clic aérien lorsque vous regardez l’objet que vous voulez suivre. Répétez cette opération à six reprises.

> [!TIP]
> Pour améliorer l’entraînement du modèle, essayez de capturer chaque image à partir de différents angles et conditions d’éclairage.

Une fois que vous avez suffisamment d’images, cliquez sur le bouton **Train** (Entraîner) pour démarrer le processus d’entraînement du modèle dans le cloud. L’activation de l’entraînement provoque le chargement de toutes les images, puis le démarrage de l’entraînement. Cette opération peut prendre jusqu’à une minute, voire plus. Un message à l’intérieur du menu indique la progression actuelle et, une fois qu’il indique que l’opération est terminée, vous pouvez arrêter l’application.

> [!TIP]
> Le composant **ObjectDetectionManager (script)** charge directement les images prises dans le service Custom Vision. En guise d’alternative, l’API Custom Vision accepte les URL vers les images. Comme exercice, vous pouvez modifier l’**ObjectDetectionManager (script)** afin qu’il charge plutôt les images dans un stockage Blob.

## <a name="detect-objects"></a>Détecter des objets

Vous pouvez maintenant tester le modèle entraîné. Exécutez l’application et, dans le *menu principal*, cliquez sur **Search Object** (Rechercher un objet) et tapez le nom de l’**objet suivi** en question. La **fiche d’objet** apparaît. Cliquez sur le bouton **Custom Vision**. À partir de là, le composant **ObjectDetectionManager** commence à effectuer des captures d’images en arrière-plan à partir de l’appareil photo, et la progression sera indiquée dans le menu. Pointez l’appareil photo sur l’objet que vous avez utilisé pour l’entraînement du modèle, et vous constaterez qu’après quelques instants il détectera l’objet.

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez appris à utiliser Azure Custom Vision pour entraîner des images et utiliser le service de classification pour détecter les images qui correspondent à l’**objet suivi** associé.

Dans le tutoriel suivant, vous allez apprendre à utiliser Azure Spatial Anchors pour lier un *objet suivi* à un emplacement dans le monde physique, puis à afficher une flèche qui guidera l’utilisateur vers l’emplacement lié de l’objet suivi.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 4. Intégration d’Azure Spatial Anchors](mr-learning-azure-04.md)