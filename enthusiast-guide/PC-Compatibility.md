---
title: Windows Mixed Reality Application de vérification de PC
description: procédure de recherche et d’utilisation de l’application Windows Mixed Reality pc Check pour tester la compatibilité de votre ordinateur avant d’acheter un casque Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, compatible, compatibilité, PC, configuration système requise
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188042"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality Application de vérification de PC

l’application **[Windows Mixed Reality pc Check](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** est la meilleure façon de s’assurer que votre ordinateur est prêt à fonctionner Windows Mixed Reality. l’application de vérification de PC Windows Mixed Reality fonctionne uniquement sur les pc avec au moins Windows 10 Version 1607 installée. pour vérifier votre version de Windows, tapez « winver » dans la barre de recherche et exécutez la commande. pour les versions Windows 10 antérieures à 1607, l’application s’affiche toujours dans le Store, mais vous obtenez une erreur lorsque vous essayez d’installer.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Après avoir exécuté l’application, vous obtiendrez l’un des messages suivants :

* **Vous êtes bien.** Votre PC a ce qu’il faut pour exécuter Windows Mixed Reality.
* **Vous y êtes presque.** ce PC peut exécuter Windows Mixed Reality, mais certaines fonctionnalités peuvent être limitées.
* **Impossible d’exécuter la réalité mixte.** Ce PC ne répond pas à la configuration minimale requise pour exécuter Windows Mixed Reality.

Vous obtiendrez ensuite une analyse de votre ordinateur par rapport au matériel, aux pilotes et au système d’exploitation requis.
![capture d’écran de la vérification de Windows Mixed Reality PC](images/screenshot-mr-pc-check.jpg) 

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

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>obtenir de l’aide sur les résultats de la vérification du PC Windows Mixed Reality

vous obtenez un rapport de compatibilité lorsque vous configurez Windows Mixed Reality ou exécutez l’application de vérification de Windows Mixed Reality PC sur votre ordinateur. Voici quelques détails sur ce que vous pouvez voir.

### <a name="youre-good-to-go"></a>![Vous êtes bien](images/glyph-succeeded.png)

Bonne nouvelle : votre PC peut s’exécuter Windows Mixed Reality. Gardez à l’esprit qu’il existe toujours des variations entre le matériel informatique et la configuration. L’expérience de la réalité mixte n’est peut-être pas la même sur tous les PC.

>[!NOTE]
>si vous voyez un message indiquant «cette configuration matérielle peut fonctionner avec Windows Mixed Reality, mais elle n’a pas encore été testée, vous pouvez rencontrer des problèmes de performances lors de l’exécution de Windows Mixed Reality pour des sessions longues.

### <a name="youre-nearly-there"></a>![Vous y êtes presque](images/glyph-warning.png)

votre ordinateur doit pouvoir exécuter Windows Mixed Reality, mais il peut ne pas fournir la meilleure expérience possible. Les graphiques peuvent se décaler, certaines applications et certains jeux peuvent ne pas s’exécuter correctement, et certains peuvent ne pas s’exécuter du tout.

Voici les messages que vous pouvez voir, et la procédure à suivre :

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Cet ordinateur dispose d’une carte graphique intégrée avec une RAM à canal unique

les cartes graphiques intégrées offrent une expérience Windows Mixed Reality optimale sur les pc avec une RAM double canal. Si vous rencontrez des problèmes de performances :

* Installez une [carte graphique discrète compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Installez une barrette RAM supplémentaire pour créer une RAM à double canal.
* Basculez vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Cet ordinateur possède une configuration graphique hybride avec une liaison PCIe incompatible

PCIe correspond à *périphérique Peripheral Interconnect Express*. Il s’agit de la connexion utilisée par un PC pour communiquer avec une carte graphique. Votre configuration peut fonctionner, mais si vous rencontrez des problèmes, vous devrez basculer vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Le pilote graphique de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

si vous rencontrez des problèmes, essayez de télécharger un nouveau pilote graphique à l’aide de Windows Update (**démarrez > Paramètres > mettre à jour & sécurité > vérifier les mises à jour**) ou accédez au site web du fabricant du fabricant du PC ou de la carte graphique.

Si cela ne fonctionne pas, vous devez ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou basculer vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality, car il ne dispose pas de suffisamment de cœurs. si Windows Mixed Reality ne fonctionne pas correctement, [effectuez une mise](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) à jour vers un ordinateur compatible ou basculez vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Ce PC n’a peut-être pas de configuration USB compatible

Si vous rencontrez des problèmes lors de l’exécution de Windows Mixed Reality :

* Connectez votre casque à un autre port USB, s’il est disponible.
* Si cela ne fonctionne pas, désinstallez le pilote USB actuel de votre PC, puis réinstallez un pilote Microsoft :

1. Sélectionnez **Démarrer**, puis tapez **« Gestionnaire de périphériques »** dans la zone de recherche.
1. Sélectionnez **Gestionnaire de périphériques** dans les résultats.
1. Développez la catégorie des contrôleurs de bus série universels, examinez les périphériques listés et désinstallez tous les pilotes incompatibles. 
 * Si la liste comprend un élément « contrôleur hôte eXtensible » sans « Microsoft » à la fin du nom de l’appareil, le pilote n’est pas compatible avec Windows Mixed Reality. Vous devez le désinstaller. Pour désinstaller un pilote, cliquez avec le bouton droit sur l’appareil dans la liste et sélectionnez **désinstaller l’appareil**. Activez la case à cocher **supprimer le logiciel de pilote pour cet appareil** , puis sélectionnez **désinstaller**.
 * Si la liste comprend un élément « contrôleur hôte eXtensible » qui comprend « eTRON » dans le nom, ce contrôleur USB n’est pas compatible avec Windows Mixed Reality. Vous devez utiliser un port USB différent sur le PC ou acheter un autre contrôleur d’hôte USB 3,0.
1. Redémarrez votre PC. 
1. Revenez à Gestionnaire de périphériques et localisez à nouveau l’élément contrôleur hôte eXtensible. Si vous voyez maintenant « Microsoft » à la fin du nom de l’appareil, vous êtes prêt à aller. Si ce n’est pas le cas, répétez les étapes de désinstallation pour supprimer toutes les autres versions non-Microsoft du pilote.
* Si cela ne fonctionne toujours pas, ajoutez une carte USB PCIe à votre PC.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>ce PC n’a pas Bluetooth 4,0 pour les contrôleurs.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Ce PC ne dispose pas d’un port USB auto-alimenté.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Ce PC devrait fonctionner, mais vous bénéficierez d’une expérience optimale avec un processeur Intel® hautes performances.

### <a name="cant-run-mixed-reality"></a>![Impossible d’exécuter la réalité mixte](images/glyph-error.png)

 [obtenir de l’aide sur les résultats de la vérification du PC Windows Mixed Reality](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
