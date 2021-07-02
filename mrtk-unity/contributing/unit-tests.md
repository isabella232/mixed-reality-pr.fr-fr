---
title: Écriture et exécution de tests
description: Tests unitaires pour vérifier la fiabilité de MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, UnitTest,
ms.openlocfilehash: c8efb192982a1cb9ca07e91d29a69b11aaffc290
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177113"
---
# <a name="writing-and-running-tests"></a><span data-ttu-id="6d772-104">Écriture et exécution de tests</span><span class="sxs-lookup"><span data-stu-id="6d772-104">Writing and running tests</span></span>

<span data-ttu-id="6d772-105">Pour garantir la fiabilité de MRTK, MRTK dispose d’un ensemble de tests pour s’assurer que les modifications apportées au code ne régressent pas les comportements existants.</span><span class="sxs-lookup"><span data-stu-id="6d772-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="6d772-106">Avoir une bonne couverture de test dans un Big code base comme MRTK est essentiel pour la stabilité et la confiance lors de l’apport de modifications.</span><span class="sxs-lookup"><span data-stu-id="6d772-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="6d772-107">MRTK utilise [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) qui utilise une intégration Unity de [nunit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="6d772-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="6d772-108">Ce guide fournit un point de départ sur la façon d’ajouter des tests à MRTK.</span><span class="sxs-lookup"><span data-stu-id="6d772-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="6d772-109">Il n’explique pas le [Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) et [nunit](https://nunit.org/) Unity qui peut être recherché dans les liens fournis.</span><span class="sxs-lookup"><span data-stu-id="6d772-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="6d772-110">Avant de soumettre une demande de tirage (pull request), veillez à :</span><span class="sxs-lookup"><span data-stu-id="6d772-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="6d772-111">Exécutez les tests localement pour que vos modifications n’empêchent pas le comportement existant (l’achèvement de PRs n’est pas autorisé en cas d’échec d’un test).</span><span class="sxs-lookup"><span data-stu-id="6d772-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="6d772-112">Si vous corrigez un bogue, écrivez un test pour tester le correctif et vous assurer que les futures modifications du code ne le rompront pas.</span><span class="sxs-lookup"><span data-stu-id="6d772-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="6d772-113">Si vous écrivez une fonctionnalité, écrivez de nouveaux tests pour empêcher les modifications de code à venir qui rompent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6d772-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="6d772-114">Les tests playMode sont censés être exécutés dans Unity 2018,4 et peuvent échouer dans d’autres versions d’Unity</span><span class="sxs-lookup"><span data-stu-id="6d772-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="6d772-115">Exécution des tests</span><span class="sxs-lookup"><span data-stu-id="6d772-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="6d772-116">Éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="6d772-116">Unity editor</span></span>

<span data-ttu-id="6d772-117">[Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) se trouve sous **Windows**  >  **General**  >  **Test Runner** et affiche tous les tests MRTK Play et Edit Mode disponibles.</span><span class="sxs-lookup"><span data-stu-id="6d772-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="6d772-118">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6d772-118">Command line</span></span>

<span data-ttu-id="6d772-119">Les tests peuvent également être exécutés par un script [PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) situé à l’adresse `Scripts\test\run_playmode_tests.ps1` .</span><span class="sxs-lookup"><span data-stu-id="6d772-119">Tests can also be run by a [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="6d772-120">Cela permet d’exécuter les tests playMode exactement tels qu’ils sont exécutés sur GitHub/CI (voir ci-dessous), et d’imprimer les résultats.</span><span class="sxs-lookup"><span data-stu-id="6d772-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="6d772-121">Voici quelques exemples d’exécution du script</span><span class="sxs-lookup"><span data-stu-id="6d772-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="6d772-122">Exécuter les tests sur le projet situé dans H:\mrtk.dev, avec Unity 2018,4 (par exemple Unity 2018.4.26 F1)</span><span class="sxs-lookup"><span data-stu-id="6d772-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="6d772-123">Exécutez les tests sur le projet situé dans H:\mrtk.dev, avec Unity 2018,4, output results to C:\ playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="6d772-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="6d772-124">Il est également possible d’exécuter plusieurs fois les tests playMode via le `run_repeat_tests.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="6d772-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="6d772-125">Tous les paramètres utilisés dans `run_playmode_tests.ps1` peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="6d772-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="6d772-126">Validation de la requête de tirage</span><span class="sxs-lookup"><span data-stu-id="6d772-126">Pull request validation</span></span>

<span data-ttu-id="6d772-127">L’élément de configuration de MRTK générera MRTK dans toutes les configurations et exécutera tous les tests en mode de modification et de lecture.</span><span class="sxs-lookup"><span data-stu-id="6d772-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="6d772-128">Vous pouvez déclencher l’élément de configuration en publiant un commentaire sur le GitHub PR `/azp run mrtk_pr` si l’utilisateur dispose de droits suffisants.</span><span class="sxs-lookup"><span data-stu-id="6d772-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="6d772-129">Les exécutions de CI sont visibles dans l’onglet « vérifications » de la demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="6d772-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="6d772-130">Une fois que tous les tests ont réussi, la demande de tirage peut être fusionnée dans main.</span><span class="sxs-lookup"><span data-stu-id="6d772-130">Only after all of the tests have passed successfully can the PR be merged into main.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="6d772-131">Tests de contrainte/tests en bloc</span><span class="sxs-lookup"><span data-stu-id="6d772-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="6d772-132">Parfois, les tests échouent occasionnellement, ce qui peut être frustrant à déboguer.</span><span class="sxs-lookup"><span data-stu-id="6d772-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="6d772-133">Pour avoir plusieurs séries de tests en local, modifiez les scripts de test conformes.</span><span class="sxs-lookup"><span data-stu-id="6d772-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="6d772-134">Le script Python suivant doit rendre ce scénario plus pratique.</span><span class="sxs-lookup"><span data-stu-id="6d772-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="6d772-135">La configuration requise pour l’exécution du script Python nécessite l' [installation de Python 3. X](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="6d772-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="6d772-136">Pour un seul test qui doit être exécuté plusieurs fois :</span><span class="sxs-lookup"><span data-stu-id="6d772-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="6d772-137">Exécutez la commande suivante à partir d’une ligne de commande ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) est recommandé)</span><span class="sxs-lookup"><span data-stu-id="6d772-137">Run the following from a command line ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="6d772-138">Copiez et collez la sortie dans votre fichier de test.</span><span class="sxs-lookup"><span data-stu-id="6d772-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="6d772-139">Le script suivant est destiné à l’exécution de plusieurs tests dans l’ordre :</span><span class="sxs-lookup"><span data-stu-id="6d772-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="6d772-140">Le nouveau fichier de test doit maintenant contenir</span><span class="sxs-lookup"><span data-stu-id="6d772-140">The new test file should now contain</span></span>

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="6d772-141">Ouvrez Test Runner et observez les nouveaux tests qui peuvent maintenant être appelés à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="6d772-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="6d772-142">Écriture des tests</span><span class="sxs-lookup"><span data-stu-id="6d772-142">Writing tests</span></span>

<span data-ttu-id="6d772-143">Il existe deux types de tests qui peuvent être ajoutés pour le nouveau code</span><span class="sxs-lookup"><span data-stu-id="6d772-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="6d772-144">Tests en mode lecture</span><span class="sxs-lookup"><span data-stu-id="6d772-144">Play mode tests</span></span>
* <span data-ttu-id="6d772-145">Tests en mode édition</span><span class="sxs-lookup"><span data-stu-id="6d772-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="6d772-146">Tests en mode lecture</span><span class="sxs-lookup"><span data-stu-id="6d772-146">Play mode tests</span></span>

<span data-ttu-id="6d772-147">Les tests en mode de lecture MRTK ont la possibilité de tester la manière dont votre nouvelle fonctionnalité répond à différentes sources d’entrée, telles que des mains ou des yeux.</span><span class="sxs-lookup"><span data-stu-id="6d772-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="6d772-148">Les nouveaux tests en mode lecture peuvent hériter de [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) ou la structure ci-dessous peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="6d772-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) or the skeleton below can be used.</span></span>

<span data-ttu-id="6d772-149">Pour créer un test en mode de lecture :</span><span class="sxs-lookup"><span data-stu-id="6d772-149">To create a new play mode test:</span></span>

* <span data-ttu-id="6d772-150">Accédez à ressources > MRTK > tests > PlayModeTests</span><span class="sxs-lookup"><span data-stu-id="6d772-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="6d772-151">Clic droit, créer > test > script de test C#</span><span class="sxs-lookup"><span data-stu-id="6d772-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="6d772-152">Remplacer le modèle par défaut par le squelette ci-dessous</span><span class="sxs-lookup"><span data-stu-id="6d772-152">Replace the default template with the skeleton below</span></span>

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a><span data-ttu-id="6d772-153">Tests en mode édition</span><span class="sxs-lookup"><span data-stu-id="6d772-153">Edit mode tests</span></span>

<span data-ttu-id="6d772-154">les tests en mode édition sont exécutés en mode édition unity et peuvent être ajoutés dans le dossier **MRTK**  >  **tests**  >  **EditModeTests** de la réalité mixte Shared Computer Toolkit référentiel.</span><span class="sxs-lookup"><span data-stu-id="6d772-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="6d772-155">Pour créer un test, le modèle suivant peut être utilisé :</span><span class="sxs-lookup"><span data-stu-id="6d772-155">To create a new test the following template can be used:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a><span data-ttu-id="6d772-156">Tester les conventions de nommage</span><span class="sxs-lookup"><span data-stu-id="6d772-156">Test naming conventions</span></span>

<span data-ttu-id="6d772-157">Les tests doivent généralement être nommés en fonction de la classe qu’ils testent ou du scénario qu’ils testent.</span><span class="sxs-lookup"><span data-stu-id="6d772-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="6d772-158">Prenons l’exemple d’une classe à tester :</span><span class="sxs-lookup"><span data-stu-id="6d772-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="6d772-159">Envisagez de nommer le test</span><span class="sxs-lookup"><span data-stu-id="6d772-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="6d772-160">Envisagez de placer le test dans une hiérarchie de dossiers similaire à son fichier non test correspondant.</span><span class="sxs-lookup"><span data-stu-id="6d772-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="6d772-161">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6d772-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="6d772-162">Cela permet de s’assurer qu’il existe un moyen évident de trouver la classe de test correspondante de chaque classe, si une telle classe de test existe.</span><span class="sxs-lookup"><span data-stu-id="6d772-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="6d772-163">Le positionnement des tests basés sur un scénario est moins défini : si le test exerce le système d’entrée global, par exemple, envisagez de le placer dans un dossier « InputSystem » dans le dossier de test en mode édition ou en mode lecture correspondant.</span><span class="sxs-lookup"><span data-stu-id="6d772-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="6d772-164">Icônes de script de test</span><span class="sxs-lookup"><span data-stu-id="6d772-164">Test script icons</span></span>

<span data-ttu-id="6d772-165">Lorsque vous ajoutez un nouveau test, modifiez le script pour qu’il dispose de l’icône MRTK correcte.</span><span class="sxs-lookup"><span data-stu-id="6d772-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="6d772-166">Pour ce faire, il existe un outil MRTK simple :</span><span class="sxs-lookup"><span data-stu-id="6d772-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="6d772-167">aller à l’élément de menu Shared Computer Toolkit de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="6d772-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="6d772-168">Cliquez sur utilitaires, puis sur mettre à jour, puis sur icônes</span><span class="sxs-lookup"><span data-stu-id="6d772-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="6d772-169">Cliquez sur tests pour que le programme de mise à jour s’exécute automatiquement, en mettant à jour tous les scripts de test dont les icônes sont manquantes</span><span class="sxs-lookup"><span data-stu-id="6d772-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="6d772-170">Méthodes de l’utilitaire MRTK</span><span class="sxs-lookup"><span data-stu-id="6d772-170">MRTK Utility methods</span></span>

<span data-ttu-id="6d772-171">Cette section présente certains des extraits de code/méthodes couramment utilisés lors de l’écriture de tests pour MRTK.</span><span class="sxs-lookup"><span data-stu-id="6d772-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="6d772-172">Deux classes utilitaires permettent de configurer les MRTK et de tester les interactions avec les composants dans MRTK</span><span class="sxs-lookup"><span data-stu-id="6d772-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="6d772-173">TestUtilities fournit les méthodes suivantes pour configurer votre MRTK Scene et GameObjects :</span><span class="sxs-lookup"><span data-stu-id="6d772-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

<span data-ttu-id="6d772-174">Reportez-vous aux documents d’API de [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) et pour obtenir d' [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) autres méthodes de ces classes util, car elles sont étendues régulièrement, tandis que les nouveaux tests sont ajoutés à MRTK.</span><span class="sxs-lookup"><span data-stu-id="6d772-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>
