---
title: Pointer du regard et valider
description: En savoir plus sur le modèle d’entrée de pointage et de validation, y compris deux types de point de regard (pointer vers l’œil et le point de regard) et divers types de validation.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: La réalité mixte, le regard, le regard, l’interaction, la conception, le suivi des yeux, le suivi des têtes, le casque de réalité mixte, le casque Windows Mixed Reality, le casque de réalité virtuelle, HoloLens, MRTK et la réalité mixte Toolkit
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196564"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="4afbc-104">Pointer du regard et valider</span><span class="sxs-lookup"><span data-stu-id="4afbc-104">Gaze and commit</span></span>

<span data-ttu-id="4afbc-105">Le point de vue du _regard et_ de la validation est un modèle d’entrée fondamental qui est étroitement lié à la façon dont nous interagissons avec nos ordinateurs à l’aide de la souris : _point & cliquez_.</span><span class="sxs-lookup"><span data-stu-id="4afbc-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="4afbc-106">Sur cette page, nous présentons deux types d’entrées de regard (pointer et Eye-regard) et différents types d’actions de validation.</span><span class="sxs-lookup"><span data-stu-id="4afbc-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="4afbc-107">Le point de _regard et la validation_ sont considérés comme un modèle d’entrée lointain avec manipulation indirecte.</span><span class="sxs-lookup"><span data-stu-id="4afbc-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="4afbc-108">Il est préférable d’utiliser le contenu holographique qui n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="4afbc-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="4afbc-109">Les casques de réalité mixte peuvent utiliser la position et l’orientation de la tête de l’utilisateur pour déterminer le vecteur de direction de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="4afbc-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="4afbc-110">Considérez le point de regard comme un laser qui pointe directement vers l’avant entre les yeux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4afbc-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="4afbc-111">C’est une approximation assez grossière de la zone vers laquelle se porte le regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4afbc-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="4afbc-112">Votre application peut croiser ce rayon avec des objets virtuels ou réels, et dessiner un curseur à cet emplacement pour permettre à l’utilisateur de savoir ce qu’il cible.</span><span class="sxs-lookup"><span data-stu-id="4afbc-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="4afbc-113">En plus de la tête de regard, certains casques de réalité mixte, tels que HoloLens 2, incluent des systèmes de suivi oculaire qui produisent un vecteur point-Orient.</span><span class="sxs-lookup"><span data-stu-id="4afbc-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="4afbc-114">Ces dispositifs fournissent une mesure précise de la zone vers laquelle se porte le regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4afbc-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="4afbc-115">Dans les deux cas, le point de regard représente un signal important pour l’intention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4afbc-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="4afbc-116">Mieux le système peut interpréter et prédire les actions prévues de l’utilisateur, plus la satisfaction des utilisateurs et les performances sont améliorées.</span><span class="sxs-lookup"><span data-stu-id="4afbc-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="4afbc-117">Voici quelques exemples de la façon dont vous êtes un développeur de réalité mixte qui peut tirer parti de la tête ou du regard :</span><span class="sxs-lookup"><span data-stu-id="4afbc-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="4afbc-118">Votre application peut faire une intersection avec le regard des hologrammes dans votre scène pour déterminer où l’attention de l’utilisateur est (plus précise avec le regard de l’oeil).</span><span class="sxs-lookup"><span data-stu-id="4afbc-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="4afbc-119">Votre application peut canaliser les gestes et les presses des contrôleurs en fonction du point de regard de l’utilisateur, ce qui permet à l’utilisateur de sélectionner, d’activer, de saisir, de faire défiler ou d’interagir de manière transparente avec ses hologrammes.</span><span class="sxs-lookup"><span data-stu-id="4afbc-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="4afbc-120">Votre application peut permettre à l’utilisateur de placer des hologrammes sur des surfaces réelles en croisant leur rayon de regard avec le maillage de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="4afbc-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="4afbc-121">Votre application peut savoir quand l’utilisateur n’est pas dans la direction d’un objet important, ce qui peut amener votre application à donner des signaux visuels et audio pour tourner vers cet objet.</span><span class="sxs-lookup"><span data-stu-id="4afbc-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="4afbc-122">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="4afbc-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4afbc-123"><strong>Modèle d’entrée</strong></span><span class="sxs-lookup"><span data-stu-id="4afbc-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="4afbc-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="4afbc-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="4afbc-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="4afbc-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="4afbc-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="4afbc-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4afbc-127">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="4afbc-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="4afbc-128">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="4afbc-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="4afbc-129">✔️ Recommandé (troisième choix ; <a href="interaction-fundamentals.md">voir les autres options</a>)</span><span class="sxs-lookup"><span data-stu-id="4afbc-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="4afbc-130">➕ Autre option</span><span class="sxs-lookup"><span data-stu-id="4afbc-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="4afbc-131">Suivre du regard et valider</span><span class="sxs-lookup"><span data-stu-id="4afbc-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="4afbc-132">❌ Non disponible</span><span class="sxs-lookup"><span data-stu-id="4afbc-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="4afbc-133">✔️ Recommandé (troisième choix ; <a href="interaction-fundamentals.md">voir les autres options</a>)</span><span class="sxs-lookup"><span data-stu-id="4afbc-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="4afbc-134">❌ Non disponible</span><span class="sxs-lookup"><span data-stu-id="4afbc-134">❌ Not available</span></span></td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="4afbc-135">Démonstration des concepts de conception du suivi des têtes et des yeux</span><span class="sxs-lookup"><span data-stu-id="4afbc-135">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="4afbc-136">Si vous souhaitez voir les concepts de conception des suivis des yeux et des yeux en action, consultez notre démonstration **conception d’hologrammes-TETE Tracking and Eye Tracking (** en anglais) ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="4afbc-136">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="4afbc-137">Une fois que vous avez terminé, poursuivez sur pour obtenir une présentation plus détaillée des rubriques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4afbc-137">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="4afbc-138">*Cette vidéo a été extraite de l’application HoloLens 2 « Designing hologrammes ». Téléchargez et profitez de l’expérience complète [ici](https://aka.ms/dhapp).*</span><span class="sxs-lookup"><span data-stu-id="4afbc-138">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="gaze"></a><span data-ttu-id="4afbc-139">Pointage du regard</span><span class="sxs-lookup"><span data-stu-id="4afbc-139">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="4afbc-140">Le regard de l’œil ou de la tête ?</span><span class="sxs-lookup"><span data-stu-id="4afbc-140">Eye- or head-gaze?</span></span>
<span data-ttu-id="4afbc-141">Il y a plusieurs points à prendre en compte lorsque vous êtes confronté à la question de savoir si vous devez utiliser le modèle d’entrée « Eye-regard and Commit » ou « Head-pointage and commit ».</span><span class="sxs-lookup"><span data-stu-id="4afbc-141">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="4afbc-142">Si vous développez pour un casque immersif ou pour HoloLens (1re génération), le choix est simple : début et validation.</span><span class="sxs-lookup"><span data-stu-id="4afbc-142">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="4afbc-143">Si vous développez pour HoloLens 2, le choix devient un peu plus difficile.</span><span class="sxs-lookup"><span data-stu-id="4afbc-143">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="4afbc-144">Il est important de comprendre les avantages et les défis inhérents à chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="4afbc-144">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="4afbc-145">Nous avons compilé un grand nombre de professionnels et de conversions dans le tableau ci-dessous pour contraster en tête et en regard.</span><span class="sxs-lookup"><span data-stu-id="4afbc-145">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="4afbc-146">Ceci est loin d’être terminé et nous vous suggérons d’en apprendre davantage sur le ciblage des regards dans la réalité mixte ici :</span><span class="sxs-lookup"><span data-stu-id="4afbc-146">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="4afbc-147">[Suivi oculaire sur hololens 2](eye-tracking.md): présentation générale de notre nouvelle fonctionnalité de suivi oculaire sur hololens 2, avec quelques conseils pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="4afbc-147">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="4afbc-148">[Œil-regard](eye-gaze-interaction.md): considérations de conception et recommandations lors de la planification de l’utilisation du suivi oculaire comme entrée.</span><span class="sxs-lookup"><span data-stu-id="4afbc-148">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="4afbc-149"><strong>Regard sur les yeux</strong></span><span class="sxs-lookup"><span data-stu-id="4afbc-149"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="4afbc-150"><strong>Ciblage avec la tête</strong></span><span class="sxs-lookup"><span data-stu-id="4afbc-150"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4afbc-151">Expédition!</span><span class="sxs-lookup"><span data-stu-id="4afbc-151">Fast!</span></span></td>
        <td><span data-ttu-id="4afbc-152">Élevé</span><span class="sxs-lookup"><span data-stu-id="4afbc-152">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4afbc-153">Faible effort (à peine les mouvements de corps nécessaires)</span><span class="sxs-lookup"><span data-stu-id="4afbc-153">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="4afbc-154">Peut être fatiguing-une gêne possible (par exemple, une fatigue du cou)</span><span class="sxs-lookup"><span data-stu-id="4afbc-154">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4afbc-155">N’a pas besoin d’un curseur, mais les commentaires subtils sont recommandés</span><span class="sxs-lookup"><span data-stu-id="4afbc-155">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="4afbc-156">Requiert l’affichage d’un curseur</span><span class="sxs-lookup"><span data-stu-id="4afbc-156">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4afbc-157">Pas de mouvements d’œil lisses, par exemple, pas bon pour le dessin</span><span class="sxs-lookup"><span data-stu-id="4afbc-157">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="4afbc-158">Plus contrôlé et plus explicite</span><span class="sxs-lookup"><span data-stu-id="4afbc-158">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4afbc-159">Difficile pour les petites cibles (par exemple, les petits boutons ou les liens de connexion à des Webliens)</span><span class="sxs-lookup"><span data-stu-id="4afbc-159">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="4afbc-160">Fidèles!</span><span class="sxs-lookup"><span data-stu-id="4afbc-160">Reliable!</span></span> <span data-ttu-id="4afbc-161">Parfait !</span><span class="sxs-lookup"><span data-stu-id="4afbc-161">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4afbc-162">...</span><span class="sxs-lookup"><span data-stu-id="4afbc-162">...</span></span></td>
        <td><span data-ttu-id="4afbc-163">...</span><span class="sxs-lookup"><span data-stu-id="4afbc-163">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="4afbc-164">Que vous utilisiez un point de regard ou un regard pour votre modèle d’entrée de point de présence et de validation, chacun d’entre eux est accompagné de différents ensembles de contraintes de conception.</span><span class="sxs-lookup"><span data-stu-id="4afbc-164">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="4afbc-165">Celles-ci sont couvertes séparément dans les Articles de regard et de [validation](gaze-and-commit-eyes.md) et de [point](gaze-and-commit-head.md) de regard.</span><span class="sxs-lookup"><span data-stu-id="4afbc-165">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="4afbc-166">Curseur</span><span class="sxs-lookup"><span data-stu-id="4afbc-166">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="4afbc-167">Pour le point de vue de la tête, la plupart des applications doivent utiliser un [curseur](cursors.md) ou une autre indication d’audit/visuel pour donner à l’utilisateur la confiance dans ce qu’ils sont sur le point d’interagir.</span><span class="sxs-lookup"><span data-stu-id="4afbc-167">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="4afbc-168">En règle générale, vous positionnez ce curseur dans le monde où le rayon de regard de son en-tête croise d’abord un objet, qui peut être un hologramme ou une surface réaliste.</span><span class="sxs-lookup"><span data-stu-id="4afbc-168">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="4afbc-169">Pour les yeux oculaires, nous vous recommandons généralement de *ne pas* afficher de curseur, car cela peut rapidement devenir gênant et ennuyeux pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4afbc-169">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="4afbc-170">À la place, mettez en surbrillance les cibles visuelles ou utilisez un curseur flou pour faire confiance à ce que l’utilisateur est sur le point d’interagir.</span><span class="sxs-lookup"><span data-stu-id="4afbc-170">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="4afbc-171">Pour plus d’informations, consultez notre [Guide de conception pour une entrée basée](eye-tracking.md) sur l’œil sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4afbc-171">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="4afbc-172">![Exemple de curseur visuel pour afficher le regard](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="4afbc-172">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="4afbc-173">*Image : un exemple de curseur visuel pour afficher le regard*</span><span class="sxs-lookup"><span data-stu-id="4afbc-173">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="4afbc-174">Commit</span><span class="sxs-lookup"><span data-stu-id="4afbc-174">Commit</span></span>
<span data-ttu-id="4afbc-175">Après avoir parlé des différentes façons de pointer vers une cible, nous _allons en parler_ plus sur la partie _validation_ dans le point de vue _et la validation_.</span><span class="sxs-lookup"><span data-stu-id="4afbc-175">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="4afbc-176">Après avoir ciblé un objet ou un élément d’interface utilisateur, l’utilisateur peut interagir ou cliquer dessus à l’aide d’une entrée secondaire.</span><span class="sxs-lookup"><span data-stu-id="4afbc-176">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="4afbc-177">C’est ce que l’on appelle l’étape de validation du modèle d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4afbc-177">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="4afbc-178">Les méthodes de validation suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="4afbc-178">The following commit methods are supported:</span></span>
- <span data-ttu-id="4afbc-179">Mouvement d’appui sur air (autrement dit, soulevez votre main et regroupez le doigt et le curseur de votre index)</span><span class="sxs-lookup"><span data-stu-id="4afbc-179">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="4afbc-180">Dites _« Sélectionner »_ ou l’une des commandes vocales ciblées</span><span class="sxs-lookup"><span data-stu-id="4afbc-180">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="4afbc-181">Appuyer sur un bouton unique sur un [Clicker HoloLens](/hololens/hololens1-clicker)</span><span class="sxs-lookup"><span data-stu-id="4afbc-181">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="4afbc-182">Appuyez sur le bouton « A » sur un boîtier de manette Xbox</span><span class="sxs-lookup"><span data-stu-id="4afbc-182">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="4afbc-183">Appuyez sur le bouton « A » sur un contrôleur d’adaptateur Xbox</span><span class="sxs-lookup"><span data-stu-id="4afbc-183">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="4afbc-184">Mouvement du toucher et de l’air</span><span class="sxs-lookup"><span data-stu-id="4afbc-184">Gaze and air tap gesture</span></span>
<span data-ttu-id="4afbc-185">Le clic aérien est une action d’appui avec la main levée.</span><span class="sxs-lookup"><span data-stu-id="4afbc-185">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="4afbc-186">Pour utiliser un robinet, soulevez le doigt de votre index jusqu’à la position prête, puis pincez-le avec votre curseur et augmentez la sauvegarde du doigt de l’index jusqu’à la version finale.</span><span class="sxs-lookup"><span data-stu-id="4afbc-186">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="4afbc-187">Sur HoloLens (1ère génération), le robinet air est l’entrée secondaire la plus courante.</span><span class="sxs-lookup"><span data-stu-id="4afbc-187">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="4afbc-188">![Doigt en position prête](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="4afbc-188">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="4afbc-189">**Doigt en position prête**</span><span class="sxs-lookup"><span data-stu-id="4afbc-189">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4afbc-190">![Appuyez sur le doigt pour appuyer ou sur](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="4afbc-190">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="4afbc-191">**Appuyez sur le doigt pour appuyer ou sur**</span><span class="sxs-lookup"><span data-stu-id="4afbc-191">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="4afbc-192">Le TAP Air est également disponible sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4afbc-192">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="4afbc-193">Elle a été allégée de la version d’origine.</span><span class="sxs-lookup"><span data-stu-id="4afbc-193">It has been relaxed from the original version.</span></span> <span data-ttu-id="4afbc-194">Presque tous les types de pincements sont maintenant pris en charge tant que la main est debout et qu’elles sont conservées.</span><span class="sxs-lookup"><span data-stu-id="4afbc-194">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="4afbc-195">Il est ainsi beaucoup plus facile pour les utilisateurs d’apprendre et d’utiliser le geste.</span><span class="sxs-lookup"><span data-stu-id="4afbc-195">This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id="4afbc-196">Ce nouveau robinet d’air remplace l’ancien par la même API. par conséquent, les applications existantes auront le nouveau comportement automatiquement après la recompilation pour HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4afbc-196">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="4afbc-197">Commande vocale en regard de « sélectionner »</span><span class="sxs-lookup"><span data-stu-id="4afbc-197">Gaze and "Select" voice command</span></span>
<span data-ttu-id="4afbc-198">Les commandes vocales sont l’une des principales méthodes d’interaction dans la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="4afbc-198">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="4afbc-199">Il fournit un mécanisme mains-libres puissant pour contrôler le système.</span><span class="sxs-lookup"><span data-stu-id="4afbc-199">It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="4afbc-200">Il existe différents types de modèles d’interactions vocales :</span><span class="sxs-lookup"><span data-stu-id="4afbc-200">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="4afbc-201">Commande « SELECT » générique qui utilise une activation de clic ou une validation comme entrée secondaire.</span><span class="sxs-lookup"><span data-stu-id="4afbc-201">The generic "Select" command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="4afbc-202">Les commandes d’objet (par exemple, « fermer » ou « agrandir ») sont exécutées et validées sur une action en tant qu’entrée secondaire.</span><span class="sxs-lookup"><span data-stu-id="4afbc-202">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="4afbc-203">Les commandes globales (par exemple, « atteindre le début ») ne nécessitent pas de cible.</span><span class="sxs-lookup"><span data-stu-id="4afbc-203">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="4afbc-204">Les interfaces utilisateur ou les entités de conversation comme Cortana disposent d’une fonctionnalité de langage naturel AI.</span><span class="sxs-lookup"><span data-stu-id="4afbc-204">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="4afbc-205">Commandes vocales personnalisées</span><span class="sxs-lookup"><span data-stu-id="4afbc-205">Custom voice commands</span></span>

<span data-ttu-id="4afbc-206">Pour en savoir plus sur les détails et sur la liste complète des commandes vocales disponibles et sur leur utilisation, consultez notre guide de [commande vocale](../out-of-scope/voice-design.md) .</span><span class="sxs-lookup"><span data-stu-id="4afbc-206">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="4afbc-207">Clic de la même façon</span><span class="sxs-lookup"><span data-stu-id="4afbc-207">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="4afbc-208">L’interutilisateur HoloLens est le premier périphérique périphérique créé spécifiquement pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4afbc-208">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="4afbc-209">Elle est incluse dans la version développement de HoloLens (1re génération).</span><span class="sxs-lookup"><span data-stu-id="4afbc-209">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="4afbc-210">L’utilisateur de l’un des clickers HoloLens permet à un utilisateur de cliquer avec un mouvement de main minimal et de valider comme entrée secondaire.</span><span class="sxs-lookup"><span data-stu-id="4afbc-210">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="4afbc-211">L’utilisateur de l’un des clickers HoloLens se connecte à HoloLens (1re génération) ou à HoloLens 2 à l’aide de la BTLE (Bluetooth Low Energy).</span><span class="sxs-lookup"><span data-stu-id="4afbc-211">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="4afbc-212">Plus d’informations et d’instructions pour coupler l’appareil</span><span class="sxs-lookup"><span data-stu-id="4afbc-212">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="4afbc-213">*Image : Clicker de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="4afbc-213">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![Dispositif de clic HoloLens](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="4afbc-215">Contrôleur de réseau sans fil en regard</span><span class="sxs-lookup"><span data-stu-id="4afbc-215">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="4afbc-216">Le contrôleur Xbox Wireless effectue une activation de clic comme entrée secondaire à l’aide du bouton « A ».</span><span class="sxs-lookup"><span data-stu-id="4afbc-216">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="4afbc-217">L’appareil est mappé à un ensemble d’actions par défaut qui facilitent la navigation et le contrôle du système.</span><span class="sxs-lookup"><span data-stu-id="4afbc-217">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="4afbc-218">Si vous souhaitez personnaliser le contrôleur, utilisez l’application Accessoires Xbox pour configurer votre contrôleur Xbox Wireless.</span><span class="sxs-lookup"><span data-stu-id="4afbc-218">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="4afbc-219">Comment associer un contrôleur Xbox à votre PC</span><span class="sxs-lookup"><span data-stu-id="4afbc-219">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="4afbc-220">*Image : contrôleur sans fil Xbox*</span><span class="sxs-lookup"><span data-stu-id="4afbc-220">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Manette Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="4afbc-222">Contrôleur adaptatif du point de regard et de Xbox</span><span class="sxs-lookup"><span data-stu-id="4afbc-222">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="4afbc-223">Conçu principalement pour répondre aux besoins des joueurs avec une mobilité limitée, le contrôleur d’adaptateur Xbox est un concentrateur unifié pour les appareils qui permet de rendre la réalité mixte plus accessible.</span><span class="sxs-lookup"><span data-stu-id="4afbc-223">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="4afbc-224">Le contrôleur d’adaptateur Xbox effectue une action de clic comme entrée secondaire à l’aide du bouton « A ».</span><span class="sxs-lookup"><span data-stu-id="4afbc-224">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="4afbc-225">L’appareil est mappé à un ensemble d’actions par défaut qui facilitent la navigation et le contrôle du système.</span><span class="sxs-lookup"><span data-stu-id="4afbc-225">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="4afbc-226">Si vous souhaitez personnaliser le contrôleur, utilisez l’application Accessoires Xbox pour configurer votre contrôleur d’adaptateur Xbox.</span><span class="sxs-lookup"><span data-stu-id="4afbc-226">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="4afbc-227">![Manette Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="4afbc-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="4afbc-228">*Manette Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="4afbc-228">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="4afbc-229">Connectez des appareils externes, tels que des commutateurs, des boutons, des montages et des joysticks, afin de créer une expérience de contrôleur personnalisée unique.</span><span class="sxs-lookup"><span data-stu-id="4afbc-229">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="4afbc-230">Les entrées de bouton, de Stick et de déclencheur sont contrôlées à l’aide d’appareils d’assistance connectés via des connecteurs 3,5-mm et des ports USB.</span><span class="sxs-lookup"><span data-stu-id="4afbc-230">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="4afbc-231">![Ports de la manette Xbox Adaptive Controller](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="4afbc-231">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="4afbc-232">*Ports de la manette Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="4afbc-232">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="4afbc-233">Instructions pour coupler l’appareil</span><span class="sxs-lookup"><span data-stu-id="4afbc-233">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="4afbc-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Plus d’informations sur le site Xbox</a></span><span class="sxs-lookup"><span data-stu-id="4afbc-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="4afbc-235">Mouvements composites</span><span class="sxs-lookup"><span data-stu-id="4afbc-235">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="4afbc-236">Clic aérien</span><span class="sxs-lookup"><span data-stu-id="4afbc-236">Air tap</span></span>
<span data-ttu-id="4afbc-237">Le mouvement d’appui sur l’air (et les autres mouvements ci-dessous) réagit uniquement à un TAP spécifique.</span><span class="sxs-lookup"><span data-stu-id="4afbc-237">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="4afbc-238">Pour détecter d’autres pressions, telles que menu ou saisis, votre application doit utiliser directement les interactions de niveau inférieur décrites dans la section relative aux mouvements de composants clés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="4afbc-238">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="4afbc-239">Appui de longue durée</span><span class="sxs-lookup"><span data-stu-id="4afbc-239">Tap and hold</span></span>
<span data-ttu-id="4afbc-240">L’appui prolongé consiste simplement à maintenir la position du doigt vers le bas pendant le clic aérien.</span><span class="sxs-lookup"><span data-stu-id="4afbc-240">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="4afbc-241">La combinaison du robinet et du maintien de l’air permet des interactions plus complexes de type « glisser-déplacer » lorsqu’elles sont combinées à un mouvement ARM, par exemple la sélection d’un objet au lieu de l’activer ou des interactions secondaires MouseDown, telles que l’émission d’un menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4afbc-241">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="4afbc-242">Toutefois, il est préférable d’utiliser cette opération lors de la conception de ce geste, car les utilisateurs peuvent être enclins à les faire passer au cours d’un mouvement étendu.</span><span class="sxs-lookup"><span data-stu-id="4afbc-242">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="4afbc-243">Manipulation</span><span class="sxs-lookup"><span data-stu-id="4afbc-243">Manipulation</span></span>
<span data-ttu-id="4afbc-244">Les mouvements de manipulation peuvent être utilisés pour déplacer, redimensionner ou faire pivoter un hologramme lorsque vous souhaitez que l’hologramme réagisse 1:1 aux mouvements manuels de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4afbc-244">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="4afbc-245">La possibilité pour l’utilisateur de dessiner ou de peindre dans le monde illustre l’utilisation de ce type de mouvement.</span><span class="sxs-lookup"><span data-stu-id="4afbc-245">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="4afbc-246">Le ciblage initial pour un mouvement de manipulation doit être effectué au moyen d’un pointage du regard ou d’un pointage.</span><span class="sxs-lookup"><span data-stu-id="4afbc-246">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="4afbc-247">Une fois le TAP et le Hold démarré, toute manipulation d’objet est gérée par des mouvements manuels, ce qui permet à l’utilisateur d’effectuer des recherches lors de la manipulation.</span><span class="sxs-lookup"><span data-stu-id="4afbc-247">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="4afbc-248">Navigation</span><span class="sxs-lookup"><span data-stu-id="4afbc-248">Navigation</span></span>
<span data-ttu-id="4afbc-249">Les mouvements de navigation fonctionnent comme une manette de jeu virtuelle et peuvent être utilisés pour parcourir des widgets d’interface utilisateur, tels que des menus circulaires.</span><span class="sxs-lookup"><span data-stu-id="4afbc-249">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="4afbc-250">Vous appuyez longuement pour démarrer le mouvement, puis déplacez votre main dans un cube 3D normalisé, centré sur l’appui initial.</span><span class="sxs-lookup"><span data-stu-id="4afbc-250">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="4afbc-251">Vous pouvez déplacer votre main le long de l’axe X, Y ou Z d’une valeur de-1 à 1, 0 étant le point de départ.</span><span class="sxs-lookup"><span data-stu-id="4afbc-251">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="4afbc-252">La navigation peut servir à générer des mouvements de zoom ou de défilement continus basés sur la vitesse, à l’image du défilement d’une interface utilisateur 2D que vous pouvez obtenir en cliquant sur le bouton central de la souris, puis en déplaçant le pointeur de la souris vers le haut ou le bas.</span><span class="sxs-lookup"><span data-stu-id="4afbc-252">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="4afbc-253">La navigation avec rails fait référence à la possibilité de reconnaître des mouvements dans certains axes jusqu’à ce qu’un certain seuil soit atteint sur cet axe.</span><span class="sxs-lookup"><span data-stu-id="4afbc-253">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="4afbc-254">Cela est utile uniquement lorsque le déplacement dans plus d’un axe est activé dans une application par le développeur, par exemple si une application est configurée pour reconnaître les gestes de navigation sur l’axe des X, Y, mais également dans l’axe des X avec rails.</span><span class="sxs-lookup"><span data-stu-id="4afbc-254">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="4afbc-255">Dans ce cas, le système reconnaît les mouvements de main sur l’axe des X tant qu’ils restent dans des rails imaginaires (repère) sur l’axe des X, si le mouvement de la main se produit également sur l’axe des Y.</span><span class="sxs-lookup"><span data-stu-id="4afbc-255">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="4afbc-256">Dans les applications 2D, l’utilisateur peut se servir de mouvements de navigation verticaux pour faire défiler l’écran, effectuer un zoom ou faire glisser un élément à l’intérieur de l’application.</span><span class="sxs-lookup"><span data-stu-id="4afbc-256">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="4afbc-257">Des interactions tactiles virtuelles sont ainsi injectées dans l’application pour simuler des mouvements tactiles du même type.</span><span class="sxs-lookup"><span data-stu-id="4afbc-257">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="4afbc-258">Les utilisateurs peuvent sélectionner les actions à effectuer en basculant entre les outils de la barre au-dessus de l’application, soit en sélectionnant le bouton, soit en disant « <défilement/glissement/zoom> outil ».</span><span class="sxs-lookup"><span data-stu-id="4afbc-258">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="4afbc-259">Plus d’informations sur les mouvements composites</span><span class="sxs-lookup"><span data-stu-id="4afbc-259">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="4afbc-260">Modules de reconnaissance des mouvements</span><span class="sxs-lookup"><span data-stu-id="4afbc-260">Gesture recognizers</span></span>

<span data-ttu-id="4afbc-261">L’un des avantages de l’utilisation de la reconnaissance des mouvements est que vous pouvez configurer un module de reconnaissance de mouvement uniquement pour les mouvements que l’hologramme actuellement ciblé peut accepter.</span><span class="sxs-lookup"><span data-stu-id="4afbc-261">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="4afbc-262">La plateforme ne fait que lever l’ambiguïté nécessaire pour distinguer les gestes pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4afbc-262">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="4afbc-263">De cette façon, un hologramme qui prend uniquement en charge le TAP-Air peut accepter n’importe quel laps de temps entre une pression et une mise en route, tandis qu’un hologramme qui prend en charge les deux robinets peut promouvoir le robinet en attente après le seuil de temps de maintien.</span><span class="sxs-lookup"><span data-stu-id="4afbc-263">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="4afbc-264">Reconnaissance des mouvements de la main</span><span class="sxs-lookup"><span data-stu-id="4afbc-264">Hand recognition</span></span>
<span data-ttu-id="4afbc-265">HoloLens reconnaît les mouvements de la main en effectuant le suivi de la position de la main, ou des mains, que l’appareil peut voir.</span><span class="sxs-lookup"><span data-stu-id="4afbc-265">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="4afbc-266">HoloLens voit les mains quand elles sont dans l’état « prêt » (dos de la main face à vous, index dressé) ou « enfoncé » (dos de la main face à vous, index abaissé).</span><span class="sxs-lookup"><span data-stu-id="4afbc-266">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="4afbc-267">Lorsque les mains sont dans d’autres poses, HoloLens les ignore.</span><span class="sxs-lookup"><span data-stu-id="4afbc-267">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="4afbc-268">Pour chaque main détectée par HoloLens, vous pouvez accéder à sa position sans orientation et à son état appuyé.</span><span class="sxs-lookup"><span data-stu-id="4afbc-268">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="4afbc-269">Quand la main s’approche du bord du cadre de mouvement, vous disposez également d’un vecteur de direction, que vous pouvez présenter à l’utilisateur afin qu’il sache comment déplacer sa main de manière à ce que HoloLens puisse la voir.</span><span class="sxs-lookup"><span data-stu-id="4afbc-269">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="4afbc-270">Cadre de mouvement</span><span class="sxs-lookup"><span data-stu-id="4afbc-270">Gesture frame</span></span>
<span data-ttu-id="4afbc-271">Pour les gestes sur HoloLens, la main doit se trouver dans un cadre de mouvement, dans une plage que les caméras de détection de mouvement peuvent voir de manière appropriée, d’un nez à l’autre et entre les épaules.</span><span class="sxs-lookup"><span data-stu-id="4afbc-271">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="4afbc-272">Les utilisateurs doivent être formés dans ce domaine de reconnaissance pour la réussite de l’action et pour leur propre confort.</span><span class="sxs-lookup"><span data-stu-id="4afbc-272">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="4afbc-273">Un grand nombre d’utilisateurs partent initialement du principe que le cadre de mouvement doit se trouver dans leur vue par le biais de HoloLens et que leurs bras ne sont pas plus confortables pour interagir.</span><span class="sxs-lookup"><span data-stu-id="4afbc-273">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="4afbc-274">Lorsque vous utilisez le clicker HoloLens, il n’est pas nécessaire que les mains soient dans le cadre de mouvement.</span><span class="sxs-lookup"><span data-stu-id="4afbc-274">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="4afbc-275">Pour les gestes continus, en particulier, il existe un risque que les utilisateurs déplacent leurs mains en dehors du cadre de mouvement pendant le mouvement intermédiaire lors du déplacement d’un objet holographique, par exemple, et la perte de leur résultat prévu.</span><span class="sxs-lookup"><span data-stu-id="4afbc-275">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="4afbc-276">Voici trois choses que vous devez envisager :</span><span class="sxs-lookup"><span data-stu-id="4afbc-276">There are three things that you should consider:</span></span>

- <span data-ttu-id="4afbc-277">Éducation de l’utilisateur sur l’existence du cadre de mouvement et les limites approximatives.</span><span class="sxs-lookup"><span data-stu-id="4afbc-277">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="4afbc-278">Ce processus est enseigné au cours de la configuration de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4afbc-278">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="4afbc-279">Notifier les utilisateurs lorsque leurs gestes approchent ou rompent les limites du cadre de mouvement au sein d’une application jusqu’à ce qu’un geste perdu aboutisse à des résultats indésirables.</span><span class="sxs-lookup"><span data-stu-id="4afbc-279">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="4afbc-280">La recherche a montré les qualités clés d’un tel système de notification.</span><span class="sxs-lookup"><span data-stu-id="4afbc-280">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="4afbc-281">L’interpréteur de commandes HoloLens fournit un bon exemple de ce type de notification, visuel, sur le curseur central, indiquant la direction dans laquelle le franchissement des limites est effectué.</span><span class="sxs-lookup"><span data-stu-id="4afbc-281">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="4afbc-282">Réduire au minimum les conséquences d’un franchissement des limites du cadre de mouvement.</span><span class="sxs-lookup"><span data-stu-id="4afbc-282">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="4afbc-283">En général, cela signifie que le résultat d’un mouvement doit être arrêté à la limite et non inversé.</span><span class="sxs-lookup"><span data-stu-id="4afbc-283">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="4afbc-284">Par exemple, si un utilisateur déplace un objet holographique dans une salle, le mouvement doit s’arrêter lorsque le cadre de mouvement est violé, et n’est pas retourné au point de départ.</span><span class="sxs-lookup"><span data-stu-id="4afbc-284">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="4afbc-285">L’utilisateur peut faire des frustrations, mais il peut comprendre plus rapidement les limites et ne pas avoir à redémarrer ses actions complètes à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="4afbc-285">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="4afbc-286">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4afbc-286">See also</span></span>
* [<span data-ttu-id="4afbc-287">Interaction basée sur le regard</span><span class="sxs-lookup"><span data-stu-id="4afbc-287">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="4afbc-288">Suivi oculaire sur HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4afbc-288">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="4afbc-289">Pointer du regard et fixer</span><span class="sxs-lookup"><span data-stu-id="4afbc-289">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4afbc-290">Mains : Manipulation directe</span><span class="sxs-lookup"><span data-stu-id="4afbc-290">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4afbc-291">Mains : Mouvements</span><span class="sxs-lookup"><span data-stu-id="4afbc-291">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="4afbc-292">Mains : Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="4afbc-292">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="4afbc-293">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="4afbc-293">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4afbc-294">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="4afbc-294">Voice input</span></span>](voice-input.md)