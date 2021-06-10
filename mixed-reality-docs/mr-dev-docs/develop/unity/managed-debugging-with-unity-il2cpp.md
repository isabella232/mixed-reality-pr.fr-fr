---
title: Débogage managé avec Unity
description: Cet article explique comment exécuter un débogueur géré sur votre projet UWP IL2CPP Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, débogage, il2cpp, HoloLens, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547076"
---
# <a name="managed-debugging-with-unity"></a>Débogage managé avec Unity

Procédez comme suit pour attacher un débogueur géré à votre Build IL2CPP Unity pour HoloLens et HoloLens 2.

1. Vous devez disposer d’un réseau qui prend en charge la [multidiffusion](https://en.wikipedia.org/wiki/Multicast).
2. Accédez à la **section paramètres de publication UWP** , puis cochez **InternetClientServer** et **PrivateNetworkClientServer**:

    ![Fonctionnalités des paramètres de publication UWP](images/il2cpp-debugging-capabilities.png)

3. Configurer les paramètres de build UWP Unity :
    - Development Build
    - Débogage des scripts
    - Attendre le débogueur managé (facultatif)

    ![Paramètres de build UWP](images/il2cpp-debugging-build.png)

4. Créez dans Unity.
5. Générez et déployez à partir de la solution Visual Studio sur votre appareil. Vous devez générer avec les configurations **Debug** ou **Release** . La configuration **principale** désactive le profileur Unity et peut empêcher le débogage optimal. Si vous le souhaitez, vérifiez **Internet (client & Server)** et les **réseaux privés (client & Server)** dans la liste des fonctionnalités dans package. appxmanifest dans la solution.
6. Assurez-vous que votre appareil est connecté au même réseau que votre ordinateur et démarrez l’application sur votre appareil.
7. Assurez-vous que l’appareil **n’est pas** connecté à votre ordinateur via USB.
8. Double-cliquez sur l’un de vos scripts dans Unity et accédez à la solution Visual Studio qui s’ouvre pour afficher et modifier.
9. Debug-> attacher le débogueur Unity.

    ![Attacher le débogueur Unity](images/il2cpp-debugging-attach.png)

10. Sélectionnez votre appareil dans la liste et cliquez sur OK pour l’attacher.

    ![Liste des appareils](images/il2cpp-debugging-machines.png)
