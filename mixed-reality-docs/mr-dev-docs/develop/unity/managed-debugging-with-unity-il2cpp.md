---
title: Débogage managé avec Unity
description: Cet article explique comment exécuter un débogueur géré sur votre projet UWP IL2CPP Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, débogage, il2cpp, HoloLens, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, UWP
ms.openlocfilehash: 92b730768b6402b356e550d8f01d85e654832aef1ac382d8f992df615a9ce1b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196537"
---
# <a name="managed-debugging-with-unity"></a>Débogage managé avec Unity

procédez comme suit pour attacher un débogueur géré à votre build IL2CPP unity pour HoloLens et HoloLens 2.

1. Vous devez disposer d’un réseau qui prend en charge la [multidiffusion](https://en.wikipedia.org/wiki/Multicast).
2. accédez à la **publication UWP Paramètres fonctionnalités** et vérifiez **InternetClientServer** et **PrivateNetworkClientServer**:

    ![fonctionnalités de la publication UWP Paramètres](images/il2cpp-debugging-capabilities.png)

3. Configurer les paramètres de build UWP Unity :
    - Development Build
    - Débogage des scripts
    - Attendre le débogueur managé (facultatif)

    ![Paramètres de Build UWP](images/il2cpp-debugging-build.png)

4. Créez dans Unity.
5. créez et déployez à partir de la solution Visual Studio sur votre appareil. Vous devez générer avec les configurations **Debug** ou **Release** . La configuration **principale** désactive le profileur Unity et peut empêcher le débogage optimal. Si vous le souhaitez, vérifiez **Internet (client & Server)** et les **réseaux privés (client & Server)** dans la liste des fonctionnalités dans package. appxmanifest dans la solution.
6. Assurez-vous que votre appareil est connecté au même réseau que votre ordinateur et démarrez l’application sur votre appareil.
7. Assurez-vous que l’appareil **n’est pas** connecté à votre ordinateur via USB.
8. Double-cliquez sur l’un de vos scripts dans unity et accédez à la solution Visual Studio qui s’ouvre pour afficher et modifier.
9. Debug-> attacher le débogueur Unity.

    ![Attacher le débogueur Unity](images/il2cpp-debugging-attach.png)

10. Sélectionnez votre appareil dans la liste et cliquez sur OK pour l’attacher.

    ![Liste des appareils](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>Voir aussi 

* [Débogage C#](/visualstudio/get-started/csharp/tutorial-debugger)
