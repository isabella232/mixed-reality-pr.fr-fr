---
title: Erreurs d'installation
description: résolution des erreurs d’installation avancée Windows Mixed Reality qui dépasse notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, Support, Installation
appliesto:
- Windows 10
ms.openlocfilehash: 702e38196ea3fda5cc7595decfeef4c6305ae2274ce6e5740af60c511447506b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213187"
---
# <a name="installation-errors"></a>Erreurs d'installation

## <a name="your-pc-cant-run-windows-mixed-reality"></a>« Votre ordinateur ne peut pas s’exécuter Windows Mixed Reality »

Votre ordinateur ne répond pas à la [Configuration minimale requise](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) pour exécuter Windows Mixed Reality. la configuration matérielle de votre ordinateur peut ne pas être compatible avec Windows Mixed Reality ou vous devrez peut-être effectuer une [mise à jour vers la dernière version de Windows](https://support.microsoft.com/help/12373/windows-update-faq). 

Windows Mixed Reality nécessite un pilote de carte graphique prenant en charge au moins WDDM 2,2. Assurez-vous que vous disposez de la dernière mise à jour du pilote auprès du fabricant. si Windows Mixed Reality configuration indique que votre carte graphique ne répond pas aux exigences et que vous pensez qu’elle le fait, assurez-vous que votre casque est branché à la bonne carte.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>« Vous êtes presque là : ce PC ne répond pas à la configuration minimale requise pour exécuter Windows Mixed Reality »

Votre ordinateur ne répond pas à la [Configuration minimale requise](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) pour la meilleure expérience dans Windows Mixed Reality. Votre ordinateur peut être en mesure d’exécuter un casque immersif, mais peut rencontrer des problèmes de performances et ne pas pouvoir exécuter certaines applications.

Windows Mixed Reality nécessite un pilote de carte graphique prenant en charge au moins WDDM 2,2. Assurez-vous que vous disposez de la dernière mise à jour du pilote auprès du fabricant. si Windows Mixed Reality configuration indique que votre carte graphique ne répond pas aux exigences et que vous pensez qu’elle le fait, assurez-vous que votre casque est branché à la bonne carte.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>«avant de pouvoir configurer Windows Mixed Reality, votre administrateur doit l’activer pour votre organisation. En savoir plus»

vous êtes probablement sur un réseau géré par l’entreprise et votre organisation utilise Windows Server Update Services (WSUS). Ces stratégies et d’autres peuvent bloquer le téléchargement. Contactez le service informatique ou l’administrateur système de votre organisation pour [activer Windows Mixed Reality](/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>« Nous n’avons pas pu télécharger le logiciel de réalité mixte » ou « raccrocher pendant le téléchargement »

* Parfois, une mise à jour en attente peut bloquer le téléchargement de logiciels de la réalité mixte. accédez à **Paramètres > Update & security > Windows Update** et assurez-vous que Windows Update est activé. Ensuite, téléchargez et installez les mises à jour en attente. si vous recevez une erreur Windows Update, procurez-vous de l’aide [ici](https://support.microsoft.com/help/10164/fix-windows-update-errors).
* Assurez-vous que votre ordinateur est connecté à Internet et qu’il dispose d’au moins 2 Go d’espace de stockage disponible. vérifiez l’état de votre réseau à l’adresse suivante : **Paramètres > réseau & l’état de > Internet**. Si vous ne pouvez pas vous connecter à Internet, procurez-vous de l’aide [ici](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues).  
* Redémarrez votre ordinateur et réessayez. 

Si ces solutions ne fonctionnent pas, essayez :
* Si votre Wi-Fi connexion réseau est définie sur [contrôlé](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq), modifiez-la en la définissant sur non contrôlé. pour désactiver une connexion limitée, accédez à : **Paramètres > réseau & l’état Internet > > modifier les propriétés de connexion > définir comme connexion limitée** et sélectionnez « désactivé ».  
* Si vous avez récemment installé une mise à jour, cela peut entraîner des problèmes. Nous vous déconseillons de supprimer les mises à jour installées, notamment les mises à jour de sécurité qui sécurisent votre ordinateur. Toutefois, la suppression de la mise à jour la plus récente peut parfois aider à déterminer la source du problème : 
    * accédez à **Paramètres > mettre à jour & sécurité > afficher l’historique des mises à jour installées > désinstaller les mises à jour**
    * Sélectionnez la dernière mise à jour installée et désinstallez.
    * À l’invite « êtes-vous sûr de vouloir désinstaller cette mise à jour ? » répondez « Oui ». Si vous recevez une erreur lorsque vous tentez d’effectuer ces étapes, vous pouvez obtenir plus de détails sur la [résolution des erreurs de Windows Update](https://support.microsoft.com//help/10164/fix-windows-update-errors). 
    * Redémarrez votre ordinateur et réessayez. 
    * si Windows Mixed Reality s’installe correctement, réinstallez les dernières mises à jour sous **Paramètres > Windows Update > rechercher les mises à jour** et voir si Windows Mixed Reality continue à fonctionner. s’il ne s’installe pas correctement, réinstallez les mises à jour et contactez le Support Windows. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>« Une erreur s’est produite et nous n’avons pas pu démarrer Windows Mixed Reality »
Pour obtenir plus d’informations sur un code d’erreur spécifique, consultez [cette page](error-codes.md). Vous pouvez également essayer d’effectuer les opérations suivantes :

* Débranchez les deux câbles du casque du PC.
* Redémarrez le PC.
* accédez à **Paramètres > mettre à jour & sécurité > Windows Update** et assurez-vous que Windows Update est activé. Téléchargez et installez les mises à jour en attente.
* Reconnectez votre casque au PC, puis recommencez l’installation.

Si ces étapes ne fonctionnent pas, désinstallez, puis réinstallez Windows Mixed Reality :
* accédez à **Paramètres > > de la réalité mixte** , puis sélectionnez désinstaller. 
* Redémarrez votre PC. 
* Pour recommencer le processus d’installation, il vous suffit de brancher votre casque sur votre PC.