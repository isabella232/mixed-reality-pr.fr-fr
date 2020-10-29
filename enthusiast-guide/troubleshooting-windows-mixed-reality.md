---
title: Résolution des problèmes de Windows Mixed Reality
description: Résolution des problèmes avancés de Windows Mixed realisation qui va au-delà de notre documentation de support technique standard.
ms.topic: article
keywords: Windows Mixed Reality, la réalité mixte, la réalité virtuelle, VR, MR, dépannage, erreurs, aide, support
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680275"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>Résolution des problèmes de Windows Mixed Reality (FAQ)

## <a name="understanding-common-installation-error-messages"></a>Description des messages d’erreur d’installation courants

### <a name="your-pc-cant-run-windows-mixed-reality"></a>« Votre ordinateur ne peut pas exécuter Windows Mixed Reality »

Votre ordinateur ne répond pas à la [Configuration minimale requise](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) pour exécuter Windows Mixed Reality. Cela peut être dû au fait que l’installation matérielle de l’ordinateur n’est pas compatible avec Windows Mixed Reality ou que vous devez effectuer une [mise à jour vers la dernière version de Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq). 

Notez que Windows Mixed Reality requiert un pilote de carte graphique prenant en charge au moins WDDM 2,2. Assurez-vous que vous disposez de la dernière mise à jour du pilote auprès du fabricant. Si le programme d’installation de Windows Mixed Reality indique que votre carte graphique ne répond pas aux exigences et que vous pensez qu’elle le fait, vérifiez que votre casque est branché à la bonne carte.

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>« Vous êtes presque là : ce PC ne répond pas à la configuration minimale requise pour exécuter Windows Mixed Reality »

Votre PC ne répond pas à la [Configuration minimale requise](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) pour la meilleure expérience dans Windows Mixed Reality. Votre ordinateur peut être en mesure d’exécuter un casque immersif, mais il peut ne pas être en mesure d’exécuter certaines applications ou peut présenter des problèmes de performances.

Notez que Windows Mixed Reality requiert un pilote de carte graphique prenant en charge au moins WDDM 2,2. Assurez-vous que vous disposez de la dernière mise à jour du pilote auprès du fabricant. Si le programme d’installation de Windows Mixed Reality indique que votre carte graphique ne répond pas aux exigences et que vous pensez qu’elle le fait, vérifiez que votre casque est branché à la bonne carte.

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>«Avant de pouvoir configurer Windows Mixed Reality, votre administrateur doit l’activer pour votre organisation. En savoir plus»

Vous êtes probablement sur un réseau géré par l’entreprise et votre organisation utilise Windows Server Update Services (WSUS) ou d’autres stratégies qui peuvent bloquer le téléchargement. Contactez le service informatique ou l’administrateur système de votre organisation pour [activer Windows Mixed Reality](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>« Nous n’avons pas pu télécharger le logiciel de réalité mixte » ou « raccrocher pendant le téléchargement »

* Parfois, une mise à jour en attente peut bloquer le téléchargement de logiciels de la réalité mixte. Accédez à **paramètres > mettre à jour & sécurité > Windows Update** et vérifiez que Windows Update est activé. Ensuite, téléchargez et installez les mises à jour en attente d’installation. Si vous recevez une erreur avec Windows Update lorsque vous tentez d’effectuer ces étapes, cliquez [ici](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors).
* Assurez-vous que votre ordinateur est connecté à Internet et qu’il dispose d’au moins 2 Go d’espace de stockage disponible. Vérifiez l’état de votre réseau à l’adresse : **paramètres > réseau & Internet > État** . Si vous ne parvenez pas à vous connecter à Internet, cliquez [ici](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) pour obtenir de l’aide.  
* Redémarrez votre ordinateur et réessayez. 

Si les solutions précédentes ne fonctionnent pas, essayez :
* Si votre connexion réseau Wi-Fi est définie sur [contrôlé](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq), modifiez-la en la définissant sur non contrôlé. Pour désactiver une connexion limitée, accédez à : **settings > Network & Internet > status > modifier les propriétés de connexion > définir comme connexion limitée** et sélectionner « désactivé ».  
* Si vous avez récemment installé une mise à jour, cela peut entraîner des problèmes. Nous vous déconseillons de supprimer les mises à jour installées, notamment les mises à jour de sécurité qui sécurisent votre ordinateur, mais la suppression de la mise à jour la plus récente peut vous aider à déterminer la source du problème. Pour ce faire : 
    * Accédez à **paramètres > mettre à jour & sécurité > afficher l’historique des mises à jour installées > désinstaller les mises à jour**
    * Sélectionnez la dernière mise à jour installée et désinstallez.
    * À l’invite « voulez-vous vraiment désinstaller cette mise à jour ? » répondez « Oui ». Si vous recevez une erreur lorsque vous tentez d’effectuer ces étapes, cliquez [ici](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors). 
    * Redémarrez votre ordinateur et réessayez. 
    * Si Windows Mixed Reality s’installe correctement, réinstallez les dernières mises à jour sous **paramètres > Windows Update > Rechercher les mises à jour** et voir si Windows Mixed Reality continue de fonctionner. S’il ne s’installe pas correctement, réinstallez les dernières mises à jour et contactez le support Windows. 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>« Une erreur s’est produite et nous n’avons pas pu démarrer Windows Mixed Reality »
* Débranchez les deux câbles de votre casque du PC.
* Redémarrez le PC.
* Accédez à **paramètres > mettre à jour & sécurité > Windows Update** et assurez-vous que Windows Update est activé. Ensuite, téléchargez et installez les mises à jour en attente.
* Reconnectez votre casque au PC, puis recommencez l’installation.

Si les étapes ci-dessus ne fonctionnent pas, essayez de désinstaller puis de réinstaller Windows Mixed Reality :
* Accédez à **paramètres > réalité mixte > désinstaller** et sélectionnez Désinstaller. 
* Redémarrez votre PC. 
* Pour recommencer le processus d’installation, il vous suffit de brancher votre casque sur votre PC.
    

## <a name="troubleshooting-setup-questions"></a>Résolution des problèmes de configuration 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Mon contrôleur Xbox ne fonctionne pas avec Windows Mixed Reality.

* Assurez-vous que votre contrôleur est allumé, entièrement débité et connecté au PC.
* Remplacez les piles du contrôleur.
* Si vous utilisez un contrôleur Bluetooth, accédez à **paramètres > appareils > Bluetooth & d’autres périphériques** sur votre ordinateur et assurez-vous qu’ils sont associés (ils doivent être listés sur la page).

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>Je ne peux pas diriger d’entrée (contrôleurs, boîtier de roulette, souris/clavier) dans Windows Mixed Reality.

Lorsque vous placez sur votre casque, l’entrée doit être automatiquement basculée vers votre expérience de réalité mixte via le capteur de présence de votre casque. Une barre bleue doit apparaître sur votre bureau :

![Bureau Windows avec entrée dirigée vers le casque](images/1050px-windowsy.png)

Si l’entrée n’est pas automatiquement basculée, vous devez basculer manuellement l’entrée sur votre casque. Pour ce faire, vous pouvez taper la **touche Windows + Y** sur votre clavier (et la même pour basculer l’entrée vers le bureau).

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>Lorsque je branche mon casque, rien ne se passe. Le portail de réalité mixte n’est pas ouvert.
Portail de réalité mixte, l’application qui vous guide à travers le programme d’installation de Windows Mixed Reality est conçue pour s’ouvrir automatiquement lorsque vous branchez un casque compatible. S’il ne s’ouvre pas, accédez à démarrer et tapez « portail de réalité mixte » dans la zone de recherche pour ouvrir l’application à partir de cet emplacement. Si vous ne trouvez pas de portail de réalité mixte, cela peut signifier que vous devez effectuer une [mise à jour vers la dernière version de Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Comment faire choisir entre « assis et debout » et « toutes les expériences » ?

Si vous choisissez « assis et debout », lors de l’installation du casque ou plus tard, vous utiliserez votre casque sans limite. Vous pouvez vous asseoir en position ou en haut, mais vous devrez sinon rester à un même endroit, car vous n’aurez pas de limite pour vous aider à éviter les obstacles physiques. Certaines applications peuvent être conçues pour fonctionner avec une limite. vous ne pourrez peut-être pas les utiliser ou vous n’aurez peut-être pas la même expérience si vous les utilisez sans limite. Consultez « qu’est-ce qu’une limite et pourquoi dois-je en créer une ? » ci-dessous pour plus d’informations.

Si vous choisissez « toutes les expériences », vous configurez une limite et vous pouvez utiliser les applications et les expériences qui fonctionnent avec une limite, ainsi que celles qui n’en ont pas besoin. 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>L’apprentissage de la réalité mixte n’a pas été exécuté lors du premier lancement et je suis allé directement dans le Windows Mixed Reality.

Vous pouvez réexécuter l’expérience d’apprentissage en suivant les [étapes de réexécution](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 


## <a name="boundary-setup-and-other-questions"></a>Configuration des limites et autres questions

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>Qu’est-ce qu’une limite et pourquoi dois-je en créer une ?

Une limite définit la zone dans laquelle vous pouvez vous déplacer pendant que vous enportez votre casque d’immersion Windows Mixed Reality. Étant donné que vous ne pouvez pas voir votre environnement lorsque vous utilisez votre casque, il est important de créer une limite pour vous aider à éviter les obstacles. La limite ressemble à un contour blanc à l’intérieur de la réalité mixte et s’affiche lorsque vous y arrivez. Quand vous le voyez, ralentissez vos mouvements et évitez de franchir la limite ou d’étendre vos membres au-delà.

La zone à l’intérieur de la limite doit être libre de mobilier, des luminaires faiblement suspendus, des ventilateurs de plafond, etc. vous ne serez pas en mesure de vous heurter à quoi que ce soit. En [savoir plus sur l’intégrité et la sécurité dans Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

### <a name="how-do-i-create-a-boundary"></a>Comment faire créer une limite ?

Quand vous configurez votre casque pour la première fois, l’application d’installation (portail de réalité mixte) vous guide tout au long des étapes de création d’une limite. Mais vous pouvez en créer un à tout moment. Pour ce faire :
1. Sélectionnez **démarrer > portail de réalité mixte** sur votre bureau. 
2. Ouvrez « menu ».
3. Sélectionnez « exécuter le programme d’installation » pour créer une nouvelle limite.

Si quelqu’un d’autre utilise votre casque, assurez-vous qu’ils comprennent la limite et comment l’utiliser. Si vous déplacez votre casque vers un nouvel emplacement, vous devez configurer une nouvelle limite qui fonctionne pour cet espace.

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>J’obtiens un message d’erreur lorsque j’essaie de créer une limite.

* Ne vous trouvez pas trop près d’un mur ou d’une autre obstruction lors de la création d’une limite.
* Veillez à conserver votre casque à la hauteur de la taille et à faire face à votre ordinateur pendant que vous tracez la limite.
* Assurez-vous que le capteur n’est pas bloqué et qu’il y a suffisamment de lumière.
* L’espace que vous tracez doit être supérieur à trois mètres carrés.
* L’espace ne doit pas être trop grand ou trop complexe. Collez-vous à une forme géométrique simple sans grand nombre de torsions et de virages.
* Ne vous contentez pas de traverser votre propre chemin d’accès lorsque vous effectuez le suivi.
* Si vous êtes bloqué dans un coin, recommencez.

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>Pendant le démarrage de la réalité mixte, je suis coincé à l’étape « faire pivoter le côté, puis à l’étage ».

Cette étape permet à votre casque de reconnaître votre espace et de restaurer un étage virtuel et une limite existants. Lorsque vous placez sur votre casque, le processus d’analyse peut prendre jusqu’à 10 secondes. Une fois l’opération terminée, vous serez dans la page d’hébergement de la réalité mixte ou vous serez invité à configurer à nouveau votre limite.

Si le processus d’analyse prend plus de 10 secondes, il peut y avoir un problème avec le capteur de proximité dans le casque :
1. Vérifiez que la vignette a été retirée du capteur de proximité. Le capteur de proximité se trouve à l’intérieur du casque, à peu près là où se trouve le centre de votre stress.
2. Vérifiez que votre capteur de proximité bascule entre les entrées sur votre casque : avec votre doigt, recouvrez et dévoilez le capteur de proximité plusieurs fois pour vérifier que l’entrée bascule sur le casque. Vous devez voir la bannière de **touche Windows + Y** en haut de votre PC. Vous pouvez basculer manuellement l’entrée sur le casque à tout moment en tapant la **touche Windows + Y** sur votre clavier.

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>Je vois un message indiquant que ma limite est introuvable. Que dois-je faire ?

Windows Mixed Reality peut avoir des difficultés à identifier vos limites existantes. Vous pouvez créer une nouvelle limite ou vous pouvez utiliser votre appareil en mode « assiste et debout ». 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Je vois un message indiquant « perte de suivi » ou « nous n’avons pas de limite pour cet espace ».

Vous devez créer une nouvelle limite. Pour ce faire :
* Sélectionnez **démarrer > portail de réalité mixte** .
* Sélectionnez « exécuter le programme d’installation ».

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>La limite est toujours visible. Comment faire disparaître ?

La limite s’affiche lorsque vous y êtes proche. Si votre limite comprend des sections qui ont une forme étroite ou irrégulière, vous pouvez vous y retrouver et la faire apparaître, plus souvent que vous le souhaitez. Pour résoudre ce problème, essayez de recréer votre limite à l’aide d’une forme plus grande et plus normale. Pour ce faire :
* Sélectionnez **démarrer > portail de réalité mixte** .
* Sélectionnez « exécuter le programme d’installation ».

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>Comment puis-je désactiver temporairement la limite ?

* Sélectionnez **démarrer > portail de réalité mixte** .
* Ouvrez « menu ». 
* Transformez « limite » en « désactivé ». Veillez à rester à un seul endroit lorsque la limite est désactivée.


## <a name="problems-in-windows-mixed-reality-home"></a>Problèmes dans la page d’hébergement de Windows Mixed Reality

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>Mes contrôleurs ne s’affichent pas dans ma page d’hébergement Windows Mixed Reality.

Assurez-vous que vos contrôleurs possèdent des piles complètes et qu’ils sont correctement couplés à l’aide de Bluetooth. Essayez de mettre les contrôleurs hors tension et à l’aide du bouton Windows. Si vous ne voyez toujours pas vos contrôleurs, essayez le jumelage et recouplez chaque contrôleur dans le menu paramètres sous **appareils > Bluetooth** .

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>L’étage de ma page d’hébergement Windows Mixed Reality ne semble pas être à la hauteur correcte ou est incliné.

Sélectionnez **démarrer > ajustement** de la salle qui se lance une fois que vous avez placé l’application dans le monde entier pour apporter des modifications tout en portant votre casque. Dans cette application, vous serez invité à utiliser le pavé tactile (contrôleur de mouvement) ou le panneau de direction (boîtier de commande) pour ajuster la hauteur du plancher. Lorsque l’étage est correct, utilisez le bouton Windows pour revenir à votre page d’hébergement.

### <a name="my-headset-has-stopped-tracking"></a>Mon casque a arrêté le suivi.

Assurez-vous que les lumières sont activées et qu’il n’y a aucun obstacle aux caméras de suivi à l’intérieur de votre casque. Si le suivi est perdu, la reprise peut prendre quelques secondes. Si le suivi ne reprend pas, essayez de redémarrer le portail Windows Mixed Reality. Pour plus d’informations, consultez suivi de la [résolution des problèmes](tracking.md) .

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>Je ne peux pas afficher un aperçu de ce que je vois dans mon casque sur mon bureau.

Le portail de réalité mixte a un bouton de **lecture** en bas de l’écran qui vous permet d’afficher un aperçu de ce que vous voyez dans votre casque sur l’écran de votre bureau. Toutefois, pour des raisons de performances, cette fonctionnalité n’est disponible que sur les PC exécutant Windows Mixed Reality ultra (90Hz).

## <a name="headset-connectivity-issues"></a>Problèmes de connectivité du casque

### <a name="my-computer-does-not-have-an-hdmi-port"></a>Mon ordinateur n’a pas de port HDMI.
Si votre ordinateur ne possède pas de port HDMI, mais dispose d’un port DisplayPort (DP), mini-DisplayPort (miniDP) ou USB-c (USB-C) pour sortir de la vidéo, vous devrez peut-être utiliser un [adaptateur pris en charge](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>Puis-je utiliser des câbles d’extension USB ou HDMI avec des casques Windows de réalité mixte ?
Les casques pour Windows Mixed Reality ne prennent pas officiellement en charge l’utilisation de câbles d’extension USB ou HDMI. L’utilisation de ces câbles peut avoir un impact significatif sur votre expérience de réalité mixte en raison des variations de l’intégrité des signaux et de la puissance du bus entre le contrôleur USB de votre PC et le casque de la réalité mixte. Si le casque affiche brièvement un écran bleu, puis que le portail de la réalité noir et mixte redémarre ou complète les énumérations en cours d’utilisation, ou si le casque audio est réduit ou devient incorrect, ou si le casque scintille entre le noir et l’affichage correct, essayez d’utiliser votre casque sans câble d’extension.

### <a name="i-am-getting-a-check-your-display-cable-error"></a>J’obtiens une erreur « vérifier votre câble d’affichage ».

* Si vous utilisez des adaptateurs pour connecter votre casque à votre ordinateur, assurez-vous qu’ils prennent en charge Windows Mixed Reality. Essayez également de connecter l’adaptateur au PC avant de connecter le HMD à l’adaptateur.
* Si votre ordinateur dispose de graphiques intégrés et discrets, assurez-vous que vous utilisez le port HDMI sur votre carte graphique active. Dans certains cas, cela peut signifier que vous devez connecter l’affichage de votre PC à un port non HDMI.
* Si votre ordinateur dispose de graphiques intégrés et discrets, et que la carte graphique intégrée est plus ancienne et ne prend pas en charge Windows Mixed Reality, essayez de désactiver le GPU intégré.
* Connectez un moniteur PC au port HDMI de votre PC. Assurez-vous que vos pilotes graphiques sont à jour. Téléchargez et installez les versions de AMD, Nvidia ou Intel directement, car elles seront probablement plus récentes que celles publiées sur Windows Update.
* Veillez à brancher le câble HDMI de votre casque sur un port de **sortie HDMI** sur votre ordinateur, et non sur un port HDMI.
* Windows n’est peut-être pas en mesure de détecter la connexion du câble d’affichage. Ouvrez la Device Manager et vérifiez si le casque est listé sous « moniteurs ». Si ce n’est pas le cas, sélectionnez **Action > Rechercher les modifications matérielles** . 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Je vois un message indiquant « placer sur votre casque », même si j’ai mon casque.

Lorsque vous placez sur votre casque, Windows Mixed realisation peut nécessiter quelques secondes pour recharger votre espace. Si ce message ne disparaît pas, assurez-vous que l’autocollant de protection a été retiré du capteur de proximité, qui se trouve à l’intérieur du casque entre les lentilles. Si cela ne résout pas le problème, contactez le fabricant de votre casque.

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Un message indique « Connectez votre casque », même si j’ai branché mon casque.

1. Assurez-vous que les câbles USB et HDMI du casque sont connectés aux ports corrects sur votre ordinateur. Voici comment identifier les ports appropriés :
    * Les ports USB 3,0 ont un logo spécial avec une marque « SS » (indiquant « supervitesse »). La pièce intérieure du port est normalement bleue, tandis que les ports USB 2,0 plus anciens sont généralement noirs ou blancs à l’intérieur.
    * Si votre ordinateur est équipé de deux ports HDMI, utilisez celui qui se connecte à la carte graphique, et non la carte mère de l’ordinateur. Il n’est pas toujours évident de savoir qui, bien que les ports discrets se trouvent souvent dans un emplacement d’extension sur l’ordinateur. Si vous essayez d’utiliser un port et qu’il ne fonctionne pas, essayez l’autre.
2. Débranchez et branchez les câbles USB et HDMI de votre casque pour vous assurer qu’ils sont connectés en toute sécurité. Lorsque vous branchez le câble USB, essayez de ne pas interrompre l’insertion du câble USB.
3. Ouvrez Device Manager et vérifiez que votre casque est listé sous « périphériques de réalité mixte ». Double-cliquez sur votre casque sous « appareils de réalité mixte » et vérifiez que l’état de l’appareil indique « ce périphérique fonctionne correctement ». Les points d’exclamation jaunes sur les appareils répertoriés dans Device Manager indiquent les erreurs signalées par les périphériques connectés à votre PC.
    * Si « capteurs Hololens » est listé avec un point d’exclamation jaune dans Device Manager, double-cliquez sur l’appareil. Si vous voyez un **«Code 10 : les pilotes de cet appareil ne sont pas installés. Il n’y a pas de pilotes compatibles pour cet appareil»** , suivez les [instructions](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) pour installer manuellement le pilote du casque.
    * Si vous utilisez plusieurs casques de réalité mixte sur votre ordinateur et que vous avez préalablement installé le pilote du casque de la réalité mixte, dans certains cas, la mise à jour manuelle du pilote peut s’appliquer uniquement au casque connecté à la fois et non à vos autres casques. Dans ce cas, vous verrez **«Code 31 : cet appareil ne fonctionne pas correctement car Windows ne peut pas charger les pilotes requis pour cet appareil. (Code 31). Le message ALPC demandé n’est plus disponible** dans Device Manager. Dans Device Manager, cliquez avec le bouton droit sur votre casque sous « appareils de réalité mixte », puis sélectionnez « désinstaller l’appareil ». Sélectionnez OK pour confirmer, puis débrancher et rebrancher votre casque.
4. Si vous voyez une énumération partielle du casque (une série de périphériques USB sont énumérés, mais rien sous les « casques de réalité mixte » dans Device Manager), essayez un concentrateur USB 3,0 en externe.
5. Accédez au site Web du fabricant du casque et mettez à jour les pilotes et le microprogramme de votre casque.
6. Connectez votre casque à un autre PC et ouvrez Device Manager. Même si ce PC n’est pas entièrement compatible avec Windows Mixed Reality, vous pouvez vérifier si votre casque est énuméré. Si votre casque n’effectue pas d’énumération sur plusieurs PC, il peut y avoir un problème matériel.

**Remarque pour les utilisateurs de surface :** Les versions antérieures du logiciel de mise à jour du microprogramme du concentrateur USB surface Dock et surface sont incompatibles avec les casques de réalité mixte. Si vous obtenez un message « Connectez votre casque » sur un PC surface, vérifiez si des appareils signalent une **Erreur « code 10 : l’appareil ne peut pas démarrer »** dans Device Manager. Dans ce cas, [supprimez le pilote en conflit](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Vous ne devez effectuer cette opération qu’une seule fois.

**Remarque pour les utilisateurs de Windows 10 N :** Si votre PC exécute Windows 10 N, vous verrez une **Erreur « code 28 : la classe d’installation n’est pas présente ou n’est pas valide »** dans Device Manager après avoir branché votre casque de réalité mixte. Les éditions N de Windows 10 ne sont pas prises en charge par Windows Mixed Reality. Pour plus d’informations, suivez ces [instructions](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) .

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un message indique « vérifier votre câble USB » ou « vitesse USB insuffisante ».

* Assurez-vous que vous utilisez un port USB 3,0 pris en charge sur votre ordinateur :
    * Assurez-vous que le câble USB de votre casque est branché.
    * Exécutez l’application de [vérification du PC Windows Mixed Reality](https://aka.ms/pccheckapp) pour vérifier que le contrôleur USB 3,0 de votre PC est pris en charge.
    * Essayez chacun des autres ports USB 3,0 sur votre PC. Certains PC disposent de plusieurs contrôleurs USB 3,0.
    * Déconnectez temporairement tous les périphériques USB connectés à votre ordinateur et connectez-vous uniquement à votre casque.
    * Sur les PC personnalisés, même si un port peut être marqué comme port USB 3,0, il peut être connecté à un contrôleur USB 2,0. Une fois votre casque connecté, ouvrez Device Manager, recherchez et cliquez sur l’un des appareils énumérés à partir de votre casque, puis accédez à **afficher > appareils par connexion** .
* Essayez votre casque sur un autre PC. Si cet autre PC n’est pas entièrement compatible avec Windows Mixed Reality, vérifiez Device Manager pour voir si le message « vitesse USB insuffisante » s’affiche. Si votre casque n’énumère pas correctement sur plusieurs PC, votre casque est peut-être défectueux.

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>Le portail de réalité mixte n’a pas été lancé automatiquement après avoir branché mon casque.

Le casque n’a peut-être pas été détecté correctement en raison d’un problème sous-jacent. Essayez de lancer le portail de réalité mixte manuellement et recherchez les messages d’erreur qui s’affichent. 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mon casque a cessé de fonctionner après avoir placé mon PC en mode veille prolongée, ou lors du redémarrage de mon PC avec mon casque connecté.

1. Ouvrez Device Manager et vérifiez que votre casque est listé sous « périphériques de réalité mixte ».
2. Double-cliquez sur votre casque sous « appareils de réalité mixte » et vérifiez que l’état de l’appareil indique « ce périphérique fonctionne correctement ».
3. Si vous voyez une erreur « code 43 » indiquant que l’appareil a cessé de fonctionner, ou si votre casque n’est pas listé sous « appareils de réalité mixte », débranchez et rebranchez le câble USB de votre casque. Microsoft étudie un éventuel problème d’interopérabilité entre les logiciels et les pilotes, ce qui peut entraîner cette erreur. Ce problème affecte un petit nombre de PC et devrait être résolu dans une prochaine mise à jour du pilote du casque de la réalité mixte.

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mon casque fait en sorte que mon PC génère une vérification de bogue (écran bleu) lorsque je mets mon PC en veille ou lorsqu’il est en mode veille prolongée.

Microsoft étudie un problème potentiel d’interopérabilité entre les logiciels et les pilotes, ce qui peut entraîner un petit nombre de PC pouvant générer une vérification de bogue « 9F » (écran bleu) quand le PC est mis en veille ou en mode veille prolongée avec le casque attaché. Ce problème devrait être résolu dans une prochaine mise à jour du pilote du casque de la réalité mixte.

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Le pilote du casque n’a pas été installé automatiquement lorsque je suis connecté au casque.

Sur les nouveaux PC, ou sur les PC équipés d’une copie de Windows 10 récemment installée, le pilote de casque peut être mis en file d’attente derrière d’autres mises à jour Windows et ne peut pas être installé immédiatement. Si vous disposez d’une édition « N » de Windows, vous devrez basculer vers une édition standard de Windows 10 pour utiliser Windows Mixed Reality. Pour l’installer manuellement :

1. Accédez à **démarrer > Device Manager** et Regardez sous « autres appareils » pour un appareil « capteurs hololens » avec un point d’exclamation jaune : ![ affichage des capteurs hololens Device Manager](images/hololenssensors.png)
2. Cliquez avec le bouton droit sur l’appareil et sélectionnez Propriétés. Si les propriétés de l’appareil qui lisent **les pilotes de cet appareil ne sont pas installées (code 28)** , fermez la fenêtre et poursuivez. S’il existe un autre message, suivez les étapes de dépannage sur le reste de cette page.
![Code 28 des capteurs HoloLens dans Device Manager](images/code28.png)
3. Cliquez à nouveau avec le bouton droit sur l’appareil et sélectionnez « mettre à jour les pilotes... ». puis « rechercher automatiquement les mises à jour logicielles de pilotes » une fois l’appareil mis à jour, vous devriez voir votre casque répertorié sous « appareils de réalité mixte » dans Device Manager : l' ![ appareil de réalité mixte apparaît dans Device Manager](images/mixedrealitydevices.png)

Si l’installation manuelle ne fonctionne pas, ou si vous ne trouvez pas le pilote sous autres périphériques, vous devez probablement désinstaller le pilote existant et le réinstaller. Pour ce faire :
1. Accédez à **démarrer > Device Manager** et Regardez sous « appareils de réalité mixte » pour votre casque. L’état de l’appareil doit indiquer que « le périphérique fonctionne correctement ».
2. Cliquez avec le bouton droit sur l’appareil, puis sélectionnez « désinstaller l’appareil ».
3. Dans la nouvelle fenêtre contextuelle qui s’affiche, activez la case à cocher « Supprimer le logiciel du pilote pour cet appareil », puis sélectionnez « Désinstaller ».
4. Quand cela se termine, débranchez le casque de votre ordinateur et rebranchez-le. Windows Update va maintenant télécharger et installer un nouveau pilote.

### <a name="troubleshooting-flowchart"></a>Organigramme de résolution des problèmes

![Connectez votre casque/Vérifiez votre câble USB](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>Problèmes d’affichage du casque de la réalité mixte ##

### <a name="my-headset-displays-are-black"></a>Mon casque s’affiche en noir.

* Vérifiez les performances et la stabilité de votre ordinateur :
    * Utilisez le gestionnaire des tâches pour vérifier si des processus sont atteignant l’UC, le GPU et/ou les lecteurs de disque de votre PC.
    * Examinez les journaux des applications et des événements système dans Windows (à l’aide de observateur d’événements) pour voir si vous avez une application qui se bloque souvent et génère des rapports Rapport d’erreurs Windows (WER).
    * Vérifiez Windows Update pour vous assurer que votre version de Windows est à jour. Vous devrez peut-être sélectionner plusieurs fois « Rechercher des mises à jour ».
* Vérifier la stabilité de l’application et du jeu :
    * Assurez-vous que votre ordinateur répond à la configuration minimale requise pour exécuter une application/un jeu qui ne fonctionne pas correctement.    
    * Assurez-vous que la version du pilote GPU est récente et recherchez les nouveaux problèmes de performances et de compatibilité et les régressions sur les nouveaux pilotes.
    * Si vous utilisez des applications et des jeux SteamVR, assurez-vous que SteamVR et la réalité mixte Windows pour les composants SteamVR sont à jour.
* Vérifier la compatibilité des adaptateurs HDMI :
    * Assurez-vous que le câble HDMI est branché.
    * Si vous utilisez un adaptateur HDMI (par exemple, un mini-Adaptateur DisplayPort pour HDMI), assurez-vous qu’il est compatible avec Windows Mixed Reality. L’adaptateur doit prendre en charge l’HDMI 2,0 et il existe de nombreux adaptateurs plus anciens qui prennent uniquement en charge 1080p. Consultez [adaptateurs recommandés pour Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
    * La commande de plug-in peut être importante. Connectez l’adaptateur HDMI à votre ordinateur avant de connecter le casque à la carte, en particulier si vous utilisez un adaptateur USB-C à HDMI. 
    * Essayez de supprimer les câbles d’extension si vous les utilisez.
* Vérifier la compatibilité de la carte graphique et du pilote :
    * Essayez le port HDMI de votre PC à l’aide d’un moniteur d’ordinateur. Certains PC peuvent avoir plus d’un port HDMI, et tous ne peuvent pas être actifs.
    * Si votre ordinateur dispose à la fois d’une unité de traitement graphique (iGPU) et d’une unité de traitement graphique (dGPU) discrètes, assurez-vous que vous êtes connecté au port HDMI de votre dGPU.<br> ![Ports HDMI](images/HP_HDMI_Ports_s.png)
    * Vérifiez la version de votre pilote GPU. Assurez-vous qu’elle est récente, mais faites attention aux nouveaux problèmes de performances et de compatibilité et aux régressions sur les nouveaux pilotes.
    * Si vous utilisez la réalité mixte sur un ordinateur portable et que vous avez installé un pilote graphique plus récent à partir du site Web du fabricant de la carte graphique, essayez de rétrograder vers le pilote de carte graphique le plus récent fourni sur le site Web du fabricant de votre ordinateur, ou sur Windows Update.
    * Si vous disposez de plusieurs moniteurs PC connectés à votre ordinateur, essayez de déconnecter temporairement tout le moniteur PC sauf un.
    * Si vous avez défini un taux de rafraîchissement personnalisé pour votre moniteur PC, essayez de rétablir temporairement un taux de rafraîchissement standard, par exemple 60 Hz.
    * Si vous avez récemment modifié votre carte graphique sans réinstaller Windows, vérifiez que le pilote du moniteur de casque est toujours installé. Une fois votre casque branché, vérifiez que « casque de réalité mixte » est listé sous le nœud analyses dans Device Manager.
    * Si votre ordinateur dispose d’une carte graphique NVIDIA, assurez-vous que le logiciel de vision 3D de NVIDIA est désactivé.
    * Sur certaines cartes graphiques (en particulier les anciennes cartes graphiques), le port HDMI peut ne pas prendre en charge la norme HDMI 2,0 ou ne pas être entièrement compatible avec Windows Mixed Reality. Essayez le port DisplayPort de votre carte graphique à l’aide d’une [carte active displayport 1,2 vers HDMI 2,0](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) .
    * Les PC HP Omen avec HP Product Number 1RJ99EA # ABU ont des ports HDMI qui sont incompatibles avec Windows Mixed Reality. Pour ce faire, ouvrez l' « Assistant de support HP » et le numéro de produit s’affiche dans la partie inférieure de l’application.
    * Si votre ordinateur est équipé d’une carte graphique AMD R9 et que vous utilisez un casque de réalité mixte Samsung, vous devez mettre à jour le microprogramme de votre casque vers la version 1.0.8 ou ultérieure pour pouvoir utiliser le port HDMI de votre carte graphique avec le casque.
    * Si vous utilisez un livre surface 2, assurez-vous que vous utilisez l' [adaptateur USB-C vers HDMI](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
* Vérifiez la présence d’un problème matériel de casque de réalité mixte :
    * Pour confirmer ou éliminer les problèmes matériels liés à votre casque de réalité mixte, essayez de connecter votre casque de réalité mixte à un autre PC. 
    * Vérifiez la compatibilité du PC et les problèmes d’installation en premier, car les symptômes sont très similaires.
* Vérifiez que le câble USB est branché sur un port USB 3,0 ou plus rapide. Les ports USB 3,0 ont un SS (Super Speed) écrit en regard. Ils sont souvent (mais pas toujours) bleus en couleur.        

Si utile, consultez le tableau de bord de dépannage de l’écran noir du casque ci-dessous.

![Écran noir/impossible de voir quoi que ce soit](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Mon casque s’affiche parfois en noir après une utilisation.

* Essayez de désactiver les fonctionnalités de suspension ou d’économie d’énergie USB que votre PC peut avoir. Par exemple, la [suspension sélective USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) dans les options d’alimentation de Windows, le paramètre « autoriser l’ordinateur à éteindre cet appareil pour économiser l’énergie » dans Device Manager, ainsi que tous les paramètres d’économie d’énergie USB dans le microprogramme de votre PC.
* Déconnectez temporairement les autres périphériques USB et les périphériques connectés à votre PC.
* Vérifiez la version de votre pilote GPU. Assurez-vous qu’elle est récente, mais faites attention aux nouveaux problèmes de performances et de compatibilité et aux régressions sur les nouveaux pilotes.

### <a name="one-of-the-displays-on-my-headset-is-black"></a>L’un des écrans de mon casque est noir.

* Si vous utilisez un adaptateur HDMI, assurez-vous qu’il prend en charge l’HDMI 2,0.
* Retirez tous les câbles d’extension USB et HDMI que vous utilisez peut-être.
* Assurez-vous que votre pilote graphique est à jour.
* Essayez le casque de la réalité mixte sur un autre PC.

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>Mon casque s’affiche en bleu pour un moment, puis le portail de réalité mixte réinitialise.

Cela indique généralement un problème de fiabilité du contrôleur USB occasionnel sur votre ordinateur :
* Essayez un autre port USB. Votre ordinateur peut avoir plusieurs contrôleurs USB 3,0.
* Retirez tous les câbles d’extension (le cas échéant).
* Essayez de déconnecter tous les autres périphériques USB de votre PC.
* Essayez de connecter un concentrateur USB 3,0 en externe à votre PC et de connecter votre casque au Hub.
* Si vous utilisez un PC de bureau, envisagez d’acheter une carte USB 3,0 PCIe pour ajouter un autre contrôleur USB à votre PC.

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Mon casque provoque le blocage de mon ordinateur ou l’affichage d’un écran noir lors du démarrage.

Sur certains PC, le fait de laisser votre casque branché avant de mettre sous tension ou pendant le redémarrage de votre PC peut interférer avec son processus de démarrage. Votre ordinateur peut sélectionner le casque s’affiche comme « moniteur principal » pour afficher la progression du démarrage du PC ou il peut être empêché de démarrer correctement et peut « se bloquer » et/ou produire un code d’erreur de signal sonore. Le comportement dépend en grande partie de la marque et du modèle du PC, et/ou de la marque et du modèle de la carte graphique. Pour résoudre ce problème :
* Connectez votre casque à un autre port de votre carte graphique (vous devrez peut-être utiliser un adaptateur pour utiliser les autres ports).
* Assurez-vous que le microprogramme BIOS/UEFI de votre ordinateur est à jour (mais mettez à jour uniquement le microprogramme BIOS/UEFI de votre ordinateur si vous y êtes familiarisé).

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Mon PC ou casque affiche le scintillement, le flash ou le reste noir lors de l’utilisation d’un PC surface.

* Assurez-vous que vous utilisez un adaptateur HDMI qui prend en charge l’HDMI 2,0. De nombreux adaptateurs HDMI plus anciens prennent uniquement en charge la résolution de 1080p, ce qui est insuffisant pour les casques de réalité mixte.
* Assurez-vous que votre pilote graphique est à jour. En plus de vérifier Windows Update, vous souhaiterez peut-être consulter le site Web du fabricant du PC pour obtenir un pilote graphique mis à jour.
* Certains appareils surface sont incompatibles avec Windows Mixed Reality. En savoir plus sur la [compatibilité des surfaces et les exigences](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>L’affichage de mon casque ne fonctionne pas après l’arrêt et le démarrage rapide.

Débranchez le câble HDMI et le câble USB du casque, puis replacez-les.

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Les affichages de mon casque sont très saccadés, mais la fenêtre d’aperçu du portail de la réalité mixte s’affiche parfaitement.

* Assurez-vous que les ressources système de votre ordinateur (processeur, mémoire et disque dur) sont disponibles et non liées à une autre application ou à un autre processus.
* Mettez à jour votre pilote Graphics.

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>J’obtiens une erreur « la classe d’installation n’est pas présente ou n’est pas valide » dans Device Manager.

Si vous voyez « capteurs HoloLens » avec un point d’exclamation jaune dans Device Manager, double-cliquez sur l’appareil pour obtenir des détails supplémentaires. Si vous voyez un message indiquant «les pilotes de cet appareil ne sont pas installés. (Code 28)--la classe d’installation n’est pas présente ou n’est pas valide. cela est généralement dû au fait que votre ordinateur exécute [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Notez que les N-éditions de Windows 10 ne prennent pas en charge Windows Mixed Reality et que vous devez installer une version non N de Windows 10.

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Mon environnement WMR est instable ou subit des interruptions lorsque je déplace mon tête et affiche une double vision.

Sur un ordinateur portable doté d’un graphique intégré et d’un GPU NVIDIA, une erreur se produit au bout d’un laps de temps qui semble entraîner l’affichage d’une image précédente après le cadre suivant, ce qui a pour effet de doubler la vision. Le problème semble se trouver sur les pilotes après le pilote graphique NVIDIA 436,48.  L’installation de ce pilote permet de résoudre le problème jusqu’à ce que NVIDIA résout le problème dans les pilotes mis à jour. Pour une installation directe du pilote graphique NVIDIA 436,48, visitez [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Je rencontre une gêne quand j’utilise mon casque.
Pour obtenir des informations générales sur le confort de Windows Mixed Reality, consultez [intégrité, sécurité et confort du casque Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort). Pour plus d’informations sur votre casque spécifique, contactez le fabricant du casque.

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Comment puis-je obtenir une vue plus claire dans mon casque ?
Essayez d’ajuster l’adéquation de votre casque. Ajustez sa position sur votre visage en la déplaçant vers le haut et vers le haut, ou vers la gauche et la droite, et ajustez les sangs pour qu’il s’ajuste.

Si votre casque la prend en charge, vous pouvez également ajuster ses paramètres d’étalonnage. Si le casque a un bouton pour ajuster l’étalonnage, utilisez-le. Si ce n’est pas le cas, accédez à **paramètres > réalité mixte > qualité visuelle** et ajustez l’étalonnage à cet endroit. Pour plus d’informations sur l’étalonnage de votre appareil spécifique, contactez le fabricant de votre casque.

## <a name="mixed-reality-portal-error-messages-and-problems"></a>Messages d’erreur et problèmes liés au portail de réalité mixte

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>J’obtiens un message d’erreur « un problème est survenu » ou je rencontre des problèmes dans le portail de réalité mixte.

Redémarrez Windows Mixed Reality :
1. Déconnectez les deux câbles du casque de votre PC.
2. Redémarrez votre PC.
3. Reconnectez votre casque.

Si cela ne fonctionne pas, assurez-vous que votre ordinateur reconnaît votre casque :
1. Sélectionnez Démarrer.
2. Tapez « gestionnaire de périphériques » dans la zone de recherche et sélectionnez-le dans la liste. 
3. Développez « appareils de réalité mixte » et vérifiez si votre casque est listé. 

S’il n’est pas listé, essayez ce qui suit :
1. Branchez le casque sur les différents ports du PC, le cas échéant.
2. Recherchez les dernières mises à jour logicielles à partir de Windows Update.
3. Désinstallez et réinstallez Windows Mixed Reality :
    1. Déconnectez les deux câbles du casque de votre PC.
    2. Sélectionnez **paramètres > réalité mixte > désinstaller** .
    3. Sélectionnez **paramètres > appareils > Bluetooth & d’autres appareils** pour découpler vos contrôleurs de mouvement. Sélectionnez chaque contrôleur, puis sélectionnez « Supprimer l’appareil ».
    4. Reconnectez votre casque à votre ordinateur pour réinstaller Windows Mixed Reality.
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>J’obtiens un message d’erreur « Vérifiez le câble USB ».

Connectez votre casque à un autre port USB (et assurez-vous qu’il s’agit d’une vitesse USB 3,0). Essayez également de supprimer les extendeurs ou les hubs entre le casque et l’ordinateur.

### <a name="im-getting-a-check-your-display-cable-error-message"></a>J’obtiens un message d’erreur « vérifier votre câble d’affichage ».

Essayez ce qui suit :
* Connectez votre casque à un DisplayPort 1,2 ou une version ultérieure, ou HDMI 1,4 ou version ultérieure. Assurez-vous que le port correspond à la carte graphique la plus avancée sur votre PC.
* Si vous utilisez un adaptateur, assurez-vous qu’il prend en charge 4K.
* Essayez d’utiliser un autre port HDMI.
* Si vous avez un moniteur externe branché dans un port HDMI, essayez de le brancher dans un DisplayPort et utilisez le port HDMI pour votre casque.


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>Codes d’erreur « un problème est survenu » et comment les résoudre

| **Codes d’erreur Windows 10** (version 1809/versions 1709, 1803) | **Message d’erreur et suggestions de résolution des problèmes**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **Vérifiez votre câble d’affichage : Assurez-vous que le câble d’affichage de votre casque est correctement branché.** <br/><br/><ol start="1"><li>Débranchez les câbles USB et HDMI de votre casque, puis rebranchez-les.</li><li>Vérifiez Device Manager et vérifiez que le moniteur « casque de réalité mixte » est présent sous « moniteurs ».</li><li>Assurez-vous que vos pilotes graphiques sont à jour (à partir du site Web du fabricant de votre carte graphique).</li><li>Si vous utilisez un adaptateur pour connecter votre casque, assurez-vous qu’il [prend en charge Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Si votre carte graphique a à la fois des ports DisplayPort et HDMI, essayez d’utiliser le port DisplayPort sur votre carte graphique et utilisez un adaptateur DisplayPort-to-HDMI de réalité mixte pris en charge.</li><li>Essayez un autre port USB 3,0 sur votre PC</li></ol> |
|   1-5 / 2197815297-5  | **Vérifiez votre câble d’affichage : l’affichage de votre casque n’a pas réussi à s’initialiser correctement. Essayez de redémarrer votre ordinateur et de reconnecter votre casque.**<br/><br/>Windows voit votre moniteur de casque, mais Windows Mixed Reality rencontre des problèmes de communication avec les affichages sur votre casque de réalité mixte. Pour résoudre ce problème :<br/><ol start="1"><li>Assurez-vous que vos pilotes graphiques sont à jour (à partir du site Web du fabricant de votre carte graphique).</li><li>Si vous utilisez un adaptateur pour connecter votre casque, assurez-vous qu’il [prend en charge Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Si votre carte graphique a à la fois des ports DisplayPort et HDMI, essayez d’utiliser le port DisplayPort sur votre carte graphique et utilisez un adaptateur DisplayPort-to-HDMI de réalité mixte pris en charge.</li><li>Essayez de redémarrer votre PC.</li></ol> |
|   7-1, 7-2, 7-3/2181038087-1, 2181038087-2, 2181038087-3  | **Windows Mixed Reality rencontre des problèmes de connexion à votre casque. Essayez de débrancher votre casque et de le rebrancher.**<br/><br/>Échec de l’initialisation complète du casque de la réalité mixte. Il s’agit probablement d’une erreur temporaire. Débranchez votre casque et rebranchez-le pour résoudre ce problème.
|   7-4 / 2181038087-4  | **Windows Mixed Reality rencontre des problèmes de connexion à votre casque. Essayez de débrancher votre casque et de le rebrancher.**<br/><br/>Le pilote du casque de la réalité mixte n’a pas pu initialiser les caméras de suivi sur votre casque. Il s’agit probablement d’une erreur temporaire. Débranchez votre casque et rebranchez-le pour résoudre ce problème.
|   7-5 / 2181038087-5  | **Windows Mixed Reality rencontre des problèmes de connexion à votre casque. Essayez de brancher votre casque sur un autre port USB et de déconnecter temporairement tous les autres périphériques USB connectés à votre PC.**<br/><br/>Windows Mixed Reality a perdu la synchronisation entre les horodateurs du cadre de l’appareil photo de la réalité mixte et les horodateurs du PC. Il peut s’agir d’une erreur temporaire ou d’une indication de problèmes d’intégrité de signal USB. Pour résoudre ce problème :</li><li>Débranchez temporairement tous vos périphériques USB et périphériques, retirez tous les câbles d’extension et branchez simplement votre casque.</li><li>Désactivez les fonctionnalités d’économie d’énergie USB sur votre ordinateur, telles que la suspension sélective dans les options d’alimentation de Windows, le paramètre « autoriser l’ordinateur à éteindre cet appareil pour économiser l’énergie » dans Device Manager et les paramètres d’économie d’énergie USB dans le microprogramme de votre PC.</li></ul>
|   7-6 / 2181038087-6  | **Il y a un problème avec le microprogramme de votre casque. Essayez de débrancher votre casque et de le rebrancher.** <br/><br/>Il peut s’agir d’une erreur temporaire. Essayez de déconnecter et de reconnecter votre casque. Si cela ne fonctionne pas :</li><li>Vérifiez les mises à jour Windows pour vous assurer que vous exécutez le dernier pilote de casque disponible.</li><li>Essayez votre casque sur un autre PC. Si vous voyez le même message d’erreur, votre casque devra être desservi.</li></ul>
|   7-7 / 2181038087-7  | **Windows Mixed Reality rencontre des problèmes de connexion à votre casque. Essayez de brancher votre casque sur un autre port USB et de déconnecter temporairement tous les autres périphériques USB connectés à votre PC.**<br/><br/>Le pilote du casque de la réalité mixte n’a pas pu initialiser le microprogramme sur votre casque. Il peut s’agir d’une erreur temporaire. Essayez de déconnecter et de reconnecter votre casque. Si cela ne fonctionne pas :<li>Débranchez temporairement les périphériques USB et les périphériques dont vous n’avez pas besoin pour exécuter Windows Mixed Reality.</li><li>Vérifiez les mises à jour Windows pour vous assurer que vous exécutez le dernier pilote de casque disponible.</li></ul>
|   7-11 / 2181038087-11 | **Votre UC est trop ancienne pour être compatible avec Windows Mixed Reality.**<br/><br/>Votre ordinateur ne vérifie pas la compatibilité, car le jeu d’instructions AVX requis par les contrôleurs de mouvement de réalité mixte est manquant dans votre processeur. Vous aurez besoin d’un [PC compatible Windows Mixed Reality](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons).
|   7-12 / 2181038087-12 | **Votre casque est connecté à un contrôleur USB incompatible. Essayez de brancher votre casque sur un autre port USB, le cas échéant. Ou bien, essayez d’installer un pilote USB Microsoft à la place des pilotes incompatibles.**<br/><br/>Votre casque peut être branché sur un port USB connecté à un pilote de contrôleur USB non-Microsoft incompatible. La possibilité de lire et de gérer le [descripteur containerId](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows)pour ces pilotes de contrôleur USB 3,0 est souvent omise, qui regroupe les parties disparates du casque de la réalité mixte en une unité cohésive (pour lire les données audio du casque approprié, vidéo les affichages appropriés et extraire les données de suivi des capteurs appropriés). Pour modifier votre pilote de contrôleur USB : <ol start="1"><li>Lancez Device Manager.</li><li>Développez la catégorie des contrôleurs de bus série universel, puis cliquez avec le bouton droit pour désinstaller le pilote pour chaque élément qui comprend le texte « contrôleur hôte eXtensible » **et** dont le nom ne contient pas « Microsoft ».</li><li>Sélectionnez supprimer le logiciel du pilote pour cet appareil pour vous assurer que les anciens pilotes sont supprimés.</li><li>Vérifiez que chaque élément qui inclut le texte « contrôleur hôte eXtensible » contient « Microsoft » à la fin.</li><li>Branchez le HMD.</li></ol>Sinon, si le problème est intermittent, le HMD peut ne pas répondre correctement aux commandes du pilote HMD. Pour corriger ce problème, débranchez le HMD pendant 30 secondes ou plus, puis rebranchez-le. | 
|   7-13 / 2181038087-13 | **Votre casque est connecté à un contrôleur USB incompatible. Essayez de brancher votre casque sur un autre port USB, le cas échéant. Si ce n’est pas le cas, vous devez installer un nouveau contrôleur USB 3,0.**<br/><br/>Windows Mixed Reality ne parvient pas à synchroniser les horodateurs du cadre de l’appareil photo de réalité mixte avec les horodateurs de votre ordinateur. Cela est probablement dû à un contrôleur d’hôte USB 3,0 incompatible qui ne prend pas en charge les ITP (paquets d’horodatage isochrone). Contactez le fabricant de votre ordinateur pour savoir si ITP peut être activé ou basculer vers un autre contrôleur hôte USB avec prise en charge de ITP. |
|   7-14 / 2181038087-14 | **Windows Mixed Reality rencontre des problèmes de connexion à votre casque. Essayez de débrancher votre casque et de le rebrancher.**<br/><br/>Windows Mixed Reality a des difficultés à initialiser le capteur de présence sur votre casque de réalité mixte. Dans Device Manager, le casque affiche le message d’erreur « PoseThread n’a pas pu initialiser le capteur de présence ». Pour résoudre ce problème :<br/><ol start="1"><li>Débranchez votre casque, puis rebranchez-le. Assurez-vous que le câble USB est branché en tout.</li><li>Essayez un autre port USB sur votre PC.</li><li>Essayez votre casque sur un autre PC pour voir si le casque s’énumère entièrement dans Device Manager sur ce PC.</li><li>Vérifiez si d’autres pilotes HID conflictuels sont installés sur votre ordinateur, par exemple à partir du clavier ou de la souris. (Recherchez les périphériques HID dans Device Manager avec un logo de point d’interrogation.)</li><li>Si vous utilisez un casque Samsung de réalité mixte exécutant Windows 10 version 1709 ou version 1803, suivez les instructions du code d’erreur 2181038087-12 pour vérifier si votre contrôleur 3,0 USB exécute un pilote de contrôleur USB non-Microsoft.</li></ol> |
|   7-15 / 2181038087-15 | **Windows Mixed Reality a détecté l’installation d’un pilote WinUSB incompatible.**<br/><br/><ol start="1"><li>Assurez-vous que le pilote WinUSB sur votre PC est celui fourni avec Windows et que les pilotes USB tiers n’ont pas remplacé la copie de WinUSB sur votre PC.</li><li>Vous devrez peut-être récupérer ou réinstaller votre installation de Windows si le problème persiste.</li></ol> |
|   13-11/-            | Le portail de réalité mixte a rencontré un problème d’inscription d’application avec Windows. Vérifiez le journal des événements d’application (à l’aide de observateur d’événements) pour voir s’il existe des détails supplémentaires. |
|   14-1/-            | Le portail de réalité mixte rencontre des problèmes lors de l’initialisation de la pile de graphiques et de composition. Pour résoudre ce problème :<ul><li>Gestionnaire de fenêtrage (DWM, un composant clé de la pile Windows Graphics) peut se bloquer. Vérifiez le journal des événements d’application (à l’aide de observateur d’événements) pour voir si cela se produit.</li><li>Essayez une désinstallation propre de votre pilote graphique, puis installez le pilote graphique le plus récent à partir du site Web du fabricant de la carte graphique.</li></ul> |
|   14-2/C0001160-101  | **Nous avons rencontré un problème lors de la connexion à votre casque. Essayez de supprimer tous les câbles d’extension que vous utilisez peut-être et vérifiez que vous avez connecté le casque au port approprié pour votre carte graphique. Si vous utilisez des adaptateurs, assurez-vous qu’ils sont compatibles avec la réalité mixte. Si vous rencontrez toujours des problèmes, essayez de mettre à jour votre pilote Graphics.**<br/><br/>L’affichage et la pile de composition de la réalité mixte n’ont pas réussi à s’initialiser. La carte graphique ou le pilote de carte graphique de votre PC peut ne pas être compatible avec Windows Mixed Reality. Pour vérifier ce qui suit : <ul><li>Vérifiez que votre ordinateur répond à la configuration système minimale requise pour Windows Mixed Reality.</li><li>Si vous utilisez les PC Dell Inspiron 5577 sur Windows 10, version 1809 ou ultérieure, vous pouvez voir cette erreur en raison d’un conflit avec la fonctionnalité de traitement graphique en couleurs en couleurs de Dell. Pour contourner ce problème, utilisez l’application TrueColor de Dell pour désactiver la fonctionnalité TrueColor, puis essayez à nouveau d’exécuter le portail de réalité mixte.</li><li>Sur un PC de bureau, installez le pilote graphique le plus récent à partir du site Web du fabricant de la carte graphique. Sur un ordinateur portable, installez le pilote graphique le plus récent pour votre marque et votre modèle à partir du site Web du fabricant de l’ordinateur portable.</li><li>Si vous avez des graphiques tiers ou que vous affichez des logiciels/accessoires, désinstallez temporairement ces applications et pilotes.</li><li>Sélectionnez « Réessayer » pour voir s’il s’agit d’un problème temporaire.</li></ul> |
|   14-3/-             | **Nous avons rencontré un problème lors de la connexion à votre casque. Essayez de supprimer tous les câbles d’extension que vous utilisez peut-être et vérifiez que vous avez connecté le casque au port approprié pour votre carte graphique. Si vous utilisez des adaptateurs, assurez-vous qu’ils sont compatibles avec la réalité mixte. Si vous rencontrez toujours des problèmes, essayez de mettre à jour votre pilote Graphics.** <br/><br/><ul><li>Si vous utilisez des modes personnalisés ou des taux de rafraîchissement sur votre moniteur PC, essayez de définir leurs taux d’actualisation sur 60 Hz.</li><li>Assurez-vous que les adaptateurs que vous utilisez prennent en charge Windows Mixed Reality.</li><li>Essayez d’installer le pilote graphique le plus récent à partir du site Web du fabricant de la carte graphique.</li><li>Cliquez sur « Réessayer » pour voir s’il s’agit d’un problème temporaire.</li></ul> |
| 14-4/-             | **Nous avons rencontré un problème lors de la connexion à votre casque. Essayez de supprimer tous les câbles d’extension que vous utilisez peut-être et vérifiez que vous avez connecté le casque au port approprié pour votre carte graphique. Si vous utilisez des adaptateurs, assurez-vous qu’ils sont compatibles avec la réalité mixte. Si vous rencontrez toujours des problèmes, essayez de mettre à jour votre pilote Graphics.** <br/><br/><ul><li>Votre ordinateur peut avoir plus de moniteurs de PC connectés que votre carte graphique ne peut en prendre en charge. Déconnectez tous les ordinateurs à l’exception de votre moniteur d’ordinateur principal.</li><li>Assurez-vous que les adaptateurs que vous utilisez prennent en charge Windows Mixed Reality.</li><li>Installez le pilote graphique le plus récent à partir du site Web du fabricant de la carte graphique.</li><li>Cliquez sur « Réessayer » pour voir s’il s’agit d’un problème temporaire.</li></ul> |
|   15-5/-             | **Le portail de réalité mixte a perdu la synchronisation avec la réalité mixte principale et les composants Windows dont il dépend.**<br/><br/><ul><li>Cela peut être dû à un problème de performances avec votre PC. Assurez-vous que le processeur, le GPU et le disque dur ne sont pas liés au gestionnaire des tâches.</li><li>Déconnectez temporairement tous les autres périphériques USB de votre PC.</li><li>Redémarrez votre PC.</li></ul> |
|   -/H0002000-0    | **Le système d’exploitation de votre PC a rencontré un État incompatible pour Windows Mixed Reality**<br/><br/>Vérifiez les mises à jour de Windows Update. |
|   -/S0002261-101, S0002361-101 | **Un problème avec un composant Shell de réalité mixte empêche le démarrage correct du portail de réalité mixte**<br/><br/><ul><li>Ouvrez le journal des applications à l’aide de observateur d’événements sur votre PC pour vérifier si une application se bloque au moment où vous avez essayé de démarrer Windows Mixed Reality.</li><li>Assurez-vous que votre pilote graphique est à jour.</li><li>L’adaptateur HDMI que vous utilisez n’est pas compatible avec Windows Mixed Reality. Consultez [ici](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)les HDMI prises en charge et recommandées pour le dongle port d’affichage (DP).</li></ul> |


## <a name="motion-controller-problems"></a>Problèmes de contrôleur de mouvement

### <a name="my-motion-controllers-arent-working-properly"></a>Mes contrôleurs de mouvement ne fonctionnent pas correctement.

Si vos [contrôleurs de mouvement](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) ne fonctionnent pas, si vous ne vous connectez pas ou si vous ne voyez pas d’image des contrôleurs quand vous enportez votre casque, procédez comme suit :
1. Assurez-vous que vos contrôleurs sont activés. Pour les activer, appuyez sur le bouton Windows et maintenez-le enfoncé pendant deux secondes.
2. Assurez-vous que les contrôleurs sont entièrement chargés et remplacez les batteries si ce n’est pas le cas.
3. Désactivez et rallumez les contrôleurs tout en les maintenant enfoncés. Appuyez sur le bouton Windows et maintenez-le enfoncé pendant quatre secondes pour désactiver un contrôleur, puis appuyez dessus et maintenez-le enfoncé pendant deux secondes pour le mettre sous tension. 
4. Sélectionnez **paramètres > appareils > Bluetooth & d’autres appareils** sur votre ordinateur et assurez-vous que les contrôleurs sont répertoriés comme couplés. Si ce n’est pas le cas, vous devez [les apparier](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality). 
5. Assurez-vous que les contrôleurs de mouvement s’affichent sous la forme « connecté ». « Jumelé » ne signifie pas nécessairement que les contrôleurs sont connectés au PC. Les contrôleurs doivent apparaître sous la catégorie « souris, clavier & stylet ». Les contrôleurs de mouvement sous « autres appareils » ont échoué au processus de jumelage et ne fonctionnent pas. Vérifier les LED des contrôleurs de mouvement : les contrôleurs allumés de façon claire sont couplés et connectés, les contrôleurs dimly lit ne sont pas connectés.
6. Accédez à **démarrer > portail de réalité mixte** sur votre ordinateur, puis sélectionnez « Menu ». Vous devez voir vos contrôleurs de mouvement listés, ainsi qu’un message d’État :
    * Prêt : les contrôleurs sont tous définis.
    * Suivi perdu : le portail de réalité mixte ne trouve pas vos contrôleurs. Tenez-les devant votre casque et redémarrez-les en appuyant sur le bouton Windows pendant 4 secondes, puis de nouveau pendant 2 secondes.
    * Batterie faible : remplacez les piles du contrôleur.
7. Si vous utilisez une carte Bluetooth USB externe, assurez-vous qu’elle est connectée à un port USB noir 2,0. Il doit également être branché aussi loin que possible de tout autre transmetteur sans fil ou disque mémoire flash USB, y compris le connecteur USB pour votre casque. 
8. Pour vérifier qu’il n’y a qu’une seule radio Bluetooth sur le PC, cliquez avec le bouton droit sur le menu Démarrer de Windows, puis sélectionnez Device Manager. Développez la section Bluetooth et recherchez un adaptateur. Si vous utilisez la configuration de l’ordinateur de bureau avec la radio intégrée, vérifiez si une antenne externe est connectée. Si aucune antenne externe n’est connectée, cela peut entraîner des problèmes de suivi. Vous avez la possibilité d’utiliser une clé Bluetooth externe (USB), de désactiver la fonctionnalité Bluetooth interne et de réessayer le jumelage et la connexion.
9. Fermez la fenêtre Paramètres Bluetooth si elle est ouverte. S’il est ouvert en arrière-plan, un grand nombre d’appels supplémentaires sont effectués au protocole Bluetooth.
10. Vérifiez le niveau de la batterie virtuelle sur le contrôleur de mouvement. En réalité mixte, activez les contrôleurs et vous pourrez voir une icône de batterie. S’il est rouge, remplacez les piles. La création de rapports de batterie est généralement plus élevée que le niveau réel juste après la connexion d’un contrôleur. Attendez environ 15 secondes pour que le niveau de la batterie soit stable, puis lisez le niveau.
11. Retirez les écouteurs et les haut-parleurs Bluetooth dans **paramètres > appareils > Bluetooth & d’autres appareils** et éteignez les appareils. Utilisez la prise casque ou les haut-parleurs intégrés sur votre casque de réalité mixte pour une expérience audio optimale.
12. Si vous avez d’autres périphériques Bluetooth associés à votre PC, tels que des casques ou des boîtiers, supprimez-les. Sélectionnez **paramètres > appareils > Bluetooth & d’autres appareils sur votre ordinateur** , sélectionnez les appareils, puis sélectionnez « Supprimer l’appareil ».
13. Débranchez le câble USB de votre casque et rebranchez-le sur le PC pour redémarrer la fonctionnalité du contrôleur sur le PC.
14. Les voyants du contrôleur clignotent lorsqu’ils sont en cours de mise à jour du microprogramme. Attendez la fin de la mise à jour du microprogramme et les contrôleurs doivent apparaître dans la réalité mixte.
15. Assurez-vous que votre ordinateur est connecté à un réseau Wi-Fi de 5 GHz. Si votre ordinateur portable est connecté à un réseau WiFi 2,4 GHz, il partage généralement la connexion Bluetooth. Cela peut avoir un impact négatif sur les performances WiFi ou Bluetooth, en fonction de la conception du produit. Remplacez la bande par défaut par 5 GHz dans les paramètres de carte réseau. Si votre réseau ne prend pas en charge 5 GHz, une clé Bluetooth peut être utilisée à la place de la fonctionnalité Bluetooth interne.
16. Si vos paramètres Bluetooth ont déjà des contrôleurs de mouvement couplés, Windows ne découvre pas les nouveaux périphériques tant que ceux-ci n’ont pas été supprimés (s’ils ont été ajoutés à l’aide d’une clé spécifique, ils peuvent uniquement être supprimés avec cette clé).
17. Si votre PC intègre Bluetooth et que vous rencontrez des problèmes de connexion, essayez d’utiliser une carte Bluetooth USB à la place. Pour ce faire, vous devez désactiver votre radio Bluetooth intégrée dans Device Manager puis coupler vos autres appareils Bluetooth avec la nouvelle carte.

### <a name="motion-controller-troubleshooting-flowchart"></a>Organigramme de résolution des problèmes du contrôleur de mouvement

![Tableau de bord de dépannage pour les contrôleurs de mouvement](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>Mon contrôleur est bloqué dans un redémarrage infini (avec un bourdonnement après le cycle LED).

Il s’agit d’un indicateur de batterie critique. Vérifiez que vous avez des piles neuves dans l’appareil. Si le problème persiste, effectuez une récupération de l' [appareil](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) pour réinitialiser les paramètres d’usine du contrôleur.

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>J’essaie de coupler mes contrôleurs, mais ils ne s’affichent pas dans le menu « Ajouter un nouveau périphérique » dans les paramètres Bluetooth.

Vérifiez que les contrôleurs ne sont pas déjà associés, supprimez-les et réessayez. Si le problème persiste, redémarrez l’ordinateur et réessayez. En cas d’échec, consultez le [Forum aux questions](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)sur le Bluetooth.

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>La vitesse du Wi-Fi devient lente sur mon Notebook quand les contrôleurs de mouvement sont activés.

Votre Notebook peut partager son antenne Wi-Fi avec Bluetooth lorsqu’il est connecté à un point d’accès 2,4 GHz. Vérifiez auprès du gestionnaire de périphériques si vous pouvez basculer la préférence de bande à 5 GHz. Si le réseau de 5 GHz n’est pas disponible et que les performances sont gravement affectées, envisagez d’utiliser une clé Bluetooth.

![Les paramètres de sélection de la bande wifi sont accessibles via le gestionnaire de périphériques](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>La reconnexion de mon deuxième contrôleur prend beaucoup de temps.

Certaines radios Intel plus anciennes rencontrent ce problème si les contrôleurs de mouvement sont mis sous tension en même temps. Évitez d’alimenter les contrôleurs en même temps.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Ma radio Qualcomm Bluetooth ne peut pas coupler les contrôleurs après un incident de PC.

Les pilotes radio Qualcomm (QCA) Bluetooth antérieurs à 10.0.0.448 peuvent finir en mauvais état après un incident Windows. Mettez complètement le PC hors tension pour contourner ce problème. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Je rencontre un mauvais suivi de contrôleur avec la radio Marvell.

Accédez à **Device Manager > > de la carte radio Bluetooth Marvell AVASTAR > propriétés > pilote** et assurez-vous que vous utilisez le pilote 15.68.9210.47 ou version ultérieure.

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>Le portail de réalité mixte fonctionne, mais mes contrôleurs de mouvement sont mal suivis (les contrôleurs restent volants, tremblements, etc.).

1. Certaines conditions d’éclairage peuvent affecter le suivi. Assurez-vous que vous n’êtes pas exposé à la lumière solaire directe et que vous n’avez pas une grande quantité de sources de lumière visible pour votre HMD (par exemple, des chaînes d’éclairages comme un arbre de Noël). 
2. Consultez les [questions fréquentes sur Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Ces symptômes sont généralement dus à des défaillances de communication entre le contrôleur et le PC hôte, et indiquent une qualité de liaison Bluetooth médiocre.

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Les LED du contrôleur de mouvement ne sont pas allumés, mais les boutons et les sticks analogiques fonctionnent toujours dans le portail de réalité mixte.

Le cache d’étalonnage du contrôleur de mouvement est peut-être endommagé. Pour supprimer le cache, exécutez la commande suivante dans une invite de commandes d’administrateur :

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Ce dossier n’est pas accessible dans l’Explorateur Windows et ne peut être modifié qu’à partir d’une invite de commandes d’administrateur. Après avoir supprimé le dossier, redémarrez votre PC et reconnectez vos contrôleurs de mouvement pour restaurer les fichiers d’étalonnage.

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Les contrôleurs de mouvement n’apparaissent pas dans les applications et jeux SteamVR.

Si vous êtes en mesure de voir vos contrôleurs de mouvement dans la maison de la falaise, mais pas dans les applications et jeux SteamVR, le pilote du modèle de contrôleur de mouvement n’est peut-être pas installé correctement. Ce pilote est téléchargé et installé automatiquement via Windows Update, mais si vous êtes sur un PC qui a des stratégies d’entreprise ou si Windows Update n’est pas limité, vous devrez peut-être l’installer manuellement. Pour vérifier que le pilote du modèle de contrôleur de mouvement est correctement installé :
1. Activez les deux contrôleurs de mouvement et assurez-vous qu’ils s’affichent comme étant « connectés » dans l’application paramètres sous **appareils > Bluetooth & autres appareils** . Si elles n’apparaissent pas ou s’affichent comme étant « jumelées », [couplez-les](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Ouvrez Device Manager et recherchez « contrôleur de mouvement-gauche » et « contrôleur de mouvement à droite » sous « Bluetooth ».
3. Sélectionnez l’un ou l’autre appareil, puis accédez à **afficher > appareils par connexion** .
4. Vous voyez maintenant une vue des appareils Bluetooth du contrôleur de mouvement, montés sur votre radio Bluetooth. Sous le même nœud que les deux contrôleurs de mouvement doivent être deux appareils « périphériques HID Bluetooth », et sous chaque périphérique HID Bluetooth doit être un appareil nommé « contrôleur de mouvement » (avec des icônes grises).
5. Double-cliquez sur chacun des appareils « contrôleur de mouvement » et accédez à l’onglet **pilote** . Vérifiez que la version de pilote indiquée correspond à l’une de [ces versions de pilote de modèle de contrôleur de mouvement](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history).

Pour télécharger et installer manuellement le pilote du modèle de contrôleur de mouvement, visitez [cette page](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) et recherchez la version du pilote correspondant à votre version de Windows 10. Les instructions d’installation sont disponibles sur la page de téléchargement.

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>La mise à jour du microprogramme des contrôleurs de mouvement prend beaucoup plus de deux minutes.

Consultez les [questions fréquentes sur Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Une mauvaise qualité de liaison Bluetooth est généralement à l’origine de ces problèmes.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Je viens d’insérer des piles neuves, mais le niveau de batterie virtuelle du contrôleur n’indique pas un niveau complet.

Le niveau de batterie du contrôleur de mouvement est réglé pour les piles AA. Certaines batteries rechargeables de basse tension peuvent ne pas être entièrement signalées, bien qu’elles soient entièrement chargées.

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>Mon contrôleur ne vibre pas quand la batterie est faible.

Les haptique sont désactivées lorsque le niveau de la batterie devient faible. Remplacez vos batteries.

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>Mon appareil est vibré trois fois, puis il est arrêté.

Les batteries fonctionnent à un niveau faible et atteignent le seuil de coupure. Remplacez vos batteries.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Mon pavé tactile du contrôleur Samsung motion est hors-Centre ou a un point mort.

Il s’agit probablement d’une erreur matérielle et vous devez revenir à votre revendeur ou fabricant d’équipement pour un remplacement ou un échange.

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>Le contrôleur ne fonctionne pas correctement et je ne parviens pas à mettre à jour l’appareil.

Restaurez-la à des conditions d’usine (vous aurez besoin de piles neuves) :
1. Débranchez et mettez hors tension les contrôleurs.
2. Ouvrez la couverture de la batterie.
3. Insérez vos nouvelles piles.
4. Appuyez sur le bouton d’appariement (l’onglet situé en bas sous les batteries) et maintenez-le enfoncé.
5. Tout en maintenant le bouton de jumelage, mettez sous tension le contrôleur en appuyant sur le bouton Windows pendant cinq secondes (maintenez les deux boutons enfoncés).
6. Relâchez les boutons et attendez la mise sous tension du contrôleur. Cela prend jusqu’à 15 secondes et aucun indicateur ne s’affiche en cas de récupération de l’appareil. Si l’appareil s’allume immédiatement sur la version du bouton, la séquence du bouton de récupération n’a pas été inscrite et vous devez réessayer.
7. Accédez à **paramètres > Bluetooth > autres appareils** , puis sélectionnez « contrôleur de mouvement-gauche » ou « contrôleur de mouvement-droite » et « supprimer l’appareil ») pour supprimer les anciennes associations de contrôleur des paramètres Bluetooth. 
8. Couplez de nouveau le contrôleur au PC.
9. Une fois connecté avec l’hôte et HMD, l’appareil est mis à jour avec le dernier microprogramme disponible.

### <a name="lights-and-indicators"></a>Lumières et indicateurs

L’anneau et les haptiques de la constellation LED indiquent l’état du contrôleur de mouvement.

| State    | Causes de l’État | Comportement de lumière et de vibration associé à l’État |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Mise sous tension**               | Maintenez le bouton Windows enfoncé sur le contrôleur pendant deux secondes pour activer le contrôleur.       | Les LED allument et le contrôleur vibre une fois. |
| **Mise hors tension**              | Maintenez le bouton Windows enfoncé sur le contrôleur pendant quatre secondes pour désactiver le contrôleur.      | Les voyants sont éteints et le contrôleur vibre deux fois. |
| **En état de veille**               | Le contrôleur passe automatiquement en état de veille lorsqu’il est motionless pendant 30 secondes. Le contrôleur sort automatiquement lorsqu’il détecte motion, sauf lorsque l’appareil n’est pas couplé avec le PC hôte. Dans ce cas, une pression sur un bouton est nécessaire pour la mettre en éveil. | Les voyants s’éteignent et clignotent toutes les trois secondes en état de veille. |
| **Jumelage**                | Appuyez et maintenez le bouton de jumelage au sein de la batterie pendant trois secondes.     | Clignotement de LED lentement en mode de couplage, et est solide lorsque vous quittez le mode de couplage. Le contrôleur vibre une fois si le jumelage a réussi ou vibre trois fois si le couplage échoue et expire. |
| **Le contrôleur se connecte/se déconnecte du PC** | Le contrôleur se connecte correctement au PC une fois que vous l’avez mis sous tension, ou le contrôleur se déconnecte du PC en cours d’utilisation pour une raison quelconque.| Le contrôleur vibre une fois sur la connexion du PC ou la déconnexion. |
| **Niveau de batterie faible**      | Le niveau de la batterie est faible.| Il n’y a pas d’indication de VOYANTs ou de vibrations lorsque la batterie est faible. Il y a une icône d’indicateur de batterie sur la poignée de la représentation du contrôleur dans le casque. Lorsque la batterie est faible, l’icône d’indicateur affiche 1/4. |
| **Niveau de batterie critique** | Lors de la mise sous tension lorsque le niveau de batterie est « critique ». Le niveau de batterie « critique » signifie que l’alimentation est insuffisante et que le contrôleur s’éteint automatiquement.| Le contrôleur vibre trois fois quand vous l’activez, puis le désactive automatiquement. À mesure que vous approchez cet État, l’icône d’indicateur de batterie affiche rouge. |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Comment puis-je savoir si j’utilise la technologie Bluetooth ?

Les contrôleurs de mouvement utilisent la même technologie Bluetooth que sur de nombreux appareils grand public et sont conçus pour fonctionner avec la fonctionnalité Bluetooth incluse dans tout ordinateur récent. Pour vérifier que votre ordinateur dispose d’une radio Bluetooth (si l’appareil a réussi l’outil de vérification de compatibilité de la réalité mixte) : 
* Cliquez avec le bouton droit sur le menu Démarrer de Windows, puis sélectionnez « Device Manager ». 
* Développez la section Bluetooth et recherchez un adaptateur. 
* Si votre ordinateur n’est pas équipé de Bluetooth, l’un des dongles recommandés est le [micro-adaptateur USB Bluetooth 4,0 Low Energy](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom). \
![Capture d’écran d’un exemple de Device Manager. L’adaptateur est la radio Bluetooth.](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>Mon PC a une technologie Bluetooth, mais je rencontre des problèmes avec mes contrôleurs de mouvement.

Les contrôleurs de mouvement doivent fonctionner avec d’autres claviers, souris et contrôleurs de jeu Bluetooth, mais l’expérience varie en fonction du modèle de clavier, de souris ou de contrôleur de jeu que vous utilisez. Voici quelques opérations que vous pouvez effectuer pour améliorer les performances :
* Si votre ordinateur possède le Bluetooth, mais que vous rencontrez toujours des problèmes avec les contrôleurs de mouvement, envisagez de remplacer votre radio Bluetooth par l’adaptateur Bluetooth externe enfichable connecté à USB. Notez que vous ne pouvez avoir qu’une seule carte radio Bluetooth active à la fois. Si vous branchez une radio externe en plus d’une radio existante, vous devez désactiver votre radio Bluetooth existante dans Device Manager (cliquez avec le bouton droit sur la carte et sélectionnez « Désactiver l’appareil ») et désassocier/recoupler tous vos appareils Bluetooth précédents.
* Si vous utilisez une carte Bluetooth USB, connectez-la à un port USB 2,0 (les ports 2,0 sont noirs et ne sont pas étiquetés « SS »), le cas échéant. Le port doit être physiquement séparé des éléments suivants :
    - le connecteur USB HMD
    - disques mémoire flash
    - disques durs
    - les récepteurs USB sans fil comme ceux des claviers/souris, branchez l’adaptateur Bluetooth USB sur le côté opposé de l’ordinateur aussi loin que possible à partir de ces autres connecteurs.
* N’installez pas de logiciel tiers.
* Fermez la fenêtre Paramètres Bluetooth si elle est ouverte. Le fait de le laisser ouvert en arrière-plan signifie qu’un grand nombre d’appels supplémentaires sont effectués au protocole Bluetooth.
* Désactivez le paramètre « afficher la notification pour se connecter à l’aide d’une paire SWIFT » sous Bluetooth & d’autres appareils pour réduire l’activité d’analyse de l’ordinateur hôte.
* Si vous utilisez une carte Bluetooth interne, vérifiez que vous utilisez une antenne Bluetooth externe. 
  * Dans ce cas, l’absence d’antenne Bluetooth externe est connue pour provoquer des problèmes de suivi. 
  * Si cela ne fonctionne pas, utilisez une clé Bluetooth externe (USB) après la désactivation du Bluetooth interne.
* Il est important que l’appareil apparaisse sous la catégorie « souris, clavier & stylet » dans les paramètres Bluetooth. Si la sous « autres appareils » est découplée et couplée à l’appareil.
* Retirez, annulez et mettez hors tension les écouteurs et les haut-parleurs Bluetooth. Celles-ci ne sont pas prises en charge avec Windows Mixed Reality. Vous pouvez utiliser la prise casque ou les haut-parleurs intégrés sur votre casque de réalité mixte pour une expérience audio optimale.

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>Comment puis-je associer mes contrôleurs de mouvement à un casque Windows Mixed Reality avec la radio Bluetooth intégrée ou les renvoyer à leur jumelage de fabrique ?

Certains casques Windows mixtes de réalité, y compris Acer OJO 500 et Samsung Odyssey +, disposent de radios Bluetooth intégrées pour une utilisation avec les contrôleurs de mouvement. Les contrôleurs de mouvement fournis avec ces casques sont précouplés au casque en usine et n’exigent pas que votre ordinateur dispose d’une radio Bluetooth distincte. Ces contrôleurs de mouvement _peuvent_ être associés manuellement à la radio Bluetooth de votre PC, par exemple, pour une utilisation avec des casques Windows Mixed realisation qui n’ont pas de radio Bluetooth intégrées. Pour ramener les contrôleurs de mouvement à leur appariement de fabriques, ou pour les associer à un casque Windows Mixed Reality avec une radio Bluetooth intégrée, exécutez l’application compagnon de l’appareil du casque (par exemple, l’application « Acer OJO 500 » ou l’application «Samsung HMD


## <a name="performance-questions"></a>Questions sur les performances

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>Comment puis-je savoir si le casque Windows Mixed realisation est rendu à 60 Hz ou 90Hz.

Vérifiez le **portail de l’appareil > onglet performances** . 

**Remarque** : Si vous avez un GPU discret avec des ports HDMI 2,0 et un processeur avec quatre cœurs physiques ou plus, vous devez obtenir 90 Hz. Si votre GPU n’a qu’une sortie HDMI 1,4, vous pouvez utiliser un adaptateur DisplayPort à [hdmi 2,0](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) comme solution de contournement. 

**Remarque** : l' **affichage du casque > paramètres de qualité visuelle** affectent uniquement le rendu de l’expérience d’hébergement Windows Mixed Reality.

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>Que dois-je faire si mon PC semble fonctionner lentement ?

Le système peut être lent pour de nombreuses raisons et, dans la plupart des cas, ce sera le cas après quelques secondes. Si vous rencontrez ce problème sur de longues périodes de temps :
1. Fermez toutes les applications inutilisées sur le bureau.
2. Assurez-vous que votre ordinateur portable est branché à une source d’alimentation.
3. Assurez-vous que le PC n’est pas en état de préchauffage.
4. Réduisez la qualité visuelle dans votre page d’hébergement Windows Mixed Reality.
5. Vérifiez que vous disposez des derniers pilotes graphiques pour votre PC (consultez la section Pilotes graphiques).

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Mon PC est en état de préchauffage lorsque j’exécute les expériences de réalité mixte. Comment faire en garder le froid ?

1. Assurez-vous que la batterie est chargée et que la source d’alimentation est branchée.
2. Assurez-vous que les ventilateurs à travers ou en dehors du PC ne sont pas bloqués.
3. Utilisez l’ordinateur dans un environnement relativement froid.
4. Assurez-vous qu’il n’existe aucune source de chaleur (par exemple, le soleil ou les orifices de chauffage) pointé sur le PC.

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Mes éléments visuels sont saccadés, se chargent lentement ou ne semblent pas corrects.
* Assurez-vous que votre casque est branché à la bonne carte graphique sur votre PC. Certains PC ont des cartes graphiques intégrées et discrètes. La carte discrète offre généralement les meilleures performances. [En savoir plus sur le matériel PC](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* Fermez les applications inutilisées sur votre bureau.
* Assurez-vous que votre casque est ajusté (déplacez-le vers le bas et vers le haut ou vers la gauche et vers la droite pour le régler).
* Réglez les paramètres visuels de votre casque dans **paramètres > la réalité mixte > affichage du casque** . Lorsque la « qualité visuelle » est définie sur « automatique », nous allons choisir la meilleure expérience de réalité mixte pour votre PC. Pour obtenir une expérience avec davantage de détails visuels, définissez « qualité visuelle » sur « haute ». Si vos visuels sont saccadés, vous souhaiterez peut-être sélectionner un paramètre inférieur.
* Essayez de régler l’étalonnage de votre casque. Les lentilles doivent être ajustées pour correspondre à votre distance interpupillary (IPD), la distance entre vos élèves. Si vous ne connaissez pas votre IPD, un Optometrist doit être en mesure de le mesurer pour vous. Il existe également des sites Web conçus pour mesurer l’IPD. Une fois que vous connaissez votre IPD, utilisez le bouton d’étalonnage de votre casque pour effectuer des ajustements. Si le casque n’a pas de bouton d’étalonnage, sélectionnez **paramètres > réalité mixte > affichage du casque** et réglez le « contrôle d’étalonnage ».


## <a name="tracking-system-problems"></a>Suivi des problèmes système

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>Le système ne trouve pas la limite et je suis présenté avec l’interface utilisateur du programme d’installation.

Cela signifie que le système de suivi n’a pas pu reconnaître votre environnement. Si vous êtes dans un nouvel environnement, vous devez configurer la [limite](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary). Si vous avez déjà utilisé l’appareil dans cet environnement et configuré une limite :
* Assurez-vous que la salle a suffisamment de lumière.
* Vérifiez que vous avez porté l’appareil et recherché dans la pièce. L’appareil doit observer votre environnement pour savoir où il se trouve. S’il est assis sur un bureau ou une table, il ne trouve pas vos limites.
* Débranchez l’appareil, fermez Windows Mixed Reality et reconnectez l’appareil.
* Un événement a peut-être changé dans votre environnement et l’appareil ne le reconnaît plus. Essayez de configurer une nouvelle limite.

Si ces étapes ne résolvent pas le problème, supprimez les données de votre environnement et réinstallez la limite.

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>Le système me présente avec l’interface utilisateur qui me demande de choisir la configuration pour toutes les expériences ou assis/debout, et je vois mes limites.

La recherche des limites de l’appareil prend trop de temps. Vous pouvez contourner ce message en choisissant l’option permettant d’utiliser une limite et vous serez dirigé vers votre page d’hébergement de la réalité Windows Mixed avec vos limites présentes.

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>Je vois souvent un message indiquant « j’ai perdu mes limites ».

Le système de suivi fait un suivi du temps et de l’identification de votre environnement. Dans cet État, l’appareil ne peut plus afficher vos limites et le casque bascule sur 3DOF pour vous permettre de vous tenir au fait de l’univers réel jusqu’à ce qu’il trouve à nouveau vos limites. Pour résoudre ce problème :
1. Assurez-vous que la salle a suffisamment de lumière.
2. Réexécutez le programme d’installation si vous avez récemment redécoré ou remodelé la salle.
3. Débranchez l’appareil, fermez Windows Mixed Reality et rebranchez-le.
4. Effacez les données de votre environnement et réinstallez l’appareil.
5. Si le message persiste, contactez le support technique.

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Je peux me pencher, mais je ne peux pas le traduire (je suis bloqué dans 3DOF).

Cela signifie que le système de suivi ne peut pas générer de pose, ou que l’application s’est arrêtée en utilisant de nouvelles données de pose à restituer. Vérifiez les points suivants :
* Assurez-vous que la salle a suffisamment de lumière.
* Assurez-vous que la salle dispose de suffisamment de détails pour effectuer le suivi.
* Débranchez l’appareil, fermez Windows Mixed Reality, puis reconnectez l’appareil.
* Si le message persiste, contactez le support technique

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>La vue dans le HMD est complètement figée.

Cela signifie généralement que l’application ou un composant de niveau système a échoué. Essayez d’effectuer les opérations suivantes :
1. Appuyez sur le bouton « démarrage » pour fermer l’application.
2. Débranchez l’appareil, fermez MRP et rebranchez l’appareil.
3. Redémarrez le PC.

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>Je vois souvent une bordure noire autour des bords de la vue dans le HMD. Il semble parfois que je regarde un tunnel.

Cela signifie que l’application ne peut pas atteindre la fréquence d’images sur votre PC et que le système utilise des trames anciennes pour afficher la vue dans le HMD. Étant donné que les applications affichent uniquement la partie du monde que vous regardez, si elles n’atteignent pas régulièrement leurs fréquences d’images, le système tentera de continuer à rendre le monde à partir d’un point de vue précédent et remplira les détails manquants avec le noir. Si cela se produit fréquemment :
1. Fermez ou terminez tous les programmes inutiles pour libérer de la mémoire et de l’UC.
2. Réduisez les paramètres de détail dans votre application.
3. Réduisez les paramètres de détail dans les paramètres de Windows Mixed Reality.

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>La vue dans le HMD est instable et subit beaucoup de perturbations.

Cela peut se produire pour plusieurs raisons. Les causes principales sont que le système ne parvient pas à afficher le contenu sur le casque ou que le système de suivi rencontre des problèmes. Vérifiez les points suivants :
1. Vérifiez que votre ordinateur n’est pas en conflit avec les ressources. Ouvrez le gestionnaire des tâches et vérifiez que vos ressources de calcul sont gratuites (par exemple, 80% de l’UC, 400 Mo de RAM et les e/s disque sont inférieures à 80%).
2. Assurez-vous que vous disposez des derniers pilotes graphiques pour votre matériel. Pour plus d’informations, consultez la section du pilote Graphics.
3. Assurez-vous que la salle a suffisamment de lumière.
4. Débranchez l’appareil, fermez Windows Mixed Reality et reconnectez l’appareil.
5. Redémarrez votre PC.
6. Si le problème persiste, contactez le support technique.

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>Le monde court rapidement et peut-être incliné ou renversé avant de revenir à la normale.

Cela peut être dû à une application ou à un composant de niveau système qui atteint une erreur irrécupérable, ou à un manque temporaire de mémoire ou de ressources processeur. Vérifiez les points suivants :
1. Ouvrez le « gestionnaire des tâches » et assurez-vous de disposer d’au moins 20% de mémoire disponible sur le processeur et 400 Mo (par exemple, 80% de l’UC, 400 Mo de RAM et les e/s disque sont inférieures à 80%).
2. Ouvrez « observateur d’événements », puis accédez à **journaux Windows >** entrées d’événements d’application et d’erreur au cours du blocage. Vérifiez si des processus se sont bloqués.
3. Essayez de redémarrer le PC si le problème persiste.

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Le monde a inversé momentanément et est revenu à la normale.

Cela est généralement dû à des erreurs lors de l’obtention de données de capteur à partir du casque pour informer les algorithmes de suivi. Si cela se produit fréquemment :
1. Branchez le casque sur un port USB 3,0 différent.
2. Branchez le casque directement sur le PC plutôt que sur un concentrateur USB 3,0.
3. Si le problème persiste, contactez le support technique.

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>Le monde est incliné, mais je peux naviguer et se déplacer dans Windows Mixed Reality.

Cela est généralement dû à des erreurs de données de capteur enregistrées dans les données d’environnement stockées sur votre PC. Cela peut entraîner l’inclinaison de la réalité Windows Mixed, parfois de manière permanente. Essayez ce qui suit :
1. Débranchez le HMD, fermez Windows Mixed Reality et rebranchez le casque.
2. Redémarrez le PC.
3. Effacez les données de votre environnement.

## <a name="webvr-questions"></a>Questions WebVR

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Pourquoi ne puis-je pas voir mes contrôleurs lors de l’affichage du contenu VR depuis Edge ?

Tous les contenus WebVR ne sont pas créés pour prendre en charge les contrôleurs de mouvement. WebVR permet aux développeurs de contenu de prendre en charge différents types d’entrée, tels que les contrôleurs de jeu ou les contrôleurs de mouvement. Si vous ne voyez pas vos contrôleurs sur un site, il est probable qu’il ne prend pas en charge le contrôleur de mouvement.

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Pourquoi ne puis-je pas utiliser la souris dans une vue WebVR immersif ?

Il s’agit d’une fonctionnalité facultative de la spécification WebVR. Tous les navigateurs ne prennent pas en charge cette fonctionnalité, et tous les contenus WebVR ne sont pas créés pour prendre en charge l’entrée de la souris. WebVR permet aux développeurs de contenu de prendre en charge différents types d’entrée, tels que la souris, le clavier, les contrôleurs de jeu ou les contrôleurs de mouvement. Le comportement d’entrée de la souris varie selon le navigateur. Au sein de Microsoft Edge, les auteurs de sites Web doivent s’assurer qu’ils acceptent « pointerlock » lors de la présentation du casque pour que l’entrée de la souris fonctionne.

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Pourquoi mon contrôleur ressemble-t-il à vive/Oculus, a-t-il un sens étrange ou les boutons sont mal mappés ?

Le site Web n’a probablement pas de prise en charge complète du contrôleur motion.

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>Pourquoi ne puis-je pas afficher les vidéos de 360 degrés de YouTube/Facebook/Vimeo/le gardien/New York Times, etc., depuis Edge en VR ?

Tout comme n’importe quelle autre spécification ou norme Web, l’auteur a le choix de l’implémenter ou non. Il existe une spécification WebVR qui permet aux sites Web de lancer des expériences VR directement à partir du navigateur, et les auteurs de ces sites Web n’ont pas implémenté cette spécification pour l’instant. Il peut y avoir des applications téléchargeables sur certaines plateformes, qui permettent d’afficher le contenu VR de ces fournisseurs.

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Pourquoi ne puis-je pas entrer VR depuis Firefox ou chrome ?

WebVR est uniquement pris en charge par les appareils Windows Mixed Reality dans Edge pour l’instant.

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Lorsque j’entre VR à partir d’un site Web, pourquoi un écran vide s’affiche-t-il dans mon casque ?

Le site Web n’a peut-être pas implémenté la prise en charge de plusieurs machines GPU (y compris les ordinateurs portables GPU hybrides). Essayez d’effectuer les opérations suivantes :
* Rechargez la page.
* Sur les ordinateurs de bureau, connectez le casque à la même carte graphique que le moniteur qui affiche Microsoft Edge. Branchez-les tous les deux dans la carte graphique plus puissante, et non dans la carte graphique intégrée.

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Lorsque je quitte VR lors de la lecture d’une vidéo à partir de Edge, le son continue de fonctionner, mais la fenêtre du bord est grisée.

Il s’agit d’un problème connu lors de l’exécution de WebVR à partir de Edge dans le cliffhouse de la réalité mixte. Pour le résoudre, appuyez sur Échap sur le clavier au lieu d’appuyer sur le bouton Windows pour quitter l’expérience WebVR, ou activez la fenêtre grisée du bord en la sélectionnant, puis arrêtez la vidéo.

### <a name="can-i-use-webvr-on-the-hololens"></a>Puis-je utiliser WebVR sur le HoloLens ?

Microsoft n’a pas annoncé de WebVR sur le HoloLens à ce stade.

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Pourquoi ma vue est-elle au niveau étage lors de l’affichage du contenu WebVR à partir de Edge ?

Le site Web ne prend pas en charge correctement les casques Windows Mixed Reality. Pour contourner ce problème :
1. Placez le casque à l’étage de votre espace.
2. Accédez à la page WebVR à l’aide de Microsoft Edge sur votre bureau (pas dans la réalité mixte).
3. Cliquez sur le bouton sur la page Web pour entrer VR.
4. Attendez 5-10 secondes que l’expérience soit entièrement entrée en mode immersif.
5. Sélectionnez le casque et placez-le sur votre tête.

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>La résolution de l’affichage est très faible dans certaines expériences WebVR.

Les sites Web ne prennent pas en charge correctement les casques haute résolution. Pour contourner ce problème :
* Si vous lancez WebVR à partir du Bureau (par opposition à depuis la cliffhouse de la réalité mixte), assurez-vous que la fenêtre est agrandie avant d’entrer VR.
* Évitez de redimensionner la fenêtre Microsoft Edge une fois que vous avez entré VR.

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Pourquoi la vue immersive WebVR se termine-t-elle lorsque je modifie les onglets du navigateur ?

Ce comportement est normal. Pour des raisons de sécurité, seul l’onglet actif du navigateur peut accéder aux casques connectés.

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Pourquoi ne puis-je pas entendre l’audio sur une expérience WebVR particulière ?

Le site Web utilise peut-être le format de fichier audio OGG, que Microsoft Edge ne prend pas actuellement en charge.

Vous pouvez signaler des sites rompus directement à l’équipe du navigateur Microsoft Edge dans le [suivi des problèmes](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)ou via Twitter à l’aide de [#EdgeBug mot-dièse](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Pourquoi les commentaires haptique ne fonctionnent-ils pas dans WebVR avec les contrôleurs de mouvement ?

Actuellement, Microsoft Edge ne prend pas en charge les haptique sur les extensions d’API du boîtier WebVR.


## <a name="steamvr-questions"></a>Questions SteamVR

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>Comment puis-je jouer à des jeux SteamVR dans mon casque d’immersion Windows Mixed Reality ?

Vous devez installer Windows Mixed Reality pour SteamVR sur votre PC et configurer SteamVR :
* [Téléchargez et installez SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe).
* Démarrez SteamVR. Le didacticiel SteamVR doit démarrer automatiquement.
* Connectez votre casque à votre ordinateur et allumez vos contrôleurs de mouvement.
* Une fois que la page d’hébergement de la réalité mixte de Windows a été chargée et que vos contrôleurs sont visibles, ouvrez l’application de vapeur sur votre bureau.
* Utilisez l’application Steam pour lancer un jeu SteamVR à partir de votre bibliothèque de vapeur. Pour lancer des jeux SteamVR sans avoir à sortir votre casque, vous pouvez les Rechercher et les lancer sous **démarrer > toutes les applications** de Windows Mixed Reality. 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>J’obtiens un message indiquant « pour utiliser SteamVR avec Windows Mixed Reality, vous devez installer le dernier Windows Update » ou « mode développeur Windows requis ».

1. Assurez-vous que votre ordinateur exécute la dernière version de Windows 10. Pour ce faire, accédez à **paramètres > système > à propos** de. Sous « spécifications Windows », assurez-vous que « version du système d’exploitation » est 16299,64 ou supérieur.
2. Assurez-vous que vous n’avez pas de mise à jour en attente de téléchargement ou d’installation. Accédez à **paramètres > mettre à jour & sécurité > Windows Update** et sélectionnez « Rechercher les mises à jour ». Il se peut que vous deviez vérifier les mises à jour plusieurs fois, afin de continuer à vérifier les mises à jour jusqu’à ce qu’aucune autre mise à jour ne soit disponible, puis redémarrez votre PC.

### <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR se bloque après la mise à jour de Windows.

Certaines versions antérieures de Windows Mixed Reality pour SteamVR ne sont plus compatibles avec Windows. Vous avez peut-être une ancienne version de Windows Mixed Reality pour SteamVR. Pour vous assurer que vous êtes à jour :
1. Dans votre bibliothèque de vapeur, accédez à **logiciel > Windows Mixed Reality for SteamVR** .
2. Cliquez avec le bouton droit et accédez à « propriétés ».
3. Sélectionnez l’onglet « mettre à jour » et sélectionnez « toujours conserver cette application à jour ».
4. Forcez la mise à jour en accédant à l’onglet « fichiers locaux » et en sélectionnant « vérifier l’intégrité des fichiers d’application ».
5. Redémarrez Steam et SteamVR.

Si SteamVR continue de se bloquer après la mise à jour, vous pouvez avoir deux installations de Windows Mixed Reality pour SteamVR sur votre ordinateur. Pour confirmer si c’est le cas :
1. Recherchez%LocalAppData%\openvr\openvrpaths.vrpath et ouvrez-le dans le bloc-notes.
2. Dans les sections « pilotes externes », recherchez plusieurs entrées pour « MixedRealityVRDriver » 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Si vous voyez plusieurs entrées, supprimez l’ancienne des deux entrées. Notez qu’une fois que vous n’avez qu’une seule entrée, il ne doit plus y avoir de virgule à la fin de la ligne, par exemple :
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Enregistrez le fichier et fermez-le.
5. Redémarrez Steam et SteamVR.

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Mes contrôleurs ne fonctionnent pas comme prévu dans SteamVR.

1. Fermez SteamVR.
2. Revenez à la réalité mixte et vérifiez que vos contrôleurs fonctionnent comme prévu.
3. Lancez à nouveau l’expérience SteamVR et vos contrôleurs doivent revenir à la normale.
4. Si les problèmes persistent, envoyez des commentaires à l’aide du [Hub de commentaires Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) sous la catégorie de réalité mixte et incluez SteamVR dans le résumé.

Notez que vous utiliserez vos contrôleurs de mouvement différemment dans différents jeux. Voici quelques notions de base pour vous aider à démarrer :
* Pour ouvrir le tableau de bord de la vapeur, appuyez sur le joystick de gauche.
* Pour quitter un jeu SteamVR et revenir à la page d’hébergement Windows Mixed Reality, appuyez sur le bouton Windows. Sélectionnez ensuite le bouton d’accueil de la réalité mixte qui apparaît à l’écran.

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Les contrôleurs de gauche et de droite sont inversés dans SteamVR.

Démarrez le jeu en désactivant vos contrôleurs, puis en le reouvrant, puis en le faisant précédé de l’un d’eux.

### <a name="my-games-are-running-slowly"></a>Mes jeux s’exécutent lentement.

1. Confirmez que votre ordinateur répond aux spécifications de SteamVR dans Windows Mixed Reality
2. Vérifiez que votre ordinateur répond aux spécifications du jeu SteamVR que vous jouez.
2. Dans le portail de réalité mixte sur votre bureau, sélectionnez « Pause » pour arrêter la version préliminaire du bureau.
3. Suivez les instructions ci-dessus pour vérifier que vous exécutez Windows 10 Build 16299,64 ou version ultérieure.
4. Assurez-vous que votre ordinateur dispose des derniers pilotes graphiques.
5. Vérifiez le gestionnaire des tâches pour connaître les autres processus qui sont en cours d’exécution sur votre ordinateur et qui consomment des ressources.
6. Vérifiez si la vapeur télécharge un jeu en arrière-plan. Cela peut consommer des ressources et compliquer l’exécution des jeux.
7. Il existe un problème de performance connu qui affecte une petite classe d’applications qui n’ont pas de fenêtre visible, par exemple SteamVR. La grande majorité des applications ne rentrent pas dans cette catégorie et un correctif sera disponible dans une prochaine mise à jour.

Si vous rencontrez toujours des problèmes de performances inattendus, envoyez-nous vos commentaires à l’aide du Hub de commentaires Windows. Veillez à suivre les instructions pour [inclure un suivi des performances SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr). 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR affiche une erreur de compositeur (par exemple, « échec de la connexion au compositeur Shared IPC (400) »).

Il existe un problème connu où cela peut se produire si votre casque et votre moniteur principal se trouvent sur deux cartes vidéo différentes. Connectez votre moniteur à la même carte que votre casque et configurez cette analyse comme moniteur principal dans **paramètres application > système > afficher** .

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Le contenu SteamVR s’affiche au mauvais endroit, comme sous le plancher ou au-dessus de mon en-tête.

Réinitialisez votre position : 
1. Cliquez sur le stick analogique du contrôleur de gauche pour afficher le « tableau de bord SteamVR ».
2. Sélectionnez le bouton « Paramètres ».
3. Sélectionnez « Réinitialiser la position assise ».

### <a name="my-steam-app-closed-unexpectedly"></a>Mon application Steam a été fermée de manière inattendue.

L’application de vapeur se ferme si vous verrouillez l’écran de votre PC, si vous retirez votre casque, si vous changez d’utilisateur ou si votre ordinateur passe en mode veille.


## <a name="speech-and-audio-problems"></a>Problèmes vocaux et audio

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Je n’entends aucun son dans mon casque ou le son est lu par mon ordinateur au lieu de mon casque.

* Si votre casque immersif n’inclut pas de casque intégré, vous devez connecter le casque à la prise jack audio sur le casque. Le Jack est souvent situé juste derrière ou sous le visière ou les glaces du casque. Si vous ne parvenez pas à le trouver, contactez le fabricant de votre casque.
* Certains casques audio ont des boutons physiques pour contrôler le volume. Si l’audio ne fonctionne pas, vérifiez si le volume est désactivé ou désactivé.
* Windows Mixed Reality est conçu pour émettre du son via votre casque immersif lorsque le portail de réalité mixte est en cours d’exécution et que vous disposez d’un casque connecté. Quand vous mettez le casque hors tension ou retournez le Visor, fermez l’application portail de réalité mixte, ou lorsque cette application n’a pas été utilisée pendant 15 minutes, l’audio bascule sur votre appareil de lecture Windows par défaut. Vous pouvez modifier ce paramètre dans **paramètres > la réalité mixte > l’audio et la parole.**
* Assurez-vous que votre casque audio est entièrement branché sur le jack audio. Le casque Acer, en particulier, peut nécessiter plus de soin pour s’assurer que le casque audio est bien branché.
* Vérifiez que le microphone/casque audio est branché sur le casque et non sur le PC.
* Le panneau de configuration Windows Sound affiche uniquement les points de terminaison audio activés, pas les points de terminaison désactivés. Le périphérique audio du casque est désactivé lorsque vous n’êtes pas équipé du casque. pour ce faire, vous devez cliquer avec le bouton droit dans le panneau de configuration du son et sélectionner « Afficher les appareils désactivés » pour le voir. le nom de l’appareil est « Realtek USB 2.0 audio ». Une fois que vous avez fait cela, vous pouvez remplacer le nom de la page « Propriétés » par un nom plus facile à reconnaître. Vous pouvez effectuer cette opération pour les onglets lecture et enregistrement.
* Si votre audio ne fonctionne pas dans les applications de réalité mixte (par exemple, Netflix), cela peut être dû à un problème connu où Windows Mixed Reality n’est pas automatiquement mis à jour pour correspondre à la version du système d’exploitation. Pour résoudre ce problème et obtenir la meilleure expérience de réalité mixte, accédez à **paramètres > mettre à jour & sécurité > Windows Update > Rechercher les mises à jour** .

**Remarque :** Le son spatial Windows Mixed Reality fonctionne mieux avec les casques intégrés ou connectés directement à votre casque immersif. Les haut-parleurs ou les écouteurs du PC connectés à l’ordinateur risquent de ne pas fonctionner correctement pour le son spatial.

**Remarque :** Windows Mixed Reality ne prend pas en charge les casques audio Bluetooth.

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Je rencontre des modifications soudaines sur le volume, a perdu du son ou subit un bourdonnement.

* Certaines applications, y compris un grand nombre de celles lancées via SteamVR, peuvent perdre du son ou se bloquer lorsque le périphérique audio change quand vous démarrez ou arrêtez le portail de réalité mixte. Redémarrez l’application après avoir ouvert l’application portail de réalité mixte pour corriger ce comportement.
* Si un autre périphérique USB multimédia (par exemple, une webcam) partage le même concentrateur USB interne ou externe avec le casque Windows Mixed Reality, le casque audio/casque du casque peut parfois avoir un très bon signal sonore ou aucun son. Connectez votre casque à un port USB qui utilise un autre concentrateur ou déconnectez/désactivez votre autre périphérique multimédia USB.
* Si vous remarquez une forte rafale de bruit du casque connecté au casque, il est possible que le concentrateur USB du PC ne soit pas en mesure de fournir suffisamment de puissance au casque Windows Mixed Reality. Si cela se produit, envoyez immédiatement un bogue au [Hub de commentaires](https://docs.microsoft.com/hololens/hololens-feedback) . Les solutions de contournement qui peuvent vous aider à inclure des câbles d’extension, à l’aide d’un CONCENTRateur USB 3,0 à alimentation externe dédié, ou à essayer un port USB différent sur le PC.

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mon casque audio Bluetooth ne fonctionne pas comme prévu.

Microsoft déconseille d’utiliser des casques audio Bluetooth avec Windows Mixed Reality. Les périphériques audio Bluetooth ne fonctionnent pas correctement avec les expériences de voix et de sons spatiales de Windows Mixed Reality, et les casques audio Bluetooth ne peuvent pas prendre en charge l’entrée de microphone et la sortie stéréo en même temps, ce qui vous empêche d’entendre la stéréo ou le son spatial quand vous l’utilisez pour gamechat ou d’autres entrées vocales. Les casques audio Bluetooth peuvent également avoir un impact négatif sur votre expérience de contrôleur de mouvement. 

### <a name="sound-isnt-coming-from-expected-directions"></a>Le son ne provient pas de la direction attendue.

La page d’hébergement de la réalité Windows Mixed inclut un son spatial (audio qui semble provenir des applications situées dans votre foyer). À mesure que vous parcourez et vous rapprochez de chaque application, la direction et le niveau du son seront modifiés pour améliorer la logique du réalisme. Voici quelques raisons de sens sonore inattendus : 
* Lorsque vous ouvrez et écoutez de la musique à partir d’une application de musique qui prend en charge les arrière-plans (telle que Groove Music) dans votre foyer, puis que vous ouvrez une expérience de VR immersif (comme un jeu), le son de l’application musicale est fondu du son spatial au stéréo. Elle peut paraître plus forte qu’avant, car il n’y a plus de distance entre vous et le son.
* Si vous aviez activé Cortana sur votre ordinateur hôte avant d’utiliser votre casque Windows Mixed Reality, vous risquez de perdre le son dans la page d’accueil de Windows Mixed Reality. Pour résoudre ce problème, désactivez l’option « laisser Cortana répondre à Hey Cortana » dans **paramètres > Cortana** sur votre bureau avant de lancer Windows Mixed Reality, ou activez « Windows Sonic pour casque » dans la fenêtre d’application de bureau dans la page d’hébergement de Windows Mixed Reality.
    1. Cliquez avec le bouton gauche sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez-la dans la liste des périphériques audio.
    2. Cliquez avec le bouton droit sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez « Windows Sonic pour casque » dans le menu « Configuration des conférenciers ».
    3. Répétez ces étapes pour tous vos périphériques audio (points de terminaison).

### <a name="speech-commands-are-not-working-as-expected"></a>Les commandes vocales ne fonctionnent pas comme prévu.

* Pour utiliser les commandes vocales, les paramètres vocaux et linguistiques de votre ordinateur doivent être définis sur une [langue prise en charge dans Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Pour vérifier vos paramètres de langue et de voix Windows, sélectionnez **paramètres > heure & langue > région & langue** et **paramètres > heure & langue** > la parole.
* Si votre casque n’a pas de microphone intégré, vous devez attacher un casque avec un microphone au casque ou sur votre PC. Pour que le commutateur d’entrée microphone soit automatiquement sur votre casque quand vous l’utilisez, accédez à **paramètres > réalité mixte > audio et parole** , puis activez « lorsque j’utilise mon casque, basculez vers casque MIC ».
* Certains casques audio ont un bouton physique pour activer et désactiver le microphone. Si les commandes vocales ne fonctionnent pas, vérifiez si votre microphone est muet.
* Les casques audio avec un microphone qui Dangles du câble Earbud ne fonctionnent pas correctement pour les commandes vocales dans les environnements avec un bruit ambiant.
* Cortana peut être lente la première fois qu’elle est appelée dans une session de portail de réalité mixte. Accédez à **paramètres > cortana > communiquer avec Cortana** et assurez-vous que l’option « laisser Cortana répondre à Hey Cortana » est activée.
* Sur certains PC, le gain de capture vocale par défaut pour votre microphone connecté au casque peut être trop faible. Si vous rencontrez des commandes vocales ou une dictée non fiables, vous pouvez essayer d’exécuter l’utilitaire de résolution des problèmes de configuration du microphone. Vous pouvez accéder à cet utilitaire de résolution des problèmes par le biais des **paramètres > & Language > Speech** , puis sélectionnez « Démarrer » dans la section « microphone ». Pour ce faire, utilisez l’application de bureau dans la page d’hébergement Windows Mixed Reality tout en portant le casque afin d’affecter le microphone que vous utilisez pour Windows Mixed Reality. Sélectionnez le point de terminaison approprié dans l’Assistant résolution des problèmes.

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Je n’ai qu’un seul casque audio et je souhaite l’utiliser à la fois pour le bureau et pour mon casque.

Si vous n’avez qu’un seul casque audio et que vous n’avez pas de casque avec casque intégré, connectez le casque audio au PC hôte au lieu du casque. Ensuite, désactivez l’option « Basculer vers l’audio du casque » dans les paramètres MRP.

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Je souhaite basculer vers Dolby Atmos pour casque.

Les environnements Windows Mixed Reality et ses applications utilisent la technologie audio spatiale Windows Sonic pour casque, qui est personnalisée pour les expériences de réalité mixte. D’autres technologies audio spatiales, telles que Dolby Atmos pour casque, peuvent être appliquées pour les applications plein écran comme les jeux SteamVR, mais pas pour les environnements de shell Windows Mixed Reality et les applications (telles que le placement d’un navigateur Web sur le mur de la maison de la falaise ou le gonflant) qui ont été conçus à l’aide de Windows Sonic pour le son et les acoustiques


## <a name="questions-about-desktop-in-mixed-reality"></a>Questions sur le bureau en réalité mixte

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Comment faire accéder au poste de travail de mon PC en réalité mixte ?
Vous pouvez accéder à votre PC de bureau en réalité mixte à l’aide de l’application de bureau. Lancez-le dans le bouton casque à partir de **Windows > toutes les applications > Bureau** . 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Comment puis-je voir plusieurs analyses en réalité mixte ?
Par défaut, l’application de bureau bascule automatiquement pour afficher l’analyse avec le focus. Si vous souhaitez voir toutes vos analyses en réalité mixte : 
* Cliquez sur l’icône surveiller dans l’angle supérieur gauche de l’application.
* Désactiver l’analyseur automatique de commutateur
* Sélectionnez l’analyse que vous souhaitez afficher.
* Lancer une autre instance de l’application de bureau
* Sélectionnez l’analyse que vous souhaitez afficher sur cette instance. 
* Répétez cette opération pour toutes vos analyses physiques. Notez que vous devrez resélectionner l’analyse pour afficher sur chaque application de bureau chaque fois que vous redémarrez la réalité mixte. 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>Mon application de bureau affiche uniquement un écran noir.
Si votre ordinateur dispose d’un GPU hybride NVIDIA, le problème peut être causé par un appareil NVIDIA exécutant le runtimebroker.exe sur le GPU discret au lieu de l’appareil intégré. Pour résoudre ce problème, suivez ces instructions sous «[Comment faire créer des paramètres de Optimus pour un nouveau programme](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)». pour ajouter C:\windows\system32\runtimebroker.exe et le forcer à s’exécuter sur le processeur « intégré Graphics ». 


## <a name="other-questions"></a>Autres questions

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>Ma mise à jour du microprogramme Samsung Odyssey ou Odyssey + du casque est bloquée.

Samsung possède et publie les mises à jour du microprogramme du casque fournies par le biais de ses applications « Samsung HMD Odyssey Setup » et « Samsung HMD Odyssey + Setup » Device Companion. Pour plus d’informations et pour obtenir de l’aide sur les problèmes de mise à jour du microprogramme Samsung, contactez le service client Samsung.

Si le processus de mise à jour du microprogramme est bloqué et qu’il n’y a pas eu de progression depuis plus de cinq minutes :
* Débranchez temporairement tous vos autres périphériques USB et recommencez la mise à jour du microprogramme.
* Connectez votre casque Samsung à un port USB 3,0 différent sur votre PC.
* Désactivation et/ou désinstallation de tous les logiciels installés qui peuvent interférer avec les mises à jour du microprogramme, comme les App Center de AORUS de gigaoctets.
* Utilisez un autre PC pour effectuer la mise à jour du microprogramme du casque Samsung.

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mon Wi-Fi ralentit lorsque j’utilise Windows Mixed Reality.

Si vous utilisez une connexion Wi-Fi 2,4 GHz, vos contrôleurs de mouvement peuvent ralentir votre Wi-Fi. Essayez l’une des opérations suivantes :
* Basculez vers une connexion Wi-Fi 5 GHz, le cas échéant. [Plus d’informations](https://support.microsoft.com/en-us/help/4000461)
* Utilisez un adaptateur Bluetooth distinct pour connecter vos contrôleurs de mouvement à votre PC. Voir les [adaptateurs recommandés](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>J’ai reçu un message indiquant qu’il faut brancher et charger mon PC. Pourquoi ?

Si vous utilisez un ordinateur portable, Windows Mixed Reality fonctionne mieux lorsque l’ordinateur est entièrement chargé et branché. 

### <a name="what-is-the-experience-options-setting"></a>Qu’est-ce que le paramètre options d’expérience ?

Le paramètre options d’expérience ( **paramètres > réalité mixte > affichage du casque > options d’expérience** ) vous permet de modifier les paramètres de performances de Windows Mixed Reality. Cela vous permet de choisir la meilleure expérience possible pour votre configuration matérielle dans une plage de contenu. L’expérience 90Hz est disponible pour tous les systèmes, mais vous souhaiterez peut-être essayer automatique pour voir le paramètre de votre choix. Voici les options disponibles :
* Automatique : Windows Mixed Reality déterminera la meilleure expérience de votre configuration matérielle. Pour la plupart des gens, c’est le meilleur choix pour commencer.
* 60Hz : définit la fréquence d’actualisation sur 60 Hz et désactive certaines fonctionnalités, telles que la capture vidéo et la version préliminaire dans le portail de réalité mixte.
* 90Hz : définit la fréquence d’actualisation sur 90Hz.

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quelles sont les langues prises en charge dans Windows Mixed Reality ?

Windows Mixed Reality est disponible dans les langues suivantes. Si votre ordinateur est défini sur une langue différente, vous pouvez toujours utiliser Windows Mixed Reality, mais l’interface s’affichera en anglais (États-Unis), et les commandes vocales et la dictée ne seront pas disponibles.

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

Le clavier à l’écran Windows Mixed Reality est en anglais (États-Unis) uniquement. Pour entrer du texte dans une autre langue, utilisez un clavier physique connecté à votre PC. Vous pouvez également utiliser la dictée dans l’un des langages Windows Mixed Reality pris en charge listés ci-dessus ; sélectionnez simplement microphone sur le clavier à l’écran.

Windows Mixed Reality est également disponible dans les langues suivantes sans commandes vocales ni fonctionnalités de dictée :

* Chinois traditionnel (Taïwan et Hong Kong)
* Néerlandais (Pays-Bas)
* Coréen (Corée)
* Russe (Russie)

### <a name="i-have-questions-about-my-headset-hardware"></a>J’ai des questions sur mon matériel de casque.

Pour plus d’informations sur votre casque, contactez le fabricant. Il peut y avoir un guide produit dans la zone, ou vous pouvez essayer le site Web du fabricant.


## <a name="how-to-uninstall-windows-mixed-reality"></a>Comment désinstaller Windows Mixed Reality

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>Comment faire désinstaller Windows Mixed Reality ?

1. Déconnectez votre casque de votre PC.
2. Fermez le portail de réalité mixte.
2. Accédez à  **démarrer > paramètres > réalité mixte** et sélectionnez Désinstaller.

Quand vous êtes prêt à recommencer à utiliser votre casque, connectez-le et le portail de réalité mixte vous guidera tout au long de la configuration.

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>J’ai reçu un message « Impossible de terminer la désinstallation de Windows Mixed Reality ».

Cela signifie que certains fichiers, y compris les informations relatives à votre environnement, peuvent toujours se trouver sur votre ordinateur. Cela peut poser des problèmes si vous décidez de réinstaller Windows Mixed Reality ultérieurement. Vous pouvez supprimer manuellement toutes les informations Windows Mixed Reality restantes de votre PC en modifiant le registre et en utilisant Windows PowerShell pour exécuter des commandes. _Si vous modifiez le registre de manière incorrecte, des problèmes sérieux peuvent survenir. Veillez à suivre ces étapes avec prudence. Pour une protection supplémentaire, sauvegardez votre registre avant de le modifier afin de pouvoir le restaurer en cas de problème._ Pour plus d’informations, consultez [Comment sauvegarder et placer le registre dans Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Pour désinstaller Windows Mixed realing à l’aide de ces commandes :
1. Redémarrez votre PC.
2. Dans la zone de **recherche** , tapez « regedit », puis sélectionnez **Oui** .
3. Supprimez les valeurs de Registre suivantes :
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, puis supprimez <b>FirstRunSucceeded</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>, puis supprimez <b>PreferDesktopSpeaker</b> et <b>PreferDesktopMic</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>, puis supprimez <b>DisableSpeechInput</b>. Remarque : les éléments de registre de HHKEY_CURRENT_USER doivent être supprimés pour chaque compte d’utilisateur sur le PC qui a utilisé Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>, puis sur supprimer l' <b>DeviceID</b> et le <b>mode</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, puis supprimez <b>OnDeviceLearningCompleted</b>.</li> 
   </ul>
4. Supprimez les clés de Registre suivantes : <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. Fermez l’éditeur du Registre.
6. Accédez à **C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** , puis supprimez **RoomBounds.jssur** . Répétez cette procédure pour chaque utilisateur qui a utilisé Windows Mixed Reality.
7. Ouvrez l’invite de commandes admin et accédez à **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . Ensuite, supprimez le contenu du dossier de **données HeadTracking** (mais pas le dossier lui-même).
8. Tapez « PowerShell » dans la **zone de recherche** , cliquez avec le bouton droit sur **Windows PowerShell** , puis sélectionnez **exécuter en tant qu’administrateur** .
9. Dans Windows PowerShell, procédez comme suit : <ul>
   <li>Copiez et collez le code suivant à l’invite de commandes, puis appuyez sur entrée : <b>DISM/Online/Get-Capabilities</b></li> 
   <li>Copiez l’identité de capacité qui commence par Analog. holographique. Desktop (si elle n’est pas&#39;t ici, cela signifie que cet élément n’est pas installé&#39;t. Dans ce cas, passez à l’étape 10).</li> 
   <li>Copiez et collez l’invite de commandes suivante, puis appuyez sur entrée : <b>DISM/Online/Remove-Capability/CapabilityName : l’identité de capacité copiée lors de la dernière étape</b></li>
   </ul>
10. Redémarrez votre PC.




