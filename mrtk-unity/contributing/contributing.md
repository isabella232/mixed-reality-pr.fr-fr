---
title: Contribution à MRTK
description: comment contribuer à la réalité mixte Shared Computer Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, rapport de bogue,
ms.openlocfilehash: b79f69cbb6dea1201c88d9fd1a354967ce40735e
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282046"
---
# <a name="contributing-to-mrtk"></a>Contribution à MRTK

la réalité mixte Shared Computer Toolkit (MRTK) salue les contributions de la communauté. Toutes les modifications sont de taille petite ou grande, doivent respecter les [normes de codage MRTK](coding-guidelines.md). Veillez donc à bien les connaître lors du développement afin d’éviter des retards lors de la révision de la modification.

Si vous avez des questions, veuillez contacter le canal de [réalité mixte sur la marge](https://holodevelopers.slack.com/messages/C2H4HT858).
Vous pouvez rejoindre la communauté Slack par le biais de l’[envoi d’invitation automatique](https://holodevelopersslack.azurewebsites.net/).

## <a name="submission-process"></a>Processus d’envoi

nous fournissons plusieurs chemins pour permettre aux développeurs de contribuer à la réalité mixte Shared Computer Toolkit, tout en commençant par la [création d’un nouveau problème](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

À partir de là, vous fichier :

- **rapport de bogues** -problème de fonctionnalité avec l’un des composants de la réalité mixte Shared Computer Toolkit
- **problème de documentation** : problème avec la [documentation](https://microsoft.github.io/MixedRealityToolkit-Unity) Shared Computer Toolkit de la réalité mixte
- **demande de fonctionnalité** -offre pour une nouvelle fonctionnalité Shared Computer Toolkit de la réalité mixte

## <a name="proposing-feature-requests"></a>Proposer des demandes de fonctionnalités

lors de la demande d’une nouvelle Shared Computer Toolkit de réalité mixte, il est important de documenter l’avantage/le problème du client à résoudre. Une fois envoyée, une demande de fonctionnalité sera examinée et discutée sur GitHub. Nous encourageons la discussion ouverte et constructive de chaque proposition de fonctionnalité pour garantir que le travail est bénéfique pour un grand segment de clients.

Pour éviter d’avoir à retravailler la fonctionnalité, il est généralement recommandé que le développement de la fonctionnalité ne commence pas au cours de la phase de vérification. Dans de nombreux cas, le processus de révision de la communauté découvre un ou plusieurs problèmes qui peuvent nécessiter des modifications significatives dans l’implémentation proposée.

> [!NOTE]
> Si vous souhaitez travailler sur un élément qui existe déjà dans notre backlog, vous pouvez utiliser cet élément de travail comme proposition. Veillez également à commenter la tâche en avertissant les détenteurs que vous travaillez pour la finaliser.

## <a name="contribution-process"></a>Processus de contribution

Pour commencer, procédez simplement comme suit :

1. Dupliquez (fork) le dépôt. Cliquez sur le bouton « fourche » en haut à droite de la page et suivez le Flow.
1. Créez une branche dans votre fourche (en dehors de la branche [principale](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) ) pour faciliter l’isolation des modifications jusqu’à ce qu’elles soient prêtes pour l’envoi. Pour les correctifs de bogues pendant une période de stabilisation de version, recherchez la branche la plus récente `prerelease/*` . Les nouvelles fonctionnalités doivent toujours entrer dans `main` .

Si vous débutez avec le flux de travail git, [consultez cette présentation de GitHub](https://guides.github.com/activities/hello-world/).

Quand vous ajoutez une correction ou une fonctionnalité de bogue, procédez comme suit :

1. Implémentez la fonctionnalité ou la résolution de bogue. Les instructions pour la création et le déploiement de MRTK sont lors du [déploiement sur les appareils Hololens et WMR](../supported-devices/wmr-mrtk.md). N’oubliez pas de suivre les [instructions de codage](../contributing/coding-guidelines.md).
1. Si vous ajoutez une fonctionnalité, ajoutez également un exemple de scène qui illustre la fonctionnalité.
1. Si vous ajoutez une fonctionnalité expérimentale, il n’est pas nécessaire d’écrire des tests et de la documentation. Au lieu de cela, suivez [les recommandations relatives aux fonctionnalités expérimentales](../contributing/experimental-features.md).
1. Ajoutez des tests pour vérifier la fonctionnalité et la résolution de bogue. Les instructions relatives à l’écriture et à l’exécution de tests se trouvent sur [UnitTests](../contributing/unit-tests.md).
1. Assurez-vous que le code et les fonctionnalités sont documentées, comme décrit dans les instructions de la [documentation](../contributing/documentation-guide.md).
1. Assurez-vous que le code fonctionne comme prévu sur toutes les plateformes. Pour obtenir la liste des plateformes prises en charge, consultez les [notes de publication](../release-notes/mrtk-26-release-notes.md) . pour les projets UWP Windows, le code doit être [conforme à WACK](https://developer.microsoft.com/windows/develop/app-certification-kit). pour ce faire, générez une solution Visual Studio, cliquez avec le bouton droit sur le projet ; **Stockage**  >  **Créer des packages d’application**. Suivez les invites et exécutez les tests WACK. Assurez-vous qu’ils ont tous été correctement.
1. Suivez les instructions des [requêtes de tirage](../contributing/pull-requests.md) lors de l’exécution d’une requête de tirage.
