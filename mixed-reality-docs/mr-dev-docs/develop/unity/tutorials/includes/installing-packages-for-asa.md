---
ms.openlocfilehash: 0a89ef77bee7eff83d4599c46ffd2681c99b2165
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175573"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="b2077-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="b2077-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="b2077-102">Dans le menu Unity, sélectionnez Gestionnaire de package **Windows** >  pour ouvrir la fenêtre **Gestionnaire de package**, puis vérifiez que la version 4.1.7 d’**AR Foundation** >  est installée **.**</span><span class="sxs-lookup"><span data-stu-id="b2077-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![Package Manager d’Unity avec AR Foundation sélectionné](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b2077-104">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="b2077-104">Importing the tutorial assets</span></span>

<span data-ttu-id="b2077-105">Ajoutez le SDK AzurespatialAnchors V2.10 à votre projet. Pour ajouter les packages, suivez ce [tutoriel](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="b2077-105">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="b2077-106">Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés** :</span><span class="sxs-lookup"><span data-stu-id="b2077-106">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="b2077-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2077-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="b2077-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2077-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="b2077-109">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="b2077-109">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](../images/mr-learning-asa/asa-02-section3-step1-2-OpenXR.png)

> [!TIP]
> <span data-ttu-id="b2077-111">Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans  [Importation des ressources du tutoriel](../mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="b2077-111">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="b2077-112">Unity 2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="b2077-112">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="b2077-113">Dans le menu Unity, sélectionnez **Windows** > **Package Manager** pour ouvrir la fenêtre Package Manager, sélectionnez une version d’**AR Foundation ultérieure à la version 4.0.12**, puis cliquez sur le bouton **Install** pour installer le package :</span><span class="sxs-lookup"><span data-stu-id="b2077-113">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![Package Manager d’Unity avec AR Foundation sélectionné](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b2077-115">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="b2077-115">Importing the tutorial assets</span></span>

<span data-ttu-id="b2077-116">Ajoutez le SDK AzurespatialAnchors V2.10 à votre projet. Pour ajouter les packages, suivez ce [tutoriel](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="b2077-116">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="b2077-117">Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés** :</span><span class="sxs-lookup"><span data-stu-id="b2077-117">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="b2077-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2077-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="b2077-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2077-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="b2077-120">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="b2077-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](../images/mr-learning-asa/asa-02-section3-step1-2-XRSDK.PNG)

> [!TIP]
> <span data-ttu-id="b2077-122">Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans  [Importation des ressources du tutoriel](../mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="b2077-122">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="b2077-123">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="b2077-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="b2077-124">Dans le menu Unity, sélectionnez **Windows** > **Package Manager** pour ouvrir la fenêtre Package Manager, sélectionnez une version d’**AR Foundation ultérieure à la version 3.1.3**, puis cliquez sur le bouton **Install** pour installer le package :</span><span class="sxs-lookup"><span data-stu-id="b2077-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![Package Manager d’Unity avec AR Foundation sélectionné](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b2077-126">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="b2077-126">Importing the tutorial assets</span></span>

<span data-ttu-id="b2077-127">Ajoutez le SDK AzurespatialAnchors V2.7.2 à votre projet. Pour ajouter les packages, suivez ce [tutoriel](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="b2077-127">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="b2077-128">Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés** :</span><span class="sxs-lookup"><span data-stu-id="b2077-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="b2077-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2077-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="b2077-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2077-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage)

<span data-ttu-id="b2077-131">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="b2077-131">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](../images/mr-learning-asa/asa-02-section3-step1-2-Legacy.png)

> [!NOTE]
> <span data-ttu-id="b2077-133">Si vous voyez des avertissements CS0618 signalant que « WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) » est obsolète, vous pouvez les ignorer.</span><span class="sxs-lookup"><span data-stu-id="b2077-133">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="b2077-134">Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans  [Importation des ressources du tutoriel](../mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="b2077-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>
