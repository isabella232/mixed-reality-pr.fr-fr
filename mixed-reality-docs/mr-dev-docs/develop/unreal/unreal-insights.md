---
title: Profilage avec Unreal Insights
description: découvrez comment utiliser des Informations inréelless sur HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: moteur 4, UE4, HoloLens, HoloLens 2, développement,, non réel, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: a13655f394b4d2531ab2ae99ee21ebe9185ebe227ef07a16e3ca54eae9375ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228597"
---
# <a name="profiling-with-unreal-insights"></a>Profilage avec Unreal Insights 

le [Informations inréel](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) est un système de profilage qui collecte, analyse et visualise les données à partir d’un moteur inréel. Le système de profilage peut vous aider à identifier les goulots d’étranglement d’optimisation et les zones où les performances des applications peuvent utiliser une augmentation. normalement, vous activez les Informationss non réels directement à partir de l’éditeur, mais pour HoloLens 2 vous devez utiliser la ligne de commande.  

## <a name="setup"></a>Installation

non réel vous permet de créer et de configurer un « profil personnalisé » dans le lanceur de HoloLens avec les paramètres de ligne de commande qui activent les Informations non réels.

1.  Recherchez l’adresse IP de votre ordinateur à l’aide de la commande **ipconfig** à l’invite de commandes. L’adresse IP est l’adresse IPv4 indiquée par ipconfig. Gardez cela à l’esprit pour plus tard lorsque vous définissez des paramètres de ligne de commande.

> [!IMPORTANT]
> Si vous êtes derrière un VPN, vous devrez peut-être fournir l’adresse IP fournie par le biais du VPN à la place.

![Capture d’écran des résultats de la ligne de commande pour la commande ipconfig](images/unreal-insights-img-01.png)

2.  Accédez au début du panneau du moteur inréel et ouvrez **Gestionnaire de périphériques** sous le bouton **lancer** :

![Capture d’écran des options de lancement avec le gestionnaire de périphériques en surbrillance](images/unreal-insights-img-02.png)

3.  Dans le Gestionnaire de périphériques, sélectionnez **Ajouter un appareil non répertorié**:

![Capture d’écran du gestionnaire de périphériques ouverte dans un moteur inréel](images/unreal-insights-img-03.png)

4. Cliquez sur **Sélectionner une plateforme** , puis choisissez **HoloLens**:

![capture d’écran de la liste déroulante ajouter un appareil sans liste avec HoloLens mis en surbrillance](images/unreal-insights-img-04.png)

5.  Si vous utilisez IPoverUSB, entrez 127.0.0.1:10 080 comme identificateur d’appareil. entrez votre nom d’utilisateur et votre mot de passe HoloLens dans leurs champs respectifs et renseignez le **nom d’affichage** comme vous le souhaitez.

> [!IMPORTANT]
> l’identificateur de l’appareil correspond à l’adresse IP du HoloLens, et non à l’ordinateur exécutant des Informationss non réelles que vous avez trouvé à l’étape 1.

![capture d’écran des détails de l’appareil HoloLens dans le gestionnaire de périphériques](images/unreal-insights-img-05.png)

6.  sélectionnez **ajouter** et votre HoloLens doit apparaître dans la liste des appareils du gestionnaire de périphériques :

![capture d’écran de la HoloLens ajoutée à la liste des appareils](images/unreal-insights-img-06.png)

## <a name="launch"></a>Lancer

1. ouvrez **Project Lanceur** à partir du panneau UE4 sous le bouton **lancer** :

![Capture d’écran des options de lancement avec le lanceur de projet en surbrillance](images/unreal-insights-img-07.png)

2. Sélectionnez le **+** bouton pour créer un profil personnalisé sous **profils de lancement personnalisés**. Une fois créé, vous pouvez toujours modifier ce profil ultérieurement :

![Capture d’écran du lanceur de projet avec les profils de lancement personnalisés mis en surbrillance](images/unreal-insights-img-08.png)

3. sélectionnez le bouton **modifier le profil** dans le HoloLens profil de lancement personnalisé et configurez :
    * Sélectionnez **Cook** to dans **le livre** pour activer la copie sur l’appareil
    * Vous pouvez vérifier que **vous souhaitez archiver ?** dans la section **Archive** pour conserver le fichier. appxbundle généré au lieu de le supprimer pour économiser de l’espace disque. Spécifiez un emplacement pour le. appxbundle et basculez vers une build de développement si vous le souhaitez

![capture d’écran des options de cook dans configuration de profil avec cook par le livre et HoloLens mis en surbrillance](images/unreal-insights-img-09.png)

4. Définir **Comment voulez-vous déployer la build ?** pour la **copier sur l’appareil** afin d’activer la section de **lancement** de l’interface utilisateur :

![Capture d’écran du lanceur de projet avec les options de déploiement avec copier sur l’appareil mis en surbrillance](images/unreal-insights-img-10.png)

5. Définissez **des paramètres de ligne de commande supplémentaires** dans la section **Launch** . Les paramètres sont écrits dans un fichier ue4commandline.txt, empaquetés dans le bundle et utilisés au lancement. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Essayez celles-ci pour les starters : **-tracehost = IP_OF_YOUR_PC-trace = Journal, Bookmark, Frame, CPU, GPU, LoadTime, file, net**
    * vous trouverez la liste complète des paramètres de lancement disponibles dans la [documentation de référence sur les Informations inréelless](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> « IP_OF_YOUR_PC » est l’adresse IP que nous avons trouvée à l’étape 1. il s’agit de l’adresse ip de l’ordinateur qui exécute des Informations non réelles, et non de l’adresse ip du HoloLens.

> [!IMPORTANT]
> Les suivis peuvent être très rapidement volumineux. Activez uniquement les canaux dont vous avez besoin pour réduire la taille de la trace.

![Capture d’écran des options de configuration du lancement](images/unreal-insights-img-11.png)

6. lancer des Informations non réelles avant le lancement de l’application ; sinon, les Informations non réelles ne peuvent pas s’initialiser correctement avant l’application :
    * le fichier exécutable Informations inréel est stocké dans le dossier du moteur de fichiers binaires, généralement comme suit : « C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe »

![Capture d’écran de l’exécution d’un exécutable d’Insights inréel](images/unreal-insights-img-12.png)

6.  sélectionnez **précédent** pour revenir à la racine de la boîte de dialogue **Project Lanceur**
7.  De retour dans l’éditeur, cliquez sur **lancer** sur votre profil de lancement personnalisé

![Capture d’écran des profils de lancement personnalisés](images/unreal-insights-img-13.png)

8.  Regardez quand votre projet est empaqueté, installé sur votre appareil et lancé

## <a name="profiling"></a>Profilage

de retour dans le Informations inréel, sélectionnez la connexion **active** à votre appareil pour démarrer le profilage

Le profil personnalisé est partagé entre les projets. À partir de là, vous pouvez utiliser le profil personnalisé que vous avez créé au lieu de le faire à chaque fois. Il vous suffit de recréer la connexion à l’appareil chaque fois que vous démarrez sans réel avec les étapes 3 à 6 de la [section Configuration](#setup).

## <a name="see-also"></a>Voir aussi
* [documentation Informations inréel](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

