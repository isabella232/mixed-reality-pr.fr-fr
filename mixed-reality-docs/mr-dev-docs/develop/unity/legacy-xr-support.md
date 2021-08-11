---
title: Utilisation du support XR intégré hérité
description: Découvrez comment configurer vos projets Unity avec et sans MRTK à l’aide de la prise en charge héritée de XR intégrée.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performance, hérité, mrtk
ms.openlocfilehash: 534df0b9c4efbe62b00af6cccb74f4203c1557e9479b2101320bab3bbdb5e565
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192052"
---
# <a name="using-legacy-built-in-xr-support"></a>Utilisation du support XR intégré hérité

## <a name="setting-up-your-project-with-mrtk"></a>Configuration de votre projet avec MRTK

MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales. MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR. Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.

> [!div class="nextstepaction"]
> [Essayer nos tutoriels MRTK](./tutorials/mr-learning-base-02.md?tabs=wsa)

Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Configuration manuelle sans MRTK

Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec PC, Mac & plateforme autonome en surbrillance](images/wmr-config-img-3.png)

si vous ciblez HoloLens 2, vous devez basculer vers le plateforme Windows universelle :

1.  sélectionner le **fichier > la Paramètres de Build...**
2.  sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**
3.  Définissez **Architecture** sur **ARM 64**.
4.  Définissez **Target device** sur **HoloLens**.
5.  Définissez **Build Type** sur **D3D**.
6.  Définissez **UWP SDK** sur **Latest installed**.
7.  Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.

![capture d’écran de la fenêtre de Paramètres de Build ouverte dans l’éditeur unity avec plateforme Windows universelle mis en surbrillance](images/wmr-config-img-4.png)

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.

> [!CAUTION]
> Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.

1. ouvrir le **Paramètres du lecteur...** à partir de la **Paramètres de Build... et** développez le groupe de **Paramètres XR**
2. dans la section **Paramètres XR** , sélectionnez **virtual reality pris en charge** pour ajouter la liste des appareils de réalité virtuelle
3. Définir le **format de profondeur** sur **16 bits** et activer le partage de **mémoire tampon de profondeur**
4. Définir le **mode de rendu stéréo** sur **une seule instance de passage**
5. Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser la communication à distance holographique 

![capture d’écran de la fenêtre paramètres Project ouverte dans l’éditeur unity avec la section paramètres du lecteur mise en surbrillance](images/wmr-config-img-9.png)