---
title: Suivi de la main dans Unreal
description: Découvrez comment utiliser les entrées de suivi manuel, les maillages de pose et de main, ainsi que les animations de liens dynamiques dans les applications de réalité mixte.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, suivi manuel, non réel, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: e482c93233348325736d2c224788e9174c1f3b67
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010159"
---
# <a name="hand-tracking-in-unreal"></a>Suivi de la main dans Unreal

Le système de suivi de la main utilise les paumes et les doigts d’une personne comme entrée. Les données sur la position et la rotation de chaque doigt, le Palm entier et les gestes manuel sont disponibles. À partir de 4,26, le suivi manuel est basé sur le plug-in HeadMountedDisplay et utilise une API commune sur l’ensemble des plateformes et appareils XR. Les fonctionnalités sont les mêmes pour les systèmes Windows Mixed Reality et OpenXR.

## <a name="hand-pose"></a>Poser à la main

La pose de main vous permet de suivre et d’utiliser les mains et les doigts de vos utilisateurs comme entrée, qui sont accessibles à la fois dans les plans et C++. L’API inréelle envoie les données sous forme de système de coordonnées, avec les battements synchronisés avec le moteur inréel.

![Squelette de main](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Animation de lien dynamique à la main

Les poses de main sont exposées à l’animation à l’aide du [plug-in Live Link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Si les plug-ins Windows Mixed Reality et Live Link sont activés :
1. Sélectionnez **fenêtre > lien dynamique** pour ouvrir la fenêtre de l’éditeur de liens actifs.
2. Sélectionner la **source** et activer la source de suivi de la **main Windows Mixed Reality**

![Source de la liaison dynamique](images/unreal/live-link-source.png)

Une fois que vous avez activé la source et ouvert une ressource d’animation, développez la section **animation** sous l’onglet Aperçu de la **scène** . vous pouvez également voir d’autres options.

![Animation des liens dynamiques](images/unreal/live-link-animation.png)

La hiérarchie d’animation manuelle est la même que dans `EWMRHandKeypoint` . L’animation peut être reciblée à l’aide de **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:

![Animation de lien dynamique 2](images/unreal/live-link-animation2.png)

Elle peut également être sous-classée dans l’éditeur :

![Remappage de liaison dynamique](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Maille manuelle

### <a name="hand-mesh-as-a-tracked-geometry"></a>Maille de main en tant que géométrie suivie

> [!IMPORTANT]
> L’obtention de maillages de main en tant que géométrie suivie dans OpenXR vous oblige à appeler **Set use main Mesh** avec la **géométrie de suivi activée**.

Pour activer ce mode, vous devez appeler **Set use main Mesh** avec **Geometry de suivi activé**:

![Plan de la lecture de début d’événement connecté pour définir la fonction de maillage à la main avec le mode de géométrie de suivi activé](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> Il n’est pas possible d’activer les deux modes en même temps. Si vous en activez un, l’autre est automatiquement désactivée.

### <a name="accessing-hand-mesh-data"></a>Accès aux données de maillage de la main

![Maille manuelle](images/unreal/hand-mesh.png)

Avant de pouvoir accéder aux données de maillage manuel, vous devez :
- Sélectionnez votre ressource **ARSessionConfig** , développez les **paramètres AR-> World Mapping** Settings, puis cochez la case **générer des données de maillage à partir de la géométrie suivie**.

Voici les paramètres de maillage par défaut :

1.  Utiliser les données de maillage pour l’occlusion
2.  Générer une collision pour les données de maillage
3.  Générer un maillage de navigation pour les données de maillage
4.  Rendu des données de maillage dans le paramètre filaire – débogage qui affiche le maillage généré

Ces valeurs de paramètre sont utilisées comme maillage de mappage spatial et par défaut. Vous pouvez les modifier à tout moment dans des plans ou du code pour n’importe quelle maille.

### <a name="c-api-reference"></a>Informations de référence sur l’API C++
Utilisez `EEARObjectClassification` pour rechercher des valeurs de maillage de main dans tous les objets suivis.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

Les délégués suivants sont appelés lorsque le système détecte tout objet suivi, y compris un maillage de main.

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Assurez-vous que vos gestionnaires de délégués suivent la signature de la fonction ci-dessous :

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Vous pouvez accéder aux données de maillage par le biais des  `UARTrackedGeometry::GetUnderlyingMesh` éléments suivants :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>Informations de référence sur l’API Blueprint

Pour travailler avec des maillages de main dans des plans :
1. Ajouter un composant **ARTrackableNotify** à un acteur Blueprint

![Notification ARTrackable](images/unreal/ar-trackable-notify.png)

2. Accédez au panneau des **Détails** et développez la section **événements** .

![ARTrackable Notify 2](images/unreal/ar-trackable-notify2.png)

3. Remplacer sur l’ajout/la mise à jour/suppression de la géométrie suivie avec les nœuds suivants dans votre graphique d’événements :

![Sur ARTrackable Notify](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Visualisation de maillage manuel dans OpenXR

La méthode recommandée pour visualiser le maillage direct consiste à utiliser le plug-in XRVisualization de Epic avec le [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

Ensuite, dans l’éditeur de modèle, vous devez utiliser la fonction de **maille Set use main** du [plug-in OpenXR de Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal) avec l' **option XRVisualization activée** comme paramètre :

![Plan de la lecture de début d’événement connecté pour définir la fonction de maillage à la main avec le mode xrvisualization activé](images/unreal-hand-tracking-img-05.png)

Pour gérer le processus de rendu, vous devez utiliser le **contrôleur de mouvement de rendu** de XRVisualization :

![Plan de la fonction de données d’obtenir le contrôleur de mouvement connecté à la fonction de contrôle de mouvement de rendu](images/unreal-hand-tracking-img-06.png)

Résultat :

![Image de la main numérique superposée sur une main humaine réelle](images/unreal-hand-tracking-img-07.png) 

Si vous avez besoin de quelque chose de plus compliqué, par exemple en dessinant une maille avec un nuanceur personnalisé, vous devez obtenir les maillages sous la forme d’une géométrie suivie. 

## <a name="hand-rays"></a>Rayon émanant de la main

La mise en place de la main fonctionne pour les interactions proches comme la saisie d’objets ou la pression sur les boutons. Toutefois, vous devez parfois travailler avec des hologrammes éloignés de vos utilisateurs. Cela peut être accompli avec des rayons de main, qui peuvent être utilisés comme périphériques de pointage à la fois dans le C++ et dans les plans. Vous pouvez dessiner un rayon de votre main à un point éloigné et, avec une certaine aide du suivi de rayon inréel, sélectionner un hologramme qui n’est normalement pas accessible. 

> [!IMPORTANT]
> Étant donné que tous les résultats de fonction changent chaque frame, ils sont tous rendus accessibles. Pour plus d’informations sur les fonctions pures et impures ou pouvant être appelées, consultez le Guide de l’utilisateur Blueprint sur les [fonctions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Mouvements

HoloLens 2 effectue le suivi des mouvements spatiaux, ce qui signifie que vous pouvez capturer ces mouvements comme entrée. Le suivi des mouvements est basé sur un modèle d’abonnement. Vous devez utiliser la fonction « configurer les gestes » pour indiquer à l’appareil les gestes que vous souhaitez suivre.  Vous trouverez plus d’informations sur les gestes dans le document sur l' [utilisation de base de HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK. À partir de là, vous pouvez passer au module suivant :

> [!div class="nextstepaction"]
> [Ancres spatiales locales](unreal-spatial-anchors.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Caméra HoloLens](unreal-hololens-camera.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.
