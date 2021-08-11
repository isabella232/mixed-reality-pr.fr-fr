---
title: Historique des versions de la communication à distance holographique
description: Restez à jour dans l’historique des versions de la fonctionnalité de communication à distance holographique pour HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, historique des versions, casque de la réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 21ba89e477872f5dfa41468f1a7f2d7507affd681556d79843c195d7d5839e7b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223552"
---
# <a name="holographic-remoting-version-history"></a>Historique des versions de la communication à distance holographique

> [!IMPORTANT]
> Ce guide est spécifique à la communication à distance holographique sur HoloLens 2.

## <a name="version-261-july-20-2021"></a>Version 2.6.1 (20 juillet 2021) <a name="v2.6.1"></a>
* L’extension de XR_MSFT_holographic_remoting_speech permet désormais de réinitialiser le module de reconnaissance vocale avec de nouveaux paramètres au cours d’une session en cours d’exécution.
* Résolution d’un problème où la fiabilité de la reconnaissance vocale a baissé sur plusieurs connexions.
* Plusieurs correctifs de bogues et améliorations de stabilité.

## <a name="version-260-june-10-2021"></a>Version 2.6.0 (10 juin 2021) <a name="v2.6.0"></a>
* La communication à distance holographique à l’aide de l’API OpenXR prend désormais en charge :
  * Nouvelle extension de XR_MSFT_holographic_remoting_speech, qui permet aux applications d’écouter des commandes vocales personnalisées dans différentes langues.
  * L’extension XR_MSFT_scene_understanding, qui fournit aux applications une représentation structurée et de haut niveau des plans, des mailles et des objets dans l’environnement de l’utilisateur, ce qui permet le développement d’applications spatialement compatibles. Toutefois, avec l’inconvénient que XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT est la seule cohérence prise en charge par xrComputeNewSceneMSFT.
  * l’extension XR_MSFT_spatial_graph_bridge, qui permet aux applications de créer des handles XrSpace pour effectuer le suivi des nœuds de Graph spatiales d’autres api ou bibliothèques de plateformes d’appareils Windows Mixed Reality. Toutefois, avec l’inconvénient que XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT est le seul type de nœud pris en charge par xrCreateSpatialGraphNodeSpaceMSFT. 
* La communication à distance holographique à l’aide de l’API de réalité mixte prend désormais en charge :
  * les surcharges SpatialGraphInteropPreview. CreateCoordinateSystemForNode, qui permettent aux applications d’effectuer le suivi des nœuds de Graph spatiales statiques afin que les utilisateurs puissent connaître les emplacements et les éléments dans leur environnement.
* La communication à distance holographique utilisant à la fois les API OpenXR et de réalité mixte prend désormais en charge :
  * Le kit de développement logiciel (SDK) Microsoft. MixedReality. SceneUnderstanding, qui permet aux applications de calculer une description de la scène entourant l’utilisateur (par exemple, murs, planchers et surfaces) fournissant des Quad, des maillages et des signaux de placement du contenu.
  * Le kit de développement logiciel (SDK) Microsoft. MixedReality. QR, qui permet aux applications de suivre l’emplacement, la taille et le contenu des codes QR détectés.
* L’exemple distant OpenXR a été mis à jour pour inclure les éléments suivants : 
  * Exemple d’utilisation de l’extension de XR_MSFT_holographic_remoting_speech.
* L’exemple distant Mixed Reality a été mis à jour pour inclure les éléments suivants :  
  * Exemple d’utilisation du kit de développement logiciel (SDK) Microsoft. MixedReality. SceneUnderstanding.
  * Exemple d’utilisation du kit de développement logiciel (SDK) Microsoft. MixedReality. QR (qui remplace le mécanisme de détection du code QR précédent).
* Le lecteur de communication à distance holographique affiche maintenant une animation de chargement pendant l’établissement de la connexion.
* Résolution des problèmes de compatibilité RenderDoc dans le runtime d’API OpenXR et dans l’exemple d’API de réalité mixte.
* Plusieurs correctifs de bogues et améliorations de stabilité.

## <a name="version-250-february-12-2021"></a>Version 2.5.0 (12 février 2021) <a name="v2.5.0"></a>
* La communication à distance holographique à l’aide de l' [API OpenXR](../native/openxr.md) prend désormais en charge :
  * Extension de XR_MSFT_spatial_anchor. Cette extension permet à une application de créer des ancres spatiales, qui sont des points d’espace libre arbitraires dans l’environnement physique de l’utilisateur qui feront l’élément d’un suivi par le Runtime.
  * Extension de XR_MSFT_controller_model. Cette extension fournit un mécanisme permettant de charger des modèles GLTF pour les contrôleurs.
  * Canaux de données personnalisés dans le cadre de l’extension de XR_MSFT_holographic_remoting. Un exemple pour cela est illustré dans l' [exemple distant OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
* Synchronisation améliorée entre le joueur et le côté distant. Cela permet de modifier dynamiquement la mise en mémoire tampon de pose et de trame, ce qui garantit que le contenu rendu distant atteint correctement les affichages à la fréquence d’images cible attendue.
* Amélioration des performances du lecteur de communication à distance holographique disponible via le Microsoft Store. sur HoloLens 2, le lecteur s’exécute à présent sur 60 images par seconde.
* Transmission optimisée des maillages de surface spatiale qui peuvent être interrogés via [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) par une application distante.
* Correction d’un problème dans lequel l’appel de méthodes SpatialAnchorManager ou la libération d’ancres entraînait des exceptions lors de la déconnexion.
* Résolution des problèmes liés aux threads entraînant des blocages lors de la fermeture des instances PlayerContext ou RemoteContext.
* lecteur de communication à distance holographique sur le bureau : affiche un message d’erreur quand Windows Mixed Reality n’est pas installé au lieu de se fermer en mode silencieux.
* De nombreux autres correctifs de bogues et améliorations de la stabilité.

## <a name="version-241-january-22-2021"></a>Version 2.4.1 (22 janvier 2021) <a name="v2.4.1"></a>

* Correction du problème avec SpatialAnchorManager :: RequestStoreAsync qui ne fonctionne pas de façon fiable lors de la connexion.
* Correction du problème avec SpatialAnchorManager :: TrySave non correctement lors de l’enregistrement d’une ancre si le point d’ancrage en question n’est pas localisable.

## <a name="version-240-december-1-2020"></a>Version 2.4.0 (1er décembre 2020) <a name="v2.4.0"></a>

* La communication à distance holographique prend désormais en charge l’écriture d’applications distantes à l’aide de l' [API OpenXR](../native/openxr.md). Consultez [écriture d’une application distante holographique à distance à l’aide des API OpenXR](holographic-remoting-create-remote-openxr.md) pour commencer.
* Correctifs de bogues et améliorations de la stabilité.

## <a name="version-231-october-10-2020"></a>Version 2.3.1 (10 octobre 2020) <a name="v2.3.1"></a>

* Correction de la régression avec la prédiction de pose à distance, ce qui a provoqué une instabilité visuelle.
* Implémentation de PerceptionDeviceSetCreateFactoryOverride, qui garantit que les PerceptionDevice.dll fournies avec la communication à distance holographique n’interfèrent pas avec la version fournie avec Windows 10.

## <a name="version-230-october-2-2020"></a>Version 2.3.0 (2 octobre 2020) <a name="v2.3.0"></a>

* Résolution des incidents, ce qui peut se produire lorsque le lecteur de communication à distance holographique est suspendu.
* Améliorations de la stabilité.

## <a name="version-223-august-28-2020"></a>Version 2.2.3 (28 août 2020) <a name="v2.2.3"></a>

* Correctifs de bogues et améliorations de la stabilité.

## <a name="version-222-july-10-2020"></a>Version 2.2.2 (10 juillet 2020) <a name="v2.2.2"></a>

* résolution du problème lié à [HolographicCamera. LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) et [HolographicCamera. RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) ne renvoyant aucun vertex de maillage de zone masqué lors de la diffusion en continu à partir d’un Windows Mixed Reality casque.
* Correction d’un incident, ce qui peut se produire avec une mauvaise connexion réseau.

## <a name="version-221-july-6-2020"></a>Version 2.2.1 (6 juillet 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) la validation du Kit de Certification des applications avec la version [2.2.0](holographic-remoting-version-history.md#v2.2.0) échouera. Si vous êtes sur la version [2.2.0](holographic-remoting-version-history.md#v2.2.0) et que vous souhaitez soumettre votre application au bail Microsoft Store p mis à jour vers la version 2.2.1.
* correction des problèmes de conformité du [Kit de Certification des applications Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Version 2.2.0 (1er juillet 2020) <a name="v2.2.0"></a>

* le lecteur de communication à distance holographique peut désormais être installé sur des pc exécutant [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md), ce qui rend possible la diffusion en continu vers des casques immersifs.
* Les [contrôleurs de mouvement](../../design/motion-controllers.md) sont désormais pris en charge par la communication à distance holographique et les données spécifiques au contrôleur peuvent être récupérées via [SpatialInteractionSource. Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) est maintenant pris en charge et l’étape actuelle peut être récupérée via [SpatialStageFrameOfReference. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). En outre, une nouvelle étape peut être demandée via [SpatialStageFrameOfReference. RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* Dans les versions précédentes, la prédiction de pose a été gérée côté joueur par le lecteur de communication à distance holographique. À partir de la version 2.2.0, la communication à distance holographique a une synchronisation temporelle et la prédiction est entièrement effectuée par l’application distante. Les utilisateurs doivent également s’attendre à une stabilité améliorée des hologrammes dans des situations difficiles sur le réseau.

## <a name="version-213-may-25-2020"></a>Version 2.1.3 (25 mai, 2020) <a name="v2.1.3"></a>

* Modification du comportement de l’événement [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) . Dans les versions précédentes, il n’était **pas** garanti qu’un [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) ajouté ait également un [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valide lors de la création du frame suivant via [HolographicSpace. CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe). À partir de la version 2.1.3, [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) est synchronisé avec les données de pose provenant du lecteur de communication à distance holographique. Les utilisateurs peuvent s’attendre à ce qu’un [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valide soit disponible pour cette caméra dans le cadre suivant.
* Ajout de **désactivé** à DepthBufferStreamResolution, qui peut être utilisé pour désactiver la diffusion en continu de tampons de profondeur via RemoteContext.ConfigureDepthVideoStream. Notez que s’il est utilisé, [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) échouera avec *E_ILLEGAL_METHOD_CALL*.
* L’écran de démarrage du lecteur de communication à distance holographique a été repensé et ne bloque pas la vue des utilisateurs.
* Améliorations de la stabilité et correctifs de bogues.

## <a name="version-212-april-5-2020"></a>Version 2.1.2 (5 avril 2020) <a name="v2.1.2"></a>

* Résolution d’un problème de compatibilité descendante audio entre le dernier lecteur de communication à distance holographique et les applications distantes utilisant une version inférieure à 2.1.0.
* Problème fixe d’ancrage spatial, qui a fermé de manière inattendue le lecteur de communication à distance holographique. Ce problème affecte également les lecteurs personnalisés.

## <a name="version-211-march-20-2020"></a>Version 2.1.1 (20 mars, 2020) <a name="v2.1.1"></a>

* Résolution d’un problème de codage vidéo avec les applications distantes lors de l’utilisation des GPU AMD.
* Améliorations des performances du lecteur de communication à distance holographique.

## <a name="version-210-march-11-2020"></a>Version 2.1.0 (11 mars, 2020) <a name="v2.1.0"></a>

* Transport réseau commuté pour utiliser [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP. Les connexions sécurisées utilisent [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Now. Notez que le [lecteur de communication à distance holographique](holographic-remoting-player.md) est toujours compatible avec toutes les versions de Remoting holographiques antérieures. Pour tirer parti du nouveau transport réseau, le lecteur de communication à distance holographique et l’application distante en question doivent utiliser la version 2.1.0.
* Ajout de la prise en charge de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Version 2.0.20 (2 février 2020) <a name="v2.0.20"></a>

* Correction de divers bogues qui mènent à des incidents.

## <a name="version-2018-december-17-2019"></a>Version 2.0.18 (17 décembre 2019) <a name="v2.0.18"></a>

* Ajout de la prise en charge de [HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Correction de divers bogues qui mènent à des incidents.
* Correction d’un bogue où un rappel HolographicSpace. CameraAdded était nécessaire pour qu’un HolographicCamera soit accepté et apparaissait comme caméra ajoutée dans le HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Version 2.0.16 (11 novembre 2019) <a name="2.0.16"></a>

* Correction du blocage dans le suivi du code QR.
* Correction de l’exception unhandeled en raison d’une attente de blocage dans le thread principal.

## <a name="version-2014-october-26-2019"></a>Version 2.0.14 (26 octobre 2019) <a name="v2.0.14"></a>

* prise en charge des nouvelles api PerceptionDevice (Windows 10 la mise à jour de novembre 2019).
* Résolution d’un problème qui empêche les événements de mouvement de conservation d’être déclenchés par SpatialGestureRecognizer.
* Problème de thread fixe lors de l’utilisation de SpatialSurfaceObserver. SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Version 2.0.12 (18 octobre 2019) <a name="v2.0.12"></a>

* Correction d’un incident dans SpatialGestureRecognizer lors de l’utilisation de NavigationRail (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Version 2.0.10 (10 octobre 2019) <a name="v2.0.10"></a>

* Résolution d’un incident lors de l’utilisation du bouton déclencheur des contrôleurs VR. la communication à distance holographique ne prend pas entièrement en charge les contrôleurs, mais uniquement le bouton déclencheur et le bouton Windows fonctionnent s’ils sont associés à HoloLens 2.

## <a name="version-209-september-19-2019"></a>Version 2.0.9 (19 septembre 2019) <a name="v2.0.9"></a>

* Ajout de la prise en charge de [SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Ajout ```IPlayerContext2``` d’une nouvelle interface (implémentée par ```PlayerContext``` ) fournissant les membres suivants :
  - Propriété [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* ```Failed_RemoteFrameTooOld```Valeur ajoutée à```BlitResult```
* Améliorations de la stabilité et de la fiabilité

## <a name="version-208-august-20-2019"></a>Version 2.0.8 (20 août, 2019) <a name="v2.0.8"></a>

* Résolution d’un incident lors de l’appel de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) avec un paramètre [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) .
* Améliorations de la stabilité et de la fiabilité

## <a name="version-207-july-26-2019"></a>Version 2.0.7 (26 juillet, 2019) <a name="v2.0.7"></a>

* Première version publique de la communication à distance holographique pour HoloLens 2.

## <a name="see-also"></a>Voir aussi

* [écriture d’une application distante de communication à distance holographique à l’aide d’api Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Écriture d’une application distante de communication à distance holographique à l’aide d’API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Écriture d’une application de lecteur de communication à distance holographique personnalisée](holographic-remoting-create-player.md)
* [Résolution des problèmes et limitations de la communication à distance holographique](holographic-remoting-troubleshooting.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)