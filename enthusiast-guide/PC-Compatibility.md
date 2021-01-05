---
title: Application de vérification du PC Windows Mixed Reality
description: Comment rechercher et utiliser l’application Windows Mixed Reality PC Check pour tester la compatibilité de votre ordinateur avant d’acheter un casque Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, compatible, compatibilité, PC, configuration système requise
appliesto:
- Windows 10
ms.openlocfilehash: 6dc187b14950f1446fd5e60c3e6db10fd2c3ce25
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725430"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Application de vérification du PC Windows Mixed Reality

L’application de **[vérification du PC Windows Mixed Reality](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** est la meilleure façon de s’assurer que votre ordinateur est prêt à exécuter Windows Mixed Reality. L’application de vérification du PC Windows Mixed Reality fonctionne uniquement sur les PC sur lesquels au moins Windows 10 version 1607 est installé. Pour vérifier votre version de Windows, tapez « winver » dans la barre de recherche et exécutez la commande. Pour les versions de Windows 10 antérieures à 1607, l’application s’affiche toujours dans le Store, mais vous obtenez une erreur lorsque vous essayez d’installer.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Après avoir exécuté l’application, vous obtiendrez l’un des messages suivants :

* **Vous êtes bien.** Votre PC a ce qu’il faut pour exécuter Windows Mixed Reality.
* **Vous y êtes presque.** Ce PC peut exécuter Windows Mixed Reality, mais certaines fonctionnalités peuvent être limitées.
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

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Obtenir de l’aide sur les résultats de la vérification du PC Windows Mixed Reality

Vous obtenez un rapport de compatibilité quand vous configurez Windows Mixed Reality ou que vous exécutez l’application Windows Mixed Reality PC Check sur votre ordinateur. Voici quelques détails sur ce que vous pouvez voir.

### <a name="youre-good-to-go"></a>![Vous êtes bien](images/glyph-succeeded.png)

Bonne nouvelle : votre PC peut exécuter Windows Mixed Reality. Gardez à l’esprit qu’il existe toujours des variations entre le matériel informatique et la configuration. L’expérience de la réalité mixte n’est peut-être pas la même sur tous les PC.

>[!NOTE]
>Si vous voyez un message indiquant «cette configuration matérielle peut fonctionner avec Windows Mixed Reality, mais qu’elle n’a pas encore été testée, vous pourriez rencontrer des problèmes de performances lors de l’exécution de Windows Mixed Reality pour de longues sessions.

### <a name="youre-nearly-there"></a>![Vous y êtes presque](images/glyph-warning.png)

Votre ordinateur doit pouvoir exécuter Windows Mixed Reality, mais il peut ne pas offrir la meilleure expérience possible. Les graphiques peuvent se décaler, certaines applications et certains jeux peuvent ne pas s’exécuter correctement, et certains peuvent ne pas s’exécuter du tout.

Voici les messages que vous pouvez voir, et la procédure à suivre :

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Cet ordinateur dispose d’une carte graphique intégrée avec une RAM à canal unique

Les cartes graphiques intégrées offrent la meilleure expérience Windows Mixed Reality sur les PC avec une RAM double canal. Si vous rencontrez des problèmes de performances :

* Installez une [carte graphique discrète compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Installez une barrette RAM supplémentaire pour créer une RAM à double canal.
* Basculez vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Cet ordinateur possède une configuration graphique hybride avec une liaison PCIe incompatible

PCIe correspond à *périphérique Peripheral Interconnect Express*. Il s’agit de la connexion utilisée par un PC pour communiquer avec une carte graphique. Votre configuration peut fonctionner, mais si vous rencontrez des problèmes, vous devrez basculer vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Le pilote graphique de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Si vous rencontrez des problèmes, essayez de télécharger un nouveau pilote graphique à l’aide de Windows Update (**Démarrez les paramètres > > mettre à jour & sécurité > Rechercher les mises à jour**), ou accédez au site Web du fabricant du fabricant de votre ordinateur ou de la carte graphique.

Si cela ne fonctionne pas, vous devez ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou basculer vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality, car il ne dispose pas de suffisamment de cœurs. Si Windows Mixed Reality ne s’exécute pas correctement, effectuez une mise à jour vers un ordinateur [compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou basculez vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Ce PC n’a peut-être pas de configuration USB compatible

Si vous rencontrez des problèmes lors de l’exécution de Windows Mixed Reality :

* Connectez votre casque à un autre port USB, s’il est disponible.
* Si cela ne fonctionne pas, désinstallez le pilote USB actuel de votre PC, puis réinstallez un pilote Microsoft :

1. Sélectionnez **Démarrer**, puis tapez **« Gestionnaire de périphériques »** dans la zone de recherche.
1. Sélectionnez **Device Manager** dans les résultats.
1. Développez la catégorie des contrôleurs de bus série universels, examinez les périphériques listés et désinstallez tous les pilotes incompatibles. 
 * Si la liste comprend un élément « contrôleur hôte eXtensible » sans « Microsoft » à la fin du nom de l’appareil, le pilote n’est pas compatible avec Windows Mixed Reality. Vous devez le désinstaller. Pour désinstaller un pilote, cliquez avec le bouton droit sur l’appareil dans la liste et sélectionnez **désinstaller l’appareil**. Activez la case à cocher **supprimer le logiciel de pilote pour cet appareil** , puis sélectionnez **désinstaller**.
 * Si la liste comprend un élément « contrôleur hôte eXtensible » qui comprend « eTRON » dans le nom, ce contrôleur USB n’est pas compatible avec Windows Mixed Reality. Vous devez utiliser un port USB différent sur le PC ou acheter un autre contrôleur d’hôte USB 3,0.
1. Redémarrez votre PC. 
1. Revenez à Device Manager et localisez à nouveau l’élément contrôleur hôte eXtensible. Si vous voyez maintenant « Microsoft » à la fin du nom de l’appareil, vous êtes prêt à aller. Si ce n’est pas le cas, répétez les étapes de désinstallation pour supprimer toutes les autres versions non-Microsoft du pilote.
* Si cela ne fonctionne toujours pas, ajoutez une carte USB PCIe à votre PC.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Ce PC ne dispose pas de Bluetooth 4,0 pour les contrôleurs.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Ce PC ne dispose pas d’un port USB auto-alimenté.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Ce PC devrait fonctionner, mais vous bénéficierez d’une expérience optimale avec un processeur Intel® hautes performances.

### <a name="cant-run-mixed-reality"></a>![Impossible d’exécuter la réalité mixte](images/glyph-error.png)

 [Obtenir de l’aide sur les résultats de la vérification du PC Windows Mixed Reality](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
