---
title: Profilage avec Unreal Insights
description: Découvrez comment utiliser des Insights inréels sur HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Moteur 4, UE4, HoloLens, HoloLens 2, développement, profilage non réel, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580834"
---
# <a name="profiling-with-unreal-insights"></a>Profilage avec Unreal Insights 

Le système de profilage qui collecte, analyse et visualise les données à partir d’un moteur inréel [est un](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) système de profilage. Le système de profilage peut vous aider à identifier les goulots d’étranglement d’optimisation et les zones où les performances des applications peuvent utiliser une augmentation. Normalement, vous activez les Insights non réels directement à partir de l’éditeur, mais pour HoloLens 2, vous devez utiliser la ligne de commande.  

## <a name="setup"></a>Programme d’installation

Non réel vous permet de créer et de configurer un « profil personnalisé » dans le lanceur HoloLens avec les paramètres de ligne de commande qui permettent d’obtenir des informations non réelles.

1.  Recherchez l’adresse IP de votre ordinateur à l’aide de la commande **ipconfig** à l’invite de commandes. L’adresse IP est l’adresse IPv4 indiquée par ipconfig. Gardez cela à l’esprit pour plus tard lorsque vous définissez des paramètres de ligne de commande.

> [!IMPORTANT]
> Si vous êtes derrière un VPN, vous devrez peut-être fournir l’adresse IP fournie par le biais du VPN à la place.

![Capture d’écran des résultats de la ligne de commande pour la commande ipconfig](images/unreal-insights-img-01.png)

2.  Accédez au début du panneau du moteur inréel et ouvrez **Device Manager** sous le bouton **lancer** :

![Capture d’écran des options de lancement avec le gestionnaire de périphériques en surbrillance](images/unreal-insights-img-02.png)

3.  Dans le Device Manager, sélectionnez **Ajouter un appareil non répertorié**:

![Capture d’écran du gestionnaire de périphériques ouverte dans un moteur inréel](images/unreal-insights-img-03.png)

4. Cliquez sur **Sélectionner une plateforme** , puis choisissez **HoloLens**:

![Capture d’écran de la liste déroulante Ajouter un appareil sans liste avec HoloLens mis en surbrillance](images/unreal-insights-img-04.png)

5.  Si vous utilisez IPoverUSB, entrez 127.0.0.1:10 080 comme identificateur d’appareil. Entrez votre utilisateur et votre mot de passe HoloLens dans leurs champs respectifs et renseignez le **nom d’affichage** comme vous le souhaitez.

> [!IMPORTANT]
> L’identificateur d’appareil est l’adresse IP du HoloLens, et non de l’ordinateur qui exécute des analyses inréelless que vous avez trouvé à l’étape 1.

![Capture d’écran des détails de l’appareil HoloLens dans le gestionnaire de périphériques](images/unreal-insights-img-05.png)

6.  Sélectionnez **Ajouter** et votre HoloLens doit apparaître dans la liste des appareils du gestionnaire de périphériques :

![Capture d’écran de HoloLens ajoutée à la liste des appareils](images/unreal-insights-img-06.png)

## <a name="launch"></a>Lancer

1. Ouvrez le **lanceur de projet** à partir du panneau UE4 sous le bouton **lancer** :

![Capture d’écran des options de lancement avec le lanceur de projet en surbrillance](images/unreal-insights-img-07.png)

2. Sélectionnez le **+** bouton pour créer un profil personnalisé sous **profils de lancement personnalisés**. Une fois créé, vous pouvez toujours modifier ce profil ultérieurement :

![Capture d’écran du lanceur de projet avec les profils de lancement personnalisés mis en surbrillance](images/unreal-insights-img-08.png)

3. Sélectionnez le bouton **modifier le profil** dans le profil de lancement personnalisé HoloLens et configurez les éléments suivants :
    * Sélectionnez **Cook** to dans **le livre** pour activer la copie sur l’appareil
    * Vous pouvez vérifier que **vous souhaitez archiver ?** dans la section **Archive** pour conserver le fichier. appxbundle généré au lieu de le supprimer pour économiser de l’espace disque. Spécifiez un emplacement pour le. appxbundle et basculez vers une build de développement si vous le souhaitez

![Capture d’écran des options de Cook dans Configuration de profil avec Cook par le livre et HoloLens mis en surbrillance](images/unreal-insights-img-09.png)

4. Définir **Comment voulez-vous déployer la build ?** pour la **copier sur l’appareil** afin d’activer la section de **lancement** de l’interface utilisateur :

![Capture d’écran du lanceur de projet avec les options de déploiement avec copier sur l’appareil mis en surbrillance](images/unreal-insights-img-10.png)

5. Définissez **des paramètres de ligne de commande supplémentaires** dans la section **Launch** . Les paramètres sont écrits dans un fichier ue4commandline.txt, empaquetés dans le bundle et utilisés au lancement. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Essayez celles-ci pour les starters : **-tracehost = IP_OF_YOUR_PC-trace = Journal, Bookmark, Frame, CPU, GPU, LoadTime, file, net**
    * Vous trouverez une liste complète des paramètres de lancement disponibles dans la [documentation de référence sur les informations inréelles](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> « IP_OF_YOUR_PC » est l’adresse IP que nous avons trouvée à l’étape 1. Il s’agit de l’adresse IP de l’ordinateur qui exécute des informations non réelles, et non de l’adresse IP du HoloLens.

> [!IMPORTANT]
> Les suivis peuvent être très rapidement volumineux. Activez uniquement les canaux dont vous avez besoin pour réduire la taille de la trace.

![Capture d’écran des options de configuration du lancement](images/unreal-insights-img-11.png)

6. Lancer des analyses non réelles avant le lancement de l’application ; sinon, les informations non réelles ne peuvent pas s’initialiser correctement avant l’application :
    * L’exécutable Unreal Insights est stocké dans le dossier du moteur de fichiers binaires, généralement comme suit : « C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe »

![Capture d’écran de l’exécution d’un exécutable d’Insights inréel](images/unreal-insights-img-12.png)

6.  Sélectionnez **précédent** pour revenir à la racine de la boîte de dialogue du **lanceur de projet**
7.  De retour dans l’éditeur, cliquez sur **lancer** sur votre profil de lancement personnalisé

![Capture d’écran des profils de lancement personnalisés](images/unreal-insights-img-13.png)

8.  Regardez quand votre projet est empaqueté, installé sur votre appareil et lancé

## <a name="profiling"></a>Profilage

De retour dans informations non réelles, sélectionnez la connexion **active** à votre appareil pour démarrer le profilage

Le profil personnalisé est partagé entre les projets. À partir de là, vous pouvez utiliser le profil personnalisé que vous avez créé au lieu de le faire à chaque fois. Il vous suffit de recréer la connexion à l’appareil chaque fois que vous démarrez sans réel avec les étapes 3 à 6 de la [section Configuration](#setup).

## <a name="see-also"></a>Voir aussi
* [Documentation sur les informations non réelles](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

