---
title: OpenXR
description: créez un moteur à l’aide de la norme d’API OpenXR portable et déployez-le sur des casques Windows Mixed Reality et HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Roadmap, extensions, Khronos, BasicXRApp, DirectX, native, application native, moteur personnalisé, intergiciel
ms.openlocfilehash: 66ef972e09617e596a7d1d097073183943037e29b462ed3070d4defac91ca6b6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193741"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR est une norme d’API gratuite et gratuite de <a href="https://www.khronos.org/" target="_blank">Khronos</a>, qui fournit aux moteurs un accès natif à une gamme de périphériques dans le spectre de la [réalité mixte](../../discover/mixed-reality.md).

vous pouvez développer à l’aide de OpenXR sur un HoloLens 2 ou Windows Mixed Reality casque d’immersion immersif sur le bureau.  si vous n’avez pas accès à un casque, vous pouvez utiliser le HoloLens 2 Emulator ou le simulateur Windows Mixed Reality à la place.

## <a name="why-openxr"></a>Pourquoi OpenXR ?

avec OpenXR, vous pouvez créer des moteurs qui ciblent des appareils holographiques, comme des HoloLens 2 et des appareils immersifs, tels que des casques Windows Mixed Reality pour les pc de bureau. OpenXR vous permet d’écrire du code une fois qui est ensuite portable sur une large gamme de plateformes matérielles.

L’API OpenXR utilise un chargeur pour connecter votre application directement à la prise en charge native de la plateforme de votre casque. les utilisateurs finaux obtiennent des performances maximales et une latence minimale, qu’ils utilisent un Windows Mixed Reality ou tout autre casque.

## <a name="what-is-openxr"></a>Qu’est-ce que OpenXR ?

L’API OpenXR fournit la prédiction de pose de base, le minutage des frames et la fonctionnalité d’entrée spatiale dont vous aurez besoin pour créer un moteur qui peut cibler des appareils holographiques et immersifs.

Pour en savoir plus sur l’API OpenXR, consultez la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">spécification</a>OpenXR 1,0, informations de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">référence</a>sur les API et <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guide de référence rapide</a>.  Pour plus d’informations, consultez la <a href="https://www.khronos.org/openxr/" target="_blank">page Khronos OpenXR</a>.

pour cibler l’ensemble complet des fonctionnalités de HoloLens 2, vous utiliserez également des extensions OpenXR spécifiques à un fournisseur et à un fournisseur qui activent des fonctionnalités supplémentaires au-delà du OpenXR 1,0 cœurs, telles que le suivi articulé, le suivi oculaire, le mappage spatial et les ancres spatiales. Pour plus d’informations, consultez la section de feuille de [route](#roadmap) ci-dessous sur les extensions qui seront fournies plus tard cette année.

OpenXR n’est pas lui-même un moteur de réalité mixte.  Au lieu de cela, OpenXR permet aux moteurs comme Unity et Unreal d’écrire du code portable une seule fois qui peut ensuite accéder aux fonctionnalités natives de la plateforme de l’appareil holographique ou immersif de l’utilisateur, quel que soit le fournisseur qui a créé cette plateforme.

## <a name="roadmap"></a>Feuille de route

La spécification OpenXR définit un mécanisme d’extension qui permet aux implémenteurs de runtime d’exposer des fonctionnalités supplémentaires au-delà des [fonctionnalités](#what-is-openxr) de base définies dans la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">spécification 1,0 de base OpenXR</a>.

Il existe trois types d’extensions OpenXR :
* **Les extensions de fournisseur (par exemple, `MSFT` ) :** activent l’innovation par fournisseur dans les fonctionnalités matérielles ou logicielles.  N’importe quel fournisseur de Runtime peut introduire et livrer une extension de fournisseur à tout moment.
  * **Extensions de fournisseurs expérimentaux (par exemple, `MSFT_preview` ) :** extensions de fournisseur expérimentales prévisualisées pour recueillir des commentaires.  `MSFT_preview` les extensions sont destinées aux appareils de développement uniquement et seront supprimées lorsque l’extension réelle est expédiée.  Pour les expérimenter, vous pouvez [activer les extensions préliminaires sur votre appareil de développement](openxr-getting-started.md#using-preview-extensions).
* **Extensions inter-fournisseurs `EXT` :** extensions inter-fournisseurs que plusieurs entreprises définissent et implémentent.  Les groupes de sociétés intéressées peuvent introduire des extensions EXT à tout moment.
* **`KHR` Extensions officielles :** extensions Khronos officielles ratifiées dans le cadre d’une version de base spec.  Les extensions KHR sont couvertes par la même licence que la spécification principale elle-même.

le Windows Mixed Reality Runtime OpenXR prend en charge un ensemble d' `MSFT` `EXT` extensions et qui offre l’ensemble complet de fonctionnalités HoloLens 2 aux applications OpenXR :

| Domaine de fonctionnalité | Disponibilité de l’extension |
|--------------|------------------------|
| Systèmes et sessions | **OpenXR 1,0 Core spec :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Espaces de référence (vue, local, intermédiaire)](../../design/coordinate-systems.md) | **OpenXR 1,0 Core spec :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Afficher les configurations (mono, stéréo) | **OpenXR 1,0 Core spec :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Chaînes d’échange](../platform-capabilities-and-apis/rendering.md)  +  [minutage des frames](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1,0 Core spec :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Couches de composition<br />(projection, quadruple) | **OpenXR 1,0 Core spec :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Entrée et haptique](../../design/interaction-fundamentals.md) | **OpenXR 1,0 Core spec :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Intégration de Direct3D 11 | **`KHR`Extension officielle publiée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Intégration de Direct3D 12 | **`KHR`Extension officielle publiée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Espace de référence non lié <br /> (expériences à l’échelle mondiale)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` extension libérée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Ancres spatiales](../../design/spatial-anchors.md) | <p>**`MSFT` extension libérée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code></p><p>**`MSFT_preview` extension dans [preview runtime 107](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_anchor_persistence_preview">XR_MSFT_spatial_anchor_persistence_preview</a></code></p> |
| [Interaction manuelle <br /> (pose/pose, pression pneumatique, prise)](../../design/hands-and-tools.md)<p>*HoloLens 2 uniquement*</p> | **`MSFT` extension libérée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Articulation manuelle + maille](../../design/hands-and-tools.md)<p>*HoloLens 2 uniquement*</p> | <p>**`EXT` extension libérée :**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` extension libérée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Suivre du regard](../../design/eye-tracking.md)<p>*HoloLens 2 uniquement*</p> | **`EXT` extension libérée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| [Capture de réalité mixte <br /> (troisième rendu à partir d’une caméra PV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2 uniquement*</p> | **`MSFT` extensions publiées :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interopérabilité avec d’autres SDK de réalité mixte<br />(par exemple, [QR](../platform-capabilities-and-apis/qr-code-tracking.md)) | <p>**`MSFT` extension libérée :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` extension publiée dans le runtime 105 :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| Interopérabilité avec l’API CoreWindow UWP<br />(par exemple, pour le clavier/la souris) | **`MSFT` extension publiée dans le runtime 103 :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Profils d’interaction du contrôleur de mouvement<br />(Samsung Odyssey et HP réverbération G2) | **`MSFT` extensions publiées dans le runtime 103 :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Modèles de rendu du contrôleur de mouvement](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` extension publiée dans le runtime 104 :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Compréhension des scènes (plans, maillages)](../../design/scene-understanding.md)<p>*HoloLens 2 uniquement*</p> | <p>**`MSFT` extension publiée dans le runtime 106 :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding">XR_MSFT_scene_understanding</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding_serialization">XR_MSFT_scene_understanding_serialization</a></code></p> |
| [Modes de reprojection de la couche <br /> de composition (reprojection automatique ou orientation uniquement)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` extension publiée dans le runtime 106 :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_composition_layer_reprojection">XR_MSFT_composition_layer_reprojection</a></code> |
| Autres extensions inter-fournisseurs | <p>**`KHR`Extensions officielles publiées :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code></p><p>**`EXT` extensions publiées :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code></p> |

Si certaines de ces extensions peuvent commencer par des extensions spécifiques au fournisseur `MSFT` , Microsoft et d’autres fournisseurs de Runtime OpenXR travaillent ensemble pour concevoir des extensions ou des fournisseurs croisés `EXT` pour la `KHR` plupart de ces domaines de fonctionnalités. Les extensions inter-fournisseurs feront du code que vous écrivez pour ces fonctionnalités portables entre les fournisseurs de Runtime, comme avec la spécification principale.

## <a name="getting-started-with-openxr"></a>Bien démarrer avec OpenXR

![capture d’écran des Minecraft joués par un utilisateur qui porte un casque de réalité mixte](images/openxr-minecraft.jpg)

*le nouveau moteur RenderDragon de Minecraft a créé sa prise en charge de desktop VR à l’aide de OpenXR !*

Microsoft travaille avec les jeux unity et Epic pour s’assurer que l’avenir de la réalité mixte est ouvert, pas seulement pour HoloLens 2, mais à travers toute la largeur de PC VR, y compris le [nouveau casque de réverbération G2 de HP](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).  OpenXR alimente la prise en charge inter-fournisseurs de la livraison de titres majeurs aujourd’hui, par exemple Minecraft et Microsoft Flight Simulator.  pour plus d’informations sur le développement pour HoloLens (1re génération), consultez les [notes de publication](/hololens/hololens1-release-notes).

Pour découvrir comment vous pouvez commencer à utiliser OpenXR dans Unity, un moteur inréel ou votre propre moteur, lisez !

### <a name="openxr-in-unity"></a>OpenXR dans Unity

la configuration d’unity recommandée de Microsoft pour le développement de HoloLens 2 et d’Windows Mixed Reality est **unity 2020,3 LTS** avec le dernier plug-in OpenXR de réalité mixte.  ce plug-in inclut la prise en charge des extensions OpenXR qui mettent en lumière les [fonctionnalités complètes de HoloLens 2 et Windows Mixed Reality casques](#roadmap), notamment le suivi des mains/yeux, les ancrages spatiaux et les contrôleurs de réverbérations HP.  MRTK-Unity prend en charge OpenXR à partir de [MRTK 2,7](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project).  Pour plus d’informations sur la prise en main d’Unity 2020 et OpenXR, consultez [choix d’une version Unity](../unity/choosing-unity-version.md).

si vous développez pour HoloLens (1re génération), vous devez continuer à utiliser **unity 2019,4 LTS** avec le backend de l’API WinRT héritée.  Si vous ciblez le nouveau contrôleur de reréverbérations de HP G2 dans une application Unity 2019, consultez nos [documents d’entrée de réverbération de HP G2](../unity/unity-reverb-g2-controllers.md).

à partir de **unity 2021,2**, OpenXR sera le seul backend unity pris en charge pour le ciblage des HoloLens 2 et des casques Windows Mixed Reality.

### <a name="openxr-in-unreal-engine"></a>OpenXR dans le moteur non réel

Le moteur 4,23 est la première version majeure du moteur de jeu à expédier la prise en charge de la version préliminaire de OpenXR 1,0 !  désormais, dans le **moteur 4,26**, la prise en charge de HoloLens 2, Windows Mixed Reality et d’autres casques desktop VR est disponible via la prise en charge OpenXR intégrée du moteur.  le moteur non réel 4,26 prend également en charge le [plug-in d’extension OpenXR de Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal), ce qui permet l’interaction manuelle et la prise en charge des contrôleurs de réverbes de HP, en éclairant l' [ensemble des fonctionnalités de HoloLens 2 et Windows Mixed Reality casques](#roadmap).  le moteur inréel 4,26 est disponible aujourd’hui sur les [jeux Epic Lanceur](https://www.unrealengine.com/download/creators), avec MRTK-Unreal 0,12 prenant en charge les projets OpenXR.

### <a name="openxr-for-native-development"></a>OpenXR pour le développement natif

vous pouvez développer à l’aide de OpenXR sur un HoloLens 2 ou Windows Mixed Reality casque d’immersion immersif sur le bureau.  si vous n’avez pas accès à un casque, vous pouvez utiliser le HoloLens 2 Emulator ou le simulateur Windows Mixed Reality à la place.

pour commencer à développer des applications OpenXR pour HoloLens 2 ou Windows Mixed Reality des casques VR, consultez [la page prise en main du développement OpenXR](openxr-getting-started.md).

Pour une visite guidée de tous les principaux composants de l’API OpenXR, ainsi que des exemples d’applications réelles utilisant OpenXR aujourd’hui, consultez cette vidéo de procédure pas à pas de 60 minutes :

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Voir aussi

* <a href="https://www.khronos.org/openxr/" target="_blank">Plus d’informations sur OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Spécification OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Informations de référence sur l’API OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guide de référence rapide de OpenXR 1,0</a>