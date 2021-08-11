---
title: Notes de publication - Octobre 2017
description: restez à jour dans les notes de publication de Windows Mixed Reality pour la Windows 10 Fall Creators Update (octobre 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Notes de publication, version, Windows 10, Build, RS3, système d’exploitation
ms.openlocfilehash: 09a33e1bc4a13c75e4c8a0ee250c7b67eb8e68e21220840037085e727acfb1f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190593"
---
# <a name="release-notes---october-2017"></a>Notes de publication - Octobre 2017

Bienvenue dans Windows Mixed Reality ! la version **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** introduit la prise en charge des nouveaux Windows Mixed Reality et des [contrôleurs de mouvement](/windows/mixed-reality/design/motion-controllers) [immersifs](/windows/mixed-reality/discover/immersive-headset-hardware-details) . vous pouvez maintenant explorer de nouveaux mondes, jouer à des jeux VR et découvrir des divertissements immersifs quand vous êtes connecté à un [PC Windows Mixed Reality](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).

les casques Windows Mixed Reality et la version des contrôleurs de mouvement sont l’aboutissement d’un effort d’équipe massif et d’un grand pas en avant pour la [plateforme Windows Mixed Reality](/windows/mixed-reality/discover/mixed-reality), y compris [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details). si HoloLens ne reçoit pas de mise à jour avec le Windows 10 Fall Creators Update, travailler sur HoloLens n’a pas été arrêté. nous aurons un grand nombre d’apprentissages et d’informations à appliquer à partir de notre travail récent sur Windows Mixed Reality dans son ensemble. en fait, Windows Mixed Reality les contrôleurs de mouvement et les casques immersifs représentent un excellent point d’entrée pour le développement d’HoloLens également, car les mêmes api, outils et concepts s’appliquent aux deux.

pour effectuer une mise à jour vers la dernière version pour chaque périphérique, ouvrez l’application **Paramètres** , accédez à **update & Security**, puis sélectionnez le bouton **rechercher les mises à jour** . sur un PC Windows 10, vous pouvez également installer manuellement le Windows 10 Fall Creators Update à l’aide de l' [outil de création de médias Windows](https://www.microsoft.com/software-download/windows10).

 **dernière version de desktop :** Windows 10 desktop octobre 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **dernière version de HoloLens :** [Windows 10 Holographique août 2016](release-notes-august-2016.md) (**10.0.14393.0**, Windows 10 mise à jour anniversaire)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Présentation de Windows Mixed Reality

le Windows 10 Fall Creators Update introduit officiellement la prise en charge des contrôleurs de mouvement et des casques Windows Mixed Reality, et Windows 10 le premier système d’exploitation spatial au monde. Voici les points principaux :
* un **[grand nombre de casques](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** : Windows Mixed Reality permet aux partenaires d’offrir différents types de casque à partir de $399 USD fournis avec des contrôleurs de mouvement.
* **[contrôleurs de mouvement](/windows/mixed-reality/design/motion-controllers)** : les contrôleurs de mouvement Windows Mixed Reality couplent sans fil avec votre PC via des Bluetooth et une fonctionnalité six degrés de liberté, de nombreuses méthodes d’entrée et IMUs.
* **[Facilité de configuration et de portabilité](./recommended-adapters-for-windows-mixed-reality-capable-pcs.md)** : configurez et commencez en moins de 10 minutes. Les casques immersifs utilisent le suivi à l’intérieur pour suivre votre mouvement et vos contrôleurs de mouvement, avec six degrés de libertés. Aucun appareil photo ou marqueur de phare externe n’est nécessaire.
* **[la prise en charge d’un plus grand nombre de pc](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)** -Windows Mixed Reality permet à davantage de personnes de bénéficier de la fonctionnalité desktop VR, avec la prise en charge de la sélection de cartes graphiques intégrées et de pc à partir de $499 USD.
* **[Windows Mixed Reality la page d’hébergement](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** : le premier système d’exploitation spatial au monde fournit un environnement d’hébergement familier pour le multitâche avec les applications 2d, le lancement de VR et de jeux et la mise en place d’hologrammes décoratifs.
* des **[jeux et des applications étonnants dans le Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** , de la vidéo immersif comme Hulu VR et 360 video aux jeux épiques comme SUPERHOT VR et Arizona soleil, le Microsoft Store a une gamme de contenu à rencontrer dans Windows Mixed Reality.
* **[accès précoce à SteamVR](./using-steamvr-with-windows-mixed-reality.md)** : le Windows 10 Fall Creators Update permet à la prise en charge des titres SteamVR d’être joué avec Windows Mixed Reality casques et des contrôleurs, ce qui rend le catalogue le plus volumineux disponible pour les utilisateurs Windows Mixed Reality.

## <a name="known-issues"></a>Problèmes connus

nous avons travaillé dur pour offrir une expérience de Windows Mixed Reality exceptionnelle, mais nous effectuons toujours le suivi de certains problèmes connus. Si vous en trouvez d’autres, [faites-nous part de vos commentaires](/windows/mixed-reality/give-us-feedback).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>application de bureau dans la Windows Mixed Reality page d’hébergement
* L’outil capture ne fonctionne pas dans l’application de bureau.
* L’application de bureau n’est pas définie lors du redémarrage.
* si vous utilisez la préversion du portail de réalité mixte sur votre bureau, lors de l’ouverture de l’application de bureau dans la Windows Mixed Reality accueil, vous remarquerez peut-être l’effet miroir infini. 
* l’exécution de l’application de bureau peut entraîner des problèmes de performances sur les pc non-Ultra Windows Mixed Reality ; Il n’est pas recommandé.  
* L’application de bureau peut être lancée automatiquement, car une fenêtre invisible sur le Bureau a le focus. 
* L’invite du contrôle de compte d’utilisateur du Bureau fera apparaître le casque en noir jusqu’à ce que l’invite soit terminée.

### <a name="windows-mixed-reality-setup"></a>configuration de Windows Mixed Reality
* quand vous configurez Windows avec un casque connecté, le moniteur de votre PC peut rester vide. débranchez votre casque pour activer la sortie sur votre moniteur d’ordinateur pour terminer l’installation de Windows.
* Lors de la création d’une limite, le suivi peut échouer. Si c’est le cas, réessayez, car le système va en savoir plus sur votre espace au fil du temps.
* si vous activez ou désactivez Cortana lors de l’installation de Windows Mixed Reality, cette modification sera appliquée aux paramètres de Cortana de bureau.
* si vous n’avez pas de casque connecté, vous risquez de manquer des conseils lorsque vous visitez pour la première fois la Windows Mixed Reality page d’hébergement.
* Bluetooth casque peut provoquer des interférences avec les contrôleurs de mouvement. nous vous recommandons de découpler ou de mettre hors tension les contrôleurs de Bluetooth pendant les sessions de Windows Mixed Reality.

### <a name="games-and-apps-from-windows-store"></a>jeux et applications de Windows Store
* Certains jeux graphiques intensifs, tels que Forza Motorsports 6, peuvent entraîner des problèmes de performances sur les PC moins aptes lorsqu’ils sont lus dans Windows Mixed Reality.

### <a name="audio"></a>Audio
* comme indiqué ci-dessus, Bluetooth les périphériques Audio ne fonctionnent pas correctement avec des expériences de Windows Mixed Reality vocales et spatiales. Ils peuvent également avoir un impact négatif sur votre interface de contrôleur de mouvement. nous vous déconseillons d’utiliser Bluetooth casques Audio avec Windows Mixed Reality.
* Vous ne pouvez pas utiliser le périphérique audio connecté (ou une partie du) au casque pour la lecture audio lorsque l’appareil n’est pas usé. Si vous n’avez qu’un seul casque audio, vous souhaiterez peut-être connecter le casque audio au PC hôte au lieu du casque. si c’est le cas, vous devez désactiver l’option « basculer vers l’audio du casque » dans **Paramètres** l'  >    >  **audio et la parole** de la réalité mixte.
* Certaines applications, y compris un grand nombre de celles lancées via SteamVR, peuvent perdre du son ou se bloquer lorsque le périphérique audio change quand vous démarrez ou arrêtez le portail de réalité mixte. Redémarrez l’application une fois que vous avez ouvert l’application portail de réalité mixte pour y remédier.
* si Cortana est activé sur votre ordinateur hôte avant d’utiliser votre casque Windows Mixed Reality, vous risquez de perdre la simulation de son spatial appliquée aux applications que vous placez autour de la Windows Mixed Reality accueil. la solution consiste à activer « Windows Sonic pour casque » sur tous les périphériques audio connectés à votre PC, y compris votre périphérique audio connecté à un casque :
   1. Cliquez avec le bouton gauche sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez dans la liste des périphériques audio.
   2. cliquez avec le bouton droit sur l’icône de haut-parleur dans la barre des tâches du bureau, puis sélectionnez « Windows Sonic pour casque » dans le menu « configuration de l’orateur ».
   3. Répétez ces étapes pour tous vos périphériques audio (points de terminaison).
>[!NOTE]
> - étant donné que les casques/enceintes connectés à votre casque ne s’affichent pas, sauf si vous les utilisez, vous devez le faire à partir de la fenêtre de l’application de bureau dans le Windows Mixed Reality page d’hébergement pour appliquer ce paramètre au périphérique audio connecté à votre casque (ou intégré à votre casque).
> - une autre option consiste à désactiver « laissez Cortana répondre à Hey Cortana » dans **Paramètres**  >  **Cortana** sur votre bureau avant de lancer Windows Mixed Reality.

* lorsqu’un autre périphérique usb multimédia (par exemple, une webcam) partage le même concentrateur usb (externe ou à l’intérieur de votre PC) avec le casque Windows Mixed Reality, dans de rares cas, le casque audio/casque peut avoir un signal sonore ou aucun son. Vous pouvez résoudre ce problème en utilisant votre casque dans un port USB qui ne partage pas le même concentrateur que l’autre, ou déconnecter/désactiver votre autre périphérique multimédia USB.
* dans de rares cas, le concentrateur USB de l’ordinateur hôte ne peut pas fournir suffisamment de puissance au casque Windows Mixed Reality et vous pouvez remarquer une rafale de bruit à partir du casque connecté au casque.

### <a name="speech"></a>Voix
* Cortana peut ne pas pouvoir lire ses signaux audio pour l’écoute/la réflexion et les réponses audio aux commandes.
* les Cortanas sur les marchés de la chine et du japon n’affichent pas correctement le texte sous le cercle Cortana en cours d’utilisation.
* la Cortana peut être lente la première fois qu’elle est appelée dans une session de portail de réalité mixte. vous pouvez contourner ce contournement en vous assurant que « laissez Cortana répondre à Hey Cortana » sous **Paramètres**  >  **Cortana**  >  **communiquer avec Cortana** est activé.
* Cortana peut s’exécuter plus lentement sur des pc qui ne sont pas Windows Mixed Reality Ultra des pc.
* lorsque votre clavier système est défini sur une langue différente de la langue de l’interface utilisateur dans Windows Mixed Reality, l’utilisation de la dictée à partir du clavier dans Windows Mixed Reality génère une boîte de dialogue d’erreur indiquant que la dictée ne fonctionne pas en raison de l’absence de connexion Wi-Fi. pour résoudre le problème, assurez-vous que la langue du clavier système correspond à la langue de l’interface utilisateur Windows Mixed Reality.
* L’Espagne n’est pas reconnue correctement comme un marché sur lequel la reconnaissance vocale est activée pour Windows Mixed Reality.

### <a name="holograms"></a>Hologrammes
* si vous avez placé un grand nombre d’hologrammes dans votre Windows Mixed Reality, certains peuvent disparaître et apparaître à l’impression. pour éviter cela, supprimez certains des hologrammes dans cette zone du Windows Mixed Reality.

### <a name="motion-controllers"></a>Contrôleurs de mouvement
* Parfois, si vous sélectionnez une page Web dans Edge, le contenu est zoom au lieu de cliquer.
* Parfois, lorsque vous sélectionnez un lien dans Edge, la sélection ne fonctionne pas.

## <a name="prior-release-notes"></a>Notes de publication antérieures
* [Notes de publication - Août 2016](release-notes-august-2016.md)
* [Notes de publication - Mai 2016](release-notes-may-2016.md)
* [Notes de publication - Mars 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Voir aussi
* [Prise en charge des casques immersifs (lien externe)](./troubleshooting-windows-mixed-reality.md)
* [Problèmes connus concernant HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Installer les outils](/windows/mixed-reality/develop/install-the-tools)
* [Envoyer vos commentaires](/windows/mixed-reality/give-us-feedback)