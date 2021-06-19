---
title: Choix de votre pipeline de développement
description: Restez à jour avec les dernières recommandations en matière de pipeline de développement Unity pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394553"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="f9ec7-104">Choix de votre pipeline de développement</span><span class="sxs-lookup"><span data-stu-id="f9ec7-104">Choosing your developer pipeline</span></span>

![Bannière du logo Unity](../images/unity_logo_banner.png)<br>

<span data-ttu-id="f9ec7-106">Bien que nous **vous recommandons actuellement d’installer unity 2019,4 LTS et d’utiliser des XR intégrées héritées pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="f9ec7-107">Boîte à outils de réalité mixte (recommandé)</span><span class="sxs-lookup"><span data-stu-id="f9ec7-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="f9ec7-108">La configuration d’Unity recommandée de Microsoft pour HoloLens 2 est la boîte à outils de réalité mixte...</span><span class="sxs-lookup"><span data-stu-id="f9ec7-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="f9ec7-109">Installer l’outil de fonctionnalité de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="f9ec7-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="f9ec7-110">[Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) est un nouveau moyen pour les développeurs de découvrir et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="f9ec7-111">Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="f9ec7-112">Une fois que vous avez validé les packages souhaités, Mixed Reality Feature Tool les télécharge dans le projet de votre choix.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f9ec7-113">Importation du kit de pratiques de réalité mixte pour Unity</span><span class="sxs-lookup"><span data-stu-id="f9ec7-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="f9ec7-115">Le [Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="f9ec7-116">Installez le package Mixed Reality Toolkit en suivant les [instructions d’installation et d’utilisation](welcome-to-mr-feature-tool.md#system-requirements) et en sélectionnant le package **Mixed Reality Toolkit Foundation**.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="f9ec7-117">Nous recommandons de suivre la section Bien démarrer de nos parcours de développement [HoloLens](unity-development-overview.md#1-getting-started) ou [VR](unity-development-wmr-overview.md#1-getting-started) proposés.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="f9ec7-118">Si vous suivez déjà le parcours de développement Unity pour HoloLens, terminez le reste des étapes de configuration ci-dessous et passez aux [tutoriels Bien démarrer avec HoloLens 2](tutorials/mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="f9ec7-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9ec7-119">Notez que les instructions d’installation ciblent la dernière combinaison stable des versions de MRTK et d’Unity, qui sont **MRTK 2.6.1** et **Unity 2019.4 LTS**.</span><span class="sxs-lookup"><span data-stu-id="f9ec7-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="f9ec7-120">Si vous ne voulez pas utiliser MRTK pour Unity, vous devrez [générer vous-même un script pour toutes les interactions et tous les comportements](configure-unity-project.md).</span><span class="sxs-lookup"><span data-stu-id="f9ec7-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f9ec7-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Bannière Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="f9ec7-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="f9ec7-122">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="f9ec7-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="f9ec7-123">Manuel</span><span class="sxs-lookup"><span data-stu-id="f9ec7-123">Manual</span></span> 

<span data-ttu-id="f9ec7-124">TBD...</span><span class="sxs-lookup"><span data-stu-id="f9ec7-124">TBD...</span></span>