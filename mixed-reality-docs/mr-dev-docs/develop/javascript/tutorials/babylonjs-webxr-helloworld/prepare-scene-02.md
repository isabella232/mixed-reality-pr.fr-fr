---
title: Didacticiel Babylon.js pour préparer une scène avec des objets 3D de base
description: Apprenez à utiliser babylon.js et à ajouter des objets 3D de base à une scène.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: réalité mixte, javascript, tutoriel, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web immersif
ms.localizationpriority: high
ms.openlocfilehash: 9d74104924aa859f5ab18248a487a7e80392809adb09361e84c5ad386f1321c4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212383"
---
# <a name="tutorial-prepare-a-scene"></a>Didacticiel : Préparer une scène

Découvrez comment préparer une scène et y ajouter des éléments 3D de base.

Dans ce tutoriel, vous allez apprendre à effectuer les actions suivantes :

> [!div class="checklist"]
> * Créer une scène
> * Ajouter une caméra
> * Ajouter de la lumière
> * Ajouter des éléments 3D de base

## <a name="before-you-begin"></a>Avant de commencer

Au cours d’une étape précédente du tutoriel, une page web de base a été créée. Ouvrez la page Web pour la modifier.

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

## <a name="create-a-scene"></a>Créer une scène

Une scène est l’endroit où tous les contenus seront affichés. Il peut y avoir plusieurs scènes et il est possible de basculer entre les scènes. En savoir plus sur la [scène babylon.js](https://doc.babylonjs.com/divingDeeper/scene).

1. Ajoutez la balise de script après l’élément HTML Canvas et ajoutez le code suivant pour créer une scène remplie de couleur noire :

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

    Dans le code ci-dessus, nous devons créer une instance du moteur de rendu web babylon.js qui restitue une scène et raccorde des événements à la zone de dessin. Pour plus d’informations sur le moteur, consultez la page de documentation [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)

1. La scène ne s’affiche pas par défaut. N’oubliez pas qu’il peut y avoir plusieurs scènes et que vous contrôlez la scène qui est affichée. Pour afficher la scène à plusieurs reprises sur chaque trame, exécutez le code suivant après avoir appelé la fonction *createScene* :

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>Ajouter d’un élément 3D de base

1. Ajoutons à présent notre première forme 3D. Dans le monde virtuel 3D, des formes sont créées à partir de *maillages*, un grand nombre de facettes triangulaires sont jointes, chaque facette étant constituée de trois vertex. Vous pouvez soit utiliser un maillage prédéfini, soit créer votre propre maillage personnalisé. Nous utiliserons un maillage de zone prédéfini, soit un cube. Pour créer la zone, utilisez [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box). Les paramètres sont le nom et les options (les options sont différentes selon le type de maillage). Ajoutez le code suivant à la fonction *createScene* :

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Ouvrez la page web dans le navigateur Microsoft Edge et vérifiez le résultat. La fenêtre du navigateur affiche une page vierge. Ouvrez DevTools à l’aide du clavier et sélectionnez F12 ou Ctrl + Maj + l (Windows, Linux) ou Cmd + Option + l (macOS). Après avoir ouvert l’onglet *Console*, vous pouvez commencer à rechercher des erreurs. Une erreur s’affiche : « Erreur non interceptée : aucune caméra définie ». À présent, nous devons ajouter une caméra à la scène.

## <a name="add-a-camera"></a>Ajouter une caméra

1. Pour afficher le monde virtuel et interagir avec celui-ci, une caméra doit être jointe à la zone de dessin. Ajoutons la caméra de type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), qui peut pivoter autour d’une cible. Les paramètres requis pour créer une instance de l’appareil photo sont les suivants :
    1. **nom** : nom de la caméra
    1. **alpha** : position angulaire le long de l’axe longitudinal (en radians)
    1. **bêta** : position angulaire le long de l’axe latitudinal (en radians)
    1. **rayon** : distance par rapport à la cible
    1. **cible** : point face auquel la caméra devrait toujours se trouver (défini par les coordonnées x-y-z)
    1. **scène** : scène dans laquelle se trouve l’appareil photo

    Alpha, bêta, rayon et cible définissent ensemble la position de la caméra dans l’espace, comme indiqué dans le diagramme ci-dessous :

    ![Caméra Alpha Bêta Rayon](../images/camera-alpha-beta-radius.jpg)

    Ajoutez le code suivant à la fonction *createScene* :

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Si vous vérifiez le résultat dans le navigateur, vous verrez une zone de dessin noire. Il manque la lumière.

## <a name="add-light"></a>Ajouter de la lumière

1. Il existe quatre types de lumières qui peuvent être utilisés avec une plage de propriétés d’éclairage : le point, l’orientation, le spot et la lumière hémisphérique. Nous allons ajouter la lumière ambiante [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) comme suit :

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
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

1. Vérifiez le résultat dans le navigateur. Vous devriez voir le cube et utiliser la souris pour faire pivoter l’appareil photo autour du cube et voir les différentes faces du cube :

![Scène de base avec cube](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiel suivant : 3. Interagir avec un objet 3D](interact-03.md)
