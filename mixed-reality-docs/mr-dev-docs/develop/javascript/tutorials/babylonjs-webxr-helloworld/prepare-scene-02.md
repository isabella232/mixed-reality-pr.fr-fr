---
title: Didacticiel Babylon.js pour préparer une scène avec des objets 3D de base
description: Apprenez à utiliser babylon.js et à ajouter des objets 3D de base à une scène.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: réalité mixte, javascript, tutoriel, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web immersif
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584502"
---
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="39662-104">Didacticiel : Préparer une scène</span><span class="sxs-lookup"><span data-stu-id="39662-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="39662-105">Découvrez comment préparer une scène et y ajouter des éléments 3D de base.</span><span class="sxs-lookup"><span data-stu-id="39662-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="39662-106">Dans ce tutoriel, vous allez apprendre à effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="39662-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="39662-107">Créer une scène</span><span class="sxs-lookup"><span data-stu-id="39662-107">Create a scene</span></span>
> * <span data-ttu-id="39662-108">Ajouter une caméra</span><span class="sxs-lookup"><span data-stu-id="39662-108">Add a camera</span></span>
> * <span data-ttu-id="39662-109">Ajouter de la lumière</span><span class="sxs-lookup"><span data-stu-id="39662-109">Add light</span></span>
> * <span data-ttu-id="39662-110">Ajouter des éléments 3D de base</span><span class="sxs-lookup"><span data-stu-id="39662-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="39662-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="39662-111">Before you begin</span></span>

<span data-ttu-id="39662-112">Au cours d’une étape précédente du tutoriel, une page web de base a été créée.</span><span class="sxs-lookup"><span data-stu-id="39662-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="39662-113">Ouvrez la page Web pour la modifier.</span><span class="sxs-lookup"><span data-stu-id="39662-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="39662-114">Créer une scène</span><span class="sxs-lookup"><span data-stu-id="39662-114">Create a scene</span></span>

<span data-ttu-id="39662-115">Une scène est l’endroit où tous les contenus seront affichés.</span><span class="sxs-lookup"><span data-stu-id="39662-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="39662-116">Il peut y avoir plusieurs scènes et il est possible de basculer entre les scènes.</span><span class="sxs-lookup"><span data-stu-id="39662-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="39662-117">En savoir plus sur la [scène babylon.js](https://doc.babylonjs.com/divingDeeper/scene).</span><span class="sxs-lookup"><span data-stu-id="39662-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="39662-118">Ajoutez la balise de script après l’élément HTML Canvas et ajoutez le code suivant pour créer une scène remplie de couleur noire :</span><span class="sxs-lookup"><span data-stu-id="39662-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    <span data-ttu-id="39662-119">Dans le code ci-dessus, nous devons créer une instance du moteur de rendu web babylon.js qui restitue une scène et raccorde des événements à la zone de dessin.</span><span class="sxs-lookup"><span data-stu-id="39662-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="39662-120">Pour plus d’informations sur le moteur, consultez la page de documentation [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span><span class="sxs-lookup"><span data-stu-id="39662-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="39662-121">La scène ne s’affiche pas par défaut.</span><span class="sxs-lookup"><span data-stu-id="39662-121">The scene is not rendered by default.</span></span> <span data-ttu-id="39662-122">N’oubliez pas qu’il peut y avoir plusieurs scènes et que vous contrôlez la scène qui est affichée.</span><span class="sxs-lookup"><span data-stu-id="39662-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="39662-123">Pour afficher la scène à plusieurs reprises sur chaque trame, exécutez le code suivant après avoir appelé la fonction *createScene* :</span><span class="sxs-lookup"><span data-stu-id="39662-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="39662-124">Ajouter d’un élément 3D de base</span><span class="sxs-lookup"><span data-stu-id="39662-124">Add basic 3D element</span></span>

1. <span data-ttu-id="39662-125">Ajoutons à présent notre première forme 3D.</span><span class="sxs-lookup"><span data-stu-id="39662-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="39662-126">Dans le monde virtuel 3D, des formes sont créées à partir de *maillages*, un grand nombre de facettes triangulaires sont jointes, chaque facette étant constituée de trois vertex.</span><span class="sxs-lookup"><span data-stu-id="39662-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="39662-127">Vous pouvez soit utiliser un maillage prédéfini, soit créer votre propre maillage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="39662-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="39662-128">Nous utiliserons un maillage de zone prédéfini, soit un cube.</span><span class="sxs-lookup"><span data-stu-id="39662-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="39662-129">Pour créer la zone, utilisez [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span><span class="sxs-lookup"><span data-stu-id="39662-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="39662-130">Les paramètres sont le nom et les options (les options sont différentes selon le type de maillage).</span><span class="sxs-lookup"><span data-stu-id="39662-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="39662-131">Ajoutez le code suivant à la fonction *createScene* :</span><span class="sxs-lookup"><span data-stu-id="39662-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="39662-132">Ouvrez la page web dans le navigateur Microsoft Edge et vérifiez le résultat.</span><span class="sxs-lookup"><span data-stu-id="39662-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="39662-133">La fenêtre du navigateur affiche une page vierge.</span><span class="sxs-lookup"><span data-stu-id="39662-133">The browser window shows a blank page.</span></span> <span data-ttu-id="39662-134">Ouvrez DevTools à l’aide du clavier et sélectionnez F12 ou Ctrl + Maj + l (Windows, Linux) ou Cmd + Option + l (macOS).</span><span class="sxs-lookup"><span data-stu-id="39662-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="39662-135">Après avoir ouvert l’onglet *Console*, vous pouvez commencer à rechercher des erreurs.</span><span class="sxs-lookup"><span data-stu-id="39662-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="39662-136">Une erreur s’affiche : « Erreur non interceptée : aucune caméra définie ».</span><span class="sxs-lookup"><span data-stu-id="39662-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="39662-137">À présent, nous devons ajouter une caméra à la scène.</span><span class="sxs-lookup"><span data-stu-id="39662-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="39662-138">Ajouter une caméra</span><span class="sxs-lookup"><span data-stu-id="39662-138">Add a camera</span></span>

1. <span data-ttu-id="39662-139">Pour afficher le monde virtuel et interagir avec celui-ci, une caméra doit être jointe à la zone de dessin.</span><span class="sxs-lookup"><span data-stu-id="39662-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="39662-140">Ajoutons la caméra de type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), qui peut pivoter autour d’une cible.</span><span class="sxs-lookup"><span data-stu-id="39662-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="39662-141">Les paramètres requis pour créer une instance de l’appareil photo sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="39662-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="39662-142">**nom** : nom de la caméra</span><span class="sxs-lookup"><span data-stu-id="39662-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="39662-143">**alpha** : position angulaire le long de l’axe longitudinal (en radians)</span><span class="sxs-lookup"><span data-stu-id="39662-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="39662-144">**bêta** : position angulaire le long de l’axe latitudinal (en radians)</span><span class="sxs-lookup"><span data-stu-id="39662-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="39662-145">**rayon** : distance par rapport à la cible</span><span class="sxs-lookup"><span data-stu-id="39662-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="39662-146">**cible** : point face auquel la caméra devrait toujours se trouver (défini par les coordonnées x-y-z)</span><span class="sxs-lookup"><span data-stu-id="39662-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="39662-147">**scène** : scène dans laquelle se trouve l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="39662-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="39662-148">Alpha, bêta, rayon et cible définissent ensemble la position de la caméra dans l’espace, comme indiqué dans le diagramme ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="39662-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![Caméra Alpha Bêta Rayon](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="39662-150">Ajoutez le code suivant à la fonction *createScene* :</span><span class="sxs-lookup"><span data-stu-id="39662-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="39662-151">Si vous vérifiez le résultat dans le navigateur, vous verrez une zone de dessin noire.</span><span class="sxs-lookup"><span data-stu-id="39662-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="39662-152">Il manque la lumière.</span><span class="sxs-lookup"><span data-stu-id="39662-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="39662-153">Ajouter de la lumière</span><span class="sxs-lookup"><span data-stu-id="39662-153">Add light</span></span>

1. <span data-ttu-id="39662-154">Il existe quatre types de lumières qui peuvent être utilisés avec une plage de propriétés d’éclairage : le point, l’orientation, le spot et la lumière hémisphérique.</span><span class="sxs-lookup"><span data-stu-id="39662-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="39662-155">Nous allons ajouter la lumière ambiante [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) comme suit :</span><span class="sxs-lookup"><span data-stu-id="39662-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="39662-156">Le code final de la page web se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="39662-156">The final code of the web page will look as follows:</span></span>

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="39662-157">Vérifiez le résultat dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="39662-157">Check the output in the browser.</span></span> <span data-ttu-id="39662-158">Vous devriez voir le cube et utiliser la souris pour faire pivoter l’appareil photo autour du cube et voir les différentes faces du cube :</span><span class="sxs-lookup"><span data-stu-id="39662-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![Scène de base avec cube](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="39662-160">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="39662-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39662-161">Didacticiel suivant : 3. Interagir avec un objet 3D</span><span class="sxs-lookup"><span data-stu-id="39662-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
