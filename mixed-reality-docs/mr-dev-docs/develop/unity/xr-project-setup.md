---
title: Configuration de votre configuration XR
description: Restez à jour avec les dernières recommandations de configuration de XR Unity pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906938"
---
# <a name="setting-up-your-xr-configuration"></a>Configuration de votre configuration XR

Lorsque vous démarrez un nouveau projet Unity, vous disposez de trois options différentes pour gérer vos besoins en matière de XR : 
* Plug-in OpenXR
* Plug-in XR Windows
* Plug-in XR hérité

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configuration de votre projet avec MRTK

MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales. MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR. Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.

> [!div class="nextstepaction"]
> [Essayer nos tutoriels MRTK](./tutorials/mr-learning-base-02.md?tabs=winxr)

Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).

### <a name="using-mrtk-with-openxr-support"></a>Utilisation de MRTK avec prise en charge de OpenXR

MRTK-Unity version 2,7 fournit de meilleures prises en charge pour le plug-in OpenXR de la réalité mixte.

Ouvrez de nouveau l' [outil Mixed Reality Feature](welcome-to-mr-feature-tool.md) pour installer la boîte à outils de la réalité mixte, si ce n’est déjà fait. La prise en charge de OpenXR est dans le package de **base** .

Pour [plus d’informations sur la migration vers OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline), consultez la documentation MRTK.

> [!NOTE]
> Lorsque vous effectuez une mise à niveau à partir d’une version antérieure de MRTK antérieure à **2.5.3**, vérifiez que la ligne suivante se trouve dans le fichier **Assets/MixedRealityToolkit. generated/link.xml** :
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Cette ligne sera ajoutée par défaut si vous avez démarré avec MRTK 2.5.4 ou une version plus récente.

## <a name="manual-setup-without-mrtk"></a>Configuration manuelle sans MRTK

Alors que Microsoft et la communauté ont créé des outils open source tels que le [Kit de MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) qui configure automatiquement l’environnement WMR, de nombreux développeurs souhaitent créer leurs expériences dès le départ.

[!INCLUDE[](includes/xr/manual-setup.md)]