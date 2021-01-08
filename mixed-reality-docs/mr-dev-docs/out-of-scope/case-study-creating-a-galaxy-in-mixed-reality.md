---
title: 'Étude de cas : création d’un Galaxy en réalité mixte'
description: En savoir plus sur l’application « Explorateur Galaxy » et sur la manière dont elle a été créée pour le service de test de présentation et d’interrogation Twitter de 24 heures par les développeurs de la communauté.
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Explorateur Galaxy, HoloLens, Windows Mixed Reality, partager votre idée, étude de cas
ms.openlocfilehash: 0226c38e9fa21407a7a6529693a2adb3c5da7659
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009779"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="7d09f-104">Étude de cas : création d’un Galaxy en réalité mixte</span><span class="sxs-lookup"><span data-stu-id="7d09f-104">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="7d09f-105">Avant la sortie de Microsoft HoloLens, nous avons demandé à notre communauté de développeurs quel type d’application il souhaite voir une build d’équipe interne expérimentée pour le nouvel appareil.</span><span class="sxs-lookup"><span data-stu-id="7d09f-105">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="7d09f-106">Plus de 5000 idées ont été partagées et, après une interrogation Twitter de 24 heures, le gagnant était une idée appelée l' [Explorateur Galaxy](../develop/unity/galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="7d09f-106">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](../develop/unity/galaxy-explorer.md).</span></span>

<span data-ttu-id="7d09f-107">Andy Zibits, responsable artistique sur le projet et karim Luccin, l’ingénieur graphique de l’équipe, évoque les efforts de collaboration entre l’art et l’ingénierie qui ont conduit à la création d’une représentation interactive et précise de la manière lactée de Galaxy dans l’Explorateur Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7d09f-107">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="7d09f-108">Le Tech</span><span class="sxs-lookup"><span data-stu-id="7d09f-108">The Tech</span></span>

<span data-ttu-id="7d09f-109">[Notre équipe](../develop/unity/galaxy-explorer.md#meet-the-team) , composée de deux concepteurs, de trois développeurs, de quatre artistes, d’un producteur et d’un testeur, avait six semaines pour créer une application entièrement fonctionnelle qui permettrait aux utilisateurs d’en savoir plus sur l’immense et la beauté de notre méthode lactée Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7d09f-109">[Our team](../develop/unity/galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="7d09f-110">Nous souhaitons tirer pleinement parti de la capacité de HoloLens à restituer les objets 3D directement dans votre espace de vie. nous avons donc décidé de créer un Galaxy réaliste où les gens seraient en mesure d’effectuer un zoom avant et de voir les étoiles individuelles, chacune sur leurs propres trajectoires.</span><span class="sxs-lookup"><span data-stu-id="7d09f-110">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="7d09f-111">Au cours de la première semaine de développement, nous avons vu quelques objectifs pour notre représentation de la méthode lactée Galaxy : elle devait avoir une profondeur, un mouvement et une sensation volumétrique, ce qui permet de créer la forme du Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7d09f-111">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="7d09f-112">Le problème lié à la création d’un Galaxy animé qui avait des milliards d’étoiles était que le nombre important d’éléments uniques nécessitant une mise à jour serait trop grand par frame pour que HoloLens s’anime à l’aide de l’UC.</span><span class="sxs-lookup"><span data-stu-id="7d09f-112">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="7d09f-113">Notre solution impliquait une combinaison complexe d’art et de science.</span><span class="sxs-lookup"><span data-stu-id="7d09f-113">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="7d09f-114">Dans les coulisses</span><span class="sxs-lookup"><span data-stu-id="7d09f-114">Behind the scenes</span></span>

<span data-ttu-id="7d09f-115">Pour permettre aux utilisateurs d’explorer des étoiles individuelles, notre première étape consistait à déterminer le nombre de particules pouvant être rendues simultanément.</span><span class="sxs-lookup"><span data-stu-id="7d09f-115">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="7d09f-116">Rendu des particules</span><span class="sxs-lookup"><span data-stu-id="7d09f-116">Rendering particles</span></span>

<span data-ttu-id="7d09f-117">Les processeurs actuels sont idéaux pour traiter des tâches en série et jusqu’à quelques tâches parallèles à la fois (selon le nombre de cœurs), mais les GPU sont beaucoup plus efficaces pour traiter des milliers d’opérations en parallèle.</span><span class="sxs-lookup"><span data-stu-id="7d09f-117">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="7d09f-118">Toutefois, étant donné qu’ils ne partagent généralement pas la même mémoire que le processeur, l’échange de données entre l’UC<>GPU peut rapidement devenir un goulot d’étranglement.</span><span class="sxs-lookup"><span data-stu-id="7d09f-118">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="7d09f-119">Notre solution consistait à créer un Galaxy sur le GPU et il devait être entièrement actif sur le GPU.</span><span class="sxs-lookup"><span data-stu-id="7d09f-119">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="7d09f-120">Nous avons commencé des tests de stress avec des milliers de particules de points dans différents modèles.</span><span class="sxs-lookup"><span data-stu-id="7d09f-120">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="7d09f-121">Cela nous a permis d’obtenir le Galaxy sur HoloLens pour voir ce qui a fonctionné et ce qui ne l’a pas fait.</span><span class="sxs-lookup"><span data-stu-id="7d09f-121">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="7d09f-122">Création de la position des étoiles</span><span class="sxs-lookup"><span data-stu-id="7d09f-122">Creating the position of the stars</span></span>

<span data-ttu-id="7d09f-123">L’un de nos membres de l’équipe a déjà écrit le code C# qui générerait des étoiles à leur position initiale.</span><span class="sxs-lookup"><span data-stu-id="7d09f-123">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="7d09f-124">Les étoiles se trouvent sur une ellipse et leur position peut être décrite par (**curveOffset**, **ellipseSize**, **Elevation**) où **curveOffset** est l’angle de l’étoile le long de l’ellipse, **ellipseSize** est la dimension de l’ellipse le long de X et de Z, et élévation l’altitude appropriée de l’étoile au sein de Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7d09f-124">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="7d09f-125">Par conséquent, nous pouvons créer une mémoire tampon ([ComputeBuffer d’Unity](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) qui serait initialisée avec chaque attribut d’étoile et l’envoyer sur le GPU là où il résiderait pour le reste de l’expérience.</span><span class="sxs-lookup"><span data-stu-id="7d09f-125">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="7d09f-126">Pour dessiner ce tampon, nous utilisons [l’DrawProcedural d’Unity](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) qui permet d’exécuter un nuanceur (code sur un GPU) sur un ensemble arbitraire de points sans avoir de maillage réel représentant le Galaxy :</span><span class="sxs-lookup"><span data-stu-id="7d09f-126">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="7d09f-127">**POURCENTAGE**</span><span class="sxs-lookup"><span data-stu-id="7d09f-127">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="7d09f-128">**VIDÉO**</span><span class="sxs-lookup"><span data-stu-id="7d09f-128">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="7d09f-129">Nous avons commencé avec des modèles circulaires bruts avec des milliers de particules.</span><span class="sxs-lookup"><span data-stu-id="7d09f-129">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="7d09f-130">Nous avons ainsi fourni la preuve que nous avions besoin de gérer de nombreuses particules et de les exécuter à des vitesses performantes, mais nous n’avions pas respecté la forme globale de Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7d09f-130">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="7d09f-131">Pour améliorer la forme, nous avons essayé divers modèles et systèmes de particules avec rotation.</span><span class="sxs-lookup"><span data-stu-id="7d09f-131">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="7d09f-132">Celles-ci ont été initialement prometteuses, car le nombre de particules et de performances est resté cohérent, mais la forme est tombée près du centre et les étoiles ont été émises vers l’extérieur, ce qui n’était pas réaliste.</span><span class="sxs-lookup"><span data-stu-id="7d09f-132">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="7d09f-133">Nous avions besoin d’une émission qui nous permettrait de manipuler le temps et de faire en sorte que les particules se déplacent de façon réaliste, en effectuant une boucle plus proche du centre du Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7d09f-133">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Nous avons essayé différents modèles et systèmes de particules qui ont pivoté, comme ceux-ci.](images/galaxy-patterns-500px.png)

<span data-ttu-id="7d09f-135">Nous avons essayé différents modèles et systèmes de particules qui ont pivoté, comme ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="7d09f-135">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="7d09f-136">Notre équipe a fait des recherches sur la façon dont galaxies fonctionne et nous avons créé un système de particule personnalisé spécifiquement pour la galaxie afin que nous puissions déplacer les particules sur les ellipses en fonction de la «[théorie des vagues de densité](https://en.wikipedia.org/wiki/Density_wave_theory)», qui theorizes que les bras d’un Galaxy sont des zones de densité plus élevée mais en flux constant, comme un bourrage de trafic.</span><span class="sxs-lookup"><span data-stu-id="7d09f-136">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="7d09f-137">Il semble stable et solide, mais les étoiles sont en fait en déplacement et en provenance des bras lorsqu’ils se déplacent sur leurs ellipses respectives.</span><span class="sxs-lookup"><span data-stu-id="7d09f-137">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="7d09f-138">Dans notre système, les particules n’existent jamais sur le processeur : nous générons les cartes et les orientons toutes sur le GPU, de sorte que le système entier est simplement un état initial + Time.</span><span class="sxs-lookup"><span data-stu-id="7d09f-138">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="7d09f-139">Elle a progressé comme suit :</span><span class="sxs-lookup"><span data-stu-id="7d09f-139">It progressed like this:</span></span>

![Progression du système de particules avec rendu GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="7d09f-141">Progression du système de particules avec rendu GPU</span><span class="sxs-lookup"><span data-stu-id="7d09f-141">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="7d09f-142">Une fois que suffisamment de ellipses ont été ajoutées et sont définies pour pivoter, le galaxies a commencé à former des « bras » où le mouvement des étoiles converge.</span><span class="sxs-lookup"><span data-stu-id="7d09f-142">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="7d09f-143">L’espacement des étoiles sur chaque tracé elliptique a été donné à caractère aléatoire, et chaque étoile a ajouté un peu de caractère aléatoire positionnel.</span><span class="sxs-lookup"><span data-stu-id="7d09f-143">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="7d09f-144">Cela a créé une distribution d’aspect plus naturelle du mouvement en étoile et de la forme ARM.</span><span class="sxs-lookup"><span data-stu-id="7d09f-144">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="7d09f-145">Enfin, nous avons ajouté la capacité de piloter la couleur en fonction de la distance par rapport au centre.</span><span class="sxs-lookup"><span data-stu-id="7d09f-145">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="7d09f-146">Création du mouvement des étoiles</span><span class="sxs-lookup"><span data-stu-id="7d09f-146">Creating the motion of the stars</span></span>

<span data-ttu-id="7d09f-147">Pour animer le mouvement de l’étoile générale, nous avons besoin d’ajouter un angle constant pour chaque image et de faire en sorte que les étoiles se déplacent le long de leurs ellipses à une vélocité radiale constante.</span><span class="sxs-lookup"><span data-stu-id="7d09f-147">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="7d09f-148">Il s’agit de la raison principale de l’utilisation de **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="7d09f-148">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="7d09f-149">Cela n’est pas techniquement correct, car les étoiles se déplacent plus rapidement sur les longs côtés des ellipses, mais le mouvement général est parfait.</span><span class="sxs-lookup"><span data-stu-id="7d09f-149">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Les étoiles se déplacent plus rapidement sur l’arc long, plus lentement sur les bords.](images/ellipse-movement.jpg)

<span data-ttu-id="7d09f-151">Les étoiles se déplacent plus rapidement sur l’arc long, plus lentement sur les bords.</span><span class="sxs-lookup"><span data-stu-id="7d09f-151">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="7d09f-152">Avec cela, chaque étoile est entièrement décrite par (**curveOffset**, **ellipseSize**, **Elevation**, **Age**) où **Age** est une accumulation du temps total qui s’est écoulé depuis le chargement de la scène.</span><span class="sxs-lookup"><span data-stu-id="7d09f-152">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="7d09f-153">Cela nous a permis de générer des dizaines de milliers d’étoiles une fois au début de l’application, puis d’animer un ensemble unique d’étoiles le long des courbes établies.</span><span class="sxs-lookup"><span data-stu-id="7d09f-153">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="7d09f-154">Dans la mesure où tout se trouve sur le GPU, le système peut animer toutes les étoiles en parallèle sans coût pour le processeur.</span><span class="sxs-lookup"><span data-stu-id="7d09f-154">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Voici à quoi elle ressemble lors du dessin de Quad White.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="7d09f-156">Voici à quoi elle ressemble lors du dessin de Quad White.</span><span class="sxs-lookup"><span data-stu-id="7d09f-156">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="7d09f-157">Pour que chaque quadruple fasse face à l’appareil photo, nous avons utilisé un nuanceur Geometry pour transformer chaque position d’étoile en rectangle 2D sur l’écran qui contiendra notre texture en étoile.</span><span class="sxs-lookup"><span data-stu-id="7d09f-157">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Losanges au lieu de quads.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="7d09f-159">Losanges au lieu de quads.</span><span class="sxs-lookup"><span data-stu-id="7d09f-159">Diamonds instead of quads.</span></span>


<span data-ttu-id="7d09f-160">Étant donné que nous voulons limiter le surdessin (nombre de fois où un pixel sera traité) autant que possible, nous avons fait tourner nos quatre cœurs afin qu’ils aient moins de chevauchement.</span><span class="sxs-lookup"><span data-stu-id="7d09f-160">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="7d09f-161">Ajout de clouds</span><span class="sxs-lookup"><span data-stu-id="7d09f-161">Adding clouds</span></span>

<span data-ttu-id="7d09f-162">Il existe de nombreuses façons d’obtenir une sensation volumétrique avec des particules, depuis le défilé de rayons à l’intérieur d’un volume jusqu’au dessin du plus grand nombre de particules possible pour simuler un Cloud.</span><span class="sxs-lookup"><span data-stu-id="7d09f-162">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="7d09f-163">Le défilé de rayon en temps réel était trop onéreux et difficile à créer. nous avons donc essayé de créer un système imposteur à l’aide d’une méthode de rendu des forêts dans les jeux, avec un grand nombre d’images 2D d’arbres dirigés vers l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="7d09f-163">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="7d09f-164">Lorsque nous faisons cela dans un jeu, nous pouvons avoir des textures d’arborescences rendues à partir d’une caméra qui pivote, enregistrer toutes ces images et, au moment de l’exécution pour chaque carte de tableau blanc, sélectionner l’image qui correspond à la direction de la vue.</span><span class="sxs-lookup"><span data-stu-id="7d09f-164">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="7d09f-165">Cela ne fonctionne pas aussi bien lorsque les images sont des hologrammes.</span><span class="sxs-lookup"><span data-stu-id="7d09f-165">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="7d09f-166">La différence entre l’œil gauche et l’œil droit le rend, afin que nous ayons besoin d’une résolution plus élevée, sinon il semble simple, avec alias ou répétitif.</span><span class="sxs-lookup"><span data-stu-id="7d09f-166">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="7d09f-167">À la deuxième tentative, nous avons essayé d’avoir autant de particules que possible.</span><span class="sxs-lookup"><span data-stu-id="7d09f-167">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="7d09f-168">Les meilleurs visuels ont été atteints quand nous avons dessiné des particules et les avons floues avant de les ajouter à la scène.</span><span class="sxs-lookup"><span data-stu-id="7d09f-168">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="7d09f-169">Les problèmes typiques de cette approche étaient liés au nombre de particules que nous pourrions tirer en une seule fois et à la zone d’écran couverte tout en maintenant 60fps.</span><span class="sxs-lookup"><span data-stu-id="7d09f-169">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="7d09f-170">Le flou de l’image résultante pour obtenir cette sensation du Cloud était généralement une opération très coûteuse.</span><span class="sxs-lookup"><span data-stu-id="7d09f-170">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Sans texture, c’est ce à quoi ressemblerait les clouds avec 2% d’opacité.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="7d09f-172">Sans texture, c’est ce à quoi ressemblerait les clouds avec 2% d’opacité.</span><span class="sxs-lookup"><span data-stu-id="7d09f-172">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="7d09f-173">L’addition et l’utilisation d’un grand nombre d’entre elles signifient que nous aurions plusieurs quatre cœurs l’un de l’autre, ce qui permet d’ombrager de façon répétée le même pixel.</span><span class="sxs-lookup"><span data-stu-id="7d09f-173">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="7d09f-174">Au centre de l’Galaxy, le même pixel a des centaines de Quad-Top les uns des autres, ce qui a eu un coût énorme lorsque l’opération est effectuée en mode plein écran.</span><span class="sxs-lookup"><span data-stu-id="7d09f-174">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="7d09f-175">Le fait d’effectuer des clouds plein écran et d’essayer de les brouiller aurait été une mauvaise idée, donc nous avons décidé de laisser le matériel faire le travail pour nous.</span><span class="sxs-lookup"><span data-stu-id="7d09f-175">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="7d09f-176">Un peu de contexte en premier</span><span class="sxs-lookup"><span data-stu-id="7d09f-176">A bit of context first</span></span>

<span data-ttu-id="7d09f-177">Lorsque vous utilisez des textures dans un jeu, la taille de la texture correspond rarement à la zone dans laquelle nous voulons l’utiliser, mais nous pouvons utiliser un autre type de filtrage de texture pour faire en sorte que la carte graphique interpole la couleur souhaitée à partir des pixels de la texture ([filtrage de texture](https://msdn.microsoft.com/library/dn642451.aspx)).</span><span class="sxs-lookup"><span data-stu-id="7d09f-177">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="7d09f-178">Le filtrage qui nous intéresse est le [Filtrage bilinéaire](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) qui calcule la valeur de tout pixel à l’aide des 4 voisins les plus proches.</span><span class="sxs-lookup"><span data-stu-id="7d09f-178">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Original avant le filtrage](images/texture-1.png)

![Résultat après le filtrage](images/texture-2.png)

<span data-ttu-id="7d09f-181">À l’aide de cette propriété, nous voyons que chaque fois que nous essayons de dessiner une texture dans une zone deux fois plus grande, le résultat est flou.</span><span class="sxs-lookup"><span data-stu-id="7d09f-181">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="7d09f-182">Au lieu d’effectuer un rendu en plein écran et de perdre ces millisecondes précieuses, nous pourrions passer à une version minuscule de l’écran.</span><span class="sxs-lookup"><span data-stu-id="7d09f-182">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="7d09f-183">Ensuite, en copiant cette texture et en l’étirant à un facteur de 2 plusieurs fois, nous revenons en mode plein écran tout en brouilleant le contenu dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7d09f-183">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 revient à une résolution complète.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="7d09f-185">x3 revient à une résolution complète.</span><span class="sxs-lookup"><span data-stu-id="7d09f-185">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="7d09f-186">Cela nous a permis d’obtenir la partie Cloud avec uniquement une fraction du coût d’origine.</span><span class="sxs-lookup"><span data-stu-id="7d09f-186">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="7d09f-187">Au lieu d’ajouter des clouds à la résolution complète, nous ne dessinons que 1/64th des pixels et remontons la texture à la résolution complète.</span><span class="sxs-lookup"><span data-stu-id="7d09f-187">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![À gauche, avec une mise à l’échelle de 1/8 à la résolution complète ; et Right, avec 3 mises à l’échelle à l’aide de la puissance 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="7d09f-189">À gauche, avec une mise à l’échelle de 1/8 à la résolution complète ; et Right, avec 3 mises à l’échelle à l’aide de la puissance 2.</span><span class="sxs-lookup"><span data-stu-id="7d09f-189">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="7d09f-190">Notez que la tentative de passer de 1/64th de la taille à la taille maximale d’un point de vue serait complètement différente, car la carte graphique utiliserait toujours 4 pixels dans notre configuration pour colorer une zone plus grande et les artefacts commencent à apparaître.</span><span class="sxs-lookup"><span data-stu-id="7d09f-190">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="7d09f-191">Ensuite, si nous ajoutons des étoiles de résolution complète avec des cartes plus petites, nous obtenons l’intégralité de Galaxy :</span><span class="sxs-lookup"><span data-stu-id="7d09f-191">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Résultat final du rendu Galaxy à l’aide des étoiles de résolution complète](images/full-galaxy-500px.png)

<span data-ttu-id="7d09f-193">Une fois que nous étions sur la bonne voie avec la forme, nous avons ajouté une couche de Clouds, remplacé les points temporaires par ceux que nous avons peints dans Photoshop, et ajouté des couleurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="7d09f-193">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="7d09f-194">Le résultat était une façon lactée de Galaxy nos équipes d’art et d’ingénierie, à la fois en matière de qualité, et a répondu à nos objectifs de profondeur, de volume et de mouvement, le tout sans imposer le processeur.</span><span class="sxs-lookup"><span data-stu-id="7d09f-194">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Notre dernière méthode de Galaxy en 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="7d09f-196">Notre dernière méthode de Galaxy en 3D.</span><span class="sxs-lookup"><span data-stu-id="7d09f-196">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="7d09f-197">Plus d’informations à explorer</span><span class="sxs-lookup"><span data-stu-id="7d09f-197">More to explore</span></span>

<span data-ttu-id="7d09f-198">Nous avons ouvert le code de l’application Galaxy Explorer et nous l’avons rendu disponible sur [GitHub](https://github.com/Microsoft/GalaxyExplorer) pour que les développeurs s’appuient sur.</span><span class="sxs-lookup"><span data-stu-id="7d09f-198">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="7d09f-199">Vous souhaitez en savoir plus sur le processus de développement de l’Explorateur Galaxy ?</span><span class="sxs-lookup"><span data-stu-id="7d09f-199">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="7d09f-200">Consultez toutes les mises à jour précédentes du projet sur le [canal Microsoft HoloLens YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="7d09f-200">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="7d09f-201">À propos des auteurs</span><span class="sxs-lookup"><span data-stu-id="7d09f-201">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="7d09f-202"><b>Karim luccin</b> est ingénieur logiciel et passionné d’éléments visuels.</span><span class="sxs-lookup"><span data-stu-id="7d09f-202"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="7d09f-203">Il était l’ingénieur graphique de l’Explorateur Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7d09f-203">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="7d09f-204"><b>Andy Zibits</b> est un responsable artistique et le passionné d’espace qui gérait l’équipe de modélisation 3D pour l’Explorateur Galaxy et lutté pour encore plus de particules.</span><span class="sxs-lookup"><span data-stu-id="7d09f-204"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="7d09f-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d09f-205">See also</span></span>
* [<span data-ttu-id="7d09f-206">Explorateur Galaxy sur GitHub</span><span class="sxs-lookup"><span data-stu-id="7d09f-206">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="7d09f-207">Mises à jour des projets de l’Explorateur Galaxy sur YouTube</span><span class="sxs-lookup"><span data-stu-id="7d09f-207">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
