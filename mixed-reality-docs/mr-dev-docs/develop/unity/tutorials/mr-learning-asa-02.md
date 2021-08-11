---
title: Bien démarrer avec Azure Spatial Anchors
description: Suivez ce cours pour découvrir comment utiliser Azure Spatial Anchors pour ancrer des objets dans une application de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure
ms.localizationpriority: high
ms.openlocfilehash: 414788d5410614c341b10ddefb6b99896c403f2e6232c9cec77987f1417e8743
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216047"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Bien démarrer avec Azure Spatial Anchors

Dans ce tutoriel, vous allez découvrir les différentes étapes nécessaires pour démarrer et arrêter une session Azure Spatial Anchors, et pour créer, charger et télécharger des ancres spatiales Azure sur un appareil.

## <a name="objectives"></a>Objectifs

* Découvrir les principes de base du développement avec Azure Spatial Anchors pour HoloLens 2
* Apprendre à créer des ancres spatiales et à les récupérer à partir d’Azure

## <a name="creating-and-preparing-the-unity-project"></a>Création et préparation du projet Unity

Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.

Suivez d’abord [Initialisation de votre projet et déploiement de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), qui inclut les étapes suivantes :

1. [Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *MRTK Tutorials*
2. [Changement de plateforme de génération](mr-learning-base-02.md#switching-the-build-platform)
3. [Importation des ressources TextMeshPro Essential](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importation de Mixed Reality Toolkit et configuration du projet Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Création et configuration de la scène](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), et affectation d’un nom pertinent à la scène, par exemple *AzureSpatialAnchors*

Ensuite, suivez les instructions de [Changement de l’option d’affichage de la reconnaissance spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour vérifier que le profil de configuration MRTK de votre scène est **DefaultHoloLens2ConfigurationProfile** et pour changer les options d’affichage du maillage de la reconnaissance spatiale en **Occlusion**.

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Installation des packages Unity intégrés et importation des ressources du tutoriel

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a>Préparation de la scène

Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, puis cliquez sur les préfabriqués suivants et faites-les glisser dans la fenêtre Hierarchy pour les ajouter à votre scène :

* Préfabriqués **ButtonParent**
* Préfabriqués **DebugWindow**
* Préfabriqués **Instructions**
* Préfabriqués **ParentAnchor**

![Unity avec des préfabriqués nouvellement ajoutés sélectionnés](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Si vous trouvez gênantes les grandes icônes de votre scène, par exemple les grandes icônes « T », vous pouvez les masquer en <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">basculant les gizmos</a> en position Off, comme le montre l’image ci-dessus.

Sélectionnez l’objet **MixedRealityToolkit** dans la fenêtre Hiérarchie, utilisez le bouton **Ajouter un composant** dans la fenêtre Inspecteur pour ajouter les composants suivants :

* AR Anchor Manager (Script)
* DisableDiagnosticsSystem (Script)

![Objet MixedRealityToolkit d’Unity avec les composants AR Anchor Manager et DisableDiagnosticsSystem ajoutés ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> Il existe un problème connu avec ASA v2.9.0 et v2.10.0-preview.1 qui requiert que deux objets supplémentaires soient placés dans la scène. Utilisez le bouton **Ajouter un composant** dans la fenêtre Inspecteur pour ajouter un gestionnaire de caméra AR (script) et une session AR (script) à l’objet **MixedRealityToolkit**. Assurez-vous de désactiver la caméra qui est créée automatiquement lors de l’ajout du gestionnaire de caméra (script) en décocher la case en regard de l’objet Camera dans la fenêtre Inspecteur. Ce problème sera traité dans la version complète d’ASA v2.10.0.
>

> [!NOTE]
> Lorsque vous ajoutez le composant AR Anchor Manager (script), le composant AR Session Origin (script) est ajouté automatiquement, car il est requis par le composant AR Anchor Manager (script).

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuration des boutons pour faire fonctionner la scène

Dans cette section, vous allez ajouter des scripts à la scène pour créer une série d’événements de bouton qui montrent le comportement de base des ancres locales et des ancres spatiales Azure dans une application.

Dans la fenêtre Hierarchy, développez l’objet **ButtonParent** et sélectionnez le premier objet enfant nommé **StartAzureSession**, puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :

* Affectez l’objet **ParentAnchor** en tant qu’écouteur pour l’événement On Click () en le faisant glisser de la fenêtre Hierarchy dans le champ **None (Object)**
* Dans la liste déroulante **No Function**, sélectionnez **AnchorModuleScript** > **StartAzureSession ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.

![Unity avec l’événement OnClick du bouton StartAzureSession configuré](images/mr-learning-asa/asa-02-section5-step1-1.png)

Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **StopAzureSession**, puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :

* Affectez l’objet **ParentAnchor** en tant qu’écouteur pour l’événement On Click () en le faisant glisser de la fenêtre Hierarchy dans le champ **None (Object)**
* Dans la liste déroulante **No Function**, sélectionnez **AnchorModuleScript** > **StopAzureSession ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.

![Unity avec l’événement OnClick du bouton StopAzureSession configuré](images/mr-learning-asa/asa-02-section5-step1-2.png)

Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **CreateAzureAnchor**, puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :

* Affectez l’objet **ParentAnchor** en tant qu’écouteur pour l’événement On Click () en le faisant glisser de la fenêtre Hierarchy dans le champ **None (Object)**
* Dans la liste déroulante **No Function**, sélectionnez **AnchorModuleScript** > **CreateAzureAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.
* Affectez l’objet **ParentAnchor** au champ vide **None (Game Object)** pour en faire l’argument de la fonction CreateAzureAnchor ().

![Unity avec l’événement OnClick du bouton CreateAzureAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-3.png)

Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **RemoveLocalAnchor**, puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :

* Affectez l’objet **ParentAnchor** en tant qu’écouteur pour l’événement On Click () en le faisant glisser de la fenêtre Hierarchy dans le champ **None (Object)**
* Dans la liste déroulante **No Function**, sélectionnez **AnchorModuleScript** > **RemoveLocalAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.
* Affectez l’objet **ParentAnchor** au champ vide **None (Game Object)** pour en faire l’argument de la fonction RemoveLocalAnchor ().

![Unity avec l’événement OnClick du bouton RemoveLocalAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-4.png)

Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **FindAzureAnchor**, puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :

* Affectez l’objet **ParentAnchor** en tant qu’écouteur pour l’événement On Click () en le faisant glisser de la fenêtre Hierarchy dans le champ **None (Object)**
* Dans la liste déroulante **No Function**, sélectionnez **AnchorModuleScript** > **FindAzureAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.

![Unity avec l’événement OnClick du bouton FindAzureAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-5.png)

Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **DeleteAzureAnchor**, puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :

* Affectez l’objet **ParentAnchor** en tant qu’écouteur pour l’événement On Click () en le faisant glisser de la fenêtre Hierarchy dans le champ **None (Object)**
* Dans la liste déroulante **No Function**, sélectionnez **AnchorModuleScript** > **DeleteAzureAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.

![Unity avec l’événement OnClick du bouton DeleteAzureAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Connexion de la scène à la ressource Azure

Dans la fenêtre Hierarchy, sélectionnez l’objet **ParentAnchor**, puis dans la fenêtre Inspector, recherchez le composant **Spatial Anchor Manager (Script)** . Configurez la section **Credentials** avec les informations d’identification du compte Azure Spatial Anchors créé dans le cadre des [prérequis](mr-learning-asa-01.md#prerequisites) pour cette série de tutoriels :

* Dans le champ **Spatial Anchors Account ID**, collez la valeur **Account ID** de votre compte Azure Spatial Anchors.
* Dans le champ **Spatial Anchors Account Key**, collez la valeur **Access Key** (primaire ou secondaire) de votre compte Azure Spatial Anchors.
* Dans le champ **Spatial Anchors Account Domain**, collez la valeur **Account Domain** de votre compte Azure Spatial Anchors.

![Unity avec Spatial Anchor Manager configuré](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Essai des comportements de base d’Azure Spatial Anchors

Azure Spatial Anchors ne peut pas s’exécuter dans Unity : pour tester la fonctionnalité Azure Spatial Anchors, vous devez donc générer et déployer l’application sur votre appareil.

> [!TIP]
> Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, reportez-vous aux instructions fournies dans [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Quand l’application s’exécute sur votre appareil, suivez les instructions à l’écran affichées dans le panneau des instructions du tutoriel Azure Spatial Anchors :

1. Déplacer le cube vers un autre emplacement
2. Démarrer la session Azure
3. Créer une ancre Azure (crée une ancre à l’emplacement du cube)
4. Arrêter la session Azure
5. Supprimer l’ancre locale (permet à l’utilisateur de déplacer le cube)
6. Déplacer le cube ailleurs
7. Démarrer la session Azure
8. Rechercher l’ancre Azure (positionne le cube à l’emplacement de l’étape 3)
9. Supprimer l’ancre Azure
10. Arrêter la session Azure

![Unity avec l’objet Instructions sélectionné](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure Spatial Anchors utilise Internet pour enregistrer et charger les données des ancres : veillez donc à ce que votre appareil soit connecté à Internet.

## <a name="anchoring-an-experience"></a>Ancrage d’une expérience

Dans les sections précédentes, vous avez découverts les principes de base d’Azure Spatial Anchors. Nous avons utilisé un cube pour représenter et visualiser l’objet de jeu parent avec l’ancre attachée. Dans cette section, vous allez découvrir comment ancrer une expérience complète en la plaçant en tant qu’enfant de l’objet ParentAnchor.

Dans la fenêtre Hierarchy, sélectionnez l’objet **ParentAnchor**, puis dans la fenêtre Inspector, configurez les composants **Transform** comme ceci :

* Affectez 1.1 à **Scale X**.
* Affectez 1.1 à **Scale Z**.

![Unity avec l’objet ParentAnchor sélectionné, positionné et mis à l’échelle](images/mr-learning-asa/asa-02-section8-step1-1.png)

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover**, puis cliquez sur le préfabriqué **RoverExplorer_Complete** et faites-le glisser dans la fenêtre Hierarchy pour l’ajouter à la scène :

![Unity avec le préfabriqué nouvellement ajouté RoverExplorer_Complete sélectionné](images/mr-learning-asa/asa-02-section8-step1-2.png)

L’objet RoverModule_Complete que vous venez d’ajouter étant toujours sélectionné dans la fenêtre Hierarchy, faites-le glisser sur l’objet **ParentAnchor** pour en faire un enfant de l’objet ParentAnchor :

![Unity avec l’objet RoverExplorer_Complete défini comme enfant de ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

Si vous regénérez le projet et déployez l’application sur votre appareil, vous pouvez à présent repositionner l’intégralité de l’expérience Rover Explorer en déplaçant le cube redimensionné.

> [!TIP]
> Il existe un grand nombre de flux d’expériences utilisateur pour les expériences de repositionnement, notamment l’utilisation d’un objet de repositionnement (comme le cube utilisé dans ce tutoriel), l’utilisation d’un bouton pour basculer un contrôle de limites qui entoure l’expérience, l’utilisation de gizmos de position et de rotation, etc.

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez découverts les principes de base d’Azure Spatial Anchors. Ce tutoriel a introduit plusieurs boutons qui vous permettent d’explorer les différentes étapes nécessaires pour démarrer et arrêter une session Azure Spatial Anchors, et pour créer, charger et télécharger des ancres spatiales Azure sur un appareil.

Dans le tutoriel suivant, vous allez apprendre à enregistrer des ID d’ancre Azure dans votre HoloLens 2 pour pouvoir les récupérer même après le redémarrage de l’application, puis à transférer des ID d’ancre entre plusieurs appareils pour obtenir un alignement spatial.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 3. Enregistrement, récupération et partage d’ancres spatiales Azure](mr-learning-asa-03.md)
