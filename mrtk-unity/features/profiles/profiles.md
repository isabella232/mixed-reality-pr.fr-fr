---
title: Profils
description: Profils de documentation dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, profils,
ms.openlocfilehash: 785d402e924a534627dfd1d742d2019d9ce9dd5a
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908243"
---
# <a name="profiles"></a>Profils

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

L’un des principaux moyens de configurer MRTK est d’utiliser les nombreux profils disponibles dans le package de base. L’[`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)objet principal d’une scène aura le profil actif, qui est un ScriptableObject. Le profil de configuration MRTK de niveau supérieur contient des données de sous-profil pour chaque noyau des systèmes centraux principaux, chacun étant conçu pour configurer le comportement de leurs sous-systèmes correspondants. En outre, ces sous-profils sont également des ScriptableObjects et peuvent donc contenir des références à d’autres objets de profil situés au niveau inférieur. Il existe une arborescence complète des profils connectés qui composent les informations de configuration pour le démarrage des sous-systèmes et des fonctionnalités MRTK.

Par exemple, le comportement du système d’entrée est régi par un profil de système d’entrée, comme le `DefaultMixedRealityInputSystemProfile` (Ressources/MRTK/Kit de développement logiciel (SDK)/Profils).

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>Inspecteur de profils</sup>

## <a name="background"></a>Arrière-plan

Les profils sont principalement destinés à prendre en charge des scénarios spécifiques sur plusieurs appareils, gérés via les fournisseurs de données. De cette façon, une application peut être conçue de façon indépendante des appareils et laisser les MRTK et les fournisseurs de données du profil gérer la prise en charge multiplateforme.

Il existe également des profils basés sur les fonctionnalités d’entrée de périphériques spécifiques, tels que le profil HoloLens 1, qui a par défaut des interactions de style GGV.

## <a name="xr-sdk"></a>Kit de développement logiciel (SDK) XR

::: moniker range=">= mrtkunity-2021-05"
Utilisez l’un des profils MRTK par défaut, qui sont tous configurés dans les pipelines XR d’Unity. Les « DefaultOpenXRConfigurationProfile » et « DefaultXRSDKConfigurationProfile » précédents sont maintenant marqués comme obsolètes.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Actuellement, il existe deux profils fournis pour le kit de développement logiciel (SDK) XR `DefaultXRSDKConfigurationProfile` et `DefaultHoloLens2XRSDKConfigurationProfile`. Par conséquent, les scènes des exemples ne sont pas entièrement prises en charge en raison des configurations spécifiques aux scènes et aux scénarios. Les exemples qui utilisent `DefaultMixedRealityToolkitConfigurationProfile` et `DefaultHoloLens2ConfigurationProfile` _peuvent_ être permutés à leurs profils du kit de développement logiciel (SDK) XR correspondants. Si vous utilisez OpenXR avec le kit de développement logiciel (SDK) XR, utilisez à la `DefaultOpenXRConfigurationProfile` place.

Un travail supplémentaire est entrepris pour faciliter la configuration et prendre en charge tous les exemples de scènes, ce qui permet de configurer côte à côte les XR et kit de développement logiciel (SDK) XR hérités. Consultez le problème [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) pour le suivi.
::: moniker-end

Pour plus d’informations sur la conversion des profils entre XR et le kit de développement logiciel (SDK) XR hérités, consultez [Configuration de MRTK pour le pipeline du kit de développement logiciel (SDK) XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline).

## <a name="default-profile"></a>Profil par défaut

MRTK fournit un ensemble de profils par défaut, qui couvre la plupart des plateformes et des scénarios pris en charge par MRTK. Par exemple, lorsque vous sélectionnez `DefaultMixedRealityToolkitConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel/Profils), vous pouvez essayer des scénarios sur VR (OpenVR, WMR) et HoloLens (1 et 2).

Notez qu’étant donné qu’il s’agit d’un profil d’utilisation générale, il n’est pas optimisé pour un cas d’usage particulier. Si vous souhaitez avoir des paramètres plus performants/spécifiques mieux adaptés à d’autres plateformes, consultez les autres profils ci-dessous, qui sont légèrement modifiés pour mieux utiliser leurs plateformes respectives.

## <a name="hololens-2-profile"></a>Profil HoloLens 2

Le MRTK fournit également un profil par défaut qui est optimisé pour le déploiement et le test sur le HoloLens 2 : `DefaultHoloLens2ConfigurationProfile` (Ressources/MRTK/Kit de développement logiciel (SDK)/Profils/HoloLens2).

Lorsque vous êtes invité à choisir un profil pour l’objet MixedRealityToolkit, utilisez ce profil au lieu du profil sélectionné par défaut.

Les principales différences entre le profil HoloLens2 et le profil par défaut sont les suivantes :

Fonctionnalités **Désactivées** :

- [Système de délimitation](../boundary/boundary-system-getting-started.md)
- [Système de téléportation](../teleport-system/teleport-system.md)
- [Système de reconnaissance spatiale](../spatial-awareness/spatial-awareness-getting-started.md)
- [Visualisation du maillage de la main](../input/hand-tracking.md) (en raison de la surcharge de performances)

Systèmes **activés** :

- Le [fournisseur de suivi oculaire](../input/eye-tracking/eye-tracking-main.md)
- Simulation d’entrée oculaire

Les paramètres de profil de la caméra sont définis pour correspondre afin que la qualité de l’éditeur et la qualité du joueur soient les mêmes. Cela diffère du profil de caméra par défaut où les affichages opaques sont définis sur une qualité supérieure. Cette modification signifie que la qualité de l’éditeur sera inférieure, ce qui correspondra davantage à ce qui sera affiché sur l’appareil.

> [!NOTE]
> Le système de reconnaissance spatiale est désactivé par défaut en fonction des commentaires des clients. il s’agit d’une visualisation intéressante pour voir initialement, mais elle est généralement désactivée pour éviter la distraction visuelle et l’impact sur les performances. Vous pouvez réactiver le système en suivant les [instructions fournies ici](../spatial-awareness/spatial-awareness-getting-started.md).
