---
title: Vue d’ensemble et objectifs du tutoriel
description: Suivez ce cours pour découvrir comment implémenter la reconnaissance faciale Azure au sein d’une application de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens
ms.localizationpriority: high
ms.openlocfilehash: b7e04a03f01beb1438f6f723c3938d05a60c9131
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581163"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="7cf3d-104">1. Vue d’ensemble et objectifs</span><span class="sxs-lookup"><span data-stu-id="7cf3d-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="7cf3d-105">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="7cf3d-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7cf3d-106"><strong>Cours</strong></span><span class="sxs-lookup"><span data-stu-id="7cf3d-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="7cf3d-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7cf3d-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7cf3d-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="7cf3d-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="7cf3d-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="7cf3d-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="7cf3d-110">✔️</span><span class="sxs-lookup"><span data-stu-id="7cf3d-110">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7cf3d-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="7cf3d-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7cf3d-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="7cf3d-112">Prerequisites</span></span>

* <span data-ttu-id="7cf3d-113">PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="7cf3d-113">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="7cf3d-114">SDK Windows 10 (10.0.18362.0 ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="7cf3d-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="7cf3d-115">Capacité de programmation C# de base</span><span class="sxs-lookup"><span data-stu-id="7cf3d-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="7cf3d-116">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="7cf3d-116">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="7cf3d-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019.2.X installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté</span><span class="sxs-lookup"><span data-stu-id="7cf3d-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7cf3d-118">La version Unity recommandée pour cette série de tutoriels est Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="7cf3d-119">Cela remplace toute exigence ou recommandation de version Unity énoncée dans les prérequis indiqués ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7cf3d-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="7cf3d-120">Leçon suivante : 2. Initialisation de votre projet et première application</span><span class="sxs-lookup"><span data-stu-id="7cf3d-120">Next lesson: 2. Initializing your project and first application</span></span>](./mr-learning-base-02.md)