---
title: Profilage avec Unreal Insights
description: découvrez comment utiliser des Informations inréelless sur HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: moteur 4, UE4, HoloLens, HoloLens 2, développement,, non réel, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779384"
---
# <a name="profiling-with-unreal-insights"></a>Profilage avec Unreal Insights

le [Informations inréel](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) est un système de profilage qui collecte, analyse et visualise les données à partir d’un moteur inréel. Le système de profilage peut vous aider à identifier les goulots d’étranglement d’optimisation et les zones où les performances des applications peuvent utiliser une augmentation. normalement, vous activez les Informationss non réels directement à partir de l’éditeur, mais pour HoloLens 2 vous devez utiliser la ligne de commande.

## <a name="setup"></a>Installation

non réel vous permet de créer et de configurer un « profil personnalisé » dans le lanceur de HoloLens avec les paramètres de ligne de commande qui activent les Informations non réels.

1. Recherchez l’adresse IP de votre ordinateur à l’aide de la commande **ipconfig** à l’invite de commandes. L’adresse IP est l’adresse IPv4 indiquée par ipconfig. Gardez cela à l’esprit pour plus tard lorsque vous définissez des paramètres de ligne de commande.

> [!IMPORTANT]
> Si vous êtes derrière un VPN, vous devrez peut-être fournir l’adresse IP fournie par le biais du VPN à la place.

![Capture d’écran des résultats de la ligne de commande pour la commande ipconfig](images/unreal-insights-img-01.png)

2. ouvrez **Project Paramètres** à partir de la barre d’outils « modifier » dans la fenêtre principale de l’éditeur.

![capture d’écran de la liste déroulante de modification avec Project Paramètres mises en](images/unreal-insights-img-15.png)

3. Faites défiler le volet gauche jusqu’à trouver l’en-tête **plateformes** , puis sélectionnez **HoloLens**.

![capture d’écran de la section plateformes dans le panneau gauche Project Paramètres avec HoloLens en surbrillance](images/unreal-insights-img-15.png)

4. Vérifiez que l’option « client Internet », « serveur client Internet » et « serveur client réseau privé » est sélectionnée pour la section **fonctionnalités** .

![Capture d’écran des options de fonctionnalités avec le client Internet, le serveur client Internet et le serveur client réseau privé sélectionné](images/unreal-insights-img-14.png)

## <a name="launch"></a>Lancer

1. ouvrez **Project Lanceur** à partir du panneau UE4 sous le bouton **lancer** :

![Capture d’écran des options de lancement avec le lanceur de projet en surbrillance](images/unreal-insights-img-07.png)

2. Sélectionnez le **+** bouton pour créer un profil personnalisé sous **profils de lancement personnalisés**. Une fois créé, vous pouvez toujours modifier ce profil ultérieurement :

![Capture d’écran du lanceur de projet avec les profils de lancement personnalisés mis en surbrillance](images/unreal-insights-img-08.png)

3. sélectionnez le bouton **modifier le profil** dans le HoloLens profil de lancement personnalisé. Dans la section **Build** , activez la case à cocher **générer UAT** et définir **des paramètres de ligne de commande supplémentaires**.
   - Essayez celles-ci pour les starters : **-tracehost = IP_OF_YOUR_PC-trace = Journal, Bookmark, Frame, CPU, GPU, LoadTime, file, net**
   - vous trouverez la liste complète des paramètres de lancement disponibles dans la [documentation de référence sur les Informations inréelless](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> « IP_OF_YOUR_PC » est l’adresse IP que nous avons trouvée à l’étape 1. il s’agit de l’adresse ip de l’ordinateur qui exécute des Informations non réelles, et non de l’adresse ip du HoloLens.

> [!IMPORTANT]
> Les suivis peuvent être très rapidement volumineux. Activez uniquement les canaux dont vous avez besoin pour réduire la taille de la trace.

![Capture d’écran des options de génération dans la configuration de profil](images/unreal-insights-img-17.png)

4. Sélectionnez **Cook** to dans **le livre** pour activer la copie sur l’appareil. assurez-vous que vos cartes sont sélectionnées dans le **Cartes cuit**.

![capture d’écran des options de cook dans configuration de profil avec cook par le livre et HoloLens mis en surbrillance](images/unreal-insights-img-09.png)

5. Définissez **Comment voulez-vous empaqueter la build dans le** **package & Store localement**. Notez le chemin d’accès de fichier que vous choisissez, car vous en aurez besoin plus tard.

![Capture d’écran des options de package dans Configuration de profil définie sur package et Store localement](images/unreal-insights-img-18.png)

6. Définissez **Comment voulez-vous déployer la build ?** pour **ne pas déployer**.

![Capture d’écran des options de déploiement dans la configuration de profil avec déploiement défini sur ne pas déployer](images/unreal-insights-img-19.png)

8. sélectionnez **précédent** pour revenir à la racine de la boîte de dialogue **Project Lanceur**
9. De retour dans l’éditeur, cliquez sur **lancer** sur votre profil de lancement personnalisé

![Capture d’écran des profils de lancement personnalisés](images/unreal-insights-img-13.png)

10. regardez à quel point votre projet est généré, puis déployez le package appxbundle (dans le chemin du package de l’étape 5) vers votre HoloLens via le portail de l’appareil.

11. lancer un Informations inréel. le fichier exécutable Informations inréel est stocké dans le dossier du moteur de fichiers binaires, généralement comme suit : « C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe »

![Capture d’écran de l’exécution d’un exécutable d’Insights inréel](images/unreal-insights-img-12.png)

12. Lancez l’application sur votre HoloLens.

## <a name="profiling"></a>Profilage

de retour dans le Informations inréel, sélectionnez la connexion **active** à votre appareil pour démarrer le profilage

Le profil personnalisé est partagé entre les projets. À partir de là, vous pouvez utiliser le profil personnalisé que vous avez créé au lieu de le faire à chaque fois. Il vous suffit de recréer la connexion à l’appareil chaque fois que vous démarrez sans réel avec les étapes 3 à 6 de la [section Configuration](#setup).

## <a name="see-also"></a>Voir aussi

- [documentation Informations inréel](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
