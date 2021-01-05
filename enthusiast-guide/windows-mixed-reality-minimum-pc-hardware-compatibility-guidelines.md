---
title: Instructions de compatibilité matérielle PC minimale pour Windows Mixed Reality
description: Graphique détaillant la configuration minimale requise pour le système PC pour la compatibilité avec Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, ultra, compatible, compatibilité, configuration système requise, PC
appliesto:
- Windows 10
ms.openlocfilehash: bd287e2089056be56330c2c2e8e9af2c079009ac
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725660"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Instructions de compatibilité matérielle PC minimale pour Windows Mixed Reality

## <a name="features-and-experiences"></a>Fonctionnalités et expériences

Windows 10 alimente Windows Mixed Reality et Windows Mixed Reality ultra. La version que vous rencontrez dépend du matériel de votre PC.

Avec Windows Mixed Reality ultra, vous bénéficiez de fonctionnalités et de fonctionnalités supplémentaires :

* Des visuels plus nets et un taux de rafraîchissement plus élevé (90 images par seconde).
* Davantage d’applications et d’expériences, y compris les jeux les plus gourmands en graphiques.
* Une fenêtre « miroir » sur votre bureau qui affiche ce que vous voyez dans la réalité mixte.
* Enregistrez et partagez des vidéos et des photos de vos expériences de réalité mixte.

## <a name="minimum-pc-hardware-guidelines"></a>Recommandations sur le matériel PC minimum à avoir

Pour une expérience optimale avec Windows Mixed Reality, commencez avec un PC compatible [Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) ou un PC compatible Windows Mixed Reality qui peut offrir des expériences ultra-Windows Mixed Reality. Windows Mixed Reality ultra offre des visuels plus nets à des taux de rafraîchissement plus élevés, des expériences d’applications supplémentaires, notamment les jeux les plus riches en graphiques, la mise en miroir de votre expérience Windows Mixed Reality sur votre ordinateur de bureau et la possibilité d’enregistrer et de partager (photos et vidéos) vos expériences avec d’autres utilisateurs. 

Vérifiez si votre PC peut exécuter Windows Mixed Reality en consultant les instructions matérielles ci-dessous et en exécutant l' [application portail de réalité mixte](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M).

Rappelez-vous que vos performances varient en fonction de votre configuration exacte. Vous devez également vous assurer que votre ordinateur dispose des [ports appropriés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) pour le casque Windows Mixed realisation en immersion que vous utilisez.

>[!NOTE]
>Les directives pour les PC de développement sont plus élevées que celles des PC des clients exécutant des applications de réalité mixte. Si vous êtes un développeur de réalité mixte, [consultez spécifications du PC de développement recommandé](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development).


## <a name="mixed-reality-portal-app"></a>Application portail de réalité mixte

Le portail de réalité mixte est la meilleure façon de s’assurer que votre ordinateur est prêt à exécuter Windows Mixed Reality. 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

Après avoir exécuté l’application, vous obtiendrez l’un des messages suivants :
* **Vous êtes bien.** Votre PC a ce qu’il faut pour exécuter Windows Mixed Reality.
* **Prend en charge certaines fonctionnalités.** Ce PC peut exécuter Windows Mixed Reality, mais certaines fonctionnalités peuvent être limitées.
* **Impossible d’exécuter la réalité mixte.** Ce PC ne répond pas à la configuration minimale requise pour exécuter Windows Mixed Reality.

Vous obtiendrez ensuite une analyse de votre ordinateur par rapport au matériel, aux pilotes et au système d’exploitation requis.
![Capture d’écran de la vérification du PC Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Icône</th><th>Signification</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Votre PC transmet l’élément requis.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Il peut y avoir des problèmes avec votre ordinateur pour les besoins donnés. Si vous rencontrez des problèmes, vous devrez peut-être dépanner ou mettre à niveau votre PC.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Votre ordinateur ne remplit pas les conditions requises pour l’élément spécifié.</td>
</tr>
</table>

 [Obtenir de l’aide sur les résultats du portail de réalité mixte](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>Directives de compatibilité
> [!IMPORTANT]
> Nous allons effectuer des mises à jour, en apportant des compléments à ces recommandations en matière de compatibilité des PC Windows Mixed Reality. Consultez régulièrement les dernières instructions et exigences.

**Spécifications compatibles avec les réverbérations HP**<br>
En raison de la résolution supérieure, les exigences suivantes s’appliquent à la réverbération HP G1 & les gammes de produits G2 pour garantir une expérience de résolution optimale de 90 Hz : 

<ul>
<li> Intel Core i5, i7, Intel xénon E3-1240 V5, équivalent ou mieux. AMD Ryzen 5 équivalent ou plus. </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, équivalent ou mieux </li> 
<li> Mémoire : 8 Go de RAM ou plus </li> 
<li> Port d’affichage 1x 1,3 </li> 
<li> 1x USB 3,0 type-C avec distribution de l’alimentation (ou adaptateur d’alimentation inclus)</li>
<li> Windows 10 mai 2019 Update ou version ultérieure </li>
</ul>

**Tous les autres casques compatibles WMR** <br>
Pour tous les autres HMDs, reportez-vous aux spécifications suivantes : 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality ultra PC</th>
    <th style="vertical-align: middle; text-align: center; width:30%">PC Windows Mixed Reality</th>
</tr><tr>
    <td style="vertical-align: middle">Système d’exploitation</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 automne Creators Update (RS3) ou version ultérieure-famille, professionnel, professionnel, éducation.<br/>    (<b>Remarque</b>: non pris en charge sur N versions ou Windows 10 professionnel en mode S)</td>
</tr><tr>
    <td style="vertical-align: middle">Processeur</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4e génération), quadruple cœur (ou supérieur) <br>AMD Ryzen 5 1400 3.4 GHz (Desktop), Quad-Core (ou supérieur)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200 (7e génération mobile), double cœur avec la technologie Intel Hyper-Threading activée (ou meilleure) <br>AMD Ryzen 5 1400 3.4 GHz (Desktop), Quad-Core (ou supérieur)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 Go DDR3 (ou plus)</td>
    <td style="vertical-align: middle; text-align: center;">8 canaux DDR3 à deux Go (ou plus)</td>
</tr><tr>
    <td style="vertical-align: middle">Espace disque disponible</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Au moins 10 Go</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Au moins 10 Go</td>
</tr><tr>
    <td style="vertical-align: middle">Carte graphique</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>Processeur graphique discret NVIDIA GTX 1060 (ou supérieur) DX12</li>
            <li>GPU discrète 470/570 (ou supérieur) AMD RX DX12 </li>
            </ul>     
            <b>Remarque :</b> Le GPU doit être hébergé dans un emplacement de liaison PCIe 3,0 X4 + </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>PROCESSEUR graphique intégré Intel HD Graphics 620 (ou version ultérieure) DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(Vérifiez si votre modèle est plus grand)</a></li>
        <li>GPU discret NVIDIA MX150 (ou supérieur)</li>
        <li>GPU NVIDIA GeForce GTX 1050 discret</li>
        <li>GPU discrète NVIDIA 965M</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Remarque :</b> Les processeurs Intel plus anciens tels que HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx et 6xxx ne sont pas pris en charge.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Pilote graphique</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">WDDM (Windows Display Driver Model) 2,2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Port d’affichage graphique</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2,0 ou DisplayPort 1,2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1,4 ou DisplayPort 1,2</td>
</tr><tr>
    <td style="vertical-align: middle">Afficher</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Affichage VGA (800x600) connecté ou externe connecté (ou plus)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Connectivité USB</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3,0 type-A </td>
</tr><tr>
    <td style="vertical-align: middle">Connectivité Bluetooth (pour les <a href="controllers-in-wmr.md">contrôleurs de mouvement</a>)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4,0</td>
</tr><tr>
    <td style="vertical-align: middle">Fréquence d’images du casque attendue</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Power</td>
    <td style="vertical-align: middle; text-align: center;">Ports USB 3,0 (type A)</td>
    <td style="vertical-align: middle; text-align: center;">Ports USB 3,0 (type A)</td>
</tr>
</table>



**Informations complémentaires :**
* Les plus grands ordinateurs portables avec des écrans d’au moins 15 pouces font le meilleur.
* Pour une expérience optimale, nous vous recommandons de disposer d’un processeur Intel® Core™ ou 7e GEN Intel® Core™ i5.
* Les configurations graphiques hybrides sont compatibles uniquement avec Windows Mixed Reality ultra. La carte graphique discrète dans une configuration hybride doit répondre à toutes les conditions requises indiquées dans les recommandations de Windows Mixed Reality pour les cartes graphiques discrètes.
* Si vous disposez d’une carte graphique discrète qui doit exécuter Windows Mixed Reality ultra, mais dont la fréquence d’actualisation par défaut est de 60 Hz (60 images par seconde), utilisez un adaptateur DisplayPort de la taille maximale de l’adaptateur HDMI 2,0 pour brancher votre casque et activer une fréquence d’actualisation de 90 Hz.
* Différents casques peuvent nécessiter des ports matériels différents. par conséquent, assurez-vous que votre ordinateur dispose des ports appropriés ou des [adaptateurs nécessaires](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) pour se connecter à votre casque.

>[!NOTE]
>Les matériels graphiques discrets et intégrés qui ne satisfont pas aux spécifications minimales confirmées n’ont pas été testés, confirmés ou optimisés pour Windows Mixed Reality et peuvent ne pas fonctionner correctement ou du tout.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality and surface

Pour une expérience Windows Mixed Reality optimale sur un appareil surface, nous recommandons le SurfaceBook 2 (15) configuré avec la NVIDIA GeForce GTX 1060 Go et 16 Go de RAM.  Cette configuration prend en charge toutes les fonctionnalités de Windows Mixed Reality @ 90 Hz et a été testée et soumise à des badges pour Windows Mixed Reality ultra.  Le livre surface 2 (13), surface Studio, portable surface et surface Pro (2017) prend en charge certaines fonctionnalités de Windows Mixed Reality lorsqu’il est configuré avec un processeur Intel Core i5 (ou mieux) et au moins 8 Go de RAM.

**Conditions requises :**
* Les produits de surface requièrent des mises à jour de pilotes pour être compatibles avec Windows Mixed Reality. Ces pilotes peuvent être installés sur votre surface en accédant à **paramètres > mise à jour et sécurité > Rechercher les mises à jour**.
* Les produits surface requièrent un [adaptateur](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) du port vidéo (mini DisplayPort ou USB-C, en fonction du PC surface) à l’HDMI 2,0 pour les casques Windows mixtes de réalité. La version la plus récente de la surface Mini-DisplayPort à l’adaptateur AV HDMI est compatible avec l’HDMI 2,0 (l’ancienne version n’est pas). De même, l' <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">adaptateur USB-C à interface HDMI</a> est également compatible avec la norme HDMI 2,0.

>[!WARNING]
>Les adaptateurs mini DisplayPort ou USB-C à HDMI ne sont pas tous dotés de la technologie HDMI 2,0. Envisagez de vérifier la compatibilité « HDMI 2,0 » explicite ou la compatibilité « 4K » sur les adaptateurs.

Pour plus d’informations sur la compatibilité des surfaces avec Windows Mixed Reality, reportez-vous au tableau ci-dessous :

<table>
    <tr>
        <th> Appareil surface </th><th> Prise en charge de la fonctionnalité Windows Mixed Reality ? </th><th> Configuration recommandée </th><th> Notes</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (original)/surface Pro 2 </td><td style="vertical-align: middle"> Aucun </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> Aucun </td><td> </td><td></td>
    </tr>
(avec Windows 10 professionnel installé) <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> Aucun </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> Aucun </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> Aucun </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Livre surface avec la base de performances </td><td style="vertical-align: middle"> Aucun </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> Aucun </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Livre surface 2 (15 &quot; ) </td><td style="vertical-align: middle"> Complète </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/16 Go de RAM </td>
        <td>
            <ul>
                <li><b>Recommandé</b>: pour une expérience Windows Mixed Reality optimale sur un appareil surface, nous recommandons le SurfaceBook 2 15» configuré avec NVIDIA GeForce GTX 1060 Go et 16 Go de RAM.  Cette configuration est testée et présente sous la forme de « Windows Mixed Reality ultra » pour prendre en charge toutes les fonctionnalités de la réalité mixte de Windows et vous permettra de profiter de la plus vaste gamme d’applications et de jeux compatibles.</li>
                <li>La carte graphique discrète NVIDIA GeForce GTX 1060 offrira une expérience Windows Mixed Reality ultra @ 90-Hz</li><br/>                <li>Pour de meilleures performances, utilisez les pilotes graphiques NVIDIA commercialisés pour surface Book 2. Des pilotes plus récents peuvent être disponibles sur le site Web NVIDIA&#39;s, mais ils ne sont pas testés.</li><br/>                <li>Nécessite <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">surface USB-C vers l’adaptateur HDMI (d'</a> autres adaptateurs peuvent fonctionner, mais ils ne sont pas testés)</li>
                <li><b>Remarque sur la station d’accueil</b>: l’utilisation du Dock de surface avec le livre surface 2 n’est pas officiellement prise en charge avec Windows Mixed Reality, en raison des limitations de l’alimentation de l’ancre de surface.</li><br/>                <li><b>Remarque sur Windows 10 version 1803</b>: si vous&#39;réexécuter Windows 10 version 1803, assurez-vous que vous&#39;réactiver le système d’exploitation 17134,137 ou une version plus récente (installée par KB4284848) pour vous assurer que vous disposez des derniers correctifs de performances. Pour plus d’informations, consultez les notes de publication de <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book 2 (13,5 &quot; ) </td><td style="vertical-align: middle"> Partiel </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/16 Go de RAM </td>
        <td>
            <ul>
                <li><b>Remarque</b>: le livre surface 2 (13) n’a pas de badge pour Windows Mixed Reality, mais prend en charge certaines fonctionnalités Windows Mixed realisation, ce qui vous permet d’utiliser un nombre limité d’applications et de jeux compatibles.  Les performances dépendent de votre configuration.</li>
                <li>Les configurations avec un processeur graphique intégré Intel Core i5/Intel HD Graphics 620 fournissent une expérience Windows Mixed Reality @ 60-Hz.</li>
                <li>Les configurations avec un GPU discret 1050 Intel Core i7/NVIDIA GeForce GTX offrent une expérience Windows Mixed Reality @ 90-Hz.</li>                       <li>Pour de meilleures performances, utilisez les pilotes graphiques NVIDIA commercialisés pour surface Book 2. Des pilotes plus récents peuvent être disponibles sur le site Web NVIDIA&#39;s, mais ils ne sont pas testés.</li>
                <li>Nécessite <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">surface USB-C vers l’adaptateur HDMI (d'</a> autres adaptateurs peuvent fonctionner, mais ils ne sont pas testés)</li>
                <li><b>Remarque sur la station d’accueil</b>: l’utilisation du Dock de surface avec le livre surface 2 n’est pas officiellement prise en charge avec Windows Mixed Reality, en raison des limitations de l’alimentation de l’ancre de surface.</li>
                <li><b>Remarque sur Windows 10 version 1803</b>: si vous&#39;réexécuter Windows 10 version 1803, assurez-vous que vous&#39;réactiver le système d’exploitation 17134,137 ou une version plus récente (installée par KB4284848) pour vous assurer que vous disposez des derniers correctifs de performances. Pour plus d’informations, consultez les notes de publication de <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> Partiel </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/16 Go de RAM </td>
        <td>
            <ul>
                <li><b>Remarque</b>: la surface Studio n’a pas de badge pour Windows Mixed Reality, mais prend en charge certaines fonctionnalités de Windows Mixed realisation, ce qui vous permet d’utiliser un nombre limité d’applications et de jeux compatibles.  Les performances dépendent de votre configuration.</li>
                <li>Les configurations avec NVIDIA GeForce GTX 965 m offriront une expérience Windows Mixed Reality @ 60-Hz.</li>
                <li>Les configurations avec NVIDIA GeForce GTX 980 m offriront une expérience Windows Mixed Reality @ 90-Hz.</li>
                <li>Surface Mini DisplayPort sur l’adaptateur HDMI 2,0 (d’autres adaptateurs peuvent fonctionner, mais ils ne sont pas testés)</li>
                <li>Le casque Windows Mixed Reality doit être connecté au port USB avec le symbole « + »</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017) </td><td style="vertical-align: middle"> Partiel </td><td style="vertical-align: middle"> Intel Core i7/Intel® IRIS™ plus Graphics 640/16 Go de RAM </td>
        <td>
            <ul>
                <li><b>Remarque</b>: le Pro Surface (2017) n’est pas badge pour Windows Mixed Reality, mais prend en charge certaines fonctionnalités de Windows Mixed realisation, ce qui vous permet d’utiliser un nombre limité d’applications et de jeux compatibles.  Les performances dépendent de votre configuration.</li>
                <li>Les configurations avec un GPU intégré Intel Core m3/Intel HD Graphics 615 ne sont <b>pas prises en charge</b></li>
                <li>Les configurations avec un processeur graphique intégré Intel Core i5/Intel HD Graphics 620 fournissent une expérience Windows Mixed Reality @ 60-Hz.</li>
                <li>Les configurations avec un GPU Intel Core i7/Intel® IRIS™ plus Graphics 640 intégré offrent une expérience Windows Mixed Reality @ 60-Hz.</li><br/><li>Nécessite surface Mini DisplayPort sur l’adaptateur HDMI 2,0 (les autres adaptateurs peuvent fonctionner, mais ils ne sont pas testés)</li>
                <li>Nécessite un <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">curseur de performances</a> défini sur « meilleures performances » lors de l’utilisation</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> Partiel </td><td style="vertical-align: middle"> Intel Core i7/Intel® IRIS™ plus Graphics 640/16 Go de RAM </td>
        <td>
            <ul>
                <li><b>Remarque</b>: l’ordinateur portable n’a pas de badge pour Windows Mixed Reality, mais il prend en charge certaines fonctionnalités Windows Mixed realisation, ce qui vous permet d’utiliser un nombre limité d’applications et de jeux compatibles.  Les performances dépendent de votre configuration.</li>
                <li>Les configurations avec un GPU intégré Intel Core m3/Intel HD Graphics 615 ne sont <b>pas prises en charge</b></li>
                <li>Les configurations avec un processeur graphique intégré Intel Core i5/Intel HD Graphics 620 fournissent une expérience Windows Mixed Reality @ 60-Hz.</li>
                <li>Les configurations avec un GPU Intel Core i7/Intel® IRIS™ plus Graphics 640 intégré offrent une expérience Windows Mixed Reality @ 60-Hz.</li><br/><li>Nécessite surface Mini DisplayPort sur l’adaptateur HDMI 2,0 (les autres adaptateurs peuvent fonctionner, mais ils ne sont pas testés)</li>
                <li>Nécessite un <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">curseur de performances</a> défini sur « meilleures performances » lors de l’utilisation</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>Voir aussi
* [Demander à la communauté](https://answers.microsoft.com)
* [Contactez-nous pour obtenir de l’aide](https://support.microsoft.com/contactus/)
* [Adaptateurs recommandés pour les PC prenant en charge Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
