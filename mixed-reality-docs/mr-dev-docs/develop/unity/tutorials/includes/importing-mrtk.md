---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176115"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="01bda-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="01bda-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="01bda-102">Une fois **MixedRealityFeatureTool** ouvert, cliquez sur **Démarrer** pour commencer à utiliser Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="01bda-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="01bda-103">La première étape consiste à faire pointer Mixed Reality Feature Tool sur votre **Chemin d’accès du projet** à l’aide du bouton représentant des **points de suspension**. Cliquez ensuite sur le bouton représentant des points de suspension à côté du chemin d’accès du projet et accédez à votre dossier de projet dans l’Explorateur. Par exemple : _D:\MixedRealityLearning\Tutoriels MRTK_.</span><span class="sxs-lookup"><span data-stu-id="01bda-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="01bda-104">Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="01bda-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="01bda-105">Cliquez ensuite sur **Découvrir les fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="01bda-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="01bda-106">La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="01bda-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="01bda-107">Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.</span><span class="sxs-lookup"><span data-stu-id="01bda-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="01bda-108">Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity.</span><span class="sxs-lookup"><span data-stu-id="01bda-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="01bda-109">Le dossier doit contenir des dossiers Ressources, Packages et Paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="01bda-110">Les fonctionnalités sont regroupées par catégorie afin de faciliter leur recherche, cliquez sur la liste déroulante **Mixed Reality Toolkit** pour rechercher les packages relatifs à Mixed Reality Toolkit et cliquez sur la liste déroulante **Prise en charge de plateformes** pour rechercher des packages associant différentes plateformes de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="01bda-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="01bda-111">Vérifiez la **Mixed Reality Toolkit Foundation** et cliquez sur la liste déroulante en regard de celle-ci afin de sélectionner **MRTK 2.7.2**, consultez également le **Plug-in Mixed Reality OpenXR 1.0.0**, puis cliquez sur la liste déroulante en regard de celui-ci pour sélectionner la version la plus récente disponible et cliquez ensuite sur le bouton **Obtenir des fonctionnalités** pour télécharger les packages sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="01bda-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="01bda-112">Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.</span><span class="sxs-lookup"><span data-stu-id="01bda-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="01bda-113">Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="01bda-114">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="01bda-114">Configuring the Unity project</span></span>

<span data-ttu-id="01bda-115">Une fois qu’Unity a fini d’importer le package à partir de la section précédente, un message d’avertissement s’affiche pour redémarrer l’éditeur Unity afin d’activer les backends pour le nouveau système de plug-in, cliquez sur **Oui**</span><span class="sxs-lookup"><span data-stu-id="01bda-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="01bda-116">Une fois qu’Unity redémarre, la fenêtre MRTK Project Configurator doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="01bda-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="01bda-117">Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer projet pour MRTK** :</span><span class="sxs-lookup"><span data-stu-id="01bda-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Ouvrir la fenêtre MRTK Project Configurator](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="01bda-119">Cliquez sur le **plug-in OpenXR Unity** pour activer la gestion des plug-ins XR et ajouter les packages requis dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="01bda-120">Ajouter un plug-in OpenXR Unity</span><span class="sxs-lookup"><span data-stu-id="01bda-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="01bda-121">Cela permet d’importer les packages Unity requis pour la Gestion de plug-in XR. Lorsque vous avez terminé, cliquez sur **Afficher les paramètres de gestion de plug-in XR** dans MRTK Project Configurator.</span><span class="sxs-lookup"><span data-stu-id="01bda-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="01bda-122">Afficher les paramètres de gestion de plug-in XR</span><span class="sxs-lookup"><span data-stu-id="01bda-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="01bda-123">La **fenêtre Paramètres du projet** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="01bda-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="01bda-124">Dans la fenêtre Paramètres du projet, sous **Gestion de plug-in XR**, vérifiez que vous êtes dans les paramètres de la plateforme Windows universelle (onglet Logo de Windows).</span><span class="sxs-lookup"><span data-stu-id="01bda-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="01bda-125">Assurez-vous également que l’option **Initialiser XR au démarrage** est cochée, puis cochez les cases **OpenXR** et **Ensemble de fonctionnalités Microsoft HoloLens** pour les activer.</span><span class="sxs-lookup"><span data-stu-id="01bda-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Activer Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="01bda-127">Une fois la case OpenXR cochée, la fenêtre MRTK Project Configurator affiche le message mis à jour avec le bouton **Appliquer les paramètres**.</span><span class="sxs-lookup"><span data-stu-id="01bda-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="01bda-128">Cliquez sur le bouton **Appliquer les paramètres**.</span><span class="sxs-lookup"><span data-stu-id="01bda-128">Click **Apply Settings** button.</span></span> 

![Fenêtre Paramètres du projet 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="01bda-130">Lorsque vous cliquez sur Appliquer les paramètres, ce message d’erreur peut s’afficher dans la console.</span><span class="sxs-lookup"><span data-stu-id="01bda-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="01bda-131">Vous pouvez poursuivre s’il s’agit de la seule erreur ou s’il n’y a aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="01bda-131">You can proceed if this is the only error or there is no error.</span></span>

![Message d’erreur de communication à distance OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="01bda-133">Pour valider la configuration d’OpenXR, cliquez sur **OpenXR** sous **Gestion de plug-in XR** et vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="01bda-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="01bda-134">Mode d’envoi en profondeur : **Profondeur de 16 bits**</span><span class="sxs-lookup"><span data-stu-id="01bda-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="01bda-135">Profils d’interaction : **Profil d’interaction manuelle Microsoft**</span><span class="sxs-lookup"><span data-stu-id="01bda-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![Fenêtre Paramètres du projet 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="01bda-137">La réduction du format de profondeur à 16 bits est facultative, mais peut contribuer à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="01bda-138">Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.</span><span class="sxs-lookup"><span data-stu-id="01bda-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="01bda-139">Dans la fenêtre **MRTK Project Configurator**, cliquez sur **Suivant**, puis cliquez sur le bouton **Appliquer** pour appliquer les paramètres.</span><span class="sxs-lookup"><span data-stu-id="01bda-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="01bda-140">(Si vous avez fermé la fenêtre, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer un projet pour MRTK**)</span><span class="sxs-lookup"><span data-stu-id="01bda-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![Fenêtre Paramètres du projet 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Fenêtre Paramètres du projet 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="01bda-143">Une fois que vous avez cliqué sur Appliquer, Unity tente de redémarrer pour que le système d’entrée prenne effet, cliquez sur **Appliquer** pour redémarrer l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="01bda-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="01bda-144">Configurer des paramètres de projet supplémentaires</span><span class="sxs-lookup"><span data-stu-id="01bda-144">Configure additional project settings</span></span>

<span data-ttu-id="01bda-145">Dans le menu Unity, sélectionnez **Edit (Modifier)** > **Project Settings (Paramètres du projet)...** pour ouvrir la fenêtre Project Settings (Paramètres du projet).</span><span class="sxs-lookup"><span data-stu-id="01bda-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="01bda-146">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="01bda-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Paramètres de publication Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="01bda-149">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="01bda-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="01bda-150">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="01bda-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="01bda-151">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="01bda-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="01bda-152">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="01bda-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="01bda-153">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="01bda-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="01bda-154">Une fois **MixedRealityFeatureTool** ouvert, cliquez sur **Démarrer** pour commencer à utiliser Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="01bda-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="01bda-155">La première étape consiste à faire pointer Mixed Reality Feature Tool sur votre **Chemin d’accès du projet** à l’aide du bouton représentant des **points de suspension**. Cliquez ensuite sur le bouton représentant des points de suspension à côté du chemin d’accès du projet et accédez à votre dossier de projet dans l’Explorateur. Par exemple : _D:\MixedRealityLearning\Tutoriels MRTK_.</span><span class="sxs-lookup"><span data-stu-id="01bda-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="01bda-156">Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="01bda-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="01bda-157">Cliquez ensuite sur **Découvrir les fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="01bda-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="01bda-158">La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="01bda-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="01bda-159">Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.</span><span class="sxs-lookup"><span data-stu-id="01bda-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="01bda-160">Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity.</span><span class="sxs-lookup"><span data-stu-id="01bda-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="01bda-161">Le dossier doit contenir des dossiers Ressources, Packages et Paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="01bda-162">Les fonctionnalités sont regroupées par catégorie pour faciliter leur recherche. Cliquez sur la liste déroulante **Mixed Reality Toolkit** pour trouver les packages qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="01bda-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="01bda-163">Cochez la case **Mixed Reality Toolkit Foundation** et cliquez sur la liste déroulante en regard de celle-ci pour sélectionner **MRTK 2.7.0**, puis cliquez sur le bouton **Obtenir des fonctionnalités** pour télécharger les packages sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="01bda-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="01bda-164">Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.</span><span class="sxs-lookup"><span data-stu-id="01bda-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="01bda-165">Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="01bda-166">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="01bda-166">Configuring the Unity project</span></span>

<span data-ttu-id="01bda-167">Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="01bda-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="01bda-168">Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer projet pour MRTK** :</span><span class="sxs-lookup"><span data-stu-id="01bda-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![ouverture de l’outil de configuration MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="01bda-170">Cliquez sur le **plug-in Unity intégré (non-OpenXR)** pour activer la gestion de plug-in XR et ajouter les packages requis dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="01bda-171">outil de configuration MRTK</span><span class="sxs-lookup"><span data-stu-id="01bda-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="01bda-172">La capture d’écran ci-dessus provient d’Unity 2020. Si vous utilisez Unity 2019, sélectionnez **Gestion XR SDK/XR**</span><span class="sxs-lookup"><span data-stu-id="01bda-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="01bda-173">Cela permet d’importer les packages Unity requis pour la gestion de plug-in XR. Une fois que vous avez terminé, cliquez sur **Afficher les paramètres** dans MRTK Project Configurator.</span><span class="sxs-lookup"><span data-stu-id="01bda-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![Fenêtre Paramètres du lecteur](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="01bda-175">La **fenêtre Paramètres du projet** s’ouvre. Dans la fenêtre Paramètres du projet sous **Gestion de plug-in XR**, assurez-vous que vous êtes dans les paramètres de la plateforme Windows universelle et que l’option **Initialiser XR au démarrage** est cochée, puis cochez la case **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="01bda-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![Fenêtre Paramètres du lecteur - Activer la réalité mixte-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="01bda-177">Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître.</span><span class="sxs-lookup"><span data-stu-id="01bda-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="01bda-178">Si ce n’est pas le cas, utilisez le menu Unity pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="01bda-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="01bda-179">Dans la fenêtre MRTK Project Configurator, cliquez sur **Suivant**, puis utilisez la liste déroulante Spatializer audio pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Appliquer** pour appliquer le paramètre :</span><span class="sxs-lookup"><span data-stu-id="01bda-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK project configurator-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="01bda-181">L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :</span><span class="sxs-lookup"><span data-stu-id="01bda-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="01bda-182">Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin.</span><span class="sxs-lookup"><span data-stu-id="01bda-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="01bda-183">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de la documentation sur les [performances](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="01bda-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="01bda-184">Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale.</span><span class="sxs-lookup"><span data-stu-id="01bda-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="01bda-185">Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.</span><span class="sxs-lookup"><span data-stu-id="01bda-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="01bda-186">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="01bda-187">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="01bda-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="01bda-188">Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.</span><span class="sxs-lookup"><span data-stu-id="01bda-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="01bda-189">Cliquez sur **Suivant**, puis sur **Terminé** dans la fenêtre MRTK Project Configurator pour terminer la configuration du projet Unity pour XRSDK.</span><span class="sxs-lookup"><span data-stu-id="01bda-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="01bda-190">Configurer des paramètres de projet supplémentaires</span><span class="sxs-lookup"><span data-stu-id="01bda-190">Configure additional project settings</span></span>

<span data-ttu-id="01bda-191">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="01bda-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="01bda-192">Dans la fenêtre Paramètres du projet, sélectionnez **Gestion de plug-in XR** > **Windows Mixed Reality** > **Paramètres du runtime**, puis utilisez la liste déroulante **Format de mémoire tampon de profondeur** pour sélectionner **16 bits de profondeur** :</span><span class="sxs-lookup"><span data-stu-id="01bda-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Unity - 16 Depth activé](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="01bda-194">La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="01bda-195">Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.</span><span class="sxs-lookup"><span data-stu-id="01bda-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="01bda-196">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="01bda-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Paramètres de publication Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="01bda-199">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="01bda-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="01bda-200">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="01bda-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="01bda-201">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="01bda-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="01bda-202">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="01bda-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="01bda-203">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="01bda-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="01bda-204">Une fois **MixedRealityFeatureTool** ouvert, cliquez sur **Démarrer** pour commencer à utiliser Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="01bda-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="01bda-205">La première étape consiste à faire pointer Mixed Reality Feature Tool sur votre **Chemin d’accès du projet** à l’aide du bouton représentant des **points de suspension**. Cliquez ensuite sur le bouton représentant des points de suspension à côté du chemin d’accès du projet et accédez à votre dossier de projet dans l’Explorateur. Par exemple : _D:\MixedRealityLearning\Tutoriels MRTK_.</span><span class="sxs-lookup"><span data-stu-id="01bda-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="01bda-206">Une fois le dossier de votre projet localisé, cliquez sur le bouton Ouvrir pour revenir à Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="01bda-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="01bda-207">Cliquez ensuite sur **Découvrir les fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="01bda-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="01bda-208">La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="01bda-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="01bda-209">Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.</span><span class="sxs-lookup"><span data-stu-id="01bda-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="01bda-210">Mixed Reality Feature Tool effectue la validation pour s’assurer qu’il a été dirigé vers un dossier de projet Unity.</span><span class="sxs-lookup"><span data-stu-id="01bda-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="01bda-211">Le dossier doit contenir des dossiers Ressources, Packages et Paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="01bda-212">Les fonctionnalités sont regroupées par catégorie pour faciliter leur recherche. Cliquez sur la liste déroulante **Mixed Reality Toolkit** pour trouver les packages qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="01bda-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="01bda-213">Cochez la case **Mixed Reality Toolkit Foundation** et cliquez sur la liste déroulante en regard de celle-ci pour sélectionner **MRTK 2.7.0**, puis cliquez sur le bouton **Obtenir des fonctionnalités** pour télécharger les packages sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="01bda-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="01bda-214">Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.</span><span class="sxs-lookup"><span data-stu-id="01bda-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="01bda-215">Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="01bda-216">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="01bda-216">Configuring the Unity project</span></span>

<span data-ttu-id="01bda-217">Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="01bda-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="01bda-218">Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement en accédant à **Mixed Reality** > **Toolkit** > **Utilitaires** > **Configurer projet pour MRTK** :</span><span class="sxs-lookup"><span data-stu-id="01bda-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Chemin du menu Configure Unity Project d’Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="01bda-220">Cliquez sur **XR antérieur** pour activer XR antérieur et ajouter les packages requis dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="01bda-222">Cliquez sur le bouton Suivant pour activer les paramètres de pipeline XR pour XR antérieur.</span><span class="sxs-lookup"><span data-stu-id="01bda-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Fenêtre Configuration de MRTK Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="01bda-224">Dans la fenêtre MRTK Project Configurator, assurez-vous que toutes les options sont cochées et utilisez également la liste déroulante **Spatializer audio** pour sélectionner le **Spatializer MS HRTF**, puis cliquez sur le bouton **Appliquer** pour appliquer le paramètre :</span><span class="sxs-lookup"><span data-stu-id="01bda-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Fenêtre de configuration de MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="01bda-226">L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :</span><span class="sxs-lookup"><span data-stu-id="01bda-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="01bda-227">Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin.</span><span class="sxs-lookup"><span data-stu-id="01bda-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="01bda-228">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de la documentation sur les [performances](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="01bda-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="01bda-229">Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale.</span><span class="sxs-lookup"><span data-stu-id="01bda-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="01bda-230">Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.</span><span class="sxs-lookup"><span data-stu-id="01bda-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="01bda-231">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="01bda-232">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="01bda-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="01bda-233">Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.</span><span class="sxs-lookup"><span data-stu-id="01bda-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="01bda-234">Cliquez sur **Suivant**, puis sur le bouton **Terminé** dans la fenêtre MRTK Project Configurator pour terminer la configuration du projet Unity pour XR antérieur.</span><span class="sxs-lookup"><span data-stu-id="01bda-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="01bda-235">Configurer des paramètres de projet supplémentaires</span><span class="sxs-lookup"><span data-stu-id="01bda-235">Configure additional project settings</span></span>

<span data-ttu-id="01bda-236">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="01bda-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="01bda-237">Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, puis utilisez la liste déroulante **Depth Format** pour sélectionner **16-bit depth** :</span><span class="sxs-lookup"><span data-stu-id="01bda-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity - 16 Depth activé](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="01bda-239">La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="01bda-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="01bda-240">Pour plus d’informations à ce sujet, reportez-vous à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Partage de mémoire tampon de profondeur (HoloLens)</a> de la documentation sur les performances de MRTK.</span><span class="sxs-lookup"><span data-stu-id="01bda-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="01bda-241">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="01bda-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Paramètres de publication Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="01bda-244">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="01bda-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="01bda-245">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="01bda-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="01bda-246">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="01bda-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="01bda-247">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="01bda-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
