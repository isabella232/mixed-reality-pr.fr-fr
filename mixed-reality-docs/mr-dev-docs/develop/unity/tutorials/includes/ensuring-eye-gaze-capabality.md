---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097796"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8dae6-101">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="8dae6-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="8dae6-102">Activation de la fonctionnalité d’entrée par pointage du regard et ajout du fournisseur de données de pointage du regard</span><span class="sxs-lookup"><span data-stu-id="8dae6-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="8dae6-103">Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Eye Gaze Input Capability** est grisée :</span><span class="sxs-lookup"><span data-stu-id="8dae6-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Fenêtre MRTK Project Configurator d’Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8dae6-105">La fonctionnalité Gaze Input doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="8dae6-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="8dae6-106">Toutefois, si elle n’est pas activée, activez-la maintenant.</span><span class="sxs-lookup"><span data-stu-id="8dae6-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="8dae6-107">Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :</span><span class="sxs-lookup"><span data-stu-id="8dae6-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="8dae6-108">Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="8dae6-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Ajout du fournisseur de données de pointage du regard 1](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="8dae6-110">Affectez **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** au champ **Type** du nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="8dae6-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Ajout du fournisseur de données de pointage du regard 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8dae6-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8dae6-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="8dae6-113">Activation de la fonctionnalité d’entrée par pointage du regard et ajout du fournisseur de données de pointage du regard</span><span class="sxs-lookup"><span data-stu-id="8dae6-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="8dae6-114">Dans la fenêtre Hierarchy, sélectionnez l’objet MixedRealityToolkit. Ensuite, dans la fenêtre Inspector, accédez à l’onglet Input :</span><span class="sxs-lookup"><span data-stu-id="8dae6-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="8dae6-115">Développez **Input Data Providers**, puis cliquez sur le bouton **+ Add Data Provider** pour ajouter un nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="8dae6-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Ajout du fournisseur de données de pointage du regard 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="8dae6-117">Affectez **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** au champ **Type** du nouveau fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="8dae6-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Ajout du fournisseur de données de pointage du regard 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="8dae6-119">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="8dae6-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="8dae6-120">Vérifier que la fonctionnalité d’entrée avec le pointage du regard est activée</span><span class="sxs-lookup"><span data-stu-id="8dae6-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="8dae6-121">Dans le menu Unity, sélectionnez Mixed Reality Toolkit > Utilities > **Configure Unity Project** pour ouvrir la fenêtre **MRTK Project Configurator** puis, dans la section **UWP Capabilities**, vérifiez que l’option **Enable Eye Gaze Input Capability** est grisée :</span><span class="sxs-lookup"><span data-stu-id="8dae6-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Fenêtre MRTK Project Configurator d’Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8dae6-123">La fonctionnalité Gaze Input doit avoir été activée lors des instructions [Appliquer les paramètres de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) lorsque vous avez configuré le projet Unity au début de cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="8dae6-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="8dae6-124">Toutefois, si elle n’est pas activée, activez-la maintenant.</span><span class="sxs-lookup"><span data-stu-id="8dae6-124">However, if it is not enabled, make sure you enable it now.</span></span>
