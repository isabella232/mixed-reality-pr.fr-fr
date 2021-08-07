---
title: Écriture et exécution de tests
description: Tests unitaires pour vérifier la fiabilité de MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, UnitTest,
ms.openlocfilehash: d528b5c16ab39271f9984bdd9e23ebca091efd53ed563149f3933ed31ed656dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216255"
---
# <a name="writing-and-running-tests"></a>Écriture et exécution de tests

Pour garantir la fiabilité de MRTK, MRTK dispose d’un ensemble de tests pour s’assurer que les modifications apportées au code ne régressent pas les comportements existants. Avoir une bonne couverture de test dans un Big code base comme MRTK est essentiel pour la stabilité et la confiance lors de l’apport de modifications.

MRTK utilise [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) qui utilise une intégration Unity de [nunit](https://nunit.org/). Ce guide fournit un point de départ sur la façon d’ajouter des tests à MRTK. Il n’explique pas le [Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) et [nunit](https://nunit.org/) Unity qui peut être recherché dans les liens fournis.

Avant de soumettre une demande de tirage (pull request), veillez à :

1. Exécutez les tests localement pour que vos modifications n’empêchent pas le comportement existant (l’achèvement de PRs n’est pas autorisé en cas d’échec d’un test).

1. Si vous corrigez un bogue, écrivez un test pour tester le correctif et vous assurer que les futures modifications du code ne le rompront pas.

1. Si vous écrivez une fonctionnalité, écrivez de nouveaux tests pour empêcher les modifications de code à venir qui rompent cette fonctionnalité.

Les tests playMode sont censés être exécutés dans Unity 2018,4 et peuvent échouer dans d’autres versions d’Unity

## <a name="running-tests"></a>Exécution des tests

### <a name="unity-editor"></a>Éditeur Unity

[Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) se trouve sous **Windows**  >  **General**  >  **Test Runner** et affiche tous les tests MRTK Play et Edit Mode disponibles.

### <a name="command-line"></a>Ligne de commande

Les tests peuvent également être exécutés par un script [PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) situé à l’adresse `Scripts\test\run_playmode_tests.ps1` . Cela permet d’exécuter les tests playMode exactement tels qu’ils sont exécutés sur GitHub/CI (voir ci-dessous), et d’imprimer les résultats. Voici quelques exemples d’exécution du script

Exécuter les tests sur le projet situé dans H:\mrtk.dev, avec Unity 2018,4 (par exemple Unity 2018.4.26 F1)

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Exécutez les tests sur le projet situé dans H:\mrtk.dev, avec Unity 2018,4, output results to C:\ playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

Il est également possible d’exécuter plusieurs fois les tests playMode via le `run_repeat_tests.ps1` script. Tous les paramètres utilisés dans `run_playmode_tests.ps1` peuvent être utilisés.

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>Validation de la requête de tirage

L’élément de configuration de MRTK générera MRTK dans toutes les configurations et exécutera tous les tests en mode de modification et de lecture. Vous pouvez déclencher l’élément de configuration en publiant un commentaire sur le GitHub PR `/azp run mrtk_pr` si l’utilisateur dispose de droits suffisants. Les exécutions de CI sont visibles dans l’onglet « vérifications » de la demande de tirage.

Une fois que tous les tests ont réussi, la demande de tirage peut être fusionnée dans main.

### <a name="stress-tests--bulk-tests"></a>Tests de contrainte/tests en bloc

Parfois, les tests échouent occasionnellement, ce qui peut être frustrant à déboguer.

Pour avoir plusieurs séries de tests en local, modifiez les scripts de test conformes. Le script Python suivant doit rendre ce scénario plus pratique.

La configuration requise pour l’exécution du script Python nécessite l' [installation de Python 3. X](https://www.python.org/downloads/).

Pour un seul test qui doit être exécuté plusieurs fois :

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

Exécutez la commande suivante à partir d’une ligne de commande ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) est recommandé)

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

Copiez et collez la sortie dans votre fichier de test. Le script suivant est destiné à l’exécution de plusieurs tests dans l’ordre :

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

Le nouveau fichier de test doit maintenant contenir

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

Ouvrez Test Runner et observez les nouveaux tests qui peuvent maintenant être appelés à plusieurs reprises.

## <a name="writing-tests"></a>Écriture des tests

Il existe deux types de tests qui peuvent être ajoutés pour le nouveau code

* Tests en mode lecture
* Tests en mode édition

### <a name="play-mode-tests"></a>Tests en mode lecture

Les tests en mode de lecture MRTK ont la possibilité de tester la manière dont votre nouvelle fonctionnalité répond à différentes sources d’entrée, telles que des mains ou des yeux.

Les nouveaux tests en mode lecture peuvent hériter de [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) ou la structure ci-dessous peut être utilisée.

Pour créer un test en mode de lecture :

* Accédez à ressources > MRTK > tests > PlayModeTests
* Clic droit, créer > test > script de test C#
* Remplacer le modèle par défaut par le squelette ci-dessous

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

### <a name="edit-mode-tests"></a>Tests en mode édition

les tests en mode édition sont exécutés en mode édition unity et peuvent être ajoutés dans le dossier **MRTK**  >  **tests**  >  **EditModeTests** de la réalité mixte Shared Computer Toolkit référentiel.
Pour créer un test, le modèle suivant peut être utilisé :

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

### <a name="test-naming-conventions"></a>Tester les conventions de nommage

Les tests doivent généralement être nommés en fonction de la classe qu’ils testent ou du scénario qu’ils testent.
Prenons l’exemple d’une classe à tester :

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

Envisagez de nommer le test

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

Envisagez de placer le test dans une hiérarchie de dossiers similaire à son fichier non test correspondant.
Par exemple :

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

Cela permet de s’assurer qu’il existe un moyen évident de trouver la classe de test correspondante de chaque classe, si une telle classe de test existe.

Le positionnement des tests basés sur un scénario est moins défini : si le test exerce le système d’entrée global, par exemple, envisagez de le placer dans un dossier « InputSystem » dans le dossier de test en mode édition ou en mode lecture correspondant.

### <a name="test-script-icons"></a>Icônes de script de test

Lorsque vous ajoutez un nouveau test, modifiez le script pour qu’il dispose de l’icône MRTK correcte. Pour ce faire, il existe un outil MRTK simple :

1. aller à l’élément de menu Shared Computer Toolkit de la réalité mixte
1. Cliquez sur utilitaires, puis sur mettre à jour, puis sur icônes
1. Cliquez sur tests pour que le programme de mise à jour s’exécute automatiquement, en mettant à jour tous les scripts de test dont les icônes sont manquantes

### <a name="mrtk-utility-methods"></a>Méthodes de l’utilitaire MRTK

Cette section présente certains des extraits de code/méthodes couramment utilisés lors de l’écriture de tests pour MRTK.

Deux classes utilitaires permettent de configurer les MRTK et de tester les interactions avec les composants dans MRTK

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities fournit les méthodes suivantes pour configurer votre MRTK Scene et GameObjects :

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

Reportez-vous aux documents d’API de [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) et pour obtenir d' [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) autres méthodes de ces classes util, car elles sont étendues régulièrement, tandis que les nouveaux tests sont ajoutés à MRTK.
