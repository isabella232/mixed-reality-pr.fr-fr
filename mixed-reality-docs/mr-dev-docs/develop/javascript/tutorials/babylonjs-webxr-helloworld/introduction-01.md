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
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>Didacticiel : créez votre première application WebXR à l’aide de babylon.js

Ce didacticiel vous montre comment créer une application de réalité mixte de base à l’aide de babylon.js et de Visual Studio Code. L’application que vous allez développer vous permettra de créer un cube, de le faire pivoter pour en faire apparaître les autres faces et d’ajouter des interactions. Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
> * Configurer un environnement de développement
> * API babylon.js pour créer des éléments 3D de base  
> * Créer une page web
> * Interagir avec des éléments 3D
> * Exécuter l’application dans un simulateur Windows Mixed Reality

## <a name="prerequisites"></a>Prérequis

* Navigateur WebXR pris en charge, par exemple [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 ou version ultérieure
* [NodeJS](https://nodejs.org/)
* Facultatif : [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10) si vous souhaitez utiliser un simulateur Windows Mixed Reality
* Facultatif : [simulateur Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>Prise en main

pour créer ce projet à partir de zéro, commencez par un projet Visual Studio Code (VSCode).

> [!NOTE]
> L’utilisation de VSCode n’est pas obligatoire, mais nous l’utiliserons pour des raisons pratiques tout au long du didacticiel. Les développeurs JavaScript plus expérimentés peuvent utiliser n’importe quel autre éditeur de leur choix, même le très simple Bloc-notes.

1. Téléchargez le fichier unique [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) ou utilisez une version en ligne qui se trouve sur le [site web officiel babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers). Vous pouvez également cloner l’intégralité du projet babylon.js à partir de [GitHub](https://github.com/BabylonJS/Babylon.js)
1. Créez un fichier vide et enregistrez-le en tant que page HTML, par exemple index.html
1. Créez un balisage HTML de base et référencez le fichier javascript babylon.js . Le code final est le suivant :

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

1. Ajoutez un élément HTML de *zone de dessin* dans le corps pour afficher le contenu de babylon.js. Notez que la zone de dessin possède un attribut d’ID qui vous permet d’accéder plus tard à cet élément HTML à partir de JavaScript.

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

1. La zone de dessin occupe toute la page web. Cela finalise notre page web. À ce stade, la page web est prête. Vous pouvez l’ouvrir dans n’importe quel navigateur et vous assurer qu’aucune erreur ne s’affiche, bien qu’il n’y ait pas encore d’expérience immersive.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiel suivant : 2. Préparer une scène](prepare-scene-02.md)