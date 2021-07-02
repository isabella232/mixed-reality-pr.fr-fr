---
title: Fenêtre Build
description: Documentation sur l’utilisation de la fenêtre de génération dans MRTK pour Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, générer, fenêtre de génération, outils
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176152"
---
# <a name="build-window"></a>Fenêtre Build
![Générer & déployer le Flow](images/MRTK_BuildWindow0.png)

La fenêtre de génération de MRTK facilite la création de & déployer vos projets MRTK-Unity. avec un simple clic sur un bouton, vous pouvez générer un projet unity et générer Visual Studio solution (. SLN), le package d’application UWP (. APPX) et installer le package d’application sur l’appareil. 


## <a name="unity-build-options"></a>Options de build Unity
![Fenêtre de génération-options de build Unity 1](images/MRTK_BuildWindow1.png)

ces scènes proviennent de la Paramètres de Build unity. Vous pouvez modifier le type d’appareil cible à l’aide du menu déroulant.

## <a name="appx-build-options"></a>Options de build AppX
![Fenêtre de génération-options de build AppX 2](images/MRTK_BuildWindow2.png)

cet onglet affiche la configuration de la solution Visual Studio. pour activer la fonctionnalité d’entrée de suivi oculaire de HoloLens 2, activez la case à cocher **capacité d’entrée en regard** . 

vous pouvez affecter le fichier. glb dans le champ **modèle d’Lanceur d’application 3d** pour l’icône du lanceur d’applications 3d personnalisé. Pour plus d’informations, consultez [instructions de conception du lanceur d’applications en 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) .

Par défaut, l' **incrémentation automatique** est vérifiée dans les options de contrôle de version. Les versions d’AppX seront automatiquement incrémentées.


## <a name="deploy-options"></a>Options de déploiement
![Fenêtre de génération-options de déploiement 3](images/MRTK_BuildWindow3.png)

Dans cet onglet, vous pouvez vous connecter à l’appareil en entrant un nom d’utilisateur et un mot de passe pour le portail de l’appareil. 

En bas de la page, vous trouverez la liste des packages d’application qui ont été créés. 

