---
title: Utilisation du suivi oculaire
description: Ce cours vous montre comment utiliser le suivi oculaire dans votre application de réalité mixte avec Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, suivi oculaire
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982881"
---
# <a name="8-using-eye-tracking"></a>8. Utilisation du suivi oculaire

Dans ce tutoriel, vous allez voir comment activer le suivi oculaire (eye-tracking) pour HoloLens 2 et comment l’ajouter aux objets en vue de déclencher des actions lorsque l’utilisateur regarde ces objets.

> [!NOTE]
> Si vous déployez également ce projet sur HoloLens (1re génération), notez que le suivi oculaire est pris en charge uniquement sur HoloLens 2.

## <a name="objectives"></a>Objectifs

* Apprendre à activer le suivi oculaire pour HoleLens 2
* Apprendre à utiliser le suivi oculaire pour déclencher une action

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Activation du pointage du regard dans le fournisseur de regard

Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, sélectionnez l’onglet MixedRealityToolkit > **Input**, puis effectuez les étapes suivantes :

* Clonez **DefaultHoloLens2InputSystemProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_HoloLens2InputSystemProfile_.
* Développez la section **Pointers**.
* Clonez **DefaultMixedRealityPointerProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_MixedRealityPointerProfile_.
* Recherchez la section **Gaze Settings** (Paramètres du regard), puis cochez la case **Is Eye Tracking Enabled** (Activation du suivi oculaire).

![Composant MixedRealityToolkit d’Unity avec les profils nouvellement créés appliqués et le suivi du regard activé](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Pour obtenir un rappel de la façon de cloner des profils MRTK, vous pouvez consulter les instructions fournies dans [Configuration des profils MRTK](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Activation du suivi oculaire simulé pour l’éditeur Unity

Dans la fenêtre Hierarchy, sélectionnez l’objet **MixedRealityToolkit**. Ensuite, dans la fenêtre Inspector, accédez à l’onglet **Input**, puis :

* Développez la section **Input Data Providers** > **Input Simulation Service**.
* Clonez **DefaultMixedRealityInputSimulationProfile**, puis attribuez-lui un nom adapté, comme _GettingStarted_MixedRealityInputSimulationProfile_.
* Recherchez **Eye Gaze Simulation** et définissez **Default Eye Gaze Simulation Mode** sur **Camera Forward Axis**

![Unity avec l’objet TextMeshPro sélectionné](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Ajout du suivi oculaire aux objets

Dans la fenêtre Hiérarchie, développez les **boutons** > **RoverExplorerButtons**, puis sélectionnez les trois objets bouton enfants :

![Unity avec l’objet Bouton sélectionné](images/mr-learning-base/base-08-section4-step1-1.png)

Avec les trois objets Bouton toujours sélectionnés, dans la fenêtre Inspecteur, utilisez le bouton **Ajouter composant** pour ajouter le composant **EyeTrackingTarget** à tous les objets sélectionnés :

![Unity avec l’objet TextMeshPro sélectionné et des composants ajoutés](images/mr-learning-base/base-08-section4-step1-2.png)

Dans la fenêtre Hiérarchie, développez **RoverExplorer** > **Boutons** > **Indicateurs** > **SeeItSayItLabel** > **TextMeshPro**

Ensuite, dans la fenêtre Hiérarchie, sélectionnez l’objet bouton **Indicateurs**, puis configurez le composant **EyeTrackingTarget** comme suit :

* Dans la section d’événement **On Look At Start ()**
  * Cliquez sur la petite icône **+** pour ajouter un autre événement.
  * Assignez l’objet **TextMeshPro** à partir du bouton **Indicateurs** au champ **Aucun (objet)**
  * Dans la liste déroulante **No Function**, sélectionnez **TextMeshPro** > **float fontSize** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
  * Définissez l’argument sur **0.06** pour augmenter la taille de police actuelle (0.04) de 50 %.
* Dans la section d’événement **On Look Away ()**
  * Cliquez sur la petite icône **+** pour ajouter un autre événement.
  * Assignez l’objet **TextMeshPro** à partir du bouton **Indicateurs** au champ **Aucun (objet)**
  * Dans la liste déroulante **No Function**, sélectionnez **TextMeshPro** > **float fontSize** pour mettre à jour cette valeur de propriété lorsque l’événement est déclenché.
  * Définissez l’argument sur **0.04** pour rétablir la taille de la police à 0.04.

![Unity avec l’objet Hints TextMeshPro sélectionné et le composant EyeTrackingTarget configuré](images/mr-learning-base/base-08-section4-step1-3.png)

**Répétez** cette étape pour l’objet bouton **Éclater** et **Réinitialiser** pour configurer le suivi oculaire des boutons restants.

Si vous passez maintenant en mode jeu, puis maintenez enfoncé le bouton de droite tout en déplaçant la souris jusqu’à ce que le regard atteigne l’un des boutons, vous verrez que la taille de police du texte augmente de 50 % et revient à sa taille d’origine lorsque l’utilisateur regarde ailleurs :

![Vue partagée du mode Play d’Unity avec le suivi atteignant Eye Tracking Target - Étiquette du bouton Explode](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez vu comment activer le suivi oculaire pour HoloLens 2 et comment l’ajouter aux objets en vue de déclencher des actions lorsque l’utilisateur regarde ces objets.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 9. Utilisation des commandes vocales](mr-learning-base-09.md)
