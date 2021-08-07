---
title: FAQ sur la voix et l’audio
description: résolution des problèmes vocaux et Audio Windows Mixed Reality qui dépasse notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, Support, problèmes Audio, problèmes vocaux
ms.openlocfilehash: d1d30cebb40d54d579e978013b9abc60981fa943d43b95a96f358092631b4d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208979"
---
# <a name="speech-and-audio-faqs"></a>FAQ sur la voix et l’audio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Je n’entends aucun son dans mon casque ou le son est lu par mon ordinateur au lieu de mon casque

* Si votre casque immersif n’inclut pas de casque intégré, connectez le casque au jack audio sur le casque. Le Jack est souvent situé juste derrière ou sous le visière ou les glaces du casque. Si vous ne parvenez pas à le trouver, contactez le fabricant de votre casque.
* Certains casques audio ont des boutons physiques pour contrôler le volume. Si l’audio ne fonctionne pas, vérifiez si le volume est désactivé ou désactivé.
* l’Audio passe à votre appareil de lecture Windows par défaut : 
    * Si vous déconnectez le casque
    * Retourner la visière vers le haut
    * Fermer l’application portail de réalité mixte
    * Quand une application n’a pas été utilisée pendant 15 minutes. 
    * vous pouvez modifier ce paramètre dans **Paramètres > la réalité mixte > l’Audio et la parole.**
* Assurez-vous que votre casque audio est branché sur le jack audio. Le casque Acer, en particulier, peut nécessiter plus de soin pour s’assurer que le casque audio est branché.
* Vérifiez que le microphone/casque audio est branché sur le casque et non sur le PC.
* le panneau de configuration du son dans **Paramètres > système > son** affiche uniquement les points de terminaison audio activés, pas les points de terminaison désactivés. Le périphérique audio du casque est désactivé lorsque vous n’êtes pas équipé du casque. Pour le voir, cliquez avec le bouton droit dans le panneau de configuration du son et choisissez « afficher les appareils désactivés ». Le nom de l’appareil est « Realtek USB 2.0 audio », qui peut être renommé dans la page « Properties » (propriétés). Vous pouvez effectuer cette opération pour les onglets lecture et enregistrement.
* Si votre audio ne fonctionne pas dans les applications de réalité mixte, par exemple avec l’application Netflix. cela peut être dû à un problème connu où Windows Mixed Reality n’est pas automatiquement mis à jour pour correspondre à la version du système d’exploitation. pour résoudre ce problème et obtenir la meilleure expérience de réalité mixte, accédez à **Paramètres > Update & Security > Windows Update > vérifier les mises à jour**.

> [!NOTE]
> * Windows Mixed Reality le son spatial fonctionne mieux avec les casques intégrés ou connectés directement à votre casque immersif. Les haut-parleurs ou les écouteurs du PC connectés à l’ordinateur risquent de ne pas fonctionner correctement pour le son spatial.
> * Windows Mixed Reality ne prend pas en charge Bluetooth casques audio.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>J’ai des changements soudains de volume, des données audio perdues ou un bourdonnement

* Certaines applications, comme celles lancées par SteamVR, peuvent perdre du son ou se bloquer lorsque le périphérique audio change quand vous démarrez ou arrêtez le portail de réalité mixte. Pour corriger cela, rouvrez le portail de réalité mixte et redémarrez l’application.
* si un autre périphérique usb multimédia (par exemple, une webcam) partage le même concentrateur usb interne ou externe avec le casque Windows Mixed Reality, la prise jack audio du casque ou le casque peut parfois avoir un signal sonore ou aucun son. Connectez votre casque à un port USB qui utilise un autre concentrateur ou déconnectez/désactivez votre autre périphérique multimédia USB.
* si vous remarquez une forte rafale de bruit de votre casque connecté, le concentrateur USB du PC peut ne pas être en mesure de fournir suffisamment d’alimentation au casque Windows Mixed Reality. Si cela se produit, envoyez un bogue au [Hub de commentaires](/hololens/hololens-feedback) et essayez :
    * retrait des câbles d’extension
    * à l’aide d’un CONCENTRateur USB 3,0 alimenté en externe et dédié
    * un port USB différent sur le PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>mon casque audio Bluetooth ne fonctionne pas comme prévu

Microsoft ne recommande pas l’utilisation de Bluetooth casques audio avec Windows Mixed Reality. Bluetooth les périphériques audio ne fonctionnent pas correctement avec Windows Mixed Reality les expériences audio et spatiales. Bluetooth les casques audio ne peuvent pas prendre en charge l’entrée de microphone et la sortie stéréo en même temps, ce qui vous empêche d’entendre la stéréo ou le son spatial quand vous l’utilisez pour gamechat ou d’autres entrées vocales. Bluetooth les casques audio peuvent également avoir un impact négatif sur votre expérience de contrôleur de mouvement.

## <a name="sound-isnt-coming-from-expected-directions"></a>Le son ne provient pas de la direction attendue

la Windows Mixed Reality à la page d’hébergement inclut un son spatial (audio qui semble provenir des applications situées dans votre foyer). À mesure que vous parcourez et vous rapprochez de chaque application, la direction et le niveau du son seront modifiés pour augmenter le degré de réalisme. Voici quelques raisons possibles pour des directions sonores inattendues :

* si vous ouvrez et lisez de la musique à partir d’une application de musique qui prend en charge les arrière-plans (comme Groove Musique) dans votre foyer, puis que vous ouvrez une expérience de type VR en immersion comme un jeu, le son de l’application music passe du son spatial au stéréo. Il peut sembler plus fort, car il n’y a plus de distance entre vous et le son.
* si vous aviez Cortana activé sur votre ordinateur avant d’utiliser votre casque Windows Mixed Reality, vous risquez de perdre le son de l’espace utilisé sur les applications de votre Windows Mixed Reality. pour résoudre ce problème, désactivez l’option « laissez Cortana répondre à Hey Cortana » dans **Paramètres > Cortana** sur votre bureau avant de lancer Windows Mixed Reality ou activez « Windows Sonic pour casque » :
    1. accédez à la fenêtre de l’application de bureau dans Windows Mixed Reality page d’hébergement.
    2. Cliquez avec le bouton gauche sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez-la dans la liste des périphériques audio.
    3. cliquez avec le bouton droit sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez « Windows Sonic pour casque » dans le menu « configuration de l’orateur ».
    4. Répétez ces étapes pour tous vos périphériques audio (points de terminaison).

## <a name="speech-commands-are-not-working-as-expected"></a>Les commandes vocales ne fonctionnent pas comme prévu

* Pour utiliser les commandes vocales, les paramètres vocaux et linguistiques de votre ordinateur doivent être définis sur une [langue prise en charge dans Windows Mixed Reality](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). pour vérifier vos paramètres de reconnaissance vocale et de langue de Windows, sélectionnez **Paramètres > &** langue > région & langue et Paramètres > & > **langue**.
* Si votre casque n’a pas de microphone intégré, vous devez attacher un casque avec un microphone au casque ou sur votre PC. pour que le commutateur d’entrée microphone soit automatiquement sur votre casque quand vous l’utilisez, accédez à **Paramètres > réalité mixte > Audio et vocale**, puis activez « lorsque j’utilise mon casque, basculez vers casque mic ».
* Certains casques audio ont un bouton physique pour activer et désactiver le microphone. Si les commandes vocales ne fonctionnent pas, vérifiez si votre microphone est muet.
* Les casques audio avec un microphone qui Dangles du câble Earbud ne conviennent pas pour les commandes vocales dans les environnements avec un bruit ambiant.
* la Cortana peut être lente la première fois qu’elle est appelée dans une session de portail de réalité mixte. accédez à **Paramètres > Cortana > communiquez avec Cortana** et assurez-vous que l’option « laissez Cortana répondre à bonjour Cortana » est activée.
* Sur certains PC, le gain de capture vocale par défaut pour votre microphone connecté au casque peut être trop faible. Si vous rencontrez des commandes vocales ou une dictée non fiables, exécutez l’utilitaire de résolution des problèmes de configuration du microphone :
    1. accédez à l’application de bureau dans la Windows Mixed Reality page d’hébergement tout en portant le casque (pour affecter le microphone que vous utilisez pour Windows Mixed Reality).
    2. accédez à **Paramètres > Time & Language > la reconnaissance vocale**.
    3. sélectionnez « Prise en main » dans la section « Microphone ».
    4. Sélectionnez le point de terminaison approprié dans l’Assistant résolution des problèmes.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Je n’ai qu’un seul casque audio et je souhaite l’utiliser à la fois pour le bureau et pour mon casque

Si vous n’avez qu’un seul casque audio et que vous n’avez pas de casque avec casque intégré, connectez le casque audio au PC au lieu du casque. Ensuite, désactivez l’option « Basculer vers l’audio du casque » dans les paramètres du portail de la réalité mixte.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Je souhaite passer à Dolby Atmos for Headphones

les environnements Windows Mixed Reality et ses applications utilisent Windows Sonic pour casque technologie audio spatiale, qui est personnalisée pour les expériences de réalité mixte. d’autres technologies audio spatiales, comme Dolby Atmos for Headphones, peuvent être appliquées pour les applications plein écran comme les jeux SteamVR, mais pas pour les environnements et applications Windows Mixed Reality shell (tels que le placement d’un navigateur web sur le mur de la salle de la falaise ou du gonflant) qui ont été conçus à l’aide de Windows Sonic pour casque son spatial et de ses acoustiques.