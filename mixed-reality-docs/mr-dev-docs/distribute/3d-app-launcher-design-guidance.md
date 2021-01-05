---
title: Guide de conception de lanceur d’applications 3D
description: Un lanceur d’applications 3D est un objet « physique » dans la maison de réalité mixte de l’utilisateur qu’il peut sélectionner pour lancer une application.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, mode de lancement d’application 3D, casque immersif, cube en direct, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, UWP, Win32, éclairage, couleur
ms.openlocfilehash: 2edb09e47da5bcbae34a37f004853002f3f65cf3
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757727"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="e0289-104">Guide de conception de lanceur d’applications 3D</span><span class="sxs-lookup"><span data-stu-id="e0289-104">3D app launcher design guidance</span></span>

<span data-ttu-id="e0289-105">Lorsque vous placez un casque Windows Mixed Reality (VR), vous accédez à la page d’hébergement Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="e0289-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home.</span></span> <span data-ttu-id="e0289-106">La maison est visualisée sous la forme d’une maison sur une falaise placée par des montagnes et de l’eau, mais vous pouvez [choisir d’autres environnements et même créer les vôtres](../design/add-custom-home-environments.md).</span><span class="sxs-lookup"><span data-stu-id="e0289-106">The home is visualized as a house on a cliff surrounded by mountains and water, but you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="e0289-107">Au sein de l’espace de la famille, un utilisateur est libre de réorganiser et d’organiser les objets et applications 3D dont il se soucie.</span><span class="sxs-lookup"><span data-stu-id="e0289-107">Within the home's space, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="e0289-108">Un **lanceur d’applications 3D** est un objet « physique » dans la maison de réalité mixte de l’utilisateur qu’il peut sélectionner pour lancer une application.</span><span class="sxs-lookup"><span data-stu-id="e0289-108">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="e0289-109">![Exemple : lanceur d’applications 3D avec un oiseau flottant](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-109">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e0289-110">*Exemple de lanceur d’application 3D d’oiseau flottant (application fictive)*</span><span class="sxs-lookup"><span data-stu-id="e0289-110">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="e0289-111">processus de création du lanceur d’applications 3D</span><span class="sxs-lookup"><span data-stu-id="e0289-111">3D app launcher creation process</span></span>

<span data-ttu-id="e0289-112">La création d’un lanceur d’applications 3D comporte trois étapes :</span><span class="sxs-lookup"><span data-stu-id="e0289-112">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="e0289-113">Conception et concept (cet article)</span><span class="sxs-lookup"><span data-stu-id="e0289-113">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="e0289-114">Modélisation et exportation</span><span class="sxs-lookup"><span data-stu-id="e0289-114">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="e0289-115">Intégration dans votre application :</span><span class="sxs-lookup"><span data-stu-id="e0289-115">Integrating it into your application:</span></span>
    * [<span data-ttu-id="e0289-116">Applications UWP</span><span class="sxs-lookup"><span data-stu-id="e0289-116">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="e0289-117">Applications Win32</span><span class="sxs-lookup"><span data-stu-id="e0289-117">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="e0289-118">Principes de conception</span><span class="sxs-lookup"><span data-stu-id="e0289-118">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="e0289-119">Fantastique, encore familier</span><span class="sxs-lookup"><span data-stu-id="e0289-119">Fantastic yet familiar</span></span>

<span data-ttu-id="e0289-120">L’environnement Windows Mixed Reality dans lequel se trouve votre lanceur d’applications est une partie familière, une partie fantastique/science-fi.</span><span class="sxs-lookup"><span data-stu-id="e0289-120">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="e0289-121">Les meilleurs lanceurs suivent les règles de ce monde.</span><span class="sxs-lookup"><span data-stu-id="e0289-121">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="e0289-122">Pensez à la façon dont vous pouvez prendre un objet représentatif familier de votre application, mais pliez certaines règles de réalité réelle.</span><span class="sxs-lookup"><span data-stu-id="e0289-122">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="e0289-123">La magie se produira.</span><span class="sxs-lookup"><span data-stu-id="e0289-123">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="e0289-124">Peu</span><span class="sxs-lookup"><span data-stu-id="e0289-124">Intuitive</span></span>

<span data-ttu-id="e0289-125">Lorsque vous examinez le lanceur d’applications, son objectif est de lancer votre application. il doit être évident et ne devrait pas provoquer de confusion.</span><span class="sxs-lookup"><span data-stu-id="e0289-125">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="e0289-126">Par exemple, assurez-vous que votre lanceur est un représentant évident et évident de votre application qu’il ne sera pas confondu avec un morceau de décor dans la maison de la falaise.</span><span class="sxs-lookup"><span data-stu-id="e0289-126">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="e0289-127">Votre lanceur d’applications doit inviter des personnes à les toucher/sélectionner.</span><span class="sxs-lookup"><span data-stu-id="e0289-127">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="e0289-128">![Exemple : nouveau lanceur d’applications de note 3D](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-128">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e0289-129">*Exemple de lanceur d’application 3D note (application fictive)*</span><span class="sxs-lookup"><span data-stu-id="e0289-129">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="e0289-130">Échelle personnelle</span><span class="sxs-lookup"><span data-stu-id="e0289-130">Home scale</span></span>

<span data-ttu-id="e0289-131">les lanceurs d’applications 3D qui vivent dans la maison de la falaise et leur taille par défaut doivent avoir un sens avec les autres objets « physiques » de l’espace.</span><span class="sxs-lookup"><span data-stu-id="e0289-131">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="e0289-132">Si vous placez votre lanceur à côté, par exemple, d’une usine de maison ou de meubles, vous devez vous sentir à la maison, à la taille.</span><span class="sxs-lookup"><span data-stu-id="e0289-132">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="e0289-133">Un bon point de départ consiste à voir comment il s’agit de 30 centimètres cubes, mais n’oubliez pas que les utilisateurs peuvent le mettre à l’échelle s’ils le souhaitent.</span><span class="sxs-lookup"><span data-stu-id="e0289-133">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="e0289-134">En toute possession</span><span class="sxs-lookup"><span data-stu-id="e0289-134">Own-able</span></span>

<span data-ttu-id="e0289-135">Le lanceur d’application doit ressembler à un objet qu’une personne peut avoir dans son espace.</span><span class="sxs-lookup"><span data-stu-id="e0289-135">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="e0289-136">Elles seront virtuellement entourées de ces éléments, de sorte que le lanceur doit avoir le même aspect que quelque chose que l’utilisateur a été jugé suffisamment souhaitable pour se rendre à la recherche et rester à proximité.</span><span class="sxs-lookup"><span data-stu-id="e0289-136">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="e0289-137">![Exemple : lanceur d’applications Astro Warp 3D](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-137">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e0289-138">*Exemple de lanceur d’application Astro Warp 3D (application fictive)*</span><span class="sxs-lookup"><span data-stu-id="e0289-138">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="e0289-139">Reconnaissable</span><span class="sxs-lookup"><span data-stu-id="e0289-139">Recognizable</span></span>

<span data-ttu-id="e0289-140">Votre lanceur d’applications 3D doit instantanément exprimer « la personnalisation de votre application » aux personnes qui l’affichent.</span><span class="sxs-lookup"><span data-stu-id="e0289-140">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="e0289-141">Si votre application contient un caractère en étoile ou un objet particulièrement identifiable, nous vous recommandons de l’utiliser en tant que partie significative de votre conception.</span><span class="sxs-lookup"><span data-stu-id="e0289-141">If you have a star character or an especially identifiable object in your app, we recommend using that as a significant part of your design.</span></span> <span data-ttu-id="e0289-142">Dans un monde de réalité mixte, un objet attire davantage l’intérêt des utilisateurs qu’un seul logo.</span><span class="sxs-lookup"><span data-stu-id="e0289-142">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="e0289-143">Les objets reconnaissables communiquent la personnalisation rapidement et clairement.</span><span class="sxs-lookup"><span data-stu-id="e0289-143">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="e0289-144">Dosage</span><span class="sxs-lookup"><span data-stu-id="e0289-144">Volumetric</span></span>

<span data-ttu-id="e0289-145">Votre application mérite plus que simplement placer votre logo sur un plan plat et l’appeler une journée.</span><span class="sxs-lookup"><span data-stu-id="e0289-145">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="e0289-146">Votre lanceur doit ressembler à un objet physique passionnant et 3D dans l’espace de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e0289-146">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="e0289-147">Une bonne approche consiste à imaginer que votre application allait avoir une info-bulle dans la parade du jour de Thanksgiving de Macy.</span><span class="sxs-lookup"><span data-stu-id="e0289-147">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="e0289-148">Demandez-vous ce que les gens étaient vraiment en mesure de tomber dans la rue ?</span><span class="sxs-lookup"><span data-stu-id="e0289-148">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="e0289-149">Que feriez-vous de tous les angles d’affichage ?</span><span class="sxs-lookup"><span data-stu-id="e0289-149">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e0289-150">![](images/20171016-140436-mixedreality-640px.jpg) *Logo* logo uniquement</span><span class="sxs-lookup"><span data-stu-id="e0289-150">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e0289-151">![Plus reconnaissable avec un caractère ](images/20171016-140557-mixedreality-640px.jpg) *plus reconnaissable avec un caractère*</span><span class="sxs-lookup"><span data-stu-id="e0289-151">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="e0289-152">![Une approche plate, pas étonnamment surprenant, est une approche plate plate ](images/20171016-155101-mixedreality-640px.jpg) *, pas étonnamment surprenant, à plat*</span><span class="sxs-lookup"><span data-stu-id="e0289-152">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e0289-153">![L’approche volumétrique illustre mieux l’approche volumétrique de votre application et ](images/20171016-161407-mixedreality-640px.jpg) *améliore votre application*</span><span class="sxs-lookup"><span data-stu-id="e0289-153">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="e0289-154">Conseils pour les bons modèles 3D</span><span class="sxs-lookup"><span data-stu-id="e0289-154">Tips for good 3D models</span></span>

* <span data-ttu-id="e0289-155">Lors de la planification de dimensions pour votre lanceur d’applications, prenez un cube de 30 cm environ.</span><span class="sxs-lookup"><span data-stu-id="e0289-155">When planning dimensions for your app launcher, shoot for roughly a 30-cm cube.</span></span> <span data-ttu-id="e0289-156">Par conséquent, un ratio de taille de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="e0289-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="e0289-157">Les modèles doivent être sous les polygones 10 000.</span><span class="sxs-lookup"><span data-stu-id="e0289-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="e0289-158">En savoir plus sur le nombre de triangles et les niveaux de détail (LODs)</span><span class="sxs-lookup"><span data-stu-id="e0289-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="e0289-159">Testez sur un casque immersif.</span><span class="sxs-lookup"><span data-stu-id="e0289-159">Test on an immersive headset.</span></span>
* <span data-ttu-id="e0289-160">Créez des détails dans la géométrie de votre modèle, dans la mesure du possible, ne vous fiez pas aux textures pour des détails.</span><span class="sxs-lookup"><span data-stu-id="e0289-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="e0289-161">Créez une géométrie fermée « eau serrée ».</span><span class="sxs-lookup"><span data-stu-id="e0289-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="e0289-162">Aucun trou n’est modélisé dans.</span><span class="sxs-lookup"><span data-stu-id="e0289-162">No holes that aren't modeled in.</span></span>
* <span data-ttu-id="e0289-163">Utilisez des matériaux naturels dans votre objet.</span><span class="sxs-lookup"><span data-stu-id="e0289-163">Use natural materials in your object.</span></span> <span data-ttu-id="e0289-164">Imaginez que vous le concevez dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="e0289-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="e0289-165">Assurez-vous que votre modèle lit bien des distances et des tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="e0289-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="e0289-166">Lorsque votre modèle est prêt à l’emploi, lisez les [instructions relatives](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)à l’exportation de ressources.</span><span class="sxs-lookup"><span data-stu-id="e0289-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="e0289-167">![Modèle avec des détails subtils dans la texture](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e0289-168">*Modèle avec des détails subtils dans la texture*</span><span class="sxs-lookup"><span data-stu-id="e0289-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="e0289-169">À éviter</span><span class="sxs-lookup"><span data-stu-id="e0289-169">What to avoid</span></span>

* <span data-ttu-id="e0289-170">N’utilisez pas de détails à contraste élevé ni de modèles et de textures de petite taille, occupés.</span><span class="sxs-lookup"><span data-stu-id="e0289-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="e0289-171">N’utilisez pas de géométrie fine : elle ne fonctionne pas bien à distance et fera mal l’alias.</span><span class="sxs-lookup"><span data-stu-id="e0289-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="e0289-172">Ne laissez pas les parties de votre modèle s’étendre trop au-delà du ratio de taille de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="e0289-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="e0289-173">Il va créer des problèmes de mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="e0289-173">It will create scaling problems.</span></span>

<span data-ttu-id="e0289-174">![Évitez les grands contrastes, les petits modèles occupés](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e0289-175">*Évitez les modèles à contraste élevé, les petits et les plus occupés*</span><span class="sxs-lookup"><span data-stu-id="e0289-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="e0289-176">Comment gérer le type</span><span class="sxs-lookup"><span data-stu-id="e0289-176">How to handle type</span></span>

* <span data-ttu-id="e0289-177">Nous vous recommandons d’utiliser votre type de lancement d’application 1/3 (ou plus).</span><span class="sxs-lookup"><span data-stu-id="e0289-177">We recommend your type takes up about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="e0289-178">Le type est l’élément principal qui donne aux gens une idée que votre lanceur est, en fait, un lanceur, ce qui est intéressant s’il est substantiel.</span><span class="sxs-lookup"><span data-stu-id="e0289-178">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s substantial.</span></span>
* <span data-ttu-id="e0289-179">Évitez de rendre le type Super étendu : essayez de le conserver dans les limites des dimensions principales des lanceurs d’applications (plus ou moins).</span><span class="sxs-lookup"><span data-stu-id="e0289-179">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="e0289-180">Le type plat peut fonctionner, mais il peut être difficile à afficher à partir de certains angles et dans certains environnements.</span><span class="sxs-lookup"><span data-stu-id="e0289-180">Flat type can work, but it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="e0289-181">Vous pouvez envisager de placer un objet solide ou un fond en arrière-plan pour faciliter cette opération.</span><span class="sxs-lookup"><span data-stu-id="e0289-181">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="e0289-182">L’ajout d’une dimension à votre type semble agréable en 3D.</span><span class="sxs-lookup"><span data-stu-id="e0289-182">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="e0289-183">L’ombrage des côtés du type d’une couleur plus sombre peut contribuer à la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="e0289-183">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e0289-184">![Le type plat sans fond peut être difficile à afficher à partir de certains angles et dans certains environnements, ](images/flattype-640px.png) *le type plat sans fond peut être difficile à afficher à partir de certains angles et dans certains environnements*</span><span class="sxs-lookup"><span data-stu-id="e0289-184">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e0289-185">![Le type avec une zone de fond intégrée peut fonctionner correctement ](images/flattypeandbkg-640px.png) *avec un fond intégré qui peut fonctionner correctement*</span><span class="sxs-lookup"><span data-stu-id="e0289-185">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e0289-186">![Le type extrudé peut fonctionner correctement si vous ombrer les côtés le ](images/20171016-160221-mixedreality-640px.jpg) *type extrudé peut fonctionner correctement si vous Nuancez les côtés*</span><span class="sxs-lookup"><span data-stu-id="e0289-186">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="e0289-187">**Tapez les couleurs qui fonctionnent**</span><span class="sxs-lookup"><span data-stu-id="e0289-187">**Type colors that work**</span></span>

* <span data-ttu-id="e0289-188">Blancs</span><span class="sxs-lookup"><span data-stu-id="e0289-188">White</span></span>
* <span data-ttu-id="e0289-189">Noir</span><span class="sxs-lookup"><span data-stu-id="e0289-189">Black</span></span>
* <span data-ttu-id="e0289-190">Couleur semi-saturée vive</span><span class="sxs-lookup"><span data-stu-id="e0289-190">Bright semi-saturated color</span></span>

<span data-ttu-id="e0289-191">![Tapez les couleurs qui fonctionnent.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-191">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e0289-192">*Tapez les couleurs qui fonctionnent*</span><span class="sxs-lookup"><span data-stu-id="e0289-192">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="e0289-193">Couleurs à éviter</span><span class="sxs-lookup"><span data-stu-id="e0289-193">Colors to avoid</span></span>

<span data-ttu-id="e0289-194">Les couleurs de type qui sont à l’origine des problèmes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0289-194">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="e0289-195">Mi-tons</span><span class="sxs-lookup"><span data-stu-id="e0289-195">Mid-tones</span></span>
* <span data-ttu-id="e0289-196">Gris</span><span class="sxs-lookup"><span data-stu-id="e0289-196">Gray</span></span>
* <span data-ttu-id="e0289-197">Couleurs sursaturées ou couleurs désaturées</span><span class="sxs-lookup"><span data-stu-id="e0289-197">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="e0289-198">![Tapez les couleurs qui provoquent des problèmes.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-198">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e0289-199">*Couleurs de type qui provoquent des problèmes*</span><span class="sxs-lookup"><span data-stu-id="e0289-199">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="e0289-200">Éclairage</span><span class="sxs-lookup"><span data-stu-id="e0289-200">Lighting</span></span>

<span data-ttu-id="e0289-201">L’éclairage de votre lanceur d’applications provient de l’environnement de la maison de la falaise.</span><span class="sxs-lookup"><span data-stu-id="e0289-201">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="e0289-202">Veillez à tester votre lanceur à plusieurs endroits de la maison, afin qu’il soit parfait dans le ciel et dans les ombres.</span><span class="sxs-lookup"><span data-stu-id="e0289-202">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="e0289-203">La bonne nouvelle, c’est que si vous avez suivi les autres conseils de conception de ce document, votre lanceur doit être en bonne forme pour la plupart des éclairages de la maison de la falaise.</span><span class="sxs-lookup"><span data-stu-id="e0289-203">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="e0289-204">Les bonnes places pour tester la manière dont votre lanceur regarde dans les différentes lumières de l’environnement sont le Studio, la salle de support, n’importe où et sur le patio Back (la zone concrète avec la pelouse).</span><span class="sxs-lookup"><span data-stu-id="e0289-204">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="e0289-205">Un autre bon test consiste à le placer en demi-feu et demi-ombre et à voir à quoi il ressemble.</span><span class="sxs-lookup"><span data-stu-id="e0289-205">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="e0289-206">![Assurez-vous que votre lanceur semble parfait en clair et dans les ombres.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0289-206">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e0289-207">*Assurez-vous que votre lanceur semble parfait dans le ciel et dans les ombres*</span><span class="sxs-lookup"><span data-stu-id="e0289-207">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="e0289-208">Texturation</span><span class="sxs-lookup"><span data-stu-id="e0289-208">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="e0289-209">Création de vos Textures</span><span class="sxs-lookup"><span data-stu-id="e0289-209">Authoring your textures</span></span>

<span data-ttu-id="e0289-210">Le format de fin de votre lanceur d’application 3D est un fichier. GLB, qui est créé à l’aide du pipeline PBR (rendu physique).</span><span class="sxs-lookup"><span data-stu-id="e0289-210">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="e0289-211">Il peut s’agir d’un processus délicat. à présent, nous vous conseillons d’employer un artiste technique si vous ne l’avez pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="e0289-211">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="e0289-212">Si vous êtes un peu vos propres méthodes-er, prenez le temps de [Rechercher et d’apprendre la terminologie du PBR](https://wiki.polycount.com/wiki/PBR) et ce qui se passe en coulisse avant de commencer vous aidera à éviter les erreurs courantes.</span><span class="sxs-lookup"><span data-stu-id="e0289-212">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="e0289-213">![Exemple : nouvelle application de note](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="e0289-213">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="e0289-214">*Exemple de lanceur d’application 3D note (application fictive)*</span><span class="sxs-lookup"><span data-stu-id="e0289-214">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="e0289-215">Outil de création recommandé</span><span class="sxs-lookup"><span data-stu-id="e0289-215">Recommended authoring tool</span></span>

<span data-ttu-id="e0289-216">Nous vous recommandons d’utiliser l’outil de création de [substance](https://www.allegorithmic.com/products/substance-painter) par Allegorithmic pour créer votre fichier final.</span><span class="sxs-lookup"><span data-stu-id="e0289-216">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="e0289-217">Si vous n’êtes pas familiarisé avec la création de nuanceurs PBR dans l’outil de création de substance, voici un [didacticiel](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="e0289-217">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="e0289-218">(Vous pouvez également utiliser la [couche 3D](https://3dcoat.com/home/), [Quixel suite 2](https://quixel.se/suite2/)ou [marmoset Toolbag](https://www.marmoset.co/toolbag/) si vous êtes plus familiarisé avec l’un d’eux).</span><span class="sxs-lookup"><span data-stu-id="e0289-218">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="e0289-219">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="e0289-219">Best practices</span></span>

* <span data-ttu-id="e0289-220">Si votre objet de lanceur d’application a été créé pour le PBR, il doit être facile de le convertir pour l’environnement de la maison de la falaise.</span><span class="sxs-lookup"><span data-stu-id="e0289-220">If your app launcher object was authored for PBR, it should be straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="e0289-221">Notre nuanceur attend un flot de travail Metal/grossiste : le nuanceur PBR non réel est une fac-similé de fermeture.</span><span class="sxs-lookup"><span data-stu-id="e0289-221">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="e0289-222">Lorsque vous exportez vos Textures, gardez à l’esprit les [tailles de texture recommandées](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .</span><span class="sxs-lookup"><span data-stu-id="e0289-222">When exporting your textures, keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="e0289-223">Veillez à créer vos objets pour l’éclairage en temps réel, à savoir :</span><span class="sxs-lookup"><span data-stu-id="e0289-223">Make sure to build your objects for real-time lighting—this means:</span></span>
  * <span data-ttu-id="e0289-224">Évitez les ombres cuites, ou les ombres peintes</span><span class="sxs-lookup"><span data-stu-id="e0289-224">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="e0289-225">Éviter l’éclairage cuit dans les textures</span><span class="sxs-lookup"><span data-stu-id="e0289-225">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="e0289-226">Utilisez l’un des packages de création de matériel PBR pour obtenir les mappages appropriés générés pour notre nuanceur</span><span class="sxs-lookup"><span data-stu-id="e0289-226">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="e0289-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0289-227">See also</span></span>

* [<span data-ttu-id="e0289-228">Créer des modèles 3D à utiliser dans la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="e0289-228">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="e0289-229">Implémenter des lanceurs d’applications 3D (applications UWP)</span><span class="sxs-lookup"><span data-stu-id="e0289-229">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="e0289-230">Implémenter des lanceurs d’applications 3D (applications Win32)</span><span class="sxs-lookup"><span data-stu-id="e0289-230">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
