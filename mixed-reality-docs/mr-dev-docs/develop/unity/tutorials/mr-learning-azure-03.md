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
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="82edc-104">3. Intégration d’Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="82edc-104">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="82edc-105">Dans ce tutoriel, vous allez apprendre à utiliser **Azure Custom Vision**. Vous allez charger un ensemble de photos pour l’associer à un *objet suivi*, les charger sur le service **Custom Vision** et démarrer le processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="82edc-105">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="82edc-106">Ensuite, vous utiliserez le service pour détecter l’*objet suivi* en capturant des photos à partir du flux de la webcam.</span><span class="sxs-lookup"><span data-stu-id="82edc-106">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="82edc-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="82edc-107">Objectives</span></span>

* <span data-ttu-id="82edc-108">Apprendre les bases d’Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="82edc-108">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="82edc-109">Apprendre à configurer la scène pour utiliser Custom Vision dans ce projet</span><span class="sxs-lookup"><span data-stu-id="82edc-109">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="82edc-110">Apprendre à intégrer les images de chargement, d’entraînement et de détection</span><span class="sxs-lookup"><span data-stu-id="82edc-110">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="82edc-111">Présentation d’Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="82edc-111">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="82edc-112">**Azure Custom Vision** fait partie de la famille **Cognitive Services** et est utilisé pour l’entraînement des classifieurs d’images.</span><span class="sxs-lookup"><span data-stu-id="82edc-112">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="82edc-113">Le classifieur d’images est un service IA qui utilise le modèle entraîné pour appliquer des étiquettes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="82edc-113">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="82edc-114">Cette fonctionnalité de classification sera utilisée par notre application pour détecter les *objets suivis*.</span><span class="sxs-lookup"><span data-stu-id="82edc-114">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="82edc-115">Apprenez-en davantage sur [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="82edc-115">Learn more about [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="82edc-116">Préparation d’Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="82edc-116">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="82edc-117">Avant de commencer, vous devez créer un projet Custom Vision ; le moyen le plus rapide consiste à utiliser le portail web.</span><span class="sxs-lookup"><span data-stu-id="82edc-117">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="82edc-118">Suivez ce [tutoriel de démarrage rapide](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) pour configurer votre compte et votre projet jusqu’à la section *Charger et étiqueter des images*.</span><span class="sxs-lookup"><span data-stu-id="82edc-118">Follow this [quickstart tutorial](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="82edc-119">Pour entraîner un modèle, vous devez avoir au moins deux étiquettes et cinq images par étiquette.</span><span class="sxs-lookup"><span data-stu-id="82edc-119">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="82edc-120">Pour utiliser cette application, vous devez créer au moins une étiquette avec cinq images, afin que le processus d’entraînement n’échoue pas par la suite.</span><span class="sxs-lookup"><span data-stu-id="82edc-120">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="82edc-121">Préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="82edc-121">Preparing the scene</span></span>

<span data-ttu-id="82edc-122">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="82edc-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Unity avec la fenêtre Project montrant le chemin vers le préfabriqué ObjectDetectionManager](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="82edc-124">À partir de là, faites glisser le préfabriqué **ObjectDetectionManager** dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="82edc-124">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![Unity avec les champs de configuration du composant de script ObjectDetectionManager affichés dans Inspector](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="82edc-126">Dans la fenêtre de hiérarchie, recherchez l’objet **ObjectDetectionManager** et sélectionnez-le.</span><span class="sxs-lookup"><span data-stu-id="82edc-126">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="82edc-127">Le préfabriqué **ObjectDetectionManager** contient le composant **ObjectDetectionManager (script)** et, comme vous pouvez le voir dans la fenêtre de l’inspecteur, il dépend des paramètres Azure et des paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="82edc-127">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on Azure settings and Project settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="82edc-128">Récupération des informations d’identification de la ressource API Azure</span><span class="sxs-lookup"><span data-stu-id="82edc-128">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="82edc-129">Les informations d’identification nécessaires pour les paramètres d’**ObjectDetectionManager (script)** peuvent être récupérées à partir du portail Azure et du portail Custom Vision.</span><span class="sxs-lookup"><span data-stu-id="82edc-129">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="retrieving-azure-settings-credentials"></a><span data-ttu-id="82edc-130">Récupération des informations d’identification des paramètres Azure</span><span class="sxs-lookup"><span data-stu-id="82edc-130">Retrieving Azure Settings credentials</span></span>

<span data-ttu-id="82edc-131">Recherchez la ressource Custom Vision de type **Cognitive Services** que vous avez créée dans la section *Préparation de la scène* de ce tutoriel (sélectionnez les noms des ressources Custom Vision qui se terminent par *-Prediction*).</span><span class="sxs-lookup"><span data-stu-id="82edc-131">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial (select custom vision resources name followed by *-Prediction* ).</span></span> <span data-ttu-id="82edc-132">Cliquez sur *Vue d’ensemble* ou sur *Clés et point de terminaison* pour récupérer les informations d’identification nécessaires.</span><span class="sxs-lookup"><span data-stu-id="82edc-132">There click on *Overview* or *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="retrieving-project-settings-credentials"></a><span data-ttu-id="82edc-133">Récupération des informations d’identification des paramètres du projet</span><span class="sxs-lookup"><span data-stu-id="82edc-133">Retrieving Project Settings credentials</span></span>

<span data-ttu-id="82edc-134">Dans le tableau de bord [Custom Vision](https://www.customvision.ai/projects), ouvrez le projet que vous avez créé pour ce tutoriel, puis cliquez en haut à droite de la page sur l’icône d’engrenage pour ouvrir la page Paramètres.</span><span class="sxs-lookup"><span data-stu-id="82edc-134">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="82edc-135">Dans la section de droite *Resources*, vous trouverez les informations d’identification nécessaires.</span><span class="sxs-lookup"><span data-stu-id="82edc-135">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="82edc-136">Le composant **ObjectDetectionManager (script)** étant maintenant configuré correctement, recherchez l’objet **SceneController** dans la hiérarchie de la scène et sélectionnez-le.</span><span class="sxs-lookup"><span data-stu-id="82edc-136">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![Unity avec les champs de configuration du composant de script SceneController affichés dans Inspector](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="82edc-138">Vous constatez que le champ *Object Detection Manager* (Gestionnaire de détection d’objets) dans le composant **SceneController** est vide. Faites glisser l’**ObjectDetectionManager** de la hiérarchie vers ce champ et enregistrez la scène.</span><span class="sxs-lookup"><span data-stu-id="82edc-138">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![Unity avec le composant de script SceneController configuré](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="82edc-140">Capturer et charger des images</span><span class="sxs-lookup"><span data-stu-id="82edc-140">Take and upload images</span></span>

<span data-ttu-id="82edc-141">Exécutez la scène, cliquez sur **Set Object** (Définir l’objet), puis tapez le nom de l’un des **objets suivis** que vous avez créés dans la [leçon précédente](mr-learning-azure-02.md).</span><span class="sxs-lookup"><span data-stu-id="82edc-141">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="82edc-142">Cliquez à présent sur le bouton **Computer Vision** qui figure en bas de la **fiche d’objet**.</span><span class="sxs-lookup"><span data-stu-id="82edc-142">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="82edc-143">Une nouvelle fenêtre s’ouvre, dans laquelle vous devez prendre six photos pour entraîner le modèle à la reconnaissance d’image.</span><span class="sxs-lookup"><span data-stu-id="82edc-143">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="82edc-144">Cliquez sur le bouton **Camera** et effectuez un clic aérien lorsque vous regardez l’objet que vous voulez suivre. Répétez cette opération à six reprises.</span><span class="sxs-lookup"><span data-stu-id="82edc-144">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="82edc-145">Pour améliorer l’entraînement du modèle, essayez de capturer chaque image à partir de différents angles et conditions d’éclairage.</span><span class="sxs-lookup"><span data-stu-id="82edc-145">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="82edc-146">Une fois que vous avez suffisamment d’images, cliquez sur le bouton **Train** (Entraîner) pour démarrer le processus d’entraînement du modèle dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="82edc-146">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="82edc-147">L’activation de l’entraînement provoque le chargement de toutes les images, puis le démarrage de l’entraînement. Cette opération peut prendre jusqu’à une minute, voire plus.</span><span class="sxs-lookup"><span data-stu-id="82edc-147">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="82edc-148">Un message à l’intérieur du menu indique la progression actuelle et, une fois qu’il indique que l’opération est terminée, vous pouvez arrêter l’application.</span><span class="sxs-lookup"><span data-stu-id="82edc-148">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="82edc-149">Le composant **ObjectDetectionManager (script)** charge directement les images prises dans le service Custom Vision.</span><span class="sxs-lookup"><span data-stu-id="82edc-149">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="82edc-150">En guise d’alternative, l’API Custom Vision accepte les URL vers les images. Comme exercice, vous pouvez modifier l’**ObjectDetectionManager (script)** afin qu’il charge plutôt les images dans un stockage Blob.</span><span class="sxs-lookup"><span data-stu-id="82edc-150">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="82edc-151">Détecter des objets</span><span class="sxs-lookup"><span data-stu-id="82edc-151">Detect objects</span></span>

<span data-ttu-id="82edc-152">Vous pouvez maintenant tester le modèle entraîné. Exécutez l’application et, dans le *menu principal*, cliquez sur **Search Object** (Rechercher un objet) et tapez le nom de l’**objet suivi** en question.</span><span class="sxs-lookup"><span data-stu-id="82edc-152">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="82edc-153">La **fiche d’objet** apparaît. Cliquez sur le bouton **Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="82edc-153">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="82edc-154">À partir de là, le composant **ObjectDetectionManager** commence à effectuer des captures d’images en arrière-plan à partir de l’appareil photo, et la progression sera indiquée dans le menu.</span><span class="sxs-lookup"><span data-stu-id="82edc-154">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="82edc-155">Pointez l’appareil photo sur l’objet que vous avez utilisé pour l’entraînement du modèle, et vous constaterez qu’après quelques instants il détectera l’objet.</span><span class="sxs-lookup"><span data-stu-id="82edc-155">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="82edc-156">Félicitations</span><span class="sxs-lookup"><span data-stu-id="82edc-156">Congratulations</span></span>

<span data-ttu-id="82edc-157">Dans ce tutoriel, vous avez appris à utiliser Azure Custom Vision pour entraîner des images et utiliser le service de classification pour détecter les images qui correspondent à l’**objet suivi** associé.</span><span class="sxs-lookup"><span data-stu-id="82edc-157">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="82edc-158">Dans le tutoriel suivant, vous allez apprendre à utiliser Azure Spatial Anchors pour lier un *objet suivi* à un emplacement dans le monde physique, puis à afficher une flèche qui guidera l’utilisateur vers l’emplacement lié de l’objet suivi.</span><span class="sxs-lookup"><span data-stu-id="82edc-158">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="82edc-159">Tutoriel suivant : 4. Intégration d’Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="82edc-159">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)