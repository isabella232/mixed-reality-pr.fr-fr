---
title: Messages d’erreur du portail de réalité mixte
description: résolution avancée des messages du portail de Windows Mixed Reality qui vont au-delà de notre documentation de support technique standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, Support, portail de réalité mixte
appliesto:
- Windows 10
ms.openlocfilehash: c85030da129d90bb0a150ad50a6990e30b68c21bc7a3899c4182e87acd4b4fa5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186869"
---
# <a name="mixed-reality-portal-error-messages"></a>Messages d’erreur du portail de réalité mixte

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>J’obtiens un message d’erreur « un problème est survenu » ou je rencontre des problèmes dans le portail de réalité mixte.

Windows Mixed Reality de redémarrage :
1. Déconnectez les deux câbles du casque de votre PC.
2. Redémarrez votre PC.
3. Reconnectez votre casque.

Si cela ne fonctionne pas, assurez-vous que votre ordinateur reconnaît votre casque :
1. Sélectionnez Démarrer.
2. Tapez « gestionnaire de périphériques » dans la zone de recherche et sélectionnez-le dans la liste. 
3. Développez « appareils de réalité mixte » et vérifiez si votre casque est listé. 

S’il n’est pas listé :
1. Branchez le casque sur les différents ports du PC, le cas échéant.
2. recherchez les dernières mises à jour logicielles à partir de Windows Update.
3. Désinstallez et réinstallez Windows Mixed Reality :
    1. Déconnectez les deux câbles du casque de votre PC.
    2. sélectionnez **Paramètres > la réalité mixte > désinstaller**.
    3. sélectionnez **Paramètres appareils > > Bluetooth & d’autres appareils** pour découpler vos contrôleurs de mouvement. Sélectionnez chaque contrôleur, puis sélectionnez « Supprimer l’appareil ».
    4. Reconnectez votre casque à votre ordinateur pour réinstaller Windows Mixed Reality.
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>J’obtiens un message d’erreur « Vérifiez le câble USB ».

Connecter votre casque sur un autre port usb (et assurez-vous qu’il s’agit d’une vitesse usb 3,0). Essayez également de supprimer les extendeurs ou les hubs entre le casque et l’ordinateur.

## <a name="im-getting-a-check-your-display-cable-error-message"></a>J’obtiens un message d’erreur « vérifier votre câble d’affichage ».

Pour résoudre le problème, procédez comme suit :
* Connecter votre casque à un DisplayPort 1,2 ou ultérieur, ou HDMI 1,4 ou version ultérieure. Assurez-vous que le port correspond à la carte graphique la plus avancée sur votre PC.
* Si vous utilisez un adaptateur, assurez-vous qu’il prend en charge 4 Ko.
* Essayez d’utiliser un autre port HDMI.
* Si vous avez un moniteur externe branché dans un port HDMI, essayez de le brancher dans un DisplayPort et utilisez le port HDMI pour votre casque.
