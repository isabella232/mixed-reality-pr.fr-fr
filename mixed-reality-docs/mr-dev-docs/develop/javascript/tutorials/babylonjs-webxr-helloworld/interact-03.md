---
title: Tutoriel babylon.js pour interagir avec des objets 3D
description: Découvrez comment utiliser babylon.js et interagir avec des objets 3D.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: réalité mixte, javascript, tutoriel, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web immersif
ms.localizationpriority: high
ms.openlocfilehash: 9aa044789c5d9d331677206dbc7ef7170bfa592075819ae73bd46aa14116122a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196886"
---
# <a name="tutorial-interact-with-3d-object"></a>Tutoriel : Interagir avec un objet 3D

Découvrez comment créer des objets 3D et des interactions pour une expérience de réalité mixte à l’aide de babylon.js. Dans cette section, vous allez commencer par quelque chose de simple, comme colorier les faces d’un cube lorsque vous sélectionnez l’objet.

Ce tutoriel couvre les rubriques suivantes :

> [!div class="checklist"]
> * Comment ajouter des interactions
> * Activer le mode immersif WebXR
> * Exécuter l’application sur le Simulateur Windows Mixed Reality
> * Exécuter et déboguer l’application sur Android Chrome

## <a name="before-you-begin"></a>Avant de commencer

Au cours d’une étape précédente du tutoriel, une page web de base avec une scène a été créée. Ouvrez la page web d’hébergement pour la modifier.

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

## <a name="add-interaction"></a>Ajouter une interaction

1. Commençons par mettre à jour notre code qui crée le cube afin que celui-ci soit peint avec une couleur aléatoire. Pour ce faire, nous allons ajouter des [matériaux](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) à notre cube. Le matériel nous permet de spécifier la couleur et les textures, et peut être utilisé pour d’autres objets. L’apparence d’un matériau dépend de la ou des lumières utilisées dans la scène et de la façon dont il est configuré pour réagir. Par exemple, diffuseColor répand la couleur sur la maille à laquelle il est attaché. Ajoutez le code suivant :

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. Maintenant que le cube est peint avec une couleur aléatoire, ajoutons une interaction pour :

    * modifier la couleur lors d’un clic sur le cube ;
    * déplacer le cube après la modification de la couleur.

    Pour ajouter des interactions, nous devons utiliser des [actions](https://doc.babylonjs.com/divingDeeper/events/actions). Une action est lancée en réponse au déclencheur d’événement. Par exemple, lorsque l’utilisateur clique sur le cube. Il nous suffit d’instancier BABYLON.ActionManager et d’inscrire une action pour certains déclencheurs. [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) exécute notre fonction JavaScript lorsqu’un utilisateur clique sur le cube :

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

1. Le code final de la page web se présente comme suit :

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

## <a name="enable-webxr-immersive-experience"></a>Activer l’expérience immersive WebXR

Maintenant que la couleur de notre cube a été modifiée, nous sommes prêts à essayer l’expérience immersive.

1. Au cours de cette étape, nous allons introduire un [plan](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground). Le cube sera suspendu dans les airs et un sol s’affichera en dessous. Pour ajouter le sol, procédez comme suit :

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    Cela crée un sol simple de 4x4 mètres.

1. Afin d’ajouter la prise en charge de WebXR, nous devons appeler *createDefaultXRExperienceAsync*, qui a pour résultat *Promesse*. Ajoutez ce code à la fin de la fonction *createScene* au lieu de *renvoyer la scène ;*  :

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. Dans la mesure où la fonction *createScene* renvoie maintenant une promesse au lieu d’une scène, nous devons modifier la façon dont les fonctions *createScene* et *engine.runRenderLoop* sont appelées. Remplacez les appels actuels de ces fonctions, qui se trouvent juste avant la balise *\</script>* , par le code ci-dessous :

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. Le code final de la page web se présente comme suit :

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

1. Le code ci-dessus génère la sortie suivante dans la fenêtre du navigateur : ![scène WebXR](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>Exécuter sur un Simulateur Windows Mixed Reality

1. [Activez le Simulateur Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) si vous ne l’avez pas encore fait.

1. Sélectionnez le bouton VR immersive dans le coin inférieur droit : ![bouton VR immersive](../images/immersive-vr-button.png)

1. Cette action lance la fenêtre Simulateur Windows Mixed Reality comme illustré ci-dessous : ![portail de réalité mixte](../images/mixed-reality-portal.png)

1. Utilisez les touches W, A, S et D de votre clavier pour avancer, revenir à gauche et à droite en fonction des besoins. Utilisez la simulation de main pour cibler le cube et appuyez sur la touche Entrée de votre clavier pour exécuter l’action de clic. La couleur du cube change et le cube se déplace vers une nouvelle position.

> [!NOTE]
> Lorsque vous ciblez le cube, assurez-vous que la fin du rayon émanant de la main (cercle blanc) croise le cube comme sur l’image ci-dessus. En savoir plus sur [Pointer et valider avec les mains](../../../../design/point-and-commit.md).

## <a name="run-and-debug-on-android-device"></a>Exécuter et déboguer sur un appareil Android

Pour activer le débogage sur votre appareil Android, procédez comme suit :

### <a name="prerequisites"></a>Prérequis

* Un serveur web qui sert des pages HTML statiques dans un contexte sécurisé (https:// ou via le réacheminement de port sur localhost) sur un ordinateur de développement. Par exemple, tirez parti du package npm *serve* en tant que simple serveur web léger traitant des fichiers HTML statiques, consultez plus de [npm de service](https://github.com/vercel/serve#readme)
* Appareil livré à l’origine avec Google Play Store et devant exécuter Android 7.0 ou une version plus récente
* Dernière version de [Google Chrome](https://support.google.com/chrome/answer/95346) sur la station de travail de développement et sur l’appareil
* Pour vérifier que l’appareil est correctement configuré pour exécuter WebXR, accédez à un [exemple de page WebXR](https://immersive-web.github.io/webxr-samples/) sur l’appareil. Un message doit s’afficher, par exemple :

    > Votre navigateur prend en charge WebXR et peut exécuter des expériences de réalité virtuelle et de réalité augmentée si vous disposez du matériel approprié.

1. Activez le mode développeur et le débogage USB sur un appareil Android. Pour plus d’informations sur la façon de procéder pour votre version d’Android, consultez la page de documentation officielle [Configurer les options de développeur sur appareil](https://developer.android.com/studio/debug/dev-options)
1. Ensuite, connectez l’appareil Android à votre ordinateur de développement ou ordinateur portable par le biais d’un câble USB
1. Assurez-vous que le serveur web sur l’ordinateur de développement est en cours d’exécution. Par exemple, accédez au dossier racine contenant votre page d’hébergement web (index.html) et exécutez le code suivant (en supposant que vous utilisez le package npm serve) :

    ```bash
    serve
    ```

1. Ouvrez Google Chrome sur votre ordinateur de développement et entrez le texte suivant dans la barre d’adresse :
    > chrome://inspect#devices ![Fenêtre Débogage USB Chrome](../images/chrome-usb-debug.png)
1. Vérifier que la case *Découvrir les périphériques USB* est cochée
1. Cliquez sur le bouton *Réacheminement de port* et vérifiez que le *Réacheminement de port* est activé et contient une entrée *localhost:5000* comme indiqué ci-dessous : ![Fenêtre Réacheminement de port Chrome](../images/chrome-port-forwarding.png)
1. Sur votre appareil Android connecté, ouvrez une fenêtre Google Chrome et accédez à *http://localhost:5000* , ce qui permet d’afficher le cube
1. Sur votre ordinateur de développement, dans Chrome, vous verrez votre appareil et une liste de pages web actuellement ouvertes ici : ![Fenêtre Inspecter Chrome](../images/chrome-inspect.png)
1. Cliquez sur le bouton *Inspecter* en regard d’une entrée *http://localhost:5000* : ![ Fenêtre Débogage DevTools Chrome](../images/chrome-debug.png)
1. Utiliser les [Devtools Chrome](https://developers.google.com/web/tools/chrome-devtools) pour déboguer la page

## <a name="takeaways"></a>Éléments importants à retenir

Voici les points les plus importants à retenir de ce tutoriel :
* Babylon.js permet de créer facilement des expériences immersives à l’aide de JavaScript
* Vous ne devez pas écrire du code de niveau bas ni apprendre à utiliser une nouvelle technologie pour créer des scènes virtuelles
* Vous pouvez créer des applications Mixed Reality avec un navigateur pris en charge par WebXR sans devoir acheter de casque

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé notre série de tutoriels babylon.js et avez appris à :
> [!div class="checklist"]
> * Configurer un environnement de développement
> * Créer une page web pour afficher les résultats
> * Utiliser l’API babylon.js pour créer des éléments 3D de base et interagir avec eux
> * Exécuter et tester l’application dans un Simulateur Windows Mixed Reality

Pour plus d’informations sur le développement de Mixed Reality JavaScript, consultez [Vue d’ensemble du développement JavaScript](/javascript-development-overview.md).
