---
title: Suivi oculaire - Configuration de base
description: Comment configurer le suivi oculaire dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, suivi oculaire,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144096"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="9d08f-104">Prise en main du suivi oculaire dans MRTK</span><span class="sxs-lookup"><span data-stu-id="9d08f-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="9d08f-105">Cette page explique comment configurer votre scène Unity MRTK pour utiliser le suivi oculaire dans votre application.</span><span class="sxs-lookup"><span data-stu-id="9d08f-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="9d08f-106">L’exemple suivant suppose que vous commencez avec une nouvelle scène.</span><span class="sxs-lookup"><span data-stu-id="9d08f-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="9d08f-107">Vous pouvez également consulter nos [exemples de suivi des yeux MRTK](../../example-scenes/eye-tracking-examples-overview.md) déjà configurés à l’aide de tonnes d’excellents exemples que vous pouvez créer directement.</span><span class="sxs-lookup"><span data-stu-id="9d08f-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="9d08f-108">Liste de vérification des exigences de suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="9d08f-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="9d08f-109">Pour que le suivi des yeux fonctionne correctement, les conditions suivantes doivent être remplies.</span><span class="sxs-lookup"><span data-stu-id="9d08f-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="9d08f-110">Si vous débutez avec le suivi oculaire sur HoloLens 2 et à la configuration du suivi oculaire dans MRTK, ne vous inquiétez pas !</span><span class="sxs-lookup"><span data-stu-id="9d08f-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="9d08f-111">Nous verrons en détail comment les traiter plus en détail ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9d08f-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="9d08f-112">Un _« oeil de regard fournisseur de données »_ doit être ajouté au système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9d08f-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="9d08f-113">Cela permet de fournir des données de suivi visuel à partir de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="9d08f-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="9d08f-114">La fonctionnalité _« GazeInput »_ doit être activée dans le manifeste de l’application.</span><span class="sxs-lookup"><span data-stu-id="9d08f-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="9d08f-115">**Cette fonctionnalité peut être définie dans Unity 2019, mais dans Unity 2018 et versions antérieures, cette fonctionnalité est disponible uniquement dans Visual Studio et via l’outil de génération MRTK**</span><span class="sxs-lookup"><span data-stu-id="9d08f-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="9d08f-116">Le HoloLens **doit** être étalonné pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9d08f-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="9d08f-117">Consultez notre [exemple pour détecter si un utilisateur est étalonné ou non](eye-tracking-is-user-calibrated.md).</span><span class="sxs-lookup"><span data-stu-id="9d08f-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="9d08f-118">Remarque sur la fonctionnalité GazeInput</span><span class="sxs-lookup"><span data-stu-id="9d08f-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="9d08f-119">Les outils de génération fournis par MRTK (par exemple, Mixed Reality Toolkit-> Utilities-> fenêtre de génération) peuvent automatiquement activer la fonctionnalité GazeInput.</span><span class="sxs-lookup"><span data-stu-id="9d08f-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="9d08f-120">Pour ce faire, vous devez vérifier que la « fonctionnalité d’entrée en regard » est cochée sous l’onglet « options de génération AppX » :</span><span class="sxs-lookup"><span data-stu-id="9d08f-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![Outils de génération MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="9d08f-122">Cet outil trouvera le manifeste AppX une fois la build Unity terminée et ajoutera manuellement la fonctionnalité GazeInput.</span><span class="sxs-lookup"><span data-stu-id="9d08f-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="9d08f-123">**Avant unity 2019, cet outil n’est pas actif lors de l’utilisation de la fenêtre de génération intégrée d’Unity** (par exemple, les paramètres de génération de fichier >).</span><span class="sxs-lookup"><span data-stu-id="9d08f-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="9d08f-124">Avant Unity 2019, lors de l’utilisation de la fenêtre de génération d’Unity, la capacité devra être ajoutée manuellement après la génération Unity, comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d08f-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="9d08f-125">Ouvrez votre projet Visual Studio compilé, puis ouvrez le _Package. appxmanifest_ dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="9d08f-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="9d08f-126">Veillez à cocher la case _'GazeInput'_ sous _capacités_.</span><span class="sxs-lookup"><span data-stu-id="9d08f-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="9d08f-127">Si vous ne voyez pas de fonctionnalité _« GazeInput »_ , vérifiez que votre système répond [à la configuration requise pour l’utilisation de MRTK](/windows/mixed-reality/develop/install-the-tools) (en particulier la version SDK Windows).</span><span class="sxs-lookup"><span data-stu-id="9d08f-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="9d08f-128">_Remarque :_ Vous ne devez effectuer cette opération que si vous effectuez une génération dans un nouveau dossier de Build.</span><span class="sxs-lookup"><span data-stu-id="9d08f-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="9d08f-129">Cela signifie que si vous avez déjà créé votre projet Unity et que vous avez configuré le appxmanifest avant et que vous ciblez à présent le même dossier, vous n’aurez pas besoin de réappliquer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="9d08f-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="9d08f-130">Configuration du suivi des yeux pas à pas</span><span class="sxs-lookup"><span data-stu-id="9d08f-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="9d08f-131">Configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="9d08f-131">Setting up the scene</span></span>

<span data-ttu-id="9d08f-132">Configurez le _MixedRealityToolkit_ en cliquant simplement sur _« Mixed Reality Toolkit-> configure... »_</span><span class="sxs-lookup"><span data-stu-id="9d08f-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="9d08f-133">dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="9d08f-133">in the menu bar.</span></span>

![MRTK configurer](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="9d08f-135">Configuration des profils MRTK requis pour le suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="9d08f-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="9d08f-136">Après avoir configuré votre scène MRTK, vous êtes invité à choisir un profil pour MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d08f-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="9d08f-137">Vous pouvez simplement sélectionner _DefaultMixedRealityToolkitConfigurationProfile_ , puis sélectionner l’option _« copier & personnaliser »_ .</span><span class="sxs-lookup"><span data-stu-id="9d08f-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![Profil MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="9d08f-139">Créer un « fournisseur de données de regard pour les yeux »</span><span class="sxs-lookup"><span data-stu-id="9d08f-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="9d08f-140">Cliquez sur l’onglet _« entrée »_ dans votre profil MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d08f-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="9d08f-141">Pour modifier la valeur par défaut ( _« DefaultMixedRealityInputSystemProfile »_ ), cliquez sur le bouton _« cloner »_ en regard de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="9d08f-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="9d08f-142">Un menu _« cloner un profil »_ s’affiche.</span><span class="sxs-lookup"><span data-stu-id="9d08f-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="9d08f-143">Cliquez simplement sur _cloner_ en bas de ce menu.</span><span class="sxs-lookup"><span data-stu-id="9d08f-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="9d08f-144">Double-cliquez sur votre nouveau profil d’entrée, développez _'Input Data Providers'_ et sélectionnez _' + Add fournisseur de données'_.</span><span class="sxs-lookup"><span data-stu-id="9d08f-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="9d08f-145">Créer un nouveau fournisseur de données :</span><span class="sxs-lookup"><span data-stu-id="9d08f-145">Create a new data provider:</span></span>
  - <span data-ttu-id="9d08f-146">Sous **type** _, sélectionnez « Microsoft. MixedReality. Toolkit. WindowsMixedReality. Input »_«  ->  _WindowsMixedRealityEyeGazeDataProvider »_</span><span class="sxs-lookup"><span data-stu-id="9d08f-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="9d08f-147">Pour la **ou les plateformes,** sélectionnez _« Windows Universal »_.</span><span class="sxs-lookup"><span data-stu-id="9d08f-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![Fournisseur de données MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="9d08f-149">Simulation du suivi oculaire dans l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="9d08f-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="9d08f-150">Vous pouvez simuler l’entrée de suivi oculaire dans l’éditeur Unity pour vous assurer que les événements sont correctement déclenchés avant de déployer l’application sur votre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9d08f-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="9d08f-151">Le signal de point de regard de l’œil est simulé en utilisant simplement l’emplacement de la caméra comme point de regard de l’œil oculaire et le vecteur d’avance de la caméra comme point de regard de l’œil.</span><span class="sxs-lookup"><span data-stu-id="9d08f-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="9d08f-152">Bien que cela soit parfait pour les tests initiaux, veuillez noter qu’il ne s’agit pas d’une bonne imitation pour des mouvements d’œil rapides.</span><span class="sxs-lookup"><span data-stu-id="9d08f-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="9d08f-153">Pour ce faire, il est préférable de vérifier les tests fréquents de vos interactions oculaires sur le HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9d08f-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="9d08f-154">**Activer le suivi oculaire simulé**:</span><span class="sxs-lookup"><span data-stu-id="9d08f-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="9d08f-155">Cliquez sur l’onglet _« entrée »_ dans votre profil de configuration MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d08f-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="9d08f-156">À partir de là, accédez au _« fournisseur de données d’entrée »_«  ->  _service de simulation d’entrée_».</span><span class="sxs-lookup"><span data-stu-id="9d08f-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="9d08f-157">Clonez le _« DefaultMixedRealityInputSimpulationProfile »_ pour y apporter des modifications.</span><span class="sxs-lookup"><span data-stu-id="9d08f-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="9d08f-158">Cochez la case _« simuler la position oculaire »_ .</span><span class="sxs-lookup"><span data-stu-id="9d08f-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![MRTK yeux simuler](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="9d08f-160">**Désactiver le curseur en regard de l’en-tête par défaut**: en général, il est recommandé d’éviter d’afficher un curseur en regard de l’œil ou, si nécessaire, de le rendre _très_ subtil.</span><span class="sxs-lookup"><span data-stu-id="9d08f-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="9d08f-161">Nous vous recommandons de masquer par défaut le curseur de pointage en forme d’en-tête par défaut attaché au profil de pointeur en regard de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d08f-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="9d08f-162">Accédez à votre profil de configuration MRTK-> _«_  ->  _pointeurs_ d’entrée »</span><span class="sxs-lookup"><span data-stu-id="9d08f-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="9d08f-163">Clonez le _« DefaultMixedRealityInputPointerProfile »_ pour y apporter des modifications.</span><span class="sxs-lookup"><span data-stu-id="9d08f-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="9d08f-164">En haut de _« paramètres du pointeur »_, vous devez assigner un curseur Prefab à _« GazeCursor »_.</span><span class="sxs-lookup"><span data-stu-id="9d08f-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="9d08f-165">Pour ce faire, vous pouvez sélectionner le Prefab _« EyeGazeCursor »_ dans MRTK Foundation.</span><span class="sxs-lookup"><span data-stu-id="9d08f-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="9d08f-166">Activation du point d’interdépendance oculaire dans le fournisseur de regard</span><span class="sxs-lookup"><span data-stu-id="9d08f-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="9d08f-167">Dans HoloLens v1, le point de regard de l’en-tête était utilisé comme technique de pointage principal.</span><span class="sxs-lookup"><span data-stu-id="9d08f-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="9d08f-168">Tandis que le point de vue est toujours disponible via le _GazeProvider_ dans MRTK, qui est attaché à votre [appareil photo](https://docs.unity3d.com/ScriptReference/Camera.html), vous pouvez cocher la case _« IsEyeTrackingEnabled »_ dans les paramètres de pointage du profil du pointeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9d08f-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="9d08f-169">Les développeurs peuvent basculer entre le code de regard basé sur les yeux et le point d’arrêt en regard de l’œil en modifiant la propriété _« IsEyeTrackingEnabled »_ de _« GazeProvider »_.</span><span class="sxs-lookup"><span data-stu-id="9d08f-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="9d08f-170">Si l’une des exigences de suivi oculaire n’est pas satisfaite, l’application repasse automatiquement au point de vue de la tête.</span><span class="sxs-lookup"><span data-stu-id="9d08f-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="9d08f-171">Accès aux données de regard visuel</span><span class="sxs-lookup"><span data-stu-id="9d08f-171">Accessing eye gaze data</span></span>

<span data-ttu-id="9d08f-172">Maintenant que votre scène est configurée pour utiliser le suivi oculaire, voyons comment y accéder dans vos scripts : [accès aux données de suivi visuel via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) et [sélections de cibles prises en charge](eye-tracking-target-selection.md)par l’œil.</span><span class="sxs-lookup"><span data-stu-id="9d08f-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="9d08f-173">Test de votre application Unity sur un HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9d08f-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="9d08f-174">La génération de votre application avec le suivi oculaire doit être similaire à la façon dont vous compilez d’autres applications MRTK HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9d08f-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="9d08f-175">Assurez-vous que vous avez activé la fonctionnalité *« entrée en regard »* , comme décrit ci-dessus dans la section, [*une remarque sur la capacité GazeInput*](#a-note-on-the-gazeinput-capability).</span><span class="sxs-lookup"><span data-stu-id="9d08f-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="9d08f-176">Étalonnage oculaire</span><span class="sxs-lookup"><span data-stu-id="9d08f-176">Eye calibration</span></span>

<span data-ttu-id="9d08f-177">Enfin, n’oubliez pas d’exécuter l’étalonnage oculaire sur votre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9d08f-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="9d08f-178">Le système de suivi oculaire ne retourne aucune entrée si l’utilisateur n’est pas étalonné.</span><span class="sxs-lookup"><span data-stu-id="9d08f-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="9d08f-179">Le moyen le plus simple d’atteindre l’étalonnage consiste à retourner le visière et à revenir en arrière.</span><span class="sxs-lookup"><span data-stu-id="9d08f-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="9d08f-180">Une notification système doit vous accueillir comme un nouvel utilisateur et vous demander de passer par l’étalonnage oculaire.</span><span class="sxs-lookup"><span data-stu-id="9d08f-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="9d08f-181">Vous pouvez également trouver l’étalonnage des yeux dans paramètres système : paramètres > système > étalonnage > étalonnage de l’œil d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d08f-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="9d08f-182">Autorisation de suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="9d08f-182">Eye tracking permission</span></span>

<span data-ttu-id="9d08f-183">Quand vous démarrez l’application sur votre HoloLens 2 pour la première fois, une invite s’affiche pour demander à l’utilisateur l’autorisation d’utiliser le suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="9d08f-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="9d08f-184">S’il n’est pas visible, cela indique généralement que la fonctionnalité _« GazeInput »_ n’a pas été définie.</span><span class="sxs-lookup"><span data-stu-id="9d08f-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="9d08f-185">Une fois l’invite d’autorisation affichée une fois, elle n’apparaît plus automatiquement.</span><span class="sxs-lookup"><span data-stu-id="9d08f-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="9d08f-186">Si vous _« avez refusé l’autorisation de suivi oculaire »_, vous pouvez le réinitialiser dans paramètres-> les applications de > de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="9d08f-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="9d08f-187">Vous devez commencer par utiliser le suivi oculaire dans votre application MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="9d08f-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="9d08f-188">N’oubliez pas de consulter [nos didacticiels de suivi des yeux MRTK et des exemples](../../example-scenes/eye-tracking-examples-overview.md) montrant comment utiliser l’entrée de suivi oculaire et fournir facilement des scripts que vous pouvez réutiliser dans vos projets.</span><span class="sxs-lookup"><span data-stu-id="9d08f-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="9d08f-189">Retour à « suivi oculaire dans le MixedRealityToolkit »</span><span class="sxs-lookup"><span data-stu-id="9d08f-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)