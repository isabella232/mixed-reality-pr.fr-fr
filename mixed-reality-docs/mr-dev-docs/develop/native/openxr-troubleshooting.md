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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="ed722-104">Résolution des problèmes d’OpenXR</span><span class="sxs-lookup"><span data-stu-id="ed722-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="ed722-105">Voici quelques conseils de dépannage pour le développement d’une application OpenXR à l’aide du runtime Windows Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ed722-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="ed722-106">Si vous avez d’autres questions sur la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">spécification OpenXR 1,0</a>, visitez les <a href="https://community.khronos.org/c/openxr" target="_blank">Forums Khronos OpenXR</a> ou la <a href="https://khr.io/slack" target="_blank">marge #openxr canal</a>.</span><span class="sxs-lookup"><span data-stu-id="ed722-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="ed722-107">Il existe des problèmes connus dans le runtime Windows Mixed Reality OpenXR actuel avec les applications x86.</span><span class="sxs-lookup"><span data-stu-id="ed722-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="ed722-108">Vous devez créer des applications Desktop OpenXR pour x64 pour le moment.</span><span class="sxs-lookup"><span data-stu-id="ed722-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="ed722-109">Application OpenXR ne démarrant pas Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ed722-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="ed722-110">Si votre application OpenXR ne démarre pas Windows Mixed Reality quand vous l’exécutez, le runtime Windows Mixed Reality OpenXR peut ne pas être défini comme le runtime actif.</span><span class="sxs-lookup"><span data-stu-id="ed722-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="ed722-111">Veillez à suivre les instructions de [prise en main de OpenXR pour les casques pour Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) pour rendre le runtime actif.</span><span class="sxs-lookup"><span data-stu-id="ed722-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="ed722-112">Vous pouvez également exécuter le [outils de développement OpenXR pour Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) pour obtenir une aide supplémentaire sur l’état du runtime Windows Mixed Reality OpenXR sur votre système.</span><span class="sxs-lookup"><span data-stu-id="ed722-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>