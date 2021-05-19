---
title: Communication à distance holographique
description: Documentation sur la communication à distance holographique MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144586"
---
# <a name="holographic-remoting"></a><span data-ttu-id="cfc57-104">Communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="cfc57-104">Holographic Remoting</span></span>

<span data-ttu-id="cfc57-105">La communication à distance holographique diffuse du contenu holographique depuis un PC vers votre Microsoft HoloLens en temps réel, à l’aide d’un Wi-Fi ou d’une connexion par câble USB.</span><span class="sxs-lookup"><span data-stu-id="cfc57-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="cfc57-106">Cette fonctionnalité peut augmenter considérablement la productivité des développeurs lors du développement d’applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="cfc57-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="cfc57-107">Le kit de développement logiciel (SDK) XR, comme indiqué ci-dessous, fait référence au [nouveau pipeline XR unity 2019,3 et au-delà](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="cfc57-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="cfc57-108">Pour plus d’informations sur l’utilisation du kit de développement logiciel (SDK) XR avec MRTK, consultez [cette page](../../configuration/getting-started-with-mrtk-and-xrsdk.md) .</span><span class="sxs-lookup"><span data-stu-id="cfc57-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="cfc57-109">Le XR hérité fait référence au pipeline XR existant qui est inclus dans Unity 2018, déconseillé dans Unity 2019,3 et supprimé dans Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="cfc57-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="cfc57-110">Configuration initiale</span><span class="sxs-lookup"><span data-stu-id="cfc57-110">Initial setup</span></span>

<span data-ttu-id="cfc57-111">Pour activer la communication à distance à un HoloLens, il est important de s’assurer que le projet utilise les derniers composants de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="cfc57-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="cfc57-112">Ouvrir la **fenêtre > le gestionnaire de package**</span><span class="sxs-lookup"><span data-stu-id="cfc57-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="cfc57-113">Si vous utilisez des XR hérités : Vérifiez que la dernière version du package **Windows Mixed Reality** est installée.</span><span class="sxs-lookup"><span data-stu-id="cfc57-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="cfc57-114">Si vous utilisez le kit de développement logiciel (SDK) XR : Vérifiez que la dernière version du package de **plug-in XR Windows** est installée.</span><span class="sxs-lookup"><span data-stu-id="cfc57-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="cfc57-115">Vérifiez que la dernière application de communication à distance holographique est installée, sur le HoloLens, via le Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="cfc57-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="cfc57-116">Reportez-vous aux [instructions de configuration de XR héritées](#legacy-xr-setup-instructions) ou aux [instructions d’installation du kit de développement logiciel (SDK) XR](#xr-sdk-setup-instructions) en fonction du pipeline utilisé dans le projet.</span><span class="sxs-lookup"><span data-stu-id="cfc57-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="cfc57-117">Instructions d’installation de XR héritées</span><span class="sxs-lookup"><span data-stu-id="cfc57-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="cfc57-118">Les instructions ci-dessous s’appliquent uniquement à la communication à distance avec HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cfc57-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="cfc57-119">Si vous effectuez uniquement la communication à distance avec HoloLens (1re génération), passez à [la connexion à hololens avec Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span><span class="sxs-lookup"><span data-stu-id="cfc57-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="cfc57-120">Lors de l’utilisation d’un HoloLens 2, la prise en charge de la main et des données de suivi oculaire à distance a été ajoutée à MRTK.</span><span class="sxs-lookup"><span data-stu-id="cfc57-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="cfc57-121">Pour activer ces fonctionnalités, suivez les étapes décrites dans [importer des DotNetWinRT dans le projet](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="cfc57-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="cfc57-122">Une fois l’importation effectuée, l’étape suivante consiste à sélectionner la configuration de la vérification de la  >    >  **réalité mixte Windows Mixed Reality** Toolkit  >  .</span><span class="sxs-lookup"><span data-stu-id="cfc57-122">Once imported, the next step is to select **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="cfc57-123">Cette étape ajoute une définition de script qui active la dépendance DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="cfc57-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="cfc57-124">Si vous utilisez Unity 2019,4 et versions ultérieures, il n’est pas nécessaire d’exécuter l’utilitaire de vérification de la configuration.</span><span class="sxs-lookup"><span data-stu-id="cfc57-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="cfc57-125">Pour activer le suivi des articulations et du suivi oculaire, suivez les étapes décrites dans le **débogage de l’accès distant HoloLens 2 via l’importation de package Unity** et les sections associées.</span><span class="sxs-lookup"><span data-stu-id="cfc57-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="cfc57-126">Débogage de l’accès distant HoloLens 2 via l’importation de package Unity</span><span class="sxs-lookup"><span data-stu-id="cfc57-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="cfc57-127">Si les jonctions de la main et le suivi oculaire de HoloLens 2 ne fonctionnent pas sur la communication à distance, il existe quelques points courants de problèmes potentiels.</span><span class="sxs-lookup"><span data-stu-id="cfc57-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="cfc57-128">Ils sont listés ci-dessous dans l’ordre dans lequel ils doivent être vérifiés.</span><span class="sxs-lookup"><span data-stu-id="cfc57-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="cfc57-129">Ces problèmes sont particulièrement pertinents lors de l’exécution sur **unity 2019,3** ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cfc57-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="cfc57-130">Importer DotNetWinRT dans le projet</span><span class="sxs-lookup"><span data-stu-id="cfc57-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="cfc57-131">Télécharger l' [outil de la fonctionnalité de réalité mixte](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="cfc57-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="cfc57-132">Dans la vue **découvrir les fonctionnalités** , sélectionnez *projections WinRT de réalité mixte*</span><span class="sxs-lookup"><span data-stu-id="cfc57-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Sélectionner le package DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="cfc57-134">Cliquez sur **recevoir des fonctionnalités** et continuer à [importer le package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="cfc57-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="cfc57-135">DOTNETWINRT_PRESENT définir les paramètres écrits dans le lecteur</span><span class="sxs-lookup"><span data-stu-id="cfc57-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="cfc57-136">Si vous utilisez Unity 2019,4 et versions ultérieures, la DOTNETWINRT_PRESENT définir est contenue dans les fichiers. asmdef appropriés et non dans les paramètres du lecteur Unity.</span><span class="sxs-lookup"><span data-stu-id="cfc57-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="cfc57-137">L’étape de configuration de la vérification n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cfc57-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="cfc57-138">À partir de MRTK version 2.5.0, pour des raisons de performances, cette #define n’est plus définie automatiquement.</span><span class="sxs-lookup"><span data-stu-id="cfc57-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="cfc57-139">Pour activer cet indicateur, utilisez l'   >    >    >  élément de menu **Vérifier la configuration** de la vérification de la réalité mixte de la réalité des outils de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="cfc57-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="cfc57-140">L’élément vérifier la configuration n’affiche pas de confirmation.</span><span class="sxs-lookup"><span data-stu-id="cfc57-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="cfc57-141">Pour confirmer que la définition a été définie, accédez aux paramètres du lecteur Unity.</span><span class="sxs-lookup"><span data-stu-id="cfc57-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="cfc57-142">À partir de là, sous l’onglet UWP, activez la case à cocher autres paramètres pour les symboles de définition de script.</span><span class="sxs-lookup"><span data-stu-id="cfc57-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="cfc57-143">Assurez-vous que DOTNETWINRT_PRESENT est correctement écrit dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="cfc57-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="cfc57-144">Si c’est le cas, cette étape a réussi.</span><span class="sxs-lookup"><span data-stu-id="cfc57-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT présente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="cfc57-146">Suppression de la prise en charge de l’accès distant spécifique à HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cfc57-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="cfc57-147">Si vous rencontrez des conflits ou d’autres problèmes en raison de la présence de l’adaptateur DotNetWinRT, veuillez [contacter l’une de nos ressources d’aide](../../index.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="cfc57-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="cfc57-148">Instructions d’installation du kit SDK XR</span><span class="sxs-lookup"><span data-stu-id="cfc57-148">XR SDK setup instructions</span></span>

<span data-ttu-id="cfc57-149">Suivez les [instructions d’installation de Windows Mixed Reality sur la page prise en main de MRTK et du kit de développement logiciel (SDK) XR](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) et assurez-vous d’effectuer l’étape requise pour la communication à distance HoloLens dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="cfc57-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="cfc57-150">Connexion au HoloLens avec Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="cfc57-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="cfc57-151">Une fois que le projet a été configuré, une connexion peut être établie avec HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfc57-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="cfc57-152">Dans **fichier > paramètres de build**, assurez-vous que le type de génération du projet est défini sur **plateforme Windows universelle**</span><span class="sxs-lookup"><span data-stu-id="cfc57-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="cfc57-153">Sur HoloLens, lancez l’application de **communication à distance holographique** .</span><span class="sxs-lookup"><span data-stu-id="cfc57-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="cfc57-154">Dans Unity, sélectionnez **windows > XR > émulation holographique (si vous utilisez un plug-in XR)/Windows XR Remoting (si vous utilisez le kit de développement logiciel (SDK) XR)**.</span><span class="sxs-lookup"><span data-stu-id="cfc57-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Démarrer l’émulation holographique](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="cfc57-156">Définissez le **mode d’émulation** à **distant sur appareil**.</span><span class="sxs-lookup"><span data-stu-id="cfc57-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Définir le mode d’émulation](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="cfc57-158">(**_S’applique uniquement aux XR hérités_**) Sélectionnez la **version** de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="cfc57-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Sélectionner la version de l’appareil](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="cfc57-160">À l’aide de l’adresse IP affichée par l’application de lecteur de communication à distance holographique, définissez le champ **ordinateur distant** .</span><span class="sxs-lookup"><span data-stu-id="cfc57-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Entrer l’adresse IP](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="cfc57-162">Cliquez sur **Connecter**.</span><span class="sxs-lookup"><span data-stu-id="cfc57-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="cfc57-163">Si vous ne pouvez pas vous connecter, assurez-vous que votre HoloLens 2 n’est pas branché sur votre ordinateur et redémarrez Unity.</span><span class="sxs-lookup"><span data-stu-id="cfc57-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="cfc57-164">Connexion au HoloLens à l’aide d’un câble USB</span><span class="sxs-lookup"><span data-stu-id="cfc57-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="cfc57-165">La connexion par câble USB offre une meilleure qualité de rendu et une meilleure stabilité.</span><span class="sxs-lookup"><span data-stu-id="cfc57-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="cfc57-166">Pour utiliser la connexion par câble USB, déconnectez-vous du HoloLens de Wi-Fi dans les paramètres de HoloLens et lancez l’application de lecteur de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="cfc57-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="cfc57-167">Elle affiche une adresse IP commençant par 169.</span><span class="sxs-lookup"><span data-stu-id="cfc57-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="cfc57-168">Utilisez cette adresse IP dans le paramètre d’émulation holographique d’Unity pour vous connecter.</span><span class="sxs-lookup"><span data-stu-id="cfc57-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="cfc57-169">Une fois que l’adresse IP pour le câble USB a été identifiée, il est possible de connecter à nouveau le HoloLens à Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="cfc57-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="cfc57-170">Démarrage d’une session de communication à distance</span><span class="sxs-lookup"><span data-stu-id="cfc57-170">Starting a remoting session</span></span>

<span data-ttu-id="cfc57-171">Avec Unity connectée à HoloLens, entrez en mode lecture dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="cfc57-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="cfc57-172">Une fois la session terminée, quittez le mode lecture.</span><span class="sxs-lookup"><span data-stu-id="cfc57-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="cfc57-173">Il existe un problème connu avec certaines versions de Unity dans laquelle l’éditeur peut se bloquer lors de l’entrée en mode lecture pendant une session de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="cfc57-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="cfc57-174">Ce problème peut se manifester si la fenêtre holographique est ouverte lorsque le projet est chargé.</span><span class="sxs-lookup"><span data-stu-id="cfc57-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="cfc57-175">Pour vous assurer que ce problème ne se produit pas, fermez toujours la boîte de dialogue holographique avant de quitter Unity.</span><span class="sxs-lookup"><span data-stu-id="cfc57-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfc57-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfc57-176">See also</span></span>

- [<span data-ttu-id="cfc57-177">Résolution des problèmes et limitations de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="cfc57-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="cfc57-178">Termes du contrat de licence logiciel Microsoft holographique Remoting</span><span class="sxs-lookup"><span data-stu-id="cfc57-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)