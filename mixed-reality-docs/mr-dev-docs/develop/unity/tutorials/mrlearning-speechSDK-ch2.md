---
title: Exécuter des commandes à l’aide de la reconnaissance vocale Azure
description: Suivez ce cours pour découvrir comment exécuter des commandes à l’aide de la reconnaissance vocale Azure dans les applications de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure, reconnaissance vocale, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: ea5f1bed8fefe692de55a10c791530f22f295f454da1925902e03d5fcb169ffd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193034"
---
# <a name="2-execute-commands-using-azure-speech-recognition"></a>2. Exécuter des commandes à l’aide de la reconnaissance vocale Azure

Dans ce tutoriel, vous allez ajouter la capacité d’exécuter des commandes en utilisant la reconnaissance vocale Azure, ce qui va vous permettre de déclencher une action en fonction du mot ou de l’expression que vous définissez.

## <a name="objectives"></a>Objectifs

* Découvrir comment la reconnaissance vocale Azure peut être utilisée pour exécuter des commandes

## <a name="instructions"></a>Instructions

Dans la fenêtre Hierachy, sélectionnez l’objet **Lunarcom** puis, dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Lunarcom Wake Word Recognizer (Script)** à l’objet Lunarcom et configurez-le de la manière suivante :

* Dans le champ **Wake Word**, entrez une expression appropriée, par exemple, _Activer le terminal_.
* Dans le champ **Dismiss Word**, entrez une expression appropriée, par exemple, _Désactiver le terminal_.

![Éditeur Unity avec le composant de script Lunarcom Wake Word Recognizer mis en évidence](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Le composant Lunarcom Wake Word Recognizer (Script) ne fait pas partie de MRTK. Il a été fourni avec les ressources de ce tutoriel.

Si vous entrez maintenant en mode Game, comme dans le tutoriel précédent, le panneau du terminal est activé par défaut, mais vous pouvez maintenant le désactiver en prononçant la valeur de Dismiss Word, **Désactiver le terminal** :

![Éditeur Unity en mode lecture avec la fonctionnalité de reconnaissance vocale en cours d’utilisation](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Et réactivez-le en prononçant la valeur de Wake Word, à savoir **Activer le terminal** :

![Éditeur Unity en mode lecture avec le terminal actif](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> L’application a besoin de se connecter à Azure, donc vérifiez que votre ordinateur/appareil est connecté à Internet.

> [!TIP]
> Si vous prévoyez d’être souvent dans l’impossibilité de vous connecter à Azure, vous pouvez aussi implémenter des commandes vocales à l’aide de MRTK en suivant les instructions données dans [Utilisation des commandes vocales](mr-learning-base-09.md).

## <a name="congratulations"></a>Félicitations

Vous avez implémenté des commandes vocales Azure. Exécutez l’application sur votre appareil pour vérifier que tout fonctionne bien.

Dans le tutoriel suivant, vous allez apprendre à traduire la parole en utilisant la traduction vocale Azure.

> [!div class="nextstepaction"]
> [Tutoriel suivant : 3. Ajout du composant de traduction vocale Azure Cognitive Services](mrlearning-speechSDK-ch3.md)
