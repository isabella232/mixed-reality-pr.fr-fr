---
title: Demandes de tirage
description: détails relatifs à GitHub demandes de tirage (pull requests).
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK, demande de tirage
ms.openlocfilehash: ffaba25a42566d6e48be7db2c5b599443b24831f8f353fe1bd59beb062a7b87e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200111"
---
# <a name="pull-requests"></a>Demandes de tirage

## <a name="prerequisites"></a>Prérequis

Si vous n’avez pas contribué à un projet Microsoft avant, vous serez peut-être invité à signer un [contrat de licence de contribution](https://cla.microsoft.com/).
Un commentaire dans la demande de tirage vous l’indiquera le cas échéant.

> [!IMPORTANT]
> Si vous êtes un employé de Microsoft et que vous n’êtes pas membre de l’[organisation Microsoft sur GitHub](https://github.com/Microsoft), veuillez lier vos comptes Microsoft et GitHub sur corpnet en visitant la page sur l’[open source chez Microsoft](https://opensource.microsoft.com/) avant de commencer votre demande de tirage. Vous devrez effectuer certaines tâches à l’avance.

## <a name="creating-a-pull-request"></a>Création d’une demande de tirage

Lorsque vous êtes prêt à envoyer une demande de tirage (pull request), [créez une requête de tirage](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/main...main?expand=1) ciblant la branche [principale](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) . Pour les correctifs de bogues pendant une période de stabilisation de version, recherchez la branche la plus récente `prerelease/*` . Les nouvelles fonctionnalités doivent toujours entrer dans `main` .

Lisez les instructions et assurez-vous que votre demande de tirage s’y conforme.

* Veillez à référencer les problèmes, demandes de fonctionnalités ou tâches auxquels la demande de tirage est associée.
* Vérifiez que la demande de tirage contient uniquement des fichiers/modifications associés à la demande de tirage.
* Vérifiez que la documentation est à jour et incluse. Vérifiez que tous les champs publics contiennent des commentaires.
* Si vous ajoutez une nouvelle fonctionnalité, vérifiez que les tests sont inclus pour valider la fonctionnalité (voir [UnitTests](../contributing/unit-tests.md)).
* Si vous corrigez un bogue, écrivez un test pour vérifier la résolution du bogue.

Les réviseurs de projet examinent vos modifications. Nous souhaitons examiner toutes les modifications dans un délai de trois jours ouvrés. Veuillez répondre aux éventuels commentaires en lien avec la révision, transmettez à votre branche de rubrique et postez un commentaire pour nous informer qu’il y a du nouveau contenu à examiner.

> [!NOTE]
> Toutes les demandes de tirage envoyées au projet seront également examinées conformément au [Guide des normes de codage MRTK](../contributing/coding-guidelines.md). Nous vous recommandons de lire ce guide avant de soumettre votre demande de tirage pour garantir un processus fluide.

## <a name="pull-request-guidelines"></a>Instructions relatives aux demandes de tirage

Ces instructions sont basées sur les [pratiques d’ingénierie de Google](https://google.github.io/eng-practices/review/developer/small-cls.html).

### <a name="keep-pull-requests-small"></a>Générer des petites demandes de tirage

Les petites demandes de tirage sont examinées plus rapidement et de manière plus approfondie, elles sont moins susceptibles d’introduire des bogues et elles sont plus faciles à restaurer et à fusionner.

La demande de tirage doit être suffisamment petite pour permettre à un ingénieur de l’examiner en moins de 30 minutes. Essayez d’effectuer une modification minimale qui ne concerne qu’un seul élément. Si vous devez créer une demande de tirage de grande taille, divisez-la en plusieurs demandes de tirage qui vont dans votre branche locale ou dans une branche de fonctionnalités du MRTK. Évitez d’ajouter de nouveaux éléments (par ex., fbx, fichiers obj) et réutilisez plutôt les ressources existantes.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>Des tests doivent être ajoutés à la demande de tirage associée à votre correctif/demande de fonctionnalité, à l’exception des urgences.

Les tests constituent la meilleure façon de s’assurer que les modifications ne font pas régresser le code existant, mais il est également facile de les oublier lors de la soumission de demandes de tirage. Exiger qu’ils soient inclus avec votre demande de tirage est un excellent moyen de s’assurer que des tests sont bien écrits.

Tous les correctifs de fonctionnalités et de bogues doivent être associés à des tests. Si vous n’avez pas l’expertise ou le temps nécessaire pour écrire un test, créez un problème pour écrire les tests et marquez-les avec l’étiquette **À prendre en compte pour l’itération actuelle**.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>La documentation doit être ajoutée à la même demande de tirage que le correctif ou la fonctionnalité.

La plupart des développeurs consultent d’abord la documentation, et non le code, quand ils veulent comprendre comment utiliser une fonctionnalité. Lorsque la documentation est à jour, les utilisateurs ont plus de facilités à s’appuyer sur le MRTK et à l’utiliser.  La documentation doit toujours être regroupée avec la demande associée pour garantir que les éléments restent à jour et cohérents.

Assurez-vous que chaque champ public, méthode, propriété contient des [commentaires de résumé avec trois barres obliques](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) afin que notre site docfx puisse générer des descriptions pour les champs/méthodes. Si nécessaire, mettez à jour les fichiers de markdown dans le dossier de documentation.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>Les descriptions des demandes de tirage doivent décrire clairement et de façon exhaustive les modifications.

De cette façon, les réviseurs ont une bonne compréhension de ce qu’ils examinent.

Si vous ajoutez des fonctionnalités qui contiennent l’expérience utilisateur, ajoutez une image/image GIF de la fonctionnalité que vous modifiez. [En voici un bon exemple](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532). Une autre suggestion consiste à avoir une image GIF avant/après, [par exemple dans cette demande de tirage](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896). [ScreenToGif](https://www.screentogif.com/) est l’outil que nous recommandons pour générer des images GIF à partir de captures d’écran.
