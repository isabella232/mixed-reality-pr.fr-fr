---
title: Affichage du feedback Azure Spatial Anchors
description: Suivez ce cours pour découvrir comment afficher le feedback Azure Spatial Anchors dans une application de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, sessions, éléments de feedback
ms.localizationpriority: high
ms.openlocfilehash: 65a814019909ecacffdd454171075c68497dae1b2123804e07ced1d7e100fdd8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215664"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Affichage du feedback Azure Spatial Anchors

Dans ce tutoriel, vous allez voir comment fournir aux utilisateurs un feedback sur la découverte des ancres, leurs événements et leur état à l’aide d’Azure Spatial Anchors (ASA).

## <a name="objectives"></a>Objectifs

* Apprendre à configurer un panneau d’interface utilisateur qui affiche des informations essentielles sur la session ASA en cours
* Connaître les éléments de feedback que le SDK ASA met à la disposition des utilisateurs

## <a name="setting-up-asa-feedback-panel"></a>Apprendre à configurer un panneau de feedback ASA

Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **Instructions** > **TextContent**. Sélectionnez **3D Object** > **Text - TextMeshPro** pour créer un objet de texte TextMeshPro en tant qu’enfant de l’objet Instructions > TextContent :

![Unity avec l’objet TextMeshPro nouvellement créé sélectionné](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Pour faciliter l’utilisation de votre scène, désactivez <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> pour l’objet ParentAnchor en cliquant sur l’icône œil à gauche de l’objet. Ceci masque l’objet dans la fenêtre Scene sans changer sa visibilité dans le jeu.

Attribuez à l’objet Text (TMP) que vous venez de créer le nom de **Feedback**, puis, dans la fenêtre Inspector, modifiez sa position et sa taille de manière à ce qu’il soit placé bien en dessous du texte d’instruction, par exemple :

* Remplacez la valeur **Pos Y** du composant Rect Transform par -0.24.
* Remplacez la valeur **Width** du composant Rect Transform par 0.555.
* Remplacez la valeur **Height** du composant Rect Transform par 0.1.

Choisissez ensuite les propriétés de police de sorte que le texte s’ajuste correctement dans la zone de texte, par exemple :

* Pour le composant TextMeshPro - Text, configurez la valeur de **Font Style** sur Bold.
* Pour le composant TextMeshPro - Text, configurez la valeur de **Font Size** sur 0.17.
* Pour le composant TextMeshPro - Text, configurez la valeur de **Alignment** sur Center et Middle.

![Unity avec un objet Feedback configuré](images/mr-learning-asa/asa-04-section1-step1-2.png)

Dans la fenêtre Hierarchy, sélectionnez l’objet **Feedback**, puis, dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Anchor Feedback Script (Script)** et le configurer de la façon suivante :

* Affectez l’objet **Feedback** au champ **Feedback Text** du composant **Anchor Feedback Script (Script)** .

![Unity avec le composant Anchor Feedback Script configuré](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez vu comment créer un panneau d’interface utilisateur. Celui-ci affiche l’état actuel de l’expérience Azure Spatial Anchors pour fournir aux utilisateurs du feedback en temps réel.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 5. Azure Spatial Anchors pour Android et iOS](mr-learning-asa-05.md)
