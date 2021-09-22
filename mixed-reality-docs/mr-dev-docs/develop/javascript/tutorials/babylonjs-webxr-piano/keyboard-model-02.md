---
title: Créer un modèle de piano 3D
description: Découvrez comment créer un modèle de piano 3D en codant avec Babylon.js
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: réalité mixte, javascript, tutoriel, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web immersif
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932507"
---
# <a name="tutorial-build-a-3d-piano-model"></a>Tutoriel : Créer un modèle de piano 3D

Dans le tutoriel précédent de la série, nous avons configuré une page web contenant une scène Babylon.js avec une caméra et une lumière. Dans ce tutoriel, nous allons créer un modèle de piano et l’ajouter à la scène.

![Maillage de piano droit](./images/standup-piano-mesh.png)

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> * Créer, positionner et fusionner des maillages
> * Créer un clavier de piano à partir de maillages de boîte
> * Importer le modèle 3D d’une structure de piano

## <a name="before-you-begin"></a>Avant de commencer

Vérifiez que vous avez bien effectué les étapes du [tutoriel précédent de la série](introduction-01.md) et que vous êtes prêt à ajouter du code.

*index.html*

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

*scene.js*

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

## <a name="getting-started"></a>Prise en main

Commençons par créer un clavier de piano simple avec la structure suivante :

![Description du registre du piano](./images/piano-register.jpg)

Dans cette image, vous avez 7 touches blanches et 5 touches noires, chacune portant le nom de la note. Un clavier de piano à 88 touches contient 7 répétitions complètes de cette sélection de touches (ou « registre ») et 4 touches supplémentaires. La fréquence d’un registre est deux fois celle du registre précédent. Ainsi, la fréquence de la hauteur de C5 (c’est-à-dire la note C dans le cinquième registre) est deux fois celle de C4, la fréquence de la hauteur de D5 est deux fois celle de D4, et ainsi de suite.

Visuellement, tous les registres se ressemblent. Nous pouvons donc commencer par examiner comment créer un clavier de piano simple avec cette sélection de touches. Plus tard, nous verrons comment l’étendre à un clavier de piano complet de 88 touches.

## <a name="build-a-simple-piano-keyboard"></a>Créer un clavier de piano simple

> [!NOTE]
> Bien qu’il soit possible de trouver des modèles 3D prédéfinis de claviers de piano en ligne et de les importer dans notre page web, nous allons créer dans ce tutoriel un clavier de toutes pièces pour pouvoir le personnaliser au maximum et voir comment créer des modèles 3D avec Babylon.js.

1. Avant de commencer à créer des maillages pour créer le clavier, notez que chaque touche noire n’est pas parfaitement alignée au milieu des deux touches blanches qui l’entourent, et que chaque touche n’a pas la même largeur. Nous devons donc créer et positionner le maillage pour chaque touche.

    ![Alignement des touches noires](./images/black-key-position.png)

1. Vous pouvez observer que chaque touche blanche se compose de deux parties : (1) la partie inférieure sous la ou les touches noires et (2) la partie supérieure à côté de la ou des touches noires. Les deux parties ont des dimensions différentes, mais sont empilées pour former une touche blanche complète.

    ![Forme de touche blanche](./images/white-key-shape-label.png)

1. Voici le code permettant de créer une touche blanche unique pour la note C (inutile de l’ajouter à *scene.js* pour l’instant) :

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    Ici, nous créons deux maillages de boîte ([Box](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh)), un pour la partie inférieure et un pour la partie supérieure de la touche blanche. Nous modifions ensuite la position de la partie supérieure pour l’empiler sur la partie inférieure et la déplacer vers la gauche pour laisser de la place à la touche noire voisine (C#).

    Enfin, ces deux parties sont fusionnées avec la fonction [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes) pour former une touche blanche complète. Voici le maillage qui est produit par ce code :

    ![Touche blanche (C)](./images/white-key-c.png)

1. Les touches noires sont plus faciles à créer. Dans la mesure où toutes les touches noires sont de forme rectangulaire, nous pouvons simplement créer une touche noire avec un maillage de boîte et un [StandardMaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color) de couleur noire.

    > [!NOTE]
    > Étant donné que la couleur de maillage par défaut est un gris clair qui ressemble au blanc, ce tutoriel n’inclut pas les étapes permettant d’ajouter un matériau de couleur blanc aux touches blanches. Toutefois, n’hésitez pas à ajouter vous-même le matériau si vous souhaitez affecter une vraie couleur blanche aux touches blanches.

    Voici le code permettant de créer la touche noire C# (là encore, inutile de l’ajouter à *scene.js*) :

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    La touche noire produite par ce code (avec la touche blanche précédente) ressemble à ceci :

    ![Touche noire (C#)](./images/black-key-csharp.png)

1. Comme vous pouvez le voir, la création des touches peut générer une grande quantité de code similaire dans la mesure où nous devons spécifier les dimensions et la position de chaque touche. Dans la section suivante, nous allons essayer d’améliorer l’efficacité du processus de création.

## <a name="build-a-simple-piano-keyboard-efficiently"></a>Créer un clavier de piano simple de manière efficace

1. Même si leur forme varie légèrement, toutes les touches blanches sont créées en combinant une partie supérieure et une partie inférieure. Nous allons implémenter une fonction générique pour créer et positionner une touche blanche.

    Ajoutez la fonction ci-dessous à *scene.js*, en dehors de la fonction `createScene()` :

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    Dans ce bloc de code, nous avons créé une fonction nommée `buildKey()` qui génère et retourne une touche blanche si `props.type` est `"white"`. En identifiant le type de la touche dans le paramètre `props`, nous pouvons créer des touches noires et blanches dans la même fonction en créant une branche avec une instruction if.

    Les paramètres de `buildKey()` sont les suivants :
    * **scene** : scène où se trouve la touche
    * **parent** : parent du maillage (ce qui nous permet de regrouper toutes les touches dans un seul parent)
    * **props** : propriétés de la touche qui sera créée

    Le paramètre `props` contient les éléments suivants pour une touche blanche :
    * **type** : "white"
    * **name** : nom de la note représentée par la touche
    * **topWidth** : largeur de la partie supérieure
    * **bottomWidth** : largeur de la partie inférieure
    * **topPositionX** : position x de la partie supérieure par rapport à la partie inférieure
    * **wholePositionX** : position x de la touche entière par rapport au point d’extrémité du registre (bord droit de la touche B)
    * **register** : registre auquel appartient la touche (nombre compris entre 0 et 8)
    * **referencePositionX** : coordonnée x du point d’extrémité du registre (utilisé comme point de référence)

    En séparant `wholePositionX` et `referencePositionX`, nous pouvons initialiser les paramètres `props` nécessaires pour créer un type spécifique de touche (par exemple, C) dans n’importe quel registre, puis ajouter `register` et `referencePositionX` à `props` au moment de la création de cette touche dans un registre spécifique (par exemple, C4, C5).

1. De même, nous pouvons écrire une fonction générique pour créer une touche noire. Développons la fonction `buildKey()` pour inclure cette logique :

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    Le paramètre `props` contient les éléments suivants pour une touche noire :

    * **type** : "black"
    * **name** : nom de la note représentée par la touche
    * **wholePositionX** : position x de la touche entière par rapport au point d’extrémité du registre (bord droit de la touche B)
    * **register** : registre auquel appartient la touche (nombre compris entre 0 et 8)
    * **referencePositionX** : coordonnée x du point d’extrémité du registre (utilisé comme point de référence)

    Le paramètre `props` nécessaire pour créer une touche noire est beaucoup plus simple. En effet, la création d’une touche noire implique uniquement la création d’une boîte, et la largeur et la position z de chaque touche noire sont identiques.

1. Maintenant que nous disposons d’une méthode plus efficace pour créer les touches, initialisons un tableau qui stocke le paramètre `props` pour chaque touche correspondant à une note dans un registre, puis appelons la fonction `buildKey()` avec chaque touche pour créer un clavier simple dans le 4e registre.

    Nous allons également créer un [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode) nommé `keyboard` pour agir en tant que [parent](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) de toutes les touches du piano. Étant donné que toute modification de position ou de mise à l’échelle appliquée au parent est également appliquée aux enfants, le fait de regrouper les touches de cette manière nous permet de les mettre à l’échelle ou de les déplacer en même temps.

    Ajoutez les lignes de code suivantes à la fonction `createScene()` :

    ```javascript
    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    Comme vous l’aurez probablement remarqué, toutes les touches sont placées en fonction de l’origine de l’espace dans ce bloc de code.

1. Voici le code contenu dans *scene.js* jusqu’à présent :

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]

        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. Voici à quoi ressemble le clavier résultant :

    ![Clavier de piano avec un registre](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>Extension à un clavier de piano de 88 touches

Dans cette section, nous allons étendre l’utilisation des fonctions de création de touche pour générer un clavier de piano complet de 88 touches.

1. Comme nous l’avons vu précédemment, un clavier de piano complet de 88 touches contient 7 registres répétés et 4 autres notes. 3 de ces notes supplémentaires se trouvent dans le registre 0 (extrémité gauche du clavier) et 1 dans le registre 8 (extrémité droite du clavier).

    ![Disposition d’un clavier de piano de 88 touches](./images/88-key-piano-keyboard-layout.jpg)

1. Pour créer les 7 répétitions complètes, nous allons tout d’abord ajouter une boucle supplémentaire autour de celle écrite précédemment. Remplacez la boucle précédente pour la fonction `buildKey()` par le code suivant :

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    Dans cette boucle, nous créons les touches pour les registres 1 à 7 et incrémentons la position de référence chaque fois que nous passons au registre suivant.

1. Nous pouvons ensuite créer le reste des touches. Ajoutez l’extrait de code suivant à la fonction `createScene()` :

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    Notez que la touche à l’extrémité gauche et celle à l’extrémité droite du clavier du piano ne tiennent pas dans les dimensions du paramètre props défini dans `keyParams` (parce qu’elles ne sont pas à côté d’une touche noire à la périphérie). Nous devons donc définir un nouvel objet `props` pour chacune d’elles afin de spécifier leur forme spéciale.

1. Une fois les modifications apportées, le clavier doit ressembler à ceci :

    ![Maillage de clavier de piano complet](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>Ajout d’une structure de piano

1. Cette scène d’un clavier qui flotte dans l’air est un peu étrange. Nous allons ajouter une structure de piano autour du clavier pour créer l’apparence d’un piano droit.

1. De la même manière que nous avons créé les touches, nous pouvons créer la structure en positionnant et en combinant un groupe de maillages de boîte.

    Cependant, nous allons vous laisser le soin d’accomplir cette tâche avec [BABYLON.SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh) pour importer le maillage prédéfini d’une structure de piano droit. Ajoutez ce segment de code à `createScene()` :

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    Là encore, nous créons un parent `TransformNode` nommé `piano` pour regrouper le clavier et la structure du piano. Nous pourrons ainsi déplacer ou mettre à l’échelle le piano complet beaucoup plus facilement en cas de besoin.

1. Une fois la structure importée, notez que le clavier se trouve en bas de la structure (puisque les coordonnées y des touches sont par défaut égales à 0). Déplaçons le clavier vers le haut pour le placer dans la structure du piano droit :

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    Comme `keyboard` est le parent de toutes les touches du piano, nous pouvons déplacer vers le haut toutes les touches du piano en modifiant simplement la position y de `keyboard`.

1. Le code final de *scene.js* doit ressembler à ce qui suit :

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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

        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        // Register 1 through 7
        var referencePositionX = -2.4*14;
        for (let register = 1; register <= 7; register++) {
            keyParams.forEach(key => {
                buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
            })
            referencePositionX += 2.4*7;
        }
    
        // Register 0
        buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
        keyParams.slice(10, 12).forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
        })
    
        // Register 8
        buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    
        // Transform node that acts as the parent of all piano components
        const piano = new BABYLON.TransformNode("piano");
        keyboard.parent = piano;
    
        // Import and scale piano frame
        BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
            const frame = meshes[0];
            frame.parent = piano;
        });
    
        // Lift the piano keyboard
        keyboard.position.y += 80;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Notre piano droit doit maintenant ressembler à ceci : ![Maillage de piano droit](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel suivant : Jouer sur le piano 3D](keyboard-interaction-03.md)
