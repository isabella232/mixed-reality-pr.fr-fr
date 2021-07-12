---
title: Définition de votre configuration XR
description: restez à jour avec les dernières recommandations de configuration de XR unity pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603711"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="0b98e-104">Définition de votre configuration XR</span><span class="sxs-lookup"><span data-stu-id="0b98e-104">Setting up your XR configuration</span></span>

<span data-ttu-id="0b98e-105">Une fois que vous avez [choisi une version Unity](choosing-unity-version.md), l’étape suivante consiste à sélectionner la configuration XR que vous allez utiliser pour créer votre application de réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="0b98e-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="0b98e-106">Choix d’une configuration XR</span><span class="sxs-lookup"><span data-stu-id="0b98e-106">Choosing an XR configuration</span></span>

<span data-ttu-id="0b98e-107">lorsque vous démarrez un nouveau projet unity, vous avez le choix entre plusieurs configurations XR : le **plug-in OpenXR de réalité mixte**, le **plug-in de XR** de la Windows et le **XR intégré hérité**.</span><span class="sxs-lookup"><span data-stu-id="0b98e-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="0b98e-108">Configuration de votre projet avec MRTK</span><span class="sxs-lookup"><span data-stu-id="0b98e-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="0b98e-109">le moyen le plus simple de configurer votre projet unity pour la réalité mixte consiste à utiliser la réalité mixte Shared Computer Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="0b98e-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="0b98e-110">MRTK pour Unity est un kit de développement multiplateforme Open source conçu pour faciliter la création d’applications de réalité mixte étonnantes.</span><span class="sxs-lookup"><span data-stu-id="0b98e-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="0b98e-112">MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales.</span><span class="sxs-lookup"><span data-stu-id="0b98e-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="0b98e-113">avec MRTK version 2, vous pouvez accélérer le développement d’applications pour Microsoft HoloLens, Windows Mixed Reality des casques immersifs (vr) et de nombreux autres appareils VR/AR.</span><span class="sxs-lookup"><span data-stu-id="0b98e-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="0b98e-114">Le projet vise à réduire les obstacles à l’entrée, ce qui permet à tout le monde de créer des applications de réalité mixte et de contribuer à la communauté dès que nous développons.</span><span class="sxs-lookup"><span data-stu-id="0b98e-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="0b98e-115">pour en savoir plus sur la Shared Computer Toolkit de la réalité mixte, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="0b98e-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="0b98e-116">Configuration manuelle sans MRTK</span><span class="sxs-lookup"><span data-stu-id="0b98e-116">Manual setup without MRTK</span></span>

<span data-ttu-id="0b98e-117">alors que Microsoft et la communauté ont créé des outils open source tels que la [réalité mixte Shared Computer Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) qui configurera automatiquement votre environnement pour la réalité mixte, certains développeurs peuvent souhaiter créer leurs expériences dès le départ.</span><span class="sxs-lookup"><span data-stu-id="0b98e-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]