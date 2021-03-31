---
title: Utilisation du plug-in XR Windows
description: Découvrez comment configurer vos projets Unity avec et sans MRTK à l’aide de la prise en charge de Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performance, Legacy, mrtk, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938106"
---
# <a name="using-windows-xr-plugin"></a>Utilisation du plug-in XR Windows

Pour les développeurs ciblant Unity 2020, le plug-in Windows XR permet d’accéder aux fonctionnalités de réalité mixte sur les casques HoloLens 2 et Windows Mixed Reality.  Ce plug-in est également pris en charge sur Unity 2019, bien qu’il existe des incompatibilités connues avec les ancres spatiales Azure lors de l’utilisation de ce plug-in sur cette version.

Alors que Microsoft et la communauté ont créé des outils open source tels que le [Kit de MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) qui configure automatiquement l’environnement WMR, de nombreux développeurs souhaitent créer leurs expériences dès le départ.  La documentation suivante montre comment configurer correctement un projet pour le développement de réalité mixte, que vous utilisiez MRTK ou non.  Les paramètres que vous devez modifier sont divisés en deux catégories : les paramètres par projet et les paramètres par scène.

## <a name="setting-up-your-project-with-mrtk"></a>Configuration de votre projet avec MRTK

MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales. MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR. Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.

> [!div class="nextstepaction"]
> [Essayez nos didacticiels MRTK](tutorials/mr-learning-base-01.md)

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

Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../design/app-views.md) au lieu d’une vue en 2D quand elle est exportée :

1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**

2. Sélectionnez **installer la gestion des plug-ins XR**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-5.png)

3. Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-7.png)

4. Développez la section **gestion du plug-in XR** et sélectionnez universels onglet Paramètres de la **plateforme Windows** .
5. Si vous utilisez Unity 2020 ou une version ultérieure, vous verrez les options permettant de vérifier **OpenXR** ou **Windows Mixed Reality**. 
    * Vous pouvez choisir l’un ou l’autre Runtime.  Si vous développez spécifiquement pour HoloLens 2 ou la réverbération HP G2 et que vous décidez d’essayer le **OpenXR**, sélectionnez la zone OpenXR et passez en revue notre guide pour [utiliser le plug-in OpenXR de réalité mixte pour Unity](openxr-getting-started.md) afin de vous préparer correctement pour ces appareils avant de revenir à ce didacticiel.

> [!NOTE]
> À partir de Unity 2020 LTS, Microsoft adopte le développement avec OpenXR.  À mesure que nous migrons vers ce chemin, dans Unity 2021,1, le plug-in Windows XR sera déconseillé et supprimé dans 2021,2, OpenXR le seul chemin pris en charge. Vous trouverez plus d’informations dans [utilisation du plug-in OpenXR de la réalité mixte](openxr-getting-started.md).

6. Si vous décidez de choisir le plug-in **Windows Mixed Reality** , cochez toutes les cases et définissez le **mode d’envoi de profondeur** sur une profondeur de **16 bits**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](images/wmr-config-img-8.png)
