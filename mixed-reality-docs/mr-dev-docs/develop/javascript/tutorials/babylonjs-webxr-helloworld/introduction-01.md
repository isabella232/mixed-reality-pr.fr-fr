---
title: Présentation des didacticiels de babylon.js et WebXR
description: Suivez ce cours pour apprendre à utiliser babylon.js et à créer une application de réalité mixte de base.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: réalité mixte, javascript, tutoriel, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web immersif
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600118"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="be666-104">Didacticiel : créez votre première application WebXR à l’aide de babylon.js</span><span class="sxs-lookup"><span data-stu-id="be666-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="be666-105">Ce didacticiel vous montre comment créer une application de réalité mixte de base à l’aide de babylon.js et de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="be666-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="be666-106">L’application que vous allez développer vous permettra de créer un cube, de le faire pivoter pour en faire apparaître les autres faces et d’ajouter des interactions.</span><span class="sxs-lookup"><span data-stu-id="be666-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="be666-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="be666-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="be666-108">Configurer un environnement de développement</span><span class="sxs-lookup"><span data-stu-id="be666-108">Set up a development environment</span></span>
> * <span data-ttu-id="be666-109">API babylon.js pour créer des éléments 3D de base</span><span class="sxs-lookup"><span data-stu-id="be666-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="be666-110">Créer une page web</span><span class="sxs-lookup"><span data-stu-id="be666-110">Create a new web page</span></span>
> * <span data-ttu-id="be666-111">Interagir avec des éléments 3D</span><span class="sxs-lookup"><span data-stu-id="be666-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="be666-112">Exécuter l’application dans un simulateur Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="be666-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be666-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="be666-113">Prerequisites</span></span>

* <span data-ttu-id="be666-114">Navigateur WebXR pris en charge, par exemple [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span><span class="sxs-lookup"><span data-stu-id="be666-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="be666-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="be666-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="be666-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="be666-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="be666-117">Facultatif : [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10) si vous souhaitez utiliser un simulateur Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="be666-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="be666-118">Facultatif : [simulateur Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="be666-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="be666-119">Prise en main</span><span class="sxs-lookup"><span data-stu-id="be666-119">Getting started</span></span>

<span data-ttu-id="be666-120">pour créer ce projet à partir de zéro, commencez par un projet Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="be666-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="be666-121">L’utilisation de VSCode n’est pas obligatoire, mais nous l’utiliserons pour des raisons pratiques tout au long du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="be666-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="be666-122">Les développeurs JavaScript plus expérimentés peuvent utiliser n’importe quel autre éditeur de leur choix, même le très simple Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="be666-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="be666-123">Téléchargez le fichier unique [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) ou utilisez une version en ligne qui se trouve sur le [site web officiel babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span><span class="sxs-lookup"><span data-stu-id="be666-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="be666-124">Vous pouvez également cloner l’intégralité du projet babylon.js à partir de [GitHub](https://github.com/BabylonJS/Babylon.js)</span><span class="sxs-lookup"><span data-stu-id="be666-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="be666-125">Créez un fichier vide et enregistrez-le en tant que page HTML, par exemple index.html</span><span class="sxs-lookup"><span data-stu-id="be666-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="be666-126">Créez un balisage HTML de base et référencez le fichier javascript babylon.js .</span><span class="sxs-lookup"><span data-stu-id="be666-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="be666-127">Le code final est le suivant :</span><span class="sxs-lookup"><span data-stu-id="be666-127">The final code is as shown below:</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. <span data-ttu-id="be666-128">Ajoutez un élément HTML de *zone de dessin* dans le corps pour afficher le contenu de babylon.js.</span><span class="sxs-lookup"><span data-stu-id="be666-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="be666-129">Notez que la zone de dessin possède un attribut d’ID qui vous permet d’accéder plus tard à cet élément HTML à partir de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="be666-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. <span data-ttu-id="be666-130">La zone de dessin occupe toute la page web.</span><span class="sxs-lookup"><span data-stu-id="be666-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="be666-131">Cela finalise notre page web.</span><span class="sxs-lookup"><span data-stu-id="be666-131">That completes our web page.</span></span> <span data-ttu-id="be666-132">À ce stade, la page web est prête.</span><span class="sxs-lookup"><span data-stu-id="be666-132">At this point, the web page is ready.</span></span> <span data-ttu-id="be666-133">Vous pouvez l’ouvrir dans n’importe quel navigateur et vous assurer qu’aucune erreur ne s’affiche, bien qu’il n’y ait pas encore d’expérience immersive.</span><span class="sxs-lookup"><span data-stu-id="be666-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="be666-134">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="be666-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be666-135">Didacticiel suivant : 2. Préparer une scène</span><span class="sxs-lookup"><span data-stu-id="be666-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)