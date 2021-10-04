---
title: Windows Mixed Reality Recommandations relatives à la compatibilité des PC
description: Graphique de vue d’ensemble détaillant la configuration minimale requise pour le système PC pour la compatibilité avec Windows Mixed Reality.
author: qianw211
ms.author: v-qianwen
ms.date: 09/22/2021
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, Ultra, compatible, compatibilité, configuration système requise, PC
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: af3228e76bc9ce54ef877b67e8e85a3bde25e140
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436730"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>instructions relatives à la compatibilité minimale du matériel PC Windows Mixed Reality

![Image du héros de compatibilité PC](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Fonctionnalités et expériences

Windows 10 et Windows 11 powers Windows Mixed Reality sur de nombreux casques sur un ensemble diversifié de matériel PC.  La puissance de votre ordinateur déterminera les expériences que vous pouvez effectuer.
Avec les PC plus hauts, vous bénéficiez de fonctionnalités et de fonctionnalités supplémentaires :

* Des visuels plus nets et un taux de rafraîchissement plus élevé.
* Davantage d’applications et d’expériences, y compris les jeux les plus gourmands en graphiques.
* Une fenêtre « miroir » sur votre bureau qui affiche ce que vous voyez dans la réalité mixte.
* Enregistrez et partagez des vidéos et des photos de vos expériences de réalité mixte.

## <a name="minimum-pc-hardware-guidelines"></a>Recommandations sur le matériel PC minimum à avoir

vérifiez si votre ordinateur peut exécuter Windows Mixed Reality en consultant les instructions matérielles ci-dessous et en exécutant l’application [portail de réalité mixte](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) .

Rappelez-vous que vos performances varient en fonction de votre configuration exacte. vous devez également vous assurer que votre ordinateur dispose des [ports appropriés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) pour le Windows Mixed Reality casque immersif que vous utilisez.

>[!NOTE]
>Les directives pour les PC de développement sont plus élevées que celles des PC des clients exécutant des applications de réalité mixte. Si vous êtes un développeur de réalité mixte, [consultez spécifications du PC de développement recommandé](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development).

## <a name="mixed-reality-portal-app"></a>Application portail de réalité mixte

Le [portail de réalité mixte](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) est la meilleure façon de s’assurer que votre ordinateur est prêt à être exécuté Windows Mixed Reality.

Après avoir exécuté l’application, vous obtiendrez l’un des messages suivants :

* **Vous êtes bien.**  Votre ordinateur est prêt à exécuter des jeux et des expériences de réalité mixte.
* **Prend en charge certaines fonctionnalités.** Votre ordinateur peut exécuter des expériences de réalité mixte.
* **Impossible d’exécuter la réalité mixte.** Ce PC ne répond pas à la configuration minimale requise pour exécuter Windows Mixed Reality.

Vous obtiendrez ensuite une analyse de votre ordinateur par rapport au matériel, aux pilotes et au système d’exploitation requis.
![capture d’écran de la vérification de Windows Mixed Reality PC](images/screenshot-mr-pc-check.jpg)

| Icône | Signification |
| --- | --- |
| <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /> | Votre PC transmet l’élément requis. |
| <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /> | Il peut y avoir des problèmes avec votre ordinateur pour les besoins donnés. Si vous rencontrez des problèmes, vous devrez peut-être dépanner ou mettre à niveau votre PC. 
| <img alt="Error" width="30" height="30" src="images/glyph-error.png" /> | Votre ordinateur ne remplit pas les conditions requises pour l’élément spécifié. |

 [Obtenir de l’aide sur les résultats du portail de réalité mixte](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Directives de compatibilité

> [!IMPORTANT]
> nous allons procéder à une mise à jour, en apportant des compléments à et à la révision de ces recommandations de compatibilité avec les PC Windows Mixed Reality. Consultez régulièrement les dernières instructions et exigences.

### <a name="high-resolution-headset-requirements"></a>Exigences relatives aux casques haute résolution

En raison de la résolution plus élevée, les exigences suivantes s’appliquent aux gammes de produits de reréverbération, G2 et Omnicept HP, afin de garantir une expérience de résolution optimale de 90 Hz :

- Intel Core i5, i7, Intel Xeon E3-1240 V5, équivalent ou mieux. AMD Ryzen 5 équivalent ou plus.  
- NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, équivalent ou mieux  
- Mémoire : 8 Go de RAM ou plus  
- Port d’affichage 1x 1,3  
- 1x USB 3,0 type-C avec distribution de l’alimentation (ou adaptateur d’alimentation inclus) 
- Windows 10 2019 mise à jour de mai ou version ultérieure  
 
**Tous les autres casques compatibles WMR** <br>
Pour tous les autres HMDs, reportez-vous aux spécifications suivantes :

| | pc Windows Mixed Reality 90Hz | Windows Mixed Reality 60 hz pc |
| --- | --- | --- |
| Système d’exploitation | Windows 10 Fall Creators Update (RS3) ou version ultérieure : famille, Pro, professionnel, éducation. <br/>    (<b>remarque</b>: non pris en charge sur N versions ou Windows 10 Professionnel en Mode S) |
| Processeur | Intel Core i5 4590 (4e génération), quadruple cœur (ou supérieur) <br> AMD Ryzen 5 1400 3.4 GHz (Desktop), Quad-Core (ou supérieur) | Intel Core i5 7200 (7e génération mobile), double cœur avec la technologie Intel Hyper-Threading activée (ou meilleure) <br> AMD Ryzen 5 1400 3.4 GHz (Desktop), Quad-Core (ou supérieur) |
| Mémoire vive (RAM) | 8 Go DDR3 (ou plus) | 8 canaux DDR3 à deux Go (ou plus) |
| Espace disque disponible | Au moins 10 Go | Au moins 10 Go |
| Carte graphique| <ul> <li>Processeur graphique discret NVIDIA GTX 1060 (ou supérieur) DX12 </li> <li>GPU discrète 470/570 (ou supérieur) AMD RX DX12 </li> </ul> <br> <b>Remarque :</b> Le GPU doit être hébergé dans un emplacement de liaison PCIe 3,0 X4 + |  <ul>  <li>PROCESSEUR graphique intégré Intel HD Graphics 620 (ou version ultérieure) DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(Vérifiez si votre modèle est plus grand)</a></li> <li>GPU discret NVIDIA MX150 (ou supérieur)</li> <li>GPU NVIDIA GeForce GTX 1050 discret</li> <li>GPU discrète NVIDIA 965M</li> <li>AMD Radeon RX 460/560</li> </ul> <b>Remarque :</b> Les processeurs Intel plus anciens tels que HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx et 6xxx ne sont pas pris en charge. |
| Pilote graphique | Windows Modèle de pilote d’affichage (WDDM) 2,2 |  |
| [Port d’affichage graphique](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | HDMI 2,0 ou DisplayPort 1,2 | HDMI 1,4 ou DisplayPort 1,2 |
| Affichage | Affichage VGA (800x600) connecté ou externe connecté (ou plus) | 
| [Connectivité USB](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | USB 3,0 | |
| connectivité Bluetooth (pour les [contrôleurs de mouvement](controllers-in-wmr.md) | Bluetooth 4,0 | |
| Fréquence d’images du casque attendue | 90 Hz | 60 Hz |
| Avancé | Ports USB 3.0 | Ports USB 3.0 |

**Informations complémentaires :**

* Les plus grands ordinateurs portables avec des écrans d’au moins 15 pouces font le meilleur.
* les configurations graphiques hybrides sont compatibles uniquement avec Windows Mixed Reality 90Hz. la carte graphique discrète dans une configuration hybride doit satisfaire à toutes les conditions requises indiquées dans le Windows Mixed Reality instructions pour les cartes graphiques discrètes.
* si vous disposez d’une carte graphique discrète qui doit s’exécuter Windows Mixed Reality 90Hz, mais qu’elle utilise par défaut une fréquence d’actualisation de 60 hz (60 images par seconde), utilisez un DisplayPort de l’adaptateur de DisplayPort à HDMI 2,0 pour brancher votre casque et activer une fréquence d’actualisation 90Hz.
* Différents casques peuvent nécessiter des ports matériels différents. par conséquent, assurez-vous que votre ordinateur dispose des ports appropriés ou des [adaptateurs nécessaires](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) pour se connecter à votre casque.

>[!NOTE]
>les matériels graphiques discrets et intégrés qui ne satisfont pas aux spécifications minimales confirmées n’ont pas été testés, confirmés ou optimisés pour Windows Mixed Reality et peuvent ne pas fonctionner correctement ou du tout.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality et Surface

pour une expérience de Windows Mixed Reality optimale sur un appareil Surface, nous vous recommandons la dernière version de SurfaceBook (15) configurée avec au moins la NVIDIA GeForce GTX 1060 go et 16 go de RAM.  cette configuration prend en charge toutes les fonctionnalités de Windows Mixed Reality et a été testée pour la Windows Mixed Reality.  les Surface Book les plus récents (13,5»), Surface Studio, Surface Laptop et Surface Pro (2017) prennent en charge certaines fonctionnalités de Windows Mixed Reality lorsqu’elles sont configurées avec un processeur Intel Core i5 (ou mieux) et au moins 8 go de RAM.

**Conditions requises :**

* Les produits de surface requièrent que les mises à jour de pilotes soient compatibles avec Windows Mixed Reality. vous pouvez installer ces pilotes sur votre Surface en accédant à **Paramètres > mise à jour et à la sécurité > rechercher les mises à jour**.
* les produits de Surface requièrent un [adaptateur](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) du port vidéo (Mini-DisplayPort ou USB-C, en fonction du PC Surface) à l’HDMI 2,0 pour Windows Mixed Reality casques. La version la plus récente de la surface Mini-DisplayPort à l’adaptateur AV HDMI est compatible avec l’HDMI 2,0 (l’ancienne version n’est pas). De même, l' <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">adaptateur USB-C à interface HDMI</a> est également compatible avec la norme HDMI 2,0.

## <a name="see-also"></a>Voir aussi

* [Demander à la communauté](https://answers.microsoft.com)
* [Contactez-nous pour obtenir de l’aide](https://support.microsoft.com/contactus/)
* [adaptateurs recommandés pour les pc prenant en charge Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
