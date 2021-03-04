---
title: Configurer votre projet sans MRTK
description: Découvrez comment configurer un nouveau projet Unity pour Windows Mixed Reality sans la boîte à outils de la réalité mixte.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performances
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117623"
---
# <a name="configuring-your-project-without-mrtk"></a>Configuration de votre projet sans MRTK

Windows Mixed Reality (WMR) est une plate-forme Microsoft introduite dans le cadre du système d’exploitation Windows 10. La plateforme WMR vous permet de créer des applications qui restituent du contenu numérique sur des appareils d’écran holographiques et VR.

Alors que Microsoft et la communauté ont créé des outils open source tels que le [Kit de MRTK (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) qui configure automatiquement l’environnement WMR, de nombreux développeurs souhaitent créer leurs expériences dès le départ.  La documentation suivante montre comment configurer correctement un projet pour le développement de réalité mixte, que vous utilisiez MRTK ou non.  Les paramètres que vous devez modifier sont divisés en deux catégories : les paramètres par projet et les paramètres par scène.

> [!NOTE]
> Vous pouvez toujours importer des MRTK par la suite. il n’y a donc aucune pénalité pour passer d’abord à l’itinéraire manuel.

Si vous choisissez la configuration manuelle WMR, les paramètres que vous devez modifier sont réparties en deux catégories : par projet et par scène.

## <a name="per-project-settings"></a>Paramètres par projet

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

### <a name="for-xrsdk"></a>Pour XRSDK 

1. Dans l’éditeur Unity, accédez à **modifier > paramètres du projet** , puis sélectionnez **gestion du plug-in XR**

2. Sélectionnez **installer la gestion des plug-ins XR**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-5.png)

3. Sélectionnez **initialiser XR au démarrage** et **Windows Mixed Reality**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la gestion du plug-in XR sélectionnée](images/wmr-config-img-7.png)

4. Développez la section **gestion du plug-in XR** et sélectionnez universels onglet Paramètres de la **plateforme Windows** .
5. Si vous utilisez Unity 2020 ou une version ultérieure, vous verrez les options permettant de vérifier **OpenXR (version préliminaire)** ou **Windows Mixed Reality**
6. Vous pouvez choisir l’un ou l’autre Runtime.  Si vous développez spécifiquement pour HoloLens 2 ou la réverbération HP G2 et que vous décidez d’essayer **OpenXR (** préversion), sélectionnez la zone OpenXR (préversion) et consultez notre guide pour [utiliser le plug-in OpenXR de réalité mixte pour Unity](openxr-getting-started.md) afin de vous préparer correctement à ces appareils avant de revenir à ce didacticiel.
7. Si vous décidez de choisir le plug-in **Windows Mixed Reality** , cochez toutes les cases et définissez le **mode d’envoi de profondeur** sur une profondeur de **16 bits**

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section Windows Mixed Reality mise en surbrillance](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Pour les XR hérités 

> [!CAUTION]
> Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.

1. Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**
2. Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle
3. Définir le **format de profondeur** sur **16 bits** et activer le partage de **mémoire tampon de profondeur**
4. Définir le **mode de rendu stéréo** sur **une seule instance de passage**
5. Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser la communication à distance holographique 

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Mise à jour du manifeste

Votre application peut désormais gérer le rendu holographique et l’entrée spatiale. Toutefois, votre application doit déclarer les fonctionnalités appropriées dans son manifeste pour tirer parti de certaines fonctionnalités. Vous pouvez trouver les fonctionnalités de vos projets en accédant à **paramètres du lecteur > paramètres pour plateforme Windows universelle > paramètres de publication > fonctionnalités**. 

Il est recommandé de rendre les déclarations de manifeste dans Unity pour les inclure dans tous les projets futurs que vous exportez. Les fonctionnalités applicables à l’activation des API Unity couramment utilisées pour la réalité mixte sont les suivantes :

|  Fonctionnalité  |  API nécessitant des fonctionnalités | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (accès aux maillages de [mappage spatial](../../design/spatial-mapping.md) sur HoloLens) &mdash; *aucune fonctionnalité nécessaire pour le suivi spatial général du casque* | 
|  WebCam  |  PhotoCapture et VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture ou VideoCapture, respectivement (lors du stockage du contenu capturé) | 
|  Microphone  |  VideoCapture (lors de la capture de l’audio), DictationRecognizer, GrammarRecognizer et KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (et pour utiliser le profileur Unity) | 

### <a name="quality-settings"></a>Paramètres de qualité

HoloLens possède un GPU de classe mobile. Si votre application cible HoloLens, vous devez commencer par les paramètres de qualité de votre application réglés pour des performances plus rapides afin de garantir qu’elle gère la fréquence d’images complète.  Une fois que vous avez plus d’informations sur votre développement, vous pouvez envisager de Upping les paramètres de qualité pour trouver le juste équilibre entre qualité et performances : 

1. Sélectionnez **modifier > paramètres du projet > qualité** 
2. Sélectionnez la **liste déroulante** sous le logo du  **Windows Store**   et sélectionnez  **très faible**. Vous saurez que le paramètre est appliqué correctement lorsque la zone de la colonne du Windows Store et la ligne très basse sont vertes 
3. Dans la section **Shadows**   , sélectionnez **Disable Shadows** . 

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres de qualité mise en surbrillance](images/wmr-config-img-10.png)<br>
*Paramètres de qualité Unity*

## <a name="per-scene-settings"></a>Paramètres par scène

### <a name="unity-camera-settings"></a>Paramètres de l’appareil photo Unity

Une fois la **réalité virtuelle prise en charge** activée, le composant [appareil photo Unity](camera-in-unity.md) gère le [suivi des têtes et le rendu stéréoscopique](../platform-capabilities-and-apis/rendering.md). Cela signifie que vous n’avez pas besoin de remplacer l’objet caméra principal par une caméra personnalisée.

Si votre application cible en particulier HoloLens, vous devez modifier quelques paramètres pour optimiser les affichages transparents de l’appareil. Ces paramètres permettent à votre contenu holographique de s’afficher dans le monde physique :

1. Dans la **hiérarchie**, sélectionnez l' **appareil photo principal** .
2. Dans le panneau **inspecteur** , définissez la **position** de la transformation sur **0, 0, 0** de sorte que l’emplacement de la tête de l’utilisateur commence à l’origine Unity World.
3. Remplacez **effacer les indicateurs** par **couleur unie**.
4. Remplacez la couleur d' **arrière-plan** par **RVBA 0, 0,** 0, 0. Le rendu noir est transparent dans HoloLens.
5. Modifiez les **plans de découpage-près** de [HoloLens recommandé](camera-in-unity.md#clip-planes) 0,85 (mètres).

![Capture d’écran de l’onglet inspecteur ouvert dans l’éditeur Unity](images/wmr-config-img-11.png)<br>
*Paramètres de l’appareil photo Unity*

> [!IMPORTANT]
> Si vous supprimez et créez un appareil photo, assurez-vous que votre nouvelle caméra est marquée comme **MainCamera**.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que votre projet est prêt, vous pouvez commencer à développer votre expérience de réalité mixte :

* Ajouter des [blocs de construction principaux](unity-development-overview.md#2-core-building-blocks)
* Découvrez les [API et les fonctionnalités de plateforme](unity-development-overview.md#3-advanced-features) disponibles
* Découvrez comment [déployer votre application](../platform-capabilities-and-apis/using-visual-studio.md#)
* Utiliser le [simulateur de réalité mixte](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Voir aussi
* [Installer les outils](../install-the-tools.md)