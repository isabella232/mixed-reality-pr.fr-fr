---
title: Divertissement basé sur l’emplacement avec Windows Mixed Reality
description: en savoir plus sur les Windows Mixed Reality pour les divertissements basés sur l’emplacement (matériel, pc de sac à dos, suivi, configuration et support).
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: en réalité mixte, vr, lbe, emplacement, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, matériel, HoloLens, multi-player, services cloud, azure
ms.openlocfilehash: e9cff1184ca60f4b64be5346a187666e7b401aab06fee87c179917e300aa07f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196783"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Divertissement basé sur l’emplacement avec Windows Mixed Reality

Au cours des dernières années, nous avons vu une croissance incroyable de la croissance et de l’innovation dans la catégorie des loisirs basés sur l’emplacement. Les systèmes traditionnels tels que les parcs de thèmes et les théâtres ont commencé à offrir des expériences immersifs à plusieurs joueurs comme des expériences complémentaires pour les emplacements et les installations existantes. Les nouveaux opérateurs et emplacements permettent de créer des expériences multilecteurs et multi-joueurs uniques à un prix intéressant aux masses. Toutes ces expériences poussent l’enveloppe pour ce qui est possible avec la réalité mixte.

ce document est un guide de prise en main de Windows Mixed Reality dans la catégorie divertissements basée sur l’emplacement. Les instructions ci-dessous peuvent également s’appliquer à des expériences basées sur l’emplacement au-delà du divertissement, telles que la formation, la conception des produits et d’autres cas d’usage.

## <a name="engineering-faq"></a>FAQ sur l’ingénierie

### <a name="hardware"></a>Matériel

**Q : quel matériel est disponible auprès de Microsoft et de ses partenaires que je peux utiliser dans mon programme d’installation ?**

R : Microsoft et ses partenaires OEM proposent un portefeuille attrayant d’appareils en fonction de vos besoins.  

Si les expériences que vous fournissez à vos clients requièrent un casque de réalité virtuelle, les casques sur le marché de HP, Samsung et Acer sont très adaptés. Chaque casque possède ses propres attributs différenciés. Pour plus d’informations, reportez-vous à la suite.

Réverbération HP : [Détails](https://hp.com/go/Reverbpro)

Samsung Odyssey + : [Détails](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer : [Détails](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

si votre emplacement est spécialisé dans des expériences de réalité mixtes ou augmentées avec des casques, consultez le Microsoft HoloLens 2.  

HoloLens 2 : préversion [de l’intérêt](https://www.microsoft.com//hololens/buy)

si vous expérimentez avec des expériences qui utilisent la vision avancée de l’ordinateur, la reconnaissance vocale et le suivi du corps, Azure Kinect DK est un bon choix.  

Kinect Azure : [détails](https://azure.microsoft.com//services/kinect-dk/)

**Q : qu’est-ce que le portefeuille de PC de poche que je peux utiliser pour exécuter mes expériences de VR de PC.**

Pour les expériences de VR du PC, nos fabricants d’ordinateurs OEM offrent une sélection incroyable de PC de sac à dos conçus exactement pour ce besoin.

HP vient de lancer son sac à dos HP VR G2, le PC portable le plus puissant au monde : optimisé pour les expériences gratuites-itinérantes, avec une puissance de 30% avec un GPU RTX 2080 à l’intérieur. [Détails](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Installation

**Q : Comment puis-je configurer plus facilement le programme d’installation et personnaliser le portail de réalité mixte pour LBE ?**

>[!NOTE]
>Cette fonctionnalité nécessite la version 2000.19061.1011.0 ou ultérieure.  

Il se peut que vous ayez besoin de plus de personnalisation du portail de réalité mixte que ce qui est normalement disponible via l’application pour déployer des applications sur des bornes ou des expériences personnalisées. La dernière mise à jour de juillet du portail de réalité mixte prend en charge plusieurs paramètres avancés, que vous pouvez définir via un fichier de configuration :  

autoriser les vérifications système en échec : normalement, le processus d’installation vérifie la compatibilité du PC avec Windows Mixed Reality avant d’effectuer l’installation. le contournement des vérifications de compatibilité peut provoquer des problèmes lors de la tentative d’exécution de Windows Mixed Reality s’il existe des problèmes de compatibilité.  

Ignorer l’application compagnon de l’appareil : le DCA fournit des étapes de configuration spécifiques au casque fournies par le fabricant et permet de mettre à jour le microprogramme du casque.  

Ignorer la configuration de la salle : au lieu d’être invité à créer une limite de salle, vous pouvez passer directement au casque en mode assis/debout.  

Ignorer l’installation d’applications à partir du Store : le programme d’installation normale installe plusieurs applications du Windows Store, notamment la visionneuse 3D et le module complémentaire de la visionneuse Edge 360. Cela va ignorer l’installation de ces applications, mais il se peut que vous manquiez des fonctionnalités d’appareil.  

Afficher l’aperçu en mode plein écran : le portail de réalité mixte affiche par défaut la préversion du casque en mode plein écran sur le PC de bureau pendant que le casque est en cours d’utilisation.  

Masquer le nouveau volet pour vous : empêche le nouveau panneau pour vous d’être développé au lancement du portail de réalité mixte.  

#### <a name="how-to-configure"></a>Pour effectuer la configuration :  

Pour définir l’une de ces configurations, vous devez créer un fichier appelé _UserConfig.js_ sous ce répertoire : _$env : localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \localstate \\_

Pour la plupart des utilisateurs, cela ressemble à ce qui suit : _C:\Users \<username> \Appdata\local\packages\ Microsoft.mixedreality.portal_8wekyb3d8bbwe \localstate \\_

Le fichier JSON doit avoir le contenu ci-dessous avec « true » défini pour l’un des paramètres ci-dessus que vous souhaitez activer :  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**Q : existe-t-il des instructions sur la configuration de l’PlaySpace ?**

R : la configuration d’un Playspace doit être effectuée comme vous le feriez avec une expérience d’installation du consommateur. Le processus de configuration de la salle vous permet également de définir les limites de votre salle. Vous trouverez plus d’informations sur la configuration des limites de la salle [ici](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

Comme indiqué dans le document ci-dessus, la coordonnée unique raisonnable PlaySpace est autour de 5mx5m. si vous souhaitez disposer d’une plus grande surface, vous pouvez utiliser la fonctionnalité d’ancrages spatiaux dans la pile d’API holographique Windows. L’utilisation de cette API nécessite une ingénierie personnalisée dans les expériences que vous êtes en train de produire.  

Pour plus d’informations sur l’optimisation de votre contenu en fonction de la taille de l’espace, consultez [cette page](/windows/mixed-reality/coordinate-systems).
 

**Q : mon espace est trop grand et je rencontre des erreurs lorsque j’essaie de configurer une expérience permanente avec les limites. Que dois-je faire pour configurer mon expérience d’itinérance gratuite ?**

R : pour configurer un espace plus grand que ~ 18x18ft, vous ne pouvez pas utiliser l’expérience de limite fournie par le système.  Les systèmes de limite s’appuient sur une « ancre » de coordonnée fixe unique, qui peut devenir instable lorsqu’un utilisateur est trop éloigné de l’ancre d’étape centrale. 

Vous pouvez configurer le mode « assiste », qui n’affiche pas la limite ou ne configure pas les limites d’un étage ou un PlaySpace.  Vous devez configurer plusieurs ancres spatiales dans l’application pour référencer des zones de limites physiques. 

Le développeur de l’application est responsable de l’affichage des protections nécessaires afin que les utilisateurs n’entrent pas en conflit avec l’environnement physique.  Il peut s’agir de murs numériques au sein de l’expérience ou d’un visuel de limite de jeu personnalisé. 

Vous trouverez des conseils sur la configuration de la limite de la salle avec WMR [ici](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

**Q : où est l’origine du PlaySpace ?**

R : l’origine du PlaySpace est déterminée par l’expérience d’installation de la salle, plus précisément la position du HMD lorsque le bouton central est enfoncé pendant l’installation. 

### <a name="multi-player-setup"></a>CONFIGURATION MULTI-JOUEURS

**Q : je déploie une expérience multi-joueurs dans à mon lieu. Est-ce pris en charge sur Windows Mixed Reality ?**

r : si vous vous abonnez au Windows 20H1 ou version ultérieure par le biais de notre programme insider, vous pouvez accéder à une nouvelle interface pour le partage de cartes. cette nouvelle fonctionnalité est disponible via l’interface du [gestionnaire de cartes](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) du Windows portail des appareils. Pour utiliser cet outil, suivez les étapes ci-dessous :
* Assurez-vous que vous avez opté pour 20H1 ou version ultérieure-après le 2019 septembre, cela signifie que nous avons utilisé notre programme Insider
* activer le portail d’appareils Windows (WDP) à l’aide de ces [instructions](/windows/uwp/debug-test-perf/device-portal-desktop)
* branchez un Windows Mixed Reality HMD sur lequel vous souhaitez télécharger un mappage existant à partir de ou importer un nouveau mappage
* Accédez au WDP dans le navigateur de votre choix à l’aide de l’URL fournie dans l’écran des paramètres.
    * Une fois que vous accédez à la section « réalité mixte » et sélectionnez « Gestionnaire de cartes ».
    * Vous pouvez maintenant utiliser le bouton « Télécharger » pour exporter un mappage existant à partir de l’ordinateur.
    * vous pouvez utiliser le bouton « Télécharger un fichier de mappage » pour importer un mappage à partir d’une exportation précédente (peut-être sur une autre machine).
    * Vous pouvez utiliser « importer » pour permettre au système d’utiliser ce mappage pour ce HMD sur cet ordinateur.

> [!NOTE] 
> Auparavant, il était possible d’utiliser l’outil package de données spatiales. Toutefois, cet outil a été publié à l’origine comme n’étant pas pris en charge et il est désormais officiellement déconseillé et ne fonctionne plus sur 20H1. Au lieu de cela, utilisez l’outil [Gestionnaire](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) de la boîte de réception comme décrit ci-dessus. 

### <a name="tracking"></a>SUIVRE

Q : comment fonctionne la technologie de suivi des casques Windows Mixed Reality ?  

La réalité mixte partage la même technologie de suivi que le HoloLens. Pour en savoir plus sur le système de suivi interne, consultez la documentation [ici](/windows/mixed-reality/enthusiast-guide/tracking-system).

Pour obtenir une description de la façon dont le système de mappage spatial de niveau supérieur fonctionne, vous pouvez lire notre description [ici](../design/spatial-mapping.md).

**Q : existe-t-il des pratiques recommandées pour obtenir un volume de suivi fiable ?**

Pour mieux configurer l’environnement pour le suivi des réussites, vous pouvez lire les meilleures pratiques dans ce [billet](/hololens/hololens-environment-considerations).

**Q : existe-t-il des nuances spécifiques avec le suivi des espaces ou des optimisations de l’échelle de l’entrepôt à prendre en compte ?**

R : les pratiques suivantes peuvent vous aider à obtenir un volume de suivi plus fiable :  

Le fait de fournir des fonctionnalités différentes dans la salle qui se chevauchent à plusieurs endroits aide le système de suivi à obtenir un verrou solide. Considérez les hachures et les hachures aléatoires au lieu d’utiliser des lignes de style de contour solides. 

Réduisez autant que possible la plage dynamique d’éclairage dans votre région. Les caméras de suivi de notre HMDs de réalité mixte ne sont pas HDR et ont des opérations AGC (gain automatique) et AEC (exposition automatique) pour gérer différents éclairages. En fonction de la répartition de la surface, des motifs et du contraste, AGC ou AEC peut vous conclure que vous êtes dans une pièce blanche ou noire, qui peut nettoyer les fonctionnalités qui peuvent être dans la « couleur » opposée. Si vous essayez de prendre une image intérieure devant une fenêtre extérieure avec une lumière de l’heure d’été et que vous ajustez l’exposition pour voir les détails en dehors de, tout ce qui se trouve à l’intérieur est sous-exposé et noir. Ou, s’il est défini à l’intérieur de, tout ce qui est à l’extérieur est maintenant surexposé et tout blanc.  

Des lumières dans une pièce (même des surcharges) qui sont en vue si le suivi des caméras peut parfois être coupable, ce qui perturbe l’AEC/AGC des caméras de suivi. L’éclairage plat/diffus vous aide.  

### <a name="mixed-reality-cloud-services-and-azure"></a>SERVICES CLOUD DE RÉALITÉ MIXTE ET AZURE 

**Q : comment Microsoft Azure aider à mon entreprise ?**

R : la gestion sur site et à distance basée sur Azure peut aider votre entreprise à être pilotée par les données, à réduire les coûts d’exploitation et à mettre à l’échelle le déploiement sur les sites existants et nouveaux. les services de cloud computing azure, tels que stockage Azure, les Azure Functions, les App Service, la mise en réseau Azure et IOT Hub peuvent vous aider dans les cas d’utilisation suivants :  

Gestion des & de déploiement des appareils à distance 

Real-Time l’analyse sur site 

Jeu intelligent LBE adaptatif 

Diffusion et déploiement de contenu LBE 

LBE de préférence du lecteur carte thermique 

Système de réservation et de réservation LBE 

**Q : je développe un MMOG spatial à déployer sur un encombrement énorme. Tous les services qui m’aident à gérer mon contenu et la persistance des objets ?**

r : les ancres spatiales Azure sont un nouveau service de réalité mixte qui permet l’utilisation de la réalité mixte multi-utilisateur, avec prise en charge spatiale, sur les appareils HoloLens, iOS et Android. Vous pouvez en savoir plus sur les ancres spatiales Azure [ici](https://azure.microsoft.com//services/spatial-anchors/).

**Question. Notre lieu est spécialisé dans les expériences multi-joueurs et je souhaite concentrer notre temps de développement sur le contenu et le développement frontal. Existe-t-il des offres qui peuvent m’aider à démarrer ou à décharger le développement principal ?**

R : Azure PlayFab est une plateforme backend complète pour les jeux en direct. Vous pouvez en savoir plus à ce sujet [ici](https://playfab.com/).

### <a name="misc"></a>Divers

**Q : J’utilise SteamVR pour déployer mes expériences. ne fonctionne-t-il Windows Mixed Reality avec SteamVR ?**

r : Windows Mixed Reality pour SteamVR permet aux utilisateurs d’exécuter des expériences SteamVR sur Windows Mixed Reality des casques immersifs. En savoir plus sur SteamVR avec WMR [ici](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).

### <a name="support-and-community"></a>Support et communauté  

Nous disposons de quelques ressources utiles pour vous aider à participer à des experts de notre équipe, à obtenir un support de dépannage et à contribuer à la communauté de développement de la réalité mixte.  

Si vous rencontrez des problèmes avec les fonctionnalités publiées publiquement, signalez un bogue à l’aide de feedback Hub. pour obtenir de l’aide, reportez-vous à cette [page](/windows/mixed-reality/enthusiast-guide/filing-feedback).

Pour obtenir de l’aide sur la résolution des problèmes liés à WMR, [prenez une demande de support](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) auprès de notre équipe de support technique.

Participez à notre canal HoloDevelopers pour collaborer avec les développeurs de réalité mixte et les experts en la matière : [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter : Suivez notre équipe de relations développeurs de réalité mixte pour les actualités, les événements et les mises à jour @MxdRealityDev 

Si vous êtes en déplacement ou autour de San Francisco, il y a toujours un problème qui se passe sur le réacteur Microsoft. Vous pouvez voir notre calendrier d’événements [ici](https://developer.microsoft.com//reactor/Location/San%20Francisco).
