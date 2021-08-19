---
title: Installer les outils
description: Commencez ici avec les versions les plus récentes d’Unity, de Visual Studio et des outils recommandés pour le développement HoloLens et VR.
author: thetuvix
ms.author: alexturn
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: 7a4440ade98a592072d340457918dade90a65f28
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905632"
---
# <a name="install-the-tools"></a>Installer les outils

Obtenez les outils dont vous avez besoin pour créer des applications Microsoft HoloLens et des casques immersifs Windows Mixed Reality (VR). Il n’existe pas de SDK de développement Windows Mixed Reality. Vous allez donc utiliser Visual Studio avec le SDK Windows 10.

Vous n’avez pas d’appareil de réalité mixte ? Si vous ne disposez pas d’un appareil HoloLens, vous pouvez installer l’[émulateur HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md) pour tester certaines fonctionnalités des applications de réalité mixte. Vous pouvez également utiliser le [simulateur Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) pour tester les applications de réalité mixte si vous ne disposez pas d’un casque immersif.

Nous vous recommandons d’installer le moteur de jeu Unity ou Unreal comme méthode la plus simple pour commencer à créer des applications de réalité mixte. Toutefois, vous pouvez également créer sur DirectX si vous souhaitez utiliser un moteur personnalisé.

Si vous utilisez Unity, vous pouvez vous servir de la simulation d’entrée de [Mixed Reality Toolkit pour Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) pour tester différents types d’interactions d’entrée, comme le suivi de la main et le suivi oculaire. Pour les projets Unreal, utilisez le [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) pour tester les interactions d’entrée courantes et les fonctionnalités de l’expérience utilisateur.

>[!TIP]
>Ajoutez cette page à vos favoris, et consultez-la régulièrement pour être informé de la publication des nouvelles versions de chaque outil recommandé pour le développement de réalité mixte.

<br>

## <a name="installation-checklist"></a>Liste de contrôle pour l’installation

| Outil | Remarques |
|---------|---------|
| ![Logo Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (lien vers l’installation manuelle)</a><br><br>Installez la version la plus récente de Windows 10 pour que le système d’exploitation de l’ordinateur soit le même que celui de la plateforme pour laquelle vous créez des applications de réalité mixte.  | **Installation de Windows 10** <br> Vous pouvez installer la version la plus récente de Windows 10 via Windows Update, dans les paramètres, ou en créant un support d’installation à l’aide du lien situé dans la colonne de gauche. <br><br>Pour plus d’informations sur les dernières fonctionnalités de réalité mixte de chaque version de Windows 10, consultez les [notes de publication de la dernière version](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md). **Activez le mode développeur sur votre PC** dans Paramètres > Mise à jour et sécurité > Pour les développeurs. <br><br> **Note pour les PC qui appartiennent ou sont gérés par l’entreprise**<br>Si votre PC est géré par le service informatique de votre entreprise, vous aurez probablement besoin de le contacter pour les mises à jour. <br><br> **Versions « N » de Windows**<br> les casques immersifs Windows Mixed Reality ne sont pas pris en charge sur les versions « N » de Windows. |
| ![Image de logo Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (version 16.8 ou ultérieure)** (lien d’installation)</a> <br><br>Environnement de développement intégré (IDE) complet pour Windows, et bien plus encore. Vous utiliserez Visual Studio pour écrire, déboguer, tester et déployer du code. | **Installation de Visual Studio 2019** <br> Veillez à installer les charges de travail suivantes : <br><br>*● Développement Desktop en C++*<br>*● Développement UWP (Plateforme Windows universelle)*<br>*● Développement de jeux avec Unity (**si vous envisagez d’utiliser Unity**)*<br><br>Dans la charge de travail UWP, **assurez-vous que les composants suivants sont inclus pour l’installation** :<br><br>*● SDK Windows 10, version 10.0.19041.0 ou 10.0.18362.0*<br>*● Connectivité de périphérique USB (requise pour le déploiement/débogage vers HoloLens via USB)*<br>*● C++ (v142) Outils de la plateforme Windows universelle (requis lors de l’utilisation d’Unity)*<br><br>**Remarque à propos de HoloLens (1re génération) et des casques Windows Mixed Reality pour PC de bureau**<br>Si vous développez uniquement des applications pour les casques de réalité mixte Windows ou HoloLens (1re génération) de bureau, vous pouvez utiliser Visual Studio 2017 et le SDK Windows installé par celui-ci.<br><br>**Problèmes connus**<br>Il existe actuellement des problèmes connus liés au débogage des applications de réalité mixte dans Visual Studio 2019, version 16.0.  Veillez à effectuer la mise à jour vers **Visual Studio 2019 version 16.8 ou ultérieure**. |
| ![Logo Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2169418" target="_blank">**Émulateur HoloLens 2 (Windows Holographique, version 21H1, mise à jour d’août 2021)** (Lien d’installation : 10.0.20348.1010)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Émulateur HoloLens (1ère génération)** (Lien vers l’installation : 10.0.17763.134)</a> <br><br>L’émulateur facultatif vous permet d’exécuter des applications sur une image de machine virtuelle HoloLens si vous ne disposez pas d’un appareil HoloLens physique.<br> <br> | Pour bien démarrer avec l’émulateur, consultez [Utilisation de l’émulateur HoloLens facultatif](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md).<br> <br> **Votre système doit prendre en charge Hyper-V** pour que l’émulateur puisse être installé. Pour plus d’informations, consultez la section concernant la configuration système ci-dessous. <br> <br> **Remarque sur l’émulateur HoloLens (1ère génération)** <br>  Visual Studio 2017 est nécessaire pour terminer l’installation. Si vous installez l’émulateur HoloLens (1re génération) avec Visual Studio 2019, vous devez désélectionner les modèles VS et les [installer à partir de Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Installer le moteur de votre choix

Maintenant que votre kit de développement logiciel (SDK) Windows 10, Visual Studio et Windows 10 est prêt à l’emploi, nous allons installer et configurer le moteur de votre choix.

> [!div class="nextstepaction"]
> [Choix de votre moteur](choosing-an-engine.md)

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="setting-developer-mode-is-grayed-out"></a>Le mode développeur est grisé

Si vous rencontrez des problèmes pour activer le mode développeur sur votre appareil, vous n’êtes peut-être pas le [propriétaire de l’appareil](/hololens/security-adminless-os). En mode multi-utilisateur, la personne qui utilise l’appareil en premier est le propriétaire de l’appareil et les utilisateurs suivants ne disposent pas des autorisations requises pour activer le mode développeur ni effectuer d’autres modifications de configuration. Toutefois, il existe une exception où le premier utilisateur peut ne pas être le propriétaire de l’appareil dans un environnement AutoPilot, ce qui est détaillé dans la [documentation sur la sécurité HoloLens](/hololens/security-adminless-os#device-owner).

Voici les solutions possibles :

* Faire en sorte que le propriétaire de l’appareil active le mode développeur avant de transmettre l’appareil à d’autres utilisateurs ou développeurs.
* Proposer à l’administrateur informatique/MDM d’activer la stratégie CSP [ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) pour l’appareil spécifique ou un groupe d’appareils de développeur.
    * Cette stratégie peut être définie par des [packages de provisionnement](/hololens/hololens-provisioning) ou via [MDM pour les appareils HoloLens](/hololens/hololens-mdm-configure).
* Utiliser l’application [ARC (Advanced Recovery Companion)](/hololens/hololens-recovery).

> [!NOTE]
> Pour plus d’informations sur la gestion des appareils, consultez la vue d’ensemble de la **[gestion des appareils HoloLens](/hololens/hololens-csp-policy-overview)** .

#### <a name="i-cant-deploy-over-usb"></a>Je ne parviens pas à effectuer le déploiement sur USB

Si vous n’êtes pas en mesure de déployer une application directement sur USB, vérifiez que vous avez rempli toutes les conditions d’installation listées ci-dessus et suivez notre [tutoriel pas à pas](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).
