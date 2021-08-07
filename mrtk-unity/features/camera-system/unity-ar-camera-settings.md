---
title: Paramètres de la caméra Unity AR
description: Documentation sur l’utilisation de l’appareil photo AR dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, appareil photo,
ms.openlocfilehash: a2d145823557b473bd7d34170b283e782151c24277b8f16586516ffe78f8e735
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210062"
---
# <a name="unity-ar-camera-settings-provider"></a>Fournisseur de paramètres de caméra Unity AR

Le fournisseur de paramètres de l’appareil Unity AR est un composant MRTK expérimental qui permet aux applications de réalité mixte de s’exécuter sur des appareils Android et iOS.

## <a name="unity-ar-camera-settings-provider-options"></a>Options du fournisseur des paramètres de l’appareil Unity AR

![Configuration des paramètres de l’appareil Unity AR](../images/camera-system/UnityArSettingsConfiguration.png)

Pour obtenir un guide sur la façon d’ajouter le fournisseur à votre scène : [Comment configurer MRTK pour iOS et Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Paramètres de suivi

Le fournisseur de paramètres de l’appareil Unity AR permet d’effectuer des options de configuration pour le suivi. Ces paramètres sont spécifiques à l’implémentation du fournisseur de paramètres d’appareil photo Unity.

**Source de pose**

La source de pose définit les types disponibles des poses de suivi de réalité augmentée. En général, ces valeurs sont mappées à un composant de l’appareil sur lequel l’application s’exécute.

Les options disponibles sont décrites dans le tableau suivant.

| Option | Description |
| --- | --- |
| Center | L’œil central d’un appareil monté en tête. |
| Caméra couleur | Caméra de couleur d’un appareil mobile. |
| Head | L’œil-tête d’un appareil monté en tête, souvent légèrement au-dessus du centre. |
| Œil gauche | L’œil gauche d’un appareil monté en tête. |
| Pose gauche | Le contrôleur de gauche pose. |
| Œil droit | L’œil droit d’un appareil monté en tête. |
| Bonne pose | Le contrôleur de droite pose. |

La valeur par défaut de la source de pose est **caméra de couleurs**, pour permettre un affichage transparent sur des appareils mobiles, tels qu’un téléphone ou une tablette.

**Type des suivis**

Le type de suivi définit la ou les parties de la pose qui seront utilisées pour le suivi.

Les options disponibles sont décrites dans le tableau suivant.

| Option | Description |
| --- | --- |
| Position | Position de l’appareil. |
| Rotation | Rotation de l’appareil. |
| Rotation et position | Position et rotation de l’appareil. |

La valeur par défaut pour le type de suivi est **rotation et position**, pour activer l’expérience de suivi la plus riche.

**Type de mise à jour**

Le type de mise à jour définit à quels points, pendant le traitement des trames, les données de pose sont échantillonnées.

Les options disponibles sont décrites dans le tableau suivant.

| Option | Description |
| --- | --- |
| Avant le rendu | Juste avant le rendu. |
| Update | Pendant la phase de mise à jour du frame. |
| Mettre à jour et avant le rendu | Pendant la phase de mise à jour et juste avant le rendu. |

La valeur par défaut pour le type de suivi est **Update et avant Render**, pour activer la latence de suivi la plus faible.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du système d’appareil photo](camera-system-overview.md)
- [création d’un fournisseur de Paramètres d’appareil photo](create-settings-provider.md)
