---
title: Fonctionnalités expérimentales
description: Document relatif aux fonctionnalités expérimentales dans MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121377"
---
# <a name="experimental-features"></a><span data-ttu-id="db8c4-104">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="db8c4-104">Experimental features</span></span>

<span data-ttu-id="db8c4-105">Certaines fonctionnalités de l’équipe MRTK sur semblent avoir beaucoup de valeur initiale même si nous n’avons pas entièrement étoffer les détails.</span><span class="sxs-lookup"><span data-stu-id="db8c4-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="db8c4-106">Pour ces types de fonctionnalités, nous souhaitons que la Communauté puisse les voir tôt.</span><span class="sxs-lookup"><span data-stu-id="db8c4-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="db8c4-107">Dans la mesure où elles sont au début du cycle, nous les étiquetons comme expérimentales pour indiquer qu’elles sont toujours en cours d’évolution et sujettes à modification au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="db8c4-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="db8c4-108">Ce qu’il faut attendre d’une fonctionnalité expérimentale</span><span class="sxs-lookup"><span data-stu-id="db8c4-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="db8c4-109">Si un composant est marqué comme étant expérimental, vous pouvez vous attendre à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="db8c4-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="db8c4-110">Exemple de scène illustrant l’utilisation, située sous `MRTK/Examples/Experimental` un sous-dossier</span><span class="sxs-lookup"><span data-stu-id="db8c4-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="db8c4-111">Les fonctionnalités expérimentales ne peuvent pas contenir de documents.</span><span class="sxs-lookup"><span data-stu-id="db8c4-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="db8c4-112">Ils n’ont probablement pas de tests.</span><span class="sxs-lookup"><span data-stu-id="db8c4-112">They probably don't have tests.</span></span>
- <span data-ttu-id="db8c4-113">Les fonctionnalités expérimentales sont sujettes à modification.</span><span class="sxs-lookup"><span data-stu-id="db8c4-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="db8c4-114">Instructions relatives aux fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="db8c4-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="db8c4-115">Le code expérimental doit résider dans un dossier distinct</span><span class="sxs-lookup"><span data-stu-id="db8c4-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="db8c4-116">Le code expérimental doit être placé dans un dossier expérimental de niveau supérieur, suivi du nom de la fonctionnalité expérimentale.</span><span class="sxs-lookup"><span data-stu-id="db8c4-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="db8c4-117">Par exemple, si vous tentez de contribuer à une nouvelle fonctionnalité FooBar, placez le code dans ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="db8c4-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="db8c4-118">Exemples de scènes, scripts `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="db8c4-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="db8c4-119">Scripts de composant, prefabs accéder à `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="db8c4-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="db8c4-120">Les inspecteurs de composants vont dans `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="db8c4-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="db8c4-121">Si vous utilisez des sous-dossiers sous le nom de la fonctionnalité expérimentale, essayez d’effectuer une mise en miroir de la même structure de dossiers de MRTK.</span><span class="sxs-lookup"><span data-stu-id="db8c4-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="db8c4-122">Par exemple, les solveurs sont placés sous `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="db8c4-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="db8c4-123">Gardez les scènes dans un dossier de scène près du haut : `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="db8c4-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="db8c4-124">Nous n’avons pas envisagé de disposer d’un seul dossier racine expérimental et de placer des expérimentations à la place `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` .</span><span class="sxs-lookup"><span data-stu-id="db8c4-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="db8c4-125">Nous avons décidé d’utiliser des dossiers à la base pour faciliter la découverte des fonctionnalités expérimentales.</span><span class="sxs-lookup"><span data-stu-id="db8c4-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="db8c4-126">Le code expérimental doit se trouver dans un espace de noms spécial</span><span class="sxs-lookup"><span data-stu-id="db8c4-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="db8c4-127">Assurez-vous que le code expérimental se trouve dans un espace de noms expérimental qui correspond à l’emplacement non expérimental.</span><span class="sxs-lookup"><span data-stu-id="db8c4-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="db8c4-128">Par exemple, si votre composant fait partie de solveurs à `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , son espace de noms doit être `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .</span><span class="sxs-lookup"><span data-stu-id="db8c4-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="db8c4-129">Pour obtenir un exemple, consultez [cette PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) .</span><span class="sxs-lookup"><span data-stu-id="db8c4-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="db8c4-130">Les fonctionnalités expérimentales doivent avoir un attribut [expérimental]</span><span class="sxs-lookup"><span data-stu-id="db8c4-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="db8c4-131">Ajoutez un `[Experimental]` attribut au-dessus de l’un de vos champs pour qu’une petite boîte de dialogue s’affiche dans l’éditeur de composant qui mentionne que votre fonctionnalité est expérimentale et sujette à des modifications importantes.</span><span class="sxs-lookup"><span data-stu-id="db8c4-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="db8c4-132">Les menus des fonctionnalités expérimentales doivent se trouver dans le sous-menu « expérimental ».</span><span class="sxs-lookup"><span data-stu-id="db8c4-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="db8c4-133">Assurez-vous que les fonctionnalités expérimentales se trouvent sous les sous-menus « expérimentaux » lors de l’ajout de commandes aux menus de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="db8c4-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="db8c4-134">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="db8c4-134">Here are a few examples:</span></span>

<span data-ttu-id="db8c4-135">Ajout d’une commande de menu de niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="db8c4-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="db8c4-136">Ajout d’un menu de composant :</span><span class="sxs-lookup"><span data-stu-id="db8c4-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="db8c4-137">Documentation</span><span class="sxs-lookup"><span data-stu-id="db8c4-137">Documentation</span></span>

<span data-ttu-id="db8c4-138">Procédez comme suit pour ajouter de la documentation pour votre fonctionnalité expérimentale :</span><span class="sxs-lookup"><span data-stu-id="db8c4-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="db8c4-139">Toute documentation relative à une fonctionnalité expérimentale doit se trouver dans un `readme.md` fichier dans le dossier expérimental.</span><span class="sxs-lookup"><span data-stu-id="db8c4-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="db8c4-140">Par exemple, MRTK/SDK/expérimental/PulseShader/Readme. MD.</span><span class="sxs-lookup"><span data-stu-id="db8c4-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="db8c4-141">Sous *vues d’ensemble des fonctionnalités* , ajoutez un lien dans la section *expérimental* à l’adresse [`Documentation/toc.yml`](../toc.yml) .</span><span class="sxs-lookup"><span data-stu-id="db8c4-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="db8c4-142">Réduire l’impact sur le code MRTK</span><span class="sxs-lookup"><span data-stu-id="db8c4-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="db8c4-143">Bien que votre modification MRTK puisse faire fonctionner votre expérience, elle peut avoir un impact sur d’autres personnes de la façon dont vous ne vous attendez pas.</span><span class="sxs-lookup"><span data-stu-id="db8c4-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="db8c4-144">Toute régression que vous apportez au code MRTK Core entraînerait la restauration de votre demande de tirage (pull request).</span><span class="sxs-lookup"><span data-stu-id="db8c4-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="db8c4-145">L’objectif est de ne pas modifier les dossiers autres que les dossiers expérimentaux.</span><span class="sxs-lookup"><span data-stu-id="db8c4-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="db8c4-146">Voici une liste des dossiers qui peuvent avoir des modifications expérimentales :</span><span class="sxs-lookup"><span data-stu-id="db8c4-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="db8c4-147">MRTK/SDK/expérimental</span><span class="sxs-lookup"><span data-stu-id="db8c4-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="db8c4-148">MRTK/Kit de développement logiciel/inspecteurs/expérimental</span><span class="sxs-lookup"><span data-stu-id="db8c4-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="db8c4-149">MRTK/examples/expérimental</span><span class="sxs-lookup"><span data-stu-id="db8c4-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="db8c4-150">Les modifications en dehors de ces dossiers doivent être traitées très attentivement.</span><span class="sxs-lookup"><span data-stu-id="db8c4-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="db8c4-151">Si votre fonctionnalité expérimentale doit inclure des modifications du code MRTK Core, envisagez de fractionner les modifications apportées MRTK en une requête de tirage distincte incluant des tests et de la documentation.</span><span class="sxs-lookup"><span data-stu-id="db8c4-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="db8c4-152">L’utilisation de votre fonctionnalité expérimentale ne doit pas avoir d’impact sur la capacité des personnes à utiliser les contrôles principaux</span><span class="sxs-lookup"><span data-stu-id="db8c4-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="db8c4-153">La plupart des gens utilisent des composants d’expérience utilisateur de base tels que le bouton ManipulationHandler et les plus fréquents.</span><span class="sxs-lookup"><span data-stu-id="db8c4-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="db8c4-154">Ils n’utiliseront probablement pas votre fonctionnalité expérimentale s’ils les empêchent d’utiliser des boutons.</span><span class="sxs-lookup"><span data-stu-id="db8c4-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="db8c4-155">L’utilisation de votre composant ne doit pas rompre les boutons, ManipulationHandler, BoundingBox ou interactive.</span><span class="sxs-lookup"><span data-stu-id="db8c4-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="db8c4-156">Par exemple, dans [ce PR ScrollableObjectCollection](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), l’ajout d’un ScrollableObjectCollection a entraîné l’incapacité des utilisateurs à utiliser le bouton HoloLens prefabs.</span><span class="sxs-lookup"><span data-stu-id="db8c4-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="db8c4-157">Même si cela n’a pas été provoqué par un bogue dans la demande de tirage (mais a plutôt exposé un bogue existant), la demande de tirage n’a pas pu être archivée.</span><span class="sxs-lookup"><span data-stu-id="db8c4-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="db8c4-158">Fournir un exemple de scène illustrant l’utilisation de la fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="db8c4-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="db8c4-159">Les utilisateurs doivent voir comment utiliser votre fonctionnalité et comment la tester.</span><span class="sxs-lookup"><span data-stu-id="db8c4-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="db8c4-160">Fournissez un exemple sous MRTK/examples/expérimental/YOUR_FEATURE</span><span class="sxs-lookup"><span data-stu-id="db8c4-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="db8c4-161">Réduire les défauts visibles par l’utilisateur dans les fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="db8c4-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="db8c4-162">D’autres n’utilisent pas la fonctionnalité expérimentale si elle ne fonctionne pas, mais elle n’est pas diplômée à une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="db8c4-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="db8c4-163">Testez votre exemple de scène sur votre plateforme cible, assurez-vous qu’elle fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="db8c4-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="db8c4-164">Assurez-vous que votre fonctionnalité fonctionne également dans l’éditeur, afin que les utilisateurs puissent rapidement itérer et voir votre fonctionnalité même s’ils n’ont pas la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="db8c4-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="db8c4-165">Diplôme du code expérimental dans le code MRTK</span><span class="sxs-lookup"><span data-stu-id="db8c4-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="db8c4-166">Si une fonctionnalité finit par être très utilisée, nous devrions la faire passer en code MRTK principal.</span><span class="sxs-lookup"><span data-stu-id="db8c4-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="db8c4-167">Pour ce faire, la fonctionnalité doit avoir des tests, de la documentation et un exemple de scène.</span><span class="sxs-lookup"><span data-stu-id="db8c4-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="db8c4-168">Lorsque vous êtes prêt à MRTK la fonctionnalité, créez un problème pour l’archivage de votre demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="db8c4-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="db8c4-169">La demande de tirage doit inclure tous les éléments nécessaires pour créer une fonctionnalité de base : les tests, la documentation et un exemple de scène présentant l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="db8c4-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="db8c4-170">En outre, n’oubliez pas de mettre à jour les espaces de noms pour supprimer le sous-espace « expérimental ».</span><span class="sxs-lookup"><span data-stu-id="db8c4-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
