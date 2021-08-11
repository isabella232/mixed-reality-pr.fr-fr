---
title: Définition de votre configuration XR
description: restez à jour avec les dernières recommandations de configuration de XR unity pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: 72f17ec9fc74143a2ae6cc51e1ffed0c73d13ef04ef5c4004537be70d1daaaca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202720"
---
# <a name="setting-up-your-xr-configuration"></a>Définition de votre configuration XR

Une fois que vous avez [choisi une version Unity](choosing-unity-version.md), l’étape suivante consiste à sélectionner la configuration XR que vous allez utiliser pour créer votre application de réalité mixte :

## <a name="choosing-an-xr-configuration"></a>Choix d’une configuration XR

lorsque vous démarrez un nouveau projet unity, vous avez le choix entre plusieurs configurations XR : le **plug-in OpenXR de réalité mixte**, le **plug-in de XR** de la Windows et le **XR intégré hérité**.

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configuration de votre projet avec MRTK

le moyen le plus simple de configurer votre projet unity pour la réalité mixte consiste à utiliser la réalité mixte Shared Computer Toolkit (MRTK).  MRTK pour Unity est un kit de développement multiplateforme Open source conçu pour faciliter la création d’applications de réalité mixte étonnantes.

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales.  avec MRTK version 2, vous pouvez accélérer le développement d’applications pour Microsoft HoloLens, Windows Mixed Reality des casques immersifs (vr) et de nombreux autres appareils VR/AR. Le projet vise à réduire les obstacles à l’entrée, ce qui permet à tout le monde de créer des applications de réalité mixte et de contribuer à la communauté dès que nous développons.

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

pour en savoir plus sur la Shared Computer Toolkit de la réalité mixte, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Configuration manuelle sans MRTK

alors que Microsoft et la communauté ont créé des outils open source tels que la [réalité mixte Shared Computer Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) qui configurera automatiquement votre environnement pour la réalité mixte, certains développeurs peuvent souhaiter créer leurs expériences dès le départ.

[!INCLUDE[](includes/xr/manual-setup.md)]