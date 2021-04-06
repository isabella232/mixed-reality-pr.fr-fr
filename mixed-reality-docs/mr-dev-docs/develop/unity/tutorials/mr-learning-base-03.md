---
title: Tutoriels de démarrage - 3. Configuration des profils MRTK
description: Ce cours vous montre comment configurer les profils Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, reconnaissance spatiale
ms.localizationpriority: high
ms.openlocfilehash: 3b44ba6c4eac3cf7b42d15c8fb19d42676b10a4a
ms.sourcegitcommit: 5017f309827c1d20df4ce656d105a1a49ba7942c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106011138"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Configuration des profils MRTK

## <a name="overview"></a>Vue d’ensemble

Dans ce tutoriel, vous allez voir comment personnaliser et configurer les profils MRTK.

Les <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles.md" target="_blank">profils MRTK</a> sont une arborescence de profils imbriqués qui constituent les informations de configuration déterminant comment les systèmes et les fonctionnalités de MRTK doivent être initialisés. Le profil de plus haut niveau, le profil de configuration, contient des profils imbriqués pour chacun des systèmes principaux. Chaque profil imbriqué est conçu pour configurer le comportement de son système correspondant.

Cet exemple va vous montrer comment masquer le maillage de la reconnaissance spatiale en modifiant les paramètres de l’observateur de maillage spatial. Vous pouvez cependant suivre ces mêmes principes pour personnaliser des paramètres ou des valeurs dans les profils MRTK.

Comme vous en avez fait l’expérience quand vous avez déployé votre projet sur votre HoloLens 2 dans le [tutoriel précédent](mr-learning-base-02.md#congratulations), le maillage de <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">reconnaissance spatiale</a> est un ensemble de mailles représentant la géométrie de l’environnement. C’est une visualisation utile à voir initialement, mais elle est généralement désactivée pour éviter de distraire visuellement l’utilisateur et d’impacter les performances en raison des ressources nécessaires à son affichage.

## <a name="objectives"></a>Objectifs

* Apprendre à personnaliser et à configurer des profils MRTK
* Apprendre à masquer le maillage de reconnaissance spatiale

## <a name="changing-the-spatial-awareness-display-option"></a>Changement de l’option d’affichage de la reconnaissance spatiale

Les principales étapes à suivre pour masquer le maillage de la reconnaissance spatiale sont les suivantes :

1. Cloner le profil de configuration par défaut
2. Activer le système de reconnaissance spatiale
3. Cloner le profil système de reconnaissance spatiale par défaut
4. Cloner le profil d’observateur de maillage de reconnaissance spatiale par défaut
5. Changer la visibilité du maillage de reconnaissance spatiale

> [!NOTE]
> Par défaut, les profils MRTK ne sont pas modifiables. Il s’agit des modèles de profil par défaut que vous devez cloner avant de pouvoir les modifier. Il existe plusieurs couches de profils imbriquées. Par conséquent, il est courant de cloner et de modifier plusieurs profils lors de la configuration d’un ou plusieurs paramètres.

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>Félicitations

Dans ce tutoriel, vous avez vu comment cloner, personnaliser et configurer les profils et les paramètres MRTK.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 4. Positionnement des objets dans la scène](mr-learning-base-04.md)