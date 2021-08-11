---
title: Azure Spatial Anchors pour Android et iOS
description: Suivez ce cours pour découvrir comment déployer un projet Unity avec Mixed Reality Toolkit (MRTK) et Azure Spatial Anchors sur Android et iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, android, ios, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6e9ae377a11d74fd9cdfca7ddb0379542d365e3365bdf07319bc8580b2e87420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215802"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Azure Spatial Anchors pour Android et iOS

Dans ce tutoriel, vous allez découvrir comment créer votre projet pour des appareils Android et iOS à l’aide des packages AR Foundation, ARCore XR Plugin et ARKit XR Plugin.

## <a name="objectives"></a>Objectifs

* Apprendre à générer votre projet sur votre appareil Android à l’aide des packages AR Foundation et ARCore XR Plugin de Unity
* Apprendre à générer votre projet sur votre appareil iOS à l’aide des packages AR Foundation et ARKit XR Plugin de Unity

## <a name="installing-inbuilt-unity-packages"></a>Installation de packages Unity intégrés

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Configurer MRTK pour l’appareil photo AR Foundation

Dans cette section, vous allez découvrir comment configurer MRTK pour le déploiement sur un appareil mobile.

Dans la fenêtre de hiérarchie, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre de l’inspecteur, sélectionnez l’onglet **Camera**, clonez le profil de la caméra et attribuez-lui un nom pertinent, par exemple **AzureSpatialAnchors_ARCameraProfile** :

![Unity avec le profil nouvellement créé ARCameraProfile sélectionné](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Pour vous rappeler comment cloner des profils MRTK, vous pouvez consulter les instructions fournies dans [Configuration des profils Mixed Reality Toolkit](mr-learning-base-03.md).

Avec l’onglet **Caméra** toujours sélectionné dans la fenêtre Inspecteur, développez les **Fournisseurs des paramètres de la caméra**, puis cliquez sur "-" pour supprimer le **Paramètre de la caméra Windows Mixed Reality** ou le **Paramètre de la caméra Windows Mixed Reality SDK XR** :

![Profil ARCameraProfile d’Unity avec ajout d’un nouveau fournisseur de données ](images/mr-learning-asa/asa-05-section2-step1-2.png)

et cliquez sur le bouton **+ Ajouter un fournisseur de paramètres de caméra**, puis développez le **Nouveau fournisseur de données** que vous venez d’ajouter :

![Caméra de réalité augmentée ajoutée pour Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

À l’aide de la liste déroulante **Type**, sélectionnez le type **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings** :

![Profil ARCameraProfile d’Unity avec le chemin vers la sélection du type de fournisseur de données](images/mr-learning-asa/asa-05-section2-step1-4.png)

Mettre à jour les définitions de script UnityAR MRTK en appelant l’élément de menu : **Mixed Reality** > **Toolkit** > **Utilitaires** > **UnityAR** > Mise à jour des définitions de script

## <a name="building-your-application-to-your-android-device"></a>Génération de votre application sur votre appareil Android

Dans cette section, vous allez découvrir comment configurer votre projet pour le générer et le déployer sur un appareil Android.

Dans le menu Unity, sélectionnez **File** > **Build Settings...** pour ouvrir la fenêtre Build Settings, puis basculez vers la plateforme Android :

![Fenêtre Build Settings d’Unity avec la plateforme Android sélectionnée](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Pour vous rappeler comment changer de plateforme de génération, consultez les instructions fournies dans [Changement de la plateforme de génération](mr-learning-base-02.md#switching-the-build-platform).

Fermez la fenêtre Build Settings.

Dans le menu Unity, sélectionnez **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer le projet pour MRTK** pour ouvrir la fenêtre **MRTK Project Configurator**, vérifiez que toutes les options sont sélectionnées, puis cliquez sur le bouton **Appliquer** pour appliquer les paramètres :

![MRTK Project Configurator Unity 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

Dans le menu Unity, sélectionnez **Edit** > **Project Settings...** pour ouvrir la fenêtre Player Settings, recherchez la section **Player** >  **Other Settings**, sélectionnez **Vulkan** et supprimez-le en cliquant sur le symbole **« - »**  :

![Fenêtre Other Settings d’Unity avec Vulcan sélectionné](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

Dans la fenêtre Build Settings, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste des scènes de la build (**Scenes In Build**). Ensuite, utilisez un câble USB pour connecter votre appareil Android à votre ordinateur et sélectionnez-le dans la liste déroulante **Run Device** :

![Fenêtre Build Settings d’Unity avec la scène ajoutée et Run Device sélectionné](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Si votre appareil n’apparaît pas dans la liste déroulante Run Device, vous devrez peut-être appuyer sur le bouton Refresh à côté de la liste déroulante.

Dans la fenêtre Build Settings, cliquez sur le bouton **Build And Run** (Générer et exécuter) pour ouvrir la fenêtre Build Android.

Choisissez un emplacement approprié où stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, attribuez un nom pertinent à l’apk, par exemple _MRTKTutorials-AzureSpatialAnchors_, puis cliquez sur le bouton **Save** pour démarrer le processus de génération :

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Save - Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> Si vous recevez une erreur dans la fenêtre Unity Console relative aux modules Android SDK, NDK ou JDK, vous devez ouvrir Unity Hub et installer les modules Android Build Support associés.

Une fois le processus de génération terminé, vos applications doivent se charger automatiquement sur votre appareil Android.

## <a name="building-your-application-to-your-ios-device"></a>Génération de votre application sur votre appareil iOS

Dans cette section, vous allez découvrir comment configurer votre projet pour le générer et le déployer sur votre appareil iOS.

Dans le menu Unity, sélectionnez **File** > **Build Settings...** pour ouvrir la fenêtre Build Settings et basculez vers la plateforme iOS :

![Fenêtre Build Settings d’Unity avec iOS sélectionné](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Pour vous rappeler comment changer de plateforme de génération, consultez les instructions fournies dans [Changement de la plateforme de génération](mr-learning-base-02.md#switching-the-build-platform).

Fermez la fenêtre Build Settings.

Dans le menu Unity, sélectionnez **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer le projet pour MRTK** pour ouvrir la fenêtre **MRTK Project Configurator**, vérifiez que toutes les options sont sélectionnées, puis cliquez sur le bouton **Appliquer** pour appliquer les paramètres :

![Fenêtre MRTK Project Configurator d’Unity - iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

Dans le menu Unity, sélectionnez **Edit** > **Project Settings...** pour ouvrir la fenêtre Player Settings, recherchez la section **Player** >  **Other Settings**, et décochez la case **Strip Engine Code** (Supprimer le code du moteur) :

![Fenêtre Other Settings d’Unity avec Strip Engine Code désactivé](images/mr-learning-asa/asa-05-section4-step1-3.png)

Fermez la fenêtre Player Settings et rouvrez la fenêtre **Build Settings**.

Dans la fenêtre Build Settings, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste des scènes de la build (**Scenes In Build**) :

![Fenêtre Build Settings d’Unity avec une scène ajoutée](images/mr-learning-asa/asa-05-section4-step1-4.png)

Dans la fenêtre Build Settings, cliquez sur le bouton **Build** pour ouvrir la fenêtre Build iOS.

Choisissez un emplacement approprié où stocker votre projet Xcode, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _MRTKTutorials-AzureSpatialAnchors_, puis cliquez sur le bouton **Select Folder** pour démarrer le processus de génération :

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Save - iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

Une fois le processus de génération terminé, suivez les instructions fournies dans [Exporter le projet Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) pour découvrir comment déployer votre projet Xcode sur votre appareil iOS.

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez appris à générer votre projet pour des appareils Android et iOS à l’aide des packages AR Foundation, ARCore XR Plugin et ARKit XR Plugin.
