---
title: Tutoriel babylon.js pour interagir avec des objets 3D
description: Découvrez comment utiliser babylon.js et interagir avec des objets 3D.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: réalité mixte, javascript, tutoriel, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web immersif
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584518"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="3734f-104">Tutoriel : Interagir avec un objet 3D</span><span class="sxs-lookup"><span data-stu-id="3734f-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="3734f-105">Découvrez comment créer des objets 3D et des interactions pour une expérience de réalité mixte à l’aide de babylon.js.</span><span class="sxs-lookup"><span data-stu-id="3734f-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="3734f-106">Dans cette section, vous allez commencer par quelque chose de simple, comme colorier les faces d’un cube lorsque vous sélectionnez l’objet.</span><span class="sxs-lookup"><span data-stu-id="3734f-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="3734f-107">Ce tutoriel couvre les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="3734f-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3734f-108">Comment ajouter des interactions</span><span class="sxs-lookup"><span data-stu-id="3734f-108">How to add interactions</span></span>
> * <span data-ttu-id="3734f-109">Activer le mode immersif WebXR</span><span class="sxs-lookup"><span data-stu-id="3734f-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="3734f-110">Exécuter l’application sur le Simulateur Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3734f-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="3734f-111">Exécuter et déboguer l’application sur Android Chrome</span><span class="sxs-lookup"><span data-stu-id="3734f-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="3734f-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="3734f-112">Before you begin</span></span>

<span data-ttu-id="3734f-113">Au cours d’une étape précédente du tutoriel, une page web de base avec une scène a été créée.</span><span class="sxs-lookup"><span data-stu-id="3734f-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="3734f-114">Ouvrez la page web d’hébergement pour la modifier.</span><span class="sxs-lookup"><span data-stu-id="3734f-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="3734f-115">Ajouter une interaction</span><span class="sxs-lookup"><span data-stu-id="3734f-115">Add interaction</span></span>

1. <span data-ttu-id="3734f-116">Commençons par mettre à jour notre code qui crée le cube afin que celui-ci soit peint avec une couleur aléatoire.</span><span class="sxs-lookup"><span data-stu-id="3734f-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="3734f-117">Pour ce faire, nous allons ajouter des [matériaux](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) à notre cube.</span><span class="sxs-lookup"><span data-stu-id="3734f-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="3734f-118">Le matériel nous permet de spécifier la couleur et les textures, et peut être utilisé pour d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="3734f-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="3734f-119">L’apparence d’un matériau dépend de la ou des lumières utilisées dans la scène et de la façon dont il est configuré pour réagir.</span><span class="sxs-lookup"><span data-stu-id="3734f-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="3734f-120">Par exemple, diffuseColor répand la couleur sur la maille à laquelle il est attaché.</span><span class="sxs-lookup"><span data-stu-id="3734f-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="3734f-121">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3734f-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="3734f-122">Maintenant que le cube est peint avec une couleur aléatoire, ajoutons une interaction pour :</span><span class="sxs-lookup"><span data-stu-id="3734f-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="3734f-123">modifier la couleur lors d’un clic sur le cube ;</span><span class="sxs-lookup"><span data-stu-id="3734f-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="3734f-124">déplacer le cube après la modification de la couleur.</span><span class="sxs-lookup"><span data-stu-id="3734f-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="3734f-125">Pour ajouter des interactions, nous devons utiliser des [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span><span class="sxs-lookup"><span data-stu-id="3734f-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="3734f-126">Une action est lancée en réponse au déclencheur d’événement.</span><span class="sxs-lookup"><span data-stu-id="3734f-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="3734f-127">Par exemple, lorsque l’utilisateur clique sur le cube.</span><span class="sxs-lookup"><span data-stu-id="3734f-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="3734f-128">Il nous suffit d’instancier BABYLON.ActionManager et d’inscrire une action pour certains déclencheurs.</span><span class="sxs-lookup"><span data-stu-id="3734f-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="3734f-129">[BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) exécute notre fonction JavaScript lorsqu’un utilisateur clique sur le cube :</span><span class="sxs-lookup"><span data-stu-id="3734f-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="3734f-130">Le code final de la page web se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="3734f-130">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="3734f-131">Activer l’expérience immersive WebXR</span><span class="sxs-lookup"><span data-stu-id="3734f-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="3734f-132">Maintenant que la couleur de notre cube a été modifiée, nous sommes prêts à essayer l’expérience immersive.</span><span class="sxs-lookup"><span data-stu-id="3734f-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="3734f-133">Au cours de cette étape, nous allons introduire un [plan](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span><span class="sxs-lookup"><span data-stu-id="3734f-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="3734f-134">Le cube sera suspendu dans les airs et un sol s’affichera en dessous.</span><span class="sxs-lookup"><span data-stu-id="3734f-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="3734f-135">Pour ajouter le sol, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3734f-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="3734f-136">Cela crée un sol simple de 4x4 mètres.</span><span class="sxs-lookup"><span data-stu-id="3734f-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="3734f-137">Afin d’ajouter la prise en charge de WebXR, nous devons appeler *createDefaultXRExperienceAsync*, qui a pour résultat *Promesse*.</span><span class="sxs-lookup"><span data-stu-id="3734f-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="3734f-138">Ajoutez ce code à la fin de la fonction *createScene* au lieu de *renvoyer la scène ;*  :</span><span class="sxs-lookup"><span data-stu-id="3734f-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="3734f-139">Dans la mesure où la fonction *createScene* renvoie maintenant une promesse au lieu d’une scène, nous devons modifier la façon dont les fonctions *createScene* et *engine.runRenderLoop* sont appelées.</span><span class="sxs-lookup"><span data-stu-id="3734f-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="3734f-140">Remplacez les appels actuels de ces fonctions, qui se trouvent juste avant la balise *\</script>* , par le code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="3734f-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="3734f-141">Le code final de la page web se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="3734f-141">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="3734f-142">Le code ci-dessus génère la sortie suivante dans la fenêtre du navigateur : ![scène WebXR](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="3734f-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="3734f-143">Exécuter sur un Simulateur Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3734f-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="3734f-144">[Activez le Simulateur Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) si vous ne l’avez pas encore fait.</span><span class="sxs-lookup"><span data-stu-id="3734f-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="3734f-145">Sélectionnez le bouton VR immersive dans le coin inférieur droit : ![bouton VR immersive](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="3734f-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="3734f-146">Cette action lance la fenêtre Simulateur Windows Mixed Reality comme illustré ci-dessous : ![portail de réalité mixte](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="3734f-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="3734f-147">Utilisez les touches W, A, S et D de votre clavier pour avancer, revenir à gauche et à droite en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="3734f-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="3734f-148">Utilisez la simulation de main pour cibler le cube et appuyez sur la touche Entrée de votre clavier pour exécuter l’action de clic.</span><span class="sxs-lookup"><span data-stu-id="3734f-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="3734f-149">La couleur du cube change et le cube se déplace vers une nouvelle position.</span><span class="sxs-lookup"><span data-stu-id="3734f-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="3734f-150">Lorsque vous ciblez le cube, assurez-vous que la fin du rayon émanant de la main (cercle blanc) croise le cube comme sur l’image ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="3734f-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="3734f-151">En savoir plus sur [Pointer et valider avec les mains](../../../../design/point-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="3734f-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="3734f-152">Exécuter et déboguer sur un appareil Android</span><span class="sxs-lookup"><span data-stu-id="3734f-152">Run and debug on Android device</span></span>

<span data-ttu-id="3734f-153">Pour activer le débogage sur votre appareil Android, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3734f-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3734f-154">Prérequis</span><span class="sxs-lookup"><span data-stu-id="3734f-154">Prerequisites</span></span>

* <span data-ttu-id="3734f-155">Un serveur web qui sert des pages HTML statiques dans un contexte sécurisé (https:// ou via le réacheminement de port sur localhost) sur un ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="3734f-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="3734f-156">Par exemple, tirez parti du package npm *serve* en tant que simple serveur web léger traitant des fichiers HTML statiques, consultez plus de [npm de service](https://github.com/vercel/serve#readme)</span><span class="sxs-lookup"><span data-stu-id="3734f-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="3734f-157">Appareil livré à l’origine avec Google Play Store et devant exécuter Android 7.0 ou une version plus récente</span><span class="sxs-lookup"><span data-stu-id="3734f-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="3734f-158">Dernière version de [Google Chrome](https://support.google.com/chrome/answer/95346) sur la station de travail de développement et sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="3734f-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="3734f-159">Pour vérifier que l’appareil est correctement configuré pour exécuter WebXR, accédez à un [exemple de page WebXR](https://immersive-web.github.io/webxr-samples/) sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="3734f-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="3734f-160">Un message doit s’afficher, par exemple :</span><span class="sxs-lookup"><span data-stu-id="3734f-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="3734f-161">Votre navigateur prend en charge WebXR et peut exécuter des expériences de réalité virtuelle et de réalité augmentée si vous disposez du matériel approprié.</span><span class="sxs-lookup"><span data-stu-id="3734f-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="3734f-162">Activez le mode développeur et le débogage USB sur un appareil Android.</span><span class="sxs-lookup"><span data-stu-id="3734f-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="3734f-163">Pour plus d’informations sur la façon de procéder pour votre version d’Android, consultez la page de documentation officielle [Configurer les options de développeur sur appareil](https://developer.android.com/studio/debug/dev-options)</span><span class="sxs-lookup"><span data-stu-id="3734f-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="3734f-164">Ensuite, connectez l’appareil Android à votre ordinateur de développement ou ordinateur portable par le biais d’un câble USB</span><span class="sxs-lookup"><span data-stu-id="3734f-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="3734f-165">Assurez-vous que le serveur web sur l’ordinateur de développement est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3734f-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="3734f-166">Par exemple, accédez au dossier racine contenant votre page d’hébergement web (index.html) et exécutez le code suivant (en supposant que vous utilisez le package npm serve) :</span><span class="sxs-lookup"><span data-stu-id="3734f-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="3734f-167">Ouvrez Google Chrome sur votre ordinateur de développement et entrez le texte suivant dans la barre d’adresse :</span><span class="sxs-lookup"><span data-stu-id="3734f-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="3734f-168">chrome://inspect#devices ![Fenêtre Débogage USB Chrome](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="3734f-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="3734f-169">Vérifier que la case *Découvrir les périphériques USB* est cochée</span><span class="sxs-lookup"><span data-stu-id="3734f-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="3734f-170">Cliquez sur le bouton *Réacheminement de port* et vérifiez que le *Réacheminement de port* est activé et contient une entrée *localhost:5000* comme indiqué ci-dessous : ![Fenêtre Réacheminement de port Chrome](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="3734f-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="3734f-171">Sur votre appareil Android connecté, ouvrez une fenêtre Google Chrome et accédez à *http://localhost:5000* , ce qui permet d’afficher le cube</span><span class="sxs-lookup"><span data-stu-id="3734f-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="3734f-172">Sur votre ordinateur de développement, dans Chrome, vous verrez votre appareil et une liste de pages web actuellement ouvertes ici : ![Fenêtre Inspecter Chrome](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="3734f-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="3734f-173">Cliquez sur le bouton *Inspecter* en regard d’une entrée *http://localhost:5000* : ![ Fenêtre Débogage DevTools Chrome](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="3734f-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="3734f-174">Utiliser les [Devtools Chrome](https://developers.google.com/web/tools/chrome-devtools) pour déboguer la page</span><span class="sxs-lookup"><span data-stu-id="3734f-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="3734f-175">Éléments importants à retenir</span><span class="sxs-lookup"><span data-stu-id="3734f-175">Takeaways</span></span>

<span data-ttu-id="3734f-176">Voici les points les plus importants à retenir de ce tutoriel :</span><span class="sxs-lookup"><span data-stu-id="3734f-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="3734f-177">Babylon.js permet de créer facilement des expériences immersives à l’aide de JavaScript</span><span class="sxs-lookup"><span data-stu-id="3734f-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="3734f-178">Vous ne devez pas écrire du code de niveau bas ni apprendre à utiliser une nouvelle technologie pour créer des scènes virtuelles</span><span class="sxs-lookup"><span data-stu-id="3734f-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="3734f-179">Vous pouvez créer des applications Mixed Reality avec un navigateur pris en charge par WebXR sans devoir acheter de casque</span><span class="sxs-lookup"><span data-stu-id="3734f-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="3734f-180">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3734f-180">Next steps</span></span>

<span data-ttu-id="3734f-181">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="3734f-181">Congratulations!</span></span> <span data-ttu-id="3734f-182">Vous avez terminé notre série de tutoriels babylon.js et avez appris à :</span><span class="sxs-lookup"><span data-stu-id="3734f-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3734f-183">Configurer un environnement de développement</span><span class="sxs-lookup"><span data-stu-id="3734f-183">Set up a development environment</span></span>
> * <span data-ttu-id="3734f-184">Créer une page web pour afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="3734f-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="3734f-185">Utiliser l’API babylon.js pour créer des éléments 3D de base et interagir avec eux</span><span class="sxs-lookup"><span data-stu-id="3734f-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="3734f-186">Exécuter et tester l’application dans un Simulateur Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3734f-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="3734f-187">Pour plus d’informations sur le développement de Mixed Reality JavaScript, consultez [Vue d’ensemble du développement JavaScript](/javascript-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3734f-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
