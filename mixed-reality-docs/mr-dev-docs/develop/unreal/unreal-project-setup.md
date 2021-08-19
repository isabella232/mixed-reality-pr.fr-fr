---
title: Configuration de votre projet Unreal
description: Découvrez comment configurer votre projet avec la dernière version d’Unreal Engine et de Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, réalité mixte, développement, fonctionnalités, nouveau projet, émulateur, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, up-to-date, outils, démarrage, principes de base, unreal, kit de ressources, hub, installation, Windows, HoloLens, openxr, mrtk
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905573"
---
# <a name="setting-up-your-unreal-project"></a>Configuration de votre projet Unreal

Nous vous recommandons d’installer [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou ultérieure pour tirer pleinement parti de la prise en charge intégrée d’HoloLens.

Accédez à l’onglet **Library** dans Epic Games Launcher, sélectionnez la flèche déroulante à côté de **Launch**, puis cliquez sur **Options**. Sous **Target Platforms**, sélectionnez **HoloLens 2** et cliquez sur **Apply**.
![Option HoloLens 2 dans l’installation d’Unreal](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importer Mixed Reality Toolkit pour Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte. MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales. Le toolkit vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.

Si vous n’avez pas encore de projet de réalité mixte, suivez les trois premières sections des [tutoriels Prise en main d’HoloLens 2](tutorials/unreal-uxt-ch1.md) pour préparer un projet pour le kit MRTK.

### <a name="introducing-the-mrtk-hub-for-unreal"></a>Présentation du Hub MRTK pour Unreal

Nous vous recommandons d’utiliser le Hub MRTK pour acquérir des plug-ins MRTK. C’est là un nouveau moyen pour les développeurs de découvrir et de mettre à jour des plug-ins de réalité mixte Microsoft et de les ajouter à leurs projets Unreal. Vous pouvez afficher les plug-ins, voir leurs dépendances et les installer dans votre projet sans quitter l’éditeur Unreal.

- Découvrez les nouveaux plug-ins de réalité mixte Microsoft et installez-les ainsi que leurs dépendances dans votre projet Unreal.
- Maintenez à jour vos plug-ins de réalité mixte Microsoft.
- Supprimez les plug-ins de réalité mixte Microsoft de votre projet si vous n’en avez plus besoin.

> [!NOTE]
> Le Hub MRTK pour Unreal n’est disponible que pour le moteur Unreal version 4.26 ou ultérieure. Pour la version 4,25 du moteur, vous pouvez obtenir les plug-ins MRTK à partir de la place de marché du moteur Unreal ou de GitHub, comme indiqué dans la [section Prise en main](unreal-development-overview.md#1-getting-started).

#### <a name="installing-the-mrtk-hub"></a>Installation du Hub MRTK

Téléchargez le plug-in à partir de la [place de marché Unreal](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub), ouvrez votre projet, puis activez le plug-in à partir de la section _Réalité mixte_ du menu _Plug-ins_ . Lorsque vous y êtes invité, redémarrez l’éditeur.

![Activer le plug-in Hub MRTK](images/hub-enable-plugin.png)

Une fois que le plug-in activé pour votre projet, vous pouvez accéder au hub en utilisant le bouton de la barre d’outils.

![Ouvrir la fenêtre Hub MRTK](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>Installation de plug-ins de réalité mixte

Pour installer un plug-in à l’aide du Hub, sélectionnez le plug-in à ajouter à votre projet, puis appuyez sur le bouton _Installer_ . Pour télécharger le plug-in, assurez-vous qu’aucun conflit n’est présent dans la zone _Problèmes_, puis appuyez sur _Confirmer_. Une fois le plug-in téléchargé, vous serez invité à redémarrer l’éditeur. Malheureusement, nous ne pouvons pas redémarrer automatiquement l’éditeur pour vous. Il arrive que la nouvelle instance de l’éditeur démarre avant la fin de l’installation.

![Installer un plug-in à l’aide du Hub MRTK](images/hub-download.png)

Une fois l’éditeur fermé, une invite de commandes s’affiche avec une barre de progression pour décompresser le plug-in téléchargé. Une invite de commandes s’affichera pour chaque plug-in installé. Une fois la décompression terminée, vous pouvez rouvrir l’éditeur et continuer votre [parcours de développement de réalité mixte](unreal-quickstart.md).

![Décompression MRTK Hub d’un plug-in via l’invite de commandes](images/hub-unpack.png)

> [!IMPORTANT]
> Une fois le plugin installé, il doit être enregistré dans le contrôle de la source comme tout autre plugin de niveau projet.

#### <a name="updating-mixed-reality-plugins"></a>Mise à jour de plug-ins de réalité mixte

Pour mettre à jour un plug-in à l’aide du Hub, sélectionnez le plug-in à mettre à jour dans la liste, puis appuyez sur le bouton _Installer_ . Pour télécharger le plug-in mis à jour, assurez-vous qu’aucun conflit n’est présent dans la zone _Problèmes_, puis appuyez sur _Confirmer_. Vous serez invité à redémarrer l’éditeur pour terminer la mise à jour. Les mises à jour de plug-ins s’effectuent pendant le démarrage de l’éditeur. Il n’est donc pas nécessaire d’attendre la fin de la décompression pour rouvrir l’éditeur.

![Mise à jour d’un plug-in via le Hub MRTK](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>Suppression de plug-ins de réalité mixte

Pour désinstaller un plug-in à l’aide du Hub, sélectionnez le plug-in à supprimer, puis la version que vous avez installée dans la liste déroulante. Pour sur le plug-in, assurez-vous qu’aucun conflit n’est présent dans la zone _Problèmes_, puis appuyez sur _Confirmer_. Vous serez invité à redémarrer l’éditeur pour terminer la suppression.

![Suppression d’un plug-in via le Hub MRTK](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>Examen des modifications et détection des incompatibilités

Vous pouvez examiner les modifications précises qui seront apportées à votre projet dans la section inférieure de la fenêtre du Hub. À partir de là, vous pouvez voir les plug-ins qui seront ajoutés ou supprimés de votre projet ainsi que les incompatibilités potentielles susceptibles de provoquer des problèmes lorsque les modifications auront été apportées.

> [!NOTE]
> La liste _Problèmes_ énumère les incompatibilités de la version du moteur Unreal et des versions de dépendance du plug-in, mais ne corrige aucun problème rien et ne suggère pas automatiquement de correctifs.

![Tentative d’installation d’un plug-in incompatible](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Image du logo Unreal](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Si vous ne souhaitez pas utiliser le MRTK pour Unreal, vous devrez générer un script pour toutes les interactions et tous les comportements.