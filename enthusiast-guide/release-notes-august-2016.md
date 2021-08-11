---
title: Notes de publication - Août 2016
description: restez à jour dans les notes de publication de HoloLens pour la version Windows 10 anniversaire pour automne 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notes de publication, système d’exploitation, plateforme, fonctionnalités, suite commerciale
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202457"
---
# <a name="release-notes---august-2016"></a>Notes de publication - Août 2016

l’équipe HoloLens écoute les commentaires des développeurs du programme Windows insider pour hiérarchiser notre travail. Continuez à [nous faire part de vos commentaires](/windows/mixed-reality/give-us-feedback) via le hub de commentaires, les [Forums des développeurs](https://forums.hololens.com) et [ @HoloLens Twitter via ](https://twitter.com/hololens). comme Windows 10 s’appuie sur la mise à jour anniversaire, l’équipe HoloLens est heureux de fournir davantage d’amélioration à l’expérience holographique. Dans cette mise à jour, nous nous sommes concentrés sur les principaux correctifs, les améliorations et l’introduction des fonctionnalités demandées par les entreprises et disponibles dans le Microsoft HoloLens Commercial Suite.

**dernière version :** Windows la mise à jour 2016 d’août (**10.0.14393.0**, Windows 10 version anniversaire)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

pour effectuer une [mise à jour vers la version actuelle](/windows/mixed-reality/updating-hololens), ouvrez l’application *Paramètres* , accédez à *update & Security*, puis sélectionnez le bouton *rechercher les mises à jour* .

## <a name="new-features"></a>Nouvelles fonctionnalités

l' **attachement au débogage de processus** HoloLens prend maintenant en charge le débogage d’attachement-à-processus. vous pouvez utiliser Visual Studio 2015 Update 3 pour vous connecter à une application en cours d’exécution sur un HoloLens et [démarrer le débogage](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app). cela fonctionne sans qu’il soit nécessaire de déployer à partir d’un projet de Visual Studio.

**mise à jour de HoloLens Emulator** nous avons également publié une version mise à jour du Emulator HoloLens.

**Prise en charge du boîtier de manette** vous pouvez désormais coupler et utiliser des boîtiers de Bluetooth avec HoloLens ! les fonctionnalités de la nouvelle version du contrôleur Xbox Wireless S Bluetooth fonctionnalités et peuvent être utilisées pour jouer à vos jeux et applications préférés. Une [mise à jour du contrôleur](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) doit être appliquée avant de pouvoir connecter le contrôleur Xbox Wireless S avec HoloLens. Le contrôleur Xbox Wireless S est pris en charge par [XInput](/windows/win32/xinput/xinput-game-controller-apis-portal) et [Windows. API Gaming. Input](/uwp/api/Windows.Gaming.Input) . vous pouvez accéder à d’autres modèles de contrôleurs Bluetooth par le biais du [Windows. API Gaming. Input](/uwp/api/Windows.Gaming.Input) .

## <a name="improvements-and-fixes"></a>Améliorations et correctifs

nous sommes synchronisés avec le reste de la mise à jour anniversaire Windows 10. ainsi, en plus des correctifs HoloLens spécifiques, vous recevez également tout le parfait de la mise à jour Windows pour améliorer la fiabilité et les performances de la plateforme. Vos commentaires sont très appréciés et classés par ordre de priorité pour les correctifs de la version.

Nous avons amélioré les expériences suivantes :
* Connectez-vous à l’expérience.
* jonctions de lieux de travail.
* efficacité énergétique des transitions d’état d’alimentation des appareils.
* stabilité avec les captures de la réalité mixte.
* fiabilité de la connectivité Bluetooth
* persistance des hologrammes dans un scénario à plusieurs applications.

Nous avons résolu les problèmes suivants :
* les profileurs et le débogueur de graphiques Visual Studio ne parviennent pas à se connecter.
* les photos & les documents ne sont pas affichés dans l’Explorateur de fichiers du portail des appareils.
* la barre d’application peut clignoter lorsque le curseur est placé au-dessus de lui en mode ajuster.
* En mode d’ajustement, le curseur en forme de point de regard de l’œil passe au curseur à quatre flèches plus lentement.
* « Hey Cortana play music » ne démarre pas Groove.
* après la mise à jour précédente, en disant « Go... » n’affiche pas correctement le panneau pin.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Présentation de Microsoft HoloLens Commercial Suite

le Microsoft HoloLens Commercial Suite est prêt pour le déploiement d’entreprise. Nous avons ajouté plusieurs [fonctionnalités commerciales](/windows/mixed-reality/commercial-features) très demandées auprès de nos premiers partenaires commerciaux.

Contactez votre gestionnaire de compte Microsoft local pour acheter le Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Principales fonctionnalités commerciales 

* **Mode plein écran.** avec HoloLens mode plein écran, vous pouvez limiter les applications à exécuter pour activer les expériences de démonstration ou de démonstration.<br>
  ![en mode plein écran, HoloLens se lance directement dans l’application de votre choix.](images/201608-kioskmode-400px.png)
* **Gestion des périphériques mobiles (GPM) pour HoloLens.** votre service informatique peut gérer plusieurs appareils HoloLens simultanément à l’aide de solutions comme Microsoft Intune. Vous pouvez gérer les paramètres, sélectionner les applications à installer et définir les configurations de sécurité adaptées aux besoins de votre organisation.<br>
  ![la gestion des appareils mobiles sur HoloLens fournit une gestion des appareils à l’échelle de l’entreprise sur plusieurs appareils.](images/201608-enterprisemanagement-400px.png)
* **Windows Update for Business.** Les mises à jour contrôlées du système d’exploitation sur les appareils et la prise en charge de la branche de maintenance à long terme.
* **Sécurité des données** Le chiffrement des données BitLocker est activé sur HoloLens pour fournir le même niveau de protection que sur n'importe quel autre appareil Windows.
* **Accès professionnel.** Toute personne de votre organisation peut se connecter à distance au réseau d’entreprise via un réseau privé virtuel sur un HoloLens. L'HoloLens peut également accéder à des réseaux Wi-Fi qui nécessitent des informations d'identification.
* **Microsoft Store pour Entreprises.** votre service informatique peut également configurer un magasin privé d’entreprise, contenant uniquement les applications de votre entreprise pour votre utilisation de HoloLens spécifique. Distribuez en toute sécurité vos logiciels d'entreprise à certains groupes d'utilisateurs.

### <a name="development-edition-vs-commercial-suite"></a>Édition Development et suite commerciale

<table>
<tr>
<th>Fonctionnalités</th><th>Development Edition</th><th>Suite commerciale</th>
</tr><tr>
<td>Chiffrement de l’appareil (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Réseau privé virtuel (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Mode plein écran</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Gestion et déploiement</th>
</tr><tr>
<td>Gestion des appareils mobiles</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Possibilité de bloquer l'annulation de l'inscription</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Accès Wi-Fi d’entreprise basé sur un certificat</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (grand public)</td><td style="text-align: center;">Consommateur</td><td style="text-align: center;">Filtrage via MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Portail Business Store</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sécurité et identité</th>
</tr><tr>
<td>Connexion avec Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Se connecter avec un compte Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Informations d'identification nouvelle génération avec déverrouillage par code PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Démarrage sécurisé</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Maintenance et support</th>
</tr><tr>
<td>Mises à jour système automatiques à mesure qu'elles arrivent</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Long-Term Servicing Branch</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Notes de publication antérieures
* [Notes de publication - Mai 2016](release-notes-may-2016.md)
* [Notes de publication - Mars 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Voir aussi
* [Problèmes connus concernant HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Fonctionnalités commerciales](/windows/mixed-reality/commercial-features)
* [Installer les outils](/windows/mixed-reality/develop/install-the-tools)
* [Utilisation de l’émulateur HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)