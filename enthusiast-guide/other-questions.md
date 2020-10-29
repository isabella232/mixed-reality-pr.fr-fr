---
title: Autres questions
description: Résolution des problèmes avancés de Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, réalité mixte, réalité virtuelle, VR, MR, dépannage, erreurs, aide, support, désinstallation de Windows Mixed Reality, langues prises en charge
appliesto:
- Windows 10
ms.openlocfilehash: a8a035a4d113a0a53f41079709660f65bfa278a0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680331"
---
# <a name="other-questions"></a>Autres questions

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Mon pilote graphique n’est pas pris en charge (j’obtiens des erreurs de défaillance du pilote Graphics).

Recherchez et exécutez « dxdiag » :
1.  Si le résultat est « Rendering de base », le pilote Graphics n’est pas installé. Pour résoudre ce problème :
    * Accédez à **Device Manager > Action > Rechercher les modifications matérielles** .
    * Utilisez Windows Update pour mettre à jour le pilote.
    * Si cela ne résout pas le problème, accédez au site Web du fabricant et installez la dernière mise à jour du pilote. 
    * Si une mise à jour n’est pas disponible pour votre GPU, WMR peut ne pas être pris en charge sur votre appareil. Si vous pensez que c’est le cas, contactez le [support technique](https://support.microsoft.com).
2.  Si vous recevez un « WDDM 2,1 » ou une version antérieure, le pilote Graphics est installé, mais il peut ne pas être la version la plus récente. Pour récupérer la version la plus récente :
    * Utilisez Windows Update pour mettre à jour le pilote.
    * Si cette mise à jour ne résout pas le problème, accédez au site Web du fabricant et installez la dernière mise à jour du pilote. 
    * Si une mise à jour n’est pas disponible pour votre GPU, WMR peut ne pas être pris en charge sur votre appareil. Si vous pensez que c’est le cas, contactez le [support technique](https://support.microsoft.com).
    
Si le programme d’installation de Windows Mixed Reality indique que votre carte graphique ne répond pas aux exigences et que vous pensez qu’elle le fait, vérifiez que votre casque est branché à la bonne carte.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>Ma mise à jour du microprogramme Samsung Odyssey ou Odyssey + du casque est bloquée.

Samsung possède et publie les mises à jour du microprogramme du casque fournies par le biais de ses applications « Samsung HMD Odyssey Setup » et « Samsung HMD Odyssey + Setup » Device Companion. Pour plus d’informations et pour obtenir de l’aide sur les problèmes de mise à jour du microprogramme Samsung, contactez le service client Samsung.

Si le processus de mise à jour du microprogramme est bloqué et qu’il n’y a pas eu de progression depuis plus de cinq minutes :
* Débranchez temporairement tous vos autres périphériques USB et recommencez la mise à jour du microprogramme.
* Connectez votre casque Samsung à un port USB 3,0 différent sur votre PC.
* Désactivez et/ou désinstallez les logiciels installés qui peuvent interférer avec les mises à jour du microprogramme, tels que le App Center AORUS du gigaoctet.
* Utilisez un autre PC pour effectuer la mise à jour du microprogramme du casque Samsung.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Comment faire accéder au poste de travail de mon PC en réalité mixte ?
Lancez l’application de bureau dans le bouton casque à partir de **Windows > toutes les applications > Bureau** pour accéder à votre ordinateur de bureau en réalité mixte.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Comment puis-je voir plusieurs analyses en réalité mixte ?
Par défaut, l’application de bureau bascule automatiquement pour afficher l’analyse avec le focus. Si vous souhaitez voir toutes vos analyses en réalité mixte : 
* Cliquez sur l’icône surveiller dans l’angle supérieur gauche de l’application.
* Désactivez « analyse automatique du commutateur ».
* Sélectionnez l’analyse que vous souhaitez afficher.
* Lancez une autre instance de l’application de bureau.
* Sélectionnez l’analyse que vous souhaitez afficher sur cette instance.
* Répétez cette opération pour toutes vos analyses physiques.
Notez que vous devrez resélectionner le moniteur à afficher sur chaque application de bureau chaque fois que vous redémarrez la réalité mixte. 

## <a name="my-desktop-app-only-shows-a-black-screen"></a>Mon application de bureau affiche uniquement un écran noir.
Si votre ordinateur dispose d’un GPU hybride NVIDIA, le problème peut être causé par un appareil NVIDIA exécutant le runtimebroker.exe sur le GPU discret au lieu de l’appareil intégré. Pour résoudre ce problème, suivez ces instructions sous «[Comment faire créer des paramètres de Optimus pour un nouveau programme](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)». pour ajouter C:\windows\system32\runtimebroker.exe et le forcer à s’exécuter sur le processeur « intégré Graphics ». 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mon Wi-Fi ralentit lorsque j’utilise Windows Mixed Reality.

Si vous utilisez une connexion Wi-Fi 2,4 GHz, vos contrôleurs de mouvement peuvent ralentir votre Wi-Fi. Essayez l’une des opérations suivantes :
* Basculez vers une connexion Wi-Fi 5 GHz, le cas échéant. [Plus d’informations](https://support.microsoft.com/en-us/help/4000461)
* Utilisez un adaptateur Bluetooth distinct pour connecter vos contrôleurs de mouvement à votre PC. Voir les [adaptateurs recommandés](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>J’ai reçu un message indiquant qu’il faut brancher et charger mon PC. Pourquoi ?

Si vous utilisez un ordinateur portable, Windows Mixed Reality fonctionne mieux lorsque l’ordinateur est entièrement chargé et branché. 

## <a name="what-is-the-experience-options-setting"></a>Qu’est-ce que le paramètre options d’expérience ?

Ce paramètre ( **paramètres > réalité mixte > affichage du casque > options d’expérience** ) vous permet de modifier les paramètres de performances de Windows Mixed Reality. Cela vous permet de choisir la meilleure expérience pour votre configuration matérielle dans une plage de contenu. Les options disponibles sont les suivantes :
* Automatique : Windows Mixed Reality déterminera la meilleure expérience de votre configuration matérielle. Pour la plupart des gens, c’est le meilleur choix pour commencer.
* 60Hz : définit la fréquence d’actualisation sur 60 Hz et désactive certaines fonctionnalités, telles que la capture vidéo et la version préliminaire dans le portail de réalité mixte.
* 90Hz : définit la fréquence d’actualisation sur 90Hz.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quelles sont les langues prises en charge dans Windows Mixed Reality ?

Windows Mixed Reality est disponible dans les langues suivantes :
* Chinois simplifié (Chine)
* Anglais (Australie)
* Anglais (Canada)
* Anglais (Grande-Bretagne)
* Anglais (États-Unis)
* Français (Canada)
* Français (France)
* Allemand (Allemagne)
* Italien (Italie)
* Japonais (Japon)
* Espagnol (Mexique)
* Espagnol (Espagne)

Vous pouvez utiliser Windows Mixed Reality si votre ordinateur est défini sur une langue différente, mais l’interface s’affiche en anglais (États-Unis), et les commandes vocales et la dictée ne sont pas disponibles. Le clavier à l’écran Windows Mixed Reality est en anglais (États-Unis) uniquement. Pour entrer du texte dans une autre langue, utilisez un clavier physique connecté à votre PC. Vous pouvez également utiliser la dictée dans l’un des langages Windows Mixed Reality pris en charge listés ci-dessus ; sélectionnez simplement microphone sur le clavier à l’écran.

Windows Mixed Reality est également disponible dans les langues suivantes sans commandes vocales ni fonctionnalités de dictée :
* Chinois traditionnel (Taïwan et Hong Kong)
* Néerlandais (Pays-Bas)
* Coréen (Corée)
* Russe (Russie)

## <a name="i-have-questions-about-my-headset-hardware"></a>J’ai des questions sur mon matériel de casque.

Pour plus d’informations sur votre casque, contactez le fabricant. Il peut y avoir un guide produit dans la zone, ou vous pouvez essayer le site Web du fabricant.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Comment faire désinstaller Windows Mixed Reality ?

1. Déconnectez votre casque de votre PC.
2. Fermez le portail Windows Mixed Reality.
2. Accédez à  **démarrer > paramètres > réalité mixte** et sélectionnez Désinstaller.

Quand vous êtes prêt à recommencer à utiliser votre casque, connectez-le et le portail Windows Mixed realer vous guidera tout au long de la configuration.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>J’ai reçu un message « Impossible de terminer la désinstallation de Windows Mixed Reality ».

Certains fichiers, y compris des informations sur votre environnement, peuvent toujours se trouver sur votre ordinateur. Cela peut poser des problèmes si vous décidez de réinstaller Windows Mixed Reality ultérieurement. Vous pouvez supprimer manuellement toutes les informations Windows Mixed Reality restantes de votre PC en modifiant le registre et en utilisant Windows PowerShell pour exécuter des commandes. _Si vous modifiez le registre de manière incorrecte, des problèmes sérieux peuvent survenir. Veillez à suivre ces étapes avec prudence. Pour une protection supplémentaire, sauvegardez votre registre avant de le modifier afin de pouvoir le restaurer en cas de problème._ Pour plus d’informations, consultez [Comment sauvegarder et placer le registre dans Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Pour désinstaller Windows Mixed realing à l’aide de ces commandes :
1. Redémarrez votre PC.
2. Dans la zone de **recherche** , tapez « regedit », puis sélectionnez « Oui ».
3. Supprimez les valeurs de Registre suivantes :
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, puis supprimez « FirstRunSucceeded ».</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>, puis supprimez « PreferDesktopSpeaker » et « PreferDesktopMic ».</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>, puis supprimez « DisableSpeechInput ». Remarque : les éléments de registre de HHKEY_CURRENT_USER doivent être supprimés pour chaque compte d’utilisateur sur le PC qui a utilisé Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>, puis supprimez « DeviceID » et « mode ».</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, puis supprimez « OnDeviceLearningCompleted ».</li> 
   </ul>
4. Supprimez les clés de Registre suivantes : <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. Fermez l’éditeur du Registre.
6. Accédez à **C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** et supprimez « RoomBounds.jssur ». Répétez cette procédure pour chaque utilisateur qui a utilisé Windows Mixed Reality.
7. Ouvrez l’invite de commandes admin et accédez à **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . Supprimez le contenu du dossier « HeadTracking Data » (mais pas le dossier lui-même).
8. Tapez « PowerShell » dans la « zone de recherche », cliquez avec le bouton droit sur « Windows PowerShell », puis sélectionnez « Exécuter en tant qu’administrateur ».
9. Dans Windows PowerShell : <ul>
   <li>À l’invite de commandes, copiez et collez <b>DISM/Online/Get-Capabilities</b>, puis appuyez sur entrée.</b></li> 
   <li>Copiez l’identité de capacité qui commence par Analog. holographique. Desktop (si elle n’est pas présente, cela signifie que cet élément n’est pas installé. Dans ce cas, passez à l’étape 10).</li> 
   <li>Copiez et collez l’invite de commandes suivante, puis appuyez sur entrée : <b>DISM/Online/Remove-Capability/CapabilityName : l’identité de capacité copiée lors de la dernière étape</b></li>
   </ul>
10. Redémarrez votre PC.

