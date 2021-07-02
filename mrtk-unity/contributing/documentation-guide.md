---
title: Instructions de documentation
description: instructions et normes de la documentation pour MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 95af19b71a9fe06dabad058e75f78d951262ba4a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175348"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="2e06e-104">Instructions de documentation</span><span class="sxs-lookup"><span data-stu-id="2e06e-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="2e06e-105">ce document décrit les directives et les normes de la réalité mixte Shared Computer Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="2e06e-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="2e06e-106">Cela fournit une introduction aux aspects techniques de l’écriture et de la génération de documentation, pour mettre en évidence des pièges courants et pour décrire le style d’écriture recommandé.</span><span class="sxs-lookup"><span data-stu-id="2e06e-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="2e06e-107">La page elle-même est supposée servir d’exemple. elle utilise donc le style prévu et les fonctionnalités de balisage les plus courantes de la documentation.</span><span class="sxs-lookup"><span data-stu-id="2e06e-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="2e06e-108">Source</span><span class="sxs-lookup"><span data-stu-id="2e06e-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="2e06e-109">Procédure</span><span class="sxs-lookup"><span data-stu-id="2e06e-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="2e06e-110">Concevez</span><span class="sxs-lookup"><span data-stu-id="2e06e-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="2e06e-111">Remarques sur les performances</span><span class="sxs-lookup"><span data-stu-id="2e06e-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="2e06e-112">Dernières modifications</span><span class="sxs-lookup"><span data-stu-id="2e06e-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="2e06e-113">Fonctionnalités et balises</span><span class="sxs-lookup"><span data-stu-id="2e06e-113">Functionality and markup</span></span>

<span data-ttu-id="2e06e-114">Cette section décrit les fonctionnalités fréquemment nécessaires.</span><span class="sxs-lookup"><span data-stu-id="2e06e-114">This section describes frequently needed features.</span></span> <span data-ttu-id="2e06e-115">Pour voir comment ils fonctionnent, examinez le code source de la page.</span><span class="sxs-lookup"><span data-stu-id="2e06e-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="2e06e-116">Listes numérotées</span><span class="sxs-lookup"><span data-stu-id="2e06e-116">Numbered lists</span></span>
   1. <span data-ttu-id="2e06e-117">Listes numérotées imbriquées avec au moins 3 espaces vides de début</span><span class="sxs-lookup"><span data-stu-id="2e06e-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="2e06e-118">Le nombre réel dans le code n’est pas pertinent. l’analyse s’occupe de définir le numéro d’élément correct.</span><span class="sxs-lookup"><span data-stu-id="2e06e-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="2e06e-119">Listes de points à puces</span><span class="sxs-lookup"><span data-stu-id="2e06e-119">Bullet point lists</span></span>
  - <span data-ttu-id="2e06e-120">Listes de points à puces imbriquées</span><span class="sxs-lookup"><span data-stu-id="2e06e-120">Nested bullet point lists</span></span>
- <span data-ttu-id="2e06e-121">Texte en **gras** avec \* \* double astérisque\*\*</span><span class="sxs-lookup"><span data-stu-id="2e06e-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="2e06e-122"> *texte* en italique avec un trait de \_ soulignement \_ ou \* un astérisque\*</span><span class="sxs-lookup"><span data-stu-id="2e06e-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="2e06e-123">Texte `highlighted as code` dans une phrase \` en utilisant des guillemets\`</span><span class="sxs-lookup"><span data-stu-id="2e06e-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="2e06e-124">Liens vers les pages docs [instructions de documentation MRTK](documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="2e06e-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="2e06e-125">Liens vers des [ancres dans une page](#style); les points d’ancrage sont formés en remplaçant les espaces par des tirets et en les convertissant en minuscules</span><span class="sxs-lookup"><span data-stu-id="2e06e-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="2e06e-126">Pour les exemples de code, nous utilisons les blocs avec trois battements \` \` \` et spécifiez *CSharp* comme langage pour la mise en surbrillance de la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="2e06e-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="2e06e-127">Quand vous mentionnez du code dans une phrase `use a single backtick` .</span><span class="sxs-lookup"><span data-stu-id="2e06e-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="2e06e-128">Éléments TODO</span><span class="sxs-lookup"><span data-stu-id="2e06e-128">TODOs</span></span>

<span data-ttu-id="2e06e-129">Évitez d’utiliser éléments todo dans docs, car ces éléments todo (comme le code éléments TODO) ont tendance à s’accumuler et à obtenir des informations sur la façon dont elles doivent être mises à jour et pourquoi la perte est perdue.</span><span class="sxs-lookup"><span data-stu-id="2e06e-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="2e06e-130">Si vous devez absolument ajouter un TODO, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e06e-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="2e06e-131">Présentez un nouveau problème sur GitHub décrivant le contexte derrière le TODO et fournissez suffisamment d’informations en arrière-plan qu’un autre contributeur serait en mesure de comprendre, puis de traiter le TODO.</span><span class="sxs-lookup"><span data-stu-id="2e06e-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="2e06e-132">Référencez l’URL du problème dans le todo dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="2e06e-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="2e06e-133">Sections en surbrillance</span><span class="sxs-lookup"><span data-stu-id="2e06e-133">Highlighted sections</span></span>

<span data-ttu-id="2e06e-134">Pour mettre en surbrillance des points spécifiques sur le lecteur, utilisez *> [!NOTE]* , *> [!WARNING]* et *> [!IMPORTANT]* pour produire les styles suivants.</span><span class="sxs-lookup"><span data-stu-id="2e06e-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="2e06e-135">Il est recommandé d’utiliser des notes pour les points généraux et les points d’avertissement/importants uniquement pour des cas spéciaux pertinents.</span><span class="sxs-lookup"><span data-stu-id="2e06e-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="2e06e-136">Exemple de note</span><span class="sxs-lookup"><span data-stu-id="2e06e-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="2e06e-137">Exemple d’avertissement</span><span class="sxs-lookup"><span data-stu-id="2e06e-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e06e-138">Exemple de commentaire important</span><span class="sxs-lookup"><span data-stu-id="2e06e-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="2e06e-139">Mise en page</span><span class="sxs-lookup"><span data-stu-id="2e06e-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="2e06e-140">Introduction</span><span class="sxs-lookup"><span data-stu-id="2e06e-140">Introduction</span></span>

<span data-ttu-id="2e06e-141">La partie juste après le titre du chapitre principal doit servir d’brève introduction à ce qu’est le chapitre.</span><span class="sxs-lookup"><span data-stu-id="2e06e-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="2e06e-142">N’effectuez pas cette opération trop longue, à la place, ajoutez des sous-titres.</span><span class="sxs-lookup"><span data-stu-id="2e06e-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="2e06e-143">Celles-ci permettent de lier des sections et peuvent être enregistrées en tant que signets.</span><span class="sxs-lookup"><span data-stu-id="2e06e-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="2e06e-144">Corps principal</span><span class="sxs-lookup"><span data-stu-id="2e06e-144">Main body</span></span>

<span data-ttu-id="2e06e-145">Utilisez des titres à deux et trois niveaux pour structurer le reste.</span><span class="sxs-lookup"><span data-stu-id="2e06e-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="2e06e-146">**Mini sections**</span><span class="sxs-lookup"><span data-stu-id="2e06e-146">**Mini Sections**</span></span>

<span data-ttu-id="2e06e-147">Utilisez une ligne de texte en gras pour les blocs qui doivent ressortir. Nous pouvons le remplacer par des titres à quatre niveaux à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="2e06e-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="2e06e-148">Section « Voir aussi »</span><span class="sxs-lookup"><span data-stu-id="2e06e-148">'See also' section</span></span>

<span data-ttu-id="2e06e-149">La plupart des pages doivent se terminer par un chapitre appelé *Voir aussi*.</span><span class="sxs-lookup"><span data-stu-id="2e06e-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="2e06e-150">Ce chapitre est simplement une liste à puces de liens vers les pages associées à cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2e06e-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="2e06e-151">Ces liens peuvent également apparaître dans le texte de la page, le cas échéant, mais cela n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2e06e-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="2e06e-152">De même, le texte de la page peut contenir des liens vers des pages qui ne sont pas liées à la rubrique principale, celles-ci ne doivent pas être incluses dans la liste *Voir aussi* .</span><span class="sxs-lookup"><span data-stu-id="2e06e-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="2e06e-153">Consultez le [chapitre « Voir aussi » de cette page](#see-also) comme exemple pour le choix des liens.</span><span class="sxs-lookup"><span data-stu-id="2e06e-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="2e06e-154">Table des matières (TOC)</span><span class="sxs-lookup"><span data-stu-id="2e06e-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="2e06e-155">Les fichiers TOC sont utilisés pour générer les barres de navigation dans la documentation MRTK github.io.</span><span class="sxs-lookup"><span data-stu-id="2e06e-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="2e06e-156">Chaque fois qu’un nouveau fichier de documentation est ajouté, assurez-vous qu’il existe une entrée pour ce fichier dans l’un des fichiers toc. yml du dossier de documentation.</span><span class="sxs-lookup"><span data-stu-id="2e06e-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="2e06e-157">Seuls les articles figurant dans les fichiers de la table des matières s’affichent dans la barre de navigation des documents du développeur. Il peut y avoir un fichier toc pour chaque sous-dossier du dossier de la documentation qui peut être lié à n’importe quel fichier TOC existant pour l’ajouter en tant que sous-section à la partie correspondante de la navigation.</span><span class="sxs-lookup"><span data-stu-id="2e06e-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="2e06e-158">Style</span><span class="sxs-lookup"><span data-stu-id="2e06e-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="2e06e-159">Style d’écriture</span><span class="sxs-lookup"><span data-stu-id="2e06e-159">Writing style</span></span>

<span data-ttu-id="2e06e-160">Règle générale : essayez d’utiliser un **son professionnel**.</span><span class="sxs-lookup"><span data-stu-id="2e06e-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="2e06e-161">Cela signifie généralement qu’il faut éviter un « ton de conversation ».</span><span class="sxs-lookup"><span data-stu-id="2e06e-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="2e06e-162">Essayez également d’éviter hyperbolique et sensationalism.</span><span class="sxs-lookup"><span data-stu-id="2e06e-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="2e06e-163">N’essayez pas d’être amusant.</span><span class="sxs-lookup"><span data-stu-id="2e06e-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="2e06e-164">Ne jamais écrire’I'</span><span class="sxs-lookup"><span data-stu-id="2e06e-164">Never write 'I'</span></span>
3. <span data-ttu-id="2e06e-165">Évitez « nous ».</span><span class="sxs-lookup"><span data-stu-id="2e06e-165">Avoid 'we'.</span></span> <span data-ttu-id="2e06e-166">Cela peut généralement être facilement reformulé en utilisant’MRTK’à la place.</span><span class="sxs-lookup"><span data-stu-id="2e06e-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="2e06e-167">Exemple : « nous prenons en charge cette fonctionnalité »-> « MRTK prend en charge cette fonctionnalité » ou « les fonctionnalités suivantes sont prises en charge... ».</span><span class="sxs-lookup"><span data-stu-id="2e06e-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="2e06e-168">De même, essayez d’éviter’vous'.</span><span class="sxs-lookup"><span data-stu-id="2e06e-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="2e06e-169">Exemple : « avec cette simple modification, votre nuanceur devient configurable ! »</span><span class="sxs-lookup"><span data-stu-id="2e06e-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="2e06e-170">-> « les nuanceurs peuvent être configurables avec un minimum d’effort ».</span><span class="sxs-lookup"><span data-stu-id="2e06e-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="2e06e-171">N’utilisez pas’expressions mal écrit'.</span><span class="sxs-lookup"><span data-stu-id="2e06e-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="2e06e-172">Évitez tout son intérêt, nous n’avons pas besoin de vendre quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="2e06e-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="2e06e-173">De même, évitez d’être trop spectaculaire.</span><span class="sxs-lookup"><span data-stu-id="2e06e-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="2e06e-174">Les points d’exclamation sont rarement nécessaires.</span><span class="sxs-lookup"><span data-stu-id="2e06e-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="2e06e-175">Mise en majuscules</span><span class="sxs-lookup"><span data-stu-id="2e06e-175">Capitalization</span></span>

- <span data-ttu-id="2e06e-176">Utilisez la **casse en phrases pour les titres**.</span><span class="sxs-lookup"><span data-stu-id="2e06e-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="2e06e-177">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="2e06e-177">Ie.</span></span> <span data-ttu-id="2e06e-178">Mettez en majuscule la première lettre et les noms, mais rien d’autre.</span><span class="sxs-lookup"><span data-stu-id="2e06e-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="2e06e-179">Utilisez l’anglais normal pour tout le reste.</span><span class="sxs-lookup"><span data-stu-id="2e06e-179">Use regular English for everything else.</span></span> <span data-ttu-id="2e06e-180">Cela signifie que vous **ne devez pas mettre en majuscules les mots arbitraires**, même s’ils contiennent une signification particulière dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="2e06e-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="2e06e-181">Préférer le *texte en italique* pour la mise en surbrillance de certains mots, [voir ci-dessous](#emphasis-and-highlighting).</span><span class="sxs-lookup"><span data-stu-id="2e06e-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="2e06e-182">Lorsqu’un lien est incorporé dans une phrase (qui est la méthode recommandée), le nom du chapitre standard utilise toujours des majuscules, ce qui rompt la règle d’aucune mise en majuscule arbitraire dans le texte.</span><span class="sxs-lookup"><span data-stu-id="2e06e-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="2e06e-183">Par conséquent, utilisez un nom de lien personnalisé pour corriger la casse.</span><span class="sxs-lookup"><span data-stu-id="2e06e-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="2e06e-184">À titre d’exemple, voici un lien vers la documentation relative au [contrôle des limites](../features/ux-building-blocks/bounds-control.md) .</span><span class="sxs-lookup"><span data-stu-id="2e06e-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="2e06e-185">Mettez les noms en majuscules, par exemple *Unity*.</span><span class="sxs-lookup"><span data-stu-id="2e06e-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="2e06e-186">Ne pas mettre en majuscules « éditeur » lors de l’écriture de l' *éditeur Unity*.</span><span class="sxs-lookup"><span data-stu-id="2e06e-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="2e06e-187">Mise en évidence et mise en surbrillance</span><span class="sxs-lookup"><span data-stu-id="2e06e-187">Emphasis and highlighting</span></span>

<span data-ttu-id="2e06e-188">Il existe deux façons de mettre en évidence ou de mettre en évidence des mots, de les mettre en gras ou de les mettre en italique.</span><span class="sxs-lookup"><span data-stu-id="2e06e-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="2e06e-189">Le texte en gras a pour effet que le **texte en gras** s’affiche et, par conséquent, peut être facilement remarqué tout en superposant un morceau de texte ou même simplement en faisant défiler une page.</span><span class="sxs-lookup"><span data-stu-id="2e06e-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="2e06e-190">Le gras est parfait pour mettre en évidence les expressions que les gens doivent mémoriser.</span><span class="sxs-lookup"><span data-stu-id="2e06e-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="2e06e-191">Toutefois, **utilisez rarement du texte en gras**, car il est généralement gênant.</span><span class="sxs-lookup"><span data-stu-id="2e06e-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="2e06e-192">Il est souvent nécessaire de regrouper un objet qui appartient logiquement ou de mettre en surbrillance un terme spécifique, car il a une signification particulière.</span><span class="sxs-lookup"><span data-stu-id="2e06e-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="2e06e-193">Ces éléments n’ont pas besoin de sortir du texte global.</span><span class="sxs-lookup"><span data-stu-id="2e06e-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="2e06e-194">Utilisez du texte en italique comme *méthode légère* pour mettre en surbrillance un événement.</span><span class="sxs-lookup"><span data-stu-id="2e06e-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="2e06e-195">De même, lorsqu’un nom de fichier, un chemin d’accès ou une entrée de menu est mentionné dans le texte, préférez le rendre italique pour le regrouper logiquement, sans gêner l’opération.</span><span class="sxs-lookup"><span data-stu-id="2e06e-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="2e06e-196">En général, essayez d' **éviter la mise en surbrillance du texte inutile**.</span><span class="sxs-lookup"><span data-stu-id="2e06e-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="2e06e-197">Les termes spéciaux peuvent être mis en surbrillance une seule fois pour que le lecteur puisse les prendre en compte, ne pas répéter la mise en surbrillance dans tout le texte, lorsqu’il n’a plus besoin d’être utilisé et qu’il ne fait que</span><span class="sxs-lookup"><span data-stu-id="2e06e-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="2e06e-198">Mention des entrées de menu</span><span class="sxs-lookup"><span data-stu-id="2e06e-198">Mentioning menu entries</span></span>

<span data-ttu-id="2e06e-199">quand vous mentionnez une entrée de menu qu’un utilisateur doit cliquer, la convention actuelle est la suivante : *Project > des fichiers > créer une feuille de >*</span><span class="sxs-lookup"><span data-stu-id="2e06e-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="2e06e-200">Liens</span><span class="sxs-lookup"><span data-stu-id="2e06e-200">Links</span></span>

<span data-ttu-id="2e06e-201">Insérez autant de liens utiles à d’autres pages que possible, mais chaque lien une seule fois.</span><span class="sxs-lookup"><span data-stu-id="2e06e-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="2e06e-202">Supposons qu’un lecteur clique sur chaque lien de la page et réfléchisse à la gêne qu’il aurait, si la même page s’ouvre 20 fois.</span><span class="sxs-lookup"><span data-stu-id="2e06e-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="2e06e-203">Préférer les liens incorporés dans une phrase :</span><span class="sxs-lookup"><span data-stu-id="2e06e-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="2e06e-204">Incorrect : les indications sont utiles.</span><span class="sxs-lookup"><span data-stu-id="2e06e-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="2e06e-205">Pour plus d’informations, consultez [ce chapitre](../contributing/documentation-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="2e06e-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="2e06e-206">BONNE : [les indications](documentation-guide.md) sont utiles.</span><span class="sxs-lookup"><span data-stu-id="2e06e-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="2e06e-207">Évitez les liens externes, ils peuvent devenir obsolètes ou contenir du contenu protégé par des droits d’auteur.</span><span class="sxs-lookup"><span data-stu-id="2e06e-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="2e06e-208">Lorsque vous ajoutez un lien, déterminez s’il doit également être listé dans la section [Voir aussi](#see-also) .</span><span class="sxs-lookup"><span data-stu-id="2e06e-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="2e06e-209">De même, vérifiez si un lien vers la nouvelle page doit être ajouté à la page liée.</span><span class="sxs-lookup"><span data-stu-id="2e06e-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="2e06e-210">Images/captures d’écran</span><span class="sxs-lookup"><span data-stu-id="2e06e-210">Images / screenshots</span></span>

<span data-ttu-id="2e06e-211">**Utilisez des captures d’écran avec modération.**</span><span class="sxs-lookup"><span data-stu-id="2e06e-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="2e06e-212">La gestion des images dans la documentation est beaucoup de travail, les petites modifications de l’interface utilisateur peuvent faire échouer de nombreuses captures d’écran.</span><span class="sxs-lookup"><span data-stu-id="2e06e-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="2e06e-213">Les règles suivantes réduisent les tâches de maintenance :</span><span class="sxs-lookup"><span data-stu-id="2e06e-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="2e06e-214">N’utilisez pas de captures d’écran pour les éléments qui peuvent être décrits dans le texte.</span><span class="sxs-lookup"><span data-stu-id="2e06e-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="2e06e-215">En particulier, n’encadrez **jamais une grille des propriétés** dans le seul but d’illustrer les noms et les valeurs des propriétés.</span><span class="sxs-lookup"><span data-stu-id="2e06e-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="2e06e-216">N’incluez pas dans une capture d’écran des éléments qui ne sont pas pertinents à ce qui est affiché.</span><span class="sxs-lookup"><span data-stu-id="2e06e-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="2e06e-217">Par exemple, lorsqu’un effet de rendu est affiché, effectuez une capture d’écran de la fenêtre d’affichage, mais excluez toute interface utilisateur autour de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="2e06e-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="2e06e-218">En présentant une certaine interface utilisateur, essayez de déplacer des fenêtres autour de ce que seule cette partie importante se trouve dans l’image.</span><span class="sxs-lookup"><span data-stu-id="2e06e-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="2e06e-219">Lorsque vous incluez l’interface utilisateur de capture d’écran, Affichez uniquement les parties importantes.</span><span class="sxs-lookup"><span data-stu-id="2e06e-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="2e06e-220">Par exemple, lorsque vous parlez de boutons dans une barre d’outils, créez une petite image qui affiche les boutons de barre d’outils importants, mais excluez tout autour de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="2e06e-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="2e06e-221">Utilisez uniquement des images faciles à reproduire.</span><span class="sxs-lookup"><span data-stu-id="2e06e-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="2e06e-222">Cela signifie que vous ne dessinez pas de marqueurs ou de surbrillance dans des captures d’écran.</span><span class="sxs-lookup"><span data-stu-id="2e06e-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="2e06e-223">Tout d’abord, il n’y a pas de règles cohérentes quant à la façon dont elles doivent s’afficher.</span><span class="sxs-lookup"><span data-stu-id="2e06e-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="2e06e-224">Deuxièmement, la reproduction d’une telle capture d’écran est un effort supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="2e06e-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="2e06e-225">Au lieu de cela, décrivez les parties importantes du texte.</span><span class="sxs-lookup"><span data-stu-id="2e06e-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="2e06e-226">Il existe des exceptions à cette règle, mais elles sont rares.</span><span class="sxs-lookup"><span data-stu-id="2e06e-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="2e06e-227">Évidemment, il est bien plus facile de recréer une image GIF animée.</span><span class="sxs-lookup"><span data-stu-id="2e06e-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="2e06e-228">Attendez-vous à la recréer jusqu’à la fin de l’heure, ou attendez-vous à ce que les gens la lèvent, s’ils ne souhaitent pas passer ce temps.</span><span class="sxs-lookup"><span data-stu-id="2e06e-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="2e06e-229">Laissez le nombre d’images dans un article faible.</span><span class="sxs-lookup"><span data-stu-id="2e06e-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="2e06e-230">Souvent, une bonne méthode consiste à créer une capture d’écran globale d’un outil, qui affiche tout, puis à décrire le reste dans le texte.</span><span class="sxs-lookup"><span data-stu-id="2e06e-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="2e06e-231">Cela facilite le remplacement de la capture d’écran si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2e06e-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="2e06e-232">Autres aspects :</span><span class="sxs-lookup"><span data-stu-id="2e06e-232">Some other aspects:</span></span>

- <span data-ttu-id="2e06e-233">L’interface utilisateur de l’éditeur pour les captures d’écran doit utiliser l’éditeur de thème gris clair, car tous les utilisateurs n’ont pas accès au thème sombre et nous aimerions que les choses restent aussi cohérentes que possible.</span><span class="sxs-lookup"><span data-stu-id="2e06e-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="2e06e-234">La largeur de l’image par défaut est de 500 pixels, car elle s’affiche bien sur la plupart des analyses.</span><span class="sxs-lookup"><span data-stu-id="2e06e-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="2e06e-235">Essayez de ne pas en faire un trop grand nombre.</span><span class="sxs-lookup"><span data-stu-id="2e06e-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="2e06e-236">la largeur de 800 pixels doit être la valeur maximale.</span><span class="sxs-lookup"><span data-stu-id="2e06e-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="2e06e-237">Utilisez les png pour les captures d’écran de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2e06e-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="2e06e-238">Utilisez des captures d’écran pour la fenêtre d’affichage 3D : png ou JPGs.</span><span class="sxs-lookup"><span data-stu-id="2e06e-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="2e06e-239">Privilégier la qualité par rapport à la compression.</span><span class="sxs-lookup"><span data-stu-id="2e06e-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="2e06e-240">Liste des propriétés du composant</span><span class="sxs-lookup"><span data-stu-id="2e06e-240">List of component properties</span></span>

<span data-ttu-id="2e06e-241">Quand vous documentez une liste de propriétés, utilisez le texte en gras pour mettre en surbrillance le nom de la propriété, puis les sauts de ligne et le texte normal pour les décrire.</span><span class="sxs-lookup"><span data-stu-id="2e06e-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="2e06e-242">N’utilisez pas de sous-chapitres ou de listes à puces.</span><span class="sxs-lookup"><span data-stu-id="2e06e-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="2e06e-243">En outre, n’oubliez pas de terminer toutes les phrases avec un point.</span><span class="sxs-lookup"><span data-stu-id="2e06e-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="2e06e-244">Liste de vérification de l’exécution de la page</span><span class="sxs-lookup"><span data-stu-id="2e06e-244">Page completion checklist</span></span>

1. <span data-ttu-id="2e06e-245">Vérifiez que les instructions de ce document ont été suivies.</span><span class="sxs-lookup"><span data-stu-id="2e06e-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="2e06e-246">Parcourez la structure du document et regardez si le nouveau document peut être mentionné sous la section [Voir aussi](#see-also) d’autres pages.</span><span class="sxs-lookup"><span data-stu-id="2e06e-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="2e06e-247">Si elle est disponible, ayez une personne ayant connaissance de la rubrique preuve de l’exactitude technique pour obtenir de l’aide.</span><span class="sxs-lookup"><span data-stu-id="2e06e-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="2e06e-248">Demander à quelqu’un de lire la page pour le style et la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="2e06e-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="2e06e-249">Il peut s’agir d’une personne ne connaissant pas la rubrique, qui est également une bonne idée d’obtenir des commentaires sur la compréhension de la documentation.</span><span class="sxs-lookup"><span data-stu-id="2e06e-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="2e06e-250">Documentation source</span><span class="sxs-lookup"><span data-stu-id="2e06e-250">Source documentation</span></span>

<span data-ttu-id="2e06e-251">La documentation de l’API sera générée automatiquement à partir des fichiers sources MRTK.</span><span class="sxs-lookup"><span data-stu-id="2e06e-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="2e06e-252">Pour faciliter cette tâche, les fichiers sources doivent contenir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2e06e-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="2e06e-253">Blocs de résumé de classe, de structure et d’énumération</span><span class="sxs-lookup"><span data-stu-id="2e06e-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="2e06e-254">Propriétés, méthodes, blocs de synthèse d’événements</span><span class="sxs-lookup"><span data-stu-id="2e06e-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="2e06e-255">Version d’introduction des fonctionnalités et dépendances</span><span class="sxs-lookup"><span data-stu-id="2e06e-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="2e06e-256">Champs sérialisés</span><span class="sxs-lookup"><span data-stu-id="2e06e-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="2e06e-257">Valeurs d’énumération</span><span class="sxs-lookup"><span data-stu-id="2e06e-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="2e06e-258">Outre les éléments ci-dessus, le code doit être correctement mis en commentaire pour permettre la maintenance, les correctifs de bogues et la facilité de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="2e06e-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="2e06e-259">Blocs de résumé de classe, de structure et d’énumération</span><span class="sxs-lookup"><span data-stu-id="2e06e-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="2e06e-260">Si une classe, un struct ou un enum est ajouté à MRTK, son objectif doit être décrit.</span><span class="sxs-lookup"><span data-stu-id="2e06e-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="2e06e-261">Cela permet de prendre la forme d’un bloc de résumé au-dessus de la classe.</span><span class="sxs-lookup"><span data-stu-id="2e06e-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="2e06e-262">S’il existe des dépendances au niveau de la classe, elles doivent être documentées dans un bloc notes, immédiatement sous le résumé.</span><span class="sxs-lookup"><span data-stu-id="2e06e-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="2e06e-263">Les requêtes de tirage soumises sans synthèses pour les classes, structures ou énumérations ne sont pas approuvées.</span><span class="sxs-lookup"><span data-stu-id="2e06e-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="2e06e-264">Propriétés, méthodes, blocs de synthèse d’événements</span><span class="sxs-lookup"><span data-stu-id="2e06e-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="2e06e-265">Les propriétés, les méthodes et les événements (PMEs) ainsi que les champs doivent être documentés avec des blocs de synthèse, quelle que soit la visibilité du code (public, privé, protégé et interne).</span><span class="sxs-lookup"><span data-stu-id="2e06e-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="2e06e-266">L’outil de génération de documentation est responsable du filtrage et de la publication des fonctionnalités publiques et protégées uniquement.</span><span class="sxs-lookup"><span data-stu-id="2e06e-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="2e06e-267">Remarque : un bloc de résumé n’est **pas** requis pour les méthodes Unity (par exemple, éveillé, Start, Update).</span><span class="sxs-lookup"><span data-stu-id="2e06e-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="2e06e-268">La documentation PME est **requise** pour l’approbation d’une demande de tirage (pull request).</span><span class="sxs-lookup"><span data-stu-id="2e06e-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="2e06e-269">Dans le cadre d’un bloc de résumé des PME, le sens et l’objectif des paramètres et des données retournées sont requis.</span><span class="sxs-lookup"><span data-stu-id="2e06e-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="2e06e-270">Version d’introduction des fonctionnalités et dépendances</span><span class="sxs-lookup"><span data-stu-id="2e06e-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="2e06e-271">Dans le cadre de la documentation Résumé de l’API, vous trouverez des informations sur la version de MRTK dans laquelle la fonctionnalité a été introduite et toutes les dépendances doivent être documentées dans un bloc notes.</span><span class="sxs-lookup"><span data-stu-id="2e06e-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="2e06e-272">Les dépendances doivent inclure des dépendances d’extension et/ou de plateforme.</span><span class="sxs-lookup"><span data-stu-id="2e06e-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="2e06e-273">Champs sérialisés</span><span class="sxs-lookup"><span data-stu-id="2e06e-273">Serialized fields</span></span>

<span data-ttu-id="2e06e-274">Il est recommandé d’utiliser l’attribut ToolTip de Unity pour fournir une documentation d’exécution pour les champs d’un script dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="2e06e-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="2e06e-275">Afin que les options de configuration soient incluses dans la documentation de l’API, les scripts sont requis pour inclure *au moins* le contenu de l’info-bulle dans un bloc de résumé.</span><span class="sxs-lookup"><span data-stu-id="2e06e-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="2e06e-276">Valeurs d’énumération</span><span class="sxs-lookup"><span data-stu-id="2e06e-276">Enumeration values</span></span>

<span data-ttu-id="2e06e-277">Lors de la définition et de l’énumération, le code doit également documenter la signification des valeurs enum à l’aide d’un bloc Summary.</span><span class="sxs-lookup"><span data-stu-id="2e06e-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="2e06e-278">Les blocs notes peuvent éventuellement être utilisés pour fournir des détails supplémentaires afin d’améliorer la compréhension.</span><span class="sxs-lookup"><span data-stu-id="2e06e-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="2e06e-279">Documentation de procédures</span><span class="sxs-lookup"><span data-stu-id="2e06e-279">How-to documentation</span></span>

<span data-ttu-id="2e06e-280">de nombreux utilisateurs du Shared Computer Toolkit de la réalité mixte n’ont peut-être pas besoin d’utiliser la documentation de l’API.</span><span class="sxs-lookup"><span data-stu-id="2e06e-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="2e06e-281">Ces utilisateurs tirent parti de nos prefabs et scripts prédéfinis et réutilisables pour créer leurs expériences.</span><span class="sxs-lookup"><span data-stu-id="2e06e-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="2e06e-282">Chaque domaine de fonctionnalité contient un ou plusieurs fichiers de démarque (. MD) qui décrivent un niveau relativement élevé, ce qui est fourni.</span><span class="sxs-lookup"><span data-stu-id="2e06e-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="2e06e-283">En fonction de la taille et/ou de la complexité d’un domaine de fonctionnalité donné, il peut être nécessaire de disposer de fichiers supplémentaires, jusqu’à un par fonctionnalité fournie.</span><span class="sxs-lookup"><span data-stu-id="2e06e-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="2e06e-284">Quand une fonctionnalité est ajoutée (ou que l’utilisation est modifiée), vous devez fournir une documentation de vue d’ensemble.</span><span class="sxs-lookup"><span data-stu-id="2e06e-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="2e06e-285">Dans le cadre de cette documentation, des sections de procédures, y compris des illustrations, doivent être fournies pour aider les clients à découvrir une fonctionnalité ou un concept dans la prise en main.</span><span class="sxs-lookup"><span data-stu-id="2e06e-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="2e06e-286">Documentation de conception</span><span class="sxs-lookup"><span data-stu-id="2e06e-286">Design documentation</span></span>

<span data-ttu-id="2e06e-287">La réalité mixte offre la possibilité de créer des mondes entièrement nouveaux.</span><span class="sxs-lookup"><span data-stu-id="2e06e-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="2e06e-288">Une partie de cette fonction est susceptible d’impliquer la création de ressources personnalisées à utiliser avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="2e06e-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="2e06e-289">Pour que cela soit aussi gratuit que possible pour les clients, les composants doivent fournir une documentation de conception décrivant les mises en forme ou autres exigences relatives aux ressources artistiques.</span><span class="sxs-lookup"><span data-stu-id="2e06e-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="2e06e-290">Voici quelques exemples où la documentation de conception peut être utile :</span><span class="sxs-lookup"><span data-stu-id="2e06e-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="2e06e-291">Modèles de curseur</span><span class="sxs-lookup"><span data-stu-id="2e06e-291">Cursor models</span></span>
- <span data-ttu-id="2e06e-292">Visualisations de mappages spatiaux</span><span class="sxs-lookup"><span data-stu-id="2e06e-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="2e06e-293">Fichiers d’effet audio</span><span class="sxs-lookup"><span data-stu-id="2e06e-293">Sound effect files</span></span>

<span data-ttu-id="2e06e-294">Ce type de documentation est **fortement** recommandé et **peut** être demandé dans le cadre de la révision d’une demande de tirage (pull request).</span><span class="sxs-lookup"><span data-stu-id="2e06e-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="2e06e-295">Cela peut être différent de la recommandation de conception sur le site de [développement MS](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="2e06e-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="2e06e-296">Remarques sur les performances</span><span class="sxs-lookup"><span data-stu-id="2e06e-296">Performance notes</span></span>

<span data-ttu-id="2e06e-297">Certaines fonctionnalités importantes sont coûteuses en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="2e06e-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="2e06e-298">Ce code dépend souvent de la façon dont il est configuré.</span><span class="sxs-lookup"><span data-stu-id="2e06e-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="2e06e-299">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2e06e-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="2e06e-300">Les remarques sur les performances sont recommandées pour les composants lourds UC et/ou GPU et **peuvent** être demandées dans le cadre d’une révision de demande de tirage.</span><span class="sxs-lookup"><span data-stu-id="2e06e-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="2e06e-301">Toutes les notes de performance applicables doivent être incluses dans la documentation de l’API **et** de la présentation.</span><span class="sxs-lookup"><span data-stu-id="2e06e-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="2e06e-302">Changements cassants</span><span class="sxs-lookup"><span data-stu-id="2e06e-302">Breaking changes</span></span>

<span data-ttu-id="2e06e-303">La documentation sur les modifications importantes consiste à se composer d’un [fichier](../contributing/breaking-changes.md) de niveau supérieur qui établit des liens vers les Breaking-Changes.MD individuels de chaque domaine de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="2e06e-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="2e06e-304">Les fichiers breaking-changes.md de la zone de fonctionnalités doivent contenir la liste de toutes les modifications avec rupture connues pour une version donnée **, ainsi que** l’historique des modifications importantes par rapport aux versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="2e06e-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="2e06e-305">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2e06e-305">For example:</span></span>

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

<span data-ttu-id="2e06e-306">Les informations contenues dans les fichiers breaking-changes.md au niveau de la fonctionnalité seront regroupées dans les notes de publication de chaque nouvelle version de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2e06e-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="2e06e-307">Toute modification avec rupture qui fait partie d’une modification **doit** être documentée dans le cadre d’une demande de tirage (pull request).</span><span class="sxs-lookup"><span data-stu-id="2e06e-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="2e06e-308">Outils pour la modification de la démarque</span><span class="sxs-lookup"><span data-stu-id="2e06e-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="2e06e-309">[Visual Studio Code](https://code.visualstudio.com/) est un outil formidable pour la modification des fichiers de démarque qui font partie de la documentation de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2e06e-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="2e06e-310">Lors de l’écriture de la documentation, l’installation des deux extensions suivantes est également fortement recommandée :</span><span class="sxs-lookup"><span data-stu-id="2e06e-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="2e06e-311">Extension docs de la démarque pour Visual Studio Code-utilisez Alt + M pour afficher un menu d’options de création de documents.</span><span class="sxs-lookup"><span data-stu-id="2e06e-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="2e06e-312">Vérificateur orthographique de code : les mots mal orthographiés sont soulignés. Cliquez avec le bouton droit sur un mot mal orthographié pour le modifier ou enregistrez-le dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="2e06e-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="2e06e-313">Ces deux packages sont fournis dans le Pack de création docs publié de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2e06e-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e06e-314">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e06e-314">See also</span></span>

- [<span data-ttu-id="2e06e-315">Exemple de lien « Voir aussi » pour la documentation</span><span class="sxs-lookup"><span data-stu-id="2e06e-315">Example "see also" link for documentation</span></span>](https://www.microsoft.com)
