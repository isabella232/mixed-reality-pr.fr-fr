---
title: Présentation des logiciels et historique des versions
description: vue d’ensemble des principaux composants logiciels pour Windows Mixed Reality, les casques immersifs et leur historique des versions.
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, composants logiciels, historique des versions, notes de publication, historique des versions
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: e20b2075e45620a7533dbb2d369d00e73b98f9c7
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436633"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Vue d’ensemble des logiciels Mixed Reality et historique des versions

## <a name="introduction-to-mixed-reality-software"></a>Présentation du logiciel de réalité mixte

Windows Mixed Reality se compose des principaux composants logiciels suivants :

1. **portail de réalité mixte**, qui offre l’expérience Windows Mixed Reality principale
    * dans Windows 10 versions 1709 et 1803, le portail de réalité mixte est un composant clé du Windows 10 système d’exploitation mis à jour via Windows Update.
    * dans Windows 10 version 1809 et ultérieure, le portail de réalité mixte est mis à jour via l’application Microsoft Store.
    * dans Windows 11 version 21H2.
2. Le **package feature-on-demand** (DOM) de la réalité mixte, téléchargé et installé automatiquement lors de la première exécution du portail de réalité mixte. Vous trouverez plus d’informations sur le package DOM [ici](/windows/application-management/manage-windows-mixed-reality) .
3. le **casque de réalité mixte et le pilote de contrôleur de mouvement**, également connu sous le nom de pilote de capteurs HoloLens, est le package de pilotes de clé qui permet à Windows Mixed Reality casques de fonctionner avec Windows Mixed Reality. il est automatiquement téléchargé et installé via Windows Update la première fois que votre casque de réalité mixte est branché, et est régulièrement mis à jour via Windows Update
4. Les pilotes de modèle de contrôleur de mouvement de réalité mixte * * contiennent les modèles 3D des contrôleurs de mouvement de réalité mixte et requis pour les expériences de réalité mixte tierces. il est automatiquement téléchargé et installé via Windows Update la première fois que vos contrôleurs de mouvement de réalité mixte sont associés à votre PC et mis à jour via Windows Update
5. **Windows 10, version 1709 (la mise à jour du créateur de automne) ou plus récente,** contient des technologies et des composants de système d’exploitation clés qui activent Windows Mixed Reality

l’utilisation de Windows Mixed Reality dans SteamVR nécessite les logiciels suivants :

6. **SteamVR**, développée et gérée par Valve Corporation, qui permet aux applications de réalité virtuelle et aux jeux sur vapeur. Vous trouverez plus d’informations [ici](https://go.microsoft.com/fwlink/?linkid=862788).
7. **Windows Mixed Reality pour** le composant SteamVR, qui pont SteamVR avec Windows Mixed Reality. vous trouverez plus d’informations sur ce composant [sur la page Windows Mixed Reality pour SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

gestion de votre casque Windows Mixed Reality :

8. l' **application compagnon d’appareils**, développée et gérée par chacun des fabricants de casque, offre une introduction rapide à votre casque Windows Mixed Reality. sur les casques dotés de la fonctionnalité de Bluetooth intégrée, l’application compagnon de l’appareil permet de restaurer les contrôleurs de mouvement à leur Bluetooth d’usine. Certains casques (tels que Samsung Odyssey et Samsung Odyssey +) utilisent également l’application Device Companion pour remettre les mises à jour du microprogramme du casque du fabricant du casque. cette application est téléchargée automatiquement la première fois que votre casque est branché et se trouve dans le Menu démarrer de Windows.

## <a name="windows-11-release-notes---october-2021"></a>notes de publication de Windows 11-octobre 2021

### <a name="infinite-expanse"></a>Étendue infini

<img src="images\infinite-expanse-win11.png" alt="The Infinite Explanse environment">

<br>

* un nouvel environnement d’hébergement virtuel pour les appareils Windows Mixed Reality présentant une réduction significative de l’étendue et de la taille, rationalisé jusqu’à l’étape singulière au lieu des Cliffhouse plus riches en fonctionnalités. 
* Conçu avec des performances à l’esprit, le étendue infini a été conçu pour répondre aux demandes des clients de longue durée pour un environnement d’hébergement virtuel nécessitant moins de ressources, qui permet aux clients d’obtenir des performances optimales de leurs jeux et expériences. 
* Ce nouvel environnement d’hébergement virtuel se trouve dans le **panneau broches** , dans le menu **emplacements** . 

### <a name="steamvr-boot-with-mixed-reality-portal-launch"></a>Lancement de SteamVR avec le portail de réalité mixte

* Nouveau paramètre disponible pour lancer automatiquement SteamVR lors du lancement de WMR, ce qui vous permet de contourner l’espace de bureau WMR et d’accéder directement à SteamVR.
   * ce nouveau paramètre se trouve dans l’application **Paramètres** en **> de démarrage et de bureau > démarrage automatique**.
    
### <a name="new-startup-experience-settings"></a>Nouveaux paramètres d’expérience de démarrage

* Nouveaux paramètres disponibles pour mieux configurer votre expérience de démarrage idéale en accroissant votre niveau de contrôle sur le lancement du portail de réalité mixte.
* Vous pouvez désormais contrôler si le portail de réalité mixte est lancé lorsqu’un appareil est connecté ou lorsque le capteur de présence est activé, ainsi que pour contrôler le mode d’ouverture de l’application de bureau virtuel.
* ces nouveaux paramètres se trouvent dans l’application **Paramètres** en **réalité mixte > Startup and Desktop**
    * Basculez vers démarrer le calcul MRP sur le plug-in HMD.
    * Activez démarrer le calcul MRP en cas de détection de la présence.
    * Active/désactive l’application de bureau ouverte sur le focus de l’application de bureau.

### <a name="prior-release-notes"></a>Notes de publication antérieures

* [Notes de publication-mai 2020](release-notes-may-2020.md)
* [Notes de publication-mai 2019](release-notes-may-2019.md)
* [Notes de publication - Octobre 2018](release-notes-october-2018.md)
* [Notes de publication-2018 avril](release-notes-april-2018.md)
* [Notes de publication - Octobre 2017](release-notes-october-2017.md)
* [Notes de publication - Août 2016](release-notes-august-2016.md)
* [Notes de publication - Mai 2016](release-notes-may-2016.md)
* [Notes de publication - Mars 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Casque de la réalité mixte et historique des versions du pilote de contrôle de mouvement ###

ce pilote est téléchargé et installé automatiquement via Windows Update, mais les liens de téléchargement sont fournis en ligne :

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, version 2004 (mai 2020 mise à jour) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 mars 2021  | Compatible avec Windows 10, la version 1903 et les versions ultérieures.<br/><ul><li>Mettez à jour l’ordre d’enroulement du maillage de la zone masquée pour que la réverbération HP G2 soit cohérente avec d’autres casques.</li><li>Améliorations de la qualité des visuels pour les casques de réverbération de HP G2.</li><li>Windows Mixed Reality les améliorations de la plateforme et de la fiabilité du casque.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 décembre 2020  | Compatible avec Windows 10, la version 1903 et les versions ultérieures.<br/><ul><li>Nouveau microprogramme de contrôleur pour le contrôleur HP afin de résoudre un problème où certains contrôleurs ont des déclencheurs non fonctionnels.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 octobre 2020  | Compatible avec Windows 10, la version 1903 et les versions ultérieures.<br/><ul><li>Prise en charge officielle de la réverbération HP G2, HP Omnicept et du nouveau contrôleur HP.</li><li>Corrections d’affichage mineur pour les casques HP et Samsung Odyssey +. (Nécessite la version 19041,546 ou une version ultérieure [du système d’exploitation](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) ou [des versions de système d’exploitation 18362,1110 et 18363,1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) ).</li><li>Améliorations de la transition de l’état d’alimentation de l’ordinateur du mode veille à la réduction des erreurs SWW 1-4.</li><li>Windows Mixed Reality les correctifs mineurs de la plateforme du casque et les améliorations de fiabilité.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 mai, 2020      | Compatible avec Windows 10, la version 1903 et les versions ultérieures.<br/><ul><li>Windows Mixed Reality les correctifs mineurs de la plateforme du casque et les améliorations de fiabilité.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, version 1903 (mai 2019 mise à jour) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 octobre 2019      | Compatible avec Windows 10, version 1809 et versions ultérieures.<br/><ul><li>correctifs mineurs de la plateforme Windows Mixed Reality casque.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 juin 2019      | Compatible avec Windows 10, version 1809 et versions ultérieures.<br/><ul><li>Windows Mixed Reality les améliorations de la plateforme et de la fiabilité du casque sur les ordinateurs en sommeil et les transitions d’état d’alimentation.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1er mai 2019      | Compatible avec Windows 10, version 1809 et versions ultérieures.<br/><ul><li>contient la mise à jour du microprogramme des casques 2017 Acer, Asus, Dell, Fujitsu, HP, Lenovo et Medion Windows Mixed Reality. Cette mise à jour du microprogramme améliore la compatibilité et la fiabilité de l’affichage du casque avec certaines cartes graphiques ou pilotes graphiques.</li><li>Windows Mixed Reality les améliorations de la plateforme et de la fiabilité du casque</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, version 1803 (mise à jour d’avril 2018) et version 1809 (mise à jour d’octobre 2018) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 janvier 2019      | Compatible avec Windows 10, la version 1803 et les versions ultérieures.<br/><ul><li>Correction du suivi des casques et des interruptions</li><li>Correctifs de fiabilité en mode lampe</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1er octobre 2018      | Version publique initiale du pilote pour Windows 10, version 1809.<br/>Compatible avec Windows 10, la version 1803 et les versions ultérieures.<br/><ul><li>active les nouvelles fonctionnalités de Windows Mixed Reality, telles que le mode torche, dans Windows 10, version 1809</li><li>Suivi des casques et améliorations de la fiabilité</li><li>Amélioration des performances et du suivi du contrôleur de mouvement</li><li>Performances et améliorations USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 avril 2018      | version publique initiale du pilote pour Windows 10, version 1803<br/> <ul><li>Suivi des casques et améliorations de la fiabilité</li><li>Amélioration des performances et du suivi du contrôleur de mouvement</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, version 1709 (automne Creators Update) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 février 2018    | <ul><li>Prise en charge officielle du casque 3Glasses Blubur S2 Mixed Reality</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 décembre 2017   | <ul><li>Résout un problème HID conduisant à *un* problème avec le code d’erreur 2181038087-7 sur certains PC</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 décembre 2017    | <ul><li>Suivi amélioré du casque</li><li>Améliorations de la réactivité du pavé tactile du contrôleur de mouvement</li><li>Résout un problème dans lequel l’installation du pilote peut parfois échouer</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 novembre, 2017   | <ul><li>Résout un problème qui a conduit au casque, parfois en noir pendant son utilisation</li><li>Résout un problème qui provoquait parfois l’apparition de contrôleurs de mouvement</li><li>Améliorations des performances du capteur de présence pour le casque Dell Visor</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | 10.0.16299.1036  | 7 novembre 2017    | <ul><li>Améliorations du mécanicien levant le contrôleur de mouvement :<ul><li>La rapidité sera désormais signalée correctement lorsque la précision de la position sera approximative, vous pouvez donc vous lancer en arrière-plan !</li><li>Vous trouverez un exemple de code pour la levée dans le package Unity « ThrowingStarter » [ici](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/). Ouvrir la scène de levée pour commencer</li></ul></li><li>Amélioration des rapports sur les batteries du contrôleur de mouvement</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | 10.0.16299.1012  | 17 octobre 2017    | Version publique initiale du pilote                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Historique de publication du pilote de modèle de contrôle de mouvement de réalité mixte ###

ce pilote est également automatiquement téléchargé et installé via Windows Update, mais des liens de téléchargement sont disponibles en ligne :

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, version 2004 (mai 2020 mise à jour)

| Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | Le 16 septembre 2020      | Version publique initiale du pilote pour les nouveaux contrôleurs de mouvement HP. Compatible avec Windows 10, la version 1903 et les versions ultérieures. Ce pilote est compatible uniquement avec les nouveaux contrôleurs de mouvement HP.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, version 1803 (mise à jour d’avril 2018) et version 1809 (mise à jour d’octobre 2018) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1er octobre 2018      | Version publique initiale du pilote pour Windows 10, version 1809. Compatible avec Windows 10, la version 1803 et les versions ultérieures.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 avril 2018      | version publique initiale du pilote pour Windows 10, version 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, version 1709 (automne Creators Update) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 octobre 2017    | Version publique initiale du pilote                          |

### <a name="mixed-reality-portal-release-history"></a>Historique de publication du portail de réalité mixte ###

dans Windows 10, version 1809 et plus récent, le [portail de réalité mixte](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) est mis à jour via l’application Microsoft Store.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, version 1809 et versions ultérieures ####

   | Version            | Date de sortie          | Modifications majeures                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 8 juin 2021          | <ul><li>ajoute des liens de dépannage vers l’application Aide pour les erreurs courantes du casque.</li><li>Résout un problème où l’application auxiliaire de l’appareil du casque peut être ignorée lors de la configuration initiale.</li><li>Met à jour la page Configuration requise avec des informations supplémentaires sur les casques haute résolution.</li><li>Met à jour l’écran de démarrage et la page d’accueil avec de nouveaux visuels.</li></ul>  |
   | 2000.21041.1051.0  | 26 avril 2021        | <ul><li>Met à jour l’icône d’application pour le portail de réalité mixte.</li></ul>  |
   | 2000.20111.1381.0  | 10 décembre 2020     | <ul><li>Met à jour la page d’accueil du portail de réalité mixte.</li><li>Réduit les erreurs de connectivité du casque lors des mises à jour du microprogramme. </li></ul>  |
   | 2000.20071.1133.0  | 5 août 2020        | <ul><li>Prise en charge de [OpenXR](/windows/mixed-reality/openxr) pour suspendre la fenêtre d’aperçu.</li></ul>  | 
   | 2000.20041.1212.0  | 11 mai 2020          | <ul><li>Résout un problème de minutage qui provoquait une erreur 15-5 incohérente.</li><li>amélioration de la prise en charge de l’exécution de Windows Mixed Reality sans connexion internet.</li><li>Amélioration de la prise en charge des contrôleurs de mouvement couplés via les **contrôleurs d’installation**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 avril 2020        | <ul><li>Prise en charge de l’inscription à des informations, des conseils et des offres sur Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | Février 11, 2020     | <ul><li>Prise en charge améliorée des applications utilisant [OpenXR](/windows/mixed-reality/openxr) sur les appareils avec la mise à jour 2019 de mai.</li><li>Résout les problèmes d’accessibilité et de focus clavier</li></ul>  | 
   | 2000.19101.1211.0  | 11 novembre 2019     | <ul><li>Résout un problème qui vous empêche de basculer des éléments visuels de limite de salle.</li><li>Résout un problème qui vous empêche de centrer un casque pendant la configuration de la limite d’espace.</li></ul>  | 
   | 2000.19081.1301.0  | 23 septembre 2019    | <ul><li>Résout un problème où un message d’erreur incorrect s’affiche avec des casques avec des problèmes matériels. Les utilisateurs qui ont reçu un code d’erreur 1-4 sur les versions précédentes peuvent désormais recevoir un code d’erreur plus spécifique pour leur état d’appareil.</li></ul>  |
   | 2000.19071.1302.0  | 13 août 2019     | <ul><li>Prise en charge des applications utilisant [OpenXR](/windows/mixed-reality/openxr) sur les appareils avec la mise à jour 2019 de mai.</li></ul>  | 
   | 2000.19061.1011.0  | 16 juillet 2019         | <ul><li>Prise en charge des options de configuration JSON pour personnaliser le comportement de l’application. En savoir plus sur [le programme d’installation pour obtenir des informations sur le lieu de divertissement avec Windows Mixed Reality](/windows/mixed-reality/location-based-experiences#setup).</li></ul>  | 

### <a name="steamvr-release-history"></a>Historique des versions SteamVR ###

Les notes de publication de la vanne pour SteamVR sont disponibles ici : [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality de l’historique des versions de SteamVR ###

vous trouverez les notes de publication pour le composant Windows Mixed Reality pour SteamVR ici :[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
