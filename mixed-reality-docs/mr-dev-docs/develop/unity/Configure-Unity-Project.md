---
title: Configurer un nouveau projet Unity pour Windows Mixed Reality
description: Instructions sur la configuration d’un projet Unity pour Windows Mixed Reality
author: thetuvix
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performances
ms.openlocfilehash: cd7e6c5681c717c37368393a605998a2ab8e4175
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677668"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurer un nouveau projet Unity pour Windows Mixed Reality 

## <a name="overview"></a>Vue d’ensemble

Windows Mixed Reality (WMR) est une plate-forme Microsoft introduite dans le cadre du système d’exploitation Windows 10. La plateforme WMR vous permet de créer des applications qui restituent du contenu numérique sur des appareils d’écran holographiques et VR.

Lors de la configuration de WMR, vous pouvez prendre deux chemins d’accès. Votre première option consiste à installer la [boîte à outils de réalité mixte (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), qui configure automatiquement l’environnement WMR. La deuxième option consiste à modifier manuellement quelques paramètres Unity pour obtenir le roulement avec WMR. 

> [!NOTE]
> Vous pouvez toujours importer des MRTK par la suite. il n’y a donc aucune pénalité pour passer d’abord à l’itinéraire manuel.

Si vous choisissez la configuration manuelle WMR, les paramètres que vous devez modifier sont réparties en deux catégories : par projet et par scène.

## <a name="per-project-settings"></a>Paramètres par projet

Le premier paramètre que vous devez modifier pour WMR est la plateforme de projet : 
1. Sélectionner le **fichier > les paramètres de Build...**
2. Sélectionnez **plateforme Windows universelle** dans la liste plateforme, puis cliquez sur **changer de plateforme** .
3. Définir le **Kit de développement logiciel** sur **Universal 10**
4. Définir un appareil **cible** sur **un appareil** pour prendre en charge les casques immersifs ou basculer vers **HoloLens**
5. Définir le **type de build** sur **D3D**
6. Définir le **SDK UWP** sur le **dernier installé**

<img src="images/unity-uwp-settings.png" width="550px" alt="Unity XR Settings">
*Paramètres XR Unity*

Une fois que la plateforme est correctement configurée, vous devez faire en sorte que votre application soit en mesure de créer une [vue immersive](../../design/app-views.md) au lieu d’une vue 2D au moment de l’exportation :
1. Dans la fenêtre **paramètres de Build...** , ouvrez paramètres du **lecteur...**
2. Sélectionnez les **paramètres de plateforme Windows universelle** onglet et développez le groupe de **paramètres XR**
3. Dans la section **paramètres XR** , activez la case à cocher **Virtual Reality pris en charge** pour ajouter la liste des **appareils Virtual Reality** .
4. Dans le groupe de **paramètres XR** , vérifiez que **« Windows Mixed Reality »** est listé comme périphérique pris en charge. (cette option peut s’afficher sous la forme **Windows holographique** dans les versions antérieures d’Unity)

![Paramètres UWP Unity](images/xrsettings.png)<br>
*Paramètres XR Unity*

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

HoloLens possède un GPU de classe mobile. Si votre application cible HoloLens, vous souhaiterez que les paramètres de qualité de votre application soient réglés pour des performances plus rapides afin de garantir qu’elle gère la fréquence d’images complète :
1. Sélectionnez **modifier > paramètres du projet > qualité**
2. Sélectionnez la **liste déroulante** sous le logo du **Windows Store** et sélectionnez **très faible**. Vous savez que le paramètre est correctement appliqué lorsque la zone dans la colonne Windows Store et la ligne **Very Low** est verte.

![Paramètres de qualité Unity](images/getting-started-unity-quality-settings.jpg)<br>
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

![Paramètres de l’appareil photo Unity](images/Unitycamerasettings.png)<br>
*Paramètres de l’appareil photo Unity*

> [!IMPORTANT]
> Si vous supprimez et créez un appareil photo, assurez-vous que votre nouvelle caméra est marquée comme **MainCamera**.

## <a name="see-also"></a>Voir aussi
* [MRTK - Guide d’installation (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Page d’accueil de la documentation MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Installer les outils](../install-the-tools.md)
* [Vue d’ensemble du développement Unity](unity-development-overview.md)
