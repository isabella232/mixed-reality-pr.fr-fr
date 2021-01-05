---
title: Vue d’ensemble des logiciels Mixed Reality et historique des versions
description: Vue d’ensemble des principaux composants logiciels de Windows Mixed Reality et de leur historique de publication
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, les composants logiciels, l’historique des versions, les notes de publication, l’historique des versions
appliesto:
- Windows 10
ms.openlocfilehash: 31adf0572482cb9857ff94c2b7ef3aee4fe538d9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726020"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Vue d’ensemble des logiciels Mixed Reality et historique des versions

## <a name="introduction-to-mixed-reality-software"></a>Présentation du logiciel de réalité mixte

Windows Mixed Reality se compose des principaux composants logiciels suivants :

1. **Portail de réalité mixte**, qui offre l’expérience Windows Mixed Reality principale
    * Dans Windows 10 versions 1709 et 1803, le portail de réalité mixte est un composant clé du système d’exploitation Windows 10 mis à jour par le biais de Windows Update.
    * Dans Windows 10 version 1809 et versions ultérieures, le portail de réalité mixte est mis à jour par le biais de l’application Microsoft Store.
2. Le **package feature-on-demand** (DOM) de la réalité mixte, téléchargé et installé automatiquement lors de la première exécution du portail de réalité mixte. Vous trouverez plus d’informations sur le package DOM [ici](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality) .
3. Le **casque de réalité mixte et le pilote de contrôleur de mouvement**, également connu sous le nom de « pilote de capteurs HoloLens », est le package de pilotes clé qui permet aux casques de Windows Mixed Reality de fonctionner avec Windows Mixed Reality. Il est automatiquement téléchargé et installé via Windows Update la première fois que votre casque de réalité mixte est branché, et est régulièrement mis à jour via Windows Update
4. Les pilotes de modèle de contrôleur de mouvement de réalité mixte * * contiennent les modèles 3D des contrôleurs de mouvement de réalité mixte et requis pour les expériences de réalité mixte tierces. Il est automatiquement téléchargé et installé via Windows Update la première fois que vos contrôleurs de mouvement de réalité mixte sont associés à votre PC et mis à jour via Windows Update
5. **Windows 10, version 1709 (la mise à jour du créateur de automne) ou plus récent** , contient des technologies et des composants de système d’exploitation clés qui activent Windows Mixed Reality.

L’utilisation de Windows Mixed Reality dans SteamVR requiert les logiciels suivants :

6. **SteamVR**, développée et gérée par Valve Corporation, qui permet aux applications de réalité virtuelle et aux jeux sur vapeur. Vous trouverez plus d’informations [ici](https://go.microsoft.com/fwlink/?linkid=862788).
7. Le composant **Windows Mixed Reality for SteamVR** , qui pont SteamVR avec Windows Mixed Reality. Vous trouverez plus d’informations sur ce composant [sur la page Windows Mixed Reality for SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Gestion de votre casque Windows Mixed Reality :

8. L' **application compagnon d’appareils**, développée et gérée par chacun des fabricants de casque, offre une introduction rapide à votre casque Windows Mixed Reality. Sur les casques dotés de la fonctionnalité Bluetooth intégrée, l’application compagnon de l’appareil permet de restaurer les contrôleurs de mouvement à leur couplage Bluetooth d’usine. Certains casques (tels que Samsung Odyssey et Samsung Odyssey +) utilisent également l’application Device Companion pour remettre les mises à jour du microprogramme du casque du fabricant du casque. Cette application est téléchargée automatiquement la première fois que votre casque est branché et se trouve dans le menu Démarrer de Windows.

## <a name="windows-10-release-notes---may-2020"></a>Notes de publication de Windows 10-mai 2020

La **mise à jour Windows 10 mai 2020 (V2004)** comprend de nouvelles fonctionnalités pour les casques de Windows Mixed Reality (VR), telles que la possibilité de lancer des applications Win32 dans la réalité mixte. HoloLens (1re génération) est dans le service à long terme (LTS), avec des mises à jour de maintenance à publier chaque mois.

Mise à niveau vers la dernière version de PC pour les casques de Windows Mixed Realing (VR), ouvrez **paramètres > mettre à jour & sécurité** et sélectionnez **Rechercher les mises à jour**. Sur un PC Windows 10, vous pouvez également installer manuellement la **mise à jour de Windows 10 2020** à l’aide de l' [outil de création de médias Windows](https://www.microsoft.com/software-download/windows10).

**Dernière version pour ordinateur de bureau**: Windows 10 V2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Mises à jour pour les casques immersif Windows Mixed Reality

#### <a name="introducing-the-new-microsoft-edge"></a>Présentation du nouveau Microsoft Edge
Comme [annoncé précédemment](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), nous avons apporté des mises à jour pour une meilleure prise en charge de l’utilisation du nouveau navigateur Microsoft Edge dans Windows Mixed Reality. Le nouveau Microsoft Edge adopte le projet open source de chrome afin de créer une meilleure compatibilité Web pour les clients et de réduire la fragmentation du Web pour tous les développeurs Web. Il prend également en charge WebXR, la nouvelle norme pour créer des expériences Web immersifs pour les casques VR, à la place de WebVR.

#### <a name="improved-settings-for-wmr"></a>Paramètres améliorés pour WMR
Grâce à vos commentaires, nous avons ajouté et clarifié les paramètres sur la page d’affichage du casque :

* **Qualité visuelle de mon domicile** -la modification de ces paramètres affecte uniquement l’environnement d’hébergement de la réalité mixte (maison et Skyloft de la falaise) :

* **Ajuster le niveau de détail et la qualité des effets dans la vie de la réalité mixte** : cela modifie certains des effets de rendu que nous utilisons dans la page d’hébergement. En particulier, la qualité visuelle des différents matériaux (le bois, le béton, etc.) sera mise à l’échelle à mesure que vous modifiez ce paramètre de faible à élevé.

* **Modifier la résolution** de la fenêtre d’application : par défaut, la plupart des fenêtres 2D lancées à la page d’hébergement sont lancées avec une résolution de 720-p. Si vous pouvez les redimensionner manuellement horizontalement & verticalement, vous pouvez également choisir de les lancer tous sur 1080p à la place. Précédemment, cette option était disponible en tant qu’option très élevée (bêta) sous qualité visuelle. Nous l’avons correctement scindée en tant que paramètre distinct maintenant.

* **Options d’expérience** : ces options permettent d’ajuster l’expérience de la réalité mixte afin de réduire la charge sur les systèmes où le matériel peut éprouver des difficultés à respecter une 90 d’images à une fréquence illimitée. Vous pouvez activer ou désactiver explicitement ces paramètres supplémentaires, ou choisir laisser Windows décider et laisser nos heuristiques décider quand les activer ou les désactiver.

* **Résolution** : Si vous avez un casque haute résolution tel que le réverbe HP, nous prenons en charge son exécution à sa résolution native ou à une résolution réduite pour des raisons de performances. Les casques antérieurs, tels que Samsung Odyssey et Odyssey +, ne prennent en charge qu’une seule résolution, vous ne pouvez donc pas modifier ce paramètre sur ces casques.

* **Fréquence d’images** : vous pouvez maintenant définir manuellement la fréquence d’images de l’affichage du casque, ou continuer à laisser Windows utiliser ses heuristiques pour déterminer si 60 hz ou 90 Hz est plus approprié.

* **Étalonnage** : comme précédemment, vous pouvez ajuster votre IPD (distance interpupillary) si elle est prise en charge par votre casque.

* **Basculement d’entrée** : basculez le comportement de basculement du focus d’entrée (Win + Y) pour qu’il soit automatique (en fonction des commentaires du capteur de présence) ou manuel.

#### <a name="new-cortana-app"></a>Nouvelle application Cortana
Cette mise à jour de Windows comprend la version la plus récente de l’application Cortana, qui est actuellement en anglais uniquement et qui ne prend plus en charge certaines commandes spécifiques à la réalité mixte comme « prendre une photo » et « prendre une vidéo ». Vous pouvez utiliser le nouveau Cortana pour lancer des applications. de plus, il prend en charge de nouvelles commandes axées sur la productivité telles que « quand est-ce que j’ai ma prochaine réunion ? ». ou « envoyez un e-mail à <name> ce que je suis en retard ».
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Mises à jour supplémentaires disponibles dans 19041,546 (publiée le 2020 octobre)
Cette mise à jour mensuelle de maintenance des postes de travail comprend les modifications suivantes pour les appareils Windows Mixed Reality : 
* Réduit les distorsions et les aberrations dans les affichages montés en tête de Windows Mixed Reality (HMD). 
* Ajoute la prise en charge des prochains contrôleurs de mouvement HP Windows Mixed Reality. 
* Modifie le comportement du paramètre de fréquence d’actualisation de 90 Hz dans Windows Mixed realisation pour qu’il ne repasse plus automatiquement à 60 Hz dans certains cas quand 90 Hz ne peut pas être atteint. 

#### <a name="help-us-improve"></a>Aidez-nous à améliorer !
Nous cherchons continuellement à améliorer la compatibilité.  Si vous trouvez que votre application Win32 classique favorite ne se comporte pas correctement dans Windows Mixed Reality, envoyez vos commentaires via notre [Hub de commentaires](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Notes de publication antérieures

* [Notes de publication-mai 2019](release-notes-may-2019.md)
* [Notes de publication - Octobre 2018](release-notes-october-2018.md)
* [Notes de publication-2018 avril](release-notes-april-2018.md)
* [Notes de publication - Octobre 2017](release-notes-october-2017.md)
* [Notes de publication - Août 2016](release-notes-august-2016.md)
* [Notes de publication - Mai 2016](release-notes-may-2016.md)
* [Notes de publication - Mars 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Casque de la réalité mixte et historique des versions du pilote de contrôle de mouvement ###

Ce pilote est téléchargé et installé automatiquement via Windows Update, mais les liens de téléchargement sont fournis en ligne :

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, version 2004 (mai 2020 mise à jour) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 décembre 2020  | Compatible avec Windows 10, version 1903 et versions ultérieures.<br/><ul><li>Nouveau microprogramme de contrôleur pour le contrôleur HP afin de résoudre un problème où certains contrôleurs ont des déclencheurs non fonctionnels.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 octobre 2020  | Compatible avec Windows 10, version 1903 et versions ultérieures.<br/><ul><li>Prise en charge officielle de la réverbération HP G2, HP Omnicept et du nouveau contrôleur HP.</li><li>Corrections d’affichage mineur pour les casques HP et Samsung Odyssey +. (Nécessite la version 19041,546 ou une version ultérieure [du système d’exploitation](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) ou [des versions de système d’exploitation 18362,1110 et 18363,1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) ).</li><li>Améliorations de la transition de l’état d’alimentation de l’ordinateur du mode veille à la réduction des erreurs SWW 1-4.</li><li>Correctifs de la plateforme du casque Windows Mixed realisation et améliorations de la fiabilité.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 mai, 2020      | Compatible avec Windows 10, version 1903 et versions ultérieures.<br/><ul><li>Correctifs de la plateforme du casque Windows Mixed realisation et améliorations de la fiabilité.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, version 1903 (mai 2019 mise à jour) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 octobre 2019      | Compatible avec Windows 10, version 1809 et versions ultérieures.<br/><ul><li>Correctifs mineurs de la plateforme du casque Windows Mixed Reality.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 juin 2019      | Compatible avec Windows 10, version 1809 et versions ultérieures.<br/><ul><li>Améliorations de la plateforme et de la fiabilité du casque Windows Mixed realisation des ordinateurs en sommeil et des transitions d’état d’alimentation.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1er mai 2019      | Compatible avec Windows 10, version 1809 et versions ultérieures.<br/><ul><li>Contient la mise à jour du microprogramme pour les casques 2017 Acer, Asus, Dell, Fujitsu, HP, Lenovo et Medion Windows Mixed Reality. Cette mise à jour du microprogramme améliore la compatibilité et la fiabilité de l’affichage du casque avec certaines cartes graphiques ou pilotes graphiques.</li><li>Améliorations de la plateforme et de la fiabilité du casque Windows Mixed Reality</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, version 1803 (mise à jour d’avril 2018) et version 1809 (mise à jour d’octobre 2018) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 janvier 2019      | Compatible avec Windows 10, version 1803 et versions ultérieures.<br/><ul><li>Correction du suivi des casques et des interruptions</li><li>Correctifs de fiabilité en mode lampe</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1er octobre 2018      | Version publique initiale du pilote pour Windows 10, version 1809.<br/>Compatible avec Windows 10, version 1803 et versions ultérieures.<br/><ul><li>Active les nouvelles fonctionnalités Windows Mixed Reality, telles que le mode torche, dans Windows 10, version 1809</li><li>Suivi des casques et améliorations de la fiabilité</li><li>Amélioration des performances et du suivi du contrôleur de mouvement</li><li>Performances et améliorations USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 avril 2018      | Version publique initiale du pilote pour Windows 10, version 1803<br/> <ul><li>Suivi des casques et améliorations de la fiabilité</li><li>Amélioration des performances et du suivi du contrôleur de mouvement</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, version 1709 (mise à jour des créateurs de automne) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 février 2018    | <ul><li>Prise en charge officielle du casque 3Glasses Blubur S2 Mixed Reality</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 décembre 2017   | <ul><li>Résout un problème HID conduisant à *un* problème avec le code d’erreur 2181038087-7 sur certains PC</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 décembre 2017    | <ul><li>Suivi amélioré du casque</li><li>Améliorations de la réactivité du pavé tactile du contrôleur de mouvement</li><li>Résout un problème dans lequel l’installation du pilote peut parfois échouer</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 novembre, 2017   | <ul><li>Résout un problème qui a conduit au casque, parfois en noir pendant son utilisation</li><li>Résout un problème qui provoquait parfois l’apparition de contrôleurs de mouvement</li><li>Améliorations des performances du capteur de présence pour le casque Dell Visor</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | 10.0.16299.1036  | 7 novembre 2017    | <ul><li>Améliorations du mécanicien levant le contrôleur de mouvement :<ul><li>La rapidité sera désormais signalée correctement lorsque la précision de la position sera approximative, vous pouvez donc vous lancer en arrière-plan !</li><li>Vous trouverez un exemple de code pour la levée dans le package Unity « ThrowingStarter » [ici](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/). Ouvrir la scène de levée pour commencer</li></ul></li><li>Amélioration des rapports sur les batteries du contrôleur de mouvement</li><li>Divers correctifs de stabilité et de fiabilité</li></ul> |
   | 10.0.16299.1012  | 17 octobre 2017    | Version publique initiale du pilote                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Historique de publication du pilote de modèle de contrôle de mouvement de réalité mixte ###

Ce pilote est également automatiquement téléchargé et installé via Windows Update, mais des liens de téléchargement sont disponibles en ligne :

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, version 2004 (mai 2020 mise à jour)

| Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | Le 16 septembre 2020      | Version publique initiale du pilote pour les nouveaux contrôleurs de mouvement HP. Compatible avec Windows 10, version 1903 et versions ultérieures. Ce pilote est compatible uniquement avec les nouveaux contrôleurs de mouvement HP.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, version 1803 (mise à jour d’avril 2018) et version 1809 (mise à jour d’octobre 2018) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1er octobre 2018      | Version publique initiale du pilote pour Windows 10, version 1809. Compatible avec Windows 10, version 1803 et versions ultérieures.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 avril 2018      | Version publique initiale du pilote pour Windows 10, version 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, version 1709 (mise à jour des créateurs de automne) ####

   | Version          | Date de sortie          | Modifications majeures                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 octobre 2017    | Version publique initiale du pilote                          |

### <a name="mixed-reality-portal-release-history"></a>Historique de publication du portail de réalité mixte ###

Dans Windows 10, la version 1809 et les versions ultérieures, le [portail de réalité mixte](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) est mis à jour par le biais de l’application Microsoft Store.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, version 1809 et versions ultérieures ####

   | Version            | Date de sortie          | Modifications majeures                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20071.1133.0  | 5 août 2020        | <ul><li>Prise en charge de [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) pour suspendre la fenêtre d’aperçu.</li></ul>  | 
   | 2000.20041.1212.0  | 11 mai 2020          | <ul><li>Résout un problème de minutage qui provoquait une erreur 15-5 incohérente.</li><li>Amélioration de la prise en charge de l’exécution de Windows Mixed Reality sans connexion Internet.</li><li>Amélioration de la prise en charge des contrôleurs de mouvement couplés via les **contrôleurs d’installation**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 avril 2020        | <ul><li>Prise en charge de l’inscription à des informations, des conseils et des offres sur Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | Février 11, 2020     | <ul><li>Prise en charge améliorée des applications utilisant [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) sur les appareils avec la mise à jour 2019 de mai.</li><li>Résout les problèmes d’accessibilité et de focus clavier</li></ul>  | 
   | 2000.19101.1211.0  | 11 novembre 2019     | <ul><li>Résout un problème qui vous empêche de basculer des éléments visuels de limite de salle.</li><li>Résout un problème qui vous empêche de centrer un casque pendant la configuration de la limite d’espace.</li></ul>  | 
   | 2000.19081.1301.0  | 23 septembre 2019    | <ul><li>Résout un problème où un message d’erreur incorrect s’affiche avec des casques avec des problèmes matériels. Les utilisateurs qui ont reçu un code d’erreur 1-4 sur les versions précédentes peuvent désormais recevoir un code d’erreur plus spécifique pour leur état d’appareil.</li></ul>  |
   | 2000.19071.1302.0  | 13 août 2019     | <ul><li>Prise en charge des applications utilisant [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) sur les appareils avec la mise à jour 2019 de mai.</li></ul>  | 
   | 2000.19061.1011.0  | 16 juillet 2019         | <ul><li>Prise en charge des options de configuration JSON pour personnaliser le comportement de l’application. Pour en savoir plus https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup , consultez.</li></ul>  | 

### <a name="steamvr-release-history"></a>Historique des versions SteamVR ###

Les notes de publication de la vanne pour SteamVR sont disponibles ici : [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Historique de publication de Windows Mixed Reality pour SteamVR ###

Vous trouverez les notes de publication du composant Windows Mixed Reality for SteamVR ici : [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
