---
title: Installer les outils
description: MRTK-Unity, installer la page de documentation des outils
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Réalité mixte, développement, MRTK, kit de ressources de réalité mixte, installer, mis à jour, outils, prise en main, bases, Unity, Visual Studio, kit de ressources, casque de réalité mixte, casque de réalité mixte Windows, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur
ms.openlocfilehash: 117b34ae858e789b1366ce5338e23b8f366377ae
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550559"
---
# <a name="install-the-tools"></a>Installer les outils

Obtenez les outils dont vous avez besoin pour créer des applications Microsoft HoloLens et des casques immersifs Windows Mixed Reality (VR). Il n’existe pas de SDK de développement Windows Mixed Reality. Vous allez donc utiliser Visual Studio avec le SDK Windows 10.

Vous n’avez pas d’appareil de réalité mixte ? Vous pouvez installer l’[émulateur HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) pour tester certaines fonctionnalités des applications de réalité mixte sans HoloLens. Vous pouvez également utiliser le [simulateur Windows Mixed Reality](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator) pour tester les applications de réalité mixte pour des casques immersifs.

Cette page vous guide tout au long de l’installation des outils dont vous avez besoin pour utiliser MRTK avec Unity. Si vous souhaitez explorer d’autres plateformes de développement de la réalité mixte, consultez la page [Présentation du développement de la réalité mixte](/windows/mixed-reality/develop/development?tabs=unity).

Vous pouvez utiliser la simulation d’entrée du [Kit de ressources de réalité mixte pour Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) pour tester différents types d’interactions d’entrée, comme le suivi de la main et le suivi oculaire.

|CONSEIL : marquez cette page et consultez-la régulièrement pour être informé de la version la plus récente de chaque outil recommandé pour le développement de réalité mixte.|
|---|

## <a name="installation-checklist"></a>Liste de contrôle pour l’installation

| Outil | Remarques |
|---------|---------|
| ![Logo Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (lien vers l’installation manuelle)</a><br><br>Installez la version la plus récente de Windows 10 pour que le système d’exploitation de l’ordinateur soit le même que celui de la plateforme pour laquelle vous créez des applications de réalité mixte.  | **Installation de Windows 10** <br> Vous pouvez installer la version la plus récente de Windows 10 via Windows Update, dans les paramètres, ou en créant un support d’installation à l’aide du lien situé dans la colonne de gauche. <br><br>Pour plus d’informations sur les dernières fonctionnalités de réalité mixte de chaque version de Windows 10, consultez les [notes de publication de la dernière version](/windows/mixed-reality/enthusiast-guide/mixed-reality-software). **Activez le mode développeur sur votre PC** dans Paramètres > Mise à jour et sécurité > Pour les développeurs. <br><br> **Note pour les PC qui appartiennent ou sont gérés par l’entreprise**<br>Si votre PC est géré par le service informatique de votre entreprise, vous aurez probablement besoin de le contacter pour les mises à jour. <br><br> **Versions « N » de Windows**<br> les casques immersifs Windows Mixed Reality ne sont pas pris en charge sur les versions « N » de Windows. |
| ![Image de logo Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (version 16.8 ou ultérieure)** (lien d’installation)</a> <br><br>Environnement de développement intégré (IDE) complet pour Windows, et bien plus encore. Vous utiliserez Visual Studio pour écrire, déboguer, tester et déployer du code. | **Installation de Visual Studio 2019** <br> Veillez à installer les charges de travail suivantes : <br><br>*● Développement Desktop en C++*<br>*● Développement UWP (Plateforme Windows universelle)*<br><br>Dans la charge de travail UWP, n’oubliez pas de sélectionner le composant facultatif suivant si vous développez pour HoloLens :<br><br>*● Connectivité des appareils USB*<br><br>**Note sur Unity**<br>Sauf si vous essayez intentionnellement d’installer une version plus récente (non LTS) de Unity dans un but spécifique, nous vous recommandons de *ne pas installer* la charge de travail Unity dans le cadre de l’installation de Visual Studio. Nous recommandons au lieu de cela d’installer le flux **Unity 2019 LTS**, comme indiqué ci-dessous.<br><br>**Problèmes connus**<br>Il existe actuellement des problèmes connus liés au débogage des applications de réalité mixte dans Visual Studio 2019, version 16.0.  Veillez à effectuer la mise à jour vers **Visual Studio 2019 version 16.8 ou ultérieure**. |
| ![Logo Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (lien vers l’installation manuelle)</a> <br><br>Fournit les tout derniers en-têtes, bibliothèques, métadonnées et outils indispensables au développement des applications Windows 10 sur HoloLens 2. | **Pour créer des applications HoloLens 2, vous devez installer le kit SDK Windows, build 18362 ou ultérieur.**<br> <br> Si vous développez uniquement des applications pour les casques de réalité mixte Windows ou HoloLens (1re génération) de bureau, vous pouvez utiliser le SDK Windows installé par Visual Studio 2019. |
| ![Logo Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**Émulateur HoloLens 2 (Windows Holographique, version 20H2, mise à jour de février 2021)** (Lien d’installation : 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Émulateur HoloLens (1ère génération)** (Lien vers l’installation : 10.0.17763.134)</a> <br><br>L’émulateur vous permet d’exécuter des applications sur une image de machine virtuelle HoloLens si vous ne disposez pas d’un appareil HoloLens physique.<br> <br> | Pour bien démarrer avec l’émulateur, consultez [Utilisation de l’émulateur HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).<br> <br> **Votre système doit prendre en charge Hyper-V** pour que l’émulateur puisse être installé. Pour plus d’informations, consultez la section concernant la configuration système ci-dessous. <br> <br> **Remarque sur l’émulateur HoloLens (1ère génération)** <br>. Si vous installez l’émulateur HoloLens (1re génération) avec Visual Studio 2019, vous devez désélectionner les modèles VS et les [installer à partir de Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="unity"></a>Unity

Maintenant que vous avez Windows 10, Visual Studio et le SDK Windows 10 prêts à l’emploi, nous allons utiliser Unity en tant que moteur pour effectuer une build.

### <a name="1-download-the-latest-version"></a>1. Télécharger la dernière version

Nous vous recommandons d’utiliser le flux [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) pour les nouveaux projets. Veillez à installer la dernière révision pour bénéficier des derniers correctifs de stabilité.

* Il est recommandé d’utiliser [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4). Unity 2018.4 LTS est également pris en charge.
* Si vous souhaitez utiliser les fonctionnalités d’évaluation [OpenXR de réalité mixte](/windows/mixed-reality/develop/unity/openxr-getting-started) avec MRTK, vous avez besoin de Unity 2020.2 ou version ultérieure.
* Si vous devez utiliser une autre version de Unity pour des raisons spécifiques, vous pouvez installer différentes versions de Unity côte à côte.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Installer Mixed Reality Feature Tool

[Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) est un nouveau moyen pour les développeurs de découvrir et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity.

Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation. Une fois que vous avez validé les packages souhaités, l’outil Fonctionnalité de réalité mixte les télécharge dans le projet Unity de votre choix.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importation du Mixed Reality Toolkit

Vous pouvez télécharger le package Kit de ressources de réalité mixte en suivant les [instructions d’installation et d’utilisation](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements) et en sélectionnant le package Foundation du kit de ressources de réalité mixte.

Si vous préférez télécharger manuellement des packages MRTK à partir de GitHub, accédez à la page Mise en production sur [Kit de ressources réalité mixte - Unity (GitHub)](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurer votre PC pour le développement de réalité mixte

Le SDK Windows 10 fonctionne de manière optimale sur le système d’exploitation Windows 10. Ce SDK est également pris en charge par Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Notez que les systèmes d’exploitation plus anciens ne prennent pas en charge tous les outils.

| Vous pouvez développer et déployer vos applications pour HoloLens, les casques immersifs VR ou les deux. Veillez à répondre aux conditions ci-dessous en fonction de vos besoins. |
|---|

#### <a name="for-hololens-development"></a>Pour le développement HoloLens

Lorsque vous configurez votre ordinateur de développement pour HoloLens, vérifiez qu’il répond aux exigences de configuration requises pour [Unity](https://docs.unity3d.com/Manual/system-requirements.html) et Visual Studio. Si vous souhaitez exécuter votre application sur un appareil HoloLens, vous devez suivre les [instructions de configuration du portail d’appareil Windows](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal). Si vous prévoyez d’utiliser l’[émulateur HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator), vérifiez également que votre PC répond à la [configuration système requise de l’émulateur HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements).

Pour bien démarrer avec l’émulateur HoloLens, consultez [Utilisation de l’émulateur HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).

Si vous prévoyez de développer des applications pour HoloLens et pour les casques immersifs (VR) Windows Mixed Reality, suivez les recommandations et les exigences système fournies dans la section ci-dessous.

### <a name="hololens-troubleshooting"></a>Résolution des problèmes concernant HoloLens

Le mode développeur est grisé

Si vous rencontrez des problèmes pour activer le mode développeur sur votre appareil, vous n’êtes peut-être pas le [propriétaire de l’appareil](/hololens/security-adminless-os). En mode multi-utilisateur, la personne qui utilise l’appareil en premier est le propriétaire de l’appareil et les utilisateurs suivants ne disposent pas des autorisations requises pour activer le mode développeur ni effectuer d’autres modifications de configuration. Toutefois, il existe une exception où le premier utilisateur peut ne pas être le propriétaire de l’appareil dans un environnement AutoPilot, ce qui est détaillé dans la [documentation sur la sécurité HoloLens](/hololens/hololens2-compliance).

Voici les solutions possibles :

* Faire en sorte que le propriétaire de l’appareil active le mode développeur avant de transmettre l’appareil à d’autres utilisateurs ou développeurs.
* Proposer à votre administrateur informatique/MDM d’activer la [stratégie CSP ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) pour l’appareil spécifique ou un groupe d’appareils de développeur.
Cette stratégie peut être définie par des [packages de provisionnement](/hololens/hololens-provisioning) ou via [MDM pour les appareils HoloLens](/hololens/hololens-mdm-configure).
* Utiliser l’application [ARC (Advanced Recovery Companion)](/hololens/hololens-recovery).

| Remarque : pour plus d’informations sur la gestion des appareils, consultez la présentation de la gestion des appareils HoloLens.|
|---|

Je ne parviens pas à effectuer le déploiement sur USB

Si vous n’êtes pas en mesure de déployer une application directement sur USB, vérifiez que vous avez rempli toutes les conditions d’installation listées ci-dessus et suivez notre [tutoriel pas à pas](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2).

Exigences de configuration du casque immersif (VR)

| Remarque : les instructions suivantes constituent les spécifications minimales actuellement recommandées qui s’appliquent à votre ordinateur de développement pour casques immersifs (VR). Ces instructions font l’objet de mises à jour régulières.|
|---|

| Avertissement : vous ne devez pas confondre ces instructions avec les [instructions de compatibilité matérielle minimale](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), qui listent les spécifications relatives à l’ordinateur personnel qui est ciblé par votre application ou votre jeu pour casque immersif (VR).|
|---|

Si votre ordinateur de développement pour casques immersifs n’a pas de ports HDMI et/ou USB 3.0 de taille suffisante, vous aurez besoin d’[adaptateurs](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) pour connecter votre casque.

Il existe actuellement des [problèmes connus](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) avec certaines configurations matérielles, en particulier avec les notebooks à l’affichage hybride.

. | Minimum | Recommandé
--- |--- |---
Processeur | Notebook : Processeur Intel Mobile Core i5 7e génération, double cœur avec hyper-threading Desktop : Processeur Intel Desktop i5 6e génération, double cœur avec hyper-threading OU AMD FX4350 quadruple cœur 4.2 Ghz| Desktop : Intel Desktop i7 6e génération (6 cœurs) OU AMD Ryzen 5 1600 (6 noyaux, 12 threads) GPU | Notebook : NVIDIA GTX 965M, AMD RX 460M (2 Go) ou supérieur, GPU compatible avec DX12 Desktop : NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 Go) ou supérieur, GPU compatible avec DX12 | Desktop : NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 Go) ou supérieur, GPU compatible avec DX12
Version WDDM du pilote GPU | Pilote WDDM 2.2
Enveloppe thermique | 15W ou supérieure
Ports d’affichage graphique | 1 port d’affichage graphique disponible pour casque (HDMI 1.4 ou DisplayPort 1.2 pour les casques 60Hz, HDMI 2.0 ou DisplayPort 1.2 pour les casques 90Hz)
Résolution de l’affichage | Résolution : SVGA (800x600) ou une plus grande profondeur de couleurs : 32 bits de couleur par pixel
Mémoire | 8 Go de RAM ou plus | 16 Go de RAM ou plus
Stockage | > 10 Go d’espace libre supplémentaire
Ports USB | 1 port USB disponible pour les casques (USB 3.0 type A) Remarque : il doit fournir un minimum de 900mA
Bluetooth | Bluetooth 4.0 (connectivité des accessoires)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Maintenant que vous avez installé les outils, nous vous recommandons de suivre notre série de tutoriels MRTK HoloLens 2.
> [!div class="nextstepaction"]
> [Série de tutoriels HoloLens 2](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)