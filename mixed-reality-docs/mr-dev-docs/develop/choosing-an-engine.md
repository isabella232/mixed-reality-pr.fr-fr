---
title: Choix de votre moteur
description: découvrez les choix de moteurs disponibles pour le développement de la réalité mixte pour HoloLens et VR.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: 14235852f8c90e7ccc4f105f2938ce514ae2933973469db9a0e01bd03d2c1b6d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227549"
---
# <a name="choosing-your-engine"></a>Choix de votre moteur

Notre documentation vous propose plusieurs chemins de développement. La première étape consiste à trouver la technologie qui vous convient. Si vous en avez déjà une en tête, passez directement à l’onglet correspondant ci-dessous. Si vous hésitez ou que vous débutez, jetez un œil aux différentes technologies présentées pour voir ce qu’elles offrent, examinez les plateformes et outils disponibles, puis commencez à créer !

> [!IMPORTANT]
> Jetez un coup d’œil à la **[présentation des guides de portage](porting-apps/porting-overview.md)** si vous avez des projets existants que vous souhaitez déplacer vers HoloLens 2 ou vers des casques VR immersifs comme les casques Reverb G2. Nous avons des guides pour les projets qui utilisent HTK, MRTK v1 ou SteamVR, ou qui ont été développés pour des casques immersifs tels qu’Oculus Rift ou HTC Vive.

## <a name="engine-overview"></a>Vue d’ensemble du moteur

* **Unity** est l’une des principales plateformes de développement en temps réel sur le marché, avec le code d’exécution sous-jacent écrit en C++ et tous les scripts de développement sont effectués en C#. Quel que soit le type de projet qui vous intéresse, qu’il s’agisse de créer des jeux, des films, des animations ou encore de restituer des concepts architecturaux ou d’ingénierie dans un monde virtuel, Unity a l’infrastructure qu’il vous faut.

* Le **moteur non réel 4** est un moteur de création puissant et open source avec une prise en charge complète de la réalité mixte en C++ et en plans. À compter d’Unreal Engine 4.25, la prise en charge d’HoloLens est complète et prête pour la production. Avec des fonctionnalités telles que le système flexible Blueprints Visual Scripting, les concepteurs peuvent utiliser pratiquement tous les concepts et outils qui sont généralement réservés aux seuls programmeurs. Les créateurs des différents secteurs peuvent bénéficier de la liberté et du contrôle qu’il offre pour créer du contenu de pointe, des expériences interactives et des mondes virtuels immersifs.

* Les développeurs **natifs** ayant une expérience d’écriture de leurs propres convertisseurs 3D peuvent créer un moteur personnalisé à l’aide de OpenXR. OpenXR est une norme d’API ouverte et libre de redevance proposée par Khronos. Elle permet aux moteurs d’accéder en mode natif à une large gamme d’appareils de fabricants qui couvrent le spectre de réalité mixte. Vous pouvez développer avec OpenXR sur HoloLens 2 ou un casque immersif Windows Mixed Reality sur le bureau.

* Les développeurs **Web** qui créent des expériences Web remarquables d’e/VR croisées peuvent utiliser **WebXR**.

    > [!NOTE]
    > **Babylon.js** pour le développement de HoloLens est actuellement en cours. Découvrez les [dernières nouvelles et participez à la communauté](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)!

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>Fonctionnalités et appareils

<br>

| Logistics | Unity | Unreal | JavaScript | Moteur personnalisé <br>(à l’aide de OpenXR) |
|---|---|---|---|---|
| Langage | C# | C++ | JavaScript | C/C++ |
| Tarifs | [Tarification Unity](https://store.unity.com/#plans-individual) | [Tarification inréel](https://www.unrealengine.com/download) | Gratuit | Gratuit |

<br>

| Fonctionnalités de l’appareil | Unity | Unreal | JavaScript | Moteur personnalisé <br>(à l’aide de OpenXR) |
|---|---|---|---|---|
| Suivi des appareils/affichages | ✔️ | ✔️ | ✔️ | ✔️ |
| Entrée manuelle | ✔️ | ✔️ | ✔️ | ✔️ |
| Entrée oculaire | ✔️ | ✔️ | ❌ | ✔️ |
| Entrée vocale | ✔️ | ✔️ | ✔️ | ✔️ |
| Contrôleurs de mouvement | ✔️ | ✔️ | ✔️ | ✔️ |
| Test de positionnement plan/maillage | ✔️ | ✔️ | ✔️ | ✔️ |
| Compréhension des scènes | ✔️ | ✔️ | ❌ | ✔️ |
| Son spatial | ✔️ | ✔️ | ✔️ | ✔️ |
| Détection du code QR | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| Matériel | Unity | Unreal | JavaScript | Moteur personnalisé <br>(à l’aide de OpenXR) |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens (1ère génération) | ✔️ | ✔️ | ❌ | WinRT (hérité) uniquement |
| [Casques Windows Mixed Reality](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| Casques SteamVR | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus Quest/Rift | ✔️ | ✔️ | ✔️ | ✔️ |
| Mobile (ARCore/ARKit) | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| Outils | Unity | Unreal | JavaScript | Moteur personnalisé <br>(à l’aide de OpenXR) |
|---|---|---|---|---|
| Mixed Reality Toolkit | ✔️ | ✔️ | ❌  | ❌ |
| Outils de verrouillage universel | ✔️ | ❌ | ❌  | ❌ |
<!-- | Maillage | ❌ | ❌ | ❌ | ❌ | -->

<br>

| Services cloud | Unity | Unreal | JavaScript | Moteur personnalisé <br>(à l’aide de OpenXR) |
|---|---|---|---|---|
| Azure Spatial Anchors | ✔️ | ✔️ | ❌ | ✔️ |
| Azure Object Anchors | ✔️ | ❌ | ❌ | ✔️ |
| Azure Remote Rendering | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * le rendu distant Azure est actuellement pris en charge dans les applications utilisant les api WinRT héritées (Windows plug-in XR dans unity). La prise en charge d’ARR pour les applications OpenXR sera bientôt disponible.

## <a name="next-steps"></a>Étapes suivantes

[!INCLUDE[](includes/tools-next-steps.md)]