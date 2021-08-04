---
title: Bien démarrer avec la communication à distance holographique de PC
description: Suivez ce cours pour découvrir comment diffuser en continu à distance des applications de réalité mixte de votre PC vers HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, communication à distance holographique sur PC, info-bulles, suivi oculaire
ms.localizationpriority: high
ms.openlocfilehash: 53ede3db405e6f6f4ccaa20ff35847ecc9081dca
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757351"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. Bien démarrer avec la communication à distance holographique de PC

Bienvenue dans les tutoriels HoloLens 2. Dans cette série de deux tutoriels, vous allez apprendre à créer une démonstration d’expérience de réalité mixte et une application PC de communication à distance holographique.

[Apprenez les bases de la communication à distance holographique.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

Dans ce tutoriel, vous allez découvrir comment créer une expérience de réalité mixte. Il présente les éléments d’interface utilisateur, la manipulation de modèle 3D, le découpage de modèle et les fonctionnalités de suivi oculaire.

Dans le second tutoriel, [Créer une application de communication à distance holographique](mr-learning-pc-holographic-remoting-02.md), vous allez apprendre à créer une application PC qui utilise la communication à distance holographique afin de streamer votre travail en cours vers le HoloLens et de le voir sans avoir à le créer en premier.

## <a name="objectives"></a>Objectifs

* Importer les ressources et configurer la scène
* Interaction avec des hologrammes en utilisant des éléments d’interface utilisateur et des boutons
* Configurer les objets 3D pour la fonctionnalité de découpage
* Apprendre à activer des info-bulles avec le suivi oculaire

## <a name="prerequisites"></a>Prérequis

* PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)
* Connaissances de base de la programmation en C++
* Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020/2019 LTS monté et le module Universal Windows Platform Build Support ajouté

Si vous n’avez pas une expérience de base avec Unity et MRTK, nous vous **recommandons vivement** de suivre la série de tutoriels [Bien démarrer](mr-learning-base-01.md) avant de continuer.

> [!IMPORTANT]
> * Cette série de didacticiels prend en charge Unity 2020 LTS (actuellement 2020.3.x), si vous utilisez Open XR et Unity 2019 LTS (actuellement 2019.4.x), si vous utilisez le WSA hérité. Cela remplace toutes les exigences de version de Unity mentionnées dans les conditions préalables référencées ci-dessus.

## <a name="creating-and-preparing-the-unity-project"></a>Création et préparation du projet Unity

Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.

Pour cela, suivez d’abord [Initialisation de votre projet et de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), ce qui inclut les étapes suivantes :

1. [Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *MRTK Tutorials*
2. [Changement de plateforme de génération](mr-learning-base-02.md#switching-the-build-platform)
3. [Importation des ressources TextMeshPro Essential](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importation de Mixed Reality Toolkit et configuration du projet Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Création et définition de la scène](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), et affectation d’un nom pertinent à la scène, par exemple **PC Holographic Remoting**

Ensuite, suivez les instructions fournies dans [Changement de l’option d’affichage de la reconnaissance spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour remplacer le profil de configuration MRTK de votre scène par **DefaultHoloLens2ConfigurationProfile**. Choisissez **Occlusion** dans les options d’affichage du maillage de la reconnaissance spatiale.

## <a name="importing-the-tutorial-assets"></a>Importation des ressources du tutoriel

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a>Création et préparation de la scène

Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.

Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**. Tout en maintenant la touche Ctrl enfoncée, cliquez sur les six préfabriqués ci-dessous.

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* Instructions
* ModelParent
* Plate-forme

![Unity avec des préfabriqués à ajouter à la scène sélectionnée](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

Faites glisser-déposer ces modèles du dossier Prefabs vers la **fenêtre Hierarchy**.

![Unity avec des préfabriqués nouvellement ajoutés encore sélectionnés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **ModelParent**, puis faire un léger zoom avant :

![Unity avec l’objet ModelParent dans le focus](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> Si vous trouvez gênantes les grandes icônes de votre scène, par exemple les grandes icônes « T », vous pouvez les masquer en <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">basculant les gizmos</a> en position Off.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuration des boutons pour faire fonctionner la scène

Dans cette section, vous allez ajouter des scripts dans la scène pour créer des événements de bouton illustrant les notions de base des fonctionnalités de changement et de découpage de modèle.

### <a name="1-configuring-the-interactable-script-component"></a>1. Configuration du composant Interactable (Script)

Dans la fenêtre Hierarchy, développez l’objet **ButtonParent**, puis sélectionnez **NextButton**. Dans la fenêtre Inspector, localisez le composant **Interactable (Script)** , puis cliquez sur l’icône **+** sous l’événement **OnClick ()** .

![Unity avec l’événement OnClick de NextButton ajouté](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

L’objet **NextButton** étant toujours sélectionné dans la fenêtre Hierarchy, cliquez sur l’objet **ButtonParent** et faites-le glisser de la fenêtre Hierarchy vers le champ vide **None (Object)** de l’événement que vous venez d’ajouter pour que l’objet ButtonParent soit à l’écoute des événements de type « clic sur un bouton » provenant de ce bouton :

![Unity avec l’écouteur d’événements OnClick de NextButton configuré](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

Cliquez sur la liste déroulante **No Function** du même événement. Sélectionnez ensuite **ViewButtonControl** > **NextModel ()** pour définir la fonction **NextModel ()** comme l’action à déclencher quand l’événement d’appui sur un bouton est déclenché par ce bouton :

![Unity avec le chemin de sélection d’action de l’événement OnClick de NextButton](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. Configuration des boutons restants

Pour chacun des boutons restants, effectuez le processus décrit ci-dessus pour affecter des fonctions aux événements **OnClick ()**  :

* Pour l’objet PreviousButton, affectez la fonction **ViewButtonControl** > **PreviousModel ()** .

* Pour ClippingButton, sélectionnez la fonction **ToggleButton** > **ToggleClipping ()** .

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. Configuration des composants View Button Control (Script) et Toggle Button (Script)

Vos boutons sont maintenant configurés pour illustrer les fonctionnalités de changement et de découpage de modèle. Il est temps d’ajouter des modèles 3D et des objets de découpage au script.

Six modèles 3D différents sont fournis à des fins de démonstration. Pour les exposer, développez ***ModelParentobject***.

L’objet ButtonParent étant toujours sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, recherchez le composant **View Button Control (Script)** , puis développez la variable **Models**.

Dans le champ **Size**, entrez le nombre de modèles 3D que vous aimeriez avoir dans votre scène. Dans ce cas, indiquez six. Des champs permettant d’ajouter de nouveaux modèles 3D sont créés.

![Unity avec les champs du composant de script ViewButtonControl](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

Faites glisser-déposer chaque objet enfant de l’objet ModelParent sur ces champs.

![Unity avec les champs du composant de script ViewButtonControl configurés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

Faites glisser-déposer l’objet **ClippingObjects** de la fenêtre Hierarchy sur le champ **Clipping Object** du composant **Toggle Button (Script)**
>[!NOTE]
>Restez dans l’objet ButtonParent.

![Unity avec les champs du composant de script ToggleButton configurés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

Dans la fenêtre Hierarchy, sélectionnez le préfabriqué **ClippingObjects** et activez-le dans la fenêtre Inspector pour activer les objets de découpage.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>Configuration des objets de découpage pour activer la fonctionnalité de découpage

Dans cette section, vous allez ajouter le renderer d’objets enfants de l’objet MarsCuriosityRover dans un objet de découpage individuel pour illustrer le découpage du modèle MarsCuriosityRover.

Dans la fenêtre Hierarchy, développez l’objet **ClippingObjects** pour exposer les trois objets de découpage que vous allez utiliser dans ce projet.

Pour configurer l’objet **ClippingSphere**, cliquez dessus, puis dans la fenêtre Inspector, recherchez le composant **Clipping Sphere (Script)** . Dans le champ Size, entrez le nombre de renderers à ajouter pour votre modèle 3D. Dans ce cas, entrez 10 pour les objets enfants de MarsCuriosityRover. Des champs permettant d’ajouter des renderers sont créés. Glissez-déposez les objets enfants du modèle MarsCuriosityRover sur ces champs.

![Unity avec les champs du composant de script ClippingSphere configurés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

Suivez le même processus et ajoutez les renderers d’objets enfants de MarsCuriosityRover aux objets **ClippingBox** et **ClippingPlane**.

Dans ce tutoriel, seul le modèle MarsCuriosityRover est utilisé pour illustrer la fonctionnalité de découpage. Il est possible d’ajouter des fonctionnalités de découpage à d’autres modèles, d’augmenter la taille du renderer et d’ajouter des renderers de maillage individuels.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>Configuration du suivi oculaire pour mettre en évidence les info-bulles

Dans cette section, nous allons examiner comment activer l’eye-tracking dans votre projet. Par exemple, vous allez implémenter les fonctionnalités nécessaires pour mettre en évidence les info-bulles attachées aux éléments de MarsCuriosityRover quand vous les regardez et les masquer quand vous détournez votre regard.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. Identifier les objets cibles et les info-bulles associées

Dans la fenêtre Hierarchy, sélectionnez l’objet ModelParent. Développez ***MarsCuriosity -> Rover** _ pour trouver les cinq éléments principaux du MarsCuriosityRover: _*POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.

* Observez les cinq objets info-bulles associés aux éléments de MarsCuriosityRover dans la fenêtre Hierarchy.
* Vous allez configurer ces objets pour les mettre en évidence quand vous regardez les éléments MarsCuriosityRover correspondants.

![Unity avec l’objet Rover sélectionné et développé](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. Implémenter les événements While Looking At Target () et On Look Away ()

Dans la fenêtre Hierarchy, sélectionnez l’objet **POI-Camera** _. Dans la fenêtre Inspector, recherchez le composant *Eye Tracking Target (Script)* , puis configurez les événements **While Looking At Target ()**  & **On Look Away ()** comme suit :

* Affectez au champ **None (Object)** l’objet **POI-Camera ToolTip**.
* Dans la liste déroulante **No Function** de l’événement **While Looking At Target ()** , sélectionnez **GameObject** > **SetActive (bool)** . Cochez la **case** située en dessous pour définir la mise en évidence de l’info-bulle comme l’action à déclencher quand vous regardez l’objet cible.

![Unity avec la configuration de l’événement EyeTrackingTarget WhileLookingAtTarget en cours](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* Suivez le même processus et cliquez sur la liste déroulante **No Function** du détecteur d’événements **On Look Away ()** . Sélectionnez ensuite **GameObject** > **SetActive (bool**), mais ne cochez pas la **case** pour définir le masquage de l’info-bulle comme l’action à déclencher quand vous détournez votre regard de l’objet cible.

![Unity avec l’événement EyeTrackingTarget OnLookAway configuré](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

Suivez le même processus et affectez aux événements **While Looking At Target ()**  & **On Look Away ()** les objets info-bulles qui correspondent aux éléments de **MarsCuriosityRover**.

Pour activer le suivi oculaire, suivez ces [instructions](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez appris à créer une expérience de réalité mixte illustrant les éléments d’interface utilisateur, la manipulation de modèle 3D, le découpage de modèle et les fonctionnalités de suivi oculaire. Les objets NextButton et PreviousButton introduits dans ce tutoriel vous ont permis d’explorer la visionneuse de modèle 3D. L’objet ClippingObjectButton vous a quant a lui permis d’activer des objets de découpage et de vous familiariser avec la fonctionnalité de découpage. Dans ce tutoriel, vous avez également examiné un élément de suivi oculaire pour activer la mise en évidence des info-bulles dans l’expérience.

Dans la leçon suivante, vous allez découvrir comment créer une application de communication à distance holographique pour PC et comment la connecter à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte.

> [!div class="nextstepaction"]
> [Leçon suivante : 2. Créer une application de communication à distance holographique](mr-learning-pc-holographic-remoting-02.md)