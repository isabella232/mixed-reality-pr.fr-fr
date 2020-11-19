---
title: Vue d’ensemble de la programmation
description: Découvrez comment accéder aux objets et interfaces maquette à l’aide de scripts.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935406"
---
# <a name="programming-overview"></a><span data-ttu-id="91138-104">Vue d’ensemble de la programmation</span><span class="sxs-lookup"><span data-stu-id="91138-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logo](../images/MaquetteIcon.png) <span data-ttu-id="91138-106">Vue d’ensemble de la programmation</span><span class="sxs-lookup"><span data-stu-id="91138-106">Programming Overview</span></span>

<span data-ttu-id="91138-107">Microsoft maquette utilise JavaScript (ECMAScript 5,1 avec extensions) basé sur l’interpréteur [JINT](https://github.com/sebastienros/jint) .</span><span class="sxs-lookup"><span data-stu-id="91138-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="91138-108">L’extension `.mqjs` est utilisée pour distinguer les fichiers JavaScript maquette du code JavaScript normal.</span><span class="sxs-lookup"><span data-stu-id="91138-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="91138-109">Les objets et interfaces maquette sont accessibles et peuvent faire l’objet d’un script à l’aide de l' `Maquette` objet.</span><span class="sxs-lookup"><span data-stu-id="91138-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="91138-110">La documentation sur les interfaces et les objets maquette est fournie dans la référence d’API de maquette.</span><span class="sxs-lookup"><span data-stu-id="91138-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="91138-111">MaquetteScript est un nouvel ajout et dans le flux, les modifications doivent être attendues.</span><span class="sxs-lookup"><span data-stu-id="91138-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="91138-112">Une documentation plus détaillée et des mises à jour sont bientôt disponibles.</span><span class="sxs-lookup"><span data-stu-id="91138-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="91138-113">Actualités sur l’écriture de scripts</span><span class="sxs-lookup"><span data-stu-id="91138-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="91138-114">TBD-scripts à la une : exemples/didacticiels</span><span class="sxs-lookup"><span data-stu-id="91138-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="91138-115">2x images/légende – lien vers la page Actualités</span><span class="sxs-lookup"><span data-stu-id="91138-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="91138-116">Prise en main de MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="91138-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="91138-117">Mqjs et JS</span><span class="sxs-lookup"><span data-stu-id="91138-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="91138-118">Modèle de programmation</span><span class="sxs-lookup"><span data-stu-id="91138-118">Programming Model</span></span>
  * <span data-ttu-id="91138-119">Modification et exécution</span><span class="sxs-lookup"><span data-stu-id="91138-119">Editing vs. Running</span></span>
* <span data-ttu-id="91138-120">Lien vers le flux de travail de programmation</span><span class="sxs-lookup"><span data-stu-id="91138-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="91138-121">Lien vers le partage des résultats</span><span class="sxs-lookup"><span data-stu-id="91138-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="91138-122">Flux de travail de programmation</span><span class="sxs-lookup"><span data-stu-id="91138-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="91138-123">TBD</span><span class="sxs-lookup"><span data-stu-id="91138-123">TBD</span></span>
* <span data-ttu-id="91138-124">REPL</span><span class="sxs-lookup"><span data-stu-id="91138-124">REPL</span></span>
* <span data-ttu-id="91138-125">Opération de script</span><span class="sxs-lookup"><span data-stu-id="91138-125">Scripting operation</span></span>
* <span data-ttu-id="91138-126">Opération du débogueur</span><span class="sxs-lookup"><span data-stu-id="91138-126">Debugger operation</span></span>
* <span data-ttu-id="91138-127">Boucle de débogage</span><span class="sxs-lookup"><span data-stu-id="91138-127">Debugging loop</span></span>
* <span data-ttu-id="91138-128">Copier/coller du code ?</span><span class="sxs-lookup"><span data-stu-id="91138-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="91138-129">Exécution de scripts. mqjs</span><span class="sxs-lookup"><span data-stu-id="91138-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="91138-130">Pour exécuter un fichier MaquetteScript. mqjs, accédez aux fenêtres compagnon de maquette et ouvrez l’onglet script pour rechercher les scripts.</span><span class="sxs-lookup"><span data-stu-id="91138-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="91138-131">Certaines options ne fonctionneront pas encore, car nous n’avons pas fourni les scripts.</span><span class="sxs-lookup"><span data-stu-id="91138-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="91138-132">Flux de travail de l’éditeur VSCode</span><span class="sxs-lookup"><span data-stu-id="91138-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="91138-133">Pour évaluer un script dans maquette à partir de VSCode, l’utilisateur doit connaître deux commandes :</span><span class="sxs-lookup"><span data-stu-id="91138-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="91138-134">`CTRL-5` évalue le texte sélectionné ou l’intégralité de la ligne où se trouve le curseur.</span><span class="sxs-lookup"><span data-stu-id="91138-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="91138-135">`CTRL-SHIFT-5` évalue l’ensemble du fichier.</span><span class="sxs-lookup"><span data-stu-id="91138-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="91138-136">Le texte est envoyé à maquette, évalué dans l’environnement JavaScript, et le résultat est renvoyé à la console de sortie de VSCode.</span><span class="sxs-lookup"><span data-stu-id="91138-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="91138-137">Cela peut être utilisé comme REPL (Read-eval-Print-Loop).</span><span class="sxs-lookup"><span data-stu-id="91138-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="91138-138">Exemple de première étape</span><span class="sxs-lookup"><span data-stu-id="91138-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="91138-139">Copiez le code suivant dans un fichier dans VSCode :</span><span class="sxs-lookup"><span data-stu-id="91138-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="91138-140">Sélectionnez le code ou uniquement les sections, puis appuyez `CTRL-5` sur Exécuter.</span><span class="sxs-lookup"><span data-stu-id="91138-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="91138-141">Cela doit créer un cube, le placer devant vous et modifier sa couleur.</span><span class="sxs-lookup"><span data-stu-id="91138-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="91138-142">Il existe d’autres exemples de recherche dans l’extension.</span><span class="sxs-lookup"><span data-stu-id="91138-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="91138-143">Partage des résultats</span><span class="sxs-lookup"><span data-stu-id="91138-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="91138-144">Partage entre les utilisateurs et les équipes</span><span class="sxs-lookup"><span data-stu-id="91138-144">How to share between users/teams</span></span>
* <span data-ttu-id="91138-145">Projet zip dans le répertoire documents</span><span class="sxs-lookup"><span data-stu-id="91138-145">Zip project in documents directory</span></span>
* <span data-ttu-id="91138-146">Copier le projet dans le partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="91138-146">Copy project to file share</span></span>
* <span data-ttu-id="91138-147">Ajout de l’emplacement de fichier des envois de partage d’équipe à l’équipe maquette</span><span class="sxs-lookup"><span data-stu-id="91138-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="91138-148">TBD</span><span class="sxs-lookup"><span data-stu-id="91138-148">TBD</span></span>
* <span data-ttu-id="91138-149">Includes, référence à du code ailleurs avec des chemins d’accès relatifs/absolus, modules</span><span class="sxs-lookup"><span data-stu-id="91138-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="91138-150">Bibliotheque?</span><span class="sxs-lookup"><span data-stu-id="91138-150">Libraries?</span></span>
* <span data-ttu-id="91138-151">Prise en charge du runtime</span><span class="sxs-lookup"><span data-stu-id="91138-151">Runtime support</span></span>
* <span data-ttu-id="91138-152">Externes non résolus-comportement lorsque des entrées manquent/se bloquent</span><span class="sxs-lookup"><span data-stu-id="91138-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="91138-153">Pouvez-vous ajouter/modifier/observer le script associé à des objets spécifiques ?</span><span class="sxs-lookup"><span data-stu-id="91138-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="91138-154">Pouvons-nous copier/coller ce script ailleurs ?</span><span class="sxs-lookup"><span data-stu-id="91138-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="91138-155">Qu’en est-il des propriétés de l’objet ?</span><span class="sxs-lookup"><span data-stu-id="91138-155">What about object properties?</span></span>
  * <span data-ttu-id="91138-156">Vous nommez des objets dans ma scène ?</span><span class="sxs-lookup"><span data-stu-id="91138-156">Naming objects in my scene?</span></span> <span data-ttu-id="91138-157">(attribution d’un nouveau nom à un script)</span><span class="sxs-lookup"><span data-stu-id="91138-157">(renaming script with it)</span></span>
  * <span data-ttu-id="91138-158">Mot clé THIS ou SELF pour le script associé à un objet</span><span class="sxs-lookup"><span data-stu-id="91138-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="91138-159">Si je clique avec le bouton droit sur un objet, puis-je voir le code qui lui est associé (et sa hiérarchie)</span><span class="sxs-lookup"><span data-stu-id="91138-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="91138-160">Puis-je sélectionner dans l’interface utilisateur et être affiché dans le code de VSCode ?</span><span class="sxs-lookup"><span data-stu-id="91138-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="91138-161">Comment conserver le code associé à un objet « ensemble » dans le fichier source du script ?</span><span class="sxs-lookup"><span data-stu-id="91138-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="91138-162">Placer la fenêtre des propriétés d’un objet quand je clique dessus ?</span><span class="sxs-lookup"><span data-stu-id="91138-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="91138-163">Dans VR et dans l’onglet principal ?</span><span class="sxs-lookup"><span data-stu-id="91138-163">In VR and in main tab?</span></span>
* <span data-ttu-id="91138-164">Problèmes de sécurité</span><span class="sxs-lookup"><span data-stu-id="91138-164">Security Issues</span></span>
* <span data-ttu-id="91138-165">Test : peut être TBD, mais nous pourrions suggérer une vidéo ou une manipulation de trame par script</span><span class="sxs-lookup"><span data-stu-id="91138-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="91138-166">Si nous disposons d’un mécanisme de création de rapports de bogues, nous pouvons rendre celui-ci accessible via le script pour les autres ( ?)... ultérieurement</span><span class="sxs-lookup"><span data-stu-id="91138-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="91138-167">Déploiement : Comment « partager » le résultat, le package en tant qu’EXE</span><span class="sxs-lookup"><span data-stu-id="91138-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="91138-168">Exécution/contrôle d’une démonstration ou d’une spectating/surveillance</span><span class="sxs-lookup"><span data-stu-id="91138-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="91138-169">Mode lecteur</span><span class="sxs-lookup"><span data-stu-id="91138-169">Player mode</span></span>
* <span data-ttu-id="91138-170">Un segment peut-il vous permettre de créer des « composants » pour le partage ?</span><span class="sxs-lookup"><span data-stu-id="91138-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="91138-171">(peut être TBD)</span><span class="sxs-lookup"><span data-stu-id="91138-171">(might  be tbd)</span></span>
  * <span data-ttu-id="91138-172">Existe-t-il #include ?</span><span class="sxs-lookup"><span data-stu-id="91138-172">Is there #include?</span></span> <span data-ttu-id="91138-173">Cela gère pure JS que je suppose mais peut avoir des conflits d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="91138-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="91138-174">Y a-t-il quelque chose que nous pourrions faire pour qu’un maquette incorpore d’autres maquette avec des objets nommés pour correspondre au code JS ?</span><span class="sxs-lookup"><span data-stu-id="91138-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
