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
ms.openlocfilehash: 464a2709600f7fff076053026797ce809b8fbf73
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340627"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Application de vérification du PC Windows Mixed Reality

L’application de **[vérification du PC Windows Mixed Reality](windows-mixed-reality-pc-check-app.md)** est la meilleure façon de s’assurer que votre ordinateur est prêt à exécuter Windows Mixed Reality.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Après avoir exécuté l’application, vous obtiendrez l’un des messages suivants :

* **Vous êtes bien.** Votre PC a ce qu’il faut pour exécuter Windows Mixed Reality.
* **Vous y êtes presque.** Ce PC peut être en mesure d’exécuter Windows Mixed Reality, mais certaines fonctionnalités peuvent être limitées.
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
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Votre PC ne remplit pas les conditions requises pour l’élément spécifié.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Obtenir de l’aide sur les résultats de la vérification du PC Windows Mixed Reality

Quand vous configurez Windows Mixed Reality ou que vous exécutez l’application Windows Mixed Reality PC Check sur votre ordinateur, vous obtenez un rapport indiquant si votre PC est prêt à être exécuté. Voici quelques détails sur ce que vous pouvez voir.

### <a name="youre-good-to-go"></a>![Vous êtes bien](images/glyph-succeeded.png)

Bonne nouvelle : votre PC peut exécuter Windows Mixed Reality. Mais gardez à l’esprit qu’il y a toujours une variation entre le matériel informatique et la configuration. l’expérience de la réalité mixte peut donc ne pas être la même sur tous les PC.

>[!NOTE]
>Si vous voyez un message indiquant «cette configuration matérielle peut fonctionner avec Windows Mixed Reality, mais qu’elle n’a pas encore été testée, vous pourriez rencontrer des problèmes de performances lors de l’exécution de Windows Mixed Reality pour de longues sessions.

### <a name="youre-nearly-there"></a>![Vous y êtes presque](images/glyph-warning.png)

Votre ordinateur doit pouvoir exécuter Windows Mixed Reality, mais il peut ne pas offrir la meilleure expérience possible. Les graphiques peuvent avoir un décalage, certaines applications et certains jeux peuvent ne pas fonctionner correctement, et certains peuvent ne pas s’exécuter du tout.

Voici les messages que vous pouvez voir, et la procédure à suivre :

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Cet ordinateur dispose d’une carte graphique intégrée avec une RAM à canal unique

Les cartes graphiques intégrées offrent la meilleure expérience Windows Mixed Reality sur les PC avec une RAM double canal. Si vous rencontrez des problèmes de performances, essayez l’une des opérations suivantes :

* Installez une [carte graphique discrète compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Installez une barrette RAM supplémentaire pour créer une RAM à double canal.
* Basculez vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Cet ordinateur possède une configuration graphique hybride avec une liaison PCIe incompatible

PCIe correspond à *périphérique Peripheral Interconnect Express*. Il s’agit de la connexion utilisée par un PC pour communiquer avec une carte graphique. Votre configuration peut fonctionner, mais si vous rencontrez des problèmes, vous devrez basculer vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Le pilote graphique de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Si vous rencontrez des problèmes, essayez de télécharger un nouveau pilote graphique à l’aide de Windows Update ( **Démarrez les paramètres > > mettre à jour & sécurité > Rechercher les mises à jour** ), ou accédez au site Web du fabricant du fabricant de votre ordinateur ou de la carte graphique.

Si cela ne fonctionne pas, vous devez ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou basculer vers un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality, car il ne dispose pas de suffisamment de cœurs. Si Windows Mixed Reality ne s’exécute pas correctement, remplacez le processeur par un processeur [compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou basculez sur un [PC compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Ce PC n’a peut-être pas de configuration USB compatible

Si vous rencontrez des problèmes lors de l’exécution de Windows Mixed Reality, procédez comme suit :

* Connectez votre casque à un autre port USB, s’il est disponible.
* Si cela ne fonctionne pas, désinstallez le pilote USB actuel de votre PC, puis réinstallez un pilote Microsoft :

1. Sélectionnez **Démarrer** , puis tapez **« Gestionnaire de périphériques »** dans la zone de recherche.
1. Sélectionnez **Device Manager** dans les résultats.
1. Développez la catégorie des contrôleurs de bus série universels, examinez les périphériques listés et désinstallez tous les pilotes incompatibles. 
 * Si la liste comprend un élément « contrôleur hôte eXtensible » qui ne contient pas « Microsoft » à la fin du nom de l’appareil, ce pilote n’est pas compatible avec Windows Mixed Reality. Vous devez le désinstaller. Pour désinstaller un pilote, cliquez avec le bouton droit sur l’appareil dans la liste et sélectionnez **désinstaller l’appareil**. Activez la case à cocher **supprimer le logiciel de pilote pour cet appareil** , puis sélectionnez **désinstaller**.
 * Si la liste comprend un élément « contrôleur hôte eXtensible » qui comprend « eTRON » dans le nom, ce contrôleur USB n’est pas compatible avec Windows Mixed Reality. Vous devez utiliser un port USB différent sur le PC ou acheter un autre contrôleur d’hôte USB 3,0.
1. Redémarrez votre PC. 
1. Revenez à Device Manager et localisez à nouveau l’élément contrôleur hôte eXtensible. Si vous voyez maintenant « Microsoft » à la fin du nom de l’appareil, vous êtes prêt à aller. Si ce n’est pas le cas, répétez les étapes de désinstallation pour supprimer toutes les autres versions non-Microsoft du pilote.
* Si cela ne fonctionne toujours pas, ajoutez une carte USB PCIe à votre PC.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Ce PC ne dispose pas de Bluetooth 4,0 pour les contrôleurs.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Ce PC ne dispose pas d’un port USB auto-alimenté.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Ce PC devrait fonctionner, mais vous bénéficierez d’une expérience optimale avec un processeur Intel® hautes performances.

### <a name="cant-run-mixed-reality"></a>![Impossible d’exécuter la réalité mixte](images/glyph-error.png)

 [Obtenir de l’aide sur les résultats de la vérification du PC Windows Mixed Reality](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
