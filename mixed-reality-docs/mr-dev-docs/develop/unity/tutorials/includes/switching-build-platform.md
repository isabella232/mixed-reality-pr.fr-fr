---
ms.openlocfilehash: d7232ca645c2a8cfb2508b090fdb7ae02c2ab010
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984251"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="09441-101">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="09441-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="09441-102">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="09441-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity - Build Settings... Chemin du menu](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="09441-104">Dans la fenêtre Paramètres de build, sélectionnez **Plateforme Windows universelle** , puis cliquez sur le bouton **Switch Platform** (Changer de plateforme) :</span><span class="sxs-lookup"><span data-stu-id="09441-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Fenêtre Build Setting d’Unity avec UWP sélectionné comme nouvelle plateforme, qui était auparavant Standalone](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="09441-106">Attendez qu’Unity termine le changement de plateforme :</span><span class="sxs-lookup"><span data-stu-id="09441-106">Wait for Unity to finish switching the platform:</span></span>

![Unity - Changement de plateforme en cours](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="09441-108">Quand Unity a terminé le changement de plateforme, cliquez sur l’icône **x** rouge pour fermer la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="09441-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Fenêtre Build d’Unity avec l’icône Fermer mise en évidence](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="09441-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="09441-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="09441-111">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="09441-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity - Build Settings... Chemin du menu](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="09441-113">Dans la fenêtre Build Settings, sélectionnez **Universal Windows Platform**, puis :</span><span class="sxs-lookup"><span data-stu-id="09441-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="09441-114">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="09441-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="09441-115">Définissez **Architecture** sur **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="09441-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="09441-116">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="09441-116">Set **Build Type** to **D3D Project**</span></span>
4.  <span data-ttu-id="09441-117">Définissez **Target SDK Version** sur **Latest Installed**</span><span class="sxs-lookup"><span data-stu-id="09441-117">Set **Target SDK Version** to **Latest Installed**</span></span>
5.  <span data-ttu-id="09441-118">Définissez **Minimum Platform Version** sur **10.0.18362**.</span><span class="sxs-lookup"><span data-stu-id="09441-118">Set **Minimum Platform Version** to **10.0.18362**</span></span>
6.  <span data-ttu-id="09441-119">Définissez **Visual Studio Version** sur **Latest Installed**</span><span class="sxs-lookup"><span data-stu-id="09441-119">Set **Visual Studio Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="09441-120">Définissez **Build and Run on** sur **USB Device**</span><span class="sxs-lookup"><span data-stu-id="09441-120">Set **Build and Run on** to **USB Device**</span></span>
8.  <span data-ttu-id="09441-121">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="09441-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9.  <span data-ttu-id="09441-122">Appuyer sur le bouton Switch Platform</span><span class="sxs-lookup"><span data-stu-id="09441-122">Click the Switch Platform button</span></span>


![Paramètres de build Unity avec les paramètres Universal Windows Platform définis](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="09441-124">Quand Unity a terminé le changement de plateforme, cliquez sur l’icône **x** rouge pour fermer la fenêtre Build Settings.</span><span class="sxs-lookup"><span data-stu-id="09441-124">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="09441-125">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="09441-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="09441-126">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="09441-126">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity - Build Settings... Chemin du menu](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="09441-128">Dans la fenêtre Paramètres de build, sélectionnez **Plateforme Windows universelle** , puis cliquez sur le bouton **Switch Platform** (Changer de plateforme) :</span><span class="sxs-lookup"><span data-stu-id="09441-128">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Fenêtre Build Setting d’Unity avec UWP sélectionné comme nouvelle plateforme, qui était auparavant Standalone](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="09441-130">Attendez qu’Unity termine le changement de plateforme :</span><span class="sxs-lookup"><span data-stu-id="09441-130">Wait for Unity to finish switching the platform:</span></span>

![Unity - Changement de plateforme en cours](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="09441-132">Quand Unity a terminé le changement de plateforme, cliquez sur l’icône **x** rouge pour fermer la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="09441-132">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Fenêtre Build d’Unity avec l’icône Fermer mise en évidence](../images/mr-learning-base/base-02-section2-step1-4.png)
