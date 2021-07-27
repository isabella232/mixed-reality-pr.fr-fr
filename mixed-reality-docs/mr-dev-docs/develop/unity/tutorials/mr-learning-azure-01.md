---
title: Azure Cloud Services pour HoloLens 2
description: Suivez ce cours pour découvrir comment implémenter différents services Azure dans une application HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: azure, réalité mixte, Unity, tutoriel, hololens, hololens 2, stockage blob azure, stockage table azure, ancres spatiales azure, azure bot framework, services cloud azure, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 3c52384b118a72b1c2f2dfaa2205e4f890e2e5a7
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224364"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Azure Cloud Services pour HoloLens 2

Bienvenue dans cette série de tutoriels consacrés à l’intégration de services **cloud Azure** dans une application **HoloLens 2**. Dans cette série de cinq tutoriels, vous allez apprendre à intégrer plusieurs services **cloud Azure** dans un projet **Unity** pour **HoloLens 2**. Avec chaque chapitre consécutif, vous ajouterez de nouveaux services **cloud Azure** pour étendre les fonctionnalités de l’application et l’expérience utilisateur, tout en apprenant les principes fondamentaux de chaque service **cloud Azure**.

> [!NOTE]
> Cette série de tutoriels se concentrera sur **HoloLens 2**, mais en raison de la nature multiplateforme de Unity, la plus grande partie de ce que vous allez apprendre s’appliquera aussi aux applications pour poste de travail et pour smartphone.

Dans ce premier tutoriel, vous allez découvrir les objectifs de la série et de chaque service cloud Azure que vous utiliserez, ainsi que la configuration du projet Unity initial.

Dans le deuxième tutoriel, [Intégration du Stockage Azure](mr-learning-azure-02.md), vous commencerez par intégrer Stockage Azure comme solution de persistance pour l’application de démonstration. Vous découvrirez également les différences entre le stockage Blob et le stockage Table, vous préparerez les ressources de projet nécessaires et configurerez la scène. Pour finir, vous apprendrez à vérifier les opérations de lecture, de mise à jour et de suppression de données.

En poursuivant avec le troisième tutoriel, [Intégration d’Azure Custom Vision](mr-learning-azure-03.md), vous allez utiliser Azure Custom Vision pour entraîner et détecter des images dans l’application HoloLens 2. Le chapitre commence par la configuration de votre propre ressource Azure Custom Vision, la préparation des composants de la scène, et la mise en œuvre de l’entraînement et de la détection de vos propres images à partir de l’application.

Ensuite, vous passez au quatrième tutoriel, [Intégration d’Azure Spatial Anchors](mr-learning-azure-04.md), avec l’exploration du service Azure Spatial Anchors pour enregistrer et rechercher des emplacements, découvrir les concepts fondamentaux, préparer les ressources nécessaires, configurer la scène et commencer à utiliser la nouvelle fonctionnalité dans l’application.

Avec le cinquième tutoriel, [Intégration d’Azure Bot Service avec LUIS](mr-learning-azure-05.md), vous terminez en ajoutant à l’application une nouvelle méthode d’interaction utilisateur : le langage naturel ! Cette fonctionnalité sera réalisée avec Azure Bot Framework et LUIS (Language Understanding). Ce chapitre final vous fait découvrir les bases d’Azure Bot Service et, pour accélérer le processus, vous allez utiliser le composeur Bot Framework comme solution avec zéro code. Une fois le bot créé, vous allez l’intégrer dans la scène et l’exécuter avec l’application HoloLens 2 dans sa dernière version.

## <a name="application-goals"></a>Objectifs de l’application

Dans cette série de tutoriels, vous allez créer une application **HoloLens 2** capable de détecter des objets à partir d’images et de trouver leur emplacement spatial. Pour définir une terminologie du domaine, vous appelez à partir de maintenant ces entités des **objets suivis**.
L’utilisateur peut créer un **objet suivi** pour associer un ensemble d’images via la vision par ordinateur et/ou un emplacement spatial. Toutes les données doivent être conservées dans le cloud. De plus, certains aspects de l’application seront éventuellement contrôlés par le langage naturel via un bot.

### <a name="features"></a>Fonctionnalités

* Gestion de base des données et des images
* Entraînement et détection d’images
* Stockage d’un emplacement spatial et conseils pour ce stockage
* Assistant bot pour utiliser certaines fonctionnalités via le langage naturel

## <a name="azure-cloud-services"></a>Services cloud Azure

Pour implémenter les fonctionnalités ci-dessus, vous utiliserez les services **cloud Azure** suivants :

### <a name="azure-storage"></a>Stockage Azure

Vous allez utiliser [Stockage Azure](https://azure.microsoft.com/services/storage/) pour la solution de persistance. Il vous permet de stocker des données sur une table et de charger des données binaires volumineuses, comme des images.

### <a name="azure-custom-vision"></a>Azure Custom Vision

Avec [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (qui fait partie d’[Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)), vous pouvez associer à des *objets suivis* un ensemble d’images, entraîner un modèle Machine Learning sur l’ensemble d’images et détecter l’*objet suivi*.

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Pour stocker un emplacement d’*objet suivi* et donner des directions guidées pour le trouver, vous utilisez [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>Azure Bot Service

L’application est pilotée principalement par une interface utilisateur traditionnelle : vous utilisez donc [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) pour ajouter une personnalité et faire office de nouvelle méthode d’interaction.

## <a name="prerequisites"></a>Prérequis

>[!TIP]
>Si vous n’avez pas encore terminé la série de [tutoriels de démarrage](mr-learning-base-01.md), nous vous conseillons de le faire avant d’aller plus loin.

* PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)
* SDK Windows 10 (10.0.18362.0 ou version ultérieure)
* Capacité de programmation C# de base
* Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* Une webcam connectée si vous voulez tester depuis l’éditeur Unity
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020/2019 LTS installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté

> [!Important]
> Cette série de tutoriels prend en charge Unity 2020 LTS (actuellement 2020.3.x) si vous utilisez Open XR ou Plug-in XR Windows, ainsi qu’Unity 2019 LTS (actuellement 2019.4.x) si vous utilisez WSA hérité. Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.

## <a name="creating-and-preparing-the-unity-project"></a>Création et préparation du projet Unity

Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.

Suivez d’abord [Initialisation de votre projet et de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), qui inclut les étapes suivantes :

1. [Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *Azure Cloud Tutorials*
2. [Changement de plateforme de génération](mr-learning-base-02.md#switching-the-build-platform)
3. [Importation des ressources TextMeshPro Essential](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importation de Mixed Reality Toolkit et configuration du projet Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Création et configuration de la scène](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), et affectation d’un nom pertinent à la scène, par exemple *AzureCloudServices*

Ensuite, suivez les instructions de [Changement de l’option d’affichage de la reconnaissance spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour vérifier que le profil de configuration MRTK de votre scène est **DefaultHololens2ConfigurationProfile** et pour changer les options d’affichage du maillage de la reconnaissance spatiale en **Occlusion**.

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Installation des packages Unity intégrés et importation des ressources du tutoriel

[!INCLUDE[](includes/installing-packages-for-azure-cloud-services.md)]

## <a name="creating-and-preparing-the-scene"></a>Création et préparation de la scène

Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**. Tout en maintenant le bouton Ctrl enfoncé, cliquez sur **SceneController**, **RootMenu** et **DataManager** pour sélectionner les trois préfabriqués :

![Unity avec les préfabriqués SceneController, RootMenu et DataManager sélectionnés](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (prefab)** contient deux scripts, **SceneController (script)** et **AppDispatcher (script)** . Le composant de script **SceneController** contient plusieurs fonctions d’expérience utilisateur et facilite la fonctionnalité de capture de photos, **AppDispatcher** étant une classe helper pour autoriser les actions d’exécution sur le thread Unity principal.

**RootMenu (prefab)** est le préfabriqué d’interface utilisateur principal qui contient toutes les fenêtres d’interface utilisateur qui sont connectées l’une à l’autre via différents petits composants de script et qui contrôlent le flux général de l’interface utilisateur de l’application.

**DataManager (prefab)** est responsable de la communication avec le stockage Azure et il sera expliqué plus en détail dans le tutoriel suivant.

Les trois préfabriqués étant sélectionnés, faites-les maintenant glisser dans la fenêtre Hierarchy pour les ajouter à la scène :

![Unity avec les préfabriqués SceneController, RootMenu et DataManager nouvellement ajoutés toujours sélectionnés](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **RootMenu**, puis effectuer à nouveau un léger zoom arrière :

![Unity avec l’objet RootMenu sélectionné](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Si vous trouvez gênantes les grandes icônes de votre scène, par exemple les grandes icônes « T », vous pouvez les masquer en <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">basculant le gizmos</a> sur la position Off.

## <a name="configuring-the-scene"></a>Configuration de la scène

Dans cette section, vous allez connecter ensemble *SceneManager*, *DataManager* et *RootMenu* pour avoir une scène de travail prête pour le tutoriel suivant, [Intégration de Stockage Azure](mr-learning-azure-01.md).

### <a name="connect-the-objects"></a>Connecter les objets

Dans la fenêtre Hierarchy, sélectionnez l’objet **DataManager** :

![Unity avec l’objet DataManager sélectionné](images/mr-learning-azure/tutorial1-section6-step1-1.png)

Dans la fenêtre Inspector, recherchez le composant **DataManager (Script)**  : vous verrez un emplacement vide sur l’événement **On Data Manager Ready ()** . À présent, dans la fenêtre Hierarchy, faites glisser l’objet **SceneController** dans l’événement **On Data Manager Ready ()** .

![Unity avec l’écouteur d’événements DataManager ajouté](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Vous remarquerez que le menu déroulant de l’événement est devenu actif. Cliquez sur le menu déroulant et accédez à **SceneController** puis, dans le sous-menu, sélectionnez l’option **Init ()**  :

![Unity avec l’action d’événement DataManager ajoutée](images/mr-learning-azure/tutorial1-section6-step1-3.png)

Dans la fenêtre Hierarchy, sélectionnez l’objet **SceneController** ; dans l’inspecteur, vous trouvez le composant **SceneController** (script).

![Unity avec SceneController sélectionné](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Vous voyez que plusieurs champs ne sont pas remplis : nous allons changer cela. Déplacez l’objet **DataManager** depuis la hiérarchie vers le champ *Data Manager* et déplacez le GameObject **RootMenu** depuis la hiérarchie vers le champ *Main Menu*.

![Unity avec SceneController configuré](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Votre scène est maintenant prête pour les tutoriels suivants. N’oubliez pas de l’enregistrer dans votre projet.

## <a name="prepare-project-build-pipeline"></a>Préparer le pipeline de génération du projet

Alors que le projet doit encore être rempli avec du contenu, vous devez effectuer certaines préparations pour que le projet soit prêt à être généré pour **HoloLens 2**.

### <a name="1-add-additional-required-capabilities"></a>1. Ajouter des fonctionnalités supplémentaires nécessaires

Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :

![Ouverture des paramètres du projet dans Unity](images/mr-learning-azure/tutorial1-section7-step1-1.png)

Dans la fenêtre Project Settings, sélectionnez **Player**, puis **Publishing Settings** :

![Paramètres de publication Unity](images/mr-learning-azure/tutorial1-section7-step1-2.png)

Dans **Publishing Settings**, accédez à la section **Capabilities** et vérifiez bien que les fonctionnalités **InternetClient**, **Microphone** et **SpatialPerception**, que vous avez activées lors de la création du projet au début de ce tutoriel, sont activées. Activez ensuite les fonctionnalités **InternetClientServer**, **PrivateNetworkClientServer** et **Webcam** :

![Fonctionnalités Unity](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Déployer l’application sur votre HoloLens 2

Certaines des fonctionnalités que vous allez utiliser dans cette série de tutoriels ne peuvent pas s’exécuter dans l’éditeur Unity : cela signifie que vous devez être familiarisé avec le déploiement de l’application sur votre appareil HoloLens 2.

> [!TIP]
> Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Tutoriels de démarrage - Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Exécuter l’application sur votre HoloLens 2 et suivre les instructions dans l’application

> [!CAUTION]
> Comme tous les services Azure utilisent Internet, vérifiez que votre appareil y est connecté.

Quand l’application s’exécute sur votre appareil, acceptez l’accès aux fonctionnalités demandées suivantes :

* Microphone
* Appareil photo

Ces fonctionnalités sont nécessaires pour que des services comme *Chat Bot* et *Custom Vision* fonctionnent correctement.

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez découvert la série de tutoriels, les fonctionnalités que vous allez implémenter et la façon dont les services **cloud Azure** permettent la réalisation de votre application *HoloLens 2*. Vous avez ajouté les composants nécessaires dans le projet et préparé la scène pour cette série de tutoriels.

Dans la leçon suivante, vous allez utiliser Stockage Azure comme solution de persistance cloud pour stocker des données et des images.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 2. Intégration de Stockage Azure](mr-learning-azure-02.md)