---
title: Langage principal
description: En savoir plus sur les détails du langage de base de maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935540"
---
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="70c90-104">Détails du langage de base MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="70c90-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="70c90-105">![Maquette logo ](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span><span class="sxs-lookup"><span data-stu-id="70c90-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="70c90-106">Accès à l' `Maquette` objet et à l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="70c90-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="70c90-107">Maquette expose les interfaces et les objets internes dans JavaScript par le biais de l' `Maquette` objet et de ses enfants.</span><span class="sxs-lookup"><span data-stu-id="70c90-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="70c90-108">Cette fonctionnalité est décrite dans la documentation relative à l' [objet maquette et](https://www.maquette.ms/doc_staging/objects/Maquette.html) à l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="70c90-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="70c90-109">L' `Maquette` objet a des fonctions de niveau supérieur pour faciliter l’interaction avec maquette lui-même et faciliter la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="70c90-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="70c90-110">Cela est décrit dans la documentation de [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span><span class="sxs-lookup"><span data-stu-id="70c90-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="70c90-111">Démarrage et chargement de maquette</span><span class="sxs-lookup"><span data-stu-id="70c90-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="70c90-112">Maquette charge et évalue des fichiers JavaScript spécifiques pour activer la configuration, l’installation et l’initialisation aux moments suivants :</span><span class="sxs-lookup"><span data-stu-id="70c90-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="70c90-113">Lors du démarrage de maquette :</span><span class="sxs-lookup"><span data-stu-id="70c90-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="70c90-114">Chaque fois qu’un projet est chargé :</span><span class="sxs-lookup"><span data-stu-id="70c90-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="70c90-115">Les projets chargent leurs scripts de projet respectifs :</span><span class="sxs-lookup"><span data-stu-id="70c90-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="70c90-116">Implémentation JavaScript</span><span class="sxs-lookup"><span data-stu-id="70c90-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="70c90-117">L’interpréteur JavaScript utilisé dans maquette est basé sur [JINT](https://github.com/sebastienros/jint).</span><span class="sxs-lookup"><span data-stu-id="70c90-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="70c90-118">JINT est compatible ECMAScript 5,1 et prend en charge des [extensions supplémentaires d’ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span><span class="sxs-lookup"><span data-stu-id="70c90-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="70c90-119">L’extension `.mqjs` est utilisée pour distinguer les fichiers JavaScript maquette du code JavaScript normal.</span><span class="sxs-lookup"><span data-stu-id="70c90-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="70c90-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70c90-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->