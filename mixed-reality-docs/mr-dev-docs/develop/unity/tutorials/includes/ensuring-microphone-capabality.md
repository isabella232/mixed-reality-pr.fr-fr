---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097413"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="b4b22-101">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="b4b22-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="b4b22-102">Activation de la fonctionnalité Microphone et ajout d’un fournisseur de données de saisie vocale</span><span class="sxs-lookup"><span data-stu-id="b4b22-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="b4b22-103">Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Microphone Capability** est grisée :</span><span class="sxs-lookup"><span data-stu-id="b4b22-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Activer la fonctionnalité du microphone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b4b22-105">La fonctionnalité Microphone doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="b4b22-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="b4b22-106">Toutefois, si elle n’est pas activée, veillez à l’activer maintenant.</span><span class="sxs-lookup"><span data-stu-id="b4b22-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="b4b22-107">Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :</span><span class="sxs-lookup"><span data-stu-id="b4b22-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="b4b22-108">Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="b4b22-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Fournisseur de données pour l’ajout de nouvelles commandes vocales](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="b4b22-110">Affectez **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** au champ **Type** du nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="b4b22-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Ajout de paramètres pour les nouvelles commandes vocales](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="b4b22-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="b4b22-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="b4b22-113">Activation de la fonctionnalité Microphone et ajout d’un fournisseur de données de saisie vocale</span><span class="sxs-lookup"><span data-stu-id="b4b22-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="b4b22-114">Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Microphone Capability** est grisée :</span><span class="sxs-lookup"><span data-stu-id="b4b22-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Activer la fonctionnalité du microphone pour OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b4b22-116">La fonctionnalité Microphone doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="b4b22-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="b4b22-117">Toutefois, si elle n’est pas activée, veillez à l’activer maintenant.</span><span class="sxs-lookup"><span data-stu-id="b4b22-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="b4b22-118">Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :</span><span class="sxs-lookup"><span data-stu-id="b4b22-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="b4b22-119">Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="b4b22-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Ajout de nouvelles commandes vocales pour OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="b4b22-121">Affectez **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** au champ **Type** du nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="b4b22-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Ajout des paramètres des nouvelles commandes vocales pour OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="b4b22-123">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="b4b22-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="b4b22-124">Vérification de l’activation de la fonctionnalité Microphone</span><span class="sxs-lookup"><span data-stu-id="b4b22-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="b4b22-125">Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Microphone Capability** est grisée :</span><span class="sxs-lookup"><span data-stu-id="b4b22-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Activer la fonctionnalité du microphone](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b4b22-127">La fonctionnalité Microphone doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="b4b22-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="b4b22-128">Toutefois, si elle n’est pas activée, veillez à l’activer maintenant.</span><span class="sxs-lookup"><span data-stu-id="b4b22-128">However, if it is not enabled, make sure you enable it now.</span></span>
