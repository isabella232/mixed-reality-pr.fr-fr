---
title: Vue d’ensemble de la communication à distance holographique
description: Découvrez ce qu’est la communication à distance holographique et comment elle peut tirer parti de votre processus de développement.
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, réalité mixte, MRTK, réalité mixte Shared Computer Toolkit, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main, communication à distance holographique, bureau, version préliminaire
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184600"
---
# <a name="holographic-remoting-overview"></a>Vue d’ensemble de la communication à distance holographique

vous pouvez utiliser la communication à distance holographique pour diffuser du contenu holographique vers votre HoloLens en temps réel. Pour ce faire, il existe deux utilisations principales et il est important de comprendre la différence :

1. (Unity ou Unreal) : **vous souhaitez afficher un aperçu et déboguer votre application pendant le processus de développement**: vous pouvez exécuter votre application localement dans l’éditeur Unity sur votre ordinateur en mode Play et diffuser l’expérience sur votre HoloLens. Cela permet de déboguer rapidement votre application sans générer et déployer un projet complet. Nous appelons ce type d’application une _application de lecture de l’accès distant holographique en mode lecture_.

    - [En savoir plus sur l’aperçu et le débogage de votre application dans Unity](../unity/preview-and-debug-your-app.md)

    - [En savoir plus sur l’aperçu et le débogage de votre application dans un environnement inréel](../unreal/unreal-streaming.md)

1. (unity, unreal or C++) : **vous souhaitez que les ressources d’un PC alimentent votre application au lieu de s’appuyer sur les ressources intégrées HoloLens**: vous pouvez créer et générer une application qui dispose d’une fonctionnalité de communication à distance holographique. l’utilisateur rencontre l’application sur le HoloLens, mais l’application s’exécute sur un pc, ce qui lui permet de tirer parti des ressources plus puissantes du pc. Cela peut s’avérer particulièrement utile si votre application a des ressources ou des modèles haute résolution et que vous ne souhaitez pas que la fréquence d’images souffre. Nous appelons ce type d’application une _application distante de communication à distance holographique_.

    - [En savoir plus sur l’utilisation des ressources PC dans Unity](../unity/use-pc-resources.md)

    - [En savoir plus sur l’utilisation des ressources PC dans des conditions inréelles](../unreal/unreal-streaming.md)

    - [écrire une application distante de communication à distance holographique à l’aide d’api Windows Mixed Reality (C++)](holographic-remoting-create-remote-wmr.md)

    - [Écrire une application distante de communication à distance holographique à l’aide d’API OpenXR (C++)](holographic-remoting-create-remote-openxr.md)

dans les deux cas, les entrées de la HoloLens--le point de regard, le mouvement, la voix et le mappage spatial sont envoyés au PC, le contenu est affiché dans une vue immersive virtuelle, et les frames rendus sont ensuite envoyés au HoloLens. 

## <a name="see-also"></a>Voir aussi

* [Holographic Remoting Player](holographic-remoting-player.md)
* [Didacticiel : prise en main de la communication à distance holographique de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Didacticiel : création d’une application PC de communication à distance holographique](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
