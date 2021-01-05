---
title: Conception d’hologrammes
description: En savoir plus sur la réalité mixte grâce à la nouvelle application de conception d’hologrammes de Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, boîte à outils de réalité mixte, hologrammes, conception d’hologrammes, apprentissage, exemple d’application, casque de réalité mixte, casque de réalité virtuelle, présentation de la réalité virtuelle
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757757"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="333ac-104">Création d’hologrammes</span><span class="sxs-lookup"><span data-stu-id="333ac-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="333ac-105">Veuillez tenir compte d’une petite fenêtre de chargement pour tenir compte de tous les gif et vidéos incorporées dans cette page.</span><span class="sxs-lookup"><span data-stu-id="333ac-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="333ac-106">Il peut être difficile de savoir comment concevoir pour la réalité mixte, car le support ne traduit pas toujours bien les processus de conception 2D.</span><span class="sxs-lookup"><span data-stu-id="333ac-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="333ac-107">Chez Microsoft, nous avons créé une application gratuite pour HoloLens 2 afin de vous aider à apprendre les principes fondamentaux de la conception d’expérience utilisateur de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="333ac-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="333ac-108">L’approche unique de la conception d’une application d’hologrammes s’approche des comportements de réalité mixte, des conseils et des recommandations pour vous aider à créer vos propres applications HoloLens attrayantes et étonnantes.</span><span class="sxs-lookup"><span data-stu-id="333ac-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="333ac-109">Téléchargez gratuitement l’application à partir de la Microsoft Store et apprenez de l’équipe de conception de la réalité mixte de Microsoft !</span><span class="sxs-lookup"><span data-stu-id="333ac-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="333ac-110">Télécharger l’application conception d’hologrammes</span><span class="sxs-lookup"><span data-stu-id="333ac-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animé de la scène de suivi des têtes dans le design de la salle de démonstration de l’hologramme](images/designing-holograms/demo-room.gif)

<span data-ttu-id="333ac-112">*Conception de la salle de démonstration de l’hologramme (également appelée maison de poupée)*</span><span class="sxs-lookup"><span data-stu-id="333ac-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="333ac-113">Conception pour la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="333ac-113">Designing for mixed reality</span></span>

<span data-ttu-id="333ac-114">Comme beaucoup d’entre vous, j’ai utilisé pour concevoir des applications mobiles.</span><span class="sxs-lookup"><span data-stu-id="333ac-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="333ac-115">En provenance d’un monde de conception 2D, le saut dans le monde de l’informatique spatiale, où tout est présent dans le monde, était un changement significatif.</span><span class="sxs-lookup"><span data-stu-id="333ac-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="333ac-116">En réalité mixte, les applications ne sont plus limitées à un écran 2D ; en fait, ils sont presque gratuits, placés dans le monde réel et interagissent avec les objets réels.</span><span class="sxs-lookup"><span data-stu-id="333ac-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="333ac-117">Pour moi, la connexion des expériences 3D aux processus de conception 2D conventionnels est l’aspect le plus difficile du développement de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="333ac-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="333ac-118">Dans les conversations avec les clients, j’entends des choses telles que «je sais quelles sont les fonctionnalités à inclure et comment les mettre en service.</span><span class="sxs-lookup"><span data-stu-id="333ac-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="333ac-119">C’est le code, je peux suivre les documents et les didacticiels, mais l’expérience de l’utilisateur ?</span><span class="sxs-lookup"><span data-stu-id="333ac-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="333ac-120">De nombreuses fonctionnalités, des options d’entrée différentes, des scénarios différents et des environnements physiques sont insurmontables.</span><span class="sxs-lookup"><span data-stu-id="333ac-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="333ac-121">![Image de l’atelier de conception HoloLens 2 de l’image San Francisco ](images/designing-holograms/workshop.jpeg)
 *de l’atelier de conception hololens 2 de San Francisco*</span><span class="sxs-lookup"><span data-stu-id="333ac-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="333ac-122">Une opportunité d’enseigner</span><span class="sxs-lookup"><span data-stu-id="333ac-122">An opportunity to teach</span></span>

<span data-ttu-id="333ac-123">Ce n’était pas évident dans un premier temps, mais une excellente opportunité était présentée pour utiliser la réalité mixte comme un support pour l’enseigner.</span><span class="sxs-lookup"><span data-stu-id="333ac-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="333ac-124">La conception d’hologrammes est une expérience visuelle qui explique les concepts et les recommandations en matière de conception de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="333ac-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="333ac-125">C’est juste vous et un enseignant qui démontre les concepts de conception de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="333ac-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="333ac-126">Tout est un point de vue de la troisième personne avec l’expérience dans votre propre espace.</span><span class="sxs-lookup"><span data-stu-id="333ac-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="333ac-127">*Vidéo sur la conception d’hologrammes*</span><span class="sxs-lookup"><span data-stu-id="333ac-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="333ac-128">Exploration de la maison de poupée</span><span class="sxs-lookup"><span data-stu-id="333ac-128">Exploring the doll house</span></span>

<span data-ttu-id="333ac-129">La maison de poupée est l’environnement virtuel que nous utilisons dans toute l’application.</span><span class="sxs-lookup"><span data-stu-id="333ac-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="333ac-130">L’environnement est une salle miniature 80 x 60 x 40 cm qui contient les éléments de base que la plupart des chambres ont en commun, comme les murs, les lampes, les meubles, une table et un téléviseur.</span><span class="sxs-lookup"><span data-stu-id="333ac-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="333ac-131">La maison de poupée est le Protagonist principal de l’expérience de l’application. nous avons donc dû nous assurer qu’elle fonctionnera très bien dans n’importe quel environnement.</span><span class="sxs-lookup"><span data-stu-id="333ac-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="333ac-132">Considérez-le comme une petite salle de démonstration pour visualiser toutes sortes de concepts de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="333ac-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="333ac-133">*Vidéo du comportement de réglage Dollhouse*</span><span class="sxs-lookup"><span data-stu-id="333ac-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="333ac-134">1:1 et prototypes 1:10</span><span class="sxs-lookup"><span data-stu-id="333ac-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="333ac-135">Notre hypothèse initiale était que les démonstrations 1:1 seraient étonnantes, presque comme en regardant un professeur réel.</span><span class="sxs-lookup"><span data-stu-id="333ac-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="333ac-136">L’utilisateur verra tout ce que voit l’enseignant à une échelle réelle.</span><span class="sxs-lookup"><span data-stu-id="333ac-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="333ac-137">Toutefois, nous avons immédiatement réalisé que quelques problèmes se produisaient :</span><span class="sxs-lookup"><span data-stu-id="333ac-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="333ac-138">La plupart des développeurs exécutent leurs applications dans des bureaux ou des salles plus petites que la salle de démonstration, ce qui ne peut pas être le cas.</span><span class="sxs-lookup"><span data-stu-id="333ac-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="333ac-139">Les affichages sont additifs, ce qui signifie que l’ensemble de l’environnement virtuel sera reporté sur la salle d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="333ac-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="333ac-140">Cela peut être confus avec deux tables, peut-être des cloisons doubles et des murs qui ne s’alignent pas.</span><span class="sxs-lookup"><span data-stu-id="333ac-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="333ac-141">Et pire de tous les environnements virtuels sont fortement limités par un champ de vue.</span><span class="sxs-lookup"><span data-stu-id="333ac-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="333ac-142">Lors d’une tentative de mise à l’échelle de la mini-1:10, le résultat était une vue d’ensemble des oiseaux fantastique dans une salle réaliste.</span><span class="sxs-lookup"><span data-stu-id="333ac-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="333ac-143">Vous pouvez voir tout ce qui se passe depuis n’importe quel angle en même temps.</span><span class="sxs-lookup"><span data-stu-id="333ac-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="333ac-144">Ce qui était le plus surprenant, c’est que la plupart des testeurs ont trouvé qu’il s’agissait d’une plus grande immersion pour voir une petite version, alors ils n’ont jamais rétabli l’échelle 1:1.</span><span class="sxs-lookup"><span data-stu-id="333ac-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="333ac-145">Nous avons donc décidé de mettre en fait la version 1:1 et d’éviter le travail supplémentaire requis pour adapter l’interface utilisateur et d’autres aspects de l’application.</span><span class="sxs-lookup"><span data-stu-id="333ac-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="333ac-146">![Champ de vue avec un champ d’affichage à l’échelle 1:1 ](images/designing-holograms/1-1-scale.png)
 *avec une échelle de 1:1*</span><span class="sxs-lookup"><span data-stu-id="333ac-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="333ac-147">![Champ de vue avec un champ d’affichage à l’échelle 1:10 ](images/designing-holograms/1-10-scale.png)
 *avec une échelle de 1:10*</span><span class="sxs-lookup"><span data-stu-id="333ac-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="333ac-148">Utilisation de la capture de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="333ac-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="333ac-149">L’une des fonctionnalités les plus caractéristiques de cette application est l’utilisation de la capture de réalité mixte pour enseigner et démontrer les concepts de conception de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="333ac-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="333ac-150">Microsoft dispose d’une réalité mixte de capture Studio à San Francisco.</span><span class="sxs-lookup"><span data-stu-id="333ac-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="333ac-151">Microsoft concède également cette technologie à d’autres Studios, y compris la dimension d’avatar à Washington D.C., la réétape à Los Angeles, les Studios de dimension à Londres, SK Telecom à Séoul et Volucap à Berlin.</span><span class="sxs-lookup"><span data-stu-id="333ac-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="333ac-152">Vous trouverez des informations supplémentaires sur nos [Studios de capture de réalité mixte ici](https://www.microsoft.com/mixed-reality/capture-studios).</span><span class="sxs-lookup"><span data-stu-id="333ac-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="333ac-153">*Métrage brut de Daniel Escudero à partir de l’une des caméras 106 dans la réalité mixte capture Studio à San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="333ac-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="333ac-154">Le processus de capture génère un maillage, des normales et une texture KeyFrame, qui peuvent être fournis sous la forme de fichiers OBJ/PNG pour une nouvelle publication, ou prêts pour la lecture en tant que fichier MP4 compressé H. 264.</span><span class="sxs-lookup"><span data-stu-id="333ac-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="333ac-155">Ces fichiers peuvent être importés dans des projets Unity, inréel, natif et WebXR.</span><span class="sxs-lookup"><span data-stu-id="333ac-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="333ac-156">Les fichiers peuvent s’exécuter sur Windows, iOS, Mac, Android, Magic LEAP et PlayStation VR.</span><span class="sxs-lookup"><span data-stu-id="333ac-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="333ac-157">*Lecteur de capture fourni pour analyser les fichiers MP4 à qui contiennent des vidéos avec des panneaux audio et incorporés.*</span><span class="sxs-lookup"><span data-stu-id="333ac-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="333ac-158">Manipulation des captures et des objets virtuels</span><span class="sxs-lookup"><span data-stu-id="333ac-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="333ac-159">Les captures de réalité mixte produisent des représentations virtuelles de personnes ou d’animaux, mais il peut arriver que vous ayez besoin de ces caractères pour interagir avec d’autres objets virtuels.</span><span class="sxs-lookup"><span data-stu-id="333ac-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="333ac-160">Les deux exemples suivants illustrent les différentes façons dont nous avons manipulé les scènes pour atteindre cet effet.</span><span class="sxs-lookup"><span data-stu-id="333ac-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="333ac-161">Réglage du pointage de la tête</span><span class="sxs-lookup"><span data-stu-id="333ac-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="333ac-162">L’ajustement de Headgaze vous permet de déplacer la tête d’une personne capturée au moment de l’exécution, ce qui signifie que vous pouvez avoir un visage de capture pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="333ac-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="333ac-163">Dans notre cas, nous l’avons utilisé pour afficher le champ de vue et le champ d’intérêt.</span><span class="sxs-lookup"><span data-stu-id="333ac-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="333ac-164">Ce que vous voyez ci-dessous est un gameobject de déplacement qui joue le rôle de cible pour le regard de la tête.</span><span class="sxs-lookup"><span data-stu-id="333ac-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="333ac-165">À mesure que nous déplaçons la cible d’un côté à l’autre, l’en-tête de la capture suit.</span><span class="sxs-lookup"><span data-stu-id="333ac-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="333ac-166">Nous avons utilisé cette astuce pour s’assurer que la capture inactive serait toujours dirigée vers des hologrammes placés dans des parties différentes de la maison de poupée.</span><span class="sxs-lookup"><span data-stu-id="333ac-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![La tête de capture qui est déplacée au moment de l’exécution après un gameobject cible dans Unity](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="333ac-168">*La tête de capture qui est déplacée au moment de l’exécution après un gameobject cible dans Unity.*</span><span class="sxs-lookup"><span data-stu-id="333ac-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="333ac-169">Synchronisation d’objets animés</span><span class="sxs-lookup"><span data-stu-id="333ac-169">Syncing Animated Objects</span></span>

<span data-ttu-id="333ac-170">Le deuxième, qui consistait à animer des objets à synchroniser avec le mouvement d’une capture.</span><span class="sxs-lookup"><span data-stu-id="333ac-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="333ac-171">Dans les différentes parties de l’application, nous avons importé des ne comportaient séquentielles d’une capture spécifique toutes les cinq frames.</span><span class="sxs-lookup"><span data-stu-id="333ac-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="333ac-172">Les ne comportaient ont ensuite été animés dans la scène pour s’assurer qu’ils correspondent au frame correspondant de la capture.</span><span class="sxs-lookup"><span data-stu-id="333ac-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="333ac-173">Il s’agit d’un processus fastidieux d’animation et de keyencadrement, mais le résultat est parfait.</span><span class="sxs-lookup"><span data-stu-id="333ac-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="333ac-174">Vous pouvez maintenant voir une capture de réalité mixte qui interagit avec des objets non capturés.</span><span class="sxs-lookup"><span data-stu-id="333ac-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Animation synchronisée entre une capture de réalité mixte et un panneau d’interface utilisateur](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="333ac-176">*Animation synchronisée entre une capture de réalité mixte et un panneau d’interface utilisateur*</span><span class="sxs-lookup"><span data-stu-id="333ac-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="333ac-177">Processus créatif de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="333ac-177">UI creative process</span></span>

<span data-ttu-id="333ac-178">Lorsque nous avons commencé la conception de l’interface utilisateur, nous souhaitons montrer une partie de la magie et des possibilités offertes par les hologrammes.</span><span class="sxs-lookup"><span data-stu-id="333ac-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="333ac-179">Il n’est pas simple d’illustrer les fenêtres 2D statiques et les zones de texte dans le monde 3D.</span><span class="sxs-lookup"><span data-stu-id="333ac-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="333ac-180">La plupart des possibilités en main ne s’affichent pas. donc, dès le début, nous avons décidé de ne plus en sortir et d’utiliser pleinement l’espace 3D holographique.</span><span class="sxs-lookup"><span data-stu-id="333ac-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="333ac-181">Dans un premier temps, nous avons commencé à ajouter de l’épaisseur aux panneaux, aux icônes et aux informations de texte.</span><span class="sxs-lookup"><span data-stu-id="333ac-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="333ac-182">Toutefois, en tant qu’utilisateur, ce que je vois est une zone de texte.</span><span class="sxs-lookup"><span data-stu-id="333ac-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="333ac-183">Les zones de texte avec des images, mais ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="333ac-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="333ac-184">Nous sommes allés plus loin en utilisant les nuanceurs MRTK (Mixed Reality Toolkit).</span><span class="sxs-lookup"><span data-stu-id="333ac-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="333ac-185">Les nuanceurs MRTK sont devenus un outil puissant et nous avons utilisé leurs fonctionnalités de stencil pour ajouter une profondeur négative aux panneaux.</span><span class="sxs-lookup"><span data-stu-id="333ac-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="333ac-186">Cela signifie qu’au lieu d’ajouter des éléments devant une zone de texte, les icônes s’affichent désormais derrière un panneau transparent.</span><span class="sxs-lookup"><span data-stu-id="333ac-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="333ac-187">Ce que je vois maintenant en tant qu’utilisateur, c’est qu’il n’est plus possible de répliquer plus dans le monde réel, et c’est là où holographique magique a commencé à se produire.</span><span class="sxs-lookup"><span data-stu-id="333ac-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="333ac-188">En outre, comme un utilisateur que je n’aime pas lire, je fais déjà beaucoup de choses dans le monde physique.</span><span class="sxs-lookup"><span data-stu-id="333ac-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="333ac-189">Évidemment, les icônes fonctionnent beaucoup mieux que le simple texte. pour fournir une aide encore plus puissante, j’ai commencé à créer un ensemble d’objets animés et d’avatars, chacun d’entre eux indiquant un petit récit sur ce qui est fait dans le scénario respectif et sur la manière dont il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="333ac-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![GIF animé d’un système de menu holographique interactif](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="333ac-191">Principaux concepts</span><span class="sxs-lookup"><span data-stu-id="333ac-191">Core concepts</span></span>

<span data-ttu-id="333ac-192">**Image holographique**</span><span class="sxs-lookup"><span data-stu-id="333ac-192">**Holographic frame**</span></span>

![GIF animé d’un utilisateur qui regarde le Dollhouse avec le cadre holographique mis en surbrillance](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="333ac-194">**Systèmes de coordonnées**</span><span class="sxs-lookup"><span data-stu-id="333ac-194">**Coordinate systems**</span></span>

![GIF animé d’un utilisateur qui regarde le Dollhouse avec les systèmes de coordonnées mis en surbrillance](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="333ac-196">**Eye-tracking**</span><span class="sxs-lookup"><span data-stu-id="333ac-196">**Eye tracking**</span></span>

![GIF animé d’un utilisateur cherchant des hologrammes stationnaires avec le point de regard de l’oeil en surbrillance](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="333ac-198">**Visualisation de l’analyse de la salle et mappage spatial**</span><span class="sxs-lookup"><span data-stu-id="333ac-198">**Room scan visualization and spatial mapping**</span></span>

![GIF animé de toutes les surfaces à l’intérieur du Dollhouse mappé](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="333ac-200">**Compréhension des scènes**</span><span class="sxs-lookup"><span data-stu-id="333ac-200">**Scene understanding**</span></span>

![GIF animé d’objets dans le Dollhouse qui est reconnu](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="333ac-202">**Pointer et valider avec des rayons de main**</span><span class="sxs-lookup"><span data-stu-id="333ac-202">**Point and commit with hand rays**</span></span>

![GIF animé d’un utilisateur qui soulève sa main avec un rayon de la main mis en surbrillance](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="333ac-204">« Essayer » les moments</span><span class="sxs-lookup"><span data-stu-id="333ac-204">"Try it out" moments</span></span>

<span data-ttu-id="333ac-205">La conception d’hologrammes enseigne les concepts de réalité mixte, mais vous permet également de les essayer dans votre salle.</span><span class="sxs-lookup"><span data-stu-id="333ac-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="333ac-206">Après quelques-unes de ces explications, nous suspendons et vous revenons à la maison de poupée et à un moment interactif.</span><span class="sxs-lookup"><span data-stu-id="333ac-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="333ac-207">Voici quelques exemples de ces moments interactifs :</span><span class="sxs-lookup"><span data-stu-id="333ac-207">Here are some examples of those interactive moments:</span></span>

![GIF animé du frame de suivi de la main montrant quand les mains sont détectées et quand elles entrent dans le champ de la vue](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="333ac-209">*Frame de suivi de la main qui indique quand les mains sont détectées et quand elles entrent dans le champ de la vue.*</span><span class="sxs-lookup"><span data-stu-id="333ac-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![GIF animé de l’interaction avec les cristaux en collision via une interaction lointaine](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="333ac-211">*Interaction avec les cristaux en collision via une interaction lointaine*</span><span class="sxs-lookup"><span data-stu-id="333ac-211">*Interacting with colliding crystals through far interaction*</span></span>

![GIF animé de l’exploration des intuitivité near interaction](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="333ac-213">*Exploration des intuitivité near interaction*</span><span class="sxs-lookup"><span data-stu-id="333ac-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="333ac-214">À propos de l’équipe</span><span class="sxs-lookup"><span data-stu-id="333ac-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="333ac-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="333ac-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="333ac-216"><i>Concepteur technique du prospect</i></span><span class="sxs-lookup"><span data-stu-id="333ac-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="333ac-217">Dan est le directeur créatif de la conception d’hologrammes et travaille actuellement en tant que responsable de la conception de l’Académie de la réalité mixte de Microsoft à San Francisco, et était auparavant un concepteur dans l’un des Studios de réalité mixte de Microsoft à Londres.</span><span class="sxs-lookup"><span data-stu-id="333ac-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="333ac-218"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="333ac-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="333ac-219"><i>Artiste 3D Senior</i></span><span class="sxs-lookup"><span data-stu-id="333ac-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="333ac-220">Martin domine la conception de l’interface utilisateur et de l’art 3D sur la conception d’hologrammes et était auparavant un artiste 3D senior chez l’un des Studios de réalité mixte de Microsoft à Berlin.</span><span class="sxs-lookup"><span data-stu-id="333ac-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="333ac-221">Nous vous remercions de l’équipe de conception de la réalité mixte pour le partage d’une grande connaissance et des gens étonnants de la [théorie des objets](https://objecttheory.com/) pour être des coéquipiers essentiels à chaque étape du projet.</span><span class="sxs-lookup"><span data-stu-id="333ac-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="333ac-222">Nous vous remercions tout pour vos talents exceptionnels, pour votre passion et vos yeux de la conception.</span><span class="sxs-lookup"><span data-stu-id="333ac-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="333ac-223">Télécharger l’application conception d’hologrammes</span><span class="sxs-lookup"><span data-stu-id="333ac-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)