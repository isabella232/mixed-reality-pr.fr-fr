---
title: Résolution des problèmes d’OpenXR
description: recherchez des ressources et des réponses aux problèmes courants de résolution des problèmes dans vos applications Windows Mixed Reality OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, native, application native, moteur personnalisé, intergiciel, résolution des problèmes
ms.openlocfilehash: 456dcf927c70aaaebc8dda1338d24acc910a1e801cf29e8880048d44f9432718
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219203"
---
# <a name="openxr-troubleshooting"></a>Résolution des problèmes d’OpenXR

voici quelques conseils de dépannage pour le développement d’une application OpenXR à l’aide du Runtime OpenXR Windows Mixed Reality.  Si vous avez d’autres questions sur la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">spécification OpenXR 1,0</a>, visitez les <a href="https://community.khronos.org/c/openxr" target="_blank">Forums Khronos OpenXR</a> ou la <a href="https://khr.io/slack" target="_blank">marge #openxr canal</a>.

>[!NOTE]
>il existe des problèmes connus dans le Windows Mixed Reality d’exécution OpenXR actuel avec les applications x86.  Vous devez créer des applications Desktop OpenXR pour x64 pour le moment.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>L’application OpenXR ne démarre pas Windows Mixed Reality

si votre application OpenXR ne démarre pas Windows Mixed Reality lorsque vous l’exécutez, le runtime Windows Mixed Reality OpenXR peut ne pas être défini en tant que runtime actif. suivez les instructions de [prise en main de OpenXR pour Windows Mixed Reality des casques](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) pour résoudre le problème.

vous pouvez également exécuter le [Outils de développement OpenXR pour Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) pour obtenir de l’aide sur l’état de vos systèmes Windows Mixed Reality le Runtime OpenXR.