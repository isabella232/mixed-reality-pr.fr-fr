---
title: Utilisation du support XR intégré hérité
description: Découvrez comment configurer vos projets Unity avec et sans MRTK à l’aide de la prise en charge héritée de XR intégrée.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, Windows Mixed Reality, UWP, XR, performance, Legacy, mrtk
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938113"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="af812-104">Utilisation du support XR intégré hérité</span><span class="sxs-lookup"><span data-stu-id="af812-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="af812-105">Configuration de votre projet avec MRTK</span><span class="sxs-lookup"><span data-stu-id="af812-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="af812-106">MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales.</span><span class="sxs-lookup"><span data-stu-id="af812-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="af812-107">MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.</span><span class="sxs-lookup"><span data-stu-id="af812-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="af812-108">Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="af812-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af812-109">Essayez nos didacticiels MRTK</span><span class="sxs-lookup"><span data-stu-id="af812-109">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="af812-110">Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="af812-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="af812-111">Configuration manuelle sans MRTK</span><span class="sxs-lookup"><span data-stu-id="af812-111">Manual setup without MRTK</span></span>

<span data-ttu-id="af812-112">Si vous ciblez Desktop VR, nous vous suggérons d’utiliser la plateforme autonome PC sélectionnée par défaut sur un nouveau projet Unity :</span><span class="sxs-lookup"><span data-stu-id="af812-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec PC, Mac & plateforme autonome en surbrillance](images/wmr-config-img-3.png)

<span data-ttu-id="af812-114">Si vous ciblez HoloLens 2, vous devez basculer vers l’plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="af812-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="af812-115">Sélectionner le **fichier > les paramètres de Build...**</span><span class="sxs-lookup"><span data-stu-id="af812-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="af812-116">Sélectionnez **plateforme Windows universelle** dans la liste plateforme et sélectionnez **basculer la plateforme**</span><span class="sxs-lookup"><span data-stu-id="af812-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="af812-117">Définir l' **architecture** sur **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="af812-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="af812-118">Définir l' **appareil cible** sur **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="af812-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="af812-119">Définir le **type de build** sur **D3D**</span><span class="sxs-lookup"><span data-stu-id="af812-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="af812-120">Définir le **SDK UWP** sur le **dernier installé**</span><span class="sxs-lookup"><span data-stu-id="af812-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="af812-121">Définir la **configuration de build** sur **Release** en raison de problèmes de performances connus avec Debug</span><span class="sxs-lookup"><span data-stu-id="af812-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Capture d’écran de la fenêtre des paramètres de build ouverte dans l’éditeur Unity avec plateforme Windows universelle mis en surbrillance](images/wmr-config-img-4.png)

<span data-ttu-id="af812-123">Après avoir défini votre plateforme, vous devez permettre à Unity de créer une [vue immersive](../../design/app-views.md) au lieu d’une vue en 2D lors de l’exportation.</span><span class="sxs-lookup"><span data-stu-id="af812-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="af812-124">Le XR hérité est déconseillé dans Unity 2019 et supprimé dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="af812-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="af812-125">Ouvrir les **paramètres du lecteur...** à partir des paramètres de **Build... et** développez le groupe de **paramètres XR**</span><span class="sxs-lookup"><span data-stu-id="af812-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="af812-126">Dans la section **paramètres XR** , sélectionnez la **réalité virtuelle prise en charge** pour ajouter la liste des appareils de réalité virtuelle</span><span class="sxs-lookup"><span data-stu-id="af812-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="af812-127">Définir le **format de profondeur** sur **16 bits** et activer le partage de **mémoire tampon de profondeur**</span><span class="sxs-lookup"><span data-stu-id="af812-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="af812-128">Définir le **mode de rendu stéréo** sur **une seule instance de passage**</span><span class="sxs-lookup"><span data-stu-id="af812-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="af812-129">Sélectionnez la **communication à distance holographique WSA prise en charge** si vous souhaitez utiliser la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="af812-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Capture d’écran de la fenêtre Paramètres du projet ouverte dans l’éditeur Unity avec la section paramètres du lecteur mise en surbrillance](images/wmr-config-img-9.png)