---
title: FAQ sur la voix et l’audio
description: Résolution des problèmes vocaux et audio Windows Mixed Reality qui va au-delà de notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, problèmes audio, problèmes vocaux
ms.openlocfilehash: d685190248dd17792f941cf53e3a57499cd3e662
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725890"
---
# <a name="speech-and-audio-faqs"></a>FAQ sur la voix et l’audio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Je n’entends aucun son dans mon casque ou le son est lu par mon ordinateur au lieu de mon casque

* Si votre casque immersif n’inclut pas de casque intégré, connectez le casque au jack audio sur le casque. Le Jack est souvent situé juste derrière ou sous le visière ou les glaces du casque. Si vous ne parvenez pas à le trouver, contactez le fabricant de votre casque.
* Certains casques audio ont des boutons physiques pour contrôler le volume. Si l’audio ne fonctionne pas, vérifiez si le volume est désactivé ou désactivé.
* L’audio bascule sur votre appareil de lecture Windows par défaut : 
    * Si vous déconnectez le casque
    * Retourner la visière vers le haut
    * Fermer l’application portail de réalité mixte
    * Quand une application n’a pas été utilisée pendant 15 minutes. 
    * Vous pouvez modifier ce paramètre dans **paramètres > la réalité mixte > l’audio et la parole.**
* Assurez-vous que votre casque audio est branché sur le jack audio. Le casque Acer, en particulier, peut nécessiter plus de soin pour s’assurer que le casque audio est branché.
* Vérifiez que le microphone/casque audio est branché sur le casque et non sur le PC.
* Le panneau de configuration du son dans **paramètres > système > le son** affiche uniquement les points de terminaison audio activés, pas les points de terminaison désactivés. Le périphérique audio du casque est désactivé lorsque vous n’êtes pas équipé du casque. Pour le voir, cliquez avec le bouton droit dans le panneau de configuration du son et choisissez « afficher les appareils désactivés ». Le nom de l’appareil est « Realtek USB 2.0 audio », qui peut être renommé dans la page « Properties » (propriétés). Vous pouvez effectuer cette opération pour les onglets lecture et enregistrement.
* Si votre audio ne fonctionne pas dans les applications de réalité mixte, par exemple avec l’application Netflix. Cela peut être dû à un problème connu où Windows Mixed Reality n’est pas automatiquement mis à jour pour correspondre à la version du système d’exploitation. Pour résoudre ce problème et obtenir la meilleure expérience de réalité mixte, accédez à **paramètres > mettre à jour & sécurité > Windows Update > Rechercher les mises à jour**.

> [!NOTE]
> * Le son spatial Windows Mixed Reality fonctionne mieux avec les casques intégrés ou connectés directement à votre casque immersif. Les haut-parleurs ou les écouteurs du PC connectés à l’ordinateur risquent de ne pas fonctionner correctement pour le son spatial.
> * Windows Mixed Reality ne prend pas en charge les casques audio Bluetooth.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>J’ai des changements soudains de volume, des données audio perdues ou un bourdonnement

* Certaines applications, comme celles lancées par SteamVR, peuvent perdre du son ou se bloquer lorsque le périphérique audio change quand vous démarrez ou arrêtez le portail de réalité mixte. Pour corriger cela, rouvrez le portail de réalité mixte et redémarrez l’application.
* Si un autre périphérique USB multimédia (par exemple, une webcam) partage le même concentrateur USB interne ou externe avec le casque Windows Mixed Reality, le casque ou le casque audio du casque peut parfois avoir un très bon bruit ou pas de son. Connectez votre casque à un port USB qui utilise un autre concentrateur ou déconnectez/désactivez votre autre périphérique multimédia USB.
* Si vous remarquez une forte rafale de bruit de votre casque connecté, le concentrateur USB du PC peut ne pas être en mesure de fournir suffisamment de puissance au casque Windows Mixed Reality. Si cela se produit, envoyez un bogue au [Hub de commentaires](https://docs.microsoft.com/hololens/hololens-feedback) et essayez :
    * retrait des câbles d’extension
    * à l’aide d’un CONCENTRateur USB 3,0 alimenté en externe et dédié
    * un port USB différent sur le PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mon casque audio Bluetooth ne fonctionne pas comme prévu

Microsoft ne recommande pas l’utilisation de casques audio Bluetooth avec Windows Mixed Reality. Les périphériques audio Bluetooth ne fonctionnent pas correctement avec Windows Mixed Reality et les expériences audio spatiales. Les casques audio Bluetooth ne peuvent pas prendre en charge l’entrée de microphone et la sortie stéréo en même temps, ce qui vous empêche d’entendre la stéréo ou le son spatial quand vous l’utilisez pour gamechat ou d’autres entrées vocales. Les casques audio Bluetooth peuvent également avoir un impact négatif sur votre expérience de contrôleur de mouvement.

## <a name="sound-isnt-coming-from-expected-directions"></a>Le son ne provient pas de la direction attendue

La page d’hébergement de la réalité Windows Mixed inclut un son spatial (audio qui semble provenir des applications situées dans votre foyer). À mesure que vous parcourez et vous rapprochez de chaque application, la direction et le niveau du son seront modifiés pour augmenter le degré de réalisme. Voici quelques raisons possibles pour des directions sonores inattendues :

* Si vous ouvrez et écoutez de la musique à partir d’une application de musique qui prend en charge l’arrière-plan (par exemple, Groove Music) dans votre foyer, puis que vous ouvrez une expérience de VR dans un jeu, le son provenant de l’application musicale est fondu du son spatial au stéréo. Il peut sembler plus fort, car il n’y a plus de distance entre vous et le son.
* Si vous aviez activé Cortana sur votre ordinateur avant d’utiliser votre casque Windows Mixed Reality, vous risquez de perdre le son de l’application dans votre page d’hébergement Windows Mixed Reality. Pour résoudre ce problème, désactivez « laisser Cortana répondre à Hey Cortana » dans **paramètres > Cortana** sur votre bureau avant de lancer Windows Mixed Reality ou activez « Windows Sonic pour casque » :
    1. Accédez à la fenêtre application de bureau dans la page d’hébergement de Windows Mixed Reality.
    2. Cliquez avec le bouton gauche sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez-la dans la liste des périphériques audio.
    3. Cliquez avec le bouton droit sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez « Windows Sonic pour casque » dans le menu « Configuration des conférenciers ».
    4. Répétez ces étapes pour tous vos périphériques audio (points de terminaison).

## <a name="speech-commands-are-not-working-as-expected"></a>Les commandes vocales ne fonctionnent pas comme prévu

* Pour utiliser les commandes vocales, les paramètres vocaux et linguistiques de votre ordinateur doivent être définis sur une [langue prise en charge dans Windows Mixed Reality](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Pour vérifier vos paramètres de langue et de voix Windows, sélectionnez **paramètres > heure & langue > région & langue** et **paramètres > heure & langue**> la parole.
* Si votre casque n’a pas de microphone intégré, vous devez attacher un casque avec un microphone au casque ou sur votre PC. Pour que le commutateur d’entrée microphone soit automatiquement sur votre casque quand vous l’utilisez, accédez à **paramètres > réalité mixte > audio et parole**, puis activez « lorsque j’utilise mon casque, basculez vers casque MIC ».
* Certains casques audio ont un bouton physique pour activer et désactiver le microphone. Si les commandes vocales ne fonctionnent pas, vérifiez si votre microphone est muet.
* Les casques audio avec un microphone qui Dangles du câble Earbud ne conviennent pas pour les commandes vocales dans les environnements avec un bruit ambiant.
* Cortana peut être lente la première fois qu’elle est appelée dans une session de portail de réalité mixte. Accédez à **paramètres > cortana > communiquer avec Cortana** et assurez-vous que l’option « laisser Cortana répondre à Hey Cortana » est activée.
* Sur certains PC, le gain de capture vocale par défaut pour votre microphone connecté au casque peut être trop faible. Si vous rencontrez des commandes vocales ou une dictée non fiables, exécutez l’utilitaire de résolution des problèmes de configuration du microphone :
    1. Accédez à l’application de bureau dans la page d’hébergement Windows Mixed Reality tout en portant le casque (pour affecter le microphone que vous utilisez pour Windows Mixed Reality).
    2. Accédez à **paramètres > heure du & > langue**.
    3. Sélectionnez « prise en main » dans la section « microphone ».
    4. Sélectionnez le point de terminaison approprié dans l’Assistant résolution des problèmes.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Je n’ai qu’un seul casque audio et je souhaite l’utiliser à la fois pour le bureau et pour mon casque

Si vous n’avez qu’un seul casque audio et que vous n’avez pas de casque avec casque intégré, connectez le casque audio au PC au lieu du casque. Ensuite, désactivez l’option « Basculer vers l’audio du casque » dans les paramètres du portail de la réalité mixte.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Je souhaite passer à Dolby Atmos pour casque

Les environnements Windows Mixed Reality et ses applications utilisent la technologie audio spatiale Windows Sonic pour casque, qui est personnalisée pour les expériences de réalité mixte. D’autres technologies audio spatiales, telles que Dolby Atmos pour casque, peuvent être appliquées pour les applications plein écran comme les jeux SteamVR, mais pas pour les applications et les environnements Windows Mixed Reality Shell (tels que le passage d’un navigateur Web au mur de la maison de la falaise ou du gonflant) qui ont été conçus à l’aide de Windows Sonic pour le son spatial et acoustiques.
