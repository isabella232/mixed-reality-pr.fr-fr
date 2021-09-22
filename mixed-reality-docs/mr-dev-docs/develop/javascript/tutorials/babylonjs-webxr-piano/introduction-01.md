---
title: Création d’un piano dans WebXR avec BabylonJS
description: Suivez cette série de tutoriels pour apprendre à créer un clavier de piano à 88 touches fonctionnel dans WebXR avec BabylonJS
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: réalité mixte, javascript, tutoriel, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web immersif
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932490"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>Tutoriel : Créer un piano dans WebXR avec Babylon.js

La fabrication d’un piano dans le monde réel nécessite beaucoup de temps, de compétences et de matériaux. Et si nous en construisions un pour le monde VR/AR ?

Dans cette série de tutoriels, vous allez découvrir comment utiliser Babylon.js pour créer une application web de réalité mixte contenant un piano droit à 88 touches fonctionnel dans le monde virtuel. Dans l’application terminée, vous pourrez vous téléporter devant le piano et en jouer en appuyant sur les touches avec vos contrôleurs de réalité mixte.

Dans cette série de tutoriels, vous allez apprendre à :

> [!div class="checklist"]
> * Créer, positionner et fusionner des maillages pour créer un clavier de piano
> * Importer un modèle Babylon.js d’une structure de piano droit
> * Ajouter des interactions de pointeur à chaque touche du piano
> * Activer la téléportation et la prise en charge de plusieurs pointeurs dans WebXR

## <a name="prerequisites"></a>Prérequis

* Ordinateur connecté à Internet
* Connaissances de base de JavaScript
* [Tutoriel Hello World JavaScript WebXR](../babylonjs-webxr-helloworld/introduction-01.md)
* Navigateur WebXR pris en charge, par exemple [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 ou version ultérieure
* [Casque VR](../../../../discover/immersive-headset-hardware-details.md) ou [simulateur Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)
* Facultatif : [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10) si vous souhaitez utiliser un simulateur Windows Mixed Reality

## <a name="getting-started"></a>Prise en main

Commençons par configurer la page web HTML qui contiendra la scène Babylon.js.

1. Créez un dossier nommé *babylonjs-piano-tutorial* et ouvrez le dossier dans Visual Studio Code.

    > [!NOTE]
    > Bien que vous ayez le choix entre plusieurs éditeurs de code, nous utiliserons Visual Studio Code tout au long de ce tutoriel pour des raisons pratiques.

1. Dans le dossier, créez un fichier nommé *index.html* et insérez le modèle ci-dessous dans le fichier :

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    Si vous avez besoin d’explications supplémentaires sur le contenu de ce modèle, consultez le [tutoriel Hello World](../babylonjs-webxr-helloworld/introduction-01.md), qui est un prérequis pour ce tutoriel.

1. Si vous essayez d’ouvrir ce fichier dans un navigateur, la console affiche une erreur indiquant que la fonction `createScene()` est introuvable. Nous allons résoudre cette erreur en implémentant la fonction `createScene()` dans la section suivante.

## <a name="setup-the-scene"></a>Configurer la scène

1. Dans le même dossier que *index.html*, créez un autre fichier nommé *scene.js*. Nous stockerons dans ce fichier tout le code JavaScript lié à la configuration de la scène et à la création du piano.

1. Ajoutons à présent la fonction `createScene()` dans *scene.js* :

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    Notez que la fonction `createScene()` est définie comme asynchrone. Nous y reviendrons dans un instant.

1. Ensuite, il nous faut une lumière et une caméra pour que la scène soit visible. Mettez à jour la fonction `createScene()` :

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    Ici, nous avons créé un [ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), qui pointe presque complètement vers le bas et qui cible le point d’origine de l’espace. La lumière que nous avons créée est un [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light) qui pointe vers le ciel et qui est utile pour simuler un espace ambiant. Nous avons également atténué un peu la lumière en diminuant son intensité.

    Si vous avez besoin d’un rappel sur la façon de créer une caméra et une lumière, relisez la [section Préparer la scène de la série de tutoriels Hello World](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera) avant de passer à l’étape suivante.

1. Enfin, étant donné que nous développons pour une plateforme WebXR, nous devons [activer l’expérience XR](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR) dans la scène en insérant la ligne suivante avant `return scene;` :

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    En JavaScript, pour utiliser le clavier `await` sur une fonction `async` au sein d’une fonction, la fonction parente doit également être `async`. C’est pourquoi nous avons précédemment défini la fonction `createScene` comme asynchrone. Plus loin dans cette série de tutoriels, nous utiliserons ce `xrHelper` pour activer et configurer différentes fonctionnalités WebXR prises en charge par Babylon.js.

1. Le fichier *scene.js* terminé doit ressembler à ceci :

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Maintenant que nous disposons d’une fonction `createScene()` opérationnelle, indiquons à *index.html* de charger le fichier *scene.js* en tant que script pour que la fonction `createScene()` soit reconnue dans *index.html*. Ajoutez cette ligne de code dans la section `<header>` du fichier HTML :

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. Ouvrez *index.html* dans votre navigateur. Vous pouvez alors constater que le message d’erreur généré précédemment n’est plus présent et que la page contient une scène Babylon.js vide.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel suivant : Créer un modèle de piano 3D](keyboard-model-02.md)
