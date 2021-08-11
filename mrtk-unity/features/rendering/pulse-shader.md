---
title: Nuanceur animé
description: Description sur les nuanceurs d’impulsions dans MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: add3aaa2a98ca2ddc1f60b0307a3defed3236d9a2c09aa70ea2d12b2d9638eba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228382"
---
# <a name="pulse-shader"></a>Nuanceur animé

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Utilisez le nuanceur d’impulsions pour animer un effet d’impulsion visuelle sur la reconstruction de la surface, un maillage manuel articulé ou tout autre maillage.

## <a name="shader-and-material"></a>Nuanceur et matériau

Les documents suivants utilisent **SR_Triangles** nuanceur. Vous pouvez configurer diverses options, telles que la couleur de remplissage, la couleur de ligne et la couleur de l’impulsion.

- **MRTK_Pulse_SpatialMeshBlue. mat** 
- **MRTK_Pulse_SpatialMeshPurple. mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue. mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple. mat** 

## <a name="prerequisites"></a>Prérequis

pour l’exemple de maillage spatial, assurez-vous que MRTK_Pulse_SpatialMeshBlue. mat ou MRTK_Pulse_SpatialMeshPurple. mat est affecté sous l’objet MixedRealityToolkit-> profil de sensibilisation spatiale-> afficher la Paramètres >.

pour l’exemple de maille, assurez-vous que MRTK_Pulse_ArticulatedHandMeshBlue. mat ou MRTK_Pulse_ArticulatedHandMeshPurple. mat est affecté dans ArticulatedHandMesh. prefab, qui doit lui-même être affecté dans MRTK Paramètres-> suivi de la main >-> de maille.

## <a name="how-it-works"></a>Fonctionnement

Le nuanceur de maille main utilise UVs pour mapper l’impulsion le long de la maille et pour faire disparaître le poignet. Le nuanceur de reconstruction de surface utilise les positions de vertex pour mapper l’impulsion.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Exemple de maillage spatial-PulseShaderSpatialMeshExample. Unity

comme pour l’expérience de l’interpréteur de commandes de HoloLens 2, vous pouvez pointer et appuyer avec la main pour générer un effet d’impulsion sur le maillage spatial. L’exemple de scène contient un objet ExampleSpatialMesh qui est une maille spatiale de test pour le mode de jeu Unity. Cet objet sera désactivé et masqué sur l’appareil.

Le script **PulseShaderSpatialMeshHandler. cs** génère l’effet d’impulsion sur le maillage spatial à la position du point d’accès si `PulseOnSelect` a la valeur true. La  `Auto Pulse` propriété peut également avoir la valeur true dans le matériel lui-même pour une animation répétée.  Dans l’exemple de scène, ce script est attaché au Prefab PulseShaderSpatialMeshParent.  Ce Prefab est référencé sous le profil de sensibilisation spatiale via la propriété Runtime spatial Mesh Prefab. Pendant l’exécution, le Prefab PulseShaderSpatialMeshParent et est instancié et ajouté à la hiérarchie spatiale (uniquement sur l’appareil, ce comportement ne peut pas être observé dans l’éditeur).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Exemple de maille manuelle-PulseShaderHandMeshExample. Unity

Cet exemple de scène illustre la visualisation du maillage à la main à l’aide du nuanceur Pulse. quand une main est détectée par l’appareil HoloLens, l’animation d’impulsions est déclenchée une seule fois. Cette rétroaction visuelle peut augmenter la confiance de l’utilisateur. 

Le script **PulseShaderHandMeshHandler. cs** génère un effet d’impulsion sur le matériau affecté. Par défaut, l’option « impulsion en main détectée » est cochée.
