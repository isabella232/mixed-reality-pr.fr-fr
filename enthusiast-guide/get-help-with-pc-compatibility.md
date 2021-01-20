---
title: Obtenir de l’aide sur la compatibilité des PC
description: Tenez-vous au fait des ressources permettant de résoudre les problèmes de compatibilité des PC quand vous travaillez avec des applications et des appareils Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, feedback, Hub de commentaires, bogues
appliesto:
- Windows 10
ms.openlocfilehash: 28b377108fdb51d7f922710e579d62e7103ef765
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580534"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obtenir de l’aide sur la compatibilité des ordinateurs dans Windows Mixed Reality

Quand vous configurez Windows Mixed Reality ou à l’aide du [portail de réalité mixte](install-windows-mixed-reality.md), vous obtenez un rapport indiquant si votre ordinateur est à la votre tâche. Nous avons réparti des détails spécifiques sur ce que vous pouvez voir dans les sections ci-dessous.

Avant de poursuivre, essayez les correctifs les plus courants ci-dessous : 

> [!div class="checklist"]
> * Vérifiez que votre ordinateur répond à la [Configuration minimale requise pour la compatibilité matérielle du PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * Vérifier que votre [carte graphique et votre processeur](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) sont compatibles
> * Vérifier la liste des [adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Mettez à jour votre pilote graphique en sélectionnant **démarrer > paramètres > mettre à jour & sécurité > Rechercher les mises à jour** 

Si vous souhaitez obtenir un contact, vous pouvez [demander à la communauté](https://answers.microsoft.com), [contacter le support technique](https://support.microsoft.com/contactus/)ou passer en revue les informations de [Dépannage](troubleshooting-windows-mixed-reality.md) .

## <a name="youre-good-to-go"></a>Vous êtes bien

Bonne nouvelle. Si vous voyez le message **vous êtes correct** , votre ordinateur peut exécuter Windows Mixed Reality. Il y a toujours une variation entre le matériel informatique et la configuration. l’expérience de réalité mixte peut donc ne pas être la même sur tous les PC.

## <a name="supports-some-features"></a>Prend en charge certaines fonctionnalités

Si vous voyez le message **prend en charge certaines fonctionnalités** , votre ordinateur peut exécuter des expériences Windows Mixed Reality, mais il peut ne pas offrir la meilleure expérience possible. Parmi les inconvénients possibles, citons les graphiques en retard, les résultats de performances et certaines applications et certains jeux que vous ne pouvez pas exécuter du tout. Nous avons listé les messages que vous pouvez voir et la procédure à suivre ci-dessous :

* [Cet ordinateur dispose d’une carte graphique intégrée avec une RAM à canal unique](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Cet ordinateur possède une configuration graphique hybride avec une liaison PCIe incompatible](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [Le pilote graphique de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Ce PC n’a peut-être pas de configuration USB compatible](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Ce PC ne dispose pas de Bluetooth 4,0 pour les contrôleurs](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [En fonction de votre casque, vous aurez peut-être besoin d’un adaptateur Bluetooth pour utiliser les contrôleurs de mouvement.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Ce PC ne dispose pas d’un port USB auto-alimenté](#this-pc-doesnt-have-a-self-powered-usb-port)
* [La carte graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [Le pilote graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [Le processeur de ce PC ne fonctionnera pas avec Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Cet ordinateur ne dispose pas de suffisamment d’espace disque libre pour exécuter Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Ce PC exécute une édition de Windows qui ne prend pas en charge Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Ce PC n’exécute pas la dernière version de Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Ce PC n’a pas de port USB 3,0](#this-pc-has-no-usb-30-port)
* [Vous ne pouvez pas exécuter cette application via le Bureau à distance](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Cet ordinateur dispose d’une carte graphique intégrée avec une RAM à canal unique

Les cartes graphiques intégrées offrent la meilleure expérience Windows Mixed Reality sur les PC avec une RAM double canal. Si vous rencontrez des problèmes de performances :

> [!div class="checklist"]
> * Installer une [carte graphique discrète compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Installer une mémoire RAM supplémentaire pour créer une RAM à double canal
> * Basculer vers un [PC compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Cet ordinateur possède une configuration graphique hybride avec une liaison PCIe incompatible

PCIe signifie *périphérique Peripheral Interconnect Express*, qui est la connexion utilisée par un PC pour communiquer avec une carte graphique. Votre configuration peut fonctionner, mais si vous rencontrez des problèmes, vous devrez basculer vers un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Le pilote graphique de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Essayez de télécharger un nouveau pilote graphique à l’aide de Windows Update par :

> [!div class="checklist"]
> * Sélection **des paramètres de démarrage > > mettre à jour & sécurité > Rechercher les mises à jour** ou accéder au site Web du fabricant du PC ou de la carte graphique
> * [Rechercher les mises à jour](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si cela ne fonctionne pas, vous devez :

> [!div class="checklist"]
> * Ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Basculer vers un [PC compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Le processeur de ce PC peut ne pas fonctionner correctement avec Windows Mixed Reality

Le processeur de votre PC peut ne pas fonctionner correctement avec Windows Mixed Reality, car il ne dispose pas de suffisamment de cœurs. Si Windows Mixed Reality ne s’exécute pas correctement :

> [!div class="checklist"]
> * Remplacer le processeur par un processeur [compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Basculer vers un [PC compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Ce PC n’a peut-être pas de configuration USB compatible

Pour les problèmes d’exécution de Windows Mixed Reality :

> [!div class="checklist"]
> * Consultez notre [documentation sur les adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) pour les solutions aux problèmes de compatibilité courants
> * Envisagez d’utiliser un [concentrateur USB alimenté en externe](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

Si les problèmes persistent :

> [!div class="checklist"]
> * Connectez votre casque à un autre port USB, si vous en avez un disponible.
> * Si cela ne fonctionne pas, désinstallez le pilote USB actuel de votre PC, puis réinstallez un pilote Microsoft :

1. Sélectionnez **Démarrer**, puis tapez « gestionnaire de périphériques » dans la zone de **recherche** .
2. Sélectionnez **Device Manager** dans les résultats.
3. Développez la catégorie des contrôleurs de bus série universels, examinez les périphériques listés et désinstallez tous les pilotes incompatibles.
    * Si la liste comprend un élément « contrôleur hôte eXtensible » qui ne contient pas « Microsoft » à la fin du nom de l’appareil, ce pilote n’est pas compatible avec Windows Mixed Reality. Vous devez le désinstaller. Pour désinstaller un pilote, cliquez avec le bouton droit sur l’appareil dans la liste et sélectionnez **désinstaller l’appareil**. Activez la case à cocher **supprimer le logiciel de pilote pour cet appareil** , puis sélectionnez **désinstaller**.
    * Si la liste comprend un élément « contrôleur hôte eXtensible » qui comprend « eTRON » dans le nom, ce contrôleur USB n’est pas compatible avec Windows Mixed Reality. Vous devez utiliser un port USB différent sur le PC ou acheter un autre contrôleur d’hôte USB 3,0.
4. Redémarrez votre PC.
5. Revenez à Device Manager et localisez à nouveau l’élément contrôleur hôte eXtensible. Si vous voyez maintenant « Microsoft » à la fin du nom de l’appareil, vous êtes prêt à aller. Si ce n’est pas le cas, répétez les étapes de désinstallation pour supprimer toute version non-Microsoft supplémentaire du pilote.

> [!div class="checklist"]
> * Si cela ne fonctionne toujours pas, ajoutez une carte USB PCIe à votre PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Ce PC ne dispose pas de Bluetooth 4,0 pour les contrôleurs

2018 et les nouveaux casques de la réalité Windows Mixed disposent déjà du Bluetooth intégré, mais si vous disposez d’un casque plus ancien, Bluetooth 4,0 est requis pour les contrôleurs de mouvement de réalité mixte. Vous pouvez toujours [utiliser Windows Mixed Reality avec un contrôleur Xbox](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset), une [souris et un clavier](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)ou un [adaptateur Bluetooth USB pour connecter les contrôleurs de mouvement](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) à votre PC. [Voir les adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>En fonction de votre casque, vous aurez peut-être besoin d’un adaptateur Bluetooth pour utiliser les contrôleurs de mouvement.

Certains casques intègrent la technologie Bluetooth, ce qui permet aux contrôleurs de s’associer directement aux casques. D’autres nécessitent une radio Bluetooth sur le PC (ou un dongle distinct) pour utiliser les contrôleurs de mouvement. Pour plus d’informations, consultez la page [adaptateurs recommandés](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) .

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Ce PC ne dispose pas d’un port USB auto-alimenté

Un port USB 3,0 auto-alimenté est nécessaire pour connecter un casque Windows Mixed Reality. Connectez un [concentrateur USB 3,0 alimenté](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) au PC et utilisez-le pour connecter votre casque.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>La carte graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality

La carte graphique de ce PC n’est pas compatible avec Windows Mixed Reality. Vous devez effectuer les opérations suivantes :

> [!div class="checklist"]
> * Ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Basculer vers un [PC compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Le pilote graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality

Le pilote graphique de ce PC ne fonctionnera pas avec Windows Mixed Reality. Essayez de télécharger un nouveau pilote graphique à l’aide de Windows Update par :

> [!div class="checklist"]
> * Sélection **des paramètres de démarrage > > mettre à jour & sécurité > Rechercher les mises à jour** ou accéder au site Web du fabricant du PC ou de la carte graphique
> * [Rechercher les mises à jour](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si cela ne fonctionne pas, vous devez :

> [!div class="checklist"]
> * Ajouter une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Basculer vers un [PC compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Le processeur de ce PC ne fonctionnera pas avec Windows Mixed Reality

Le processeur de ce PC ne prend pas en charge les instructions AVX/POPCNT. Pour exécuter Windows Mixed Reality, vous devez :

> [!div class="checklist"]
> * Remplacez-le par une [carte graphique compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Basculer vers un [PC compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Cet ordinateur ne dispose pas de suffisamment d’espace disque libre pour exécuter Windows Mixed Reality

Windows Mixed Reality requiert 10 Go d’espace disque libre pour l’installation et des performances optimales. Libérez de l’espace sur votre lecteur, puis réessayez de configurer à partir du début.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Ce PC exécute une édition de Windows qui ne prend pas en charge Windows Mixed Reality

Windows Mixed Reality fonctionne sur [Windows 10 famille](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) et [Windows 10 professionnel](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). Vous devez installer l’une de ces éditions pour utiliser Windows Mixed Reality.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Ce PC n’exécute pas la dernière version de Windows 10

Windows Mixed Reality requiert la mise à jour des créateurs de automne Windows 10. [Mettez à jour votre PC](https://support.microsoft.com/help/4028685) , puis réessayez.

### <a name="this-pc-has-no-usb-30-port"></a>Ce PC n’a pas de port USB 3,0

Vous avez besoin d’un port USB 3,0 pour connecter un casque Windows Mixed Reality. Si vous utilisez un PC de bureau, ajoutez une carte USB PCIe. Pour les ordinateurs portables, vous devez passer à un [PC compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Vous ne pouvez pas exécuter cette application via le Bureau à distance

Pour utiliser Windows Mixed Reality, vous avez besoin d’un PC avec un moniteur connecté. Si vous utilisez une machine virtuelle ou si vous n’avez pas de moniteur, essayez d’utiliser une carte graphique virtuelle. Il s’agit d’un appareil qui se connecte au DisplayPort du PC et émule un écran d’ordinateur.

## <a name="getting-the-best-performance"></a>Obtenir des performances optimales

Certaines configurations matérielles peuvent entraîner des problèmes de performances avec Windows Mixed Reality. Pour les problèmes tels que le chargement lent, les visuels saccadés ou la qualité visuelle médiocre, essayez les correctifs courants suivants :

* Fermez toutes les applications ouvertes en cours d’exécution sur votre ordinateur de bureau
* Si vous utilisez un adaptateur USB-C ou DisplayPort vers HDMI, essayez-en un autre. Voir les adaptateurs recommandés
* Si des moniteurs supplémentaires sont connectés à la carte graphique du PC, déconnectez-les
* Essayez de télécharger des applications de réalité mixte différentes à partir du Windows Store, certaines peuvent fonctionner mieux avec la configuration de votre ordinateur
* Consultez notre documentation sur les questions sur les [performances](performance-questions.md)

Si vous rencontrez toujours des problèmes de performances, mettez à jour les paramètres [Windows Mixed Reality](set-up-windows-mixed-reality.md) suivants pour une expérience utilisateur optimale :

* Expérience
* Résolution
* Fréquence d’images
* Étalonnage

> [!NOTE]
> Si vous voyez un message indiquant «cette configuration matérielle peut fonctionner avec Windows Mixed Reality, mais qu’elle n’a pas encore été testée, vous pourriez rencontrer des problèmes de performances lors de l’exécution de Windows Mixed Reality pour de longues sessions.

## <a name="working-with-steamvr"></a>Utilisation de SteamVR

Profiter des jeux à partir de SteamVR est un excellent moyen d’expérimenter tout ce qu’il faut offrir. Toutefois, vous souhaiterez vous assurer que vous [obtenez les meilleures performances](performance-questions.md) de votre appareil immersif. Une fois que vous [avez installé la](https://store.steampowered.com/about)diffusion en continu :

* Suivez les instructions relatives [à l’utilisation de SteamVR avec Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* Installer les applications de [test de performances SteamVR](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Point de contrôle suivant de VR

Si vous suivez le trajet VR que nous avons disposé, vous êtes presque prêt à acheter un appareil. À partir de là, vous pouvez passer à la dernière avant d’acheter un point de contrôle :

> [!div class="nextstepaction"]
> [FAQ sur l’achat](before-you-buy-faqs.md)

Ou accédez directement à la section mise en route :

> [!div class="nextstepaction"]
> [Configuration de la réalité mixte Windows](set-up-windows-mixed-reality.md)

Vous pouvez toujours revenir au voyage de [VR](vr-journey.md) à tout moment.