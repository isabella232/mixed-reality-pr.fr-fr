---
title: Notes de publication - Octobre 2018
description: restez à jour dans les notes de publication de HoloLens et Windows Mixed Reality pour la mise à jour Windows 10 d’octobre 2018/RS5.
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: Notes de publication, version, Windows 10, Build, RS5, système d’exploitation
ms.openlocfilehash: e046025ff4952a6e8779545374ec59d9f49c907ad3174b188474ae040cb28ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219967"
---
# <a name="release-notes---october-2018"></a>Notes de publication - Octobre 2018

le **[Mise à jour d’octobre 2018 de Windows 10](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (également appelé RS5) comprend de nouvelles fonctionnalités pour HoloLens et Windows Mixed Reality des casques immersifs connectés aux pc. 

pour effectuer une mise à jour vers la dernière version sur HoloLens ou PC (pour les casques immersifs Windows Mixed Reality), ouvrez l’application **Paramètres** , accédez à **mettre à jour & sécurité**, puis sélectionnez le bouton **rechercher les mises à jour** . sur un PC Windows 10, vous pouvez également installer manuellement le Mise à jour d’octobre 2018 de Windows 10 à l’aide de l' [outil de création de médias Windows](https://www.microsoft.com/software-download/windows10).

**dernière version de Desktop :** Mise à jour d’octobre 2018 de Windows 10 (**10.0.17763.107**)<br>
**dernière version de HoloLens :** Mise à jour d’octobre 2018 de Windows 10 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>nouvelles fonctionnalités pour Windows Mixed Reality les casques immersifs

le Mise à jour d’octobre 2018 de Windows 10 offre de nombreuses améliorations pour l’utilisation de casques Windows Mixed Reality immersifs (VR) avec votre PC de bureau.

### <a name="for-everyone"></a>Pour tout le monde

* **Torche de la réalité mixte** : ouvrez un portail dans le monde réel pour trouver votre clavier, consultez une personne à proximité ou examinez votre environnement sans supprimer votre casque ! vous pouvez activer la vidéo torche de la réalité mixte à partir de la menu Démarrer, en appuyant sur Windows + attrape sur votre contrôleur de mouvement, ou en disant « flash allumé/éteint ». Pointez votre contrôleur dans la direction de ce que vous souhaitez voir, comme l’utilisation d’un torche dans l’obscurité.

    ![Torche de la réalité mixte](images/mr-flashlight.png)

* **Nouvelles applications et façons de lancer du contenu dans la réalité mixte**
    * si vous utilisez [Windows Mixed Reality pour SteamVR](./using-steamvr-with-windows-mixed-reality.md), vos titres SteamVR s’affichent désormais dans le menu Démarrer et les lanceurs d’applications de chaque peuvent être placés dans la page d’hébergement de la réalité mixte.
    
        ![Lanceurs d’applications SteamVR](images/steamvr-launchers.png)
        
    * Nouvelle application *360 Video* pour découvrir une sélection régulièrement organisée de vidéos de 360 degrés.
    * Nouvelle application *WebVR Showcase* permettant de découvrir une sélection d’expériences WebVR régulièrement organisée.
    * les clients de la première Windows Mixed Reality entrent dans la maison de la falaise et le trouvent préremplis avec les lanceurs d’applications en 3d pour certaines de nos applications et jeux immersifs favoris de la Microsoft Store.
    * Microsoft Edge windows inclut maintenant un bouton *partager* .
* **menu actions rapides** : à partir d’une application de réalité mixte immersive, vous pouvez appuyer sur le bouton Windows pour accéder à un nouveau menu actions rapides, avec un accès facile au *menu SteamVR*, à la *capture photo/vidéo*, à la *torche* et à la *page d’habitation*.
* **prise en charge des** casques de pc-Windows Mixed Reality immersifs (VR) sur les pc de sac à dos sans avoir besoin d’un émulateur d’affichage une fois l’installation terminée.
* **nouvelles fonctionnalités audio** : vous pouvez maintenant mettre en miroir le son à partir d’une expérience de Windows Mixed Reality sur la prise jack audio (ou le casque) de votre casque *et* un périphérique audio connecté à votre PC (comme les haut-parleurs externes). Nous avons également ajouté un indicateur visuel pour le niveau du volume dans l’affichage de votre casque.
* **Autres améliorations**
    * les mises à jour du portail de réalité mixte sont désormais fournies via le Microsoft Store, ce qui permet d’accélérer les mises à jour entre les versions principales de Windows. notez que cela s’applique uniquement à l’application de bureau et que l’expérience du casque Windows Mixed Reality est toujours mise à jour avec le système d’exploitation. 
    * lorsque les casques sont en veille, Windows Mixed Reality applications sont interrompues au lieu de s’arrêter (jusqu’à la fermeture du portail de réalité mixte).
    
### <a name="for-developers"></a>Pour les développeurs

* **[suivi du code qr](/windows/mixed-reality/develop/platform-capabilities-and-apis/qr-code-tracking)** -activer le suivi du code qr dans votre application de réalité mixte, ce qui permet à Windows Mixed Reality des casques immersifs (VR) d’analyser les codes QR et de les signaler aux applications intéressées.
* **Prise en charge de la DRM matérielle pour les applications immersives** : les développeurs peuvent désormais demander des textures de mémoire tampon en mémoire tampon de matériel si elles sont prises en charge par le matériel d’affichage, ce qui permet aux applications d’utiliser du contenu protégé par le matériel provenant de sources telles que PlayReady
* **[intégration de l’interface utilisateur de capture de réalité mixte dans des applications immersifs](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** : les développeurs peuvent intégrer la capture de réalité mixte dans leurs applications à l’aide de l' [interface utilisateur de capture d’appareil photo](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) intégrée Windows avec quelques lignes de code.

## <a name="new-features-for-hololens"></a>Nouvelles fonctionnalités de HoloLens

la Mise à jour d’octobre 2018 de Windows 10 est publiquement disponible pour tous les clients HoloLens et comprend un certain nombre d’améliorations, telles que :

### <a name="for-everyone"></a>Pour tout le monde

* **menu actions rapides** : dans une application de réalité mixte immersive, vous pouvez appuyer sur le bouton Windows pour accéder à un nouveau menu actions rapides, avec un accès facile pour *démarrer l’enregistrement vidéo*, *prendre des photos*, *accueil mixte* de la réalité, *changer le volume* et *Connecter*.
* **démarrer/arrêter la capture vidéo à partir du menu actions de démarrage ou rapide** : si vous démarrez la capture vidéo à partir du menu menu Démarrer ou actions rapides, vous pouvez arrêter l’enregistrement à partir du même emplacement. (N’oubliez pas que vous pouvez toujours le faire avec les commandes vocales.)
* **Project à un appareil compatible Miracast** : Project votre contenu de HoloLens sur un appareil à Surface proche ou une TV/moniteur si vous utilisez un écran ou un adaptateur compatible avec Miracast.
* **nouvelles notifications** : affichez et répondez aux notifications sur HoloLens, comme vous le feriez sur un PC.  
* **Superpositions utiles dans les applications de réalité mixte immersif** : vous verrez maintenant des superpositions telles que le clavier, les boîtes de dialogue, le sélecteur de fichiers, etc. lors de l’utilisation d’applications de réalité mixte immersives.
* **indicateur visuel pour la modification de volume** -quand vous utilisez les boutons monter/descendre en volume sur votre HoloLens vous voyez un indicateur visuel du niveau du volume dans le casque.
* **Nouveaux éléments visuels pour le démarrage de l’appareil** : un indicateur de chargement a été ajouté pendant le processus de démarrage pour fournir des commentaires visuels sur le chargement du système.
* **partage proche** : l’expérience de partage Windows à proximité vous permet de partager une capture avec un appareil Windows proche.  
* **partager à partir de Microsoft Edge** -Microsoft Edge comprend désormais un bouton *partager* . 

### <a name="for-developers"></a>Pour les développeurs

* **[intégration de l’interface utilisateur de capture de réalité mixte dans des applications immersifs](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** : les développeurs peuvent intégrer la capture de réalité mixte dans leurs applications à l’aide de l' [interface utilisateur de capture d’appareil photo](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) intégrée Windows avec quelques lignes de code.

### <a name="for-commercial-customers"></a>Pour les clients commerciaux

* **activer l’approvisionnement après l’installation** : vous pouvez maintenant appliquer un package de configuration du runtime à tout moment à l’aide de Paramètres.
* **accès affecté avec les groupes de Azure AD** : vous pouvez désormais utiliser des groupes Azure AD pour la configuration d’Windows accès affecté pour configurer une configuration plein ou multi-application kiosk.
* **Épingler la connexion sur le commutateur de profil à partir de l’écran** de connexion : la connexion du code confidentiel est maintenant disponible pour « autre utilisateur » dans l’écran de connexion. 
* **lire les informations matérielles de l’appareil via MDM** -les administrateurs informatiques peuvent voir et suivre les HoloLens par numéro de série de l’appareil dans leur console MDM.
* **définir HoloLens nom de l’appareil via MDM (rename)** : les administrateurs informatiques peuvent voir et renommer HoloLens appareils dans leur console MDM.

### <a name="for-international-customers"></a>Pour les clients internationaux

vous pouvez désormais utiliser HoloLens avec une interface utilisateur localisée pour le chinois simplifié ou le japonais, y compris le clavier Pinyin localisé, la dictée, la conversion de texte par synthèse vocale (TTS) et les commandes vocales.

## <a name="known-issues"></a>Problèmes connus

nous avons travaillé dur pour offrir une expérience de Windows Mixed Reality exceptionnelle, mais nous effectuons toujours le suivi de certains problèmes connus. Si vous en trouvez d’autres, faites [-nous part de vos commentaires](/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Après la mise à jour
vous pouvez remarquer les problèmes suivants lors de l’utilisation de l’Mise à jour d’octobre 2018 de Windows 10 sur votre HoloLens :
* **Les applications peuvent se retrouver dans une boucle de connexion lorsqu’elles sont lancées à partir d’une notification** : certaines applications nécessitant une connexion peuvent se retrouver dans une boucle de connexion sans fin lorsqu’elles sont lancées à partir d’une notification. par exemple, cela peut se produire après l’installation de l’application Microsoft Portail d’entreprise à partir du Microsoft Store et son lancement à partir de la notification d’installation terminée.
* La **page de connexion de l’application peut s’exécuter avec une page vierge** : dans certains cas, lorsqu’une invite de connexion s’affiche sur votre application, à la fin, la page de connexion ne se ferme pas et affiche une page vide (noire). Vous pouvez fermer la page vide ou la déplacer pour dévoiler l’application ci-dessous. par exemple, cela peut se produire lors de la connexion lors de l’inscription MDM à partir de l’application Paramètres. 

## <a name="provide-feedback-and-report-issues"></a>Fournir des commentaires et signaler des problèmes

utilisez l' [application Hub de commentaires sur votre HoloLens ou Windows 10 PC](/windows/mixed-reality/give-us-feedback) pour fournir des commentaires et signaler des problèmes. L’utilisation de feedback Hub garantit que toutes les informations de diagnostic nécessaires sont incluses pour aider nos ingénieurs à déboguer et résoudre rapidement le problème.

>[!NOTE]
>Veillez à accepter l’invite qui vous demande si vous souhaitez que le hub de commentaires accède à votre dossier documents (sélectionnez **Oui** lorsque vous y êtes invité).

## <a name="prior-release-notes"></a>Notes de publication antérieures

* [Notes de publication-2018 avril](release-notes-april-2018.md)
* [Notes de publication - Octobre 2017](release-notes-october-2017.md)
* [Notes de publication - Août 2016](release-notes-august-2016.md)
* [Notes de publication - Mai 2016](release-notes-may-2016.md)
* [Notes de publication - Mars 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Voir aussi
* [Prise en charge des casques immersifs (lien externe)](./troubleshooting-windows-mixed-reality.md)
* [prise en charge des HoloLens (lien externe)](https://support.microsoft.com/products/hololens)
* [Installer les outils](/windows/mixed-reality/develop/install-the-tools)
* [Envoyer vos commentaires](/windows/mixed-reality/give-us-feedback)