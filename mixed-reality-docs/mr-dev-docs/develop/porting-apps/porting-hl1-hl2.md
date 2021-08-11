---
title: Portage des applications HoloLens (1ère gén.) sur HoloLens 2
description: Conçu pour les développeurs qui disposent déjà d’une application HoloLens (1re génération) et d’anciennes versions de MRTK, et qui souhaitent effectuer le portage vers MRTK version 2 et HoloLens 2.
author: hferrone
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, MRTK, MRTK version 2, HoloLens 2, unity, portage, HoloLens 1ère génération, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, migration, bonnes pratiques, ARM
ms.openlocfilehash: f7a70a8bd5a6d11d6502b431b17bbd3391d24ce4e19f0a842503ccae834589fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219281"
---
# <a name="porting-hololens-1st-gen-apps-to-hololens-2"></a>Portage des applications HoloLens (1ère gén.) sur HoloLens 2

Ce guide sur mesure a été conçu pour aider les développeurs qui disposent d’une application Unity pour HoloLens (1re génération) à effectuer le portage de leur application vers l’appareil HoloLens 2. Le portage d’une application Unity pour HoloLens (1re génération) vers HoloLens 2 comprend quatre étapes clés. 

Les sections ci-dessous expliquent en détail chacune de ces étapes :

| Étape 1 | Étape 2 | Étape 3 | Étape 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logo Visual Studio](../images/visualstudio_logo.png) | ![Logo Unity](../../design/images/logo-unity.png)| ![Icône Unity](../unity/images/hololens2_icon.jpg) | ![Logo MRTK](../../design/images/74-12.png) |
| Télécharger les derniers outils | Mettre à jour un projet Unity | Compiler pour ARM | Effectuer une migration vers MRTK v2

## <a name="prerequisites"></a>Prérequis

Avant de démarrer le processus de portage, nous vous **recommandons vivement** d’utiliser le contrôle de code source pour enregistrer un instantané de l’état d’origine de vos applications. Nous vous recommandons également d’*enregistrer* les états des points de contrôle à différents stades du processus. Le fait de disposer d’une autre instance Unity de l’application d’origine peut être utile pour effectuer une comparaison côte à côte pendant le processus de portage. 

> [!NOTE]
> Avant d’effectuer le portage, vérifiez que vous avez installé les derniers outils de développement Windows Mixed Reality. Pour la plupart des développeurs HoloLens, il s’agit d’effectuer une mise à jour vers la dernière version de Visual Studio 2019 et d’installer le SDK Windows correspondant. Le contenu ci-dessous offre une présentation détaillée des différentes versions de Unity et de Mixed Reality Toolkit (MRTK), version 2.
>
> Pour plus d’informations, consultez [Installer les outils](../install-the-tools.md).

## <a name="migrate-project-to-the-latest-version-of-unity"></a>Effectuer la migration d’un projet vers la dernière version de Unity

Si vous utilisez [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), nous vous recommandons d’effectuer la mise à jour vers MRTK 2.7 avant de mettre votre projet à niveau vers [Unity 2020.3 LTS](../unity/choosing-unity-version.md). MRTK 2.7 prend en charge Unity 2018, 2019 et 2020, ce qui vous permet de vous assurer que votre projet est prêt pour Unity 2020 et ce, même avant la mise à niveau d’Unity. Évaluez les [dépendances de plug-ins](https://docs.unity3d.com/Manual/Plugins.html) qui existent actuellement dans votre projet et déterminez si ces DLL peuvent être créées pour ARM64. Pour les projets avec un plug-in dépendant ARM64, vous devrez peut-être continuer à créer votre application pour ARM.

## <a name="update-sceneproject-settings-in-unity"></a>Mettre à jour les paramètres de scène et de projet dans Unity

Après la mise à jour vers [Unity 2020.3 LTS](https://unity3d.com/unity/qa/lts-releases), nous vous recommandons de mettre à jour certains paramètres dans Unity pour des résultats optimaux sur l’appareil. Ces paramètres sont décrits en détail sous [Paramètres recommandés pour Unity](../unity/Recommended-settings-for-Unity.md).

En résumé, le [back-end d’écriture de script .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) est déconseillé dans Unity 2018 et **supprimé** dans Unity 2019. Les développeurs doivent sérieusement envisager de basculer leur projet vers [IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP.html)

> [!NOTE]
> Il est possible que le back-end d’écriture de code IL2CPP entraîne des temps de génération plus longs entre Unity et Visual Studio. Les développeurs doivent configurer leur ordinateur de développement de manière à [optimiser les temps de génération IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Il peut également être avantageux de configurer un [serveur de cache](https://docs.unity3d.com/Manual/CacheServer.html), en particulier pour les projets Unity qui comprennent une grande quantité de ressources (à l’exclusion des fichiers de script) ainsi que pour les scènes et les ressources qui changent constamment. Lorsque vous ouvrez un projet, Unity stocke les ressources éligibles dans un format de cache interne sur l’ordinateur de développement. Les éléments doivent être réimportés et retraités après modification. Ce processus peut être effectué une fois puis enregistré dans un serveur de cache. Pour gagner du temps, vous pouvez le partager avec les autres développeurs, au lieu que chaque développeur réimporte localement les éléments modifiés.

Une fois qu’ils ont pris en compte les changements importants entraînés par la mise à jour de la version de Unity, générez et testez vos applications actuelles sur HoloLens (1re génération). C’est le bon moment pour créer et enregistrer une validation dans le contrôle de code source.

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compiler des dépendances ou des plug-ins pour processeurs ARM

HoloLens (1re génération) exécutait les applications sur un processeur x86 alors que l’HoloLens 2 utilise un processeur ARM. Les applications HoloLens existantes doivent être portées pour prendre en charge ARM. Comme indiqué plus haut, Unity 2018 LTS prend en charge la compilation d’applications ARM32, alors qu’Unity 2019 et les versions ultérieures prennent en charge la compilation d’applications ARM32 et ARM64. Il est recommandé de développer des applications ARM64, car celles-ci fournissent de meilleures performances. Toutefois, cela nécessite que toutes les [dépendances de plug-ins](https://docs.unity3d.com/Manual/Plugins.html) soient également conçues pour ARM64.

Passez en revue toutes les dépendances DLL qui se trouvent dans votre application. Nous vous recommandons de supprimer les dépendances qui ne sont plus nécessaires pour votre projet. Pour les autres plug-ins nécessaires, ingérez les fichiers binaires ARM32 ou ARM64 dans votre projet Unity.

Après l’ingestion des DLL nécessaires, créez une solution Visual Studio dans Unity et compilez un AppX pour ARM dans Visual Studio afin de tester si votre application peut être conçue pour les processeurs ARM. Il est conseillé d’enregistrer l’application sous forme de commit dans votre solution de contrôle de code source.

> [!IMPORTANT]
> Vous pouvez exécuter l’application utilisant MRTK v1 sur HoloLens 2 après avoir remplacé la cible de build par ARM, à supposer que toutes les autres conditions soient remplies. Vous devez donc veiller à disposer des versions ARM de tous vos plug-ins. Toutefois, votre application n’aura pas accès aux fonctions spécifiques à HoloLens 2 comme la main articulée et le suivi oculaire. MRTK v1 et MRTK v2 ont des espaces de noms différents qui permettent aux deux versions d’être dans le même projet, ce qui est utile pour passer de l’une à l’autre.

## <a name="update-to-mrtk-version-2"></a>Effectuer une mise à jour vers MRTK version 2

[MRTK version 2](https://github.com/microsoft/MixedRealityToolkit-Unity) est le nouveau kit d’outils en supplément de Unity qui prend en charge à la fois HoloLens (1re génération) et HoloLens 2. Il s’agit également du kit dans lequel toutes les nouvelles fonctionnalités HoloLens 2 ont été ajoutées, notamment les interactions avec les mains et le suivi oculaire.

Pour plus d’informations sur l’utilisation de MRTK version 2, consultez les ressources suivantes :

- [Page d’accueil Documentation MRTK](/windows/mixed-reality/mrtk-unity)
- [Guide d'installation](/windows/mixed-reality/mrtk-unity/install-the-tools)
- [MRTK - Suivi de la main](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
- [MRTK - Suivi du regard](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

### <a name="prepare-for-the-migration"></a>Se préparer à la migration

Avant d’ingérer les nouveaux [fichiers *.unitypackage pour MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), il est recommandé d’effectuer un inventaire de **1) tout code personnalisé intégré à MRTK v1** et **2) tout code personnalisé pour les interactions d’entrée ou les composants d’expérience utilisateur**. Lors de l’ingestion de MRTK v2, le conflit le plus fréquemment rencontré par les développeurs de réalité mixte concerne les entrées et les interactions. Nous vous recommandons de lire l’article concernant le [modèle d’entrée MRTK v2](/windows/mixed-reality/mrtk-unity/features/input/overview).

Enfin, [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) est passé d’un modèle de scripts et d’objets gestionnaires en scène à une architecture de configuration et de fournisseur de services. La hiérarchie de scène et le modèle d’architecture sont désormais plus propres. Toutefois, ce changement nécessite que vous compreniez les nouveaux profils de configuration. Lisez le [Guide de configuration de Mixed Reality Toolkit](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) pour vous familiariser avec les profils et les paramètres importants que vous devez adapter aux besoins de votre application.

### <a name="migrating-the-project"></a>Migration du projet

Après l’importation de [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), votre projet Unity comprend probablement plusieurs erreurs liées au compilateur. Ces erreurs sont généralement dues à la nouvelle structure des espaces de noms et aux nouveaux noms de composants. Pour corriger ces erreurs, dans vos scripts, remplacez les anciens espaces de noms et composants par les nouveaux.

Pour plus d’informations sur les différences entre HTK/MRTK et MRTK v2 au niveau des API, consultez le guide de portage sur le [wiki MRTK Version 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide).

### <a name="best-practices"></a>Bonnes pratiques

- Privilégier l’utilisation du [nuanceur MRTK standard](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).
- Travailler sur un seul changement important à la fois (par exemple, passer de IFocusable à [IMixedRealityFocusHandler](/dotnet/api/microsoft.mixedreality.toolkit.input.imixedrealityfocushandler)).
- Effectuer des tests après chaque modification et utiliser le contrôle de code source.
- Utiliser l’expérience utilisateur MRTK par défaut (boutons, fenêtres, etc.) dans la mesure du possible.
- Éviter de modifier directement les fichiers MRTK. Pour cela, ajouter des wrappers autour des composants MRTK.
  - Cette action facilite les futures mises à jour et ingestion de MRTK.
- Explorer les exemples de scènes fournis dans MRTK (surtout *HandInteractionExamples.scene*).
- Recréer une interface utilisateur basée sur les canevas avec des quadrants, des colliders et du texte TextMeshPro.
- Activer [Partage de mémoire tampon en profondeur](../unity/camera-in-unity.md#sharing-depth-buffers) ou [définir le point de focus](../unity/focus-point-in-unity.md) ; préférer utiliser une mémoire tampon de profondeur 16 bits pour obtenir de meilleures performances. Vérifier lors de l’affichage de la couleur que la profondeur est également affichée. Unity n’écrit généralement pas de profondeur pour les gameobjects transparents et de texte.
- Définir le chemin de rendu d’instance à passage unique.
- Utilisez le [profil de configuration HoloLens 2 pour MRTK](/windows/mixed-reality/mrtk-unity/features/profiles/profiles#hololens-2-profile).

### <a name="testing-your-application"></a>Test de votre application

Dans MRTK Version 2, vous pouvez simuler des interactions avec les mains directement dans Unity et développer avec les nouvelles API pour les interactions avec les mains et le suivi oculaire. L’appareil HoloLens 2 est nécessaire pour créer une expérience utilisateur satisfaisante. Nous vous invitons à commencer à étudier la documentation et les outils pour mieux comprendre de quoi il s’agit. [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) prend en charge le développement sur HoloLens 1re génération. Les modèles d’entrée traditionnels, comme la sélection via un clic dans l’air, peuvent être testés sur HoloLens (1re génération). 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Mise à jour de votre modèle d’interaction pour HoloLens 2

> [!CAUTION]
> Si votre projet utilise des API XR.WSA, celles-ci seront progressivement supprimées au profit des nouvelles API d’entrée XR d’Unity dans les futures versions d’Unity. Vous trouverez plus d’informations sur les [API d’entrée XR ici](https://docs.unity3d.com/Manual/xr_input.html).

Une fois que votre application est portée et préparée pour HoloLens 2, vous êtes prêt pour la mise à jour de votre modèle d’interaction et des positionnements de vos conceptions d’hologrammes.
Dans HoloLens (1re génération), votre application comprend probablement un modèle d’interaction de type « Suivi et validation » avec des hologrammes relativement lointains qui rentrent entièrement dans le champ de vision.

Voici les étapes permettant de mettre à jour votre application afin de l’adapter à HoloLens 2 :
1.  Composants MRTK : En fonction du travail préalable, si vous avez ajouté [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), vous pourrez tirer parti de plusieurs composants ou scripts conçus et optimisés pour HoloLens 2.

2.  Modèle d’interaction : Envisagez de mettre à jour votre modèle d’interaction. Pour la plupart des scénarios, nous vous recommandons de passer du modèle « Suivi et validation » au modèle d’interaction manuelle. Étant donné que les hologrammes sont généralement hors de portée, le passage à l’interaction manuelle permet des rayons de pointage plus lointains et des mouvements de saisie.

3.  Positionnement des hologrammes : Une fois que vous êtes passé au modèle d’interaction manuelle, vous pouvez rapprocher les hologrammes afin d’interagir directement avec eux, en utilisant des mouvements de saisie à l’aide de vos mains. Les types d’hologrammes qu’il est recommandé de rapprocher dans le but de les manipuler directement sont les menus, les contrôles et les boutons de petite taille, ainsi que les hologrammes qui rentrent entièrement dans le champ de vision HoloLens 2 lorsque vous les manipulez ou les inspectez.
<br>
Les applications et les scénarios ont tous leurs propres spécificités. Nous continuerons donc à affiner et à publier des conseils de conception adaptées à chaque situation, en nous basant sur vos commentaires et sur vos expériences.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Autres avertissements et informations sur le déplacement d’applications de x86 vers ARM

- Les applications Unity sont simples, car vous pouvez créer un pack d’applications ARM ou déployer directement sur l’appareil pour exécuter le pack. Le développement de certains plug-ins natifs Unity peut constituer un défi. Pour cette raison, vous devez mettre à niveau tous les plug-ins Unity natifs vers Visual Studio 2019, puis recréer pour ARM.

- Une application utilisait le plug-in Unity AudioKinetic Wwise, et cette version d’Unity n’avait pas de plug-in UWP ARM, ce qui rendait très difficile la réutilisation des fonctionnalités audio dans l’application en question pour qu’elles s’exécutent sur ARM. Vérifiez que tous les plug-ins nécessaires pour vos plans de développement sont installés et disponibles dans Unity.

- Dans certains cas, il est possible qu’un plug-in UWP/ARM n’existe pas pour les plug-ins requis par l’application, ce qui bloque la capacité à porter l’application et à l’exécuter sur HoloLens 2. Contactez votre fournisseur de plug-ins pour résoudre le problème et obtenir une prise en charge d’ARM.

- Dans les nuanceurs, minfloat et ses variantes (telles que min16float, minint, etc.) peuvent ne pas avoir le même comportement dans HoloLens 2 que dans HoloLens (1re génération). Ceux-ci ont pour but de garantir que le nombre de bits spécifié sera utilisé (au minimum). Avec les processeurs graphiques Intel/Nvidia, ils sont le plus souvent traités comme des 32 bits. Sur ARM, le nombre de bits spécifié est respecté. Dans la pratique, cela signifie que les nombres peuvent avoir une précision ou une portée moindre dans HoloLens 2 que dans HoloLens (1re génération).

- Les instructions _asm ne semblent pas fonctionner sur ARM, ce qui signifie que tout code utilisant les instructions _asm doit être réécrit.

- ARM ne prend pas en charge le jeu d’instructions SIMD, car plusieurs en-têtes, comme xmmintrin.h, emmintrin.h, tmmintrin.h et immintrin.h, ne sont pas disponibles sur ARM.

- Sur ARM, le compilateur du nuanceur est exécuté lors du premier appel de dessin, après le chargement du nuanceur ou après la modification d’un élément dont dépend le nuanceur, mais pas au moment du chargement du nuanceur. L’impact sur le taux de trames peut être visible, en fonction du nombre de nuanceurs qui doivent être compilés. Cela peut avoir des implications sur la façon dont les nuanceurs doivent être gérés, packagés et mis à jour sur HoloLens 2 par rapport à HoloLens (1re génération).

## <a name="see-also"></a>Voir aussi

* [Installer les outils](../install-the-tools.md)
* [MRTK - Guide d’installation](/windows/mixed-reality/mrtk-unity/install-the-tools)
* [Page d’accueil Documentation MRTK](/windows/mixed-reality/mrtk-unity)
* [Portage de HoloToolkit/MRTK sur MRTK version 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
* [Paramètres recommandés pour Unity](../unity/recommended-settings-for-unity.md)
* [Comprendre les performances pour la réalité mixte](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)