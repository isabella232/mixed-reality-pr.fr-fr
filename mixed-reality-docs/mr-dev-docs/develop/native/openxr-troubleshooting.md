---
title: Résolution des problèmes d’OpenXR
description: Résolvez les problèmes dans vos applications OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, native, application native, moteur personnalisé, intergiciel, résolution des problèmes
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903095"
---
# <a name="openxr-troubleshooting"></a>Résolution des problèmes d’OpenXR

Voici quelques conseils de dépannage pour le développement d’une application OpenXR à l’aide du runtime Windows Mixed Reality OpenXR.  Si vous avez d’autres questions sur la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">spécification OpenXR 1,0</a>, visitez les <a href="https://community.khronos.org/c/openxr" target="_blank">Forums Khronos OpenXR</a> ou la <a href="https://khr.io/slack" target="_blank">marge #openxr canal</a>.

>[!NOTE]
>Il existe des problèmes connus dans le runtime Windows Mixed Reality OpenXR actuel avec les applications x86.  Vous devez créer des applications Desktop OpenXR pour x64 pour le moment.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Application OpenXR ne démarrant pas Windows Mixed Reality

Si votre application OpenXR ne démarre pas Windows Mixed Reality quand vous l’exécutez, le runtime Windows Mixed Reality OpenXR peut ne pas être défini comme le runtime actif.  Veillez à suivre les instructions de [prise en main de OpenXR pour les casques pour Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) pour rendre le runtime actif.

Vous pouvez également exécuter le [outils de développement OpenXR pour Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) pour obtenir une aide supplémentaire sur l’état du runtime Windows Mixed Reality OpenXR sur votre système.