---
title: 1. Mise en route
description: Partie 1 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: efa0bc210fc20b9e639954a06e97eb78661d87e5
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712578"
---
# <a name="1-getting-started"></a>1. Mise en route

Que vous soyez débutant ou expérimenté dans la réalité mixte, ce tutoriel est parfait pour démarrer votre parcours [HoloLens 2](../../../index.yml) et [Unreal Engine](https://www.unrealengine.com/en-US/). Cette série de tutoriels vous guide dans la création d’une application interactive de jeu d’échecs en utilisant le [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), qui fait partie de [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). Ce plug-in vous permet d’ajouter des fonctionnalités d’expérience utilisateur courantes à vos projets à l’aide de code, de blueprints et d’exemples. 

![Scène finale dans la fenêtre Viewport](images/unreal-uxt/5-endscene.PNG)

À la fin de cette série, vous aurez une expérience des actions suivantes :
* Création d’un nouveau projet
* La configuration de la réalité mixte
* L’utilisation des entrées utilisateur
* L’ajout de boutons
* Le jeu sur un émulateur ou un appareil

## <a name="prerequisites"></a>Prérequis

Avant de commencer, vérifiez que vous avez installé les éléments suivants :
* Windows 10 1809 ou version ultérieure
* SDK Windows 10 (10.0.18362.0 ou version ultérieure)
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.26 ou ultérieur
* Appareil Microsoft HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) ou [émulateur](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)
* Visual Studio 2019 avec les charges de travail ci-dessous

### <a name="installing-visual-studio-2019"></a>Installation de Visual Studio 2019

Vérifiez d’abord que votre installation a tous les packages Visual Studio nécessaires :
1. Installez la dernière version de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).
1. Installez les [charges de travail](/visualstudio/install/modify-visual-studio#modify-workloads) suivantes :
    * Développement Desktop en C++
    * Développement .NET Desktop
    * Développement pour la plateforme Windows universelle
1. Dans Développement pour la plateforme Windows universelle, sélectionnez : 
    * Connectivité des périphériques USB
    * Outils de plateforme Windows universelle C++ (v142)

1. Installez les [composants](/visualstudio/install/modify-visual-studio#modify-individual-components) suivants :
    * Compilateurs, outils de build et runtimes > MSVC v142 - VS 2019 C++ ARM64 Build Tools (dernière version)

Vous pouvez confirmer l’installation avec l’image suivante

![Cycles importants dans le programme d’installation de Visual Studio](images/unreal-uxt/1-install-the-tools.png)

C’est tout ! Vous êtes maintenant prêt à lancer le projet de jeu d’échecs.

[Section suivante : 2. Initialisation de votre projet et première application](unreal-uxt-ch2.md)