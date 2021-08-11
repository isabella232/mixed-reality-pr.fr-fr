---
title: Vue d’ensemble de la communication à distance holographique
description: Découvrez ce qu’est la communication à distance holographique et comment elle peut tirer parti de votre processus de développement.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, réalité mixte, MRTK, réalité mixte Shared Computer Toolkit, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main, communication à distance holographique, bureau, version préliminaire
ms.openlocfilehash: 1b20590429b7df209e805ed8e94de5a6010bdbb609edc10fc5854cd4df86f64c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217115"
---
# <a name="holographic-remoting-overview"></a>Vue d’ensemble de la communication à distance holographique

lorsque vous ajoutez la prise en charge du rendu holographique à votre application ou à votre jeu de PC, il permet à l’application de diffuser du contenu holographique vers votre HoloLens 2 en temps réel. C’est un excellent moyen de déboguer rapidement votre application sans générer et déployer un projet complet. les entrées de pointage, de mouvement, de voix et de mappage spatial sont envoyées à partir de votre HoloLens 2 sur votre pc, le contenu est affiché dans une vue immersive virtuelle à l’aide des ressources système supérieures du pc, et les frames rendus sont ensuite renvoyés à votre HoloLens 2. la communication à distance holographique est également disponible pour Windows Mixed Reality les casques immersifs.

vous ajoutez la communication à distance holographique à votre application de bureau ou UWP via un package NuGet, et la connexion est établie à l’aide du Wi-Fi standard. Du code supplémentaire est nécessaire pour gérer la connexion et le rendu dans une vue immersive. Une connexion à distance classique aura une latence aussi faible que 50 ms de latence. Votre appareil affiche le contenu diffusé en continu à l’aide d’une application « joueur » qui peut signaler la latence en temps réel.

Si vous êtes un développeur Unity, vous pouvez également utiliser la communication à distance holographique en exécutant votre application dans l’éditeur Unity en mode lecture.

## <a name="see-also"></a>Voir aussi
* [Holographic Remoting Player](holographic-remoting-player.md)
* [écriture d’une application distante de communication à distance holographique à l’aide d’api Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Écriture d’une application distante de communication à distance holographique à l’aide d’API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Didacticiel : prise en main de la communication à distance holographique de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Didacticiel : création d’une application PC de communication à distance holographique](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
