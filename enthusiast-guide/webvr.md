---
title: Utilisation de WebVR avec Windows Mixed Reality
description: Décrit WebVR et comment l’utiliser avec Microsoft Edge sur des casques Windows de réalité mixte.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, WebVR, Edge, Microsoft Edge, navigation Web
ms.openlocfilehash: e57ad060a1a539e90631d1b9f1808d1e8466e669
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174340"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="a8dda-104">Utilisation de WebVR avec Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a8dda-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT] 
><span data-ttu-id="a8dda-105">La plupart des navigateurs Web modernes ont déconseillé la prise en charge de WebVR en faveur de WebXR, la nouvelle norme pour la création d’expériences Web immersifs pour les casques VR.</span><span class="sxs-lookup"><span data-stu-id="a8dda-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="a8dda-106">Installez la nouvelle prise en charge de [Microsoft Edge](using-microsoft-edge.md) pour WebXR.</span><span class="sxs-lookup"><span data-stu-id="a8dda-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="a8dda-107">Qu'est-ce que WebVR ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-107">What is WebVR?</span></span>

<span data-ttu-id="a8dda-108">[WebVR](https://webvr.info) est une spécification ouverte qui permet d’expérimenter VR dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="a8dda-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="a8dda-109">Si un site Web implémente la prise en charge de WebVR et fournit du contenu 3D, il peut afficher le contenu immersif dans le casque, avec le consentement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a8dda-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="a8dda-110">Quelle est la différence entre WebVR et la navigation sur le Web en VR ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-110">What is the difference between WebVR and browsing the web in VR?</span></span>

<span data-ttu-id="a8dda-111">WebVR est une technologie qui permet à un auteur de site Web d’ajouter des fonctionnalités VR à une page.</span><span class="sxs-lookup"><span data-stu-id="a8dda-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="a8dda-112">L’API WebVR est utilisée par une page pour afficher le contenu 3D (par exemple, une vidéo de 360 degrés, un modèle 3D ou un jeu 3D) à l’intégralité de votre casque.</span><span class="sxs-lookup"><span data-stu-id="a8dda-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="a8dda-113">**Exemple :** Affichage d’une vidéo 360 sur [CNN.com/VR](http://cnn.com/vr).</span><span class="sxs-lookup"><span data-stu-id="a8dda-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="a8dda-114">Si une page prend en charge WebVR, elle ajoute un bouton ou un autre élément d’interface utilisateur sur lequel vous pouvez cliquer pour entrer VR.</span><span class="sxs-lookup"><span data-stu-id="a8dda-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="a8dda-115">La navigation sur le Web en VR signifie que vous utilisez le navigateur Edge pendant que vous portez votre casque, en tant qu’ardoise d’application 2D dans le Cliffhouse.</span><span class="sxs-lookup"><span data-stu-id="a8dda-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="a8dda-116">Tous les sites Web prennent-ils en charge WebVR ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-116">Do all websites support WebVR?</span></span>

<span data-ttu-id="a8dda-117">Non.</span><span class="sxs-lookup"><span data-stu-id="a8dda-117">No.</span></span> <span data-ttu-id="a8dda-118">Les auteurs de sites Web doivent s’abonner à l’utilisation de WebVR. en outre, ils peuvent créer des sites qui sont optimisés pour des navigateurs, des casques et des contrôleurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="a8dda-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="a8dda-119">Par exemple, un contenu WebVR est optimisé pour les périphériques mobile VR uniquement.</span><span class="sxs-lookup"><span data-stu-id="a8dda-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="a8dda-120">En outre, gardez à l’esprit que les sites Web doivent créer et fournir explicitement du contenu WebVR.</span><span class="sxs-lookup"><span data-stu-id="a8dda-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="a8dda-121">Le nombre de sites dont le contenu est compatible WebVR augmente chaque jour.</span><span class="sxs-lookup"><span data-stu-id="a8dda-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="a8dda-122">Puis-je utiliser mon vive/Oculus, etc. pour afficher le contenu de WebVR dans Microsoft Edge ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge?</span></span>

<span data-ttu-id="a8dda-123">Non.</span><span class="sxs-lookup"><span data-stu-id="a8dda-123">No.</span></span> <span data-ttu-id="a8dda-124">Vous devez utiliser un casque Windows Mixed Reality pour utiliser WebVR dans Edge.</span><span class="sxs-lookup"><span data-stu-id="a8dda-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="a8dda-125">Toutefois, vous pourrez peut-être accéder au contenu de WebVR dans un autre navigateur. consultez la liste complète des appareils et navigateurs compatibles à l’adresse suivante : [WebVR. Rocks](http://webvr.rocks/).</span><span class="sxs-lookup"><span data-stu-id="a8dda-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="a8dda-126">Où puis-je trouver la documentation du développeur WebVR ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-126">Where can I find the WebVR developer documentation?</span></span>

<span data-ttu-id="a8dda-127">La documentation du développeur se trouve ici : [WebVR Developer documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span><span class="sxs-lookup"><span data-stu-id="a8dda-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="a8dda-128">J’ai trouvé un site Web avec WebVR qui ne fonctionne pas dans Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a8dda-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="a8dda-129">Que faire ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-129">What do I do?</span></span>

<span data-ttu-id="a8dda-130">Vous pouvez signaler des sites rompus directement à l’équipe du navigateur Microsoft Edge dans le [suivi des problèmes](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)ou via Twitter à l’aide de [#EdgeBug mot-dièse](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span><span class="sxs-lookup"><span data-stu-id="a8dda-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="a8dda-131">Vous pouvez également consigner les bogues à l’aide de l’application Hub de commentaires Windows sous catégorie :</span><span class="sxs-lookup"><span data-stu-id="a8dda-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="a8dda-132">Problèmes liés au site Web de > Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a8dda-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="a8dda-133">Qu’est-ce qu’une bonne page pour tester si WebVR fonctionne ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-133">What is a good page to test if WebVR is working?</span></span>

<span data-ttu-id="a8dda-134">Consultez les [exemples webvr.info](http://webvr.info/samples/XX-vr-controllers.html).</span><span class="sxs-lookup"><span data-stu-id="a8dda-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="a8dda-135">Comment faire configurer WebVR ?</span><span class="sxs-lookup"><span data-stu-id="a8dda-135">How do I set up WebVR?</span></span>

<span data-ttu-id="a8dda-136">Pour expérimenter du contenu WebVR sur un casque Windows Mixed Reality (à l’aide d’un matériel ou d’une simulation), vous devez :</span><span class="sxs-lookup"><span data-stu-id="a8dda-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>
1. <span data-ttu-id="a8dda-137">Vérifiez que votre casque est connecté.</span><span class="sxs-lookup"><span data-stu-id="a8dda-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="a8dda-138">Lancez Microsoft Edge sur le bureau ou dans une réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="a8dda-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="a8dda-139">Accédez à une page WebVR activée.</span><span class="sxs-lookup"><span data-stu-id="a8dda-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="a8dda-140">Cliquez sur le bouton ENTER VR dans la page (l’emplacement et la représentation visuelle de ce bouton peuvent varier selon le site Web).</span><span class="sxs-lookup"><span data-stu-id="a8dda-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="a8dda-141">Il peut ressembler à ceci : </span><span class="sxs-lookup"><span data-stu-id="a8dda-141">It may look similar to:</span></span>\
   ![Image de lunettes](images/75px-enter-vr.png)
5. <span data-ttu-id="a8dda-143">La première fois que vous essayez d’entrer VR sur un domaine spécifique, le navigateur vous demande le consentement d’utiliser la vue immersive, cliquez sur Oui :</span><span class="sxs-lookup"><span data-stu-id="a8dda-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![Interface utilisateur de consentement affichée lors de la première tentative d’entrée de VR sur un domaine particulier](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="a8dda-145">Votre casque doit commencer à afficher le contenu WebVR.</span><span class="sxs-lookup"><span data-stu-id="a8dda-145">Your headset should begin displaying the WebVR content.</span></span>


## <a name="see-also"></a><span data-ttu-id="a8dda-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8dda-146">See also</span></span>

* [<span data-ttu-id="a8dda-147">Résolution des problèmes de > WebVR</span><span class="sxs-lookup"><span data-stu-id="a8dda-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="a8dda-148">Comment accéder à votre première expérience WebVR</span><span class="sxs-lookup"><span data-stu-id="a8dda-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="a8dda-149">Utilisation de jeux et d’applications dans Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a8dda-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="a8dda-150">Votre foyer de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="a8dda-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="a8dda-151">Système de suivi</span><span class="sxs-lookup"><span data-stu-id="a8dda-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="a8dda-152">Contrôleurs de mouvement</span><span class="sxs-lookup"><span data-stu-id="a8dda-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="a8dda-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="a8dda-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="a8dda-154">Envoi de commentaires</span><span class="sxs-lookup"><span data-stu-id="a8dda-154">Filing feedback</span></span>](filing-feedback.md)
