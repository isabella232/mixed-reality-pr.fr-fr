---
title: Choix de votre pipeline de développement
description: Restez à jour avec les dernières recommandations en matière de pipeline de développement Unity pour le développement d’applications HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, casque de réalité mixte, casque Windows Mixed Reality, casque de réalité virtuelle, Unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394553"
---
# <a name="choosing-your-developer-pipeline"></a>Choix de votre pipeline de développement

![Bannière du logo Unity](../images/unity_logo_banner.png)<br>

Bien que nous **vous recommandons actuellement d’installer unity 2019,4 LTS et d’utiliser des XR intégrées héritées pour le** développement de la réalité mixte, vous pouvez également créer des applications avec d’autres configurations Unity.

## <a name="mixed-reality-toolkit-recommended"></a>Boîte à outils de réalité mixte (recommandé)

La configuration d’Unity recommandée de Microsoft pour HoloLens 2 est la boîte à outils de réalité mixte...

### <a name="install-the-mixed-reality-feature-tool"></a>Installer l’outil de fonctionnalité de réalité mixte

[Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) est un nouveau moyen pour les développeurs de découvrir et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity. 

Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation. Une fois que vous avez validé les packages souhaités, Mixed Reality Feature Tool les télécharge dans le projet de votre choix.

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a>Importation du kit de pratiques de réalité mixte pour Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

Le [Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte. 

* Installez le package Mixed Reality Toolkit en suivant les [instructions d’installation et d’utilisation](welcome-to-mr-feature-tool.md#system-requirements) et en sélectionnant le package **Mixed Reality Toolkit Foundation**.

Nous recommandons de suivre la section Bien démarrer de nos parcours de développement [HoloLens](unity-development-overview.md#1-getting-started) ou [VR](unity-development-wmr-overview.md#1-getting-started) proposés. Si vous suivez déjà le parcours de développement Unity pour HoloLens, terminez le reste des étapes de configuration ci-dessous et passez aux [tutoriels Bien démarrer avec HoloLens 2](tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Notez que les instructions d’installation ciblent la dernière combinaison stable des versions de MRTK et d’Unity, qui sont **MRTK 2.6.1** et **Unity 2019.4 LTS**.

> [!NOTE]
> Si vous ne voulez pas utiliser MRTK pour Unity, vous devrez [générer vous-même un script pour toutes les interactions et tous les comportements](configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Bannière Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a>Manuel 

TBD...