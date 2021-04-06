---
title: Utilisation du support XR intégré hérité
description: Découvrez comment configurer vos projets Unity avec et sans MRTK à l’aide de la prise en charge héritée de XR intégrée.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performance, Legacy, mrtk
ms.openlocfilehash: 09989b3b2b7fa1d351235a2cc9b885d4795dc2b6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088528"
---
# <a name="using-legacy-built-in-xr-support"></a>Utilisation du support XR intégré hérité

## <a name="setting-up-your-project-with-mrtk"></a>Configuration de votre projet avec MRTK

MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales. MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR. Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.

> [!div class="nextstepaction"]
> [Essayez nos didacticiels MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=wsa)

Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity) .

## <a name="manual-setup-without-mrtk"></a>Configuration manuelle sans MRTK

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](images/wmr-config-img-3.png)

Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :

1.  Sélectionner le **fichier > les paramètres de Build...**
2.  Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définir l' **architecture** sur **ARM 64**
4.  Définir l' **appareil cible** sur **HoloLens**
5.  Définir le **type de build** sur **D3D**
6.  Définir le **SDK UWP** sur le **dernier installé**
7.  Définir la **configuration de build** sur **Release** en raison de problèmes de performances connus avec Debug

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.

> [!CAUTION]
> Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.

1. Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**
2. Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle
3. Définir le **format de profondeur** sur **16 bits** et activer le partage de **mémoire tampon de profondeur**
4. Définir le **mode de rendu stéréo** sur **une seule instance de passage**
5. Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser la communication à distance holographique 

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](images/wmr-config-img-9.png)