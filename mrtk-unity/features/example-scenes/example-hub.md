---
title: Hub d’exemples MRTK
description: Vue d’ensemble des exemples de scènes dans MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 2b7e1234ed79a99e826184e42c319f84582ff23a
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757050"
---
# <a name="mrtk-examples-hub"></a>Hub d’exemples MRTK

![Hub d’exemples MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

MRTK exemple Hub est une scène Unity qui facilite l’expérience dans plusieurs scènes. Elle utilise le système de scène de MRTK pour charger & décharger les scènes.

**MRTKExamplesHub. Unity** est la scène de conteneur qui a des composants partagés, y compris ``MixedRealityToolkit`` et ``MixedRealityPlayspace`` . La scène **MRTKExamplesHubMainMenu. Unity** contient les boutons de cube.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>téléchargez l’application à partir de Microsoft Store dans HoloLens 2
si vous avez HoloLens 2 appareil, vous pouvez télécharger et installer directement l’application sur votre appareil.

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>Prérequis

MRTK exemple Hub utilise le [service de transition de scène](../extensions/scene-transition-service.md) et les scripts associés. si vous utilisez MRTK via des packages unity, importez **Microsoft. MixedReality. Shared Computer Toolkit. Unity. extensions. x.x.** . x. x. pour Unity qui fait partie des [packages de version](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Si vous utilisez MRTK via le clone du référentiel, vous devez déjà disposer du dossier **MRTK/extensions** dans votre projet.

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub Scene et le système de scène

Ouvrez **MRTKExamplesHub. Unity** qui se trouve à `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` l’emplacement est une scène vide avec MixedRealityToolkit, MixedRealityPlayspace et LoadHubOnStartup. Cette scène est configurée pour utiliser le système de scène de MRTK. Cliquez `MixedRealitySceneSystem` sous MixedRealityToolkit. Elle affiche les informations du système de scène dans le panneau de l’inspecteur.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

En bas de l’inspecteur, il affiche la liste des scènes définies dans le profil de système de scène. Vous pouvez cliquer sur les noms des scènes pour les charger/décharger.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Exemple de chargement de la scène _MRTKExamplesHub_ en cliquant sur le nom de la scène dans la liste.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Exemple de chargement de la scène _HandInteractionExamples_ .
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Exemple de chargement de plusieurs scènes.

## <a name="running-the-scene"></a>Exécution de la scène

La scène fonctionne dans le mode jeu de Unity et sur l’appareil. Exécutez la scène **MRTKExamplesHub** dans l’éditeur Unity et utilisez la simulation d’entrée de MRTK pour interagir avec le contenu de la scène. Pour générer et déployer, il vous suffit de créer une scène **MRTKExamplesHub** avec d’autres scènes incluses dans la liste du système de scène. l’inspecteur facilite également l’ajout de scènes à la Paramètres de génération. dans le Paramètres de génération, assurez-vous que **MRTKExamplesHub** scene est en haut de la liste à l’index 0.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Comment MRTKExamplesHub charge une scène

Dans la scène **MRTKExamplesHub** , vous pouvez trouver ``ExamplesHubButton`` Prefab.
Il existe un objet **FrontPlate** dans le Prefab qui contient ``Interactable`` .
À l’aide des ``OnClick()`` événements et de l' ``OnTouch()`` événement, il déclenche la fonction **LoadContent ()** du script **LoadContentScene** .
Dans l’inspecteur du script **LoadContentScene** , vous pouvez définir le nom de la scène à charger.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

Le script utilise la fonction LoadContent () du système de scène pour charger la scène.
Pour plus d’informations, reportez-vous à la page [système de scène](../scene-system/scene-system-getting-started.md) .

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Retour à la scène du menu principal

Pour revenir à la scène du menu principal (MRTKExamplesHubMainMenu Scene), vous pouvez utiliser la même méthode système de scène `LoadContent()` . **ToggleFeaturesPanelExamplesHub. Prefab** fournit le bouton « démarrage » qui contient le script **LoadContentScene** . Utilisez ce Prefab ou un bouton Accueil personnalisé dans chaque scène pour permettre à l’utilisateur de revenir à la scène principale. Vous pouvez placer **ToggleFeaturesPanelExamplesHub. Prefab** dans la scène **MRTKExamplesHub** pour le rendre toujours visible, car **MRTKExamplesHub** est une scène de conteneur partagée. Veillez à masquer/désactiver **ToggleFeaturesPanel. Prefab** dans chaque exemple de scène.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Ajout de boutons supplémentaires

Dans l’objet **CubeCollection** , dupliquez (ou ajoutez) _ExampleHubButton_ prefabs, puis cliquez sur **mettre à jour la collection** dans le `GridObjectCollection` .
La disposition du cylindre sera mise à jour en fonction du nouveau nombre total de boutons.
Pour plus d’informations, reportez-vous à la page [collection d’objets](../ux-building-blocks/object-collection.md) .

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Après avoir ajouté les boutons, mettez à jour le nom de la scène dans le script **LoadContentScene** (comme expliqué ci-dessus).
Ajoutez des scènes supplémentaires au profil du système de scène.
