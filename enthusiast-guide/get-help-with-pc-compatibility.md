---
title: Obtenir de l’aide sur la compatibilité des ordinateurs dans Windows Mixed Reality
description: Ressources d’aide pour les problèmes de compatibilité des PC lors de l’utilisation de Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
appliesto:
- Windows 10
ms.openlocfilehash: b9b9d46e2ab71fa90960e403ceac94b95ba01440
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92293078"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obtenir de l’aide sur la compatibilité des ordinateurs dans Windows Mixed Reality

Quand vous configurez Windows Mixed Reality ou que vous exécutez l’application [Windows Mixed Reality PC Check](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab) sur votre ordinateur, vous obtenez un rapport indiquant si votre PC est prêt à être exécuté. Voici quelques détails sur ce que vous pouvez voir.

Pour vous assurer que vous pouvez exécuter la réalité mixte, veuillez consulter la [Configuration minimale requise pour la compatibilité matérielle du PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).

## <a name="youre-good-to-go"></a>Vous êtes bien

Bonne nouvelle : votre PC peut exécuter Windows Mixed Reality. Mais gardez à l’esprit qu’il y a toujours une variation entre le matériel informatique et la configuration. l’expérience de la réalité mixte peut donc ne pas être la même sur tous les PC.

## <a name="supports-some-features"></a>Prend en charge certaines fonctionnalités

Votre ordinateur doit pouvoir exécuter certaines expériences Windows Mixed Reality, mais peut ne pas fournir la meilleure expérience possible. Les graphiques peuvent avoir un décalage, certaines applications et certains jeux peuvent ne pas fonctionner correctement, et certains peuvent ne pas s’exécuter du tout. 

Voici les messages que vous pouvez voir, et la procédure à suivre :

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Cet ordinateur dispose d’une carte graphique intégrée avec une RAM à canal unique

Les cartes graphiques intégrées offrent la meilleure expérience Windows Mixed Reality sur les PC avec une RAM double canal. Si vous rencontrez des problèmes de performances, essayez l’une des opérations suivantes :

* Installez une [carte graphique discrète compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines).
* Installez une barrette RAM supplémentaire pour créer une RAM à double canal.
* Basculez vers un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Cet ordinateur possède une configuration graphique hybride avec une liaison PCIe incompatible

PCIe correspond à *périphérique Peripheral Interconnect Express*. Il s’agit de la connexion utilisée par un PC pour communiquer avec une carte graphique. Votre configuration peut fonctionner, mais si vous rencontrez des problèmes, vous devrez basculer vers un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Le pilote graphique de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Si vous rencontrez des problèmes, essayez de télécharger un nouveau pilote graphique à l’aide de Windows Update (**Démarrez les paramètres > > mettre à jour & sécurité > Rechercher les mises à jour**), ou accédez au site Web du fabricant du fabricant de votre ordinateur ou de la carte graphique.

> [!div class="nextstepaction"]
> [Rechercher les mises à jour](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si cela ne fonctionne pas, vous devez ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou basculer vers un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality, car il ne dispose pas de suffisamment de cœurs. Si Windows Mixed Reality ne s’exécute pas correctement, remplacez le processeur par un processeur [compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou basculez sur un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Ce PC n’a peut-être pas de configuration USB compatible

Si vous rencontrez des problèmes lors de l’exécution de Windows Mixed Reality, procédez comme suit :

* Connectez votre casque à un autre port USB, s’il est disponible.
* Si cela ne fonctionne pas, désinstallez le pilote USB actuel de votre PC, puis réinstallez un pilote Microsoft :

1. Sélectionnez **Démarrer**, puis tapez « gestionnaire de périphériques » dans la zone de **recherche** .
2. Sélectionnez **Device Manager** dans les résultats.
3. Développez la catégorie des contrôleurs de bus série universels, examinez les périphériques listés et désinstallez tous les pilotes incompatibles.
    * Si la liste comprend un élément « contrôleur hôte eXtensible » qui ne contient pas « Microsoft » à la fin du nom de l’appareil, ce pilote n’est pas compatible avec Windows Mixed Reality. Vous devez le désinstaller. Pour désinstaller un pilote, cliquez avec le bouton droit sur l’appareil dans la liste et sélectionnez **désinstaller l’appareil**. Activez la case à cocher **supprimer le logiciel de pilote pour cet appareil** , puis sélectionnez **désinstaller**.
    * Si la liste comprend un élément « contrôleur hôte eXtensible » qui comprend « eTRON » dans le nom, ce contrôleur USB n’est pas compatible avec Windows Mixed Reality. Vous devez utiliser un port USB différent sur le PC ou acheter un autre contrôleur d’hôte USB 3,0.
4. Redémarrez votre PC.
5. Revenez à Device Manager et localisez à nouveau l’élément contrôleur hôte eXtensible. Si vous voyez maintenant « Microsoft » à la fin du nom de l’appareil, vous êtes prêt à aller. Si ce n’est pas le cas, répétez les étapes de désinstallation pour supprimer toutes les autres versions non-Microsoft du pilote.

* Si cela ne fonctionne toujours pas, ajoutez une carte USB PCIe à votre PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Ce PC ne dispose pas de Bluetooth 4,0 pour les contrôleurs

Bluetooth 4,0 est requis pour les contrôleurs de mouvement de réalité mixte sur certains casques. Vous pouvez toujours utiliser Windows Mixed Reality avec un contrôleur Xbox ou à l’aide de la souris et du clavier, ou vous pouvez utiliser un adaptateur Bluetooth USB pour connecter les contrôleurs de mouvement à votre PC. [Voir les adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>En fonction de votre casque, vous aurez peut-être besoin d’un adaptateur Bluetooth pour utiliser les contrôleurs de mouvement.

Certains casques intègrent Bluetooth afin que les contrôleurs puissent s’associer directement aux casques. D’autres nécessitent une radio Bluetooth sur le PC (ou un dongle distinct) pour utiliser les contrôleurs de mouvement. [Voir les adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Ce PC ne dispose pas d’un port USB auto-alimenté

Un port USB 3,0 auto-alimenté est nécessaire pour connecter un casque Windows Mixed Reality. Connectez un concentrateur USB 3,0 alimenté au PC et utilisez-le pour connecter votre casque.

### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Ce PC devrait fonctionner, mais vous bénéficierez d’une expérience optimale avec un processeur Intel® hautes performances.

Ce PC devrait fonctionner, mais un processeur Intel hautes performances offrira la meilleure expérience. Nous vous recommandons de disposer d’un processeur Intel® Core™ ou 7e GEN Intel® Core™ i5.

## <a name="cant-run-windows-mixed-reality"></a>Impossible d’exécuter Windows Mixed Reality

Voici les messages que vous pouvez voir, et la procédure à suivre :

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>La carte graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality

La carte graphique de ce PC n’est pas compatible avec Windows Mixed Reality. Vous devez ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou basculer vers un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Le pilote graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality

Le pilote graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality. Essayez de télécharger un nouveau pilote graphique à l’aide de Windows Update (**Démarrez les paramètres > > mettre à jour & sécurité > vérifier les mises à jour**) ou accédez au fabricant du PC ou au site Web du fabricant de la carte graphique. 

> [!div class="nextstepaction"]
> [Rechercher les mises à jour](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si cela ne fonctionne pas, vous devez ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou basculer vers un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Le processeur de ce PC ne fonctionnera pas avec Windows Mixed Reality

Le processeur de ce PC ne supprot pas les instructions AVX/POPCNT. Pour exécuter Windows Mixed Reality, vous devez le remplacer par une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou basculer vers un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Cet ordinateur ne dispose pas de suffisamment d’espace disque libre pour exécuter Windows Mixed Reality

Windows Mixed Reality requiert 10 Go d’espace disque libre pour l’installation et des performances optimales. Libérez de l’espace sur votre lecteur, puis recommencez l’installation.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Ce PC exécute une édition de Windows qui ne prend pas en charge Windows Mixed Reality

Windows Mixed Reality fonctionne sur Windows 10 famille et Windows 10 professionnel. Vous devez installer l’une de ces éditions pour pouvoir utiliser Windows Mixed Reality.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Ce PC n’exécute pas la dernière version de Windows 10

Windows Mixed Reality requiert la mise à jour des créateurs de automne Windows 10. [Mettez à jour votre PC](https://support.microsoft.com/help/4028685) , puis réessayez.

### <a name="this-pc-has-no-usb-30-port"></a>Ce PC n’a pas de port USB 3,0

Vous avez besoin d’un port USB 3,0 pour connecter un casque Windows Mixed Reality. Si vous utilisez un PC de bureau, ajoutez une carte USB PCIe. Si vous utilisez un ordinateur portable, vous devez passer à un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Vous ne pouvez pas exécuter cette application via le Bureau à distance

Pour utiliser Windows Mixed Reality, vous disposez d’un ordinateur avec un moniteur connecté. Si vous utilisez une machine virtuelle ou si vous n’avez pas de moniteur, essayez d’utiliser une carte graphique virtuelle. Il s’agit d’un appareil qui se connecte au DisplayPort du PC et émule un écran d’ordinateur. 

## <a name="getting-the-best-performance"></a>Obtenir des performances optimales

Certaines configurations matérielles peuvent entraîner des problèmes de performances avec Windows Mixed Reality. Pour les problèmes tels que le chargement lent, les visuels saccadés ou la qualité visuelle médiocre, essayez les correctifs courants suivants :

* Fermez toutes les applications ouvertes en cours d’exécution sur votre ordinateur de bureau.
* Si vous utilisez un adaptateur USB-C ou DisplayPort vers HDMI, essayez-en un autre. Voir les adaptateurs recommandés
* Si des moniteurs supplémentaires sont connectés à la carte graphique du PC, déconnectez-les.
* Essayez de télécharger des applications de réalité mixte différentes à partir du Windows Store, certaines peuvent fonctionner mieux avec la configuration de votre ordinateur.

> [!NOTE]
> Si vous voyez un message indiquant «cette configuration matérielle peut fonctionner avec Windows Mixed Reality, mais qu’elle n’a pas encore été testée, vous pourriez rencontrer des problèmes de performances lors de l’exécution de Windows Mixed Reality pour de longues sessions.

## <a name="see-also"></a>Voir aussi

* [Demander à la communauté](https://answers.microsoft.com)
* [Contactez-nous pour obtenir de l’aide](https://support.microsoft.com/contactus/)
* [Dépannage](troubleshooting-windows-mixed-reality.md)