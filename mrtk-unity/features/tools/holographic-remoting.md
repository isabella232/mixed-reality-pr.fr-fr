---
title: Communication à distance holographique
description: Documentation sur la communication à distance holographique MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176640"
---
# <a name="holographic-remoting"></a><span data-ttu-id="b0ff5-104">Communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="b0ff5-104">Holographic remoting</span></span>

<span data-ttu-id="b0ff5-105">la communication à distance holographique diffuse du contenu holographique depuis un PC vers votre Microsoft HoloLens en temps réel, à l’aide d’une connexion Wi-Fi ou d’un câble USB.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="b0ff5-106">Cette fonctionnalité peut augmenter considérablement la productivité des développeurs lors du développement d’applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="b0ff5-107">Le kit de développement logiciel (SDK) XR, comme indiqué ci-dessous, fait référence au [nouveau pipeline XR unity 2019,3 et au-delà](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="b0ff5-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="b0ff5-108">Pour plus d’informations sur l’utilisation du kit de développement logiciel (SDK) XR avec MRTK, consultez [cette page](../../configuration/getting-started-with-mrtk-and-xrsdk.md) .</span><span class="sxs-lookup"><span data-stu-id="b0ff5-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="b0ff5-109">Le XR hérité fait référence au pipeline XR existant qui est inclus dans Unity 2018, déconseillé dans Unity 2019,3 et supprimé dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="b0ff5-110">Configuration initiale</span><span class="sxs-lookup"><span data-stu-id="b0ff5-110">Initial setup</span></span>

<span data-ttu-id="b0ff5-111">pour activer la communication à distance à un HoloLens, il est important de s’assurer que le projet utilise les derniers composants de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="b0ff5-112">ouvrez la **fenêtre > Gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="b0ff5-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="b0ff5-113">si vous utilisez des XR hérités : vérifiez que la dernière version du package de **Windows Mixed Reality** est installée.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="b0ff5-114">si vous utilisez le kit de développement logiciel (SDK) XR : vérifiez que la dernière version du package de **plug-in Windows XR** est installée.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="b0ff5-115">vérifiez que la dernière application de communication à distance holographique est installée, sur le HoloLens, via le Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="b0ff5-116">Reportez-vous aux [instructions de configuration de XR héritées](#legacy-xr-setup-instructions) ou aux [instructions d’installation du kit de développement logiciel (SDK) XR](#xr-sdk-setup-instructions) en fonction du pipeline utilisé dans le projet.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="b0ff5-117">Instructions d’installation de XR héritées</span><span class="sxs-lookup"><span data-stu-id="b0ff5-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="b0ff5-118">Les instructions ci-dessous s’appliquent uniquement à la communication à distance avec HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="b0ff5-119">si vous effectuez uniquement la communication à distance avec HoloLens (1re génération), passez à [la connexion au HoloLens avec Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span><span class="sxs-lookup"><span data-stu-id="b0ff5-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="b0ff5-120">lors de l’utilisation d’un HoloLens 2, la prise en charge de la main et des données de suivi oculaire à distance a été ajoutée à MRTK.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="b0ff5-121">Pour activer ces fonctionnalités, suivez les étapes décrites dans [importer des DotNetWinRT dans le projet](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="b0ff5-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="b0ff5-122">une fois importé, l’étape suivante consiste à sélectionner la **réalité mixte**  >  **Shared Computer Toolkit**  >  **utilitaires**  >  **Windows Mixed Reality**  >  **vérifier la Configuration**.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="b0ff5-123">Cette étape ajoute une définition de script qui active la dépendance DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="b0ff5-124">Si vous utilisez Unity 2019,4 et versions ultérieures, il n’est pas nécessaire d’exécuter l’utilitaire de vérification de la configuration.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="b0ff5-125">pour activer le suivi des jointures manuelles et du suivi oculaire, suivez les étapes décrites dans le **débogage HoloLens 2 la communication à distance via l’importation de packages unity** et les sections associées.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="b0ff5-126">débogage HoloLens 2 la communication à distance via l’importation de package unity</span><span class="sxs-lookup"><span data-stu-id="b0ff5-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="b0ff5-127">si HoloLens 2 jointures manuelles et le suivi oculaire ne fonctionnent pas sur la communication à distance, il existe quelques points courants de problèmes potentiels.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="b0ff5-128">Ils sont listés ci-dessous dans l’ordre dans lequel ils doivent être vérifiés.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="b0ff5-129">Ces problèmes sont particulièrement pertinents lors de l’exécution sur **unity 2019,3** ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="b0ff5-130">Importer DotNetWinRT dans le projet</span><span class="sxs-lookup"><span data-stu-id="b0ff5-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="b0ff5-131">Télécharger l' [outil de la fonctionnalité de réalité mixte](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="b0ff5-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="b0ff5-132">Dans la vue **découvrir les fonctionnalités** , sélectionnez *projections WinRT de réalité mixte*</span><span class="sxs-lookup"><span data-stu-id="b0ff5-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Sélectionner le package DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="b0ff5-134">Cliquez sur **recevoir des fonctionnalités** et continuer à [importer le package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="b0ff5-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="b0ff5-135">DOTNETWINRT_PRESENT définir les paramètres écrits dans le lecteur</span><span class="sxs-lookup"><span data-stu-id="b0ff5-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="b0ff5-136">si vous utilisez unity 2019,4 et versions ultérieures, la DOTNETWINRT_PRESENT définir est contenue dans les fichiers. asmdef appropriés et non dans le Paramètres de lecteur unity.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="b0ff5-137">L’étape de configuration de la vérification n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="b0ff5-138">À partir de MRTK version 2.5.0, pour des raisons de performances, cette #define n’est plus définie automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="b0ff5-139">pour activer cet indicateur, utilisez l’élément de menu vérifier la **réalité mixte Shared Computer Toolkit**  >  **utilitaires**  >  **Windows Mixed Reality**  >  **vérifier la Configuration** .</span><span class="sxs-lookup"><span data-stu-id="b0ff5-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="b0ff5-140">L’élément vérifier la configuration n’affiche pas de confirmation.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="b0ff5-141">pour confirmer que la définition a été définie, accédez au Paramètres du lecteur unity.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="b0ff5-142">à partir de là, sous l’onglet UWP, cochez autres Paramètres pour les symboles de définition de script.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="b0ff5-143">Assurez-vous que DOTNETWINRT_PRESENT est correctement écrit dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="b0ff5-144">Si c’est le cas, cette étape a réussi.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT présente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="b0ff5-146">suppression de la prise en charge de la communication à distance spécifique à HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b0ff5-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="b0ff5-147">Si vous rencontrez des conflits ou d’autres problèmes en raison de la présence de l’adaptateur DotNetWinRT, veuillez [contacter l’une de nos ressources d’aide](../../index.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="b0ff5-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="b0ff5-148">Instructions d’installation du kit SDK XR</span><span class="sxs-lookup"><span data-stu-id="b0ff5-148">XR SDK setup instructions</span></span>

<span data-ttu-id="b0ff5-149">suivez les [instructions d’installation de Windows Mixed Reality sur la page prise en main du kit de développement logiciel (SDK) MRTK et XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) et assurez-vous d’effectuer l’étape requise dans le cadre de l’éditeur HoloLens la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="b0ff5-150">connexion au HoloLens avec Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="b0ff5-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="b0ff5-151">Une fois que le projet a été configuré, une connexion peut être établie avec l’HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="b0ff5-152">dans **fichier > build Paramètres**, vérifiez que le type de génération du projet est défini sur **plateforme Windows universelle**</span><span class="sxs-lookup"><span data-stu-id="b0ff5-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="b0ff5-153">sur la HoloLens, lancez l’application de **communication à distance holographique** .</span><span class="sxs-lookup"><span data-stu-id="b0ff5-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="b0ff5-154">dans unity, sélectionnez **windows > XR > émulation holographique (si vous utilisez le kit de développement logiciel (SDK) XR hérité XR)/Windows la communication à distance du plug-in (si vous utilisez XR SDK)**.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Démarrer l’émulation holographique](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="b0ff5-156">Définissez le **mode d’émulation** à **distant sur appareil**.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Définir le mode d’émulation](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="b0ff5-158">(**_S’applique uniquement aux XR hérités_**) Sélectionnez la **version** de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Sélectionner la version de l’appareil](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="b0ff5-160">À l’aide de l’adresse IP affichée par l’application de lecteur de communication à distance holographique, définissez le champ **ordinateur distant** .</span><span class="sxs-lookup"><span data-stu-id="b0ff5-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Entrer l’adresse IP](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="b0ff5-162">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="b0ff5-163">si vous ne pouvez pas vous connecter, assurez-vous que votre HoloLens 2 n’est pas branché sur votre ordinateur et redémarrez unity.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="b0ff5-164">connexion au HoloLens à l’aide d’un câble USB</span><span class="sxs-lookup"><span data-stu-id="b0ff5-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="b0ff5-165">La connexion par câble USB offre une meilleure qualité de rendu et une meilleure stabilité.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="b0ff5-166">pour utiliser la connexion par câble USB, déconnectez-vous du HoloLens de Wi-Fi dans le Paramètres de HoloLens et lancez l’application de lecteur de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="b0ff5-167">Elle affiche une adresse IP commençant par 169.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="b0ff5-168">Utilisez cette adresse IP dans le paramètre d’émulation holographique d’Unity pour vous connecter.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="b0ff5-169">une fois que l’adresse IP pour le câble USB a été identifiée, il est possible de connecter à nouveau le HoloLens à Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="b0ff5-170">Démarrage d’une session de communication à distance</span><span class="sxs-lookup"><span data-stu-id="b0ff5-170">Starting a remoting session</span></span>

<span data-ttu-id="b0ff5-171">avec unity connectée au HoloLens, entrez en mode lecture dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="b0ff5-172">Une fois la session terminée, quittez le mode lecture.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="b0ff5-173">Il existe un problème connu avec certaines versions de Unity dans laquelle l’éditeur peut se bloquer lors de l’entrée en mode lecture pendant une session de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="b0ff5-174">Ce problème peut se manifester si la fenêtre holographique est ouverte lorsque le projet est chargé.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="b0ff5-175">Pour vous assurer que ce problème ne se produit pas, fermez toujours la boîte de dialogue holographique avant de quitter Unity.</span><span class="sxs-lookup"><span data-stu-id="b0ff5-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0ff5-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0ff5-176">See also</span></span>

- [<span data-ttu-id="b0ff5-177">Résolution des problèmes et limitations de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="b0ff5-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="b0ff5-178">Termes du contrat de licence logiciel Microsoft holographique Remoting</span><span class="sxs-lookup"><span data-stu-id="b0ff5-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
