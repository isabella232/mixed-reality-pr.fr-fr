---
title: Format du fichier d’animation d’entrée
description: Documentation sur la spécification de format de fichier binaire d’animation d’entrée dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 400212d80833f5d8dfbb3c5265c755ed2e127131
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177001"
---
# <a name="input-animation-file-format"></a>Format du fichier d’animation d’entrée

## <a name="overall-structure"></a>Structure globale

Le fichier binaire d’animation d’entrée commence par un nombre magique entier 64 bits. La valeur de ce nombre en notation hexadécimale est `0x6a8faf6e0f9e42c6` et peut être utilisée pour identifier les fichiers d’animation d’entrée valides.

Les huit octets suivants sont deux valeurs Int32 qui déclarent le numéro de version principale et secondaire du fichier.

Le reste du fichier est pris en considération par les données d’animation, qui peuvent changer entre les numéros de version.

| Section | Type |
|---------|------|
| Nombre magique | Int64 |
| Numéro de version principale | Int32 |
| Numéro de version mineure | Int32 |
| Données d’animation | _Voir la section version_ |

## <a name="version-11"></a>Version 1.1

Les données d’animation d’entrée se composent de trois valeurs booléennes qui indiquent si l’animation contient des données de pointage d’appareil photo, de main et oculaire, suivies d’une séquence de courbes d’animation. Les courbes présentes dépendent des valeurs de ces valeurs booléennes. Chaque courbe peut avoir un nombre différent d’images clés.

| Section | Type | Notes |
|---------|------|------|
| A une photo | Boolean | |
| Contient des données de la main | Boolean | |
| A un regard oculaire| Boolean | |
| Appareil photo | [Créer des courbes](#pose-curves) | Uniquement en cas de pose de l’appareil photo |
| Suivi de la main à gauche | [Courbe booléenne](#boolean-curve) | Uniquement si les données de la main ont la valeur true |
| Suivi à droite | [Courbe booléenne](#boolean-curve) | Uniquement si les données de la main ont la valeur true |
| Pincer la main à gauche | [Courbe booléenne](#boolean-curve) | Uniquement si les données de la main ont la valeur true |
| Pincement manuel | [Courbe booléenne](#boolean-curve) | Uniquement si les données de la main ont la valeur true |
| Jointures à gauche | [Courbes de pose conjointe](#joint-pose-curves) | Uniquement si les données de la main ont la valeur true |
| Jointures manuelles droite | [Courbes de pose conjointe](#joint-pose-curves) | Uniquement si les données de la main ont la valeur true |
| Point de regard | [Courbes de rayon](#ray-curves)] | Uniquement si a un point de regard visuel est vrai |

## <a name="version-10"></a>Version 1.0

Les données d’animation d’entrée se composent d’une séquence de courbes d’animation. Le nombre et la signification des courbes d’animation sont fixes, mais chaque courbe peut avoir un nombre différent d’images clés.

| Section | Type |
|---------|------|
| Appareil photo | [Créer des courbes](#pose-curves) |
| Suivi de la main à gauche | [Courbe booléenne](#boolean-curve) |
| Suivi à droite | [Courbe booléenne](#boolean-curve) |
| Pincer la main à gauche | [Courbe booléenne](#boolean-curve) |
| Pincement manuel | [Courbe booléenne](#boolean-curve) |
| Jointures à gauche | [Courbes de pose conjointe](#joint-pose-curves) |
| Jointures manuelles droite | [Courbes de pose conjointe](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Courbes de pose conjointe

Pour chaque main, une séquence de courbes d’animation communes est stockée. Le nombre de jointures est fixe et un ensemble de courbes de pose est stocké pour chaque jointure.

| Section | Type |
|---------|------|
| Aucun | [Créer des courbes](#pose-curves) |
| Du poignet | [Créer des courbes](#pose-curves) |
| Palm | [Créer des courbes](#pose-curves) |
| ThumbMetacarpalJoint | [Créer des courbes](#pose-curves) |
| ThumbProximalJoint | [Créer des courbes](#pose-curves) |
| ThumbDistalJoint | [Créer des courbes](#pose-curves) |
| ThumbTip | [Créer des courbes](#pose-curves) |
| IndexMetacarpal | [Créer des courbes](#pose-curves) |
| IndexKnuckle | [Créer des courbes](#pose-curves) |
| IndexMiddleJoint | [Créer des courbes](#pose-curves) |
| IndexDistalJoint | [Créer des courbes](#pose-curves) |
| IndexTip | [Créer des courbes](#pose-curves) |
| MiddleMetacarpal | [Créer des courbes](#pose-curves) |
| MiddleKnuckle | [Créer des courbes](#pose-curves) |
| MiddleMiddleJoint | [Créer des courbes](#pose-curves) |
| MiddleDistalJoint | [Créer des courbes](#pose-curves) |
| MiddleTip | [Créer des courbes](#pose-curves) |
| RingMetacarpal | [Créer des courbes](#pose-curves) |
| RingKnuckle | [Créer des courbes](#pose-curves) |
| RingMiddleJoint | [Créer des courbes](#pose-curves) |
| RingDistalJoint | [Créer des courbes](#pose-curves) |
| RingTip | [Créer des courbes](#pose-curves) |
| PinkyMetacarpal | [Créer des courbes](#pose-curves) |
| PinkyKnuckle | [Créer des courbes](#pose-curves) |
| PinkyMiddleJoint | [Créer des courbes](#pose-curves) |
| PinkyDistalJoint | [Créer des courbes](#pose-curves) |
| PinkyTip | [Créer des courbes](#pose-curves) |

### <a name="pose-curves"></a>Créer des courbes

Les courbes de pose sont une séquence de 3 courbes d’animation pour le vecteur de position, suivie de 4 courbes d’animation pour le Quaternion de rotation.

| Section | Type |
|---------|------|
| Position X | [Courbe flottante](#float-curve) |
| Position Y | [Courbe flottante](#float-curve) |
| Position Z | [Courbe flottante](#float-curve) |
| Rotation X | [Courbe flottante](#float-curve) |
| Rotation Y | [Courbe flottante](#float-curve) |
| Rotation Z | [Courbe flottante](#float-curve) |
| Rotation W | [Courbe flottante](#float-curve) |

### <a name="ray-curves"></a>Courbes de rayon

Les courbes de rayon sont une séquence de 3 courbes d’animation pour le vecteur d’origine, suivie de 3 courbes d’animation pour le vecteur de direction.

| Section | Type |
|---------|------|
| Origine X | [Courbe flottante](#float-curve) |
| Origine Y | [Courbe flottante](#float-curve) |
| Origine Z | [Courbe flottante](#float-curve) |
| Direction X | [Courbe flottante](#float-curve) |
| Direction Y | [Courbe flottante](#float-curve) |
| Direction Z | [Courbe flottante](#float-curve) |

### <a name="float-curve"></a>Courbe flottante

Les courbes à virgule flottante sont des courbes de Bézier à part entière avec un nombre variable d’images clés. Chaque image clé stocke un temps et une valeur de courbe, ainsi que des tangentes et des poids à gauche et à droite de chaque image clé.

| Section | Type |
|---------|------|
| Mode de pré-habillage | Int32, [mode habillage](#wrap-mode) |
| Mode après retour à la ligne | Int32, [mode habillage](#wrap-mode) |
| Nombre d’images clés | Int32 |
| Images clés | [Image clé à virgule flottante](#float-keyframe) |

### <a name="float-keyframe"></a>Image clé à virgule flottante

Une image clé en virgule flottante stocke les valeurs de tangente et de poids en même temps que la valeur et l’heure de base.

| Section | Type |
|---------|------|
| Temps | Float32 |
| Valeur | Float32 |
| Intangente | Float32 |
| En tangente | Float32 |
| Inpoids | Float32 |
| Poids | Float32 |
| WeightedMode | Int32, [mode pondéré](#weighted-mode) |

### <a name="boolean-curve"></a>Courbe booléenne

Les courbes booléennes sont des séquences simples de valeurs on/off. Sur chaque image clé, la valeur de la courbe est retournée immédiatement.

| Section | Type |
|---------|------|
| Mode de pré-habillage | Int32, [mode habillage](#wrap-mode) |
| Mode après retour à la ligne | Int32, [mode habillage](#wrap-mode) |
| Nombre d’images clés | Int32 |
| Images clés | [Image clé booléenne](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Image clé booléenne

Une image clé booléenne stocke uniquement une heure et une valeur.

| Section | Type |
|---------|------|
| Temps | Float32 |
| Valeur | Float32 |

### <a name="wrap-mode"></a>Mode habillage

La sémantique des modes pré-et après retour à la ligne suit la définition [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) . Il s’agit d’une combinaison des bits suivants :

| Valeur | Signification |
|-------|---------|
| 0 | Default : lit le mode de répétition par défaut défini à un niveau supérieur. |
| 1 | Une fois : lorsque le temps atteint la fin du clip d’animation, le clip s’arrête automatiquement et l’heure est réinitialisée au début du clip. |
| 2 | Boucle : quand le temps atteint la fin du clip d’animation, l’heure se poursuit au début. |
| 4 | Essai pingpong : lorsque le temps atteint la fin du clip d’animation, l’heure effectue un test ping de la minuterie entre le début et la fin. |
| 8 | ClampForever : lit l’animation. Lorsqu’il atteint la fin, il continue de reproduire la dernière image et ne s’arrête jamais. |

### <a name="weighted-mode"></a>Mode pondéré

La sémantique du mode pondéré suit la définition [WeightedMode Unity](https://docs.unity3d.com/ScriptReference/WeightedMode.html) .

| Valeur | Signification |
|-------|---------|
| 0 | None : exclure les deux types d’inpoids ou de poids lors du calcul des segments de courbe. |
| 1 | Dans : inclure inpoids lors du calcul du segment de courbe précédent. |
| 2 | Out : inclure le poids pour le calcul du segment de courbe suivant. |
| 3 | Les deux : incluent l’inpoids et le poids pour le calcul des segments de courbe. |
