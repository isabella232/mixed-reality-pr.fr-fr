---
title: Afficher un aperçu et déboguer votre application avec la communication à distance holographique et le mode lecture
description: Utiliser la communication à distance holographique et le mode lecture pour afficher un aperçu et déboguer votre application
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, réalité mixte, MRTK, réalité mixte Shared Computer Toolkit, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main, communication à distance holographique, bureau, préversion, débogage
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203837"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>Afficher un aperçu et déboguer votre application à l’aide de la communication à distance holographique et du mode lecture

Cet article explique le cas d’usage suivant pour la communication à distance holographique : 

- **Vous souhaitez afficher un aperçu et déboguer votre application pendant le processus de développement**: vous pouvez exécuter votre application localement dans l’éditeur Unity sur votre ordinateur en mode lecture et diffuser l’expérience sur votre HoloLens. Cela permet de déboguer rapidement votre application sans générer et déployer un projet complet. Nous appelons ce type d’application une _application de lecture de l’accès distant holographique en mode lecture_. les entrées de l’HoloLens--le point d’interrogation, le mouvement, la voix et le mappage spatial sont envoyés au PC, où le contenu est affiché dans une vue immersive virtuelle. Les frames rendus sont ensuite envoyés au HoloLens. 

Pour en savoir plus sur la communication à distance holographique, consultez [vue d’ensemble de la communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-overview.md)

notez que vous pouvez également utiliser la communication à distance holographique si [vous souhaitez que les ressources d’un PC alimentent votre application](use-pc-resources.md) au lieu de s’appuyer sur les HoloLens les ressources intégrées.

## <a name="set-up-holographic-remoting"></a>Configurer la communication à distance holographique

pour utiliser la communication à distance holographique, vous devez installer l’application de [lecteur de communication à distance holographique](../platform-capabilities-and-apis/holographic-remoting-player.md) à partir du Microsoft Store sur votre HoloLens. Comme expliqué ci-dessous, une fois que vous avez téléchargé et exécuté l’application, vous voyez le numéro de version et l’adresse IP auxquels vous souhaitez vous connecter. **Vous aurez besoin de v 2.4 ou version ultérieure pour pouvoir utiliser le plug-in OpenXR**.

La communication à distance holographique requiert un PC rapide et une connexion Wi-Fi. Pour plus d’informations, consultez l’article du joueur de communication à distance holographique ci-dessus.

![Capture d’écran du lecteur de communication à distance holographique en cours d’exécution dans le HoloLens](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>Voir aussi
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Didacticiel : prise en main de la communication à distance holographique de PC](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Didacticiel : création d’une application PC de communication à distance holographique](tutorials/mr-learning-pc-holographic-remoting-02.md)
