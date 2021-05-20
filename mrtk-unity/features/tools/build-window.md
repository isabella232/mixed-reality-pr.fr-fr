---
title: Fenêtre de génération MRTK
description: Documentation sur l’utilisation de la fenêtre de génération dans MRTK pour Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Build, fenêtre de génération, outils
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196852"
---
# <a name="build-window"></a>Fenêtre Build
![Générer & déployer le Flow](images/MRTK_BuildWindow0.png)

La fenêtre de génération de MRTK facilite la création de & déployer vos projets MRTK-Unity. Avec un seul clic de bouton, vous pouvez générer un projet Unity et générer une solution Visual Studio (. SLN), le package d’application UWP (. APPX) et installer le package d’application sur l’appareil. 


## <a name="unity-build-options"></a>Options de build Unity
![Fenêtre de génération-options de build Unity 1](images/MRTK_BuildWindow1.png)

Ces scènes proviennent des paramètres de build Unity. Vous pouvez modifier le type d’appareil cible à l’aide du menu déroulant.

## <a name="appx-build-options"></a>Options de build AppX
![Fenêtre de génération-options de build AppX 2](images/MRTK_BuildWindow2.png)

Cet onglet affiche la configuration de la solution Visual Studio. Pour activer la fonctionnalité d’entrée de suivi oculaire de HoloLens 2, activez la case à cocher **capacité d’entrée en regard** . 

Vous pouvez affecter le fichier. GLB dans le champ **modèle du lanceur d’applications 3D** de l’icône du lanceur d’applications 3D personnalisé. Pour plus d’informations, consultez [instructions de conception du lanceur d’applications en 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) .

Par défaut, l' **incrémentation automatique** est vérifiée dans les options de contrôle de version. Les versions d’AppX seront automatiquement incrémentées.


## <a name="deploy-options"></a>Options de déploiement
![Fenêtre de génération-options de déploiement 3](images/MRTK_BuildWindow3.png)

Dans cet onglet, vous pouvez vous connecter à l’appareil en entrant un nom d’utilisateur et un mot de passe pour le portail de l’appareil. 

En bas de la page, vous trouverez la liste des packages d’application qui ont été créés. 

